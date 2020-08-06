---
title: 全体結合変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eaaab1abf2587979e947cc1be24cbedf8f61b6e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644048"
---
# <a name="union-all-transformation"></a><span data-ttu-id="cdb98-102">全体結合変換</span><span class="sxs-lookup"><span data-stu-id="cdb98-102">Union All Transformation</span></span>
  <span data-ttu-id="cdb98-103">全体結合変換は、複数の入力を 1 つの出力に結合します。</span><span class="sxs-lookup"><span data-stu-id="cdb98-103">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="cdb98-104">たとえば、5 つの異なるフラット ファイル ソースからの出力を全体結合変換への入力とし、1 つの出力に結合できます。</span><span class="sxs-lookup"><span data-stu-id="cdb98-104">For example, the outputs from five different Flat File sources can be inputs to the Union All transformation and combined into one output.</span></span>  
  
## <a name="inputs-and-outputs"></a><span data-ttu-id="cdb98-105">入力および出力</span><span class="sxs-lookup"><span data-stu-id="cdb98-105">Inputs and Outputs</span></span>  
 <span data-ttu-id="cdb98-106">変換入力は、変換出力に 1 つずつ追加されます。行の並べ替えは発生しません。</span><span class="sxs-lookup"><span data-stu-id="cdb98-106">The transformation inputs are added to the transformation output one after the other; no reordering of rows occurs.</span></span> <span data-ttu-id="cdb98-107">パッケージで並べ替え出力が必要な場合は、全体結合変換ではなくマージ変換を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdb98-107">If the package requires a sorted output, you should use the Merge transformation instead of the Union All transformation.</span></span>  
  
 <span data-ttu-id="cdb98-108">全体結合変換に連結した最初の入力が変換出力のソースとなり、これから変換出力が作成されます。</span><span class="sxs-lookup"><span data-stu-id="cdb98-108">The first input that you connect to the Union All transformation is the input from which the transformation creates the transformation output.</span></span> <span data-ttu-id="cdb98-109">全体結合変換に次に連結した入力の列は、変換出力の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="cdb98-109">The columns in the inputs you subsequently connect to the transformation are mapped to the columns in the transformation output.</span></span>  
  
 <span data-ttu-id="cdb98-110">入力をマージするには、入力の列を出力の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="cdb98-110">To merge inputs, you map columns in the inputs to columns in the output.</span></span> <span data-ttu-id="cdb98-111">最低 1 つの入力の列を、各出力列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdb98-111">A column from at least one input must be mapped to each output column.</span></span> <span data-ttu-id="cdb98-112">2 つの列の間のマッピングでは、列のメタデータが一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdb98-112">The mapping between two columns requires that the metadata of the columns match.</span></span> <span data-ttu-id="cdb98-113">たとえば、マップされた列は同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdb98-113">For example, the mapped columns must have the same data type.</span></span>  
  
 <span data-ttu-id="cdb98-114">マップされた列に文字列データが含まれ、出力列の長さが入力列の長さよりも短い場合、入力列を含めることができるように、出力列の長さが自動的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="cdb98-114">If the mapped columns contain string data and the output column is shorter in length than the input column, the output column is automatically increased in length to contain the input column.</span></span> <span data-ttu-id="cdb98-115">出力列にマップされない入力列は、出力列の値が NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cdb98-115">Input columns that are not mapped to output columns are set to null values in the output columns.</span></span>  
  
 <span data-ttu-id="cdb98-116">この変換は、複数の入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="cdb98-116">This transformation has multiple inputs and one output.</span></span> <span data-ttu-id="cdb98-117">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cdb98-117">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-union-all-transformation"></a><span data-ttu-id="cdb98-118">全体結合変換の構成</span><span class="sxs-lookup"><span data-stu-id="cdb98-118">Configuration of the Union All Transformation</span></span>  
 <span data-ttu-id="cdb98-119">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="cdb98-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cdb98-120">**[全体結合変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [全体結合変換エディター](../../union-all-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdb98-120">For more information about the properties that you can set in the **Union All Transformation Editor** dialog box, see [Union All Transformation Editor](../../union-all-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="cdb98-121">プログラムによって設定できるプロパティの詳細については、「 [共通プロパティ](../../common-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdb98-121">For more information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
 <span data-ttu-id="cdb98-122">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdb98-122">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cdb98-123">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="cdb98-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="cdb98-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cdb98-124">Related Tasks</span></span>  
 [<span data-ttu-id="cdb98-125">全体結合変換を使用してデータをマージする</span><span class="sxs-lookup"><span data-stu-id="cdb98-125">Merge Data by Using the Union All Transformation</span></span>](union-all-transformation.md)  
  
  
