---
title: ポリシー ベースの管理を使用したサーバーの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- facet See facets
- Declarative Management Framework See Policy-Based Management
- surface area configuration [SQL Server], Policy-Based Management
- Policy-Based Management
- facets [Policy-Based Management]
- Policy-Based Management, administering
- conditions [Policy-Based Management]
- facets [Policy-Based Management], about facets
- PolicyAdministratorRole role
ms.assetid: ef2a7b3b-614b-405d-a04a-2464a019df40
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c0f415ffbc10b93cee2037da78daef3b7ee5aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714209"
---
# <a name="administer-servers-by-using-policy-based-management"></a><span data-ttu-id="0e852-102">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="0e852-102">Administer Servers by Using Policy-Based Management</span></span>
  <span data-ttu-id="0e852-103">ポリシー ベースの管理とは、1 つ以上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを管理するためのシステムのことです。</span><span class="sxs-lookup"><span data-stu-id="0e852-103">Policy-Based Management is a system for managing one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0e852-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ポリシー管理者は、ポリシー ベースの管理を使用する際、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してサーバー上のエンティティ ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス、データベース、その他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトなど) を管理するためのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e852-104">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] policy administrators use Policy-Based Management, they use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create policies to manage entities on the server, such as the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], databases, or other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span>  
  
## <a name="benefits-of-policy-based-management"></a><span data-ttu-id="0e852-105">ポリシー ベースの管理の利点</span><span class="sxs-lookup"><span data-stu-id="0e852-105">Benefits of Policy-Based Management</span></span>  
 <span data-ttu-id="0e852-106">ポリシー ベースの管理は、次のシナリオに示すような問題の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0e852-106">Policy-Based Management is helpful in resolving the issues presented in the following scenarios:</span></span>  
  
-   <span data-ttu-id="0e852-107">会社のポリシーで、データベース メールまたは SQL Mail の有効化が禁止されています。</span><span class="sxs-lookup"><span data-stu-id="0e852-107">A company policy prohibits enabling Database Mail or SQL Mail.</span></span> <span data-ttu-id="0e852-108">これら 2 つの機能のサーバー状態を確認するポリシーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-108">A policy is created to check the server state of those two features.</span></span> <span data-ttu-id="0e852-109">管理者がサーバー状態をポリシーと比較します。</span><span class="sxs-lookup"><span data-stu-id="0e852-109">An administrator compares the server state to the policy.</span></span> <span data-ttu-id="0e852-110">サーバー状態が準拠していない場合、管理者が構成モードを選択すると、ポリシーによりサーバー状態が準拠するようになります。</span><span class="sxs-lookup"><span data-stu-id="0e852-110">If the server state is out of compliance, the administrator chooses the Configure mode and the policy brings the server state into compliance.</span></span>  
  
-   <span data-ttu-id="0e852-111">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに、すべてのストアド プロシージャが文字列 AW_ で始まることを必須とする名前付け規則があります。</span><span class="sxs-lookup"><span data-stu-id="0e852-111">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database has a naming convention that requires all stored procedures to start with the letters AW_.</span></span> <span data-ttu-id="0e852-112">このポリシーを適用するポリシーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-112">A policy is created to enforce this policy.</span></span> <span data-ttu-id="0e852-113">管理者がこのポリシーをテストし、準拠していないストアド プロシージャの一覧を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0e852-113">An administrator tests this policy and receives a list of stored procedures that are out of compliance.</span></span> <span data-ttu-id="0e852-114">今後、ストアド プロシージャがこの名前付け規則に準拠しない場合、そのストアド プロシージャの作成ステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="0e852-114">If future stored procedures do not comply with this naming convention, the creation statements for the stored procedures fail.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e852-115">ポリシーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部の機能の動作に影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="0e852-115">Be aware that policies can affect how some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features work.</span></span> <span data-ttu-id="0e852-116">たとえば、変更データ キャプチャとトランザクション レプリケーションでは、インデックスがない systranschemas テーブルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-116">For example, change data capture and transactional replication both use the systranschemas table, which does not have an index.</span></span> <span data-ttu-id="0e852-117">すべてのテーブルにインデックスが必要であるというポリシーを有効にして、このポリシーへの準拠を適用した場合、これらの機能が失敗します。</span><span class="sxs-lookup"><span data-stu-id="0e852-117">If you enable a policy that all tables must have an index, enforcing compliance of the policy will cause these features to fail.</span></span>  
  
 <span data-ttu-id="0e852-118">ポリシーの作成と管理は、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="0e852-118">Policies are created and managed by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="0e852-119">処理の手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0e852-119">The process includes the following steps:</span></span>  
  
