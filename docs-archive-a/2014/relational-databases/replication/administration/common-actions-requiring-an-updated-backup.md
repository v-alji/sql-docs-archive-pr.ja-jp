---
title: 一般にバックアップの更新が必要になるアクション | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], actions requiring a backup
- restoring [SQL Server replication], actions requiring a backup
- backups [SQL Server replication], actions requiring a backup
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3eb10bdca8ee188f7b322a46665c38129d57052b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713034"
---
# <a name="common-actions-requiring-an-updated-backup"></a><span data-ttu-id="8678b-102">一般にバックアップの更新が必要になるアクション</span><span class="sxs-lookup"><span data-stu-id="8678b-102">Common Actions Requiring an Updated Backup</span></span>
  <span data-ttu-id="8678b-103">定期的なログ バックアップを実行する場合は、レプリケーション関連の変更をログ バックアップでキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8678b-103">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="8678b-104">ログ バックアップを実行しない場合は、レプリケーション スキーマまたはトポロジを変更した後でパブリケーション、ディストリビューション、サブスクリプション、 **msdb**、および **master** の各データ ベースのバックアップを実行してください。</span><span class="sxs-lookup"><span data-stu-id="8678b-104">If you don't perform log backups, perform a backup of the publication, distribution, subscription, **msdb**, and **master** databases after making modifications to your replication schema or topology.</span></span>  
  
## <a name="publication-database"></a><span data-ttu-id="8678b-105">パブリケーション データベース</span><span class="sxs-lookup"><span data-stu-id="8678b-105">Publication Database</span></span>  
 <span data-ttu-id="8678b-106">以下の処理の後で、パブリケーション データベースをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="8678b-106">Backup the publication database after:</span></span>  
  
-   <span data-ttu-id="8678b-107">パブリケーションの新規作成。</span><span class="sxs-lookup"><span data-stu-id="8678b-107">Creating new publications.</span></span>  
  
-   <span data-ttu-id="8678b-108">フィルター選択を含む、任意のパブリケーション プロパティの変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-108">Changing any publication property, including filtering.</span></span>  
  
-   <span data-ttu-id="8678b-109">既存のパブリケーションへのアーティクル追加。</span><span class="sxs-lookup"><span data-stu-id="8678b-109">Adding articles to an existing publication.</span></span>  
  
-   <span data-ttu-id="8678b-110">1 つのパブリケーション全体にわたる、サブスクリプションの再初期化。</span><span class="sxs-lookup"><span data-stu-id="8678b-110">Performing a publication-wide reinitialization of subscriptions.</span></span>  
  
-   <span data-ttu-id="8678b-111">パブリッシュされたテーブルでのスキーマの変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-111">Making a schema change on a published table.</span></span>  
  
-   <span data-ttu-id="8678b-112">[sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql) による要求時スクリプトの実行。</span><span class="sxs-lookup"><span data-stu-id="8678b-112">Performing on-demand script execution with [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).</span></span>  
  
-   <span data-ttu-id="8678b-113">任意のアーティクル プロパティの変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-113">Changing any article property.</span></span>  
  
-   <span data-ttu-id="8678b-114">任意のパブリケーションの削除。</span><span class="sxs-lookup"><span data-stu-id="8678b-114">Dropping any publications.</span></span>  
  
-   <span data-ttu-id="8678b-115">任意のアーティクルの削除。</span><span class="sxs-lookup"><span data-stu-id="8678b-115">Dropping any articles.</span></span>  
  
-   <span data-ttu-id="8678b-116">レプリケーションの無効化。</span><span class="sxs-lookup"><span data-stu-id="8678b-116">Disabling replication.</span></span>  
  
## <a name="distribution-database"></a><span data-ttu-id="8678b-117">ディストリビューション データベース</span><span class="sxs-lookup"><span data-stu-id="8678b-117">Distribution Database</span></span>  
 <span data-ttu-id="8678b-118">以下の処理の後で、ディストリビューション データベースをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="8678b-118">Backup the distribution database after:</span></span>  
  
-   <span data-ttu-id="8678b-119">レプリケーション エージェント プロファイルの作成または変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-119">Creating or modifying replication agent profiles.</span></span>  
  
-   <span data-ttu-id="8678b-120">レプリケーション エージェント プロファイルのパラメーターの変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-120">Modifying replication agent profile parameters.</span></span>  
  
-   <span data-ttu-id="8678b-121">任意のプッシュ サブスクリプションについての、レプリケーション エージェント プロパティ (スケジュールを含む) の変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-121">Changing the replication agent properties (including schedules) for any push subscriptions.</span></span>  
  
-   <span data-ttu-id="8678b-122">自動 ID 範囲管理機能による新しい ID 範囲の割り当て。</span><span class="sxs-lookup"><span data-stu-id="8678b-122">A new range of identities is assigned by the automatic identity range management feature.</span></span>  
  
