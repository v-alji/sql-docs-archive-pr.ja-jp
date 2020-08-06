---
title: SQL Server データベース エンジン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server]
- SQL Server Database Engine
ms.assetid: 65e2f424-1386-45a6-8912-bd053f434073
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a6c243115e940f7af085c0068d2ca5c277aa5162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632070"
---
# <a name="sql-server-database-engine"></a><span data-ttu-id="7b82f-102">SQL Server データベース エンジン</span><span class="sxs-lookup"><span data-stu-id="7b82f-102">SQL Server Database Engine</span></span>
  <span data-ttu-id="7b82f-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] は、データの格納、処理、セキュリティ確保のための中心的なサービスです。</span><span class="sxs-lookup"><span data-stu-id="7b82f-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="7b82f-104">[!INCLUDE[ssDE](../includes/ssde-md.md)]は、アクセス制御と高速トランザクション処理を提供しており、これらを活用すれば、企業内で最も大規模なデータ処理アプリケーションの要件にも対応できます。</span><span class="sxs-lookup"><span data-stu-id="7b82f-104">The [!INCLUDE[ssDE](../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications within your enterprise.</span></span>

 <span data-ttu-id="7b82f-105">[!INCLUDE[ssDE](../includes/ssde-md.md)]を使用すると、オンライン トランザクション処理やオンライン分析処理のデータのリレーショナル データベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7b82f-105">Use the [!INCLUDE[ssDE](../includes/ssde-md.md)] to create relational databases for online transaction processing or online analytical processing data.</span></span> <span data-ttu-id="7b82f-106">これには、データを格納するためのテーブル、インデックスなどのデータベース オブジェクト、ビュー、およびデータの表示、管理、セキュリティ保護のためのストアド プロシージャの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b82f-106">This includes creating tables for storing data, and database objects such as indexes, views, and stored procedures for viewing, managing, and securing data.</span></span> <span data-ttu-id="7b82f-107">データベース オブジェクトの管理には [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を、サーバー イベントのキャプチャには [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b82f-107">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the database objects, and [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to capture server events.</span></span>

 <span data-ttu-id="7b82f-108">領域の![小さいファイルフォルダー](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") **を参照**するアイコン[新機能 (データベースエンジン)](whats-new-in-sql-server-2016.md)</span><span class="sxs-lookup"><span data-stu-id="7b82f-108">**Browse Content by Area** ![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [What's New (Database Engine)](whats-new-in-sql-server-2016.md)</span></span>

 <span data-ttu-id="7b82f-109">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [SQL Server データベースエンジン旧バージョン](sql-server-database-engine-backward-compatibility.md)との互換性</span><span class="sxs-lookup"><span data-stu-id="7b82f-109">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Database Engine Backward Compatibility](sql-server-database-engine-backward-compatibility.md)</span></span>

 <span data-ttu-id="7b82f-110">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [SQL Server 管理ツール旧バージョン](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md)との互換性</span><span class="sxs-lookup"><span data-stu-id="7b82f-110">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Management Tools Backward Compatibility](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md)</span></span>

 <span data-ttu-id="7b82f-111">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[データベースの機能とタスク](../../2014/database-engine/database-engine-features-and-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="7b82f-111">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Database Features and Tasks](../../2014/database-engine/database-engine-features-and-tasks.md)</span></span>

 <span data-ttu-id="7b82f-112">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[テクニカルリファレンス](../../2014/database-engine/technical-reference-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="7b82f-112">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference](../../2014/database-engine/technical-reference-database-engine.md)</span></span>

 <span data-ttu-id="7b82f-113">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [transact-sql リファレンス](/sql/t-sql/language-reference)</span><span class="sxs-lookup"><span data-stu-id="7b82f-113">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Transact-SQL Reference](/sql/t-sql/language-reference)</span></span>

 <span data-ttu-id="7b82f-114">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [XQuery リファレンス](/sql/xquery/xquery-language-reference-sql-server)</span><span class="sxs-lookup"><span data-stu-id="7b82f-114">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [XQuery Reference](/sql/xquery/xquery-language-reference-sql-server)</span></span>

## <a name="see-also"></a><span data-ttu-id="7b82f-115">参照</span><span class="sxs-lookup"><span data-stu-id="7b82f-115">See Also</span></span>
 [<span data-ttu-id="7b82f-116">SQL Server リソース センター</span><span class="sxs-lookup"><span data-stu-id="7b82f-116">SQL Server Resource Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=219676)


