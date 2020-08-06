---
title: パースペクティブの作成と管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d0029ff61aa05e2e83f34833c3d0af17ddb3beb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632755"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a><span data-ttu-id="c807d-102">パースペクティブの作成と管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="c807d-102">Create and Manage Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="c807d-103">パースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="c807d-103">Perspectives define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span> <span data-ttu-id="c807d-104">このトピックのタスクでは、モデル デザイナーで **[パースペクティブ]** ダイアログ ボックスを使用して、パースペクティブを作成し管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c807d-104">The tasks in this topic describe how to create and manage perspectives by using the **Perspectives** dialog box in the model designer.</span></span>  
  
 <span data-ttu-id="c807d-105">このトピックでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c807d-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="c807d-106">パースペクティブを追加するには</span><span class="sxs-lookup"><span data-stu-id="c807d-106">To add a perspective</span></span>](#bkmk_add)  
  
-   [<span data-ttu-id="c807d-107">パースペクティブを編集するには</span><span class="sxs-lookup"><span data-stu-id="c807d-107">To edit a perspective</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="c807d-108">パースペクティブの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="c807d-108">To rename a perspective</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="c807d-109">パースペクティブを削除するには</span><span class="sxs-lookup"><span data-stu-id="c807d-109">To delete a perspective</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="c807d-110">パースペクティブをコピーするには</span><span class="sxs-lookup"><span data-stu-id="c807d-110">To copy a perspective</span></span>](#bkmk_copy)  
  
## <a name="tasks"></a><span data-ttu-id="c807d-111">タスク</span><span class="sxs-lookup"><span data-stu-id="c807d-111">Tasks</span></span>  
 <span data-ttu-id="c807d-112">パースペクティブを作成するには、 **[パースペクティブ]** ダイアログ ボックスを使用します。このダイアログ ボックスでは、パースペクティブの追加、編集、削除、コピー、表示の各操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c807d-112">To create perspectives, you will use the **Perspectives** dialog box, where you can add, edit, delete, copy, and view perspectives.</span></span> <span data-ttu-id="c807d-113">**[パースペクティブ]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[パースペクティブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c807d-113">To view the **Perspectives** dialog box, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click on the **Model** menu, and then click **Perspectives**.</span></span>  
  
###  <a name="to-add-a-perspective"></a><a name="bkmk_add"></a> <span data-ttu-id="c807d-114">パースペクティブを追加するには</span><span class="sxs-lookup"><span data-stu-id="c807d-114">To add a perspective</span></span>  
  
-   <span data-ttu-id="c807d-115">新しいパースペクティブを追加するには、 **[新しいパースペクティブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c807d-115">To add a new perspective, click **New Perspective**.</span></span> <span data-ttu-id="c807d-116">パースペクティブに含めるフィールド オブジェクトのチェック ボックスをオンまたはオフにできます。新しいパースペクティブの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c807d-116">You can then check and uncheck field objects to be included and provide a name for the new perspective.</span></span>  
  
     <span data-ttu-id="c807d-117">すべてのフィールド オブジェクトのフィールドが空のパースペクティブを作成した場合、そのパースペクティブを使用するユーザーには空の "フィールドの一覧" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c807d-117">If you create an empty perspective with all of the field object fields, then a user using this perspective will see an empty Field List.</span></span> <span data-ttu-id="c807d-118">パースペクティブには 1 つ以上のテーブルおよび列を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c807d-118">Perspectives should contain at least one table and column.</span></span>  
  
###  <a name="to-edit-a-perspective"></a><a name="bkmk_edit"></a><span data-ttu-id="c807d-119">パースペクティブを編集するには</span><span class="sxs-lookup"><span data-stu-id="c807d-119">To edit a perspective</span></span>  
  
-   <span data-ttu-id="c807d-120">パースペクティブを変更するには、パースペクティブの列にあるフィールドをオンまたはオフにします。これにより、パースペクティブのフィールドオブジェクトが追加および削除されます。</span><span class="sxs-lookup"><span data-stu-id="c807d-120">To modify a perspective, check and uncheck fields in the perspective's column, which adds and removes field objects from the perspective.</span></span>  
  
###  <a name="to-rename-a-perspective"></a><a name="bkmk_rename"></a><span data-ttu-id="c807d-121">パースペクティブの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="c807d-121">To rename a perspective</span></span>  
  
-   <span data-ttu-id="c807d-122">パースペクティブの列ヘッダー (パースペクティブの名前) にマウスポインターを合わせると、[**名前の変更**] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c807d-122">When you hover over a perspective's column header (the name of the perspective), the **Rename** button appears.</span></span> <span data-ttu-id="c807d-123">パースペクティブの名前を変更するには、 **[名前の変更]** をクリックした後、新しい名前を入力するか、既存の名前を編集します。</span><span class="sxs-lookup"><span data-stu-id="c807d-123">To rename the perspective, click **Rename**, and then enter a new name or edit the existing name.</span></span>  
  
###  <a name="to-delete-a-perspective"></a><a name="bkmk_delete"></a><span data-ttu-id="c807d-124">パースペクティブを削除するには</span><span class="sxs-lookup"><span data-stu-id="c807d-124">To delete a perspective</span></span>  
  
-   <span data-ttu-id="c807d-125">パースペクティブの列ヘッダー (パースペクティブの名前) にマウスポインターを合わせると、[**削除**] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c807d-125">When you hover over a perspective's column header (the name of the perspective), the **Delete** button appears.</span></span> <span data-ttu-id="c807d-126">パースペクティブを削除するには、 **[削除]** ボタンをクリックし、確認ウィンドウで **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c807d-126">To delete the perspective, click the **Delete** button, and then click **Yes** in the confirmation window.</span></span>  
  
###  <a name="to-copy-a-perspective"></a><a name="bkmk_copy"></a><span data-ttu-id="c807d-127">パースペクティブをコピーするには</span><span class="sxs-lookup"><span data-stu-id="c807d-127">To copy a perspective</span></span>  
  
-   <span data-ttu-id="c807d-128">パースペクティブの列ヘッダーにマウスポインターを合わせると、[**コピー** ] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c807d-128">When you hover over a perspective's column header, the **Copy** button appears.</span></span> <span data-ttu-id="c807d-129">そのパースペクティブのコピーを作成するには、 **[コピー]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c807d-129">To create a copy of that perspective, click the **Copy** button.</span></span> <span data-ttu-id="c807d-130">既存のパースペクティブの右側に、選択したパースペクティブのコピーが新しいパースペクティブとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="c807d-130">A copy of the selected perspective is added as a new perspective to the right of existing perspectives.</span></span> <span data-ttu-id="c807d-131">新しいパースペクティブは、コピーしたパースペクティブの名前を継承しますが、名前の末尾には " *- コピー* " という注釈が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c807d-131">The new perspective inherits the name of the copied perspective and a *- Copy* annotation is appended to the end of the name.</span></span> <span data-ttu-id="c807d-132">たとえば、 *sales*パースペクティブのコピーが作成された場合、新しいパースペクティブは " *sales-copy*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c807d-132">For example, if a copy of the *Sales* perspective is created, the new perspective is called *Sales - Copy*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c807d-133">参照</span><span class="sxs-lookup"><span data-stu-id="c807d-133">See Also</span></span>  
 <span data-ttu-id="c807d-134">[SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="c807d-134">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="c807d-135">階層 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="c807d-135">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
