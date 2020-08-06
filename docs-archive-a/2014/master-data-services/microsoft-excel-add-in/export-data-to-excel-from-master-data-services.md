---
title: MDS から Excel にデータを読み込む |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 35672807d5bb108e9386f892aea1847d45ebeb33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715482"
---
# <a name="load-data-from-mds-into-excel"></a><span data-ttu-id="6234f-102">MDS から Excel へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="6234f-102">Load Data from MDS into Excel</span></span>
  <span data-ttu-id="6234f-103">では、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] データを操作するために、MDS リポジトリからデータを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6234f-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository in order to work with it.</span></span>  
  
 <span data-ttu-id="6234f-104">読み込み前にデータセットをフィルター処理する場合は、「 [Excel 用 MDS アドイン&#41;を読み込む前にデータをフィルター処理する &#40;](filter-data-before-exporting-mds-add-in-for-excel.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6234f-104">If you want to filter the dataset before loading, see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) instead.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6234f-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="6234f-105">Prerequisites</span></span>  
 <span data-ttu-id="6234f-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="6234f-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="6234f-107">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6234f-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-load-data-from-mds-into-excel"></a><span data-ttu-id="6234f-108">MDS から Excel にデータを読み込むには</span><span class="sxs-lookup"><span data-stu-id="6234f-108">To load data from MDS into Excel</span></span>  
  
1.  <span data-ttu-id="6234f-109">Excel を開いて、 **[マスター データ]** タブで MDS リポジトリに接続します。</span><span class="sxs-lookup"><span data-stu-id="6234f-109">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="6234f-110">詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6234f-110">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="6234f-111">**[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="6234f-111">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="6234f-112">エンティティの一覧が作成されます。</span><span class="sxs-lookup"><span data-stu-id="6234f-112">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="6234f-113">**[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6234f-113">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="6234f-114">**[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。</span><span class="sxs-lookup"><span data-stu-id="6234f-114">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="6234f-115">ペインを有効にするには、新しいワークシートを開きます。</span><span class="sxs-lookup"><span data-stu-id="6234f-115">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="6234f-116">**[マスター データ エクスプローラー]** ペインのエンティティの一覧で、読み込むエンティティをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6234f-116">In the **Master Data Explorer** pane, in the list of entities, double-click the entity you want to load.</span></span>  
  
    > [!NOTE]  
    >  -   <span data-ttu-id="6234f-117">最初の 100 万個のメンバーだけが Excel に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6234f-117">Only the first one million members are loaded into Excel.</span></span> <span data-ttu-id="6234f-118">読み込む前に一覧をフィルター処理するには、リボンの **[接続と読み込み]** グループで、 **[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6234f-118">To filter the list before loading, on the ribbon in the **Connect and Load** group, click **Filter**.</span></span>  
    > -   <span data-ttu-id="6234f-119">制約リスト (ドメイン ベースの属性) である列では、最初の 25,000 個の値だけが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6234f-119">In columns that are constrained lists (domain-based attributes), only the first 25,000 values are loaded.</span></span> <span data-ttu-id="6234f-120">この数値は、Excel がインストールされているコンピューターにある、excelusersettings.config ファイルの MaximumDbaEntitySize プロパティで変更できます。</span><span class="sxs-lookup"><span data-stu-id="6234f-120">You can change this number in the MaximumDbaEntitySize property in the excelusersettings.config file located on the computer that Excel is installed on.</span></span> <span data-ttu-id="6234f-121">このファイルは、C:\Users \\<user \> \AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="6234f-121">This file is located in C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices\\.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6234f-122">32 ビットの Excel で Microsoft Excel 用アドインを使用して、テキスト区切りのデータを読み込み、 **[ロードするセル数]** プロパティと **[パブリッシュするセル数]** プロパティの設定が両方とも最大値の 1000 に設定されている場合、メモリ不足エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6234f-122">When you load text-delimited data using the Add-in for Microsoft Excel with 32-bit Excel, and the settings for the **Cell Count to Load** and **Cell Count to Publish** properties are both set to the maximum of 1000, an out-of-memory error will occur.</span></span> <span data-ttu-id="6234f-123">**[ロードするセル数]** および **[パブリッシュするセル数]** に最大値を設定するには、64 ビットの Excel を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6234f-123">You have to use 64-bit Excel to use the maximum settings for **Cell Count to Load** and **Cell Count to Publish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6234f-124">次の手順</span><span class="sxs-lookup"><span data-stu-id="6234f-124">Next Steps</span></span>  
 [<span data-ttu-id="6234f-125">Excel から MDS へのデータのパブリッシュ &#40;Excel 用 MDS アドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="6234f-125">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="6234f-126">参照</span><span class="sxs-lookup"><span data-stu-id="6234f-126">See Also</span></span>  
 <span data-ttu-id="6234f-127">[データ &#40;Excel 用 MDS アドインの読み込み&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6234f-127">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="6234f-128">[[フィルター] ダイアログボックス &#40;Excel 用 MDS アドイン&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6234f-128">[Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="6234f-129">データ &#40;Excel 用 MDS アドインの公開&#41;</span><span class="sxs-lookup"><span data-stu-id="6234f-129">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
