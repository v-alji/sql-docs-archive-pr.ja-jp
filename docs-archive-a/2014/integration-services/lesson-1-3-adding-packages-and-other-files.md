---
title: '手順 3: パッケージとその他のファイルの追加 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a7e6ec9c-d31d-4613-9525-8947a7b358f7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d5ddcb6315576558161119a8774bccbd63fa5844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641104"
---
# <a name="step-3-adding-packages-and-other-files"></a><span data-ttu-id="944db-102">手順 3:パッケージとその他のファイルの追加</span><span class="sxs-lookup"><span data-stu-id="944db-102">Step 3: Adding Packages and Other Files</span></span>
  <span data-ttu-id="944db-103">このタスクでは、既存のパッケージ、個々のパッケージをサポートする補助ファイル、および Readme を、前のタスクで作成した Deployment Tutorial プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="944db-103">In this task, you will add existing packages, ancillary files that support individual packages, and a Readme to the Deployment Tutorial project that you created in the previous task.</span></span> <span data-ttu-id="944db-104">たとえば、パッケージのデータを含んでいる XML データ ファイルや、プロジェクトのすべてのパッケージに関する Readme 情報を提供するテキスト ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="944db-104">For example, you will add an XML data file that contains the data for a package and a text file that provides Readme information about all the packages in the project.</span></span>  
  
 <span data-ttu-id="944db-105">パッケージをテスト環境または運用環境に配置するとき、通常はデータ ファイルを配置に含めるのではなく、テスト バージョンまたは運用バージョンのデータ ファイルまたはデータベースにアクセスできるように、構成ファイルでデータ ソースへのパスを更新します。</span><span class="sxs-lookup"><span data-stu-id="944db-105">When you deploy packages to a test or production environment, you typically do not include the data files in the deployment, but instead use configurations to update the paths of the data sources to access test or production versions of the data files or databases.</span></span> <span data-ttu-id="944db-106">このチュートリアルでは、手順を説明する目的で、データ ファイルをパッケージの配置に含めます。</span><span class="sxs-lookup"><span data-stu-id="944db-106">For instructional purposes, this tutorial includes data files in the package deployment.</span></span>  
  
 <span data-ttu-id="944db-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のサンプルをインストールすると、パッケージとパッケージで使用されるサンプル データがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="944db-107">The packages and the sample data that the packages use are installed when you install the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="944db-108">Deployment Tutorial プロジェクトに次のパッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="944db-108">You will add the following packages to the Deployment Tutorial project:</span></span>  
  
-   <span data-ttu-id="944db-109">**DataTransfer。**</span><span class="sxs-lookup"><span data-stu-id="944db-109">**DataTransfer.**</span></span> <span data-ttu-id="944db-110">フラット ファイルからデータを抽出し、列の値を評価して、条件に応じてデータセット内で行を維持し、データを AdventureWorks データベースのテーブルに読み込む基本パッケージです。</span><span class="sxs-lookup"><span data-stu-id="944db-110">Basic package that extracts data from a flat file, evaluates column values to conditionally keep rows in the dataset, and loads data into a table in the AdventureWorks database.</span></span>  
  
-   <span data-ttu-id="944db-111">**LoadXMLData。**</span><span class="sxs-lookup"><span data-stu-id="944db-111">**LoadXMLData.**</span></span> <span data-ttu-id="944db-112">XML データ ファイルからデータを抽出し、列の値を評価して集計し、AdventureWorks データベースのテーブルにデータを読み込むデータ転送パッケージです。</span><span class="sxs-lookup"><span data-stu-id="944db-112">Data-transfer package that extracts data from an XML data file, evaluates and aggregates column values, and loads data into a table in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="944db-113">これらのパッケージの配置をサポートするために、次の付属ファイルを Deployment Tutorial プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="944db-113">To support the deployment of these packages, you will add the following ancillary files to the Deployment Tutorial project.</span></span>  
  
