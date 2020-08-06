---
title: データまたはログ ファイルのデータベースからの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- deleting files
- removing files
- removing data
- data deletions [SQL Server]
- file deletion [SQL Server]
- deleting data
ms.assetid: 0db4018c-ce2c-4ba1-bb29-1e4f3791c925
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f7bd170e085e9bc94b00446545850e905efaa34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742197"
---
# <a name="delete-data-or-log-files-from-a-database"></a><span data-ttu-id="d3ba0-102">データまたはログ ファイルのデータベースからの削除</span><span class="sxs-lookup"><span data-stu-id="d3ba0-102">Delete Data or Log Files from a Database</span></span>
  <span data-ttu-id="d3ba0-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データ ファイルまたはログ ファイルを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-103">This topic describes how to delete data or log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d3ba0-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="d3ba0-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d3ba0-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="d3ba0-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="d3ba0-106">ファイルは削除する前に空にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-106">A file must be empty before it can be deleted.</span></span> <span data-ttu-id="d3ba0-107">詳細については、「 [ファイルの圧縮](shrink-a-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-107">For more information, see [Shrink a File](shrink-a-file.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d3ba0-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d3ba0-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d3ba0-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="d3ba0-109">Permissions</span></span>  
 <span data-ttu-id="d3ba0-110">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-110">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d3ba0-111">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d3ba0-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="d3ba0-112">データ ファイルまたはログ ファイルをデータベースから削除するには</span><span class="sxs-lookup"><span data-stu-id="d3ba0-112">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="d3ba0-113">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-113">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d3ba0-114">**[データベース]** を展開し、ファイルを削除するデータベースを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-114">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d3ba0-115">**[ファイル]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-115">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="d3ba0-116">**[データベース ファイル]** グリッドで、削除するファイルをクリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-116">In the **Database files** grid, select the file to delete and then click **Remove**.</span></span>  
  
5.  <span data-ttu-id="d3ba0-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-117">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d3ba0-118">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d3ba0-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="d3ba0-119">データ ファイルまたはログ ファイルをデータベースから削除するには</span><span class="sxs-lookup"><span data-stu-id="d3ba0-119">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="d3ba0-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-120">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d3ba0-121">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-121">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d3ba0-122">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-122">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d3ba0-123">次の例では、 `test1dat4`ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-123">This example removes the file `test1dat4`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase4](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase4)]  
  
 <span data-ttu-id="d3ba0-124">詳細については、「[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3ba0-124">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ba0-125">参照</span><span class="sxs-lookup"><span data-stu-id="d3ba0-125">See Also</span></span>  
 <span data-ttu-id="d3ba0-126">[データベースの圧縮](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="d3ba0-126">[Shrink a Database](shrink-a-database.md) </span></span>  
 [<span data-ttu-id="d3ba0-127">データベースに対するデータ ファイルまたはログ ファイルの追加</span><span class="sxs-lookup"><span data-stu-id="d3ba0-127">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
