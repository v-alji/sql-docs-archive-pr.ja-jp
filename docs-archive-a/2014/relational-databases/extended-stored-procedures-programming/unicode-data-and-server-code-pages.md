---
title: Unicode データおよびサーバーコードページ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- Unicode [SQL Server], extended stored procedures
- extended stored procedures [SQL Server], metadata
ms.assetid: 52310260-a892-4b27-ad2e-bf164b98ee80
author: rothja
ms.author: jroth
ms.openlocfilehash: e88a43ee242e9fa84ac3a5573c7d3ca3dc0369d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631027"
---
# <a name="unicode-data-and-server-code-pages"></a><span data-ttu-id="ccbee-102">Unicode データおよびサーバー コード ページ</span><span class="sxs-lookup"><span data-stu-id="ccbee-102">Unicode Data and Server Code Pages</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="ccbee-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="ccbee-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="ccbee-104">拡張ストアド プロシージャ API は、Unicode データを扱うことはできますが、Unicode メタデータを扱うことはできません。</span><span class="sxs-lookup"><span data-stu-id="ccbee-104">The Extended Stored Procedure API is enabled for Unicode data; however, it is not enabled for Unicode metadata.</span></span> <span data-ttu-id="ccbee-105">#define Unicode ディレクティブは、拡張ストアド プロシージャ API にまったく影響しません。</span><span class="sxs-lookup"><span data-stu-id="ccbee-105">The #define Unicode directive does not have any effect on the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="ccbee-106">拡張ストアド プロシージャ API が返したメタデータ、または拡張ストアド プロシージャ アプリケーションによって拡張ストアド プロシージャ API に渡されたメタデータは、すべてサーバーのマルチバイト コード ページにあることが想定されています。</span><span class="sxs-lookup"><span data-stu-id="ccbee-106">All metadata returned by, or provided to the Extended Stored Procedure API by your extended stored procedure application is assumed to be in the multibyte code page of the server.</span></span> <span data-ttu-id="ccbee-107">拡張ストアドプロシージャ API サーバーアプリケーションの既定のコードページは、アプリケーションが実行されているコンピューターの ANSI コードページです。これは、SRV_SPROC_CODEPAGE に設定されたフィールドパラメーターを使用して**srv_pfield**を呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="ccbee-107">The default code page of an Extended Stored Procedure API server application is the ANSI code page of the computer on which the application is running, which can be obtained by calling **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE.</span></span>  
  
 <span data-ttu-id="ccbee-108">Unicode 対応の拡張ストアド プロシージャ API アプリケーションの場合は、Unicode メタデータの列名やエラー メッセージなどを拡張ストアド プロシージャ API に渡す前に、マルチバイト データに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccbee-108">If your Extended Stored Procedure API application is Unicode-enabled, you must convert your Unicode metadata column names, error messages, and so on, to multibyte data before passing this data to the Extended Stored Procedure API.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccbee-109">例</span><span class="sxs-lookup"><span data-stu-id="ccbee-109">Example</span></span>  
 <span data-ttu-id="ccbee-110">次の拡張ストアド プロシージャは、上記で説明した Unicode 変換の例です。</span><span class="sxs-lookup"><span data-stu-id="ccbee-110">The following extended stored procedure provides an example of the Unicode conversions discussed.</span></span> <span data-ttu-id="ccbee-111">以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="ccbee-111">Note that:</span></span>  
  
-   <span data-ttu-id="ccbee-112">列が SRVNVARCHAR として記述されているので、列データは Unicode データとして**srv_describe**に渡されます。</span><span class="sxs-lookup"><span data-stu-id="ccbee-112">Column data is passed as Unicode data to **srv_describe** because the column is described to be SRVNVARCHAR.</span></span>  
  
