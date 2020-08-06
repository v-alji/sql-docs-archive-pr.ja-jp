---
title: 多次元モデルのパースペクティブ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- hiding objects from perspective
- renaming perspectives
- attributes [Analysis Services], default members
- removing perspectives
- perspectives [Analysis Services]
- names [Analysis Services], perspectives
- cubes [Analysis Services], perspectives
- deleting perspectives
ms.assetid: 5a3d6577-6833-4c24-820c-b65bb856157b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2d4be87ddbd691710b361d8b07d225bce37659fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634108"
---
# <a name="perspectives-in-multidimensional-models"></a><span data-ttu-id="4b076-102">多次元モデルのパースペクティブ</span><span class="sxs-lookup"><span data-stu-id="4b076-102">Perspectives in Multidimensional Models</span></span>
  <span data-ttu-id="4b076-103">パースペクティブは、特定のアプリケーションまたはユーザーのグループに対して作成されるキューブのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="4b076-103">A perspective is a subset of a cube created for a particular application or group of users.</span></span> <span data-ttu-id="4b076-104">キューブ自体は既定のパースペクティブになります。</span><span class="sxs-lookup"><span data-stu-id="4b076-104">The cube itself is the default perspective.</span></span> <span data-ttu-id="4b076-105">パースペクティブは、キューブとしてクライアントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b076-105">A perspective is exposed to a client as a cube.</span></span> <span data-ttu-id="4b076-106">ユーザーがパースペクティブを表示すると、キューブと同じように表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b076-106">When a user views a perspective, it appears like another cube.</span></span> <span data-ttu-id="4b076-107">パースペクティブで書き戻しによりキューブ データに行われる変更は、元のキューブに対して行われます。</span><span class="sxs-lookup"><span data-stu-id="4b076-107">Any changes made to cube data through writeback in the perspective are to the original cube.</span></span> <span data-ttu-id="4b076-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のビューの詳細については、「 [パースペクティブ](../multidimensional-models-olap-logical-cube-objects/perspectives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b076-108">For more information about the views in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Perspectives](../multidimensional-models-olap-logical-cube-objects/perspectives.md).</span></span>  
  
 <span data-ttu-id="4b076-109">キューブのパースペクティブを作成または変更するには、キューブ デザイナーの **[パースペクティブ]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b076-109">Use the **Perspectives** tab in Cube Designer to create or modify perspectives in a cube.</span></span> <span data-ttu-id="4b076-110">**[パースペクティブ]** タブの最初の列は **[キューブ オブジェクト]** 列で、この列にはキューブ内のオブジェクトがすべて一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b076-110">The first column of the **Perspectives** tab is the **Cube Objects** column, which lists all the objects in the cube.</span></span> <span data-ttu-id="4b076-111">これは、キューブ自体である、キューブの既定のパースペクティブに対応しています。</span><span class="sxs-lookup"><span data-stu-id="4b076-111">This corresponds to the default perspective for the cube, which is the cube itself.</span></span>  
  
