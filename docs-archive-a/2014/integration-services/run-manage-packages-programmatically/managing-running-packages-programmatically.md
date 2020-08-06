---
title: プログラムによるパッケージの実行の管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95c5f9c28b407631764d64523b37a6295870542a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740140"
---
# <a name="managing-running-packages-programmatically"></a><span data-ttu-id="64f5f-102">プログラムによるパッケージの実行の管理</span><span class="sxs-lookup"><span data-stu-id="64f5f-102">Managing Running Packages Programmatically</span></span>
  <span data-ttu-id="64f5f-103">プログラムによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを操作する際に、現在実行中のパッケージを特定することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="64f5f-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which packages are currently running.</span></span> <span data-ttu-id="64f5f-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすメソッドとクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="64f5f-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides methods and classes to satisfy these requirements.</span></span>  
  
 <span data-ttu-id="64f5f-105">パッケージの監視の詳細については、「[パッケージの管理 &#40;SSIS サービス&#41;](../service/package-management-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f5f-105">For more information about monitoring packages, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="64f5f-106">このトピックで説明するすべてのメソッドには、`Microsoft.SqlServer.ManagedDTS` アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="64f5f-106">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="64f5f-107">新しいプロジェクトに参照を追加した後、 <xref:Microsoft.SqlServer.Dts.Runtime> またはステートメントを使用して名前空間をインポートし `using` `Imports` ます。</span><span class="sxs-lookup"><span data-stu-id="64f5f-107">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64f5f-108">SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドでは、"."、localhost、またはローカル サーバーのサーバー名のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="64f5f-108">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="64f5f-109">"(local)" は使用できません。</span><span class="sxs-lookup"><span data-stu-id="64f5f-109">You cannot use "(local)".</span></span>  
  
## <a name="determining-which-packages-are-currently-running"></a><span data-ttu-id="64f5f-110">現在実行中のパッケージの特定</span><span class="sxs-lookup"><span data-stu-id="64f5f-110">Determining Which Packages Are Currently Running</span></span>  
 <span data-ttu-id="64f5f-111">特定のサーバーでどのパッケージが現在実行されているかを調べるには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="64f5f-111">To determine which packages are currently running on the specified server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> method.</span></span> <span data-ttu-id="64f5f-112">このメソッドは、<xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> コレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="64f5f-112">This method returns a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection of <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64f5f-113">管理者に対しては、現在コンピューターで実行されているすべてのパッケージが表示されます。他のユーザーに対しては、自分が起動したパッケージのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64f5f-113">Administrators see all packages that are currently executing on the computer; other users see only those packages that they have launched.</span></span>  
  
## <a name="working-with-running-packages"></a><span data-ttu-id="64f5f-114">実行中のパッケージの操作</span><span class="sxs-lookup"><span data-stu-id="64f5f-114">Working with Running Packages</span></span>  
 <span data-ttu-id="64f5f-115">現在実行中のパッケージを特定した後、そのパッケージの情報を取得したり、パッケージの停止を要求することができます。</span><span class="sxs-lookup"><span data-stu-id="64f5f-115">After you have determined which packages are currently running, you can retrieve information about the packages and request that a package be stopped.</span></span>  
  
### <a name="getting-information-about-a-running-package"></a><span data-ttu-id="64f5f-116">実行中のパッケージの情報の取得</span><span class="sxs-lookup"><span data-stu-id="64f5f-116">Getting Information about a Running Package</span></span>  
 <span data-ttu-id="64f5f-117"><xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> コレクションを反復処理するときに、<xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> オブジェクトのプロパティを使用して、パッケージを探したり、実行中のパッケージに関する追加情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="64f5f-117">As you iterate through the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection, you can use the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to locate a package or to obtain additional information about the packages that are running:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a><span data-ttu-id="64f5f-118">実行中のパッケージの停止</span><span class="sxs-lookup"><span data-stu-id="64f5f-118">Stopping a Running Package</span></span>  
 <span data-ttu-id="64f5f-119"><xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> メソッドを呼び出して、そのパッケージを停止するように要求できます。</span><span class="sxs-lookup"><span data-stu-id="64f5f-119">You can call the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to request that the package be stopped.</span></span> <span data-ttu-id="64f5f-120">停止要求が発行されてからパッケージが実際に停止するまでの間に遅延が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="64f5f-120">There may be a delay between the time that a stop request is issued and the time that the package actually stops.</span></span>  
  
<span data-ttu-id="64f5f-121">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="64f5f-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="64f5f-122">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f5f-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="64f5f-123">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="64f5f-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="64f5f-124">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="64f5f-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f5f-125">参照</span><span class="sxs-lookup"><span data-stu-id="64f5f-125">See Also</span></span>  
 <span data-ttu-id="64f5f-126">[SSIS サービス&#41;の Package Management &#40;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="64f5f-126">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="64f5f-127">プログラムによる使用可能なパッケージの列挙</span><span class="sxs-lookup"><span data-stu-id="64f5f-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
