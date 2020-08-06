---
title: 派生列変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntrans.f1
helpviewer_keywords:
- multiple derived columns
- expressions [Integration Services], derived columns
- derived columns
- columns [Integration Services], derivations
- Derived Column transformation
ms.assetid: 8eba755e-8e48-4233-bd1e-09a46bf2692f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bbdc46f2e67b1b859fcfa446c584373cfbeca0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632024"
---
# <a name="derived-column-transformation"></a><span data-ttu-id="9f41f-102">派生列変換</span><span class="sxs-lookup"><span data-stu-id="9f41f-102">Derived Column Transformation</span></span>
  <span data-ttu-id="9f41f-103">派生列変換では、式を変換入力列に適用することにより新しい列の値を作成します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-103">The Derived Column transformation creates new column values by applying expressions to transformation input columns.</span></span> <span data-ttu-id="9f41f-104">式には、変換入力からの列、変数、関数、および演算子の任意の組み合わせを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-104">An expression can contain any combination of variables, functions, operators, and columns from the transformation input.</span></span> <span data-ttu-id="9f41f-105">結果は、新しい列として追加するか、または既存の列の値を置き換える値として挿入できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-105">The result can be added as a new column or inserted into an existing column as a replacement value.</span></span> <span data-ttu-id="9f41f-106">派生列変換では複数の派生列を定義でき、任意の変数または入力列を複数の式に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-106">The Derived Column transformation can define multiple derived columns, and any variable or input columns can appear in multiple expressions.</span></span>  
  
 <span data-ttu-id="9f41f-107">この変換を使用すると、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-107">You can use this transformation to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="9f41f-108">複数の異なる列のデータを 1 つの派生列に連結します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-108">Concatenate data from different columns into a derived column.</span></span> <span data-ttu-id="9f41f-109">たとえば、 **という式を使用すると、** FirstName **列と** LastName **列の値を、1 つの**FullName `FirstName + " " + LastName`という名前の派生列に結合できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-109">For example, you can combine values from the **FirstName** and **LastName** columns into a single derived column named **FullName**, by using the expression `FirstName + " " + LastName`.</span></span>  
  
-   <span data-ttu-id="9f41f-110">SUBSTRING などの関数を使用して文字列データから文字を抽出し、その結果を派生列に格納します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-110">Extract characters from string data by using functions such as SUBSTRING, and then store the result in a derived column.</span></span> <span data-ttu-id="9f41f-111">たとえば、 **という式を使用すると、** FirstName `SUBSTRING(FirstName,1,1)`列から名前の頭文字を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-111">For example, you can extract a person's initial from the **FirstName** column, by using the expression `SUBSTRING(FirstName,1,1)`.</span></span>  
  
-   <span data-ttu-id="9f41f-112">数学関数を数値データに適用し、その結果を派生列に格納します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-112">Apply mathematical functions to numeric data and store the result in a derived column.</span></span> <span data-ttu-id="9f41f-113">たとえば、 **という式を使用すると、数値列**SalesTax `ROUND(SalesTax, 2)`の長さと有効桁数を、小数点以下 2 桁に変更できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-113">For example, you can change the length and precision of a numeric column, **SalesTax**, to a number with two decimal places, by using the expression `ROUND(SalesTax, 2)`.</span></span>  
  
-   <span data-ttu-id="9f41f-114">入力列と変数を比較する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-114">Create expressions that compare input columns and variables.</span></span> <span data-ttu-id="9f41f-115">たとえば、 **という式を使用すると、変数** Version **と列**ProductVersion **のデータを比較し、その比較結果に応じて、** Version **と**ProductVersion `ProductVersion == @Version? ProductVersion : @Version`のどちらかの値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-115">For example, you can compare the variable **Version** against the data in the column **ProductVersion**, and depending on the comparison result, use the value of either **Version** or **ProductVersion**, by using the expression `ProductVersion == @Version? ProductVersion : @Version`.</span></span>  
  
