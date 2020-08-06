---
title: '[Package Management オプションの選択] (SSIS パッケージアップグレードウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectpackagemgtoptions.f1
ms.assetid: 810fc020-51cd-43ed-9f35-af99b4f35947
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5113ad5a1f6758a75742ca58aef04ce92168649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645732"
---
# <a name="select-package-management-options-ssis-package-upgrade-wizard"></a><span data-ttu-id="e6171-102">[パッケージ管理オプションの選択] (SSIS パッケージ アップグレード ウィザード)</span><span class="sxs-lookup"><span data-stu-id="e6171-102">Select Package Management Options (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="e6171-103">**[パッケージ管理オプションの選択]** ページを使用すると、パッケージのアップグレードに関するオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e6171-103">Use the **Select Package Management Options** page to specify options for upgrading packages.</span></span>  
  
 <span data-ttu-id="e6171-104">**SSIS パッケージ アップグレード ウィザードを実行するには**</span><span class="sxs-lookup"><span data-stu-id="e6171-104">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="e6171-105">SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="e6171-105">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="e6171-106">Options</span><span class="sxs-lookup"><span data-stu-id="e6171-106">Options</span></span>  
 <span data-ttu-id="e6171-107">**[接続文字列を更新して新しいプロバイダー名を使用する]**</span><span class="sxs-lookup"><span data-stu-id="e6171-107">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="e6171-108">現在のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]の次のプロバイダーの名前を使用するように、接続文字列を更新します。</span><span class="sxs-lookup"><span data-stu-id="e6171-108">Update the connection strings to use the names for the following providers for the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="e6171-109">OLE DB Provider for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6171-109">OLE DB Provider for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e6171-110">Native Client</span><span class="sxs-lookup"><span data-stu-id="e6171-110">Native Client</span></span>  
  
 <span data-ttu-id="e6171-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、接続マネージャーに格納されている接続文字列だけを更新します。</span><span class="sxs-lookup"><span data-stu-id="e6171-111">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="e6171-112">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の式言語またはスクリプト タスクのコードによって動的に構築される接続文字列は更新しません。</span><span class="sxs-lookup"><span data-stu-id="e6171-112">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="e6171-113">**[アップグレード パッケージの検証]**</span><span class="sxs-lookup"><span data-stu-id="e6171-113">**Validate upgrade packages**</span></span>  
 <span data-ttu-id="e6171-114">アップグレード パッケージを検証し、検証に合格したアップグレード パッケージだけを保存します。</span><span class="sxs-lookup"><span data-stu-id="e6171-114">Validate the upgrade packages and save only those upgrade packages that pass validation.</span></span>  
  
 <span data-ttu-id="e6171-115">このオプションを選択しない場合、ウィザードでアップグレード パッケージの検証が行われません。</span><span class="sxs-lookup"><span data-stu-id="e6171-115">If you do not select this option, the wizard will not validate upgrade packages.</span></span> <span data-ttu-id="e6171-116">したがって、有効なパッケージかどうかにかかわらず、すべてのアップグレード パッケージが保存されます。</span><span class="sxs-lookup"><span data-stu-id="e6171-116">Therefore, the wizard will save all upgrade packages, regardless of whether the packages are valid or not.</span></span> <span data-ttu-id="e6171-117">ウィザードの **[アップグレード先の場所を選択]** ページで指定したアップグレード先に、アップグレード パッケージが保存されます。</span><span class="sxs-lookup"><span data-stu-id="e6171-117">The wizard saves upgrade packages to the destination that is specified on the **SelectDestination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="e6171-118">検証を行うと、アップグレード プロセスにかかる時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="e6171-118">Validation adds time to the upgrade process.</span></span> <span data-ttu-id="e6171-119">アップグレードに成功する可能性の高い大規模なパッケージに対しては、このオプションを選択しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e6171-119">We recommend that you do not select this option for large packages that are likely to be upgraded successfully.</span></span>  
  
 <span data-ttu-id="e6171-120">**[新しいパッケージ ID を作成する]**</span><span class="sxs-lookup"><span data-stu-id="e6171-120">**Create new package IDs**</span></span>  
 <span data-ttu-id="e6171-121">アップグレード パッケージの新しいパッケージ ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="e6171-121">Create new package IDs for the upgrade packages.</span></span>  
  
 <span data-ttu-id="e6171-122">**[パッケージのアップグレードに失敗してもアップグレード処理を続行する]**</span><span class="sxs-lookup"><span data-stu-id="e6171-122">**Continue upgrade process when a package upgrade fails**</span></span>  
 <span data-ttu-id="e6171-123">あるパッケージをアップグレードできなかった場合に、残りのパッケージのアップグレードを [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードで続行します。</span><span class="sxs-lookup"><span data-stu-id="e6171-123">Specify that when a package cannot be upgraded, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard continues to upgrade the remaining packages.</span></span>  
  
 <span data-ttu-id="e6171-124">**[パッケージ名の競合]**</span><span class="sxs-lookup"><span data-stu-id="e6171-124">**Package name conflicts**</span></span>  
 <span data-ttu-id="e6171-125">同じ名前のパッケージをウィザードで処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6171-125">Specify how the wizard should handle packages that have the same name.</span></span> <span data-ttu-id="e6171-126">このオプションには、次の表に示す値があります。</span><span class="sxs-lookup"><span data-stu-id="e6171-126">This option has the values listed in the following table.</span></span>  
  
 <span data-ttu-id="e6171-127">**[既存のパッケージ ファイルを上書き]**</span><span class="sxs-lookup"><span data-stu-id="e6171-127">**Overwrite existing package files**</span></span>  
 <span data-ttu-id="e6171-128">既存のパッケージを同じ名前のアップグレード パッケージで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e6171-128">Replaces the existing package with the upgrade package of the same name.</span></span>  
  
 <span data-ttu-id="e6171-129">**[アップグレード パッケージ名に数値サフィックスを追加]**</span><span class="sxs-lookup"><span data-stu-id="e6171-129">**Add numeric suffixes to upgrade package names**</span></span>  
 <span data-ttu-id="e6171-130">アップグレード パッケージの名前に数値サフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="e6171-130">Adds a numeric suffix to the name of the upgrade package.</span></span>  
  
 <span data-ttu-id="e6171-131">**[パッケージをアップグレードしない]**</span><span class="sxs-lookup"><span data-stu-id="e6171-131">**Do not upgrade packages**</span></span>  
 <span data-ttu-id="e6171-132">そのパッケージのアップグレードを停止し、ウィザードの完了時にエラーを表示します。</span><span class="sxs-lookup"><span data-stu-id="e6171-132">Stops the packages from being upgraded and displays an error when you complete the wizard.</span></span>  
  
 <span data-ttu-id="e6171-133">ウィザードの **[アップグレード先の場所を選択]** ページで **[ソースの場所に保存]** オプションを選択した場合は、これらのオプションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="e6171-133">These options are not available when you select the **Save to source location** option on the **Select Destination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="e6171-134">**[構成を無視する]**</span><span class="sxs-lookup"><span data-stu-id="e6171-134">**Ignore Configurations**</span></span>  
 <span data-ttu-id="e6171-135">パッケージのアップグレード中にパッケージ構成を読み込みません。</span><span class="sxs-lookup"><span data-stu-id="e6171-135">Does not load package configurations during the package upgrade.</span></span> <span data-ttu-id="e6171-136">このオプションを選択すると、パッケージのアップグレードに必要な時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="e6171-136">Selecting this option reduces the time required to upgrade the package.</span></span>  
  
 <span data-ttu-id="e6171-137">**[元のパッケージをバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="e6171-137">**Backup original packages**</span></span>  
 <span data-ttu-id="e6171-138">ウィザードで、元のパッケージを **SSISBackupFolder** フォルダーにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="e6171-138">Have the wizard back up the original packages to an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="e6171-139">元のパッケージとアップグレード済みパッケージが格納されるフォルダーに、 **SSISBackupFolder** サブフォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6171-139">The wizard creates the **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6171-140">このオプションを使用できるのは、元のパッケージとアップグレード済みパッケージをファイル システム内の同一フォルダーに格納するように指定した場合だけです。</span><span class="sxs-lookup"><span data-stu-id="e6171-140">This option is available only when you specify that the original packages and the upgraded packages are stored in the file system and in the same folder.</span></span>  
  
 <span data-ttu-id="e6171-141">詳細については、「 [SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6171-141">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6171-142">参照</span><span class="sxs-lookup"><span data-stu-id="e6171-142">See Also</span></span>  
 [<span data-ttu-id="e6171-143">Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="e6171-143">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