|<span data-ttu-id="944db-114">Package</span><span class="sxs-lookup"><span data-stu-id="944db-114">Package</span></span>|<span data-ttu-id="944db-115">ファイル</span><span class="sxs-lookup"><span data-stu-id="944db-115">File</span></span>|  
|-------------|----------|  
|<span data-ttu-id="944db-116">DataTransfer</span><span class="sxs-lookup"><span data-stu-id="944db-116">DataTransfer</span></span>|<span data-ttu-id="944db-117">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="944db-117">NewCustomers.txt</span></span>|  
|<span data-ttu-id="944db-118">LoadXMLData</span><span class="sxs-lookup"><span data-stu-id="944db-118">LoadXMLData</span></span>|<span data-ttu-id="944db-119">orders.xml および orders.xsd</span><span class="sxs-lookup"><span data-stu-id="944db-119">orders.xml and orders.xsd</span></span>|  
  
 <span data-ttu-id="944db-120">また、Readme も追加します。これは、Deployment Tutorial プロジェクトに関する情報を提供するテキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="944db-120">You will also add a Readme, which is a text file that provides information about the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="944db-121">次の手順で使用するパスでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のサンプルが既定の場所である [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)]にインストールされていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="944db-121">The paths used in the following procedures assume that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples were installed in the default location, [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)].</span></span> <span data-ttu-id="944db-122">サンプルを別の場所にインストールした場合は、手順でその場所を使用してください。</span><span class="sxs-lookup"><span data-stu-id="944db-122">If you installed the samples to a different location, you should use that location instead in the procedures.</span></span>  
  
 <span data-ttu-id="944db-123">次のタスクでは、DataTransfer パッケージと LoadXMLData パッケージに構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="944db-123">In the next task, you will add configurations to the DataTransfer and LoadXMLData packages.</span></span> <span data-ttu-id="944db-124">構成はすべて XML ファイルで保存され、システム環境変数を使用して、これらのファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="944db-124">All configurations are stored in XML files, and you will use a system environment variable to specify the location of the files.</span></span> <span data-ttu-id="944db-125">構成ファイルを作成して、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="944db-125">After you create the configuration files, you will add them to the project.</span></span>  
  
### <a name="to-add-packages-to-the-deployment-tutorial-project"></a><span data-ttu-id="944db-126">Deployment Tutorial プロジェクトにパッケージを追加するには</span><span class="sxs-lookup"><span data-stu-id="944db-126">To add packages to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="944db-127">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントして、 **[SQL Server Data Tools]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-127">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="944db-128">**[ファイル]** メニューの **[開く]** をクリックし、 **[プロジェクト/ソリューション]** をクリックします。次に、 **[Deployment Tutorial]** フォルダーをクリックして **[開く]** をクリックし、 **Deployment Tutorial.sln**をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-128">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="944db-129">ソリューション エクスプローラーで、Deployment Tutorial を右クリックして  **追加** をクリックし、**既存のパッケージ** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-129">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Package**.</span></span>  
  
4.  <span data-ttu-id="944db-130">**[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]** で、 **[ファイル システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-130">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
5.  <span data-ttu-id="944db-131">参照ボタン ( **[...]** ) をクリックして、C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages に移動し、**DataTransfer.dtsx** をクリックして **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-131">Click the browse **(...)** button, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages, select **DataTransfer.dtsx**, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="944db-132">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-132">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="944db-133">手順 3. ～ 6. を繰り返して LoadXMLData.dtsx を追加します。このパッケージは C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages にあります。</span><span class="sxs-lookup"><span data-stu-id="944db-133">Repeat steps 3 - 6, and this time add LoadXMLData.dtsx, which is found in C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages.</span></span>  
  
### <a name="to-add-ancillary-files-to-the-deployment-tutorial-project"></a><span data-ttu-id="944db-134">Deployment Tutorial プロジェクトに付属ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="944db-134">To add ancillary files to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="944db-135">ソリューション エクスプローラーで、Deployment Tutorial を右クリックして  **追加** をクリックし、**既存の項目** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-135">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="944db-136">**[既存の項目の追加 - Deployment Tutorial]** ダイアログ ボックスで C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data に移動し、orders.xml、orders.xsd、および NewCustomers.txt を選択して、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-136">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data, select orders.xml, orders.xsd, and NewCustomers.txt, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="944db-137">**[既存の項目の追加 - Deployment Tutorial]** ダイアログ ボックスで C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\に移動し、Readme.txt を選択して、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-137">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\, select Readme.txt and click **Add**.</span></span>  
  
4.  <span data-ttu-id="944db-138">ファイル メニューの  **すべてを保存** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="944db-138">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="944db-139">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="944db-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="944db-140">手順 4: パッケージ構成の追加</span><span class="sxs-lookup"><span data-stu-id="944db-140">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
<span data-ttu-id="944db-141">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="944db-141">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="944db-142">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="944db-142">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="944db-143">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="944db-143">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="944db-144">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="944db-144">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
