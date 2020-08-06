---
title: 利用状況モニター | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 71fd0d1172b4fcd5739a3af1a60246cc7dce3b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739757"
---
# <a name="activity-monitor"></a><span data-ttu-id="45ba0-102">利用状況モニター</span><span class="sxs-lookup"><span data-stu-id="45ba0-102">Activity Monitor</span></span>
  <span data-ttu-id="45ba0-103">利用状況モニターには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスおよびこれらのプロセスが現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに与える影響に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45ba0-103">Activity Monitor displays information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-activity-monitor"></a><span data-ttu-id="45ba0-104">利用状況モニターの利点</span><span class="sxs-lookup"><span data-stu-id="45ba0-104">Benefits of Activity Monitor</span></span>  
 <span data-ttu-id="45ba0-105">利用状況モニターは、[**概要**]、[**アクティブなユーザータスク**]、[**リソースの待機**]、[**データファイル I/o**]、および [最近の**コストの高いクエリ**] の展開と折りたたみが可能なペインを含むタブ付きドキュメントウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="45ba0-105">Activity Monitor is a tabbed document window that has the following expandable and collapsible panes: **Overview**, **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries**.</span></span> <span data-ttu-id="45ba0-106">ペインを展開すると、利用状況モニターによってインスタンスに対して情報のクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="45ba0-106">When any pane is expanded, Activity Monitor queries the instance for information.</span></span> <span data-ttu-id="45ba0-107">ペインを折りたたむと、そのペインのすべての利用状況クエリが停止します。</span><span class="sxs-lookup"><span data-stu-id="45ba0-107">When a pane is collapsed, all querying activity stops for that pane.</span></span> <span data-ttu-id="45ba0-108">また、1 つ以上のペインを同時に展開し、インスタンスのさまざまな利用状況を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="45ba0-108">You can also expand one or more panes at the same time to view different kinds of activity on the instance.</span></span>  
  
 <span data-ttu-id="45ba0-109">[**アクティブなユーザータスク**]、[**リソースの待機**]、[**データファイル I/o**]、および [最近の負荷の**高いクエリ**] ペインに含まれている列については、次の方法で表示をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="45ba0-109">For the columns that are included in the **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries** panes, you can customize the display in the following ways:</span></span>  
  
1.  <span data-ttu-id="45ba0-110">列の順序を並べ替えるには、列見出しをクリックして見出しのリボン内の別の場所にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45ba0-110">To rearrange the order of the columns, click the column heading and drag it to another location in the heading ribbon.</span></span>  
  
2.  <span data-ttu-id="45ba0-111">列を並べ替えるには、列名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45ba0-111">To sort a column, click the column name.</span></span>  
  
3.  <span data-ttu-id="45ba0-112">1 つ以上の列をフィルター処理するには、列見出しの下矢印をクリックして値を選択します。</span><span class="sxs-lookup"><span data-stu-id="45ba0-112">To filter on one or more columns, click the drop-down arrow in the column heading, and then select a value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="45ba0-113">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="45ba0-113">Related Tasks</span></span>  
 <span data-ttu-id="45ba0-114">利用状況モニターに関連したタスクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="45ba0-114">Use the following tasks to get started with Activity Monitor:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45ba0-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="45ba0-115">**Description**</span></span>|<span data-ttu-id="45ba0-116">**トピック**</span><span class="sxs-lookup"><span data-stu-id="45ba0-116">**Topic**</span></span>|  
|<span data-ttu-id="45ba0-117">利用状況モニターを開く方法、および利用状況モニターの更新間隔の設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45ba0-117">Describes how to open Activity Monitor and how to set the Activity Monitor refresh interval.</span></span>|[<span data-ttu-id="45ba0-118">利用状況モニターを開く方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="45ba0-118">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|<span data-ttu-id="45ba0-119">サーバー パフォーマンスおよびアクティビティの監視に関するトピックを紹介します。</span><span class="sxs-lookup"><span data-stu-id="45ba0-119">Links to topics for server performance and activity monitoring.</span></span>|[<span data-ttu-id="45ba0-120">サーバーのパフォーマンスと利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="45ba0-120">Server Performance and Activity Monitoring</span></span>](../performance/server-performance-and-activity-monitoring.md)|  
  
  
