---
title: '[バックアップ先の場所の選択] (SSIS パッケージアップグレードウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectdestinationlocation.f1
ms.assetid: 89274a71-0ffe-4889-84df-f5a7d78459ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9411157434c3dbb9fb033f7b63b5e6041fd8f75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645734"
---
# <a name="select-destination-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="0160b-102">[アップグレード先の場所を選択] (SSIS パッケージ アップグレード ウィザード)</span><span class="sxs-lookup"><span data-stu-id="0160b-102">Select Destination Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="0160b-103">**[アップグレード先の場所を選択]** ページを使用すると、アップグレードされたパッケージの保存先を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0160b-103">Use the **Select Destination Location** page to specify the destination to which to save the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0160b-104">このページは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトから実行した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0160b-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="0160b-105">**SSIS パッケージ アップグレード ウィザードを実行するには**</span><span class="sxs-lookup"><span data-stu-id="0160b-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="0160b-106">SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="0160b-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="0160b-107">静的オプション</span><span class="sxs-lookup"><span data-stu-id="0160b-107">Static Options</span></span>  
 <span data-ttu-id="0160b-108">**[アップグレード元の場所に保存する]**</span><span class="sxs-lookup"><span data-stu-id="0160b-108">**Save to source location**</span></span>  
 <span data-ttu-id="0160b-109">ウィザードの **[ソースの場所を選択]** ページで指定した場所と同じ場所に、アップグレードされたパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="0160b-109">Save the upgraded packages to the same location as specified on the **Select Source Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="0160b-110">元のパッケージがファイル システムに格納されている場合に、ウィザードでそれらのパッケージをバックアップするには、 **[ソースの場所に保存]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0160b-110">If the original packages are stored in the file system and you want the wizard to back up those packages, select the **Save to source location** option.</span></span> <span data-ttu-id="0160b-111">詳細については、「 [SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0160b-111">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
 <span data-ttu-id="0160b-112">**[新しいアップグレード先の場所を選択]**</span><span class="sxs-lookup"><span data-stu-id="0160b-112">**Select new destination location**</span></span>  
 <span data-ttu-id="0160b-113">このページで指定したアップグレード先の場所に、アップグレードされたパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="0160b-113">Save the upgraded packages to the destination location that is specified on this page.</span></span>  
  
 <span data-ttu-id="0160b-114">**パッケージソース**</span><span class="sxs-lookup"><span data-stu-id="0160b-114">**Package source**</span></span>  
 <span data-ttu-id="0160b-115">アップグレード パッケージが格納される場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="0160b-115">Specify where the upgrade packages are to be stored.</span></span> <span data-ttu-id="0160b-116">このオプションには、次の表に示す値があります。</span><span class="sxs-lookup"><span data-stu-id="0160b-116">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="0160b-117">値</span><span class="sxs-lookup"><span data-stu-id="0160b-117">Value</span></span>|<span data-ttu-id="0160b-118">説明</span><span class="sxs-lookup"><span data-stu-id="0160b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0160b-119">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="0160b-119">**File System**</span></span>|<span data-ttu-id="0160b-120">アップグレードされたパッケージをローカル コンピューター上のフォルダーに保存することを示します。</span><span class="sxs-lookup"><span data-stu-id="0160b-120">Indicates that the upgraded packages are to be saved to a folder on the local computer.</span></span>|  
|<span data-ttu-id="0160b-121">**[SSIS パッケージ ストア]**</span><span class="sxs-lookup"><span data-stu-id="0160b-121">**SSIS Package Store**</span></span>|<span data-ttu-id="0160b-122">アップグレードされたパッケージを Integration Services パッケージ ストア内に保存することを示します。</span><span class="sxs-lookup"><span data-stu-id="0160b-122">Indicates that the upgraded packages are to be saved to the Integration Services package store.</span></span> <span data-ttu-id="0160b-123">パッケージ ストアは、Integration Services サービスが管理するファイル システム フォルダーのセットで構成されます。</span><span class="sxs-lookup"><span data-stu-id="0160b-123">The package store consists of the set of file system folders that the Integration Services service manages.</span></span> <span data-ttu-id="0160b-124">詳細については、「[パッケージの管理 &#40;SSIS サービス&#41;](service/package-management-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0160b-124">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="0160b-125">この値を選択すると、対応する**パッケージ ソース**動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0160b-125">Selecting this value displays the corresponding **Package source** dynamics options.</span></span>|  
|<span data-ttu-id="0160b-126">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="0160b-126">**Microsoft SQL Server**</span></span>|<span data-ttu-id="0160b-127">アップグレードされたパッケージを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の既存のインスタンスに保存することを示します。</span><span class="sxs-lookup"><span data-stu-id="0160b-127">Indicates that the upgraded packages are to be saved to an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="0160b-128">この値を選択すると、対応する **パッケージ ソース** 動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0160b-128">Selecting this value displays the corresponding dynamic **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="0160b-129">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="0160b-129">**Folder**</span></span>  
 <span data-ttu-id="0160b-130">アップグレードされたパッケージを保存するフォルダーの名前を入力するか、 **[参照]** をクリックしてフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="0160b-130">Type the name of a folder to which the upgraded packages will be saved, or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="0160b-131">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="0160b-131">**Browse**</span></span>  
 <span data-ttu-id="0160b-132">アップグレードされたパッケージを保存するフォルダーを、参照して指定します。</span><span class="sxs-lookup"><span data-stu-id="0160b-132">Browse to locate the folder to which the upgraded packages will be saved.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="0160b-133">パッケージ ソース動的オプション</span><span class="sxs-lookup"><span data-stu-id="0160b-133">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="0160b-134">[パッケージ ソース] = [SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="0160b-134">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="0160b-135">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="0160b-135">**Server**</span></span>  
 <span data-ttu-id="0160b-136">アップグレード パッケージを保存するサーバーの名前を入力するか、一覧からサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="0160b-136">Type the name of the server to which the upgrade packages will be saved, or select a server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="0160b-137">[パッケージ ソース] = [Microsoft SQL Server]</span><span class="sxs-lookup"><span data-stu-id="0160b-137">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="0160b-138">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="0160b-138">**Server**</span></span>  
 <span data-ttu-id="0160b-139">アップグレード パッケージを保存するサーバーの名前を入力するか、一覧からこのサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="0160b-139">Type the name of the server to which the upgrade packages will be saved, or select this server in the list.</span></span>  
  
 <span data-ttu-id="0160b-140">**Windows 認証を使用する**</span><span class="sxs-lookup"><span data-stu-id="0160b-140">**Use Windows authentication**</span></span>  
 <span data-ttu-id="0160b-141">Windows 認証を使用してサーバーに接続する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="0160b-141">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="0160b-142">**SQL Server 認証を使用する**</span><span class="sxs-lookup"><span data-stu-id="0160b-142">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="0160b-143">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用してサーバーに接続する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="0160b-143">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="0160b-144">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0160b-144">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="0160b-145">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="0160b-145">**User name**</span></span>  
 <span data-ttu-id="0160b-146">サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="0160b-146">Type the user name to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="0160b-147">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="0160b-147">**Password**</span></span>  
 <span data-ttu-id="0160b-148">サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="0160b-148">Type the password to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0160b-149">参照</span><span class="sxs-lookup"><span data-stu-id="0160b-149">See Also</span></span>  
 [<span data-ttu-id="0160b-150">Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="0160b-150">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
