---
title: マージ パブリケーションの互換性レベルの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], replication
- backward compatibility [SQL Server], replication
- publications [SQL Server replication], backward compatibility
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04ad80b0c99e7282ff2acfa459a08665efbdee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645513"
---
# <a name="set-the-compatibility-level-for-merge-publications"></a><span data-ttu-id="e7ec2-102">マージ パブリケーションの互換性レベルの設定</span><span class="sxs-lookup"><span data-stu-id="e7ec2-102">Set the Compatibility Level for Merge Publications</span></span>
  <span data-ttu-id="e7ec2-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ パブリケーションの互換性レベルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-103">This topic describes how to set the compatibility level for merge publications in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e7ec2-104">マージ レプリケーションでは、パブリケーションの互換性レベルを使用して、指定されたデータベースのパブリケーションで使用できる機能を決定します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-104">Merge replication uses the publication compatibility level to determine which features can be used by publications in a given database.</span></span>  
  
 <span data-ttu-id="e7ec2-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e7ec2-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e7ec2-106">**マージ パブリケーションのパブリケーション互換性レベルを設定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="e7ec2-106">**To set the compatibility level for merge publications, using:**</span></span>  
  
     [<span data-ttu-id="e7ec2-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7ec2-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e7ec2-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7ec2-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e7ec2-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e7ec2-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e7ec2-110">パブリケーションの新規作成ウィザードの **[サブスクライバーの種類]** ページで互換性レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-110">Set the compatibility level on the **Subscriber Types** page of the New Publication Wizard.</span></span> <span data-ttu-id="e7ec2-111">このウィザードへのアクセスの詳細については、「 [Create a Publication](create-a-publication.md)を使用して、マージ パブリケーションの互換性レベルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-111">For more information on accessing this wizard, see [Create a Publication](create-a-publication.md).</span></span> <span data-ttu-id="e7ec2-112">パブリケーション スナップショットの作成後、互換性レベルを上げることはできますが、下げることはできません。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-112">After a publication snapshot is created, the compatibility level can be increased but cannot be decreased.</span></span> <span data-ttu-id="e7ec2-113">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[全般]** ページで互換性レベルを上げます。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-113">Increase the compatibility level on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="e7ec2-114">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-114">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="e7ec2-115">パブリケーションの互換性レベルを上げた場合、設定した互換性レベルよりも前のバージョンを実行しているサーバーでは、既存のサブスクリプションを同期できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-115">If you increase the publication compatibility level, any existing subscriptions at servers running versions prior to the compatibility level will no longer be able to synchronize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7ec2-116">互換性レベルはパブリケーションの他のプロパティ、および有効になるアーティクルのプロパティと密接に関連しているため、互換性レベルとその他のプロパティをこのダイアログ ボックスで同時に変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-116">Because the compatibility level has implications for other publication properties and for which article properties are valid, do not change the compatibility level and other properties in the same use of the dialog box.</span></span> <span data-ttu-id="e7ec2-117">プロパティの変更後、パブリケーションのスナップショットを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-117">The snapshot for the publication should be regenerated after the property is changed.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level"></a><span data-ttu-id="e7ec2-118">パブリケーションの互換性レベルを設定するには</span><span class="sxs-lookup"><span data-stu-id="e7ec2-118">To set the publication compatibility level</span></span>  
  
-   <span data-ttu-id="e7ec2-119">パブリケーションの新規作成ウィザードの **[サブスクライバーの種類]** ページで、パブリケーションがサポートするサブスクライバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-119">On the **Subscriber Types** page of the New Publication Wizard, select the types of Subscribers that the publication should support.</span></span>  
  
#### <a name="to-increase-the-publication-compatibility-level"></a><span data-ttu-id="e7ec2-120">パブリケーションの互換性レベルを上げるには</span><span class="sxs-lookup"><span data-stu-id="e7ec2-120">To increase the publication compatibility level</span></span>  
  
-   <span data-ttu-id="e7ec2-121">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[全般]** ページで、 **[互換性レベル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-121">On the **General** page of the **Publication Properties - \<Publication>** dialog box, select for **Compatibility level**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e7ec2-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e7ec2-122">Using Transact-SQL</span></span>  
 <span data-ttu-id="e7ec2-123">マージ パブリケーションの互換性レベルは、パブリケーションを作成したときにプログラムで設定するか、または後でプログラムから変更できます。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-123">The compatibility level for a merge publication can either be set programmatically when a publication is created or modified programmatically at a later time.</span></span> <span data-ttu-id="e7ec2-124">レプリケーション ストアド プロシージャを使用して、このパブリケーション プロパティを設定または変更できます。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-124">You can use replication stored procedures to set or change this publication property.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level-for-a-merge-publication"></a><span data-ttu-id="e7ec2-125">マージ パブリケーションのパブリケーション互換性レベルを設定するには</span><span class="sxs-lookup"><span data-stu-id="e7ec2-125">To set the publication compatibility level for a merge publication</span></span>  
  
1.  <span data-ttu-id="e7ec2-126">パブリッシャーで[sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。このとき、の値を指定して、 **@publication_compatibility_level** パブリケーションを以前のバージョンのと互換性があるようにし [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-126">At the Publisher, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value for **@publication_compatibility_level** to make the publication compatible with older versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e7ec2-127">詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-127">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="e7ec2-128">マージ パブリケーションのパブリケーション互換性レベルを変更するには</span><span class="sxs-lookup"><span data-stu-id="e7ec2-128">To change the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="e7ec2-129">[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行 sp_changemergepublication、に**publication_compatibility_level**を、 **@property** に適切なパブリケーション互換性レベルを指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-129">Execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **publication_compatibility_level** for **@property** and the appropriate publication compatibility level for **@value**.</span></span>  
  
#### <a name="to-determine-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="e7ec2-130">マージ パブリケーションのパブリケーション互換性レベルを確認するには</span><span class="sxs-lookup"><span data-stu-id="e7ec2-130">To determine the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="e7ec2-131">目的のパブリケーションを指定して、[sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-131">Execute [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the desired publication.</span></span>  
  
2.  <span data-ttu-id="e7ec2-132">結果セットの **backward_comp_level** 列で、パブリケーションの互換性レベルを調べます。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-132">Locate the publication compatibility level in the **backward_comp_level** column in the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="e7ec2-133">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7ec2-133">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="e7ec2-134">次の例では、マージ パブリケーションを作成して、パブリケーションの互換性レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-134">This example creates a merge publication and sets the publication compatibility level.</span></span>  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 <span data-ttu-id="e7ec2-135">次の例では、マージ パブリケーションのパブリケーション互換性レベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-135">This example changes the publication compatibility level for the merge publication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7ec2-136">パブリケーションで特定の互換性レベルを必要とする機能を使用していると、パブリケーションの互換性レベルの変更が許可されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-136">Changing the publication compatibility level might not be allowed if the publication uses any features that require a particular compatibility level.</span></span> <span data-ttu-id="e7ec2-137">詳しくは、「[レプリケーションの旧バージョンとの互換性](../replication-backward-compatibility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-137">For more information, see [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 <span data-ttu-id="e7ec2-138">次の例では、マージ パブリケーションの現在のパブリケーション互換性レベルが返されます。</span><span class="sxs-lookup"><span data-stu-id="e7ec2-138">This example returns the current publication compatibility level for the merge publication.</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7ec2-139">参照</span><span class="sxs-lookup"><span data-stu-id="e7ec2-139">See Also</span></span>  
 [<span data-ttu-id="e7ec2-140">パブリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="e7ec2-140">Create a Publication</span></span>](create-a-publication.md)  
  
  
