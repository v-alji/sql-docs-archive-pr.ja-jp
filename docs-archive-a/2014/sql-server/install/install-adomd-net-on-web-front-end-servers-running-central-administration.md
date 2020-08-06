---
title: サーバーの全体管理を実行している Web フロントエンドサーバーに ADOMD.NET をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0d9f52bf612c4878a8dacd4f5acfdcc135ae115e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632290"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a><span data-ttu-id="4e7c7-102">サーバーの全体管理を実行している Web フロントエンド サーバーに ADOMD.NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="4e7c7-102">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>
  <span data-ttu-id="4e7c7-103">Excel Services または PowerPivot for SharePoint がインストールされていない、サーバーの全体管理のトポロジを持つファームに PowerPivot for SharePoint をインストールするときに、PowerPivot 管理ダッシュボードの組み込みレポートへのフル アクセスが必要な場合は、Microsoft ADOMD.NET クライアント ライブラリをダウンロードしてインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-103">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="4e7c7-104">ダッシュボードの一部のレポートでは、ADOMD.NET を使用して、ファームの PowerPivot クエリ処理およびサーバーの状態に関するレポート データを提供する内部データにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-104">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span>  
  
 <span data-ttu-id="4e7c7-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="4e7c7-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="4e7c7-106">SharePoint 2013 では、プロバイダーは SQL Server 機能パックに含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-106">For SharePoint 2013, the provider is included in the SQL Server feature pack.</span></span> <span data-ttu-id="4e7c7-107">spPowerPivot.msi をダウンロードする方法の詳細については、「 [Microsoft SQL Server 2014 機能パック](https://www.microsoft.com/download/details.aspx?id=35577)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-107">For information on how to download spPowerPivot.msi, see [Microsoft SQL Server 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35577)</span></span>  
  
### <a name="download-and-install-the-client-library"></a><span data-ttu-id="4e7c7-108">クライアント ライブラリのダウンロードとインストール</span><span class="sxs-lookup"><span data-stu-id="4e7c7-108">Download and install the client library</span></span>  
  
1.  <span data-ttu-id="4e7c7-109">[ [SQL Server 2014 Feature Pack] ページ](https://go.microsoft.com/fwlink/?LinkID=296473)で、Microsoft ADOMD.NET を見つけます。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-109">On the [SQL Server 2014 Feature Pack page](https://go.microsoft.com/fwlink/?LinkID=296473), find Microsoft ADOMD.NET.</span></span>  
  
2.  <span data-ttu-id="4e7c7-110">`SQL_AS_ADOMD.msi` インストール プログラムの x64 パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-110">Download the x64 Package of the `SQL_AS_ADOMD.msi` installation program.</span></span>  
  
3.  <span data-ttu-id="4e7c7-111">.Msi を実行して、ライブラリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-111">Run the .msi to install the library.</span></span>  
  
4.  <span data-ttu-id="4e7c7-112">インストールの完了後、IIS をリセットします。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-112">Reset IIS after installation is finished.</span></span> <span data-ttu-id="4e7c7-113">管理コマンドプロンプトを開き、「 **IISRESET**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-113">Open an administrative command prompt and type **IISRESET**.</span></span>  
  
### <a name="verify-installation"></a><span data-ttu-id="4e7c7-114">インストールの確認</span><span class="sxs-lookup"><span data-stu-id="4e7c7-114">Verify installation</span></span>  
  
1.  <span data-ttu-id="4e7c7-115">Windows\Assembly に移動します。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-115">Go to Windows\Assembly.</span></span>  
  
2.  <span data-ttu-id="4e7c7-116">Microsoft.analysisservices.sharepoint.integration.dll を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-116">Right-click Microsoft.AnalysisServices.AdomdClient and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="4e7c7-117">**[バージョン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-117">Click **Version**.</span></span>  
  
4.  <span data-ttu-id="4e7c7-118">バージョンに12.00 が含まれていることを確認します。\<build number></span><span class="sxs-lookup"><span data-stu-id="4e7c7-118">Verify that the version includes 12.00.\<build number></span></span> <span data-ttu-id="4e7c7-119">また、説明は Microsoft.analysisservice.adomdclient になります。</span><span class="sxs-lookup"><span data-stu-id="4e7c7-119">and that the description is Microsoft.AnalysisService.AdomdClient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7c7-120">参照</span><span class="sxs-lookup"><span data-stu-id="4e7c7-120">See Also</span></span>  
 [<span data-ttu-id="4e7c7-121">PowerPivot 管理ダッシュボードと使用状況データ</span><span class="sxs-lookup"><span data-stu-id="4e7c7-121">PowerPivot Management Dashboard and Usage Data</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)  
  
  
