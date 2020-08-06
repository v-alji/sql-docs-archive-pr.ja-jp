---
title: '手順 2: Foreach ループ コンテナーの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de5e8875c43edda618ccef4839c88c3b84a003cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632575"
---
# <a name="step-2-adding-and-configuring-the-foreach-loop-container"></a><span data-ttu-id="ad9c5-102">手順 2:Foreach ループ コンテナーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="ad9c5-102">Step 2: Adding and Configuring the Foreach Loop Container</span></span>
  <span data-ttu-id="ad9c5-103">この実習では、フラット ファイルのフォルダー全体にループ機能を付加し、レッスン 1 で使用したデータ フロー変換と同じ変換を各フラット ファイルに適用します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-103">In this task, you will add the ability to loop through a folder of flat files and apply the same data flow transformation used in Lesson 1 to each of those flat files.</span></span> <span data-ttu-id="ad9c5-104">そのためには、Foreach ループ コンテナーを制御フローに追加して、構成します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-104">You do this by adding and configuring a Foreach Loop container to the control flow.</span></span>  
  
 <span data-ttu-id="ad9c5-105">Foreach ループ コンテナーを追加したら、フォルダー内の各フラット ファイルに接続できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-105">The Foreach Loop container that you add must be able to connect to each flat file in the folder.</span></span> <span data-ttu-id="ad9c5-106">フォルダー内のファイルはすべて同じ形式なので、Foreach ループ コンテナーは、どのファイルに接続する場合でも同じフラット ファイル接続マネージャーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-106">Because all the files in the folder have the same format, the Foreach Loop container can use the same Flat File connection manager to connect to each of these files.</span></span> <span data-ttu-id="ad9c5-107">このループ コンテナーが使用するフラット ファイル接続マネージャーは、レッスン 1 で作成したフラット ファイル接続マネージャーと同じものです。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-107">The Flat File connection manager that the container will use is the same Flat File connection manager that you created in Lesson 1.</span></span>  
  
 <span data-ttu-id="ad9c5-108">レッスン 1 で作成したフラット ファイル接続マネージャーは、現在、1 つのフラット ファイルにのみ接続しています。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-108">Currently, the Flat File connection manager from Lesson 1 connects to only one, specific flat file.</span></span> <span data-ttu-id="ad9c5-109">フォルダーの各フラット ファイルに 1 つずつ接続するには、Foreach ループ コンテナーとフラット ファイル接続マネージャーをそれぞれ次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-109">To iteratively connect to each flat file in the folder, you will have to configure both the Foreach Loop container and the Flat File connection manager as follows:</span></span>  
  
-   <span data-ttu-id="ad9c5-110">**ForEach ループ コンテナー:** このコンテナーの列挙値をユーザー定義のパッケージ変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-110">**Foreach Loop container:** You will map the enumerated value of the container to a user-defined package variable.</span></span> <span data-ttu-id="ad9c5-111">ForEach ループ コンテナーは、このユーザー定義の変数を使用して、フラット ファイル接続マネージャーの `ConnectionString` プロパティを動的に変更しながら、フォルダー内の各フラット ファイルへ順番に接続します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-111">The container will then use this user-defined variable to dynamically modify the `ConnectionString` property of the Flat File connection manager and iteratively connect to each flat file in the folder.</span></span>  
  
