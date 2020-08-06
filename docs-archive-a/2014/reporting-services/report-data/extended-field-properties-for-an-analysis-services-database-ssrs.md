---
title: Analysis Services データベースに対する拡張フィールド プロパティ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d7d87e2-bf0d-4ebb-a287-80b5a967a3f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5c0a8ebcb739cdf6b3fa34acf467309e7854db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742874"
---
# <a name="extended-field-properties-for-an-analysis-services-database-ssrs"></a><span data-ttu-id="7f871-102">Analysis Services データベースに対する拡張フィールド プロパティ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7f871-102">Extended Field Properties for an Analysis Services Database (SSRS)</span></span>
  <span data-ttu-id="7f871-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ処理拡張機能では、拡張フィールド プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7f871-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension supports extended field properties.</span></span> <span data-ttu-id="7f871-104">拡張フィールド プロパティとは、データ ソースにありデータ処理拡張機能でサポートされるフィールド プロパティ `Value` および `IsMissing` に加えて使用するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7f871-104">Extended field properties are properties in addition to the field properties `Value` and `IsMissing` that are available on the data source and supported by the data processing extension.</span></span> <span data-ttu-id="7f871-105">拡張プロパティは、レポート データセットのフィールド コレクションの一部としてレポート データ ペインには表示されません。</span><span class="sxs-lookup"><span data-stu-id="7f871-105">Extended properties do not appear in the Report Data pane as part of the field collection for a report dataset.</span></span> <span data-ttu-id="7f871-106">拡張フィールドプロパティの値をレポートに含めるには、組み込みコレクションを使用して名前で指定する式を記述し `Fields` ます。</span><span class="sxs-lookup"><span data-stu-id="7f871-106">You can include extended field property values in your report by writing expressions that specify them by name using the built-in `Fields` collection.</span></span>  
  
 <span data-ttu-id="7f871-107">拡張プロパティには、定義済みプロパティとカスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7f871-107">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="7f871-108">定義済みプロパティとは、特定のフィールド プロパティ名にマップされ、組み込み `Fields` コレクションを介して名前でアクセスできる、複数のデータ ソースに共通のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7f871-108">Predefined properties are properties common to multiple data sources that are mapped to specific field property names and can be accessed through the built-in `Fields` collection by name.</span></span> <span data-ttu-id="7f871-109">カスタム プロパティは、各データ プロバイダーに固有であり、拡張プロパティ名を文字列として扱う構文のみを使用して、組み込み `Fields` コレクションを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7f871-109">Custom properties are specific to each data provider and can be accessed through the built-in `Fields` collection only through syntax using the extended property name as a string.</span></span>  
  
 <span data-ttu-id="7f871-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX クエリ デザイナーをグラフィカル モードで使用してクエリを定義する場合、定義済みの一連のセル プロパティおよびディメンション プロパティが自動的に MDX クエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7f871-110">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX query designer in graphical mode to define your query, a predefined set of cell properties and dimension properties are automatically added to the MDX query.</span></span> <span data-ttu-id="7f871-111">レポート内では、MDX クエリに明記されている拡張プロパティのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f871-111">You can only use extended properties that are specifically listed in the MDX query in your report.</span></span> <span data-ttu-id="7f871-112">レポートによっては、既定の MDX コマンド テキストを変更して、キューブに定義されている他のディメンションまたはカスタム プロパティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7f871-112">Depending on your report, you may want to modify the default MDX command text to include other dimension or custom properties defined in the cube.</span></span> <span data-ttu-id="7f871-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースで使用できる拡張フィールドの詳細については、「[プロパティ値の作成および使用 (MDX)](../../analysis-services/creating-and-using-property-values-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f871-113">For more information about extended fields available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data sources, see [Creating and Using Property Values &#40;MDX&#41;](../../analysis-services/creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="working-with-field-properties-in-a-report"></a><span data-ttu-id="7f871-114">レポートのフィールド プロパティの操作</span><span class="sxs-lookup"><span data-stu-id="7f871-114">Working with Field Properties in a Report</span></span>  
 <span data-ttu-id="7f871-115">拡張フィールド プロパティには、定義済みプロパティとデータ プロバイダー固有のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7f871-115">Extended field properties include predefined properties and data provider-specific properties.</span></span> <span data-ttu-id="7f871-116">フィールド プロパティは、データセット用に作成されたクエリに存在しますが、 **レポート データ** ペインのフィールド一覧に表示されません。したがって、フィールド プロパティをレポートのデザイン画面にドラッグすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7f871-116">Field properties do not appear with the field list in the **Report Data** pane, even though they are in the query built for a dataset; therefore, you cannot drag field properties onto your report design surface.</span></span> <span data-ttu-id="7f871-117">その代わり、フィールドをレポートにドラッグし、フィールドの `Value` プロパティを、使用するプロパティに変更します。</span><span class="sxs-lookup"><span data-stu-id="7f871-117">Instead, you must drag the field onto the report and then change the `Value` property of the field to the property that you want to use.</span></span> <span data-ttu-id="7f871-118">たとえば、キューブからのセル データが既に書式設定されている場合は、 `=Fields!FieldName.FormattedValue`の式を使用することで、FormattedValue フィールド プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f871-118">For example, if the cell data from a cube has already been formatted, you can use the FormattedValue field property by using the following expression: `=Fields!FieldName.FormattedValue`.</span></span>  
  
 <span data-ttu-id="7f871-119">事前に定義されていない拡張プロパティを参照するには、式で次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f871-119">To refer to an extended property that is not predefined, use the following syntax in an expression:</span></span>  
  
-   <span data-ttu-id="7f871-120">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="7f871-120">*Fields!FieldName("PropertyName")*</span></span>  
  
## <a name="predefined-field-properties"></a><span data-ttu-id="7f871-121">定義済みフィールド プロパティ</span><span class="sxs-lookup"><span data-stu-id="7f871-121">Predefined Field Properties</span></span>  
 <span data-ttu-id="7f871-122">ほとんどの場合、定義済みフィールド プロパティはメジャー、レベル、またはディメンションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="7f871-122">In most cases, predefined field properties apply to measures, levels, or dimensions.</span></span> <span data-ttu-id="7f871-123">定義済みフィールド プロパティは、対応する値が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースに格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f871-123">A predefined field property must have a corresponding value stored in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="7f871-124">値が存在しない場合、または、レベルにメジャーのみのフィールド プロパティを指定する場合、プロパティは NULL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-124">If a value does not exist, or if you specify a measure-only field property on a level (for example), the property returns a null value.</span></span>  
  
 <span data-ttu-id="7f871-125">次の構文のいずれかを使用して、式から定義済みプロパティを参照できます。</span><span class="sxs-lookup"><span data-stu-id="7f871-125">You can use either of the following syntaxes to refer to a predefined property from an expression:</span></span>  
  
-   <span data-ttu-id="7f871-126">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="7f871-126">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="7f871-127">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="7f871-127">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="7f871-128">次の表に、使用できる定義済みフィールド プロパティの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7f871-128">The following table provides a list of predefined field properties that you can use.</span></span>  
  
|<span data-ttu-id="7f871-129">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="7f871-129">**Property**</span></span>|<span data-ttu-id="7f871-130">**Type**</span><span class="sxs-lookup"><span data-stu-id="7f871-130">**Type**</span></span>|<span data-ttu-id="7f871-131">**説明/有効値**</span><span class="sxs-lookup"><span data-stu-id="7f871-131">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="7f871-132">フィールドのデータ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f871-132">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="7f871-133">フィールドが結果データセットに存在するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7f871-133">Indicates whether the field was found in the resulting data set.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="7f871-134">レベルの完全修飾名を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-134">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="7f871-135">たとえば、 `UniqueName` 従業員の値が *[employee]. [Employee Department]。[Department] です。 & [Sales] です。 & [北アメリカの営業マネージャー] です。 & [272]*。</span><span class="sxs-lookup"><span data-stu-id="7f871-135">For example, the `UniqueName` value for an employee might be *[Employee].[Employee Department].[Department].&[Sales].&[North American Sales Manager].&[272]*.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="7f871-136">データベースで定義されたフィールドの背景色を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-136">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="7f871-137">データベースで定義されたアイテムの前景色を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-137">Returns the foreground color defined in the database for the item.</span></span>|  
|`FontFamily`|`String`|<span data-ttu-id="7f871-138">データベースで定義されたアイテムのフォント名を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-138">Returns the name of the font defined in the database for the item.</span></span>|  
|`FontSize`|`String`|<span data-ttu-id="7f871-139">データベースで定義されたアイテムのフォントのポイント サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-139">Returns the point size of the font defined in the database for the item.</span></span>|  
|`FontWeight`|`String`|<span data-ttu-id="7f871-140">データベースで定義されたアイテムのフォントの太さを返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-140">Returns the weight of the font defined in the database for the item.</span></span>|  
|`FontStyle`|`String`|<span data-ttu-id="7f871-141">データベースで定義されたアイテムのフォントのスタイルを返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-141">Returns the style of the font defined in the database for the item.</span></span>|  
|`TextDecoration`|`String`|<span data-ttu-id="7f871-142">データベースで定義されたアイテムの特殊なテキストの書式設定を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-142">Returns special text formatting defined in the database for the item.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="7f871-143">メジャーまたは主要データに対して書式設定した値を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-143">Returns a formatted value for a measure or key figure.</span></span> <span data-ttu-id="7f871-144">たとえば、 `FormattedValue` **Sales Amount Quota**のプロパティは、$1124400.00 のような通貨形式を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-144">For example, the `FormattedValue` property for **Sales Amount Quota** returns a currency format like $1,124,400.00.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="7f871-145">レベルのキーを返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-145">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="7f871-146">親子階層の場合は、レベル番号またはディメンション番号を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-146">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="7f871-147">親子階層の場合は、親レベルの完全修飾名を返します。</span><span class="sxs-lookup"><span data-stu-id="7f871-147">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7f871-148">レポートが実行されてそのデータセットのデータを取得する際にデータ ソース ( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] キューブなど) によってこれらの値が提供される場合にのみ、これらの拡張フィールド プロパティに対応する値が存在します。</span><span class="sxs-lookup"><span data-stu-id="7f871-148">Values exist for these extended field properties only if the data source (for example, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cube) provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="7f871-149">その場合、次のセクションに示す構文を使用して、すべての式からこれらのフィールド プロパティ値を参照できます。</span><span class="sxs-lookup"><span data-stu-id="7f871-149">You can then refer to those field property values from any expression using the syntax described in the following section.</span></span> <span data-ttu-id="7f871-150">ただし、これらのフィールドはこのデータ プロバイダーに固有であるため、これらの値に加えた変更はレポート定義には保存されません。</span><span class="sxs-lookup"><span data-stu-id="7f871-150">However, because these fields are specific to this data provider, changes that you make to these values are not saved with the report definition.</span></span>  
  
