---
title: DDL トリガーに関する情報の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cd71d188c2f53bd9872359199c07d700688552d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644893"
---
# <a name="get-information-about-ddl-triggers"></a><span data-ttu-id="04b29-102">DDL トリガーに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="04b29-102">Get Information About DDL Triggers</span></span>
  <span data-ttu-id="04b29-103">ここに記載されているカタログ ビューを使用すると、DDL トリガーに関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="04b29-103">The catalog views listed in this section can be used to get information about DDL Triggers.</span></span>  
  
 <span data-ttu-id="04b29-104">**DDL トリガーを起動できるイベントまたはイベント グループに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-104">**To get information about the events or event groups on which a DDL trigger can fire.**</span></span>  
  
-   [<span data-ttu-id="04b29-105">sys.trigger_event_types &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-105">sys.trigger_event_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 <span data-ttu-id="04b29-106">**トリガーの依存関係を表示するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-106">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="04b29-107">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-107">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="04b29-108">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-108">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="04b29-109">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-109">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a><span data-ttu-id="04b29-110">データベース スコープの DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="04b29-110">Database-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="04b29-111">**データベース スコープのトリガーに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-111">**To get information about database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="04b29-112">sys.triggers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-112">sys.triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 <span data-ttu-id="04b29-113">**トリガーを起動するデータベース イベントに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-113">**To get information about database events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="04b29-114">sys.trigger_events &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-114">sys.trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 <span data-ttu-id="04b29-115">**データベース スコープのトリガーの定義を表示するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-115">**To view the definition of a database-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="04b29-116">sys.sql_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-116">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 <span data-ttu-id="04b29-117">**データベース スコープの CLR トリガーに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-117">**To get information about CLR database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="04b29-118">sys.assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-118">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a><span data-ttu-id="04b29-119">サーバー スコープの DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="04b29-119">Server-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="04b29-120">**サーバー スコープのトリガーに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-120">**To get information about server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="04b29-121">sys.server_triggers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-121">sys.server_triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 <span data-ttu-id="04b29-122">**トリガーを起動するサーバー イベントに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-122">**To get information about server events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="04b29-123">sys.server_trigger_events &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-123">sys.server_trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 <span data-ttu-id="04b29-124">**サーバー スコープのトリガーの定義を表示するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-124">**To view the definition of a server-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="04b29-125">sys.server_sql_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-125">sys.server_sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 <span data-ttu-id="04b29-126">**サーバー スコープの CLR トリガーに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="04b29-126">**To get information about CLR server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="04b29-127">sys.server_assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04b29-127">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="04b29-128">参照</span><span class="sxs-lookup"><span data-stu-id="04b29-128">See Also</span></span>  
 [<span data-ttu-id="04b29-129">DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="04b29-129">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
