---
title: SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, upgrading
- upgrading Integration Services packages
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bcafd1c9750d8333639ca2d315512a2c2b8759c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641150"
---
# <a name="upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="d632b-102">SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="d632b-102">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>
  <span data-ttu-id="d632b-103">以前のバージョンの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で作成したパッケージは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で使用される [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 形式にアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="d632b-103">You can upgrade packages that were created in earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] format that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d632b-104">には、このプロセスを容易に行うための [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d632b-104">provides the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard to help in this process.</span></span> <span data-ttu-id="d632b-105">このウィザードは元のパッケージをバックアップするように構成できるため、アップグレードが難しい場合は、元のパッケージを引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="d632b-105">Because you can configure the wizard to backup up your original packages, you can continue to use the original packages if you experience upgrade difficulties.</span></span>  
  
 <span data-ttu-id="d632b-106">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインストール時にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d632b-106">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is installed when [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d632b-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の Standard Edition、Enterprise Edition、および Developer Edition で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d632b-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is available in the Standard, Enterprise, and Developer Editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d632b-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのアップグレード方法については、「 [Integration Services パッケージのアップグレード](upgrade-integration-services-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d632b-108">For more information about how to upgrade [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="d632b-109">以降では、ウィザードの実行方法と元のパッケージのバックアップ方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d632b-109">The remainder of this topic describes how to run the wizard and back up the original packages.</span></span>  
  
## <a name="running-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="d632b-110">SSIS パッケージ アップグレード ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="d632b-110">Running the SSIS Package Upgrade Wizard</span></span>  
 <span data-ttu-id="d632b-111">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、またはコマンド プロンプトから実行できます。</span><span class="sxs-lookup"><span data-stu-id="d632b-111">You can run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or at the command prompt.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-data-tools"></a><span data-ttu-id="d632b-112">SQL Server データ ツールからウィザードを実行するには</span><span class="sxs-lookup"><span data-stu-id="d632b-112">To run the wizard from SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="d632b-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="d632b-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="d632b-114">ソリューション エクスプローラーで、 **[SSIS パッケージ]** ノードを右クリックして **[すべてのパッケージをアップグレード]** をクリックし、このノードの下のすべてのパッケージをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="d632b-114">In Solution Explorer, right-click the **SSIS Packages** node, and then click **Upgrade All Packages** to upgrade all the packages under this node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d632b-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージまたは [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] パッケージが含まれる [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] プロジェクトを開いた場合、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードが自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="d632b-115">When you open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] packages, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] automatically opens the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-management-studio"></a><span data-ttu-id="d632b-116">SQL Server Management Studio からウィザードを実行するには</span><span class="sxs-lookup"><span data-stu-id="d632b-116">To run the wizard from SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="d632b-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に接続し、 **[格納されたパッケージ]** ノードを展開して **[ファイル システム]** ノードまたは **[MSDB]** ノードを右クリックし、 **[パッケージのアップグレード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d632b-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expand the **Stored Packages** node, and right-click the **File System** or **MSDB** node, and then click **Upgrade Packages**.</span></span>  
  
#### <a name="to-run-the-wizard-at-the-command-prompt"></a><span data-ttu-id="d632b-118">コマンド プロンプトでウィザードを実行するには</span><span class="sxs-lookup"><span data-stu-id="d632b-118">To run the wizard at the command prompt</span></span>  
  
-   <span data-ttu-id="d632b-119">コマンドプロンプトで、 **C:\Program Server\120\DTS\Binn**フォルダーから SSISUpgrade.exe ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="d632b-119">At the command prompt, run the SSISUpgrade.exe file from the **C:\Program Files\Microsoft SQL Server\120\DTS\Binn** folder.</span></span>  
  
## <a name="backing-up-the-original-packages"></a><span data-ttu-id="d632b-120">元のパッケージのバックアップ</span><span class="sxs-lookup"><span data-stu-id="d632b-120">Backing Up the Original Packages</span></span>  
 <span data-ttu-id="d632b-121">元のパッケージをバックアップするには、元のパッケージとアップグレードされたパッケージの両方をファイル システム内の同一フォルダーに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d632b-121">To back up the original packages, both the original packages and the upgraded packages must be stored in the same folder in the file system.</span></span> <span data-ttu-id="d632b-122">この格納場所は、ウィザードの実行方法に応じて、自動的に選択される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d632b-122">Depending on how you run the wizard, this storage location might be automatically selected.</span></span>  
  
-   <span data-ttu-id="d632b-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]から実行すると、元のパッケージとアップグレードされたパッケージの両方がファイル システム内の同一フォルダーに自動的に格納されます。</span><span class="sxs-lookup"><span data-stu-id="d632b-123">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the wizard automatically stores both the original packages and upgraded packages in the same folder in the file system.</span></span>  
  
-   <span data-ttu-id="d632b-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトから実行すると、元のパッケージとアップグレードされたパッケージに異なる格納場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d632b-124">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, you can specify different storage locations for the original and upgraded packages.</span></span> <span data-ttu-id="d632b-125">元のパッケージをバックアップするには、元のパッケージとアップグレードされたパッケージの両方がファイル システム内の同一フォルダーに格納されるように指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d632b-125">To back up the original packages, make sure to specify that both the original and upgraded packages are stored in the same folder in the file system.</span></span> <span data-ttu-id="d632b-126">他の格納オプションを指定すると、元のパッケージをバックアップできません。</span><span class="sxs-lookup"><span data-stu-id="d632b-126">If you specify any other storage options, the wizard will not be able to back up the original packages.</span></span>  
  
 <span data-ttu-id="d632b-127">ウィザードで元のパッケージをバックアップすると、元のパッケージのコピーが **SSISBackupFolder** フォルダーにバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="d632b-127">When the wizard backs up the original packages, the wizard stores a copy of the original packages in an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="d632b-128">この **SSISBackupFolder** フォルダーは、元のパッケージとアップグレードされたパッケージが格納されるフォルダーのサブフォルダーとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="d632b-128">The wizard creates this **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-management-studio-or-at-the-command-prompt"></a><span data-ttu-id="d632b-129">SQL Server Management Studio またはコマンド プロンプトで元のパッケージをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="d632b-129">To back up the original packages in SQL Server Management Studio or at the command prompt</span></span>  
  
1.  <span data-ttu-id="d632b-130">元のパッケージをファイル システム上の場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="d632b-130">Save the original packages to a location on the file system.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d632b-131">ウィザードのバックアップ オプションは、ファイル システムに格納されているパッケージに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="d632b-131">The backup option in the wizard only works with packages that have been stored to the file system.</span></span>  
  
2.  <span data-ttu-id="d632b-132">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトで、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d632b-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
3.  <span data-ttu-id="d632b-133">ウィザードの **[アップグレード元の場所の選択]** ページで、 **[パッケージのアップグレード元]** プロパティを **[ファイル システム]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="d632b-133">On the **Select Source Location** page of the wizard, set the **Package source** property to **File System**.</span></span>  
  
4.  <span data-ttu-id="d632b-134">ウィザードの **[アップグレード先の場所の選択]** ページで、 **[アップグレード元の場所に保存する]** をクリックして、アップグレードされたパッケージを、元のパッケージと同じ場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="d632b-134">On the **Select Destination Location** page of the wizard, select **Save to source location** tosave the upgraded packages to the same location as the original packages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d632b-135">ウィザードのバックアップ オプションを使用できるのは、アップグレードされたパッケージが元のパッケージと同じフォルダーに格納されている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="d632b-135">The backup option in the wizard is available only when the upgraded packages are stored in the same folder as the original packages.</span></span>  
  
5.  <span data-ttu-id="d632b-136">ウィザードの **[パッケージ管理オプションの選択]** ページで、 **[元のパッケージをバックアップする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d632b-136">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-data-tools"></a><span data-ttu-id="d632b-137">SQLServer データ ツールの元のパッケージをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="d632b-137">To back up the original packages in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="d632b-138">元のパッケージをファイル システム上の場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="d632b-138">Save the original packages to a location on the file system.</span></span>  
  
2.  <span data-ttu-id="d632b-139">ウィザードの **[パッケージ管理オプションの選択]** ページで、 **[元のパッケージをバックアップする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d632b-139">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="d632b-140">[**元のパッケージのバックアップ**] オプションは、でまたはプロジェクトを開いたときには表示されません。このオプションを指定すると、 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ウィザードが [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="d632b-140">The **Backup original packages** option is not displayed when you open a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which automatically launches the wizard.</span></span>  
  
3.  <span data-ttu-id="d632b-141">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d632b-141">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
  
