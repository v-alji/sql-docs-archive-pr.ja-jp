---
title: SQL Server 管理オブジェクト (SMO) プログラミングガイド |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server]
- SQL Server Management Objects
- programming [SMO]
ms.assetid: 4cde2b85-2a31-4cac-8d16-7a4196066193
author: stevestein
ms.author: sstein
ms.openlocfilehash: 863e3fc90f750f91611a6fa75655783c7802ec23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711845"
---
# <a name="sql-server-management-objects-smo-programming-guide"></a><span data-ttu-id="131f6-102">SQL Server 管理オブジェクト (SMO) プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="131f6-102">SQL Server Management Objects (SMO) Programming Guide</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="131f6-103">管理オブジェクト (SMO) は、管理のすべての側面をプログラミングできるように設計されたオブジェクトのコレクションです [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="131f6-103">Management Objects (SMO) is a collection of objects that are designed for programming all aspects of managing [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="131f6-104">レプリケーション管理オブジェクト (RMO) は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション管理をカプセル化するオブジェクトの集まりです。</span><span class="sxs-lookup"><span data-stu-id="131f6-104">Replication Management Objects (RMO) is a collection of objects that encapsulates [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication management.</span></span>  
  
|<span data-ttu-id="131f6-105">トピック</span><span class="sxs-lookup"><span data-stu-id="131f6-105">Topic</span></span>|<span data-ttu-id="131f6-106">説明</span><span class="sxs-lookup"><span data-stu-id="131f6-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="131f6-107">SMO プログラムの作成</span><span class="sxs-lookup"><span data-stu-id="131f6-107">Creating SMO Programs</span></span>](create-program/creating-smo-programs.md)<br /><br /> [<span data-ttu-id="131f6-108">プログラミング特有のタスク</span><span class="sxs-lookup"><span data-stu-id="131f6-108">Programming Specific Tasks</span></span>](tasks/programming-specific-tasks.md)|<span data-ttu-id="131f6-109">Microsoft.SqlServer.management、Microsoft.SqlServer.Management.NotificationServices、Microsoft.SqlServer.Management.Smo、Microsoft.SqlServer.Management.Smo.Agent、Microsoft.SqlServer.Management.Smo.Broker、Microsoft.SqlServer.Management.Smo.Mail、Microsoft.SqlServer.Management.Smo.RegisteredServers、Microsoft.SqlServer.Management.Smo.Wmi、および Microsoft.SqlServer.Management.Trace 名前空間内の SMO オブジェクトのプログラミングについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="131f6-109">Provides information about programming the SMO objects in the Microsoft.SqlServer.management, Microsoft.SqlServer.Management.NotificationServices, Microsoft.SqlServer.Management.Smo, Microsoft.SqlServer.Management.Smo.Agent, Microsoft.SqlServer.Management.Smo.Broker, Microsoft.SqlServer.Management.Smo.Mail, Microsoft.SqlServer.Management.Smo.RegisteredServers, Microsoft.SqlServer.Management.Smo.Wmi, and Microsoft.SqlServer.Management.Trace namespaces.</span></span><br /><br /> <span data-ttu-id="131f6-110">データベースを定義し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を管理するプログラムを記述する手順についても説明します。</span><span class="sxs-lookup"><span data-stu-id="131f6-110">This includes instructions to write programs that define databases and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="131f6-111">SMO を使用して、データベースの作成、バックアップの実行、ジョブの作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成、権限の割り当て、およびその他のさまざまな管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="131f6-111">You can use SMO to create databases, perform backups, create jobs, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assign permissions, and to perform many other administrative tasks.</span></span>|  
|[<span data-ttu-id="131f6-112">開発者ガイド &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="131f6-112">Developer's Guide &#40;Replication&#41;</span></span>](../replication/concepts/replication-developer-documentation.md)|<span data-ttu-id="131f6-113">Microsoft.SqlServer.Replication 名前空間内の RMO オブジェクトのプログラミングについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="131f6-113">Provides information about programming the RMO objects in the Microsoft.SqlServer.Replication namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="131f6-114">参照</span><span class="sxs-lookup"><span data-stu-id="131f6-114">See Also</span></span>  
 [<span data-ttu-id="131f6-115">開発者ガイド &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="131f6-115">Developer's Guide &#40;Replication&#41;</span></span>](../replication/concepts/replication-developer-documentation.md)  
  
  
