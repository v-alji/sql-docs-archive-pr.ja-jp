---
title: '手順 2: パッケージ構成の有効化と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a804efcd84ebe563a13f61443fe19096788ca809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633894"
---
# <a name="step-2-enabling-and-configuring-package-configurations"></a><span data-ttu-id="6a460-102">手順 2:パッケージ構成の有効化と構成</span><span class="sxs-lookup"><span data-stu-id="6a460-102">Step 2: Enabling and Configuring Package Configurations</span></span>
  <span data-ttu-id="6a460-103">ここでは、パッケージ構成ウィザードを使用することで、プロジェクトをパッケージ配置モデルに変換してパッケージ構成を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6a460-103">In this task, you will convert the project to the Package Deployment Model and enable package configurations using the Package Configuration Wizard.</span></span> <span data-ttu-id="6a460-104">ここでは、Foreach ループ コンテナーの `Directory` プロパティの構成設定が記述された XML 構成ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="6a460-104">You will use this wizard to generate an XML configuration file that contains configuration settings for the `Directory` property of the Foreach Loop container.</span></span> <span data-ttu-id="6a460-105">Directory プロパティの値は、実行時に更新できる新しいパッケージ レベル変数を使って指定します。</span><span class="sxs-lookup"><span data-stu-id="6a460-105">The value of the Directory property is supplied by a new package-level variable that you can update at run time.</span></span> <span data-ttu-id="6a460-106">また、テスト時に使用する新しいサンプル データを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a460-106">Additionally, you will populate a new sample data folder to use during testing.</span></span>  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a><span data-ttu-id="6a460-107">Directory プロパティにマップする新しいパッケージ レベル変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="6a460-107">To create a new package-level variable mapped to the Directory property</span></span>  
  
