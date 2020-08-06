---
title: カスタムメンバー式の定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- members [Analysis Services], custom
- custom rollup formulas [Analysis Services]
- MDX [Analysis Services], custom rollup formulas
- custom member formulas [Analysis Services]
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51649bea0c4134971b342b779c778b857343e62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741442"
---
# <a name="define-custom-member-formulas"></a><span data-ttu-id="7e4a6-102">カスタム メンバー式の定義</span><span class="sxs-lookup"><span data-stu-id="7e4a6-102">Define Custom Member Formulas</span></span>
  <span data-ttu-id="7e4a6-103">カスタム メンバー式と呼ばれる多次元式 (MDX) を定義すると、指定した属性のメンバーに値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-103">You can define a Multidimensional Expressions (MDX) expression, called a custom member formula, to supply the values for the members of a specified attribute.</span></span> <span data-ttu-id="7e4a6-104">データ ソース ビューからのテーブルの列は、属性のメンバーごとに、そのメンバーの値の指定に使用される式を提供します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-104">A column in a table from a data source view provides, for each member in an attribute, the expression used to supply the value for that member.</span></span>  
  
 <span data-ttu-id="7e4a6-105">カスタム メンバー式により、メンバーに関連付けられたセル値が判別され、メジャーの集計関数がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-105">Custom member formulas determine the cell values that are associated with members and override the aggregate functions of measures.</span></span> <span data-ttu-id="7e4a6-106">カスタム メンバー式は、MDX で記述します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-106">Custom member formulas are written in MDX.</span></span> <span data-ttu-id="7e4a6-107">各カスタム メンバー式は、1 つのメンバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-107">Each custom member formula applies to a single member.</span></span> <span data-ttu-id="7e4a6-108">カスタム メンバー式は、ディメンション テーブルまたはディメンション テーブルとの外部キー リレーションシップを持つ別のテーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-108">Custom member formulas are stored in the dimension table or in another table that has a foreign key relationship with the dimension table.</span></span>  
  
 <span data-ttu-id="7e4a6-109">属性の `CustomRollupColumn` プロパティは、属性のメンバーのカスタム メンバー式が含まれている列を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-109">The `CustomRollupColumn` property on an attribute specifies the column that contains custom member formulas for members of the attribute.</span></span> <span data-ttu-id="7e4a6-110">列の行が空の場合は、メンバーのセル値は通常どおり返されます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-110">If a row in the column is empty, the cell value for the member is returned normally.</span></span> <span data-ttu-id="7e4a6-111">列の式が有効でない場合は、メンバーを使用するセル値が取得されるたびに実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-111">If the formula in the column is not valid, a run-time error occurs whenever a cell value that uses the member is retrieved.</span></span>  
  
 <span data-ttu-id="7e4a6-112">属性のカスタム メンバー式を指定する前に、属性が含まれているディメンション テーブル、つまり直接関連するテーブルに、カスタム メンバー式を保存するための文字列型の列があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-112">Before you can specify custom member formulas for an attribute, make sure that the dimension table that contains the attribute, or a directly related table, has a string column to store the custom member formulas.</span></span> <span data-ttu-id="7e4a6-113">この場合は、 `CustomRollupColumn` 属性のプロパティを手動で設定するか、ビジネスインテリジェンスウィザードのカスタムメンバー式の拡張機能の設定を使用して、属性に対するカスタムメンバー式を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-113">If this is the case, you can either set the `CustomRollupColumn` property on an attribute manually or use the Set Custom Member Formula enhancement of the Business Intelligence Wizard to enable a custom member formula on an attribute.</span></span> <span data-ttu-id="7e4a6-114">この拡張機能の使用方法については、「 [ディメンションの属性に対するカスタム メンバー式の設定](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-114">For more information about how to use this enhancement, see [Set Custom Member Formulas for Attributes in a Dimension](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md).</span></span>  
  
## <a name="evaluating-custom-member-formulas"></a><span data-ttu-id="7e4a6-115">カスタム メンバー式の評価</span><span class="sxs-lookup"><span data-stu-id="7e4a6-115">Evaluating Custom Member Formulas</span></span>  
 <span data-ttu-id="7e4a6-116">カスタム メンバー式は、計算されるメンバーとは異なります。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-116">Custom member formulas differ from calculated members.</span></span> <span data-ttu-id="7e4a6-117">カスタム メンバー式は、ディメンション テーブルに存在しているメンバーに適用され、メンバーの値のみを提供します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-117">Custom member formulas apply to members that exist in dimension tables, and only provide the value of the member.</span></span> <span data-ttu-id="7e4a6-118">これに対して、計算されるメンバーはディメンション テーブルに格納されず、ディメンションまたは階層に含まれている他のメンバーのデータとメタデータの両方を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-118">In contrast, calculated members are not stored in dimension tables, and calculated member expressions define both data and metadata for additional members included in a dimension or hierarchy.</span></span>  
  
 <span data-ttu-id="7e4a6-119">カスタム メンバー式は、メジャーに関連付けられている集計関数をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-119">Custom member formulas override the aggregate functions associated with measures.</span></span> <span data-ttu-id="7e4a6-120">たとえば、カスタム メンバー式を指定する前に、時間ディメンションの以下のメンバーについて、`Sum` 集計関数を使用するメジャーが次の値であるとします。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-120">For example, before a custom member formula is specified, a measure using the `Sum` aggregate function has the following values for the following members of the Time dimension:</span></span>  
  
-   <span data-ttu-id="7e4a6-121">2003: 2100</span><span class="sxs-lookup"><span data-stu-id="7e4a6-121">2003: 2100</span></span>  
  
    -   <span data-ttu-id="7e4a6-122">Quarter 1: 700</span><span class="sxs-lookup"><span data-stu-id="7e4a6-122">Quarter 1: 700</span></span>  
  
    -   <span data-ttu-id="7e4a6-123">Quarter 2: 500</span><span class="sxs-lookup"><span data-stu-id="7e4a6-123">Quarter 2: 500</span></span>  
  
    -   <span data-ttu-id="7e4a6-124">Quarter 3: 100</span><span class="sxs-lookup"><span data-stu-id="7e4a6-124">Quarter 3: 100</span></span>  
  
    -   <span data-ttu-id="7e4a6-125">Quarter 4: 800</span><span class="sxs-lookup"><span data-stu-id="7e4a6-125">Quarter 4: 800</span></span>  
  
-   <span data-ttu-id="7e4a6-126">2004: 1500</span><span class="sxs-lookup"><span data-stu-id="7e4a6-126">2004: 1500</span></span>  
  
    -   <span data-ttu-id="7e4a6-127">Quarter 1: 600</span><span class="sxs-lookup"><span data-stu-id="7e4a6-127">Quarter 1: 600</span></span>  
  
    -   <span data-ttu-id="7e4a6-128">Quarter 2: 200</span><span class="sxs-lookup"><span data-stu-id="7e4a6-128">Quarter 2: 200</span></span>  
  
    -   <span data-ttu-id="7e4a6-129">Quarter 3: 300</span><span class="sxs-lookup"><span data-stu-id="7e4a6-129">Quarter 3: 300</span></span>  
  
    -   <span data-ttu-id="7e4a6-130">Quarter 4: 400</span><span class="sxs-lookup"><span data-stu-id="7e4a6-130">Quarter 4: 400</span></span>  
  
 <span data-ttu-id="7e4a6-131">カスタム メンバー式を使用すると、メンバーの値は代わりにカスタム ロールアップ式によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-131">With a custom member formula, the value of the member is instead supplied by the custom rollup formula.</span></span> <span data-ttu-id="7e4a6-132">たとえば、次のカスタム メンバー式を使用すると、時間ディメンションの 2004 メンバーの Quarter 4 子メンバーの値を 450 に指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-132">For example, the following custom member formula can be used to supply the value for the Quarter 4 child member of the 2004 member in the Time dimension as 450.</span></span>  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 <span data-ttu-id="7e4a6-133">カスタム メンバー式は、ディメンション テーブルの列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-133">Custom member formulas are stored in a column of the dimension table.</span></span> <span data-ttu-id="7e4a6-134">属性の `CustomRollupColumn` プロパティを設定して、カスタム ロールアップ式を有効にします。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-134">You enable custom rollup formulas by setting the `CustomRollupColumn` property on an attribute.</span></span>  
  
 <span data-ttu-id="7e4a6-135">1 つの MDX 式を属性のすべてのメンバーに適用するには、MDX 式をリテラル文字列として返すディメンション テーブルで名前付き計算を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-135">To apply a single MDX expression to all members of an attribute, create a named calculation on the dimension table that returns an MDX expression as a literal string.</span></span> <span data-ttu-id="7e4a6-136">次に、名前付き計算を、構成する属性の `CustomRollupColumn` プロパティ設定で指定します。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-136">Then, specify the named calculation with the `CustomRollupColumn` property setting on the attribute that you want to configure.</span></span> <span data-ttu-id="7e4a6-137">名前付き計算は、SQL 式によって定義される行の値を返す、データ ソース ビュー テーブルの列です。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-137">A named calculation is a column in a data source view table that returns row values defined by a SQL expression.</span></span> <span data-ttu-id="7e4a6-138">名前付き計算の構築方法については、「[データ ソース ビューでの名前付き計算の定義 (Analysis Services)](define-named-calculations-in-a-data-source-view-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-138">For more information about constructing named calculations, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e4a6-139">特定の属性に基づいているすべてのレベルのメンバーではなく、特定のレベルのメンバーに MDX 式を適用するには、レベルの MDX スクリプトとして式を定義できます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-139">To apply an MDX expression to members of a particular level instead of to members of all levels based on a particular attribute, you can define the expression as an MDX script on the level.</span></span> <span data-ttu-id="7e4a6-140">詳細については、「[MDX スクリプティングの基礎 (Analysis Services)](mdx/mdx-scripting-fundamentals-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-140">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
 <span data-ttu-id="7e4a6-141">計算されるメンバーと属性のメンバーのカスタム ロールアップ式の両方を使用する場合は、評価の順序に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-141">If you use both calculated members and custom rollup formulas for members of an attribute, you should be aware of the order of evaluation.</span></span> <span data-ttu-id="7e4a6-142">計算されるメンバーは、カスタム ロールアップ式が解決される前に解決されます。</span><span class="sxs-lookup"><span data-stu-id="7e4a6-142">Calculated members are resolved before custom rollup formulas are resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e4a6-143">参照</span><span class="sxs-lookup"><span data-stu-id="7e4a6-143">See Also</span></span>  
 <span data-ttu-id="7e4a6-144">[属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="7e4a6-144">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 [<span data-ttu-id="7e4a6-145">ディメンションの属性に対するカスタム メンバー式の設定</span><span class="sxs-lookup"><span data-stu-id="7e4a6-145">Set Custom Member Formulas for Attributes in a Dimension</span></span>](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  
