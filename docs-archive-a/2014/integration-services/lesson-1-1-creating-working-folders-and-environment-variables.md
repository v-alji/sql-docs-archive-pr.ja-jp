---
title: '手順 1: 作業フォルダーと環境変数の作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45091ba2-ea3d-4399-9814-489d812b42cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63308d406e230538e5ca8b90dbb55bb802759bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641110"
---
# <a name="step-1-creating-working-folders-and-environment-variables"></a><span data-ttu-id="67401-102">手順 1:作業フォルダーと環境変数の作成</span><span class="sxs-lookup"><span data-stu-id="67401-102">Step 1: Creating Working Folders and Environment Variables</span></span>
  <span data-ttu-id="67401-103">このタスクでは、この後のチュートリアル タスクで使用する作業フォルダー (C:\DeploymentTutorial) と新しいシステム環境変数 (`DataTransfer` および `LoadXMLData`) を作成します。</span><span class="sxs-lookup"><span data-stu-id="67401-103">In this task, you will create the working folder (C:\DeploymentTutorial) and the new system environment variables (`DataTransfer` and `LoadXMLData`) that you will use in later tutorial tasks.</span></span>  
  
 <span data-ttu-id="67401-104">作業フォルダーは、C ドライブのルートにあります。</span><span class="sxs-lookup"><span data-stu-id="67401-104">The working folder is at the root of the C drive.</span></span> <span data-ttu-id="67401-105">別のドライブまたは場所を使用する必要がある場合は、変更してかまいません。</span><span class="sxs-lookup"><span data-stu-id="67401-105">If you must use a different drive or location, you can do that.</span></span> <span data-ttu-id="67401-106">ただし、この場所を書き留めておいて、チュートリアルで DeploymentTutorial 作業フォルダーの場所が参照されたときに、該当する場所を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67401-106">However, you need to note this location and then use it wherever the tutorial refers to the location of the DeploymentTutorial working folder.</span></span>  
  
 <span data-ttu-id="67401-107">この後のレッスンでは、ファイル システムに保存されているパッケージを msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースの sysssispackages テーブルに配置します。</span><span class="sxs-lookup"><span data-stu-id="67401-107">In a later lesson, you will deploy packages that are saved to the file system to the sysssispackages table in the msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="67401-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージは別のコンピューターに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="67401-108">Ideally you will deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to a different computer.</span></span> <span data-ttu-id="67401-109">これが不可能な場合でも、パッケージをローカル コンピューターの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに配置してこのチュートリアルを実行すれば、多くのことを学習できます。</span><span class="sxs-lookup"><span data-stu-id="67401-109">If that is not possible, you can still learn a lot from doing this tutorial by deploying the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is on the local computer.</span></span> <span data-ttu-id="67401-110">ローカル コンピューターと配置先コンピューターで使用する環境変数には同じ変数名が付いていますが、変数に格納される値は異なります。</span><span class="sxs-lookup"><span data-stu-id="67401-110">The environment variables that are used on the local and destination computers have the same variable names, but different values are stored in the variables.</span></span> <span data-ttu-id="67401-111">たとえば、ローカル コンピューターでは、環境変数 `DataTransfer` の値は C:\DeploymentTutorial フォルダーを参照しています。一方、ターゲット コンピューターでは、環境変数 `DataTransfer` は C:\DeploymentTutorialInstall フォルダーを参照しています。</span><span class="sxs-lookup"><span data-stu-id="67401-111">For example, on the local computer, the value of the environment variable `DataTransfer` references the C:\DeploymentTutorial folder, whereas on the target computer the environment variable `DataTransfer` references the C:\DeploymentTutorialInstall folder.</span></span>  
  
 <span data-ttu-id="67401-112">ローカル コンピューターに配置する場合は、1 つのセットの環境変数を作成するだけで済みます。ただし、ローカルの配置を行う前に、環境変数を適切な値に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67401-112">If you plan to deploy to the local computer, you need to create only one set of environment variables; however, you will need to update the value of the environment variables to an appropriate value before you do the local deployment.</span></span>  
  
 <span data-ttu-id="67401-113">パッケージを別のコンピューターに配置する場合は、2 つのセットの環境変数を作成する必要があります。1 つはローカル コンピューター用で、もう 1 つは配置先コンピューター用です。</span><span class="sxs-lookup"><span data-stu-id="67401-113">If you plan to deploy the packages to a different computer, you must create two sets of environment variables: one set for the local computer, and one set for the destination computer.</span></span> <span data-ttu-id="67401-114">現時点では、ソース コンピューター用の変数のみを作成できます。配置先コンピューター用の変数は後で作成しますが、配置先コンピューターにパッケージをインストールする前に、このコンピューターでフォルダーと環境変数が使用可能になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="67401-114">You can create only the variables for the source computer now, and create the variables for the destination computer later, but you must have both the folder and environment variables available on the destination computer before you can install the packages on that computer.</span></span>  
  
