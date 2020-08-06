---
title: '手順 4: パッケージ構成の追加 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e04a5321-63d5-4ec5-85b9-cb4eaf6c87f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 416cf17f967a145fccef1341b77f71a02ff3f3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641095"
---
# <a name="step-4-adding-package-configurations"></a><span data-ttu-id="cde22-102">手順 4:パッケージ構成の追加</span><span class="sxs-lookup"><span data-stu-id="cde22-102">Step 4: Adding Package Configurations</span></span>
  <span data-ttu-id="cde22-103">ここでは、各パッケージに構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="cde22-103">In this task, you will add a configuration to each package.</span></span> <span data-ttu-id="cde22-104">パッケージ プロパティとパッケージ オブジェクトの値は、構成によって実行時に更新されます。</span><span class="sxs-lookup"><span data-stu-id="cde22-104">Configurations update the values of package properties and package objects at run time.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="cde22-105">にはさまざまな種類の構成があります。</span><span class="sxs-lookup"><span data-stu-id="cde22-105">provides a variety of configuration types.</span></span> <span data-ttu-id="cde22-106">構成は、環境変数、レジストリ エントリ、ユーザー定義変数、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブル、XML ファイルに格納できます。</span><span class="sxs-lookup"><span data-stu-id="cde22-106">You can store configurations in environment variables, registry entries, user-defined variables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables, and XML files.</span></span> <span data-ttu-id="cde22-107">さらに柔軟性を高めるため、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では間接構成を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cde22-107">To provide additional flexibility, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] supports the use of indirect configurations.</span></span> <span data-ttu-id="cde22-108">これは、環境変数を使用して構成の場所を指定し、それによって実際の値を指定する方法です。</span><span class="sxs-lookup"><span data-stu-id="cde22-108">This means that you use an environment variable to specify the location of the configuration, which in turn specifies the actual values.</span></span> <span data-ttu-id="cde22-109">Deployment Tutorial プロジェクトのパッケージでは、XML 構成ファイルと間接構成を組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="cde22-109">The packages in the Deployment Tutorial project use a combination of XML configuration files and indirect configurations.</span></span> <span data-ttu-id="cde22-110">XML 構成ファイルには、複数のプロパティの構成を含めることができ、必要に応じて複数のパッケージから参照できます。</span><span class="sxs-lookup"><span data-stu-id="cde22-110">An XML configuration file can include configurations for multiple properties, and when appropriate, can be referenced by multiple packages.</span></span> <span data-ttu-id="cde22-111">このチュートリアルでは、パッケージごとに異なる構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="cde22-111">In this tutorial, you will use a separate configuration file for each package.</span></span>  
  
 <span data-ttu-id="cde22-112">構成ファイルには、接続文字列などの機密情報が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cde22-112">Configuration files frequently contain sensitive information such as connection strings.</span></span> <span data-ttu-id="cde22-113">したがって、アクセス制御リスト (ACL) を使用して、ファイルを保存する場所やフォルダーへのアクセスを制限し、パッケージの実行が許可されているユーザーまたはアカウントにのみアクセス権を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="cde22-113">Therefore, you should use an access control list (ACL) to restrict access to the location or folder where you store the files, and give access only to users or accounts that are permitted to run packages.</span></span> <span data-ttu-id="cde22-114">詳細については、「 [パッケージで使用されるファイルへのアクセス](../../2014/integration-services/access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cde22-114">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="cde22-115">前の作業で Deployment Tutorial プロジェクトに追加したパッケージ (DataTransfer と LoadXMLData) は、ターゲット サーバーに配置した後で正常に実行できるようにするには、構成が必要になります。</span><span class="sxs-lookup"><span data-stu-id="cde22-115">The packages (DataTransfer and LoadXMLData) that you added to the Deployment Tutorial project in the previous task need configurations to run successfully after they are deployed to the target server.</span></span> <span data-ttu-id="cde22-116">構成を実装するには、最初に XML 構成ファイルの間接構成を作成し、次に XML 構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cde22-116">To implement configurations, you will first create the indirect configurations for the XML configuration files, and then you will create the XML configuration files.</span></span>  
  
 <span data-ttu-id="cde22-117">DataTransferConfig.dtsConfig と LoadXMLData.dtsConfig の 2 つの構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cde22-117">You will create two configuration files, DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig.</span></span> <span data-ttu-id="cde22-118">これらのファイルには、パッケージで使用されるデータ ファイルとログ ファイルの場所を指定する名前と値のペアが含まれており、パッケージのプロパティはこれらの値で更新されます。</span><span class="sxs-lookup"><span data-stu-id="cde22-118">These files contain name-value pairs that update the properties in packages that specify the location of the data and log files used by the package.</span></span> <span data-ttu-id="cde22-119">後で、配置プロセスの手順として、配置先のコンピューターのファイルの新しい場所が反映されるように構成ファイルの値を更新します。</span><span class="sxs-lookup"><span data-stu-id="cde22-119">Later, as a step in the deployment process, you will update the values in the configuration files to reflect the new location of the files on the destination computer.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="cde22-120">で、DataTransferConfig.dtsConfig と LoadXMLData.dtsConfig が DataTransfer および LoadXMLData パッケージと依存関係にあることが認識され、次のレッスンで配置バンドルを作成するときに構成ファイルが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="cde22-120">recognizes that the DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig are dependencies of the DataTransfer and LoadXMLData packages, and automatically includes the configuration files when you create the deployment bundle in the next lesson.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-datatransfer-package"></a><span data-ttu-id="cde22-121">DataTransfer パッケージの間接構成を作成するには</span><span class="sxs-lookup"><span data-stu-id="cde22-121">To create indirect configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="cde22-122">ソリューション エクスプローラーで DataTransfer.dtsx をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-122">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="cde22-123">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、制御フロー デザイン画面の背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-123">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="cde22-124">**[SSIS]** メニューの **[パッケージ構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-124">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="cde22-125">**[パッケージ構成オーガナイザー]** ダイアログ ボックスで、 **[パッケージの構成を有効にする]** をオンにして、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-125">In the **Package Configuration Organize**r dialog box, select **Enable package configurations** if it is not already selected, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="cde22-126">パッケージ構成ウィザードの [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-126">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="cde22-127">[構成の種類の選択] ページで、[構成の**種類**] ボックスの一覧から [ **XML 構成ファイル**] を選択し、[**構成の場所を環境変数に格納**する] オプションを選択して、 `DataTransfer,` 一覧で**DataTransfer**環境変数を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="cde22-127">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, and type `DataTransfer,` or select the **DataTransfer** environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde22-128">環境変数を一覧で選択できるようにするには、変数を追加した後でコンピューターを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cde22-128">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span> <span data-ttu-id="cde22-129">コンピューターの再起動を避けたい場合は、環境変数の名前を入力してください。</span><span class="sxs-lookup"><span data-stu-id="cde22-129">If you do not want to restart the computer, you can type the name of the environment variable.</span></span>  
  
7.  <span data-ttu-id="cde22-130">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-130">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="cde22-131">[ウィザードの完了] ページで、 **[構成名]** ボックスに「 **DataTransfer EV Configuration** 」と入力し、 **[プレビュー]** ペインで構成の内容を確認してから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-131">On the Completing the Wizard page, type **DataTransfer EV Configuration** in the **Configuration name** box, review the configuration contents in the **Preview** pane, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="cde22-132">**[パッケージ構成オーガナイザー]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="cde22-132">Close the **Package Configuration Organize**r dialog box.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-datatransfer-package"></a><span data-ttu-id="cde22-133">DataTransfer パッケージの XML 構成を作成するには</span><span class="sxs-lookup"><span data-stu-id="cde22-133">To create the XML configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="cde22-134">ソリューション エクスプローラーで DataTransfer.dtsx をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-134">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="cde22-135">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、制御フロー デザイン画面の背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-135">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="cde22-136">**[SSIS]** メニューの **[パッケージ構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-136">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="cde22-137">[パッケージ構成オーガナイザー] ダイアログ ボックスで、 **[パッケージの構成を有効にする]** チェック ボックスをオンにし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-137">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="cde22-138">パッケージ構成ウィザードの [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-138">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="cde22-139">[構成の種類の選択] ページで、 **[構成の種類]** ボックスの一覧から **[XML 構成ファイル]** を選択し、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-139">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and then click **Browse**.</span></span>  
  
7.  <span data-ttu-id="cde22-140">**[構成ファイルの場所の選択]** ダイアログ ボックスで、C:\DeploymentTutorial に移動し、 **[ファイル名]** ボックスに「 **DataTransferConfig** 」と入力してから、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-140">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **DataTransferConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="cde22-141">[構成の種類の選択] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-141">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="cde22-142">[エクスポートするプロパティの選択] ページで、DataTransfer、接続マネージャー、Deployment Tutorial Log、および Properties を展開し、 **[接続文字列]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cde22-142">On the Select Properties to Export page, expand DataTransfer, Connection Managers, Deployment Tutorial Log, and Properties, and then select the **Connection String** check-box.</span></span>  
  
10. <span data-ttu-id="cde22-143">接続マネージャー内で NewCustomers を展開し、 **[接続文字列]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cde22-143">Within Connection Managers, expand NewCustomers, and then select the **Connection String** check-box.</span></span>  
  
11. <span data-ttu-id="cde22-144">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-144">Click **Next**.</span></span>  
  
12. <span data-ttu-id="cde22-145">[ウィザードの完了] ページで、 **[構成名]** ボックスに「 **DataTransfer Configuration** 」と入力し、構成の内容を確認してから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-145">On the Completing the Wizard page, type **DataTransfer Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="cde22-146">**[パッケージ構成オーガナイザー]** ダイアログ ボックスで、DataTransfer EV Configuration が最初に、DataTransfer Configuration が 2 番目に表示されていることを確認し、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-146">In the **Package Configuration Organizer** dialog box, verify that DataTransfer EV Configuration is listed first, and DataTransfer Configuration is listed second, and then click **Close**.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="cde22-147">LoadXMLData パッケージの間接構成を作成するには</span><span class="sxs-lookup"><span data-stu-id="cde22-147">To create indirect configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="cde22-148">ソリューション エクスプローラーで LoadXMLData.dtsx をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-148">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="cde22-149">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、制御フロー デザイン画面の背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-149">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="cde22-150">**[SSIS]** メニューの **[パッケージ構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-150">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="cde22-151">**[パッケージ構成オーガナイザー]** ダイアログ ボックスの **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-151">In the **Package Configuration Organize**r dialog box, Click **Add**.</span></span>  
  
5.  <span data-ttu-id="cde22-152">パッケージ構成ウィザードの [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-152">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="cde22-153">[構成の種類の選択] ページで、[構成の**種類**] ボックスの一覧の [ **XML 構成ファイル**] を選択し、[**構成の場所を環境変数に格納**する] オプションを選択して、 `LoadXMLData` `LoadXMLData` 一覧にある環境変数を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="cde22-153">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, type `LoadXMLData` or select the `LoadXMLData` environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde22-154">環境変数を一覧で選択できるようにするには、変数を追加した後でコンピューターを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cde22-154">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span>  
  
7.  <span data-ttu-id="cde22-155">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-155">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="cde22-156">[ウィザードの完了] ページで、 **[構成名]** ボックスに「 **LoadXMLData EV Configuration** 」と入力し、構成の内容を確認してから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-156">On the Completing the Wizard page, type **LoadXMLData EV Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="cde22-157">LoadXMLData パッケージの XML 構成を作成するには</span><span class="sxs-lookup"><span data-stu-id="cde22-157">To create the XML configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="cde22-158">ソリューション エクスプローラーで LoadXMLData.dtsx をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-158">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="cde22-159">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、制御フロー デザイン画面の背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-159">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="cde22-160">**[SSIS]** メニューの **[パッケージ構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-160">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="cde22-161">[パッケージ構成オーガナイザー] ダイアログ ボックスで、 **[パッケージの構成を有効にする]** チェック ボックスをオンにし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-161">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and click **Add**.</span></span>  
  
5.  <span data-ttu-id="cde22-162">パッケージ構成ウィザードの [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-162">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="cde22-163">[構成の種類の選択] ページで、 **[構成の種類]** ボックスの一覧から **[XML 構成ファイル]** を選択し、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-163">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and click **Browse**.</span></span>  
  
7.  <span data-ttu-id="cde22-164">**[構成ファイルの場所の選択]** ダイアログ ボックスで、C:\DeploymentTutorial に移動し、 **[ファイル名]** ボックスに「 **LoadXMLDataConfig** 」と入力してから、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-164">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **LoadXMLDataConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="cde22-165">[構成の種類の選択] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-165">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="cde22-166">[エクスポートするプロパティの選択] ページで、LoadXMLData、実行可能ファイル、Load XML Data、および Properties を展開し、 **[XMLSource].[XMLData]** チェック ボックスと **[XMLSource].[XMLSchemaDefinition]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cde22-166">On the Select Properties to Export page, expand LoadXMLData, Executables, Load XML Data, and Properties, and then select the **[XMLSource].[XMLData]** and **[XMLSource].[XMLSchemaDefinition]** check boxes.</span></span>  
  
10. <span data-ttu-id="cde22-167">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-167">Click **Next**.</span></span>  
  
11. <span data-ttu-id="cde22-168">[ウィザードの完了] ページで、 **[構成名]** ボックスに「 **LoadXMLData Configuration** 」と入力し、構成の内容を確認してから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-168">On the Completing the Wizard page, type **LoadXMLData Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
12. <span data-ttu-id="cde22-169">**[パッケージ構成オーガナイザー]** ダイアログ ボックスで、LoadXMLData EV Configuration が最初に、LoadXMLData Configuration が 2 番目に表示されていることを確認し、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cde22-169">In the **Package Configuration Organizer** dialog box, verify that the LoadXMLData EV Configuration is listed first, and the LoadXMLData Configuration is listed second, and then click **Close**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="cde22-170">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="cde22-170">Next Task in Lesson</span></span>  
 [<span data-ttu-id="cde22-171">手順 5:更新したパッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="cde22-171">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
<span data-ttu-id="cde22-172">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="cde22-172">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cde22-173">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cde22-173">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cde22-174">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="cde22-174">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cde22-175">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="cde22-175">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde22-176">参照</span><span class="sxs-lookup"><span data-stu-id="cde22-176">See Also</span></span>  
 <span data-ttu-id="cde22-177">[パッケージの構成](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="cde22-177">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="cde22-178">[パッケージ構成の作成](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="cde22-178">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 [<span data-ttu-id="cde22-179">パッケージで使用されるファイルへのアクセス</span><span class="sxs-lookup"><span data-stu-id="cde22-179">Access to Files Used by Packages</span></span>](../../2014/integration-services/access-to-files-used-by-packages.md)  
  
  
