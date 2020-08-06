---
title: '[SQL Server エージェントのプロパティ] ([履歴] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d67ff3da97e11292abcac03958fe1e423b35d7d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644269"
---
# <a name="sql-server-agent-properties-history-page"></a><span data-ttu-id="4afb5-102">SQL Server エージェントのプロパティ ([履歴] ページ)</span><span class="sxs-lookup"><span data-stu-id="4afb5-102">SQL Server Agent Properties (History Page)</span></span>
  <span data-ttu-id="4afb5-103">このページを使用すると、エージェントサービスの履歴ログを管理するための設定を表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="4afb5-103">Use this page to view and modify settings for managing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service history log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4afb5-104">Options</span><span class="sxs-lookup"><span data-stu-id="4afb5-104">Options</span></span>  
 <span data-ttu-id="4afb5-105">**[ジョブ履歴ログのサイズを制限する]**</span><span class="sxs-lookup"><span data-stu-id="4afb5-105">**Limit size of job history log**</span></span>  
 <span data-ttu-id="4afb5-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがログで保持するジョブ履歴情報のサイズの上限を設定します。</span><span class="sxs-lookup"><span data-stu-id="4afb5-106">Sets limits for the amount of job history information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains in the log.</span></span>  
  
 <span data-ttu-id="4afb5-107">**[ジョブ履歴ログの最大サイズ (行)]**</span><span class="sxs-lookup"><span data-stu-id="4afb5-107">**Maximum job history log size (in rows)**</span></span>  
 <span data-ttu-id="4afb5-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって保持される行の最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="4afb5-108">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains.</span></span> <span data-ttu-id="4afb5-109">ログの大きさがここで設定した行数に達すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは新しい行を入力するときにログの最も古い行を削除します。</span><span class="sxs-lookup"><span data-stu-id="4afb5-109">When the log grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="4afb5-110">**[ジョブごとのジョブ履歴の最大行数]**</span><span class="sxs-lookup"><span data-stu-id="4afb5-110">**Maximum job history rows per job**</span></span>  
 <span data-ttu-id="4afb5-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによってジョブごとに保持される行の最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="4afb5-111">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains per job.</span></span> <span data-ttu-id="4afb5-112">特定のジョブの履歴サイズがここで設定した行数に達すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは新しい行を入力するときにログの最も古い行を削除します。</span><span class="sxs-lookup"><span data-stu-id="4afb5-112">When the history for a particular job grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="4afb5-113">**[エージェントの履歴を削除する]**</span><span class="sxs-lookup"><span data-stu-id="4afb5-113">**Remove agent history**</span></span>  
 <span data-ttu-id="4afb5-114">ログ内のエントリの保存期間が指定された期間を超えたときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがそのエントリを削除するように指定します。</span><span class="sxs-lookup"><span data-stu-id="4afb5-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will remove entries that have been in the log longer than a specified length of time.</span></span> <span data-ttu-id="4afb5-115">これは、履歴を削除するために、1 回だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="4afb5-115">This is a one-time execution to remove the history.</span></span> <span data-ttu-id="4afb5-116">繰り返し実行する必要がある場合は、クリーンアップ ジョブのメンテナンス プランを作成してスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="4afb5-116">If a reoccurring job is needed, create and schedule a maintenance plan with a cleanup job.</span></span>  
  
 <span data-ttu-id="4afb5-117">**[経過期間]**</span><span class="sxs-lookup"><span data-stu-id="4afb5-117">**Older than**</span></span>  
 <span data-ttu-id="4afb5-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがエントリを保持する期間を設定します。</span><span class="sxs-lookup"><span data-stu-id="4afb5-118">Sets the amount of time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will retain entries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4afb5-119">参照</span><span class="sxs-lookup"><span data-stu-id="4afb5-119">See Also</span></span>  
 [<span data-ttu-id="4afb5-120">SQL Server エージェント エラー ログ</span><span class="sxs-lookup"><span data-stu-id="4afb5-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
