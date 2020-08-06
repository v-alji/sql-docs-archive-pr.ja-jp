---
title: データセット フィールド コレクションの参照 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 006c6bd3-d776-4c20-9092-32e40688ac49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e4140c35f8035e3ac8fae37aefb9d7f2afcaecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644341"
---
# <a name="dataset-fields-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="4cef0-102">データセット フィールド コレクションの参照 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4cef0-102">Dataset Fields Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4cef0-103">レポート内の各データセットには、1 つのフィールド コレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-103">Each dataset in a report contains one Fields collection.</span></span> <span data-ttu-id="4cef0-104">フィールド コレクションは、データセット クエリによって指定されるフィールドと、ユーザーが作成する追加の計算フィールドのセットです。</span><span class="sxs-lookup"><span data-stu-id="4cef0-104">The Fields collection is the set of fields specified by the dataset query plus any additional calculated fields that you create.</span></span> <span data-ttu-id="4cef0-105">データセットを作成すると、フィールド コレクションが **[レポート データ]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-105">After you create a dataset, the field collection appears in the **Report Data** pane.</span></span>  
  
 <span data-ttu-id="4cef0-106">式内の単純なフィールド参照は、デザイン画面に単純な式として表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-106">A simple field reference in an expression displays on the design surface as a simple expression.</span></span> <span data-ttu-id="4cef0-107">たとえば、フィールド `Sales` をレポート データ ペインからデザイン画面のテーブル セルにドラッグすると、 `[Sales]` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-107">For example, when you drag the field `Sales` from the Report Data pane to a table cell on the design surface, `[Sales]` is displayed.</span></span> <span data-ttu-id="4cef0-108">この式は、テキスト ボックスの Value プロパティに対して設定されている基本となる式 `=Fields!Sales.Value` を表しています。</span><span class="sxs-lookup"><span data-stu-id="4cef0-108">This represents the underlying expression `=Fields!Sales.Value` that is set on the text box Value property.</span></span> <span data-ttu-id="4cef0-109">レポートが実行されると、レポート プロセッサによってこの式が評価され、テーブル セルのテキスト ボックスにデータ ソースの実際のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-109">When the report runs, the report processor evaluates this expression and displays the actual data from the data source in the text box in the table cell.</span></span> <span data-ttu-id="4cef0-110">詳細については、「[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)」および「[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cef0-110">For more, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) and [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-the-field-collection-for-a-dataset"></a><span data-ttu-id="4cef0-111">データセットのフィールド コレクションの表示</span><span class="sxs-lookup"><span data-stu-id="4cef0-111">Displaying the Field Collection for a Dataset</span></span>  
 <span data-ttu-id="4cef0-112">フィールド コレクションの個々の値を表示するには、各フィールドをテーブル詳細行にドラッグして、レポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4cef0-112">To display the individual values for a field collection, drag each field to a table detail row and run the report.</span></span> <span data-ttu-id="4cef0-113">フィールド参照がテーブル データ領域または一覧データ領域の詳細行に含まれている場合は、データセットの行ごとの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-113">References from the detail row of a table or list data region display a value for each row in the dataset.</span></span>  
  
 <span data-ttu-id="4cef0-114">フィールドの集約値を表示するには、各数値フィールドをマトリックスのデータ領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4cef0-114">To display summarized values for a field, drag each numeric field to the data area of a matrix.</span></span> <span data-ttu-id="4cef0-115">行の総数を計算する既定の集計関数は、 `=Sum(Fields!Sales.Value)`などの Sum 関数です。</span><span class="sxs-lookup"><span data-stu-id="4cef0-115">The default aggregate function for the total row is Sum, for example, `=Sum(Fields!Sales.Value)`.</span></span> <span data-ttu-id="4cef0-116">既定の関数を変更して、別の合計を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-116">You can change the default function in order to calculate different totals.</span></span> <span data-ttu-id="4cef0-117">詳細については、「 [集計関数リファレンス (レポート ビルダーおよび SSRS)](report-builder-functions-aggregate-functions-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cef0-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="4cef0-118">テキスト ボックス内のフィールド コレクションに関する集約値を (データ領域の一部ではなく) デザイン画面に直接表示するには、集計関数のスコープとしてデータセット名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-118">To display summarized values for a field collection in a text box directly on the design surface (not part of a data region), you must specify the dataset name as a scope for the aggregate function.</span></span> <span data-ttu-id="4cef0-119">たとえば、 `SalesData`という名前のデータセットの場合は、 `Sales`という式によってフィールド `=Sum(Fields!Sales,"SalesData")`のすべての値の合計が指定されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-119">For example, for a dataset named `SalesData`, the following expression specifies the total of all values for the field `Sales`: `=Sum(Fields!Sales,"SalesData")`.</span></span>  
  
 <span data-ttu-id="4cef0-120">**[式]** ダイアログ ボックスを使用して単純なフィールド参照を定義する場合は、カテゴリ ペインでフィールド コレクションを選択して、使用可能なフィールドの一覧を **フィールド** ペインに表示できます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-120">When you use the **Expression** dialog box to define a simple field reference, you can select the Fields collection in the Category pane and see the list of available fields in the **Field** pane.</span></span> <span data-ttu-id="4cef0-121">各フィールドには、Value や IsMissing などのいくつかのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-121">Each field has several properties, including Value and IsMissing.</span></span> <span data-ttu-id="4cef0-122">残りのプロパティは、データ ソースの種類によってはデータセットで使用できる場合がある、定義済みの拡張フィールド プロパティです。</span><span class="sxs-lookup"><span data-stu-id="4cef0-122">The remaining properties are predefined extended field properties that may be available to the dataset depending on the data source type.</span></span>  
  
### <a name="detecting-nulls-for-a-dataset-field"></a><span data-ttu-id="4cef0-123">値が NULL であるデータセット フィールドの検出</span><span class="sxs-lookup"><span data-stu-id="4cef0-123">Detecting Nulls for a Dataset Field</span></span>  
 <span data-ttu-id="4cef0-124">NULL ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) であるフィールド値を検出するには、関数 `IsNothing` を使用します。</span><span class="sxs-lookup"><span data-stu-id="4cef0-124">To detect a field value that is null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), you can use the function `IsNothing`.</span></span> <span data-ttu-id="4cef0-125">次の式をテーブル詳細行のテキスト ボックスに配置すると、フィールド `MiddleName` がテストされ、値が NULL の場合は "No Middle Name" という文字列、値が NULL 以外の場合はフィールド値そのもので置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-125">When placed in a text box in a table details row, the following expression tests the field `MiddleName` and substitutes the text "No Middle Name" when the value is null, and the field value itself when the value is not null:</span></span>  
  
 `=IIF(IsNothing(Fields!MiddleName.Value),"No Middle Name",Fields!MiddleName.Value)`  
  
