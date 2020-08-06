---
title: トレースデータの再生 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 19ff5285-fb9d-4fd1-97c4-ec72c311c384
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6c929d7c617ba4dc496eedabaccbbe50da32d08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632250"
---
# <a name="replay-trace-data"></a><span data-ttu-id="3f128-102">トレース データの再生</span><span class="sxs-lookup"><span data-stu-id="3f128-102">Replay Trace Data</span></span>
  <span data-ttu-id="3f128-103">入力トレース データが準備できたら、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生機能を使用して、分散再生を開始できます。</span><span class="sxs-lookup"><span data-stu-id="3f128-103">You can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature after you have prepared the input trace data.</span></span> <span data-ttu-id="3f128-104">詳細については、「 [入力トレース データの準備](prepare-the-input-trace-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f128-104">For more information, see [Prepare the Input Trace Data](prepare-the-input-trace-data.md).</span></span>  
  
 <span data-ttu-id="3f128-105">分散再生のイベント再生段階を開始するには、管理ツールの **replay** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3f128-105">Use the administration tool **replay** option to initiate the event replay stage of the distributed replay.</span></span> <span data-ttu-id="3f128-106">この段階は、トレース データのディスパッチと、分散再生の開始および同期の 2 つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="3f128-106">This stage consists of two parts: the trace data dispatch and the starting and synchronizing of the distributed replay.</span></span>  
  
 <span data-ttu-id="3f128-107">![イベントの分散再生](../../database-engine/media/eventreplay.gif "イベントの分散再生")</span><span class="sxs-lookup"><span data-stu-id="3f128-107">![Distributed Event Replay](../../database-engine/media/eventreplay.gif "Distributed Event Replay")</span></span>  
  
 <span data-ttu-id="3f128-108">トレース データは、2 つのシーケンス モード (ストレス モードまたは同期モード) のいずれかで再生できます。</span><span class="sxs-lookup"><span data-stu-id="3f128-108">You can replay trace data in one of two sequencing modes: stress mode or synchronization mode.</span></span> <span data-ttu-id="3f128-109">既定の動作では、ストレス モードでトレース データを再生します。</span><span class="sxs-lookup"><span data-stu-id="3f128-109">The default behavior is to replay trace data in stress mode.</span></span> <span data-ttu-id="3f128-110">イベント再生段階とシーケンス モードの詳細については、「 [SQL Server Distributed Replay](sql-server-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f128-110">For more information about the event replay stage and sequencing modes, see [SQL Server Distributed Replay](sql-server-distributed-replay.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f128-111">入力トレース データは、Distributed Replay と互換性があるバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f128-111">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="3f128-112">また、入力トレース データは、トレース データを再生するターゲット サーバーと互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f128-112">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="3f128-113">バージョンの要件の詳細については、「 [Distributed Replay Requirements](distributed-replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f128-113">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-replay-the-trace"></a><span data-ttu-id="3f128-114">トレースを再生するには</span><span class="sxs-lookup"><span data-stu-id="3f128-114">To replay the trace</span></span>  
  
1.  <span data-ttu-id="3f128-115">**(省略可能) 再生の構成設定を変更する**:シーケンス モード、各種のスケーリング値など、再生の構成設定を変更する場合は、XML ベースの再生構成ファイル `DReplay.exe.replay.config` の `<ReplayOptions>` 要素を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f128-115">**(Optional) Modify replay configuration settings**: If you want to modify the replay configuration settings, such as the sequencing mode and various scaling values, you must modify the `<ReplayOptions>` element of the XML-based replay configuration file `DReplay.exe.replay.config`.</span></span> <span data-ttu-id="3f128-116">また、 `<OutputOptions>` 要素を変更すると、行数を記録するかどうかなどの出力設定を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f128-116">You can also modify the `<OutputOptions>` element to specify output settings, such as whether to record the row count.</span></span> <span data-ttu-id="3f128-117">再生構成ファイルを変更する場合は、元のファイルではなく、コピーを変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3f128-117">If you modify the replay configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="3f128-118">設定を変更するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3f128-118">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="3f128-119">既定の再生構成ファイル `DReplay.exe.replay.config`のコピーを作成し、新しいファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="3f128-119">Make a copy of the default replay configuration file, `DReplay.exe.replay.config`, and rename the new file.</span></span> <span data-ttu-id="3f128-120">既定の再生構成ファイルは管理ツールのインストール フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="3f128-120">The default replay configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="3f128-121">新しい構成ファイル内の再生の構成設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="3f128-121">Modify the replay configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="3f128-122">イベント再生段階 (次の手順) を開始するときに、 *replay* オプションの **config_file** パラメーターを使用して、変更した構成ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-122">When initiating the event replay stage (the next step), use the *config_file* parameter of the **replay** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="3f128-123">再生構成ファイルの詳細については、「 [Distributed Replay の構成](configure-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f128-123">For more information about the replay configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="3f128-124">**イベント再生段階を開始する**:分散再生を開始するには、**replay** オプションを使用して、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f128-124">**Initiate the event replay stage**: To start the distributed replay, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="3f128-125">詳細については、「[replay オプション &#40;Distributed Replay 管理ツール&#41;](replay-option-distributed-replay-administration-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f128-125">For more information, see [Replay Option &#40;Distributed Replay Administration Tool&#41;](replay-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="3f128-126">Windows のコマンド プロンプト ユーティリティ (`CMD.exe`) を開き、Distributed Replay 管理ツール (`DReplay.exe`) のインストール場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="3f128-126">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="3f128-127">(省略可能) 管理ツールを実行するコンピューターとは別のコンピューター上でコントローラー サービスが実行されている場合、 *controller* パラメーター **-m**を使用して、コントローラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-127">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="3f128-128">*controller_working_directory* パラメーター **-d**を使用して、前処理段階でコントローラーに保存した中間ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-128">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file was saved on the controller during the preprocess stage.</span></span>  
  
    4.  <span data-ttu-id="3f128-129">(省略可能) **-o** パラメーターを使用して、各クライアントで再生アクティビティを結果のトレース ファイルにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="3f128-129">(Optional) Use the **-o** parameter to capture the replay activity in a result trace file on each client.</span></span>  
  
    5.  <span data-ttu-id="3f128-130">(省略可能) *target_server* パラメーター **-s**を使用して、分散再生クライアントでトレース ワークロードを再生する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-130">(Optional) Use the *target_server* parameter, **-s**, to specify the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where the distributed replay clients should replay the trace workload.</span></span> <span data-ttu-id="3f128-131">`<Server>` 要素を使用して、再生構成ファイルの `<ReplayOptions>` 要素でターゲット サーバーを指定している場合、このパラメーターは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3f128-131">This parameter is not required if you used the `<Server>` element to specify the target server in the `<ReplayOptions>` element of the replay configuration file.</span></span>  
  
    6.  <span data-ttu-id="3f128-132">*clients* パラメーター **-w**を使用して、再生に参加する分散再生クライアントを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-132">Use the *clients* parameter, **-w**, to specify the distributed replay clients that should participate in the replay.</span></span> <span data-ttu-id="3f128-133">クライアント コンピューター名はコンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-133">List the client computer names, separated by commas.</span></span> <span data-ttu-id="3f128-134">注:IP アドレスは指定できません。</span><span class="sxs-lookup"><span data-stu-id="3f128-134">Note: IP addresses are not allowed.</span></span>  
  
    7.  <span data-ttu-id="3f128-135">(省略可能) *config_file* パラメーター **-c**を使用して、再生構成ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-135">(Optional) Use the *config_file* parameter, **-c**, to specify location of the replay configuration file.</span></span> <span data-ttu-id="3f128-136">既定の再生構成ファイルのコピーを変更した場合は、このパラメーターを使用して、新しい構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-136">Use this parameter to point to the new configuration file if you have modified a copy of the default replay configuration file.</span></span>  
  
    8.  <span data-ttu-id="3f128-137">(省略可能) *status_interval* パラメーター **-f**を使用して、30 秒以外の周期で状態メッセージを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f128-137">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency other than 30 seconds.</span></span>  
  
     <span data-ttu-id="3f128-138">たとえば、次の構文では、コントローラー サービスと同じコンピューターで再生段階を開始し、 `c:\WorkingDir`にあるコントローラー作業ディレクトリを使用し、参加している各クライアントで再生アクティビティをキャプチャして、クライアント `client1` と `client2` を使用して再生を実行し、残りの再生の構成設定を `c:\modifiedreplay.config`にある変更済みの再生構成ファイルから取得します。</span><span class="sxs-lookup"><span data-stu-id="3f128-138">For example, the following syntax initiates the replay stage on the same computer as the controller service, uses a controller working directory located at `c:\WorkingDir`, captures the replay activity on each participating client, uses clients `client1` and `client2` to perform the replay, and obtains the remaining replay configuration settings from a modified replay configuration file located at `c:\modifiedreplay.config`:</span></span>  
  
     `dreplay replay -d c:\WorkingDir -o -w client1,client2 -c c:\modifiedreplay.config`  
  
3.  <span data-ttu-id="3f128-139">分散再生が終了すると、管理ツールから概要情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="3f128-139">When the distributed replay has finished, the administration tool returns summary information.</span></span> <span data-ttu-id="3f128-140">**-o** オプションを指定した場合、各クライアントで再生アクティビティが結果のトレース ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3f128-140">If you specified the **-o** option, the replay activity has been saved in result trace files on each client.</span></span> <span data-ttu-id="3f128-141">結果のトレース ファイルの詳細については、「 [再生結果の確認](review-the-replay-results.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f128-141">For more information about the result trace files, see [Review the Replay Results](review-the-replay-results.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f128-142">参照</span><span class="sxs-lookup"><span data-stu-id="3f128-142">See Also</span></span>  
 <span data-ttu-id="3f128-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="3f128-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="3f128-144">[管理ツール コマンド ライン オプション &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3f128-144">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="3f128-145">分散再生の構成</span><span class="sxs-lookup"><span data-stu-id="3f128-145">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
