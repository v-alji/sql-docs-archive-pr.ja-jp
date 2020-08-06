---
title: MSSQLSERVER_926 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae6796c9f4869d45223ab1283a68fc2bfe78aa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640003"
---
# <a name="mssqlserver_926"></a><span data-ttu-id="d823c-102">MSSQLSERVER_926</span><span class="sxs-lookup"><span data-stu-id="d823c-102">MSSQLSERVER_926</span></span>
    
## <a name="details"></a><span data-ttu-id="d823c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d823c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d823c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d823c-104">Product Name</span></span>|<span data-ttu-id="d823c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d823c-105">SQL Server</span></span>|  
|<span data-ttu-id="d823c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d823c-106">Event ID</span></span>|<span data-ttu-id="d823c-107">926</span><span class="sxs-lookup"><span data-stu-id="d823c-107">926</span></span>|  
|<span data-ttu-id="d823c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d823c-108">Event Source</span></span>|<span data-ttu-id="d823c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d823c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d823c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d823c-110">Component</span></span>|<span data-ttu-id="d823c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d823c-111">SQLEngine</span></span>|  
|<span data-ttu-id="d823c-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d823c-112">Symbolic Name</span></span>|<span data-ttu-id="d823c-113">DB_SUSPECT</span><span class="sxs-lookup"><span data-stu-id="d823c-113">DB_SUSPECT</span></span>|  
|<span data-ttu-id="d823c-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d823c-114">Message Text</span></span>|<span data-ttu-id="d823c-115">データベース '%.\*ls' を開けません。</span><span class="sxs-lookup"><span data-stu-id="d823c-115">Database '%.\*ls' cannot be opened.</span></span> <span data-ttu-id="d823c-116">このデータベースは、復旧により問題ありと設定されています。</span><span class="sxs-lookup"><span data-stu-id="d823c-116">It has been marked SUSPECT by recovery.</span></span> <span data-ttu-id="d823c-117">詳細については、SQL Server のエラー ログを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d823c-117">See the SQL Server errorlog for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d823c-118">説明</span><span class="sxs-lookup"><span data-stu-id="d823c-118">Explanation</span></span>  
 <span data-ttu-id="d823c-119">データベースが問題ありと設定されるのは、データベースのトランザクションを一貫性のある状態にする復旧処理が失敗したためです。</span><span class="sxs-lookup"><span data-stu-id="d823c-119">The database is marked as suspect because it failed the recovery process that brings a database to a consistent transactional state.</span></span> <span data-ttu-id="d823c-120">この現象は、次の操作で発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d823c-120">This can occur during the following operations:</span></span>  
  
-   <span data-ttu-id="d823c-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの起動。</span><span class="sxs-lookup"><span data-stu-id="d823c-121">Starting up an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d823c-122">データベースのインポート。</span><span class="sxs-lookup"><span data-stu-id="d823c-122">Attaching a database.</span></span>  
  
-   <span data-ttu-id="d823c-123">RESTORE データベースまたは RESTORE LOG プロシージャの使用。</span><span class="sxs-lookup"><span data-stu-id="d823c-123">Using the RESTORE database or RESTORE LOG procedures.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d823c-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d823c-124">User Action</span></span>  
 <span data-ttu-id="d823c-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを調査し、エラーの原因を特定します。</span><span class="sxs-lookup"><span data-stu-id="d823c-125">Inspect the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and determine the cause of the error.</span></span> <span data-ttu-id="d823c-126">復旧の失敗後に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再起動された場合は、以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを参照し、復旧が失敗した原因を確認します。</span><span class="sxs-lookup"><span data-stu-id="d823c-126">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been restarted since the failed recovery, look at previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs to see the reason why recovery failed.</span></span>  
  
 <span data-ttu-id="d823c-127">永続的な I/O エラー、破損ページ、またはその他のハードウェア障害によって復旧に失敗した場合は、原因となっているハードウェア障害を解決してから、バックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="d823c-127">If the recovery failed because of a persistent I/O error, a torn page, or other possible hardware problem, resolve the underlying hardware problem and restore the database by using a backup.</span></span> <span data-ttu-id="d823c-128">バックアップが用意されていない場合は、DBCC CHECKDB の修復オプションを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="d823c-128">If no backups are available, consider the repair options of DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="d823c-129">この問題を解決できない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d823c-129">If you are unable to resolve this problem, contact your primary support provider.</span></span> <span data-ttu-id="d823c-130">確認用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログをご用意ください。</span><span class="sxs-lookup"><span data-stu-id="d823c-130">Have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log available for review.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d823c-131">参照</span><span class="sxs-lookup"><span data-stu-id="d823c-131">See Also</span></span>  
 <span data-ttu-id="d823c-132">[SQL Server データベースのバックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="d823c-132">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="d823c-133">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d823c-133">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="d823c-134">[sys.sysデータベース &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d823c-134">[sys.sysdatabases &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span></span>  
 [<span data-ttu-id="d823c-135">データベースのデタッチとアタッチ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d823c-135">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
