---
title: 'チュートリアル: Transact-SQL ステートメントの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL statements, tutorials
- Transact-SQL tutorials
- tutorials [Transact-SQL]
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ac190d6099bca1a38ca2f286e6ce048fe5322e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741502"
---
# <a name="tutorial-writing-transact-sql-statements"></a><span data-ttu-id="b463b-102">チュートリアル: Transact-SQL ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="b463b-102">Tutorial: Writing Transact-SQL Statements</span></span>
  <span data-ttu-id="b463b-103">[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの作成チュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="b463b-103">Welcome to the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="b463b-104">このチュートリアルは、SQL ステートメントを初めて作成するユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="b463b-104">This tutorial is intended for users who are new to writing SQL statements.</span></span> <span data-ttu-id="b463b-105">ここでは初心者のユーザーを対象に、テーブルを作成し、データを挿入するための基本的なステートメントを紹介します。</span><span class="sxs-lookup"><span data-stu-id="b463b-105">It will help new users get started by reviewing some basic statements for creating tables and inserting data.</span></span> <span data-ttu-id="b463b-106">このチュートリアルでは、 [!INCLUDE[tsql](../includes/tsql-md.md)]製品に実装されている SQL 規格の [!INCLUDE[msCoName](../includes/msconame-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="b463b-106">This tutorial uses [!INCLUDE[tsql](../includes/tsql-md.md)], the [!INCLUDE[msCoName](../includes/msconame-md.md)] implementation of the SQL standard.</span></span> <span data-ttu-id="b463b-107">このチュートリアルは、 [!INCLUDE[tsql](../includes/tsql-md.md)] 言語を簡単に紹介することを目的としています。 [!INCLUDE[tsql](../includes/tsql-md.md)] クラスの代わりとなるものではありません。</span><span class="sxs-lookup"><span data-stu-id="b463b-107">This tutorial is intended as a brief introduction to the [!INCLUDE[tsql](../includes/tsql-md.md)] language and not as a replacement for a [!INCLUDE[tsql](../includes/tsql-md.md)] class.</span></span> <span data-ttu-id="b463b-108">このチュートリアルで使用するステートメントは意図的に簡潔化されており、通常の実稼働データベースに見られる複雑性を表すものではありません。</span><span class="sxs-lookup"><span data-stu-id="b463b-108">The statements in this tutorial are intentionally simple, and are not meant to represent the complexity found in a typical production database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b463b-109">データベースの初心者ユーザーは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ステートメントを作成する代わりに、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../includes/tsql-md.md)] を操作した方が通常は簡単です。</span><span class="sxs-lookup"><span data-stu-id="b463b-109">Novice users of databases will usually find it easier to work with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], instead of writing [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="b463b-110">詳細情報</span><span class="sxs-lookup"><span data-stu-id="b463b-110">Finding More Information</span></span>  
 <span data-ttu-id="b463b-111">特定のステートメントの詳細については、SQL Server オンライン ブックで名前を指定してステートメントを検索するか、[コンテンツ] を使用して、[Transact-SQL リファレンス (データベース エンジン)](/sql/t-sql/language-reference) の下にアルファベット順に列挙されている 1,800 の言語要素を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b463b-111">To find more information about any specific statement, either search for the statement by name in SQL Server Books Online, or use the Contents to browse the 1,800 language elements listed alphabetically under [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span> <span data-ttu-id="b463b-112">情報を検索する別の方法として、興味のある内容に関連するキーワードを検索する方法があります。</span><span class="sxs-lookup"><span data-stu-id="b463b-112">Another good strategy for finding information is to search for key words that are related to the subject matter you are interested in.</span></span> <span data-ttu-id="b463b-113">たとえば、日付の一部 (月など) を返す方法を求めるには、 **日付 [SQL Server]** のインデックスを検索し、 **日付要素**を選択します。</span><span class="sxs-lookup"><span data-stu-id="b463b-113">For example, if you want to know how to return a part of a date (such as the month), search the index for **dates [SQL Server]**, and then select **dateparts**.</span></span> <span data-ttu-id="b463b-114">これにより、トピック [「DATEPART (Transact-SQL)」](/sql/t-sql/functions/datepart-transact-sql) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b463b-114">This takes you to the topic [DATEPART &#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql).</span></span> <span data-ttu-id="b463b-115">別の例として、文字列の操作方法を求めるには、 **文字列関数**を検索します。</span><span class="sxs-lookup"><span data-stu-id="b463b-115">As another example, to find out how to work with strings, search for **string functions**.</span></span> <span data-ttu-id="b463b-116">これにより、トピック [「文字列関数 (Transact-SQL)」](/sql/t-sql/functions/string-functions-transact-sql) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b463b-116">This takes you to the topic [String Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="b463b-117">学習する内容</span><span class="sxs-lookup"><span data-stu-id="b463b-117">What You Will Learn</span></span>  
 <span data-ttu-id="b463b-118">このチュートリアルでは、データベースの作成、データベースのテーブルの作成、テーブルへのデータの挿入、データの更新、読み取り、削除、およびテーブルの削除の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b463b-118">This tutorial shows you how to create a database, create a table in the database, insert data into the table, update the data, read the data, delete the data, and then delete the table.</span></span> <span data-ttu-id="b463b-119">ユーザーは、ビューやストアド プロシージャを作成し、データベースとデータのユーザーを構成します。</span><span class="sxs-lookup"><span data-stu-id="b463b-119">You will create views and stored procedures and configure a user to the database and the data.</span></span>  
  
 <span data-ttu-id="b463b-120">このチュートリアルは、次の 3 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="b463b-120">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="b463b-121">レッスン 1: データベース オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="b463b-121">Lesson 1: Creating Database Objects</span></span>](lesson-1-creating-database-objects.md)  
 <span data-ttu-id="b463b-122">このレッスンでは、データベースを作成し、データベースにテーブルを作成し、データをテーブルに挿入します。さらに、データを更新し、読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b463b-122">In this lesson, you create a database, create a table in the database, insert data into the table, update the data, and read the data.</span></span>  
  
 [<span data-ttu-id="b463b-123">レッスン 2: データベース オブジェクトに対するアクセス許可の構成</span><span class="sxs-lookup"><span data-stu-id="b463b-123">Lesson 2: Configuring Permissions on Database Objects</span></span>](lesson-2-configuring-permissions-on-database-objects.md)  
 <span data-ttu-id="b463b-124">このレッスンでは、ログインとユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b463b-124">In this lesson, you create a login and user.</span></span> <span data-ttu-id="b463b-125">また、ビューとストアド プロシージャも作成し、ストアド プロシージャにユーザー権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="b463b-125">You will also create a view and a stored procedure, and then grant the user permission to the stored procedure.</span></span>  
  
 [<span data-ttu-id="b463b-126">レッスン 3: データベース オブジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="b463b-126">Lesson 3: Deleting Database Objects</span></span>](lesson-3-1-deleting-database-objects.md)  
 <span data-ttu-id="b463b-127">このレッスンでは、データへのアクセス権を削除し、データをテーブルから削除し、テーブル、次にデータベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="b463b-127">In this lesson, you remove access to data, delete data from a table, delete the table, and then delete the database.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b463b-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="b463b-128">Requirements</span></span>  
 <span data-ttu-id="b463b-129">このチュートリアルを完了するにあたって SQL 言語に関する知識は必要ありませんが、テーブルなどの基本的なデータベース概念は理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b463b-129">To complete this tutorial, you do not have to know the SQL language, but you should understand basic database concepts such as tables.</span></span> <span data-ttu-id="b463b-130">このチュートリアルでは、データベースと Windows ユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b463b-130">During this tutorial, you will create a database and create a Windows user.</span></span> <span data-ttu-id="b463b-131">これらのタスクには高レベルのアクセス許可が必要なので、コンピューターには管理者としてログインしてください。</span><span class="sxs-lookup"><span data-stu-id="b463b-131">These tasks require a high level of permissions; therefore, you should log in to the computer as an administrator.</span></span>  
  
 <span data-ttu-id="b463b-132">システムには次のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b463b-132">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="b463b-133">任意のエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b463b-133">Any edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b463b-134">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] または Management Studio Express</span><span class="sxs-lookup"><span data-stu-id="b463b-134">Either [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or Management Studio Express.</span></span>  
  
-   <span data-ttu-id="b463b-135">Internet Explorer 6 以降。</span><span class="sxs-lookup"><span data-stu-id="b463b-135">Internet Explorer 6 or later.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b463b-136">チュートリアルを確認するときは、ドキュメントビューアーのツールバーに **[次へ**] ボタンと [**前**へ] ボタンを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b463b-136">When you review the tutorials, we recommend that you add the **Next** and **Previous** buttons to the document viewer toolbar.</span></span>  
  
  