1.  <span data-ttu-id="0e852-120">構成するプロパティを含むポリシー ベースの管理ファセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="0e852-120">Select a Policy-Based Management facet that contains the properties to be configured.</span></span>  
  
2.  <span data-ttu-id="0e852-121">管理ファセットの状態を指定する条件を定義します。</span><span class="sxs-lookup"><span data-stu-id="0e852-121">Define a condition that specifies the state of a management facet.</span></span>  
  
3.  <span data-ttu-id="0e852-122">条件、対象セットをフィルター処理する追加条件、および評価モードを示すポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="0e852-122">Define a policy that contains the condition, additional conditions that filter the target sets, and the evaluation mode.</span></span>  
  
4.  <span data-ttu-id="0e852-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがポリシーに準拠しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0e852-123">Check whether an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is in compliance with the policy.</span></span>  
  
 <span data-ttu-id="0e852-124">ポリシーに違反する場合は、オブジェクト エクスプローラーで、対象およびオブジェクト エクスプローラー ツリーの上位にあるノードの横に、重大な状態の警告が赤いアイコンとして示されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-124">For failed policies, Object Explorer indicates a critical health warning as a red icon next to the target and the nodes that are higher in the Object Explorer tree.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e852-125">ポリシーのオブジェクト セットをシステムが計算する際、既定ではシステム オブジェクトが除外されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-125">When the system computes the object set for a policy, by default the system objects are excluded.</span></span>  <span data-ttu-id="0e852-126">たとえば、ポリシーのオブジェクト セットがすべてのテーブルを参照する場合、システム テーブルにはそのポリシーが適用されません。</span><span class="sxs-lookup"><span data-stu-id="0e852-126">For example, if the object set of the policy refers to all tables, the policy will not apply to system tables.</span></span> <span data-ttu-id="0e852-127">システム オブジェクトに対してポリシーを評価する必要がある場合は、ユーザーが、それらのオブジェクト セットに対し、システム オブジェクトを明示的に追加できます。</span><span class="sxs-lookup"><span data-stu-id="0e852-127">If users want to evaluate a policy against system objects, they can explicitly add system objects to the object set.</span></span> <span data-ttu-id="0e852-128">**"スケジュールに基づいて確認"** の評価モードではすべてのポリシーがサポートされますが、パフォーマンス上の理由により、 **"変更時に確認"** の評価モードでは、任意のオブジェクト セットを含んだポリシーは、必ずしもすべてサポートされるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="0e852-128">However, though all policies are supported for **check on schedule** evaluation mode, for performance reason, not all policies with arbitrary object sets are supported for **check on change** evaluation mode.</span></span> <span data-ttu-id="0e852-129">詳細については、「」を参照してください。[https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span><span class="sxs-lookup"><span data-stu-id="0e852-129">For more information, see [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span></span>  
  
## <a name="policy-based-management-concepts"></a><span data-ttu-id="0e852-130">ポリシー ベースの管理の概念</span><span class="sxs-lookup"><span data-stu-id="0e852-130">Policy-Based Management Concepts</span></span>  
 <span data-ttu-id="0e852-131">ポリシー ベースの管理は 3 つの要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-131">Policy-Based Management has three components:</span></span>  
  
