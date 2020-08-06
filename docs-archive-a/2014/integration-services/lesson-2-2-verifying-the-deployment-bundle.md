---
title: '手順 2: 配置バンドルの確認 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f452a87154175ac05a050761d8f12b6bfe61cd8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632573"
---
# <a name="step-2-verifying-the-deployment-bundle"></a><span data-ttu-id="2b2a5-102">手順 2:配置バンドルの確認</span><span class="sxs-lookup"><span data-stu-id="2b2a5-102">Step 2: Verifying the Deployment Bundle</span></span>
  <span data-ttu-id="2b2a5-103">レッスン 1 では、Deployment Tutorial プロジェクトを作成し、パッケージと補助ファイルをプロジェクトに追加しました。前のタスクでプロジェクトの配置ユーティリティを構築しました。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-103">In lesson 1, you created the Deployment Tutorial project and added packages and ancillary files to the project; in the previous task you built a deployment utility for the project.</span></span>  
  
 <span data-ttu-id="2b2a5-104">このタスクでは、配置バンドルの内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-104">In this task, you will verify the contents of the deployment bundle.</span></span> <span data-ttu-id="2b2a5-105">配置バンドルとは、目的のコンピューターにコピーしてパッケージのインストールに使用するフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-105">The deployment bundle is the folder that you will copy to the destination computer and use to install packages.</span></span> <span data-ttu-id="2b2a5-106">配置ユーティリティの場所として既定値の bin\Deployment を使用した場合は、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの Deployment Tutorial フォルダー内にある Bin\Deployment フォルダーが配置バンドルです。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-106">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Bin\Deployment folder within the Deployment Tutorial folder in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a><span data-ttu-id="2b2a5-107">配置バンドルの内容を確認するには</span><span class="sxs-lookup"><span data-stu-id="2b2a5-107">To verify the content of deployment bundle</span></span>  
  
1.  <span data-ttu-id="2b2a5-108">コンピューターで bin\Deployment フォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-108">Locate the bin\Deployment folder on your computer.</span></span>  
  
2.  <span data-ttu-id="2b2a5-109">次のファイルがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-109">Verify that the following files are present:</span></span>  
  
    -   <span data-ttu-id="2b2a5-110">DataTransfer.dtsx</span><span class="sxs-lookup"><span data-stu-id="2b2a5-110">DataTransfer.dtsx</span></span>  
  
    -   <span data-ttu-id="2b2a5-111">datatransferconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="2b2a5-111">datatransferconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="2b2a5-112">Deployment Tutorial.SSISDeploymentManifest</span><span class="sxs-lookup"><span data-stu-id="2b2a5-112">Deployment Tutorial.SSISDeploymentManifest</span></span>  
  
    -   <span data-ttu-id="2b2a5-113">LoadXMLData.dtsx</span><span class="sxs-lookup"><span data-stu-id="2b2a5-113">LoadXMLData.dtsx</span></span>  
  
    -   <span data-ttu-id="2b2a5-114">loadxmldataconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="2b2a5-114">loadxmldataconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="2b2a5-115">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="2b2a5-115">NewCustomers.txt</span></span>  
  
    -   <span data-ttu-id="2b2a5-116">orders.xml</span><span class="sxs-lookup"><span data-stu-id="2b2a5-116">orders.xml</span></span>  
  
    -   <span data-ttu-id="2b2a5-117">orders.xsd</span><span class="sxs-lookup"><span data-stu-id="2b2a5-117">orders.xsd</span></span>  
  
    -   <span data-ttu-id="2b2a5-118">Readme.txt</span><span class="sxs-lookup"><span data-stu-id="2b2a5-118">Readme.txt</span></span>  
  
3.  <span data-ttu-id="2b2a5-119">[Deployment Tutorial.SSISDeploymentManifest] を右クリックし、 **[ファイルを開くアプリケーションの選択]** をポイントして、 **[Internet Explorer]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-119">Right-click Deployment Tutorial.SSISDeploymentManifest, point **to Open With**, and then click **Internet Explorer**.</span></span> <span data-ttu-id="2b2a5-120">メモ帳などのテキスト エディターでもファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-120">You can also open the file in a text editor such as Notepad.</span></span> <span data-ttu-id="2b2a5-121">ファイルの XML コードは次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-121">The XML code of the file should be the following:</span></span>  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  <span data-ttu-id="2b2a5-122">属性の値 `AllowConfigurationChanges` が**true**であり、xml に2つのパッケージそれぞれに対応する要素、4つの `Package` `MiscellaneousFile` 非パッケージファイルそれぞれに対応する要素、および `ConfigurationFile` 2 つの xml 構成ファイルそれぞれに対応する要素が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-122">Verify that the value of the `AllowConfigurationChanges` attribute is **true** and the XML includes a `Package` element for each of the two packages, a `MiscellaneousFile` element for each of the four non-package files, and a `ConfigurationFile` element for each of the two XML configuration files.</span></span>  
  
5.  <span data-ttu-id="2b2a5-123">Internet Explorer またはテキスト エディターを終了します。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-123">Exit Internet Explorer or the text editor.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="2b2a5-124">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="2b2a5-124">Next Lesson</span></span>  
 [<span data-ttu-id="2b2a5-125">レッスン 3:パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="2b2a5-125">Lesson 3: Installing Packages</span></span>](../integration-services/lesson-3-install-ssis-package.md)  
  
<span data-ttu-id="2b2a5-126">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="2b2a5-126">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2b2a5-127">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2b2a5-128">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="2b2a5-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2b2a5-129">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="2b2a5-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
