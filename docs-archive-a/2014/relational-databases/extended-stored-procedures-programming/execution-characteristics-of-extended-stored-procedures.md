---
title: 拡張ストアドプロシージャの実行特性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
ms.openlocfilehash: edbd73797699d65f694e91bc3035e0dc9366c9d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632481"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a><span data-ttu-id="b2e4a-102">拡張ストアド プロシージャの実行における特性</span><span class="sxs-lookup"><span data-stu-id="b2e4a-102">Execution Characteristics of Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="b2e4a-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="b2e4a-104">拡張ストアド プロシージャの実行には次の 3 つの特性があります。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-104">The execution of an extended stored procedure has these characteristics:</span></span>  
  
-   <span data-ttu-id="b2e4a-105">拡張ストアドプロシージャ関数は、のセキュリティコンテキストで実行され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-105">The extended stored procedure function is executed under the security context of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b2e4a-106">拡張ストアド プロシージャ関数は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の処理領域で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-106">The extended stored procedure function runs in the process space of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b2e4a-107">拡張ストアド プロシージャの実行に関連付けられているスレッドは、クライアント接続に使用するスレッドと同じです。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-107">The thread associated with the execution of the extended stored procedure is the same one used for the client connection.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b2e4a-108">システム管理者は、拡張ストアド プロシージャをサーバーに追加し、他のユーザーに実行権限を許可する前に、各拡張ストアド プロシージャに有害なコードや悪意のあるコードが含まれていないことを十分に確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-108">Before adding extended stored procedures to the server and granting execute permissions to other users, the system administrator should thoroughly review each extended stored procedure to make sure that it does not contain harmful or malicious code.</span></span>  
  
-  
  
 <span data-ttu-id="b2e4a-109">拡張ストアドプロシージャ DLL が読み込まれると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が停止するか、管理者が DBCC *DLL_name* (FREE) を使用して dll を明示的にアンロードするまで、dll はサーバーのアドレス空間に読み込まれたままになります。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-109">After the extended stored procedure DLL is loaded, the DLL remains loaded in the address space of the server until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is stopped or the administrator explicitly unloads the DLL by using DBCC *DLL_name* (FREE).</span></span>  
  
 <span data-ttu-id="b2e4a-110">EXECUTE ステートメントを使用すると、拡張ストアド プロシージャをストアド プロシージャとして [!INCLUDE[tsql](../../includes/tsql-md.md)] から実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-110">The extended stored procedure can be executed from [!INCLUDE[tsql](../../includes/tsql-md.md)] as a stored procedure by using the EXECUTE statement:</span></span>  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2e4a-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2e4a-111">Parameters</span></span>  
 <span data-ttu-id="b2e4a-112">\@ *retval*</span><span class="sxs-lookup"><span data-stu-id="b2e4a-112">\@ *retval*</span></span>  
 <span data-ttu-id="b2e4a-113">戻り値です。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-113">Is a return value.</span></span>  
  
 <span data-ttu-id="b2e4a-114">\@*param1*</span><span class="sxs-lookup"><span data-stu-id="b2e4a-114">\@ *param1*</span></span>  
 <span data-ttu-id="b2e4a-115">入力パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-115">Is an input parameter.</span></span>  
  
 <span data-ttu-id="b2e4a-116">\@*param2*</span><span class="sxs-lookup"><span data-stu-id="b2e4a-116">\@ *param2*</span></span>  
 <span data-ttu-id="b2e4a-117">入力/出力パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-117">Is an input/output parameter.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b2e4a-118">拡張ストアド プロシージャを使用すると、パフォーマンスの向上や、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能強化を図ることができます。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-118">Extended stored procedures offer performance enhancements and extend [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="b2e4a-119">ただし、拡張ストアド プロシージャ DLL と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は同じアドレス領域を共有するため、問題のあるプロシージャにより [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能が影響を受けることがあります。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-119">However, because the extended stored procedure DLL and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] share the same address space, a problem procedure can adversely affect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functioning.</span></span> <span data-ttu-id="b2e4a-120">拡張ストアド プロシージャ DLL によってスローされる例外は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で処理されますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ領域に損傷を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-120">Although exceptions thrown by the extended stored procedure DLL are handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible to damage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data areas.</span></span> <span data-ttu-id="b2e4a-121">セキュリティ措置として、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に拡張ストアド プロシージャを組み込むことができるのは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者だけに限定されています。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-121">As a security precaution, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrators can add extended stored procedures to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b2e4a-122">これらのプロシージャは詳細にテストしてからインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2e4a-122">These procedures should be thoroughly tested before they are installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e4a-123">参照</span><span class="sxs-lookup"><span data-stu-id="b2e4a-123">See Also</span></span>  
 <span data-ttu-id="b2e4a-124">[拡張ストアドプロシージャのプログラミング](database-engine-extended-stored-procedures-programming.md) </span><span class="sxs-lookup"><span data-stu-id="b2e4a-124">[Programming Extended Stored Procedures](database-engine-extended-stored-procedures-programming.md) </span></span>  
 [<span data-ttu-id="b2e4a-125">SQL Server にインストールされた拡張ストアド プロシージャの照会</span><span class="sxs-lookup"><span data-stu-id="b2e4a-125">Querying Extended Stored Procedures Installed in SQL Server</span></span>](querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