## <a name="creating-or-deleting-perspectives"></a><span data-ttu-id="4b076-112">パースペクティブの作成または削除</span><span class="sxs-lookup"><span data-stu-id="4b076-112">Creating or Deleting Perspectives</span></span>  
 <span data-ttu-id="4b076-113">パースペクティブを **[パースペクティブ]** タブに追加するには、 **[キューブ]** メニューの **[新しいパースペクティブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b076-113">You can add a perspective to the **Perspectives** tab by clicking **New Perspective** on the **Cube** menu.</span></span> <span data-ttu-id="4b076-114">ツール バーの **[新しいパースペクティブ]** ボタンをクリックするか、ペイン内を右クリックしてショートカット メニューの **[新しいパースペクティブ]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4b076-114">You can also click the **New Perspective** button on the toolbar, or right-click anywhere in the pane and click **New Perspective** on the shortcut menu.</span></span> <span data-ttu-id="4b076-115">キューブに追加できるパースペクティブの数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="4b076-115">You can add any number of perspectives to a cube.</span></span>  
  
 <span data-ttu-id="4b076-116">パースペクティブを削除するには、削除するパースペクティブの列内の任意のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b076-116">To remove a perspective, first click any cell in the column for the perspective that you want to delete.</span></span> <span data-ttu-id="4b076-117">次に、 **[キューブ]** メニューで、 **[パースペクティブの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b076-117">Then, on the **Cube** menu, click **Delete Perspective**.</span></span> <span data-ttu-id="4b076-118">ツール バーの **[パースペクティブの削除]** ボタンをクリックするか、削除するパースペクティブ内の任意のセルを右クリックし、ショートカット メニューの **[パースペクティブの削除]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4b076-118">You can also click the **Delete Perspective** button on the toolbar, or right-click any cell in the perspective you want to delete, and then click **Delete Perspective** on the shortcut menu.</span></span>  
  
## <a name="renaming-perspectives"></a><span data-ttu-id="4b076-119">パースペクティブ名の変更</span><span class="sxs-lookup"><span data-stu-id="4b076-119">Renaming Perspectives</span></span>  
 <span data-ttu-id="4b076-120">各パースペクティブの最初の行には、パースペクティブの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b076-120">The first row of each perspective shows its name.</span></span> <span data-ttu-id="4b076-121">パースペクティブを作成したときの初期の名前は「パースペクティブ」になります (「パースペクティブ」という名前が既に存在する場合は、1 から始まる序数が名前の後に付けられます)。</span><span class="sxs-lookup"><span data-stu-id="4b076-121">When you create a perspective, the name is initially Perspective (followed by an ordinal number, starting with 1, if there is already a perspective called Perspective).</span></span> <span data-ttu-id="4b076-122">この名前をクリックすると、名前を編集できます。</span><span class="sxs-lookup"><span data-stu-id="4b076-122">You can click the name to edit it.</span></span>  
  
## <a name="hiding-objects-from-a-perspective"></a><span data-ttu-id="4b076-123">パースペクティブのオブジェクトの非表示</span><span class="sxs-lookup"><span data-stu-id="4b076-123">Hiding Objects from a Perspective</span></span>  
 <span data-ttu-id="4b076-124">パースペクティブのオブジェクトを非表示にするには、パースペクティブの列にあるオブジェクトに対応する行のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="4b076-124">To hide an object from a perspective, clear the check box in the row that corresponds to the object in the column for the perspective.</span></span> <span data-ttu-id="4b076-125">パースペクティブで非表示にできるキューブ オブジェクトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4b076-125">The cube objects that can be hidden from a perspective are:</span></span>  
  
-   <span data-ttu-id="4b076-126">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="4b076-126">Measure groups</span></span>  
  
-   <span data-ttu-id="4b076-127">メジャー</span><span class="sxs-lookup"><span data-stu-id="4b076-127">Measures</span></span>  
  
-   <span data-ttu-id="4b076-128">Dimensions</span><span class="sxs-lookup"><span data-stu-id="4b076-128">Dimensions</span></span>  
  
-   <span data-ttu-id="4b076-129">階層</span><span class="sxs-lookup"><span data-stu-id="4b076-129">Hierarchies</span></span>  
  
-   <span data-ttu-id="4b076-130">名前付きセット</span><span class="sxs-lookup"><span data-stu-id="4b076-130">Named sets</span></span>  
  
-   <span data-ttu-id="4b076-131">KPI</span><span class="sxs-lookup"><span data-stu-id="4b076-131">KPIs</span></span>  
  
-   <span data-ttu-id="4b076-132">Actions</span><span class="sxs-lookup"><span data-stu-id="4b076-132">Actions</span></span>  
  
-   <span data-ttu-id="4b076-133">計算されるメンバー</span><span class="sxs-lookup"><span data-stu-id="4b076-133">Calculated members</span></span>  
  
 <span data-ttu-id="4b076-134">オブジェクトを表示するには、**[キューブ オブジェクト]** の下にあるオブジェクトの種類のカテゴリ ( **[メジャー グループ]**、 **[ディメンション]**、 **[KPI]**、 **[計算]**、または **[アクション]**) を展開します。</span><span class="sxs-lookup"><span data-stu-id="4b076-134">To view any object, expand the category (**Measure Groups**, **Dimensions**, **KPIs**, **Calculations**, or **Actions**) for any object type under **Cube Objects**.</span></span> <span data-ttu-id="4b076-135">ディメンション内の階層または属性を表示するには、まず、ディメンションを展開してから、 **[階層]** または **[属性]** 行を展開します。</span><span class="sxs-lookup"><span data-stu-id="4b076-135">To view hierarchies or attributes in a dimension, first expand a dimension, and then expand the **Hierarchies** or **Attributes** row.</span></span> <span data-ttu-id="4b076-136">メジャー グループ内のメジャーを表示するには、メジャー グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b076-136">To view measures in a measure group, expand the measure group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b076-137">参照</span><span class="sxs-lookup"><span data-stu-id="4b076-137">See Also</span></span>  
 [<span data-ttu-id="4b076-138">多次元モデルのキューブ</span><span class="sxs-lookup"><span data-stu-id="4b076-138">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
