---
title: データのインポート (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 403eca212611397fb3ba30f8fe12a2aa8b5e83ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632011"
---
# <a name="data-import-master-data-services"></a><span data-ttu-id="93c2a-102">データのインポート (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="93c2a-102">Data Import (Master Data Services)</span></span>
  <span data-ttu-id="93c2a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]内のデータのモデルを作成すると、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースでデータの追加と変更ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="93c2a-103">Once you've created a model for your data in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can start adding data and make changes to data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>   <span data-ttu-id="93c2a-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ステージング テーブル、ストアド プロシージャ、マスター データ マネージャーを使います。</span><span class="sxs-lookup"><span data-stu-id="93c2a-104">You use [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] staging tables, stored procedures and Master Data Manager .</span></span>

 <span data-ttu-id="93c2a-105">また、を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] MDS リポジトリ (データベース) にデータを追加することもでき [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-105">You can also use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], to add data to the MDS repository ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database).</span></span> <span data-ttu-id="93c2a-106">詳細については、「[データ &#40;Excel 用 MDS アドイン&#41;のパブリッシュ](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c2a-106">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>

 <span data-ttu-id="93c2a-107">データを追加して更新するときに、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-107">When you add and update data, you can do the following.</span></span>

-   <span data-ttu-id="93c2a-108">メンバーの読み込みと更新、属性値の更新</span><span class="sxs-lookup"><span data-stu-id="93c2a-108">Load and update members, and update attribute values</span></span>

-   <span data-ttu-id="93c2a-109">メンバーの非アクティブ化と削除</span><span class="sxs-lookup"><span data-stu-id="93c2a-109">Deactivate and delete members</span></span>

-   <span data-ttu-id="93c2a-110">明示的階層メンバーの移動</span><span class="sxs-lookup"><span data-stu-id="93c2a-110">Move explicit hierarchy members</span></span>

 <span data-ttu-id="93c2a-111">データの追加と更新には、次の主要なタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-111">Adding and updating data  includes the following main tasks.</span></span>

1.  <span data-ttu-id="93c2a-112">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのステージング テーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-112">Load data into the staging tables in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>

2.  <span data-ttu-id="93c2a-113">ステージング テーブルから適切な [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] テーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-113">Load the data from the staging tables into the appropriate [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] tables.</span></span>

     <span data-ttu-id="93c2a-114">ステージング ストアド プロシージャや [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を使って、データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-114">You use staging stored procedures or [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to load the data.</span></span>

> [!NOTE]
>  <span data-ttu-id="93c2a-115">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] では、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ステージング プロセスのサポートは非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="93c2a-115">In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], support for the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging processes is deprecated.</span></span>

## <a name="deactivating-and-deleting-members"></a><span data-ttu-id="93c2a-116">メンバーの非アクティブ化と削除</span><span class="sxs-lookup"><span data-stu-id="93c2a-116">Deactivating and Deleting Members</span></span>
 <span data-ttu-id="93c2a-117">非アクティブにしたメンバーは、再びアクティブにできます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-117">Deactivating means the member can be reactivated.</span></span> <span data-ttu-id="93c2a-118">メンバーを再びアクティブにすると、階層およびコレクションにおける属性とメンバーシップが復元されます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-118">If you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span> <span data-ttu-id="93c2a-119">以前のトランザクションはすべてそのままです。</span><span class="sxs-lookup"><span data-stu-id="93c2a-119">All previous transactions are intact.</span></span> <span data-ttu-id="93c2a-120">マスター データ マネージャーの **[バージョン管理]** 機能領域の管理者は、非アクティブになっているトランザクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-120">Deactivation transactions are visible to administrators in the **Version Management** functional area of the Master Data Manager.</span></span>

 <span data-ttu-id="93c2a-121">削除したメンバーは、システムから完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-121">Deleting means purging the member from the system permanently.</span></span> <span data-ttu-id="93c2a-122">そのメンバーのすべてのトランザクション、すべてのリレーションシップ、およびすべての属性が完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-122">All transactions for the member, all relationships, and all attributes are permanently deleted.</span></span>

