---
title: トレースの停止 (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], stopping
- stopping traces
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 501ea4a4838f8e2ea42fc475c486466d48020a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719148"
---
# <a name="stop-a-trace-sql-server-profiler"></a><span data-ttu-id="d4e5c-102">トレースの停止 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="d4e5c-102">Stop a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="d4e5c-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、実行中のトレースを停止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-103">This topic describes how to stop a trace that is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="d4e5c-104">トレースを停止すると、データのキャプチャも停止します。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-104">Stopping a trace stops data from being captured.</span></span> <span data-ttu-id="d4e5c-105">トレースを停止した場合、トレースを再開すると、既にキャプチャしたデータは失われます。ただし、トレース ファイルまたはトレース テーブルにキャプチャしたデータが失われることはありません。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-105">After a trace is stopped, it cannot be restarted without losing previously captured data, unless the data has been captured to a trace file or trace table.</span></span> <span data-ttu-id="d4e5c-106">トレースを停止した後に、キャプチャしたデータをテーブルまたはファイルに保存することは可能です。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-106">You can also save the collected data to a table or file after stopping a trace.</span></span> <span data-ttu-id="d4e5c-107">トレースを停止しても、あらかじめ選択されているすべてのトレース プロパティは保存されます。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-107">All trace properties that were previously selected are preserved when a trace is stopped.</span></span> <span data-ttu-id="d4e5c-108">トレースを停止した後は、名前、イベント、列、およびフィルターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-108">When a trace is stopped, you can change the name, events, columns, and filters.</span></span>  
  
### <a name="to-stop-a-trace"></a><span data-ttu-id="d4e5c-109">トレースを停止するには</span><span class="sxs-lookup"><span data-stu-id="d4e5c-109">To stop a trace</span></span>  
  
1.  <span data-ttu-id="d4e5c-110">実行中のトレースを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-110">Select a trace that is running.</span></span>  
  
2.  <span data-ttu-id="d4e5c-111">**[ファイル]** メニューの **[トレースの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4e5c-111">On the **File** menu, click **Stop Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e5c-112">参照</span><span class="sxs-lookup"><span data-stu-id="d4e5c-112">See Also</span></span>  
 [<span data-ttu-id="d4e5c-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d4e5c-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
