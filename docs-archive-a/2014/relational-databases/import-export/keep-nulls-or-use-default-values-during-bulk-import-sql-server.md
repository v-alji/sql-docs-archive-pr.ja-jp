---
title: 一括インポート中の NULL の保持または既定値の使用 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], null values
- bulk importing [SQL Server], default values
- data formats [SQL Server], null values
- bulk rowset providers [SQL Server]
- bcp utility [SQL Server], null values
- BULK INSERT statement
- default values
- OPENROWSET function, bulk importing
- data formats [SQL Server], default values
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 856aa12f6ad5e5094324e0df65941bc63d611451
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741053"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a><span data-ttu-id="89b98-102">一括インポート中の NULL の保持または既定値の使用 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="89b98-102">Keep Nulls or Use Default Values During Bulk Import (SQL Server)</span></span>
  <span data-ttu-id="89b98-103">既定では、データをテーブルにインポートするとき、 **bcp** コマンドと BULK INSERT ステートメントによって、テーブルの列に対して定義されているすべての既定値が監視されます。</span><span class="sxs-lookup"><span data-stu-id="89b98-103">By default, when data is imported into a table, the **bcp** command and BULK INSERT statement observe any defaults that are defined for the columns in the table.</span></span> <span data-ttu-id="89b98-104">たとえば、データ ファイルに NULL フィールドがある場合は、NULL 値の代わりにその列の既定値が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="89b98-104">For example, if there is a null field in a data file, the default value for the column is loaded instead.</span></span> <span data-ttu-id="89b98-105">**bcp** コマンドと BULK INSERT ステートメントの両方で、NULL 値を保持することを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="89b98-105">The **bcp** command and BULK INSERT statement both allow you to specify that nulls values be retained.</span></span>  
  
 <span data-ttu-id="89b98-106">これに対し、通常の INSERT ステートメントでは、既定値が挿入されるのではなく、NULL 値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="89b98-106">In contrast, a regular INSERT statement retains the null value instead of inserting a default value.</span></span> <span data-ttu-id="89b98-107">INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメントでは、通常の INSERT と同じ基本的な動作に加えて、既定値を挿入するためのテーブル ヒントがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="89b98-107">The INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement provides the same basic behavior as regular INSERT but additionally supports a table hint for inserting the default values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89b98-108">テーブル列をスキップするサンプル フォーマット ファイルについては、「[フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b98-108">For sample format files that skip a table column, see [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="89b98-109">サンプル テーブルとデータ ファイル</span><span class="sxs-lookup"><span data-stu-id="89b98-109">Sample Table and Data File</span></span>  
 <span data-ttu-id="89b98-110">このトピックに記載されている例を実行するには、サンプル テーブルとデータ ファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-110">To run the examples in this topic, you need to create a sample table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="89b98-111">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="89b98-111">Sample Table</span></span>  
 <span data-ttu-id="89b98-112">以下の例を実行するには、 **dbo** スキーマに基づいて、 **MyTestDefaultCol2** という名前のテーブルを **AdventureWorks** サンプル データベース内で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-112">The examples require that a table named **MyTestDefaultCol2** be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="89b98-113">このテーブルを作成するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="89b98-113">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 <span data-ttu-id="89b98-114">2 番目のテーブル列 `Col2`には既定値があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="89b98-114">Notice that the second table column, `Col2`, has a default value.</span></span>  
  
### <a name="sample-format-file"></a><span data-ttu-id="89b98-115">サンプル フォーマット ファイル</span><span class="sxs-lookup"><span data-stu-id="89b98-115">Sample Format File</span></span>  
 <span data-ttu-id="89b98-116">一括インポートの一部の例では、`MyTestDefaultCol2-f-c.Fmt` テーブルに対応している XML 以外のフォーマット ファイル `MyTestDefaultCol2` を使用します。</span><span class="sxs-lookup"><span data-stu-id="89b98-116">Some of the bulk-import examples use a non-XML format file, `MyTestDefaultCol2-f-c.Fmt` that corresponds exactly to the `MyTestDefaultCol2` table.</span></span> <span data-ttu-id="89b98-117">このフォーマット ファイルを作成するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="89b98-117">To create this format file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 <span data-ttu-id="89b98-118">フォーマット ファイルの作成方法の詳細については、「 [フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="89b98-118">For more information about creating format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="89b98-119">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="89b98-119">Sample Data File</span></span>  
 <span data-ttu-id="89b98-120">この例では、2 番目のフィールドに値を含まないサンプル データ ファイル `MyTestEmptyField2-c.Dat`を使用します。</span><span class="sxs-lookup"><span data-stu-id="89b98-120">The example uses a sample data file, `MyTestEmptyField2-c.Dat`, that contains no values in the second field.</span></span> <span data-ttu-id="89b98-121">`MyTestEmptyField2-c.Dat` データ ファイルには、以下のレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89b98-121">The `MyTestEmptyField2-c.Dat` data file contains the following records.</span></span>  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## <a name="keeping-null-values-with-bcp-or-bulk-insert"></a><span data-ttu-id="89b98-122">bcp または BULK INSERT を使用した NULL 値の保持</span><span class="sxs-lookup"><span data-stu-id="89b98-122">Keeping Null Values with bcp or BULK INSERT</span></span>  
 <span data-ttu-id="89b98-123">以下の修飾子は、一括インポート操作中、テーブル列の既定値がある場合にその既定値を継承するのではなく、データ ファイルの空のフィールドにそのフィールドの NULL 値を保持することを指定しています。</span><span class="sxs-lookup"><span data-stu-id="89b98-123">The following qualifiers specify that an empty field in the data file retains its null value during the bulk-import operation, rather than inheriting a default value (if any) for the table columns.</span></span>  
  
|<span data-ttu-id="89b98-124">command</span><span class="sxs-lookup"><span data-stu-id="89b98-124">Command</span></span>|<span data-ttu-id="89b98-125">Qualifier</span><span class="sxs-lookup"><span data-stu-id="89b98-125">Qualifier</span></span>|<span data-ttu-id="89b98-126">修飾子の種類</span><span class="sxs-lookup"><span data-stu-id="89b98-126">Qualifier type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="89b98-127">**bcp**</span><span class="sxs-lookup"><span data-stu-id="89b98-127">**bcp**</span></span>|`-k`|<span data-ttu-id="89b98-128">Switch</span><span class="sxs-lookup"><span data-stu-id="89b98-128">Switch</span></span>|  
|<span data-ttu-id="89b98-129">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="89b98-129">BULK INSERT</span></span>|<span data-ttu-id="89b98-130">KEEPNULLS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="89b98-130">KEEPNULLS<sup>1</sup></span></span>|<span data-ttu-id="89b98-131">引数</span><span class="sxs-lookup"><span data-stu-id="89b98-131">Argument</span></span>|  
  
 <span data-ttu-id="89b98-132"><sup>1</sup> BULK INSERT の場合、既定値を使用できない場合は、null 値を許容するようにテーブル列を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-132"><sup>1</sup> For BULK INSERT, if default values are not available, the table column must be defined to allow null values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89b98-133">上記の修飾子は、一括インポート コマンドによるテーブルでの DEFAULT 定義の確認を無効にします。</span><span class="sxs-lookup"><span data-stu-id="89b98-133">These qualifiers disable checking of DEFAULT definitions on a table by these bulk-import commands.</span></span> <span data-ttu-id="89b98-134">ただし、同時に実行するすべての INSERT ステートメントでは、DEFAULT 定義が必要です。</span><span class="sxs-lookup"><span data-stu-id="89b98-134">However, for any concurrent INSERT statements, DEFAULT definitions are expected.</span></span>  
  
 <span data-ttu-id="89b98-135">詳細については、「[bcp ユーティリティ](../../tools/bcp-utility.md)」と「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b98-135">For more information, see [bcp Utility](../../tools/bcp-utility.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89b98-136">例</span><span class="sxs-lookup"><span data-stu-id="89b98-136">Examples</span></span>  
 <span data-ttu-id="89b98-137">以下の例では、 **bcp** または BULK INSERT を使用して一括インポートを行い、NULL 値を保持します。</span><span class="sxs-lookup"><span data-stu-id="89b98-137">The examples in this section bulk import using **bcp** or BULK INSERT and keep null values.</span></span>  
  
 <span data-ttu-id="89b98-138">2 番目のテーブル列 **Col2**には、既定値があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-138">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="89b98-139">データ ファイルの対応するフィールドには、空の文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="89b98-139">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="89b98-140">既定では、 **bcp** または BULK INSERT を使用して、このデータ ファイルから **MyTestDefaultCol2** テーブルにデータをインポートすると、 **Col2** の既定値が挿入され、以下の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="89b98-140">By default, when **bcp** or BULK INSERT is used to import data from this data file into the **MyTestDefaultCol2** table, the default value of **Col2** is inserted, producing the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 <span data-ttu-id="89b98-141">"" ではなく "" を挿入するに `NULL` `Default value of Col2` は、次の `-k` **bcp**と BULK INSERT の例に示すように、switch または keepnull オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-141">To insert "`NULL`" instead of "`Default value of Col2`", you need to use the `-k` switch or KEEPNULL option, as demonstrated in the following **bcp** and BULK INSERT examples.</span></span>  
  
#### <a name="using-bcp-and-keeping-null-values"></a><span data-ttu-id="89b98-142">bcp の使用および NULL 値の保持</span><span class="sxs-lookup"><span data-stu-id="89b98-142">Using bcp and Keeping Null Values</span></span>  
 <span data-ttu-id="89b98-143">次の例では、 **bcp** コマンドで NULL 値を保持する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89b98-143">The following example demonstrates how to keep null values in a **bcp** command.</span></span> <span data-ttu-id="89b98-144">**Bcp**コマンドには、次のスイッチが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89b98-144">The **bcp** command contains the following switches:</span></span>  
  
|<span data-ttu-id="89b98-145">Switch</span><span class="sxs-lookup"><span data-stu-id="89b98-145">Switch</span></span>|<span data-ttu-id="89b98-146">説明</span><span class="sxs-lookup"><span data-stu-id="89b98-146">Description</span></span>|  
|------------|-----------------|  
|`-f`|<span data-ttu-id="89b98-147">コマンドでフォーマット ファイルが使用されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="89b98-147">Specifies that the command is using a format file..</span></span>|  
|`-k`|<span data-ttu-id="89b98-148">一括コピー操作時、空の列には、挿入される列の既定値ではなく、NULL 値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="89b98-148">Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.</span></span>|  
|`-T`|<span data-ttu-id="89b98-149">bcp ユーティリティが信頼関係接続を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することを指定します。</span><span class="sxs-lookup"><span data-stu-id="89b98-149">Specifies that the bcp utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="89b98-150">Windows のコマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="89b98-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### <a name="using-bulk-insert-and-keeping-null-values"></a><span data-ttu-id="89b98-151">BULK INSERT の使用および NULL 値の保持</span><span class="sxs-lookup"><span data-stu-id="89b98-151">Using BULK INSERT and Keeping Null Values</span></span>  
 <span data-ttu-id="89b98-152">次の例では、BULK INSERT ステートメントで KEEPNULLS オプションを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89b98-152">The following example demonstrates how to use the KEEPNULLS option in a BULK INSERT statement.</span></span> <span data-ttu-id="89b98-153">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリ エディターなどのクエリ ツールから、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="89b98-153">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a><span data-ttu-id="89b98-154">INSERT ... SELECT \* FROM OPENROWSET(BULK...) を使用した既定値の保持</span><span class="sxs-lookup"><span data-stu-id="89b98-154">Keeping Default Values with INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
 <span data-ttu-id="89b98-155">既定では、一括読み込み操作で指定されていない列は、INSERT...SELECT \* FROM OPENROWSET (BULK...)。ただし、データファイルの空のフィールドに対して、対応するテーブル列が既定値 (存在する場合) を使用するように指定することができます。</span><span class="sxs-lookup"><span data-stu-id="89b98-155">By default, any columns that are not specified in the bulk-load operation are set to NULL by INSERT ... SELECT \* FROM OPENROWSET(BULK...). However, you can specify that for an empty field in the data file, the corresponding table column uses its default value (if any).</span></span> <span data-ttu-id="89b98-156">既定値を使用するには、次のテーブル ヒントを指定します。</span><span class="sxs-lookup"><span data-stu-id="89b98-156">To use default values, specify the following table hint:</span></span>  
  
|<span data-ttu-id="89b98-157">command</span><span class="sxs-lookup"><span data-stu-id="89b98-157">Command</span></span>|<span data-ttu-id="89b98-158">Qualifier</span><span class="sxs-lookup"><span data-stu-id="89b98-158">Qualifier</span></span>|<span data-ttu-id="89b98-159">修飾子の種類</span><span class="sxs-lookup"><span data-stu-id="89b98-159">Qualifier Type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="89b98-160">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="89b98-160">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="89b98-161">WITH(KEEPDEFAULTS)</span><span class="sxs-lookup"><span data-stu-id="89b98-161">WITH(KEEPDEFAULTS)</span></span>|<span data-ttu-id="89b98-162">テーブル ヒント</span><span class="sxs-lookup"><span data-stu-id="89b98-162">Table hint</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="89b98-163">詳細については、「transact-sql [&#41;の &#40;挿入](/sql/t-sql/statements/insert-transact-sql)」、「 [SELECT &#40;transact-sql&#41;](/sql/t-sql/queries/select-transact-sql)」、「 [OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql)」、および「[テーブルヒント &#40;transact-sql](/sql/t-sql/queries/hints-transact-sql-table)&#41;」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b98-163">for more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89b98-164">例</span><span class="sxs-lookup"><span data-stu-id="89b98-164">Examples</span></span>  
 <span data-ttu-id="89b98-165">次の INSERT ... SELECT \* FROM OPENROWSET(BULK...) の例では、データを一括インポートし、既定値を保持します。</span><span class="sxs-lookup"><span data-stu-id="89b98-165">The following INSERT ... SELECT \* FROM OPENROWSET(BULK...) example bulk imports data and keeps the default values.</span></span>  
  
 <span data-ttu-id="89b98-166">この例を実行するには、 **MyTestDefaultCol2** サンプル テーブルと `MyTestEmptyField2-c.Dat` データ ファイルを作成し、 `MyTestDefaultCol2-f-c.Fmt`というフォーマット ファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-166">To run the examples, you need to create the **MyTestDefaultCol2** sample table, the `MyTestEmptyField2-c.Dat` data file, and use a format file, `MyTestDefaultCol2-f-c.Fmt`.</span></span> <span data-ttu-id="89b98-167">これらのサンプルの作成については、このトピックの前半の「サンプル テーブルとデータ ファイル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b98-167">For information on creating these samples, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="89b98-168">2 番目のテーブル列 **Col2**には、既定値があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-168">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="89b98-169">データ ファイルの対応するフィールドには、空の文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="89b98-169">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="89b98-170">INSERT...SELECT \* FROM OPENROWSET (BULK...) は、このデータファイルのフィールドを**MyTestDefaultCol2**テーブルにインポートします。既定では、NULL は既定値ではなく**Col2**に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="89b98-170">When INSERT ... SELECT \* FROM OPENROWSET(BULK...) import the fields of this data file into the **MyTestDefaultCol2** table, by default, NULL is inserted into **Col2** instead of the default value.</span></span> <span data-ttu-id="89b98-171">この既定の動作により、以下の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="89b98-171">This default behavior produces the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 <span data-ttu-id="89b98-172">"`Default value of Col2`" ではなく既定値 "`NULL`" を挿入するには、次の例で説明するように、KEEPDEFAULTS テーブル ヒントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b98-172">To insert the default value, "`Default value of Col2`", instead of "`NULL`", you need to use KEEPDEFAULTS table hint, as demonstrated in the following example.</span></span> <span data-ttu-id="89b98-173">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリ エディターなどのクエリ ツールから、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="89b98-173">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="89b98-174">関連タスク</span><span class="sxs-lookup"><span data-stu-id="89b98-174">Related Tasks</span></span>  
  
-   [<span data-ttu-id="89b98-175">データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-175">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="89b98-176">一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-176">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="89b98-177">**フォーマット ファイルを作成するには**</span><span class="sxs-lookup"><span data-stu-id="89b98-177">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="89b98-178">フォーマット ファイルの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-178">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="89b98-179">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-179">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="89b98-180">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-180">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="89b98-181">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-181">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="89b98-182">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-182">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="89b98-183">**一括インポートまたは一括エクスポートのデータ形式を使用するには**</span><span class="sxs-lookup"><span data-stu-id="89b98-183">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="89b98-184">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="89b98-184">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="89b98-185">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-185">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="89b98-186">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-186">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="89b98-187">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="89b98-188">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="89b98-189">**bcp を使用した互換性のためのデータ形式を指定するには**</span><span class="sxs-lookup"><span data-stu-id="89b98-189">**To specify data formats for compatibility when using bcp**</span></span>  
  
-   [<span data-ttu-id="89b98-190">フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-190">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="89b98-191">bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-191">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="89b98-192">bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-192">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="89b98-193">参照</span><span class="sxs-lookup"><span data-stu-id="89b98-193">See Also</span></span>  
 <span data-ttu-id="89b98-194">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="89b98-194">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="89b98-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="89b98-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="89b98-196">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="89b98-196">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="89b98-197">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="89b98-197">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="89b98-198">テーブル ヒント &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="89b98-198">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