-   <span data-ttu-id="0e852-132">ポリシー管理</span><span class="sxs-lookup"><span data-stu-id="0e852-132">Policy management</span></span>  
  
     <span data-ttu-id="0e852-133">ポリシー管理者がポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e852-133">Policy administrators create policies.</span></span>  
  
-   <span data-ttu-id="0e852-134">明示的な管理</span><span class="sxs-lookup"><span data-stu-id="0e852-134">Explicit administration</span></span>  
  
     <span data-ttu-id="0e852-135">管理者が 1 つ以上の管理対象を選択し、対象が特定のポリシーに準拠しているかどうかを明示的に確認するか、対象をポリシーに明示的に準拠させます。</span><span class="sxs-lookup"><span data-stu-id="0e852-135">Administrators select one or more managed targets and explicitly check that the targets comply with a specific policy, or explicitly make the targets comply with a policy.</span></span>  
  
-   <span data-ttu-id="0e852-136">評価モード</span><span class="sxs-lookup"><span data-stu-id="0e852-136">Evaluation modes</span></span>  
  
     <span data-ttu-id="0e852-137">実行モードには次の 4 種類があり、そのうち 3 つは自動化できます。</span><span class="sxs-lookup"><span data-stu-id="0e852-137">There are four evaluation modes, three of which can be automated:</span></span>  
  
    -   <span data-ttu-id="0e852-138">**オンデマンド**。</span><span class="sxs-lookup"><span data-stu-id="0e852-138">**On demand**.</span></span> <span data-ttu-id="0e852-139">このモードでは、ユーザーが直接指定した場合にポリシーが評価されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-139">This mode evaluates the policy when directly specified by the user.</span></span>  
  
    -   <span data-ttu-id="0e852-140">**変更時: 回避**します。</span><span class="sxs-lookup"><span data-stu-id="0e852-140">**On change: prevent**.</span></span> <span data-ttu-id="0e852-141">この自動モードでは、DDL トリガーを使用してポリシー違反が防止されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-141">This automated mode uses DDL triggers to prevent policy violations.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="0e852-142">nested triggers サーバー構成オプションが無効になっている場合、 **[変更時: 回避]** は正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="0e852-142">If the nested triggers server configuration option is disabled, **On change: prevent** will not work correctly.</span></span> <span data-ttu-id="0e852-143">ポリシー ベースの管理では、この評価モードを使用するポリシーに準拠しない DDL 操作の検出およびロールバックに DDL トリガーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-143">Policy-Based Management relies on DDL triggers to detect and roll back DDL operations that do not comply with policies that use this evaluation mode.</span></span> <span data-ttu-id="0e852-144">ポリシー ベースの管理の DDL トリガーを削除するか、nested triggers を無効にすると、この評価モードが失敗したり、予期しない動作をすることがあります。</span><span class="sxs-lookup"><span data-stu-id="0e852-144">Removing the Policy-Based Management DDL triggers or disabling nest triggers, will cause this evaluation mode to fail or perform unexpectedly.</span></span>  
  
    -   <span data-ttu-id="0e852-145">**変更時: ログのみ**。</span><span class="sxs-lookup"><span data-stu-id="0e852-145">**On change: log only**.</span></span> <span data-ttu-id="0e852-146">この自動モードでは、関連する変更が行われたときにイベント通知を使用してポリシーが評価されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-146">This automated mode uses event notification to evaluate a policy when a relevant change is made.</span></span>  
  
    -   <span data-ttu-id="0e852-147">**[スケジュールで**実行する。</span><span class="sxs-lookup"><span data-stu-id="0e852-147">**On schedule**.</span></span> <span data-ttu-id="0e852-148">この自動モードでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを使用してポリシーが定期的に評価されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-148">This automated mode uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to periodically evaluate a policy.</span></span>  
  
     <span data-ttu-id="0e852-149">自動ポリシーが有効になっていない場合、ポリシー ベースの管理はシステム パフォーマンスに影響しません。</span><span class="sxs-lookup"><span data-stu-id="0e852-149">When automated policies are not enabled, Policy-Based Management will not affect system performance.</span></span>  
  
## <a name="policy-based-management-terms"></a><span data-ttu-id="0e852-150">ポリシー ベースの管理の用語</span><span class="sxs-lookup"><span data-stu-id="0e852-150">Policy-Based Management Terms</span></span>  
 <span data-ttu-id="0e852-151">ポリシー ベースの管理の管理対象</span><span class="sxs-lookup"><span data-stu-id="0e852-151">Policy-Based Management managed target</span></span>  
 <span data-ttu-id="0e852-152">ポリシー ベースの管理で管理する [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] インスタンス、データベース、テーブル、インデックスなどのエンティティ。</span><span class="sxs-lookup"><span data-stu-id="0e852-152">Entities that are managed by Policy-Based Management, such as an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], a database, a table, or an index.</span></span> <span data-ttu-id="0e852-153">サーバー インスタンス内のすべての対象で、対象となる階層が構成されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-153">All targets in a server instance form a target hierarchy.</span></span> <span data-ttu-id="0e852-154">対象セットは、対象となる階層に一連の対象フィルターを適用した結果得られる一連の対象です (HumanResources スキーマが所有するデータベース内のすべてのテーブルなど)。</span><span class="sxs-lookup"><span data-stu-id="0e852-154">A target set is the set of targets that results from applying a set of target filters to the target hierarchy, for example, all the tables in the database owned by the HumanResources schema.</span></span>  
  
 <span data-ttu-id="0e852-155">ポリシー ベースの管理ファセット</span><span class="sxs-lookup"><span data-stu-id="0e852-155">Policy-Based Management facet</span></span>  
 <span data-ttu-id="0e852-156">特定の種類の管理対象の動作または特性をモデル化した一連の論理プロパティ。</span><span class="sxs-lookup"><span data-stu-id="0e852-156">A set of logical properties that model the behavior or characteristics for certain types of managed targets.</span></span> <span data-ttu-id="0e852-157">プロパティの数と特性がファセットに組み込まれ、その追加や削除はファセットの作成者のみが実行できます。</span><span class="sxs-lookup"><span data-stu-id="0e852-157">The number and characteristics of the properties are built into the facet and can be added or removed by only the maker of the facet.</span></span> <span data-ttu-id="0e852-158">1 種類の対象で 1 つ以上の管理ファセットを実装したり、1 種類以上の対象で 1 つの管理ファセットを実装したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="0e852-158">A target type can implement one or more management facets, and a management facet can be implemented by one or more target types.</span></span> <span data-ttu-id="0e852-159">ファセットのプロパティの中には、特定のバージョンにしか適用できないものもあります。</span><span class="sxs-lookup"><span data-stu-id="0e852-159">Some properties of a facet can only apply to a specific version..</span></span>  
  
 <span data-ttu-id="0e852-160">ポリシー ベースの管理条件</span><span class="sxs-lookup"><span data-stu-id="0e852-160">Policy-Based Management condition</span></span>  
 <span data-ttu-id="0e852-161">管理ファセットについて、ポリシー ベースの管理の管理対象の一連の許可状態を指定するブール式。</span><span class="sxs-lookup"><span data-stu-id="0e852-161">A Boolean expression that specifies a set of allowed states of a Policy-Based Management managed target with regard to a management facet.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0e852-162">は、条件の評価時に照合順序に従おうとします。</span><span class="sxs-lookup"><span data-stu-id="0e852-162">tries to observe collations when evaluating a condition.</span></span> <span data-ttu-id="0e852-163">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の照合順序が Windows の照合順序と一致しないときは、条件をテストして、アルゴリズムによる競合の解決方法を調べてください。</span><span class="sxs-lookup"><span data-stu-id="0e852-163">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations do not exactly match Windows collations, test your condition to determine how the algorithm resolves conflicts.</span></span>  
  
 <span data-ttu-id="0e852-164">ポリシー ベースの管理ポリシー</span><span class="sxs-lookup"><span data-stu-id="0e852-164">Policy-Based Management policy</span></span>  
 <span data-ttu-id="0e852-165">ポリシー ベースの管理条件と、評価モード、対象フィルター、スケジュールなどの想定される動作。</span><span class="sxs-lookup"><span data-stu-id="0e852-165">A Policy-Based Management condition and the expected behavior, for example, evaluation mode, target filters, and schedule.</span></span> <span data-ttu-id="0e852-166">1 つのポリシーには 1 つの条件しか含めることができません。</span><span class="sxs-lookup"><span data-stu-id="0e852-166">A policy can contain only one condition.</span></span> <span data-ttu-id="0e852-167">ポリシーは有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="0e852-167">Policies can be enabled or disabled.</span></span> <span data-ttu-id="0e852-168">ポリシーは msdb データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-168">Policies are stored in the msdb database.</span></span>  
  
 <span data-ttu-id="0e852-169">ポリシー ベースの管理のポリシー カテゴリ</span><span class="sxs-lookup"><span data-stu-id="0e852-169">Policy-Based Management policy category</span></span>  
 <span data-ttu-id="0e852-170">ポリシーの管理に役立つユーザー定義のカテゴリ。</span><span class="sxs-lookup"><span data-stu-id="0e852-170">A user-defined category to help manage policies.</span></span> <span data-ttu-id="0e852-171">ユーザーは、ポリシーをさまざまなポリシー カテゴリに分類できます。</span><span class="sxs-lookup"><span data-stu-id="0e852-171">Users can classify policies into different policy categories.</span></span> <span data-ttu-id="0e852-172">ポリシーは 1 つのポリシー カテゴリだけに属します。</span><span class="sxs-lookup"><span data-stu-id="0e852-172">A policy belongs to one and only one policy category.</span></span> <span data-ttu-id="0e852-173">ポリシー カテゴリはデータベースとサーバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-173">Policy categories apply to databases and servers.</span></span> <span data-ttu-id="0e852-174">データベース レベルでは、次の条件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="0e852-174">At the database level, the following conditions apply:</span></span>  
  
