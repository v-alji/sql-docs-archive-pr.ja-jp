---
title: データの一括インポート時の ID 値の保持 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07f6714f27f60afda91134034509ff439d92f071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643338"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a><span data-ttu-id="9ea20-102">データの一括インポート時の ID 値の保持 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9ea20-102">Keep Identity Values When Bulk Importing Data (SQL Server)</span></span>
  <span data-ttu-id="9ea20-103">Id 値を含むデータファイルは、のインスタンスに一括インポートでき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9ea20-103">Data files that contain identity values can be bulk imported into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9ea20-104">既定では、インポートされたデータ ファイルの ID 列の値は無視され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって固有の値が自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9ea20-104">By default, the values for the identity column in the data file that is imported are ignored and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns unique values automatically.</span></span> <span data-ttu-id="9ea20-105">固有の値は、テーブル作成時に指定されたシード値と増分値に基づいています。</span><span class="sxs-lookup"><span data-stu-id="9ea20-105">The unique values are based on the seed and increment values that are specified during table creation.</span></span>  
  
 <span data-ttu-id="9ea20-106">データ ファイルにテーブルの ID 列の値が含まれていない場合は、フォーマット ファイルを使用してデータをインポートするときにテーブルの ID 列をスキップするように指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-106">If the data file does not contain values for the identifier column in the table, use a format file to specify that the identifier column in the table should be skipped when importing data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9ea20-107">は固有の値をこの列に自動的に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ea20-107">assigns unique values for the column automatically.</span></span>  
  
 <span data-ttu-id="9ea20-108">テーブルにデータ行を一括インポートするときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が ID 値を割り当てないようにするには、適切な keep-identity コマンド修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-108">To prevent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from assigning identity values while bulk importing data rows into a table, use the appropriate keep-identity command qualifier.</span></span> <span data-ttu-id="9ea20-109">keep-identity 修飾子を指定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではデータ ファイルの ID 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-109">When you specify a keep-identity qualifier, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the identity values in the data file.</span></span> <span data-ttu-id="9ea20-110">このような修飾子は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9ea20-110">These qualifiers are as follows:</span></span>  
  
