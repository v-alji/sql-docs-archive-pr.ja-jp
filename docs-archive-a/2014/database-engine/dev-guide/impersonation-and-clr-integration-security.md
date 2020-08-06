---
title: 権限借用と CLR 統合のセキュリティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2313733c5a24f28c44571dd230ddc58fc9a1264
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742502"
---
# <a name="impersonation-and-clr-integration-security"></a><span data-ttu-id="5f406-102">権限借用と CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="5f406-102">Impersonation and CLR Integration Security</span></span>
  <span data-ttu-id="5f406-103">マネージド コードが外部リソースにアクセスする際に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、そのルーチンを実行している現在の実行コンテキストの権限を自動的には借用しません。</span><span class="sxs-lookup"><span data-stu-id="5f406-103">When managed code accesses external resources, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not automatically impersonate the current execution context under which the routine is executing.</span></span> <span data-ttu-id="5f406-104">`EXTERNAL_ACCESS` および `UNSAFE` アセンブリのコードは、現在の実行コンテキストの権限を明示的に借用することができます。</span><span class="sxs-lookup"><span data-stu-id="5f406-104">Code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can explicitly impersonate the current execution context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f406-105">偽装の動作変更の詳細については、「 [SQL Server 2014 のデータベースエンジン機能における重大な変更](../breaking-changes-to-database-engine-features-in-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f406-105">For information on behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="5f406-106">インプロセス データ アクセス プロバイダーには、`SqlContext.WindowsIdentity` というアプリケーション プログラミング インターフェイスが用意されています。これを使用して、現在のセキュリティ コンテキストに関連付けられたトークンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="5f406-106">The in-process data access provider provides an application programming interface, `SqlContext.WindowsIdentity`, that can be used to retrieve the token associated with the current security context.</span></span> <span data-ttu-id="5f406-107">`EXTERNAL_ACCESS` アセンブリと `UNSAFE` アセンブリのマネージド コードでは、このメソッドを使用してコンテキストを取得し、.NET Framework `WindowsIdentity.Impersonate` メソッドを使用してそのコンテキストの権限を借用できます。</span><span class="sxs-lookup"><span data-stu-id="5f406-107">Managed code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can use this method to retrieve the context and use the .NET Framework `WindowsIdentity.Impersonate` method to impersonate that context.</span></span> <span data-ttu-id="5f406-108">ユーザー コードから明示的に権限を借用するときは、次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5f406-108">The following restrictions apply when user code explicitly impersonates:</span></span>  
  
-   <span data-ttu-id="5f406-109">マネージド コードが権限を借用している状態のときは、インプロセス データ アクセスは許可されません。</span><span class="sxs-lookup"><span data-stu-id="5f406-109">In-process data access is not allowed when managed code is in an impersonated state.</span></span> <span data-ttu-id="5f406-110">コードで、権限借用を元に戻してから、インプロセス データ アクセスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5f406-110">Code can undo impersonation and then call in-process data access.</span></span> <span data-ttu-id="5f406-111">このためには、元の `WindowsImpersonationContext` メソッドの戻り値 (`Impersonate` オブジェクト) を格納し、この `Undo` の `WindowsImpersonationContext` メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f406-111">Note that this requires storing the return value (a `WindowsImpersonationContext` object) of the original `Impersonate` method, and calling the `Undo` method on this `WindowsImpersonationContext`.</span></span>  
  
     <span data-ttu-id="5f406-112">つまり、インプロセス データ アクセスは、常に、セッションに対して有効な現在のセキュリティ コンテキストで行われます。</span><span class="sxs-lookup"><span data-stu-id="5f406-112">This restriction means that when in-process data access occurs, it is always in the context of the current security context in effect for the session.</span></span> <span data-ttu-id="5f406-113">マネージド コード内の明示的な権限借用によりこれを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="5f406-113">It cannot be modified by explicit impersonation within managed code.</span></span>  
  
-   <span data-ttu-id="5f406-114">(たとえば、スレッドを作成してコードを非同期に実行する `UNSAFE` アセンブリを経由するなどして) 非同期に実行されているマネージド コードの場合、インプロセス データ アクセスは一切許可されません。</span><span class="sxs-lookup"><span data-stu-id="5f406-114">For managed code executing asynchronously (for example, through `UNSAFE` assemblies creating threads and running code asynchronously), in-process data access is never allowed.</span></span> <span data-ttu-id="5f406-115">これは、権限借用の有無には関係ありません。</span><span class="sxs-lookup"><span data-stu-id="5f406-115">This is true whether or not there is impersonation.</span></span>  
  
 <span data-ttu-id="5f406-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とは異なる権限を借用したコンテキストでコードを実行している場合、インプロセス データ アクセスの呼び出しを行うことはできません。つまり、インプロセス データ アクセスの呼び出しを行う前に、権限借用のコンテキストを元に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f406-116">When code is running in an impersonated context that is different from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it cannot perform in-process data access calls; it should undo the impersonation context before making in-process data access calls.</span></span> <span data-ttu-id="5f406-117">マネージド コードからのインプロセス データ アクセスでは常に、マネージド コードへの [!INCLUDE[tsql](../../includes/tsql-md.md)] エントリ ポイントの本来の実行コンテキストが承認に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f406-117">When in-process data access is made from managed code, the original execution context of the [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point into the managed code is always used for authorization.</span></span>  
  
 <span data-ttu-id="5f406-118">既に説明したように、`EXTERNAL_ACCESS` アセンブリと `UNSAFE` アセンブリはどちらも、現在のセキュリティ コンテキストの権限を自主的に借用する場合以外は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントでオペレーティング システム リソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="5f406-118">Both `EXTERNAL_ACCESS` assemblies and `UNSAFE` assemblies access operating system resources with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account, unless they voluntarily impersonate the current security context as previously described.</span></span> <span data-ttu-id="5f406-119">このため、`EXTERNAL_ACCESS` アセンブリの作成者には、`SAFE` アセンブリの作成者よりも高いレベルの信頼度が必要です。この信頼度は、`EXTERNAL ACCESS` ログイン レベルの権限で指定されます。</span><span class="sxs-lookup"><span data-stu-id="5f406-119">Because of this, the authors of `EXTERNAL_ACCESS` assemblies require a higher level of trust than those of `SAFE` assemblies, which is specified by the `EXTERNAL ACCESS` login-level permission.</span></span> <span data-ttu-id="5f406-120">`EXTERNAL ACCESS` 権限は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントでコードを実行できるログインのみに許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f406-120">Only logins who are trusted to run code under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account should be granted the `EXTERNAL ACCESS` permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f406-121">参照</span><span class="sxs-lookup"><span data-stu-id="5f406-121">See Also</span></span>  
 <span data-ttu-id="5f406-122">[CLR 統合のセキュリティ](../../relational-databases/clr-integration/security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="5f406-122">[CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="5f406-123">接続の権限借用と資格情報</span><span class="sxs-lookup"><span data-stu-id="5f406-123">Impersonation and Credentials for Connections</span></span>](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  