### <a name="detecting-missing-fields-for-dynamic-queries-at-run-time"></a><span data-ttu-id="4cef0-126">実行時の動的クエリにおける存在しないフィールドの検出</span><span class="sxs-lookup"><span data-stu-id="4cef0-126">Detecting Missing Fields for Dynamic Queries at Run Time</span></span>  
 <span data-ttu-id="4cef0-127">既定では、フィールド コレクションのアイテムには、Value および IsMissing という 2 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-127">By default, items in the Fields collection have two properties: Value and IsMissing.</span></span> <span data-ttu-id="4cef0-128">IsMissing プロパティは、デザイン時にデータセットに対して定義されているフィールドが、実行時に取得されたフィールドに存在するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4cef0-128">The IsMissing property indicates whether a field that is defined for a dataset at design time is contained in the fields retrieved at run time.</span></span> <span data-ttu-id="4cef0-129">たとえば、クエリでは、入力パラメーターによって結果セットが変化するストアドプロシージャを呼び出すことができます。また、クエリでテーブル定義が変更された場合もあり `SELECT * FROM` *\<table>* ます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-129">For example, your query might call a stored procedure in which the result set varies with an input parameter, or your query might be `SELECT * FROM` *\<table>* where the table definition changed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cef0-130">IsMissing は、任意の種類のデータ ソースに関して、デザイン時と実行時の間にデータセット スキーマに加えられた変更を検出します。</span><span class="sxs-lookup"><span data-stu-id="4cef0-130">IsMissing detects changes in the dataset schema between design time and run time for any type of data source.</span></span> <span data-ttu-id="4cef0-131">IsMissing は、多次元キューブ内の空のメンバーを検出するためには使用できません `EMPTY` 。また、およびの MDX クエリ言語の概念とは関係がありません `NON EMPTY` 。</span><span class="sxs-lookup"><span data-stu-id="4cef0-131">IsMissing cannot be used to detect empty members in a multidimensional cube and is not related to the MDX query language concepts of `EMPTY` and `NON EMPTY`.</span></span>  
  
 <span data-ttu-id="4cef0-132">IsMissing プロパティをカスタム コードでテストすると、結果セットにフィールドが含まれているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-132">You can test the IsMissing property in custom code to determine if a field is present in the result set.</span></span> <span data-ttu-id="4cef0-133">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数では、関数の呼び出しに含まれているすべてのパラメーターが評価されるので、存在しないパラメーターへの参照が評価されたときにエラーが返されます。そのため、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数の呼び出しで `IIF` や `SWITCH` などの式を使用してフィールドの有無をテストすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4cef0-133">You cannot test for its presence using an expression with a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function call such as `IIF` or `SWITCH`, because [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] evaluates all parameters in the call to the function, which results in an error when the reference to the missing is evaluated.</span></span>  
  