|<span data-ttu-id="9ea20-111">command</span><span class="sxs-lookup"><span data-stu-id="9ea20-111">Command</span></span>|<span data-ttu-id="9ea20-112">Keep-identity 修飾子</span><span class="sxs-lookup"><span data-stu-id="9ea20-112">Keep-identity qualifier</span></span>|<span data-ttu-id="9ea20-113">修飾子の種類</span><span class="sxs-lookup"><span data-stu-id="9ea20-113">Qualifier type</span></span>|  
|-------------|------------------------------|--------------------|  
|`bcp`|<span data-ttu-id="9ea20-114">**-E**</span><span class="sxs-lookup"><span data-stu-id="9ea20-114">**-E**</span></span>|<span data-ttu-id="9ea20-115">Switch</span><span class="sxs-lookup"><span data-stu-id="9ea20-115">Switch</span></span>|  
|<span data-ttu-id="9ea20-116">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="9ea20-116">BULK INSERT</span></span>|<span data-ttu-id="9ea20-117">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="9ea20-117">KEEPIDENTITY</span></span>|<span data-ttu-id="9ea20-118">引数</span><span class="sxs-lookup"><span data-stu-id="9ea20-118">Argument</span></span>|  
|<span data-ttu-id="9ea20-119">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="9ea20-119">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="9ea20-120">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="9ea20-120">KEEPIDENTITY</span></span>|<span data-ttu-id="9ea20-121">テーブル ヒント</span><span class="sxs-lookup"><span data-stu-id="9ea20-121">Table hint</span></span>|  
  
 <span data-ttu-id="9ea20-122">詳細については、「[bcp Utility](../../tools/bcp-utility.md)」、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」、「[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」、「[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)」、「[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)」、「[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ea20-122">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ea20-123">複数のテーブルで使用できる自動的に増分する番号、またはテーブルを参照せずにアプリケーションから呼び出すことができる自動的に増分する番号を作成するには、「[シーケンス番号](../sequence-numbers/sequence-numbers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ea20-123">To create an automatically incrementing number that can be used in multiple tables or that can be called from applications without referencing any table, see [Sequence Numbers](../sequence-numbers/sequence-numbers.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9ea20-124">例</span><span class="sxs-lookup"><span data-stu-id="9ea20-124">Examples</span></span>  
 <span data-ttu-id="9ea20-125">このトピックの例では、INSERT ... SELECT \* FROM OPENROWSET(BULK...) を使用し、既定値を維持して、データを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="9ea20-125">The examples in this topic bulk import data using INSERT ... SELECT \* FROM OPENROWSET(BULK...) and keeping default values.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="9ea20-126">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="9ea20-126">Sample Table</span></span>  
 <span data-ttu-id="9ea20-127">この一括インポートの例では、**dbo** スキーマの下にある **AdventureWorks** サンプル データベースで **myTestKeepNulls** というテーブルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea20-127">The bulk-import examples require that a table named **myTestKeepNulls** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="9ea20-128">このテーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="9ea20-128">To create this table.</span></span> <span data-ttu-id="9ea20-129">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-129">in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 <span data-ttu-id="9ea20-130">`myDepartment` の基になる **Department** テーブルには IDENTITY_INSERT があり、OFF に設定されています。</span><span class="sxs-lookup"><span data-stu-id="9ea20-130">The **Department** table on which `myDepartment` is based has IDENTITY_INSERT is set to OFF.</span></span> <span data-ttu-id="9ea20-131">したがって、ID 列にデータをインポートするには、KEEPIDENTITY または **-E** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea20-131">Therefore, to import data into an identity column you must specify KEEPIDENTITY or **-E**.</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="9ea20-132">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="9ea20-132">Sample Data File</span></span>  
 <span data-ttu-id="9ea20-133">一括インポートの例で使用したデータ ファイルには、ネイティブ形式で `HumanResources.Department` テーブルから一括エクスポートされたデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ea20-133">The data file used in the bulk-import examples contains data bulk exported from the `HumanResources.Department` table in native format.</span></span> <span data-ttu-id="9ea20-134">このデータ ファイルを作成するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-134">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a><span data-ttu-id="9ea20-135">サンプル フォーマット ファイル</span><span class="sxs-lookup"><span data-stu-id="9ea20-135">Sample Format File</span></span>  
 <span data-ttu-id="9ea20-136">この一括インポートの例では `myDepartment-f-x-n.Xml` という XML フォーマット ファイルを使用します。ここではネイティブのデータ形式が使用されています。</span><span class="sxs-lookup"><span data-stu-id="9ea20-136">This bulk-import examples use an XML format file, `myDepartment-f-x-n.Xml`, which uses native data formats.</span></span> <span data-ttu-id="9ea20-137">この例では、`bcp` を使用して、`HumanResources.Department` データベースの `AdventureWorks` テーブルからこのフォーマット ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-137">This example uses `bcp` to create to generate this format file from the `HumanResources.Department` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="9ea20-138">Windows のコマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-138">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 <span data-ttu-id="9ea20-139">フォーマット ファイルの作成方法の詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ea20-139">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a><span data-ttu-id="9ea20-140">A.</span><span class="sxs-lookup"><span data-stu-id="9ea20-140">A.</span></span> <span data-ttu-id="9ea20-141">bcp を使用して ID 値を保持する方法</span><span class="sxs-lookup"><span data-stu-id="9ea20-141">Using bcp and Keeping Identity Values</span></span>  
 <span data-ttu-id="9ea20-142">次の例では、`bcp` を使用してデータを一括インポートするときに ID 値を保持する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-142">The following example demonstrates how to keep identity values when using `bcp` to bulk import data.</span></span> <span data-ttu-id="9ea20-143">`bcp` コマンドは、フォーマット ファイル `myDepartment-f-n-x.Xml` を使用し、次のスイッチを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="9ea20-143">The `bcp` command uses the format file, `myDepartment-f-n-x.Xml`, and contains the following switches:</span></span>  
  
|<span data-ttu-id="9ea20-144">修飾子</span><span class="sxs-lookup"><span data-stu-id="9ea20-144">Qualifiers</span></span>|<span data-ttu-id="9ea20-145">説明</span><span class="sxs-lookup"><span data-stu-id="9ea20-145">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="9ea20-146">**-E**</span><span class="sxs-lookup"><span data-stu-id="9ea20-146">**-E**</span></span>|<span data-ttu-id="9ea20-147">データ ファイルの ID 値を ID 列に使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-147">Specifies that identity value or values in the data file are to be used for the identity column.</span></span>|  
|<span data-ttu-id="9ea20-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="9ea20-148">**-T**</span></span>|<span data-ttu-id="9ea20-149">`bcp`ユーティリティが信頼関係接続を使用してに接続するように指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9ea20-149">Specifies that the `bcp` utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="9ea20-150">Windows のコマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a><span data-ttu-id="9ea20-151">B.</span><span class="sxs-lookup"><span data-stu-id="9ea20-151">B.</span></span> <span data-ttu-id="9ea20-152">BULK INSERT を使用して ID 値を保持する方法</span><span class="sxs-lookup"><span data-stu-id="9ea20-152">Using BULK INSERT and Keeping Identity Values</span></span>  
 <span data-ttu-id="9ea20-153">次の例では、BULK INSERT を使用して、`myDepartment-c.Dat` ファイルから `AdventureWorks.HumanResources.myDepartment` テーブルにデータを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="9ea20-153">The following example uses BULK INSERT to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="9ea20-154">このステートメントは、`myDepartment-f-n-x.Xml` フォーマット ファイルを使用し、データ ファイル内の任意の ID 値が必ず保持されるように KEEPIDENTITY オプションを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="9ea20-154">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY option to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="9ea20-155">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-155">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a><span data-ttu-id="9ea20-156">C.</span><span class="sxs-lookup"><span data-stu-id="9ea20-156">C.</span></span> <span data-ttu-id="9ea20-157">OPENROWSET を使用して ID 値を保持する方法</span><span class="sxs-lookup"><span data-stu-id="9ea20-157">Using OPENROWSET and Keeping Identity Values</span></span>  
 <span data-ttu-id="9ea20-158">次の例では、OPENROWSET 一括行セット プロバイダーを使用して、`myDepartment-c.Dat` ファイルから `AdventureWorks.HumanResources.myDepartment` テーブルにデータを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="9ea20-158">The following example uses the OPENROWSET bulk rowset provider to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="9ea20-159">このステートメントは、`myDepartment-f-n-x.Xml` フォーマット ファイルを使用し、データ ファイル内の任意の ID 値が必ず保持されるように KEEPIDENTITY ヒントを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="9ea20-159">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY hint to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="9ea20-160">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="9ea20-160">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9ea20-161">関連タスク</span><span class="sxs-lookup"><span data-stu-id="9ea20-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9ea20-162">一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-162">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-163">一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-163">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="9ea20-164">**フォーマット ファイルを作成するには**</span><span class="sxs-lookup"><span data-stu-id="9ea20-164">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="9ea20-165">フォーマット ファイルの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-165">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-166">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-166">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-167">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-167">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-168">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-168">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-169">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-169">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="9ea20-170">**一括インポートまたは一括エクスポートのデータ形式を使用するには**</span><span class="sxs-lookup"><span data-stu-id="9ea20-170">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="9ea20-171">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="9ea20-171">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-172">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-172">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-173">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-173">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-174">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-174">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="9ea20-175">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-175">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="9ea20-176">**bcp を使用した互換性のためのデータ形式を指定するには**</span><span class="sxs-lookup"><span data-stu-id="9ea20-176">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="9ea20-177">フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-177">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="9ea20-178">bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-178">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="9ea20-179">bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-179">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ea20-180">参照</span><span class="sxs-lookup"><span data-stu-id="9ea20-180">See Also</span></span>  
 <span data-ttu-id="9ea20-181">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ea20-181">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="9ea20-182">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="9ea20-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="9ea20-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ea20-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="9ea20-184">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ea20-184">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="9ea20-185">テーブル ヒント &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ea20-185">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
