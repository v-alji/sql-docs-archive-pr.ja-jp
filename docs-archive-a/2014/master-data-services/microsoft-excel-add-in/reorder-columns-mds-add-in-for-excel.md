---
title: 列の並べ替え (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f0c47a631ffe699936a8d45bcc4e47e0b6f0a985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714470"
---
# <a name="reorder-columns-mds-add-in-for-excel"></a><span data-ttu-id="34f1a-102">列の並べ替え (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="34f1a-102">Reorder Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="34f1a-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] では、読み込み前に一覧をフィルター処理して列を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="34f1a-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you can reorder columns by filtering the list before loading.</span></span>  
  
 <span data-ttu-id="34f1a-104">**[フィルター]** ダイアログ ボックスの属性を並べ替えると、Excel には新しい順序でデータが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="34f1a-104">When you reorder attributes in the **Filter** dialog box, the data is loaded into Excel with the new order.</span></span> <span data-ttu-id="34f1a-105">しかし、次にその属性データをフィルター処理すると、元のデザインの順序に戻ります。</span><span class="sxs-lookup"><span data-stu-id="34f1a-105">However, the next time that you filter the attribute data, the order will revert to the order in the original design.</span></span> <span data-ttu-id="34f1a-106">順序を完全に変更するには、管理者がマスター データ マネージャーの **[システム管理]** 領域で順序を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34f1a-106">To change the order permanently, an administrator should change the order in the **System Administration** area of Master Data Manager.</span></span> <span data-ttu-id="34f1a-107">詳細については、「 [Change the Order of Attributes](../change-the-order-of-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34f1a-107">For more information, see [Change the Order of Attributes](../change-the-order-of-attributes.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="34f1a-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="34f1a-108">Prerequisites</span></span>  
 <span data-ttu-id="34f1a-109">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="34f1a-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="34f1a-110">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="34f1a-110">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-reorder-mds-managed-columns"></a><span data-ttu-id="34f1a-111">MDS によって管理される列を並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="34f1a-111">To reorder MDS-managed columns</span></span>  
  
1.  <span data-ttu-id="34f1a-112">Excel を開いて、 **[マスター データ]** タブで MDS リポジトリに接続します。</span><span class="sxs-lookup"><span data-stu-id="34f1a-112">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="34f1a-113">詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34f1a-113">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="34f1a-114">**[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="34f1a-114">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="34f1a-115">エンティティの一覧が作成されます。</span><span class="sxs-lookup"><span data-stu-id="34f1a-115">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="34f1a-116">**[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34f1a-116">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="34f1a-117">**[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。</span><span class="sxs-lookup"><span data-stu-id="34f1a-117">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="34f1a-118">ペインを有効にするには、新しいワークシートを開きます。</span><span class="sxs-lookup"><span data-stu-id="34f1a-118">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="34f1a-119">**[マスター データ エクスプローラー]** ペインで、エンティティをクリックします。</span><span class="sxs-lookup"><span data-stu-id="34f1a-119">In the **Master Data Explorer** pane, click an entity.</span></span>  
  
4.  <span data-ttu-id="34f1a-120">**[接続と読み込み]** グループで、 **[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34f1a-120">In the **Connect and Load** group, click **Filter**.</span></span>  
  
5.  <span data-ttu-id="34f1a-121">**[フィルター]** ダイアログ ボックスの **[列]** セクションに表示される属性の一覧で、移動する属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34f1a-121">In the **Filter** dialog box, in the **Columns** section, in the list of attributes, click the attribute you want to move.</span></span>  
  
6.  <span data-ttu-id="34f1a-122">一覧の右側で、 **上** 矢印または **下** 矢印をクリックして、ワークシート内の属性を左右に移動します。</span><span class="sxs-lookup"><span data-stu-id="34f1a-122">To the right of the list, click the **Up** or **Down** arrow to move the attribute left and right in the worksheet.</span></span>  
  
7.  <span data-ttu-id="34f1a-123">ワークシート内で目的の順序 (左から右) となるまで、各属性について手順 7. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="34f1a-123">Repeat step 7 for each attribute until the top-to-bottom order represents the left-to-right order you want in the worksheet.</span></span>  
  
8.  <span data-ttu-id="34f1a-124">**[データの読み込み]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34f1a-124">Click **Load Data**.</span></span> <span data-ttu-id="34f1a-125">MDS によって管理されるデータがシートに入力され、指定した順序で列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="34f1a-125">The sheet is populated with MDS-managed data and the columns are displayed in the order you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f1a-126">参照</span><span class="sxs-lookup"><span data-stu-id="34f1a-126">See Also</span></span>  
 [<span data-ttu-id="34f1a-127">データ &#40;Excel 用 MDS アドインの読み込み&#41;</span><span class="sxs-lookup"><span data-stu-id="34f1a-127">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  
