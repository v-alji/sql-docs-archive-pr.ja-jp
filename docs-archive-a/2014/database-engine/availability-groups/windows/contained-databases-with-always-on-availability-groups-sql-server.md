---
title: 包含データベースと Always On 可用性グループ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c8a0b41ee7224dad83fb41691a4898c15b7b38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632118"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a><span data-ttu-id="5b982-102">包含データベースと Always On 可用性グループ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5b982-102">Contained Databases with Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="5b982-103">このトピックには、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]と共に包含データベースを使用する方法に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5b982-103">This topic contains information about the using a contained database with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="5b982-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5b982-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="5b982-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="5b982-105">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="5b982-106">関連タスク</span><span class="sxs-lookup"><span data-stu-id="5b982-106">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5b982-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="5b982-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="5b982-108">包含データベースを可用性グループに追加する前に、その可用性グループの可用性レプリカをホストする各サーバー インスタンスで、`contained database authentication` サーバー オプションが `1` に設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5b982-108">Before adding a contained database to an availability group, ensure that the `contained database authentication` server option is set to `1` on every server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="5b982-109">詳細については、「 [contained database authentication サーバー構成オプション](../../configure-windows/contained-database-authentication-server-configuration-option.md) 」および「 [サーバー構成オプション &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)と共に包含データベースを使用する方法に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5b982-109">For more information, see [contained database authentication Server Configuration Option](../../configure-windows/contained-database-authentication-server-configuration-option.md) and [Server Configuration Options &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5b982-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="5b982-110">Related Tasks</span></span>  
  
-   [<span data-ttu-id="5b982-111">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5b982-111">Server Configuration Options &#40;SQL Server&#41;</span></span>](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b982-112">参照</span><span class="sxs-lookup"><span data-stu-id="5b982-112">See Also</span></span>  
 <span data-ttu-id="5b982-113">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5b982-113">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="5b982-114">包含データベース</span><span class="sxs-lookup"><span data-stu-id="5b982-114">Contained Databases</span></span>](../../../relational-databases/databases/contained-databases.md)  
  
  
