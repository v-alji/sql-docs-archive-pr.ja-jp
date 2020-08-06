---
title: フォーマット ファイルを使用したテーブル列のスキップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- skipping columns when importing
- format files [SQL Server], skipping columns
ms.assetid: 30e0e7b9-d131-46c7-90a4-6ccf77e3d4f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 153ef21209ff4261020e26aca3bc52d28dc852a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646151"
---
# <a name="use-a-format-file-to-skip-a-table-column-sql-server"></a><span data-ttu-id="f4852-102">フォーマット ファイルを使用したテーブル列のスキップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4852-102">Use a Format File to Skip a Table Column (SQL Server)</span></span>
  <span data-ttu-id="f4852-103">このトピックでは、フォーマット ファイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4852-103">This topic describes format files.</span></span> <span data-ttu-id="f4852-104">フォーマット ファイルを使用すると、データ ファイルにフィールドが存在しない場合にテーブル列のインポートをスキップできます。</span><span class="sxs-lookup"><span data-stu-id="f4852-104">You can use a format file to skip importing a table column when the field does not exist in the data file.</span></span> <span data-ttu-id="f4852-105">スキップされる列に NULL 値が許容されているか、既定値があるか、またはその両方の場合のみ、テーブルの列の数より少ないフィールドをデータ ファイルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f4852-105">A data file can contain fewer fields than the number of columns in the table only if the skipped columns are nullable and/or have default value.</span></span>

## <a name="sample-table-and-data-file"></a><span data-ttu-id="f4852-106">サンプル テーブルとデータ ファイル</span><span class="sxs-lookup"><span data-stu-id="f4852-106">Sample Table and Data File</span></span>
 <span data-ttu-id="f4852-107">次の例では、 `myTestSkipCol` サンプル データベースで [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] というテーブルを **dbo** スキーマを使用して作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-107">The following examples require a table named `myTestSkipCol` in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="f4852-108">このテーブルは次のように作成します。</span><span class="sxs-lookup"><span data-stu-id="f4852-108">Create this table as follows:</span></span>

```
USE AdventureWorks2012;
GO
CREATE TABLE myTestSkipCol 
   (
   Col1 smallint,
   Col2 nvarchar(50) NULL,
   Col3 nvarchar(50) not NULL
   );
GO
```

 <span data-ttu-id="f4852-109">次の例では、 `myTestSkipCol2.dat`というサンプル データ ファイルを使用します。対応するテーブルには列が 3 つありますが、このファイルにはフィールドが 2 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="f4852-109">The following examples use a sample data file, `myTestSkipCol2.dat`, which contains only two fields, although the corresponding table contains three columns:</span></span>

```
1,DataForColumn3
1,DataForColumn3
1,DataForColumn3

```

 <span data-ttu-id="f4852-110">`myTestSkipCol2.dat` から `myTestSkipCol` テーブルにデータを一括インポートするには、フォーマット ファイルで最初のデータ フィールドを `Col1`にマップし、 `Col3`をスキップして 2 番目のフィールドを `Col2`にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-110">To bulk import data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col1`, the second field to `Col3`, skipping `Col2`.</span></span>

## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="f4852-111">XML 以外のフォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="f4852-111">Using a Non-XML Format File</span></span>
 <span data-ttu-id="f4852-112">XML 以外のフォーマット ファイルを変更して、テーブル列をスキップすることができます。</span><span class="sxs-lookup"><span data-stu-id="f4852-112">You can modify a non-XML format file to skip a table column.</span></span> <span data-ttu-id="f4852-113">通常、この作業は、 **bcp** ユーティリティを使用して XML 以外の既定のフォーマット ファイルを作成して、その既定のファイルをテキスト エディターで変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-113">Typically, this involves using the **bcp** utility to create a default non-XML format file and the modifying the default file in a text editor.</span></span> <span data-ttu-id="f4852-114">変更後のフォーマット ファイルでは、既存の各フィールドを対応するテーブル列にマップし、スキップする列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-114">The modified format file must map each existing fields to its corresponding table column and indicate which table column or columns to skip.</span></span> <span data-ttu-id="f4852-115">XML 以外の既定のデータ ファイルを変更するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-115">Two alternatives exist for modifying a default non-XML data file.</span></span> <span data-ttu-id="f4852-116">どちらの方法も、データ ファイルにデータ フィールドが存在しないこと、および対応するテーブル列にデータが挿入されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f4852-116">Either alternative indicates that the data field does not exist in the data file and that no data will be inserted into the corresponding table column.</span></span>

