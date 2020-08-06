---
title: Transact-SQL スクリプトの再生 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5abf22a1201ac927f12ef9e4cfdd1f6d3026d00a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737248"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a><span data-ttu-id="297c6-102">Transact-SQL スクリプトの再生 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="297c6-102">Replay a Transact-SQL Script (SQL Server Profiler)</span></span>
  <span data-ttu-id="297c6-103">パフォーマンスの問題に対して考えられる解決策をテストする場合、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを再生し、変更を加える前と加えた後のパフォーマンスを比較します。</span><span class="sxs-lookup"><span data-stu-id="297c6-103">When you test possible solutions to a performance problem, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, and compare performance before and after your changes.</span></span>  
  
### <a name="to-replay-a-transact-sql-script"></a><span data-ttu-id="297c6-104">Transact-SQL スクリプトを再生するには</span><span class="sxs-lookup"><span data-stu-id="297c6-104">To replay a Transact-SQL script</span></span>  
  
1.  <span data-ttu-id="297c6-105">**[ファイル]** メニューの **[開く]** をポイントし、 **[スクリプト ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="297c6-105">On the **File** menu, point to **Open**, and then click **Script File**.</span></span>  
  
2.  <span data-ttu-id="297c6-106">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルを選択して開きます。</span><span class="sxs-lookup"><span data-stu-id="297c6-106">Select the [!INCLUDE[tsql](../../includes/tsql-md.md)] script file you want to open.</span></span> <span data-ttu-id="297c6-107">再生に必要なイベントが [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトに含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="297c6-107">Make sure that the [!INCLUDE[tsql](../../includes/tsql-md.md)] script contains events necessary for replay.</span></span> <span data-ttu-id="297c6-108">詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="297c6-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
3.  <span data-ttu-id="297c6-109">**[再生]** メニューの **[開始]** をクリックし、スクリプトを再生するサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="297c6-109">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the script.</span></span>  
  
4.  <span data-ttu-id="297c6-110">**[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="297c6-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297c6-111">参照</span><span class="sxs-lookup"><span data-stu-id="297c6-111">See Also</span></span>  
 <span data-ttu-id="297c6-112">[トレースの再生](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="297c6-112">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="297c6-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="297c6-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
