---
title: データベースのライフサイクル管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Data sync
- SQL Database
- Azure Training Kit
- Database development
- Database backup
- Database connection management
- Database community
- Backup and restore
- Database import and export
- SQL Data Sync
- Azure Service Dashboard
- SQL Server Management Studio
- Database management
- Database export
- SQL Server Data Tools
- SSMS
- SSDT
- Database migration
- Database connectivity
ms.assetid: 91da13a4-0eea-4e88-b608-dada881ff5f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a2c469b23e1ce4134767920547297b23ec030cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643949"
---
# <a name="database-lifecycle-management"></a><span data-ttu-id="93400-102">データベースのライフサイクル管理</span><span class="sxs-lookup"><span data-stu-id="93400-102">Database Lifecycle Management</span></span>
  <span data-ttu-id="93400-103">データベース ライフ サイクル管理 (DLM) は、データベースとデータ資産を管理するためのポリシー ベースのアプローチです。</span><span class="sxs-lookup"><span data-stu-id="93400-103">Database lifecycle management (DLM) is a policy-based approach to managing databases and data assets.</span></span> <span data-ttu-id="93400-104">DLM は製品ではなく、データベース アプリケーションのデータベース スキーマ、データ、およびメタデータを管理するための包括的なアプローチです。</span><span class="sxs-lookup"><span data-stu-id="93400-104">DLM is not a product but a comprehensive approach to managing the database schema, data, and metadata for a database application.</span></span> <span data-ttu-id="93400-105">DLM に対するよく考えられた積極的なアプローチにより、組織では、パフォーマンス、保護、可用性、およびコストの適切なレベルに応じてデータ リソースを管理できます。</span><span class="sxs-lookup"><span data-stu-id="93400-105">A thoughtful and proactive approach to DLM enables an organization to manage data resources according to appropriate levels of performance, protection, availability, and cost.</span></span>  
  
 <span data-ttu-id="93400-106">DLM では、まずプロジェクトのデザインと目的を考察することから始めます。次に、データベースの開発、テスト、構築、配置、管理、監視、およびバックアップの各操作を行ってから、最後にデータをアーカイブします。</span><span class="sxs-lookup"><span data-stu-id="93400-106">DLM begins with discussion of project design and intent, continues with database develop, test, build, deploy, maintain, monitor, and backup activities, and ends with data archive.</span></span> <span data-ttu-id="93400-107">このトピックでは、データベースの開発から始まり、構築、配置、監視の各操作を進める、DLM の段階の概要を示します (図 1)。</span><span class="sxs-lookup"><span data-stu-id="93400-107">This topic provides an overview of the stages of DLM that begin with database development and progress through build, deploy, and monitor actions (Figure 1).</span></span> <span data-ttu-id="93400-108">また、データ管理作業や、インポートとエクスポート、バックアップ、移行、同期などのデータ移行操作も示します。</span><span class="sxs-lookup"><span data-stu-id="93400-108">Also included are data management activities, and data portability operations like import/export, backup, migrate, and sync.</span></span>  
  
 <span data-ttu-id="93400-109">トピック全体を確認するには、「 [データベース ライフ サイクル管理 (DLM)](https://go.microsoft.com/fwlink/?LinkId=276949)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93400-109">To read the complete topic, see [Database Lifecycle Management (DLM)](https://go.microsoft.com/fwlink/?LinkId=276949).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93400-110">参照</span><span class="sxs-lookup"><span data-stu-id="93400-110">See Also</span></span>  
 <span data-ttu-id="93400-111">[Azure ホーム ページ](https://www.windowsazure.com/) </span><span class="sxs-lookup"><span data-stu-id="93400-111">[Azure Home Page](https://www.windowsazure.com/) </span></span>  
 <span data-ttu-id="93400-112">[Azure デベロッパー センター](https://www.windowsazure.com/develop/overview/) </span><span class="sxs-lookup"><span data-stu-id="93400-112">[Azure Developer Center](https://www.windowsazure.com/develop/overview/) </span></span>  
 <span data-ttu-id="93400-113">[Azure 管理センター](https://www.windowsazure.com/manage/overview/) </span><span class="sxs-lookup"><span data-stu-id="93400-113">[Azure Manage Center](https://www.windowsazure.com/manage/overview/) </span></span>  
 <span data-ttu-id="93400-114">[Azure チーム ブログ](https://www.windowsazure.com/community/blog/) </span><span class="sxs-lookup"><span data-stu-id="93400-114">[Azure Team Blog](https://www.windowsazure.com/community/blog/) </span></span>  
 [<span data-ttu-id="93400-115">Azure サポート オプション</span><span class="sxs-lookup"><span data-stu-id="93400-115">Azure Support Options</span></span>](https://www.windowsazure.com/support/contact/)  
  