### <a name="creating-a-default-non-xml-format-file"></a><span data-ttu-id="f4852-117">XML 以外の既定のフォーマット ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="f4852-117">Creating a Default Non-XML Format File</span></span>
 <span data-ttu-id="f4852-118">ここでは、以下の `myTestSkipCol` bcp **コマンドで** サンプル テーブル用に作成した、XML 以外の既定のフォーマット ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4852-118">This topic uses the default non-XML format file that was created for the `myTestSkipCol` sample table by using the following **bcp** command:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.fmt -c -T
```

 <span data-ttu-id="f4852-119">上記のコマンドでは、 `myTestSkipCol_Default.fmt`という XML 以外のフォーマット ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4852-119">The previous command creates a non-XML format file, `myTestSkipCol_Default.fmt`.</span></span> <span data-ttu-id="f4852-120">このフォーマット ファイルは *bcp* で作成した形式なので、 **既定のフォーマット ファイル**といいます。</span><span class="sxs-lookup"><span data-stu-id="f4852-120">This format file is called a *default format file* because it is the form generated by **bcp**.</span></span> <span data-ttu-id="f4852-121">既定のフォーマット ファイルには通常、データ ファイル フィールドとテーブル列の一対一の対応が記述されます。</span><span class="sxs-lookup"><span data-stu-id="f4852-121">Typically, a default format file describes a one-to-one correspondence between data-file fields and table columns.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="f4852-122">場合によっては、接続先サーバー インスタンスの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-122">You might have to specify the name of the server instance to which you are connecting.</span></span> <span data-ttu-id="f4852-123">また、ユーザー名とパスワードの指定が必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f4852-123">Also, you might have to specify the user name and password.</span></span> <span data-ttu-id="f4852-124">詳細については、「 [bcp Utility](../../tools/bcp-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4852-124">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>

 <span data-ttu-id="f4852-125">次の図に、この既定のフォーマット ファイルのサンプルで使用されている値を示します。</span><span class="sxs-lookup"><span data-stu-id="f4852-125">The following illustration shows the values in this sample default format files.</span></span> <span data-ttu-id="f4852-126">図には、各フォーマット ファイル フィールドの名前も示しています。</span><span class="sxs-lookup"><span data-stu-id="f4852-126">The illustration also shows the name of each format-file field.</span></span>

 <span data-ttu-id="f4852-127">![myTestSkipCol 用の既定の非 XML 形式ファイル](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "myTestSkipCol 用の既定の非 XML 形式ファイル")</span><span class="sxs-lookup"><span data-stu-id="f4852-127">![default non-XML format file for myTestSkipCol](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "default non-XML format file for myTestSkipCol")</span></span>

> [!NOTE]
>  <span data-ttu-id="f4852-128">フォーマット ファイル フィールドの詳細については、「[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4852-128">For more information about the format-file fields, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="methods-for-modifying-a-non-xml-format-file"></a><span data-ttu-id="f4852-129">XML 以外のフォーマット ファイルを変更する方法</span><span class="sxs-lookup"><span data-stu-id="f4852-129">Methods for Modifying a Non-XML Format File</span></span>
 <span data-ttu-id="f4852-130">テーブル列をスキップするには、既定の XML 以外のフォーマット ファイルを編集し、そのファイルを以下のいずれかの方法で変更します。</span><span class="sxs-lookup"><span data-stu-id="f4852-130">To skip a table column, edit the default non-XML format file and modify the file by using one of the following alternative methods:</span></span>

-   <span data-ttu-id="f4852-131">推奨されている方法には、3 つの基本的な手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4852-131">The preferred method involves three basic steps.</span></span> <span data-ttu-id="f4852-132">まず、データ ファイルに存在しないフィールドを記述しているフォーマット ファイルの行をすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="f4852-132">First, delete any format-file row that describes a field that is missing from the data file.</span></span> <span data-ttu-id="f4852-133">次に、削除したフォーマット ファイルの行に続く各行の "ホスト ファイル フィールドの順序" の値を減らします。</span><span class="sxs-lookup"><span data-stu-id="f4852-133">Then, reduce the "Host file field order" value of each format-file row that follows a deleted row.</span></span> <span data-ttu-id="f4852-134">"ホスト ファイル フィールドの順序" の値が、データ ファイル内での各データ フィールドの実際の場所を反映した 1 ～ *n*の通し番号になるようにします。</span><span class="sxs-lookup"><span data-stu-id="f4852-134">The goal is sequential "Host file field order" values, 1 through *n*, that reflect the actual position of each data field in the data file.</span></span> <span data-ttu-id="f4852-135">最後に、データ ファイル内の実際のフィールド数が反映されるように、"列の数" フィールドの値を減らします。</span><span class="sxs-lookup"><span data-stu-id="f4852-135">Finally, reduce the value in the "Number of columns" field to reflect the actual number of fields in the data file.</span></span>

     <span data-ttu-id="f4852-136">次の例は、このトピックの「XML 以外の既定のフォーマット ファイルの作成」で既に作成した `myTestSkipCol` テーブルの既定のフォーマット ファイルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="f4852-136">The following example is based on the default format file for the `myTestSkipCol` table, which is created in "Creating a Default Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="f4852-137">変更後のフォーマット ファイルは、最初のデータ フィールドを `Col1`にマップし、 `Col2`をスキップして、2 番目のデータ フィールドを `Col3`にマップしています。</span><span class="sxs-lookup"><span data-stu-id="f4852-137">This modified format file maps the first data field to `Col1`, skips `Col2`, and maps the second data field to `Col3`.</span></span> <span data-ttu-id="f4852-138">`Col2` に相当する行は削除されています。</span><span class="sxs-lookup"><span data-stu-id="f4852-138">The row for `Col2` has been deleted.</span></span> <span data-ttu-id="f4852-139">他の変更点は太字で示してあります。</span><span class="sxs-lookup"><span data-stu-id="f4852-139">Other modifications are indicated in bold:</span></span>

    ```
    9.0
    2
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

