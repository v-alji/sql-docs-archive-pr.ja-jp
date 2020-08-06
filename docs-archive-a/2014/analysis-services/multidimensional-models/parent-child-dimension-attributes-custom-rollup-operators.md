---
title: 親子ディメンションのカスタムロールアップ演算子 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: db12ccc6703ee4863dd3b6bd598d2317b54fce6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642370"
---
# <a name="custom-rollup-operators-in-parent-child-dimensions"></a><span data-ttu-id="00da8-102">親子ディメンションのカスタム ロールアップ演算子</span><span class="sxs-lookup"><span data-stu-id="00da8-102">Custom Rollup Operators in Parent-Child Dimensions</span></span>
  <span data-ttu-id="00da8-103">カスタム ロールアップ演算子を使用すると、親子階層でメンバーの値を親の値にロール アップする方法を簡単に制御できます。</span><span class="sxs-lookup"><span data-stu-id="00da8-103">Custom rollup operators provide a simple way to control how member values are rolled up into parent values in a parent-child hierarchy.</span></span> <span data-ttu-id="00da8-104">親子リレーションシップを含んでいるディメンションでは、親属性のすべての計算されないメンバーのロールアップを指定する単項演算子を含んでいる列を指定します。</span><span class="sxs-lookup"><span data-stu-id="00da8-104">In a dimension containing a parent-child relationship, you specify a column that contains unary operators that specify rollup for all noncalculated members of the parent attribute.</span></span> <span data-ttu-id="00da8-105">単項演算子は、親メンバーの値が評価されるたびにメンバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="00da8-105">The unary operator is applied to members whenever the values of the parent members are evaluated.</span></span>  
  
 <span data-ttu-id="00da8-106">単項演算子は、親属性の `UnaryOperatorColumn` プロパティで定義した列に保存され、属性の各メンバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="00da8-106">The unary operators are stored in column defined by the `UnaryOperatorColumn` property of the parent attribute, and they are applied to each member of the attribute.</span></span> <span data-ttu-id="00da8-107">このプロパティで指定する列は、ディメンション テーブルに存在するか、ディメンション テーブル内の外部キーによってそのディメンション テーブルに関連付けられているテーブルに存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00da8-107">The column specified by this property can reside either in the dimension table or in a table related to the dimension table by a foreign key in the dimension table.</span></span>  
  
 <span data-ttu-id="00da8-108">カスタム ロールアップ演算子の機能は、カスタム メンバー式に似ていますが、それよりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="00da8-108">Custom rollup operators provide functionality similar to, but more simplified than, custom member formulas.</span></span> <span data-ttu-id="00da8-109">カスタム メンバー式では、多次元式 (MDX) を使用して、メンバーのロール アップ方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="00da8-109">A custom member formula uses Multidimensional Expressions (MDX) expressions to determine how the members are rolled up.</span></span> <span data-ttu-id="00da8-110">これに対し、カスタム ロールアップ演算子では、単純な単項演算子を使用して、メンバーの値が親に与える影響を決定します。</span><span class="sxs-lookup"><span data-stu-id="00da8-110">In contrast, a custom rollup operator uses a simple unary operator to determine how the value of a member affects the parent.</span></span> <span data-ttu-id="00da8-111">ディメンション内の前のレベルのカスタム メンバー式は、レベルのカスタム ロールアップ演算子をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="00da8-111">Custom member formulas of the preceding level in a dimension override a level's custom rollup operator.</span></span>  
  
## <a name="custom-rollup-precedence"></a><span data-ttu-id="00da8-112">カスタム ロールアップの優先順位</span><span class="sxs-lookup"><span data-stu-id="00da8-112">Custom Rollup Precedence</span></span>  
 <span data-ttu-id="00da8-113">優先順位の面では、階層内のレベルのソース属性のカスタム ロールアップ演算子は、前のレベルのカスタム メンバー式をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="00da8-113">In terms of precedence, the custom rollup operators of the source attribute for a level in a hierarchy override the custom member formulas of the previous level.</span></span> <span data-ttu-id="00da8-114">ただし、前のレベルのカスタムメンバー式は、レベルのカスタム ロールアップ演算子をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="00da8-114">However, the custom member formulas of the preceding level override the custom rollup operators of a level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00da8-115">参照</span><span class="sxs-lookup"><span data-stu-id="00da8-115">See Also</span></span>  
 <span data-ttu-id="00da8-116">[カスタムメンバー式の定義](attribute-properties-define-custom-member-formulas.md) </span><span class="sxs-lookup"><span data-stu-id="00da8-116">[Define Custom Member Formulas](attribute-properties-define-custom-member-formulas.md) </span></span>  
 [<span data-ttu-id="00da8-117">親子ディメンションの単項演算子</span><span class="sxs-lookup"><span data-stu-id="00da8-117">Unary Operators in Parent-Child Dimensions</span></span>](parent-child-dimension-attributes-unary-operators.md)  
  
  