-   <span data-ttu-id="0e852-175">データベース所有者は、データベースを一連のポリシー カテゴリにサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="0e852-175">Database owners can subscribe a database to a set of policy categories.</span></span>  
  
-   <span data-ttu-id="0e852-176">そのサブスクライブ先のカテゴリのポリシーのみがデータベースを制御できます。</span><span class="sxs-lookup"><span data-stu-id="0e852-176">Only policies from its subscribed categories can govern a database.</span></span>  
  
-   <span data-ttu-id="0e852-177">データベースはすべて、既定のポリシー カテゴリに暗黙的にサブスクライブしています。</span><span class="sxs-lookup"><span data-stu-id="0e852-177">All databases implicitly subscribe to the default policy category.</span></span>  
  
 <span data-ttu-id="0e852-178">サーバー レベルでは、すべてのデータベースにポリシー カテゴリを適用できます。</span><span class="sxs-lookup"><span data-stu-id="0e852-178">At the server level, policy categories can be applied to all databases.</span></span>  
  
 <span data-ttu-id="0e852-179">有効なポリシー</span><span class="sxs-lookup"><span data-stu-id="0e852-179">Effective policy</span></span>  
 <span data-ttu-id="0e852-180">対象の有効なポリシーとは、この対象を制御するポリシーのことです。</span><span class="sxs-lookup"><span data-stu-id="0e852-180">The effective policies of a target are those policies that govern this target.</span></span> <span data-ttu-id="0e852-181">ポリシーは、次のすべての条件を満たす場合にのみ対象について有効になります。</span><span class="sxs-lookup"><span data-stu-id="0e852-181">A policy is effective with regard to a target only if all the following conditions are satisfied:</span></span>  
  
