---
title: トレースを実行するための Transact-SQL スクリプトの作成 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d4b4bebb2a3e05e3de12e59c53ccca9c980afd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711257"
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a><span data-ttu-id="47b0f-102">トレースを実行するための Transact-SQL スクリプトの作成 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="47b0f-102">Create a Transact-SQL Script for Running a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="47b0f-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、既存のトレース ファイルまたはトレース テーブルから Transact-SQL スクリプトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="47b0f-103">This topic describes how to create a Transact-SQL script from an existing trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a><span data-ttu-id="47b0f-104">トレースを実行するための Transact-SQL スクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="47b0f-104">To create a Transact-SQL script to run a trace</span></span>  
  
1.  <span data-ttu-id="47b0f-105">トレース ファイルまたはトレース テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="47b0f-105">Open a trace file or table.</span></span> <span data-ttu-id="47b0f-106">詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="47b0f-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="47b0f-107">**[ファイル]** メニューで **[エクスポート]** 、 **[トレース定義のスクリプト]** の順にポイントし、トレースするサーバーに対応するバージョンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="47b0f-107">On the**File**menu, point to **Export**, point to **Script Trace Definition**, and then click the version that corresponds to the server you want to trace.</span></span>  
  
3.  <span data-ttu-id="47b0f-108">**[名前を付けて保存]** ダイアログ ボックスで、スクリプト ファイルの名前を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47b0f-108">In the **Save As** dialog box, enter a name for the script file, and then click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b0f-109">参照</span><span class="sxs-lookup"><span data-stu-id="47b0f-109">See Also</span></span>  
 <span data-ttu-id="47b0f-110">[SQL Server プロファイラーのテンプレートと権限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="47b0f-110">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="47b0f-111">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="47b0f-111">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
