---
title: '[制約式の確認] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38268d4e49a9c674c100bc22c0782e3e61477967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630751"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a><span data-ttu-id="82b98-102">[制約式の確認] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82b98-102">Check Constraint Expression Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="82b98-103">テーブルまたは列に CHECK 制約を適用する場合は、SQL 式を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="82b98-103">When you attach a check constraint to a table or column, you must include an SQL expression.</span></span> <span data-ttu-id="82b98-104">CHECK 制約式をボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="82b98-104">Type the check constraint expression in the box provided.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="82b98-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="82b98-105">UI element list</span></span>  
 <span data-ttu-id="82b98-106">式</span><span class="sxs-lookup"><span data-stu-id="82b98-106">Expression</span></span>  
 <span data-ttu-id="82b98-107">式を入力します。</span><span class="sxs-lookup"><span data-stu-id="82b98-107">Enter the expression</span></span>  
  
 <span data-ttu-id="82b98-108">データが単一の条件を満たすかどうかを確認するには単一の制約式を作成し、データが複数の条件を満たすかどうかを確認するにはブール型の演算子を使用した複合式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="82b98-108">You can create a simple constraint expression to check data for a simple condition; or you can create a complex expression, using Boolean operators, to check data for several conditions.</span></span> <span data-ttu-id="82b98-109">たとえば、authors テーブルに、5 桁の文字列を必要とする zip 列が含まれていると仮定します。</span><span class="sxs-lookup"><span data-stu-id="82b98-109">For example, suppose the authors table has a zip column where a 5-digit character string is required.</span></span> <span data-ttu-id="82b98-110">このとき、次の制約式では、5 桁の数値だけが許可されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-110">This sample constraint expression guarantees that only 5-digit numbers are allowed:</span></span>  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
 <span data-ttu-id="82b98-111">または、sales テーブルに、0 より大きい値を必要とする qty という列が含まれていると仮定します。</span><span class="sxs-lookup"><span data-stu-id="82b98-111">Or suppose the sales table has a column called qty which requires a value greater than 0.</span></span> <span data-ttu-id="82b98-112">このとき、下に示す制約では、常に正の値だけが許可されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-112">This sample constraint guarantees that only positive values are allowed:</span></span>  
  
```  
qty > 0  
```  
  
 <span data-ttu-id="82b98-113">または、orders テーブルで、クレジット カードによる注文に使用できるクレジット カードの種類が制限されると仮定します。</span><span class="sxs-lookup"><span data-stu-id="82b98-113">Or suppose the orders table limits the type of credit cards accepted for all credit card orders.</span></span> <span data-ttu-id="82b98-114">このとき、下に示す制約では、クレジット カードでの注文時に、Visa、MasterCard、または American Express のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-114">This sample constraint guarantees that if the order is placed on a credit card, then only Visa, MasterCard, or American Express is accepted:</span></span>  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a><span data-ttu-id="82b98-115">制約式を定義するには</span><span class="sxs-lookup"><span data-stu-id="82b98-115">To define a constraint expression</span></span>  
 <span data-ttu-id="82b98-116">プロパティ ページの [制約のチェック] タブで、次の構文を使用して [制約式] ボックスに式を入力します。</span><span class="sxs-lookup"><span data-stu-id="82b98-116">In the Check Constraints tab of the property pages, type an expression in the Constraint expression box using the following syntax:</span></span>  
  
 `{constant | column_name | function | (subquery)}`  
  
 `[{operator | AND | OR | NOT}`  
  
 `{constant | column_name | function | (subquery)}...]`  
  
 <span data-ttu-id="82b98-117">SQL 構文は、次のパラメーターで構成されています。</span><span class="sxs-lookup"><span data-stu-id="82b98-117">The SQL syntax is made up of the following parameters:</span></span>  
  
