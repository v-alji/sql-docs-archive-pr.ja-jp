---
title: 'レッスン 3: パッケージのインストール |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8b58cee7bd8e16cd0ca2e726dc8e5eff2cfec5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640141"
---
# <a name="lesson-3-installing-packages"></a><span data-ttu-id="c902b-102">レッスン 3:パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="c902b-102">Lesson 3: Installing Packages</span></span>
  <span data-ttu-id="c902b-103">「[レッスン 2: 配置バンドルの作成](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)」では、配置ユーティリティを構築し、別のコンピューターにパッケージをインストールする必要がある項目を含む配置バンドルを作成しました。</span><span class="sxs-lookup"><span data-stu-id="c902b-103">In [Lesson 2: Creating the Deployment Bundle](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md), you built a deployment utility and created the deployment bundle that contains the items that you must install packages on another computer.</span></span> <span data-ttu-id="c902b-104">また、配置バンドルのファイル リストを確認し、配置ユーティリティの構築時に作成されたマニフェスト ファイルの内容も調べました。</span><span class="sxs-lookup"><span data-stu-id="c902b-104">You also verified the file list in the deployment bundle and examined the contents of the manifest file that was created when you built the deployment utility.</span></span>  
  
 <span data-ttu-id="c902b-105">このレッスンでは、配置バンドルを目的のコンピューターにコピーし、パッケージ インストール ウィザードを実行して、そのコンピューターにパッケージ、パッケージの依存関係、および補助ファイルをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c902b-105">In this lesson, you will copy the deployment bundle to the destination computer and then run the Package Installation Wizard to install the packages, package dependencies, and ancillary files on that computer.</span></span> <span data-ttu-id="c902b-106">パッケージは**msdb**データベースにインストールされ、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] その他の項目はファイルシステムにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c902b-106">The packages will be installed in the **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database and the other items will be installed in the file system.</span></span> <span data-ttu-id="c902b-107">パッケージのインストールが完了すると、パッケージ実行ユーティリティを使用して [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] からパッケージを実行し、配置をテストします。</span><span class="sxs-lookup"><span data-stu-id="c902b-107">After you complete the package installation, you will test the deployment by running the packages from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] using the Execute Package Utility.</span></span>  
  
 <span data-ttu-id="c902b-108">**このレッスンの推定所要時間:** 30 分</span><span class="sxs-lookup"><span data-stu-id="c902b-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="c902b-109">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="c902b-109">Lesson Tasks</span></span>  
 <span data-ttu-id="c902b-110">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c902b-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="c902b-111">手順 1:配置バンドルのコピー</span><span class="sxs-lookup"><span data-stu-id="c902b-111">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [<span data-ttu-id="c902b-112">手順 2:パッケージ インストール ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="c902b-112">Step 2: Running the Package Installation Wizard</span></span>](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [<span data-ttu-id="c902b-113">手順 3:配置したパッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="c902b-113">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="c902b-114">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="c902b-114">Start the Lesson</span></span>  
 [<span data-ttu-id="c902b-115">手順 1:配置バンドルのコピー</span><span class="sxs-lookup"><span data-stu-id="c902b-115">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
<span data-ttu-id="c902b-116">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="c902b-116">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c902b-117">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c902b-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c902b-118">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="c902b-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c902b-119">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="c902b-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
