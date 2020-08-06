---
title: レポートのパブリッシュ |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb54308a6b15260d4c336950f231d0ee40836430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631623"
---
# <a name="publish-reports"></a><span data-ttu-id="3a920-102">レポートのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="3a920-102">Publish Reports</span></span>
  <span data-ttu-id="3a920-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]から、プロジェクトを配置してレポート サーバーにレポート サーバー プロジェクト内のすべてのレポートおよび共有データ ソースをパブリッシュしたり、単一のレポートをパブリッシュしたりできます。</span><span class="sxs-lookup"><span data-stu-id="3a920-103">From[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can publish either all the reports and shared data sources in a Report Server project to a report server by deploying the project, or you can publish a single report.</span></span> <span data-ttu-id="3a920-104">レポートをパブリッシュする前に、ターゲット レポート サーバーの URL を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a920-104">Before you can publish a report you must specify the URL of the target report server.</span></span> <span data-ttu-id="3a920-105">詳細については、「[配置プロパティを設定する (Reporting Services)](tools/set-deployment-properties-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a920-105">For more information, see [Set Deployment Properties &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md).</span></span>  
  
 <span data-ttu-id="3a920-106">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] バージョンを使用すると、 [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] と [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] の両方のレポートを開くことや、変更、プレビュー、保存、およびパブリッシュを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3a920-106">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to open, modify, preview, save, and publish both [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] and [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] reports.</span></span> <span data-ttu-id="3a920-107">詳細については、「 [SQL Server データ ツールの配置およびバージョン サポート (SSRS)](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="3a920-107">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
### <a name="to-publish-all-reports-in-a-project"></a><span data-ttu-id="3a920-108">プロジェクトのすべてのレポートをパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="3a920-108">To publish all reports in a project</span></span>  
  
-   <span data-ttu-id="3a920-109">[**ビルド**] メニューの [\*\*配置 \<report project name> \*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a920-109">On the **Build** menu, click **Deploy \<report project name>**.</span></span> <span data-ttu-id="3a920-110">または、ソリューション エクスプローラーでレポート プロジェクトを右クリックして、 **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a920-110">Alternatively, in Solution Explorer, right-click the report project and then click **Deploy**.</span></span> <span data-ttu-id="3a920-111">パブリッシュ処理の状態が、[出力] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a920-111">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a920-112">レポート サーバー プロジェクトを配置すると、レポート プロジェクトの共有データ ソースも配置されます。</span><span class="sxs-lookup"><span data-stu-id="3a920-112">When you deploy a Report Server project, the shared data sources in the report project are also deployed.</span></span>  
  
### <a name="to-publish-a-single-report"></a><span data-ttu-id="3a920-113">1 つのレポートをパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="3a920-113">To publish a single report</span></span>  
  
-   <span data-ttu-id="3a920-114">ソリューション エクスプローラーで、レポートを右クリックし、 **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a920-114">In Solution Explorer, right-click the report and then click **Deploy**.</span></span> <span data-ttu-id="3a920-115">パブリッシュ処理の状態が、[出力] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a920-115">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a920-116">レポートをパブリッシュするときは、レポートが使用する共有データ ソースを配置する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="3a920-116">When you publish a report, you must also deploy the shared data sources that the report uses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a920-117">参照</span><span class="sxs-lookup"><span data-stu-id="3a920-117">See Also</span></span>  
 <span data-ttu-id="3a920-118">[データソースとレポートのパブリッシュ](reports/publishing-data-sources-and-reports.md) </span><span class="sxs-lookup"><span data-stu-id="3a920-118">[Publishing Data Sources and Reports](reports/publishing-data-sources-and-reports.md) </span></span>  
 <span data-ttu-id="3a920-119">[レポートのプレビュー](reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="3a920-119">[Previewing Reports](reports/previewing-reports.md) </span></span>  
 <span data-ttu-id="3a920-120">[レポートサーバーへのレポートのパブリッシュ](reports/publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="3a920-120">[Publishing Reports to a Report Server](reports/publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="3a920-121">[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3a920-121">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3a920-122">レポートのエクスポート &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a920-122">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
