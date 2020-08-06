---
title: SQL Server Data Tools | でパッケージを実行します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31ca2390ef6bb04b63e4de9978193aed8884da36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713241"
---
# <a name="run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="e9e91-102">SQL Server Data Tools でのパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="e9e91-102">Run a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="e9e91-103">一般に、パッケージの開発、デバッグ、およびテストの段階では、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9e91-103">You typically run packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] during the development, debugging, and testing of packages.</span></span> <span data-ttu-id="e9e91-104">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーからパッケージを実行すると、パッケージは常に即座に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e9e91-104">When you run a package from [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the package always runs immediately.</span></span>  
  
 <span data-ttu-id="e9e91-105">パッケージの実行中は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[進行状況]** タブにパッケージの実行の進行状況が表示されます。パッケージおよびそのタスクおよびコンテナーの開始時間と終了時間に加え、パッケージ内で失敗したタスクまたはコンテナーに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9e91-105">While a package is running, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer displays the progress of package execution on the **Progress** tab. You can view the start and finish time of the package and its tasks and containers, in addition to information about any tasks or containers in the package that failed.</span></span> <span data-ttu-id="e9e91-106">パッケージの実行が完了した後は、 **[実行結果]** タブで実行時情報を確認できます。詳細については、 [「制御フローのデバッグ」](control-flow/control-flow.md)の「進行状況レポート」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9e91-106">After the package finishes running, the run-time information remains available on the **Execution Results** tab. For more information, see the section, "Progress Reporting," in the topic, [Debugging Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="e9e91-107">**デザイン時配置**。</span><span class="sxs-lookup"><span data-stu-id="e9e91-107">**Design-time deployment**.</span></span> <span data-ttu-id="e9e91-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]でパッケージを実行すると、そのパッケージが構築されフォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="e9e91-108">When you run a package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the package is built and then deployed to a folder.</span></span> <span data-ttu-id="e9e91-109">パッケージを実行する前に、パッケージを配置するフォルダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e9e91-109">Before you run the package, you can specify the folder to which the package is deployed.</span></span> <span data-ttu-id="e9e91-110">フォルダーを指定しない場合、既定で **bin** フォルダーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9e91-110">If you do not specify a folder, the **bin** folder is used by default.</span></span> <span data-ttu-id="e9e91-111">こうした配置方法は、デザイン時配置と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e9e91-111">This type of deployment is called design-time deployment.</span></span>  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="e9e91-112">SQL Server Data Tools でパッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="e9e91-112">To run a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="e9e91-113">ソリューションに複数のプロジェクトが含まれている場合は、ソリューション エクスプローラーで、パッケージを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを右クリックし、 **[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ プロジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="e9e91-113">In Solution Explorer, if your solution contains multiple projects, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package, and then click **Set as StartUp Object** to set the startup project.</span></span>  
  
2.  <span data-ttu-id="e9e91-114">プロジェクトに複数のパッケージが含まれている場合は、ソリューション エクスプローラーで、パッケージの 1 つを右クリックし、 **[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ パッケージを設定します。</span><span class="sxs-lookup"><span data-stu-id="e9e91-114">In Solution Explorer, if your project contains multiple packages, right-click a package, and then click **Set as StartUp Object** to set the startup package.</span></span>  
  
3.  <span data-ttu-id="e9e91-115">パッケージを実行するには、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e9e91-115">To run a package, use one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="e9e91-116">実行するパッケージを開き、メニュー バーの **[デバッグ開始]** をクリックするか、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9e91-116">Open the package that you want to run and then click **Start Debugging** on the menu bar, or press F5.</span></span> <span data-ttu-id="e9e91-117">パッケージの実行が完了したら、Shift キーを押しながら F5 キーを押して、デザイン モードに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9e91-117">After the package finishes running, press Shift+F5 to return to design mode.</span></span>  
  
    -   <span data-ttu-id="e9e91-118">ソリューション エクスプローラーでパッケージを右クリックし、 **[パッケージの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9e91-118">In Solution Explorer, right-click the package, and then click **Execute Package**.</span></span>  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a><span data-ttu-id="e9e91-119">デザイン時配置用に別のフォルダーを指定するには</span><span class="sxs-lookup"><span data-stu-id="e9e91-119">To specify a different folder for design-time deployment</span></span>  
  
1.  <span data-ttu-id="e9e91-120">ソリューション エクスプローラーで、実行するパッケージが含まれる [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクト フォルダーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9e91-120">In Solution Explorer, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project folder that contains the package you want to run, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e9e91-121">**[\<project name> プロパティ ページ]** ダイアログ ボックスで、 **[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9e91-121">In the **\<project name> Property Pages** dialog box, click **Build**.</span></span>  
  
3.  <span data-ttu-id="e9e91-122">OutputPath プロパティの値を更新して、デザイン時配置用に使用するフォルダーを指定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9e91-122">Update the value in the OutputPath property to specify the folder you want to use for design-time deployment, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e91-123">参照</span><span class="sxs-lookup"><span data-stu-id="e9e91-123">See Also</span></span>  
 <span data-ttu-id="e9e91-124">[プロジェクトとパッケージの実行](packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e9e91-124">[Execution of Projects and Packages](packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="e9e91-125">Integration Services &#40;SSIS&#41; パッケージ</span><span class="sxs-lookup"><span data-stu-id="e9e91-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
