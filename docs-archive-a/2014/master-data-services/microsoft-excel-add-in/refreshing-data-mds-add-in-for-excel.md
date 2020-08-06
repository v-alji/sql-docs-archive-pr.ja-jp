---
title: データの更新 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 58dbe99a-288d-4f1c-9cd5-704d6836c945
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 49b6e7bc19c41911c626965b9d1de132796367f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741113"
---
# <a name="refreshing-data-mds-add-in-for-excel"></a><span data-ttu-id="8496c-102">データの更新 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="8496c-102">Refreshing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="8496c-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、MDS リポジトリから最新の情報を取得する必要があるときに、新しいワークシートを開くことなくデータを更新できます。</span><span class="sxs-lookup"><span data-stu-id="8496c-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], refresh data when you want to get the latest information from the MDS repository without opening a new worksheet.</span></span> <span data-ttu-id="8496c-104">すべてのセルを更新することも、選択したセルだけを更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="8496c-104">You can refresh either all cells or a selection of cells.</span></span> <span data-ttu-id="8496c-105">これは、カスタム式や MDS で管理されないその他のデータを含む列を挿入し、そのデータを保存する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8496c-105">This can be useful when you have inserted columns with custom formulas or other data that is not managed in MDS and you want to preserve it.</span></span>  
  
## <a name="when-you-can-refresh-mds-managed-data"></a><span data-ttu-id="8496c-106">MDS によって管理されるデータを更新できる場合</span><span class="sxs-lookup"><span data-stu-id="8496c-106">When You Can Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="8496c-107">アクティブなワークシートに MDS によって管理されるデータが既に含まれている場合、アクティブなワークシート内の MDS によって管理されるデータを更新できます。</span><span class="sxs-lookup"><span data-stu-id="8496c-107">You can refresh MDS-managed data in an active worksheet if the active worksheet already contains MDS-managed data.</span></span> <span data-ttu-id="8496c-108">属性値を変更した場合や、メンバーをワークシートに追加した場合は、更新する前に変更をパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8496c-108">If you have changed attribute values or added members to the worksheet, you must publish your changes before you can refresh.</span></span>  
  
## <a name="refreshing-a-selection"></a><span data-ttu-id="8496c-109">選択範囲の更新</span><span class="sxs-lookup"><span data-stu-id="8496c-109">Refreshing a Selection</span></span>  
 <span data-ttu-id="8496c-110">すべてのセルを更新するか、選択したセルだけを更新するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8496c-110">You have the choice of refreshing all cells or refreshing only selected cells.</span></span> <span data-ttu-id="8496c-111">選択するセルは連続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8496c-111">The selected cells must be contiguous.</span></span> <span data-ttu-id="8496c-112">連続した一連のセルが選択されると、そのセット内にある MDS によって管理されるセルは、サーバー上に現在格納されている値を表示するために更新されます。</span><span class="sxs-lookup"><span data-stu-id="8496c-112">If a set of contiguous cells is selected, all MDS managed cells in that set will be updated to display the values currently stored on the server.</span></span> <span data-ttu-id="8496c-113">MDS によって管理されていない未変更の行および列は、まったく影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="8496c-113">Unchanged rows and columns that are not managed by MDS are not affected in any way.</span></span>  
  
## <a name="what-happens-when-you-refresh-mds-managed-data"></a><span data-ttu-id="8496c-114">MDS によって管理されるデータを更新したときの処理</span><span class="sxs-lookup"><span data-stu-id="8496c-114">What Happens When You Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="8496c-115">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]でデータを更新したときに、シート内の MDS によって管理されるデータがどのように処理されるかは、データを最後に読み込んだ後に MDS リポジトリで行った変更の内容によります。</span><span class="sxs-lookup"><span data-stu-id="8496c-115">When you refresh data in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], what happens to the MDS-managed data in the sheet depends on what has changed in the MDS repository since you last loaded the data.</span></span>  
  
-   <span data-ttu-id="8496c-116">新しいメンバーをリポジトリに追加した場合は、そのメンバーがワークシートの末尾に追加され、緑色で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="8496c-116">If new members have been added to repository, they are added to the end of the worksheet and are highlighted in green.</span></span>  
  
