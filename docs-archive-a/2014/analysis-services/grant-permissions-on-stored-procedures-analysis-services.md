---
title: ストアドプロシージャに対する権限の許可 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13d75ca8b6ff6e7d482e9d69894091518aa9469e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634714"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a><span data-ttu-id="febb5-102">ストアド プロシージャに対する権限の付与 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="febb5-102">Grant permissions on stored procedures (Analysis Services)</span></span>
  <span data-ttu-id="febb5-103">のストアドプロシージャ (またはアセンブリ) [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、.net プログラミング言語で記述された外部ルーチンで [!INCLUDE[msCoName](../includes/msconame-md.md)] あり、の機能を拡張 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="febb5-103">Stored procedures, or assemblies, in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] are external routines, written in a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET programming language, that extend the capabilities of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="febb5-104">開発者は、アセンブリを使用して、言語間の統合、例外処理、バージョン管理サポート、デプロイサポート、デバッグサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="febb5-104">Assemblies let the developer take advantage of cross-language integration, exception handling, versioning support, deployment support, and debugging support.</span></span>  
  
 <span data-ttu-id="febb5-105">アセンブリを登録するには、サーバー管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="febb5-105">You must be a Server Administrator to register an assembly.</span></span> <span data-ttu-id="febb5-106">「 [&#41;Analysis Services &#40;サーバー管理者のアクセス許可を付与](instances/grant-server-admin-rights-to-an-analysis-services-instance.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="febb5-106">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
## <a name="security-context-for-stored-procedure-execution"></a><span data-ttu-id="febb5-107">ストアド プロシージャの実行のセキュリティ コンテキスト</span><span class="sxs-lookup"><span data-stu-id="febb5-107">Security context for stored procedure execution</span></span>  
 <span data-ttu-id="febb5-108">すべてのユーザーがストアド プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="febb5-108">Any user can call a stored procedure.</span></span> <span data-ttu-id="febb5-109">ストアド プロシージャは、その構成方法により、プロシージャを呼び出すユーザーのコンテキスト、または匿名ユーザーのコンテキストのいずれかで実行できます。</span><span class="sxs-lookup"><span data-stu-id="febb5-109">Depending on how the stored procedure was configured, the procedure can run either in the context of the user calling the procedure or in the context of an anonymous user.</span></span> <span data-ttu-id="febb5-110">匿名ユーザーにはセキュリティ コンテキストがないため、匿名アクセスを許可するには、この機能を [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスの構成と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="febb5-110">Because an anonymous user has no security context, use this capability together with configuring the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to permit anonymous access.</span></span>  
  
 <span data-ttu-id="febb5-111">ユーザーがストアド プロシージャを呼び出してから、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でストアド プロシージャが実行されるまでに、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、ストアド プロシージャ内のアクションが評価されます。</span><span class="sxs-lookup"><span data-stu-id="febb5-111">After the user calls a stored procedure but before [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] runs the stored procedure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] evaluates the actions within the stored procedure.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="febb5-112">は、ユーザーに与えられた権限と、プロシージャの実行に使用される権限セットの共通部分に基づき、ストアド プロシージャ内のアクションを評価します。</span><span class="sxs-lookup"><span data-stu-id="febb5-112">evaluates the actions in a stored procedure based on the intersection of the permissions granted to the user and the permission set used to run the procedure.</span></span> <span data-ttu-id="febb5-113">ストアド プロシージャに、ユーザーのデータベース ロールでは実行できないアクションある場合、そのアクションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="febb5-113">If the stored procedure contains any action that cannot be performed by the database role for the user, that action will not be performed.</span></span>  
  
 <span data-ttu-id="febb5-114">ストアド プロシージャの実行に使用する権限セットを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="febb5-114">Following are the permission sets that are used to run stored procedures:</span></span>  
  
-   <span data-ttu-id="febb5-115">**安全**安全な権限セットでは、ストアドプロシージャは .NET Framework 内の保護されたリソースにアクセスできません [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="febb5-115">**Safe** With the Safe permission set, a stored procedure cannot access the protected resources in the [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="febb5-116">この権限セットでは、計算のみが可能です。</span><span class="sxs-lookup"><span data-stu-id="febb5-116">This permission set only allows for computations.</span></span> <span data-ttu-id="febb5-117">これは最も安全な権限で、情報が [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の外に漏れることがないほか、権限が昇格される心配もなく、データ改ざんの攻撃のリスクを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="febb5-117">This is the safest permission set; information does not leak outside [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], permissions cannot be elevated, and the risk of data tampering attacks is minimized.</span></span>  
  
-   <span data-ttu-id="febb5-118">**外部アクセス**外部アクセス権限が設定されている場合、ストアドプロシージャはマネージコードを使用して外部リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="febb5-118">**External Access** With the External Access permission set, a stored procedure can access external resources by using managed code.</span></span> <span data-ttu-id="febb5-119">ストアド プロシージャをこの権限セットに設定すると、サーバー不安定の原因となるプログラミング エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="febb5-119">Setting a stored procedure to this permission set will not cause programming errors that could lead to server instability.</span></span> <span data-ttu-id="febb5-120">ただし、この権限セットは、情報がサーバーの外に漏れる結果をもたらす場合があり、権限の昇格や、データ改ざんの攻撃の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="febb5-120">However, this permission set may result in information leaking outside the server, and the possibility of an elevation in permission and data tampering attacks.</span></span>  
  
-   <span data-ttu-id="febb5-121">**無制限**無制限の権限セットを使用すると、ストアドプロシージャは任意のコードを使用して外部リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="febb5-121">**Unrestricted** With the Unrestricted permission set, a stored procedure can access external resources by using any code.</span></span> <span data-ttu-id="febb5-122">この権限セットが指定されている場合、ストアド プロシージャに対してセキュリティも信頼性も保証されません。</span><span class="sxs-lookup"><span data-stu-id="febb5-122">With this permission set, there are no security or reliability guarantees for stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febb5-123">参照</span><span class="sxs-lookup"><span data-stu-id="febb5-123">See Also</span></span>  
 [<span data-ttu-id="febb5-124">多次元モデルのアセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="febb5-124">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
