---
title: srv_senddone (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_senddone
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
author: rothja
ms.author: jroth
ms.openlocfilehash: 877acdc1b666c7f4cbaab737590a1c55e474eb05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743238"
---
# <a name="srv_senddone-extended-stored-procedure-api"></a><span data-ttu-id="c5d98-102">srv_senddone (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="c5d98-102">srv_senddone (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="c5d98-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="c5d98-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="c5d98-104">結果完了メッセージをクライアントに送信します。</span><span class="sxs-lookup"><span data-stu-id="c5d98-104">Sends a result completion message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d98-105">構文</span><span class="sxs-lookup"><span data-stu-id="c5d98-105">Syntax</span></span>  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5d98-106">引数</span><span class="sxs-lookup"><span data-stu-id="c5d98-106">Arguments</span></span>  
 <span data-ttu-id="c5d98-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="c5d98-107">*srvproc*</span></span>  
 <span data-ttu-id="c5d98-108">特定のクライアント接続のためのハンドル (この場合は、言語要求を受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="c5d98-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="c5d98-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5d98-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="c5d98-110">*status*</span><span class="sxs-lookup"><span data-stu-id="c5d98-110">*status*</span></span>  
 <span data-ttu-id="c5d98-111">各種の *status* フラグに使用する 2 バイトのフィールドです。</span><span class="sxs-lookup"><span data-stu-id="c5d98-111">Is a 2-byte field for various *status* flags.</span></span> <span data-ttu-id="c5d98-112">*status* フラグの値に AND 論理演算子や OR 論理演算子を使用することにより、複数のフラグを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c5d98-112">Multiple flags can be set by using the AND and OR logical operators with *status* flag values.</span></span> <span data-ttu-id="c5d98-113">次の表は、使用可能な *status* フラグを示しています。</span><span class="sxs-lookup"><span data-stu-id="c5d98-113">The following table lists possible *status* flags.</span></span>  
  
|<span data-ttu-id="c5d98-114">status フラグ</span><span class="sxs-lookup"><span data-stu-id="c5d98-114">Status flag</span></span>|<span data-ttu-id="c5d98-115">説明</span><span class="sxs-lookup"><span data-stu-id="c5d98-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c5d98-116">SRV_DONE_COUNT</span><span class="sxs-lookup"><span data-stu-id="c5d98-116">SRV_DONE_COUNT</span></span>|<span data-ttu-id="c5d98-117">*count* パラメーターに有効なカウントを格納します。</span><span class="sxs-lookup"><span data-stu-id="c5d98-117">The *count* parameter contains a valid count.</span></span>|  
|<span data-ttu-id="c5d98-118">SRV_DONE_ERROR</span><span class="sxs-lookup"><span data-stu-id="c5d98-118">SRV_DONE_ERROR</span></span>|<span data-ttu-id="c5d98-119">現在のクライアント コマンドがエラーを受け取ったことを示します。</span><span class="sxs-lookup"><span data-stu-id="c5d98-119">The current client command received an error.</span></span>|  
  
 <span data-ttu-id="c5d98-120">*info*</span><span class="sxs-lookup"><span data-stu-id="c5d98-120">*info*</span></span>  
 <span data-ttu-id="c5d98-121">2 バイトの予約フィールドです。</span><span class="sxs-lookup"><span data-stu-id="c5d98-121">Is a reserved, 2-byte field.</span></span> <span data-ttu-id="c5d98-122">この値は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="c5d98-122">Set this value to 0.</span></span>  
  
 <span data-ttu-id="c5d98-123">*count*</span><span class="sxs-lookup"><span data-stu-id="c5d98-123">*count*</span></span>  
 <span data-ttu-id="c5d98-124">現在の結果セットに対するカウントを示す 4 バイト フィールドです。</span><span class="sxs-lookup"><span data-stu-id="c5d98-124">Is a 4-byte field used to indicate a count for the current result set.</span></span> <span data-ttu-id="c5d98-125">*status* フィールドに SRV_DONE_COUNT フラグを設定した場合、*count* には有効なカウントが格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5d98-125">If the SRV_DONE_COUNT flag is set in the *status* field, *count* holds a valid count.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="c5d98-126">戻り値</span><span class="sxs-lookup"><span data-stu-id="c5d98-126">Returns</span></span>  
 <span data-ttu-id="c5d98-127">SUCCEED または FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="c5d98-127">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5d98-128">解説</span><span class="sxs-lookup"><span data-stu-id="c5d98-128">Remarks</span></span>  
 <span data-ttu-id="c5d98-129">サーバーは 1 つのクライアント要求から、複数のコマンドを実行して複数の結果セットを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c5d98-129">A client request can cause the server to execute a number of commands and to return a number of result sets.</span></span> <span data-ttu-id="c5d98-130">**srv_senddone** は、各結果セットに対して結果完了メッセージをクライアントに返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5d98-130">For each result set, **srv_senddone** must return a result completion message to the client.</span></span>  
  
 <span data-ttu-id="c5d98-131">*count* フィールドは、コマンドの影響を受ける行数を示します。</span><span class="sxs-lookup"><span data-stu-id="c5d98-131">The *count* field indicates the number of rows affected by a command.</span></span> <span data-ttu-id="c5d98-132">*count* フィールドにカウントが格納されている場合は、*status* フィールドに SRV_DONE_COUNT フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5d98-132">If the *count* field contains a count, the SRV_DONE_COUNT flag should be set in the *status* field.</span></span> <span data-ttu-id="c5d98-133">この設定により、*count* の値が 0 かどうか、*count* フィールドが使用されていないのかをクライアントが区別できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c5d98-133">This setting allows the client to distinguish between a *count* value of 0 and an unused *count* field.</span></span>  
  
 <span data-ttu-id="c5d98-134">**srv_senddone** を SRV_CONNECT ハンドラーから呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="c5d98-134">Do not call **srv_senddone** from the SRV_CONNECT handler.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c5d98-135">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5d98-135">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="c5d98-136">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c5d98-136">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
