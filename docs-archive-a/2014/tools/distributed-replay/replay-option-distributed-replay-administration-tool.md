---
title: replay オプション (分散再生管理ツール) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: a3114d7c2a2a7908e4e010fbf5d80c7d332d264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740620"
---
# <a name="replay-option-distributed-replay-administration-tool"></a><span data-ttu-id="455af-102">replay オプション (Distributed Replay 管理ツール)</span><span class="sxs-lookup"><span data-stu-id="455af-102">Replay Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="455af-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生管理ツールは、 `DReplay.exe` 分散再生コントローラーとの通信に使用できるコマンドラインツールです。</span><span class="sxs-lookup"><span data-stu-id="455af-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="455af-104">このトピックでは、 **replay** コマンド ライン オプションとそれに対応する構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="455af-104">This topic describes the **replay** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="455af-105">**replay** オプションはイベント再生段階を開始します。ここでは、コントローラーは、指定されたクライアントに再生データをディスパッチし、分散再生を開始して、クライアントを同期します。</span><span class="sxs-lookup"><span data-stu-id="455af-105">The **replay** option initiates the event replay stage, in which the controller dispatches replay data to the specified clients, launches the distributed replay and synchronizes the clients.</span></span> <span data-ttu-id="455af-106">必要に応じて、再生に参加している各クライアントは再生アクティビティを記録し、結果トレース ファイルをローカルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="455af-106">Optionally, each client participating in the replay can record the replay activity and save a result trace file locally.</span></span>

 <span data-ttu-id="455af-107">![トピック リンク アイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン") 管理ツールの構文で使用される構文表記規則の詳細については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="455af-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="455af-108">構文</span><span class="sxs-lookup"><span data-stu-id="455af-108">Syntax</span></span>

```

      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]
    [-starget_server] -wclients [-cconfig_file]
    [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="455af-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="455af-109">Parameters</span></span>
 <span data-ttu-id="455af-110">**-m** *コントローラー*コントローラーのコンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="455af-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="455af-111">"`localhost`" または "`.`" を使用してローカル コンピューターを参照できます。</span><span class="sxs-lookup"><span data-stu-id="455af-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="455af-112">**-m** パラメーターが指定されていない場合、ローカル コンピューターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="455af-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="455af-113">**-d** *controller_working_dir*中間ファイルを格納するコントローラー上のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="455af-113">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="455af-114">**-d** パラメーターは必須です。</span><span class="sxs-lookup"><span data-stu-id="455af-114">The **-d** parameter is required.</span></span>

 <span data-ttu-id="455af-115">これには次の要件があります。</span><span class="sxs-lookup"><span data-stu-id="455af-115">The following requirements apply:</span></span>

-   <span data-ttu-id="455af-116">ディレクトリはコントローラー上に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="455af-116">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="455af-117">ドライブ文字で始まる完全なパスを指定する必要があります (たとえば、 `c:\WorkingDir`)。</span><span class="sxs-lookup"><span data-stu-id="455af-117">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="455af-118">パスはバックスラッシュ "`\`" で終了することはできません。</span><span class="sxs-lookup"><span data-stu-id="455af-118">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="455af-119">UNC パスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="455af-119">UNC paths are not supported.</span></span>

 <span data-ttu-id="455af-120">**-o**クライアントの再生アクティビティをキャプチャし、クライアント構成ファイルの要素によって指定されたパスの結果トレースファイルに保存し `<ResultDirectory>` `DReplayClient.xml` ます。</span><span class="sxs-lookup"><span data-stu-id="455af-120">**-o** Captures the clients' replay activity and saves it to a result trace file in the path specified by the `<ResultDirectory>` element in the client configuration file, `DReplayClient.xml`.</span></span>

 <span data-ttu-id="455af-121">**-o** パラメーターが指定されていない場合は、結果トレース ファイルは生成されません。</span><span class="sxs-lookup"><span data-stu-id="455af-121">When the **-o** parameter is not specified, the result trace file is not generated.</span></span> <span data-ttu-id="455af-122">コンソール出力は再生の最後に概要情報を返しますが、他の再生統計情報は提供されません。</span><span class="sxs-lookup"><span data-stu-id="455af-122">The console output returns summary information at the end of replay, but no other replay statistics are available.</span></span>

 <span data-ttu-id="455af-123">**-s** *target_server* [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散ワークロードの再生に使用するの対象インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="455af-123">**-s** *target_server* Specifies the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that the distributed workload should be replayed against.</span></span> <span data-ttu-id="455af-124">このパラメーターは、 **server_name[\instance name]** の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="455af-124">You must specify this parameter in the format **server_name[\instance name]**.</span></span>

 <span data-ttu-id="455af-125">"`localhost`" または "`.`" をターゲット サーバーとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="455af-125">You cannot use "`localhost`" or "`.`" as the target server.</span></span>

 <span data-ttu-id="455af-126">再生構成ファイル **の** セクションに `<Server>` 要素が指定されている場合、 `<ReplayOptions>` -s `DReplay.exe.replay.config`パラメーターは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="455af-126">The **-s** parameter is not required if the `<Server>` element is specified in the `<ReplayOptions>` section of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="455af-127">**-s** パラメーターが使用されている場合、再生構成ファイルの `<Server>` セクションの `<ReplayOptions>` 要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="455af-127">If the **-s** parameter is used, the `<Server>` element in the `<ReplayOptions>` section of the replay configuration file will be ignored.</span></span>

 <span data-ttu-id="455af-128">**-w** *クライアント*この必須パラメーターは、分散再生に参加するクライアントのコンピューター名を指定するコンマ区切りのリスト (スペースなし) です。</span><span class="sxs-lookup"><span data-stu-id="455af-128">**-w** *clients* This required parameter is a comma-separated list (without spaces) that specifies the computer names of clients that should participate in the distributed replay.</span></span> <span data-ttu-id="455af-129">IP アドレスは指定できません。</span><span class="sxs-lookup"><span data-stu-id="455af-129">IP addresses are not allowed.</span></span> <span data-ttu-id="455af-130">コントローラーにクライアントが既に登録されている必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="455af-130">Be aware that the clients must already be registered with the controller.</span></span>

> [!NOTE]
>  <span data-ttu-id="455af-131">クライアント サービスが開始するときに、クライアント構成ファイルで指定されているコントローラーにクライアントが登録されます。</span><span class="sxs-lookup"><span data-stu-id="455af-131">Each client registers with the controller that is specified in the client configuration file when the client service starts.</span></span>

 <span data-ttu-id="455af-132">**-c** *config_file*は、再生構成ファイルの完全なパスです。別の場所に格納されている場所を指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="455af-132">**-c** *config_file* Is the full path of the replay configuration file; used to specify the location when it is stored in a different location.</span></span>

 <span data-ttu-id="455af-133">再生構成ファイル **の既定値を使用する場合、** -c `DReplay.exe.replay.config`パラメーターは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="455af-133">The **-c** parameter is not required if you want to use the default values of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="455af-134">**-f** *status_interval*状態を表示する頻度 (秒単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="455af-134">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="455af-135">**-f** を指定しない場合は、既定の間隔は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="455af-135">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="455af-136">例</span><span class="sxs-lookup"><span data-stu-id="455af-136">Examples</span></span>
 <span data-ttu-id="455af-137">この例の分散再生では、変更された再生構成ファイル `DReplay.exe.replay.config`から多くの動作が派生しています。</span><span class="sxs-lookup"><span data-stu-id="455af-137">In this example, the distributed replay derives much of its behavior from a modified replay configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="455af-138">**-m** パラメーターは、 `controller1` というコンピューターがコントローラーとして動作するように指定しています。</span><span class="sxs-lookup"><span data-stu-id="455af-138">The **-m** parameter specifies that a computer named `controller1` acts as the controller.</span></span> <span data-ttu-id="455af-139">コントローラー サービスが別のコンピューターで実行されている場合は、コンピューター名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="455af-139">The computer name must be specified when the controller service is running on a different computer.</span></span>

-   <span data-ttu-id="455af-140">**-d** パラメーターは、コントローラーの中間ファイルの場所として `c:\WorkingDir`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="455af-140">The **-d** parameter specifies the location of the intermediate file on the controller, `c:\WorkingDir`.</span></span>

-   <span data-ttu-id="455af-141">**-o** パラメーターは、指定された各クライアントが再生アクティビティをキャプチャし、それを結果トレース ファイルに保存するように指定しています。</span><span class="sxs-lookup"><span data-stu-id="455af-141">The **-o** parameter specifies that each specified client capture the replay activity and save it to a result trace file.</span></span> <span data-ttu-id="455af-142">注:構成ファイル内の `<ResultTrace>` 要素は、行数と結果セットが記録される場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="455af-142">Note: The `<ResultTrace>` element in the configuration file can be used to specify if row count and result set be recorded.</span></span>

-   <span data-ttu-id="455af-143">**-w** パラメーターは、 `client1` から `client4` までのコンピューターがクライアントとして分散再生に参加するように指定しています。</span><span class="sxs-lookup"><span data-stu-id="455af-143">The **-w** parameter specifies that computers `client1` through `client4` participate as clients in the distributed replay.</span></span>

-   <span data-ttu-id="455af-144">**-c** パラメーターは、変更された構成ファイル `DReplay.exe.replay.config`を指すために使用されています。</span><span class="sxs-lookup"><span data-stu-id="455af-144">The **-c** parameter is used to point to the modified configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="455af-145">再生構成ファイル **の** 要素で `<Server>` 要素が指定されているため、 `<ReplayOptions>` -s `DReplay.exe.replay.config`パラメーターは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="455af-145">The **-s** parameter is not required because the `<Server>` element is specified in the `<ReplayOptions>` element of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="455af-146">管理ツールがコントローラーとは別のコンピューターから実行される場合、イベント再生段階は、次の構文で開始されます。</span><span class="sxs-lookup"><span data-stu-id="455af-146">The event replay stage is initiated with the following syntax, when the administration tool is run from a different computer than the controller:</span></span>

```
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config
```

 <span data-ttu-id="455af-147">同期シーケンス モードを指定するために、 `<SequencingMode>` ファイルの `DReplay.exe.replay.config` 要素が値 `synchronization`と同じに設定されます。</span><span class="sxs-lookup"><span data-stu-id="455af-147">To specify a synchronous sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `synchronization`.</span></span> <span data-ttu-id="455af-148">再生構成ファイルの `<ResultTrace>` セクションは、行数を記録するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="455af-148">The `<ResultTrace>` section of the replay configuration file is modified to specify that row count be recorded.</span></span> <span data-ttu-id="455af-149">これらの変更を示したものが、次の XML 例です。</span><span class="sxs-lookup"><span data-stu-id="455af-149">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance</Server>
        <SequencingMode>synchronization</SequencingMode>
        <ConnectTimeScale></ConnectTimeScale>
        <ThinkTimeScale></ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

 <span data-ttu-id="455af-150">ストレス シーケンス モードを指定するために、 `<SequencingMode>` ファイルの `DReplay.exe.replay.config` 要素が値 `stress`と同じに設定されます。</span><span class="sxs-lookup"><span data-stu-id="455af-150">To specify a stress sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `stress`.</span></span> <span data-ttu-id="455af-151">`<ConnectTimeScale>` および `<ThinkTimeScale>` 要素が値 `50` に設定されます (50% を指定する場合)。</span><span class="sxs-lookup"><span data-stu-id="455af-151">The `<ConnectTimeScale>` and `<ThinkTimeScale>` elements are set to the value `50` (to specify 50 percent).</span></span> <span data-ttu-id="455af-152">接続時間と待ち時間の詳細については、「 [Configure Distributed Replay](configure-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="455af-152">For more information about connect time and think time, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span> <span data-ttu-id="455af-153">これらの変更を示したものが、次の XML 例です。</span><span class="sxs-lookup"><span data-stu-id="455af-153">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance_name</Server>
        <SequencingMode>stress</SequencingMode>
        <ConnectTimeScale>50</ConnectTimeScale>
        <ThinkTimeScale>50</ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="455af-154">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="455af-154">Permissions</span></span>
 <span data-ttu-id="455af-155">対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="455af-155">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="455af-156">ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="455af-156">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="455af-157">詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="455af-157">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="455af-158">参照</span><span class="sxs-lookup"><span data-stu-id="455af-158">See Also</span></span>
 <span data-ttu-id="455af-159">[トレースデータ](replay-trace-data.md)[の再生再生結果を確認](review-the-replay-results.md)[する:](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2)分散再生を使用して分散再生[SQL Server 分散再生フォーラム](https://social.technet.microsoft.com/Forums/sl/sqldru/)の分散再生[構成](configure-distributed-replay.md)し、SQL Server を使用して分散再生のロードテストを実行し、SQL Server を使用してをロードテストします。[第1部](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1) [SQL Server](sql-server-distributed-replay.md)</span><span class="sxs-lookup"><span data-stu-id="455af-159">[Replay Trace Data](replay-trace-data.md) [Review the Replay Results](review-the-replay-results.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md) [SQL Server Distributed Replay Forum](https://social.technet.microsoft.com/Forums/sl/sqldru/) [Using Distributed Replay to Load Test Your SQL Server - Part 2](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2) [Using Distributed Replay to Load Test Your SQL Server - Part 1](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)</span></span>


