---
title: '[テーブルとビューの選択] (データソースビューウィザード) (Analysis Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.selecttablesandviews.f1
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac7159255ef526d871ed8906fc873d9f16d2eb64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738886"
---
# <a name="select-tables-and-views-data-source-view-wizard-analysis-services"></a><span data-ttu-id="a2100-102">[テーブルとビューの選択] (データ ソース ビュー ウィザード) (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a2100-102">Select Tables and Views (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="a2100-103">**[テーブルとビューの選択]** ページを使用すると、データ ソース ビューに含めるテーブルまたはビューをデータ ソースから選択できます。</span><span class="sxs-lookup"><span data-stu-id="a2100-103">Use the **Select Tables and Views** page to select the tables or views from the data source that you want to include in the data source view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a2100-104">Options</span><span class="sxs-lookup"><span data-stu-id="a2100-104">Options</span></span>  
 <span data-ttu-id="a2100-105">**Available objects**</span><span class="sxs-lookup"><span data-stu-id="a2100-105">**Available objects**</span></span>  
 <span data-ttu-id="a2100-106">データ ソース スキーマのテーブルおよびビューをリストします。</span><span class="sxs-lookup"><span data-stu-id="a2100-106">Lists the tables and views in the data source schema.</span></span> <span data-ttu-id="a2100-107">複数のスキーマが一覧される場合、スキーマ名が各オブジェクトの名前のプレフィックスになります。</span><span class="sxs-lookup"><span data-stu-id="a2100-107">The schema name prefixes the name of every object if more than one schema is listed.</span></span> <span data-ttu-id="a2100-108">スキーマが 1 つしか表示されない場合、スキーマ名はオブジェクトの名前のプレフィックスにはなりません。</span><span class="sxs-lookup"><span data-stu-id="a2100-108">If only one schema is listed, the schema's name does not prefix the object names.</span></span>  
  
 <span data-ttu-id="a2100-109">昇順または降順でリストを並べ替えるには、 **[名前]** または **[種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2100-109">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="a2100-110">**Included objects**</span><span class="sxs-lookup"><span data-stu-id="a2100-110">**Included objects**</span></span>  
 <span data-ttu-id="a2100-111">データ ソース ビューに含めるテーブルとビューを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a2100-111">Lists the tables and views to include in the data source view.</span></span>  
  
 <span data-ttu-id="a2100-112">昇順または降順でリストを並べ替えるには、 **[名前]** または **[種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2100-112">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="a2100-113">**Assert**</span><span class="sxs-lookup"><span data-stu-id="a2100-113">**Filter**</span></span>  
 <span data-ttu-id="a2100-114">**[使用できるオブジェクト]** にリストされるオブジェクトをフィルターします。</span><span class="sxs-lookup"><span data-stu-id="a2100-114">Filters the objects listed under **Available objects**.</span></span> <span data-ttu-id="a2100-115">文字列を入力して **[フィルター]** ボタンをクリックすると、指定された文字列を含む名前のみが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2100-115">Type a string, and then click **Filter** to list only the names that contain a specified string.</span></span> <span data-ttu-id="a2100-116">正確な文字列を検索するには、文字列を二重引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="a2100-116">To find an exact string of characters, enclose the string between double quotation marks.</span></span> <span data-ttu-id="a2100-117">大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="a2100-117">The filter is not case sensitive.</span></span>  
  
 <span data-ttu-id="a2100-118">次の表に一覧表示されているワイルドカード文字をフィルター文字列に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a2100-118">You can include the wildcard characters listed in the following table anywhere in the filter string.</span></span>  
  
|<span data-ttu-id="a2100-119">ワイルドカード文字</span><span class="sxs-lookup"><span data-stu-id="a2100-119">Wildcard character</span></span>|<span data-ttu-id="a2100-120">値</span><span class="sxs-lookup"><span data-stu-id="a2100-120">Value</span></span>|  
|------------------------|-----------|  
|**\***|<span data-ttu-id="a2100-121">任意の文字列</span><span class="sxs-lookup"><span data-stu-id="a2100-121">Any string of characters</span></span>|  
|**%**|<span data-ttu-id="a2100-122">任意の文字列</span><span class="sxs-lookup"><span data-stu-id="a2100-122">Any string of characters</span></span>|  
|<span data-ttu-id="a2100-123">**?**</span><span class="sxs-lookup"><span data-stu-id="a2100-123">**?**</span></span>|<span data-ttu-id="a2100-124">1 つの文字</span><span class="sxs-lookup"><span data-stu-id="a2100-124">A single character</span></span>|  
|<span data-ttu-id="a2100-125">**"** *string* **"**</span><span class="sxs-lookup"><span data-stu-id="a2100-125">**"** *string* **"**</span></span>|<span data-ttu-id="a2100-126">リテラル文字列。</span><span class="sxs-lookup"><span data-stu-id="a2100-126">A literal string of characters.</span></span> <span data-ttu-id="a2100-127">このワイルドカード文字は、オブジェクト名内の任意の部分文字列に一致します。</span><span class="sxs-lookup"><span data-stu-id="a2100-127">This wildcard character will match any substring within the object name.</span></span>|  
  
 <span data-ttu-id="a2100-128">**Show system objects**</span><span class="sxs-lookup"><span data-stu-id="a2100-128">**Show system objects**</span></span>  
 <span data-ttu-id="a2100-129">**[使用できるオブジェクト]** にシステム オブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="a2100-129">Displays system objects under **Available objects**.</span></span> <span data-ttu-id="a2100-130">このオプションは、データ ソース プロバイダーがシステム オブジェクトを公開する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2100-130">This option is available only if the data source provider exposes system objects.</span></span> <span data-ttu-id="a2100-131">**[含まれているオブジェクト]** の一覧からシステム オブジェクトを削除すると、自動的にこのオプションが選択されます。</span><span class="sxs-lookup"><span data-stu-id="a2100-131">Removing a system object from the **Included objects** list automatically selects this option.</span></span>  
  
 <span data-ttu-id="a2100-132">**Add related tables**</span><span class="sxs-lookup"><span data-stu-id="a2100-132">**Add related tables**</span></span>  
 <span data-ttu-id="a2100-133">**[含まれているオブジェクト]** の一覧に関連するすべてのテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="a2100-133">Adds all the tables that are related to those listed under **Included objects**.</span></span> <span data-ttu-id="a2100-134">このオプションではビューを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2100-134">This option does not add views.</span></span> <span data-ttu-id="a2100-135">ただし、パーティション テーブルは追加できます。</span><span class="sxs-lookup"><span data-stu-id="a2100-135">However, this option does add partitioned tables.</span></span> <span data-ttu-id="a2100-136">ウィザードの **[名前の一致]** ページで名前の一致条件を選択した場合、このオプションは選択された条件に従って、論理的な関連テーブルも含みます。</span><span class="sxs-lookup"><span data-stu-id="a2100-136">If you select name-matching criteria on the **Name Matching** page of the wizard, this option also includes logically related tables according to the criteria you select.</span></span> <span data-ttu-id="a2100-137">テーブルには、新しく追加された関連テーブルに関連している場合や、元のテーブルと同一の構造を持つ場合のテーブルも含まれます。</span><span class="sxs-lookup"><span data-stu-id="a2100-137">Tables are also included if they are related to the newly added related tables, and if they have an identical structure to the original table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2100-138">参照</span><span class="sxs-lookup"><span data-stu-id="a2100-138">See Also</span></span>  
 <span data-ttu-id="a2100-139">[データソースビューウィザードの F1 ヘルプ &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a2100-139">[Data Source View Wizard F1 Help &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span></span>  
 [<span data-ttu-id="a2100-140">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="a2100-140">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
