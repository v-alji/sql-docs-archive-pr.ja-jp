---
title: 接続 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4dc41afc6dd59cade9e75475c7cb914d14a8937
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631132"
---
# <a name="connections-mds-add-in-for-excel"></a><span data-ttu-id="ea0fb-102">接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="ea0fb-102">Connections (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="ea0fb-103">データを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]にダウンロードするには、まず接続を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-103">To download data in to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must first create a connection.</span></span> <span data-ttu-id="ea0fb-104">接続とは、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスがどの MDS データベースに接続するかを認識する方法です。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-104">A connection is how the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service knows which MDS database to connect to.</span></span>  
  
 <span data-ttu-id="ea0fb-105">通常、接続文字列は [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL (http://contoso/mds など) です。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-105">The connection string is usually the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
 <span data-ttu-id="ea0fb-106">Excel を起動するたびに、MDS リポジトリに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-106">Each time you start Excel, you must connect to an MDS repository.</span></span> <span data-ttu-id="ea0fb-107">ただし、アクティブなワークシートに MDS によって管理されるデータが既に含まれている場合だけは例外です。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-107">The only exception is when the active spreadsheet already contains MDS-managed data.</span></span> <span data-ttu-id="ea0fb-108">この場合は、シート内のデータを更新またはパブリッシュするたびに接続が自動的に確立されます。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-108">In this case, a connection is automatically made each time you refresh or publish data in the sheet.</span></span>  
  
 <span data-ttu-id="ea0fb-109">複数の接続を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-109">You can create multiple connections.</span></span> <span data-ttu-id="ea0fb-110">最後にアクセスした接続が既定と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-110">The most recently-accessed connection is considered the default.</span></span>  
  
 <span data-ttu-id="ea0fb-111">複数のユーザーが同時に接続できます。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-111">Multiple users can be connected at the same time.</span></span> <span data-ttu-id="ea0fb-112">ただし、複数のユーザーが同じデータをパブリッシュしようとすると競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-112">However, conflicts can arise when multiple users attempt to publish the same data.</span></span> <span data-ttu-id="ea0fb-113">詳細については、「[データ &#40;Excel 用 MDS アドイン&#41;のパブリッシュ](overview-importing-data-from-excel-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-113">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="ea0fb-114">自動接続とよく使用するデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="ea0fb-114">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="ea0fb-115">常に同じサーバーに接続して同じデータ セットを読み込む場合は、接続およびフィルター情報を含むショートカット クエリ ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-115">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="ea0fb-116">クエリ ファイルの詳細については、「 [ショートカット クエリ ファイル (Excel 用 MDS アドイン)](shortcut-query-files-mds-add-in-for-excel.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-116">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="data-quality-services"></a><span data-ttu-id="ea0fb-117">Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="ea0fb-117">Data Quality Services</span></span>  
 <span data-ttu-id="ea0fb-118">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] には、MDS リポジトリにパブリッシュする前にデータを照合するための Data Quality Services 機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-118">The [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] has Data Quality Services functionality to help you match data before publishing it to the MDS repository.</span></span> <span data-ttu-id="ea0fb-119">接続時に、DQS データベースが MDS データベースと同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにインストールされている場合は、リボンに DQS ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-119">When you make a connection, if a DQS database is installed on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the MDS database, you will be able to view DQS buttons on the ribbon.</span></span> <span data-ttu-id="ea0fb-120">DQS_Main データベースがインスタンスに存在しない場合、DQS ボタンは表示されず、データ品質機能を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-120">If the DQS_Main database does not exist on the instance, these buttons are not displayed and data quality functionality is not available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="ea0fb-121">接続のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ea0fb-121">Troubleshooting Connections</span></span>  
 <span data-ttu-id="ea0fb-122">MDS に接続するときに問題が発生した場合は、「 [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) トラブルシューティングのヒント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-122">When you connect to MDS, if you encounter any issues see [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) for troubleshooting tips.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ea0fb-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ea0fb-123">Related Tasks</span></span>  
  
|<span data-ttu-id="ea0fb-124">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="ea0fb-124">Task Description</span></span>|<span data-ttu-id="ea0fb-125">トピック</span><span class="sxs-lookup"><span data-stu-id="ea0fb-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ea0fb-126">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-126">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="ea0fb-127">MDS リポジトリへの接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="ea0fb-127">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="ea0fb-128">MDS データを Excel に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-128">Load MDS data into Excel.</span></span>|[<span data-ttu-id="ea0fb-129">MDS から Excel へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="ea0fb-129">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="ea0fb-130">Excel に読み込む前に MDS データをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="ea0fb-130">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="ea0fb-131">&#40;Excel 用 MDS アドインを読み込む前にデータをフィルター処理する&#41;</span><span class="sxs-lookup"><span data-stu-id="ea0fb-131">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="ea0fb-132">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ea0fb-132">Related Content</span></span>  
  
-   [<span data-ttu-id="ea0fb-133">データ &#40;Excel 用 MDS アドインの読み込み&#41;</span><span class="sxs-lookup"><span data-stu-id="ea0fb-133">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="ea0fb-134">ショートカット クエリ ファイル (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="ea0fb-134">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="ea0fb-135">Microsoft Excel 用マスター データ サービス アドイン</span><span class="sxs-lookup"><span data-stu-id="ea0fb-135">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
