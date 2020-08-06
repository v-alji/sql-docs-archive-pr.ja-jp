---
title: 列セットの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, column sets
- column sets
ms.assetid: a4f9de95-dc8f-4ad8-b957-137e32bfa500
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9cb496137c3986b78a55862e434c153d354a42ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645471"
---
# <a name="use-column-sets"></a><span data-ttu-id="f2191-102">列セットの使用</span><span class="sxs-lookup"><span data-stu-id="f2191-102">Use Column Sets</span></span>
  <span data-ttu-id="f2191-103">スパース列を使用するテーブルでは、テーブル内のすべてのスパース列を返すための列セットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f2191-103">Tables that use sparse columns can designate a column set to return all sparse columns in the table.</span></span> <span data-ttu-id="f2191-104">列セットは、型指定されていない XML 表記であり、テーブルのすべてのスパース列を 1 つにまとめて構造化した出力です。</span><span class="sxs-lookup"><span data-stu-id="f2191-104">A column set is an untyped XML representation that combines all the sparse columns of a table into a structured output.</span></span> <span data-ttu-id="f2191-105">列セットは、テーブルに物理的に保存されないという点で計算列に似ています。</span><span class="sxs-lookup"><span data-stu-id="f2191-105">A column set is like a calculated column in that the column set is not physically stored in the table.</span></span> <span data-ttu-id="f2191-106">計算列と異なるのは、列セットが直接更新できる点です。</span><span class="sxs-lookup"><span data-stu-id="f2191-106">A column set differs from a calculated column in that the column set is directly updatable.</span></span>  
  
 <span data-ttu-id="f2191-107">テーブルに多数の列があり、その個別操作が煩雑である場合は、列セットの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f2191-107">You should consider using column sets when the number of columns in a table is large, and operating on them individually is cumbersome.</span></span> <span data-ttu-id="f2191-108">多数の列を含むテーブルで列セットを使用してデータの選択や挿入を行うと、アプリケーションのパフォーマンスがある程度向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f2191-108">Applications might see some performance improvement when they select and insert data by using column sets on tables that have lots of columns.</span></span> <span data-ttu-id="f2191-109">ただし、テーブル内の列に多数のインデックスが定義されている場合は、列セットのパフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="f2191-109">However, the performance of column sets can be reduced when many indexes are defined on the columns in the table.</span></span> <span data-ttu-id="f2191-110">これは、実行プランに必要なメモリ容量が増えるためです。</span><span class="sxs-lookup"><span data-stu-id="f2191-110">This is because the amount of memory that is required for an execution plan increases.</span></span>  
  
 <span data-ttu-id="f2191-111">列セットを定義するには、[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) または [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ステートメントで *<column_set_name>* FOR ALL_SPARSE_COLUMNS キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2191-111">To define a column set, use the *<column_set_name>* FOR ALL_SPARSE_COLUMNS keywords in the[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
## <a name="guidelines-for-using-column-sets"></a><span data-ttu-id="f2191-112">列セットの使用に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="f2191-112">Guidelines for Using Column Sets</span></span>  
 <span data-ttu-id="f2191-113">列セットを使用する場合は、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="f2191-113">When you use column sets, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="f2191-114">スパース列と列セットは、同じステートメントの一部として追加できます。</span><span class="sxs-lookup"><span data-stu-id="f2191-114">Sparse columns and a column set can be added as part of the same statement.</span></span>  
  
-   <span data-ttu-id="f2191-115">列セットは変更できません。</span><span class="sxs-lookup"><span data-stu-id="f2191-115">The column set cannot be changed.</span></span> <span data-ttu-id="f2191-116">列セットを変更するには、列セットを削除してから再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2191-116">To change a column set, you must delete and re-create the column set.</span></span>  
  
-   <span data-ttu-id="f2191-117">既にスパース列が含まれているテーブルには列セットを追加できません。</span><span class="sxs-lookup"><span data-stu-id="f2191-117">A column set cannot be added to a table if that table already contains sparse columns.</span></span>  
  
-   <span data-ttu-id="f2191-118">スパース列を含んでいないテーブルには列セットを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f2191-118">A column set can be added to a table that does not include any sparse columns.</span></span> <span data-ttu-id="f2191-119">テーブルに後からスパース列が追加された場合は、列セット内に配置されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-119">If sparse columns are later added to the table, they will appear in the column set.</span></span>  
  
-   <span data-ttu-id="f2191-120">1 つのテーブルに作成できる列セットは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="f2191-120">Only one column set is allowed per table.</span></span>  
  
-   <span data-ttu-id="f2191-121">列セットはオプションであり、スパース列を使用するために必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="f2191-121">A column set is optional and is not required to use sparse columns.</span></span>  
  
-   <span data-ttu-id="f2191-122">列セットには制約や既定値を定義できません。</span><span class="sxs-lookup"><span data-stu-id="f2191-122">Constraints or default values cannot be defined on a column set.</span></span>  
  
-   <span data-ttu-id="f2191-123">計算列に列セットの列を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="f2191-123">Computed columns cannot contain column set columns.</span></span>  
  
-   <span data-ttu-id="f2191-124">列セットを含むテーブルでは、分散クエリがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f2191-124">Distributed queries are not supported on tables that contain column sets.</span></span>  
  
-   <span data-ttu-id="f2191-125">レプリケーションでは列セットはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f2191-125">Replication does not support column sets.</span></span>  
  
-   <span data-ttu-id="f2191-126">変更データ キャプチャでは列セットはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f2191-126">Change data capture does not support column sets.</span></span>  
  
-   <span data-ttu-id="f2191-127">列セットは、どの種類のインデックスにも組み込むことができません。</span><span class="sxs-lookup"><span data-stu-id="f2191-127">A column set cannot be part of any kind of index.</span></span> <span data-ttu-id="f2191-128">これには、XML インデックス、フルテキスト インデックス、およびインデックス付きビューが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f2191-128">This includes XML indexes, full-text indexes, and indexed views.</span></span> <span data-ttu-id="f2191-129">列セットをインデックスの付加列として追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="f2191-129">A column set cannot be added as an included column in any index.</span></span>  
  
-   <span data-ttu-id="f2191-130">フィルター選択されたインデックスまたはフィルター選択された統計情報のフィルター式では、列セットを使用できません。</span><span class="sxs-lookup"><span data-stu-id="f2191-130">A column set cannot be used in the filter expression of a filtered index or filtered statistics.</span></span>  
  
-   <span data-ttu-id="f2191-131">ビューに含まれている列セットは、そのビューで XML 列として表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-131">When a view includes a column set, the column set appears in the view as an XML column.</span></span>  
  
-   <span data-ttu-id="f2191-132">インデックス付きビューの定義に列セットを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="f2191-132">A column set cannot be included in an indexed view definition.</span></span>  
  
-   <span data-ttu-id="f2191-133">列セットを含むテーブルを含んでいるパーティション ビューは、そのビューでスパース列が名前で指定されている場合に更新できます。</span><span class="sxs-lookup"><span data-stu-id="f2191-133">Partitioned views that include tables that contain column sets are updatable when the partitioned view specifies the sparse columns by name.</span></span> <span data-ttu-id="f2191-134">列セットを参照しているパーティション ビューは更新できません。</span><span class="sxs-lookup"><span data-stu-id="f2191-134">A partitioned view is not updatable when it references the column set.</span></span>  
  
-   <span data-ttu-id="f2191-135">列セットを参照するクエリ通知は許可されません。</span><span class="sxs-lookup"><span data-stu-id="f2191-135">Query notifications that refer to column sets are not permitted.</span></span>  
  
-   <span data-ttu-id="f2191-136">XML データのサイズは 2 GB に制限されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-136">XML data has a size limit of 2 GB.</span></span> <span data-ttu-id="f2191-137">行内の NULL ではないすべてのスパース列のデータの合計がこの制限を超えると、クエリまたは DML 操作でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f2191-137">If the combined data of all the nonnull sparse columns in a row exceeds this limit, the query or DML operation will produce an error.</span></span>  
  
-   <span data-ttu-id="f2191-138">COLUMNS_UPDATED 関数から返されるデータの詳細については、「 [スパース列の使用](use-sparse-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2191-138">For information about the data that is returned by the COLUMNS_UPDATED function, see [Use Sparse Columns](use-sparse-columns.md).</span></span>  
  
## <a name="guidelines-for-selecting-data-from-a-column-set"></a><span data-ttu-id="f2191-139">列セットからのデータの選択に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="f2191-139">Guidelines for Selecting Data from a Column Set</span></span>  
 <span data-ttu-id="f2191-140">列セットからデータを選択する場合は、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="f2191-140">Consider the following guidelines for selecting data from a column set:</span></span>  
  
-   <span data-ttu-id="f2191-141">列セットは、概念的には更新可能な XML 計算列の一種であり、基になる一連のリレーショナル列を単一の XML 表記に集約します。</span><span class="sxs-lookup"><span data-stu-id="f2191-141">Conceptually, a column set is a type of updatable, computed XML column that aggregates a set of underlying relational columns into a single XML representation.</span></span> <span data-ttu-id="f2191-142">列セットは、ALL_SPARSE_COLUMNS プロパティのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f2191-142">The column set only supports the ALL_SPARSE_COLUMNS property.</span></span> <span data-ttu-id="f2191-143">このプロパティは、特定の行のすべてのスパース列から NULL 以外の値を集計するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-143">This property is used to aggregate all nonnull values from all sparse columns for a particular row.</span></span>  
  
-   <span data-ttu-id="f2191-144">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] テーブル エディターでは、列セットは編集可能な XML フィールドとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-144">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] table editor, column sets are displayed as an editable XML field.</span></span> <span data-ttu-id="f2191-145">列セットは次の形式で定義します。</span><span class="sxs-lookup"><span data-stu-id="f2191-145">Define column sets in the format:</span></span>  
  
    ```  
    <column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...  
    ```  
  
     <span data-ttu-id="f2191-146">列セットの値の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f2191-146">Examples of column set values are as follows:</span></span>  
  
    -   `<sparseProp1>10</sparseProp1><sparseProp3>20</sparseProp3>`  
  
    -   `<DocTitle>Bicycle Parts List</DocTitle><Region>West</Region>`  
  
-   <span data-ttu-id="f2191-147">NULL 値が格納されたスパース列は、列セットの XML 表記で省略されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-147">Sparse columns that contain null values are omitted from the XML representation for the column set.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="f2191-148">列セットを追加すると、SELECT \* クエリの動作が変わります。</span><span class="sxs-lookup"><span data-stu-id="f2191-148">Adding a column set changes the behavior of SELECT \* queries.</span></span> <span data-ttu-id="f2191-149">クエリから列セットが XML 列として返されるようになり、個々のスパース列は返されなくなります。</span><span class="sxs-lookup"><span data-stu-id="f2191-149">The query will return the column set as an XML column and not return the individual sparse columns.</span></span> <span data-ttu-id="f2191-150">スキーマ設計者とソフトウェア開発者は、既存のアプリケーションが動作不能とならないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2191-150">Schema designers and software developers must be careful not to break existing applications.</span></span>  
  
## <a name="inserting-or-modifying-data-in-a-column-set"></a><span data-ttu-id="f2191-151">列セットのデータの挿入または変更</span><span class="sxs-lookup"><span data-stu-id="f2191-151">Inserting or Modifying Data in a Column Set</span></span>  
 <span data-ttu-id="f2191-152">スパース列のデータ操作を実行するには、個々の列の名前を使用するか、または列セットの名前を参照し、列セットの XML 形式を使用して列セットの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2191-152">Data manipulation of a sparse column can be performed by using the name of the individual columns, or by referencing the name of the column set and specifying the values of the column set by using the XML format of the column set.</span></span> <span data-ttu-id="f2191-153">XML 列では、スパース列を任意の順序で配置できます。</span><span class="sxs-lookup"><span data-stu-id="f2191-153">Sparse columns can appear in any order in the XML column.</span></span>  
  
 <span data-ttu-id="f2191-154">XML 列セットを使用してスパース列の値を挿入または更新すると、基になるスパース列に挿入された値が `xml` データ型から暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-154">When sparse column values are inserted or updated by using the XML column set, the values that are inserted into the underlying sparse columns are implicitly converted from the `xml` data type.</span></span> <span data-ttu-id="f2191-155">数値列の場合、数値列の XML に含まれる空白値は空白の文字列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-155">In the case of numeric columns, a blank value in the XML for the numeric column converts to an empty string.</span></span> <span data-ttu-id="f2191-156">これにより、次の例のように、数値列にゼロが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-156">This causes a zero to be inserted into the numeric column as shown in the following example.</span></span>  
  
```  
CREATE TABLE t (i int SPARSE, cs xml column_set FOR ALL_SPARSE_COLUMNS);  
GO  
INSERT t(cs) VALUES ('<i/>');  
GO  
SELECT i FROM t;  
GO  
```  
  
 <span data-ttu-id="f2191-157">この例では、 `i`列に値が指定されていませんが、値 `0` が挿入されています。</span><span class="sxs-lookup"><span data-stu-id="f2191-157">In this example, no value was specified for the column `i`, but the value `0` was inserted.</span></span>  
  
## <a name="using-the-sql_variant-data-type"></a><span data-ttu-id="f2191-158">sql_variant データ型の使用</span><span class="sxs-lookup"><span data-stu-id="f2191-158">Using the sql_variant Data Type</span></span>  
 <span data-ttu-id="f2191-159">`sql_variant` データ型には、`int`、`char`、`date` などの種類の異なる複数のデータ型を格納できます。</span><span class="sxs-lookup"><span data-stu-id="f2191-159">The `sql_variant` date type can store multiple different data types, such as `int`, `char`, and `date`.</span></span> <span data-ttu-id="f2191-160">列セットは、`sql_variant` 値に関連付けられている小数点以下桁数、有効桁数、ロケール情報などのデータ型情報を、生成された XML 列に属性として出力します。</span><span class="sxs-lookup"><span data-stu-id="f2191-160">Column sets output the data type information such as scale, precision, and locale information that is associated with a `sql_variant` value as attributes in the generated XML column.</span></span> <span data-ttu-id="f2191-161">これらの属性を、列セットでの挿入または更新操作の入力としてカスタム生成 XML ステートメントで指定しようとすると、一部の属性が必須となり、一部の属性に既定値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f2191-161">If you try to provide these attributes in a custom-generated XML statement as an input for an insert or update operation on a column set, some of these attributes are required and some of them are assigned a default value.</span></span> <span data-ttu-id="f2191-162">値が指定されなかったときにサーバーで生成されるデータ型と既定値の一覧を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f2191-162">The following table lists the data types and the default values that the server generates when the value is not provided.</span></span>  
  
|<span data-ttu-id="f2191-163">データ型</span><span class="sxs-lookup"><span data-stu-id="f2191-163">Data type</span></span>|<span data-ttu-id="f2191-164">localeID\*</span><span class="sxs-lookup"><span data-stu-id="f2191-164">localeID\*</span></span>|<span data-ttu-id="f2191-165">sqlCompareOptions</span><span class="sxs-lookup"><span data-stu-id="f2191-165">sqlCompareOptions</span></span>|<span data-ttu-id="f2191-166">sqlCollationVersion</span><span class="sxs-lookup"><span data-stu-id="f2191-166">sqlCollationVersion</span></span>|<span data-ttu-id="f2191-167">SqlSortId</span><span class="sxs-lookup"><span data-stu-id="f2191-167">SqlSortId</span></span>|<span data-ttu-id="f2191-168">最大の長さ</span><span class="sxs-lookup"><span data-stu-id="f2191-168">Maximum length</span></span>|<span data-ttu-id="f2191-169">Precision</span><span class="sxs-lookup"><span data-stu-id="f2191-169">Precision</span></span>|<span data-ttu-id="f2191-170">スケール</span><span class="sxs-lookup"><span data-stu-id="f2191-170">Scale</span></span>|  
|---------------|----------------|-----------------------|-------------------------|---------------|--------------------|---------------|-----------|  
|<span data-ttu-id="f2191-171">`char`, `varchar`, `binary`</span><span class="sxs-lookup"><span data-stu-id="f2191-171">`char`, `varchar`, `binary`</span></span>|<span data-ttu-id="f2191-172">-1</span><span class="sxs-lookup"><span data-stu-id="f2191-172">-1</span></span>|<span data-ttu-id="f2191-173">'Default'</span><span class="sxs-lookup"><span data-stu-id="f2191-173">'Default'</span></span>|<span data-ttu-id="f2191-174">0</span><span class="sxs-lookup"><span data-stu-id="f2191-174">0</span></span>|<span data-ttu-id="f2191-175">0</span><span class="sxs-lookup"><span data-stu-id="f2191-175">0</span></span>|<span data-ttu-id="f2191-176">8000</span><span class="sxs-lookup"><span data-stu-id="f2191-176">8000</span></span>|<span data-ttu-id="f2191-177">なし\*\*</span><span class="sxs-lookup"><span data-stu-id="f2191-177">Not applicable\*\*</span></span>|<span data-ttu-id="f2191-178">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-178">Not applicable</span></span>|  
|`nvarchar`|<span data-ttu-id="f2191-179">-1</span><span class="sxs-lookup"><span data-stu-id="f2191-179">-1</span></span>|<span data-ttu-id="f2191-180">'Default'</span><span class="sxs-lookup"><span data-stu-id="f2191-180">'Default'</span></span>|<span data-ttu-id="f2191-181">0</span><span class="sxs-lookup"><span data-stu-id="f2191-181">0</span></span>|<span data-ttu-id="f2191-182">0</span><span class="sxs-lookup"><span data-stu-id="f2191-182">0</span></span>|<span data-ttu-id="f2191-183">4000</span><span class="sxs-lookup"><span data-stu-id="f2191-183">4000</span></span>|<span data-ttu-id="f2191-184">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-184">Not applicable</span></span>|<span data-ttu-id="f2191-185">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-185">Not applicable</span></span>|  
|<span data-ttu-id="f2191-186">`decimal`, `float`, `real`</span><span class="sxs-lookup"><span data-stu-id="f2191-186">`decimal`, `float`, `real`</span></span>|<span data-ttu-id="f2191-187">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-187">Not applicable</span></span>|<span data-ttu-id="f2191-188">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-188">Not applicable</span></span>|<span data-ttu-id="f2191-189">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-189">Not applicable</span></span>|<span data-ttu-id="f2191-190">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-190">Not applicable</span></span>|<span data-ttu-id="f2191-191">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-191">Not applicable</span></span>|<span data-ttu-id="f2191-192">18</span><span class="sxs-lookup"><span data-stu-id="f2191-192">18</span></span>|<span data-ttu-id="f2191-193">0</span><span class="sxs-lookup"><span data-stu-id="f2191-193">0</span></span>|  
|<span data-ttu-id="f2191-194">`integer`, `bigint`, `tinyint`, `smallint`</span><span class="sxs-lookup"><span data-stu-id="f2191-194">`integer`, `bigint`, `tinyint`, `smallint`</span></span>|<span data-ttu-id="f2191-195">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-195">Not applicable</span></span>|<span data-ttu-id="f2191-196">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-196">Not applicable</span></span>|<span data-ttu-id="f2191-197">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-197">Not applicable</span></span>|<span data-ttu-id="f2191-198">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-198">Not applicable</span></span>|<span data-ttu-id="f2191-199">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-199">Not applicable</span></span>|<span data-ttu-id="f2191-200">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-200">Not applicable</span></span>|<span data-ttu-id="f2191-201">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-201">Not applicable</span></span>|  
|`datetime2`|<span data-ttu-id="f2191-202">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-202">Not applicable</span></span>|<span data-ttu-id="f2191-203">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-203">Not applicable</span></span>|<span data-ttu-id="f2191-204">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-204">Not applicable</span></span>|<span data-ttu-id="f2191-205">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-205">Not applicable</span></span>|<span data-ttu-id="f2191-206">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-206">Not applicable</span></span>|<span data-ttu-id="f2191-207">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-207">Not applicable</span></span>|<span data-ttu-id="f2191-208">7</span><span class="sxs-lookup"><span data-stu-id="f2191-208">7</span></span>|  
|`datetime offset`|<span data-ttu-id="f2191-209">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-209">Not applicable</span></span>|<span data-ttu-id="f2191-210">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-210">Not applicable</span></span>|<span data-ttu-id="f2191-211">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-211">Not applicable</span></span>|<span data-ttu-id="f2191-212">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-212">Not applicable</span></span>|<span data-ttu-id="f2191-213">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-213">Not applicable</span></span>|<span data-ttu-id="f2191-214">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-214">Not applicable</span></span>|<span data-ttu-id="f2191-215">7</span><span class="sxs-lookup"><span data-stu-id="f2191-215">7</span></span>|  
|<span data-ttu-id="f2191-216">`datetime`, `date`, `smalldatetime`</span><span class="sxs-lookup"><span data-stu-id="f2191-216">`datetime`, `date`, `smalldatetime`</span></span>|<span data-ttu-id="f2191-217">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-217">Not applicable</span></span>|<span data-ttu-id="f2191-218">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-218">Not applicable</span></span>|<span data-ttu-id="f2191-219">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-219">Not applicable</span></span>|<span data-ttu-id="f2191-220">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-220">Not applicable</span></span>|<span data-ttu-id="f2191-221">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-221">Not applicable</span></span>|<span data-ttu-id="f2191-222">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-222">Not applicable</span></span>|<span data-ttu-id="f2191-223">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-223">Not applicable</span></span>|  
|<span data-ttu-id="f2191-224">`money`, `smallmoney`</span><span class="sxs-lookup"><span data-stu-id="f2191-224">`money`, `smallmoney`</span></span>|<span data-ttu-id="f2191-225">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-225">Not applicable</span></span>|<span data-ttu-id="f2191-226">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-226">Not applicable</span></span>|<span data-ttu-id="f2191-227">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-227">Not applicable</span></span>|<span data-ttu-id="f2191-228">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-228">Not applicable</span></span>|<span data-ttu-id="f2191-229">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-229">Not applicable</span></span>|<span data-ttu-id="f2191-230">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-230">Not applicable</span></span>|<span data-ttu-id="f2191-231">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-231">Not applicable</span></span>|  
|`time`|<span data-ttu-id="f2191-232">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-232">Not applicable</span></span>|<span data-ttu-id="f2191-233">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-233">Not applicable</span></span>|<span data-ttu-id="f2191-234">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-234">Not applicable</span></span>|<span data-ttu-id="f2191-235">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-235">Not applicable</span></span>|<span data-ttu-id="f2191-236">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-236">Not applicable</span></span>|<span data-ttu-id="f2191-237">適用なし</span><span class="sxs-lookup"><span data-stu-id="f2191-237">Not applicable</span></span>|<span data-ttu-id="f2191-238">7</span><span class="sxs-lookup"><span data-stu-id="f2191-238">7</span></span>|  
  
 <span data-ttu-id="f2191-239">\*  localeID -1 は既定のロケールを意味します。</span><span class="sxs-lookup"><span data-stu-id="f2191-239">\*  localeID -1 means the default locale.</span></span> <span data-ttu-id="f2191-240">英語ロケールは 1033 です。</span><span class="sxs-lookup"><span data-stu-id="f2191-240">The English locale is 1033.</span></span>  
  
 <span data-ttu-id="f2191-241">\*\*  なし = 列セットでの選択操作時に、対象の属性に対して値が出力されません。</span><span class="sxs-lookup"><span data-stu-id="f2191-241">\*\*  Not applicable = No values are output for these attributes during a select operation on the column set.</span></span> <span data-ttu-id="f2191-242">挿入または更新操作で列セットに対して指定された XML 表記で呼び出し元がこの属性に値を指定すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f2191-242">Generates an error when a value is specified for this attribute by the caller in the XML representation provided for a column set in an insert or update operation.</span></span>  
  
## <a name="security"></a><span data-ttu-id="f2191-243">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f2191-243">Security</span></span>  
 <span data-ttu-id="f2191-244">列セットのセキュリティ モデルは、テーブルと列の間に介在するセキュリティ モデルと同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="f2191-244">The security model for a column set works similar to the security model that exists between table and columns.</span></span> <span data-ttu-id="f2191-245">列セットはミニテーブルとして視覚化できます。選択操作は、このミニテーブルに対する SELECT \* 操作と同様です。</span><span class="sxs-lookup"><span data-stu-id="f2191-245">Column sets can be visualized as a minitable and a select operation is like a SELECT \* operation on this minitable.</span></span> <span data-ttu-id="f2191-246">ただし、列セットとスパース列は、厳密なコンテナーではなくグループ化の関係にあります。</span><span class="sxs-lookup"><span data-stu-id="f2191-246">But, the relationship between column set to sparse columns is a grouping relationship instead of strictly a container.</span></span> <span data-ttu-id="f2191-247">セキュリティ モデルでは、列セットの列に対してセキュリティがチェックされ、基になるスパース列で DENY 操作が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-247">The security model checks the security on the column set column, and honors the DENY operations on the underlying sparse columns.</span></span> <span data-ttu-id="f2191-248">セキュリティ モデルには、これ以外に次のような特性があります。</span><span class="sxs-lookup"><span data-stu-id="f2191-248">Additional characteristics of the security model are as follows:</span></span>  
  
-   <span data-ttu-id="f2191-249">列セットの列に対し、テーブル内の他の列と同様に、セキュリティ権限を与えたり取り消したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="f2191-249">Security permissions can be granted and revoked from the column set column, similar to any other column in the table.</span></span>  
  
-   <span data-ttu-id="f2191-250">列セットの列に対して SELECT、INSERT、UPDATE、DELETE、および REFERENCES 権限の GRANT または REVOKE を実行しても、そのセットの基になるメンバー列には反映されません。</span><span class="sxs-lookup"><span data-stu-id="f2191-250">A GRANT or REVOKE of SELECT, INSERT, UPDATE, DELETE, and REFERENCES permission on a column set column does not propagate to the underlying member columns of that set.</span></span> <span data-ttu-id="f2191-251">これは、列セットの列を使用する場合にのみ当てはまります。</span><span class="sxs-lookup"><span data-stu-id="f2191-251">It applies only to the usage of the column set column.</span></span> <span data-ttu-id="f2191-252">列セットに対する DENY 権限は、テーブルの基になるスパース列に反映されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-252">DENY permission on a column set does propagate to the underlying sparse columns of the table.</span></span>  
  
-   <span data-ttu-id="f2191-253">列セットの列に対して SELECT、INSERT、UPDATE、DELETE の各ステートメントを実行するには、ユーザーはその列セットの列についての対応する権限、およびテーブル内のすべてのスパース列についての対応する権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2191-253">Executing SELECT, INSERT, UPDATE, and DELETE statements on the column set column require that the user has corresponding permissions on the column set column, and also the corresponding permission on all the sparse columns in the table.</span></span> <span data-ttu-id="f2191-254">列セットはテーブル内のすべてのスパース列を表すため、すべてのスパース列についての権限が必要になります。これには、変更の対象ではないスパース列も含まれます。</span><span class="sxs-lookup"><span data-stu-id="f2191-254">Because the column set represents all the sparse columns in the table, you must have permission on all the sparse columns, and this includes sparse columns that you might not be changing.</span></span>  
  
-   <span data-ttu-id="f2191-255">スパース列または列セットに対して REVOKE ステートメントを実行すると、セキュリティは、既定でその親オブジェクトのセキュリティに設定されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-255">Executing a REVOKE statement on a sparse column or column set defaults the security to their parent object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f2191-256">例</span><span class="sxs-lookup"><span data-stu-id="f2191-256">Examples</span></span>  
 <span data-ttu-id="f2191-257">次の例では、ドキュメント テーブルに `DocID` 列と `Title`列のセットが共通で含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2191-257">In the following examples, a document table contains the common set of columns `DocID` and `Title`.</span></span> <span data-ttu-id="f2191-258">製造グループは、すべての製造ドキュメントに `ProductionSpecification` 列と `ProductionLocation` 列を必要とします。</span><span class="sxs-lookup"><span data-stu-id="f2191-258">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="f2191-259">マーケティング グループは、マーケティング ドキュメントに `MarketingSurveyGroup` 列を必要とします。</span><span class="sxs-lookup"><span data-stu-id="f2191-259">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span>  
  
### <a name="a-creating-a-table-that-has-a-column-set"></a><span data-ttu-id="f2191-260">A.</span><span class="sxs-lookup"><span data-stu-id="f2191-260">A.</span></span> <span data-ttu-id="f2191-261">列セットを含むテーブルを作成する</span><span class="sxs-lookup"><span data-stu-id="f2191-261">Creating a table that has a column set</span></span>  
 <span data-ttu-id="f2191-262">次の例では、スパース列を使用し、列セット `SpecialPurposeColumns`を含むテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2191-262">The following example creates the table that uses sparse columns and includes the column set `SpecialPurposeColumns`.</span></span> <span data-ttu-id="f2191-263">例では、テーブルに 2 つの行を挿入した後に、テーブルからデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2191-263">The example inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2191-264">このテーブルは、簡単に表示して確認できるように、5 つの列のみで構成されています。</span><span class="sxs-lookup"><span data-stu-id="f2191-264">This table has only five columns to make it easier to display and read.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStoreWithColumnSet  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL,  
     MarketingProgramID int SPARSE NULL,  
     SpecialPurposeColumns XML COLUMN_SET FOR ALL_SPARSE_COLUMNS);  
