---
title: パッケージの構成を作成する |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, configurations
- Package Configurations Organizer dialog box
- SSIS packages, configurations
- Integration Services packages, configurations
- configurations [Integration Services]
- packages [Integration Services], configurations
- deploying packages [Integration Services], configurations
ms.assetid: 91ac0347-f908-44f5-bd3d-115790223af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58c93242c9ef51a5e00076bd367e46b43187098e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639572"
---
# <a name="create-package-configurations"></a><span data-ttu-id="4515d-102">パッケージ構成を作成する</span><span class="sxs-lookup"><span data-stu-id="4515d-102">Create Package Configurations</span></span>
  <span data-ttu-id="4515d-103">パッケージの構成は、 **[パッケージ構成オーガナイザー]** ダイアログ ボックスまたはパッケージ構成ウィザードを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="4515d-103">You create package configurations by using the **Package Configuration Organizer** dialog box and the Package Configuration Wizard.</span></span> <span data-ttu-id="4515d-104">これらのツールにアクセスするには、 **で** [SSIS] **メニューの** [パッケージ構成] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4515d-104">To access these tools, click **Package Configurations** on the **SSIS** menu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4515d-105">また、**構成**プロパティの横にある省略記号ボタンをクリックして、**パッケージ構成オーガナイザー**にアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4515d-105">You can also access the **Package Configuration Organizer**, by clicking the ellipsis button next to the **Configuration** property.</span></span> <span data-ttu-id="4515d-106">構成プロパティは、パッケージのプロパティ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4515d-106">The Configuration property appears in the properties window for the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4515d-107">パッケージ配置モデルの構成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4515d-107">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="4515d-108">パラメーターは、プロジェクト配置モデルの構成の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="4515d-108">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="4515d-109">プロジェクト配置モデルを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="4515d-109">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="4515d-110">配置モデルの詳細については、「 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4515d-110">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="4515d-111">**[パッケージ構成オーガナイザー]** ダイアログ ボックスでは、パッケージに対する構成の有効化、構成の追加および削除、構成の優先読み込み順序の設定を行えます。</span><span class="sxs-lookup"><span data-stu-id="4515d-111">In the **Package Configuration Organizer** dialog box, you can enable packages to use configurations, add and delete configurations, and set the preferred order in which configurations should be loaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4515d-112">パッケージ構成を優先順序で読み込むと、 **[パッケージ構成オーガナイザー]** ダイアログ ボックスに表示された一覧の上から下へと構成が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="4515d-112">When package configurations load in the preferred order, configurations load from the top of the list shown in the **Package Configuration Organizer** dialog box to the bottom of the list.</span></span> <span data-ttu-id="4515d-113">ただし、実行時にパッケージ構成が優先順序で読み込まれるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="4515d-113">However, at run time, package configurations might not load in the preferred order.</span></span> <span data-ttu-id="4515d-114">具体的には、親のパッケージ構成は他の種類の構成の後に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="4515d-114">In particular, parent package configurations load after configurations of other types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4515d-115">複数の構成で同じオブジェクト プロパティが設定された場合、最後に読み込まれた値が実行時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4515d-115">If multiple configurations set the same object property, the value loaded last is used at run time.</span></span>  
  
 <span data-ttu-id="4515d-116">**[パッケージ構成オーガナイザー]** ダイアログ ボックスから、手順に従って構成を作成できるパッケージ構成ウィザードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4515d-116">From the **Package Configuration Organizer** dialog box, you run the Package Configuration Wizard, which guides you through the steps to create a configuration.</span></span> <span data-ttu-id="4515d-117">パッケージ構成ウィザードを実行するには、 **[パッケージ構成オーガナイザー]** ダイアログ ボックスで新しい構成を追加するか、既存の構成を編集します。</span><span class="sxs-lookup"><span data-stu-id="4515d-117">To run the Package Configuration Wizard, add a new configuration in the **Package Configurations Organizer** dialog box or edit an existing one.</span></span> <span data-ttu-id="4515d-118">ウィザードの各ページで、構成の種類を選択し、構成に直接アクセスするか環境変数を使用するかを選択し、構成に保存するプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="4515d-118">On the wizard pages, you choose the configuration type, select whether you want to access the configuration directly or use environment variables, and select the properties to save in the configuration.</span></span>  
  
 <span data-ttu-id="4515d-119">次の例は、パッケージ構成ウィザードの [ウィザードの完了] ページに表示される、変数およびパッケージの対象になるプロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="4515d-119">The following example shows the target properties of a variable and a package as they appear on the Completing the Wizard page of the Package Configuration Wizard.:</span></span>  
  
 <span data-ttu-id="4515d-120">\Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]</span><span class="sxs-lookup"><span data-stu-id="4515d-120">\Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]</span></span>  
  
 <span data-ttu-id="4515d-121">\Package.Properties[MaximumErrorCount]</span><span class="sxs-lookup"><span data-stu-id="4515d-121">\Package.Properties[MaximumErrorCount]</span></span>  
  
 <span data-ttu-id="4515d-122">\Package.Properties[LoggingMode]</span><span class="sxs-lookup"><span data-stu-id="4515d-122">\Package.Properties[LoggingMode]</span></span>  
  
 <span data-ttu-id="4515d-123">\Package.Properties[LocaleID]</span><span class="sxs-lookup"><span data-stu-id="4515d-123">\Package.Properties[LocaleID]</span></span>  
  
 <span data-ttu-id="4515d-124">\Package\My SQL Task.Variables[User::varTableName].Properties[Value]</span><span class="sxs-lookup"><span data-stu-id="4515d-124">\Package\My SQL Task.Variables[User::varTableName].Properties[Value]</span></span>  
  
 <span data-ttu-id="4515d-125">この例では、構成によって次のプロパティが更新されます。</span><span class="sxs-lookup"><span data-stu-id="4515d-125">In this example, the configuration updates these properties:</span></span>  
  
