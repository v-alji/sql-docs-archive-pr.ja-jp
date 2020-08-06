---
title: 非推奨のシステムストアドプロシージャへの参照を削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65e7da666beaf84050dd8d60caf4cac5bfc013c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720846"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a><span data-ttu-id="efacf-102">非推奨ｎおシステム ストアド プロシージャの参照の削除</span><span class="sxs-lookup"><span data-stu-id="efacf-102">Remove references to deprecated system stored procedures</span></span>
  <span data-ttu-id="efacf-103">アップグレード アドバイザーによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できなくなった、ドキュメントに記載されていないシステム ストアド プロシージャおよび拡張ストアド プロシージャを参照するステートメントが検出されました。</span><span class="sxs-lookup"><span data-stu-id="efacf-103">Upgrade Advisor detected statements that reference undocumented system stored procedures and extended stored procedures that are no longer available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efacf-104">これらのオブジェクトを参照するステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="efacf-104">Statements that reference these objects will fail.</span></span> <span data-ttu-id="efacf-105">今後のリリースで予告なしに機能が変更または削除される可能性があるので、ドキュメントに記載されていないシステム オブジェクトまたは API を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="efacf-105">Do not use undocumented system objects or APIs as the functionality might change or be removed without notification in a future release.</span></span>  
  
## <a name="component"></a><span data-ttu-id="efacf-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="efacf-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="efacf-107">説明</span><span class="sxs-lookup"><span data-stu-id="efacf-107">Description</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="efacf-108">ドキュメントに記載されているシステム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="efacf-108">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="efacf-109">ドキュメントに記載されている以下のシステム ストアド プロシージャは削除されています。</span><span class="sxs-lookup"><span data-stu-id="efacf-109">The following documented system stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="efacf-110">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="efacf-110">sp_addalias</span></span>  
  
-   <span data-ttu-id="efacf-111">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="efacf-111">sp_addgroup</span></span>  
  
-   <span data-ttu-id="efacf-112">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="efacf-112">sp_changegroup</span></span>  
  
-   <span data-ttu-id="efacf-113">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="efacf-113">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="efacf-114">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="efacf-114">sp_helpgroup</span></span>  
  
### <a name="undocumented-system-stored-procedures"></a><span data-ttu-id="efacf-115">ドキュメントに記載されていないシステム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="efacf-115">Undocumented System Stored Procedures</span></span>  
 <span data-ttu-id="efacf-116">ドキュメントに記載されていない以下のシステム ストアド プロシージャおよび拡張ストアド プロシージャは削除されています。</span><span class="sxs-lookup"><span data-stu-id="efacf-116">The following undocumented system stored procedures and extended stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="efacf-117">sp_articlesynctranprocs</span><span class="sxs-lookup"><span data-stu-id="efacf-117">sp_articlesynctranprocs</span></span>  
  
-   <span data-ttu-id="efacf-118">sp_diskdefault</span><span class="sxs-lookup"><span data-stu-id="efacf-118">sp_diskdefault</span></span>  
  
-   <span data-ttu-id="efacf-119">sp_EventLog</span><span class="sxs-lookup"><span data-stu-id="efacf-119">sp_EventLog</span></span>  
  
-   <span data-ttu-id="efacf-120">sp_GetMBCSCharLen</span><span class="sxs-lookup"><span data-stu-id="efacf-120">sp_GetMBCSCharLen</span></span>  
  
-   <span data-ttu-id="efacf-121">sp_helplog</span><span class="sxs-lookup"><span data-stu-id="efacf-121">sp_helplog</span></span>  
  
-   <span data-ttu-id="efacf-122">sp_helpsql</span><span class="sxs-lookup"><span data-stu-id="efacf-122">sp_helpsql</span></span>  
  
-   <span data-ttu-id="efacf-123">sp_IsMBCSLeadByte</span><span class="sxs-lookup"><span data-stu-id="efacf-123">sp_IsMBCSLeadByte</span></span>  
  
-   <span data-ttu-id="efacf-124">sp_lock2</span><span class="sxs-lookup"><span data-stu-id="efacf-124">sp_lock2</span></span>  
  
-   <span data-ttu-id="efacf-125">sp_MSget_current_activity</span><span class="sxs-lookup"><span data-stu-id="efacf-125">sp_MSget_current_activity</span></span>  
  
-   <span data-ttu-id="efacf-126">sp_MSset_current_activity</span><span class="sxs-lookup"><span data-stu-id="efacf-126">sp_MSset_current_activity</span></span>  
  
-   <span data-ttu-id="efacf-127">sp_MSobjessearch</span><span class="sxs-lookup"><span data-stu-id="efacf-127">sp_MSobjessearch</span></span>  
  
-   <span data-ttu-id="efacf-128">xp_enum_ActiveScriptEngines</span><span class="sxs-lookup"><span data-stu-id="efacf-128">xp_enum_ActiveScriptEngines</span></span>  
  
-   <span data-ttu-id="efacf-129">xp_eventlog</span><span class="sxs-lookup"><span data-stu-id="efacf-129">xp_eventlog</span></span>  
  
