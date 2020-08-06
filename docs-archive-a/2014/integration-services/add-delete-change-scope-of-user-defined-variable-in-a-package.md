---
title: パッケージ内のユーザー定義変数のスコープを追加、削除、変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], adding
ms.assetid: cbf40c7f-3c8a-48cd-aefa-8b37faf8b40e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7e5980fc7f730c69ef886e4e80760cfbdc9e4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640215"
---
# <a name="add-delete-change-scope-of-user-defined-variable-in-a-package"></a><span data-ttu-id="0d492-102">パッケージ内のユーザー定義変数のスコープの追加、削除、変更</span><span class="sxs-lookup"><span data-stu-id="0d492-102">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>
  <span data-ttu-id="0d492-103">この手順では、 **[変数]** ウィンドウを使用して、パッケージ内のユーザー定義変数のスコープを追加、削除、および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d492-103">These procedures describe how to add, delete, and change the scope of a user-defined variable in a package by using the **Variables** window.</span></span>  
  
 <span data-ttu-id="0d492-104">変数のスコープの詳細については、「 [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)領域の下にあります。</span><span class="sxs-lookup"><span data-stu-id="0d492-104">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0d492-105">には、システム情報を実行時に利用可能にしたり、パッケージやイベント ハンドラーなどのコンテナーで使用できるシステム変数も用意されています。</span><span class="sxs-lookup"><span data-stu-id="0d492-105">also provides system variables that make system information available at run time and can be used in containers such as packages and event handlers.</span></span> <span data-ttu-id="0d492-106">システム変数は削除できません。</span><span class="sxs-lookup"><span data-stu-id="0d492-106">You cannot delete system variables.</span></span>  
  
### <a name="to-add-a-variable"></a><span data-ttu-id="0d492-107">変数を追加するには</span><span class="sxs-lookup"><span data-stu-id="0d492-107">To add a variable</span></span>  
  
1.  <span data-ttu-id="0d492-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、操作する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="0d492-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="0d492-109">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0d492-109">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="0d492-110">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、変数のスコープを定義するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="0d492-110">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="0d492-111">スコープをパッケージに設定するには、 **[制御フロー]** タブのデザイン画面上の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-111">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="0d492-112">スコープをイベント ハンドラーに設定するには、 **[イベント ハンドラー]** タブのデザイン画面で、実行可能ファイルおよびイベント ハンドラーを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d492-112">To set the scope to an event handler, select an executable and an event handler on the design surface of the **Event Handler** tab.</span></span>  
  
    -   <span data-ttu-id="0d492-113">スコープをタスクまたはコンテナーに設定するには、 **[制御フロー]** タブまたは **[イベント ハンドラー]** タブのデザイン画面で、タスクまたはコンテナーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-113">To set the scope to a task or container, on the design surface of the **Control Flow** tab or the **Event Handler** tab, click a task or container.</span></span>  
  
4.  <span data-ttu-id="0d492-114">**[SSIS]** メニューの **[変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-114">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="0d492-115">必要に応じて、View.Variables コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[変数]** ウィンドウを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="0d492-115">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
5.  <span data-ttu-id="0d492-116">[**変数**] ウィンドウで、[**変数の追加**] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-116">In the **Variables** window, click the **Add Variable** icon.</span></span> <span data-ttu-id="0d492-117">新しい変数が一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0d492-117">The new variable is added to the list.</span></span>  
  
6.  <span data-ttu-id="0d492-118">必要に応じて、 **[グリッドのオプション]** アイコンをクリックし、 **[可変グリッドのオプション]** ダイアログ ボックスに表示する追加の列を選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-118">Optionally, click the **Grid Options** icon, select additional columns to show in the **Variables Grid Options** dialog box, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="0d492-119">必要に応じて、変数のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="0d492-119">Optionally, set the variable properties.</span></span> <span data-ttu-id="0d492-120">詳細については、「 [ユーザー定義変数のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)によって定義された変数です。</span><span class="sxs-lookup"><span data-stu-id="0d492-120">For more information, see [Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md).</span></span>  
  
8.  <span data-ttu-id="0d492-121">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-variable"></a><span data-ttu-id="0d492-122">変数を削除するには</span><span class="sxs-lookup"><span data-stu-id="0d492-122">To delete a variable</span></span>  
  
1.  <span data-ttu-id="0d492-123">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0d492-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="0d492-124">ソリューション エクスプローラーで、パッケージを右クリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0d492-124">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="0d492-125">**[SSIS]** メニューの **[変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-125">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="0d492-126">必要に応じて、View.Variables コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[変数]** ウィンドウを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="0d492-126">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="0d492-127">削除する変数を選択し、 **[変数の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-127">Select the variable to delete, and then click **Delete Variable**.</span></span>  
  
     <span data-ttu-id="0d492-128">[変数] ウィンドウに変数が表示されない場合は、[**グリッドのオプション**] をクリックし、[**すべてのスコープの変数を表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d492-128">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="0d492-129">**[変数の削除の確認]** ダイアログ ボックスが開いた場合は、 **[はい]** をクリックして確定します。</span><span class="sxs-lookup"><span data-stu-id="0d492-129">If the **Confirm Deletion of Variables** dialog box opens, click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="0d492-130">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-change-the-scope-of-a-variable"></a><span data-ttu-id="0d492-131">変数のスコープを変更するには</span><span class="sxs-lookup"><span data-stu-id="0d492-131">To change the scope of a variable</span></span>  
  
1.  <span data-ttu-id="0d492-132">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0d492-132">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="0d492-133">ソリューション エクスプローラーで、パッケージを右クリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0d492-133">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="0d492-134">**[SSIS]** メニューの **[変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-134">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="0d492-135">必要に応じて、View.Variables コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[変数]** ウィンドウを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="0d492-135">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="0d492-136">変数を選択して、 **[変数の移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-136">Select the variable and then click **Move Variable**.</span></span>  
  
     <span data-ttu-id="0d492-137">[変数] ウィンドウに変数が表示されない場合は、[**グリッドのオプション**] をクリックし、[**すべてのスコープの変数を表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d492-137">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="0d492-138">**[新しいスコープの選択]** ダイアログ ボックスで、パッケージまたはパッケージ内のコンテナー、タスク、またはイベント ハンドラーを選択して、変数のスコープを変更します。</span><span class="sxs-lookup"><span data-stu-id="0d492-138">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
6.  <span data-ttu-id="0d492-139">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d492-139">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d492-140">参照</span><span class="sxs-lookup"><span data-stu-id="0d492-140">See Also</span></span>  
 <span data-ttu-id="0d492-141">[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="0d492-141">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="0d492-142">[パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="0d492-142">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="0d492-143">[ユーザー定義変数のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span><span class="sxs-lookup"><span data-stu-id="0d492-143">[Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span></span>  
 [<span data-ttu-id="0d492-144">子パッケージでの変数とパラメーターの値の使用</span><span class="sxs-lookup"><span data-stu-id="0d492-144">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
  
