---
title: bcp_sendrow |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d2f55486ba57101ffc7b1903de5d19ac8eaaca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634504"
---
# <a name="bcp_sendrow"></a><span data-ttu-id="b783c-102">bcp_sendrow</span><span class="sxs-lookup"><span data-stu-id="b783c-102">bcp_sendrow</span></span>
  <span data-ttu-id="b783c-103">プログラム変数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にデータ行を送信します。</span><span class="sxs-lookup"><span data-stu-id="b783c-103">Sends a row of data from program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b783c-104">構文</span><span class="sxs-lookup"><span data-stu-id="b783c-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b783c-105">引数</span><span class="sxs-lookup"><span data-stu-id="b783c-105">Arguments</span></span>  
 <span data-ttu-id="b783c-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="b783c-106">*hdbc*</span></span>  
 <span data-ttu-id="b783c-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="b783c-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b783c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b783c-108">Returns</span></span>  
 <span data-ttu-id="b783c-109">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="b783c-109">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b783c-110">解説</span><span class="sxs-lookup"><span data-stu-id="b783c-110">Remarks</span></span>  
 <span data-ttu-id="b783c-111">**Bcp_sendrow**関数は、プログラム変数から行を作成し、に送信し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b783c-111">The **bcp_sendrow** function builds a row from program variables and sends it to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b783c-112">**Bcp_sendrow**を呼び出す前に、行データを含むプログラム変数を指定するために[bcp_bind](bcp-bind.md)の呼び出しを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b783c-112">Before calling **bcp_sendrow**, you must make calls to [bcp_bind](bcp-bind.md) to specify the program variables containing row data.</span></span>  
  
 <span data-ttu-id="b783c-113">Long 型の可変長データ型を指定して**bcp_bind**が呼び出された場合 (たとえば、SQLTEXT の*Edatatype*パラメーターと null 以外の*pData*パラメーター)、 **bcp_sendrow**他のデータ型の場合と同様に、entiredata 値が送信されます。</span><span class="sxs-lookup"><span data-stu-id="b783c-113">If **bcp_bind** is called specifying a long, variable-length data type, for example, an *eDataType* parameter of SQLTEXT and a nonNULL *pData* parameter, **bcp_sendrow** sends the entiredata value, just as it does for any other data type.</span></span> <span data-ttu-id="b783c-114">ただし、 **bcp_bind**に*PDATA*パラメーターが NULL の場合は、指定されたデータを含むすべての列がに送信された直後に、 **bcp_sendrow**制御がアプリケーションに返され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b783c-114">If, however, **bcp_bind** has a NULL *pData* parameter, **bcp_sendrow** returns control to the application immediately after all columns with data specified are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b783c-115">その後、アプリケーションは[bcp_moretext](bcp-moretext.md)を繰り返し呼び出して、長い可変長データをチャンクとして一度に送信でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b783c-115">The application can then call [bcp_moretext](bcp-moretext.md) repeatedly to send the long, variable-length data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a chunk at a time.</span></span> <span data-ttu-id="b783c-116">詳細については、「 [bcp_moretext](bcp-moretext.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b783c-116">For more information, see [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="b783c-117">プログラム変数からテーブルに行を一括コピーするために**bcp_sendrow**を使用する場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ユーザーが[bcp_batch](bcp-batch.md)または[bcp_done](bcp-done.md)を呼び出したときにのみ行がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="b783c-117">When **bcp_sendrow** is used to bulk copy rows from program variables into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, rows are committed only when the user calls [bcp_batch](bcp-batch.md) or [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="b783c-118">ユーザーは、 *n*行ごとに**bcp_batch**を呼び出すことも、受信データの期間間になどがあるときに呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="b783c-118">The user can choose to call **bcp_batch** once every *n* rows or when there is a lull between periods of incoming data.</span></span> <span data-ttu-id="b783c-119">**Bcp_batch**が呼び出されない場合、 **bcp_done**が呼び出されたときに行がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="b783c-119">If **bcp_batch** is never called, the rows are committed when **bcp_done** is called.</span></span>  
  
 <span data-ttu-id="b783c-120">での一括コピーの重大な変更については [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、「 [ODBC&#41;&#40;の一括コピー操作の実行](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b783c-120">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b783c-121">参照</span><span class="sxs-lookup"><span data-stu-id="b783c-121">See Also</span></span>  
 [<span data-ttu-id="b783c-122">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="b783c-122">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