GO  
```  
  
### <a name="b-inserting-data-to-a-table-by-using-the-names-of-the-sparse-columns"></a><span data-ttu-id="f2191-265">B.</span><span class="sxs-lookup"><span data-stu-id="f2191-265">B.</span></span> <span data-ttu-id="f2191-266">スパース列の名前を使用してテーブルにデータを挿入する</span><span class="sxs-lookup"><span data-stu-id="f2191-266">Inserting data to a table by using the names of the sparse columns</span></span>  
 <span data-ttu-id="f2191-267">次の例では、例 A で作成したテーブルに 2 つの行を挿入します。列セットは参照せず、スパース列の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="f2191-267">The following examples insert two rows into the table that is created in example A. The examples use the names of the sparse columns and do not reference the column set.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStoreWithColumnSet (DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
### <a name="c-inserting-data-to-a-table-by-using-the-name-of-the-column-set"></a><span data-ttu-id="f2191-268">C.</span><span class="sxs-lookup"><span data-stu-id="f2191-268">C.</span></span> <span data-ttu-id="f2191-269">列セットの名前を使用してテーブルにデータを挿入する</span><span class="sxs-lookup"><span data-stu-id="f2191-269">Inserting data to a table by using the name of the column set</span></span>  
 <span data-ttu-id="f2191-270">次の例では、例 A で作成したテーブルに 3 つ目の行を挿入します。今回はスパース列の名前を使用しません。</span><span class="sxs-lookup"><span data-stu-id="f2191-270">The following example inserts a third row into the table that is created in example A. This time the names of the sparse columns are not used.</span></span> <span data-ttu-id="f2191-271">代わりに、列セットの名前を使用し、挿入操作によって 4 つのスパース列の 2 つに XML 形式で値を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f2191-271">Instead, the name of the column set is used, and the insert provides the values for two of the four sparse columns in XML format.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, SpecialPurposeColumns)  
VALUES (3, 'Tire Spec 2', '<ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>');  
GO  
```  
  
