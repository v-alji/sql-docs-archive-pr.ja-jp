---
title: インストール先の指定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
ms.openlocfilehash: e830fc353898e3ec835b338e84765a0cad0de43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641900"
---
# <a name="specifying-the-installation-target"></a><span data-ttu-id="785e7-102">インストール先の指定</span><span class="sxs-lookup"><span data-stu-id="785e7-102">Specifying the Installation Target</span></span>
  <span data-ttu-id="785e7-103">配置ウィザードでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インストール先の情報を \<*project name*> deploymenttargets ファイルから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="785e7-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the installation target information from the \<*project name*>.deploymenttargets file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="785e7-104">は、プロジェクトのビルド時にこのファイルを作成し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="785e7-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="785e7-105">では、[ **Deployment** *\<project name>* **プロパティページ**] ダイアログボックスの [配置] ページで指定したデータベースとサーバーを使用して、 \<*project name*> .targets ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="785e7-105">uses the database and server specified on the **Deployment** page of the *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.targets file.</span></span>  
  
## <a name="modifying-the-installation-target-for-deployment"></a><span data-ttu-id="785e7-106">配置に関するインストール先の変更</span><span class="sxs-lookup"><span data-stu-id="785e7-106">Modifying the Installation Target for Deployment</span></span>  
 <span data-ttu-id="785e7-107">場合によっては、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [配置] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ページで指定されたものとは別のデータベースまたは **インスタンスに** プロジェクトを配置する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="785e7-107">In some situations, you may need to deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is different than the one specified on the **Deployment** page.</span></span> <span data-ttu-id="785e7-108">たとえば、配置前のテストを行うためにプロジェクトをサーバーに配置し、テストの完了後にそのプロジェクトを実稼働サーバーに配置する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="785e7-108">For example, you may want to deploy the project to a server for testing before deployment, and then deploy it to a production server after testing is finished.</span></span> <span data-ttu-id="785e7-109">また、完成したテスト済みのプロジェクトをネットワーク負荷分散クラスター内の複数の実稼働サーバーに配置するか、ステージング サーバーおよび実稼働サーバーに配置する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="785e7-109">You may also want to deploy a completed and tested project to multiple production servers in a Network Load Balancing cluster, or to a staging server and a production server.</span></span>  
  
 <span data-ttu-id="785e7-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを別のデータベースまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置するには、次の手順で説明するいずれかの方法に従って、入力ファイル内のインストール先を変更します。</span><span class="sxs-lookup"><span data-stu-id="785e7-110">To deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a different database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you can change the installation target in the input file by using one of the methods described in the following procedure.</span></span>  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a><span data-ttu-id="785e7-111">入力ファイルの生成後にインストール先を変更するには</span><span class="sxs-lookup"><span data-stu-id="785e7-111">To change the installation target after the input files have been generated</span></span>  
  
-   <span data-ttu-id="785e7-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行します。</span><span class="sxs-lookup"><span data-stu-id="785e7-112">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="785e7-113">**[インストールの対象]** ページで、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスとデータベースの新しいインストール先を指定します。</span><span class="sxs-lookup"><span data-stu-id="785e7-113">On the **Installation Target** page, specify a new destination for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database.</span></span>  
  
     <span data-ttu-id="785e7-114">または</span><span class="sxs-lookup"><span data-stu-id="785e7-114">-or-</span></span>  
  
-   <span data-ttu-id="785e7-115">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="785e7-115">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="785e7-116">応答ファイル モードの詳細については、「 [Analysis Services 配置ウィザードの実行](running-the-analysis-services-deployment-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="785e7-116">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="785e7-117">または</span><span class="sxs-lookup"><span data-stu-id="785e7-117">-or-</span></span>  
  
-   <span data-ttu-id="785e7-118">任意の \<*project name*> テキストエディターを使用して、deploymenttargets ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="785e7-118">Modify the \<*project name*>.deploymenttargets file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785e7-119">参照</span><span class="sxs-lookup"><span data-stu-id="785e7-119">See Also</span></span>  
 <span data-ttu-id="785e7-120">[パーティションおよびロールの配置オプションの指定](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="785e7-120">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 <span data-ttu-id="785e7-121">[ソリューション配置の構成設定の指定](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="785e7-121">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="785e7-122">処理オプションの指定</span><span class="sxs-lookup"><span data-stu-id="785e7-122">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
