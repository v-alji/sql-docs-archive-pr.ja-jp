---
title: Integration Services の配置ウィザード |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9afdc529baa4546f126eb67456927e770cb345dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736570"
---
# <a name="integration-services-deployment-wizard"></a><span data-ttu-id="d8964-102">Integration Services 配置ウィザード</span><span class="sxs-lookup"><span data-stu-id="d8964-102">Integration Services Deployment Wizard</span></span>
  <span data-ttu-id="d8964-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 配置ウィザードでは、プロジェクト配置モデルを使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの SSISDB カタログにプロジェクトが配置されます。</span><span class="sxs-lookup"><span data-stu-id="d8964-103">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard deploys projects to the SSISDB catalog on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance using the project deployment model.</span></span>  
  
 <span data-ttu-id="d8964-104">で開いているプロジェクトから配置ウィザードを起動するには、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [**プロジェクト**] メニューの [**配置**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8964-104">To start the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard from an open project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], select **Deploy** from the **Project** menu.</span></span> <span data-ttu-id="d8964-105">でウィザードを開始するには、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] オブジェクトエクスプローラーで [ **Integration Services カタログ**] [SSISDB] ノードの順に展開し、[  >  **SSISDB** **プロジェクト**] フォルダーを右クリックして、[**プロジェクトの配置**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8964-105">To start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** > **SSISDB** node in Object Explorer, right-click the **Projects** folder, and then click **Deploy Project**.</span></span>  
  
 <span data-ttu-id="d8964-106">このウィザードでは、次の 4 つの手順を行います。</span><span class="sxs-lookup"><span data-stu-id="d8964-106">The wizard proceeds through the following four steps.</span></span> <span data-ttu-id="d8964-107">次の手順に移動する場合は [**次**へ] をクリックし、前の手順に戻る場合は [**前**へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8964-107">Click **Next** to move to the next step, or **Previous** to return to the previous step.</span></span>  
  
1.  <span data-ttu-id="d8964-108">**[ソースの選択]** -デプロイするプロジェクトを選択し [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d8964-108">**Select Source** - Select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that you want to deploy.</span></span>  
  
2.  <span data-ttu-id="d8964-109">**[変換先] を選択**し、プロジェクトの変換先を選択します。</span><span class="sxs-lookup"><span data-stu-id="d8964-109">**Select Destination** - Select the project destination.</span></span>  
  
3.  <span data-ttu-id="d8964-110">**レビュー** -選択内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d8964-110">**Review** - Displays your selections.</span></span>  
  
4.  <span data-ttu-id="d8964-111">[**配置/結果**]-プロジェクトを配置し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="d8964-111">**Deploy/Results** - Deploys the project and displays the results.</span></span>  
  
## <a name="select-source"></a><span data-ttu-id="d8964-112">ソースを選択する</span><span class="sxs-lookup"><span data-stu-id="d8964-112">Select Source</span></span>  
 <span data-ttu-id="d8964-113">作成したプロジェクト配置ファイルを配置するには、[**プロジェクト配置ファイル**] を選択し、ispac ファイルのパスを入力するか、[**参照**] をクリックしてプロジェクトフォルダー内で検索します。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8964-113">To deploy a project deployment file that you created, select **Project deployment file** and enter the path to the .ispac file or click **Browse** to find it in the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project folder.</span></span> <span data-ttu-id="d8964-114">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログにあるプロジェクトを配置するには、 **[Integration Services カタログ]** を選択し、サーバー名とカタログ内のプロジェクトのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d8964-114">To deploy a project that resides in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, select **Integration Services catalog**, and then enter the server name and the path to the project in the catalog.</span></span>  
  
 <span data-ttu-id="d8964-115">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でウィザードを起動すると、既定では、開いているプロジェクトがソースとして選択され、この手順が省略されます。</span><span class="sxs-lookup"><span data-stu-id="d8964-115">If you start the wizard in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], then by default the wizard selects the open project as the source and skips this step.</span></span> <span data-ttu-id="d8964-116">この手順に戻り、別のソースを選択するには、[**前**へ] をクリックするか、左ペインで [**ソースの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8964-116">To return to this step and select a different source, click **Previous** or click **Select Source** in the left pane.</span></span>  
  
## <a name="select-destination"></a><span data-ttu-id="d8964-117">[配置先の選択]</span><span class="sxs-lookup"><span data-stu-id="d8964-117">Select Destination</span></span>  
 <span data-ttu-id="d8964-118">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログでプロジェクトの配置先フォルダーを選択するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスを入力するか、 **[参照]** をクリックしてサーバーの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="d8964-118">To select the destination folder for the project in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, enter the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance or click **Browse** to select from a list of servers.</span></span> <span data-ttu-id="d8964-119">SSISDB でプロジェクトのパスを入力するか、 **[参照]** をクリックしてプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d8964-119">Enter the project path in SSISDB or click **Browse** to select it.</span></span>  
  
 <span data-ttu-id="d8964-120">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でウィザードを起動すると、既定では、接続されているサーバー インスタンスが選択され、選択したプロジェクトのパスが入力されます。</span><span class="sxs-lookup"><span data-stu-id="d8964-120">If you start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], then by default the wizard selects the connected server instance and enters the path to the selected project.</span></span> <span data-ttu-id="d8964-121">プロジェクトを別の場所に配置するようにこれらの値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d8964-121">You can change these values to deploy the project to a different location.</span></span>  
  
## <a name="review"></a><span data-ttu-id="d8964-122">確認</span><span class="sxs-lookup"><span data-stu-id="d8964-122">Review</span></span>  
 <span data-ttu-id="d8964-123">プロジェクトを配置する前に、選択した設定をウィザードで確認できます。</span><span class="sxs-lookup"><span data-stu-id="d8964-123">The wizard allows you to review the settings you have selected before deploying the project.</span></span> <span data-ttu-id="d8964-124">選択内容を変更するには、 **[戻る]** をクリックするか、左ペインでいずれかの手順をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8964-124">You can change your selections by clicking **Previous**, or by clicking any of the steps in the left pane.</span></span>  
  
## <a name="deployresults"></a><span data-ttu-id="d8964-125">配置/結果</span><span class="sxs-lookup"><span data-stu-id="d8964-125">Deploy/Results</span></span>  
 <span data-ttu-id="d8964-126">[**レビュー** ] ページの [**配置**] をクリックすると、プロジェクトが配置され、[**結果**] ページに各アクションの成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d8964-126">When you click **Deploy** from the **Review** page, the project is deployed and the **Results** page displays the success or failure of each action.</span></span> <span data-ttu-id="d8964-127">アクションが失敗した場合は、 **[結果]** 列の **[失敗]** をクリックすると、エラーの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d8964-127">If the action fails, click the **Failed** in the **Result** column to display an explanation of the error.</span></span> <span data-ttu-id="d8964-128">結果を XML ファイルに保存するには、[**レポートの保存...** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8964-128">Click **Save Report...** to save the results to an XML file.</span></span>  
  
 <span data-ttu-id="d8964-129">**[閉じる]** をクリックしてウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="d8964-129">Click **Close** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8964-130">参照</span><span class="sxs-lookup"><span data-stu-id="d8964-130">See Also</span></span>  
 <span data-ttu-id="d8964-131">[Integration Services サーバーへのプロジェクトの配置](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="d8964-131">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 [<span data-ttu-id="d8964-132">プロジェクトとパッケージの展開</span><span class="sxs-lookup"><span data-stu-id="d8964-132">Deployment of Projects and Packages</span></span>](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
