---
title: パブリケーション プロパティの表示および変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- publications [SQL Server replication], properties
- articles [SQL Server replication], properties
- modifying replication properties, publications
- publications [SQL Server replication], modifying
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 89b969bc3e285bbdc633a2b39d237968b216069a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631791"
---
# <a name="view-and-modify-publication-properties"></a><span data-ttu-id="add06-102">パブリケーション プロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="add06-102">View and Modify Publication Properties</span></span>
  <span data-ttu-id="add06-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリケーションのプロパティを表示および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="add06-103">This topic describes how to view and modify publication properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="add06-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="add06-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="add06-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="add06-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="add06-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="add06-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="add06-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="add06-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="add06-108">**パブリケーションのプロパティを表示または変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="add06-108">**To view and modify publication properties, using:**</span></span>  
  
     [<span data-ttu-id="add06-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="add06-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="add06-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="add06-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="add06-111">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="add06-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="add06-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="add06-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="add06-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="add06-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="add06-114">パブリケーションの作成後には変更できないプロパティや、パブリケーションへのサブスクリプションがある場合には変更できないプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="add06-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="add06-115">変更できないプロパティは、読み取り専用として表示されます。</span><span class="sxs-lookup"><span data-stu-id="add06-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="add06-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="add06-116">Recommendations</span></span>  
  
-   <span data-ttu-id="add06-117">パブリケーションの作成後、プロパティの変更によっては新しいスナップショットが必要となります。</span><span class="sxs-lookup"><span data-stu-id="add06-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="add06-118">パブリケーションにサブスクリプションが含まれている場合、変更によっては、すべてのサブスクリプションを再初期化する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="add06-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="add06-119">詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」 (パブリケーションおよびアーティクルのプロパティの変更) と「[既存のパブリケーションでのアーティクルの追加および削除](add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add06-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="add06-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="add06-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="add06-121">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] とレプリケーション モニターで使用可能な **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、パブリケーションのプロパティを表示および変更します。</span><span class="sxs-lookup"><span data-stu-id="add06-121">View and modify publication properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="add06-122">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add06-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="add06-123">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスには、以下のページがあります。</span><span class="sxs-lookup"><span data-stu-id="add06-123">The **Publication Properties - \<Publication>** dialog box includes the following pages:</span></span>  
  
-   <span data-ttu-id="add06-124">**[全般]** ページ。パブリケーションの名前と説明、データベースの名前、パブリケーションの種類、およびサブスクリプションの有効期限の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="add06-124">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="add06-125">**[アーティクル]** ページ。パブリケーションの新規作成ウィザードの **[アーティクル]** ページに相当します。</span><span class="sxs-lookup"><span data-stu-id="add06-125">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="add06-126">このページでは、アーティクルの追加や削除、およびアーティクルのプロパティや列のフィルター選択の変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="add06-126">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="add06-127">**[行のフィルター選択]** ページ。パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページに相当します。</span><span class="sxs-lookup"><span data-stu-id="add06-127">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="add06-128">このページでは、すべての種類のパブリケーションの静的行フィルターや、マージ パブリケーションのパラメーター化された行フィルターと結合フィルターを追加、編集、および削除できます。</span><span class="sxs-lookup"><span data-stu-id="add06-128">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="add06-129">**[スナップショット]** ページ。このページでは、スナップショットの形式と場所、スナップショットを圧縮するかどうか、およびスナップショットの適用の前後に実行するスクリプトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="add06-129">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="add06-130">**[FTP スナップショット]** ページ (スナップショット パブリケーション、トランザクション パブリケーション、および SQL Server 2005 より前のバージョンを実行しているパブリッシャーのマージ パブリケーションの場合)。このページでは、サブスクライバーがスナップショット ファイルをファイル転送プロトコル (FTP) でダウンロードできるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="add06-130">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="add06-131">**[FTP スナップショットとインターネット]** ページ (SQL Server 2005 以降を実行しているパブリッシャーからのマージ パブリケーションの場合)。このページでは、サブスクライバーがスナップショット ファイルを FTP でダウンロードできるかどうか、および HTTPS でサブスクリプションを同期できるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="add06-131">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="add06-132">**[サブスクリプション オプション]** ページ。このページでは、すべてのサブスクリプションに適用されるさまざまなオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="add06-132">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="add06-133">利用できるオプションは、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="add06-133">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="add06-134">**[パブリケーション アクセス リスト]** ページ。このページでは、パブリケーションにアクセスできるログインやグループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="add06-134">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="add06-135">**[エージェント セキュリティ]** ページ。このページでは、エージェントの実行やレプリケーション トポロジ内のコンピューターへの接続に使用されるアカウントの設定にアクセスできます。この設定を使用するエージェントは、すべてのパブリケーションのスナップショット エージェント、すべてのトランザクション パブリケーションのログ リーダー エージェント、およびキュー更新サブスクリプションを許可するトランザクション パブリケーションのキュー リーダー エージェントです。</span><span class="sxs-lookup"><span data-stu-id="add06-135">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="add06-136">**[データ パーティション]** ページ (SQL Server 2005 以降を実行しているパブリッシャーからのマージ パブリケーションの場合)。このページでは、パラメーター化されたフィルターを使用するパブリケーションのサブスクライバーが、スナップショットを利用できない場合にスナップショットを要求できるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="add06-136">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="add06-137">また、1 つ以上のパーティションのスナップショットを 1 回生成したり、スケジュールによって定期的に生成したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="add06-137">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-management-studio"></a><span data-ttu-id="add06-138">Management Studio でパブリケーションのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="add06-138">To view and modify publication properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="add06-139">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="add06-139">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="add06-140">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="add06-140">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="add06-141">パブリケーションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="add06-141">Right-click a publication, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="add06-142">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="add06-142">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-replication-monitor"></a><span data-ttu-id="add06-143">レプリケーション モニターでパブリケーションのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="add06-143">To view and modify publication properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="add06-144">レプリケーション モニターの左ペインでパブリッシャー グループを展開し、パブリッシャーを展開します。</span><span class="sxs-lookup"><span data-stu-id="add06-144">Expand a Publisher group in the left pane of Replication Monitor, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="add06-145">パブリケーションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="add06-145">Right-click a publication, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="add06-146">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="add06-146">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="add06-147">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="add06-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="add06-148">パブリケーションのプロパティは、レプリケーションのストアド プロシージャを使用して、プログラムから変更および取得できます。</span><span class="sxs-lookup"><span data-stu-id="add06-148">Publications can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="add06-149">どのストアド プロシージャを使用するかは、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="add06-149">The stored procedures that you use will depend on the type of publication.</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="add06-150">スナップショット パブリケーションまたはトランザクション パブリケーションのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="add06-150">To view the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="add06-151">**\@publication** パラメーターにパブリケーション名を指定して、[sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="add06-151">Execute [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="add06-152">このパラメーターを指定しなかった場合、パブリッシャーのすべてのパブリケーションの情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="add06-152">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="add06-153">スナップショット パブリケーションまたはトランザクション パブリケーションのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="add06-153">To change the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="add06-154">[sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。このとき、変更するパブリケーションのプロパティを **\@property** パラメーターに指定し、このプロパティの新しい値を **\@value** パラメーターに指定します。</span><span class="sxs-lookup"><span data-stu-id="add06-154">Execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying the publication property to change in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="add06-155">さらに、新しいスナップショットを生成する必要がある場合は、 **\@force_invalidate_snapshot** に **1** を、また、サブスクライバーを再初期化する必要がある場合は、 **\@force_reinit_subscription** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="add06-155">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="add06-156">変更時に新しいスナップショットの生成または再初期化が必要となるプロパティの詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add06-156">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-merge-publication"></a><span data-ttu-id="add06-157">マージ パブリケーションのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="add06-157">To view the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="add06-158">**\@publication** パラメーターにパブリケーション名を指定して、[sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="add06-158">Execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="add06-159">このパラメーターを指定しなかった場合、パブリッシャーのすべてのパブリケーションの情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="add06-159">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-merge-publication"></a><span data-ttu-id="add06-160">マージ パブリケーションのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="add06-160">To change the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="add06-161">[sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) を実行します。このとき、変更するパブリケーションのプロパティを **\@property** パラメーターに指定し、このプロパティの新しい値を **\@value** パラメーターに指定します。</span><span class="sxs-lookup"><span data-stu-id="add06-161">Execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying the publication property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="add06-162">さらに、新しいスナップショットを生成する必要がある場合は、 **\@force_invalidate_snapshot** に **1** を、また、サブスクライバーを再初期化する必要がある場合は、 **\@force_reinit_subscription** に **1** を指定します。変更時に新しいスナップショットの生成または再初期化が必要となるプロパティの詳細については、「[パブリケーションおよびアーティクルのプロパティの変更](change-publication-and-article-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add06-162">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription** For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot"></a><span data-ttu-id="add06-163">スナップショットのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="add06-163">To view the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="add06-164">**\@publication** パラメーターにパブリケーション名を指定して、[sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="add06-164">Execute [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot"></a><span data-ttu-id="add06-165">スナップショットのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="add06-165">To change the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="add06-166">変更対象のスナップショット パラメーターに新しいスナップショット プロパティを少なくとも 1 つ指定して、 [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="add06-166">Execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql), specifying one or more of the new snapshot properties for the appropriate snapshot parameters.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="add06-167">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="add06-167">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="add06-168">パブリケーションのプロパティを取得するトランザクション レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="add06-168">This transactional replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_helppublication)]  
  
 <span data-ttu-id="add06-169">パブリケーションのスキーマ レプリケーションを無効化するトランザクション レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="add06-169">This transactional replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_changepublication)]  
  
 <span data-ttu-id="add06-170">パブリケーションのプロパティを取得するマージ レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="add06-170">This merge replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_helpmergepublication)]  
  
 <span data-ttu-id="add06-171">パブリケーションのスキーマ レプリケーションを無効化するマージ レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="add06-171">This merge replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_changemergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="add06-172">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="add06-172">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="add06-173">レプリケーション管理オブジェクト (RMO) を使用して、パブリケーションの変更とそのプロパティへのアクセスをプログラムから実行できます。</span><span class="sxs-lookup"><span data-stu-id="add06-173">You can modify publications and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="add06-174">パブリケーション プロパティの表示と変更に使用する RMO クラスは、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="add06-174">The RMO classes that you use to view or modify publication properties depend on the type of publication.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="add06-175">スナップショット パブリケーションまたはトランザクション パブリケーションのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="add06-175">To view or modify properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="add06-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="add06-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="add06-177"><xref:Microsoft.SqlServer.Replication.TransPublication> クラスのインスタンスを作成し、パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティと <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定して、手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="add06-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="add06-178"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="add06-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="add06-179">このメソッドが `false` を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="add06-179">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="add06-180">(省略可) プロパティを変更するには、設定可能なプロパティに新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="add06-180">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="add06-181"><xref:Microsoft.SqlServer.Replication.PublicationAttributes> プロパティに特定の <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 値が設定されているかどうかを判断するには、論理積演算子 (Microsoft Visual C# では `&`、Microsoft Visual Basic では `And`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="add06-181">Use the logical AND operator (`&` in Microsoft Visual C# and `And` in Microsoft Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="add06-182"><xref:Microsoft.SqlServer.Replication.PublicationAttributes> プロパティの <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 値を変更するには、包括的論理和演算子 (Visual C# では `|`、Visual Basic では `Or`) および排他的論理和演算子 (Visual C# では `^`、Visual Basic では `Xor`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="add06-182">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="add06-183">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `true` を指定した場合、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="add06-183">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="add06-184"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `false` (既定値) を指定した場合、変更は直ちにサーバーに送られます。</span><span class="sxs-lookup"><span data-stu-id="add06-184">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-merge-publication"></a><span data-ttu-id="add06-185">マージ パブリケーションのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="add06-185">To view or modify properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="add06-186"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="add06-186">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="add06-187"><xref:Microsoft.SqlServer.Replication.MergePublication> クラスのインスタンスを作成し、パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティと <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定して、手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="add06-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="add06-188"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="add06-188">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="add06-189">このメソッドが `false` を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="add06-189">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="add06-190">(省略可) プロパティを変更するには、設定可能なプロパティに新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="add06-190">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="add06-191"><xref:Microsoft.SqlServer.Replication.PublicationAttributes> プロパティに特定の <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 値が設定されているかどうかを判断するには、論理積演算子 (Visual C# では `&`、Visual Basic では `And`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="add06-191">Use the logical AND operator (`&` in Visual C# and `And` in Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="add06-192"><xref:Microsoft.SqlServer.Replication.PublicationAttributes> プロパティの <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 値を変更するには、包括的論理和演算子 (Visual C# では `|`、Visual Basic では `Or`) および排他的論理和演算子 (Visual C# では `^`、Visual Basic では `Xor`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="add06-192">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="add06-193">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `true` を指定した場合、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="add06-193">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="add06-194"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `false` (既定値) を指定した場合、変更は直ちにサーバーに送られます。</span><span class="sxs-lookup"><span data-stu-id="add06-194">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="add06-195">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="add06-195">Examples (RMO)</span></span>  
 <span data-ttu-id="add06-196">次の例では、トランザクション パブリケーションにパブリケーション属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="add06-196">This example sets publication attributes for a transactional publication.</span></span> <span data-ttu-id="add06-197">変更は明示的にサーバーに送られるまでキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="add06-197">The changes are cached until explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 <span data-ttu-id="add06-198">次の例では、マージ パブリケーションの DDL レプリケーションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="add06-198">This example disables DDL replication for a merge publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## <a name="see-also"></a><span data-ttu-id="add06-199">参照</span><span class="sxs-lookup"><span data-stu-id="add06-199">See Also</span></span>  
 <span data-ttu-id="add06-200">[データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="add06-200">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="add06-201">[パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="add06-201">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="add06-202">[パブリケーション データベースでのスキーマの変更](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="add06-202">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 <span data-ttu-id="add06-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="add06-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="add06-204">[パブリケーションに対してアーティクルを追加または削除する](add-articles-to-and-drop-articles-from-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="add06-204">[Add Articles to and Drop Articles from a Publication](add-articles-to-and-drop-articles-from-a-publication.md) </span></span>  
 <span data-ttu-id="add06-205">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="add06-205">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="add06-206">アーティクルのプロパティの表示と変更</span><span class="sxs-lookup"><span data-stu-id="add06-206">View and Modify Article Properties</span></span>](view-and-modify-article-properties.md)  
  
  
