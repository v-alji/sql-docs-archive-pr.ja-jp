---
title: '手順 1: 配置バンドルのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 326a85a4d04fc22382457b4e2e919f81096ce989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645179"
---
# <a name="step-1-copying-the-deployment-bundle"></a><span data-ttu-id="312df-102">手順 1:配置バンドルのコピー</span><span class="sxs-lookup"><span data-stu-id="312df-102">Step 1: Copying the Deployment Bundle</span></span>
  <span data-ttu-id="312df-103">このタスクでは、配置先コンピューターに配置バンドルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="312df-103">In this task, you will copy the deployment bundle to the destination computer.</span></span>  
  
 <span data-ttu-id="312df-104">配置先コンピューターに配置バンドルをコピーするには、まず配置先コンピューターにパブリック共有を作成し、ドライブをパブリック共有にマッピングして、配置バンドルを共有にコピーするのが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="312df-104">The easiest way to copy the deployment bundle to the destination computer is to first create a public share on the destination computer, map a drive to the public share, and then copy the deployment bundle to the share.</span></span> <span data-ttu-id="312df-105">パブリック フォルダーを作成して構成する方法や、ドライブのマッピング方法がわからない場合は、Windows のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="312df-105">If you do not know how to create and configure public folders or map drives, see the Windows documentation.</span></span>  
  
### <a name="to-copy-the-deployment-bundle"></a><span data-ttu-id="312df-106">配置バンドルをコピーするには</span><span class="sxs-lookup"><span data-stu-id="312df-106">To copy the deployment bundle</span></span>  
  
1.  <span data-ttu-id="312df-107">コンピューターで配置バンドルを探します。</span><span class="sxs-lookup"><span data-stu-id="312df-107">Locate the deployment bundle on your computer.</span></span>  
  
     <span data-ttu-id="312df-108">既定の場所を使用した場合、配置バンドルは Deployment Tutorial フォルダーの Bin\Deployment フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="312df-108">If you used the default location, the deployment bundle is the Bin\Deployment folder within the Deployment Tutorial folder.</span></span>  
  
2.  <span data-ttu-id="312df-109">Deployment フォルダーを右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="312df-109">Right-click the Deployment folder and click **Copy**.</span></span>  
  
3.  <span data-ttu-id="312df-110">ターゲット コンピューターで、フォルダーをコピーするパブリック共有を探し、 **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="312df-110">Locate the public share to which you want to copy the folder on the target computer and click **Paste**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="312df-111">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="312df-111">Next Task in Lesson</span></span>  
 [<span data-ttu-id="312df-112">手順 2: パッケージ インストール ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="312df-112">Step 2: Running the Package Installation Wizard</span></span>](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
<span data-ttu-id="312df-113">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="312df-113">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="312df-114">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="312df-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="312df-115">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="312df-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="312df-116">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="312df-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
