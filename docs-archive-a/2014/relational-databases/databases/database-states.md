---
title: データベースの状態 | Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASESTATES.F1
helpviewer_keywords:
- emergency database state [SQL Server]
- verifying database states
- viewing database states
- displaying database states
- database states [SQL Server]
- current database state
- offline database state [SQL Server]
- suspect database state
- recovery pending database state [SQL Server]
- states [SQL Server], databases
- online database state
- states [SQL Server]
- restoring database state [SQL Server]
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0aec4e5fb367f5fe9bf8fca5ed056269930cf2db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742206"
---
# <a name="database-states"></a><span data-ttu-id="fa61d-102">データベースの状態</span><span class="sxs-lookup"><span data-stu-id="fa61d-102">Database States</span></span>
  <span data-ttu-id="fa61d-103">データベースは、常に、ある特定の状態にあります。</span><span class="sxs-lookup"><span data-stu-id="fa61d-103">A database is always in one specific state.</span></span> <span data-ttu-id="fa61d-104">たとえば、ONLINE、OFFLINE、SUSPECT などです。</span><span class="sxs-lookup"><span data-stu-id="fa61d-104">For example, these states include ONLINE, OFFLINE, or SUSPECT.</span></span> <span data-ttu-id="fa61d-105">データベースの現在の状態を確認するには、 **sys.databases** カタログ ビューで [state_desc](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 列を選択するか、 **DATABASEPROPERTYEX** 関数で [Status](/sql/t-sql/functions/databasepropertyex-transact-sql) プロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="fa61d-105">To verify the current state of a database, select the **state_desc** column in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view or the **Status** property in the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function.</span></span>  
  
## <a name="database-state-definitions"></a><span data-ttu-id="fa61d-106">データベースの状態の定義</span><span class="sxs-lookup"><span data-stu-id="fa61d-106">Database State Definitions</span></span>  
 <span data-ttu-id="fa61d-107">次の表では、データベースの状態を定義します。</span><span class="sxs-lookup"><span data-stu-id="fa61d-107">The following table defines the database states.</span></span>  
  
|<span data-ttu-id="fa61d-108">State</span><span class="sxs-lookup"><span data-stu-id="fa61d-108">State</span></span>|<span data-ttu-id="fa61d-109">定義</span><span class="sxs-lookup"><span data-stu-id="fa61d-109">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="fa61d-110">ONLINE</span><span class="sxs-lookup"><span data-stu-id="fa61d-110">ONLINE</span></span>|<span data-ttu-id="fa61d-111">データベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-111">Database is available for access.</span></span> <span data-ttu-id="fa61d-112">復旧時に行われる元に戻すフェーズが完了していなくても、プライマリ ファイル グループはオンラインです。</span><span class="sxs-lookup"><span data-stu-id="fa61d-112">The primary filegroup is online, although the undo phase of recovery may not have been completed.</span></span>|  
|<span data-ttu-id="fa61d-113">OFFLINE</span><span class="sxs-lookup"><span data-stu-id="fa61d-113">OFFLINE</span></span>|<span data-ttu-id="fa61d-114">データベースは使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa61d-114">Database is unavailable.</span></span> <span data-ttu-id="fa61d-115">ユーザーの明示的な操作によってデータベースがオフラインになり、ユーザーが新たな操作を行うまでオフラインのままになります。</span><span class="sxs-lookup"><span data-stu-id="fa61d-115">A database becomes offline by explicit user action and remains offline until additional user action is taken.</span></span> <span data-ttu-id="fa61d-116">たとえば、ファイルを新しいディスクに移動するために、データベースをオフラインにできます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-116">For example, the database may be taken offline in order to move a file to a new disk.</span></span> <span data-ttu-id="fa61d-117">移動の完了後に、データベースをオンラインに戻します。</span><span class="sxs-lookup"><span data-stu-id="fa61d-117">The database is then brought back online after the move has been completed.</span></span>|  
|<span data-ttu-id="fa61d-118">RESTORING</span><span class="sxs-lookup"><span data-stu-id="fa61d-118">RESTORING</span></span>|<span data-ttu-id="fa61d-119">プライマリ ファイル グループの 1 つ以上のファイルが復元中か、1 つ以上のセカンダリ ファイルがオフラインで復元中です。</span><span class="sxs-lookup"><span data-stu-id="fa61d-119">One or more files of the primary filegroup are being restored, or one or more secondary files are being restored offline.</span></span> <span data-ttu-id="fa61d-120">データベースは使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa61d-120">The database is unavailable.</span></span>|  
|<span data-ttu-id="fa61d-121">RECOVERING</span><span class="sxs-lookup"><span data-stu-id="fa61d-121">RECOVERING</span></span>|<span data-ttu-id="fa61d-122">データベースが復旧中です。</span><span class="sxs-lookup"><span data-stu-id="fa61d-122">Database is being recovered.</span></span> <span data-ttu-id="fa61d-123">復旧処理は一時的な状態です。復旧が成功すると、データベースは自動的に online 状態になります。</span><span class="sxs-lookup"><span data-stu-id="fa61d-123">The recovering process is a transient state; the database will automatically become online if the recovery succeeds.</span></span> <span data-ttu-id="fa61d-124">復旧が失敗すると、データベースは suspect 状態になります。</span><span class="sxs-lookup"><span data-stu-id="fa61d-124">If the recovery fails, the database will become suspect.</span></span> <span data-ttu-id="fa61d-125">データベースは使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa61d-125">The database is unavailable.</span></span>|  
|<span data-ttu-id="fa61d-126">RECOVERY PENDING</span><span class="sxs-lookup"><span data-stu-id="fa61d-126">RECOVERY PENDING</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="fa61d-127">で、復旧中にリソースに関連するエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fa61d-127">has encountered a resource-related error during recovery.</span></span> <span data-ttu-id="fa61d-128">データベースは破損していませんが、ファイルが見つからないか、システム リソースの制限によりデータベースを起動できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa61d-128">The database is not damaged, but files may be missing or system resource limitations may be preventing it from starting.</span></span> <span data-ttu-id="fa61d-129">データベースは使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa61d-129">The database is unavailable.</span></span> <span data-ttu-id="fa61d-130">エラーを解決して復旧処理を完了するには、ユーザーによる新たな操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="fa61d-130">Additional action by the user is required to resolve the error and let the recovery process be completed.</span></span>|  
|<span data-ttu-id="fa61d-131">SUSPECT</span><span class="sxs-lookup"><span data-stu-id="fa61d-131">SUSPECT</span></span>|<span data-ttu-id="fa61d-132">少なくともプライマリ ファイル グループが問題のある状態で、破損している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa61d-132">At least the primary filegroup is suspect and may be damaged.</span></span> <span data-ttu-id="fa61d-133">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の起動中にはデータベースを復旧できません。</span><span class="sxs-lookup"><span data-stu-id="fa61d-133">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fa61d-134">データベースは使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa61d-134">The database is unavailable.</span></span> <span data-ttu-id="fa61d-135">問題を解決するには、ユーザーによる新たな操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="fa61d-135">Additional action by the user is required to resolve the problem.</span></span>|  
|<span data-ttu-id="fa61d-136">EMERGENCY</span><span class="sxs-lookup"><span data-stu-id="fa61d-136">EMERGENCY</span></span>|<span data-ttu-id="fa61d-137">ユーザーがデータベースを変更し、状態を EMERGENCY に設定しました。</span><span class="sxs-lookup"><span data-stu-id="fa61d-137">User has changed the database and set the status to EMERGENCY.</span></span> <span data-ttu-id="fa61d-138">データベースはシングル ユーザー モードになり、修復または復元できます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-138">The database is in single-user mode and may be repaired or restored.</span></span> <span data-ttu-id="fa61d-139">データベースは READ_ONLY に設定され、ログ記録が無効になり、アクセスが **sysadmin** 固定サーバー ロールのメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-139">The database is marked READ_ONLY, logging is disabled, and access is limited to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="fa61d-140">EMERGENCY は、主にトラブルシューティングの目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-140">EMERGENCY is primarily used for troubleshooting purposes.</span></span> <span data-ttu-id="fa61d-141">たとえば、suspect に設定されたデータベースを、EMERGENCY 状態に設定できます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-141">For example, a database marked as suspect can be set to the EMERGENCY state.</span></span> <span data-ttu-id="fa61d-142">これにより、システム管理者にデータベースへの読み取り専用のアクセスを許可できます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-142">This could permit the system administrator read-only access to the database.</span></span> <span data-ttu-id="fa61d-143">**sysadmin** 固定サーバー ロールのメンバーのみが、データベースを EMERGENCY 状態に設定できます。</span><span class="sxs-lookup"><span data-stu-id="fa61d-143">Only members of the **sysadmin** fixed server role can set a database to the EMERGENCY state.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="fa61d-144">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="fa61d-144">Related Content</span></span>  
 [<span data-ttu-id="fa61d-145">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fa61d-145">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="fa61d-146">ミラーリング状態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fa61d-146">Mirroring States &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [<span data-ttu-id="fa61d-147">ファイルの状態</span><span class="sxs-lookup"><span data-stu-id="fa61d-147">File States</span></span>](file-states.md)  
  
  