-   <span data-ttu-id="f4852-140">スキップするテーブル列に対応するフォーマット ファイルの行の定義を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="f4852-140">Alternatively, to skip a table column, you can modify the definition of the format-file row that corresponds to the table column.</span></span> <span data-ttu-id="f4852-141">変更するフォーマット ファイルの行は、"プレフィックス長"、"ホスト ファイルのデータ長"、および "サーバーの列の順序" の値を 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-141">In this format-file row, the "prefix length," "host file data length," and "server column order" values must be set to 0.</span></span> <span data-ttu-id="f4852-142">さらに、"ターミネータ" および "列の照合順序" のフィールド値を "" (NULL) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-142">Also, the "terminator" and "column collation" fields must be set to "" (NULL).</span></span>

     <span data-ttu-id="f4852-143">"サーバーの列名" の値は、実際の列名が不要な場合でも、空でない文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-143">The "server column name" value requires a nonblank string, though the actual column name is not necessary.</span></span> <span data-ttu-id="f4852-144">残りのフォーマット フィールドは既定値のままにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-144">The remaining format fields require their default values.</span></span>

     <span data-ttu-id="f4852-145">次の例も、 `myTestSkipCol` テーブルの既定のフォーマット ファイルから作成しました。</span><span class="sxs-lookup"><span data-stu-id="f4852-145">The following example is also derived from the default format file for the `myTestSkipCol` table.</span></span> <span data-ttu-id="f4852-146">0 または NULL にする必要がある値を太字で示してあります。</span><span class="sxs-lookup"><span data-stu-id="f4852-146">Values that must be 0 or NULL are indicated in bold.</span></span>

    ```
    9.0
    3
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       00""0     Col2         ""
    3       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

### <a name="examples"></a><span data-ttu-id="f4852-147">例</span><span class="sxs-lookup"><span data-stu-id="f4852-147">Examples</span></span>
 <span data-ttu-id="f4852-148">以下の例は、このトピックの「サンプル テーブルとデータ ファイル」で既に作成した `myTestSkipCol` サンプル テーブルおよび `myTestSkipCol2.dat` サンプル データ ファイルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="f4852-148">The following examples are also based on the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span>

#### <a name="using-bulk-insert"></a><span data-ttu-id="f4852-149">BULK INSERT の使用</span><span class="sxs-lookup"><span data-stu-id="f4852-149">Using BULK INSERT</span></span>
 <span data-ttu-id="f4852-150">次の例を動作させるには、このトピックの「XML 以外のフォーマット ファイルを変更する方法」で既に作成した、変更後の XML 以外のフォーマット ファイルの 1 つを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4852-150">This example works by using either of the modified non-XML format files created in "Methods for Modifying a Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="f4852-151">この例では、変更後のフォーマット ファイルの名前を `C:\myTestSkipCol2.fmt`とします。</span><span class="sxs-lookup"><span data-stu-id="f4852-151">In this example, the modified format file is named `C:\myTestSkipCol2.fmt`.</span></span> <span data-ttu-id="f4852-152">`BULK INSERT` を使用して `myTestSkipCol2.dat` データ ファイルを一括インポートするには、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のクエリ エディターで次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="f4852-152">To use `BULK INSERT` to bulk import the `myTestSkipCol2.dat` data file, in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
BULK INSERT myTestSkipCol 
   FROM 'C:\myTestSkipCol2.dat' 
   WITH (FORMATFILE = 'C:\myTestSkipCol2.fmt');
GO
SELECT * FROM myTestSkipCol;
GO
```

