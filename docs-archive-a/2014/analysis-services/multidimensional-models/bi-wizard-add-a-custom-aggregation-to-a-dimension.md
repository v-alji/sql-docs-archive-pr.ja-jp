---
title: ディメンションへのカスタム集計の追加 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed843b8b0005ff62f05b13ebd20024d528857388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632157"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a><span data-ttu-id="27bbc-102">ディメンションへのカスタム集計の追加</span><span class="sxs-lookup"><span data-stu-id="27bbc-102">Add a Custom Aggregation to a Dimension</span></span>
  <span data-ttu-id="27bbc-103">カスタム集計拡張機能をキューブまたはディメンションに追加して、ディメンション メンバーに関連付けられている既定の集計を、別の単項演算子に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="27bbc-103">Add a custom aggregation enhancement to a cube or dimension to replace the default aggregations that are associated with a dimension member with a different unary operator.</span></span> <span data-ttu-id="27bbc-104">この拡張機能では、親子階層内のメンバーのロールアップを定義する単項演算子列がディメンション テーブルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="27bbc-104">This enhancement specifies a unary operator column in the dimension table that defines rollup for members in a parent-child hierarchy.</span></span> <span data-ttu-id="27bbc-105">単項演算子は、親子階層内の親属性に適用されます。</span><span class="sxs-lookup"><span data-stu-id="27bbc-105">The unary operator acts on the parent attribute in a parent-child hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27bbc-106">カスタム集計は、既存のデータ ソースを基にしたディメンションにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="27bbc-106">A custom aggregation is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="27bbc-107">データ ソースを使用せずに作成されたディメンションに対しては、スキーマ生成ウィザードを実行し、データ ソース ビューを作成してからカスタム集計を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27bbc-107">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding the custom aggregation.</span></span>  
  
 <span data-ttu-id="27bbc-108">カスタム集計を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページで **[単項演算子の指定]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="27bbc-108">To add a custom aggregation, you use the Business Intelligence Wizard, and select the **Specify a unary operator** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="27bbc-109">次に、このウィザードでは、カスタム集計の適用先のディメンションを選択し、カスタム集計を識別する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="27bbc-109">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom aggregation and identifying the custom aggregation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27bbc-110">ビジネス インテリジェンス ウィザードを実行してカスタム集計を追加する前に、拡張するディメンションに親子属性階層が含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="27bbc-110">Before you run the Business Intelligence Wizard to add a custom aggregation, make sure that the dimension that you want to enhance contains a parent-child attribute hierarchy.</span></span> <span data-ttu-id="27bbc-111">詳細については、「[親子階層](parent-child-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27bbc-111">For more information, see [Parent-Child Hierarchy](parent-child-dimension.md).</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="27bbc-112">ディメンションの選択</span><span class="sxs-lookup"><span data-stu-id="27bbc-112">Selecting a Dimension</span></span>  
 <span data-ttu-id="27bbc-113">ウィザードの最初の **[単項演算子の指定]** ページで、カスタム集計の適用先のディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="27bbc-113">On the first **Specify a Unary Operator** page of the wizard, you specify the dimension to which you want to apply a custom aggregation.</span></span> <span data-ttu-id="27bbc-114">この選択したディメンションに追加されるカスタム集計が、ディメンションへの変更内容になります。</span><span class="sxs-lookup"><span data-stu-id="27bbc-114">The custom aggregation added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="27bbc-115">これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="27bbc-115">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="adding-custom-aggregation-unary-operator"></a><span data-ttu-id="27bbc-116">カスタム集計 (単項演算子) の追加</span><span class="sxs-lookup"><span data-stu-id="27bbc-116">Adding Custom Aggregation (Unary Operator)</span></span>  
 <span data-ttu-id="27bbc-117">**[単項演算子の指定]** の次のページで、カスタム集計の親属性と、単項演算子のディメンション テーブル内の基になる列を指定します。</span><span class="sxs-lookup"><span data-stu-id="27bbc-117">On the second **Specify a Unary Operator** page, you specify the parent attribute that you want for the custom aggregation and the source column in the dimension table for the unary operator.</span></span> <span data-ttu-id="27bbc-118">**親属性**は、プロパティがに設定されている属性を一覧表示 `Usage` `Parent` します。</span><span class="sxs-lookup"><span data-stu-id="27bbc-118">**Parent attribute** lists attributes that have their `Usage` property set to `Parent`.</span></span> <span data-ttu-id="27bbc-119">複数の親属性が存在する場合は、使用する親子リレーションシップに対応する親属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="27bbc-119">If there is more than one parent attribute, choose the parent attribute that corresponds to the parent-child relationship that you want to use.</span></span> <span data-ttu-id="27bbc-120">親属性が一覧に含まれていない場合、ディメンションには有効な親子階層が存在していません。</span><span class="sxs-lookup"><span data-stu-id="27bbc-120">If there is no parent attribute listed, then the dimension does not have a valid parent-child hierarchy.</span></span>  
  
 <span data-ttu-id="27bbc-121">**[基になる列]** で、単項演算子を含む文字列の列を選択します</span><span class="sxs-lookup"><span data-stu-id="27bbc-121">In **Source column**, you select the string column that contains the unary operators.</span></span> <span data-ttu-id="27bbc-122">(この選択によって、親属性のプロパティが設定さ `UnaryOperatorColumn` れます)。ディメンションテーブルには、単項ロールアップ演算子を指定する文字列列も必要です。</span><span class="sxs-lookup"><span data-stu-id="27bbc-122">(This selection sets the `UnaryOperatorColumn` property on the parent attribute.) The dimension table should also have a string column that specifies the unary rollup operator.</span></span> <span data-ttu-id="27bbc-123">この列の文字列値には、有効な集計演算子が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="27bbc-123">The string values in this column should contain valid aggregation operators.</span></span> <span data-ttu-id="27bbc-124">行が空の場合は、対応するメンバーが普通に計算されます。</span><span class="sxs-lookup"><span data-stu-id="27bbc-124">If a row is empty, the corresponding member is calculated normally.</span></span> <span data-ttu-id="27bbc-125">列の式が有効でない場合は、そのメンバーを使用するセル値が取得されたときに実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="27bbc-125">If the formula in a column is not valid, a run-time error occurs when a cell value that uses the member is retrieved.</span></span> <span data-ttu-id="27bbc-126">詳細については、 [「親子ディメンションの単項演算子」](parent-child-dimension-attributes-unary-operators.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27bbc-126">For more information, see [Unary Operators in Parent-Child Dimensions](parent-child-dimension-attributes-unary-operators.md).</span></span>  
  
  
