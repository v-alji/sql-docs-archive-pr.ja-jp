---
title: 入力トレースデータを準備する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c14fd3d2-5770-47c2-a851-cc13ddbc9bf5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c13dddcf29f93940fa4eae6b2849dcfb278ae3b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719256"
---
# <a name="prepare-the-input-trace-data"></a><span data-ttu-id="d6748-102">入力トレース データの準備</span><span class="sxs-lookup"><span data-stu-id="d6748-102">Prepare the Input Trace Data</span></span>
  <span data-ttu-id="d6748-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生機能を使用して分散再生を開始する前に、分散再生管理ツールから前処理段階を開始することで、入力トレース データを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6748-103">Before you can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature, you must prepare the input trace data by initiating the preprocess stage from the distributed replay administration tool.</span></span> <span data-ttu-id="d6748-104">前処理段階で、Distributed Replay Controller がトレース データを処理し、中間ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d6748-104">In the preprocess stage, the distributed replay controller processes the trace data and generates an intermediate file:</span></span>  
  
 <span data-ttu-id="d6748-105">![分散再生の前処理段階](../../database-engine/media/preprocess.gif "分散再生の前処理段階")</span><span class="sxs-lookup"><span data-stu-id="d6748-105">![Distributed replay preprocess stage](../../database-engine/media/preprocess.gif "Distributed replay preprocess stage")</span></span>  
  
 <span data-ttu-id="d6748-106">前処理段階の詳細については、「 [SQL Server Distributed Replay](sql-server-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6748-106">For more information about the preprocess stage, see [SQL Server Distributed Replay](sql-server-distributed-replay.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6748-107">入力トレース データは、Distributed Replay と互換性があるバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6748-107">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="d6748-108">また、入力トレース データは、トレース データを再生するターゲット サーバーと互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6748-108">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="d6748-109">バージョンの要件の詳細については、「 [Distributed Replay Requirements](distributed-replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6748-109">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-prepare-the-input-trace-data"></a><span data-ttu-id="d6748-110">入力トレース データを準備するには</span><span class="sxs-lookup"><span data-stu-id="d6748-110">To prepare the input trace data</span></span>  
  
1.  <span data-ttu-id="d6748-111">**(省略可能) 前処理構成設定の変更**:前処理構成設定 (システム セッションをフィルター処理するかどうか、最大アイドル時間を構成するかどうかなど) を変更する場合は、XML ベースの前処理構成ファイル `DReplay.exe.preprocess.config` の `<PreprocessModifiers>` 要素を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6748-111">**(Optional) Modify preprocess configuration settings**: If you want to modify the preprocess configuration settings, such as whether to filter system sessions or to configure the maximum idle time, you must modify the `<PreprocessModifiers>` element of the XML-based preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span> <span data-ttu-id="d6748-112">前処理構成ファイルを変更する場合は、元のファイルではなく、コピーを変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d6748-112">If you modify the preprocess configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="d6748-113">設定を変更するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d6748-113">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="d6748-114">既定の前処理構成ファイル `DReplay.exe.preprocess.config`のコピーを作成し、新しいファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="d6748-114">Make a copy of the default preprocess configuration file, `DReplay.exe.preprocess.config`, and rename the new file.</span></span> <span data-ttu-id="d6748-115">既定の前処理構成ファイルは管理ツールのインストール フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="d6748-115">The default preprocess configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="d6748-116">新しい構成ファイル内の前処理構成設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="d6748-116">Modify the preprocess configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="d6748-117">前処理段階 (次の手順) を開始するときに、 *前処理* オプションの **config_file** パラメーターを使用して、変更した構成ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6748-117">When initiating the preprocess stage (the next step), use the *config_file* parameter of the **preprocess** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="d6748-118">前処理構成ファイルの詳細については、「 [Distributed Replay の構成](configure-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6748-118">For more information about the preprocess configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="d6748-119">**前処理段階を開始する**:入力トレース データを準備するには、**preprocess** オプションを使用して、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6748-119">**Initiate the preprocess stage**: To prepare the input trace data, you must run the administration tool with the **preprocess** option.</span></span> <span data-ttu-id="d6748-120">詳細については、「[前処理オプション &#40;Distributed Replay 管理ツール&#41;](preprocess-option-distributed-replay-administration-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6748-120">For more information, see [Preprocess Option &#40;Distributed Replay Administration Tool&#41;](preprocess-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="d6748-121">Windows のコマンド プロンプト ユーティリティ (`CMD.exe`) を開き、Distributed Replay 管理ツール (`DReplay.exe`) のインストール場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="d6748-121">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="d6748-122">(省略可能) 管理ツールを実行するコンピューターとは別のコンピューター上でコントローラー サービスが実行されている場合、 *controller* パラメーター **-m**を使用して、コントローラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d6748-122">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="d6748-123">*input_trace_file* パラメーター **-i**を使用して、入力トレース ファイルの場所と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6748-123">Use the *input_trace_file* parameter, **-i**, to specify the location and name of the input trace files.</span></span>  
  
    4.  <span data-ttu-id="d6748-124">*controller_working_directory* パラメーター **-d**を使用して、コントローラーで中間ファイルを保存する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6748-124">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file should be saved on the controller.</span></span>  
  
    5.  <span data-ttu-id="d6748-125">(省略可能) *config_file* パラメーター **-c**を使用して、前処理構成ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6748-125">(Optional) Use the *config_file* parameter, **-c**, to specify location of the preprocess configuration file.</span></span> <span data-ttu-id="d6748-126">既定の前処理構成ファイルのコピーを変更した場合は、このパラメーターを使用して、新しい構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d6748-126">Use this parameter to point to the new configuration file if you have modified a copy of the default preprocess configuration file.</span></span>  
  
    6.  <span data-ttu-id="d6748-127">(省略可能) *status_interval* パラメーター **-f**を使用して、30 秒以外の周期で状態メッセージを管理ツールで表示させるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d6748-127">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency different than 30 seconds.</span></span>  
  
     <span data-ttu-id="d6748-128">たとえば、 `c:\trace1.trc`にあるトレース ファイルに対して、コントローラー サービスと同じコンピューターで前処理段階を開始し、コントローラー作業ディレクトリが `c:\WorkingDir` にあり、既定の 30 秒で状態メッセージが表示される場合、 `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span><span class="sxs-lookup"><span data-stu-id="d6748-128">For example, initiating the preprocess stage on the same computer as the controller service, for a trace file located at `c:\trace1.trc`, a controller working directory located at `c:\WorkingDir` , and a status message displayed at the default value of 30 seconds, requires the syntax: `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span></span>  
  
3.  <span data-ttu-id="d6748-129">前処理段階が完了したら、コントローラー作業ディレクトリに中間ファイルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="d6748-129">After the preprocess stage is complete, the intermediate file is stored in the controller working directory.</span></span> <span data-ttu-id="d6748-130">イベント再生段階を開始するには、 **再生** オプションを使用して、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6748-130">To initiate the event replay stage, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="d6748-131">詳細については、「 [トレース データの再生](replay-trace-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6748-131">For more information, see [Replay Trace Data](replay-trace-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6748-132">参照</span><span class="sxs-lookup"><span data-stu-id="d6748-132">See Also</span></span>  
 <span data-ttu-id="d6748-133">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="d6748-133">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="d6748-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="d6748-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="d6748-135">[管理ツール コマンド ライン オプション &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="d6748-135">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="d6748-136">分散再生の構成</span><span class="sxs-lookup"><span data-stu-id="d6748-136">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
