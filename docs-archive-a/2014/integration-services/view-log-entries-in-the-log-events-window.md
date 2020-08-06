---
title: '[ログイベント] ウィンドウでログエントリを表示する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16b6f11758d7de2c833731cd007426000a01d8ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712114"
---
# <a name="view-log-entries-in-the-log-events-window"></a><span data-ttu-id="b6369-102">[ログ イベント] ウィンドウでログ エントリを表示する</span><span class="sxs-lookup"><span data-stu-id="b6369-102">View Log Entries in the Log Events Window</span></span>
  <span data-ttu-id="b6369-103">この手順では、パッケージを実行して、パッケージが書き込むログ エントリを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6369-103">This procedure describes how to run a package and view the log entries it writes.</span></span> <span data-ttu-id="b6369-104">ログ エントリはリアルタイムで表示できます。</span><span class="sxs-lookup"><span data-stu-id="b6369-104">You can view the log entries in real time.</span></span> <span data-ttu-id="b6369-105">**[ログ イベント]** ウィンドウに書き込まれたログ エントリは、さらに詳しく分析するためにコピーして保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6369-105">The log entries that are written to the **Log Events** window can also be copied and saved for further analysis.</span></span>  
  
 <span data-ttu-id="b6369-106">**[ログ イベント]** ウィンドウにエントリを書き込むために、ログ エントリをログに書き込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b6369-106">It is not necessary to write the log entries to a log to write the entries to the **Log Events** window.</span></span>  
  
### <a name="to-view-log-entries"></a><span data-ttu-id="b6369-107">ログ エントリを表示するには</span><span class="sxs-lookup"><span data-stu-id="b6369-107">To view log entries</span></span>  
  
1.  <span data-ttu-id="b6369-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b6369-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b6369-109">**[SSIS]** メニューの **[ログ イベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6369-109">On the **SSIS** menu, click **Log Events**.</span></span> <span data-ttu-id="b6369-110">必要に応じて、View.LogEvents コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[ログ イベント]** ウィンドウを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6369-110">You can optionally display the **Log Events** window by mapping the View.LogEvents command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
3.  <span data-ttu-id="b6369-111">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6369-111">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="b6369-112">実行時に、ログ記録可能なイベントやカスタム メッセージが見つかると、各イベントまたはメッセージのログ エントリが **[ログ イベント]** ウィンドウに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="b6369-112">As the runtime encounters the events and custom messages that are enabled for logging, log entries for each event or message are written to the **Log Events** window.</span></span>  
  
4.  <span data-ttu-id="b6369-113">**[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6369-113">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
     <span data-ttu-id="b6369-114">**[ログ イベント]** ウィンドウのログ エントリは、パッケージを再実行するか、別のパッケージを実行するか、または [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]を終了するまでは、そのまま使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6369-114">The log entries remain available in the **Log Events** window until you rerun the package, run a different package, or close [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
5.  <span data-ttu-id="b6369-115">**[ログ イベント]** ウィンドウで、ログ エントリを表示します。</span><span class="sxs-lookup"><span data-stu-id="b6369-115">View the log entries in the **Log Events** window.</span></span>  
  
6.  <span data-ttu-id="b6369-116">必要に応じて、コピーするログ エントリを右クリックして **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6369-116">Optionally, click the log entries to copy, right-click, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="b6369-117">必要に応じて、ログ エントリをダブルクリックし、 **[ログ エントリ]** ダイアログ ボックスで、1 つのログ エントリの詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="b6369-117">Optionally, double-click a log entry, and in the **Log Entry** dialog box, view the details for a single log entry.</span></span>  
  
8.  <span data-ttu-id="b6369-118">**[ログ エントリ]** ダイアログ ボックスで、上矢印および下矢印をクリックして前後のログ エントリを表示し、コピー アイコンをクリックしてログ エントリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="b6369-118">In the **Log Entry** dialog box, click the up and down arrows to display the previous or next log entry, and click the copy icon to copy the log entry.</span></span>  
  
9. <span data-ttu-id="b6369-119">テキスト エディターを開いて貼り付けた後、ログ エントリをテキスト ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="b6369-119">Open a text editor, paste, and then save the log entry to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6369-120">参照</span><span class="sxs-lookup"><span data-stu-id="b6369-120">See Also</span></span>  
 [<span data-ttu-id="b6369-121">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="b6369-121">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
