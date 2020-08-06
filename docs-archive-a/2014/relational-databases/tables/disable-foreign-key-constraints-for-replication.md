---
title: レプリケーションに対して外部キー制約を無効にする方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ee7f2fb7b0a27870a09a9d99b723b7faf739aeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639928"
---
# <a name="disable-foreign-key-constraints-for-replication"></a><span data-ttu-id="49152-102">レプリケーションに対して外部キー制約を無効にする方法</span><span class="sxs-lookup"><span data-stu-id="49152-102">Disable Foreign Key Constraints for Replication</span></span>
  <span data-ttu-id="49152-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、レプリケーションに対する外部キー制約を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="49152-103">You can disable foreign key constraints for replication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="49152-104">これは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのデータをパブリッシュする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="49152-104">This can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49152-105">レプリケーションを使用してテーブルをパブリッシュした場合、レプリケーション エージェントが実行する操作については外部キー制約が自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="49152-105">If a table is published using replication, foreign key constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="49152-106">レプリケーション エージェントがサブスクライバー側で挿入、更新、または削除を実行した場合、制約のチェックは行われません。ユーザーが挿入、更新、または削除を実行した場合は、制約のチェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="49152-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="49152-107">制約がレプリケーション エージェントに対して無効になるのは、データが最初に挿入、更新、または削除された際に、発行者側で既に制約がチェックされているためです。</span><span class="sxs-lookup"><span data-stu-id="49152-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span>  
  
 <span data-ttu-id="49152-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="49152-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="49152-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="49152-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="49152-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="49152-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="49152-111">**以下を使用してレプリケーションに対する外部キー制約を無効にするには**</span><span class="sxs-lookup"><span data-stu-id="49152-111">**To disable a foreign key constraint for replication, using:**</span></span>  
  
     [<span data-ttu-id="49152-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="49152-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="49152-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="49152-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="49152-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="49152-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="49152-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="49152-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="49152-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="49152-116">Permissions</span></span>  
 <span data-ttu-id="49152-117">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="49152-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="49152-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="49152-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="49152-119">レプリケーションに対して外部キー制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="49152-119">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="49152-120">**オブジェクト エクスプローラー**で、変更する外部キー制約が含まれているテーブルを展開し、 **[キー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="49152-120">In **Object Explorer**, expand the table with the foreign key constraint you want to modify, and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="49152-121">外部キー制約を右クリックし、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49152-121">Right-click the foreign key constraint and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="49152-122">**[外部キーのリレーションシップ]** ダイアログ ボックスで、 **[レプリケーションに対して適用]** の値として **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49152-122">In the **Foreign Key Relationships** dialog box, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="49152-123">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49152-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="49152-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="49152-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="49152-125">レプリケーションに対して外部キー制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="49152-125">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="49152-126">[!INCLUDE[tsql](../../includes/tsql-md.md)]でこの作業を実行するには、外部キー制約を削除します。</span><span class="sxs-lookup"><span data-stu-id="49152-126">To perform this task in [!INCLUDE[tsql](../../includes/tsql-md.md)], drop the foreign key constraint.</span></span> <span data-ttu-id="49152-127">次に、新しい外部キー制約を追加し、NOT FOR REPLICATION オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="49152-127">Then add a new foreign key constraint and specify the NOT FOR REPLICATION option.</span></span>  
  
 <span data-ttu-id="49152-128">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49152-128">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
