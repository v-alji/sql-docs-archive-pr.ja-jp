---
title: 読み込み前にデータをフィルター処理する (Excel 用 MDS アドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6d0ccf667f37763326e27dcd8d0cfc005627ebc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715481"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a><span data-ttu-id="7234b-102">読み込み前のデータのフィルター処理 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="7234b-102">Filter Data before Loading (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="7234b-103">で [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 、Excel に読み込むデータのサイズまたは範囲を制限する場合は、データをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="7234b-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filter data when you want to limit the size or scope of data that you are loading into Excel.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7234b-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="7234b-104">Prerequisites</span></span>  
 <span data-ttu-id="7234b-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="7234b-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7234b-106">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7234b-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-filter-data-before-loading"></a><span data-ttu-id="7234b-107">読み込み前にデータをフィルター処理するには</span><span class="sxs-lookup"><span data-stu-id="7234b-107">To filter data before loading</span></span>  
  
1.  <span data-ttu-id="7234b-108">Excel を開いて、 **[マスター データ]** タブで MDS リポジトリに接続します。</span><span class="sxs-lookup"><span data-stu-id="7234b-108">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="7234b-109">詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7234b-109">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="7234b-110">**[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7234b-110">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="7234b-111">エンティティの一覧が作成されます。</span><span class="sxs-lookup"><span data-stu-id="7234b-111">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="7234b-112">**[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7234b-112">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="7234b-113">**[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。</span><span class="sxs-lookup"><span data-stu-id="7234b-113">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="7234b-114">ペインを有効にするには、新しいワークシートを開きます。</span><span class="sxs-lookup"><span data-stu-id="7234b-114">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="7234b-115">**[マスター データ エクスプローラー]** ペインのエンティティの一覧で、フィルター処理するエンティティをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7234b-115">In the **Master Data Explorer** pane, in the list of entities, click the entity you want to filter.</span></span>  
  
4.  <span data-ttu-id="7234b-116">リボンの **[接続と読み込み]** グループで、 **[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7234b-116">On the ribbon, in the **Connect and Load** group, click **Filter**.</span></span>  
  
5.  <span data-ttu-id="7234b-117">**[フィルター]** ダイアログ ボックスで、表示する属性 (列) を選択して列の順序を設定し、必要に応じて、返される行が少なくなるようにデータをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="7234b-117">Complete the **Filter** dialog box by selecting the attributes (columns) to display, setting the order of the columns, and if needed, filtering the data so fewer rows are returned.</span></span> <span data-ttu-id="7234b-118">**[概要]** ペインで、返されるデータ量を確認します。</span><span class="sxs-lookup"><span data-stu-id="7234b-118">View the **Summary** pane for how much data will be returned.</span></span> <span data-ttu-id="7234b-119">詳細については、「[[フィルター] ダイアログ ボックス (Excel 用 MDS アドイン)](filter-dialog-box-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7234b-119">For more information, see [Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md).</span></span>  
  
6.  <span data-ttu-id="7234b-120">**[データの読み込み]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7234b-120">Click **Load Data**.</span></span> <span data-ttu-id="7234b-121">シートに MDS によって管理されるデータが入力されます。</span><span class="sxs-lookup"><span data-stu-id="7234b-121">The sheet is populated with MDS-managed data.</span></span>  
  
    > [!NOTE]  
    >  -   <span data-ttu-id="7234b-122">最初の 100 万個のメンバーだけが Excel に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7234b-122">Only the first one million members are loaded into Excel.</span></span>  
    > -   <span data-ttu-id="7234b-123">制約リスト (ドメインベースの属性) の列では、最初の1000値のみが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7234b-123">In columns that are constrained lists (domain-based attributes), only the first 1000 values are loaded.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7234b-124">次の手順</span><span class="sxs-lookup"><span data-stu-id="7234b-124">Next Steps</span></span>  
 [<span data-ttu-id="7234b-125">Excel から MDS へのデータのパブリッシュ &#40;Excel 用 MDS アドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="7234b-125">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="7234b-126">参照</span><span class="sxs-lookup"><span data-stu-id="7234b-126">See Also</span></span>  
 <span data-ttu-id="7234b-127">[データ &#40;Excel 用 MDS アドインの読み込み&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="7234b-127">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="7234b-128">[[フィルター] ダイアログボックス &#40;Excel 用 MDS アドイン&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="7234b-128">[Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="7234b-129">列の並べ替え (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="7234b-129">Reorder Columns &#40;MDS Add-in for Excel&#41;</span></span>](reorder-columns-mds-add-in-for-excel.md)  
  
  
