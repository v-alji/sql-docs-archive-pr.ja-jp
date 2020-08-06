---
title: SQL Server 2014 | のマスターデータサービス廃止された機能Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 595b8bf9829ee57ff0d3bee1a82e527876ecc4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646181"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="a7579-102">SQL Server 2014 で提供が中止されたマスター データ サービス機能</span><span class="sxs-lookup"><span data-stu-id="a7579-102">Discontinued Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="a7579-103">このトピックでは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で使用できなくなった [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7579-103">This topic describes [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are no longer available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="sssql14-discontinued-features"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="a7579-104">提供が中止された機能</span><span class="sxs-lookup"><span data-stu-id="a7579-104">Discontinued Features</span></span>  
 <span data-ttu-id="a7579-105">今回のリリースで提供が中止された機能はありません。</span><span class="sxs-lookup"><span data-stu-id="a7579-105">There are no discontinued features in this release.</span></span>  
  
## <a name="sssql11-discontinued-features"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="a7579-106">提供が中止された機能</span><span class="sxs-lookup"><span data-stu-id="a7579-106">Discontinued Features</span></span>  
  
### <a name="security"></a><span data-ttu-id="a7579-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a7579-107">Security</span></span>  
 <span data-ttu-id="a7579-108">セキュリティの割り当てを簡単にするために、モデル オブジェクト権限を派生階層、明示的階層、および属性グループの各オブジェクトに割り当てることができなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-108">To make assigning security easier, you can no longer assign model object permissions to the Derived Hierarchy, Explicit Hierarchy, and Attribute Group objects.</span></span>  
  
-   <span data-ttu-id="a7579-109">派生階層権限は、モデルに基づくようになりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-109">Derived hierarchy permissions are now based on the model.</span></span> <span data-ttu-id="a7579-110">たとえば、派生階層に対する権限をユーザーに付与するには、モデルオブジェクトに**更新**を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7579-110">For example, if you want a user to have permission to a derived hierarchy, you must assign **Update** to the model object.</span></span> <span data-ttu-id="a7579-111">その後、ユーザーにアクセスを許可しないエンティティに対して、**拒否**アクセス権を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="a7579-111">Then you can assign **Deny** access to any entities you don't want the user to have access to.</span></span>  
  
-   <span data-ttu-id="a7579-112">明示的階層権限は、エンティティに基づくようになりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-112">Explicit hierarchy permissions are now based on the entity.</span></span> <span data-ttu-id="a7579-113">たとえば、ユーザーが Account エンティティに対する**更新**権限を持っている場合、そのエンティティのすべての明示的階層が更新可能になります。</span><span class="sxs-lookup"><span data-stu-id="a7579-113">For example, if the user has **Update** permissions to an Account entity, then all explicit hierarchies for the entity will be updateable.</span></span>  
  
-   <span data-ttu-id="a7579-114">[**ユーザー/グループの権限**] 機能領域では、属性グループの権限を割り当てることができなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-114">Attribute group permissions can no longer be assigned in the **User and Group Permissions** functional area.</span></span> <span data-ttu-id="a7579-115">代わりに、属性グループが作成される [**システム管理**] 機能領域で、ユーザーとグループに属性グループに対する**更新**権限を付与することができます。</span><span class="sxs-lookup"><span data-stu-id="a7579-115">Instead, in the **System Administration** functional area where attribute groups are created, users and groups can be given **Update** permission to attribute groups.</span></span> <span data-ttu-id="a7579-116">属性グループに対する**読み取り**専用権限は使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-116">**Read-only** permission to attribute groups is no longer available.</span></span>  
  
### <a name="staging-process"></a><span data-ttu-id="a7579-117">ステージング処理</span><span class="sxs-lookup"><span data-stu-id="a7579-117">Staging Process</span></span>  
 <span data-ttu-id="a7579-118">新しいステージング処理を使用して、次の操作を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7579-118">You cannot use the new staging process to:</span></span>  
  
-   <span data-ttu-id="a7579-119">コレクションの作成または削除。</span><span class="sxs-lookup"><span data-stu-id="a7579-119">Create or delete collections.</span></span>  
  
-   <span data-ttu-id="a7579-120">コレクションへのメンバーの追加またはコレクションからのメンバーの削除。</span><span class="sxs-lookup"><span data-stu-id="a7579-120">Add members to or remove members from collections.</span></span>  
  
-   <span data-ttu-id="a7579-121">メンバーまたはコレクションの再アクティブ化。</span><span class="sxs-lookup"><span data-stu-id="a7579-121">Reactivate members and collections.</span></span>  
  
 <span data-ttu-id="a7579-122">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] のステージング処理を使用して、コレクションを操作できます。</span><span class="sxs-lookup"><span data-stu-id="a7579-122">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process to work with collections.</span></span>  
  