#### <a name="example-for-controlling-the-visibility-of-a-dynamic-column-for-a-missing-field"></a><span data-ttu-id="4cef0-134">存在しないフィールド用の動的列の表示を制御する例</span><span class="sxs-lookup"><span data-stu-id="4cef0-134">Example for Controlling the Visibility of a Dynamic Column for a Missing Field</span></span>  
 <span data-ttu-id="4cef0-135">データセット内のフィールドを表示する列の表示を制御するための式を設定するには、まず、フィールドの有無に基づいてブール値を返すカスタム コード関数を定義しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-135">To set an expression that controls the visibility of a column that displays a field in a dataset, you must first define a custom code function that returns a Boolean value based on whether the field is missing.</span></span> <span data-ttu-id="4cef0-136">たとえば、次のカスタム コード関数では、フィールドが存在しない場合に true、フィールドが存在する場合に false が返されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-136">For example, the following custom code function returns true if the field is missing and false if the field exists.</span></span>  
  
```  
Public Function IsFieldMissing(field as Field) as Boolean  
 If (field.IsMissing) Then  
 Return True  
  Else   
  Return False  
 End If  
End Function  
```  
  
 <span data-ttu-id="4cef0-137">この関数を使用して列の表示を制御するには、列の Hidden プロパティを次の式に設定します。</span><span class="sxs-lookup"><span data-stu-id="4cef0-137">To use this function to control visibility of a column, set the Hidden property of the column to the following expression:</span></span>  
  
 `=Code.IsFieldMissing(Fields!FieldName)`  
  
 <span data-ttu-id="4cef0-138">フィールドが存在しない場合、列は非表示になります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-138">The column is hidden when the field does not exist.</span></span>  
  
#### <a name="example-for-controlling-the-text-box-value-for-a-missing-field"></a><span data-ttu-id="4cef0-139">存在しないフィールドのテキスト ボックス値を制御する例</span><span class="sxs-lookup"><span data-stu-id="4cef0-139">Example for Controlling the Text Box Value for a Missing Field</span></span>  
 <span data-ttu-id="4cef0-140">存在しないフィールドの値を指定文字列で置き換えるには、カスタム コードを作成して、フィールドが存在しない場合にそのフィールド値の代わりに使用できる文字列が返されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-140">To substitute text that you write in place of the value of a missing field, you must write custom code that returns text you can use in place of a field value when the field is missing.</span></span> <span data-ttu-id="4cef0-141">たとえば、次のカスタム コード関数を実行すると、フィールドが存在する場合はフィールドの値が返され、フィールドが存在しない場合は 2 番目のパラメーターとして指定したメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-141">For example, the following custom code function returns the value of the field if the field exists, and the message that you specify as the second parameter if the field does not exist:</span></span>  
  
```  
Public Function IsFieldMissingThenString(field as Field, strMessage as String) as String  
 If (field.IsMissing) Then  
  Return strMessage  
 Else   
  Return field.Value  
  End If  
End Function  
```  
  
 <span data-ttu-id="4cef0-142">この関数をテキスト ボックスで使用するには、次の式を Value プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="4cef0-142">To use this function in a text box, add the following expression to the Value property:</span></span>  
  
 `=Code.IsFieldMissingThenString(Fields!FieldName,"Missing")`  
  
 <span data-ttu-id="4cef0-143">テキスト ボックスには、フィールド値または指定した文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-143">The text box displays either the field value or the text that you specified.</span></span>  
  
### <a name="using-extended-field-properties"></a><span data-ttu-id="4cef0-144">拡張フィールド プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="4cef0-144">Using Extended Field Properties</span></span>  
 <span data-ttu-id="4cef0-145">拡張フィールド プロパティは、データ処理拡張機能によってフィールドに定義された追加プロパティであり、データセットのデータ ソースの種類に基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-145">Extended field properties are additional properties defined on a field by the data processing extension, which is determined by the data source type for the dataset.</span></span> <span data-ttu-id="4cef0-146">拡張フィールド プロパティには、定義済みのものと、データ ソースの種類に固有のものがあります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-146">Extended field properties are predefined or specific to a data source type.</span></span> <span data-ttu-id="4cef0-147">詳細については、「[Analysis Services データベースに対する拡張フィールド プロパティ &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cef0-147">For more information, see [Extended Field Properties for an Analysis Services Database &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md).</span></span>  
  
 <span data-ttu-id="4cef0-148">そのフィールドでサポートされていないプロパティを指定した場合、式は `null` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4cef0-148">If you specify a property that is not supported for that field, the expression evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="4cef0-149">データ プロバイダーが拡張フィールド プロパティをサポートしていない場合や、クエリ実行時にフィールドが見つからなかった場合、`null` 型と `Nothing` 型のプロパティの値は `String` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Object`) に、`Integer` 型のプロパティの値はゼロ (0) になります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-149">If a data provider does not support extended field properties, or if the field is not found when the query is executed, the value for the property is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) for properties of type `String` and `Object`, and zero (0) for properties of type `Integer`.</span></span> <span data-ttu-id="4cef0-150">データ処理拡張機能は、この構文を含むクエリを最適化することにより、定義済みのプロパティを利用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="4cef0-150">A data processing extension may take advantage of predefined properties by optimizing queries that include this syntax.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cef0-151">参照</span><span class="sxs-lookup"><span data-stu-id="4cef0-151">See Also</span></span>  
 <span data-ttu-id="4cef0-152">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4cef0-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4cef0-153">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="4cef0-153">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-datasets-ssrs.md)  
  
  
