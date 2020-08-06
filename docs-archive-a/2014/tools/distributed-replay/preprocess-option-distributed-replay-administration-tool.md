---
title: 前処理オプション (分散再生管理ツール) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7f168d45b03473d958e202bd75116f4519d2fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634188"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a><span data-ttu-id="e2c32-102">前処理オプション (Distributed Replay 管理ツール)</span><span class="sxs-lookup"><span data-stu-id="e2c32-102">Preprocess Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="e2c32-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生管理ツールは、 `DReplay.exe` 分散再生コントローラーとの通信に使用できるコマンドラインツールです。</span><span class="sxs-lookup"><span data-stu-id="e2c32-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="e2c32-104">このトピックでは、 **preprocess** コマンド ライン オプションとそれに対応する構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-104">This topic describes the **preprocess** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="e2c32-105">**preprocess** オプションは、前処理段階を開始します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-105">The **preprocess** option initiates the preprocess stage.</span></span> <span data-ttu-id="e2c32-106">この段階では、ターゲット サーバーに対して、コントローラーが入力トレース データの再生の準備を行います。</span><span class="sxs-lookup"><span data-stu-id="e2c32-106">During this stage, the controller prepares the input trace data for replay against the target server.</span></span>

 <span data-ttu-id="e2c32-107">![トピック リンク アイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン") 管理ツールの構文で使用される構文表記規則の詳細については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c32-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="e2c32-108">構文</span><span class="sxs-lookup"><span data-stu-id="e2c32-108">Syntax</span></span>

```

      dreplay preprocess [-mcontroller] -iinput_trace_file
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="e2c32-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2c32-109">Parameters</span></span>
 <span data-ttu-id="e2c32-110">**-m** *コントローラー*コントローラーのコンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="e2c32-111">"`localhost`" または "`.`" を使用してローカル コンピューターを参照できます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="e2c32-112">**-m** パラメーターが指定されていない場合、ローカル コンピューターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="e2c32-113">**-i** *input_trace_file* 、など、コントローラー上の入力トレースファイルの完全なパスを指定し `D:\Mytrace.trc` ます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-113">**-i** *input_trace_file* Specifies the full path of the input trace file on the controller, such as `D:\Mytrace.trc`.</span></span> <span data-ttu-id="e2c32-114">**-i** パラメーターは必須です。</span><span class="sxs-lookup"><span data-stu-id="e2c32-114">The **-i** parameter is required.</span></span>

 <span data-ttu-id="e2c32-115">同じディレクトリにロールオーバー ファイルがある場合は、自動的に読み込まれて使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-115">If there are rollover files in the same directory, they will be loaded and used automatically.</span></span> <span data-ttu-id="e2c32-116">ファイルは、ファイル ロールオーバー名前付け規則に準拠する必要があります (例: `Mytrace.trc`、`Mytrace_1.trc`、`Mytrace_2.trc`、`Mytrace_3.trc`、... `Mytrace_n.trc`)。</span><span class="sxs-lookup"><span data-stu-id="e2c32-116">The files must follow the file rollover naming convention, for example: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, ... `Mytrace_n.trc`.</span></span>

> [!NOTE]
>  <span data-ttu-id="e2c32-117">コントローラーとは別のコンピューターで管理ツールを使用している場合は、このパラメーターにローカル パスを使用できるように、コントローラーに入力トレース ファイルをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c32-117">If you are using the administration tool on a different computer than the controller, you will need to copy the input trace files to the controller so that a local path can be used for this parameter.</span></span>

 <span data-ttu-id="e2c32-118">**-d** *controller_working_dir*中間ファイルを格納するコントローラー上のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-118">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="e2c32-119">**-d** パラメーターは必須です。</span><span class="sxs-lookup"><span data-stu-id="e2c32-119">The **-d** parameter is required.</span></span>

 <span data-ttu-id="e2c32-120">これには次の要件があります。</span><span class="sxs-lookup"><span data-stu-id="e2c32-120">The following requirements apply:</span></span>

-   <span data-ttu-id="e2c32-121">ディレクトリはコントローラー上に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c32-121">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="e2c32-122">ドライブ文字で始まる完全なパスを指定する必要があります (たとえば、 `c:\WorkingDir`)。</span><span class="sxs-lookup"><span data-stu-id="e2c32-122">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="e2c32-123">パスはバックスラッシュ "`\`" で終了することはできません。</span><span class="sxs-lookup"><span data-stu-id="e2c32-123">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="e2c32-124">UNC パスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e2c32-124">UNC paths are not supported.</span></span>

 <span data-ttu-id="e2c32-125">**-c** *config_file*は、前処理構成ファイルの完全なパスです。別の場所に格納されている場合に、前処理構成ファイルの場所を指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-125">**-c** *config_file* Is the full path of the preprocess configuration file; used to specify the location of the preprocess configuration file when stored in a different location.</span></span> <span data-ttu-id="e2c32-126">このパラメーターは UNC パスにするか、または管理ツールを実行するコンピューター上にローカルに置くことができます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-126">This parameter can be a UNC path, or can reside locally on the computer where you run the administration tool.</span></span>

 <span data-ttu-id="e2c32-127">**-c** パラメーターは、フィルターが必要ない場合または最大アイドル時間を変更しない場合は、必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e2c32-127">The **-c** parameter is not required if no filtering is needed, or if you do not want to modify the maximum idle time.</span></span>

 <span data-ttu-id="e2c32-128">**-c** パラメーターが指定されない場合は、既定の前処理構成ファイル `DReplay.exe.preprocess.config`が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-128">Without the **-c** parameter, the default preprocess configuration file, `DReplay.exe.preprocess.config`, is used.</span></span>

 <span data-ttu-id="e2c32-129">**-f** *status_interval*ステータスメッセージを表示する頻度 (秒単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-129">**-f** *status_interval* Specifies the frequency (in seconds) at which to display status messages.</span></span>

 <span data-ttu-id="e2c32-130">**-f** を指定しない場合は、既定の間隔は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="e2c32-130">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="e2c32-131">例</span><span class="sxs-lookup"><span data-stu-id="e2c32-131">Examples</span></span>
 <span data-ttu-id="e2c32-132">この例では、すべての既定の設定で前処理段階が開始されます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-132">In this example, the preprocess stage is initiated with all of the default settings.</span></span> <span data-ttu-id="e2c32-133">値 `localhost` は、コントローラー サービスが管理ツールと同じコンピューターで実行されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-133">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span> <span data-ttu-id="e2c32-134">*input_trace_file* パラメーターは、入力トレース データ `c:\mytrace.trc`の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-134">The *input_trace_file* parameter specifies the location of the input trace data, `c:\mytrace.trc`.</span></span> <span data-ttu-id="e2c32-135">トレース ファイルのフィルターがないため、 **-c** パラメーターを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e2c32-135">Because there is no trace file filtering involved, the **-c** parameter does have to be specified.</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir
```

 <span data-ttu-id="e2c32-136">この例では、前処理段階が開始され、変更した前処理構成ファイルが指定されます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-136">In this example, the preprocess stage is initiated and a modified preprocess configuration file is specified.</span></span> <span data-ttu-id="e2c32-137">前の例とは異なり、 **-c** パラメーターを使用して、別の場所に格納されている変更された構成ファイルを指定しています。</span><span class="sxs-lookup"><span data-stu-id="e2c32-137">Unlike the previous example, the **-c** parameter is used to point to the modified configuration file, if you have stored it in a different location.</span></span> <span data-ttu-id="e2c32-138">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-138">For example:</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config
```

 <span data-ttu-id="e2c32-139">変更された前処理構成ファイルでは、分散再生中にシステム セッションを除外するフィルター条件が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-139">In the modified preprocess configuration file, a filter condition is added that filters out system sessions during distributed replay.</span></span> <span data-ttu-id="e2c32-140">`<PreprocessModifiers>` 要素を前処理構成ファイル `DReplay.exe.preprocess.config`で変更することで、フィルターが追加されます。</span><span class="sxs-lookup"><span data-stu-id="e2c32-140">The filter is added by modifying the `<PreprocessModifiers>` element in the preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span>

 <span data-ttu-id="e2c32-141">変更された構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e2c32-141">The following shows an example of the modified configuration file:</span></span>

```
<?xml version='1.0'?>
<Options>
    <PreprocessModifiers>
        <IncSystemSession>No</IncSystemSession>
        <MaxIdleTime>-1</MaxIdleTime>
    </PreprocessModifiers>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="e2c32-142">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="e2c32-142">Permissions</span></span>
 <span data-ttu-id="e2c32-143">対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c32-143">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="e2c32-144">ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c32-144">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="e2c32-145">詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c32-145">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2c32-146">参照</span><span class="sxs-lookup"><span data-stu-id="e2c32-146">See Also</span></span>
 <span data-ttu-id="e2c32-147">[入力トレースデータ SQL Server を準備](prepare-the-input-trace-data.md)[分散再生](sql-server-distributed-replay.md)[構成分散再生](configure-distributed-replay.md)</span><span class="sxs-lookup"><span data-stu-id="e2c32-147">[Prepare the Input Trace Data](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md)</span></span>


