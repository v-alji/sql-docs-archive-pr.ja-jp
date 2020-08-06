---
title: アーティクルの定義 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d7ff1f5f516d438ed07a203223acf32970a7961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645520"
---
# <a name="define-an-article"></a><span data-ttu-id="fe6b5-102">アーティクルの定義</span><span class="sxs-lookup"><span data-stu-id="fe6b5-102">Define an Article</span></span>
  <span data-ttu-id="fe6b5-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、アーティクルを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-103">This topic describes how to define an article in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="fe6b5-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="fe6b5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fe6b5-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="fe6b5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fe6b5-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fe6b5-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fe6b5-107">Security</span><span class="sxs-lookup"><span data-stu-id="fe6b5-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fe6b5-108">**アーティクルを定義するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="fe6b5-108">**To define an article, using:**</span></span>  
  
     [<span data-ttu-id="fe6b5-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fe6b5-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fe6b5-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fe6b5-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="fe6b5-111">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="fe6b5-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fe6b5-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="fe6b5-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fe6b5-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fe6b5-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fe6b5-114">アーティクルの名前には % , \* , [ , ] , | , : , " , ? を使用できません。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-114">Article names cannot include any of the following characters: % , \* , [ , ] , | , : , " , ?</span></span> <span data-ttu-id="fe6b5-115">, ' , \ , / , \< , >.</span><span class="sxs-lookup"><span data-stu-id="fe6b5-115">, ' , \ , / , \< , >.</span></span> <span data-ttu-id="fe6b5-116">データベース内のオブジェクトにこれらの文字が使用されているときに、そのオブジェクトをレプリケートする場合、そのオブジェクト名とは異なる名前をアーティクルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-116">If objects in the database include any of these characters and you want to replicate them, you must specify an article name that is different from the object name.</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fe6b5-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fe6b5-117">Security</span></span>  
 <span data-ttu-id="fe6b5-118">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-118">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="fe6b5-119">資格情報を保存する必要がある場合は、 [Windows .NET&#xA0;Framework に用意されている](https://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../../includes/msconame-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-119">If you must store credentials, use the [cryptographic services](https://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fe6b5-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="fe6b5-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="fe6b5-121">パブリケーションの新規作成ウィザードにより、パブリケーションを作成し、アーティクルを定義します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-121">Create publications and define articles with the New Publication Wizard.</span></span> <span data-ttu-id="fe6b5-122">パブリケーションを作成したら、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスでパブリケーションのプロパティを表示および変更します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-122">After a publication is created, view and modify publication properties in the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="fe6b5-123">Oracle データベースからパブリケーションを作成する方法については、「[Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md)」(Oracle データベースからパブリケーションを作成する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-123">For information about creating a publication from an Oracle database, see [Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md).</span></span>  
  
#### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="fe6b5-124">パブリケーションを作成し、アーティクルを定義するには</span><span class="sxs-lookup"><span data-stu-id="fe6b5-124">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="fe6b5-125">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-125">Connect to the Publisher in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="fe6b5-126">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-126">Expand the **Replication** folder, and then right-click the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="fe6b5-127">**[新しいパブリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-127">Click **New Publication**.</span></span>  
  
4.  <span data-ttu-id="fe6b5-128">パブリケーションの新規作成ウィザードのページに従い、以下の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-128">Follow the pages in the New Publication Wizard to:</span></span>  
  
    -   <span data-ttu-id="fe6b5-129">サーバーでディストリビューションが構成されていない場合は、ディストリビューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-129">Specify a Distributor if distribution has not been configured on the server.</span></span> <span data-ttu-id="fe6b5-130">ディストリビューションの構成の詳細については、「[Configure Publishing and Distribution](../configure-publishing-and-distribution.md)」(パブリッシュとディストリビューションの構成) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-130">For more information about configuring distribution, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
         <span data-ttu-id="fe6b5-131">**[ディストリビューター]** ページで、パブリッシャー サーバーが独自のディストリビューター (ローカル ディストリビューター) として機能するように指定した場合、このサーバーはディストリビューターとして構成されていないため、パブリケーションの新規作成ウィザードでサーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-131">If you specify on the **Distributor** page that the Publisher server will act as its own Distributor (a local Distributor), and the server is not configured as a Distributor, the New Publication Wizard will configure the server.</span></span> <span data-ttu-id="fe6b5-132">**[スナップショット フォルダー]** ページで、ディストリビューターの既定のスナップショット フォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-132">You will specify a default snapshot folder for the Distributor on the **Snapshot Folder** page.</span></span> <span data-ttu-id="fe6b5-133">スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-133">The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it.</span></span> <span data-ttu-id="fe6b5-134">フォルダーの適切なセキュリティ保護の詳細については、「[Secure the Snapshot Folder](../security/secure-the-snapshot-folder.md)」(スナップショット フォルダーのセキュリティ保護) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-134">For more information about securing the folder appropriately, see [Secure the Snapshot Folder](../security/secure-the-snapshot-folder.md).</span></span>  
  
         <span data-ttu-id="fe6b5-135">別のサーバーがディストリビューターとして機能するように指定する場合は、パブリッシャーからディストリビューターへの接続のため、 **[管理パスワード]** ページでパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-135">If you specify that another server should act as the Distributor, you must enter a password on the **Administrative Password** page for connections made from the Publisher to the Distributor.</span></span> <span data-ttu-id="fe6b5-136">このパスワードは、リモート ディストリビューターでパブリッシャーを有効にしたときに指定したパスワードと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-136">This password must match the password specified when the Publisher was enabled at the remote Distributor.</span></span>  
  
         <span data-ttu-id="fe6b5-137">詳しくは、「 [Configure Distribution](../configure-distribution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-137">For more information, see [Configure Distribution](../configure-distribution.md).</span></span>  
  
    -   <span data-ttu-id="fe6b5-138">パブリケーション データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-138">Choose a publication database.</span></span>  
  
    -   <span data-ttu-id="fe6b5-139">パブリケーションの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-139">Select a publication type.</span></span> <span data-ttu-id="fe6b5-140">詳細については、「[Types of Replication](../types-of-replication.md)」(レプリケーションの種類) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-140">For more information, see [Types of Replication](../types-of-replication.md).</span></span>  
  
    -   <span data-ttu-id="fe6b5-141">パブリッシュするデータおよびデータベース オブジェクトを指定します。必要に応じて、テーブル アーティクルから列をフィルター選択し、アーティクルのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-141">Specify data and database objects to publish; optionally filter columns from table articles, and set article properties.</span></span>  
  
    -   <span data-ttu-id="fe6b5-142">必要に応じて、テーブル アーティクルから行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-142">Optionally filter rows from table articles.</span></span> <span data-ttu-id="fe6b5-143">詳細については、「[パブリッシュされたデータのフィルター選択](filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-143">For more information, see [Filter Published Data](filter-published-data.md).</span></span>  
  
    -   <span data-ttu-id="fe6b5-144">スナップショット エージェントのスケジュールを設定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-144">Set the Snapshot Agent schedule.</span></span>  
  
    -   <span data-ttu-id="fe6b5-145">以下のレプリケーション エージェントの実行および接続に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-145">Specify the credentials under which the following replication agents run and make connections:</span></span>  
  
         <span data-ttu-id="fe6b5-146">\-すべてのパブリケーション用のスナップショット エージェント。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-146">\- Snapshot Agent for all publications.</span></span>  
  
         <span data-ttu-id="fe6b5-147">\-すべてのトランザクション パブリケーション用のログ リーダー エージェント。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-147">\- Log Reader Agent for all transactional publications.</span></span>  
  
         <span data-ttu-id="fe6b5-148">\-更新サブスクリプションを許可するトランザクション パブリケーションのキュー リーダー エージェント。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-148">\- Queue Reader Agent for transactional publications that allow updating subscriptions.</span></span>  
  
         <span data-ttu-id="fe6b5-149">詳細については、「 [Replication Agent Security Model](../security/replication-agent-security-model.md) 」および「 [Replication Security Best Practices](../security/replication-security-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-149">For more information, see [Replication Agent Security Model](../security/replication-agent-security-model.md) and [Replication Security Best Practices](../security/replication-security-best-practices.md).</span></span>  
  
    -   <span data-ttu-id="fe6b5-150">必要に応じて、パブリケーションのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-150">Optionally script the publication.</span></span> <span data-ttu-id="fe6b5-151">詳細については、「[レプリケーションのスクリプト作成](../scripting-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-151">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
    -   <span data-ttu-id="fe6b5-152">パブリケーションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-152">Specify a name for the publication.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fe6b5-153">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="fe6b5-153">Using Transact-SQL</span></span>  
 <span data-ttu-id="fe6b5-154">パブリケーションが作成された後、プログラムでレプリケーション ストアド プロシージャを使用してアーティクルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-154">After a publication has been created, articles can be created programmatically using replication stored procedures.</span></span> <span data-ttu-id="fe6b5-155">アーティクルの作成に使用するストアド プロシージャは、定義するアーティクルのパブリケーションの種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-155">The stored procedures used to create an article will depend on the type of publication for which the article is being defined.</span></span> <span data-ttu-id="fe6b5-156">詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-156">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="fe6b5-157">スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを定義するには</span><span class="sxs-lookup"><span data-stu-id="fe6b5-157">To define an article for a Snapshot or Transactional Publication</span></span>  
  
1.  <span data-ttu-id="fe6b5-158">パブリッシャー側のパブリケーション データベースに対して、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-158">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="fe6b5-159">\*\* \@ パブリケーション**のアーティクルが属しているパブリケーションの名前、**アーティクルのアーティクル名、 \@ \*\* \*\* \@ source_object\*\*にパブリッシュされるデータベースオブジェクト、およびその他のオプションパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-159">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and any other optional parameters.</span></span> <span data-ttu-id="fe6b5-160">**Dbo**以外の場合は、 \*\* \@ source_owner\*\*を使用して、オブジェクトのスキーマ所有権を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-160">Use **\@source_owner** to specify the schema ownership of the object, if not **dbo**.</span></span> <span data-ttu-id="fe6b5-161">アーティクルがログベースのテーブルアーティクルでない場合は、 \*\* \@ 種類\*\*にアーティクルの種類を指定します。詳細については、「[レプリケーション Transact-sql プログラミング&#41;&#40;アーティクルの種類を指定](specify-article-types-replication-transact-sql-programming.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-161">If the article is not a log-based table article, specify the article type for **\@type**; for more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md).</span></span>  
  
2.  <span data-ttu-id="fe6b5-162">テーブル内の行を行方向にフィルター選択する場合、またはアーティクルを表示する場合は、 [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) を使用してフィルター句を定義します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-162">To horizontally filter rows in a table or view an article, use [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) to define the filter clause.</span></span> <span data-ttu-id="fe6b5-163">詳しくは、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-163">For more information, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
3.  <span data-ttu-id="fe6b5-164">テーブル内の列を列方向にフィルター選択する場合、またはアーティクルを表示する場合は、 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-164">To vertically filter columns in a table or view an article, use [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql).</span></span> <span data-ttu-id="fe6b5-165">詳しくは、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-165">For more information, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
4.  <span data-ttu-id="fe6b5-166">アーティクルをフィルター選択する場合、 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-166">Execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) if the article is filtered.</span></span>  
  
5.  <span data-ttu-id="fe6b5-167">パブリケーションに既存のサブスクリプションがあり、 [immediate_sync](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) 列の **sp_helppublication** が **0** を返す場合、 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) を呼び出して既存の各サブスクリプションにアーティクルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-167">If the publication has existing subscriptions and [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) returns a value of **0** in the **immediate_sync** column, you must call [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) to add the article to each existing subscription.</span></span>  
  
6.  <span data-ttu-id="fe6b5-168">パブリケーションに既存のプル サブスクリプションがある場合、パブリッシャーで [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) を実行し、既存のプル サブスクリプションに対して新しいアーティクルのみを含む新しいスナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-168">If the publication has existing pull subscriptions, execute [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) at the Publisher to create a new snapshot for existing pull subscriptions that contains just the new article.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe6b5-169">スナップショットを使用して初期化しないサブスクリプションの場合、この処理は [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) によって実行されるため、 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-169">For subscriptions that are not initialized using a snapshot, you do not need to execute [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) as this procedure is executed by [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span>  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a><span data-ttu-id="fe6b5-170">マージ パブリケーションのアーティクルを定義するには</span><span class="sxs-lookup"><span data-stu-id="fe6b5-170">To define an article for a Merge Publication</span></span>  
  
1.  <span data-ttu-id="fe6b5-171">パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="fe6b5-172">\*\* \@ パブリケーションの**名前、 \*\* \@ アーティクル**の名前、およびパブリッシュするオブジェクトを指定して、 \*\* \@ source_object\*\*します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-172">Specify the name of the publication for **\@publication**, a name for the article name for **\@article**, and the object being published for **\@source_object**.</span></span> <span data-ttu-id="fe6b5-173">テーブル行を行方向にフィルター選択するには、 \*\* \@ subset_filterclause\*\*の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-173">To horizontally filter table rows, specify a value for **\@subset_filterclause**.</span></span> <span data-ttu-id="fe6b5-174">詳細については、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) 」および「 [静的行フィルターの定義および変更](define-and-modify-a-static-row-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-174">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) and [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span> <span data-ttu-id="fe6b5-175">アーティクルがテーブルアーティクルでない場合は、[ \*\* \@ 種類\*\*] にアーティクルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-175">If the article is not a table article, specify the article type for **\@type**.</span></span> <span data-ttu-id="fe6b5-176">詳細については、「[Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md)」(アーティクルの種類の指定 (レプリケーション Transact-SQL プログラミング)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-176">For more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md).</span></span>  
  
2.  <span data-ttu-id="fe6b5-177">(省略可) パブリッシャー側のパブリケーション データベースに対して [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) を実行し、2 つのアーティクル間に結合フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-177">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="fe6b5-178">詳しくは、「 [マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-178">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
3.  <span data-ttu-id="fe6b5-179">(省略可) パブリッシャー側のパブリケーション データベースに対して [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) を実行し、テーブル列をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-179">(Optional) At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) to filter table columns.</span></span> <span data-ttu-id="fe6b5-180">詳しくは、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-180">For more information, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="fe6b5-181">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fe6b5-181">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="fe6b5-182">この例では、 `Product` テーブルに基づいてトランザクション パブリケーションにアーティクルを定義します。アーティクルは行方向および列方向にフィルター選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-182">This example defines an article based on the `Product` table for a transactional publication, where the article is filtered both horizontally and vertically.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="fe6b5-183">この例では、マージ パブリケーションのアーティクルを定義します。 `SalesOrderHeader` アーティクルは **SalesPersonID**に基づいて静的にフィルター選択され、 `SalesOrderDetail` アーティクルは `SalesOrderHeader`に基づいて結合フィルターが適用されます。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-183">This example defines articles for a merge publication, where the `SalesOrderHeader` article is statically filtered based on **SalesPersonID**, and the `SalesOrderDetail` article is join filtered based on `SalesOrderHeader`.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="fe6b5-184">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="fe6b5-184">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="fe6b5-185">レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってアーティクルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-185">You can define articles programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="fe6b5-186">アーティクルの定義に使用する RMO クラスは、アーティクルを定義するパブリケーションの種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-186">The RMO classes that you use to define an article depend on the type of publication for which the article is defined.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="fe6b5-187">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="fe6b5-187">Examples (RMO)</span></span>  
 <span data-ttu-id="fe6b5-188">次の例では、行フィルターと列フィルターを含むアーティクルをトランザクション パブリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-188">The following example adds an article with row and column filters to a transactional publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 <span data-ttu-id="fe6b5-189">次の例では、マージ パブリケーションに 3 つのアーティクルを追加します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-189">The following example adds three articles to a merge publication.</span></span> <span data-ttu-id="fe6b5-190">このアーティクルには列フィルターがあり、2 つの結合フィルターを使用してパラメーター化された行フィルターを他のアーティクルに反映します。</span><span class="sxs-lookup"><span data-stu-id="fe6b5-190">The articles have column filters, and two join filters are used to propagate a parameterized row filter to the other articles.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a><span data-ttu-id="fe6b5-191">参照</span><span class="sxs-lookup"><span data-stu-id="fe6b5-191">See Also</span></span>  
 <span data-ttu-id="fe6b5-192">[Create a Publication](create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="fe6b5-192">[Create a Publication](create-a-publication.md) </span></span>  
 <span data-ttu-id="fe6b5-193">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="fe6b5-193">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="fe6b5-194">[既存のパブリケーションでのアーティクルの追加と削除](add-articles-to-and-drop-articles-from-existing-publications.md) </span><span class="sxs-lookup"><span data-stu-id="fe6b5-194">[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md) </span></span>  
 <span data-ttu-id="fe6b5-195">[パブリッシュされたデータのフィルター処理](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe6b5-195">[Filter Published Data](filter-published-data.md) </span></span>  
 <span data-ttu-id="fe6b5-196">[データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="fe6b5-196">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="fe6b5-197">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="fe6b5-197">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
