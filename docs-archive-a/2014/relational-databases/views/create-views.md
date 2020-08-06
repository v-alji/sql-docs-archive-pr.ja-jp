---
title: ビューの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], creating
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8280f6d65d7252cad423abef849207111492c044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631724"
---
# <a name="create-views"></a><span data-ttu-id="25c83-102">ビューの作成</span><span class="sxs-lookup"><span data-stu-id="25c83-102">Create Views</span></span>
  <span data-ttu-id="25c83-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ビューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="25c83-103">You can create views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="25c83-104">ビューは、次の目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="25c83-104">A view can be used for the following purposes:</span></span>  
  
-   <span data-ttu-id="25c83-105">各ユーザーのデータベースに対する認識を特化、簡素化、およびカスタマイズする。</span><span class="sxs-lookup"><span data-stu-id="25c83-105">To focus, simplify, and customize the perception each user has of the database.</span></span>  
  
-   <span data-ttu-id="25c83-106">基になるベース テーブルに直接アクセスする権限をユーザーに与えずに、ユーザーがビューを介してデータにアクセスできるように設定することにより、セキュリティのメカニズムとして使用する。</span><span class="sxs-lookup"><span data-stu-id="25c83-106">As a security mechanism by allowing users to access data through the view, without granting the users permissions to directly access the underlying base tables.</span></span>  
  
-   <span data-ttu-id="25c83-107">テーブルのスキーマが変更された場合に、そのテーブルをエミュレートするための後方互換性インターフェイスを提供する。</span><span class="sxs-lookup"><span data-stu-id="25c83-107">To provide a backward compatible interface to emulate a table whose schema has changed.</span></span>  
  
 <span data-ttu-id="25c83-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="25c83-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="25c83-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="25c83-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="25c83-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="25c83-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="25c83-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="25c83-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="25c83-112">**以下を使用してビューを作成するには**</span><span class="sxs-lookup"><span data-stu-id="25c83-112">**To create a view, using:**</span></span>  
  
     [<span data-ttu-id="25c83-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="25c83-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="25c83-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25c83-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="25c83-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="25c83-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="25c83-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="25c83-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="25c83-117">ビューは現在のデータベースでのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="25c83-117">A view can be created only in the current database.</span></span>  
  
 <span data-ttu-id="25c83-118">1 つのビューで保持できる列の数は最大 1,024 です。</span><span class="sxs-lookup"><span data-stu-id="25c83-118">A view can have a maximum of 1,024 columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="25c83-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="25c83-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="25c83-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="25c83-120">Permissions</span></span>  
 <span data-ttu-id="25c83-121">データベースの CREATE VIEW 権限と、ビューが作成されているスキーマの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="25c83-121">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="25c83-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="25c83-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-view-by-using-the-query-and-view-designer"></a><span data-ttu-id="25c83-123">クエリおよびビュー デザイナーを使用してビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="25c83-123">To create a view by using the Query and View Designer</span></span>  
  
1.  <span data-ttu-id="25c83-124">**オブジェクト エクスプローラー**で、新しいビューを作成するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="25c83-124">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="25c83-125">**[ビュー]** フォルダーを右クリックし、 **[新しいビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25c83-125">Right-click the **Views** folder, then click **New View...**.</span></span>  
  
3.  <span data-ttu-id="25c83-126">**[テーブルの追加]** ダイアログ ボックスで、新しいビューに含める 1 つまたは複数の要素を、[テーブル]、[ビュー]、[関数]、および [シノニム] のいずれかのタブから選択します。</span><span class="sxs-lookup"><span data-stu-id="25c83-126">In the **Add Table** dialog box, select the element or elements that you want to include in your new view from one of the following tabs: Tables, Views, Functions, and Synonyms.</span></span>  
  
4.  <span data-ttu-id="25c83-127">**[追加]** をクリックし、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25c83-127">Click **Add**, then click **Close**.</span></span>  
  
5.  <span data-ttu-id="25c83-128">**ダイアグラム ペイン**で、新しいビューに含める列またはその他の要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="25c83-128">In the **Diagram Pane**, select the columns or other elements to include in the new view.</span></span>  
  
6.  <span data-ttu-id="25c83-129">**抽出条件ペイン**で、列の追加の並べ替え条件またはフィルター条件を選択します。</span><span class="sxs-lookup"><span data-stu-id="25c83-129">In the **Criteria Pane**, select additional sort or filter criteria for the columns.</span></span>  
  
7.  <span data-ttu-id="25c83-130">**ファイル** メニューの **view name**_の保存_をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25c83-130">On the **File** menu, click **Save**_view name_.</span></span>  
  
8.  <span data-ttu-id="25c83-131">**[名前の選択]** ダイアログ ボックスで、新しいビューの名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25c83-131">In the **Choose Name** dialog box, enter a name for the new view and click **OK**.</span></span>  
  
     <span data-ttu-id="25c83-132">クエリおよびビュー デザイナーの詳細については、「[クエリおよびビュー デザイナー &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25c83-132">For more information about the query and view designer, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="25c83-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="25c83-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-view"></a><span data-ttu-id="25c83-134">ビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="25c83-134">To create a view</span></span>  
  
1.  <span data-ttu-id="25c83-135">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="25c83-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="25c83-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25c83-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="25c83-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25c83-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 <span data-ttu-id="25c83-138">詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25c83-138">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
  