### <a name="example-extended-properties"></a><span data-ttu-id="7f871-151">拡張プロパティの例</span><span class="sxs-lookup"><span data-stu-id="7f871-151">Example Extended Properties</span></span>  
 <span data-ttu-id="7f871-152">拡張プロパティの例として、次の MDX クエリおよび結果セットには、キューブに対して定義されているディメンション属性で使用できるいくつかのメンバー プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f871-152">To illustrate extended properties, the following MDX query and result set include several member properties available from a dimension attribute defined for a cube.</span></span> <span data-ttu-id="7f871-153">含まれているメンバー プロパティは、MEMBER_CAPTION、UNIQUENAME、Properties("Day Name")、MEMBER_VALUE、PARENT_UNIQUE_NAME、および MEMBER_KEY です。</span><span class="sxs-lookup"><span data-stu-id="7f871-153">The member properties included are MEMBER_CAPTION, UNIQUENAME, Properties("Day Name"), MEMBER_VALUE, PARENT_UNIQUE_NAME, and MEMBER_KEY.</span></span>  
  
 <span data-ttu-id="7f871-154">この MDX クエリは、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベースに付属している [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW データベース内の [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] キューブに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="7f871-154">This MDX query runs against the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] cube in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW database, included with the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample databases.</span></span>  
  
