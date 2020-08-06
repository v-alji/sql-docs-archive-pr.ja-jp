---
title: アーティクルの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 082f90d33c2b8dedfae34dcada9b3935bed134ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633072"
---
# <a name="delete-an-article"></a><span data-ttu-id="a0c22-102">アーティクルの削除</span><span class="sxs-lookup"><span data-stu-id="a0c22-102">Delete an Article</span></span>
  <span data-ttu-id="a0c22-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)] またはレプリケーション管理オブジェクト (RMO) を使用して、アーティクルを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-103">This topic describes how to delete an article in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or Replication Management Objects (RMO).</span></span> <span data-ttu-id="a0c22-104">アーティクルを削除できる条件と、アーティクルを削除するために新しいスナップショットやサブスクリプションの再初期化が必要かどうかについては、「[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md)」(既存のパブリケーションでのアーティクルの追加と削除) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a0c22-104">For information about the conditions under which articles can be dropped and whether dropping an article requires a new snapshot or the reinitialization of subscriptions, see [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a0c22-105">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a0c22-105">Using Transact-SQL</span></span>  
 <span data-ttu-id="a0c22-106">アーティクルは、レプリケーション ストアド プロシージャを使用してプログラムで削除できます。</span><span class="sxs-lookup"><span data-stu-id="a0c22-106">Articles can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="a0c22-107">使用するストアド プロシージャは、アーティクルが属するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a0c22-107">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a0c22-108">スナップショット パブリケーションまたはトランザクション パブリケーションからアーティクルを削除するには</span><span class="sxs-lookup"><span data-stu-id="a0c22-108">To delete an article from a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a0c22-109">[sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) を実行して、**\@article** で指定されているアーティクルを **\@publication** で指定されているパブリケーションから削除します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-109">Execute [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="a0c22-110">\*\* \@ Force_invalidate_snapshot**に値**1\*\*を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-110">Specify a value of **1** for **\@force_invalidate_snapshot**.</span></span>  
  
2.  <span data-ttu-id="a0c22-111">(省略可) パブリッシュされたオブジェクトをデータベースから完全に削除するには、パブリッシャーのパブリケーション データベースに対して `DROP <objectname>` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-111">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a><span data-ttu-id="a0c22-112">アーティクルをマージ パブリケーションから削除するには</span><span class="sxs-lookup"><span data-stu-id="a0c22-112">To delete an article from a merge publication</span></span>  
  
1.  <span data-ttu-id="a0c22-113">[sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) を実行して、**\@article** で指定されているアーティクルを **\@publication** で指定されているパブリケーションから削除します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-113">Execute [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="a0c22-114">必要に応じて、 \*\* \@ force_invalidate_snapshot**に**1**を指定し、 \*\* \@ force_reinit_subscription**に値**1**を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-114">If necessary, specify a value of **1** for **\@force_invalidate_snapshot** and a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="a0c22-115">(省略可) パブリッシュされたオブジェクトをデータベースから完全に削除するには、パブリッシャーのパブリケーション データベースに対して `DROP <objectname>` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-115">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a0c22-116">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a0c22-116">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="a0c22-117">次の例では、トランザクション パブリケーションからアーティクルを削除します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-117">The following example deletes an article from a transactional publication.</span></span> <span data-ttu-id="a0c22-118">この変更によって既存のスナップショットが無効になるため、 \*\* \@ force_invalidate_snapshot**パラメーターに値**1\*\*が指定されています。</span><span class="sxs-lookup"><span data-stu-id="a0c22-118">Because this change invalidates the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 <span data-ttu-id="a0c22-119">次の例では、マージ パブリケーションから 2 つのアーティクルを削除します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-119">The following example deletes two articles from a merge publication.</span></span> <span data-ttu-id="a0c22-120">これらの変更によって既存のスナップショットが無効になるため、 \*\* \@ force_invalidate_snapshot**パラメーターに値**1\*\*が指定されています。</span><span class="sxs-lookup"><span data-stu-id="a0c22-120">Because these changes invalidate the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="a0c22-121">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="a0c22-121">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="a0c22-122">アーティクルは、レプリケーション管理オブジェクト (RMO) を使用してプログラムから削除できます。</span><span class="sxs-lookup"><span data-stu-id="a0c22-122">You can delete articles programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="a0c22-123">アーティクルを削除する際に使用する RMO のクラスは、アーティクルが属しているパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a0c22-123">The RMO classes you use to delete an article depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a0c22-124">スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを削除するには</span><span class="sxs-lookup"><span data-stu-id="a0c22-124">To delete an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a0c22-125"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-125">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a0c22-126"><xref:Microsoft.SqlServer.Replication.TransArticle> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-126">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="a0c22-127"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-127">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="a0c22-128">手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-128">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="a0c22-129"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティを調べて、アーティクルが存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-129">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="a0c22-130">このプロパティの値が `false` の場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。</span><span class="sxs-lookup"><span data-stu-id="a0c22-130">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="a0c22-131"><xref:Microsoft.SqlServer.Replication.Article.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-131">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="a0c22-132">すべての接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0c22-132">Close all connections.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="a0c22-133">マージ パブリケーションのアーティクルを削除するには</span><span class="sxs-lookup"><span data-stu-id="a0c22-133">To delete an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="a0c22-134"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-134">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a0c22-135"><xref:Microsoft.SqlServer.Replication.MergeArticle> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-135">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="a0c22-136"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-136">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="a0c22-137">手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-137">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="a0c22-138"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティを調べて、アーティクルが存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-138">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="a0c22-139">このプロパティの値が `false` の場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。</span><span class="sxs-lookup"><span data-stu-id="a0c22-139">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="a0c22-140"><xref:Microsoft.SqlServer.Replication.Article.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a0c22-140">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="a0c22-141">すべての接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0c22-141">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c22-142">参照</span><span class="sxs-lookup"><span data-stu-id="a0c22-142">See Also</span></span>  
 <span data-ttu-id="a0c22-143">[既存のパブリケーションでのアーティクルの追加と削除](add-articles-to-and-drop-articles-from-existing-publications.md) </span><span class="sxs-lookup"><span data-stu-id="a0c22-143">[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md) </span></span>  
 [<span data-ttu-id="a0c22-144">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="a0c22-144">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
