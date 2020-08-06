---
title: テーブルバインドの詳細 ([パーティションソース] ダイアログボックス) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10845e18a2b7c74a8ed3aeec42f710b9706dc94a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639681"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="e9f3b-102">テーブル バインドの詳細 ([パーティション ソース] ダイアログ ボックス) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="e9f3b-102">Table Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e9f3b-103">**[パーティション ソース]** ダイアログ ボックスの **[テーブル バインド]** オプションを使用すると、パーティション用のデータを提供するファクト テーブルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-103">Use the **Table Binding** option in the **Partition Source** dialog box to specify the fact table that provides the data for the partition.</span></span> <span data-ttu-id="e9f3b-104">このペインを表示するには、 **[パーティション ソース]** ダイアログ ボックスの **[バインドの種類]** オプションで **[テーブル バインド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-104">You can display this pane by selecting **Table Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e9f3b-105">Options</span><span class="sxs-lookup"><span data-stu-id="e9f3b-105">Options</span></span>  
 <span data-ttu-id="e9f3b-106">**[メジャー グループ]**</span><span class="sxs-lookup"><span data-stu-id="e9f3b-106">**Measure group**</span></span>  
 <span data-ttu-id="e9f3b-107">このパーティションのメジャー グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-107">Displays the measure group for this partition.</span></span>  
  
 <span data-ttu-id="e9f3b-108">[**場所**]</span><span class="sxs-lookup"><span data-stu-id="e9f3b-108">**Look in**</span></span>  
 <span data-ttu-id="e9f3b-109">このパーティションのソース テーブルを含む、データ ソースまたはデータ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="e9f3b-110">既定では、選択したメジャー グループで使用されているデータ ソース ビューが選択されています。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-110">The data source view used by the selected measure group is selected by default.</span></span>  
  
 <span data-ttu-id="e9f3b-111">**[フィルター テーブル]**</span><span class="sxs-lookup"><span data-stu-id="e9f3b-111">**Filter tables**</span></span>  
 <span data-ttu-id="e9f3b-112">**[使用できるテーブル]** に表示されるテーブルを、テーブル名で制限するために使用する文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="e9f3b-113">**テーブルを検索します**</span><span class="sxs-lookup"><span data-stu-id="e9f3b-113">**Find tables**</span></span>  
 <span data-ttu-id="e9f3b-114">**[使用できるテーブル]** 内のテーブルの一覧を更新します。文字列が **[フィルター テーブル]** で指定された場合は、さらに一覧を制限します。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="e9f3b-115">**[使用できるテーブル]**</span><span class="sxs-lookup"><span data-stu-id="e9f3b-115">**Available tables**</span></span>  
 <span data-ttu-id="e9f3b-116">クリックして、パーティション用のソース テーブルとして使用するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-116">Click to select the table to use as a source table for the partition.</span></span>  
  
 <span data-ttu-id="e9f3b-117">**[フィルター テーブル]** でフィルターが指定されていない場合、 **[検索対象]** で指定したデータ ソースまたはデータ ソース ビューのすべてのテーブルが一覧表示されます。このテーブルの構造は、 **[メジャー グループ]** で指定したメジャー グループで使用されるファクト テーブルに類似しています。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-117">If no filter is specified in **Filter tables**, all tables in the data source or data source view specified in **Look in** that are similar in structure to the fact table used by the measure group specified in **Measure group** are listed.</span></span>  
  
 <span data-ttu-id="e9f3b-118">**[フィルター テーブル]** でフィルターが指定されている場合、その条件を満たすテーブル名と比較され、一覧がさらに限定されます。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-118">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the above criteria.</span></span> <span data-ttu-id="e9f3b-119">**[フィルター テーブル]** で指定された文字列を含むテーブルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9f3b-119">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f3b-120">参照</span><span class="sxs-lookup"><span data-stu-id="e9f3b-120">See Also</span></span>  
 <span data-ttu-id="e9f3b-121">[[パーティションソース] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="e9f3b-121">[Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
