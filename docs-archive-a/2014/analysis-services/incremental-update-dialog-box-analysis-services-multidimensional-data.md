---
title: '[増分更新] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6115a5123fd6e72cee0ebccaac5f539be8aebfbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644680"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="0bf07-102">[増分更新] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="0bf07-102">Incremental Update Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="0bf07-103">**および** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [増分更新] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、メジャー グループおよびパーティションの増分更新の際に使用される設定を定義できます。</span><span class="sxs-lookup"><span data-stu-id="0bf07-103">Use the **Incremental Update** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to define the settings that are used when measure groups and partitions are incrementally updated.</span></span> <span data-ttu-id="0bf07-104">**[増分更新]** ダイアログ ボックスを表示するには、 **[処理]** ダイアログ ボックスで **[オブジェクト一覧]** グリッドの **[設定]** 列にある **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bf07-104">You can display the **Incremental Update** dialog box by clicking **Configure** in the **Settings** column of the **Object list** grid in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0bf07-105">Options</span><span class="sxs-lookup"><span data-stu-id="0bf07-105">Options</span></span>  
  
|<span data-ttu-id="0bf07-106">期間</span><span class="sxs-lookup"><span data-stu-id="0bf07-106">Term</span></span>|<span data-ttu-id="0bf07-107">定義</span><span class="sxs-lookup"><span data-stu-id="0bf07-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="0bf07-108">**メジャーグループ**</span><span class="sxs-lookup"><span data-stu-id="0bf07-108">**Measure Group**</span></span>|<span data-ttu-id="0bf07-109">増分更新を行うメジャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-109">Select the measure group to incrementally update.</span></span><br /><br /> <span data-ttu-id="0bf07-110">注: このオプションは、キューブの増分更新を行う場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-110">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="0bf07-111">メジャー グループまたはパーティションの増分更新を行う場合、このオプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-111">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="0bf07-112">**パーティション**</span><span class="sxs-lookup"><span data-stu-id="0bf07-112">**Partition**</span></span>|<span data-ttu-id="0bf07-113">更新するパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-113">Select the partition to update.</span></span><br /><br /> <span data-ttu-id="0bf07-114">注: このオプションは、キューブの増分更新を行う場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-114">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="0bf07-115">メジャー グループまたはパーティションの増分更新を行う場合、このオプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-115">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="0bf07-116">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="0bf07-116">**Table**</span></span>|<span data-ttu-id="0bf07-117">テーブルにあるオブジェクトを更新します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-117">Click to update the object from a table.</span></span>|  
|<span data-ttu-id="0bf07-118">**[データ ソースまたはビュー]**</span><span class="sxs-lookup"><span data-stu-id="0bf07-118">**Data source or view**</span></span>|<span data-ttu-id="0bf07-119">ソース テーブルがあるデータ ソースまたはデータ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-119">Select the data source or data source view in which the source table is located.</span></span><br /><br /> <span data-ttu-id="0bf07-120">注: このオプションは、 **[テーブル]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-120">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="0bf07-121">**[テーブルのスキーマと名前]**</span><span class="sxs-lookup"><span data-stu-id="0bf07-121">**Table schema and name**</span></span>|<span data-ttu-id="0bf07-122">キューブ、メジャー グループ、またはパーティションの増分更新を行うためのデータの取得に使用されるソース テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-122">Select the source table used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="0bf07-123">注: このオプションは、 **[テーブル]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-123">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="0bf07-124">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="0bf07-124">**Query**</span></span>|<span data-ttu-id="0bf07-125">クエリにあるオブジェクトを更新します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-125">Click to update the object from a query.</span></span>|  
|<span data-ttu-id="0bf07-126">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="0bf07-126">**Data Source**</span></span>|<span data-ttu-id="0bf07-127">クエリを実行するテーブルがあるデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-127">Select the data source in which the tables to be queried are located.</span></span><br /><br /> <span data-ttu-id="0bf07-128">注: このオプションは、 **[クエリ]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-128">Note: This option is enabled only if **Query** is selected.</span></span>|  
|<span data-ttu-id="0bf07-129">**[クエリ テキスト]**</span><span class="sxs-lookup"><span data-stu-id="0bf07-129">**Text of the query**</span></span>|<span data-ttu-id="0bf07-130">キューブ、メジャー グループ、またはパーティションの増分更新を行うためのデータの取得に使用されるクエリのテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="0bf07-130">Type the text of the query used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="0bf07-131">注: このオプションは、 **[クエリ]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0bf07-131">Note: This option is enabled only if **Query** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bf07-132">参照</span><span class="sxs-lookup"><span data-stu-id="0bf07-132">See Also</span></span>  
 <span data-ttu-id="0bf07-133">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="0bf07-133">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="0bf07-134">[[処理] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="0bf07-134">[Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](process-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
