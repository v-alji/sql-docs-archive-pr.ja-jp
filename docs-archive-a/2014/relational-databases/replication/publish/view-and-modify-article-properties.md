---
title: アーティクルのプロパティの表示および変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changearticle
- sp_helparticle
- viewing replication properties
- sp_changemergearticle
- sp_helpmergearticle
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- articles [SQL Server replication], properties
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8194b5cc2d4c4a2f1f116ca5a99ea16e18156f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719833"
---
# <a name="view-and-modify-article-properties"></a><span data-ttu-id="a77b4-102">アーティクルのプロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="a77b4-102">View and Modify Article Properties</span></span>
  <span data-ttu-id="a77b4-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、アーティクルのプロパティを表示および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-103">This topic describes how to view and modify article properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="a77b4-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a77b4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a77b4-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a77b4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a77b4-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a77b4-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a77b4-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="a77b4-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="a77b4-108">**アーティクルのプロパティを表示および変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="a77b4-108">**To view and modify article properties, using:**</span></span>  
  
     [<span data-ttu-id="a77b4-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a77b4-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a77b4-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a77b4-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="a77b4-111">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="a77b4-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a77b4-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="a77b4-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a77b4-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a77b4-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a77b4-114">パブリケーションの作成後には変更できないプロパティや、パブリケーションへのサブスクリプションがある場合には変更できないプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="a77b4-115">変更できないプロパティは、読み取り専用として表示されます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a77b4-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="a77b4-116">Recommendations</span></span>  
  
-   <span data-ttu-id="a77b4-117">パブリケーションの作成後、プロパティの変更によっては新しいスナップショットが必要となります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="a77b4-118">パブリケーションにサブスクリプションが含まれている場合、変更によっては、すべてのサブスクリプションを再初期化する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="a77b4-119">詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」 (パブリケーションおよびアーティクルのプロパティの変更) と「[既存のパブリケーションでのアーティクルの追加および削除](add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a77b4-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a77b4-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a77b4-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a77b4-121">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] とレプリケーション モニターにある **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、アーティクルのプロパティを表示および変更します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-121">View and modify article properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="a77b4-122">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a77b4-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="a77b4-123">**[全般]** ページ。パブリケーションの名前と説明、データベースの名前、パブリケーションの種類、およびサブスクリプションの有効期限の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a77b4-123">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="a77b4-124">**[アーティクル]** ページ。パブリケーションの新規作成ウィザードの **[アーティクル]** ページに相当します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-124">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="a77b4-125">このページでは、アーティクルの追加や削除、およびアーティクルのプロパティや列のフィルター選択の変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-125">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="a77b4-126">**[行のフィルター選択]** ページ。パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページに相当します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-126">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="a77b4-127">このページでは、すべての種類のパブリケーションの静的行フィルターや、マージ パブリケーションのパラメーター化された行フィルターと結合フィルターを追加、編集、および削除できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-127">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="a77b4-128">**[スナップショット]** ページ。このページでは、スナップショットの形式と場所、スナップショットを圧縮するかどうか、およびスナップショットの適用の前後に実行するスクリプトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-128">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="a77b4-129">**[FTP スナップショット]** ページ (スナップショット パブリケーション、トランザクション パブリケーション、および SQL Server 2005 より前のバージョンを実行しているパブリッシャーのマージ パブリケーションの場合)。このページでは、サブスクライバーがスナップショット ファイルをファイル転送プロトコル (FTP) でダウンロードできるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-129">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="a77b4-130">**[FTP スナップショットとインターネット]** ページ (SQL Server 2005 以降を実行しているパブリッシャーからのマージ パブリケーションの場合)。このページでは、サブスクライバーがスナップショット ファイルを FTP でダウンロードできるかどうか、および HTTPS でサブスクリプションを同期できるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-130">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="a77b4-131">**[サブスクリプション オプション]** ページ。このページでは、すべてのサブスクリプションに適用されるさまざまなオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-131">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="a77b4-132">利用できるオプションは、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-132">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="a77b4-133">**[パブリケーション アクセス リスト]** ページ。このページでは、パブリケーションにアクセスできるログインやグループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-133">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="a77b4-134">**[エージェント セキュリティ]** ページ。このページでは、エージェントの実行やレプリケーション トポロジ内のコンピューターへの接続に使用されるアカウントの設定にアクセスできます。この設定を使用するエージェントは、すべてのパブリケーションのスナップショット エージェント、すべてのトランザクション パブリケーションのログ リーダー エージェント、およびキュー更新サブスクリプションを許可するトランザクション パブリケーションのキュー リーダー エージェントです。</span><span class="sxs-lookup"><span data-stu-id="a77b4-134">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="a77b4-135">**[データ パーティション]** ページ (SQL Server 2005 以降を実行しているパブリッシャーからのマージ パブリケーションの場合)。このページでは、パラメーター化されたフィルターを使用するパブリケーションのサブスクライバーが、スナップショットを利用できない場合にスナップショットを要求できるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-135">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="a77b4-136">また、1 つ以上のパーティションのスナップショットを 1 回生成したり、スケジュールによって定期的に生成したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-136">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-article-properties"></a><span data-ttu-id="a77b4-137">アーティクルのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="a77b4-137">To view and modify article properties</span></span>  
  
1.  <span data-ttu-id="a77b4-138">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、アーティクルを選択し、 **[アーティクルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a77b4-138">On the **Articles** Page of the **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="a77b4-139">プロパティの変更を適用するアーティクルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-139">Select which articles property changes should apply to:</span></span>  
  
    -   <span data-ttu-id="a77b4-140">**[反転表示された \<ObjectType> アーティクルのプロパティを設定]** をクリックして、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、 **[アーティクル]** ページのオブジェクト ペインで反転表示されたオブジェクトのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-140">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="a77b4-141">**[すべての\<ObjectType> アーティクルのプロパティを設定]** をクリックして、 **[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、パブリケーション用に選択されていないオブジェクトも含め、 **[アーティクル]** ページのオブジェクト ペインにあるこの種類のすべてのオブジェクトに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-141">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a77b4-142">**[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスで行われたプロパティの変更は、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスで以前行われた変更をすべてオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a77b4-142">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="a77b4-143">たとえば、あるオブジェクトの種類のすべてのアーティクルに対して複数の既定を設定し、かつそれぞれのオブジェクトに対してプロパティを設定する場合には、最初にすべてのアーティクルに対する既定を設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-143">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="a77b4-144">次に、それぞれのオブジェクトに対してプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-144">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="a77b4-145">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a77b4-145">Modify any properties if necessary, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="a77b4-146">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a77b4-146">Click **OK** on the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a77b4-147">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a77b4-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="a77b4-148">アーティクルのプロパティは、レプリケーションのストアド プロシージャを使用して、プログラムから変更および取得できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-148">Articles can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="a77b4-149">使用するストアド プロシージャは、アーティクルが属するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-149">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a77b4-150">スナップショット パブリケーションまたはトランザクション パブリケーションに属するアーティクルのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="a77b4-150">To view the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a77b4-151">[Sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)を実行します。 \*\* \@ パブリケーション**パラメーターにはパブリケーションの名前を指定し、 \*\* \@ アーティクル**パラメーターにはアーティクルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-151">Execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="a77b4-152">\*\* \@ アーティクル\*\*を指定しない場合は、パブリケーションのすべてのアーティクルに関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-152">If you do not specify **\@article**, information will be returned for all articles in the publication.</span></span>  
  
2.  <span data-ttu-id="a77b4-153">テーブル アーティクルについて [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) を実行し、ベース テーブルで使用できるすべての列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-153">Execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a77b4-154">スナップショット パブリケーションまたはトランザクション パブリケーションに属するアーティクルのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="a77b4-154">To modify the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a77b4-155">[Sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)を実行します。これには、 \*\* \@ property**パラメーターで変更するアーティクルプロパティと** \@ value\*\*パラメーターのこのプロパティの新しい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-155">Execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a77b4-156">変更時に新しいスナップショットの生成が必要な場合は、 \*\* \@ force_invalidate_snapshot**に**1**を指定する必要があります。また、サブスクライバーを再初期化する必要がある場合は、 \*\* \@ force_reinit_subscription**に値**1**を指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-156">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="a77b4-157">変更時に新しいスナップショットの生成または再初期化が必要となるプロパティの詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a77b4-157">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="a77b4-158">マージ パブリケーションに属するアーティクルのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="a77b4-158">To view the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="a77b4-159">[Sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)を実行します。 \*\* \@ パブリケーション**パラメーターにはパブリケーションの名前を指定し、 \*\* \@ アーティクル**パラメーターにはアーティクルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-159">Execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="a77b4-160">これらのパラメーターを指定しない場合、パブリケーションまたはパブリッシャーのすべてのアーティクルに関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-160">If you do not specify these parameters, information will be returned for all articles in a publication or at the publisher.</span></span>  
  
2.  <span data-ttu-id="a77b4-161">テーブル アーティクルに対して [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) を実行し、ベース テーブルで使用できるすべての列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-161">Execute [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="a77b4-162">マージ パブリケーションに属するアーティクルのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="a77b4-162">To modify the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="a77b4-163">[Sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。これには、 \*\* \@ property**パラメーターで変更するアーティクルプロパティと** \@ value\*\*パラメーターのこのプロパティの新しい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-163">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a77b4-164">変更時に新しいスナップショットの生成が必要な場合は、 \*\* \@ force_invalidate_snapshot**に**1**を指定する必要があります。また、サブスクライバーを再初期化する必要がある場合は、 \*\* \@ force_reinit_subscription**に値**1**を指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-164">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="a77b4-165">変更時に新しいスナップショットの生成または再初期化が必要となるプロパティの詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a77b4-165">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a77b4-166">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a77b4-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="a77b4-167">パブリッシュされたアーティクルのプロパティを取得するトランザクション レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-167">This transactional replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_helptranarticle)]  
  
 <span data-ttu-id="a77b4-168">パブリッシュされたアーティクルのスキーマ オプションを変更するトランザクション レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-168">This transactional replication example changes the schema options for the published article.</span></span>  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_changetranarticle)]  
  
 <span data-ttu-id="a77b4-169">パブリッシュされたアーティクルのプロパティを取得するマージ レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-169">This merge replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_helpmergearticle)]  
  
 <span data-ttu-id="a77b4-170">パブリッシュされたアーティクルの競合検出の設定を変更するマージ レプリケーションの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-170">This merge replication example changes the conflict detection settings for a published article.</span></span>  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_changemergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="a77b4-171">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="a77b4-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="a77b4-172">アーティクルのプロパティは、レプリケーション管理オブジェクト (RMO) を使用してプログラムから変更できます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-172">You can modify articles and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="a77b4-173">アーティクルのプロパティを表示または変更する際に使用する RMO のクラスは、アーティクルが属しているパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a77b4-173">The RMO classes you use to view or modify article properties depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a77b4-174">スナップショット パブリケーションまたはトランザクション パブリケーションに属しているアーティクルのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="a77b4-174">To view or modify properties of an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a77b4-175"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-175">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a77b4-176"><xref:Microsoft.SqlServer.Replication.TransArticle> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="a77b4-177"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-177">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="a77b4-178">手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="a77b4-179"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="a77b4-180">このメソッドから `false` が返された場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。</span><span class="sxs-lookup"><span data-stu-id="a77b4-180">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="a77b4-181">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.TransArticle> の設定可能なプロパティに新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="a77b4-182">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `true` を指定した場合、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="a77b4-182">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="a77b4-183"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `false` (既定値) を指定した場合、変更は直ちにサーバーに送られます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-183">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="a77b4-184">マージ パブリケーションに属しているアーティクルのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="a77b4-184">To view or modify properties of an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="a77b4-185"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-185">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a77b4-186"><xref:Microsoft.SqlServer.Replication.MergeArticle> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="a77b4-187"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-187">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="a77b4-188">手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-188">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="a77b4-189"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-189">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="a77b4-190">このメソッドから `false` が返された場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。</span><span class="sxs-lookup"><span data-stu-id="a77b4-190">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="a77b4-191">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.MergeArticle> の設定可能なプロパティに新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a77b4-191">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="a77b4-192">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `true` を指定した場合、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="a77b4-192">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="a77b4-193"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に `false` (既定値) を指定した場合、変更は直ちにサーバーに送られます。</span><span class="sxs-lookup"><span data-stu-id="a77b4-193">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="a77b4-194">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="a77b4-194">Example (RMO)</span></span>  
 <span data-ttu-id="a77b4-195">次の例では、マージ アーティクルに変更を加え、アーティクル用のビジネス ロジック ハンドラーを指定しています。</span><span class="sxs-lookup"><span data-stu-id="a77b4-195">This example changes a merge article to specify the business logic handler used by the article.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="a77b4-196">参照</span><span class="sxs-lookup"><span data-stu-id="a77b4-196">See Also</span></span>  
 <span data-ttu-id="a77b4-197">[マージ アーティクルのビジネス ロジック ハンドラーの実装](../implement-a-business-logic-handler-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="a77b4-197">[Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="a77b4-198">[データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="a77b4-198">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="a77b4-199">[パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a77b4-199">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="a77b4-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="a77b4-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="a77b4-201">マージ レプリケーションの競合検出および解決の詳細</span><span class="sxs-lookup"><span data-stu-id="a77b4-201">Advanced Merge Replication Conflict Detection and Resolution</span></span>](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
