---
title: フォルダーとファイルのアクセス許可 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], file and folder
- folders [Master Data Services]
- files [Master Data Services]
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
author: lrtoyou1223
ms.author: lle
robots: noindex,nofollow
ms.openlocfilehash: 6dc356e074574a4c520b1f4de2f41db0e983c4df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715510"
---
# <a name="folder-and-file-permissions-master-data-services"></a><span data-ttu-id="36bf7-102">フォルダーとファイルの権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="36bf7-102">Folder and File Permissions (Master Data Services)</span></span>
  <span data-ttu-id="36bf7-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のインストール時に、ファイル システムで指定のインストール パスにフォルダーとファイルが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 共有機能用にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="36bf7-103">When you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], folders and files are installed in the file system at the installation path you specify for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features.</span></span> <span data-ttu-id="36bf7-104">共有機能に既定のインストールパスを使用する場合 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、のインストールパス [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は*drive*://SQL server の Data Services です。</span><span class="sxs-lookup"><span data-stu-id="36bf7-104">If you use the default installation path for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features, the installation path for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span> <span data-ttu-id="36bf7-105">共有機能のインストール パスは変更できますが、親フォルダーから継承される権限と [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]に対して明示的に設定されている権限に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36bf7-105">Although you can change the shared features installation path, be aware of permissions that are inherited from the parent folder and permissions that are explicitly set for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>  
  
## <a name="inherited-permissions"></a><span data-ttu-id="36bf7-106">継承された権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-106">Inherited Permissions</span></span>  
 <span data-ttu-id="36bf7-107">**Microsoft SQL Server** フォルダー、 **Master Data Services** フォルダー、および大半のサブフォルダーとファイルは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセットアップで指定した親フォルダーから権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="36bf7-107">The **Microsoft SQL Server** folder, the **Master Data Services** folder, and most subfolders and files inherit permissions from the parent folder specified in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="36bf7-108">既定のインストール場所を使用している場合、権限の継承元の親フォルダーは *drive*:\Program Files です。</span><span class="sxs-lookup"><span data-stu-id="36bf7-108">If you choose the default installation location, the parent folder that permissions are inherited from is *drive*:\Program Files.</span></span> <span data-ttu-id="36bf7-109">次の表では、 **Program Files**に対する既定の権限について説明します。</span><span class="sxs-lookup"><span data-stu-id="36bf7-109">The following table describes the default permissions for **Program Files**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36bf7-110">**Program Files**に対する既定の権限を変更するか、または別のインストール場所を選択すると、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のフォルダーとファイルは対応する親フォルダーから権限を継承します。そのため、次の表で説明する権限と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="36bf7-110">If you modify default permissions for **Program Files**, or you choose a different installation location, the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] folders and files inherit permissions from their parent folder accordingly, and the permissions might differ from those described in the following table.</span></span>  
  
###### <a name="program-files-default-permissions"></a><span data-ttu-id="36bf7-111">Program Files の既定の権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-111">Program Files Default Permissions</span></span>  
  
|<span data-ttu-id="36bf7-112">グループ名またはアカウント名</span><span class="sxs-lookup"><span data-stu-id="36bf7-112">Group or account name</span></span>|<span data-ttu-id="36bf7-113">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="36bf7-113">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="36bf7-114">CREATOR OWNER</span><span class="sxs-lookup"><span data-stu-id="36bf7-114">CREATOR OWNER</span></span>|<span data-ttu-id="36bf7-115">特別な権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-115">Special permissions</span></span>|  
|<span data-ttu-id="36bf7-116">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="36bf7-116">SYSTEM</span></span>|<span data-ttu-id="36bf7-117">特別な権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-117">Special permissions</span></span>|  
|<span data-ttu-id="36bf7-118">管理者</span><span class="sxs-lookup"><span data-stu-id="36bf7-118">Administrators</span></span>|<span data-ttu-id="36bf7-119">特別な権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-119">Special permissions</span></span>|  
|<span data-ttu-id="36bf7-120">ユーザー</span><span class="sxs-lookup"><span data-stu-id="36bf7-120">Users</span></span>|<span data-ttu-id="36bf7-121">読み取りと実行、フォルダー内容の一覧表示、読み取り</span><span class="sxs-lookup"><span data-stu-id="36bf7-121">Read & execute, List folder contents, Read</span></span>|  
|<span data-ttu-id="36bf7-122">TrustedInstaller</span><span class="sxs-lookup"><span data-stu-id="36bf7-122">TrustedInstaller</span></span>|<span data-ttu-id="36bf7-123">フォルダー内容の一覧表示、特別な権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-123">List folder contents, Special permissions</span></span>|  
  
