---
title: データベースに対するデータ ファイルまたはログ ファイルの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- adding data files
- adding files
- adding log files
- file additions [SQL Server], steps
- files [SQL Server], adding
- data additions [SQL Server]
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
author: stevestein
ms.author: sstein
ms.openlocfilehash: f72e00f9dab422652237b4b85579c544d0cda9fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742238"
---
# <a name="add-data-or-log-files-to-a-database"></a><span data-ttu-id="61177-102">データベースに対するデータ ファイルまたはログ ファイルの追加</span><span class="sxs-lookup"><span data-stu-id="61177-102">Add Data or Log Files to a Database</span></span>
  <span data-ttu-id="61177-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースにデータ ファイルまたはログ ファイルを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="61177-103">This topic describes how to add data or log files to a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="61177-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="61177-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="61177-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="61177-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="61177-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="61177-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="61177-107">Security</span><span class="sxs-lookup"><span data-stu-id="61177-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="61177-108">**以下を使用してデータ ファイルまたはログ ファイルをデータベースに追加するには:**</span><span class="sxs-lookup"><span data-stu-id="61177-108">**To add data or log files to a database, using:**</span></span>  
  
     [<span data-ttu-id="61177-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61177-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="61177-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61177-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="61177-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="61177-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="61177-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="61177-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="61177-113">BACKUP ステートメントの実行中にファイルを追加したり削除したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="61177-113">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
-   <span data-ttu-id="61177-114">各データベースに、最大 32,767 のファイルと 32,767 のファイル グループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="61177-114">A maximum of 32,767 files and 32,767 filegroups can be specified for each database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="61177-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="61177-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="61177-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="61177-116">Permissions</span></span>  
 <span data-ttu-id="61177-117">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="61177-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="61177-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="61177-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="61177-119">データ ファイルまたはログ ファイルをデータベースに追加するには</span><span class="sxs-lookup"><span data-stu-id="61177-119">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="61177-120">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="61177-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="61177-121">**[データベース]** を展開し、ファイルを追加するデータベースを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-121">Expand **Databases**, right-click the database from which to add the files, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="61177-122">**[データベースのプロパティ]** ダイアログ ボックスで、 **[ファイル]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-122">In the **Database Properties** dialog box, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="61177-123">データ ファイルまたはトランザクション ログ ファイルを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-123">To add a data or transaction log file, click **Add**.</span></span>  
  
5.  <span data-ttu-id="61177-124">**[データベース ファイル]** グリッドに、ファイルの論理名を入力します。</span><span class="sxs-lookup"><span data-stu-id="61177-124">In the **Database files** grid, enter a logical name for the file.</span></span> <span data-ttu-id="61177-125">このファイル名は、データベース内で一意になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="61177-125">The file name must be unique within the database.</span></span>  
  
6.  <span data-ttu-id="61177-126">ファイルの種類 (データまたはログ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="61177-126">Select the file type, data or log.</span></span>  
  
7.  <span data-ttu-id="61177-127">データ ファイルの場合、ファイルを含めるファイル グループを一覧から選択するか、 **\<new filegroup>** を選択して新しいファイル グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="61177-127">For a data file, select the filegroup in which the file should be included from the list, or select **\<new filegroup>** to create a new filegroup.</span></span> <span data-ttu-id="61177-128">トランザクション ログはファイル グループに追加できません。</span><span class="sxs-lookup"><span data-stu-id="61177-128">Transaction logs cannot be put in filegroups.</span></span>  
  
8.  <span data-ttu-id="61177-129">ファイルの初期サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="61177-129">Specify the initial size of the file.</span></span> <span data-ttu-id="61177-130">データベースに格納するデータの予想最大量に基づいて、データ ファイルのサイズを可能な限り大きく設定しておきます。</span><span class="sxs-lookup"><span data-stu-id="61177-130">Make the data file as large as possible, based on the maximum amount of data you expect in the database.</span></span>  
  
9. <span data-ttu-id="61177-131">ファイルの拡張方法を指定するには、 **[自動拡張]** 列で参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-131">To specify how the file should grow, click (**...**) in the **Autogrowth** column.</span></span> <span data-ttu-id="61177-132">次のオプションから選択します。</span><span class="sxs-lookup"><span data-stu-id="61177-132">Select from the following options:</span></span>  
  
    1.  <span data-ttu-id="61177-133">データ領域の追加が必要になったときに、現在選択されているファイルを拡張できるようにするには、 **[自動拡張を有効にする]** チェック ボックスをオンにして、次のオプションから選択します。</span><span class="sxs-lookup"><span data-stu-id="61177-133">To allow for the currently selected file to grow as more data space is required, select the **Enable Autogrowth** check box and then select from the following options:</span></span>  
  
    2.  <span data-ttu-id="61177-134">ファイルを一定の増加値で拡張することを指定するには、 **[MB 単位]** をクリックして、値を指定します。</span><span class="sxs-lookup"><span data-stu-id="61177-134">To specify that the file should grow by fixed increments, select **In Megabytes** and specify a value.</span></span>  
  
    3.  <span data-ttu-id="61177-135">現在のファイル サイズとの比率でファイルを拡張することを指定するには、 **[比率]** をクリックして、値を指定します。</span><span class="sxs-lookup"><span data-stu-id="61177-135">To specify that the file should grow by a percentage of the current file size, select **In Percent** and specify a value.</span></span>  
  
10. <span data-ttu-id="61177-136">最大ファイル サイズの制限を指定するには、次のオプションから選択します。</span><span class="sxs-lookup"><span data-stu-id="61177-136">To specify the maximum file size limit, select from the following options:</span></span>  
  
    1.  <span data-ttu-id="61177-137">ファイルを拡張できる最大サイズを指定するには、 **[ファイル拡張の制限 (MB)]** をクリックして、値を指定します。</span><span class="sxs-lookup"><span data-stu-id="61177-137">To specify the maximum size the file should be able to grow to, select **Restricted File Growth (MB)** and specify a value.</span></span>  
  
    2.  <span data-ttu-id="61177-138">必要なだけファイルを拡張できるようにするには、 **[ファイルを無制限に拡張]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-138">To allow for the file to grow as much as needed, select **Unrestricted File Growth**.</span></span>  
  
    3.  <span data-ttu-id="61177-139">ファイルの拡張を禁止するには、 **[自動拡張を有効にする]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="61177-139">To prevent the file from growing, clear the **Enable Autogrowth** check box.</span></span> <span data-ttu-id="61177-140">このように設定しておくと、ファイルのサイズが、 **[初期サイズ (MB)]** 列に指定した値より大きくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="61177-140">The size of the file will not grow beyond the value specified in the **Initial Size (MB)** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="61177-141">データベースの最大サイズは、使用できるディスクの空き領域、および使用中の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンによって決まるライセンス制限で決定されます。</span><span class="sxs-lookup"><span data-stu-id="61177-141">The maximum database size is determined by the amount of disk space available and the licensing limits determined by the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using.</span></span>  
  
11. <span data-ttu-id="61177-142">ファイルの場所のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="61177-142">Specify the path for the file location.</span></span> <span data-ttu-id="61177-143">指定したパスは、ファイルを追加する前に存在していなければなりません。</span><span class="sxs-lookup"><span data-stu-id="61177-143">The specified path must exist before adding the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="61177-144">データ ファイルとトランザクション ログ ファイルは、既定では単一ディスクのシステムに適合するように、同じドライブおよびパスに配置されますが、実稼働環境ではこれが最適ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="61177-144">By default, the data and transaction logs are put on the same drive and path to accommodate single-disk systems, but may not be optimal for production environments.</span></span> <span data-ttu-id="61177-145">詳細については、「 [Database Files and Filegroups](database-files-and-filegroups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61177-145">For more information, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
12. <span data-ttu-id="61177-146">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-146">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="61177-147">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="61177-147">Using Transact-SQL</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="61177-148">データ ファイルまたはログ ファイルをデータベースに追加するには</span><span class="sxs-lookup"><span data-stu-id="61177-148">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="61177-149">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="61177-149">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="61177-150">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-150">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="61177-151">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61177-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="61177-152">この例では、2 つのファイルから成るファイル グループをデータベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="61177-152">The example adds a filegroup with two files to a database.</span></span> <span data-ttu-id="61177-153">`Test1FG1` データベースに [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ファイル グループを作成し、そのファイル グループに 5 MB のファイルを 2 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="61177-153">The example creates the filegroup `Test1FG1` in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database and adds two 5-MB files to the filegroup.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase2](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase2)]  
  
 <span data-ttu-id="61177-154">詳細については、「[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61177-154">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61177-155">参照</span><span class="sxs-lookup"><span data-stu-id="61177-155">See Also</span></span>  
 <span data-ttu-id="61177-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="61177-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="61177-157">[データまたはログ ファイルのデータベースからの削除](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="61177-157">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 [<span data-ttu-id="61177-158">データベースのサイズを大きくする</span><span class="sxs-lookup"><span data-stu-id="61177-158">Increase the Size of a Database</span></span>](increase-the-size-of-a-database.md)  
  
  
