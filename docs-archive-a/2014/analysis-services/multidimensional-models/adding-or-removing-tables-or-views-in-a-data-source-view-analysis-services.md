---
title: データソースビューでのテーブルまたはビューの追加または削除 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
author: minewiskan
ms.author: owend
ms.openlocfilehash: da1bc2b1ac0af7576cfe3c3593b451f78d6a9fae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645219"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a><span data-ttu-id="a3b58-102">データ ソース ビューでのテーブルまたはビューの追加または削除 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a3b58-102">Adding or Removing Tables or Views in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="a3b58-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でデータ ソース ビュー (DSV) を作成したら、テーブルおよび列を追加または削除することにより、データ ソース ビュー デザイナーでそれを変更できます。これには、別のデータ ソースからのテーブルと列の追加と削除も含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-103">After you have created a data source view (DSV) in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can modify it in Data Source View Designer by adding or removing tables and columns, including tables and columns from another data source.</span></span>  
  
 <span data-ttu-id="a3b58-104">データ ソース ビュー デザイナーで DSV を開くには、ソリューション エクスプローラーで DSV をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3b58-104">To open the DSV in Data Source View Designer, you double-click the DSV in Solution Explorer.</span></span> <span data-ttu-id="a3b58-105">DSV を開いたら、ボタン バーまたはメニューにある **[テーブルの追加と削除]** を使用して DSV を変更または拡張できます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-105">Once you open the DSV, you can use the **Add/Remove Tables** command on the button bar or menu to modify or extend the DSV.</span></span> <span data-ttu-id="a3b58-106">さらに、ダイアグラム内のオブジェクトを操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-106">You can also work with the objects in the diagram.</span></span> <span data-ttu-id="a3b58-107">たとえば、オブジェクトを選択して、キーボードの Del キーを使用してそのオブジェクトを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-107">For example, you can select an object and then use the Delete key on your keyboard to remove an object.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a3b58-108">テーブルの削除は注意して行ってください。</span><span class="sxs-lookup"><span data-stu-id="a3b58-108">Use caution when removing a table.</span></span> <span data-ttu-id="a3b58-109">テーブルを削除すると、関連する列およびリレーションシップのすべてが DSV から削除され、そのテーブルにバインドされているすべてのオブジェクトが無効になります。</span><span class="sxs-lookup"><span data-stu-id="a3b58-109">Removing a table deletes all the associated columns and relationships from the DSV and invalidates all objects bound to that table.</span></span>  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a><span data-ttu-id="a3b58-110">追加または削除するテーブルまたはビューの選択</span><span class="sxs-lookup"><span data-stu-id="a3b58-110">Selecting Tables or Views to Add or Remove</span></span>  
 <span data-ttu-id="a3b58-111">**[テーブルの追加と削除]** ダイアログ ボックスを使用すると、 **[使用できるオブジェクト]** ボックスの一覧と **[含まれているオブジェクト]** ボックスの一覧の間でテーブルまたはビューを移動できます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-111">Using the **Add/Remove Tables** dialog box, you can move tables or views between the **Available objects** and **Included objects** lists.</span></span> <span data-ttu-id="a3b58-112">初期の **[使用できるオブジェクト]** ボックスの一覧には、まだデータ ソース ビューにないプライマリ データ ソースのテーブルまたはビューが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3b58-112">The **Available objects** list initially includes any tables or views in the primary data source that are not already in the data source view.</span></span> <span data-ttu-id="a3b58-113">プライマリ データ ソースが `OPENROWSET` 機能をサポートしている場合は、プロジェクトまたはデータベースの他のデータ ソースからテーブルまたはビューを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-113">If the primary data source supports the `OPENROWSET` function, you can also add tables or views from other data sources in the project or database.</span></span>  
  
 <span data-ttu-id="a3b58-114">DSV でのテーブルの追加または削除により、DSV で現在選択されているダイアグラムでもそのテーブルが追加または削除されます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-114">Adding or removing a table to the DSV also adds or removes the table to the currently selected diagram in the DSV.</span></span> <span data-ttu-id="a3b58-115">ダイアグラムの詳細については、「 [データ ソース ビュー デザイナーでのダイアグラムの操作 &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3b58-115">For more information on diagrams, see [Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md).</span></span>  
  
 <span data-ttu-id="a3b58-116">**[テーブルの追加と削除]** ダイアログ ボックスの **[含まれているオブジェクト]** ボックスの一覧にテーブルを移動すると、関連テーブルもすべて追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a3b58-116">After you move a table to the **Included objects** list in the **Add/Remove Tables** dialog box, you can add all related tables.</span></span> <span data-ttu-id="a3b58-117">データ ソース内に外部キー制約が存在する場合は、この操作により、制約に従ってテーブルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="a3b58-117">This operation adds tables according to foreign key constraints in the data source, if such constraints exist.</span></span> <span data-ttu-id="a3b58-118">外部キー制約が存在しない場合は、データ ソース ビューの `NameMatchingCriteria` プロパティを使用して、リレーションシップを指定できます。指定するには、テーブル内の列名の一致基準を指定してリレーションシップを生成します。</span><span class="sxs-lookup"><span data-stu-id="a3b58-118">If foreign key constraints do not exist, you can use the `NameMatchingCriteria` property of the data source view to determine relationships by specifying a criterion for matching column names in tables to generate likely relationships.</span></span> <span data-ttu-id="a3b58-119">`NameMatchingCriteria`データソースビューに対してプロパティが指定されている場合は、[**関連テーブルの追加**] をクリックして、一致する列名を持つデータソースからテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3b58-119">If the `NameMatchingCriteria`property is specified for the data source view, click **Add Related Tables** to add tables from the data source that have matching column names.</span></span> <span data-ttu-id="a3b58-120">プロパティの設定の詳細については `NameMatchingCriteria` 、「[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3b58-120">For more information about setting the `NameMatchingCriteria` property, see [Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3b58-121">データ ソース ビューでオブジェクトの追加や削除を行っても、基になるデータ ソースは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="a3b58-121">Adding or removing objects in a data source view does not affect the underlying data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b58-122">参照</span><span class="sxs-lookup"><span data-stu-id="a3b58-122">See Also</span></span>  
 <span data-ttu-id="a3b58-123">[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a3b58-123">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="a3b58-124">データ ソース ビュー デザイナーでのダイアグラムの操作 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a3b58-124">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