## <a name="using-an-xml-format-file"></a><span data-ttu-id="f4852-153">XML フォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="f4852-153">Using an XML Format File</span></span>
 <span data-ttu-id="f4852-154">XML フォーマット ファイルでは、 **bcp** コマンドまたは BULK INSERT ステートメントを使用して直接テーブルにインポートする場合は、列をスキップできません。</span><span class="sxs-lookup"><span data-stu-id="f4852-154">With an XML format file, you cannot skip a column when you are importing directly into a table by using a **bcp** command or a BULK INSERT statement.</span></span> <span data-ttu-id="f4852-155">ただし、テーブルの最後の列を除くすべての列にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="f4852-155">However, you can import into all but the last column of a table.</span></span> <span data-ttu-id="f4852-156">最後の列を除く特定の列をスキップする必要がある場合、データ ファイルに含まれている列のみを含んでいる対象テーブルのビューを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-156">If you have to skip any but the last column, you must create a view of the target table that contains only the columns contained in the data file.</span></span> <span data-ttu-id="f4852-157">その後、データ ファイルからビューにデータを一括インポートできます。</span><span class="sxs-lookup"><span data-stu-id="f4852-157">Then, you can bulk import data from that file into the view.</span></span>

 <span data-ttu-id="f4852-158">OPENROWSET(BULK...) を使用してテーブル列をスキップするために XML フォーマット ファイルを使用するには、次のように選択リストおよび対象テーブルの列リストを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4852-158">To use an XML format file to skip a table column by using OPENROWSET(BULK...), you have to provide explicit list of columns in the select list and also in the target table, as follows:</span></span>

 <span data-ttu-id="f4852-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="f4852-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span></span>

### <a name="creating-a-default-xml-format-file"></a><span data-ttu-id="f4852-160">既定の XML フォーマット ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="f4852-160">Creating a Default XML Format File</span></span>
 <span data-ttu-id="f4852-161">変換後のフォーマット ファイルの例は、このトピックの「サンプル テーブルとデータ ファイル」で既に作成した `myTestSkipCol` サンプル テーブルおよびデータ ファイルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="f4852-161">The examples of modified format files are based on the `myTestSkipCol` sample table and data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="f4852-162">次の **bcp** コマンドを実行すると、 `myTestSkipCol` テーブルの既定の XML フォーマット ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f4852-162">The following **bcp** command creates a default XML format file for the `myTestSkipCol` table:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.xml -c -x -T