-   <span data-ttu-id="4515d-126">ユーザー定義変数 `TodaysDate`の RaiseChangedEvent プロパティ。</span><span class="sxs-lookup"><span data-stu-id="4515d-126">The RaiseChangedEvent property of user-defined variable, `TodaysDate`.</span></span>  
  
-   <span data-ttu-id="4515d-127">パッケージの MaximumErrorCount プロパティ、LoggingMode プロパティ、および LocaleID プロパティ。</span><span class="sxs-lookup"><span data-stu-id="4515d-127">The MaximumErrorCount, LoggingMode, and LocaleID properties of the package.</span></span>  
  
-   <span data-ttu-id="4515d-128">ユーザー定義変数 `varTableName`の Value プロパティ (タスク My SQL Task のスコープ内)。</span><span class="sxs-lookup"><span data-stu-id="4515d-128">The Value property of user-defined variable, `varTableName`, within scope of the task, My SQL Task.</span></span>  
  
 <span data-ttu-id="4515d-129">"\Package" はルートを表し、ピリオド (.) は構成で更新されるプロパティへのパスを定義するオブジェクトを区切ります。</span><span class="sxs-lookup"><span data-stu-id="4515d-129">The "\Package" represents the root, and periods (.) separate the objects that define the path to the property that the configuration updates.</span></span> <span data-ttu-id="4515d-130">変数とプロパティの名前は角かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="4515d-130">The names of variables and properties are enclosed in brackets.</span></span> <span data-ttu-id="4515d-131">パッケージ名に関係なく、構成では常に Package という用語を使用します。ただし、その他のオブジェクトのパスにはすべてユーザーが定義した名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="4515d-131">The term Package is always used in configuration, regardless of the package name; however, all other objects in the path use their user-defined names.</span></span>  
  
 <span data-ttu-id="4515d-132">ウィザードの終了後、新しい構成が **[パッケージ構成オーガナイザー]** ダイアログ ボックスの構成の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="4515d-132">After the wizard finishes, the new configuration is added to the configuration list in the **Package Configuration Organizer** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4515d-133">パッケージ構成ウィザードの最後に表示される [ウィザードの完了] ページには、構成内の対象プロパティが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="4515d-133">The last page in the Package Configuration Wizard, Completing the Wizard, lists the target properties in the configuration.</span></span> <span data-ttu-id="4515d-134">**dtexec** コマンド プロンプト ユーティリティを使用してパッケージの実行時にプロパティを更新するには、パッケージ構成ウィザードを実行してプロパティのパスを表す文字列を生成し、それらの文字列をコピーしてコマンド プロンプト ウィンドウに貼り付け、 **dtexec**の set オプションと一緒に使用します。</span><span class="sxs-lookup"><span data-stu-id="4515d-134">If you want to update properties when you run packages by using the **dtexec** command prompt utility, you can generate the strings that represent the property paths by running the Package Configuration Wizard and then copy and paste them into the command prompt window for use with the set option of **dtexec.**</span></span>  
  
 <span data-ttu-id="4515d-135">次の表に、 **[パッケージ構成オーガナイザー]** ダイアログ ボックスの構成の一覧の列を示します。</span><span class="sxs-lookup"><span data-stu-id="4515d-135">The following table describes the columns in the configuration list in the **Package Configuration Organizer** dialog box.</span></span>  
  
