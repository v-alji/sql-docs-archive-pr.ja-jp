---
title: データベース スキーマの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3ac0c00768db6501c7d786c35758c1a9d75a5a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714069"
---
# <a name="create-a-database-schema"></a><span data-ttu-id="4127f-102">データベース スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="4127f-102">Create a Database Schema</span></span>
  <span data-ttu-id="4127f-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4127f-103">This topic describes how to create a schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4127f-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4127f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4127f-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4127f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4127f-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4127f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4127f-107">Security</span><span class="sxs-lookup"><span data-stu-id="4127f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4127f-108">**スキーマを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="4127f-108">**To create a schema, using:**</span></span>  
  
     [<span data-ttu-id="4127f-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4127f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4127f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4127f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4127f-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="4127f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4127f-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4127f-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4127f-113">新しいスキーマは、データベース ユーザー、データベース ロール、またはアプリケーション ロールのいずれかのデータベース レベルのプリンシパルが所有します。</span><span class="sxs-lookup"><span data-stu-id="4127f-113">The new schema is owned by one of the following database-level principals: database user, database role, or application role.</span></span> <span data-ttu-id="4127f-114">スキーマ内に作成されるオブジェクトはスキーマの所有者が所有し、 **sys.objects** 内の **principal_id**は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="4127f-114">Objects created within a schema are owned by the owner of the schema, and have a NULL **principal_id** in **sys.objects**.</span></span> <span data-ttu-id="4127f-115">スキーマが含まれるオブジェクトの所有権は、データベース レベルのプリンシパルに譲渡できますが、スキーマ内のオブジェクトに対する CONTROL 権限は常にスキーマ所有者が保持します。</span><span class="sxs-lookup"><span data-stu-id="4127f-115">Ownership of schema-contained objects can be transferred to any database-level principal, but the schema owner always retains CONTROL permission on objects within the schema.</span></span>  
  
-   <span data-ttu-id="4127f-116">データベース オブジェクトを作成する場合に、有効なドメイン プリンシパル (ユーザーまたはグループ) をオブジェクト所有者として指定すると、ドメイン プリンシパルがスキーマとしてデータベースに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4127f-116">When creating a database object, if you specify a valid domain principal (user or group) as the object owner, the domain principal will be added to the database as a schema.</span></span> <span data-ttu-id="4127f-117">新しいスキーマは、そのドメイン プリンシパルが所有します。</span><span class="sxs-lookup"><span data-stu-id="4127f-117">The new schema will be owned by that domain principal.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4127f-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4127f-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4127f-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="4127f-119">Permissions</span></span>  
  
-   <span data-ttu-id="4127f-120">データベースに対する CREATE SCHEMA 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4127f-120">Requires CREATE SCHEMA permission on the database.</span></span>  
  
-   <span data-ttu-id="4127f-121">別のユーザーを、作成されるスキーマの所有者として指定する場合、呼び出し元は、そのユーザーに対する IMPERSONATE 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4127f-121">To specify another user as the owner of the schema being created, the caller must have IMPERSONATE permission on that user.</span></span> <span data-ttu-id="4127f-122">データベース ロールを所有者として指定する場合、呼び出し元は、データベース ロールのメンバーシップまたはデータベース ロールに対する ALTER 権限のいずれかを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4127f-122">If a database role is specified as the owner, the caller must have one of the following: membership in the role or ALTER permission on the role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4127f-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4127f-123">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-schema"></a><span data-ttu-id="4127f-124">スキーマを作成するには</span><span class="sxs-lookup"><span data-stu-id="4127f-124">To create a schema</span></span>  
  
1.  <span data-ttu-id="4127f-125">オブジェクト エクスプローラーで、 **[データベース]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4127f-125">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="4127f-126">新しいデータベース スキーマを作成するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="4127f-126">Expand the database in which to create the new database schema.</span></span>  
  
3.  <span data-ttu-id="4127f-127">**[セキュリティ]** フォルダーを右クリックし、 **[新規作成]** をポイントして、 **[スキーマ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4127f-127">Right-click the **Security** folder, point to **New**, and select **Schema**.</span></span>  
  
4.  <span data-ttu-id="4127f-128">**[スキーマ - 新規作成]** ダイアログ ボックスの **[全般]** ページで、 **[スキーマ名]** ボックスに新しいスキーマの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4127f-128">In the **Schema - New** dialog box, on the **General** page, enter a name for the new schema in the **Schema name** box.</span></span>  
  
5.  <span data-ttu-id="4127f-129">**[スキーマの所有者]** ボックスに、スキーマを所有するデータベース ユーザーまたはロールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4127f-129">In the **Schema owner** box, enter the name of a database user or role to own the schema.</span></span> <span data-ttu-id="4127f-130">または、 **[検索]** をクリックして **[ロールとユーザーの検索]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="4127f-130">Alternately, click **Search** to open the **Search Roles and Users** dialog box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="4127f-131">追加オプション</span><span class="sxs-lookup"><span data-stu-id="4127f-131">Additional Options</span></span>  
 <span data-ttu-id="4127f-132">**[スキーマ - 新規作成]** ダイアログ ボックスには次の 2 つのページもあり、それぞれにオプションが用意されています: **[権限]** 、 **[拡張プロパティ]** 。</span><span class="sxs-lookup"><span data-stu-id="4127f-132">The **Schema- New** dialog box also offers options on two additional pages: **Permissions** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="4127f-133">**[権限]** ページには、すべてのセキュリティ保護可能なリソースと、ログインに付与できる、セキュリティ保護可能なリソースに対する権限が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="4127f-133">The **Permissions** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="4127f-134">**[拡張プロパティ]** ページでは、カスタム プロパティをデータベース ユーザーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="4127f-134">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4127f-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4127f-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schema"></a><span data-ttu-id="4127f-136">スキーマを作成するには</span><span class="sxs-lookup"><span data-stu-id="4127f-136">To create a schema</span></span>  
  
1.  <span data-ttu-id="4127f-137">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="4127f-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4127f-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4127f-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4127f-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4127f-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 <span data-ttu-id="4127f-140">詳細については、「[CREATE SCHEMA &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4127f-140">For more information, see [CREATE SCHEMA &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql).</span></span>  
  
  
