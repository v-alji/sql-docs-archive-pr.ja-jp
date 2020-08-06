---
title: レポート履歴を制限する (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01318b1e1ccf0b0bf4512ab57de90cbf5ebc7365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713782"
---
# <a name="limit-report-history-report-manager"></a><span data-ttu-id="3eb3e-102">レポート履歴を制限する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="3eb3e-102">Limit Report History (Report Manager)</span></span>
  <span data-ttu-id="3eb3e-103">レポート履歴とは、時間の経過と共に作成されるレポート スナップショットの集まりです。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="3eb3e-104">レポート履歴は必要時に作成できるほか、どの程度の頻度でスナップショットを作成し、レポート履歴に追加するかをスケジュールで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-104">You can create report history on demand, or schedule how often a snapshot is created and added to report history.</span></span>  
  
 <span data-ttu-id="3eb3e-105">レポート履歴は、レポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-105">Report history is stored in the report server database.</span></span> <span data-ttu-id="3eb3e-106">レポート スナップショットに大量のデータが含まれている場合は、スナップショットを保持することによるデータベース サイズへの影響を最小限に抑えるために、レポート履歴を制限することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-106">If report snapshots contain a large amount of data, you might consider limiting report history to minimize the affect of snapshot retention on database size.</span></span>  
  
### <a name="to-configure-report-history-for-a-report-server"></a><span data-ttu-id="3eb3e-107">レポート サーバーのレポート履歴を構成するには</span><span class="sxs-lookup"><span data-stu-id="3eb3e-107">To configure report history for a report server</span></span>  
  
1.  <span data-ttu-id="3eb3e-108">レポート マネージャーのグローバル ツール バーで、 **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-108">In Report Manager, click **Site Settings** on the global toolbar.</span></span>  
  
2.  <span data-ttu-id="3eb3e-109">すべてのレポート履歴を制限なく保持する場合は、 **[レポート履歴に無制限の数のスナップショットを保持する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-109">Select **Keep an unlimited number of snapshots in report history** if you want to keep all report history indefinitely.</span></span> <span data-ttu-id="3eb3e-110">それ以外の場合は、 **[レポート履歴のコピーの数を制限する]** を選択し、特定のレポートに対して保持できるスナップショットの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-110">Otherwise, select **Limit the copies of report history** to specify the maximum number of snapshots that can be kept for any given report.</span></span>  
  
3.  <span data-ttu-id="3eb3e-111">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-111">Click **Apply**.</span></span>  
  
### <a name="to-configure-report-history-for-a-specific-report"></a><span data-ttu-id="3eb3e-112">特定のレポートのレポート履歴を構成するには</span><span class="sxs-lookup"><span data-stu-id="3eb3e-112">To configure report history for a specific report</span></span>  
  
1.  <span data-ttu-id="3eb3e-113">レポート マネージャーで、履歴を構成するレポートに移動し、そのレポートをクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-113">In Report Manager, navigate to the report for which you want to configure history, and then click the report to open it.</span></span>  
  
2.  <span data-ttu-id="3eb3e-114">**[プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-114">Click the **Properties** tab.</span></span>  
  
3.  <span data-ttu-id="3eb3e-115">[**履歴**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-115">Click the **History** tab.</span></span>  
  
4.  <span data-ttu-id="3eb3e-116">レポートのオプションを選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-116">Select the options for your report and click **Apply**.</span></span> <span data-ttu-id="3eb3e-117">各オプションに関する詳細については、「[[スナップショット オプション] プロパティ ページ &#40;レポート マネージャー&#41;](../snapshot-options-properties-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3eb3e-117">For details about each option, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../snapshot-options-properties-page-report-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb3e-118">参照</span><span class="sxs-lookup"><span data-stu-id="3eb3e-118">See Also</span></span>  
 <span data-ttu-id="3eb3e-119">[レポート履歴へのスナップショットの追加 &#40;レポートマネージャー&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="3eb3e-119">[Add a Snapshot to Report History &#40;Report Manager&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 [<span data-ttu-id="3eb3e-120">レポート マネージャー &#40;SSRS ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="3eb3e-120">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
