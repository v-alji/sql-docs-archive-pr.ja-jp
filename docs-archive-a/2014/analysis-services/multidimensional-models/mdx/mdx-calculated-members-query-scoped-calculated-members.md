---
title: クエリスコープの計算されるメンバーの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c0b3e7184f3cc6abd189344bbce1b6e1f948ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639701"
---
# <a name="creating-query-scoped-calculated-members-mdx"></a><span data-ttu-id="040fb-102">クエリ スコープの計算されるメンバーの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="040fb-102">Creating Query-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="040fb-103">1 つの多次元式 (MDX) クエリでのみ計算されるメンバーが必要な場合は、WITH キーワードを使用してその計算されるメンバーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="040fb-103">If a calculated member is only required for a single Multidimensional Expressions (MDX) query, you can define that calculated member by using the WITH keyword.</span></span> <span data-ttu-id="040fb-104">WITH キーワードを使用して作成した計算されるメンバーは、そのクエリの実行が終了した時点で存在しなくなります。</span><span class="sxs-lookup"><span data-stu-id="040fb-104">A calculated member that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="040fb-105">このトピックで説明するように、WITH キーワードの構文は非常に柔軟なので、計算されるメンバーに基づいて別の計算されるメンバーを定義することも可能です。</span><span class="sxs-lookup"><span data-stu-id="040fb-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even allowing a calculated member to be based on another calculated member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="040fb-106">計算されるメンバーの詳細については、「[MDX での計算されるメンバーの作成 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="040fb-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="040fb-107">WITH キーワードの構文</span><span class="sxs-lookup"><span data-stu-id="040fb-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="040fb-108">MDX の SELECT ステートメントに WITH キーワードを追加するための構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="040fb-108">Use the following syntax to add the WITH keyword to an MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 <span data-ttu-id="040fb-109">WITH キーワードの構文で使用する `Member_Identifier` の値は、計算されるメンバーの完全修飾名です。</span><span class="sxs-lookup"><span data-stu-id="040fb-109">In the syntax for the WITH keyword, the `Member_Identifier` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="040fb-110">完全修飾名には、計算されるメンバーを関連付けるディメンションまたはレベルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="040fb-110">This fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="040fb-111">`MDX_Expression` の値は、その式の値が評価された後の計算されるメンバーの値を返します。</span><span class="sxs-lookup"><span data-stu-id="040fb-111">The `MDX_Expression` value returns the value of the calculated member after the expression value has been evaluated.</span></span> <span data-ttu-id="040fb-112">必要に応じて、 `MemberProperty_Identifier` の値にセル プロパティの名前を、 `Scalar_Expression` の値にセル プロパティの値を指定して、計算されるメンバーの固有セル プロパティの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="040fb-112">The values of intrinsic cell properties for a calculated member can be optionally specified by supplying the name of the cell property in the `MemberProperty_Identifier` value and the value of the cell property in the `Scalar_Expression` value.</span></span>  
  
## <a name="with-keyword-examples"></a><span data-ttu-id="040fb-113">WITH キーワードの例</span><span class="sxs-lookup"><span data-stu-id="040fb-113">WITH Keyword Examples</span></span>  
 <span data-ttu-id="040fb-114">次の MDX クエリは、計算されるメンバー `[Measures].[Special Discount]`を定義し、元の割引額に基づいて特殊な割引額を計算します。</span><span class="sxs-lookup"><span data-stu-id="040fb-114">The following MDX query defines a calculated member, `[Measures].[Special Discount]`, calculating a special discount based on the original discount amount.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 <span data-ttu-id="040fb-115">計算されるメンバーは、階層内のどこにでも作成できます。</span><span class="sxs-lookup"><span data-stu-id="040fb-115">You can also create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="040fb-116">たとえば、次の例に示す MDX クエリは、仮想的な Sales キューブの計算されるメンバー `[BigSeller]` を定義しています。</span><span class="sxs-lookup"><span data-stu-id="040fb-116">For example, the following MDX query defines the `[BigSeller]` calculated member for a hypothetical Sales cube.</span></span> <span data-ttu-id="040fb-117">この計算されるメンバーは、指定したストアのビールとワインの売上数量が 100.00 以上かどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="040fb-117">This calculated member determines whether a specified store has at least 100.00 in unit sales for beer and wine.</span></span> <span data-ttu-id="040fb-118">ただし、このクエリは、 `[BigSeller]` という計算されるメンバーを `[Product]` ディメンションの子メンバーではなく `[Beer and Wine]` メンバーの子メンバーとして作成します。</span><span class="sxs-lookup"><span data-stu-id="040fb-118">However, the query creates the `[BigSeller]` calculated member not as a child member of the `[Product]` dimension, but instead as a child member of the `[Beer and Wine]` member.</span></span>  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 <span data-ttu-id="040fb-119">計算されるメンバーの基になるメンバーは、キューブ内の既存のメンバーである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="040fb-119">Calculated members do not have to depend only on existing members in a cube.</span></span> <span data-ttu-id="040fb-120">同じ MDX 式で定義する他の計算されるメンバーに基づく計算されるメンバーを作成することも可能です。</span><span class="sxs-lookup"><span data-stu-id="040fb-120">Calculated member can also be based on other calculated members defined in the same MDX expression.</span></span> <span data-ttu-id="040fb-121">たとえば、次の MDX クエリは、最初の計算されるメンバー `[Measures].[Special Discount]`で作成する値に基づいて、2 番目の計算されるメンバー `[Measures].[Special Discounted Amount]`の値を生成します。</span><span class="sxs-lookup"><span data-stu-id="040fb-121">For example, the following MDX query uses the value created in the first calculated member, `[Measures].[Special Discount]`, to generate the value of the second calculated member, `[Measures].[Special Discounted Amount]`.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="040fb-122">参照</span><span class="sxs-lookup"><span data-stu-id="040fb-122">See Also</span></span>  
 <span data-ttu-id="040fb-123">[Mdx 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="040fb-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 <span data-ttu-id="040fb-124">[SELECT ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="040fb-124">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="040fb-125">セッション スコープの計算されるメンバーの作成 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="040fb-125">Creating Session-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
