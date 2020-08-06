---
title: トレース表示の既定値の設定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], defaults
ms.assetid: d471aaed-c40c-4c55-a993-835e6394b5d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2272f23511f955b3509d4a9e357100a96f5f8852
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737189"
---
# <a name="set-trace-display-defaults-sql-server-profiler"></a><span data-ttu-id="ee3fd-102">トレース表示の既定値の設定 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="ee3fd-102">Set Trace Display Defaults (SQL Server Profiler)</span></span>
  <span data-ttu-id="ee3fd-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] がトレースをトレース ウィンドウに表示する際に使用するフォントの種類やサイズ、スタイルを指定するツール オプションを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-103">This topic describes how to set tool options, which specify the font types, size, and style that [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] uses to display traces in the trace window.</span></span> <span data-ttu-id="ee3fd-104">また、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] により、すべての日付と時刻を、オペレーティング システムに構成されている地域設定で表示するよう指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-104">You can also specify that [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] displays all dates and times with the regional settings that are configured for your operating system.</span></span>  
  
### <a name="to-set-trace-display-defaults"></a><span data-ttu-id="ee3fd-105">トレース表示の既定値を設定するには</span><span class="sxs-lookup"><span data-stu-id="ee3fd-105">To set trace display defaults</span></span>  
  
1.  <span data-ttu-id="ee3fd-106">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-106">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="ee3fd-107">**[全般オプション]** ダイアログ ボックスで、 **[フォントの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-107">In the **General Options** dialog box, click **Choose Font**.</span></span>  
  
3.  <span data-ttu-id="ee3fd-108">**[フォント]** ダイアログ ボックスで、 **でのトレースの表示に使用する**[フォント名] **、** [スタイル] **、** [サイズ] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-108">In the **Font** dialog box, select the **Font**, the **Font style**, and **Size** to be used by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to display traces.</span></span>  
  
4.  <span data-ttu-id="ee3fd-109">**[OK]** をクリックして設定を適用し、 **[フォント]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-109">Click **OK**to apply the settings and close the **Font** dialog box.</span></span>  
  
5.  <span data-ttu-id="ee3fd-110">**[全般オプション]** ダイアログ ボックスで、 **[日時の値の表示に地域別設定を使用する]** チェック ボックスをオンにし、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] がトレースを表示する際にシステムに構成されている地域設定を使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-110">In the **General Options** dialog box, check **Use regional settings to display date and time values** to configure [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to use the regional settings that are configured for your system when it displays traces.</span></span>  
  
6.  <span data-ttu-id="ee3fd-111">**[OK]** をクリックして **[全般オプション]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ee3fd-111">Click **OK** to close the **General Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee3fd-112">参照</span><span class="sxs-lookup"><span data-stu-id="ee3fd-112">See Also</span></span>  
 [<span data-ttu-id="ee3fd-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ee3fd-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
