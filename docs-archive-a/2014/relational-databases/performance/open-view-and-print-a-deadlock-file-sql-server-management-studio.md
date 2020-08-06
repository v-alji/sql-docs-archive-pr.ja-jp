---
title: デッドロック ファイルを開く、表示、および印刷する方法 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08bacd7a99e45e10163216c69057b167088441ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642747"
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a><span data-ttu-id="3b2f7-102">デッドロック ファイルを開く、表示、および印刷する方法 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3b2f7-102">Open, View, and Print a Deadlock File (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3b2f7-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でデッドロックが発生したら、デッドロック情報をキャプチャしてファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-103">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] generates a deadlock, you can capture and save the deadlock information to a file.</span></span> <span data-ttu-id="3b2f7-104">保存したデッドロック ファイルは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で開いて表示または印刷できます。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-104">After you have saved the deadlock file, you can open it in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view or print.</span></span>  
  
### <a name="to-open-and-view-a-deadlock-file"></a><span data-ttu-id="3b2f7-105">デッドロック ファイルを開いて表示するには</span><span class="sxs-lookup"><span data-stu-id="3b2f7-105">To open and view a deadlock file</span></span>  
  
1.  <span data-ttu-id="3b2f7-106">で、[**ファイル**] メニューの [開く] をポイントし、[ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **ファイル**] をクリックします。 **Open**</span><span class="sxs-lookup"><span data-stu-id="3b2f7-106">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="3b2f7-107">**[ファイルを開く]** ダイアログ ボックスで、 **[ファイルの種類]** ボックスの一覧から [SQL デッドロック ファイル] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-107">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="3b2f7-108">これにより、デッドロック ファイルだけが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-108">You will now have a filtered list of only deadlock files.</span></span>  
  
### <a name="to-print-a-deadlock-file"></a><span data-ttu-id="3b2f7-109">デッドロック ファイルを印刷するには</span><span class="sxs-lookup"><span data-stu-id="3b2f7-109">To print a deadlock file</span></span>  
  
1.  <span data-ttu-id="3b2f7-110">**で** [ファイル] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-110">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="3b2f7-111">**[ファイルを開く]** ダイアログ ボックスで、 **[ファイルの種類]** ボックスの一覧から [SQL デッドロック ファイル] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-111">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="3b2f7-112">これにより、デッドロック ファイルだけが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-112">You will now have a filtered list of only deadlock files.</span></span>  
  
3.  <span data-ttu-id="3b2f7-113">印刷するデッドロック ファイルを選択して、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-113">Select the deadlock file you want to print, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="3b2f7-114">**[ファイル]** メニューの **[印刷]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b2f7-114">On the **File** menu, click **Print.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b2f7-115">参照</span><span class="sxs-lookup"><span data-stu-id="3b2f7-115">See Also</span></span>  
 [<span data-ttu-id="3b2f7-116">Deadlock Graph の保存 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="3b2f7-116">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
  
