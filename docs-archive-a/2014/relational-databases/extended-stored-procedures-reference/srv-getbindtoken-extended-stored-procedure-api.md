---
title: srv_getbindtoken (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_getbindtoken
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_getbindtoken
ms.assetid: c947d011-08ac-4fb8-b925-3da6e0999277
author: rothja
ms.author: jroth
ms.openlocfilehash: d42f95c8a7df87f20ebaa30501b96b5f2a00815a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645072"
---
# <a name="srv_getbindtoken-extended-stored-procedure-api"></a><span data-ttu-id="58763-102">srv_getbindtoken (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="58763-102">srv_getbindtoken (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="58763-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="58763-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="58763-104">拡張ストアド プロシージャを起動する現在のクライアント セッションに含まれるトランザクションのバインド トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="58763-104">Obtains a bind token of the transaction in the current client session that invokes the extended stored procedure.</span></span>  
  
 <span data-ttu-id="58763-105">すると拡張ストアド プロシージャは **sp_bindsession** を使用して、同じサーバーに対して作成した新しいセッションを既存のトランザクションにバインドします。これにより新しいセッションは、この拡張ストアド プロシージャを起動したクライアント セッションと、同じトランザクション ロック領域を共有できるようになります。</span><span class="sxs-lookup"><span data-stu-id="58763-105">The extended stored procedure can then use **sp_bindsession** to bind any new session it creates against the same server to the existing transaction so that the new session can share the same transaction lock space with the client session that invoked the extended stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58763-106">構文</span><span class="sxs-lookup"><span data-stu-id="58763-106">Syntax</span></span>  
  
```  
  
int srv_getbindtoken (  
SRV_PROC*  
srvproc  
,  
char*  
bindtoken  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="58763-107">引数</span><span class="sxs-lookup"><span data-stu-id="58763-107">Arguments</span></span>  
 <span data-ttu-id="58763-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="58763-108">*srvproc*</span></span>  
 <span data-ttu-id="58763-109">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="58763-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="58763-110">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用するすべての情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="58763-110">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="58763-111">*bindtoken*</span><span class="sxs-lookup"><span data-stu-id="58763-111">*bindtoken*</span></span>  
 <span data-ttu-id="58763-112">バインド トークンのコピー先バッファーを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="58763-112">Is a pointer to a buffer where the bind token will be copied.</span></span> <span data-ttu-id="58763-113">バインド トークンは NULL 終端文字列として表されます。</span><span class="sxs-lookup"><span data-stu-id="58763-113">The bind token is represented as a null-terminated string.</span></span> <span data-ttu-id="58763-114">指定するバッファーは、255 バイト以上の長さにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="58763-114">The buffer you specify should be at least 255 bytes in length.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="58763-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="58763-115">Returns</span></span>  
 <span data-ttu-id="58763-116">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="58763-116">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58763-117">解説</span><span class="sxs-lookup"><span data-stu-id="58763-117">Remarks</span></span>  
  
### <a name="to-bind-an-extended-stored-procedure-session-to-the-client-session-that-called-it-so-they-share-the-same-transaction-lock-space"></a><span data-ttu-id="58763-118">同じトランザクション ロック領域を共有するために、拡張ストアド プロシージャのセッションを呼び出し元のクライアント セッションにバインドするには</span><span class="sxs-lookup"><span data-stu-id="58763-118">To bind an extended stored procedure session to the client session that called it so they share the same transaction lock space</span></span>  
  
1.  <span data-ttu-id="58763-119">拡張ストアド プロシージャが **svr_getbindtoken** を呼び出し、そのセッションの現在のトランザクションのバインド トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="58763-119">The extended stored procedure calls **svr_getbindtoken** to get the bind token for the current transaction in the session.</span></span> <span data-ttu-id="58763-120">トークンは、指定された *bindtoken* パラメーターで返されます。</span><span class="sxs-lookup"><span data-stu-id="58763-120">The token is returned in the given *bindtoken* parameter.</span></span>  
  
2.  <span data-ttu-id="58763-121">拡張ストアド プロシージャが同じサーバーに対して新しいセッションを開きます。</span><span class="sxs-lookup"><span data-stu-id="58763-121">The extended stored procedure opens new session(s) against the same server.</span></span> <span data-ttu-id="58763-122">そのセッション内で、拡張ストアド プロシージャが **sp_bindsession** を含むバインド トークンを使用し、新しいセッションを同じトランザクションにバインドします。</span><span class="sxs-lookup"><span data-stu-id="58763-122">Inside that session, the extended stored procedure uses the bind token with **sp_bindsession** to bind the new session to the same transaction.</span></span> <span data-ttu-id="58763-123">この拡張ストアド プロシージャは、複数のセッションを作成し、すべてのセッションを同じトランザクションにバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="58763-123">The extended stored procedure can create multiple sessions and bind all the sessions to the same transaction.</span></span>  
  
3.  <span data-ttu-id="58763-124">外部ストアド プロシージャが返されたり、**sp_bindsession** が空文字列で呼び出されたりすると、セッションのバインドが解除されます。</span><span class="sxs-lookup"><span data-stu-id="58763-124">A bound session is unbound when the external stored procedure returns or when **sp_bindsession** is called with an empty string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58763-125">共有の接続にアクセスできるバインドされたセッションは、一度に 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="58763-125">Only one bound session at a time can have access to a shared connection.</span></span> <span data-ttu-id="58763-126">あるセッションが現在サーバーでステートメントを実行しているかサーバーからの結果を待っている場合、バインドされた同じ接続を共有している他のセッションは、現在のセッションで現在のステートメントの実行が完了するまでサーバーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="58763-126">If one session is currently executing a statement at the server or has results pending from the server, no other sessions sharing the same bound connection can gain access to the server until the current session has finished executing the current statement.</span></span> <span data-ttu-id="58763-127">あるセッションが、サーバーがビジー状態のときに接続にアクセスを試みると、そのセッションは競合状態になりにエラーが返されます。その際、接続が使用中なので後でセッションを再試行する必要があることが示されます。</span><span class="sxs-lookup"><span data-stu-id="58763-127">If a session attempts to gain access to the connection while the server is busy, an error is returned to the conflicting session indicating the connection is in use and the session should retry later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="58763-128">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="58763-128">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="58763-129">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="58763-129">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58763-130">参照</span><span class="sxs-lookup"><span data-stu-id="58763-130">See Also</span></span>  
 <span data-ttu-id="58763-131">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58763-131">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 [<span data-ttu-id="58763-132">sp_getbindtoken &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="58763-132">sp_getbindtoken &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)  
  
  