> [!NOTE]
>  <span data-ttu-id="93c2a-123">ステージングを使用してメンバーを再アクティブ化することはできません。</span><span class="sxs-lookup"><span data-stu-id="93c2a-123">You cannot use staging to reactivate members.</span></span> <span data-ttu-id="93c2a-124">マスター データ マネージャーで手動で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="93c2a-124">You must do it manually in the Master Data Manager.</span></span> <span data-ttu-id="93c2a-125">詳細については、「[メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)](reactivate-a-member-or-collection-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c2a-125">For more information, see [Reactivate a Member or Collection &#40;Master Data Services&#41;](reactivate-a-member-or-collection-master-data-services.md).</span></span>
> 
>  <span data-ttu-id="93c2a-126">ステージングを使用してコレクションを削除または非アクティブ化することはできません。</span><span class="sxs-lookup"><span data-stu-id="93c2a-126">You cannot use staging to delete or deactivate collections.</span></span> <span data-ttu-id="93c2a-127">手動でのコレクションの非アクティブ化の詳細については、「[メンバーまたはコレクションを削除する (マスター データ サービス)](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c2a-127">For more information on manually deactivating collections, see [Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md).</span></span>

## <a name="moving-explicit-hierarchy-members"></a><span data-ttu-id="93c2a-128">明示的階層メンバーの移動</span><span class="sxs-lookup"><span data-stu-id="93c2a-128">Moving explicit hierarchy members</span></span>
 <span data-ttu-id="93c2a-129">明示的階層に含まれるメンバーの位置を一括で移動するときは、次を指定できます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-129">When you move the location of members in explicit hierarchies in bulk, you can designate the following.</span></span>

-   <span data-ttu-id="93c2a-130">統合メンバーの親として統合メンバー。</span><span class="sxs-lookup"><span data-stu-id="93c2a-130">A consolidated member as a parent of a consolidated member.</span></span>

-   <span data-ttu-id="93c2a-131">リーフ メンバーの親として統合メンバー。</span><span class="sxs-lookup"><span data-stu-id="93c2a-131">A consolidated member as a parent of a leaf member.</span></span>

-   <span data-ttu-id="93c2a-132">リーフ メンバーまたは統合メンバーの兄弟としてリーフ メンバー。</span><span class="sxs-lookup"><span data-stu-id="93c2a-132">A leaf member as a sibling of a leaf or consolidated member.</span></span>

-   <span data-ttu-id="93c2a-133">リーフ メンバーまたは統合メンバーの兄弟として統合メンバー。</span><span class="sxs-lookup"><span data-stu-id="93c2a-133">A consolidated member as a sibling of a leaf or consolidated member.</span></span>

## <a name="staging-tables-and-stored-procedures"></a><span data-ttu-id="93c2a-134">ステージング テーブルとストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="93c2a-134">Staging Tables and Stored Procedures</span></span>
 <span data-ttu-id="93c2a-135">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースには、データを設定できる、次の種類のステージング テーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="93c2a-135">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database includes the following types of staging tables that you can populate with your  data.</span></span>

-   [<span data-ttu-id="93c2a-136">リーフ メンバー ステージング テーブル (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="93c2a-136">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="93c2a-137">統合メンバー ステージング テーブル (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="93c2a-137">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="93c2a-138">リレーションシップ ステージング テーブル (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="93c2a-138">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)

 <span data-ttu-id="93c2a-139">モデル内の各エンティティには、ステージング テーブルがあります。</span><span class="sxs-lookup"><span data-stu-id="93c2a-139">For each entity in the model, there is a staging table.</span></span> <span data-ttu-id="93c2a-140">テーブル名は、対応するエンティティと、リーフ メンバーなどのエンティティ型を示します。</span><span class="sxs-lookup"><span data-stu-id="93c2a-140">The table name indicates the corresponding entity, and the entity type such as leaf member.</span></span> <span data-ttu-id="93c2a-141">次の画像は、通貨、顧客、製品のエンティティのステージング テーブルを示しています。</span><span class="sxs-lookup"><span data-stu-id="93c2a-141">The following image shows the staging tables for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="93c2a-142">![MDS データベースのステージング テーブル](../../2014/master-data-services/media/mds-stagingtables.png "MDS データベースのステージング テーブル")</span><span class="sxs-lookup"><span data-stu-id="93c2a-142">![Staging Tables in MDS database](../../2014/master-data-services/media/mds-stagingtables.png "Staging Tables in MDS database")</span></span>

 <span data-ttu-id="93c2a-143">テーブルの名前はエンティティの作成時に指定され、変更できません。</span><span class="sxs-lookup"><span data-stu-id="93c2a-143">The name of the  table is specified when an entity is created and cannot be changed.</span></span> <span data-ttu-id="93c2a-144">ステージング テーブルの名前に _1 またはその他の数値が含まれる場合は、エンティティの作成時にその名前のテーブルが既に存在していたことを示します。</span><span class="sxs-lookup"><span data-stu-id="93c2a-144">If the staging table name contains a _1 or other number, another table of that name already existed when the entity was created.</span></span>

 <span data-ttu-id="93c2a-145">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、次の種類のステージング ストアド プロシージャが含まれています。</span><span class="sxs-lookup"><span data-stu-id="93c2a-145">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] includes the following types of staging stored procedures.</span></span>

-   <span data-ttu-id="93c2a-146">stg. udp_ \<name> _Leaf</span><span class="sxs-lookup"><span data-stu-id="93c2a-146">stg.udp_\<name>_Leaf</span></span>

-   <span data-ttu-id="93c2a-147">stg. udp_ \<name> _Consolidated</span><span class="sxs-lookup"><span data-stu-id="93c2a-147">stg.udp_\<name>_Consolidated</span></span>

-   <span data-ttu-id="93c2a-148">stg. udp_ \<name> _Relationship</span><span class="sxs-lookup"><span data-stu-id="93c2a-148">stg.udp_\<name>_Relationship</span></span>

 <span data-ttu-id="93c2a-149">モデル内の各エンティティには、リーフ メンバー、統合メンバー、リレーションシップ ステージング テーブルに対応する 3 つのストアド プロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="93c2a-149">For each entity in the model, there are three stored procedures that correspond to the leaf member, consolidated member, and relationship staging tables.</span></span>  <span data-ttu-id="93c2a-150">次の画像は、通貨、顧客、製品のエンティティのステージング ストアド テーブルを示しています。</span><span class="sxs-lookup"><span data-stu-id="93c2a-150">The following image shows the staging stored procedures for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="93c2a-151">![MDS データベースでのステージング ストアド プロシージャ](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "MDS データベースでのステージング ストアド プロシージャ")</span><span class="sxs-lookup"><span data-stu-id="93c2a-151">![Staging Stored Procedures in MDS database](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "Staging Stored Procedures in MDS database")</span></span>

 <span data-ttu-id="93c2a-152">ストアド プロシージャの詳細については、「[ステージング ストアド プロシージャ (マスター データ サービス)](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c2a-152">For more information on the stored procedures, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>

## <a name="logging-transactions"></a><span data-ttu-id="93c2a-153">トランザクションのログ記録</span><span class="sxs-lookup"><span data-stu-id="93c2a-153">Logging Transactions</span></span>
 <span data-ttu-id="93c2a-154">データまたはリレーションシップのインポート時または更新時に発生するトランザクションは、すべてログに記録することができます。</span><span class="sxs-lookup"><span data-stu-id="93c2a-154">All transactions that occur when data or relationships are imported or updated can be logged.</span></span> <span data-ttu-id="93c2a-155">ストアド プロシージャのオプションによって、このログ記録が可能になります。</span><span class="sxs-lookup"><span data-stu-id="93c2a-155">An option in the stored procedure allows this logging.</span></span> <span data-ttu-id="93c2a-156">ステージング処理を [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]から開始する場合、ログ記録は行われません。</span><span class="sxs-lookup"><span data-stu-id="93c2a-156">If you initiate the staging process using [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], no logging occurs.</span></span>

 <span data-ttu-id="93c2a-157">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]では、 **[すべてのステージング トランザクションをログに記録]** 設定がステージング データのこのメソッドに適用されません。</span><span class="sxs-lookup"><span data-stu-id="93c2a-157">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], the **Log staging transactions** setting does not apply to this method of staging data.</span></span>

## <a name="related-content"></a><span data-ttu-id="93c2a-158">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="93c2a-158">Related Content</span></span>

-   [<span data-ttu-id="93c2a-159">検証 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="93c2a-159">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)

-   [<span data-ttu-id="93c2a-160">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="93c2a-160">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)