-   <span data-ttu-id="0e852-182">ポリシーが有効になっている。</span><span class="sxs-lookup"><span data-stu-id="0e852-182">The policy is enabled.</span></span>  
  
-   <span data-ttu-id="0e852-183">対象がポリシーの対象セットに属している。</span><span class="sxs-lookup"><span data-stu-id="0e852-183">The target belongs to the target set of the policy.</span></span>  
  
-   <span data-ttu-id="0e852-184">対象または対象のいずれかの先祖がこのポリシーを含んでいるポリシー グループにサブスクライブしている。</span><span class="sxs-lookup"><span data-stu-id="0e852-184">The target or one of the targets ancestors subscribes to the policy group that contains this policy.</span></span>  
  
## <a name="policy-based-management-tasks"></a><span data-ttu-id="0e852-185">ポリシー ベースの管理のタスク</span><span class="sxs-lookup"><span data-stu-id="0e852-185">Policy-Based Management Tasks</span></span>  
 <span data-ttu-id="0e852-186">ポリシー ベースの管理とは、1 つ以上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを管理するためのポリシー ベースのシステムのことです。</span><span class="sxs-lookup"><span data-stu-id="0e852-186">Policy-Based Management is a policy based system for managing one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0e852-187">ポリシー ベースの管理を使用して、条件式を含む条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="0e852-187">Use Policy-Based Management to create conditions that contain condition expressions.</span></span> <span data-ttu-id="0e852-188">次に、作成した条件を対象のデータベース オブジェクトに適用するポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e852-188">Then, create policies that apply the conditions to database target objects.</span></span>  
  