1.  <span data-ttu-id="6a460-108">**デザイナーで、** [制御フロー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブの背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-108">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="6a460-109">これにより、作成する変数のスコープがこのパッケージに限定されます。</span><span class="sxs-lookup"><span data-stu-id="6a460-109">This sets the scope for the variable you will create to the package.</span></span>  
  
2.  <span data-ttu-id="6a460-110">[ [!INCLUDE[ssIS](../includes/ssis-md.md)] ] メニューの **[変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-110">On the [!INCLUDE[ssIS](../includes/ssis-md.md)] menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="6a460-111">**[変数]** ウィンドウで、[変数の追加] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-111">In the **Variables** window, click the Add Variable icon.</span></span>  
  
4.  <span data-ttu-id="6a460-112">**[名前]** ボックスに「 **varFolderName**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="6a460-112">In the **Name** box, type **varFolderName**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6a460-113">変数名では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="6a460-113">Variable names are case sensitive.</span></span>  
  
5.  <span data-ttu-id="6a460-114">[**スコープ**] ボックスにパッケージの名前 (レッスン 5) が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a460-114">Verify that the **Scope** box shows the name of the package, Lesson 5.</span></span>  
  
6.  <span data-ttu-id="6a460-115">**変数の** [データ型] `varFolderName` ボックスの値を **[String]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="6a460-115">Set the value of the **Data Type** box of the `varFolderName` variable to **String**.</span></span>  
  
7.  <span data-ttu-id="6a460-116">**[制御フロー]** タブに戻り、 **[Foreach File in Folder]** コンテナーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-116">Return to the **Control Flow** tab and double-click the **Foreach File in Folder** container.</span></span>  
  
8.  <span data-ttu-id="6a460-117">[ **Foreach ループエディター**] の [**コレクション**] ページで、[**式**] をクリックし、省略記号ボタン ([. **..])** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-117">On the **Collection** page of the **Foreach Loop Editor**, click **Expressions**, and then click the ellipsis button **(...)**.</span></span>  
  
9. <span data-ttu-id="6a460-118">[**プロパティ式エディター**] で、**プロパティ**リスト内をクリックし、を選択し `Directory` ます。</span><span class="sxs-lookup"><span data-stu-id="6a460-118">In the **Property Expressions Editor**, click in the **Property** list, and select `Directory`.</span></span>  
  
10. <span data-ttu-id="6a460-119">[**式**] ボックスで、省略記号ボタン **([...])** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-119">In the **Expression** box, click the ellipsis button **(...)**.</span></span>  
  
11. <span data-ttu-id="6a460-120">**[式ビルダー]** で [変数] フォルダーを展開し、 **User::varFolderName** 変数を **[式]** ボックスへドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6a460-120">In the **Expression Builder**, expand the Variables folder, and drag the variable **User::varFolderName** to the **Expression** box.</span></span>  
  
12. <span data-ttu-id="6a460-121">**[OK]** をクリックして **[式ビルダー]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="6a460-121">Click **OK** to exit the **Expression Builder**.</span></span>  
  
13. <span data-ttu-id="6a460-122">**[OK]** をクリックして **[プロパティ式エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="6a460-122">Click **OK** to exit the **Property Expressions Editor**.</span></span>  
  
14. <span data-ttu-id="6a460-123">**[OK]** をクリックし、 **[Foreach ループ エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="6a460-123">Click **OK** to exit the **Foreach Loop Editor**.</span></span>  
  
### <a name="to-enable-package-configurations"></a><span data-ttu-id="6a460-124">パッケージ構成を有効にするには</span><span class="sxs-lookup"><span data-stu-id="6a460-124">To enable package configurations</span></span>  
  
1.  <span data-ttu-id="6a460-125">**[プロジェクト]** メニューの **[パッケージ配置モデルに変換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-125">On the **Project Menu**, click **Convert to Package Deployment Model**.</span></span>  
  
2.  <span data-ttu-id="6a460-126">警告のメッセージで **[OK]** をクリックし、変換が完了したら、 **[パッケージ配置モデルに変換]** ダイアログで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-126">Click **OK** on the warning prompt and, once the conversion is complete, click **OK** on the **Convert to Package Deployment Model** dialog.</span></span>  
  
3.  <span data-ttu-id="6a460-127">**デザイナーで、** [制御フロー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブの背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-127">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
4.  <span data-ttu-id="6a460-128">**[SSIS]** メニューの **[パッケージ構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-128">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
5.  <span data-ttu-id="6a460-129">**[パッケージ構成オーガナイザー]** ダイアログ ボックスで **[パッケージの構成を有効にする]** をクリックし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-129">In the **Package Configurations Organizer** dialog box, select **Enable Package Configurations**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="6a460-130">パッケージ構成ウィザードの [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-130">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
7.  <span data-ttu-id="6a460-131">**[構成の種類の選択]** ページで、 **[構成の種類]** が **[XML 構成ファイル]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a460-131">On the **Select Configuration Type** page, verify that the **Configuration type** is set to **XML configuration file**.</span></span>  
  
8.  <span data-ttu-id="6a460-132">**[構成の種類の選択]** ページで **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-132">On the **Select Configuration Type** page, click **Browse**.</span></span>  
  
9. <span data-ttu-id="6a460-133">**[構成ファイルの場所の選択]** ダイアログ ボックスが開きます。既定の場所はプロジェクト フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="6a460-133">By default, the **Select Configuration File Location** dialog box will open to the project folder.</span></span>  
  
10. <span data-ttu-id="6a460-134">**[構成ファイルの場所の選択]** ダイアログ ボックスで、 **[ファイル名]** に「 **SSISTutorial**」と入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-134">In the **Select Configuration File Location** dialog box, for **File name** type **SSISTutorial**, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="6a460-135">**[構成の種類の選択]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-135">On the **Select Configuration Type** page, click **Next.**</span></span>  
  
12. <span data-ttu-id="6a460-136">[**エクスポートするプロパティの選択**] ページの [**オブジェクト**] ペインで、[**変数**] を展開し、[ **varfoldername**]、[ **Properties**] の順に展開して、[**値**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6a460-136">On the **Select Properties to Export** page, in the **Objects** pane, expand **Variables**, expand **varFolderName**, expand **Properties**, and then select **Value**.</span></span>  
  
13. <span data-ttu-id="6a460-137">**[エクスポートするプロパティの選択]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-137">On the **Select Properties to Export** page, click **Next**.</span></span>  
  
14. <span data-ttu-id="6a460-138">**[ウィザードの完了]** ページで、作成した構成の構成名を入力します。たとえば、「 **SSIS Tutorial Directory configuration**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="6a460-138">On the **Completing the Wizard** page, type a configuration name for the configuration, such as **SSIS Tutorial Directory configuration**.</span></span> <span data-ttu-id="6a460-139">ここに入力した構成名が **[パッケージ構成オーガナイザー]** ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a460-139">This is the configuration name that is displayed in the **Package Configuration Organizer** dialog box.</span></span>  
  
15. <span data-ttu-id="6a460-140">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="6a460-141">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a460-141">Click **Close**.</span></span>  
  
17. <span data-ttu-id="6a460-142">ウィザードによって、Ssistutorial.dtsconfig という名前の構成ファイルが作成されます。この構成ファイルには、変数のの構成設定が含まれています。これにより、 `value` `Directory` 列挙子のプロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="6a460-142">The wizard creates a configuration file, named SSISTutorial.dtsConfig, that contains configuration settings for the `value` of the variable that in turn sets the `Directory` property of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6a460-143">通常、構成ファイルにはパッケージのプロパティに関する複雑な情報が含まれていますが、このチュートリアルでは、次の構成情報のみを使用します:</span><span class="sxs-lookup"><span data-stu-id="6a460-143">A configuration file typically contains complex information about the package properties, but for this tutorial the only configuration information should be</span></span>  
    > <span data-ttu-id="6a460-144"><Configuration ConfiguredType="Property"</span><span class="sxs-lookup"><span data-stu-id="6a460-144"><Configuration ConfiguredType="Property"</span></span>  
    > <span data-ttu-id="6a460-145">Path = "\ Package. Variables [User:: varFolderName]。プロパティ [値] "ValueType =" 文字列 "\></span><span class="sxs-lookup"><span data-stu-id="6a460-145">Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"\></span></span>  
    >  \<ConfiguredValue>\</ConfiguredValue>  
    > <span data-ttu-id="6a460-146">\</Configuration>.</span><span class="sxs-lookup"><span data-stu-id="6a460-146">\</Configuration>.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="6a460-147">新しいサンプル データ フォルダーを作成して、データを取り込むには</span><span class="sxs-lookup"><span data-stu-id="6a460-147">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="6a460-148">Windows エクスプローラーで、ドライブのルートレベル (C: など \\ ) に、という名前の新しいフォルダーを作成し `New Sample Data` ます。</span><span class="sxs-lookup"><span data-stu-id="6a460-148">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named `New Sample Data`.</span></span>  
  
2.  <span data-ttu-id="6a460-149">コンピューター上でサンプル ファイルを探し、フォルダーから 3 つのファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="6a460-149">Locate the sample files on your computer and copy three of the files from the folder.</span></span>  
  
3.  <span data-ttu-id="6a460-150">フォルダーに、 `New Sample Data` コピーしたファイルを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6a460-150">In the `New Sample Data` folder, paste the copied files.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6a460-151">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="6a460-151">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6a460-152">手順 3:Directory プロパティの構成値の変更</span><span class="sxs-lookup"><span data-stu-id="6a460-152">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
  