|<span data-ttu-id="82b98-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82b98-118">Parameter</span></span>|<span data-ttu-id="82b98-119">説明</span><span class="sxs-lookup"><span data-stu-id="82b98-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82b98-120">定数 (constant)</span><span class="sxs-lookup"><span data-stu-id="82b98-120">constant</span></span>|<span data-ttu-id="82b98-121">数値データ、文字データなどのリテラル値です。</span><span class="sxs-lookup"><span data-stu-id="82b98-121">A literal value, such as numeric or character data.</span></span> <span data-ttu-id="82b98-122">文字データは単一引用符 (') で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="82b98-122">Character data must be enclosed within single quotation marks (').</span></span>|  
|<span data-ttu-id="82b98-123">column_name</span><span class="sxs-lookup"><span data-stu-id="82b98-123">column_name</span></span>|<span data-ttu-id="82b98-124">列を指定します。</span><span class="sxs-lookup"><span data-stu-id="82b98-124">Specifies a column.</span></span>|  
|<span data-ttu-id="82b98-125">関数 (function)</span><span class="sxs-lookup"><span data-stu-id="82b98-125">function</span></span>|<span data-ttu-id="82b98-126">組み込み関数です。</span><span class="sxs-lookup"><span data-stu-id="82b98-126">A built-in function.</span></span>|  
|<span data-ttu-id="82b98-127">operator</span><span class="sxs-lookup"><span data-stu-id="82b98-127">operator</span></span>|<span data-ttu-id="82b98-128">算術演算子、ビット処理演算子、比較演算子、または文字列演算子です。</span><span class="sxs-lookup"><span data-stu-id="82b98-128">Arithmetic, bitwise, comparison, or string operators.</span></span>|  
|<span data-ttu-id="82b98-129">AND</span><span class="sxs-lookup"><span data-stu-id="82b98-129">AND</span></span>|<span data-ttu-id="82b98-130">ブール式で 2 つの式を結合するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="82b98-130">Use in Boolean expressions to connect two expressions.</span></span> <span data-ttu-id="82b98-131">両方の式が true のとき、結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-131">Results are returned when both expressions are true.</span></span><br /><br /> <span data-ttu-id="82b98-132">1 つのステートメントで AND と OR が使用されているときは、AND が先に処理されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-132">When AND and OR are both used in a statement, AND is processed first.</span></span> <span data-ttu-id="82b98-133">実行順序は、かっこを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="82b98-133">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="82b98-134">OR</span><span class="sxs-lookup"><span data-stu-id="82b98-134">OR</span></span>|<span data-ttu-id="82b98-135">ブール式で 2 つ以上の条件を結合するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="82b98-135">Use in Boolean expressions to connect two or more conditions.</span></span> <span data-ttu-id="82b98-136">どちらかの条件が true のとき、結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-136">Results are returned when either condition is true.</span></span><br /><br /> <span data-ttu-id="82b98-137">1 つのステートメントで AND と OR が使用されているときは、OR は AND の後に処理されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-137">When AND and OR are both used in a statement, OR is evaluated after AND.</span></span> <span data-ttu-id="82b98-138">実行順序は、かっこを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="82b98-138">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="82b98-139">NOT</span><span class="sxs-lookup"><span data-stu-id="82b98-139">NOT</span></span>|<span data-ttu-id="82b98-140">LIKE、NULL、BETWEEN、IN、EXISTS などのキーワードを含むすべてのブール式を否定します。</span><span class="sxs-lookup"><span data-stu-id="82b98-140">Negates any Boolean expression (which can include keywords, such as LIKE, NULL, BETWEEN, IN, and EXISTS).</span></span><br /><br /> <span data-ttu-id="82b98-141">1 つのステートメントで複数の論理演算子が使用されているときは、NOT が先に処理されます。</span><span class="sxs-lookup"><span data-stu-id="82b98-141">When more than one logical operator is used in a statement, NOT is processed first.</span></span> <span data-ttu-id="82b98-142">実行順序は、かっこを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="82b98-142">You can change the order of execution by using parentheses.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82b98-143">参照</span><span class="sxs-lookup"><span data-stu-id="82b98-143">See Also</span></span>  
 <span data-ttu-id="82b98-144">[Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="82b98-144">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="82b98-145">UNIQUE 制約の作成</span><span class="sxs-lookup"><span data-stu-id="82b98-145">Create Unique Constraints</span></span>](../../relational-databases/tables/create-unique-constraints.md)  
  
  
