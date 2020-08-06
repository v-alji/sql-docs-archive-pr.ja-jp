---
title: cancel オプション (分散再生管理ツール) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
ms.openlocfilehash: d132fbf5ce541a2bdab82e44dc55e6fc92df536d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641920"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a><span data-ttu-id="4362f-102">cancel オプション (Distributed Replay 管理ツール)</span><span class="sxs-lookup"><span data-stu-id="4362f-102">Cancel Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="4362f-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生管理ツールは、 `DReplay.exe` 分散再生コントローラーとの通信に使用できるコマンドラインツールです。</span><span class="sxs-lookup"><span data-stu-id="4362f-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="4362f-104">このトピックでは、 **cancel** コマンド ライン オプションとそれに対応する構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="4362f-104">This topic describes the **cancel** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="4362f-105">**cancel** オプションは、コントローラーで実行されている現在の操作をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="4362f-105">The **cancel** option cancels the current operation that is running on the controller.</span></span>

 <span data-ttu-id="4362f-106">![トピック リンク アイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン") 管理ツールの構文で使用される構文表記規則の詳細については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4362f-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="4362f-107">構文</span><span class="sxs-lookup"><span data-stu-id="4362f-107">Syntax</span></span>

```

dreplay cancel [-mcontroller] [-q] 
```

#### <a name="parameters"></a><span data-ttu-id="4362f-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4362f-108">Parameters</span></span>
 <span data-ttu-id="4362f-109">**-m** *コントローラー*コントローラーのコンピューター名。</span><span class="sxs-lookup"><span data-stu-id="4362f-109">**-m** *controller* The computer name of the controller.</span></span> <span data-ttu-id="4362f-110">"`localhost`" または "`.`" を使用してローカル コンピューターを参照できます。</span><span class="sxs-lookup"><span data-stu-id="4362f-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="4362f-111">**-m** パラメーターが指定されていない場合、ローカル コンピューターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4362f-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="4362f-112">**-q**Quiet モード。</span><span class="sxs-lookup"><span data-stu-id="4362f-112">**-q** Quiet mode.</span></span> <span data-ttu-id="4362f-113">確認のプロンプトは表示されません。</span><span class="sxs-lookup"><span data-stu-id="4362f-113">Does not prompt for confirmation.</span></span>

 <span data-ttu-id="4362f-114">**-q** パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="4362f-114">The **-q** parameter is optional.</span></span>

## <a name="examples"></a><span data-ttu-id="4362f-115">例</span><span class="sxs-lookup"><span data-stu-id="4362f-115">Examples</span></span>
 <span data-ttu-id="4362f-116">次の例では、非表示モードでキャンセル要求が送信されます。</span><span class="sxs-lookup"><span data-stu-id="4362f-116">In the following example, a cancel request is submitted in quiet mode.</span></span> <span data-ttu-id="4362f-117">値 `localhost` は、コントローラー サービスが管理ツールと同じコンピューターで実行されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="4362f-117">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay cancel -m localhost -q
```

## <a name="permissions"></a><span data-ttu-id="4362f-118">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="4362f-118">Permissions</span></span>
 <span data-ttu-id="4362f-119">対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4362f-119">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="4362f-120">ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4362f-120">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="4362f-121">詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4362f-121">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4362f-122">参照</span><span class="sxs-lookup"><span data-stu-id="4362f-122">See Also</span></span>
 [<span data-ttu-id="4362f-123">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="4362f-123">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)


