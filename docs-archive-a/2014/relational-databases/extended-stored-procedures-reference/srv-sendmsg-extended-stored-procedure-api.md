---
title: srv_sendmsg (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
author: rothja
ms.author: jroth
ms.openlocfilehash: 0821ad88f48313cfadea634a489def9b242a49f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743234"
---
# <a name="srv_sendmsg-extended-stored-procedure-api"></a><span data-ttu-id="390bf-102">srv_sendmsg (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="390bf-102">srv_sendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="390bf-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="390bf-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="390bf-104">クライアントにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="390bf-104">Sends a message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="390bf-105">Syntax</span></span>  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="390bf-106">引数</span><span class="sxs-lookup"><span data-stu-id="390bf-106">Arguments</span></span>  
 <span data-ttu-id="390bf-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="390bf-107">*srvproc*</span></span>  
 <span data-ttu-id="390bf-108">特定のクライアント接続のためのハンドル (この場合は、言語要求を受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="390bf-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="390bf-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="390bf-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="390bf-110">*msgtype*</span><span class="sxs-lookup"><span data-stu-id="390bf-110">*msgtype*</span></span>  
 <span data-ttu-id="390bf-111">サーバーから送信されるメッセージの種類が情報メッセージかエラー メッセージかによって、SRV_MSG_INFO または SRV_MSG_ERROR を指定します。</span><span class="sxs-lookup"><span data-stu-id="390bf-111">Is either SRV_MSG_INFO or SRV_MSG_ERROR, depending on whether the server is sending an informational or error message.</span></span>  
  
 <span data-ttu-id="390bf-112">*msgnum*</span><span class="sxs-lookup"><span data-stu-id="390bf-112">*msgnum*</span></span>  
 <span data-ttu-id="390bf-113">4 バイトのメッセージ番号です。</span><span class="sxs-lookup"><span data-stu-id="390bf-113">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="390bf-114">*class*</span><span class="sxs-lookup"><span data-stu-id="390bf-114">*class*</span></span>  
 <span data-ttu-id="390bf-115">エラーの重大度を指定します。</span><span class="sxs-lookup"><span data-stu-id="390bf-115">Specifies the error severity.</span></span> <span data-ttu-id="390bf-116">重大度が 10 以下の場合は、情報メッセージと見なされます。</span><span class="sxs-lookup"><span data-stu-id="390bf-116">A severity less than or equal to 10 is considered an informational message.</span></span>  
  
 <span data-ttu-id="390bf-117">*状態*</span><span class="sxs-lookup"><span data-stu-id="390bf-117">*state*</span></span>  
 <span data-ttu-id="390bf-118">現在のメッセージのエラー状態番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="390bf-118">Provides the error state number for the current message.</span></span> <span data-ttu-id="390bf-119">エラー状態番号により、エラーの内容に関する情報を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="390bf-119">The error state number provides information about the context of the error.</span></span> <span data-ttu-id="390bf-120">有効な状態番号の範囲は 0 ～ 255 です。</span><span class="sxs-lookup"><span data-stu-id="390bf-120">Valid state numbers are from 0 through 255.</span></span>  
  
 <span data-ttu-id="390bf-121">*rpcname*</span><span class="sxs-lookup"><span data-stu-id="390bf-121">*rpcname*</span></span>  
 <span data-ttu-id="390bf-122">現時点では、サポートされません。</span><span class="sxs-lookup"><span data-stu-id="390bf-122">Is currently not supported.</span></span>  
  
 <span data-ttu-id="390bf-123">*rpcnamelen*</span><span class="sxs-lookup"><span data-stu-id="390bf-123">*rpcnamelen*</span></span>  
 <span data-ttu-id="390bf-124">現時点では、サポートされません。</span><span class="sxs-lookup"><span data-stu-id="390bf-124">Is currently not supported.</span></span>  
  
 <span data-ttu-id="390bf-125">*linenum*</span><span class="sxs-lookup"><span data-stu-id="390bf-125">*linenum*</span></span>  
 <span data-ttu-id="390bf-126">メッセージが該当する言語コマンド バッチ内の行番号です。</span><span class="sxs-lookup"><span data-stu-id="390bf-126">Is the line number in the language command batch where the message applies.</span></span> <span data-ttu-id="390bf-127">行番号は 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="390bf-127">Line numbers start at 1.</span></span> <span data-ttu-id="390bf-128">メッセージに *linenum* が不要である場合は、0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="390bf-128">If *linenum* does not apply to the message, set to 0.</span></span>  
  
 <span data-ttu-id="390bf-129">*message*</span><span class="sxs-lookup"><span data-stu-id="390bf-129">*message*</span></span>  
 <span data-ttu-id="390bf-130">クライアントに送信される文字列を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="390bf-130">Is a pointer to the character string to be sent to the client.</span></span>  
  
 <span data-ttu-id="390bf-131">*msglen*</span><span class="sxs-lookup"><span data-stu-id="390bf-131">*msglen*</span></span>  
 <span data-ttu-id="390bf-132">*message* の長さをバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="390bf-132">Specifies the length, in bytes, of *message*.</span></span> <span data-ttu-id="390bf-133">*message* が NULL 終端である場合は、*msglen* を SRV_NULLTERM に設定します。</span><span class="sxs-lookup"><span data-stu-id="390bf-133">If *message* is null-terminated, set *msglen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="390bf-134">戻り値</span><span class="sxs-lookup"><span data-stu-id="390bf-134">Returns</span></span>  
 <span data-ttu-id="390bf-135">SUCCEED または FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="390bf-135">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="390bf-136">解説</span><span class="sxs-lookup"><span data-stu-id="390bf-136">Remarks</span></span>  
 <span data-ttu-id="390bf-137">この関数は、エラー メッセージまたは情報メッセージをクライアントに送信する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="390bf-137">This function sends error or informational messages to the client.</span></span> <span data-ttu-id="390bf-138">メッセージが送信されるたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="390bf-138">It is called once for each message to be sent.</span></span>  
  
 <span data-ttu-id="390bf-139">メッセージは、**srv_sendrow** によるすべての行 (あれば) の送信前後に任意の順序で **srv_sendmsg** を使用してクライアントに送信できます。</span><span class="sxs-lookup"><span data-stu-id="390bf-139">Messages can be sent to the client with **srv_sendmsg** in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="390bf-140">すべてのメッセージ (あれば) は **srv_senddone** で完了状態が送信される前にクライアントに送信しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="390bf-140">All messages, if any, must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
 <span data-ttu-id="390bf-141">Unicode でメッセージを送信するには、**srv_sendmsg** ではなく **srv_wsendmsg** を使用してください。</span><span class="sxs-lookup"><span data-stu-id="390bf-141">To send messages in Unicode, use **srv_wsendmsg** rather than **srv_sendmsg**.</span></span>  
  
 <span data-ttu-id="390bf-142">詳しくは、「[Unicode データおよびサーバー コード ページ](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="390bf-142">For more information see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="390bf-143">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="390bf-143">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="390bf-144">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="390bf-144">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
