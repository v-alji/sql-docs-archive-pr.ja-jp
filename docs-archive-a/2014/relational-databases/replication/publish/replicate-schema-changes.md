---
title: スキーマ変更のレプリケート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bec2f363cd8c4f7dea45935568a88722b19323fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641614"
---
# <a name="replicate-schema-changes"></a><span data-ttu-id="1b213-102">スキーマ変更のレプリケート</span><span class="sxs-lookup"><span data-stu-id="1b213-102">Replicate Schema Changes</span></span>
  <span data-ttu-id="1b213-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマの変更をレプリケートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b213-103">This topic describes how to replicate schema changes in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1b213-104">パブリッシュされたアーティクルに対し、次のようなスキーマ変更を行った場合、変更内容が既定で [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーに反映されます。</span><span class="sxs-lookup"><span data-stu-id="1b213-104">If you make the following schema changes to a published article, they are propagated, by default, to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="1b213-105">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="1b213-105">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="1b213-106">ALTER VIEW</span><span class="sxs-lookup"><span data-stu-id="1b213-106">ALTER VIEW</span></span>  
  
-   <span data-ttu-id="1b213-107">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="1b213-107">ALTER PROCEDURE</span></span>  
  
-   <span data-ttu-id="1b213-108">ALTER FUNCTION</span><span class="sxs-lookup"><span data-stu-id="1b213-108">ALTER FUNCTION</span></span>  
  
-   <span data-ttu-id="1b213-109">ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="1b213-109">ALTER TRIGGER</span></span>  
  
 <span data-ttu-id="1b213-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1b213-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1b213-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1b213-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1b213-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1b213-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="1b213-113">**スキーマの変更をレプリケートするために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="1b213-113">**To replicate schema changes, using:**</span></span>  
  
     [<span data-ttu-id="1b213-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1b213-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1b213-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1b213-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1b213-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="1b213-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1b213-117">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1b213-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1b213-118">ALTER TABLE ...DROP COLUMN ステートメントは、スキーマ変更のレプリケーションを無効にした場合でも、サブスクリプションに削除対象の列が含まれているすべてのサブスクライバーに必ずレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="1b213-118">The ALTER TABLE ... DROP COLUMN statement is always replicated to all Subscribers whose subscription contains the columns being dropped, even if you disable the replication of schema changes.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1b213-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1b213-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1b213-120">パブリケーションに対するスキーマ変更をレプリケートしない場合は、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスでスキーマ変更のレプリケーションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="1b213-120">If you do not want to replicate schema changes for a publication, disable the replication of schema changes in the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="1b213-121">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b213-121">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-disable-replication-of-schema-changes"></a><span data-ttu-id="1b213-122">スキーマ変更のレプリケーションを無効にするには</span><span class="sxs-lookup"><span data-stu-id="1b213-122">To disable replication of schema changes</span></span>  
  
1.  <span data-ttu-id="1b213-123">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、 **[スキーマ変更のレプリケート]** プロパティの値を **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="1b213-123">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, set the value of the **Replicate schema changes** property to **False**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="1b213-124">特定のスキーマ変更だけを反映させるには、スキーマを変更する前にプロパティを **[True]** に設定し、変更後に **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="1b213-124">To propagate only specific schema changes, set the property to **True** before a schema change, and then set it to **False** after the change is made.</span></span> <span data-ttu-id="1b213-125">逆に、ほとんどのスキーマ変更を反映するには、スキーマ変更前にプロパティを **[False]** に設定し、変更後に **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="1b213-125">Conversely, to propagate most schema changes, but not a given change, set the property to **False** before the schema change, and then set it to **True** after the change is made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1b213-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1b213-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="1b213-127">レプリケーションのストアド プロシージャを使用すると、これらのスキーマ変更をレプリケートするかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b213-127">You can use replication stored procedures to specify whether these schema changes are replicated.</span></span> <span data-ttu-id="1b213-128">どのストアド プロシージャを使用するかは、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="1b213-128">The stored procedure that you use depends on the type of publication.</span></span>  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="1b213-129">スキーマ変更をレプリケートしないスナップショット パブリケーションまたはトランザクション パブリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="1b213-129">To create a snapshot or transactional publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="1b213-130">パブリッシャー側のパブリケーションデータベースに対して[sp_addpublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)を実行します。このとき、 \*\* \@ replicate_ddl**には**0\*\*の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b213-130">At the Publisher on the publication database, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="1b213-131">詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1b213-131">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="1b213-132">スキーマ変更をレプリケートしないマージ パブリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="1b213-132">To create a merge publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="1b213-133">パブリッシャー側のパブリケーションデータベースに対して[sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。このとき、 \*\* \@ replicate_ddl**には**0\*\*の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b213-133">At the Publisher on the publication database, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="1b213-134">詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1b213-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="1b213-135">スナップショット パブリケーションまたはトランザクション パブリケーションでスキーマ変更のレプリケートを一時的に無効化するには</span><span class="sxs-lookup"><span data-stu-id="1b213-135">To temporarily disable replicating schema changes for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="1b213-136">スキーマ変更のレプリケーションを含むパブリケーションの場合は、 [sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。このとき、 \*\* \@ プロパティ**には**replicate_ddl**を、値には**0**を指定します** \@ \*\*。</span><span class="sxs-lookup"><span data-stu-id="1b213-136">For a publication with replication of schema changes, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="1b213-137">パブリッシュされたオブジェクトに対し、DDL コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b213-137">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="1b213-138">Optional[Sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行して、スキーマ変更のレプリケートを再度有効にします。 \*\* \@ プロパティ**には**replicate_ddl**を、値には**1**を指定します** \@ \*\*。</span><span class="sxs-lookup"><span data-stu-id="1b213-138">(Optional) Re-enable replicating schema changes by executing [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a><span data-ttu-id="1b213-139">マージ パブリケーションでスキーマ変更のレプリケートを一時的に無効化するには</span><span class="sxs-lookup"><span data-stu-id="1b213-139">To temporarily disable replicating schema changes for a merge publication</span></span>  
  
1.  <span data-ttu-id="1b213-140">スキーマ変更のレプリケーションを含むパブリケーションの場合は、 [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。このとき、 \*\* \@ プロパティ**には**replicate_ddl**を、値には**0**を指定します** \@ \*\*。</span><span class="sxs-lookup"><span data-stu-id="1b213-140">For a publication with replication of schema changes, execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="1b213-141">パブリッシュされたオブジェクトに対し、DDL コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b213-141">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="1b213-142">Optional[Sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行して、スキーマ変更のレプリケートを再度有効にします。 \*\* \@ プロパティ**には**replicate_ddl**を、値には**1**を指定します** \@ \*\*。</span><span class="sxs-lookup"><span data-stu-id="1b213-142">(Optional) Re-enable replicating schema changes by executing [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b213-143">参照</span><span class="sxs-lookup"><span data-stu-id="1b213-143">See Also</span></span>  
 <span data-ttu-id="1b213-144">[パブリケーション データベースでのスキーマの変更](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="1b213-144">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 [<span data-ttu-id="1b213-145">パブリケーション データベースでのスキーマの変更</span><span class="sxs-lookup"><span data-stu-id="1b213-145">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