-   <span data-ttu-id="ad9c5-112">**フラットファイル接続マネージャー:** レッスン1で作成した接続マネージャーを変更するには、ユーザー定義変数を使用して接続マネージャーのプロパティを設定し `ConnectionString` ます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-112">**Flat File connection manager:** You will modify the connection manager that was created in Lesson 1 by using a user-defined variable to populate the connection manager's `ConnectionString` property.</span></span>  
  
 <span data-ttu-id="ad9c5-113">この実習の手順では、ForEach ループ コンテナーを作成し、ユーザー定義パッケージ変数を使用するように変更する方法、およびデータ フロー タスクをこのループに追加する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-113">The procedures in this task show you how to create and modify the Foreach Loop container to use a user-defined package variable and to add the data flow task to the loop.</span></span> <span data-ttu-id="ad9c5-114">次の実習では、ユーザー定義変数を使用するようにフラット ファイル接続マネージャーを変更します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-114">You will learn how to modify the Flat File connection manager to use a user-defined variable in the next task.</span></span>  
  
 <span data-ttu-id="ad9c5-115">上記のように変更した後でこのパッケージを実行すると、Foreach ループ コンテナーによって、Sample Data フォルダー内のすべてのファイルが反復的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-115">After you have made these modifications to the package, when the package is run, the Foreach Loop Container will iterate through the collection of files in the Sample Data folder.</span></span> <span data-ttu-id="ad9c5-116">条件と一致するファイルが検出されるたびに、ユーザー定義の変数にそのファイルの名前が取り込まれ、Sample Currency Data フラット ファイル接続マネージャーの `ConnectionString` プロパティにマップされます。さらに、そのファイルに対してデータ フローが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-116">Each time a file is found that matches the criteria, the Foreach Loop Container will populate the user-defined variable with the file name, map the user-defined variable to the `ConnectionString` property of the Sample Currency Data Flat File connection manager, and then run the data flow against that file.</span></span> <span data-ttu-id="ad9c5-117">つまり、Foreach ループの反復処理が実行されるたびに、データ フロー タスクではそれぞれ異なるフラット ファイルが使用されることになります。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-117">Therefore, in each iteration of the Foreach Loop the Data Flow task will consume a different flat file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad9c5-118">[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では制御フローとデータ フローが分離されているので、制御フローにループを追加した場合でも、データ フローを修正する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-118">Because [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates control flow from data flow, any looping that you add to the control flow will not require modification to the data flow.</span></span> <span data-ttu-id="ad9c5-119">したがって、レッスン 1 で作成したデータ フローは変更する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-119">Therefore, the data flow that you created in Lesson 1 does not have to be changed.</span></span>  
  
### <a name="to-add-a-foreach-loop-container"></a><span data-ttu-id="ad9c5-120">ForEach ループ コンテナーを追加するには</span><span class="sxs-lookup"><span data-stu-id="ad9c5-120">To add a Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="ad9c5-121">**SQL Server Data Tools**で **[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-121">In **SQL Server Data Tools**, click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="ad9c5-122">**SSIS ツールボックス**で **[コンテナー]** を展開し、 **[ForEach ループ コンテナー]** を **[制御フロー]** タブのデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-122">In the **SSIS Toolbox**, expand **Containers**, and then drag a **Foreach Loop Container** onto the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="ad9c5-123">新しく追加した **[ForEach ループ コンテナー]** を右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-123">Right-click the newly added **Foreach Loop Container** and select **Edit**.</span></span>  
  
4.  <span data-ttu-id="ad9c5-124">[ **Foreach ループエディター** ] ダイアログボックスの **[全般**] ページで、[**名前**] に「」と入力し `Foreach File in Folder` ます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-124">In the **Foreach Loop Editor** dialog box, on the **General** page, for **Name**, enter `Foreach File in Folder`.</span></span> <span data-ttu-id="ad9c5-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-125">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ad9c5-126">[Foreach ループコンテナー] を右クリックし、[**プロパティ**] をクリックします。プロパティウィンドウで、 `LocaleID` プロパティが**英語 (米国)** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-126">Right-click the Foreach Loop container, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a><span data-ttu-id="ad9c5-127">ForEach ループ コンテナーの列挙子を構成するには</span><span class="sxs-lookup"><span data-stu-id="ad9c5-127">To configure the enumerator for the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="ad9c5-128">Foreach File in Folder をダブルクリックして、 **[Foreach ループ エディター]** をもう一度開きます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-128">Double-click Foreach File in Folder to reopen the **Foreach Loop Editor**.</span></span>  
  
2.  <span data-ttu-id="ad9c5-129">**[コレクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-129">Click **Collection**.</span></span>  
  
3.  <span data-ttu-id="ad9c5-130">**[コレクション]** ページで、 **[Foreach File 列挙子]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-130">On the **Collection** page, select **Foreach File Enumerator**.</span></span>  
  
4.  <span data-ttu-id="ad9c5-131">**[列挙子の構成]** で、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-131">In the **Enumerator configuration** group, click **Browse**.</span></span>  
  
5.  <span data-ttu-id="ad9c5-132">**[フォルダーの参照]** ダイアログ ボックスで、Currency_\*.txt ファイルが保存されている、コンピューター上のフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-132">In the **Browse for Folder** dialog box, locate the folder on your machine that contains the Currency_\*.txt files.</span></span>  
  
     <span data-ttu-id="ad9c5-133">このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-133">This sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="ad9c5-134">サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-134">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="ad9c5-135">「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-135">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="ad9c5-136">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-136">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="ad9c5-137">ハイパーリンク " https://msftisprodsamples.codeplex.com/downloads/get/578097 " SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-137">Click the  HYPERLINK "https://msftisprodsamples.codeplex.com/downloads/get/578097" SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
6.  <span data-ttu-id="ad9c5-138">**[ファイル]** ボックスに「**Currency_\*.txt**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-138">In the **Files** box, type **Currency_\*.txt**.</span></span>  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a><span data-ttu-id="ad9c5-139">ユーザー定義の変数に列挙子をマップするには</span><span class="sxs-lookup"><span data-stu-id="ad9c5-139">To map the enumerator to a user-defined variable</span></span>  
  
1.  <span data-ttu-id="ad9c5-140">**[変数のマッピング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-140">Click **Variable Mappings**.</span></span>  
  
2.  <span data-ttu-id="ad9c5-141">[**変数のマッピング**] ページの [**変数**] 列で、空のセルをクリックしてを選択し **\<New Variable...>** ます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-141">On the **Variable Mappings** page, in the **Variable** column, click the empty cell and select **\<New Variable...>**.</span></span>  
  
3.  <span data-ttu-id="ad9c5-142">[**変数の追加**] ダイアログボックスで、[**名前**] に「」と入力 `varFileName` します。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-142">In the **Add Variable** dialog box, for **Name**, type `varFileName`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ad9c5-143">変数名では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-143">Variable names are case sensitive.</span></span>  
  
4.  <span data-ttu-id="ad9c5-144">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-144">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ad9c5-145">再び **[OK]** をクリックし、 **[Foreach ループ エディター]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-145">Click **OK** again to exit the **Foreach Loop Editor** dialog box.</span></span>  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a><span data-ttu-id="ad9c5-146">データ フロー タスクをループに追加するには</span><span class="sxs-lookup"><span data-stu-id="ad9c5-146">To add the data flow task to the loop</span></span>  
  
-   <span data-ttu-id="ad9c5-147">[ **Extract Sample Currency data** ] データフロータスクを、名前を変更した Foreach ループコンテナーにドラッグし `Foreach File in Folder` ます。</span><span class="sxs-lookup"><span data-stu-id="ad9c5-147">Drag the **Extract Sample Currency Data** data flow task onto the Foreach Loop container now renamed `Foreach File in Folder`.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="ad9c5-148">次のレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="ad9c5-148">Next Lesson Task</span></span>  
 [<span data-ttu-id="ad9c5-149">手順 3:フラット ファイル接続マネージャーの変更</span><span class="sxs-lookup"><span data-stu-id="ad9c5-149">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="ad9c5-150">参照</span><span class="sxs-lookup"><span data-stu-id="ad9c5-150">See Also</span></span>  
 <span data-ttu-id="ad9c5-151">[Foreach ループコンテナーの構成](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="ad9c5-151">[Configure a Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="ad9c5-152">パッケージで変数を使用する</span><span class="sxs-lookup"><span data-stu-id="ad9c5-152">Use Variables in Packages</span></span>](use-variables-in-packages.md)  
  
