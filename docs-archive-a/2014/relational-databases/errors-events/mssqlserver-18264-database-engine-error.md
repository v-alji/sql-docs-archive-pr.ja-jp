---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3edfeb82601e254c02df87cc4a978b9ab5e653e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642107"
---
# <a name="mssqlserver_18264"></a><span data-ttu-id="14755-102">MSSQLSERVER_18264</span><span class="sxs-lookup"><span data-stu-id="14755-102">MSSQLSERVER_18264</span></span>
    
## <a name="details"></a><span data-ttu-id="14755-103">詳細</span><span class="sxs-lookup"><span data-stu-id="14755-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14755-104">製品名</span><span class="sxs-lookup"><span data-stu-id="14755-104">Product Name</span></span>|<span data-ttu-id="14755-105">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="14755-105">Microsoft SQL Server</span></span>|  
|<span data-ttu-id="14755-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="14755-106">Event ID</span></span>|<span data-ttu-id="14755-107">18264</span><span class="sxs-lookup"><span data-stu-id="14755-107">18264</span></span>|  
|<span data-ttu-id="14755-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="14755-108">Event Source</span></span>|<span data-ttu-id="14755-109">MSSQLENGINE</span><span class="sxs-lookup"><span data-stu-id="14755-109">MSSQLENGINE</span></span>|  
|<span data-ttu-id="14755-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="14755-110">Component</span></span>|<span data-ttu-id="14755-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="14755-111">SQLEngine</span></span>|  
|<span data-ttu-id="14755-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="14755-112">Symbolic Name</span></span>|<span data-ttu-id="14755-113">STRMIO_DBDUMP</span><span class="sxs-lookup"><span data-stu-id="14755-113">STRMIO_DBDUMP</span></span>|  
|<span data-ttu-id="14755-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="14755-114">Message Text</span></span>|<span data-ttu-id="14755-115">データベースがバックアップされました。</span><span class="sxs-lookup"><span data-stu-id="14755-115">Database backed up.</span></span> <span data-ttu-id="14755-116">データベース: %s、作成日 (時間): %s(%s)、ダンプされたページ: %d、最初の LSN: %s、最後の LSN: %s、ダンプ デバイスの数: %d、デバイス情報: (%s)。</span><span class="sxs-lookup"><span data-stu-id="14755-116">Database: %s, creation date(time): %s(%s), pages dumped: %d, first LSN: %s, last LSN: %s, number of dump devices: %d, device information: (%s).</span></span> <span data-ttu-id="14755-117">このメッセージは情報提供だけを目的としています。</span><span class="sxs-lookup"><span data-stu-id="14755-117">This is an informational message only.</span></span> <span data-ttu-id="14755-118">ユーザーによる操作は不要です。</span><span class="sxs-lookup"><span data-stu-id="14755-118">No user action is required.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="14755-119">説明</span><span class="sxs-lookup"><span data-stu-id="14755-119">Explanation</span></span>  
 <span data-ttu-id="14755-120">既定では、バックアップが成功するたびに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにこの情報メッセージが追加されます。</span><span class="sxs-lookup"><span data-stu-id="14755-120">By default, every successful backup adds this informational message to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the system event log.</span></span> <span data-ttu-id="14755-121">トランザクション ログを頻繁にバックアップすると、これらのメッセージがすぐに蓄積され、他のメッセージを探すのが困難になるほど大きなエラー ログが生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="14755-121">If you very frequently back up the transaction log, these messages can accumulate quickly, creating very large error logs that can make finding other messages difficult.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14755-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="14755-122">User Action</span></span>  
 <span data-ttu-id="14755-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のトレース フラグ **3226** を使用すると、これらのログ エントリを除外できます。</span><span class="sxs-lookup"><span data-stu-id="14755-123">You can suppress these log entries by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace flag **3226**.</span></span> <span data-ttu-id="14755-124">頻度の高いログ バックアップを実行している場合やスクリプトがこれらのエントリに依存していない場合は、このトレース フラグを有効にすると便利です。</span><span class="sxs-lookup"><span data-stu-id="14755-124">Enabling this trace flag is useful if you are running frequent log backups and if none of your scripts depend on those entries.</span></span>  
  
 <span data-ttu-id="14755-125">トレース フラグの使用方法の詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="14755-125">For information about using trace flags, see SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14755-126">参照</span><span class="sxs-lookup"><span data-stu-id="14755-126">See Also</span></span>  
 [<span data-ttu-id="14755-127">トレース フラグ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="14755-127">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
