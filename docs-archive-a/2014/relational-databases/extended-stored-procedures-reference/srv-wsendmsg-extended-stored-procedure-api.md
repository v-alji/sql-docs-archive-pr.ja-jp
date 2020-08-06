---
title: srv_wsendmsg (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_wsendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
ms.openlocfilehash: 4cc915cce0befccb5c5af58e703c11b750af855b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742106"
---
# <a name="srv_wsendmsg-extended-stored-procedure-api"></a><span data-ttu-id="86d18-102">srv_wsendmsg (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="86d18-102">srv_wsendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="86d18-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="86d18-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="86d18-104">クライアントに Unicode メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="86d18-104">Sends a Unicode message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d18-105">構文</span><span class="sxs-lookup"><span data-stu-id="86d18-105">Syntax</span></span>  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="86d18-106">引数</span><span class="sxs-lookup"><span data-stu-id="86d18-106">Arguments</span></span>  
 <span data-ttu-id="86d18-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="86d18-107">*srvproc*</span></span>  
 <span data-ttu-id="86d18-108">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="86d18-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="86d18-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="86d18-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="86d18-110">*Msgnum*</span><span class="sxs-lookup"><span data-stu-id="86d18-110">*Msgnum*</span></span>  
 <span data-ttu-id="86d18-111">4 バイトのメッセージ番号です。</span><span class="sxs-lookup"><span data-stu-id="86d18-111">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="86d18-112">*Severity*</span><span class="sxs-lookup"><span data-stu-id="86d18-112">*Severity*</span></span>  
 <span data-ttu-id="86d18-113">エラーの重大度を指定します。</span><span class="sxs-lookup"><span data-stu-id="86d18-113">Specifies the severity of the error.</span></span> <span data-ttu-id="86d18-114">重大度が 10 以下の場合は情報メッセージと見なされ、10 より大きい場合はエラー メッセージと見なされます。</span><span class="sxs-lookup"><span data-stu-id="86d18-114">A severity less than or equal to 10 is considered an informational message; otherwise, it is an error.</span></span>  
  
 <span data-ttu-id="86d18-115">*message*</span><span class="sxs-lookup"><span data-stu-id="86d18-115">*message*</span></span>  
 <span data-ttu-id="86d18-116">クライアントに送信される Unicode 文字列を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="86d18-116">Is a pointer to a Unicode string to be sent to the client.</span></span>  
  
 <span data-ttu-id="86d18-117">*msglen*</span><span class="sxs-lookup"><span data-stu-id="86d18-117">*msglen*</span></span>  
 <span data-ttu-id="86d18-118">*message* の長さを文字数で指定します。</span><span class="sxs-lookup"><span data-stu-id="86d18-118">Specifies the length, in characters, of *message*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="86d18-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="86d18-119">Returns</span></span>  
 <span data-ttu-id="86d18-120">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="86d18-120">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86d18-121">解説</span><span class="sxs-lookup"><span data-stu-id="86d18-121">Remarks</span></span>  
 <span data-ttu-id="86d18-122">この関数は、Unicode でメッセージを送信するために使用します。</span><span class="sxs-lookup"><span data-stu-id="86d18-122">Use this function to send messages in Unicode.</span></span> <span data-ttu-id="86d18-123">この関数は **srv_sendmsg** と似ていますが、送信されるメッセージは DBCHAR 型ではなく WCHAR 型の文字列です。</span><span class="sxs-lookup"><span data-stu-id="86d18-123">It is similar to **srv_sendmsg**, but the message it sends is a WCHAR string rather than type DBCHAR string.</span></span> <span data-ttu-id="86d18-124">メッセージの長さはバイト数ではなく文字数で報告され、*msglen* が SRV_NULLTERM とは等しくならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="86d18-124">Note that message length is reported in characters rather than bytes, and *msglen* will never be equal to SRV_NULLTERM.</span></span>  
  
 <span data-ttu-id="86d18-125">次の場合、この関数は FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="86d18-125">The function returns FAIL when</span></span>  
  
-   <span data-ttu-id="86d18-126">*msglen* が 0 から 32242 の範囲内にない場合。</span><span class="sxs-lookup"><span data-stu-id="86d18-126">The *msglen* given is not in the range of 0-32242.</span></span>  
  
-   <span data-ttu-id="86d18-127">*msglen* が 0 で、メッセージ ポインターが NULL の場合。</span><span class="sxs-lookup"><span data-stu-id="86d18-127">The *msglen* given is 0 but the message pointer is NULL.</span></span>  
  
-   <span data-ttu-id="86d18-128">ネットワーク経由でエラー メッセージを送信するときにエラーが発生した場合。</span><span class="sxs-lookup"><span data-stu-id="86d18-128">There is error when sending the error message through network.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="86d18-129">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86d18-129">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="86d18-130">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86d18-130">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d18-131">参照</span><span class="sxs-lookup"><span data-stu-id="86d18-131">See Also</span></span>  
 [<span data-ttu-id="86d18-132">srv_sendmsg &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="86d18-132">srv_sendmsg &#40;Extended Stored Procedure API&#41;</span></span>](srv-sendmsg-extended-stored-procedure-api.md)  
  
  
