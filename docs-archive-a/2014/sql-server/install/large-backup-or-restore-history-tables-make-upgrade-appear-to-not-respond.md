---
title: 大きなバックアップまたは復元の履歴テーブルによってアップグレードが応答しないように見える |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 918c20f58c00c535d8ed41d887e9671f5e821a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632280"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a><span data-ttu-id="66bf7-102">バックアップまたは復元のサイズの大きい履歴テーブルではアップグレードが応答を停止したように見える</span><span class="sxs-lookup"><span data-stu-id="66bf7-102">Large backup or restore history tables make upgrade appear to not respond</span></span>
  <span data-ttu-id="66bf7-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、バックアップと復元の履歴テーブルの一部に新しい列が追加されました。</span><span class="sxs-lookup"><span data-stu-id="66bf7-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], new columns were added to some of the backup and restore history tables.</span></span> <span data-ttu-id="66bf7-104">これらのテーブルをアップグレードするには、新しい列を追加するためにテーブルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66bf7-104">Upgrading these tables requires altering them to add the new columns.</span></span> <span data-ttu-id="66bf7-105">これらのテーブルのうちの 1 つ以上のテーブルに大量の行が含まれている場合、アップグレードの際に、テーブルに列を追加する ALTER TABLE ステートメントで非常に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="66bf7-105">If one or more of these tables contains a large number of rows, the upgrade will stall for a substantial amount of time on the ALTER TABLE statement that adds columns to that table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="66bf7-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="66bf7-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="66bf7-107">説明</span><span class="sxs-lookup"><span data-stu-id="66bf7-107">Description</span></span>  
 <span data-ttu-id="66bf7-108">次のいずれかのバックアップまたは復元履歴テーブルに多数の行が含まれていると、アップグレードが応答を停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="66bf7-108">Upgrade can appear to stop responding if any of the following backup or restore history tables contains a large number of rows:</span></span>  
  
-   <span data-ttu-id="66bf7-109">**backupfile**</span><span class="sxs-lookup"><span data-stu-id="66bf7-109">**backupfile**</span></span>  
  
-   <span data-ttu-id="66bf7-110">**backupmediafamily**</span><span class="sxs-lookup"><span data-stu-id="66bf7-110">**backupmediafamily**</span></span>  
  
-   <span data-ttu-id="66bf7-111">**backupmediaset**</span><span class="sxs-lookup"><span data-stu-id="66bf7-111">**backupmediaset**</span></span>  
  
-   <span data-ttu-id="66bf7-112">**backupset**</span><span class="sxs-lookup"><span data-stu-id="66bf7-112">**backupset**</span></span>  
  
-   <span data-ttu-id="66bf7-113">**restorefile**</span><span class="sxs-lookup"><span data-stu-id="66bf7-113">**restorefile**</span></span>  
  
-   <span data-ttu-id="66bf7-114">**restorefilegroup**</span><span class="sxs-lookup"><span data-stu-id="66bf7-114">**restorefilegroup**</span></span>  
  
-   <span data-ttu-id="66bf7-115">**restorehistory**</span><span class="sxs-lookup"><span data-stu-id="66bf7-115">**restorehistory**</span></span>  
  
 <span data-ttu-id="66bf7-116">これらのテーブルに 10,000 以上の行が含まれている場合、アップグレード アドバイザーは不適格であることを示すエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="66bf7-116">If any of these tables has 10,000 or more rows, Upgrade Advisor reports a noncompliance failure.</span></span> <span data-ttu-id="66bf7-117">どのテーブルが許容行数を超えたのかは報告されません。</span><span class="sxs-lookup"><span data-stu-id="66bf7-117">It does not report which table exceeds the allowed number of rows.</span></span> <span data-ttu-id="66bf7-118">10,000 行を超える最初のテーブルでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="66bf7-118">The first table that exceeds 10,000 rows causes the failure.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="66bf7-119">修正措置</span><span class="sxs-lookup"><span data-stu-id="66bf7-119">Corrective Action</span></span>  
 <span data-ttu-id="66bf7-120">テーブルが 10,000 行を超えている場合は、データベースをアップグレードする前に、10,000 行未満に減らすことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66bf7-120">Before you upgrade a database, if any of these tables exceeds 10,000 rows, we recommend that you reduce the number to less than 10,000.</span></span> <span data-ttu-id="66bf7-121">これらのすべてのテーブルの行を減らすには、 **sp_delete_backuphistory**ストアドプロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="66bf7-121">To reduce rows in all of these tables, you can run the **sp_delete_backuphistory** stored procedure.</span></span> <span data-ttu-id="66bf7-122">このプロシージャは、バックアップと復元のすべての履歴テーブルに含まれているエントリのうち、指定した日付よりも古いバックアップ セットのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="66bf7-122">This procedure deletes the entries in all of the backup and restore history tables for backup sets older than a specified date.</span></span> <span data-ttu-id="66bf7-123">詳細については、「[sp_delete_backuphistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66bf7-123">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66bf7-124">バックアップと復元の履歴テーブルが 10,000 行を超えるデータベースはアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="66bf7-124">You can upgrade a database whose backup and restore history tables are larger than 10,000 rows.</span></span> <span data-ttu-id="66bf7-125">ただし、サイズの大きいテーブルの変更には時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="66bf7-125">But the upgrade may appear to stall while large tables are being altered.</span></span> <span data-ttu-id="66bf7-126">テーブルのサイズが大きいほど、セットアップの完了に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="66bf7-126">The larger the tables, the longer that Setup takes to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66bf7-127">参照</span><span class="sxs-lookup"><span data-stu-id="66bf7-127">See Also</span></span>  
 <span data-ttu-id="66bf7-128">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="66bf7-128">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="66bf7-129">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="66bf7-129">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