-   <span data-ttu-id="9f41f-116">datetime 値の一部を抽出します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-116">Extract parts of a datetime value.</span></span> <span data-ttu-id="9f41f-117">たとえば、 `DATEPART("year",GETDATE())`という式を使用すると、GETDATE 関数と DATEPART 関数を使用して現在の年を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-117">For example, you can use the GETDATE and DATEPART functions to extract the current year, by using the expression `DATEPART("year",GETDATE())`.</span></span>  
  
-   <span data-ttu-id="9f41f-118">式を使用して、日付文字列を特定の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-118">Convert date strings to a specific format using an expression.</span></span>  
  
## <a name="configuration-of-the-derived-column-transformation"></a><span data-ttu-id="9f41f-119">派生列変換の構成</span><span class="sxs-lookup"><span data-stu-id="9f41f-119">Configuration of the Derived Column Transformation</span></span>  
 <span data-ttu-id="9f41f-120">派生列変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-120">You can configure the Derived column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="9f41f-121">各入力列または変更する新しい列に対し、式を設定します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-121">Provide an expression for each input column or new column that will be changed.</span></span> <span data-ttu-id="9f41f-122">詳細については、「 [Integration Services (SSIS) 式](../../expressions/integration-services-ssis-expressions.md)に評価されるまでそのワークフローを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9f41f-123">派生列変換によって上書きされる入力列を式が参照する場合、その式は派生した値ではなく、列の元の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-123">If an expression references an input column that is overwritten by the Derived Column transformation, the expression uses the original value of the column, not the derived value.</span></span>  
  
-   <span data-ttu-id="9f41f-124">データ型が `string` の結果を新しい列に追加する場合は、コード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-124">If adding results to new columns and the data type is `string`, specify a code page.</span></span> <span data-ttu-id="9f41f-125">詳しくは、「 [Comparing String Data](../comparing-string-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9f41f-125">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="9f41f-126">派生列変換には、FriendlyExpression カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9f41f-126">The Derived Column transformation includes the FriendlyExpression custom property.</span></span> <span data-ttu-id="9f41f-127">このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-127">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="9f41f-128">詳細については、「 [パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」および「 [変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f41f-128">For more information, see [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="9f41f-129">この変換は、1 つの入力、1 つの標準出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="9f41f-129">This transformation has one input, one regular output, and one error output.</span></span>  
  
 <span data-ttu-id="9f41f-130">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="9f41f-130">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9f41f-131">**[派生列変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [派生列変換エディター](../../derived-column-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f41f-131">For more information about the properties that you can set in the **Derived Column Transformation Editor** dialog box, see [Derived Column Transformation Editor](../../derived-column-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="9f41f-132">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="9f41f-132">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="9f41f-133">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f41f-133">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9f41f-134">Common Properties</span><span class="sxs-lookup"><span data-stu-id="9f41f-134">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="9f41f-135">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="9f41f-135">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="9f41f-136">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f41f-136">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9f41f-137">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="9f41f-137">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="9f41f-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9f41f-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9f41f-139">派生列変換を使用して列の値を取得する</span><span class="sxs-lookup"><span data-stu-id="9f41f-139">Derive Column Values by Using the Derived Column Transformation</span></span>](derived-column-transformation.md)  
  
## <a name="related-content"></a><span data-ttu-id="9f41f-140">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="9f41f-140">Related Content</span></span>  
 <span data-ttu-id="9f41f-141">social.technet.microsoft.com の技術記事「 [SSIS 式の例](https://go.microsoft.com/fwlink/?LinkId=220761)」</span><span class="sxs-lookup"><span data-stu-id="9f41f-141">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
 <span data-ttu-id="9f41f-142">記事「 [SSIS を使用して列データを分割する方法](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9f41f-142">Blog, [How to Split Column Data using SSIS](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html).</span></span>  
  
  
