---
title: '手順 5: 更新したパッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a075af2e030c8257d01abf5eba7d330b1cc8efe7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641090"
---
# <a name="step-5-testing-the-updated-packages"></a><span data-ttu-id="84302-102">手順 5:更新したパッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="84302-102">Step 5: Testing the Updated Packages</span></span>
  <span data-ttu-id="84302-103">次のレッスンでは、目的のコンピューターにチュートリアル パッケージをインストールするときに使用する配置バンドルを作成しますが、その前にパッケージをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="84302-103">Before you go on to the next lesson, in which you will create the deployment bundle to use to install the tutorial packages on the destination computer, you should test the packages.</span></span> <span data-ttu-id="84302-104">この作業では、Deployment Tutorial プロジェクトに追加して構成を拡張したパッケージ DataTransfer.dtsx および LoadXMLData を実行します。</span><span class="sxs-lookup"><span data-stu-id="84302-104">In this task, you will run the packages, DataTransfer.dtsx and LoadXMLData, that you added to the Deployment Tutorial project and then extended with configurations.</span></span>  
  
 <span data-ttu-id="84302-105">パッケージを実行すると、パッケージ内の各実行ファイルが完了したときに緑色になります。</span><span class="sxs-lookup"><span data-stu-id="84302-105">When the packages run, each executable in the package becomes a green color as it completes successfully.</span></span> <span data-ttu-id="84302-106">実行ファイルのすべてが緑色になると、パッケージの実行に成功したことを表します。</span><span class="sxs-lookup"><span data-stu-id="84302-106">When all executables are green, the package has completed successfully.</span></span> <span data-ttu-id="84302-107">**[進行状況]** タブでパッケージ実行の進み具合を見ることもできます。</span><span class="sxs-lookup"><span data-stu-id="84302-107">You can also view the package execution progress on the **Progress** tab.</span></span>  
  
 <span data-ttu-id="84302-108">パッケージの実行に失敗した場合は、次のレッスンに進む前に修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84302-108">If the packages do not run successfully, you must fix them before you go on to the next lesson.</span></span>  
  
### <a name="to-run-the-datatransfer-package"></a><span data-ttu-id="84302-109">DataTransfer パッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="84302-109">To run the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="84302-110">ソリューション エクスプローラーで [DataTransfer.dtsx] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84302-110">In Solution Explorer, click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="84302-111">**[デバッグ]** メニューの **[デバッグ開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84302-111">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="84302-112">パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84302-112">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-run-the-loadxmldata-package"></a><span data-ttu-id="84302-113">LoadXMLData パッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="84302-113">To run the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="84302-114">ソリューション エクスプローラーで [LoadXMLData.dtsx] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84302-114">In Solution Explorer, click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="84302-115">**[デバッグ]** メニューの **[デバッグ開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84302-115">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="84302-116">パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84302-116">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="84302-117">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="84302-117">Next Lesson</span></span>  
 [<span data-ttu-id="84302-118">レッスン 2: 配置バンドルの作成</span><span class="sxs-lookup"><span data-stu-id="84302-118">Lesson 2: Creating the Deployment Bundle</span></span>](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
<span data-ttu-id="84302-119">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="84302-119">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="84302-120">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="84302-120">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="84302-121">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="84302-121">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="84302-122">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="84302-122">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
