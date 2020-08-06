---
title: Web サービス操作の分類 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e3f346b5-7e26-481d-9821-1846e2e91289
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0f7dd682f55c16c6dcbff9f0f669593a10486da6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643459"
---
# <a name="categorized-web-service-operations-master-data-services"></a><span data-ttu-id="51a13-102">Web サービス操作の分類 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="51a13-102">Categorized Web Service Operations (Master Data Services)</span></span>
  <span data-ttu-id="51a13-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスには、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] がユーザー インターフェイスを通じて行うすべての機能をコード記述で制御できるようにするための操作が、完全なセットとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="51a13-103">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service contains a complete set of operations that let you write code to control all of the features that [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] does through its user interface.</span></span> <span data-ttu-id="51a13-104">Web サービス操作は、<xref:Microsoft.MasterDataServices.IService> インターフェイスによって定義され、<xref:Microsoft.MasterDataServices.ServiceClient> クラスのメソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-104">The web service operations are defined by the <xref:Microsoft.MasterDataServices.IService> interface and are implemented as methods in the <xref:Microsoft.MasterDataServices.ServiceClient> class.</span></span> <span data-ttu-id="51a13-105">このトピックでは、Web サービス API の使用方法を理解しやすくするために、Web サービス操作を概念ごとのカテゴリに分類します。</span><span class="sxs-lookup"><span data-stu-id="51a13-105">This topic groups the web service operations into conceptual categories to help you understand how to use the web service API.</span></span>  
  
