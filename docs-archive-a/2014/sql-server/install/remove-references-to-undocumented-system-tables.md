---
title: ドキュメントに記載されていないシステムテーブルへの参照を削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 45c38038ee3d3214e4303c0ddbe0110be926c37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720847"
---
# <a name="remove-references-to-undocumented-system-tables"></a><span data-ttu-id="e130b-102">ドキュメントに記載されていないシステム テーブルへの参照の削除</span><span class="sxs-lookup"><span data-stu-id="e130b-102">Remove references to undocumented system tables</span></span>
  <span data-ttu-id="e130b-103">以前のリリースのドキュメントには記載されていなかった多くのシステム テーブルが変更されたか、存在しなくなりました。そのため、アップグレード後にそのようなシステム テーブルを使用すると、エラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e130b-103">Many system tables that were undocumented in prior releases have changed or no longer exist; therefore, using these tables may cause errors after upgrading.</span></span> <span data-ttu-id="e130b-104">アップグレード アドバイザーはシステム テーブル名への参照を検索するので、システム テーブルと同じ名前のユーザー テーブルへの参照を報告します。</span><span class="sxs-lookup"><span data-stu-id="e130b-104">Because Upgrade Advisor looks for references to system table names, it will report references to any user tables that have the same names as system tables.</span></span>  
  
## <a name="component"></a><span data-ttu-id="e130b-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e130b-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="e130b-106">説明</span><span class="sxs-lookup"><span data-stu-id="e130b-106">Description</span></span>  
 <span data-ttu-id="e130b-107">ドキュメントに記載されていない以下のシステム テーブルは削除されました。</span><span class="sxs-lookup"><span data-stu-id="e130b-107">The following undocumented system tables are removed:</span></span>  
  
-   <span data-ttu-id="e130b-108">**spt_datatype_info**</span><span class="sxs-lookup"><span data-stu-id="e130b-108">**spt_datatype_info**</span></span>  
  
-   <span data-ttu-id="e130b-109">**spt_datatype_info_ext**</span><span class="sxs-lookup"><span data-stu-id="e130b-109">**spt_datatype_info_ext**</span></span>  
  
-   <span data-ttu-id="e130b-110">**spt_provider_types**</span><span class="sxs-lookup"><span data-stu-id="e130b-110">**spt_provider_types**</span></span>  
  
-   <span data-ttu-id="e130b-111">**spt_server_info**</span><span class="sxs-lookup"><span data-stu-id="e130b-111">**spt_server_info**</span></span>  
  
-   <span data-ttu-id="e130b-112">**spt_values**</span><span class="sxs-lookup"><span data-stu-id="e130b-112">**spt_values**</span></span>  
  
-   <span data-ttu-id="e130b-113">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="e130b-113">**sysfulltextnotify**</span></span>  
  
-   <span data-ttu-id="e130b-114">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="e130b-114">**syslocks**</span></span>  
  
-   <span data-ttu-id="e130b-115">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="e130b-115">**sysproperties**</span></span>  
  
-   <span data-ttu-id="e130b-116">**sysprotects_aux**</span><span class="sxs-lookup"><span data-stu-id="e130b-116">**sysprotects_aux**</span></span>  
  
-   <span data-ttu-id="e130b-117">**sysprotects_view**</span><span class="sxs-lookup"><span data-stu-id="e130b-117">**sysprotects_view**</span></span>  
  
-   <span data-ttu-id="e130b-118">**SYSREMOTE_CATALOGS**</span><span class="sxs-lookup"><span data-stu-id="e130b-118">**SYSREMOTE_CATALOGS**</span></span>  
  
-   <span data-ttu-id="e130b-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="e130b-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="e130b-120">**SYSREMOTE_COLUMNS**</span><span class="sxs-lookup"><span data-stu-id="e130b-120">**SYSREMOTE_COLUMNS**</span></span>  
  
-   <span data-ttu-id="e130b-121">**SYSREMOTE_FOREIGN_KEYS**</span><span class="sxs-lookup"><span data-stu-id="e130b-121">**SYSREMOTE_FOREIGN_KEYS**</span></span>  
  
-   <span data-ttu-id="e130b-122">**SYSREMOTE_INDEXES**</span><span class="sxs-lookup"><span data-stu-id="e130b-122">**SYSREMOTE_INDEXES**</span></span>  
  
