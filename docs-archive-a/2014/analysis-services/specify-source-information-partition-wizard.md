---
title: 基になる情報の指定 (パーティションウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifydsvandfacttables.f1
ms.assetid: b6c13587-c690-45d9-af90-b3d652afc55b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088a8abf7b143b68766f22af37f8ff4fa2065d65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643510"
---
# <a name="specify-source-information-partition-wizard"></a><span data-ttu-id="09c5c-102">[基になる情報の指定] (パーティション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="09c5c-102">Specify Source Information (Partition Wizard)</span></span>
  <span data-ttu-id="09c5c-103">**[基になる情報の指定]** ページを使用すると、パーティションを作成するメジャー グループと、パーティションのデータ ソース ビューとフィルター テーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="09c5c-103">Use the **Specify Source Information** page to select the measure group in which to create the partition, and also the data source view and filter tables for your partition.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="09c5c-104"> 他のパーティションによって使用される **[使用できるテーブル]** 内のテーブルを指定する場合は、 **[行の制限]** ページ内でクエリを指定するか、キューブ内でリスクの複製データを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09c5c-104">If you specify a table in **Available Tables** that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="09c5c-105">Options</span><span class="sxs-lookup"><span data-stu-id="09c5c-105">Options</span></span>  
 <span data-ttu-id="09c5c-106">**[メジャー グループ]**</span><span class="sxs-lookup"><span data-stu-id="09c5c-106">**Measure group**</span></span>  
 <span data-ttu-id="09c5c-107">このパーティションのメジャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="09c5c-107">Select a measure group for this partition.</span></span>  
  
 <span data-ttu-id="09c5c-108">[**場所**]</span><span class="sxs-lookup"><span data-stu-id="09c5c-108">**Look in**</span></span>  
 <span data-ttu-id="09c5c-109">このパーティションのソース テーブルを含む、データ ソースまたはデータ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="09c5c-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="09c5c-110">メジャー グループによって使用されるデータ ソース ビューが既定で選択されます。</span><span class="sxs-lookup"><span data-stu-id="09c5c-110">The data source view used by the measure group is selected by default.</span></span>  
  
 <span data-ttu-id="09c5c-111">**[フィルター テーブル]**</span><span class="sxs-lookup"><span data-stu-id="09c5c-111">**Filter tables**</span></span>  
 <span data-ttu-id="09c5c-112">**[使用できるテーブル]** に表示されるテーブルを、テーブル名で制限するために使用する文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="09c5c-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="09c5c-113">**テーブルを検索します**</span><span class="sxs-lookup"><span data-stu-id="09c5c-113">**Find tables**</span></span>  
 <span data-ttu-id="09c5c-114">**[使用できるテーブル]** 内のテーブルの一覧を更新します。文字列が **[フィルター テーブル]** で指定された場合は、さらに一覧を制限します。</span><span class="sxs-lookup"><span data-stu-id="09c5c-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="09c5c-115">**[使用できるテーブル]**</span><span class="sxs-lookup"><span data-stu-id="09c5c-115">**Available tables**</span></span>  
 <span data-ttu-id="09c5c-116">テーブルを選択し、パーティションのソース テーブルとして使用します。</span><span class="sxs-lookup"><span data-stu-id="09c5c-116">Select the tables to use as source tables for partitions.</span></span> <span data-ttu-id="09c5c-117">**パーティション ウィザード** により、 **[使用できるテーブル]** で選択したテーブルごとに 1 つのパーティションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="09c5c-117">The **Partition Wizard** creates one partition for each table selected in **Available tables**.</span></span>  
  
 <span data-ttu-id="09c5c-118">**[フィルター テーブル]** でフィルターが指定されていない場合は、 **[検索対象]** で指定されているデータ ソースまたはデータ ソース ビューで、 **[メジャー グループ]** で指定されているメジャー グループが使用するファクト テーブルと同じ構造を持つデータ ソースまたはデータ ソース ビュー内のすべてのテーブルが、このオプションによって一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="09c5c-118">If no filter is specified in **Filter tables**, this option lists all tables in the data source or data source view that are specified in **Look in** and that are similar in structure to the fact table used by the measure group specified in **Measure group**.</span></span>  
  
 <span data-ttu-id="09c5c-119">**[フィルター テーブル]** でフィルターが指定されている場合は、以前の条件に一致するテーブル名に対するフィルターを比較することによってさらにリストが制限されます。</span><span class="sxs-lookup"><span data-stu-id="09c5c-119">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the previous criteria.</span></span> <span data-ttu-id="09c5c-120">**[フィルター テーブル]** で指定された文字列を含むテーブルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="09c5c-120">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09c5c-121">複数のテーブルが選択されている場合は、 **[行の制限]** ページは表示されず、選択したテーブルから作成されるパーティションに対して、行を制限することはできません。</span><span class="sxs-lookup"><span data-stu-id="09c5c-121">If more than one table is selected, the **Restrict Rows** page cannot be displayed and rows cannot be restricted for the partitions created from the selected tables.</span></span> <span data-ttu-id="09c5c-122">パーティションごとに行を制限するには、パーティションを作成するテーブルごとにパーティション ウィザードを 1 回実行します。</span><span class="sxs-lookup"><span data-stu-id="09c5c-122">To restrict rows for each partition, run the Partition Wizard once for each table from which a partition is to be created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c5c-123">参照</span><span class="sxs-lookup"><span data-stu-id="09c5c-123">See Also</span></span>  
 [<span data-ttu-id="09c5c-124">パーティション (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="09c5c-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