```  
WITH MEMBER [Measures].[DateCaption]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_CAPTION'   
   MEMBER [Measures].[DateUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.UNIQUENAME'   
   MEMBER [Measures].[DateDayName]   
      AS '[Date].[Date].Properties("Day Name")'   
   MEMBER [Measures].[DateValueinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_VALUE'   
   MEMBER [Measures].[DateParentUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.PARENT_UNIQUE_NAME'   
   MEMBER [Measures].[DateMemberKeyinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_KEY'   
SELECT {  
   [Measures].[DateCaption],   
   [Measures].[DateUniqueName],   
   [Measures].[DateDayName],   
   [Measures].[DateValueinOriginalDatatype],  
   [Measures].[DateParentUniqueName],  
   [Measures].[DateMemberKeyinOriginalDatatype]  
   } ON COLUMNS , [Date].[Date].ALLMEMBERS ON ROWS   
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="7f871-155">このクエリを MDX クエリ ペインで実行すると、1,158 行の結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="7f871-155">When you run this query in an MDX query pane, you get a result set with 1158 rows.</span></span> <span data-ttu-id="7f871-156">最初の 4 行を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7f871-156">The first four rows are shown in the following table.</span></span>  
  
|<span data-ttu-id="7f871-157">DateCaption</span><span class="sxs-lookup"><span data-stu-id="7f871-157">DateCaption</span></span>|<span data-ttu-id="7f871-158">DateUniqueName</span><span class="sxs-lookup"><span data-stu-id="7f871-158">DateUniqueName</span></span>|<span data-ttu-id="7f871-159">DateDayName</span><span class="sxs-lookup"><span data-stu-id="7f871-159">DateDayName</span></span>|<span data-ttu-id="7f871-160">DateValueinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="7f871-160">DateValueinOriginalDatatype</span></span>|<span data-ttu-id="7f871-161">DateParentUniqueName</span><span class="sxs-lookup"><span data-stu-id="7f871-161">DateParentUniqueName</span></span>|<span data-ttu-id="7f871-162">DateMemberKeyinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="7f871-162">DateMemberKeyinOriginalDatatype</span></span>|  
|-----------------|--------------------|-----------------|---------------------------------|--------------------------|-------------------------------------|  
|<span data-ttu-id="7f871-163">All Periods</span><span class="sxs-lookup"><span data-stu-id="7f871-163">All Periods</span></span>|<span data-ttu-id="7f871-164">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="7f871-164">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="7f871-165">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-165">(null)</span></span>|<span data-ttu-id="7f871-166">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-166">(null)</span></span>|<span data-ttu-id="7f871-167">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-167">(null)</span></span>|<span data-ttu-id="7f871-168">0</span><span class="sxs-lookup"><span data-stu-id="7f871-168">0</span></span>|  
|<span data-ttu-id="7f871-169">1-Jul-01</span><span class="sxs-lookup"><span data-stu-id="7f871-169">1-Jul-01</span></span>|<span data-ttu-id="7f871-170">[Date].[Date].&[1]</span><span class="sxs-lookup"><span data-stu-id="7f871-170">[Date].[Date].&[1]</span></span>|<span data-ttu-id="7f871-171">土曜日</span><span class="sxs-lookup"><span data-stu-id="7f871-171">Sunday</span></span>|<span data-ttu-id="7f871-172">7/1/2001</span><span class="sxs-lookup"><span data-stu-id="7f871-172">7/1/2001</span></span>|<span data-ttu-id="7f871-173">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="7f871-173">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="7f871-174">1</span><span class="sxs-lookup"><span data-stu-id="7f871-174">1</span></span>|  
|<span data-ttu-id="7f871-175">2-Jul-01</span><span class="sxs-lookup"><span data-stu-id="7f871-175">2-Jul-01</span></span>|<span data-ttu-id="7f871-176">[Date].[Date].&[2]</span><span class="sxs-lookup"><span data-stu-id="7f871-176">[Date].[Date].&[2]</span></span>|<span data-ttu-id="7f871-177">月曜日</span><span class="sxs-lookup"><span data-stu-id="7f871-177">Monday</span></span>|<span data-ttu-id="7f871-178">7/2/2001</span><span class="sxs-lookup"><span data-stu-id="7f871-178">7/2/2001</span></span>|<span data-ttu-id="7f871-179">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="7f871-179">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="7f871-180">2</span><span class="sxs-lookup"><span data-stu-id="7f871-180">2</span></span>|  
|<span data-ttu-id="7f871-181">3-Jul-01</span><span class="sxs-lookup"><span data-stu-id="7f871-181">3-Jul-01</span></span>|<span data-ttu-id="7f871-182">[Date].[Date].&[3]</span><span class="sxs-lookup"><span data-stu-id="7f871-182">[Date].[Date].&[3]</span></span>|<span data-ttu-id="7f871-183">火曜日</span><span class="sxs-lookup"><span data-stu-id="7f871-183">Tuesday</span></span>|<span data-ttu-id="7f871-184">7/3/2001</span><span class="sxs-lookup"><span data-stu-id="7f871-184">7/3/2001</span></span>|<span data-ttu-id="7f871-185">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="7f871-185">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="7f871-186">3</span><span class="sxs-lookup"><span data-stu-id="7f871-186">3</span></span>|  
  
 <span data-ttu-id="7f871-187">MDX クエリ デザイナーのグラフィカル モードを使用して作成される既定の MDX クエリに、ディメンション プロパティとして含まれるのは MEMBER_CAPTION と UNIQUENAME のみです。</span><span class="sxs-lookup"><span data-stu-id="7f871-187">Default MDX queries built using the MDX Query Designer in graphical mode only include MEMBER_CAPTION and UNIQUENAME for dimension properties.</span></span> <span data-ttu-id="7f871-188">既定では、これらの値は常に `String` データ型です。</span><span class="sxs-lookup"><span data-stu-id="7f871-188">By default, these values always are data type `String`.</span></span>  
  
 <span data-ttu-id="7f871-189">メンバー プロパティの元のデータ型を保持する必要がある場合は、テキスト ベースのクエリ デザイナーで既定の MDX ステートメントを変更することによって、追加のプロパティ MEMBER_VALUE を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7f871-189">If you need a member property in its original data type, you can include an additional property MEMBER_VALUE by modifying the default MDX statement in the text-based query designer.</span></span> <span data-ttu-id="7f871-190">次の単純な MDX ステートメントでは、取得するディメンション プロパティのリストに MEMBER_VALUE が追加されています。</span><span class="sxs-lookup"><span data-stu-id="7f871-190">In the following simple MDX statement, MEMBER_VALUE has been added to the list of dimension properties to retrieve.</span></span>  
  
```  
SELECT NON EMPTY {[Measures].[Order Count]} ON COLUMNS,   
NON EMPTY { ([Date].[Month of Year].[Month of Year] ) }   
DIMENSION PROPERTIES   
   MEMBER_CAPTION, MEMBER_UNIQUE_NAME, MEMBER_VALUE ON ROWS   
