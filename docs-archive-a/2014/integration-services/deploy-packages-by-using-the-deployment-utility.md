---
title: 配置ユーティリティを使用してパッケージを配置する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], installing
- installing packages
- dependencies [Integration Services]
- deploying packages [Integration Services], installing
ms.assetid: eaf4b56e-2023-4d17-971c-703031da758c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a09ad307dc0215fca679cfb1ef5a37031f951caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718621"
---
# <a name="deploy-packages-by-using-the-deployment-utility"></a><span data-ttu-id="5b62e-102">配置ユーティリティを使用してパッケージを配置する</span><span class="sxs-lookup"><span data-stu-id="5b62e-102">Deploy Packages by Using the Deployment Utility</span></span>
  <span data-ttu-id="5b62e-103">配置ユーティリティを構築し、その配置ユーティリティが構築されたコンピューター以外のコンピューターに [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトのパッケージをインストールする場合は、最初に配置フォルダーを目的のコンピューターにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b62e-103">When you have built a deployment utility to install packages from an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different computer than the one on which the deployment utility was built, you must first copy the deployment folder to the destination computer.</span></span>  
  
 <span data-ttu-id="5b62e-104">配置フォルダーのパスは、配置ユーティリティを作成した [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの DeploymentOutputPath プロパティで指定されます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-104">The path of the deployment folder is specified in the DeploymentOutputPath property of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you created the deployment utility.</span></span> <span data-ttu-id="5b62e-105">既定のパスは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを基準とする bin\Deployment です。</span><span class="sxs-lookup"><span data-stu-id="5b62e-105">The default path is bin\Deployment, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="5b62e-106">詳細については、「 [配置ユーティリティを作成する](../../2014/integration-services/create-a-deployment-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b62e-106">For more information, see [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="5b62e-107">パッケージ インストール ウィザードを使用してパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="5b62e-107">You use the Package Installation Wizard to install the packages.</span></span> <span data-ttu-id="5b62e-108">ウィザードを起動し、配置フォルダーをサーバーにコピーしてから、配置ユーティリティ ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b62e-108">To launch the wizard, double-click the deployment utility file after you have copied the deployment folder to the server.</span></span> <span data-ttu-id="5b62e-109">このファイルは、\<project name>.SSISDeploymentManifest という名前で、インストール先のコンピューターの配置フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="5b62e-109">This file is named \<project name>.SSISDeploymentManifest, and can be found in the deployment folder on the destination computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b62e-110">配置するパッケージのバージョンによっては、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の異なるバージョンがサイド バイ サイドでインストールされている場合にエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b62e-110">Depending on the version of the package that you are deploying, you might encounter an error if you have different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installed side-by-side.</span></span> <span data-ttu-id="5b62e-111">このエラーが発生するのは、.SSISDeploymentManifest ファイル名拡張子が [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のすべてのバージョンで同じであるためです。</span><span class="sxs-lookup"><span data-stu-id="5b62e-111">This error can occur because the .SSISDeploymentManifest file name extension is the same for all versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="5b62e-112">このファイルをダブルクリックすると、最後にインストールしたバージョンの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のインストーラー (dtsinstall.exe) が呼び出されますが、配置ユーティリティ ファイルとはバージョンが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5b62e-112">Double-clicking the file calls the installer (dtsinstall.exe) for the most recently installed version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], which might not be the same version as the deployment utility file.</span></span> <span data-ttu-id="5b62e-113">この問題を回避するには、コマンド ラインから正しいバージョンの dtsinstall.exe を実行し、配置ユーティリティ ファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-113">To work around this problem, run the correct version of dtsinstall.exe from the command line, and provide the path of the deployment utility file.</span></span>  
  
 <span data-ttu-id="5b62e-114">パッケージ インストール ウィザードを使用すると、手順に従ってパッケージをファイル システムまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-114">The Package Installation Wizard guides you through the steps to install packages to the file system or to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5b62e-115">インストールは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-115">You can configure the installation in the following ways:</span></span>  
  
-   <span data-ttu-id="5b62e-116">パッケージをインストールする場所の種類と場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-116">Choosing the location type and location to install the packages.</span></span>  
  
-   <span data-ttu-id="5b62e-117">パッケージの依存関係をインストールする場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-117">Choosing location to install package dependencies.</span></span>  
  
-   <span data-ttu-id="5b62e-118">パッケージがターゲット サーバーにインストールされた後に、パッケージを検証します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-118">Validating the packages after they are installed on the target server.</span></span>  
  
 <span data-ttu-id="5b62e-119">パッケージのファイル ベースの依存関係は、必ずファイル システムにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-119">The file-based dependencies for packages are always installed to the file system.</span></span> <span data-ttu-id="5b62e-120">パッケージをファイル システムにインストールする場合、依存関係は、パッケージ用に指定したのと同じフォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-120">If you install a package to the file system, the dependencies are installed in the same folder as the one that you specify for the package.</span></span> <span data-ttu-id="5b62e-121">パッケージを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]にインストールする場合は、ファイル ベースの依存関係を格納するフォルダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-121">If you install a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify the folder in which to store the file-based dependencies.</span></span>  
  
 <span data-ttu-id="5b62e-122">パッケージに含まれている構成をインストール先のコンピューター用に合わせて変更したい場合は、ウィザードを使ってプロパティの値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-122">If the package includes configurations that you want to modify for use on the destination computer, you can update the values of the properties by using the wizard.</span></span>  
  
 <span data-ttu-id="5b62e-123">パッケージ インストール ウィザードを使ってパッケージをインストールする方法に加えて、 **dtutil** コマンド プロンプト ユーティリティを使ってパッケージをコピーおよび移動する方法があります。</span><span class="sxs-lookup"><span data-stu-id="5b62e-123">In addition to installing packages by using the Package Installation Wizard, you can copy and move packages by using the **dtutil** command prompt utility.</span></span> <span data-ttu-id="5b62e-124">詳細については、「 [dtutil ユーティリティ](dtutil-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b62e-124">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-deploy-packages-to-an-instance-of-sql-server"></a><span data-ttu-id="5b62e-125">SQL Server のインスタンスにパッケージを配置するには</span><span class="sxs-lookup"><span data-stu-id="5b62e-125">To deploy packages to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="5b62e-126">ターゲット コンピューターの配置フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-126">Open the deployment folder on the target computer.</span></span>  
  
2.  <span data-ttu-id="5b62e-127">\<project name>.SSISDeploymentManifest という名前のマニフェスト ファイルをダブルクリックして、パッケージ インストール ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-127">Double-click the manifest file, \<project name>.SSISDeploymentManifest, to start the Package Installation Wizard.</span></span>  
  
3.  <span data-ttu-id="5b62e-128">**[SSIS パッケージの配置]** ページで、 **[SQL Server に配置]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-128">On the **Deploy SSIS Packages** page, select the **SQL Server deployment** option.</span></span>  
  
4.  <span data-ttu-id="5b62e-129">必要に応じて、ターゲット サーバーにパッケージがインストールされた後で検証を行う場合は、 **[インストール後にパッケージを検証する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-129">Optionally, select **Validate packages after installation** to validate packages after they are installed on the target server.</span></span>  
  
5.  <span data-ttu-id="5b62e-130">**[インストール先の SQL Server の指定]** ページで、パッケージをインストールする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定し、認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-130">On the **Specify Target SQL Server** page, specify the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to install the packages to and select an authentication mode.</span></span> <span data-ttu-id="5b62e-131">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択する場合は、ユーザー名とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b62e-131">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and a password.</span></span>  
  
6.  <span data-ttu-id="5b62e-132">**[インストール フォルダーの選択]** ページで、パッケージの依存関係をインストールするファイル システムのフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b62e-132">On the **Select Installation Folder** page, specify the folder in the file system for the package dependencies that will be installed.</span></span>  
  
7.  <span data-ttu-id="5b62e-133">パッケージに構成が含まれる場合は、[パッケージの構成] ページで構成を編集して、 **[値]** の一覧の値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-133">If the package includes configurations, you can edit configurations by updating values in the **Value** list on the Configure Packages page.</span></span>  
  
8.  <span data-ttu-id="5b62e-134">インストール後にパッケージの検証を行うように選択した場合、配置したパッケージの検証結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b62e-134">If you elected to validate packages after installation, view the validation results of the deployed packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b62e-135">参照</span><span class="sxs-lookup"><span data-stu-id="5b62e-135">See Also</span></span>  
 [<span data-ttu-id="5b62e-136">SSIS&#41;&#40;パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="5b62e-136">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