### <a name="d-observing-the-results-of-a-column-set-when-select--is-used"></a><span data-ttu-id="f2191-272">D.</span><span class="sxs-lookup"><span data-stu-id="f2191-272">D.</span></span> <span data-ttu-id="f2191-273">SELECT \* を使用したときの列セットの結果を確認する</span><span class="sxs-lookup"><span data-stu-id="f2191-273">Observing the results of a column set when SELECT \* is used</span></span>  
 <span data-ttu-id="f2191-274">次の例では、列セットを含むテーブルからすべての列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f2191-274">The following example selects all the columns from the table that contains a column set.</span></span> <span data-ttu-id="f2191-275">この操作で、スパース列の値の組み合わせを含んだ XML 列が返されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-275">It returns an XML column with the combined values of the sparse columns.</span></span> <span data-ttu-id="f2191-276">スパース列が個別に返されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f2191-276">It does not return the sparse columns individually.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns FROM DocumentStoreWithColumnSet ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1      Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `2      Survey 2142  <MarketingSurveyGroup>Men 25 - 35</MarketingSurveyGroup>`  
  
 `3      Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="e-observing-the-results-of-selecting-the-column-set-by-name"></a><span data-ttu-id="f2191-277">E.</span><span class="sxs-lookup"><span data-stu-id="f2191-277">E.</span></span> <span data-ttu-id="f2191-278">列セットを名前で選択した場合の結果を確認する</span><span class="sxs-lookup"><span data-stu-id="f2191-278">Observing the results of selecting the column set by name</span></span>  
 <span data-ttu-id="f2191-279">製造部門にマーケティング データは必要ないため、この例では `WHERE` 句を追加して出力を制限します。</span><span class="sxs-lookup"><span data-stu-id="f2191-279">Because the Production department is not interested in the marketing data, this example adds a `WHERE` clause to restrict the output.</span></span> <span data-ttu-id="f2191-280">例では、列セットの名前が使用されています。</span><span class="sxs-lookup"><span data-stu-id="f2191-280">The example uses the name of the column set.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns  
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1     Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `3     Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="f-observing-the-results-of-selecting-sparse-columns-by-name"></a><span data-ttu-id="f2191-281">F.</span><span class="sxs-lookup"><span data-stu-id="f2191-281">F.</span></span> <span data-ttu-id="f2191-282">スパース列を名前で選択した場合の結果を確認する</span><span class="sxs-lookup"><span data-stu-id="f2191-282">Observing the results of selecting sparse columns by name</span></span>  
 <span data-ttu-id="f2191-283">テーブルに列セットが含まれている場合でも、次の例のように個々の列名を使用してテーブルに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f2191-283">When a table contains a column set, you can still query the table by using the individual column names as shown in the following example.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        ProductionSpecification ProductionLocation`  
  
 `1     Tire Spec 1  AXZZ217                 27`  
  
 `3     Tire Spec 2  AXW9R411                38`  
  
