---
title: パーティションおよびロールの配置オプションの指定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c8dd7bcb482c2d28a18e3039f5acb777b121202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644658"
---
# <a name="specifying-partition-and-role-deployment-options"></a><span data-ttu-id="fa9f0-102">パーティションおよびロールの配置オプションの指定</span><span class="sxs-lookup"><span data-stu-id="fa9f0-102">Specifying Partition and Role Deployment Options</span></span>
  <span data-ttu-id="fa9f0-103">配置ウィザードでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploymentoptions ファイルからパーティションおよびロールの配置オプションを読み取ります。 \<*project name*></span><span class="sxs-lookup"><span data-stu-id="fa9f0-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the partition and role deployment options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="fa9f0-104">は、プロジェクトのビルド時にこのファイルを作成し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="fa9f0-105">\<*project name*>deploymentoptions ファイルが作成されるときに、現在のプロジェクトのパーティションおよびロールの配置オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-105">uses the partition and role deployment options of the current project when the \<*project name*>.deploymentoptions file is created.</span></span> <span data-ttu-id="fa9f0-106">構成設定の詳細については、「 [配置スクリプトを作成するための入力ファイルについて](deployment-script-files-input-used-to-create-deployment-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-106">For more information about configuration settings, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a><span data-ttu-id="fa9f0-107">パーティションおよびロールの配置オプションの確認</span><span class="sxs-lookup"><span data-stu-id="fa9f0-107">Reviewing the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="fa9f0-108">Deploymentoptions ファイルの配置オプションは次のとおりです。 \<*project name*></span><span class="sxs-lookup"><span data-stu-id="fa9f0-108">The deployment options in the \<*project name*>.deploymentoptions file include the following:</span></span>  
  
 <span data-ttu-id="fa9f0-109">**パーティション配置オプション**</span><span class="sxs-lookup"><span data-stu-id="fa9f0-109">**Partition deployment options**</span></span>  
 <span data-ttu-id="fa9f0-110">\<*project name*>Deploymentoptions ファイルは、転送先データベースの既存のパーティションを保持するか上書きするか (既定値) を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-110">The \<*project name*>.deploymentoptions file specifies whether existing partitions in the destination database are retained or overwritten (default).</span></span> <span data-ttu-id="fa9f0-111">既存のパーティションを保持する場合、新しいパーティションのみが配置され、既存のすべてのメジャー グループのパーティションおよび集計デザインはそのまま残されます。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-111">If existing partitions are retained, only new partitions will be deployed, and the partitions and aggregation designs on all existing measure groups are left unchanged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa9f0-112">パーティションが含まれているメジャー グループを削除すると、パーティションも自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-112">If the measure group in which the partition exists is deleted, the partition is automatically deleted.</span></span>  
  
 <span data-ttu-id="fa9f0-113">**ロール配置オプション**</span><span class="sxs-lookup"><span data-stu-id="fa9f0-113">**Role deployment options**</span></span>  
 <span data-ttu-id="fa9f0-114">\<*project name*>Deploymentoptions ファイルは、次のいずれかのロール配置オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-114">The \<*project name*>.deploymentoptions file specifies one of the following role deployment options:</span></span>  
  
-   <span data-ttu-id="fa9f0-115">配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールおよびロール メンバーのみが配置されます。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-115">Existing roles and role members in the destination database are retained, and only new roles and role members are deployed.</span></span>  
  
-   <span data-ttu-id="fa9f0-116">配置先データベースの既存のすべてのロールおよびメンバーは、配置するロールおよびメンバーに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-116">All existing roles and members in the destination database are replaced by the roles and members being deployed.</span></span>  
  
-   <span data-ttu-id="fa9f0-117">配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールは配置されません。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-117">Existing roles and role members in the destination database are retained, and no new roles are deployed.</span></span>  
  
-   <span data-ttu-id="fa9f0-118">**注** 既存のロールおよびメンバーが保持される場合、これらのロールに関連付けられた権限はリセットされてなくなります。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-118">**Note** When existing roles and members are retained, the permissions associated with those roles are reset to none.</span></span> <span data-ttu-id="fa9f0-119">セキュリティ権限は、オブジェクトが関連付けられているセキュリティ ロールではなく、オブジェクト自体に含まれています。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-119">Security permissions are contained by the objects they secure, not by the security roles with which they are associated.</span></span> <span data-ttu-id="fa9f0-120">Analysis Service 配置ウィザードを使用してこの動作を操作する方法の詳細については、Microsoft サポート技術情報の「ロールとメンバーの保持」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-120">For more information about how to work with this behavior by using the Analysis Service Deployment Wizard, see 'Retain Roles and Members' in the Microsoft Knowledge Base.</span></span>  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a><span data-ttu-id="fa9f0-121">パーティションおよびロールの配置オプションの変更</span><span class="sxs-lookup"><span data-stu-id="fa9f0-121">Modifying the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="fa9f0-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Deploymentoptions ファイルに格納されているものとは別のパーティションおよびロールのオプションを使用して、プロジェクトを配置する必要がある場合があります。 \<*project name*></span><span class="sxs-lookup"><span data-stu-id="fa9f0-122">You may have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different partition and role options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="fa9f0-123">たとえば、deploymentoptions ファイルに示されている既存のすべてのパーティション、ロール、およびメンバーを置き換えるのではなく、既存のパーティション、ロール、およびロールメンバーを保持することができます。 \<*project name*></span><span class="sxs-lookup"><span data-stu-id="fa9f0-123">For example, you may want to retain existing partitions, roles, and role members, instead of replacing all existing partitions, roles, and members as indicated in the \<*project name*>.deploymentoptions file.</span></span>  
  
 <span data-ttu-id="fa9f0-124">プロジェクト内のパーティションおよびロールの配置を変更する場合 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、プロジェクト内のパーティションおよびロールの設定を変更することはできません。の [ *\<project name>* **プロパティページ**] ダイアログボックスにはこれらのオプションが表示されないため [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-124">To modify the deployment of partitions and roles in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you cannot change the partition and roles settings within the project because the *\<project name>* **Properties Pages** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] does not display these options.</span></span> <span data-ttu-id="fa9f0-125">ロールおよびパーティションの配置オプションを変更する場合は、 \<*project name*> deploymentoptions ファイル自体でこの情報を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-125">If you want to change the deployment options for roles and partitions, you must change this information within the \<*project name*>.deploymentoptions file itself.</span></span> <span data-ttu-id="fa9f0-126">次の手順では、deploymentoptions ファイル内のパーティションおよびロールの配置オプションを変更する方法について説明します。 \<*project name*></span><span class="sxs-lookup"><span data-stu-id="fa9f0-126">The following procedure describes how to change the partition and role deployment options within the \<*project name*>.deploymentoptions file.</span></span>  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a><span data-ttu-id="fa9f0-127">入力ファイルの生成後にパーティションまたはロールの配置を変更するには</span><span class="sxs-lookup"><span data-stu-id="fa9f0-127">To change the deployment of partitions or roles after the input files have been generated</span></span>  
  
-   <span data-ttu-id="fa9f0-128">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行し、 **[パーティションとロールのオプションの指定]** ページで、パーティションおよびロールの新しい配置オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-128">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively, and on the **Partition and Role Deployment Options** page, specify new deployment options for the partitions and roles.</span></span>  
  
     <span data-ttu-id="fa9f0-129">または</span><span class="sxs-lookup"><span data-stu-id="fa9f0-129">-or-</span></span>  
  
-   <span data-ttu-id="fa9f0-130">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt, and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="fa9f0-131">(応答ファイルモードの詳細については、「 [Analysis Services 配置ウィザードの実行](running-the-analysis-services-deployment-wizard.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-131">(For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).)</span></span>  
  
     <span data-ttu-id="fa9f0-132">または</span><span class="sxs-lookup"><span data-stu-id="fa9f0-132">-or-</span></span>  
  
-   <span data-ttu-id="fa9f0-133">任意の \<*project name*> テキストエディターで. deploymentoptions を開き、オプションを手動で変更します。</span><span class="sxs-lookup"><span data-stu-id="fa9f0-133">Open the \<*project name*>.deploymentoptions in any text editor and manually change the options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9f0-134">参照</span><span class="sxs-lookup"><span data-stu-id="fa9f0-134">See Also</span></span>  
 <span data-ttu-id="fa9f0-135">[インストール先の指定](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="fa9f0-135">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="fa9f0-136">[ソリューション配置の構成設定の指定](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="fa9f0-136">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="fa9f0-137">処理オプションの指定</span><span class="sxs-lookup"><span data-stu-id="fa9f0-137">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
