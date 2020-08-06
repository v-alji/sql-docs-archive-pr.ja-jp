---
title: データ ソースとレポートのパブリッシュ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing data sources [Reporting Services]
- publishing reports [Reporting Services]
- data sources [Reporting Services], managing
ms.assetid: 3a740f8a-1060-4ec3-938b-2305b6887ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 941362afde1cfe5dd3d235c9f243fb17875adadc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712717"
---
# <a name="publishing-data-sources-and-reports"></a><span data-ttu-id="9e614-102">データ ソースとレポートのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="9e614-102">Publishing Data Sources and Reports</span></span>
  <span data-ttu-id="9e614-103">レポートをパブリッシュする前に、レポートをプレビューしてレポート実行時の表示を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e614-103">Before publishing your report, you should preview the report to see how it will look when it is run.</span></span> <span data-ttu-id="9e614-104">プレビュー後も、表示結果に満足できるまでデザインを調整できます。</span><span class="sxs-lookup"><span data-stu-id="9e614-104">You can continue to refine the design until you are satisfied with the results.</span></span>  
  
 <span data-ttu-id="9e614-105">レポートをデザインしてテストした後に、他のユーザーとレポートを共有する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9e614-105">After you design and test your report, you may want to share it with other individuals.</span></span> <span data-ttu-id="9e614-106">レポートを共有するには、レポート サーバーまたは SharePoint サイトにレポートをパブリッシュ ( *配置*) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e614-106">To share your report, you need to publish, or *deploy*, it to a report server or SharePoint site.</span></span> <span data-ttu-id="9e614-107">レポートがパブリッシュされると、レポート サーバーまたは SharePoint サイトに対する権限を持っている場合は、レポートを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9e614-107">After it has been published, individuals who have permissions to the report server or the SharePoint site can run your report.</span></span> <span data-ttu-id="9e614-108">さらに、レポート サーバーに対する管理者権限を持っている場合は、レポートを定期的に更新してユーザーに送信できるようにレポートのサブスクリプションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9e614-108">In addition, a person with administrator permissions on the report server can create subscriptions to your report so that the report can be updated and sent to users on a regular schedule.</span></span>  
  
 <span data-ttu-id="9e614-109">共有データ ソースを使用してレポートを作成した場合は、レポートと同じ場所に共有データ ソースをパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e614-109">If you used a shared data source to create your report, you need to publish it to the same location as the report.</span></span> <span data-ttu-id="9e614-110">レポートと同様、共有データ ソースはレポート サーバー上で個別に管理できます。</span><span class="sxs-lookup"><span data-stu-id="9e614-110">Like reports, shared data sources can be managed separately on the report server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e614-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9e614-111">In This Section</span></span>  
 [<span data-ttu-id="9e614-112">レポートのプレビュー</span><span class="sxs-lookup"><span data-stu-id="9e614-112">Previewing Reports</span></span>](previewing-reports.md)  
 <span data-ttu-id="9e614-113">レポートをパブリッシュする前にプレビューする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e614-113">Describes how to preview a report before you publish it.</span></span>  
  
 [<span data-ttu-id="9e614-114">レポート サーバーへのレポートのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="9e614-114">Publishing Reports to a Report Server</span></span>](publishing-reports-to-a-report-server.md)  
 <span data-ttu-id="9e614-115">レポートをレポート サーバーにパブリッシュする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e614-115">Describes how to publish a report to a report server.</span></span>  
  
 [<span data-ttu-id="9e614-116">SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="9e614-116">URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;</span></span>](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)  
 <span data-ttu-id="9e614-117">レポートを SharePoint サイトにパブリッシュする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e614-117">Describes how to publish a report to a SharePoint site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e614-118">参照</span><span class="sxs-lookup"><span data-stu-id="9e614-118">See Also</span></span>  
 <span data-ttu-id="9e614-119">[Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="9e614-119">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="9e614-120">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e614-120">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="9e614-121">[ページレイアウトと表示 &#40;レポートビルダーと SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e614-121">[Page Layout and Rendering &#40;Report Builder and SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e614-122">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e614-122">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="9e614-123">[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e614-123">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e614-124">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e614-124">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9e614-125">レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9e614-125">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)  
  
  
