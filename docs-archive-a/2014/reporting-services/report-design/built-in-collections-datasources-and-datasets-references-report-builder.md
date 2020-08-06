---
title: DataSources コレクションと DataSets コレクションの参照 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 560a42daf4d4580adde5b6100fe23f2c646fff08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644338"
---
# <a name="datasources-and-datasets-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="43143-102">DataSources コレクションと DataSets コレクションの参照 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="43143-102">DataSources and DataSets Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="43143-103">`DataSources` コレクションは、レポートで使用されているすべてのデータ ソースを表します。</span><span class="sxs-lookup"><span data-stu-id="43143-103">The `DataSources` collection represents all the data sources used in a report.</span></span> <span data-ttu-id="43143-104">同様に、`DataSets` コレクションは、レポート内のすべてのデータ ソースのデータセットすべてを表します。</span><span class="sxs-lookup"><span data-stu-id="43143-104">Similarly, the `DataSets` collection represents all the datasets for all the data sources in a report.</span></span> <span data-ttu-id="43143-105">参照するデータ ソース別に構成されているレポート データセットの階層ビューを表示するには、 **[レポート データ]** ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="43143-105">Use the **Report Data** pane for a hierarchical view of report datasets organized under the data source they reference.</span></span> <span data-ttu-id="43143-106">これらのコレクションへの参照を含めても、レポートをプレビューしたときには値が表示されません。</span><span class="sxs-lookup"><span data-stu-id="43143-106">If you include references to these collections, you will not see values when previewing your report.</span></span> <span data-ttu-id="43143-107">このコレクションを使用できるのは、レポートがレポート サーバーにパブリッシュされた後だけです。</span><span class="sxs-lookup"><span data-stu-id="43143-107">These collections are only available after the report has been published to a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a><span data-ttu-id="43143-108">DataSources</span><span class="sxs-lookup"><span data-stu-id="43143-108">DataSources</span></span>  
 <span data-ttu-id="43143-109">`DataSources` コレクションは、パブリッシュ済みレポート定義で参照されるデータ ソースを表します。</span><span class="sxs-lookup"><span data-stu-id="43143-109">The `DataSources` collection represents the data sources referenced in a published report definition.</span></span> <span data-ttu-id="43143-110">この情報をレポートに含め、レポート データのソースを説明することもできます。</span><span class="sxs-lookup"><span data-stu-id="43143-110">You may choose to include this information in your report to document the source of the report data.</span></span> <span data-ttu-id="43143-111">このコレクションは、 **プレビュー** モードでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="43143-111">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="43143-112">次の表では、`DataSources` コレクション内の変数について説明します。</span><span class="sxs-lookup"><span data-stu-id="43143-112">The following table describes the variables within the `DataSources` collection.</span></span>  
  
|<span data-ttu-id="43143-113">**変数**</span><span class="sxs-lookup"><span data-stu-id="43143-113">**Variable**</span></span>|`Type`|<span data-ttu-id="43143-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="43143-114">**Description**</span></span>|  
|------------------|--------------|---------------------|  
|`DataSourceReference`|`String`|<span data-ttu-id="43143-115">レポート サーバー上のデータ ソース定義の完全パスです。</span><span class="sxs-lookup"><span data-stu-id="43143-115">The full path of the data source definition on the report server.</span></span> <span data-ttu-id="43143-116">たとえば、レポートでレポート履歴の一部として使用されたすべてのデータ ソースの一覧を含める場合があります。</span><span class="sxs-lookup"><span data-stu-id="43143-116">For example, you might include a list of all the data sources a report used as part of a report history.</span></span> <span data-ttu-id="43143-117">次の例では、AdventureWorks2012 という名前のデータ ソースの完全パスを示します。</span><span class="sxs-lookup"><span data-stu-id="43143-117">The following example shows the full path for the data source named AdventureWorks2012:</span></span><br /><br /> <span data-ttu-id="43143-118">`/DataSources/AdventureWorks2012`.</span><span class="sxs-lookup"><span data-stu-id="43143-118">`/DataSources/AdventureWorks2012`.</span></span>|  
|`Type`|`String`|<span data-ttu-id="43143-119">データ ソースのデータ プロバイダーの種類です。</span><span class="sxs-lookup"><span data-stu-id="43143-119">The type of data provider for the data source.</span></span> <span data-ttu-id="43143-120">たとえば、「 `SQL` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="43143-120">For example, `SQL`.</span></span>|  
  
