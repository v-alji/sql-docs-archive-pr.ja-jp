---
title: プログラムによるパッケージとフォルダーの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 695ff4ad020dbdfb2564b4964a55324db4248517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740129"
---
# <a name="managing-packages-and-folders-programmatically"></a><span data-ttu-id="4f69c-102">プログラムによるパッケージとフォルダーの管理</span><span class="sxs-lookup"><span data-stu-id="4f69c-102">Managing Packages and Folders Programmatically</span></span>
  <span data-ttu-id="4f69c-103">プログラムで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを操作する際に、個々のパッケージやフォルダーが存在するかどうかを判断したり、パッケージが格納されたフォルダーを管理したりする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="4f69c-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine whether an individual package or folder exists, or to manage the folders in which packages are stored.</span></span> <span data-ttu-id="4f69c-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> <span data-ttu-id="4f69c-105">パッケージまたはフォルダーが存在するかどうかの判断</span><span class="sxs-lookup"><span data-stu-id="4f69c-105">Determining Whether a Package or Folder Exists</span></span>  
 <span data-ttu-id="4f69c-106">保存済みのパッケージの読み込みと実行を行う前に、プログラムによってそのパッケージが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-106">To determine programmatically whether a saved package exists, call one of the following methods before attempting to load and run the package:</span></span>  
  
|<span data-ttu-id="4f69c-107">保存先</span><span class="sxs-lookup"><span data-stu-id="4f69c-107">Storage Location</span></span>|<span data-ttu-id="4f69c-108">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="4f69c-108">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="4f69c-109">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="4f69c-109">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 <span data-ttu-id="4f69c-110">フォルダーに保存されているパッケージを一覧表示する前に、プログラムによってそのフォルダーが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-110">To determine programmatically whether a folder exists, call one of the following methods before attempting to list the packages stored in the folder, :</span></span>  
  
|<span data-ttu-id="4f69c-111">保存先</span><span class="sxs-lookup"><span data-stu-id="4f69c-111">Storage Location</span></span>|<span data-ttu-id="4f69c-112">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="4f69c-112">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="4f69c-113">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="4f69c-113">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  

  
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> <span data-ttu-id="4f69c-114">パッケージとフォルダーの管理</span><span class="sxs-lookup"><span data-stu-id="4f69c-114">Managing Packages and Folders</span></span>  
 <span data-ttu-id="4f69c-115"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスには、パッケージおよびそれを格納するフォルダーの管理用に、追加のメソッドが提供されています。</span><span class="sxs-lookup"><span data-stu-id="4f69c-115">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides additional methods for managing packages and the folders in which they are stored.</span></span>  
  
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> <span data-ttu-id="4f69c-116">パッケージの削除</span><span class="sxs-lookup"><span data-stu-id="4f69c-116">Removing a Package</span></span>  
 <span data-ttu-id="4f69c-117">プログラムにより保存済みパッケージを削除するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-117">To remove a saved package programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="4f69c-118">保存先</span><span class="sxs-lookup"><span data-stu-id="4f69c-118">Storage Location</span></span>|<span data-ttu-id="4f69c-119">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="4f69c-119">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="4f69c-120">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="4f69c-120">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="creating-a-folder"></a><a name="managing_create"></a> <span data-ttu-id="4f69c-121">フォルダーの作成</span><span class="sxs-lookup"><span data-stu-id="4f69c-121">Creating a Folder</span></span>  
 <span data-ttu-id="4f69c-122">プログラムによりストレージ フォルダーを作成するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-122">To create a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="4f69c-123">保存先</span><span class="sxs-lookup"><span data-stu-id="4f69c-123">Storage Location</span></span>|<span data-ttu-id="4f69c-124">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="4f69c-124">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="4f69c-125">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="4f69c-125">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> <span data-ttu-id="4f69c-126">フォルダーの削除</span><span class="sxs-lookup"><span data-stu-id="4f69c-126">Removing a Folder</span></span>  
 <span data-ttu-id="4f69c-127">プログラムによりストレージ フォルダーを削除するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-127">To remove a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="4f69c-128">保存先</span><span class="sxs-lookup"><span data-stu-id="4f69c-128">Storage Location</span></span>|<span data-ttu-id="4f69c-129">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="4f69c-129">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="4f69c-130">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="4f69c-130">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> <span data-ttu-id="4f69c-131">フォルダーの名前変更</span><span class="sxs-lookup"><span data-stu-id="4f69c-131">Renaming a Folder</span></span>  
 <span data-ttu-id="4f69c-132">プログラムによりストレージ フォルダーの名前を変更するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-132">To rename a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="4f69c-133">保存先</span><span class="sxs-lookup"><span data-stu-id="4f69c-133">Storage Location</span></span>|<span data-ttu-id="4f69c-134">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="4f69c-134">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="4f69c-135">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="4f69c-135">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
<span data-ttu-id="4f69c-136">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="4f69c-136">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4f69c-137">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f69c-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4f69c-138">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="4f69c-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4f69c-139">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="4f69c-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f69c-140">参照</span><span class="sxs-lookup"><span data-stu-id="4f69c-140">See Also</span></span>  
 <span data-ttu-id="4f69c-141">[SSIS サービス&#41;の Package Management &#40;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="4f69c-141">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="4f69c-142">プログラムによる使用可能なパッケージの列挙</span><span class="sxs-lookup"><span data-stu-id="4f69c-142">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
