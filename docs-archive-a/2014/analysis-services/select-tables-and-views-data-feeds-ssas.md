---
title: '[テーブルとビューの選択] (データフィード) (SSAS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviewsdf.f1
ms.assetid: 6c4fafe0-e02e-47d1-b8bc-e70e872690af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 46c317ecf2a87adcde264e8d6d7e822eb833b8b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639683"
---
# <a name="select-tables-and-views-data-feeds-ssas"></a><span data-ttu-id="7bb0c-102">[テーブルとビューの選択] (データ フィード) (SSAS)</span><span class="sxs-lookup"><span data-stu-id="7bb0c-102">Select Tables and Views (Data Feeds) (SSAS)</span></span>
  <span data-ttu-id="7bb0c-103">**テーブルのインポート ウィザード** のこのページを使用すると、データのインポート元となるテーブルとビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-103">This page of the **Table Import Wizard** enables you to select the tables and views that you want to import data from.</span></span> <span data-ttu-id="7bb0c-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="7bb0c-105">このページに表示されるテーブルとビューは、インポートの成功を保証するものではありません。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-105">The appearance of tables and views on this page does not guarantee that import will succeed.</span></span> <span data-ttu-id="7bb0c-106">[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-106">If the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
 <span data-ttu-id="7bb0c-107">Windows 認証を使用したデータ ソースの場合、[テーブルとビューの選択] ダイアログにおけるテーブルおよびビューは、現在のユーザーの資格情報を使用してフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the tables and views in the Select Tables and Views dialog.</span></span> <span data-ttu-id="7bb0c-108">その他のデータ ソースについては、接続文字列に指定された資格情報を使用してデータがフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7bb0c-109">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="7bb0c-109">UI element list</span></span>  
 <span data-ttu-id="7bb0c-110">**データフィード URL**</span><span class="sxs-lookup"><span data-stu-id="7bb0c-110">**Data feed URL**</span></span>  
 <span data-ttu-id="7bb0c-111">選択したデータ フィードの URL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-111">Displays the URL for the data feed that you selected.</span></span>  
  
 <span data-ttu-id="7bb0c-112">**テーブルとビュー**</span><span class="sxs-lookup"><span data-stu-id="7bb0c-112">**Tables and views**</span></span>  
 <span data-ttu-id="7bb0c-113">データ フィードのテーブルおよびビューが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-113">Lists the tables and views in the data feed.</span></span> <span data-ttu-id="7bb0c-114">インポートする各テーブルとビューの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-114">Select the checkbox beside each table and view that you want to import.</span></span>  
  
 <span data-ttu-id="7bb0c-115">**基になるテーブル**</span><span class="sxs-lookup"><span data-stu-id="7bb0c-115">**Source Table**</span></span>  
 <span data-ttu-id="7bb0c-116">データ ソースの種類に応じて、ソース テーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-116">Specifies the name of the source table based on the type of data source.</span></span>  
  
 <span data-ttu-id="7bb0c-117">**フレンドリ名**</span><span class="sxs-lookup"><span data-stu-id="7bb0c-117">**Friendly Name**</span></span>  
 <span data-ttu-id="7bb0c-118">ソース テーブルの表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-118">Specifies the friendly name of the source table.</span></span> <span data-ttu-id="7bb0c-119">既定では、 **[ソース テーブル]** 列に表示されるソース テーブルの名前が列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-119">By default, the column displays the name of the source table that appears in the **Source Table** column.</span></span>  
  
 <span data-ttu-id="7bb0c-120">**フィルターの詳細**</span><span class="sxs-lookup"><span data-stu-id="7bb0c-120">**Filter Details**</span></span>  
 <span data-ttu-id="7bb0c-121">インポートするデータにフィルターが適用されると、**[フィルターの詳細]** ダイアログ ボックスにデータ インポート フィルターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-121">Displays the data import filter in the **Filter Details** dialog box, when a filter has been applied to the data that is being imported.</span></span> <span data-ttu-id="7bb0c-122">詳細については、「[[フィルターの詳細] (SSAS)](filter-details-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-122">For more information, see [Filter Details &#40;SSAS&#41;](filter-details-ssas.md).</span></span>  
  
 <span data-ttu-id="7bb0c-123">**[プレビューとフィルター]**</span><span class="sxs-lookup"><span data-stu-id="7bb0c-123">**Preview and Filter**</span></span>  
 <span data-ttu-id="7bb0c-124">インポートするデータにフィルターを適用するときに使用する **[選択したテーブルのプレビュー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-124">Displays the **Preview Selected Table** dialog box that is used to apply a filter to the data that is being imported.</span></span> <span data-ttu-id="7bb0c-125">詳細については、「[[選択したテーブルのプレビュー] (SSAS)](preview-selected-table-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-125">For more information, see [Preview Selected Table &#40;SSAS&#41;](preview-selected-table-ssas.md).</span></span>  
  
 <span data-ttu-id="7bb0c-126">**[関連テーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="7bb0c-126">**Select Related Tables**</span></span>  
 <span data-ttu-id="7bb0c-127">選択したテーブルとビューに関連するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7bb0c-127">Select tables that are related to the tables and views that you have selected.</span></span>  
  
  
