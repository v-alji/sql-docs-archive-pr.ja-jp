---
title: status オプション (分散再生管理ツール) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ce3d07bc357c5f3788fb6f995a43399021b3553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711361"
---
# <a name="status-option-distributed-replay-administration-tool"></a><span data-ttu-id="f7b15-102">status オプション (Distributed Replay 管理ツール)</span><span class="sxs-lookup"><span data-stu-id="f7b15-102">Status Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="f7b15-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生管理ツールは、 `DReplay.exe` 分散再生コントローラーとの通信に使用できるコマンドラインツールです。</span><span class="sxs-lookup"><span data-stu-id="f7b15-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="f7b15-104">このトピックでは、 **status** コマンド ライン オプションとそれに対応する構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7b15-104">This topic describes the **status** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="f7b15-105">**status** オプションは、コントローラーに照会し、現在の状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="f7b15-105">The **status** option queries the controller and displays the current status.</span></span>

 <span data-ttu-id="f7b15-106">![トピック リンク アイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン") 管理ツールの構文で使用される構文表記規則の詳細については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7b15-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="f7b15-107">構文</span><span class="sxs-lookup"><span data-stu-id="f7b15-107">Syntax</span></span>

```

dreplay status [-mcontroller] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="f7b15-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7b15-108">Parameters</span></span>
 <span data-ttu-id="f7b15-109">**-m** *コントローラー*コントローラーのコンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7b15-109">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="f7b15-110">"`localhost`" または "`.`" を使用してローカル コンピューターを参照できます。</span><span class="sxs-lookup"><span data-stu-id="f7b15-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="f7b15-111">**-m** パラメーターが指定されていない場合、ローカル コンピューターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7b15-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="f7b15-112">**-f** *status_interval*状態を表示する頻度 (秒単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7b15-112">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="f7b15-113">**-f** パラメーターを指定しない場合は、既定の間隔は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="f7b15-113">If the **-f** parameter is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="f7b15-114">例</span><span class="sxs-lookup"><span data-stu-id="f7b15-114">Examples</span></span>
 <span data-ttu-id="f7b15-115">次の例では、現在の状態は 60 秒ごとに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7b15-115">In the following example, the current status is displayed every 60 seconds.</span></span> <span data-ttu-id="f7b15-116">値 `localhost` は、コントローラー サービスが管理ツールと同じコンピューターで実行されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="f7b15-116">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay status -m localhost -f 60
```

## <a name="permissions"></a><span data-ttu-id="f7b15-117">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="f7b15-117">Permissions</span></span>
 <span data-ttu-id="f7b15-118">対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7b15-118">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="f7b15-119">ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7b15-119">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="f7b15-120">詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7b15-120">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7b15-121">参照</span><span class="sxs-lookup"><span data-stu-id="f7b15-121">See Also</span></span>
 <span data-ttu-id="f7b15-122">[SQL Server 分散再生](sql-server-distributed-replay.md) [transact-sql デバッガー](../../relational-databases/scripting/transact-sql-debugger.md)</span><span class="sxs-lookup"><span data-stu-id="f7b15-122">[SQL Server Distributed Replay](sql-server-distributed-replay.md) [Transact-SQL Debugger](../../relational-databases/scripting/transact-sql-debugger.md)</span></span>