### <a name="g-updating-a-table-by-using-a-column-set"></a><span data-ttu-id="f2191-284">G.</span><span class="sxs-lookup"><span data-stu-id="f2191-284">G.</span></span> <span data-ttu-id="f2191-285">列セットを使用してテーブルを更新する</span><span class="sxs-lookup"><span data-stu-id="f2191-285">Updating a table by using a column set</span></span>  
 <span data-ttu-id="f2191-286">次の例では、3 番目のレコードを、その行で使用されている 2 つのスパース列の新しい値で更新します。</span><span class="sxs-lookup"><span data-stu-id="f2191-286">The following example updates the third record with new values for both sparse columns that are used by that row.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification><ProductionLocation>38</ProductionLocation>'  
WHERE DocID = 3 ;  
GO  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f2191-287">UPDATE ステートメントで列セットを使用すると、テーブル内のすべてのスパース列が更新されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-287">An UPDATE statement that uses a column set updates all the sparse columns in the table.</span></span> <span data-ttu-id="f2191-288">参照されていないスパース列は、NULL に更新されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-288">Sparse columns that are not referenced are updated to NULL.</span></span>  
  
 <span data-ttu-id="f2191-289">次の例では、3 番目のレコードを更新しますが、作成された 2 つの列の 1 つにのみ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2191-289">The following example updates the third record, but only specifies the value of one of the two populated columns.</span></span> <span data-ttu-id="f2191-290">2 番目の列である `ProductionLocation` は `UPDATE` ステートメントに含まれず、NULL に更新されます。</span><span class="sxs-lookup"><span data-stu-id="f2191-290">The second column `ProductionLocation` is not included in the `UPDATE` statement and is updated to NULL.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification>'  
WHERE DocID = 3 ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2191-291">参照</span><span class="sxs-lookup"><span data-stu-id="f2191-291">See Also</span></span>  
 [<span data-ttu-id="f2191-292">スパース列の使用</span><span class="sxs-lookup"><span data-stu-id="f2191-292">Use Sparse Columns</span></span>](use-sparse-columns.md)  
  
  