-   <span data-ttu-id="e130b-123">**SYSREMOTE_PRIMARY_KEYS**</span><span class="sxs-lookup"><span data-stu-id="e130b-123">**SYSREMOTE_PRIMARY_KEYS**</span></span>  
  
-   <span data-ttu-id="e130b-124">**SYSREMOTE_PROVIDER_TYPES**</span><span class="sxs-lookup"><span data-stu-id="e130b-124">**SYSREMOTE_PROVIDER_TYPES**</span></span>  
  
-   <span data-ttu-id="e130b-125">**SYSREMOTE_SCHEMATA**</span><span class="sxs-lookup"><span data-stu-id="e130b-125">**SYSREMOTE_SCHEMATA**</span></span>  
  
-   <span data-ttu-id="e130b-126">**SYSREMOTE_STATISTICS**</span><span class="sxs-lookup"><span data-stu-id="e130b-126">**SYSREMOTE_STATISTICS**</span></span>  
  
-   <span data-ttu-id="e130b-127">**SYSREMOTE_TABLE_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="e130b-127">**SYSREMOTE_TABLE_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="e130b-128">**SYSREMOTE_TABLES**</span><span class="sxs-lookup"><span data-stu-id="e130b-128">**SYSREMOTE_TABLES**</span></span>  
  
-   <span data-ttu-id="e130b-129">**SYSREMOTE_VIEWS**</span><span class="sxs-lookup"><span data-stu-id="e130b-129">**SYSREMOTE_VIEWS**</span></span>  
  
-   <span data-ttu-id="e130b-130">**syssegments**</span><span class="sxs-lookup"><span data-stu-id="e130b-130">**syssegments**</span></span>  
  
-   <span data-ttu-id="e130b-131">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="e130b-131">**sysxlogins**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="e130b-132">修正措置</span><span class="sxs-lookup"><span data-stu-id="e130b-132">Corrective Action</span></span>  
 <span data-ttu-id="e130b-133">次の表に従ってアプリケーションを修正してください。</span><span class="sxs-lookup"><span data-stu-id="e130b-133">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="e130b-134">以前のシステム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e130b-134">Instead of</span></span>|<span data-ttu-id="e130b-135">用途</span><span class="sxs-lookup"><span data-stu-id="e130b-135">Use</span></span>|  
|----------------|---------|  
|<span data-ttu-id="e130b-136">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="e130b-136">**sysfulltextnotify**</span></span>|<span data-ttu-id="e130b-137">OBJECTPROPERTYEX 関数の**TableFulltextPendingChanges**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="e130b-137">**TableFulltextPendingChanges** property of the OBJECTPROPERTYEX function.</span></span>|  
|<span data-ttu-id="e130b-138">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="e130b-138">**syslocks**</span></span>|<span data-ttu-id="e130b-139">**dm_tran_locks**動的管理ビュー、sp_lock、または**sys.syslockinfo**互換性ビュー。</span><span class="sxs-lookup"><span data-stu-id="e130b-139">**sys.dm_tran_locks** dynamic management view, or sp_lock, or the **sys.syslockinfo** compatibility view.</span></span>|  
|<span data-ttu-id="e130b-140">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="e130b-140">**sysproperties**</span></span>|<span data-ttu-id="e130b-141">**extended_properties**カタログビューまたは**fn_listextendedproperty**関数</span><span class="sxs-lookup"><span data-stu-id="e130b-141">**sys.extended_properties** catalog view or the **fn_listextendedproperty** function</span></span>|  
|<span data-ttu-id="e130b-142">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="e130b-142">**sysxlogins**</span></span>|<span data-ttu-id="e130b-143">**server_principals**カタログビューまたは**syslogins**互換性ビュー。</span><span class="sxs-lookup"><span data-stu-id="e130b-143">**sys.server_principals** catalog view or **syslogins** compatibility view.</span></span>|  
|<span data-ttu-id="e130b-144">すべての**spt_** テーブル</span><span class="sxs-lookup"><span data-stu-id="e130b-144">all **spt_** tables</span></span>|<span data-ttu-id="e130b-145">置き換えることはできません</span><span class="sxs-lookup"><span data-stu-id="e130b-145">No replacement available</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e130b-146">参照</span><span class="sxs-lookup"><span data-stu-id="e130b-146">See Also</span></span>  
 <span data-ttu-id="e130b-147">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="e130b-147">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="e130b-148">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="e130b-148">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
