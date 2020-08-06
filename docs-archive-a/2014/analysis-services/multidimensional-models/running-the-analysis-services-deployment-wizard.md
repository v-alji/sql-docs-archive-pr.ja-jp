---
title: Analysis Services 配置ウィザードの実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6207e3e7981f52ca158f50515166d237e0524ea7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743545"
---
# <a name="running-the-analysis-services-deployment-wizard"></a><span data-ttu-id="4a3db-102">Analysis Services 配置ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="4a3db-102">Running the Analysis Services Deployment Wizard</span></span>
  <span data-ttu-id="4a3db-103">配置ウィザードを使用してプロジェクトを配置する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 次の方法でウィザードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-103">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard to deploy a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can run the wizard in the following ways:</span></span>  
  
-   <span data-ttu-id="4a3db-104">**対話的に実行**[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話的に実行すると、ユーザーの入力によって対話的に変更された入力ファイルに基づいて、XML 配置スクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-104">**Interactively** When run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML deployment script based on the input files, as modified interactively by user input.</span></span> <span data-ttu-id="4a3db-105">ユーザーによる変更は、配置スクリプトのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-105">The wizard applies any user modifications only to the deployment script.</span></span> <span data-ttu-id="4a3db-106">入力ファイルが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="4a3db-106">The wizard does not modify the input files.</span></span> <span data-ttu-id="4a3db-107">入力ファイルの詳細については、「 [配置スクリプトを作成するための入力ファイルについて](deployment-script-files-input-used-to-create-deployment-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a3db-107">For more information about the input files, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
-   <span data-ttu-id="4a3db-108">**コマンドプロンプトから**コマンドプロンプトで実行すると、配置ウィザードによって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ウィザードの実行に使用するスイッチに基づいて XML for Analysis (XMLA) 配置スクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-108">**From the command prompt** When run at the command prompt, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML for Analysis (XMLA) deployment script based upon the switches that you use to run the wizard.</span></span> <span data-ttu-id="4a3db-109">ウィザードでは、ユーザーの入力を求めてその入力に基づいて入力ファイルを変更するか、入力ファイルをそのまま使用して自動的に配置を実行するか、後で使用可能な配置スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-109">The wizard may any one of the following: prompt you for user input and modify input files based on that input; run a silent, unattended deployment using the input files as is; or create a deployment script that you can use later.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="4a3db-110">Analysis Services 配置ウィザードの対話的な実行</span><span class="sxs-lookup"><span data-stu-id="4a3db-110">Running the Analysis Services Deployment Wizard Interactively</span></span>  
 <span data-ttu-id="4a3db-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話的に実行すると、入力ファイルから値が読み取られ、その情報が提示されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-111">When you run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the values from the input files and presents this information to you.</span></span> <span data-ttu-id="4a3db-112">これらの入力値 (配置先、構成設定、配置オプション、接続文字列パスワードなど) を変更するか、そのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-112">You can modify these input values-such as deployment destination, configuration settings, deployment options, and connection string passwords-or leave them as is.</span></span> <span data-ttu-id="4a3db-113">入力値を変更した場合、ウィザードではこれらの変更値を使用して XMLA 配置スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-113">If you change any input values, the wizard uses these changes when generating the XMLA deployment script.</span></span> <span data-ttu-id="4a3db-114">ただし、入力ファイルの値は変更されません。</span><span class="sxs-lookup"><span data-stu-id="4a3db-114">However, the wizard does not make any changes to the values in the input file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a3db-115">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードで入力値が変更されるようにするには、コマンド プロンプトでウィザードを応答ファイル モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-115">If you want to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard modify the input values, run the wizard at the command prompt and set the wizard to run in answer file mode.</span></span>  
  
 <span data-ttu-id="4a3db-116">入力値を確認し、必要な変更を行うと、ウィザードによって XMLA 配置スクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-116">After you review the input values and make any wanted changes, the wizard generates the XMLA deployment script.</span></span> <span data-ttu-id="4a3db-117">この配置スクリプトは配置先サーバーで直ちに実行することも、後で使用するために保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-117">You can run this deployment script immediately on the destination server or save the script for later use.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="4a3db-118">Analysis Services 配置ウィザードを対話的に実行するには</span><span class="sxs-lookup"><span data-stu-id="4a3db-118">To run the Analysis Services Deployment Wizard interactively</span></span>  
  
-   <span data-ttu-id="4a3db-119">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**、 **[Analysis Services]** の順にポイントして、 **[配置ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a3db-119">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Analysis Services**, and then click **Deployment Wizard**.</span></span>  
  
     <span data-ttu-id="4a3db-120">または</span><span class="sxs-lookup"><span data-stu-id="4a3db-120">-or-</span></span>  
  
-   <span data-ttu-id="4a3db-121">プロジェクトの**Projects**フォルダーで、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *\<project name>* . asdatabase ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a3db-121">In the **Projects** folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, double-click the *\<project name>*.asdatabase file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a3db-122">Asdatabase ファイルが見つからない場合は *\<project name>* 、Search を使用して \*. asdatabase を指定します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-122">If you cannot find the *\<project name>*.asdatabase file, try using Search and specify \*.asdatabase.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="4a3db-123">コマンド プロンプトでの Analysis Services 配置ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="4a3db-123">Running the Analysis Services Deployment Wizard at the Command Prompt</span></span>  
 <span data-ttu-id="4a3db-124">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードは、コマンド プロンプトで実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-124">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard can also be run at the command prompt.</span></span> <span data-ttu-id="4a3db-125">コマンド プロンプトを使用する場合は、.asdatabase ファイルへの完全パスを指定し、次のいずれかのモードでウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-125">When you run the wizard at the command prompt, you provide the full path to the .asdatabase file and  run the wizard in one of the following modes:</span></span>  
  
 <span data-ttu-id="4a3db-126">**応答ファイル モード**</span><span class="sxs-lookup"><span data-stu-id="4a3db-126">**Answer file mode**</span></span>  
 <span data-ttu-id="4a3db-127">応答ファイル モードでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でビルドされたときに生成された入力ファイルを対話的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-127">In answer file mode, the wizard lets you interactively modify the input files that were originally generated when the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project was built in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="4a3db-128">これらの変更された入力ファイルは XMLA 配置スクリプトの生成前に保存されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-128">The wizard saves these modified input files before generating the XMLA deployment script.</span></span> <span data-ttu-id="4a3db-129">変更された入力ファイルは、次にウィザードを実行したときの開始点として使用されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-129">The modified input files become the new starting point the next time that the wizard is run.</span></span>  
  
 <span data-ttu-id="4a3db-130">ウィザードを応答ファイルモードで実行するには、 **/a**スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-130">To run the wizard in answer file mode, use the **/a** switch.</span></span>  
  
 <span data-ttu-id="4a3db-131">**サイレント モード**</span><span class="sxs-lookup"><span data-stu-id="4a3db-131">**Silent mode**</span></span>  
 <span data-ttu-id="4a3db-132">サイレント モードでは、ウィザードは入力ファイルに含まれている情報に基づいて、自動的に配置を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-132">In silent mode, the wizard runs a silent, unattended deployment based on the information resident in the input files.</span></span>  
  
 <span data-ttu-id="4a3db-133">サイレントモードでウィザードを実行するには、 **/s**スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-133">To run the wizard in silent mode, use the **/s** switch.</span></span> <span data-ttu-id="4a3db-134">サイレント モードでウィザードを実行した場合、メッセージはコンソールに出力されます。ログ ファイルを指定した場合はログ ファイルに出力されます。</span><span class="sxs-lookup"><span data-stu-id="4a3db-134">When you run the wizard in silent mode, messages are output to the console or to a log file if one is provided.</span></span>  
  
 <span data-ttu-id="4a3db-135">**出力モード**</span><span class="sxs-lookup"><span data-stu-id="4a3db-135">**Output mode**</span></span>  
 <span data-ttu-id="4a3db-136">出力モードでは、ウィザードは入力ファイルに基づいて、後で実行するための XMLA 配置スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-136">In output mode, the wizard generates an XMLA deployment script for later execution based on the input files.</span></span>  
  
 <span data-ttu-id="4a3db-137">ウィザードを出力モードで実行するには、 **/o**スイッチを使用して出力ファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-137">To run the wizard in output mode, use the **/o** switch and provide an output file name.</span></span>  
  
 <span data-ttu-id="4a3db-138">これらのコマンド ライン スイッチの詳細については、「 [配置ユーティリティを使用したモデル ソリューションの配置](deploy-model-solutions-with-the-deployment-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a3db-138">For more information about these command line switches, see [Deploy Model Solutions with the Deployment Utility](deploy-model-solutions-with-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="4a3db-139">次の手順では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-139">The following procedure describes how to run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="4a3db-140">Analysis Services 配置ウィザードをコマンド プロンプトで実行するには</span><span class="sxs-lookup"><span data-stu-id="4a3db-140">To run the Analysis Services Deployment Wizard at the command prompt</span></span>  
  
1.  <span data-ttu-id="4a3db-141">コマンド プロンプトを開き、C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-141">Open a command prompt and navigate to the C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE folder.</span></span>  
  
2.  <span data-ttu-id="4a3db-142">「 **Microsoft.AnalysisServices.Deployment.exe** 」の後に、ウィザードを実行するモードに対応するスイッチを入力します。</span><span class="sxs-lookup"><span data-stu-id="4a3db-142">Type **Microsoft.AnalysisServices.Deployment.exe** followed by the switches that correspond to the mode in which you want to run the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3db-143">参照</span><span class="sxs-lookup"><span data-stu-id="4a3db-143">See Also</span></span>  
 <span data-ttu-id="4a3db-144">[Analysis Services 配置スクリプトについて](understanding-the-analysis-services-deployment-script.md) </span><span class="sxs-lookup"><span data-stu-id="4a3db-144">[Understanding the Analysis Services Deployment Script](understanding-the-analysis-services-deployment-script.md) </span></span>  
 [<span data-ttu-id="4a3db-145">Deploy Model Solutions Using the Deployment Wizard</span><span class="sxs-lookup"><span data-stu-id="4a3db-145">Deploy Model Solutions Using the Deployment Wizard</span></span>](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