|<span data-ttu-id="0e852-189">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="0e852-189">Task Description</span></span>|<span data-ttu-id="0e852-190">トピック</span><span class="sxs-lookup"><span data-stu-id="0e852-190">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0e852-191">ポリシー ベースの管理ポリシーの格納方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-191">Describes how Policy-Based Management policies are stored.</span></span>|<span data-ttu-id="0e852-192">ポリシー ベースの管理のストレージ</span><span class="sxs-lookup"><span data-stu-id="0e852-192">Policy-Based Management Storage</span></span>|  
|<span data-ttu-id="0e852-193">ポリシー管理者にポリシー エラーを通知する警告の構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-193">Describes how to configure alerts to notify policy administrators of policy failures.</span></span>|[<span data-ttu-id="0e852-194">ポリシー管理者にポリシー エラーを通知する警告の構成</span><span class="sxs-lookup"><span data-stu-id="0e852-194">Configure Alerts to Notify Policy Administrators of Policy Failures</span></span>](configure-alerts-to-notify-policy-administrators-of-policy-failures.md)|  
|<span data-ttu-id="0e852-195">ポリシー ベースの管理条件を作成、表示、変更、および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-195">Describes how to create, view, modify, and delete a Policy-based Management condition.</span></span>|[<span data-ttu-id="0e852-196">新しいポリシー ベースの管理条件の作成</span><span class="sxs-lookup"><span data-stu-id="0e852-196">Create a New Policy-Based Management Condition</span></span>](create-a-new-policy-based-management-condition.md)<br /><br /> [<span data-ttu-id="0e852-197">ポリシー ベースの管理条件の削除</span><span class="sxs-lookup"><span data-stu-id="0e852-197">Delete a Policy-Based Management Condition</span></span>](delete-a-policy-based-management-condition.md)<br /><br /> [<span data-ttu-id="0e852-198">ポリシー ベースの管理条件のプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="0e852-198">View or Modify the Properties of a Policy-Based Management Condition</span></span>](view-or-modify-the-properties-of-a-policy-based-management-condition.md)|  
|<span data-ttu-id="0e852-199">ポリシー ベースの管理ポリシーを作成、表示、変更、および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-199">Describes how to create, view, modify, and delete a Policy-Based Management policy.</span></span>|[<span data-ttu-id="0e852-200">ポリシー ベースの管理ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="0e852-200">Create a Policy-Based Management Policy</span></span>](create-a-policy-based-management-policy.md)<br /><br /> [<span data-ttu-id="0e852-201">ポリシー ベースの管理ポリシーの削除</span><span class="sxs-lookup"><span data-stu-id="0e852-201">Delete a Policy-Based Management Policy</span></span>](delete-a-policy-based-management-policy.md)<br /><br /> [<span data-ttu-id="0e852-202">ポリシー ベースの管理ポリシーのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="0e852-202">View or Modify the Properties of a Policy-Based Management Policy</span></span>](view-or-modify-the-properties-of-a-policy-based-management-policy.md)|  
|<span data-ttu-id="0e852-203">ポリシー ベースの管理ポリシーをエクスポートおよびインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-203">Describes how to export and import a Policy-based Management policy.</span></span>|[<span data-ttu-id="0e852-204">ポリシー ベースの管理ポリシーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="0e852-204">Export a Policy-Based Management Policy</span></span>](export-a-policy-based-management-policy.md)<br /><br /> [<span data-ttu-id="0e852-205">ポリシー ベースの管理ポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="0e852-205">Import a Policy-Based Management Policy</span></span>](import-a-policy-based-management-policy.md)|  
|<span data-ttu-id="0e852-206">サーバー インスタンス、データベース、サーバー オブジェクト、またはデータベース オブジェクトがポリシーに準拠していることを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-206">Describes how to verify that a server instance, database, server object, or database object complies with a policy.</span></span>|[<span data-ttu-id="0e852-207">オブジェクトからのポリシー ベースの管理ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="0e852-207">Evaluate a Policy-Based Management Policy from an Object</span></span>](evaluate-a-policy-based-management-policy-from-an-object.md)<br /><br /> [<span data-ttu-id="0e852-208">ポリシーからのポリシー ベースの管理ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="0e852-208">Evaluate a Policy-Based Management Policy from That Policy</span></span>](evaluate-a-policy-based-management-policy-from-that-policy.md)<br /><br /> [<span data-ttu-id="0e852-209">ポリシー ベースの管理ポリシーがスケジュールに従っていることの評価</span><span class="sxs-lookup"><span data-stu-id="0e852-209">Evaluate a Policy-Based Management Policy on a Schedule</span></span>](evaluate-a-policy-based-management-policy-on-a-schedule.md)|  
|<span data-ttu-id="0e852-210">ポリシー ベースの管理ファセットの状態を表示してファイルにコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-210">Describes how to view and copy a Policy-based Management facet state to a file.</span></span>|[<span data-ttu-id="0e852-211">ポリシー ベースの管理ファセットの操作</span><span class="sxs-lookup"><span data-stu-id="0e852-211">Working with Policy-Based Management Facets</span></span>](working-with-policy-based-management-facets.md)|  
|<span data-ttu-id="0e852-212">ベスト プラクティス ポリシーとしてインポートできる一連のポリシー ファイルを提供し、インスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを含む対象セットに対してポリシーを評価する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e852-212">Provides a set of policy files that you can import as best practice policies, and describes how to evaluate the policies against a target set that includes instances, instance objects, databases, or database objects.</span></span>|[<span data-ttu-id="0e852-213">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="0e852-213">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)|  
|<span data-ttu-id="0e852-214">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーの **[ポリシー管理]** ノードに関する F1 ヘルプ トピックを提供します。</span><span class="sxs-lookup"><span data-stu-id="0e852-214">Provides the F1 Help topics for the **PolicyManagement** node of Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|<span data-ttu-id="0e852-215">[[ポリシー管理] ノード &#40;オブジェクト エクスプローラー&#41;](../../ssms/object/object-explorer.md)</span><span class="sxs-lookup"><span data-stu-id="0e852-215">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e852-216">参照</span><span class="sxs-lookup"><span data-stu-id="0e852-216">See Also</span></span>  
 [<span data-ttu-id="0e852-217">ポリシーベースの管理ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e852-217">Policy-Based Management Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/policy-based-management-views-transact-sql)  
  
  