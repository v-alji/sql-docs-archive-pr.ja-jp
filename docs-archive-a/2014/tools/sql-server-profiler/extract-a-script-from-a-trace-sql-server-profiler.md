---
title: トレースからのスクリプトの抽出 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6633fafb8a39b189093044ef39694afa601af7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711246"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a><span data-ttu-id="7e6fa-102">トレースからのスクリプトの抽出 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="7e6fa-102">Extract a Script from a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="7e6fa-103">このトピックでは、トレース ファイルまたはテーブルから [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントを抽出し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]スクリプト ファイルとして保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e6fa-103">This topic describes how to extract [!INCLUDE[tsql](../../includes/tsql-md.md)] events from a trace file or table and save them as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a><span data-ttu-id="7e6fa-104">トレース ファイルまたはテーブルから Transact-SQL スクリプトを抽出するには</span><span class="sxs-lookup"><span data-stu-id="7e6fa-104">To extract a Transact-SQL script from a trace file or table</span></span>  
  
1.  <span data-ttu-id="7e6fa-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルに保存する [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントが含まれているトレース ファイルまたはテーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7e6fa-105">Open a trace file or table that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] events that you want to save to a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="7e6fa-106">詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e6fa-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="7e6fa-107">**[ファイル]** メニューで **[エクスポート]** 、 **[SQL Server イベントの抽出]** の順にポイントし、 **[Transact-SQL イベントの抽出]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e6fa-107">On the **File** menu, point to **Export**, point to **Extract SQL Server Events**, and then click **Extract Transact-SQL Events**.</span></span>  
  
3.  <span data-ttu-id="7e6fa-108">**[名前を付けて保存]** ダイアログ ボックスで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルの名前を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e6fa-108">In the **Save As** dialog box, type a name for the [!INCLUDE[tsql](../../includes/tsql-md.md)] file, and click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6fa-109">参照</span><span class="sxs-lookup"><span data-stu-id="7e6fa-109">See Also</span></span>  
 [<span data-ttu-id="7e6fa-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="7e6fa-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
