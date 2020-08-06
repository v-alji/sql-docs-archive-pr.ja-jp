---
title: 'レッスン 2: 配置バンドルの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 927bcd393e4b54e92971c197d93dcc1e2804dcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642867"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a><span data-ttu-id="ca13d-102">レッスン 2: 配置バンドルの作成</span><span class="sxs-lookup"><span data-stu-id="ca13d-102">Lesson 2: Creating the Deployment Bundle</span></span>
  <span data-ttu-id="ca13d-103">[「レッスン 1: 配置バンドルを作成する準備」](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)では、Deployment Tutorial という名前の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成し、パッケージとサポート ファイルをプロジェクトに追加して、パッケージに構成を実装しました。</span><span class="sxs-lookup"><span data-stu-id="ca13d-103">In [Lesson 1: Preparing to Create the Deployment Bundle](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md), you created the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project named Deployment Tutorial, added the packages and supporting files to the project, and implemented configurations in packages.</span></span>  
  
 <span data-ttu-id="ca13d-104">このレッスンでは、配置バンドルを作成します。配置バンドルとは、他のコンピューターにパッケージをインストールするために必要なアイテムが含まれているフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="ca13d-104">In this lesson, you will create the deployment bundle, which is a folder that contains the items that you need to install packages on another computer.</span></span> <span data-ttu-id="ca13d-105">配置バンドルには、Deployment Tutorial プロジェクトの配置マニフェスト、パッケージのコピー、サポート ファイルのコピーを含めます。</span><span class="sxs-lookup"><span data-stu-id="ca13d-105">The deployment bundle will include a deployment manifest, copies of the packages, and copies of the supporting files from the Deployment Tutorial project.</span></span> <span data-ttu-id="ca13d-106">配置マニフェストとは、配置バンドルに含まれているパッケージ、その他のファイル、および構成の一覧です。</span><span class="sxs-lookup"><span data-stu-id="ca13d-106">The deployment manifest lists the packages, miscellaneous files, and configurations in the deployment bundle.</span></span>  
  
 <span data-ttu-id="ca13d-107">また、配置バンドルに含まれているファイルの一覧を確認し、マニフェストの内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="ca13d-107">You will also verify the file list in the deployment bundle and examine the contents of the manifest.</span></span>  
  
 <span data-ttu-id="ca13d-108">**このレッスンの推定所要時間:** 30 分</span><span class="sxs-lookup"><span data-stu-id="ca13d-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="ca13d-109">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="ca13d-109">Lesson Tasks</span></span>  
 <span data-ttu-id="ca13d-110">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ca13d-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="ca13d-111">手順 1: 配置ユーティリティの構築</span><span class="sxs-lookup"><span data-stu-id="ca13d-111">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [<span data-ttu-id="ca13d-112">手順 2: 配置バンドルの確認</span><span class="sxs-lookup"><span data-stu-id="ca13d-112">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="ca13d-113">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="ca13d-113">Start the Lesson</span></span>  
 [<span data-ttu-id="ca13d-114">手順 1: 配置ユーティリティの構築</span><span class="sxs-lookup"><span data-stu-id="ca13d-114">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
<span data-ttu-id="ca13d-115">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="ca13d-115">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ca13d-116">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca13d-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ca13d-117">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="ca13d-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ca13d-118">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="ca13d-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