```

 <span data-ttu-id="f4852-163">作成される既定の XML フォーマット ファイルには、次に示すように、データ ファイル フィールドとテーブル列の一対一の対応が記述されます。</span><span class="sxs-lookup"><span data-stu-id="f4852-163">The resulting default non-XML format file describes a one-to-one correspondence between data-file fields and table columns, as follows:</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

> [!NOTE]
>  <span data-ttu-id="f4852-164">XML フォーマット ファイルの構造については、「[XML フォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4852-164">For information about the structure of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="examples"></a><span data-ttu-id="f4852-165">例</span><span class="sxs-lookup"><span data-stu-id="f4852-165">Examples</span></span>
 <span data-ttu-id="f4852-166">ここに記載している例は、このトピックの「サンプル テーブルとデータ ファイル」で既に作成した `myTestSkipCol` サンプル テーブルおよび `myTestSkipCol2.dat` サンプル データ ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4852-166">The examples in this section use the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="f4852-167">`myTestSkipCol2.dat` から `myTestSkipCol` テーブルにデータをインポートするため、変更した XML フォーマット ファイル `myTestSkipCol2-x.xml`を使用します。</span><span class="sxs-lookup"><span data-stu-id="f4852-167">To import the data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the examples use the following modified XML format file, `myTestSkipCol2-x.xml`.</span></span> <span data-ttu-id="f4852-168">このファイルは、このトピックの「既定の XML フォーマット ファイルの作成」で既に作成したフォーマット ファイルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="f4852-168">This is based on the format file that is created in "Creating a Default XML Format File," earlier in this topic.</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

#### <a name="using-openrowsetbulk"></a><span data-ttu-id="f4852-169">OPENROWSET(BULK...) の使用</span><span class="sxs-lookup"><span data-stu-id="f4852-169">Using OPENROWSET(BULK...)</span></span>
 <span data-ttu-id="f4852-170">次の例では、 `OPENROWSET` 一括行セット プロバイダーと `myTestSkipCol2.xml` フォーマット ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4852-170">The following example uses the `OPENROWSET` bulk rowset provider and the `myTestSkipCol2.xml` format file.</span></span> <span data-ttu-id="f4852-171">この例では、 `myTestSkipCol2.dat` データ ファイルを `myTestSkipCol` テーブルに一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="f4852-171">The example bulk imports the `myTestSkipCol2.dat` data file into the `myTestSkipCol` table.</span></span> <span data-ttu-id="f4852-172">必要に応じて、ステートメントでは、選択リストおよびターゲット テーブルの列の一覧を明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="f4852-172">The statement contains an explicit list of columns in the select list and also in the target table, as required.</span></span>

 <span data-ttu-id="f4852-173">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のクエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="f4852-173">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'  
       ) as t1 ;
GO
```

#### <a name="using-bulk-import-on-a-view"></a><span data-ttu-id="f4852-174">ビューに対する BULK IMPORT の使用</span><span class="sxs-lookup"><span data-stu-id="f4852-174">Using BULK IMPORT on a View</span></span>
 <span data-ttu-id="f4852-175">次の例では、 `v_myTestSkipCol` テーブルに `myTestSkipCol` ビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4852-175">The following example creates the `v_myTestSkipCol` on the `myTestSkipCol` table.</span></span> <span data-ttu-id="f4852-176">このビューでは 2 番目のテーブル列である `Col2`がスキップされます。</span><span class="sxs-lookup"><span data-stu-id="f4852-176">This view skips the second table column, `Col2`.</span></span> <span data-ttu-id="f4852-177">その後、 `BULK INSERT` を使用して `myTestSkipCol2.dat` データ ファイルをこのビューにインポートします。</span><span class="sxs-lookup"><span data-stu-id="f4852-177">The example then uses `BULK INSERT` to import the `myTestSkipCol2.dat` data file into this view.</span></span>

 <span data-ttu-id="f4852-178">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のクエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="f4852-178">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
CREATE VIEW v_myTestSkipCol AS
    SELECT Col1,Col3
    FROM myTestSkipCol;
GO

USE AdventureWorks2012;
GO
BULK INSERT v_myTestSkipCol
FROM 'C:\myTestSkipCol2.dat'
WITH (FORMATFILE='C:\myTestSkipCol2.xml');
GO
```

## <a name="see-also"></a><span data-ttu-id="f4852-179">参照</span><span class="sxs-lookup"><span data-stu-id="f4852-179">See Also</span></span>
 <span data-ttu-id="f4852-180">[Bcp ユーティリティ](../../tools/bcp-utility.md) [BULK INSERT &#40;sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;Transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql)フォーマットファイルを使用して[データフィールドをスキップ](use-a-format-file-to-skip-a-data-field-sql-server.md)&#40;SQL Server&#41;フォーマットファイルを使用して[テーブル列をデータファイルフィールドにマップ](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)&#40;SQL Server&#41;フォーマットファイルを使用して[データを一括インポートする](use-a-format-file-to-bulk-import-data-sql-server.md)&#40;SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4852-180">[bcp Utility](../../tools/bcp-utility.md) [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md) [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md) [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)</span></span>