## <a name="datasets"></a><span data-ttu-id="43143-121">データセット</span><span class="sxs-lookup"><span data-stu-id="43143-121">DataSets</span></span>  
 <span data-ttu-id="43143-122">`DataSets` コレクションは、レポート定義で参照されるデータセットを表します。</span><span class="sxs-lookup"><span data-stu-id="43143-122">The `DataSets` collection represents the datasets referenced in a report definition.</span></span> <span data-ttu-id="43143-123">レポートのクエリをテキスト ボックスに含めて、レポート内のデータに関心を持っているユーザーが元のコマンド テキストを参照できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="43143-123">You may choose to include the query in the report in a text box, so a user interested in exactly which data is in the report can see the original command text.</span></span> <span data-ttu-id="43143-124">このコレクションは、 **プレビュー** モードでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="43143-124">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="43143-125">次の表では、`DataSets` コレクションのメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="43143-125">The following table describes the members of the `DataSets` collection.</span></span>  
  
|<span data-ttu-id="43143-126">**Member**</span><span class="sxs-lookup"><span data-stu-id="43143-126">**Member**</span></span>|`Type`|<span data-ttu-id="43143-127">**説明**</span><span class="sxs-lookup"><span data-stu-id="43143-127">**Description**</span></span>|  
|----------------|--------------|---------------------|  
|`CommandText`|`String`|<span data-ttu-id="43143-128">データベース データ ソースの場合、これはデータ ソースからデータを取得するために使用するクエリです。</span><span class="sxs-lookup"><span data-stu-id="43143-128">For database data sources, this is the query used to retrieve data from the data source.</span></span> <span data-ttu-id="43143-129">クエリが式の場合は、評価済みの式になります。</span><span class="sxs-lookup"><span data-stu-id="43143-129">If the query is an expression, this is the evaluated expression.</span></span>|  
|`RewrittenCommandText`|`String`|<span data-ttu-id="43143-130">データ プロバイダーの展開された CommandText 値。</span><span class="sxs-lookup"><span data-stu-id="43143-130">The data provider's expanded CommandText value.</span></span> <span data-ttu-id="43143-131">これは通常、レポート パラメーターにマップされたクエリ パラメーターと共にレポートに使用されます。</span><span class="sxs-lookup"><span data-stu-id="43143-131">This is typically used for reports with query parameters that are mapped to report parameters.</span></span> <span data-ttu-id="43143-132">コマンド テキスト パラメーター参照を、マップされたレポート パラメーターに対して選択された定数値に展開する場合、データ プロバイダーがこのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="43143-132">The data provider sets this property when expanding the command text parameter references into the constant values selected for the mapped report parameters.</span></span>|  
  
### <a name="using-query-expressions"></a><span data-ttu-id="43143-133">クエリ式の使用</span><span class="sxs-lookup"><span data-stu-id="43143-133">Using Query Expressions</span></span>  
 <span data-ttu-id="43143-134">式を使用して、データセットに含まれているクエリを定義できます。</span><span class="sxs-lookup"><span data-stu-id="43143-134">You can use expressions to define the query that is contained in a dataset.</span></span> <span data-ttu-id="43143-135">この機能を使用して、ユーザーからの入力や他のデータセットのデータ、その他の変数によりクエリが変化するようにレポートをデザインできます。</span><span class="sxs-lookup"><span data-stu-id="43143-135">You can use this feature to design reports in which the query changes based on input from the user, data in other datasets, or other variables.</span></span> <span data-ttu-id="43143-136">クエリについては、「[レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43143-136">For more information about queries, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43143-137">参照</span><span class="sxs-lookup"><span data-stu-id="43143-137">See Also</span></span>  
 <span data-ttu-id="43143-138">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43143-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="43143-139">式の例 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="43143-139">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
