---
title: データベースのサイズを大きくする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71dcb00b3f5525f7059fc54911baed929f763008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742189"
---
# <a name="increase-the-size-of-a-database"></a><span data-ttu-id="eab39-102">データベースのサイズを大きくする</span><span class="sxs-lookup"><span data-stu-id="eab39-102">Increase the Size of a Database</span></span>
  <span data-ttu-id="eab39-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースのサイズを大きくする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eab39-103">This topic describes how to increase the size of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="eab39-104">既存のデータ ファイルまたはログ ファイルのサイズを大きくするか、データベースに新しいファイルを追加することで、データベースを拡張します。</span><span class="sxs-lookup"><span data-stu-id="eab39-104">The database is expanded by either increasing the size of an existing data or log file or by adding a new file to the database.</span></span>  
  
 <span data-ttu-id="eab39-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="eab39-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eab39-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="eab39-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eab39-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eab39-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="eab39-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eab39-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eab39-109">**以下を使用してデータベースのサイズを大きくするには:**</span><span class="sxs-lookup"><span data-stu-id="eab39-109">**To increase the size of a database, using:**</span></span>  
  
     [<span data-ttu-id="eab39-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eab39-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eab39-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eab39-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eab39-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="eab39-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eab39-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eab39-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="eab39-114">BACKUP ステートメントの実行中にファイルを追加したり削除したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="eab39-114">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eab39-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eab39-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eab39-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="eab39-116">Permissions</span></span>  
 <span data-ttu-id="eab39-117">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eab39-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eab39-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="eab39-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="eab39-119">データベースのサイズを大きくするには</span><span class="sxs-lookup"><span data-stu-id="eab39-119">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="eab39-120">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="eab39-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="eab39-121">**[データベース]** を展開し、サイズを大きくするデータベースを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab39-121">Expand **Databases**, right-click the database to increase, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="eab39-122">**[データベースのプロパティ]** ダイアログ ボックスで、 **[ファイル]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab39-122">In **Database Properties**, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="eab39-123">既存のファイルのサイズを大きくするには、目的のファイルの **[初期サイズ (MB)]** 列の値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="eab39-123">To increase the size of an existing file, increase the value in the **Initial Size (MB)** column for the file.</span></span> <span data-ttu-id="eab39-124">データベースのサイズは、少なくとも 1 MB ずつ大きくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eab39-124">You must increase the size of the database by at least 1 megabyte.</span></span>  
  
5.  <span data-ttu-id="eab39-125">新しいファイルを追加してデータベースのサイズを大きくするには、 **[追加]** をクリックして、新しいファイルの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="eab39-125">To increase the size of the database by adding a new file, click **Add** and then enter the values for the new file.</span></span> <span data-ttu-id="eab39-126">詳細については、「 [データベースに対するデータ ファイルまたはログ ファイルの追加](add-data-or-log-files-to-a-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eab39-126">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
6.  <span data-ttu-id="eab39-127">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab39-127">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eab39-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="eab39-128">Using Transact-SQL</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="eab39-129">データベースのサイズを大きくするには</span><span class="sxs-lookup"><span data-stu-id="eab39-129">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="eab39-130">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="eab39-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eab39-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab39-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eab39-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab39-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="eab39-133">この例では、 `test1dat3`ファイルのサイズを拡張します。</span><span class="sxs-lookup"><span data-stu-id="eab39-133">This example increases the size of the file `test1dat3`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 <span data-ttu-id="eab39-134">詳細については、「[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eab39-134">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab39-135">参照</span><span class="sxs-lookup"><span data-stu-id="eab39-135">See Also</span></span>  
 <span data-ttu-id="eab39-136">[データベースに対するデータ ファイルまたはログ ファイルの追加](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="eab39-136">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="eab39-137">データベースの圧縮</span><span class="sxs-lookup"><span data-stu-id="eab39-137">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
