---
title: srv_pfieldex (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: a474eafcb6b6d42161a7e67ce7f93636269c46c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633849"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a><span data-ttu-id="adca1-102">srv_pfieldex (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="adca1-102">srv_pfieldex (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="adca1-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="adca1-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="adca1-104">要求された SRV_PROC フィールドを格納したデータへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="adca1-104">Returns a pointer to data containing the requested SRV_PROC field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adca1-105">構文</span><span class="sxs-lookup"><span data-stu-id="adca1-105">Syntax</span></span>  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="adca1-106">引数</span><span class="sxs-lookup"><span data-stu-id="adca1-106">Arguments</span></span>  
 <span data-ttu-id="adca1-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="adca1-107">*srvproc*</span></span>  
 <span data-ttu-id="adca1-108">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="adca1-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="adca1-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="adca1-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="adca1-110">*分野*</span><span class="sxs-lookup"><span data-stu-id="adca1-110">*field*</span></span>  
 <span data-ttu-id="adca1-111">返す *srvproc* フィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="adca1-111">Specifies the *srvproc* field to return.</span></span>  
  
|<span data-ttu-id="adca1-112">フィールド</span><span class="sxs-lookup"><span data-stu-id="adca1-112">Field</span></span>|<span data-ttu-id="adca1-113">説明</span><span class="sxs-lookup"><span data-stu-id="adca1-113">Description</span></span>|<span data-ttu-id="adca1-114">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="adca1-114">Return-type</span></span>|  
|-----------|-----------------|------------------|  
|<span data-ttu-id="adca1-115">SRV_MSGLCID</span><span class="sxs-lookup"><span data-stu-id="adca1-115">SRV_MSGLCID</span></span>|<span data-ttu-id="adca1-116">現在のセッションのメッセージ LCID。</span><span class="sxs-lookup"><span data-stu-id="adca1-116">Current session message LCID.</span></span>|<span data-ttu-id="adca1-117">ULONG\*</span><span class="sxs-lookup"><span data-stu-id="adca1-117">ULONG\*</span></span>|  
|<span data-ttu-id="adca1-118">SRV_INSTANCENAME</span><span class="sxs-lookup"><span data-stu-id="adca1-118">SRV_INSTANCENAME</span></span>|<span data-ttu-id="adca1-119">インスタンス名 (指定されている場合)。それ以外の場合は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="adca1-119">Instance name (if named); otherwise, returns NULL.</span></span>|<span data-ttu-id="adca1-120">WCHAR\*</span><span class="sxs-lookup"><span data-stu-id="adca1-120">WCHAR\*</span></span>|  
  
 <span data-ttu-id="adca1-121">*len*</span><span class="sxs-lookup"><span data-stu-id="adca1-121">*len*</span></span>  
 <span data-ttu-id="adca1-122">返される *field* 値の長さ (バイト単位) を格納した **int** 型変数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="adca1-122">Is a pointer to an **int** variable that contains the length of the returned *field* value in bytes.</span></span> <span data-ttu-id="adca1-123">*len* が NULL の場合、長さは返されていません。</span><span class="sxs-lookup"><span data-stu-id="adca1-123">If *len* is NULL, the length is not returned.</span></span> <span data-ttu-id="adca1-124">NULL が返されると、\**len* は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="adca1-124">When NULL is returned \**len* is set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="adca1-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="adca1-125">Returns</span></span>  
 <span data-ttu-id="adca1-126">*field* によってデータ型が決定されるデータを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="adca1-126">A pointer to data whose type depends on *field*.</span></span> <span data-ttu-id="adca1-127">*len* または *srvproc* が NULL の場合は NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="adca1-127">NULL is returned when *len* is NULL or *srvproc* is NULL.</span></span> <span data-ttu-id="adca1-128">*field* が不明の場合は NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="adca1-128">If the *field* is unknown, NULL is returned.</span></span> <span data-ttu-id="adca1-129">NULL が返されると、\**len* は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="adca1-129">When NULL is returned \**len* is set to 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="adca1-130">サーバーから返されるバッファーは読み取り専用にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="adca1-130">The buffer returned from the server should be read only.</span></span> <span data-ttu-id="adca1-131">そうでない場合、サーバーの状態が壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="adca1-131">Otherwise, the server state may be corrupted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adca1-132">解説</span><span class="sxs-lookup"><span data-stu-id="adca1-132">Remarks</span></span>  
 <span data-ttu-id="adca1-133">**セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="adca1-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="adca1-134">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="adca1-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
