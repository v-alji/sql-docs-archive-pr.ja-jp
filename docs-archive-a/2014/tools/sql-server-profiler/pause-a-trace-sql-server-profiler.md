---
title: トレースを一時停止する (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: stevestein
ms.author: sstein
ms.openlocfilehash: cdc9dbbd01099b1d33787a72b0bd59b65cea722e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711249"
---
# <a name="pause-a-trace-sql-server-profiler"></a><span data-ttu-id="12f96-102">トレースの一時停止 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="12f96-102">Pause a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="12f96-103">トレースを一時停止すると、トレースを再開するまで、それ以上のイベント データはキャプチャされません。</span><span class="sxs-lookup"><span data-stu-id="12f96-103">Pausing a trace prevents further event data from being captured until the trace is restarted.</span></span>  
  
 <span data-ttu-id="12f96-104">トレースを一時停止すると、トレースを再開するまで、それ以上のイベント データはキャプチャされません。</span><span class="sxs-lookup"><span data-stu-id="12f96-104">When you pause a trace, you prevent event data from being captured until the trace is restarted.</span></span> <span data-ttu-id="12f96-105">トレースを再開すると、トレース操作が再開されます。</span><span class="sxs-lookup"><span data-stu-id="12f96-105">Restarting a trace lets trace operations resume.</span></span> <span data-ttu-id="12f96-106">キャプチャを再開しても、それ以前にキャプチャしたデータが失われることはありません。</span><span class="sxs-lookup"><span data-stu-id="12f96-106">No previously captured data is lost after a restart.</span></span> <span data-ttu-id="12f96-107">トレースを再開すると、その時点から、データのキャプチャが再開されます。</span><span class="sxs-lookup"><span data-stu-id="12f96-107">When the trace is restarted, data capturing resumes from that point onward.</span></span> <span data-ttu-id="12f96-108">トレースを一時停止している間は、名前、イベント、列、およびフィルターを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="12f96-108">While a trace is paused, you can change the name, events, columns, and filters.</span></span> <span data-ttu-id="12f96-109">ただし、トレース データの送信先またはサーバー接続は変更できません。</span><span class="sxs-lookup"><span data-stu-id="12f96-109">However, you cannot change the destinations to which you are sending the trace data, nor change the server connection.</span></span>  
  
### <a name="to-pause-a-trace"></a><span data-ttu-id="12f96-110">トレースを一時停止するには</span><span class="sxs-lookup"><span data-stu-id="12f96-110">To pause a trace</span></span>  
  
1.  <span data-ttu-id="12f96-111">実行中のトレースを含んでいるウィンドウを選択します。</span><span class="sxs-lookup"><span data-stu-id="12f96-111">Select a window that contains a running trace.</span></span>  
  
2.  <span data-ttu-id="12f96-112">**[ファイル]** メニューの **[トレースの一時停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12f96-112">On the **File** menu, click **Pause Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f96-113">参照</span><span class="sxs-lookup"><span data-stu-id="12f96-113">See Also</span></span>  
 [<span data-ttu-id="12f96-114">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="12f96-114">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