FROM [Adventure Works]  
CELL PROPERTIES   
   VALUE, BACK_COLOR, FORE_COLOR,   
   FORMATTED_VALUE, FORMAT_STRING,   
   FONT_NAME, FONT_SIZE, FONT_FLAGS  
```  
  
 <span data-ttu-id="7f871-191">MDX 結果ペインに表示された結果の最初の 4 行を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7f871-191">The first four rows of the result in the MDX Results pane appear in the following table.</span></span>  
  
|<span data-ttu-id="7f871-192">Month of Year</span><span class="sxs-lookup"><span data-stu-id="7f871-192">Month of Year</span></span>|<span data-ttu-id="7f871-193">Order Count</span><span class="sxs-lookup"><span data-stu-id="7f871-193">Order Count</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="7f871-194">January</span><span class="sxs-lookup"><span data-stu-id="7f871-194">January</span></span>|<span data-ttu-id="7f871-195">2,481</span><span class="sxs-lookup"><span data-stu-id="7f871-195">2,481</span></span>|  
|<span data-ttu-id="7f871-196">Ferbruary</span><span class="sxs-lookup"><span data-stu-id="7f871-196">February</span></span>|<span data-ttu-id="7f871-197">2,684</span><span class="sxs-lookup"><span data-stu-id="7f871-197">2,684</span></span>|  
|<span data-ttu-id="7f871-198">3 月</span><span class="sxs-lookup"><span data-stu-id="7f871-198">March</span></span>|<span data-ttu-id="7f871-199">2,749</span><span class="sxs-lookup"><span data-stu-id="7f871-199">2,749</span></span>|  
|<span data-ttu-id="7f871-200">April</span><span class="sxs-lookup"><span data-stu-id="7f871-200">April</span></span>|<span data-ttu-id="7f871-201">2,739</span><span class="sxs-lookup"><span data-stu-id="7f871-201">2,739</span></span>|  
  
 <span data-ttu-id="7f871-202">プロパティは MDX の SELECT ステートメントに含まれていますが、結果セット列には表示されません。</span><span class="sxs-lookup"><span data-stu-id="7f871-202">Even though the properties are part of the MDX select statement, they do not appear in the result set columns.</span></span> <span data-ttu-id="7f871-203">そこで、拡張プロパティ機能を使用すると、データをレポートに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="7f871-203">Nevertheless, the data is available for a report by using the extended properties feature.</span></span> <span data-ttu-id="7f871-204">の MDX クエリ結果ペインでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] セルをダブルクリックして、セルプロパティの値がキューブで設定されている場合はその値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="7f871-204">In an MDX query result pane in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can double-click on the cell and see the cell property values if they are set in the cube.</span></span> <span data-ttu-id="7f871-205">1,379 という値が格納されている最初の Order Count セルをダブルクリックすると、ポップアップ ウィンドウに次のセル プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f871-205">If you double-click on the first Order Count cell that contains 1,379, you will see a pop-up window with the following cell properties:</span></span>  
  
|<span data-ttu-id="7f871-206">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7f871-206">Property</span></span>|<span data-ttu-id="7f871-207">値</span><span class="sxs-lookup"><span data-stu-id="7f871-207">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="7f871-208">CellOrdinal</span><span class="sxs-lookup"><span data-stu-id="7f871-208">CellOrdinal</span></span>|<span data-ttu-id="7f871-209">0</span><span class="sxs-lookup"><span data-stu-id="7f871-209">0</span></span>|  
|<span data-ttu-id="7f871-210">値</span><span class="sxs-lookup"><span data-stu-id="7f871-210">VALUE</span></span>|<span data-ttu-id="7f871-211">2481</span><span class="sxs-lookup"><span data-stu-id="7f871-211">2481</span></span>|  
|<span data-ttu-id="7f871-212">BACK_COLOR</span><span class="sxs-lookup"><span data-stu-id="7f871-212">BACK_COLOR</span></span>|<span data-ttu-id="7f871-213">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-213">(null)</span></span>|  
|<span data-ttu-id="7f871-214">FORE_COLOR</span><span class="sxs-lookup"><span data-stu-id="7f871-214">FORE_COLOR</span></span>|<span data-ttu-id="7f871-215">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-215">(null)</span></span>|  
|<span data-ttu-id="7f871-216">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="7f871-216">FORMATTED_VALUE</span></span>|<span data-ttu-id="7f871-217">2,481</span><span class="sxs-lookup"><span data-stu-id="7f871-217">2,481</span></span>|  
|<span data-ttu-id="7f871-218">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="7f871-218">FORMAT_STRING</span></span>|<span data-ttu-id="7f871-219">#,#</span><span class="sxs-lookup"><span data-stu-id="7f871-219">#,#</span></span>|  
|<span data-ttu-id="7f871-220">FONT_NAME</span><span class="sxs-lookup"><span data-stu-id="7f871-220">FONT_NAME</span></span>|<span data-ttu-id="7f871-221">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-221">(null)</span></span>|  
|<span data-ttu-id="7f871-222">FONT_SIZE</span><span class="sxs-lookup"><span data-stu-id="7f871-222">FONT_SIZE</span></span>|<span data-ttu-id="7f871-223">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-223">(null)</span></span>|  
|<span data-ttu-id="7f871-224">FONT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="7f871-224">FONT_FLAGS</span></span>|<span data-ttu-id="7f871-225">(null)</span><span class="sxs-lookup"><span data-stu-id="7f871-225">(null)</span></span>|  
  
 <span data-ttu-id="7f871-226">このクエリを使用してレポート データセットを作成し、データセットをテーブルにバインドすると、フィールドの既定の VALUE プロパティが表示されます (たとえば `=Fields!Month_of_Year!Value`)。</span><span class="sxs-lookup"><span data-stu-id="7f871-226">If you create a report dataset with this query and bind the dataset to a table, you can see the default VALUE property for a field, for example, `=Fields!Month_of_Year!Value`.</span></span> <span data-ttu-id="7f871-227">Value フィールドでは `String` データ型が使用されるので、この式をテーブルの並べ替え式として設定した場合、テーブルは月のアルファベット順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="7f871-227">If you set this expression as the sort expression for the table, your results will be to sort the table alphabetically by month because the Value field uses a `String` data type.</span></span> <span data-ttu-id="7f871-228">月がカレンダー順に並ぶ (つまり、January が先頭に来て December が最後に来る) ようにテーブルを並べ替えるには、次の式を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f871-228">To sort the table in so that the months are in the order they occur in the year with January first and December last, use the following expression:</span></span>  
  
```  
=Fields!Month_of_Year("MEMBER_VALUE")  
```  
  
 <span data-ttu-id="7f871-229">これにより、データ ソースの元の整数データ型に基づいてフィールドの値が並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="7f871-229">This sorts the value of the field in its original integer data type from the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f871-230">参照</span><span class="sxs-lookup"><span data-stu-id="7f871-230">See Also</span></span>  
 <span data-ttu-id="7f871-231">[式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f871-231">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7f871-232">[式に含まれる組み込みコレクション &#40;レポートビルダーと SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="7f871-232">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="7f871-233">データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7f871-233">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