### <a name="to-create-the-local-working-folder"></a><span data-ttu-id="67401-115">ローカルの作業フォルダーを作成するには</span><span class="sxs-lookup"><span data-stu-id="67401-115">To create the local working folder</span></span>  
  
1.  <span data-ttu-id="67401-116">[スタート] メニューを右クリックし、[エクスプローラー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-116">Right-click the Start menu, and click Explore.</span></span>  
  
2.  <span data-ttu-id="67401-117">**[ローカル ディスク (C:)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-117">Click **Local Disk (C:)**.</span></span>  
  
3.  <span data-ttu-id="67401-118">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[フォルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-118">On the **File** menu, point to **New**, and then click **Folder**.</span></span>  
  
4.  <span data-ttu-id="67401-119">新しいフォルダーの名前をに変更 `DeploymentTutorial` します。</span><span class="sxs-lookup"><span data-stu-id="67401-119">Rename New Folder to `DeploymentTutorial`.</span></span>  
  
### <a name="to-create-local-environment-variables"></a><span data-ttu-id="67401-120">ローカルの環境変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="67401-120">To create local environment variables</span></span>  
  
1.  <span data-ttu-id="67401-121">**[スタート]** ボタンをクリックし、 **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-121">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="67401-122">コントロール パネルで、 **[システム]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-122">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="67401-123">**[システムのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** タブをクリックし、 **[環境変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-123">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="67401-124">**[環境変数]** ダイアログ ボックスの **[システム環境変数]** フレームで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-124">In the **Environment Variables** dialog box, in the **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="67401-125">[**新しいシステム変数**] ダイアログボックスで、[ `DataTransfer` **変数名**] ボックスに「」と入力し、[変数の `C:\DeploymentTutorial\datatransferconfig.dtsconfig` **値**] ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="67401-125">In the **New System Variable** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorial\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="67401-126">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-126">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="67401-127">もう一度 [**新規**] をクリックし、[ `LoadXMLData` **変数名**] ボックスに「」と入力し、[ `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` 変数の**値**] ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="67401-127">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="67401-128">**[OK]** をクリックして **[環境変数]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="67401-128">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="67401-129">**[OK]** をクリックして **[システムのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="67401-129">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="67401-130">必要に応じて、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="67401-130">Optionally, restart your computer.</span></span> <span data-ttu-id="67401-131">コンピューターを再起動しない場合、新しい変数の名前はパッケージ構成ウィザードには表示されませんが、この変数を使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="67401-131">If you do not restart the computer, the name of the new variable will not be displayed in the Package Configuration Wizard, but you can still use it.</span></span>  
  
### <a name="to-create-destination-environment-variables"></a><span data-ttu-id="67401-132">配置先の環境変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="67401-132">To create destination environment variables</span></span>  
  
1.  <span data-ttu-id="67401-133">**[スタート]** ボタンをクリックし、 **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-133">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="67401-134">コントロール パネルで、 **[システム]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-134">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="67401-135">**[システムのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** タブをクリックし、 **[環境変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-135">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="67401-136">**[環境変数]** ダイアログ ボックスの **[システム環境変数]** フレームで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-136">In the **Environment Variables** dialog box, in **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="67401-137">[**新しいシステム変数**] ダイアログボックスで、[ `DataTransfer` **変数名**] ボックスに「」と入力し、[変数の `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` **値**] ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="67401-137">In the **New System Variables** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="67401-138">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67401-138">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="67401-139">もう一度 [**新規**] をクリックし、[ `LoadXMLData` **変数名**] ボックスに「」と入力し、[ `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` 変数の**値**] ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="67401-139">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="67401-140">**[OK]** をクリックして **[環境変数]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="67401-140">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="67401-141">**[OK]** をクリックして **[システムのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="67401-141">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="67401-142">必要に応じて、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="67401-142">Optionally, restart your computer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="67401-143">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="67401-143">Next Task in Lesson</span></span>  
 [<span data-ttu-id="67401-144">手順 2: 配置プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="67401-144">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
<span data-ttu-id="67401-145">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="67401-145">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="67401-146">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="67401-146">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="67401-147">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="67401-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="67401-148">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="67401-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
