---
title: サーバー監査とデータベース監査の仕様を作成する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlaudit.dbaudit.general.f1
helpviewer_keywords:
- audits [SQL Server], creating database specification
- database audit [SQL Server]
ms.assetid: 26ee85de-6e97-4318-b526-900924d96e62
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0cad01eae45d534f0f74911ce8f57827858cc920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716198"
---
# <a name="create-a-server-audit-and-database-audit-specification"></a><span data-ttu-id="58c09-102">サーバー監査の仕様およびデータベース監査の仕様を作成する方法</span><span class="sxs-lookup"><span data-stu-id="58c09-102">Create a Server Audit and Database Audit Specification</span></span>
  <span data-ttu-id="58c09-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]でサーバー監査とデータベース監査の仕様を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="58c09-103">This topic describes how to create a server audit and database audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="58c09-104">*のインスタンスや* データベースの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 監査 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、システムで発生するイベントの追跡およびログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="58c09-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="58c09-105">*SQL Server Audit* オブジェクトは、監視するサーバー レベルまたはデータベース レベルのアクションおよびアクションのグループの 1 つのインスタンスを収集します。</span><span class="sxs-lookup"><span data-stu-id="58c09-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="58c09-106">監査は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス レベルで行われます。</span><span class="sxs-lookup"><span data-stu-id="58c09-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="58c09-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスごとに複数の監査を使用できます。</span><span class="sxs-lookup"><span data-stu-id="58c09-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="58c09-108">" *データベース レベルの監査の仕様* " オブジェクトも、監査に属しています。</span><span class="sxs-lookup"><span data-stu-id="58c09-108">The *Database-Level Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="58c09-109">各監査では、SQL Server データベースごとに 1 つのデータベース監査の仕様を作成できます。</span><span class="sxs-lookup"><span data-stu-id="58c09-109">You can create one database audit specification per SQL Server database per audit.</span></span> <span data-ttu-id="58c09-110">詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](sql-server-audit-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58c09-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="58c09-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="58c09-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="58c09-112">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="58c09-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="58c09-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="58c09-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="58c09-114">Security</span><span class="sxs-lookup"><span data-stu-id="58c09-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="58c09-115">**サーバー監査とデータベース監査の仕様を作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="58c09-115">**To create a server audit and database audit specification, using:**</span></span>  
  
     [<span data-ttu-id="58c09-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58c09-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="58c09-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58c09-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="58c09-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="58c09-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="58c09-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="58c09-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="58c09-120">データベース監査仕様は、セキュリティ保護できないオブジェクトであり、特定のデータベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="58c09-120">Database audit specifications are non-securable objects that reside in a given database.</span></span> <span data-ttu-id="58c09-121">作成されたデータベース監査仕様は無効な状態です。</span><span class="sxs-lookup"><span data-stu-id="58c09-121">When a database audit specification is created, it is in a disabled state.</span></span>  
  
 <span data-ttu-id="58c09-122">ユーザー データベースでデータベース監査の仕様を作成または変更するときは、システム ビューなど、サーバー スコープ オブジェクトの監査アクションは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="58c09-122">When you are creating or modifying a database audit specification in a user database, do not include audit actions on server-scope objects, such as the system views.</span></span> <span data-ttu-id="58c09-123">サーバー スコープ オブジェクトが含まれている場合、監査が作成されます。</span><span class="sxs-lookup"><span data-stu-id="58c09-123">If server-scoped objects are included, the audit will be created.</span></span> <span data-ttu-id="58c09-124">ただし、サーバー スコープ オブジェクトは対象にならず、エラーは返されません。</span><span class="sxs-lookup"><span data-stu-id="58c09-124">However, the server-scoped objects will not be included, and no error will be returned.</span></span> <span data-ttu-id="58c09-125">サーバー スコープ オブジェクトを監査するには、master データベースのデータベース監査の仕様を使用してください。</span><span class="sxs-lookup"><span data-stu-id="58c09-125">To audit server-scope objects, use a database audit specification in the master database.</span></span>  
  
 <span data-ttu-id="58c09-126">`tempdb` システム データベースを除き、データベース監査の仕様は、その仕様が作成されるデータベースに存在します。</span><span class="sxs-lookup"><span data-stu-id="58c09-126">Database audit specifications reside in the database where they are created, with the exception of the `tempdb` system database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="58c09-127">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="58c09-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="58c09-128">Permissions</span><span class="sxs-lookup"><span data-stu-id="58c09-128">Permissions</span></span>  
  
-   <span data-ttu-id="58c09-129">ALTER ANY DATABASE AUDIT 権限を持つユーザーは、データベース監査仕様を作成し、任意の監査にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="58c09-129">Users with the ALTER ANY DATABASE AUDIT permission can create database audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="58c09-130">データベース監査仕様の作成後は、CONTROL SERVER 権限または ALTER ANY DATABASE AUDIT 権限を持つプリンシパル、または sysadmin アカウントがその仕様を表示できます。</span><span class="sxs-lookup"><span data-stu-id="58c09-130">After a database audit specification is created, it can be viewed by principals with the CONTROL SERVER,  ALTER ANY DATABASE AUDIT permissions, or the sysadmin account.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="58c09-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="58c09-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="58c09-132">サーバー監査を作成するには</span><span class="sxs-lookup"><span data-stu-id="58c09-132">To create a server audit</span></span>  
  
1.  <span data-ttu-id="58c09-133">オブジェクト エクスプローラーで、 **[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="58c09-133">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="58c09-134">[**監査**] フォルダーを右クリックし、[**新しい監査**] を選択します。詳細については、「[サーバー監査およびサーバー監査の仕様を作成する](create-a-server-audit-and-server-audit-specification.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58c09-134">Right-click the **Audits** folder and select **New Audit...**. For more information, see [Create a Server Audit and Server Audit Specification](create-a-server-audit-and-server-audit-specification.md).</span></span>  
  
3.  <span data-ttu-id="58c09-135">オプションの選択が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58c09-135">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="58c09-136">データベース レベルの監査仕様を作成するには</span><span class="sxs-lookup"><span data-stu-id="58c09-136">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="58c09-137">オブジェクト エクスプローラーで、監査仕様を作成するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="58c09-137">In Object Explorer, expand the database where you want to create an audit specification.</span></span>  
  
2.  <span data-ttu-id="58c09-138">**[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="58c09-138">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="58c09-139">[**データベース監査の仕様**] フォルダーを右クリックし、[**新しいデータベース監査の仕様**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="58c09-139">Right-click the **Database Audit Specifications** folder and select **New Database Audit Specification...**.</span></span>  
  
     <span data-ttu-id="58c09-140">**[データベース監査の仕様の作成]** ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="58c09-140">The following options are available on the **Create Database Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="58c09-141">**名前**</span><span class="sxs-lookup"><span data-stu-id="58c09-141">**Name**</span></span>  
     <span data-ttu-id="58c09-142">データベース監査の仕様の名前。</span><span class="sxs-lookup"><span data-stu-id="58c09-142">The name of the database audit specification.</span></span> <span data-ttu-id="58c09-143">この名前は、新しいサーバー監査の仕様を作成すると自動的に生成されますが、編集可能です。</span><span class="sxs-lookup"><span data-stu-id="58c09-143">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="58c09-144">**監査**</span><span class="sxs-lookup"><span data-stu-id="58c09-144">**Audit**</span></span>  
     <span data-ttu-id="58c09-145">既存のデータベース監査の名前。</span><span class="sxs-lookup"><span data-stu-id="58c09-145">The name of an existing database audit.</span></span> <span data-ttu-id="58c09-146">監査の名前を入力するか、一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="58c09-146">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="58c09-147">**[監査アクションの種類]**</span><span class="sxs-lookup"><span data-stu-id="58c09-147">**Audit Action Type**</span></span>  
     <span data-ttu-id="58c09-148">キャプチャするデータベース レベルの監査アクション グループと監査アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="58c09-148">Specifies the database-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="58c09-149">データベース レベルの監査アクション グループと監査アクションの一覧、およびそれらに含まれるイベントの説明については、「 [SQL Server 監査のアクション グループとアクション](sql-server-audit-action-groups-and-actions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="58c09-149">For the list of database-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="58c09-150">**[オブジェクト スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="58c09-150">**Object Schema**</span></span>  
     <span data-ttu-id="58c09-151">指定した **[オブジェクト名]** のスキーマを表示します。</span><span class="sxs-lookup"><span data-stu-id="58c09-151">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="58c09-152">**[オブジェクト名]**</span><span class="sxs-lookup"><span data-stu-id="58c09-152">**Object Name**</span></span>  
     <span data-ttu-id="58c09-153">監査するオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="58c09-153">The name of the object to audit.</span></span> <span data-ttu-id="58c09-154">これは監査アクションにのみ使用できます。監査グループには適用されません。</span><span class="sxs-lookup"><span data-stu-id="58c09-154">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="58c09-155">**省略記号 (...)**</span><span class="sxs-lookup"><span data-stu-id="58c09-155">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="58c09-156">指定した **[監査アクションの種類]** に基づいて、使用可能なオブジェクトを参照して選択するための **[オブジェクトの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="58c09-156">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="58c09-157">**[プリンシパル名]**</span><span class="sxs-lookup"><span data-stu-id="58c09-157">**Principal Name**</span></span>  
     <span data-ttu-id="58c09-158">監査対象のオブジェクトで監査をフィルター選択するためのアカウント。</span><span class="sxs-lookup"><span data-stu-id="58c09-158">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="58c09-159">**省略記号 (...)**</span><span class="sxs-lookup"><span data-stu-id="58c09-159">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="58c09-160">指定した **[オブジェクト名]** に基づいて、使用可能なオブジェクトを参照して選択するための **[オブジェクトの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="58c09-160">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
4.  <span data-ttu-id="58c09-161">オプションの選択が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58c09-161">When you are finished selecting option, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="58c09-162">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="58c09-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="58c09-163">サーバー監査を作成するには</span><span class="sxs-lookup"><span data-stu-id="58c09-163">To create a server audit</span></span>  
  
1.  <span data-ttu-id="58c09-164">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="58c09-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="58c09-165">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58c09-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="58c09-166">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58c09-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE master ;  
    GO  
    -- Create the server audit.   
    CREATE SERVER AUDIT Payrole_Security_Audit  
        TO FILE ( FILEPATH =   
    'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA' ) ;   
    GO  
    -- Enable the server audit.   
    ALTER SERVER AUDIT Payrole_Security_Audit   
    WITH (STATE = ON) ;  
    ```  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="58c09-167">データベース レベルの監査仕様を作成するには</span><span class="sxs-lookup"><span data-stu-id="58c09-167">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="58c09-168">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="58c09-168">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="58c09-169">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58c09-169">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="58c09-170">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58c09-170">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="58c09-171">この例では、 `Audit_Pay_Tables` テーブルに対する `dbo` ユーザーによる SELECT ステートメントと INSERT ステートメントを、定義済みのサーバー監査に基づいて監査する `HumanResources.EmployeePayHistory` という名前のデータベース監査仕様を作成します。</span><span class="sxs-lookup"><span data-stu-id="58c09-171">The example creates a database audit specification called `Audit_Pay_Tables` that audits SELECT and INSERT statements by the `dbo` user, for the `HumanResources.EmployeePayHistory` table based on the server audit defined above.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    -- Create the database audit specification.   
    CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
    FOR SERVER AUDIT Payrole_Security_Audit  
    ADD (SELECT , INSERT  
         ON HumanResources.EmployeePayHistory BY dbo )   
    WITH (STATE = ON) ;   
    GO  
  
    ```  
  
 <span data-ttu-id="58c09-172">詳細については、「[CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql)」と「[CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58c09-172">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql).</span></span>  
  
  
