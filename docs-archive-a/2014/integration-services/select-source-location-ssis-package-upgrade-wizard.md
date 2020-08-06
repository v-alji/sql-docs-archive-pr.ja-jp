---
title: '[ソースの場所の選択] (SSIS パッケージアップグレードウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e24eec77dc87a6215f9d686cf5af964cc244d68d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712137"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="48d4e-102">[ソースの場所を選択] (SSIS パッケージ アップグレード ウィザード)</span><span class="sxs-lookup"><span data-stu-id="48d4e-102">Select Source Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="48d4e-103">**[ソースの場所を選択]** ページを使用すると、パッケージのアップグレード元を指定できます。</span><span class="sxs-lookup"><span data-stu-id="48d4e-103">Use the **Select Source Location** page to specify the source from which to upgrade packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48d4e-104">このページは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトから実行した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="48d4e-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="48d4e-105">**SSIS パッケージ アップグレード ウィザードを実行するには**</span><span class="sxs-lookup"><span data-stu-id="48d4e-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="48d4e-106">SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="48d4e-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="48d4e-107">静的オプション</span><span class="sxs-lookup"><span data-stu-id="48d4e-107">Static Options</span></span>  
 <span data-ttu-id="48d4e-108">**パッケージソース**</span><span class="sxs-lookup"><span data-stu-id="48d4e-108">**Package source**</span></span>  
 <span data-ttu-id="48d4e-109">アップグレードするパッケージが格納されている場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-109">Select the storage location that contains the packages to be upgraded.</span></span> <span data-ttu-id="48d4e-110">このオプションには、次の表に示す値があります。</span><span class="sxs-lookup"><span data-stu-id="48d4e-110">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="48d4e-111">値</span><span class="sxs-lookup"><span data-stu-id="48d4e-111">Value</span></span>|<span data-ttu-id="48d4e-112">説明</span><span class="sxs-lookup"><span data-stu-id="48d4e-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48d4e-113">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="48d4e-113">**File System**</span></span>|<span data-ttu-id="48d4e-114">アップグレードするパッケージがローカル コンピューター上のフォルダーにあることを示します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-114">Indicates that the packages to be upgraded are in a folder on the local computer.</span></span><br /><br /> <span data-ttu-id="48d4e-115">パッケージをアップグレードする前に元のパッケージをウィザードでバックアップするには、元のパッケージがファイル システムに格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="48d4e-115">To have the wizard back up the original packages before upgrading those packages, the original packages must be stored in the file system.</span></span> <span data-ttu-id="48d4e-116">詳細については、方法に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48d4e-116">For more information, see How To Topic.</span></span>|  
|<span data-ttu-id="48d4e-117">**[SSIS パッケージ ストア]**</span><span class="sxs-lookup"><span data-stu-id="48d4e-117">**SSIS Package Store**</span></span>|<span data-ttu-id="48d4e-118">アップグレードするパッケージがパッケージ ストア内にあることを示します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-118">Indicates that the packages to be upgraded are in the package store.</span></span> <span data-ttu-id="48d4e-119">パッケージ ストアは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するファイル システム フォルダーのセットで構成されます。</span><span class="sxs-lookup"><span data-stu-id="48d4e-119">The package store consists of the set of file system folders that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span> <span data-ttu-id="48d4e-120">詳細については、「[パッケージの管理 &#40;SSIS サービス&#41;](service/package-management-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48d4e-120">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="48d4e-121">この値を選択すると、対応する **パッケージ ソース** 動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48d4e-121">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
|<span data-ttu-id="48d4e-122">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="48d4e-122">**Microsoft SQL Server**</span></span>|<span data-ttu-id="48d4e-123">アップグレードするパッケージが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の既存のインスタンス内にあることを示します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-123">Indicates the packages to be upgraded are from an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="48d4e-124">この値を選択すると、対応する **パッケージ ソース** 動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48d4e-124">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="48d4e-125">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="48d4e-125">**Folder**</span></span>  
 <span data-ttu-id="48d4e-126">アップグレードするパッケージが格納されているフォルダーの名前を入力するか、 **[参照]** をクリックしてフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-126">Type the name of a folder that contains the packages you want to upgrade or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="48d4e-127">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="48d4e-127">**Browse**</span></span>  
 <span data-ttu-id="48d4e-128">アップグレードするパッケージが格納されているフォルダーを参照して指定します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-128">Browse to locate the folder that contains the packages you want to upgrade.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="48d4e-129">パッケージ ソース動的オプション</span><span class="sxs-lookup"><span data-stu-id="48d4e-129">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="48d4e-130">[パッケージ ソース] = [SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="48d4e-130">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="48d4e-131">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="48d4e-131">**Server**</span></span>  
 <span data-ttu-id="48d4e-132">アップグレードするパッケージが存在するサーバーの名前を入力するか、一覧からこのサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-132">Type the name of the server that has the packages to be upgraded, or select this server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="48d4e-133">[パッケージ ソース] = [Microsoft SQL Server]</span><span class="sxs-lookup"><span data-stu-id="48d4e-133">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="48d4e-134">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="48d4e-134">**Server**</span></span>  
 <span data-ttu-id="48d4e-135">アップグレードするパッケージが存在するサーバーの名前を入力するか、一覧からこのサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-135">Type the name of the server that has the packages to be upgraded, or select this server from the list.</span></span>  
  
 <span data-ttu-id="48d4e-136">**Windows 認証を使用する**</span><span class="sxs-lookup"><span data-stu-id="48d4e-136">**Use Windows authentication**</span></span>  
 <span data-ttu-id="48d4e-137">Windows 認証を使用してサーバーに接続する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-137">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="48d4e-138">**SQL Server 認証を使用する**</span><span class="sxs-lookup"><span data-stu-id="48d4e-138">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="48d4e-139">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用してサーバーに接続する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-139">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="48d4e-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48d4e-140">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="48d4e-141">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="48d4e-141">**User name**</span></span>  
 <span data-ttu-id="48d4e-142">サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-142">Type the user name that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
 <span data-ttu-id="48d4e-143">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="48d4e-143">**Password**</span></span>  
 <span data-ttu-id="48d4e-144">サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="48d4e-144">Type the password that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d4e-145">参照</span><span class="sxs-lookup"><span data-stu-id="48d4e-145">See Also</span></span>  
 [<span data-ttu-id="48d4e-146">Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="48d4e-146">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
