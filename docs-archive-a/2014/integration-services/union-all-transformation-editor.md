---
title: 全体結合変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7e84c106767aa897b2e419b51ca5b5c538501cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633199"
---
# <a name="union-all-transformation-editor"></a><span data-ttu-id="bd98c-102">全体結合変換エディター</span><span class="sxs-lookup"><span data-stu-id="bd98c-102">Union All Transformation Editor</span></span>
  <span data-ttu-id="bd98c-103">**[全体結合変換エディター]** ダイアログ ボックスを使用すると、複数の入力行セットを 1 つの出力行セットにマージできます。</span><span class="sxs-lookup"><span data-stu-id="bd98c-103">Use the **Union All Transformation Editor** dialog box to merge several input rowsets into a single output rowset.</span></span> <span data-ttu-id="bd98c-104">データ フローに全体結合変換を含めることで、複数のデータ フローのデータをマージしたり、全体結合変換を入れ子にして複雑なデータセットを作成したり、データ内のエラーを修正した後で行を再マージしたりできます。</span><span class="sxs-lookup"><span data-stu-id="bd98c-104">By including the Union All transformation in a data flow, you can merge data from multiple data flows, create complex datasets by nesting Union All transformations, and re-merge rows after you correct errors in the data.</span></span>  
  
 <span data-ttu-id="bd98c-105">全体結合変換の詳細については、「 [Union All Transformation](data-flow/transformations/union-all-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd98c-105">To learn more about the Union All transformation, see [Union All Transformation](data-flow/transformations/union-all-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bd98c-106">Options</span><span class="sxs-lookup"><span data-stu-id="bd98c-106">Options</span></span>  
 <span data-ttu-id="bd98c-107">**出力列の名前**</span><span class="sxs-lookup"><span data-stu-id="bd98c-107">**Output Column Name**</span></span>  
 <span data-ttu-id="bd98c-108">各列に対して別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="bd98c-108">Type an alias for each column.</span></span> <span data-ttu-id="bd98c-109">既定では最初の (参照) 入力の入力列の名前が使用されますが、一意なわかりやすい名前を任意に付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="bd98c-109">The default is the name of the input column from the first (reference) input; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="bd98c-110">**[全体結合 入力 1]**</span><span class="sxs-lookup"><span data-stu-id="bd98c-110">**Union All Input 1**</span></span>  
 <span data-ttu-id="bd98c-111">最初の (参照) 入力で使用可能な入力列を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="bd98c-111">Select from the list of available input columns in the first (reference) input.</span></span> <span data-ttu-id="bd98c-112">マップされた列のメタデータが一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd98c-112">The metadata of mapped columns must match.</span></span>  
  
 <span data-ttu-id="bd98c-113">**[全体結合 入力 n]**</span><span class="sxs-lookup"><span data-stu-id="bd98c-113">**Union All Input n**</span></span>  
 <span data-ttu-id="bd98c-114">2 番目およびその他の入力で使用可能な入力列を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="bd98c-114">Select from the list of available input columns in the second and additional inputs.</span></span> <span data-ttu-id="bd98c-115">マップされた列のメタデータが一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd98c-115">The metadata of mapped columns must match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd98c-116">参照</span><span class="sxs-lookup"><span data-stu-id="bd98c-116">See Also</span></span>  
 <span data-ttu-id="bd98c-117">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bd98c-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bd98c-118">[全体結合変換を使用してデータをマージする](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="bd98c-118">[Merge Data by Using the Union All Transformation](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span></span>  
 <span data-ttu-id="bd98c-119">[マージ変換](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="bd98c-119">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="bd98c-120">マージ結合変換</span><span class="sxs-lookup"><span data-stu-id="bd98c-120">Merge Join Transformation</span></span>](data-flow/transformations/merge-join-transformation.md)  
  
  