## <a name="explicit-permissions"></a><span data-ttu-id="36bf7-124">明示的権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-124">Explicit Permissions</span></span>  
 <span data-ttu-id="36bf7-125">**MDSTempDir** フォルダーと [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config ファイル ( **WebApplication** フォルダーにあります) は、権限を継承しません。</span><span class="sxs-lookup"><span data-stu-id="36bf7-125">The **MDSTempDir** folder and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file (in the **WebApplication** folder) do not inherit permissions.</span></span> <span data-ttu-id="36bf7-126">これらには、選択したインストール パスに関係なく、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールするときに明示的に設定された権限があります。</span><span class="sxs-lookup"><span data-stu-id="36bf7-126">They have permissions that are set explicitly when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], regardless of the installation path you choose.</span></span> <span data-ttu-id="36bf7-127">これらの権限を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="36bf7-127">Do not modify these permissions.</span></span>  
  
###### <a name="mdstempdir-permissions"></a><span data-ttu-id="36bf7-128">MDSTempDir 権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-128">MDSTempDir Permissions</span></span>  
  
|<span data-ttu-id="36bf7-129">グループ名またはアカウント名</span><span class="sxs-lookup"><span data-stu-id="36bf7-129">Group or account name</span></span>|<span data-ttu-id="36bf7-130">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="36bf7-130">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="36bf7-131">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="36bf7-131">SYSTEM</span></span>|<span data-ttu-id="36bf7-132">変更、読み取りと実行、フォルダー内容の一覧表示、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="36bf7-132">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="36bf7-133">管理者</span><span class="sxs-lookup"><span data-stu-id="36bf7-133">Administrators</span></span>|<span data-ttu-id="36bf7-134">変更、読み取りと実行、フォルダー内容の一覧表示、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="36bf7-134">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="36bf7-135">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="36bf7-135">MDS_ServiceAccounts</span></span>|<span data-ttu-id="36bf7-136">変更、読み取りと実行、フォルダー内容の一覧表示、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="36bf7-136">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
  
###### <a name="webconfig-permissions"></a><span data-ttu-id="36bf7-137">Web.config 権限</span><span class="sxs-lookup"><span data-stu-id="36bf7-137">Web.config Permissions</span></span>  
  
|<span data-ttu-id="36bf7-138">グループ名またはアカウント名</span><span class="sxs-lookup"><span data-stu-id="36bf7-138">Group or account name</span></span>|<span data-ttu-id="36bf7-139">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="36bf7-139">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="36bf7-140">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="36bf7-140">SYSTEM</span></span>|<span data-ttu-id="36bf7-141">フル コントロール、変更、読み取りと実行、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="36bf7-141">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="36bf7-142">管理者</span><span class="sxs-lookup"><span data-stu-id="36bf7-142">Administrators</span></span>|<span data-ttu-id="36bf7-143">フル コントロール、変更、読み取りと実行、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="36bf7-143">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="36bf7-144">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="36bf7-144">MDS_ServiceAccounts</span></span>|<span data-ttu-id="36bf7-145">読み取りと実行、読み取り</span><span class="sxs-lookup"><span data-stu-id="36bf7-145">Read & execute, Read</span></span>|  
  
 <span data-ttu-id="36bf7-146">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config ファイルのコンテンツの詳細については、「[Web 設定リファレンス (マスター データ サービス)](web-configuration-reference-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36bf7-146">For more information about the contents of the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file, see [Web Configuration Reference &#40;Master Data Services&#41;](web-configuration-reference-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bf7-147">参照</span><span class="sxs-lookup"><span data-stu-id="36bf7-147">See Also</span></span>  
 [<span data-ttu-id="36bf7-148">マスター データ サービスのインストール</span><span class="sxs-lookup"><span data-stu-id="36bf7-148">Install Master Data Services</span></span>](install-windows/install-master-data-services.md)  
  
  
