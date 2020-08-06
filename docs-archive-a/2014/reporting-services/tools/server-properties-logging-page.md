---
title: '[サーバーのプロパティ] ([ログ記録] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a04c27fd790a1ad5c4ba453b43af5983a6440e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641975"
---
# <a name="server-properties-logging-page"></a><span data-ttu-id="a8267-102">[サーバーのプロパティ]\([ログ記録] ページ)</span><span class="sxs-lookup"><span data-stu-id="a8267-102">Server Properties (Logging Page)</span></span>
  <span data-ttu-id="a8267-103">このページを使用すると、レポート サーバーで収集されるレポート実行データに制限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a8267-103">Use this page to set limits on the report execution data that is collected by a report server.</span></span> <span data-ttu-id="a8267-104">実行データはレポート サーバー データベースに内部的に格納されます。</span><span class="sxs-lookup"><span data-stu-id="a8267-104">Execution data is stored internally in the report server database.</span></span> <span data-ttu-id="a8267-105">ネイティブ モードまたは SharePoint 統合モードで実行されているレポート サーバーのレポート処理を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="a8267-105">You can track report activity for report server that runs in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="a8267-106">レポート サーバーがスケールアウト配置の一部である場合、レポート実行ログでは、配置全体に対するすべてのレポート処理のレコードが 1 つのログ ファイルで保持されます。</span><span class="sxs-lookup"><span data-stu-id="a8267-106">If the report server is part of a scale-out deployment, the report execution log maintains a record of all report activity for the entire deployment in a single log file.</span></span>  
  
 <span data-ttu-id="a8267-107">このページを開くには、を起動して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] レポートサーバーに接続し、レポートサーバー名を右クリックして、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8267-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="a8267-108">**[ログ記録]** をクリックするとこのページが開きます。</span><span class="sxs-lookup"><span data-stu-id="a8267-108">Click **Logging** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a8267-109">Options</span><span class="sxs-lookup"><span data-stu-id="a8267-109">Options</span></span>  
 <span data-ttu-id="a8267-110">**[レポート実行のログ記録を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="a8267-110">**Enable report execution logging**</span></span>  
 <span data-ttu-id="a8267-111">サーバーのレポート処理に関する情報を作成して保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8267-111">Click to create and store information about report activity on the server.</span></span> <span data-ttu-id="a8267-112">このオプションを有効にした場合、レポート サーバーにより、使用されたレポートの種類、レポート処理の頻度、実行されたレポート操作の種類、出力形式、およびレポートの実行者が追跡されます。</span><span class="sxs-lookup"><span data-stu-id="a8267-112">If this option is enabled, the report server will track which reports are used, the frequency of report processing, the type of report operation that was performed, the output format, and who ran the report.</span></span> <span data-ttu-id="a8267-113">ログにキャプチャされるその他のデータポイントの詳細については、「[レポートサーバー実行ログと ExecutionLog3 ビュー](../report-server/report-server-executionlog-and-the-executionlog3-view.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8267-113">For more information about additional data points that are captured in the log, see [Report Server Execution Log and the ExecutionLog3 View](../report-server/report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
 <span data-ttu-id="a8267-114">**[次の日数が経過したログ エントリを削除する]**</span><span class="sxs-lookup"><span data-stu-id="a8267-114">**Remove log entries older than this number of days**</span></span>  
 <span data-ttu-id="a8267-115">レポート実行ログからログ エントリが削除されるまでの経過日数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8267-115">Specify the number of days after which log entries will be trimmed from the report execution log.</span></span> <span data-ttu-id="a8267-116">既定値は 60 日です。</span><span class="sxs-lookup"><span data-stu-id="a8267-116">The default value is 60 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8267-117">参照</span><span class="sxs-lookup"><span data-stu-id="a8267-117">See Also</span></span>  
 <span data-ttu-id="a8267-118">[レポートサーバーのプロパティ &#40;Management Studio の設定&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a8267-118">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="a8267-119">[Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a8267-119">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="a8267-120">[Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="a8267-120">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="a8267-121">[Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a8267-121">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="a8267-122">レポート サーバー実行ログと ExecutionLog3 ビュー</span><span class="sxs-lookup"><span data-stu-id="a8267-122">Report Server Execution Log and the ExecutionLog3 View</span></span>](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
