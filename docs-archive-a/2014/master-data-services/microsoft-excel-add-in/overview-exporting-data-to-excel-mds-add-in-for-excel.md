---
title: データを読み込んでいます (Excel 用 MDS アドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c01bbbc90fcc68c3de976332721b69ad26e606e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645139"
---
# <a name="loading-data-mds-add-in-for-excel"></a><span data-ttu-id="d1ecc-102">データの読み込み (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="d1ecc-102">Loading Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="d1ecc-103">では、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 作業する前に、MDS リポジトリからアクティブな Excel ワークシートにデータを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository into an active Excel worksheet before you can work with it.</span></span> <span data-ttu-id="d1ecc-104">データの操作が完了したら、そのデータを他のユーザーが共有できるように MDS リポジトリにパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-104">When you are done working with the data, publish it to the MDS repository so other users can share it.</span></span>  
  
 <span data-ttu-id="d1ecc-105">読み込むことができるデータは、アクセスする権限があるデータに限定されます。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-105">The data you can load is limited to the data you have permission to access.</span></span> <span data-ttu-id="d1ecc-106">データにアクセスする権限は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションで設定するか、プログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-106">Permission to access data is set in the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application or set programmatically.</span></span>  
  
 <span data-ttu-id="d1ecc-107">大量のデータを読み込む場合は、読み込みに長時間かかる可能性があるデータのときに表示される警告を設定できます。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-107">When you load large amounts of data, you can set warnings that are displayed when the data that might take a long time to load.</span></span> <span data-ttu-id="d1ecc-108">この操作を行うには、 **[オプション]** グループの **[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-108">To do this, in the **Options** group, click **Settings**.</span></span> <span data-ttu-id="d1ecc-109">**[データ]** タブで、 **[大きなデータ セットの場合にフィルター警告を表示する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-109">On the **Data** tab, select the **Display filter warning for large data sets**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d1ecc-110">MDS が有効なブックは、Excel 用 MDS アドインを使用している Excel でのみ開き、更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-110">An MDS-enabled workbook must be opened and updated only in Excel with the MDS Add-in for Excel.</span></span> <span data-ttu-id="d1ecc-111">MDS Excel アドインがインストールされていないコンピューター上の Excel で、MDS が有効なブックを開くことはサポートされていませんし、ブック ファイルを破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-111">Opening an MDS-enabled workbook in Excel on a computer in which the MDS Excel Add-in is not installed is not supported, and could cause corruption of the workbook file.</span></span> <span data-ttu-id="d1ecc-112">他のユーザーとデータを共有したい場合は、ワークシートを保存して電子メールで送信するのではなく、ショートカット クエリ ファイルをそのユーザーに電子メールで送信します。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-112">If you want to share data with someone else, email a shortcut query file to them, rather than saving the worksheet and emailing it.</span></span> <span data-ttu-id="d1ecc-113">クエリの詳細については、「[ショートカット クエリ ファイルの電子メールでの送信 (Excel 用 MDS アドイン)](email-a-shortcut-query-file-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-113">For more information on the query, see [Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).</span></span>  
  
## <a name="filtering-data"></a><span data-ttu-id="d1ecc-114">データのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="d1ecc-114">Filtering Data</span></span>  
 <span data-ttu-id="d1ecc-115">読み込む前にデータをフィルター処理して、ダウンロードするデータの量を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-115">You can filter data before loading to limit the amount of data that you're going to download.</span></span> <span data-ttu-id="d1ecc-116">これには、読み込む属性 (列)、属性を表示する順序、および使用するメンバー (データ行) の選択が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-116">This includes choosing which attributes (columns) you want to load, the order you want to display the attributes, and the members (rows of data) you want to work with.</span></span> <span data-ttu-id="d1ecc-117">詳細については、「 [&#40;Excel 用 MDS アドイン&#41;を読み込む前にデータをフィルター処理する](filter-data-before-exporting-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-117">For more info see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="d1ecc-118">自動接続とよく使用するデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="d1ecc-118">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="d1ecc-119">常に同じサーバーに接続して同じデータ セットを読み込む場合は、接続およびフィルター情報を含むショートカット クエリ ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-119">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="d1ecc-120">クエリ ファイルの詳細については、「 [ショートカット クエリ ファイル (Excel 用 MDS アドイン)](shortcut-query-files-mds-add-in-for-excel.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-120">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="refreshing-data"></a><span data-ttu-id="d1ecc-121">データの更新</span><span class="sxs-lookup"><span data-stu-id="d1ecc-121">Refreshing Data</span></span>  
 <span data-ttu-id="d1ecc-122">MDS リポジトリのデータは、読み込んだ後に他のユーザーによって更新される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-122">Data in the MDS repository may be updated by other users after you load it.</span></span> <span data-ttu-id="d1ecc-123">このようなデータを取得しても、MDS データ以外のデータに加えた変更は失われません。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-123">You can retrieve this data without losing changes you've made to non-MDS data.</span></span> <span data-ttu-id="d1ecc-124">詳細については、「[データの更新 (Excel 用 MDS アドイン)](refreshing-data-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-124">For more information, see [Refreshing Data &#40;MDS Add-in for Excel&#41;](refreshing-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d1ecc-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d1ecc-125">Related Tasks</span></span>  
  
|<span data-ttu-id="d1ecc-126">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="d1ecc-126">Task Description</span></span>|<span data-ttu-id="d1ecc-127">トピック</span><span class="sxs-lookup"><span data-stu-id="d1ecc-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="d1ecc-128">Excel に読み込む前に MDS データをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-128">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="d1ecc-129">&#40;Excel 用 MDS アドインを読み込む前にデータをフィルター処理する&#41;</span><span class="sxs-lookup"><span data-stu-id="d1ecc-129">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|<span data-ttu-id="d1ecc-130">MDS データを Excel に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-130">Load MDS data into Excel.</span></span>|[<span data-ttu-id="d1ecc-131">MDS から Excel へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="d1ecc-131">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="d1ecc-132">データをダウンロードする前に列の順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="d1ecc-132">Change the order of columns before you download data.</span></span>|[<span data-ttu-id="d1ecc-133">列の並べ替え (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="d1ecc-133">Reorder Columns &#40;MDS Add-in for Excel&#41;</span></span>](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="d1ecc-134">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="d1ecc-134">Related Content</span></span>  
  
-   [<span data-ttu-id="d1ecc-135">接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="d1ecc-135">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="d1ecc-136">ショートカット クエリ ファイル (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="d1ecc-136">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="d1ecc-137">Microsoft Excel 用マスター データ サービス アドイン</span><span class="sxs-lookup"><span data-stu-id="d1ecc-137">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="d1ecc-138">セキュリティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d1ecc-138">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  
