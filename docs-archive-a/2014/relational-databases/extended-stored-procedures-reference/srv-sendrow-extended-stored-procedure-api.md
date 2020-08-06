---
title: srv_sendrow (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendrow
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: df40348b8792a70f84719abfb42152fda9487e6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743233"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a><span data-ttu-id="7f3cc-102">srv_sendrow (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="7f3cc-102">srv_sendrow (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="7f3cc-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="7f3cc-104">クライアントに 1 行のデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-104">Transmits a row of data to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f3cc-105">構文</span><span class="sxs-lookup"><span data-stu-id="7f3cc-105">Syntax</span></span>  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f3cc-106">引数</span><span class="sxs-lookup"><span data-stu-id="7f3cc-106">Arguments</span></span>  
 <span data-ttu-id="7f3cc-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="7f3cc-107">*srvproc*</span></span>  
 <span data-ttu-id="7f3cc-108">特定のクライアント接続のためのハンドル (この場合は、言語要求を受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="7f3cc-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7f3cc-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f3cc-110">Returns</span></span>  
 <span data-ttu-id="7f3cc-111">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f3cc-112">解説</span><span class="sxs-lookup"><span data-stu-id="7f3cc-112">Remarks</span></span>  
 <span data-ttu-id="7f3cc-113">**srv_sendrow** 関数は、クライアントに送信される各行につき 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-113">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="7f3cc-114">**srv_sendmsg**、**srv_status**、または **srv_senddone** を使用してメッセージ、状態値、または完了状態を送信する前に、すべての行をクライアントに送信しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-114">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, **srv_status**, or **srv_senddone**.</span></span>  
  
 <span data-ttu-id="7f3cc-115">**srv_describe** によってすべての列を定義していない行を送信すると、拡張ストアド プロシージャ API アプリケーションで情報エラー メッセージが生成され、クライアントに FAIL が返されます。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-115">Sending a row that has not had all its columns defined with **srv_describe** causes the Extended Stored Procedure API application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="7f3cc-116">この場合、その行は送信されません。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-116">In this case, the row is not sent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f3cc-117">拡張ストアド プロシージャ API ではクライアントへの計算行の送信はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-117">The Extended Stored Procedure API does not support sending compute rows to the client.</span></span> <span data-ttu-id="7f3cc-118">また、`ntext` 型、`text` 型、または `image` 型のデータを格納している行をクライアントに送信した場合、テキスト ポインターおよびテキスト タイムスタンプは含まれません。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-118">Also, if a row containing `ntext`, `text`, or `image` data is sent to the client, the text pointer and text timestamp are not included.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7f3cc-119">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="7f3cc-120">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7f3cc-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f3cc-121">参照</span><span class="sxs-lookup"><span data-stu-id="7f3cc-121">See Also</span></span>  
 [<span data-ttu-id="7f3cc-122">srv_describe &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="7f3cc-122">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