-   <span data-ttu-id="8496c-117">リポジトリからメンバーを削除した場合は、そのメンバーがワークシートから削除されます。</span><span class="sxs-lookup"><span data-stu-id="8496c-117">If members were deleted from the repository, they are deleted from the worksheet.</span></span>  
  
-   <span data-ttu-id="8496c-118">MDS リポジトリで属性値を変更した場合は、MDS リポジトリのその値を使用して、ワークシート内の値が更新されます。</span><span class="sxs-lookup"><span data-stu-id="8496c-118">If an attribute value has changed in the MDS repository, the value in the worksheet is updated with value from the MDS repository.</span></span> <span data-ttu-id="8496c-119">セルの色は変化しません。</span><span class="sxs-lookup"><span data-stu-id="8496c-119">The cell color does not change.</span></span>  
  
> [!WARNING]
>  -   <span data-ttu-id="8496c-120">アクティブなワークシートで、MDS によって管理されるデータ下の行に管理されないデータが存在する場合、管理されないデータが上書きされることがあります。</span><span class="sxs-lookup"><span data-stu-id="8496c-120">In the active worksheet, if non-managed data exists in rows beneath the MDS-managed data, the non-managed data may be overwritten.</span></span> <span data-ttu-id="8496c-121">これは、シートを更新して、管理されないデータと重複する、MDS によって管理されるデータの新しい行を追加した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="8496c-121">This occurs when you refresh the sheet and new rows of MDS-managed data, which overlap with the non-managed data, are added.</span></span>  
> -   <span data-ttu-id="8496c-122">更新すると、MDS によって管理されるセルのコメントは削除されます。</span><span class="sxs-lookup"><span data-stu-id="8496c-122">When you refresh, comments on MDS-managed cells are deleted.</span></span>  
  
## <a name="how-to-refresh-mds-managed-data"></a><span data-ttu-id="8496c-123">MDS によって管理されるデータを更新する方法</span><span class="sxs-lookup"><span data-stu-id="8496c-123">How to Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="8496c-124">リボンの **[接続と読み込み]** グループの **[更新]** ボタンには、 **[すべて更新]** と **[選択範囲を更新]** の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="8496c-124">In the **Connect and Load** group on the ribbon, the **Refresh** button has two options, **Refresh All** and **Refresh Selection**.</span></span> <span data-ttu-id="8496c-125">このリボン ボタンの既定アクションは、 **[すべて更新]** です。</span><span class="sxs-lookup"><span data-stu-id="8496c-125">The default action of the ribbon button is **Refresh All**.</span></span> <span data-ttu-id="8496c-126">シート全体をサーバーの値に更新するには、 **[更新]** ボタンをクリックするか、 **[すべて更新]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="8496c-126">To refresh the entire sheet with values from the server, click the **Refresh** button or choose the **Refresh All** option.</span></span> <span data-ttu-id="8496c-127">シート内のいくつかのセルのみを更新するには、該当するセルを選択し (1 つの連続する範囲である必要があります)、 **[選択範囲を更新]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="8496c-127">To refresh only some of the cells in a sheet, select the cells (must be one contiguous selection) and choose the **Refresh Selection** option.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8496c-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8496c-128">Related Tasks</span></span>  
  
|<span data-ttu-id="8496c-129">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="8496c-129">Task Description</span></span>|<span data-ttu-id="8496c-130">トピック</span><span class="sxs-lookup"><span data-stu-id="8496c-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="8496c-131">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="8496c-131">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="8496c-132">MDS リポジトリへの接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="8496c-132">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="8496c-133">MDS データを Excel に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8496c-133">Load MDS data into Excel.</span></span>|[<span data-ttu-id="8496c-134">MDS から Excel へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="8496c-134">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="8496c-135">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="8496c-135">Related Content</span></span>  
  
-   [<span data-ttu-id="8496c-136">接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="8496c-136">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="8496c-137">データ &#40;Excel 用 MDS アドインの読み込み&#41;</span><span class="sxs-lookup"><span data-stu-id="8496c-137">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="8496c-138">Microsoft Excel 用マスター データ サービス アドイン</span><span class="sxs-lookup"><span data-stu-id="8496c-138">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