## <a name="subscription-database"></a><span data-ttu-id="8678b-123">サブスクリプション データベース</span><span class="sxs-lookup"><span data-stu-id="8678b-123">Subscription Database</span></span>  
 <span data-ttu-id="8678b-124">以下の処理の後で、サブスクリプション データベースをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="8678b-124">Backup the subscription database after:</span></span>  
  
-   <span data-ttu-id="8678b-125">任意のサブスクリプション プロパティの変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-125">Changing any subscription property.</span></span>  
  
-   <span data-ttu-id="8678b-126">パブリッシャーにあるマージ サブスクリプションの優先順位の変更。</span><span class="sxs-lookup"><span data-stu-id="8678b-126">Changing the priority for a merge subscription at the Publisher.</span></span>  
  
-   <span data-ttu-id="8678b-127">任意のサブスクリプションの削除。</span><span class="sxs-lookup"><span data-stu-id="8678b-127">Dropping any subscriptions.</span></span>  
  
-   <span data-ttu-id="8678b-128">レプリケーションの無効化。</span><span class="sxs-lookup"><span data-stu-id="8678b-128">Disabling replication.</span></span>  
  
## <a name="msdb-database"></a><span data-ttu-id="8678b-129">msdb データベース</span><span class="sxs-lookup"><span data-stu-id="8678b-129">msdb Database</span></span>  
 <span data-ttu-id="8678b-130">以下の処理の後で、適切なノードで **msdb** システム データベースをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="8678b-130">Backup the **msdb** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="8678b-131">レプリケーションの有効化または無効化。</span><span class="sxs-lookup"><span data-stu-id="8678b-131">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="8678b-132">ディストリビューション データベースの追加または削除 (ディストリビューターで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-132">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="8678b-133">データベースのパブリッシュを有効化または無効化 (パブリッシャーで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-133">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="8678b-134">レプリケーション エージェント プロファイルの作成または変更 (ディストリビューターで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-134">Creating or modifying replication agent profiles (at the Distributor).</span></span>  
  
-   <span data-ttu-id="8678b-135">任意のレプリケーション エージェント パラメーターの変更 (ディストリビューターで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-135">Modifying any replication agent profile parameters (at the Distributor).</span></span>  
  
-   <span data-ttu-id="8678b-136">任意のプッシュ サブスクリプションについて、レプリケーション エージェント プロパティ (スケジュールを含む) の変更 (ディストリビューターで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-136">Changing the replication agent properties (including schedules) for any push subscriptions (at the Distributor).</span></span>  
  
-   <span data-ttu-id="8678b-137">任意のプル サブスクリプションについて、レプリケーション エージェント プロパティ (スケジュールを含む) の変更 (サブスクライバーで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-137">Changing the replication agent properties (including schedules) for any pull subscriptions (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="8678b-138">変換可能なサブスクリプションを使用するトランザクション パブリケーションに関連する DTS パッケージの作成 (ディストリビューターおよびサブスクライバーで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-138">Creating a DTS package associated with a transactional publication that uses transformable subscriptions (at the Distributor and Subscriber).</span></span>  
  
-   <span data-ttu-id="8678b-139">変換可能なサブスクリプションの追加または削除 (ディストリビューターおよびサブスクライバーで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-139">Adding or dropping a transformable subscription (at the Distributor and Subscriber).</span></span>  
  
## <a name="master-database"></a><span data-ttu-id="8678b-140">master データベース</span><span class="sxs-lookup"><span data-stu-id="8678b-140">master Database</span></span>  
 <span data-ttu-id="8678b-141">以下の処理の後で、適切なノードで **master** システム データベースをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="8678b-141">Backup the **master** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="8678b-142">レプリケーションの有効化または無効化。</span><span class="sxs-lookup"><span data-stu-id="8678b-142">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="8678b-143">ディストリビューション データベースの追加または削除 (ディストリビューターで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-143">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="8678b-144">データベースのパブリッシュを有効化または無効化 (パブリッシャーで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-144">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="8678b-145">任意のデータベースについて、先頭のパブリケーションの追加、または末尾のパブリケーションの削除 (パブリッシャーで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-145">Adding the first or dropping the last publication in any database (at the Publisher).</span></span>  
  
-   <span data-ttu-id="8678b-146">任意のデータベースについて、先頭のサブスクリプションの追加、または末尾のサブスクリプションの削除 (サブスクライバーで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-146">Adding the first or dropping the last subscription in any database (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="8678b-147">ディストリビューション パブリッシャーのパブリッシャーの有効化または無効化 (パブリッシャーおよびディストリビューターで)。</span><span class="sxs-lookup"><span data-stu-id="8678b-147">Enabling or disabling a Publisher at a Distribution Publisher (at the Publisher and Distributor).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8678b-148">参照</span><span class="sxs-lookup"><span data-stu-id="8678b-148">See Also</span></span>  
 <span data-ttu-id="8678b-149">[SQL Server データベースのバックアップと復元](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="8678b-149">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="8678b-150">レプリケートされたデータベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="8678b-150">Back Up and Restore Replicated Databases</span></span>](back-up-and-restore-replicated-databases.md)  
  
  
