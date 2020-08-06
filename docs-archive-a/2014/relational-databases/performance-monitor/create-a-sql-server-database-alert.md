---
title: SQL Server データベース警告の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fd0cc926412d64f7686744ee60840a32473d2386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739756"
---
# <a name="create-a-sql-server-database-alert"></a><span data-ttu-id="fa240-102">SQL Server データベース警告の作成</span><span class="sxs-lookup"><span data-stu-id="fa240-102">Create a SQL Server Database Alert</span></span>
  <span data-ttu-id="fa240-103">システム モニターでは、システム モニターのカウンターがしきい値に達したときに発生する警告を作成できます。</span><span class="sxs-lookup"><span data-stu-id="fa240-103">You can use System Monitor to create an alert that is raised when a threshold value for a System Monitor counter has been reached.</span></span> <span data-ttu-id="fa240-104">警告が発せられると、システム モニターは、その警告状況を処理するために記述されたカスタム アプリケーションなどのアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="fa240-104">In response to the alert, System Monitor launches an application, such as a custom application written to handle the alert condition.</span></span> <span data-ttu-id="fa240-105">たとえば、デッドロックの数が特定の値を超えたときに発生する警告を作成できます。</span><span class="sxs-lookup"><span data-stu-id="fa240-105">For example, you could create an alert that is raised when the number of deadlocks exceeds a specific value.</span></span>  
  
 <span data-ttu-id="fa240-106">警告は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用して定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="fa240-106">Alerts also can be defined by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="fa240-107">詳細については、「 [警告](../../ssms/agent/alerts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa240-107">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
 <span data-ttu-id="fa240-108">システム モニターを使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース警告を設定する方法の詳細については、「[SQL Server データベースの警告のセットアップ &#40;Windows&#41;](../performance/set-up-a-sql-server-database-alert-windows.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fa240-108">For more information about using System Monitor to set up a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database alert, see [Set Up a SQL Server Database Alert &#40;Windows&#41;](../performance/set-up-a-sql-server-database-alert-windows.md) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa240-109">参照</span><span class="sxs-lookup"><span data-stu-id="fa240-109">See Also</span></span>  
 <span data-ttu-id="fa240-110">[sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fa240-110">[sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql) </span></span>  
 [<span data-ttu-id="fa240-111">sys.sysperfinfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fa240-111">sys.sysperfinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql)  
  
  
