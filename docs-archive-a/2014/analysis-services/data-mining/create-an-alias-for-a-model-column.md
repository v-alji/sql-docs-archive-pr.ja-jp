---
title: モデル列の別名を作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 908c0a8d8caa810badf4b82dc3dd3f411d09f323
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632786"
---
# <a name="create-an-alias-for-a-model-column"></a><span data-ttu-id="fe5a1-102">モデル列の別名の作成</span><span class="sxs-lookup"><span data-stu-id="fe5a1-102">Create an Alias for a Model Column</span></span>
  <span data-ttu-id="fe5a1-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、モデル列の別名を作成できます。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create an alias for a model column.</span></span> <span data-ttu-id="fe5a1-104">この機能は、マイニング構造名が長すぎて扱いにくい場合や、内容またはモデル内での使い方をわかりやすくするために列名を変更する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-104">This might be useful when the mining structure name is too long to easily work with, or when you want to rename the column to be more descriptive of its contents or usage in the model.</span></span> <span data-ttu-id="fe5a1-105">たとえば、構造列のコピーを作成して特定のモデル専用に列を分離すると、列名を変更して内容を正確に反映できます。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-105">For example, if you make a copy of a structure column and then discretize the column differently for a particular model, you can rename the column to reflect the content more accurately.</span></span>  
  
 <span data-ttu-id="fe5a1-106">モデル列の別名を作成するには、 **[プロパティ]** ペインを使用し、列の [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-106">To create an alias for a model column, you use the **Properties** pane and set the [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) property of the column.</span></span>  
  
 <span data-ttu-id="fe5a1-107">データ マイニング デザイナーの **[マイニング モデル]** タブに、列の使用法のラベルの横にかっこで囲まれて別名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-107">On the **Mining Models** tab of Data Mining Designer, the alias appears enclosed in parentheses next to the column usage label.</span></span>  
  
 <span data-ttu-id="fe5a1-108">マイニング モデルのプロパティを設定する方法については、「 [マイニング モデル列](mining-model-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-108">For information about how to set the properties of a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a><span data-ttu-id="fe5a1-109">マイニング モデル列に別名を追加するには</span><span class="sxs-lookup"><span data-stu-id="fe5a1-109">To add an alias to a mining model column</span></span>  
  
1.  <span data-ttu-id="fe5a1-110">データ マイニング デザイナーの **[マイニング モデル]** タブで、変更するマイニング列のマイニング モデル内のセルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-110">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the mining model for the mining column that you want to change, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="fe5a1-111">画面の右側の **[プロパティ]** ウィンドウで、Name プロパティの横のセルをクリックし、現在の値を削除します。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-111">In the **Properties** window on the right side of the screen, click the cell next to the Name property and delete the current value.</span></span> <span data-ttu-id="fe5a1-112">列の新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe5a1-112">Type a new name for the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5a1-113">参照</span><span class="sxs-lookup"><span data-stu-id="fe5a1-113">See Also</span></span>  
 <span data-ttu-id="fe5a1-114">[マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="fe5a1-114">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="fe5a1-115">マイニング モデルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="fe5a1-115">Mining Model Properties</span></span>](mining-model-properties.md)  
  
  
