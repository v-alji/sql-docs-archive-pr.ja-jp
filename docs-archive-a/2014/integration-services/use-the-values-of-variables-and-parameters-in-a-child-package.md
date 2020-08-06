---
title: 子パッケージの変数とパラメーターの値を使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- configurations [Integration Services]
- packages [Integration Services], configurations
- variables [Integration Services], adding
ms.assetid: 9b939edb-4e17-48e5-8428-855beb10049c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 28561db91e5e924d8b25f9c7be7a4a51c6c315ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642866"
---
# <a name="use-the-values-of-variables-and-parameters-in-a-child-package"></a><span data-ttu-id="4c133-102">子パッケージでの変数およびパラメーターの値の使用</span><span class="sxs-lookup"><span data-stu-id="4c133-102">Use the Values of Variables and Parameters in a Child Package</span></span>
  <span data-ttu-id="4c133-103">この手順では、構成の種類として親変数を使用するパッケージ構成を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c133-103">This procedure describes how to create a package configuration that uses the parent variable configuration type.</span></span> <span data-ttu-id="4c133-104">この構成の種類を使用すると、親パッケージから実行される子パッケージが親内の変数にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="4c133-104">This configuration type enables a child package that is run from a parent package to access a variable in the parent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c133-105">親パッケージの変数またはパラメーター、またはプロジェクトのパラメーターを子パッケージのパラメーターにマップするようにパッケージ実行タスクを構成することで、値を子パッケージに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="4c133-105">You can also pass values to a child package by configuring the Execute Package Task to map parent package variables or parameters, or project parameters, to child package parameters.</span></span> <span data-ttu-id="4c133-106">詳細については、「 [パッケージ実行タスク](control-flow/execute-package-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c133-106">For more information, see [Execute Package Task](control-flow/execute-package-task.md).</span></span>  
  
 <span data-ttu-id="4c133-107">親パッケージ内のこの変数は、子パッケージのパッケージ構成を作成する前に作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c133-107">It is not necessary to create the variable in the parent package before you create the package configuration in the child package.</span></span> <span data-ttu-id="4c133-108">変数はいつでも親パッケージに追加できますが、パッケージ構成では親変数の正確な名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c133-108">You can add the variable to the parent package at any time, but you must use the exact name of the parent variable in the package configuration.</span></span> <span data-ttu-id="4c133-109">ただし、親変数パッケージ構成を作成するには、子パッケージ内に、この構成で更新できる変数が既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c133-109">However, before you can create a parent variable configuration, there must be an existing variable in the child package that the configuration can update.</span></span> <span data-ttu-id="4c133-110">変数の追加と構成の詳細については、「 [パッケージ内のユーザー定義変数のスコープの追加、削除、変更](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c133-110">For more information about adding and configuring variables, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
 <span data-ttu-id="4c133-111">親変数パッケージ構成で使用される親パッケージ内の変数のスコープは、パッケージ実行タスク、タスクを含むコンテナー、またはパッケージに設定できます。</span><span class="sxs-lookup"><span data-stu-id="4c133-111">The scope of the variable in the parent package that is used in a parent variable configuration can be set to the Execute Package task, to the container that has the task, or to the package.</span></span> <span data-ttu-id="4c133-112">パッケージ内で同じ名前の複数の変数が定義されている場合、パッケージ実行タスクのスコープ内で最も近い変数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c133-112">If multiple variables with the same name are defined in a package, the variable that is closest in scope to the Execute Package task is used.</span></span> <span data-ttu-id="4c133-113">パッケージ実行タスクに最も近いスコープは、タスク自体です。</span><span class="sxs-lookup"><span data-stu-id="4c133-113">The closest scope to the Execute Package task is the task itself.</span></span>  
  
### <a name="to-add-a-variable-to-a-parent-package"></a><span data-ttu-id="4c133-114">親パッケージに変数を追加するには</span><span class="sxs-lookup"><span data-stu-id="4c133-114">To add a variable to a parent package</span></span>  
  
1.  <span data-ttu-id="4c133-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、子パッケージに渡す変数の追加先パッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4c133-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a variable to pass to a child package.</span></span>  
  
2.  <span data-ttu-id="4c133-116">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="4c133-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4c133-117">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、変数のスコープを定義するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4c133-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="4c133-118">スコープをパッケージに設定するには、 **[制御フロー]** タブのデザイン画面上の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-118">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="4c133-119">スコープをパッケージ実行タスクの親コンテナーに設定するには、コンテナーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-119">To set the scope to a parent container of the Execute Package task, click the container.</span></span>  
  
    -   <span data-ttu-id="4c133-120">スコープをパッケージ実行タスクに設定するには、タスクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-120">To set the scope to the Execute Package task, click the task.</span></span>  
  
4.  <span data-ttu-id="4c133-121">変数を追加および構成します。</span><span class="sxs-lookup"><span data-stu-id="4c133-121">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c133-122">変数で格納するデータと互換性のあるデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c133-122">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="4c133-123">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-variable-to-a-child-package"></a><span data-ttu-id="4c133-124">子パッケージに変数を追加するには</span><span class="sxs-lookup"><span data-stu-id="4c133-124">To add a variable to a child package</span></span>  
  
1.  <span data-ttu-id="4c133-125">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、親変数パッケージ構成の追加先パッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4c133-125">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a parent variable configuration.</span></span>  
  
2.  <span data-ttu-id="4c133-126">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="4c133-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4c133-127">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、スコープをパッケージに設定するには、 **[制御フロー]** タブのデザイン画面上の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-127">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="4c133-128">変数を追加および構成します。</span><span class="sxs-lookup"><span data-stu-id="4c133-128">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c133-129">変数で格納するデータと互換性のあるデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c133-129">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="4c133-130">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-parent-package-configuration-to-a-child-package"></a><span data-ttu-id="4c133-131">親パッケージ構成を子パッケージに追加するには</span><span class="sxs-lookup"><span data-stu-id="4c133-131">To add a parent package configuration to a child package</span></span>  
  
1.  <span data-ttu-id="4c133-132">子パッケージが開かれていない場合は、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で開きます。</span><span class="sxs-lookup"><span data-stu-id="4c133-132">If it is not already open, open the child package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4c133-133">**[制御フロー]** タブのデザイン画面で任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-133">Click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="4c133-134">**[SSIS]** メニューの **[パッケージ構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-134">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="4c133-135">**[パッケージ構成オーガナイザー]** ダイアログ ボックスで、 **[パッケージの構成を有効にする]** を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-135">In the **Package Configuration Organizer** dialog box, select **Enable package configuration**, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="4c133-136">パッケージ構成ウィザードの初期画面で、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-136">On the welcome page of the Package Configuration Wizard, click **Next.**</span></span>  
  
6.  <span data-ttu-id="4c133-137">[構成の種類の選択] ページの **[構成の種類]** ボックスの一覧で、 **[親パッケージ変数]** を選択して、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4c133-137">On the Select Configuration Type page, in the **Configuration type** list, select **Parent package variable** and do one of the following:</span></span>  
  
    -   <span data-ttu-id="4c133-138">**[構成設定を直接指定する]** を選択し、 **[親変数]** ボックスで、その構成で使用する親パッケージ内の変数名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c133-138">Select **Specify configuration settings directly**, and then in the **Parent variable** box, provide the name of the variable in the parent package to use in the configuration.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="4c133-139">変数名では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="4c133-139">Variable names are case sensitive.</span></span>  
  
    -   <span data-ttu-id="4c133-140">**[構成の場所を環境変数に格納する]** を選択し、 **[環境変数]** ボックスの一覧で、変数の名前を含む環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c133-140">Select or **Configuration location is stored in an environment variable,** and then in the **Environment variable list**, select the environmentvariable that contains the name of the variable.</span></span>  
  
7.  <span data-ttu-id="4c133-141">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-141">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="4c133-142">[対象になるプロパティの選択] ページで、 **[変数]** ノードを展開し、構成する変数の **[プロパティ]** ノードを展開した後、構成によって設定されるプロパティをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-142">On the Select Target Property page, expand the **Variable** node, and expand the **Properties** node of the variable to configure, and then click the property to be set by the configuration.</span></span>  
  
9. <span data-ttu-id="4c133-143">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-143">Click **Next**.</span></span>  
  
10. <span data-ttu-id="4c133-144">[ウィザードの完了] ページで、必要に応じて、構成の既定の名前を変更し、構成情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="4c133-144">On the Completing the Wizard page, optionally, modify the default name of the configuration and review the configuration information.</span></span>  
  
11. <span data-ttu-id="4c133-145">**[完了]** をクリックしてウィザードを完了し、 **[パッケージ構成オーガナイザー]** ダイアログ ボックスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4c133-145">Click **Finish** to complete the wizard and return to the **Package Configuration Organizer** dialog box.</span></span>  
  
12. <span data-ttu-id="4c133-146">**[パッケージ構成オーガナイザー]** ダイアログ ボックスの **[構成]** タブに、新しい構成が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c133-146">In the **Package Configuration Organizer** dialog box, the **Configuration** box lists the new configuration.</span></span>  
  
13. <span data-ttu-id="4c133-147">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c133-147">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c133-148">参照</span><span class="sxs-lookup"><span data-stu-id="4c133-148">See Also</span></span>  
 <span data-ttu-id="4c133-149">[パッケージの構成](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="4c133-149">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="4c133-150">[パッケージ構成の作成](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="4c133-150">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="4c133-151">[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="4c133-151">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="4c133-152">パッケージで変数を使用する</span><span class="sxs-lookup"><span data-stu-id="4c133-152">Use Variables in Packages</span></span>](../../2014/integration-services/use-variables-in-packages.md)  
  
  
