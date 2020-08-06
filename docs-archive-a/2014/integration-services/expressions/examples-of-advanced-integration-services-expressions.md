---
title: Integration Services 式の詳細の例 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- operators [Integration Services]
- expressions [Integration Services], examples
- examples [Integration Services]
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb1e8dc6f9bffd22c917414f80f6ba9f257b25b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640179"
---
# <a name="examples-of-advanced-integration-services-expressions"></a><span data-ttu-id="41693-102">Integration Services 式の詳細の例</span><span class="sxs-lookup"><span data-stu-id="41693-102">Examples of Advanced Integration Services Expressions</span></span>
  <span data-ttu-id="41693-103">このセクションでは、複数の演算子と関数を組み合わせた詳細な式の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="41693-103">This section provides examples of advanced expressions that combine multiple operators and functions.</span></span> <span data-ttu-id="41693-104">式が優先順位制約または条件分割変換で使用される場合、式はブール型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="41693-104">If an expression is used in a precedence constraint or the Conditional Split transformation, it must evaluate to a Boolean.</span></span> <span data-ttu-id="41693-105">ただしこの制限は、プロパティ式、変数、派生列変換、または For ループ コンテナーで使用される式には適用されません。</span><span class="sxs-lookup"><span data-stu-id="41693-105">That restriction, however, does not apply to expressions used in property expressions, variables, the Derived Column transformation, or the For Loop container.</span></span>  
  
 <span data-ttu-id="41693-106">次の例では、**AdventureWorks** および [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-106">The following examples use the **AdventureWorks** and the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="41693-107">それぞれの例では、式で使用するテーブルを判別します。</span><span class="sxs-lookup"><span data-stu-id="41693-107">Each example identifies the tables it uses.</span></span>  
  
## <a name="boolean-expressions"></a><span data-ttu-id="41693-108">ブール式</span><span class="sxs-lookup"><span data-stu-id="41693-108">Boolean Expressions</span></span>  
  
-   <span data-ttu-id="41693-109">この例では、 **Product** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-109">This example uses the **Product** table.</span></span> <span data-ttu-id="41693-110">式は、 **SellStartDate** 列の月エントリを評価し、その月が 6 月以降の場合に TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="41693-110">The expression evaluates the month entry in the **SellStartDate** column and returns TRUE if the month is June or later.</span></span>  
  
    ```  
    DATEPART("mm",SellStartDate) > 6  
    ```  
  
-   <span data-ttu-id="41693-111">この例では、 **Product** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-111">This example uses the **Product** table.</span></span> <span data-ttu-id="41693-112">式は、 **ListPrice** 列を **StandardCost** 列で割った結果を丸め、その結果が 1.5 よりも大きい場合に TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="41693-112">The expression evaluates the rounded result of dividing the **ListPrice** column by the **StandardCost** column, and returns TRUE if the result is greater than 1.5.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) > 1.50  
    ```  
  
-   <span data-ttu-id="41693-113">この例では、 **Product** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-113">This example uses the **Product** table.</span></span> <span data-ttu-id="41693-114">式は、3 つの演算すべてが TRUE に評価された場合に TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="41693-114">The expression returns TRUE if all three operations evaluate to TRUE.</span></span> <span data-ttu-id="41693-115">**Size** 列のデータ型と **BikeSize** 変数のデータ型に互換性がない場合、式には、2 番目の例で示すように明示的なキャストが必要です。</span><span class="sxs-lookup"><span data-stu-id="41693-115">If the **Size** column and the **BikeSize** variable have incompatible data types, the expression requires an explicit cast as shown the second example.</span></span> <span data-ttu-id="41693-116">DT_WSTR へのキャストには、文字列の長さも含まれます。</span><span class="sxs-lookup"><span data-stu-id="41693-116">The cast to DT_WSTR includes the length of the string.</span></span>  
  
    ```  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE && Size != @BikeSize  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE  && Size != (DT_WSTR,10)@BikeSize  
    ```  
  
-   <span data-ttu-id="41693-117">この例では、 **CurrencyRate** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-117">This example uses the **CurrencyRate** table.</span></span> <span data-ttu-id="41693-118">式は、テーブル内の値と変数を比較します。</span><span class="sxs-lookup"><span data-stu-id="41693-118">The expression compares values in tables and variables.</span></span> <span data-ttu-id="41693-119">**FromCurrencyCode** 列または **ToCurrencyCode** 列のエントリが変数の値と等しく、かつ **AverageRate** の値が **EndOfDayRate**の値よりも大きい場合、式は TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="41693-119">It returns TRUE if entries in the **FromCurrencyCode** or **ToCurrencyCode** columns are equal to variable values and if the value in **AverageRate** is greater that the value in **EndOfDayRate**.</span></span>  
  
    ```  
    (FromCurrencyCode == @FromCur || ToCurrencyCode == @ToCur) && AverageRate > EndOfDayRate  
    ```  
  
-   <span data-ttu-id="41693-120">この例では、 **Currency** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-120">This example uses the **Currency** table.</span></span> <span data-ttu-id="41693-121">**Name** 列の最初の文字が a または A でない場合、式は TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="41693-121">The expression returns TRUE if the first character in the **Name** column is not a or A.</span></span>  
  
    ```  
    SUBSTRING(UPPER(Name),1,1) != "A"  
    ```  
  
     <span data-ttu-id="41693-122">次の式は同じ結果を返しますが、1 文字だけ大文字に変換されるため、より効率的です。</span><span class="sxs-lookup"><span data-stu-id="41693-122">The following expression provides the same results, but it is more efficient because only one character is converted to uppercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Name,1,1)) != "A"  
    ```  
  
## <a name="non-boolean-expressions"></a><span data-ttu-id="41693-123">ブール式以外の式</span><span class="sxs-lookup"><span data-stu-id="41693-123">Non-Boolean Expressions</span></span>  
 <span data-ttu-id="41693-124">ブール式以外の式は、派生列変換、プロパティ式、および For ループ コンテナーで使用されます。</span><span class="sxs-lookup"><span data-stu-id="41693-124">Non-Boolean expressions are used in the Derived Column transformation, property expressions, and the For Loop container.</span></span>  
  
-   <span data-ttu-id="41693-125">この例では、 **Contact** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-125">This example uses the **Contact** table.</span></span> <span data-ttu-id="41693-126">式は、 **FirstName**、 **MiddleName**、および **LastName** 列から先頭および末尾のスペースを削除します。</span><span class="sxs-lookup"><span data-stu-id="41693-126">The expression removes leading and trailing spaces from the **FirstName**, **MiddleName**, and **LastName** columns.</span></span> <span data-ttu-id="41693-127">**MiddleName** 列が NULL でない場合は最初の文字を抽出し、そのミドル ネーム イニシャルと **FirstName** および **LastName**の値を連結して、値の間に適切なスペースを挿入します。</span><span class="sxs-lookup"><span data-stu-id="41693-127">It extracts the first letter of the **MiddleName** column if it is not null, concatenates the middle initial and the values in **FirstName** and **LastName**, and inserts appropriate spaces between values.</span></span>  
  
    ```  
    TRIM(FirstName) + " " + (!ISNULL(MiddleName) ? SUBSTRING(MiddleName,1,1) + " " : "") + TRIM(LastName)  
    ```  
  
-   <span data-ttu-id="41693-128">この例では、 **Contact** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-128">This example uses the **Contact** table.</span></span> <span data-ttu-id="41693-129">式は、 **Salutation** 列のエントリを検証します。</span><span class="sxs-lookup"><span data-stu-id="41693-129">The expression validates entries in the **Salutation** column.</span></span> <span data-ttu-id="41693-130">**Salutation** のエントリまたは空の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="41693-130">It returns a **Salutation** entry or an empty string.</span></span>  
  
    ```  
    (Salutation == "Sr." || Salutation == "Ms." || Salutation == "Sra." || Salutation == "Mr.") ? Salutation : ""  
    ```  
  
-   <span data-ttu-id="41693-131">この例では、 **Product** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-131">This example uses the **Product** table.</span></span> <span data-ttu-id="41693-132">式は、 **Color** 列の最初の文字を大文字に変換し、残りの文字を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="41693-132">The expression converts the first character in the **Color** column to uppercase and converts remaining characters to lowercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Color,1,1)) + LOWER(SUBSTRING(Color,2,15))  
    ```  
  
-   <span data-ttu-id="41693-133">この例では、 **Product** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-133">This example uses the **Product** table.</span></span> <span data-ttu-id="41693-134">式は、製品が販売された月数を計算し、 **SellStartDate** または **SellEndDate** 列のどちらかが NULL の場合、文字列 "Unknown" を返します。</span><span class="sxs-lookup"><span data-stu-id="41693-134">The expression calculates the number of months a product has been sold and returns the string "Unknown" if either the **SellStartDate** or the **SellEndDate** column contains NULL.</span></span>  
  
    ```  
    !(ISNULL(SellStartDate)) && !(ISNULL(SellEndDate)) ? (DT_WSTR,2)DATEDIFF("mm",SellStartDate,SellEndDate) : "Unknown"  
    ```  
  
-   <span data-ttu-id="41693-135">この例では、 **Product** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41693-135">This example uses the **Product** table.</span></span> <span data-ttu-id="41693-136">式は、 **StandardCost** 列の利益率を計算し、その結果を有効桁数 2 桁に丸めます。</span><span class="sxs-lookup"><span data-stu-id="41693-136">The expression calculates the markup on the **StandardCost** column and rounds the result to a precision of two.</span></span> <span data-ttu-id="41693-137">結果はパーセンテージで表されます。</span><span class="sxs-lookup"><span data-stu-id="41693-137">The result is presented as a percentage.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) * 100  
    ```  
  
## <a name="related-tasks"></a><span data-ttu-id="41693-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="41693-138">Related Tasks</span></span>  
 [<span data-ttu-id="41693-139">データ フロー コンポーネントで式を使用する</span><span class="sxs-lookup"><span data-stu-id="41693-139">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="41693-140">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="41693-140">Related Content</span></span>  
 <span data-ttu-id="41693-141">pragmaticworks.com の技術記事「 [SSIS 式チート シート](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)」</span><span class="sxs-lookup"><span data-stu-id="41693-141">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
