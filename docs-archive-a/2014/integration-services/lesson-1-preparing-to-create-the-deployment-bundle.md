---
title: 'レッスン 1: 配置バンドルを作成する準備 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0deda2a81ddd86d4e40c1c546232b8056264508a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641081"
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a><span data-ttu-id="fdf99-102">レッスン 1: 配置バンドルを作成する準備</span><span class="sxs-lookup"><span data-stu-id="fdf99-102">Lesson 1: Preparing to Create the Deployment Bundle</span></span>
  <span data-ttu-id="fdf99-103">このレッスンでは、チュートリアルをサポートする作業フォルダーと環境変数を作成し、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成します。さらに、いくつかのパッケージとそのサポート ファイルをプロジェクトに追加し、パッケージに構成を実装します。</span><span class="sxs-lookup"><span data-stu-id="fdf99-103">In this lesson, you will create the working folders and environment variables that support the tutorial, create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add several packages and their supporting files to the project, and implement configurations in packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="fdf99-104">では、プロジェクトの基本構造の上にパッケージが配置されます。したがって、配置バンドルを作成する最初のステップとして、すべてのパッケージおよびパッケージの依存関係を 1 つの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトにまとめる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdf99-104">deploys packages on a project basis; therefore, as the first step in creating the deployment bundle, you must collect all the packages and package dependencies into one [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="fdf99-105">配置するパッケージに他の情報を含めると役立つことがよくあります。たとえば、このグループのパッケージに関する基本的な情報を記述した Readme ファイルもプロジェクトに追加する予定です。</span><span class="sxs-lookup"><span data-stu-id="fdf99-105">Frequently it is useful to include other information with the deployed packages: for example you will also add to the project a Readme file that provides basic documentation for this group of packages.</span></span>  
  
 <span data-ttu-id="fdf99-106">パッケージとファイルを追加した後、まだ構成を使用していないパッケージに構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="fdf99-106">After you have added the packages and files, you will add configurations to packages that do not already use configurations.</span></span> <span data-ttu-id="fdf99-107">構成を実装すると、パッケージとパッケージ オブジェクトのプロパティが実行時に更新されます。</span><span class="sxs-lookup"><span data-stu-id="fdf99-107">The configurations update properties of packages and package objects at run time.</span></span> <span data-ttu-id="fdf99-108">後のレッスンで、パッケージの配置時にこれらの構成の値を変更して、配置先の環境でパッケージがサポートされるようにします。</span><span class="sxs-lookup"><span data-stu-id="fdf99-108">In a later lesson, you will modify the values of these configurations during package deployment to support the packages in the deployed-to environment.</span></span>  
  
 <span data-ttu-id="fdf99-109">構成を追加した後、配置時に解決する必要がある問題をより的確に把握するために、ETL パッケージを作成するための [!INCLUDE[ssIS](../includes/ssis-md.md)] のグラフィカルなツールである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] デザイナーでパッケージを開き、パッケージおよびパッケージの要素のプロパティと、パッケージの構成を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fdf99-109">After you have added the configurations, you should open the packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] graphical tool for building ETL packages, and examine the properties of packages and package elements as well as the package configurations to better understand the issues that the deployment needs to address.</span></span> <span data-ttu-id="fdf99-110">たとえば、パッケージの 1 つを使用してテキスト ファイルからデータを抽出するので、配置したパッケージが正常に実行されるには、データ ファイルの場所を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdf99-110">For example, one of the packages extracts data from text files, so the location of the data files must be updated before the deployed packages will run successfully.</span></span>  
  
 <span data-ttu-id="fdf99-111">**このレッスンの推定所要時間:** 1 時間</span><span class="sxs-lookup"><span data-stu-id="fdf99-111">**Estimated time to complete this lesson:** 1 hour</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="fdf99-112">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="fdf99-112">Lesson Tasks</span></span>  
 <span data-ttu-id="fdf99-113">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fdf99-113">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="fdf99-114">手順 1: 作業フォルダーと環境変数の作成</span><span class="sxs-lookup"><span data-stu-id="fdf99-114">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [<span data-ttu-id="fdf99-115">手順 2: 配置プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="fdf99-115">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [<span data-ttu-id="fdf99-116">手順 3: パッケージとその他のファイルの追加</span><span class="sxs-lookup"><span data-stu-id="fdf99-116">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [<span data-ttu-id="fdf99-117">手順 4: パッケージ構成の追加</span><span class="sxs-lookup"><span data-stu-id="fdf99-117">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [<span data-ttu-id="fdf99-118">手順 5: 更新したパッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="fdf99-118">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="fdf99-119">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="fdf99-119">Start the Lesson</span></span>  
 [<span data-ttu-id="fdf99-120">手順 1: 作業フォルダーと環境変数の作成</span><span class="sxs-lookup"><span data-stu-id="fdf99-120">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
<span data-ttu-id="fdf99-121">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="fdf99-121">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="fdf99-122">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdf99-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="fdf99-123">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="fdf99-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="fdf99-124">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="fdf99-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
