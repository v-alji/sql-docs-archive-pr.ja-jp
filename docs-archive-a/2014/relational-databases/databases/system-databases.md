---
title: システム データベース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65deee685c2205a7c6e41ed86f71c69639555d7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711990"
---
# <a name="system-databases"></a><span data-ttu-id="1aeac-102">システム データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-102">System Databases</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1aeac-103">には、次のシステム データベースが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1aeac-103">includes the following system databases.</span></span>  
  
|<span data-ttu-id="1aeac-104">システム データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-104">System database</span></span>|<span data-ttu-id="1aeac-105">説明</span><span class="sxs-lookup"><span data-stu-id="1aeac-105">Description</span></span>|  
|---------------------|-----------------|  
|[<span data-ttu-id="1aeac-106">master データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-106">master Database</span></span>](master-database.md)|<span data-ttu-id="1aeac-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスのシステムレベルの情報をすべて記録します。</span><span class="sxs-lookup"><span data-stu-id="1aeac-107">Records all the system-level information for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="1aeac-108">msdb データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-108">msdb Database</span></span>](msdb-database.md)|<span data-ttu-id="1aeac-109">警告やジョブのスケジュールを設定するために SQL Server エージェントにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-109">Is used by SQL Server Agent for scheduling alerts and jobs.</span></span>|  
|[<span data-ttu-id="1aeac-110">model データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-110">model Database</span></span>](model-database.md)|<span data-ttu-id="1aeac-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスで作成されたすべてのデータベースのテンプレートとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-111">Is used as the template for all databases created on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1aeac-112">データベース サイズ、照合順序、復旧モデル、およびその他のデータベース オプションなどの **model** データベースに変更を加えると、その変更内容は、それ以降に作成されるすべてのデータベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-112">Modifications made to the **model** database, such as database size, collation, recovery model, and other database options, are applied to any databases created afterward.</span></span>|  
|[<span data-ttu-id="1aeac-113">Resource データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-113">Resource Database</span></span>](resource-database.md)|<span data-ttu-id="1aeac-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に装備されているシステム オブジェクトを格納する読み取り専用のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="1aeac-114">Is a read-only database that contains system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1aeac-115">システム オブジェクトは、物理的には **Resource** データベースに保存されていますが、すべてのデータベースの **sys** スキーマに論理的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-115">System objects are physically persisted in the **Resource** database, but they logically appear in the **sys** schema of every database.</span></span>|  
|[<span data-ttu-id="1aeac-116">tempdb データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-116">tempdb Database</span></span>](tempdb-database.md)|<span data-ttu-id="1aeac-117">一時オブジェクトや生成途中の結果セットを保存するためのワークスペースです。</span><span class="sxs-lookup"><span data-stu-id="1aeac-117">Is a workspace for holding temporary objects or intermediate result sets.</span></span>|  
  
## <a name="modifying-system-data"></a><span data-ttu-id="1aeac-118">システム データの変更</span><span class="sxs-lookup"><span data-stu-id="1aeac-118">Modifying System Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1aeac-119">では、ユーザーは、システム テーブル、システム ストアド プロシージャ、カタログ ビューなどのシステム オブジェクトに含まれている情報を直接更新できません。</span><span class="sxs-lookup"><span data-stu-id="1aeac-119">does not support users directly updating the information in system objects such as system tables, system stored procedures, and catalog views.</span></span> <span data-ttu-id="1aeac-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、代わりに完全な管理ツール セットが用意されています。ユーザーは、これらのツールを使用して、システムを完全に管理し、データベース内のすべてのユーザーとオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-120">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a complete set of administrative tools that let users fully administer their system and manage all users and objects in a database.</span></span> <span data-ttu-id="1aeac-121">コーディネートは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1aeac-121">These include the following:</span></span>  
  
-   <span data-ttu-id="1aeac-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]などの管理ユーティリティ。</span><span class="sxs-lookup"><span data-stu-id="1aeac-122">Administration utilities, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="1aeac-123">SQL-SMO API。</span><span class="sxs-lookup"><span data-stu-id="1aeac-123">SQL-SMO API.</span></span> <span data-ttu-id="1aeac-124">このツールを使用すると、プログラマはアプリケーションに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を管理するための完全な機能を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-124">This lets programmers include complete functionality for administering [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in their applications.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="1aeac-125">スクリプトとストアド プロシージャ。</span><span class="sxs-lookup"><span data-stu-id="1aeac-125">scripts and stored procedures.</span></span> <span data-ttu-id="1aeac-126">これらのツールでは、システム ストアド プロシージャと [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-126">These can use system stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements.</span></span>  
  
 <span data-ttu-id="1aeac-127">上記のツールを使用すると、アプリケーションをシステム オブジェクトの変更による影響から保護できます。</span><span class="sxs-lookup"><span data-stu-id="1aeac-127">These tools shield applications from changes in the system objects.</span></span> <span data-ttu-id="1aeac-128">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に追加された新機能をサポートするために、そのバージョンのシステム テーブルを変更する必要があることがあります。</span><span class="sxs-lookup"><span data-stu-id="1aeac-128">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sometimes has to change the system tables in new versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support new functionality that is being added in that version.</span></span> <span data-ttu-id="1aeac-129">多くの場合、システム テーブルを直接参照する SELECT ステートメントを実行しているアプリケーションでは、旧形式のシステム テーブルに依存しています。</span><span class="sxs-lookup"><span data-stu-id="1aeac-129">Applications issuing SELECT statements that directly reference system tables are frequently dependent on the old format of the system tables.</span></span> <span data-ttu-id="1aeac-130">そのような場合、システム テーブルに対して SELECT ステートメントを実行するアプリケーションが作成し直されるまで、サイトを新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードできない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1aeac-130">Sites may not be able to upgrade to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until they have rewritten applications that are selecting from system tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1aeac-131">では、システム ストアド プロシージャ、DDL、および SQL-SMO の公開された各インターフェイスを考慮し、これらの旧バージョンとの互換性を維持できるように機能します。</span><span class="sxs-lookup"><span data-stu-id="1aeac-131">considers the system stored procedures, DDL, and SQL-SMO published interfaces, and works to maintain the backward compatibility of these interfaces.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1aeac-132">システム テーブルで定義されたトリガーでは、システムの動作が変更されることがあるので、このようなトリガーはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1aeac-132">does not support triggers defined on the system tables, because they might modify the operation of the system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1aeac-133">システム データベースを UNC 共有ディレクトリに置くことはできません。</span><span class="sxs-lookup"><span data-stu-id="1aeac-133">System databases cannot reside on UNC share directories.</span></span>  
  
## <a name="viewing-system-database-data"></a><span data-ttu-id="1aeac-134">システム データベース データの表示</span><span class="sxs-lookup"><span data-stu-id="1aeac-134">Viewing System Database Data</span></span>  
 <span data-ttu-id="1aeac-135">システム テーブルに対する直接的なクエリを実行するような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、アプリケーションが必要とする情報を取得する方法が他にない場合を除いて、作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="1aeac-135">You should not code [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that directly query the system tables, unless that is the only way to obtain the information that is required by the application.</span></span> <span data-ttu-id="1aeac-136">代わりに、アプリケーションで、次のツールを使用してカタログ情報やシステム情報を取得することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1aeac-136">Instead, applications should obtain catalog and system information by using the following:</span></span>  
  
-   <span data-ttu-id="1aeac-137">システム カタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="1aeac-137">System catalog views</span></span>  
  
-   <span data-ttu-id="1aeac-138">SQL-SMO。</span><span class="sxs-lookup"><span data-stu-id="1aeac-138">SQL-SMO</span></span>  
  
-   <span data-ttu-id="1aeac-139">WMI (Windows Management Instrumentation) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="1aeac-139">Windows Management Instrumentation (WMI) interface</span></span>  
  
-   <span data-ttu-id="1aeac-140">カタログ関数、メソッド、属性、または、ADO、OLE DB、ODBC などのアプリケーションで使用されるデータ API のプロパティ。</span><span class="sxs-lookup"><span data-stu-id="1aeac-140">Catalog functions, methods, attributes, or properties of the data API used in the application, such as ADO, OLE DB, or ODBC.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="1aeac-141">システム ストアド プロシージャと組み込み関数。</span><span class="sxs-lookup"><span data-stu-id="1aeac-141">system stored procedures and built-in functions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1aeac-142">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1aeac-142">Related Tasks</span></span>  
 [<span data-ttu-id="1aeac-143">システム データベースのバックアップと復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1aeac-143">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="1aeac-144">オブジェクトエクスプローラーのシステムオブジェクトを非表示にする</span><span class="sxs-lookup"><span data-stu-id="1aeac-144">Hide System Objects in Object Explorer</span></span>](../../ssms/object/object-explorer.md)  
  
## <a name="related-content"></a><span data-ttu-id="1aeac-145">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="1aeac-145">Related Content</span></span>  
 [<span data-ttu-id="1aeac-146">カタログ ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1aeac-146">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
 [<span data-ttu-id="1aeac-147">データベース</span><span class="sxs-lookup"><span data-stu-id="1aeac-147">Databases</span></span>](databases.md)  
  
  