### <a name="model-deployment-wizard"></a><span data-ttu-id="a7579-123">モデル配置ウィザード</span><span class="sxs-lookup"><span data-stu-id="a7579-123">Model Deployment Wizard</span></span>  
 <span data-ttu-id="a7579-124">データを含むパッケージは、ウィザードを使用して [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションに作成および配置することができなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-124">Packages that contain data can no longer be created and deployed by using the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="a7579-125">代わりに、新しいコマンド ライン ユーティリティを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a7579-125">A new command line utility can be used instead.</span></span> <span data-ttu-id="a7579-126">詳細については、「[モデルの配置 (マスター データ サービス)](deploying-models-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7579-126">For more information, see [Deploying Models &#40;Master Data Services&#41;](deploying-models-master-data-services.md).</span></span>  
  
 <span data-ttu-id="a7579-127">このウィザードは、データを含まないパッケージの作成および配置には引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7579-127">The wizard can still be used to create and deploy packages that do not contain data.</span></span>  
  
 <span data-ttu-id="a7579-128">また、パッケージは作成されたエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のみで展開できます。</span><span class="sxs-lookup"><span data-stu-id="a7579-128">In addition, packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="a7579-129">つまり、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で作成されたパッケージを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]に配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7579-129">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="a7579-130">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 環境にパッケージを展開してから、データベースを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] にアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7579-130">You must deploy the package to a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] environment and then upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="code-generation-business-rules"></a><span data-ttu-id="a7579-131">コード生成のビジネス ルール</span><span class="sxs-lookup"><span data-stu-id="a7579-131">Code Generation Business Rules</span></span>  
 <span data-ttu-id="a7579-132">Code 属性の値を自動的に生成するビジネス ルールを管理する方法が変わりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-132">Business rules that automatically generate values for the Code attribute are now administered differently.</span></span> <span data-ttu-id="a7579-133">以前は、Code 属性の値を生成するために、[**システム管理**] 機能領域の [**ビジネスルール**] の [生成された値] アクション**に既定の属性を**使用しました。</span><span class="sxs-lookup"><span data-stu-id="a7579-133">Previously, to generate values for the Code attribute, you used the **Default attribute to a generated value** action in the **System Administration** functional area under **Business Rules**.</span></span> <span data-ttu-id="a7579-134">ここで、**システム管理**で、エンティティを編集して、自動的に生成されたコード値を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7579-134">Now, in **System Administration**, you must edit the entity to enable automatically-generated Code values.</span></span> <span data-ttu-id="a7579-135">詳細については、「[自動コード作成 &#40;マスターデータサービス&#41;](automatic-code-creation-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7579-135">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).</span></span>  
  
 <span data-ttu-id="a7579-136">この種類のルールが格納された [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] モデルの配置パッケージを持っている場合は、データベースを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] にアップグレードすると、ビジネス ルールが除外されます。</span><span class="sxs-lookup"><span data-stu-id="a7579-136">If you have a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] model deployment package that contains a rule of this type, when you upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the business rule will be excluded.</span></span>  
  
### <a name="bulk-updates-and-exporting"></a><span data-ttu-id="a7579-137">一括更新と一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="a7579-137">Bulk Updates and Exporting</span></span>  
 <span data-ttu-id="a7579-138">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで、複数のメンバーの属性値を一括更新することができなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-138">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer update attribute values for multiple members in bulk.</span></span> <span data-ttu-id="a7579-139">一括更新を行うには、ステージング処理またはを使用し [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a7579-139">To do bulk updates, use the staging process or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="a7579-140">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで、メンバーを Excel にエクスポートできなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-140">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer export members to Excel.</span></span> <span data-ttu-id="a7579-141">Excel でメンバーを操作するには、を使用し [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a7579-141">To work with members in Excel, use the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="a7579-142">トランザクション</span><span class="sxs-lookup"><span data-stu-id="a7579-142">Transactions</span></span>  
 <span data-ttu-id="a7579-143">[**エクスプローラー** ] 機能領域では、ユーザーは自分のトランザクションを元に戻すことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="a7579-143">In the **Explorer** functional area, users can no longer revert their own transactions.</span></span> <span data-ttu-id="a7579-144">以前は、ユーザーは**エクスプローラー**でデータに対して行った変更を元に戻すことができました。</span><span class="sxs-lookup"><span data-stu-id="a7579-144">Previously, users could revert changes they made to data in **Explorer**.</span></span> <span data-ttu-id="a7579-145">管理者は、[**バージョン管理**] 機能領域のすべてのユーザーのトランザクションを元に戻すこともできます。</span><span class="sxs-lookup"><span data-stu-id="a7579-145">Administrators can still revert transactions for all users in the **Version Management** functional area.</span></span>  
  
 <span data-ttu-id="a7579-146">注釈が永続的に保持されるようになり、削除できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-146">Annotations are now permanent and cannot be deleted.</span></span> <span data-ttu-id="a7579-147">以前は、注釈はトランザクションと見なされていて、トランザクションを元に戻すことで削除できました。</span><span class="sxs-lookup"><span data-stu-id="a7579-147">Previously, annotations were considered transactions and could be deleted by reverting the transaction.</span></span>  
  
### <a name="web-service"></a><span data-ttu-id="a7579-148">Web サービス</span><span class="sxs-lookup"><span data-stu-id="a7579-148">Web Service</span></span>  
 <span data-ttu-id="a7579-149">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サービスが、Silverlight の必要に応じて自動的に有効にされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-149">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] web service is now enabled automatically, as required by Silverlight.</span></span> <span data-ttu-id="a7579-150">以前は、Web サービスは手動で有効にする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="a7579-150">Previously, the web service had to be enabled manually.</span></span>  
  
### <a name="powershell-cmdlets"></a><span data-ttu-id="a7579-151">PowerShell コマンドレット</span><span class="sxs-lookup"><span data-stu-id="a7579-151">PowerShell Cmdlets</span></span>  
 <span data-ttu-id="a7579-152">MDS に PowerShell コマンドレットが含まれなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7579-152">MDS no longer includes PowerShell cmdlets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7579-153">参照</span><span class="sxs-lookup"><span data-stu-id="a7579-153">See Also</span></span>  
 [<span data-ttu-id="a7579-154">SQL Server 2014 に含まれている非推奨のマスター データ サービス機能</span><span class="sxs-lookup"><span data-stu-id="a7579-154">Deprecated Master Data Services Features in SQL Server 2014</span></span>](deprecated-master-data-services-features.md)  
  
  
