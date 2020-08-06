---
title: データベースエンジンアップグレードに関するその他の問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db496112fc975304bb2d7da9d9ea1c52e6dd8bec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634225"
---
# <a name="other-database-engine-upgrade-issues"></a><span data-ttu-id="9a800-102">データベース エンジンのアップグレードに関するその他の問題</span><span class="sxs-lookup"><span data-stu-id="9a800-102">Other Database Engine Upgrade Issues</span></span>
  <span data-ttu-id="9a800-103">アップグレードに関する次の問題は、現在のバージョンのアップグレード アドバイザーでは検出されません。</span><span class="sxs-lookup"><span data-stu-id="9a800-103">The following upgrade issues cannot be detected by the current version of Upgrade Advisor.</span></span> <span data-ttu-id="9a800-104">一覧表示されている問題を確認し、使用するシステムへの影響を判断してください。</span><span class="sxs-lookup"><span data-stu-id="9a800-104">Review the issues listed below to evaluate their potential impact to your systems.</span></span>  
  
## <a name="multiple-database-engine-deprecated-features"></a><span data-ttu-id="9a800-105">データベース エンジンの複数の非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="9a800-105">Multiple Database Engine Deprecated Features</span></span>  
 <span data-ttu-id="9a800-106">次に示す [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはオプションは非推奨とされます：</span><span class="sxs-lookup"><span data-stu-id="9a800-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or options are deprecated:</span></span>  
  
-   <span data-ttu-id="9a800-107">BACKUP LOG の NO_LOG オプションと TRUNCATE_ONLY オプション</span><span class="sxs-lookup"><span data-stu-id="9a800-107">NO_LOG and TRUNCATE_ONLY options of BACKUP LOG</span></span>  
  
-   <span data-ttu-id="9a800-108">BACKUP TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="9a800-108">BACKUP TRANSACTION</span></span>  
  
-   <span data-ttu-id="9a800-109">RESTORE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="9a800-109">RESTORE TRANSACTION</span></span>  
  
-   <span data-ttu-id="9a800-110">DUMP</span><span class="sxs-lookup"><span data-stu-id="9a800-110">DUMP</span></span>  
  
-   <span data-ttu-id="9a800-111">LOAD</span><span class="sxs-lookup"><span data-stu-id="9a800-111">LOAD</span></span>  
  
-   <span data-ttu-id="9a800-112">DBCC CONCURRENCYVIOLATION</span><span class="sxs-lookup"><span data-stu-id="9a800-112">DBCC CONCURRENCYVIOLATION</span></span>  
  
-   <span data-ttu-id="9a800-113">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="9a800-113">sp_addalias</span></span>  
  
-   <span data-ttu-id="9a800-114">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="9a800-114">sp_addgroup</span></span>  
  
-   <span data-ttu-id="9a800-115">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="9a800-115">sp_changegroup</span></span>  
  
-   <span data-ttu-id="9a800-116">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="9a800-116">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="9a800-117">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="9a800-117">sp_helpgroup</span></span>  
  
-   <span data-ttu-id="9a800-118">syssegments</span><span class="sxs-lookup"><span data-stu-id="9a800-118">syssegments</span></span>  
  
 <span data-ttu-id="9a800-119">VIA プロトコルの使用による[!INCLUDE[ssDE](../../includes/ssde-md.md)]への接続は、非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="9a800-119">Use of the VIA protocol to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is deprecated.</span></span>  
  
## <a name="new-data-types"></a><span data-ttu-id="9a800-120">新しいデータ型</span><span class="sxs-lookup"><span data-stu-id="9a800-120">New Data Types</span></span>  
 <span data-ttu-id="9a800-121">次の型がシステム型として予約されます。</span><span class="sxs-lookup"><span data-stu-id="9a800-121">The following will be reserved system types.</span></span> <span data-ttu-id="9a800-122">アップグレードする前、またはアップグレードした後に、競合する既存のユーザー定義型の名前を変更してください。</span><span class="sxs-lookup"><span data-stu-id="9a800-122">Rename the existing conflicting user defined types either before or after upgrade.</span></span>  
  
-   <span data-ttu-id="9a800-123">[地理的な場所]</span><span class="sxs-lookup"><span data-stu-id="9a800-123">Geography</span></span>  
  
-   <span data-ttu-id="9a800-124">ジオメトリ</span><span class="sxs-lookup"><span data-stu-id="9a800-124">Geometry</span></span>  
  
-   <span data-ttu-id="9a800-125">Datetime2</span><span class="sxs-lookup"><span data-stu-id="9a800-125">Datetime2</span></span>  
  
-   <span data-ttu-id="9a800-126">HierarchyID</span><span class="sxs-lookup"><span data-stu-id="9a800-126">HierarchyID</span></span>  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a><span data-ttu-id="9a800-127">定義済みのトリガーを使用できなくなった OUTPUT INTO 句の対象テーブル</span><span class="sxs-lookup"><span data-stu-id="9a800-127">Target Table of the OUTPUT INTO Clause Cannot Have Any Defined Triggers</span></span>  
 <span data-ttu-id="9a800-128">テーブルに有効なトリガーがある場合、ターゲットテーブルに出力することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a800-128">OUTPUT INTO a target table when the table has any enabled triggers is not supported.</span></span>  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a><span data-ttu-id="9a800-129">OUTPUT INTO 句の対象がテーブルである場合に発生する UDF のコンパイル時エラー</span><span class="sxs-lookup"><span data-stu-id="9a800-129">Compile Time Error for UDFs When the Target of an OUTPUT INTO Clause is a Table</span></span>  
 <span data-ttu-id="9a800-130">ユーザー定義関数 (UDF) は、データベースの状態を変更するアクションの実行には使用できません。</span><span class="sxs-lookup"><span data-stu-id="9a800-130">User-defined functions (UDF) cannot be used to perform actions that modify the database state.</span></span> <span data-ttu-id="9a800-131">たとえば、テーブル変数以外のオブジェクトに対して、UDF で DDL (CREATE、ALTER、DROP) または DML (INSERT、UPDATE、DELETE) アクションを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a800-131">For example, a UDF cannot perform any DDL (CREATE/ALTER/DROP) or DML (INSERT/UPDATE/DELETE) actions on any objects, except for table variables.</span></span>  
  
## <a name="merge-is-a-reserved-keyword"></a><span data-ttu-id="9a800-132">予約済みキーワードになった MERGE</span><span class="sxs-lookup"><span data-stu-id="9a800-132">MERGE is a Reserved Keyword</span></span>  
 <span data-ttu-id="9a800-133">MERGE は完全に予約されたキーワードになりました。</span><span class="sxs-lookup"><span data-stu-id="9a800-133">MERGE is now a fully-reserved keyword.</span></span> <span data-ttu-id="9a800-134">アプリケーションでは、MERGE という名前のオブジェクト (テーブルや列など) を使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9a800-134">Applications can no longer have objects (table, column, etc.) called MERGE.</span></span>  
  
## <a name="rename-cdc-schema"></a><span data-ttu-id="9a800-135">CDC スキーマの名前の変更</span><span class="sxs-lookup"><span data-stu-id="9a800-135">Rename CDC Schema</span></span>  
 <span data-ttu-id="9a800-136">CDC というスキーマ名が存在します。</span><span class="sxs-lookup"><span data-stu-id="9a800-136">There is a schema name called CDC.</span></span> <span data-ttu-id="9a800-137">このスキーマ名は、**変更データキャプチャ**がデータベースに対して有効になっている場合は使用できません。</span><span class="sxs-lookup"><span data-stu-id="9a800-137">This schema name cannot be in used if **Change Data Capture** is enabled for the database.</span></span>  
  
 <span data-ttu-id="9a800-138">データベースの**変更データキャプチャ**を有効にする前に、CDC スキーマを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a800-138">You must drop the CDC schema before you enable **Change Data Capture** for the database.</span></span> <span data-ttu-id="9a800-139">この手順は、アップグレードの前でも後でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="9a800-139">This step can be done before or after the upgrade.</span></span> <span data-ttu-id="9a800-140">スキーマを削除するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9a800-140">To drop the schema, use the following steps:</span></span>  
  
1.  <span data-ttu-id="9a800-141">ALTER SCHEMA を使用して、CDC スキーマから新しいスキーマ名にオブジェクトを転送します。</span><span class="sxs-lookup"><span data-stu-id="9a800-141">Transfer the objects from CDC schema to a new schema name using ALTER SCHEMA.</span></span>  
  
2.  <span data-ttu-id="9a800-142">新しいスキーマ内のオブジェクトに対する権限を確認します。</span><span class="sxs-lookup"><span data-stu-id="9a800-142">Verify permissions for the objects in the new schema.</span></span>  
  
3.  <span data-ttu-id="9a800-143">アプリケーションに必要な変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="9a800-143">Make necessary modifications to the application.</span></span>  
  
4.  <span data-ttu-id="9a800-144">DROP SCHEMA を使用して CDC スキーマを削除します。</span><span class="sxs-lookup"><span data-stu-id="9a800-144">Drop the CDC schema using DROP SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a800-145">参照</span><span class="sxs-lookup"><span data-stu-id="9a800-145">See Also</span></span>  
 [<span data-ttu-id="9a800-146">データベース エンジンのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="9a800-146">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
