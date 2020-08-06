---
title: データマイニングディメンションを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 265cf671bbc825258f0b2bd6627690e8c52f252b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711154"
---
# <a name="create-a-data-mining-dimension"></a><span data-ttu-id="3e383-102">データ マイニング ディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="3e383-102">Create a Data Mining Dimension</span></span>
  <span data-ttu-id="3e383-103">マイニング構造が OLAP キューブに基づいている場合は、マイニング モデルのコンテンツが含まれているディメンションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3e383-103">If your mining structure is based on an OLAP cube, you can create a dimension that contains the content of the mining model.</span></span> <span data-ttu-id="3e383-104">作成したディメンションは、ソース キューブに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="3e383-104">You can then incorporate the dimension back into the source cube.</span></span>  
  
 <span data-ttu-id="3e383-105">また、ディメンションの参照、ディメンションによるモデルの結果の調査、または MDX によるディメンションに対するクエリを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="3e383-105">You can also browse the dimension, use it to explore the model results, or query the dimension using MDX.</span></span>  
  
### <a name="to-create-a-data-mining-dimension"></a><span data-ttu-id="3e383-106">データ マイニング ディメンションを作成するには</span><span class="sxs-lookup"><span data-stu-id="3e383-106">To create a data mining dimension</span></span>  
  
1.  <span data-ttu-id="3e383-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のデータ マイニング デザイナーで、 **[マイニング構造]** タブまたは **[マイニング モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e383-107">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], select either the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="3e383-108">**[マイニング モデル]** メニューの **[データ マイニング ディメンションの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e383-108">From the **Mining Model** menu, select **Create a Data Mining Dimension**.</span></span>  
  
     <span data-ttu-id="3e383-109">**[データ マイニング ディメンションの作成]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="3e383-109">The **Create Data Mining Dimension** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="3e383-110">**[データ マイニング ディメンションの作成]** ダイアログ ボックスの **[モデル名]** 一覧で、OLAP マイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3e383-110">In the **Model name** list of the **Create Data Mining Dimension** dialog box, select an OLAP mining model.</span></span>  
  
4.  <span data-ttu-id="3e383-111">**[ディメンション名]** ボックスに、新しいデータ マイニング ディメンションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3e383-111">In the **Dimension name** box, enter a name for the new data mining dimension.</span></span>  
  
5.  <span data-ttu-id="3e383-112">新しいデータ マイニング ディメンションが含まれているキューブを作成するには、 **[キューブを作成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e383-112">If you want to create a cube that includes the new data mining dimension, select **Create cube**.</span></span> <span data-ttu-id="3e383-113">**[キューブを作成する]** を選択すると、キューブの新しい名前を入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3e383-113">After you select **Create cube**, you can enter a new name for the cube.</span></span>  
  
6.  <span data-ttu-id="3e383-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e383-114">Click **OK**.</span></span>  
  
     <span data-ttu-id="3e383-115">データ マイニング ディメンションが作成され、ソリューション エクスプローラーの **[ディメンション]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3e383-115">The data mining dimension is created and is added to the **Dimensions** folder in Solution Explorer.</span></span> <span data-ttu-id="3e383-116">**[キューブを作成する]** を選択した場合は、新しいキューブも作成され、 **[キューブ]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3e383-116">If you selected **Create cube**, a new cube is also created and is added to the **Cubes** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e383-117">参照</span><span class="sxs-lookup"><span data-stu-id="3e383-117">See Also</span></span>  
 [<span data-ttu-id="3e383-118">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="3e383-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
