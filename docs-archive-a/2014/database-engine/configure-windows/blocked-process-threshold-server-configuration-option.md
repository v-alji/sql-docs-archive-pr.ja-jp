---
title: blocked process threshold サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9d5b61aaf23a8e74cb11afbf4e8bdb958fde6abe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736781"
---
# <a name="blocked-process-threshold-server-configuration-option"></a><span data-ttu-id="0e91e-102">blocked process threshold サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="0e91e-102">blocked process threshold Server Configuration Option</span></span>
  <span data-ttu-id="0e91e-103">ブロックされたプロセスのレポートを生成するためのしきい値を秒単位で指定するには、 **blocked process threshold** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="0e91e-103">Use the **blocked process threshold** option to specify the threshold, in seconds, at which blocked process reports are generated.</span></span> <span data-ttu-id="0e91e-104">しきい値は 0 ～ 86,400 の範囲で設定できます。</span><span class="sxs-lookup"><span data-stu-id="0e91e-104">The threshold can be set from 0 to 86,400.</span></span> <span data-ttu-id="0e91e-105">既定では、ブロックされているプロセスのレポートは生成されません。</span><span class="sxs-lookup"><span data-stu-id="0e91e-105">By default, no blocked process reports are produced.</span></span> <span data-ttu-id="0e91e-106">システム タスクや、検出可能なデッドロックを生成しないリソースで待機しているタスクの場合、このイベントは生成されません。</span><span class="sxs-lookup"><span data-stu-id="0e91e-106">This event is not generated for system tasks or for tasks that are waiting on resources that do not generate detectable deadlocks.</span></span>  
  
 <span data-ttu-id="0e91e-107">このイベントが生成されたときに [警告](../../ssms/agent/alerts.md) が実行されるように定義できます。</span><span class="sxs-lookup"><span data-stu-id="0e91e-107">You can define an [alert](../../ssms/agent/alerts.md) to be executed when this event is generated.</span></span> <span data-ttu-id="0e91e-108">たとえば、ブロック状態を処理する適切な操作を行うために、管理者を呼び出すように選択できます。</span><span class="sxs-lookup"><span data-stu-id="0e91e-108">So for example, you can choose to page the administrator to take appropriate action to handle the blocking situation.</span></span>  
  
 <span data-ttu-id="0e91e-109">blocked process threshold オプションでは、デッドロック監視バックグラウンド スレッドを使用して、設定されたしきい値より長い間待機しているか、またはしきい値の数倍の時間待機しているタスクの一覧を調べます。</span><span class="sxs-lookup"><span data-stu-id="0e91e-109">Blocked process threshold uses the deadlock monitor background thread to walk through the list of tasks waiting for a time greater than or multiples of the configured threshold.</span></span> <span data-ttu-id="0e91e-110">イベントは、ブロックされた各タスクの報告間隔ごとに 1 回生成されます。</span><span class="sxs-lookup"><span data-stu-id="0e91e-110">The event is generated once per reporting interval for each of the blocked tasks.</span></span>  
  
 <span data-ttu-id="0e91e-111">ブロックされたプロセスのレポートは、ベスト エフォートの原則で行われます。</span><span class="sxs-lookup"><span data-stu-id="0e91e-111">The blocked process report is done on a best effort basis.</span></span> <span data-ttu-id="0e91e-112">リアルタイムまたはリアルタイムに近い報告は保証されていません。</span><span class="sxs-lookup"><span data-stu-id="0e91e-112">There is no guarantee of any real-time or even close to real-time reporting.</span></span>  
  
 <span data-ttu-id="0e91e-113">この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="0e91e-113">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0e91e-114">例</span><span class="sxs-lookup"><span data-stu-id="0e91e-114">Examples</span></span>  
 <span data-ttu-id="0e91e-115">次の例では、 `blocked process threshold` を `20` 秒に設定して、ブロックされたタスクごとに、ブロックされたプロセスのレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="0e91e-115">The following example sets the `blocked process threshold` to `20` seconds, generating a blocked process report for each task that is blocked.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e91e-116">参照</span><span class="sxs-lookup"><span data-stu-id="0e91e-116">See Also</span></span>  
 <span data-ttu-id="0e91e-117">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e91e-117">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="0e91e-118">Blocked Process Report イベント クラス</span><span class="sxs-lookup"><span data-stu-id="0e91e-118">Blocked Process Report Event Class</span></span>](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
