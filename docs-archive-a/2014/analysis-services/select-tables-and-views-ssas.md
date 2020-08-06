---
title: '[テーブルとビューの選択] (SSAS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviews.f1
ms.assetid: 5e8121cc-03f0-4168-98cf-63c5c032bb0b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 891da51478670122f5dbce8fdd7be55c98c898c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738887"
---
# <a name="select-tables-and-views-ssas"></a><span data-ttu-id="54f7b-102">[テーブルとビューの選択] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="54f7b-102">Select Tables and Views (SSAS)</span></span>
  <span data-ttu-id="54f7b-103">**テーブルのインポート ウィザード** のこのページを使用すると、データのインポート元となるテーブルとビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-103">This page of the **Table Import Wizard** enables you to select the tables and views that you want to import data from.</span></span> <span data-ttu-id="54f7b-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54f7b-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="54f7b-105">このページに表示されるテーブルとビューは、インポートの成功を保証するものではありません。</span><span class="sxs-lookup"><span data-stu-id="54f7b-105">The appearance of tables and views on this page does not guarantee that import will succeed.</span></span> <span data-ttu-id="54f7b-106">[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="54f7b-106">If the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
 <span data-ttu-id="54f7b-107">Windows 認証を使用したデータ ソースの場合、[テーブルとビューの選択] ダイアログにおけるテーブルおよびビューは、現在のユーザーの資格情報を使用してフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the tables and views in the Select Tables and Views dialog.</span></span> <span data-ttu-id="54f7b-108">その他のデータ ソースについては、接続文字列に指定された資格情報を使用してデータがフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="54f7b-109">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="54f7b-109">UI element list</span></span>  
 <span data-ttu-id="54f7b-110">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="54f7b-110">**Server**</span></span>  
 <span data-ttu-id="54f7b-111">接続先のサーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-111">Displays the server that you are connected to.</span></span>  
  
 <span data-ttu-id="54f7b-112">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="54f7b-112">**Database**</span></span>  
 <span data-ttu-id="54f7b-113">選択したデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-113">Displays the database that you selected.</span></span>  
  
 <span data-ttu-id="54f7b-114">**Tables と Views**</span><span class="sxs-lookup"><span data-stu-id="54f7b-114">**Tables and Views**</span></span>  
 <span data-ttu-id="54f7b-115">データベース内のテーブルとビューの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-115">Lists the tables and views in the database.</span></span> <span data-ttu-id="54f7b-116">インポートする各テーブルとビューの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="54f7b-116">Select the checkbox beside each table and view that you want to import.</span></span>  
  
 <span data-ttu-id="54f7b-117">**基になるテーブル**</span><span class="sxs-lookup"><span data-stu-id="54f7b-117">**Source Table**</span></span>  
 <span data-ttu-id="54f7b-118">データ ソースの種類に応じて、ソース テーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="54f7b-118">Specifies the name of the source table based on the type of data source.</span></span>  
  
 <span data-ttu-id="54f7b-119">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="54f7b-119">**Schema**</span></span>  
 <span data-ttu-id="54f7b-120">ソース テーブルが含まれているスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="54f7b-120">Specifies the schema in which the source table is contained.</span></span> <span data-ttu-id="54f7b-121">データベースの種類によっては、スキーマは、他のオブジェクトのコンテナーの機能を果たし (テーブルなど)、それらのオブジェクトの所有権を示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-121">Depending on the type of database, a schema functions as a container for other objects, such as tables, and can also indicate ownership of those objects.</span></span>  
  
 <span data-ttu-id="54f7b-122">**フレンドリ名**</span><span class="sxs-lookup"><span data-stu-id="54f7b-122">**Friendly Name**</span></span>  
 <span data-ttu-id="54f7b-123">ソース テーブルの表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="54f7b-123">Specifies the friendly name of the source table.</span></span> <span data-ttu-id="54f7b-124">既定では、 **[ソース テーブル]** 列に表示されるソース テーブルの名前が列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-124">By default, the column displays the name of the source table that appears in the **Source Table** column.</span></span> <span data-ttu-id="54f7b-125">ソース データベースで使用される名前とは異なる名前を使用する場合は、名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="54f7b-125">Change the name if you want to use a different name than the name used in the source database.</span></span>  
  
 <span data-ttu-id="54f7b-126">**フィルターの詳細**</span><span class="sxs-lookup"><span data-stu-id="54f7b-126">**Filter Details**</span></span>  
 <span data-ttu-id="54f7b-127">インポートするデータにフィルターが適用されると、**[フィルターの詳細]** ダイアログ ボックスにデータ インポート フィルターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-127">When a filter has been applied to the data that is being imported, displays the data import filter in the **Filter Details** dialog box.</span></span> <span data-ttu-id="54f7b-128">詳細については、「[[フィルターの詳細] (SSAS)](filter-details-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54f7b-128">For more information, see [Filter Details &#40;SSAS&#41;](filter-details-ssas.md).</span></span>  
  
 <span data-ttu-id="54f7b-129">**[プレビューとフィルター]**</span><span class="sxs-lookup"><span data-stu-id="54f7b-129">**Preview and Filter**</span></span>  
 <span data-ttu-id="54f7b-130">インポートするデータにフィルターを適用するときに使用する **[選択したテーブルのプレビュー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54f7b-130">Displays the **Preview Selected Table** dialog box that is used to apply a filter to the data that is being imported.</span></span> <span data-ttu-id="54f7b-131">詳細については、「[[選択したテーブルのプレビュー] (SSAS)](preview-selected-table-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54f7b-131">For more information, see [Preview Selected Table &#40;SSAS&#41;](preview-selected-table-ssas.md).</span></span>  
  
 <span data-ttu-id="54f7b-132">**[関連テーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="54f7b-132">**Select Related Tables**</span></span>  
 <span data-ttu-id="54f7b-133">既に選択したテーブルとビューに関連するテーブルとビューをインポートする場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="54f7b-133">Selects for import those tables and views that are related to the tables and views that you have already selected.</span></span>  
  
  
