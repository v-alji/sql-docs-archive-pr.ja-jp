---
title: テーブルの複製 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 793a38416f86a5b43a3e3bb2420127d7acf2af1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634374"
---
# <a name="duplicate-tables"></a><span data-ttu-id="41ae4-102">テーブルの複製</span><span class="sxs-lookup"><span data-stu-id="41ae4-102">Duplicate Tables</span></span>
  <span data-ttu-id="41ae4-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、新しいテーブルを作成して既存のテーブルから列情報をコピーすることで既存のテーブルを複製できます。</span><span class="sxs-lookup"><span data-stu-id="41ae4-103">You can duplicate an existing table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] by creating a new table and then copying column information from an existing table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="41ae4-104">この操作によって複製されるのはテーブルの構造のみです。テーブル行は複製されません。</span><span class="sxs-lookup"><span data-stu-id="41ae4-104">This operation duplicates only the structure of a table; it does not duplicate any table rows.</span></span>  
  
 <span data-ttu-id="41ae4-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="41ae4-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="41ae4-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="41ae4-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="41ae4-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="41ae4-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="41ae4-108">**テーブルを複製するための方法:**</span><span class="sxs-lookup"><span data-stu-id="41ae4-108">**To duplicate a table, using:**</span></span>  
  
     [<span data-ttu-id="41ae4-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="41ae4-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="41ae4-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41ae4-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="41ae4-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="41ae4-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="41ae4-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="41ae4-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="41ae4-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="41ae4-113">Permissions</span></span>  
 <span data-ttu-id="41ae4-114">対象となるデータベースの CREATE TABLE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="41ae4-114">Requires CREATE TABLE permission in the destination database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="41ae4-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="41ae4-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-duplicate-a-table"></a><span data-ttu-id="41ae4-116">テーブルを複製するには</span><span class="sxs-lookup"><span data-stu-id="41ae4-116">To duplicate a table</span></span>  
  
1.  <span data-ttu-id="41ae4-117">テーブルを作成するデータベースに接続していること、およびそのデータベースがオブジェクト エクスプローラーで選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="41ae4-117">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="41ae4-118">オブジェクト エクスプローラーで、 **[テーブル]** を右クリックし、 **[新しいテーブル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-118">In Object Explorer, right-click **Tables** and click **New Table**.</span></span>  
  
3.  <span data-ttu-id="41ae4-119">オブジェクト エクスプローラーで、コピーするテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-119">In Object Explorer right-click the table you want to copy and click **Design**.</span></span>  
  
4.  <span data-ttu-id="41ae4-120">既存のテーブルの列を選択し、 **[編集]** メニューの **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-120">Select the columns in the existing table and, from the **Edit** menu, click **Copy**.</span></span>  
  
5.  <span data-ttu-id="41ae4-121">新しいテーブルに戻り、1 行目を選択します。</span><span class="sxs-lookup"><span data-stu-id="41ae4-121">Switch back to the new table and select the first row.</span></span>  
  
6.  <span data-ttu-id="41ae4-122">**[編集]** メニューの **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-122">From the **Edit** menu, click **Paste**.</span></span>  
  
7.  <span data-ttu-id="41ae4-123">**[ファイル]** メニューの **[<_テーブル名_> を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-123">From the **File** menu, click **Save**_table name_.</span></span>  
  
8.  <span data-ttu-id="41ae4-124">**[名前の選択]** ダイアログ ボックスで、新しいテーブルの名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-124">In the **Choose Name** dialog box, type a name for the new table and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="41ae4-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="41ae4-125">Using Transact-SQL</span></span>  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a><span data-ttu-id="41ae4-126">クエリ エディターでテーブルを複製するには</span><span class="sxs-lookup"><span data-stu-id="41ae4-126">To duplicate a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="41ae4-127">テーブルを作成するデータベースに接続していること、およびそのデータベースがオブジェクト エクスプローラーで選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="41ae4-127">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="41ae4-128">複製するテーブルを右クリックし、 **[テーブルをスクリプト化]** をポイントして、 **[CREATE]** をポイントします。次に、 **[新しいクエリ エディター ウィンドウ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-128">Right-click the table you wish to duplicate, point to **Script Table as**, then point to **CREATE to**, and then select **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="41ae4-129">テーブルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="41ae4-129">Change the name of the table.</span></span>  
  
4.  <span data-ttu-id="41ae4-130">新しいテーブルに必要でない列をすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="41ae4-130">Remove any columns that are not needed in the new table.</span></span>  
  
5.  <span data-ttu-id="41ae4-131">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ae4-131">Click **Execute**.</span></span>  
  
  