|<span data-ttu-id="4515d-136">列</span><span class="sxs-lookup"><span data-stu-id="4515d-136">Column</span></span>|<span data-ttu-id="4515d-137">説明</span><span class="sxs-lookup"><span data-stu-id="4515d-137">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4515d-138">**[構成名]**</span><span class="sxs-lookup"><span data-stu-id="4515d-138">**Configuration Name**</span></span>|<span data-ttu-id="4515d-139">構成の名前です。</span><span class="sxs-lookup"><span data-stu-id="4515d-139">The name of the configuration.</span></span>|  
|<span data-ttu-id="4515d-140">**[構成の種類]**</span><span class="sxs-lookup"><span data-stu-id="4515d-140">**Configuration Type**</span></span>|<span data-ttu-id="4515d-141">構成の種類です。</span><span class="sxs-lookup"><span data-stu-id="4515d-141">The configuration type.</span></span>|  
|<span data-ttu-id="4515d-142">**[構成文字列]**</span><span class="sxs-lookup"><span data-stu-id="4515d-142">**Configuration String**</span></span>|<span data-ttu-id="4515d-143">構成の場所です。</span><span class="sxs-lookup"><span data-stu-id="4515d-143">The location of the configuration.</span></span> <span data-ttu-id="4515d-144">場所は、パス、環境変数、レジストリ キー、親パッケージの変数名、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースのテーブルの場合があります。</span><span class="sxs-lookup"><span data-stu-id="4515d-144">The location can be a path, an environment variable, a Registry key, a parent package variable name, or a table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="4515d-145">**[対象になるオブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="4515d-145">**Target Object**</span></span>|<span data-ttu-id="4515d-146">構成を持つプロパティを設定するオブジェクトの名前です。</span><span class="sxs-lookup"><span data-stu-id="4515d-146">The name of the object with a property that has a configuration.</span></span> <span data-ttu-id="4515d-147">構成が XML 構成ファイルの場合、構成で複数のオブジェクトを更新できるため、この列は空白になります。</span><span class="sxs-lookup"><span data-stu-id="4515d-147">If the configuration is an XML configuration file, the column is blank, because the configuration can update multiple objects.</span></span>|  
|<span data-ttu-id="4515d-148">**[対象になるプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="4515d-148">**Target Property**</span></span>|<span data-ttu-id="4515d-149">プロパティの名前。</span><span class="sxs-lookup"><span data-stu-id="4515d-149">The name of the property.</span></span> <span data-ttu-id="4515d-150">構成が XML 構成ファイルまたは SQL Server テーブルに書き込まれる場合は、構成で複数のオブジェクトを更新できるため、この列は空白になります。</span><span class="sxs-lookup"><span data-stu-id="4515d-150">If the configuration writes to an XML configuration file or a SQL Server table, the column is blank, because the configuration can update multiple objects.</span></span>|  
  
### <a name="to-create-a-package-configuration"></a><span data-ttu-id="4515d-151">パッケージの構成を作成するには</span><span class="sxs-lookup"><span data-stu-id="4515d-151">To create a package configuration</span></span>  
  
1.  <span data-ttu-id="4515d-152">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4515d-152">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="4515d-153">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="4515d-153">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4515d-154">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[制御フロー]** タブ、 **[データ フロー]** タブ、 **[イベント ハンドラー]** タブ、または **[パッケージ エクスプローラー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4515d-154">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow**, **Data Flow**, **Event Handler**, or **Package Explorer** tab.</span></span>  
  
4.  <span data-ttu-id="4515d-155">**[SSIS]** メニューの **[パッケージ構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4515d-155">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
5.  <span data-ttu-id="4515d-156">**[パッケージ構成オーガナイザー]** ダイアログ ボックスで、 **[パッケージの構成を有効にする]** を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4515d-156">In the **Package Configuration Organizer** dialog box, select **Enable package configurations**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="4515d-157">パッケージ構成ウィザードの最初のページが表示されたら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4515d-157">On the welcome page of the Package Configuration Wizard page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="4515d-158">[構成の種類の選択] ページで構成の種類を指定してから、選択した構成の種類に対応するプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4515d-158">On the Select Configuration Type page, specify the configuration type, and then set the properties that are relevant to the configuration type.</span></span> <span data-ttu-id="4515d-159">詳細については、「 [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4515d-159">For more information, see [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).</span></span>  
  
8.  <span data-ttu-id="4515d-160">[エクスポートするプロパティの選択] ページで、構成に含めるパッケージ オブジェクトのプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="4515d-160">On the Select Properties to Export page, select the properties of package objects to include in the configuration.</span></span> <span data-ttu-id="4515d-161">この構成の種類でサポートされているプロパティが 1 つのみである場合、ウィザード ページのタイトルは [対象になるプロパティの選択] になります。</span><span class="sxs-lookup"><span data-stu-id="4515d-161">If the configuration type supports only one property, the title of this wizard page is Select Target Property.</span></span> <span data-ttu-id="4515d-162">詳細については、「 [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4515d-162">For more information, see [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4515d-163">構成の種類が **[XML 構成ファイル]** および **[SQL Server]** の場合のみ、構成に複数のプロパティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4515d-163">Only the **XML Configuration File** and **SQL Server** configuration types support including multiple properties in a configuration.</span></span>  
  
9. <span data-ttu-id="4515d-164">[ウィザードの完了] というページが表示されたら、構成の名前を入力して **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4515d-164">On the Completing the Wizard page, type the name of the configuration, and then click **Finish**.</span></span>  
  
10. <span data-ttu-id="4515d-165">**[パッケージ構成オーガナイザー]** ダイアログ ボックスで構成を確認します。</span><span class="sxs-lookup"><span data-stu-id="4515d-165">View the configuration in the **Package Configuration Organizer** dialog box.</span></span>  
  
11. <span data-ttu-id="4515d-166">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4515d-166">Click **Close**.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="4515d-167">外部リソース</span><span class="sxs-lookup"><span data-stu-id="4515d-167">External Resources</span></span>  
  
-   <span data-ttu-id="4515d-168">msdn.microsoft.com の技術記事「 [Integration Services パッケージ構成について](https://go.microsoft.com/fwlink/?LinkId=165643)」</span><span class="sxs-lookup"><span data-stu-id="4515d-168">Technical article, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="4515d-169">Www.sqlis.com のブログ記事「[コードパッケージ構成でのパッケージの作成](https://go.microsoft.com/fwlink/?LinkId=217663)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4515d-169">Blog entry, [Creating packages in code - Package Configurations](https://go.microsoft.com/fwlink/?LinkId=217663), on www.sqlis.com.</span></span>  
  
-   <span data-ttu-id="4515d-170">ブログ記事「 [API サンプル-プログラムによるパッケージへの構成ファイルの追加](https://go.microsoft.com/fwlink/?LinkId=217664)」 (blogs.msdn.com) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4515d-170">Blog entry, [API Sample - Programmatically add a configuration file to a package](https://go.microsoft.com/fwlink/?LinkId=217664), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4515d-171">参照</span><span class="sxs-lookup"><span data-stu-id="4515d-171">See Also</span></span>  
 <span data-ttu-id="4515d-172">[パッケージの構成](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="4515d-172">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="4515d-173">[SSIS&#41;&#40;パッケージの配置](packages/legacy-package-deployment-ssis.md) </span><span class="sxs-lookup"><span data-stu-id="4515d-173">[Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span></span>  
 [<span data-ttu-id="4515d-174">プログラムでの変数の使用</span><span class="sxs-lookup"><span data-stu-id="4515d-174">Working with Variables Programmatically</span></span>](building-packages-programmatically/working-with-variables-programmatically.md)  
  
  
