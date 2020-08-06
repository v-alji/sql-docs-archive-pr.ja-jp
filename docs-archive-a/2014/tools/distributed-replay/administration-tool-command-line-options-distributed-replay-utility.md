---
title: 管理ツール コマンド ライン オプション (分散再生ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 506be071f44937d82902585e5a0621212083dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641921"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a><span data-ttu-id="af208-102">管理ツール コマンド ライン オプション (Distributed Replay Utility)</span><span class="sxs-lookup"><span data-stu-id="af208-102">Administration Tool Command-line Options (Distributed Replay Utility)</span></span>
  <span data-ttu-id="af208-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生管理ツールは、 `DReplay.exe` 分散再生コントローラーとの通信に使用できるコマンドラインツールです。</span><span class="sxs-lookup"><span data-stu-id="af208-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="af208-104">管理ツールを使用して、コントローラー上の操作を開始、監視、取り消しできます。</span><span class="sxs-lookup"><span data-stu-id="af208-104">Use the administration tool to initiate, monitor, and cancel operations on the controller.</span></span>  
  
 <span data-ttu-id="af208-105">![トピック リンク アイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン") 管理ツールの構文で使用される構文表記規則の詳細については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af208-105">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af208-106">構文</span><span class="sxs-lookup"><span data-stu-id="af208-106">Syntax</span></span>  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a><span data-ttu-id="af208-107">解説</span><span class="sxs-lookup"><span data-stu-id="af208-107">Remarks</span></span>  
 <span data-ttu-id="af208-108">`DReplay.exe` では、次のコマンド ライン オプションを発行することができます。</span><span class="sxs-lookup"><span data-stu-id="af208-108">You can issue the following command-line options with `DReplay.exe`:</span></span>  
  
 <span data-ttu-id="af208-109">**preprocess**</span><span class="sxs-lookup"><span data-stu-id="af208-109">**preprocess**</span></span>  
 <span data-ttu-id="af208-110">前処理段階を開始します。</span><span class="sxs-lookup"><span data-stu-id="af208-110">Initiates the preprocess stage.</span></span> <span data-ttu-id="af208-111">コントローラーは、ターゲット サーバーに対する再生のために、運用環境からキャプチャした入力トレース データの準備を行います。</span><span class="sxs-lookup"><span data-stu-id="af208-111">The controller prepares the input trace data, which you captured from the production environment, for replay against the target server.</span></span>  
  
 <span data-ttu-id="af208-112">**再生 (replay)**</span><span class="sxs-lookup"><span data-stu-id="af208-112">**replay**</span></span>  
 <span data-ttu-id="af208-113">イベント再生段階を開始します。</span><span class="sxs-lookup"><span data-stu-id="af208-113">Initiates the event replay stage.</span></span> <span data-ttu-id="af208-114">コントローラーは、指定されたクライアントに再生データをディスパッチし、分散再生を開始して、クライアントを同期します。</span><span class="sxs-lookup"><span data-stu-id="af208-114">The controller dispatches replay data to the specified clients, launches the distributed replay, and synchronizes the clients.</span></span> <span data-ttu-id="af208-115">必要に応じて、選択された各クライアントは、再生アクティビティを記録し、結果トレース ファイルをローカルに保存します。</span><span class="sxs-lookup"><span data-stu-id="af208-115">Optionally, each client that was selected records the replay activity and saves result trace files locally.</span></span>  
  
 <span data-ttu-id="af208-116">**status**</span><span class="sxs-lookup"><span data-stu-id="af208-116">**status**</span></span>  
 <span data-ttu-id="af208-117">コントローラーにクエリし、現在の状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="af208-117">Queries the controller and displays the current status.</span></span>  
  
 <span data-ttu-id="af208-118">**cancel**</span><span class="sxs-lookup"><span data-stu-id="af208-118">**cancel**</span></span>  
 <span data-ttu-id="af208-119">コントローラーで実行されている現在の操作を取り消します。</span><span class="sxs-lookup"><span data-stu-id="af208-119">Cancels the current operation that is running on the controller.</span></span>  
  
 <span data-ttu-id="af208-120">コマンドの引数や例などの構文情報の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af208-120">For detailed syntax information that includes the command arguments and examples, see the following topics:</span></span>  
  
-   [<span data-ttu-id="af208-121">前処理オプション &#40;Distributed Replay 管理ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="af208-121">Preprocess Option &#40;Distributed Replay Administration Tool&#41;</span></span>](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="af208-122">replay オプション &#40;Distributed Replay 管理ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="af208-122">Replay Option &#40;Distributed Replay Administration Tool&#41;</span></span>](replay-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="af208-123">status オプション &#40;Distributed Replay 管理ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="af208-123">Status Option &#40;Distributed Replay Administration Tool&#41;</span></span>](status-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="af208-124">cancel オプション &#40;Distributed Replay 管理ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="af208-124">Cancel Option &#40;Distributed Replay Administration Tool&#41;</span></span>](cancel-option-distributed-replay-administration-tool.md)  
  
 <span data-ttu-id="af208-125">RPC は、言語イベントとしてではなく RPC として再生されます。</span><span class="sxs-lookup"><span data-stu-id="af208-125">RPCs are replayed as RPCs and not as language events.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="af208-126">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="af208-126">Permissions</span></span>  
 <span data-ttu-id="af208-127">対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af208-127">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="af208-128">ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="af208-128">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>  
  
 <span data-ttu-id="af208-129">詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af208-129">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af208-130">参照</span><span class="sxs-lookup"><span data-stu-id="af208-130">See Also</span></span>  
 [<span data-ttu-id="af208-131">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="af208-131">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)  
  
  
