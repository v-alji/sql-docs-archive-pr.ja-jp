---
title: Integration Services (SSIS) Server |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0da83cdac269499dfbde7a6387a4af4690c83ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642247"
---
# <a name="integration-services-ssis-server"></a><span data-ttu-id="9b320-102">Integration Services (SSIS) サーバー</span><span class="sxs-lookup"><span data-stu-id="9b320-102">Integration Services (SSIS) Server</span></span>
  <span data-ttu-id="9b320-103">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でパッケージをデザインしてテストしたら、パッケージを含むプロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置できます。</span><span class="sxs-lookup"><span data-stu-id="9b320-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="9b320-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーは、`SSISDB` データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="9b320-104">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database.</span></span> <span data-ttu-id="9b320-105">データベースには、パッケージ、プロジェクト、パラメーター、権限、サーバーのプロパティ、および運用履歴というオブジェクトが格納されます。</span><span class="sxs-lookup"><span data-stu-id="9b320-105">The database stores the following objects: packages, projects, parameters, permissions, server properties, and operational history.</span></span>  
  
 <span data-ttu-id="9b320-106">`SSISDB` データベース内のオブジェクト情報は、パブリック ビューに対してクエリを実行することで公開されます。</span><span class="sxs-lookup"><span data-stu-id="9b320-106">The `SSISDB` database exposes the object information in public views that you can query.</span></span> <span data-ttu-id="9b320-107">また、データベースには、オブジェクトを管理するために呼び出すことができるストアド プロシージャも用意されています。</span><span class="sxs-lookup"><span data-stu-id="9b320-107">The database also provides stored procedures that you can call to manage the objects.</span></span>  
  
 <span data-ttu-id="9b320-108">プロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するには、まず `SSISDB` カタログを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b320-108">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you need to create the `SSISDB` catalog.</span></span>  
  
 <span data-ttu-id="9b320-109">SSISDB カタログの機能の概要については、「[SSIS カタログ](ssis-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b320-109">For an overview of the SSISDB catalog functionality, see [SSIS Catalog](ssis-catalog.md).</span></span>  
  
## <a name="high-availability"></a><span data-ttu-id="9b320-110">高可用性</span><span class="sxs-lookup"><span data-stu-id="9b320-110">High Availability</span></span>  
 <span data-ttu-id="9b320-111">他のユーザー データベースと同様に、`SSISDB` データベースでデータベース ミラーリングとレプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9b320-111">Like other user databases, the `SSISDB` database does support database mirroring and replication.</span></span> <span data-ttu-id="9b320-112">ミラーリングとレプリケーションの詳細については、「[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b320-112">For more information about mirroring and replication, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="9b320-113">SSIS と AlwaysOn 可用性グループを利用して SSISDB とそのコンテンツの高可用性を実現することもできます。</span><span class="sxs-lookup"><span data-stu-id="9b320-113">You can also provide high-availability of SSISDB and its contents by making use of SSIS and AlwaysOn Availability Groups.</span></span> <span data-ttu-id="9b320-114">詳細については、Matt Masson による blogs.msdn.com のブログ記事「 [SSIS と AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b320-114">For more information, see this blog post by Matt Masson, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
##  <a name="integration-services-server-in-sql-server-management-studio"></a><a name="ssms"></a> <span data-ttu-id="9b320-115">SQL Server Management Studio の Integration Services サーバー</span><span class="sxs-lookup"><span data-stu-id="9b320-115">Integration Services Server in SQL Server Management Studio</span></span>  
 <span data-ttu-id="9b320-116">`SSISDB` データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続している場合、オブジェクト エクスプローラーに、次のオブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b320-116">When you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database, you see the following objects in Object Explorer:</span></span>  
  
-   <span data-ttu-id="9b320-117">**SSISDB データベース**</span><span class="sxs-lookup"><span data-stu-id="9b320-117">**SSISDB Database**</span></span>  
  
     <span data-ttu-id="9b320-118">データベースは、 `SSISDB` オブジェクトエクスプローラーの [**データベース**] ノードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b320-118">The `SSISDB` database appears under the **Databases** node in Object Explore.</span></span> <span data-ttu-id="9b320-119">ビューに対してクエリを実行し、ストアド プロシージャを呼び出して、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーとサーバーに格納されているオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="9b320-119">You can query the views and call the stored procedures that manage the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server and the objects that are stored on the server.</span></span>  
  
-   <span data-ttu-id="9b320-120">**統合サービス カタログ**</span><span class="sxs-lookup"><span data-stu-id="9b320-120">**Integration Services Catalogs**</span></span>  
  
     <span data-ttu-id="9b320-121">**[Integration Services カタログ]** ノードには、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトおよび環境のフォルダーが存在します。</span><span class="sxs-lookup"><span data-stu-id="9b320-121">Under the **Integration Services Catalogs** node there are folders for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects and environments.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9b320-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9b320-122">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9b320-123">SSIS カタログの作成</span><span class="sxs-lookup"><span data-stu-id="9b320-123">Create the SSIS Catalog</span></span>](../create-the-ssis-catalog.md)  
  
-   [<span data-ttu-id="9b320-124">Integration Services サーバー上のパッケージの一覧を表示する</span><span class="sxs-lookup"><span data-stu-id="9b320-124">View the List of Packages on the Integration Services Server</span></span>](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [<span data-ttu-id="9b320-125">Integration Services サーバーへのプロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="9b320-125">Deploy Projects to Integration Services Server</span></span>](../deploy-projects-to-integration-services-server.md)  
  
-   [<span data-ttu-id="9b320-126">SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="9b320-126">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="9b320-127">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="9b320-127">Related Content</span></span>  
 <span data-ttu-id="9b320-128">blogs.msdn.com のブログ エントリ「 [SSIS と AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873)」。</span><span class="sxs-lookup"><span data-stu-id="9b320-128">Blog entry, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
  
