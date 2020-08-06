---
title: '手順 1: 配置ユーティリティの構築 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3d32dcbf4bfcf9758dfe58803b75094d1807aa90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641075"
---
# <a name="step-1-building-the-deployment-utility"></a><span data-ttu-id="fd231-102">手順 1:配置ユーティリティの構築</span><span class="sxs-lookup"><span data-stu-id="fd231-102">Step 1: Building the Deployment Utility</span></span>
  <span data-ttu-id="fd231-103">ここでは、Deployment Tutorial プロジェクト用の配置ユーティリティを構成し、構築します。</span><span class="sxs-lookup"><span data-stu-id="fd231-103">In this task, you will configure and build a deployment utility for the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="fd231-104">配置ユーティリティを構築する前に、Deployment Tutorial プロジェクトのプロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd231-104">Before you can build the deployment utility, you must modify the properties of the Deployment Tutorial project.</span></span> <span data-ttu-id="fd231-105">これらのプロパティを構成するには、 **[Deployment Tutorial プロパティ ページ]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd231-105">You will use the **Deployment Tutorial Property Pages** dialog box to configure these properties.</span></span> <span data-ttu-id="fd231-106">このダイアログ ボックスでは、配置中に構成を更新する機能を有効にし、構築プロセスによる配置ユーティリティの生成を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd231-106">In this dialog box, you must enable the ability to update configurations during deployment and specify that the build process generates a deployment utility.</span></span> <span data-ttu-id="fd231-107">プロパティを設定したら、プロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="fd231-107">After you set the properties, you will build the project.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="fd231-108">には、パッケージのデバッグに使用できる一連のウィンドウが用意されています。</span><span class="sxs-lookup"><span data-stu-id="fd231-108">provides a set of windows that you can use to debug packages.</span></span> <span data-ttu-id="fd231-109">これらのウィンドウでは、エラー、警告、および情報メッセージの表示、実行時のパッケージ状態の追跡、または構築プロセスの進行状況と結果の表示ができます。</span><span class="sxs-lookup"><span data-stu-id="fd231-109">You can view error, warning, and information messages, track about the status of packages at run time, or view the progress and results of build processes.</span></span> <span data-ttu-id="fd231-110">このレッスンでは、配置ユーティリティの構築の進行状況と結果を出力ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="fd231-110">For this lesson, you will use the Output window to view the progress and results of building the deployment utility.</span></span>  
  
### <a name="to-set-the-deployment-utility-properties"></a><span data-ttu-id="fd231-111">配置ユーティリティのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="fd231-111">To set the deployment utility properties</span></span>  
  
1.  <span data-ttu-id="fd231-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントして、 **[Business Intelligence Development Studio]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-112">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="fd231-113">**[ファイル]** メニューの **[開く]** をクリックし、 **[プロジェクト/ソリューション]** をクリックします。次に、 **[Deployment Tutorial]** フォルダーをクリックして **[開く]** をクリックし、 **Deployment Tutorial.sln**をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-113">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="fd231-114">ソリューション エクスプローラーで [Deployment Tutorial] を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-114">In Solution Explorer, right-click Deployment Tutorial and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="fd231-115">**[Deployment Tutorial プロパティ ページ]** ダイアログ ボックスで、[構成プロパティ] を展開し、[配置ユーティリティ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-115">In the **Deployment Tutorial Property Pages** dialog box, expand Configuration Properties, and click Deployment Utility.</span></span>  
  
5.  <span data-ttu-id="fd231-116">[**配置チュートリアルプロパティページ**] ダイアログボックスの右ペインで、 `AllowConfigurationChanges` がに設定されていることを確認し、 `true` `CreateDeploymentUtility` をに設定し、 `true` 必要に応じての既定値を更新し `DeploymentOutputPath` ます。</span><span class="sxs-lookup"><span data-stu-id="fd231-116">In the right pane of the **Deployment Tutorial Property Pages** dialog box, verify that `AllowConfigurationChanges` is set to `true`, set `CreateDeploymentUtility` to `true`, and optionally update the default value of `DeploymentOutputPath`.</span></span>  
  
6.  <span data-ttu-id="fd231-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-117">Click **OK**.</span></span>  
  
### <a name="to-build-the-deployment-utility"></a><span data-ttu-id="fd231-118">配置ユーティリティを構築するには</span><span class="sxs-lookup"><span data-stu-id="fd231-118">To build the deployment utility</span></span>  
  
1.  <span data-ttu-id="fd231-119">ソリューション エクスプローラーで、 **[Deployment Tutorial]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-119">In Solution Explorer, click **Deployment Tutorial**.</span></span>  
  
2.  <span data-ttu-id="fd231-120">**[表示]** メニューの **[出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-120">On the **View** menu, click **Output**.</span></span> <span data-ttu-id="fd231-121">既定では、出力ウィンドウは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の左下隅に配置されます。</span><span class="sxs-lookup"><span data-stu-id="fd231-121">By default, the Output window is located in the bottom left corner of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="fd231-122">**[ビルド]** メニューの **[Deployment Tutorial のビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-122">On the **Build** menu, click **Build Deployment Tutorial**.</span></span>  
  
4.  <span data-ttu-id="fd231-123">出力ウィンドウに、次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd231-123">In the Output window, verify the following information:</span></span>  
  
     <span data-ttu-id="fd231-124">ビルド開始:  SQL Integration Services プロジェクト: インクリメンタル...</span><span class="sxs-lookup"><span data-stu-id="fd231-124">Build started: SQL Integration Services project: Incremental ...</span></span>  
  
     <span data-ttu-id="fd231-125">配置ユーティリティを作成しています</span><span class="sxs-lookup"><span data-stu-id="fd231-125">Creating deployment utility...</span></span>  
  
     <span data-ttu-id="fd231-126">配置ユーティリティが作成されました。</span><span class="sxs-lookup"><span data-stu-id="fd231-126">Deployment Utility created.</span></span>  
  
     <span data-ttu-id="fd231-127">ビルドの完了 -- エラー 0 個、警告 0 個</span><span class="sxs-lookup"><span data-stu-id="fd231-127">Build complete -- 0 errors, 0 warnings</span></span>  
  
     <span data-ttu-id="fd231-128">========== ビルド: 0 正常終了、0 失敗、1 更新、0 スキップ ==========</span><span class="sxs-lookup"><span data-stu-id="fd231-128">========== Build: 0 succeeded, 0 failed, 1 up-to-date, 0 skipped ==========</span></span>  
  
5.  <span data-ttu-id="fd231-129">**[ファイル]** メニューの **[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-129">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="fd231-130">Deployment Tutorial アイテムへの変更の保存を指示するメッセージが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd231-130">If prompted to save changes to Deployment Tutorial items, click **Yes**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fd231-131">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="fd231-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fd231-132">手順 2: 配置バンドルの確認</span><span class="sxs-lookup"><span data-stu-id="fd231-132">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
<span data-ttu-id="fd231-133">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="fd231-133">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="fd231-134">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd231-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="fd231-135">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="fd231-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="fd231-136">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="fd231-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd231-137">参照</span><span class="sxs-lookup"><span data-stu-id="fd231-137">See Also</span></span>  
 [<span data-ttu-id="fd231-138">配置ユーティリティを作成する</span><span class="sxs-lookup"><span data-stu-id="fd231-138">Create a Deployment Utility</span></span>](../../2014/integration-services/create-a-deployment-utility.md)  
  
  
