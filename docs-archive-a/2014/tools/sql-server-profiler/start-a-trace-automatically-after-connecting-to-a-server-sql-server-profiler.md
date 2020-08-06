---
title: サーバーへの接続後の自動的なトレースの開始 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- automatic trace start
- traces [SQL Server], starting
- starting trace automatically
ms.assetid: d74b848d-e796-49af-a8c5-dd69230f3a78
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2c8cae3e47a6f48014cbafe588dde782c097260
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719166"
---
# <a name="start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler"></a><span data-ttu-id="5192e-102">サーバーへの接続後の自動的なトレースの開始 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="5192e-102">Start a Trace Automatically after Connecting to a Server (SQL Server Profiler)</span></span>
  <span data-ttu-id="5192e-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]のインスタンスに接続したら、自動的にトレースが開始されるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5192e-103">This topic describes how to start traces automatically after connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-start-a-trace-automatically-after-connecting-to-a-server-with-sql-server-profiler"></a><span data-ttu-id="5192e-104">SQL Server Profiler を使用してサーバーへの接続後に自動的にトレースが開始されるようにするには</span><span class="sxs-lookup"><span data-stu-id="5192e-104">To start a trace automatically after connecting to a server with SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="5192e-105">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5192e-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="5192e-106">**[接続の確立直後にトレースを開始する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="5192e-106">Select the **Start tracing immediately after making a connection** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5192e-107">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5192e-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="5192e-108">トレースのプロパティを編集する場合は、まずこのチェック ボックスをオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5192e-108">To edit trace properties, you must first turn this setting off.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5192e-109">参照</span><span class="sxs-lookup"><span data-stu-id="5192e-109">See Also</span></span>  
 [<span data-ttu-id="5192e-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="5192e-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