-   <span data-ttu-id="efacf-130">xp_GetAdminGroupName</span><span class="sxs-lookup"><span data-stu-id="efacf-130">xp_GetAdminGroupName</span></span>  
  
-   <span data-ttu-id="efacf-131">xp_GetFileDetails</span><span class="sxs-lookup"><span data-stu-id="efacf-131">xp_GetFileDetails</span></span>  
  
-   <span data-ttu-id="efacf-132">xp_GetLocalSystemAccountName</span><span class="sxs-lookup"><span data-stu-id="efacf-132">xp_GetLocalSystemAccountName</span></span>  
  
-   <span data-ttu-id="efacf-133">xp_IsNTAdmin</span><span class="sxs-lookup"><span data-stu-id="efacf-133">xp_IsNTAdmin</span></span>  
  
-   <span data-ttu-id="efacf-134">xp_MSLocalSystem</span><span class="sxs-lookup"><span data-stu-id="efacf-134">xp_MSLocalSystem</span></span>  
  
-   <span data-ttu-id="efacf-135">xp_MSnt2000</span><span class="sxs-lookup"><span data-stu-id="efacf-135">xp_MSnt2000</span></span>  
  
-   <span data-ttu-id="efacf-136">xp_MSplatform</span><span class="sxs-lookup"><span data-stu-id="efacf-136">xp_MSplatform</span></span>  
  
-   <span data-ttu-id="efacf-137">xp_SetSecurity</span><span class="sxs-lookup"><span data-stu-id="efacf-137">xp_SetSecurity</span></span>  
  
-   <span data-ttu-id="efacf-138">xp_varbintohexstr</span><span class="sxs-lookup"><span data-stu-id="efacf-138">xp_varbintohexstr</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="efacf-139">修正措置</span><span class="sxs-lookup"><span data-stu-id="efacf-139">Corrective Action</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="efacf-140">ドキュメントに記載されているシステム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="efacf-140">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="efacf-141">次の表に従ってアプリケーションを修正してください。</span><span class="sxs-lookup"><span data-stu-id="efacf-141">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="efacf-142">以前のシステム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="efacf-142">Instead of</span></span>|<span data-ttu-id="efacf-143">方法</span><span class="sxs-lookup"><span data-stu-id="efacf-143">Do this</span></span>|  
|----------------|-------------|  
|<span data-ttu-id="efacf-144">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="efacf-144">sp_addalias</span></span>|<span data-ttu-id="efacf-145">別名をユーザー アカウントとデータベース ロールの組み合わせで置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="efacf-145">Replace aliases with a combination of user accounts and database roles.</span></span> <span data-ttu-id="efacf-146">詳細については、SQL Server オンライン ブックの「CREATE USER (Transact-SQL)」および「CREATE ROLE (Transact-SQL)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efacf-146">For more information, see "CREATE USER (Transact-SQL)" and "CREATE ROLE (Transact-SQL)" in SQL Server Books Online.</span></span> <span data-ttu-id="efacf-147">アップグレードされたデータベースで別名を削除するには、sp_dropalias を使用します。</span><span class="sxs-lookup"><span data-stu-id="efacf-147">Remove aliases in upgraded databases by using sp_dropalias.</span></span>|  
|<span data-ttu-id="efacf-148">sp_addgroupsp_changegroup</span><span class="sxs-lookup"><span data-stu-id="efacf-148">sp_addgroupsp_changegroup</span></span><br /><br /> <span data-ttu-id="efacf-149">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="efacf-149">sp_dropgroup</span></span><br /><br /> <span data-ttu-id="efacf-150">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="efacf-150">sp_helpgroup</span></span>|<span data-ttu-id="efacf-151">ロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="efacf-151">Use roles.</span></span> <span data-ttu-id="efacf-152">詳細については、SQL Server オンライン ブックの「サーバー レベルのロール」および「データベース レベルのロール」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efacf-152">For more information, see "Server-Level Roles" and "Database-Level Roles" in SQL Server Books Online.</span></span>|  
  
### <a name="undocmented-system-stored-procedures"></a><span data-ttu-id="efacf-153">Undocmented システムストアドプロシージャ</span><span class="sxs-lookup"><span data-stu-id="efacf-153">Undocmented System Stored Procedures</span></span>  
 <span data-ttu-id="efacf-154">ドキュメントに記載されていないシステム ストアド プロシージャの代わりに、同じ機能を持つ CLR ストアド プロシージャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="efacf-154">You can create CLR stored procedures with equivalent functionality to replace the undocumented system stored procedures.</span></span> <span data-ttu-id="efacf-155">詳細については、SQL Server オンライン ブックの「CLR ストアド プロシージャ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efacf-155">For more information, see the topic "CLR Stored Procedures" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efacf-156">参照</span><span class="sxs-lookup"><span data-stu-id="efacf-156">See Also</span></span>  
 <span data-ttu-id="efacf-157">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="efacf-157">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="efacf-158">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="efacf-158">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