## <a name="model-operations"></a><span data-ttu-id="51a13-106">モデルの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-106">Model Operations</span></span>  
 <span data-ttu-id="51a13-107">これらの操作は、モデルの作成、更新、削除のほか、モデルの全コンテンツ (エンティティ、階層、バージョンなど) に対する操作に使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-107">These operations are used to create, update, and delete models, as well as to operate on all the contents of a model, such as entities, hierarchies, and versions.</span></span> <span data-ttu-id="51a13-108">詳細については、「[モデル (マスター データ サービス)](../models-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-108">For more information, see [Models &#40;Master Data Services&#41;](../models-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>|  
  
## <a name="entity-operations"></a><span data-ttu-id="51a13-109">エンティティの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-109">Entity Operations</span></span>  
 <span data-ttu-id="51a13-110">これらの操作は、単一のエンティティのメンバーを作成、更新、削除するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-110">These operations are used to create, update, and delete the members of a single entity.</span></span> <span data-ttu-id="51a13-111">詳細については、「[エンティティ &#40;マスター データ サービス&#41;](../entities-master-data-services.md)」と「[メンバー &#40;マスター データ サービス&#41;](../members-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-111">For more information, see [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md) and [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberKeyLookup%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersUpdate%2A>|  
  
## <a name="member-operations"></a><span data-ttu-id="51a13-112">メンバーの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-112">Member Operations</span></span>  
 <span data-ttu-id="51a13-113">これらの操作は、メンバーを取得、更新、削除するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-113">These operations are used to get, update, and delete members.</span></span> <span data-ttu-id="51a13-114">操作されるメンバーのセットには、複数のエンティティからのメンバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="51a13-114">The set of members operated on can contain members from multiple entities.</span></span> <span data-ttu-id="51a13-115">詳細については、「[バージョン (マスター データ サービス)](../members-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-115">For more information, see [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersGet%2A>|  
  
## <a name="attribute-and-hierarchy-operations"></a><span data-ttu-id="51a13-116">属性と階層の操作</span><span class="sxs-lookup"><span data-stu-id="51a13-116">Attribute and Hierarchy Operations</span></span>  
 <span data-ttu-id="51a13-117">これらの操作は、属性や階層の情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-117">These operations are used to get attribute and hierarchy information.</span></span> <span data-ttu-id="51a13-118">属性と階層は、モデル操作 (<xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A> など) を使用して変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="51a13-118">Attributes and hierarchies can also be modified by using the model operations, such as <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>.</span></span> <span data-ttu-id="51a13-119">詳細については、「[属性 &#40;マスター データ サービス&#41;](../attributes-master-data-services.md)」と「[階層 &#40;マスター データ サービス&#41;](../hierarchies-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-119">For more information, see [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) and [Hierarchies &#40;Master Data Services&#41;](../hierarchies-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAttributesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.HierarchyMembersGet%2A>|  
  
## <a name="business-rule-operations"></a><span data-ttu-id="51a13-120">ビジネス ルールの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-120">Business Rule Operations</span></span>  
 <span data-ttu-id="51a13-121">これらの操作は、ビジネス ルールを作成、更新、削除、パブリッシュするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-121">These operations are used to create, update, delete, and publish business rules.</span></span> <span data-ttu-id="51a13-122">詳細については、「[ビジネス ルール (マスター データ サービス)](../business-rules-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-122">For more information, see [Business Rules &#40;Master Data Services&#41;](../business-rules-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPaletteGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPublish%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesUpdate%2A>|  
  
## <a name="annotation-operations"></a><span data-ttu-id="51a13-123">注釈の操作</span><span class="sxs-lookup"><span data-stu-id="51a13-123">Annotation Operations</span></span>  
 <span data-ttu-id="51a13-124">これらの操作は、注釈を作成、更新、削除するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-124">These operations are used to create, update, and delete annotations.</span></span> <span data-ttu-id="51a13-125">詳細については、「[注釈 &#40;マスター データ サービス&#41;](../annotations-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-125">For more information, see [Annotations &#40;Master Data Services&#41;](../annotations-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsGet%2A>|  
  
## <a name="transaction-operations"></a><span data-ttu-id="51a13-126">トランザクションの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-126">Transaction Operations</span></span>  
 <span data-ttu-id="51a13-127">これらの操作は、トランザクションを取得および破棄するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-127">These operations are used to get and reverse transactions.</span></span> <span data-ttu-id="51a13-128">詳細については、「[トランザクション (マスター データ サービス)](../transactions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-128">For more information, see [Transactions &#40;Master Data Services&#41;](../transactions-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsReverse%2A>|  
  
## <a name="version-and-validation-operations"></a><span data-ttu-id="51a13-129">バージョンと検証の操作</span><span class="sxs-lookup"><span data-stu-id="51a13-129">Version and Validation Operations</span></span>  
 <span data-ttu-id="51a13-130">これらの操作は、バージョンをコピーおよび検証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-130">These operations are used to copy and validate versions.</span></span> <span data-ttu-id="51a13-131">詳細については、「[バージョン &#40;マスター データ サービス&#41;](../versions-master-data-services.md)」と「[検証 &#40;マスター データ サービス&#41;](../validation-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-131">For more information, see [Versions &#40;Master Data Services&#41;](../versions-master-data-services.md) and [Validation &#40;Master Data Services&#41;](../validation-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.VersionCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationProcess%2A>|  
  
## <a name="data-quality-operations"></a><span data-ttu-id="51a13-132">データ品質の操作</span><span class="sxs-lookup"><span data-stu-id="51a13-132">Data Quality Operations</span></span>  
 <span data-ttu-id="51a13-133">これらの操作は、データ品質タスクの実行と、それらの結果の確認に使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-133">These operations are used to perform data quality tasks and to examine their results.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityCleansingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityMatchingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStart%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityInstalledState%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityKnowledgeBasesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationResultsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStatus%2A>|  
  
## <a name="data-import-operations"></a><span data-ttu-id="51a13-134">データ インポートの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-134">Data Import Operations</span></span>  
 <span data-ttu-id="51a13-135">これらの操作は、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースにデータをインポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-135">These operations are used to import data into a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="51a13-136">詳細については、「[データのインポート &#40;マスター データ サービス&#41;](../overview-importing-data-from-tables-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-136">For more information, see [Data Import &#40;Master Data Services&#41;](../overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingLoad%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingProcess%2A>|  
  
 <span data-ttu-id="51a13-137">次の操作は、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] に含まれるステージング処理を使用してデータをインポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-137">The following operations are used to import data by using the staging process included in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="51a13-138">これらの操作は、既存のデータベースをサポートする目的にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-138">These operations should be used only to support existing databases.</span></span> <span data-ttu-id="51a13-139">新規の開発には、先に示した操作を使用してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-139">For new development, use the previously listed operations.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingNameCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingProcess%2A>|  
  
## <a name="data-export-operations"></a><span data-ttu-id="51a13-140">データ エクスポートの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-140">Data Export Operations</span></span>  
 <span data-ttu-id="51a13-141">これらの操作は、サブスクリプション ビューを使用してデータをエクスポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-141">These operations are used to export data through the use of subscription views.</span></span> <span data-ttu-id="51a13-142">詳細については、「[データ &#40;マスターデータサービス&#41;のエクスポート](../overview-exporting-data-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-142">For more information, see [Exporting Data &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewUpdate%2A>|  
  
## <a name="security-operations"></a><span data-ttu-id="51a13-143">セキュリティ運用担当者</span><span class="sxs-lookup"><span data-stu-id="51a13-143">Security Operations</span></span>  
 <span data-ttu-id="51a13-144">これらの操作は、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースへのアクセスを制御するセキュリティ設定を変更するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-144">These operations are used to modify the security settings that control access to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="51a13-145">詳細については、「[セキュリティ (マスター データ サービス)](../security-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a13-145">For more information, see [Security &#40;Master Data Services&#41;](../security-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesUpdate%2A>|  
  
## <a name="system-operations"></a><span data-ttu-id="51a13-146">システムの操作</span><span class="sxs-lookup"><span data-stu-id="51a13-146">System Operations</span></span>  
 <span data-ttu-id="51a13-147">これらの操作は、システム設定やユーザー設定を取得および更新するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a13-147">These operations are used to get and update system settings and user preferences.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceVersionGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemDomainListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemPropertiesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesUpdate%2A>|  
  
  
