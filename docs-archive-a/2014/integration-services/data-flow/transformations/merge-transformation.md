---
title: マージ変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d1d35e92b5978016b6a53956e5b6f1f6642f5ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740177"
---
# <a name="merge-transformation"></a><span data-ttu-id="dfbb0-102">マージ変換</span><span class="sxs-lookup"><span data-stu-id="dfbb0-102">Merge Transformation</span></span>
  <span data-ttu-id="dfbb0-103">マージ変換は、並べ替えられた 2 つのデータセットを 1 つのデータセットに結合します。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-103">The Merge transformation combines two sorted datasets into a single dataset.</span></span> <span data-ttu-id="dfbb0-104">各データセットの行は、各キー列の値に基づいて出力に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-104">The rows from each dataset are inserted into the output based on values in their key columns.</span></span>  
  
 <span data-ttu-id="dfbb0-105">データ フローにマージ変換を含めると、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-105">By including the Merge transformation in a data flow, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="dfbb0-106">テーブルやファイルなど、2 つのデータ ソースのデータをマージします。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-106">Merge data from two data sources, such as tables and files.</span></span>  
  
-   <span data-ttu-id="dfbb0-107">マージ変換を入れ子にして、複合データセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-107">Create complex datasets by nesting Merge transformations.</span></span>  
  
-   <span data-ttu-id="dfbb0-108">データのエラーを修正後、行を再マージします。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-108">Remerge rows after correcting errors in the data.</span></span>  
  
 <span data-ttu-id="dfbb0-109">マージ変換は、全体結合変換と似ています。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-109">The Merge transformation is similar to the Union All transformations.</span></span> <span data-ttu-id="dfbb0-110">次の場合には、マージ変換ではなく全体結合変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-110">Use the Union All transformation instead of the Merge transformation in the following situations:</span></span>  
  
-   <span data-ttu-id="dfbb0-111">変換入力の並べ替えを行わない場合。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-111">The transformation inputs are not sorted.</span></span>  
  
-   <span data-ttu-id="dfbb0-112">結合された出力を並べ替える必要がない場合。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-112">The combined output does not need to be sorted.</span></span>  
  
-   <span data-ttu-id="dfbb0-113">マージ変換は 3 つ以上の入力をとります。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-113">The transformation has more than two inputs.</span></span>  
  
## <a name="input-requirements"></a><span data-ttu-id="dfbb0-114">入力要件</span><span class="sxs-lookup"><span data-stu-id="dfbb0-114">Input Requirements</span></span>  
 <span data-ttu-id="dfbb0-115">マージ変換では、入力データが並べ替えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-115">The Merge Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="dfbb0-116">この重要な要件の詳細については、「 [マージ変換およびマージ結合変換用にデータを並べ替える](sort-data-for-the-merge-and-merge-join-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-116">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="dfbb0-117">マージ変換では、入力されたマージ列のメタデータが一致している必要もあります。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-117">The Merge transformation also requires that the merged columns in its inputs have matching metadata.</span></span> <span data-ttu-id="dfbb0-118">たとえば、数値データ型の列と文字データ型の列はマージできません。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-118">For example, you cannot merge a column that has a numeric data type with a column that has a character data type.</span></span> <span data-ttu-id="dfbb0-119">データが文字列データ型の場合、2 番目の入力の列の長さは、マージ先の最初の入力の列の長さ以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-119">If the data has a string data type, the length of the column in the second input must be less than or equal to the length of the column in the first input with which it is merged.</span></span>  
  
 <span data-ttu-id="dfbb0-120">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーのマージ変換のユーザー インターフェイスでは、同じメタデータを持つ列は自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-120">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the user interface for the Merge transformation automatically maps columns that have the same metadata.</span></span> <span data-ttu-id="dfbb0-121">互換性のあるデータ型を持つ他の列は、手動でマップできます。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-121">You can then manually map other columns that have compatible data types.</span></span>  
  
 <span data-ttu-id="dfbb0-122">この変換は、2 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-122">This transformation has two inputs and one output.</span></span> <span data-ttu-id="dfbb0-123">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-123">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-merge-transformation"></a><span data-ttu-id="dfbb0-124">マージ変換の構成</span><span class="sxs-lookup"><span data-stu-id="dfbb0-124">Configuration of the Merge Transformation</span></span>  
 <span data-ttu-id="dfbb0-125">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-125">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="dfbb0-126">**[マージ変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [マージ変換エディター](../../merge-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-126">For more information about the properties that you can set in the **Merge Transformation Editor** dialog box, see [Merge Transformation Editor](../../merge-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="dfbb0-127">プログラムによって設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-127">For more information about the properties that you can programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="dfbb0-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="dfbb0-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="dfbb0-129">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="dfbb0-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="dfbb0-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="dfbb0-130">Related Tasks</span></span>  
 <span data-ttu-id="dfbb0-131">プロパティの設定方法の詳細については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfbb0-131">For details about how to set properties, see the following topics:</span></span>  
  
-   [<span data-ttu-id="dfbb0-132">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="dfbb0-132">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="dfbb0-133">マージ変換およびマージ結合変換用にデータを並べ替える</span><span class="sxs-lookup"><span data-stu-id="dfbb0-133">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="dfbb0-134">参照</span><span class="sxs-lookup"><span data-stu-id="dfbb0-134">See Also</span></span>  
 <span data-ttu-id="dfbb0-135">[マージ結合変換](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="dfbb0-135">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="dfbb0-136">[全体結合変換](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="dfbb0-136">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="dfbb0-137">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="dfbb0-137">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="dfbb0-138">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="dfbb0-138">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
