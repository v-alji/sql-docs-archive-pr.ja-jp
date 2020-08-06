---
title: SQL Server のレプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e51f45e06939971ada6166fb977c787ad0354926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631769"
---
# <a name="sql-server-replication"></a><span data-ttu-id="ba57e-102">SQL Server のレプリケーション</span><span class="sxs-lookup"><span data-stu-id="ba57e-102">SQL Server Replication</span></span>
  <span data-ttu-id="ba57e-103">レプリケーションとは、あるデータベースから別のデータベースにデータやデータベース オブジェクトをコピーおよび配布し、それらのデータベースを同期させて一貫性を保つための一連のテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="ba57e-103">Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span> <span data-ttu-id="ba57e-104">レプリケーションを使用すると、ローカル エリア ネットワーク、ワイド エリア ネットワーク、ダイヤルアップ接続、ワイヤレス接続、インターネットなどを経由して、別の場所や、リモート ユーザーまたはモバイル ユーザーにデータを配布することができます。</span><span class="sxs-lookup"><span data-stu-id="ba57e-104">Using replication, you can distribute data to different locations and to remote or mobile users over local and wide area networks, dial-up connections, wireless connections, and the Internet.</span></span>  
  
 <span data-ttu-id="ba57e-105">トランザクション レプリケーションは、高いスループットが必要とされるサーバー間のシナリオで使用されるのが一般的です。たとえば、スケーラビリティと可用性の向上、データ ウェアハウジングとレポート、複数サイトからのデータの統合、異種データの統合、バッチ処理のオフロードなどのシナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ba57e-105">Transactional replication is typically used in server-to-server scenarios that require high throughput, including: improving scalability and availability; data warehousing and reporting; integrating data from multiple sites; integrating heterogeneous data; and offloading batch processing.</span></span> <span data-ttu-id="ba57e-106">マージ レプリケーションは、データの競合の可能性があるモバイル アプリケーションや分散サーバー アプリケーションを主な対象としています。</span><span class="sxs-lookup"><span data-stu-id="ba57e-106">Merge replication is primarily designed for mobile applications or distributed server applications that have possible data conflicts.</span></span> <span data-ttu-id="ba57e-107">モバイル ユーザーとのデータ交換、店舗販売時点管理 (POS) アプリケーション、複数サイトからのデータの統合などのシナリオが一般的です。</span><span class="sxs-lookup"><span data-stu-id="ba57e-107">Common scenarios include: exchanging data with mobile users; consumer point of sale (POS) applications; and integration of data from multiple sites.</span></span> <span data-ttu-id="ba57e-108">スナップショット レプリケーションは、トランザクション レプリケーションとマージ レプリケーションに初期データセットを提供するために使用されます。データの完全な更新が必要な場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba57e-108">Snapshot replication is used to provide the initial data set for transactional and merge replication; it can also be used when complete refreshes of data are appropriate.</span></span> <span data-ttu-id="ba57e-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この 3 種類のレプリケーションにより、企業全体のデータの同期のための強力かつ柔軟なシステムが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba57e-109">With these three types of replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a powerful and flexible system for synchronizing data across your enterprise.</span></span> <span data-ttu-id="ba57e-110">SQLCE 3.5 および SQLCE 4.0 に対するレプリケーションは [!INCLUDE[win8srv](../../includes/win8srv-md.md)] と [!INCLUDE[win8](../../includes/win8-md.md)]の両方でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ba57e-110">Replication to SQLCE 3.5 and SQLCE 4.0 is supported on both [!INCLUDE[win8srv](../../includes/win8srv-md.md)] and [!INCLUDE[win8](../../includes/win8-md.md)].</span></span>  
  
 <span data-ttu-id="ba57e-111">レプリケーションの代替手段として、Microsoft Sync Framework を使用してデータベースを同期できます。</span><span class="sxs-lookup"><span data-stu-id="ba57e-111">As an alternative to replication, you can synchronize databases by using Microsoft Sync Framework.</span></span> <span data-ttu-id="ba57e-112">Sync Framework には、SQL Server、SQL Server Express、SQL Server Compact、および SQL Azure の各データベース間での同期を容易にするコンポーネントと、直感的かつ柔軟性の高い API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ba57e-112">Sync Framework includes components and an intuitive and flexible API that make it easy to synchronize among SQL Server, SQL Server Express, SQL Server Compact, and SQL Azure databases.</span></span> <span data-ttu-id="ba57e-113">また、Sync Framework には、SQL Server データベースと、ADO.NET と互換性があるその他のデータベースとの間で同期を行うために使用できるクラスもあります。</span><span class="sxs-lookup"><span data-stu-id="ba57e-113">Sync Framework also includes classes that can be adapted to synchronize between a SQL Server database and any other database that is compatible with ADO.NET.</span></span> <span data-ttu-id="ba57e-114">Sync Framework のデータベース同期コンポーネントの詳細については、「 [データベースの同期](https://go.microsoft.com/fwlink/?LinkId=209079)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba57e-114">For detailed documentation of the Sync Framework database synchronization components, see [Synchronizing Databases](https://go.microsoft.com/fwlink/?LinkId=209079).</span></span> <span data-ttu-id="ba57e-115">Sync Framework の概要の詳細については、「 [Microsoft Sync Framework デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=209078)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba57e-115">For an overview of Sync Framework, see [Microsoft Sync Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=209078).</span></span> <span data-ttu-id="ba57e-116">Sync Framework とマージ レプリケーションとの比較の詳細については、データベースの同期の「 [概要とシナリオ](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba57e-116">For a comparison between Sync Framework and Merge Replication, see [Synchronizing Databases Overview](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)</span></span>  
  

## <a name="whats-new"></a><span data-ttu-id="ba57e-117">新機能</span><span class="sxs-lookup"><span data-stu-id="ba57e-117">What's new</span></span> 
- <span data-ttu-id="ba57e-118">SQL Server 2017 では、SQL Server のレプリケーションに重要な新機能は加えられていません。</span><span class="sxs-lookup"><span data-stu-id="ba57e-118">SQL Server 2017 has not introduced significant new features to SQL Server replication.</span></span> 
- <span data-ttu-id="ba57e-119">SQL Server 2016 では、SQL Server のレプリケーションに重要な新機能は加えられていません。</span><span class="sxs-lookup"><span data-stu-id="ba57e-119">SQL Server 2016 has not introduced significant new features to SQL Server replication.</span></span> 

<span data-ttu-id="ba57e-120">下位互換性の情報については、「[レプリケーションの旧バージョンとの互換性](replication-backward-compatibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba57e-120">For backward compatibility information see, [Replication Backward Compatibility](replication-backward-compatibility.md)</span></span> 


 ## <a name="replication-security"></a><span data-ttu-id="ba57e-121">レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="ba57e-121">Replication security</span></span>
  
-   [<span data-ttu-id="ba57e-122">レプリケーションのセキュリティ設定の表示および変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-122">View and Modify Replication Security Settings</span></span>](security/view-and-modify-replication-security-settings.md)  
-   [<span data-ttu-id="ba57e-123">パブリケーション アクセス リストのログインの管理</span><span class="sxs-lookup"><span data-stu-id="ba57e-123">Manage Logins in the Publication Access List</span></span>](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="publishing-and-distribution"></a><span data-ttu-id="ba57e-124">パブリッシングおよびディストリビューション</span><span class="sxs-lookup"><span data-stu-id="ba57e-124">Publishing and Distribution</span></span>  
  
-   [<span data-ttu-id="ba57e-125">パブリッシングおよびディストリビューションの構成</span><span class="sxs-lookup"><span data-stu-id="ba57e-125">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)   
-   [<span data-ttu-id="ba57e-126">パブリケーション プロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-126">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="ba57e-127">パブリッシングおよびディストリビューションの無効化</span><span class="sxs-lookup"><span data-stu-id="ba57e-127">Disable Publishing and Distribution</span></span>](disable-publishing-and-distribution.md)  
  
## <a name="publications-and-articles"></a><span data-ttu-id="ba57e-128">パブリケーションおよびアーティクル</span><span class="sxs-lookup"><span data-stu-id="ba57e-128">Publications and Articles</span></span> 
  
-   [<span data-ttu-id="ba57e-129">パブリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="ba57e-129">Create a Publication</span></span>](publish/create-a-publication.md)    
-   [<span data-ttu-id="ba57e-130">アーティクルの定義</span><span class="sxs-lookup"><span data-stu-id="ba57e-130">Define an Article</span></span>](publish/define-an-article.md)   
-   [<span data-ttu-id="ba57e-131">パブリケーション プロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-131">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="ba57e-132">アーティクルのプロパティの表示と変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-132">View and Modify Article Properties</span></span>](publish/view-and-modify-article-properties.md)    
-   [<span data-ttu-id="ba57e-133">パブリケーションの削除</span><span class="sxs-lookup"><span data-stu-id="ba57e-133">Delete a Publication</span></span>](publish/delete-a-publication.md)   
-   [<span data-ttu-id="ba57e-134">アーティクルの削除</span><span class="sxs-lookup"><span data-stu-id="ba57e-134">Delete an Article</span></span>](publish/delete-an-article.md)    
-   [<span data-ttu-id="ba57e-135">Oracle データベースからのパブリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ba57e-135">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   
-   [<span data-ttu-id="ba57e-136">サブスクリプションの有効期限の設定</span><span class="sxs-lookup"><span data-stu-id="ba57e-136">Set the Expiration Period for Subscriptions</span></span>](publish/set-the-expiration-period-for-subscriptions.md)  
-   [<span data-ttu-id="ba57e-137">スキーマ オプションの指定</span><span class="sxs-lookup"><span data-stu-id="ba57e-137">Specify Schema Options</span></span>](publish/specify-schema-options.md)  
-   [<span data-ttu-id="ba57e-138">スキーマ変更のレプリケート</span><span class="sxs-lookup"><span data-stu-id="ba57e-138">Replicate Schema Changes</span></span>](publish/replicate-schema-changes.md)    
-   [<span data-ttu-id="ba57e-139">ID 列の管理</span><span class="sxs-lookup"><span data-stu-id="ba57e-139">Manage Identity Columns</span></span>](publish/manage-identity-columns.md)   
-   [<span data-ttu-id="ba57e-140">マージ パブリケーションの互換性レベルの設定</span><span class="sxs-lookup"><span data-stu-id="ba57e-140">Set the Compatibility Level for Merge Publications</span></span>](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a><span data-ttu-id="ba57e-141">スナップショット オプション</span><span class="sxs-lookup"><span data-stu-id="ba57e-141">Snapshot Options</span></span>  
  
-   [<span data-ttu-id="ba57e-142">スナップショットのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="ba57e-142">Configure Snapshot Properties</span></span>](publish/configure-snapshot-properties-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="ba57e-143">FTP でのスナップショットの配信</span><span class="sxs-lookup"><span data-stu-id="ba57e-143">Deliver a Snapshot Through FTP</span></span>](publish/deliver-a-snapshot-through-ftp.md) 
  
### <a name="filter-data"></a><span data-ttu-id="ba57e-144">データのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="ba57e-144">Filter Data</span></span>  
  
-   [<span data-ttu-id="ba57e-145">列フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-145">Define and Modify a Column Filter</span></span>](publish/define-and-modify-a-column-filter.md)    
-   [<span data-ttu-id="ba57e-146">静的行フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-146">Define and Modify a Static Row Filter</span></span>](publish/define-and-modify-a-static-row-filter.md)    
-   [<span data-ttu-id="ba57e-147">マージ アーティクルのパラメーター化された行フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-147">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)    
-   [<span data-ttu-id="ba57e-148">パラメーター化された行フィルターの最適化</span><span class="sxs-lookup"><span data-stu-id="ba57e-148">Optimize Parameterized Row Filters</span></span>](publish/optimize-parameterized-row-filters.md)    
-   [<span data-ttu-id="ba57e-149">マージ アーティクル間の結合フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-149">Define and Modify a Join Filter Between Merge Articles</span></span>](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a><span data-ttu-id="ba57e-150">トランザクション レプリケーション オプション</span><span class="sxs-lookup"><span data-stu-id="ba57e-150">Transactional Replication Options</span></span>  
  
-   [<span data-ttu-id="ba57e-151">データの変更をトランザクション アーティクルに反映する方法の設定</span><span class="sxs-lookup"><span data-stu-id="ba57e-151">Set the Propagation Method for Data Changes to Transactional Articles</span></span>](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)    
-   [<span data-ttu-id="ba57e-152">トランザクション パブリケーションの更新可能なサブスクリプションの有効化</span><span class="sxs-lookup"><span data-stu-id="ba57e-152">Enable Updating Subscriptions for Transactional Publications</span></span>](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a><span data-ttu-id="ba57e-153">マージ レプリケーション オプション</span><span class="sxs-lookup"><span data-stu-id="ba57e-153">Merge Replication Options</span></span>  
  
-   [<span data-ttu-id="ba57e-154">マージ テーブル アーティクル間に論理レコード リレーションシップを定義する</span><span class="sxs-lookup"><span data-stu-id="ba57e-154">Define a Logical Record Relationship Between Merge Table Articles</span></span>](publish/define-a-logical-record-relationship-between-merge-table-articles.md)    
-   [<span data-ttu-id="ba57e-155">マージ レプリケーションのプロパティの指定</span><span class="sxs-lookup"><span data-stu-id="ba57e-155">Specify Merge replication properties</span></span>](publish/specify-merge-replication-properties.md)    
-   [<span data-ttu-id="ba57e-156">マージ アーティクル競合回避モジュールの指定</span><span class="sxs-lookup"><span data-stu-id="ba57e-156">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)    

  
## <a name="manage-subscriptions"></a><span data-ttu-id="ba57e-157">サブスクリプションを管理する</span><span class="sxs-lookup"><span data-stu-id="ba57e-157">Manage Subscriptions</span></span>  
  
-   [<span data-ttu-id="ba57e-158">Create a Pull Subscription</span><span class="sxs-lookup"><span data-stu-id="ba57e-158">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)    
-   [<span data-ttu-id="ba57e-159">プル サブスクリプションのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-159">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)    
-   [<span data-ttu-id="ba57e-160">プル サブスクリプションの削除</span><span class="sxs-lookup"><span data-stu-id="ba57e-160">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)    
-   [<span data-ttu-id="ba57e-161">プッシュ サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="ba57e-161">Create a Push Subscription</span></span>](create-a-push-subscription.md)   
-   [<span data-ttu-id="ba57e-162">プッシュ サブスクリプションのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="ba57e-162">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)   
-   [<span data-ttu-id="ba57e-163">プッシュ サブスクリプションの削除</span><span class="sxs-lookup"><span data-stu-id="ba57e-163">Delete a Push Subscription</span></span>](delete-a-push-subscription.md)   
-   [<span data-ttu-id="ba57e-164">同期スケジュールの指定</span><span class="sxs-lookup"><span data-stu-id="ba57e-164">Specify Synchronization Schedules</span></span>](specify-synchronization-schedules.md)    
-   [<span data-ttu-id="ba57e-165">トランザクション パブリケーションの更新可能なサブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="ba57e-165">Create an Updatable Subscription to a Transactional Publication</span></span>](publish/create-an-updatable-subscription-to-a-transactional-publication.md)  
-   [<span data-ttu-id="ba57e-166">SQL Server 以外のサブスクライバーのサブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="ba57e-166">Create a Subscription for a Non-SQL Server Subscriber</span></span>](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronize-subscriptions"></a><span data-ttu-id="ba57e-167">サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="ba57e-167">Synchronize Subscriptions</span></span>  
  
-   [<span data-ttu-id="ba57e-168">初期スナップショットの作成および適用</span><span class="sxs-lookup"><span data-stu-id="ba57e-168">Create and Apply the Initial Snapshot</span></span>](create-and-apply-the-initial-snapshot.md)   
-   [<span data-ttu-id="ba57e-169">パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成</span><span class="sxs-lookup"><span data-stu-id="ba57e-169">Create a Snapshot for a Merge Publication with Parameterized Filters</span></span>](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="ba57e-170">バックアップからのトランザクション サブスクリプションの初期化</span><span class="sxs-lookup"><span data-stu-id="ba57e-170">Initialize a Transactional Subscription from a Backup</span></span>](initialize-a-transactional-subscription-from-a-backup.md)    
-   [<span data-ttu-id="ba57e-171">手動によるサブスクリプションの初期化</span><span class="sxs-lookup"><span data-stu-id="ba57e-171">Initialize a Subscription Manually</span></span>](initialize-a-subscription-manually.md)    
-   [<span data-ttu-id="ba57e-172">プル サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="ba57e-172">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)    
-   [<span data-ttu-id="ba57e-173">プッシュ サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="ba57e-173">Synchronize a Push Subscription</span></span>](synchronize-a-push-subscription.md)   
-   [<span data-ttu-id="ba57e-174">サブスクリプションの再初期化</span><span class="sxs-lookup"><span data-stu-id="ba57e-174">Reinitialize a Subscription</span></span>](reinitialize-a-subscription.md)    
-   [<span data-ttu-id="ba57e-175">同期中のスクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="ba57e-175">Execute Scripts During Synchronization</span></span>](execute-scripts-during-synchronization-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="ba57e-176">マージ アーティクルのビジネス ロジック ハンドラーの実装</span><span class="sxs-lookup"><span data-stu-id="ba57e-176">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
-   [<span data-ttu-id="ba57e-177">ビジネス ロジック ハンドラーのデバッグ&#40;レプリケーション プログラミング&#41;</span><span class="sxs-lookup"><span data-stu-id="ba57e-177">Debug a Business Logic Handler &#40;Replication Programming&#41;</span></span>](debug-a-business-logic-handler-replication-programming.md)    
-   [<span data-ttu-id="ba57e-178">同期中にトリガーと制約の動作を制御する</span><span class="sxs-lookup"><span data-stu-id="ba57e-178">Control the Behavior of Triggers and Constraints During Synchronization</span></span>](control-behavior-of-triggers-and-constraints-in-synchronization.md)    
-   [<span data-ttu-id="ba57e-179">マージ アーティクルのカスタム競合回避モジュールの実装</span><span class="sxs-lookup"><span data-stu-id="ba57e-179">Implement a Custom Conflict Resolver for a Merge Article</span></span>](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administeration"></a><span data-ttu-id="ba57e-180">このように</span><span class="sxs-lookup"><span data-stu-id="ba57e-180">Administeration</span></span> 
  
-   [<span data-ttu-id="ba57e-181">レプリケーション エージェント プロファイルの操作</span><span class="sxs-lookup"><span data-stu-id="ba57e-181">Work with Replication Agent Profiles</span></span>](agents/work-with-replication-agent-profiles.md)   
-   [<span data-ttu-id="ba57e-182">サブスクライバーでのデータの検証</span><span class="sxs-lookup"><span data-stu-id="ba57e-182">Validate Data at the Subscriber</span></span>](validate-data-at-the-subscriber.md)    
-   [<span data-ttu-id="ba57e-183">パラメーター化されたフィルターによるマージ パブリケーションのパーティションの管理</span><span class="sxs-lookup"><span data-stu-id="ba57e-183">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="ba57e-184">マージ パブリケーションでのテーブルへのデータの一括読み込み</span><span class="sxs-lookup"><span data-stu-id="ba57e-184">Bulk-Load Data into Tables in a Merge Publication</span></span>](bulk-load-data-into-tables-in-a-merge-publication.md)    
-   [<span data-ttu-id="ba57e-185">マージメタデータのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="ba57e-185">Clean Up Merge Metadata</span></span>](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="ba57e-186">マージアーティクルのダミー更新の実行</span><span class="sxs-lookup"><span data-stu-id="ba57e-186">Perform a Dummy Update for a Merge Article</span></span>](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="ba57e-187">ディストリビューションデータベース内のレプリケートされたコマンドおよびその他の情報を表示する</span><span class="sxs-lookup"><span data-stu-id="ba57e-187">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="ba57e-188">トランザクション レプリケーションの連携バックアップの有効化</span><span class="sxs-lookup"><span data-stu-id="ba57e-188">Enable Coordinated Backups for Transactional Replication</span></span>](administration/enable-coordinated-backups-for-transactional-replication.md)   
-   [<span data-ttu-id="ba57e-189">ピアツーピアトポロジの管理</span><span class="sxs-lookup"><span data-stu-id="ba57e-189">Administer a Peer-to-Peer Topology</span></span>](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="ba57e-190">レプリケーショントポロジの停止</span><span class="sxs-lookup"><span data-stu-id="ba57e-190">Quiesce a Replication Topology</span></span>](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="ba57e-191">Oracle パブリッシャー用のトランザクション セット ジョブの構成</span><span class="sxs-lookup"><span data-stu-id="ba57e-191">Configure the Transaction Set Job for an Oracle Publisher</span></span>](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
-   [<span data-ttu-id="ba57e-192">レプリケーションスクリプトのアップグレード</span><span class="sxs-lookup"><span data-stu-id="ba57e-192">Upgrade Replication Scripts</span></span>](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitor"></a><span data-ttu-id="ba57e-193">モニター</span><span class="sxs-lookup"><span data-stu-id="ba57e-193">Monitor</span></span>
  
-   [<span data-ttu-id="ba57e-194">管理者以外のユーザーがレプリケーション モニターを使用できるようにする</span><span class="sxs-lookup"><span data-stu-id="ba57e-194">Allow Non-Administrators to Use Replication Monitor</span></span>](monitor/allow-non-administrators-to-use-replication-monitor.md)    
-   [<span data-ttu-id="ba57e-195">プログラムによるレプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="ba57e-195">Programmatically Monitor Replication</span></span>](monitor/programmatically-monitor-replication.md)    
-   [<span data-ttu-id="ba57e-196">ディストリビューションデータベース内のレプリケートされたコマンドおよびその他の情報を表示する</span><span class="sxs-lookup"><span data-stu-id="ba57e-196">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="ba57e-197">マージ パブリケーションの競合情報の表示</span><span class="sxs-lookup"><span data-stu-id="ba57e-197">View Conflict Information for Merge Publications</span></span>](view-conflict-information-for-merge-publications.md) 
-   [<span data-ttu-id="ba57e-198">待機時間を計測して Connections for Transactional Replication を検証します。</span><span class="sxs-lookup"><span data-stu-id="ba57e-198">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  