-   <span data-ttu-id="ccbee-113">列名のメタデータは、マルチバイトデータとして**srv_describe**に渡されます。</span><span class="sxs-lookup"><span data-stu-id="ccbee-113">Column name metadata is passed to **srv_describe** as multibyte data.</span></span>  
  
     <span data-ttu-id="ccbee-114">拡張ストアドプロシージャは、フィールドパラメーターを SRV_SPROC_CODEPAGE に設定して**srv_pfield**を呼び出し、のマルチバイトコードページを取得し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ccbee-114">The extended stored procedure calls **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE to obtain the multibyte code page of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ccbee-115">エラーメッセージは、マルチバイトデータとして**srv_sendmsg**に渡されます。</span><span class="sxs-lookup"><span data-stu-id="ccbee-115">Error messages are passed to **srv_sendmsg** as multibyte data.</span></span>  
  
    ```  
    __declspec(dllexport) RETCODE proc1 (SRV_PROC *srvproc)  
    {  
        #define MAX_COL_NAME_LEN 25  
        #define MAX_COL_DATA_LEN 50  
        #define MAX_ERR_MSG_LEN 250  
        #define MAX_SERVER_ERROR 20000  
        #define XP_ERROR_NUMBER MAX_SERVER_ERROR+1  
  
        int retval;  
        UINT serverCodePage;  
        CHAR *szServerCodePage;  
  
        WCHAR unicodeColumnName[MAX_COL_NAME_LEN];  
        CHAR multibyteColumnName[MAX_COL_NAME_LEN];  
  
        WCHAR unicodeColumnData[MAX_COL_DATA_LEN];  
  
        WCHAR unicodeErrorMessage[MAX_ERR_MSG_LEN];  
        CHAR  multibyteErrorMessage[MAX_ERR_MSG_LEN];  
  
        lstrcpyW (unicodeColumnName, L"column1");  
        lstrcpyW (unicodeColumnData, L"column1 data");  
        lstrcpyW (unicodeErrorMessage, L"No Error!");  
  
        // Obtain server code page.  
        //  
        szServerCodePage = srv_pfield (srvproc, SRV_SPROC_CODEPAGE, NULL);      
        if (NULL != szServerCodePage)  
            serverCodePage = atol(szServerCodePage);  
        else   
        {   // Problem situation exists.  
            srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
            return 1;  
        }  
  
        // Convert column name for Unicode to multibyte using the   
        // server code page.  
        //  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeColumnName,              // wide-character string  
            -1,                             // string is null terminated  
            multibyteColumnName,            // address of buffer for new  
                                            //   string  
            sizeof (multibyteColumnName),   // size of buffer  
            NULL, NULL);  
  
        if (0 == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"Conversion to multibyte  
            failed.");  
            goto Error;  
        }  
  
        retval = srv_describe (srvproc, 1, multibyteColumnName,  
        SRV_NULLTERM,   
          SRVNVARCHAR, MAX_COL_DATA_LEN*sizeof(WCHAR), // destination  
            SRVNVARCHAR, lstrlenW(unicodeColumnData)*sizeof(WCHAR),  
            unicodeColumnData); //source  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_describe failed.");  
            goto Error;  
        }  
  
       retval = srv_sendrow(srvproc);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_sendrow failed.");  
            goto Error;  
        }  
  
        retval = srv_senddone (srvproc, SRV_DONE_MORE|SRV_DONE_COUNT, 0, 1);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_senddone failed.");  
            goto Error;  
        }  
  
        return 0;  
    Error:  
        // convert error message from Unicode to multibyte.  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeErrorMessage,            // wide-character string  
            -1,                             // string is null terminated  
            multibyteErrorMessage,          // address of buffer for new  
                                            //   string  
            sizeof (multibyteErrorMessage), // size of buffer  
            NULL, NULL);  
  
    srv_sendmsg(srvproc, SRV_MSG_ERROR, XP_ERROR_NUMBER, SRV_INFO, 1,  
                NULL, 0, __LINE__,   
                multibyteErrorMessage,  
                SRV_NULLTERM);  
  
        srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
  
        return 1;  
    }  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ccbee-116">参照</span><span class="sxs-lookup"><span data-stu-id="ccbee-116">See Also</span></span>  
 [<span data-ttu-id="ccbee-117">srv_wsendmsg &#40;拡張ストアドプロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="ccbee-117">srv_wsendmsg &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-wsendmsg-extended-stored-procedure-api.md)  
  
  
