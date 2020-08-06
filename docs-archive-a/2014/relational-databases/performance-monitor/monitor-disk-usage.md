---
title: ディスクの使用量の監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51479b024864322d34dc3b0208e29e93d7454184
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739744"
---
# <a name="monitor-disk-usage"></a><span data-ttu-id="9f2ac-102">ディスクの使用量の監視</span><span class="sxs-lookup"><span data-stu-id="9f2ac-102">Monitor Disk Usage</span></span>
  <span data-ttu-id="9f2ac-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Microsoft Windows オペレーティング システムの入出力 (I/O) 呼び出しを使用して、ディスクに対する読み取りおよび書き込み操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="9f2ac-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses Microsoft Windows operating system input/output (I/O) calls to perform read and write operations on your disk.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9f2ac-104">では、ディスク I/O を実行する時期と方法が管理されます。ただし、基本的な I/O 操作は Windows オペレーティング システムで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9f2ac-104">manages when and how disk I/O is performed, but the Windows operating system performs the underlying I/O operations.</span></span> <span data-ttu-id="9f2ac-105">I/O サブシステムには、システム バス、ディスク コントローラー カード、ディスク、テープ ドライブ、CD-ROM ドライブなど、多数の I/O 装置が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9f2ac-105">The I/O subsystem includes the system bus, disk controller cards, disks, tape drives, CD-ROM drive, and many other I/O devices.</span></span> <span data-ttu-id="9f2ac-106">ディスク I/O は、頻繁にシステムのボトルネックの原因となります。</span><span class="sxs-lookup"><span data-stu-id="9f2ac-106">Disk I/O is frequently the cause of bottlenecks in a system.</span></span>  
  
 <span data-ttu-id="9f2ac-107">ディスク利用状況の監視には、次の 2 つの領域があります。</span><span class="sxs-lookup"><span data-stu-id="9f2ac-107">Monitoring disk activity involves two areas of focus:</span></span>  
  
-   <span data-ttu-id="9f2ac-108">ディスク I/O の監視と、過度なページングの検出</span><span class="sxs-lookup"><span data-stu-id="9f2ac-108">Monitoring Disk I/O and Detecting Excess Paging</span></span>  
  
-   <span data-ttu-id="9f2ac-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成されるディスク利用状況の隔離</span><span class="sxs-lookup"><span data-stu-id="9f2ac-109">Isolating Disk Activity That [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Creates</span></span>  
  
 <span data-ttu-id="9f2ac-110">詳細については、「[ディスク使用量の監視](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f2ac-110">For more information see, [Monitoring Disk Usage](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)</span></span>  
  
  
