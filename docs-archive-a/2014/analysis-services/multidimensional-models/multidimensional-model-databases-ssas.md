---
title: 多次元モデルデータベース (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8dc4e7c872f87244e8353c80bd9acfcce584c167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641888"
---
# <a name="multidimensional-model-databases-ssas"></a><span data-ttu-id="abab7-102">多次元モデル データベース (SSAS)</span><span class="sxs-lookup"><span data-stu-id="abab7-102">Multidimensional Model Databases (SSAS)</span></span>
  <span data-ttu-id="abab7-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースは、データ ソース、データ ソース ビュー、キューブ、ディメンション、およびロールのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="abab7-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is a collection of data sources, data source views, cubes, dimensions, and roles.</span></span> <span data-ttu-id="abab7-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースには、データ マイニング用の構造、およびユーザー定義の関数をデータベースに追加するために使用されるカスタム アセンブリをオプションで含めることができます。</span><span class="sxs-lookup"><span data-stu-id="abab7-104">Optionally, an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can include structures for data mining, and custom assemblies that provide a way for you to add user-defined functions to the database.</span></span>  
  
 <span data-ttu-id="abab7-105">キューブは、Analysis Services における基本的なクエリ オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="abab7-105">Cubes are the fundamental query objects in Analysis Services.</span></span> <span data-ttu-id="abab7-106">クライアント アプリケーション経由で Analysis Services データベースに接続する場合は、そのデータベース内のキューブに接続します。</span><span class="sxs-lookup"><span data-stu-id="abab7-106">When you connect to an Analysis Services database via a client application, you connect to a cube within that database.</span></span> <span data-ttu-id="abab7-107">ディメンション、アセンブリ、ロール、またはマイニング構造を複数のコンテキストにわたって再利用している場合、データベースには複数のキューブが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="abab7-107">A database might contain multiple cubes if you are reusing dimensions, assemblies, roles, or mining structures across multiple contexts.</span></span>  
  
 <span data-ttu-id="abab7-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの作成と変更は、プログラムを使用して行うか、次のいずれかの対話的な方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="abab7-108">You can create and modify a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database programmatically or by using one of these interactive methods:</span></span>  
  
-   <span data-ttu-id="abab7-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] から [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトを、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに配置します。</span><span class="sxs-lookup"><span data-stu-id="abab7-109">Deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to a designated instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="abab7-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースは、その名前が付いたデータベースがそのインスタンス内に存在しない場合にこのプロセスによって作成されます。さらに、新しく作成されたデータベース内に、指定されたオブジェクトがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="abab7-110">This process creates an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, if a database with that name does not already exist within that instance, and instantiates the designed objects within the newly created database.</span></span> <span data-ttu-id="abab7-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]データベースを使用する場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのオブジェクトに加えた変更は、プロジェクトが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置されたときにのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="abab7-111">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], changes made to objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project take effect only when the project is deployed to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="abab7-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス内に空の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースを作成します。これを行うには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のどちらかを使用します。次に、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用してデータベースに直接接続し、プロジェクト内ではなくこのデータベース内にオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="abab7-112">Create an empty [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then connect directly to that database using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create objects within it (rather than within a project).</span></span> <span data-ttu-id="abab7-113">この方法で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを使用するときは、オブジェクトに加えた変更は、変更したオブジェクトの保存時に接続しているデータベースで有効になります。</span><span class="sxs-lookup"><span data-stu-id="abab7-113">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in this manner, changes made to objects take effect in the database to which you are connecting when the changed object is saved.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="abab7-114">では、ソース管理ソフトウェアの統合を使用し、開発者が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内で同時に異なるオブジェクトを処理するのをサポートします。</span><span class="sxs-lookup"><span data-stu-id="abab7-114">uses integration with source control software to support multiple developers working with different objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project at the same time.</span></span> <span data-ttu-id="abab7-115">また、開発者は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト経由ではなく、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースと直接やり取りを行うことができますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのオブジェクトが、配置のために使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトと同期しなくなるリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="abab7-115">A developer can also interact with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database directly, rather than through an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, but the risk of this is that the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span> <span data-ttu-id="abab7-116">配置後、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースを管理します。</span><span class="sxs-lookup"><span data-stu-id="abab7-116">After deployment, you administer an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="abab7-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して、パーティションやロールなど、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースに一定の変更を加えることもできます。これにより、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのオブジェクトが、この配置のために使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトと同期しなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="abab7-117">Certain changes can also be made to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as to partitions and roles, which can also cause the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="abab7-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="abab7-118">Related Tasks</span></span>  
 [<span data-ttu-id="abab7-119">Analysis Services データベースのインポートとデタッチ</span><span class="sxs-lookup"><span data-stu-id="abab7-119">Attach and Detach Analysis Services Databases</span></span>](attach-and-detach-analysis-services-databases.md)  
  
 [<span data-ttu-id="abab7-120">Analysis Services データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="abab7-120">Backup and Restore of Analysis Services Databases</span></span>](backup-and-restore-of-analysis-services-databases.md)  
  
 [<span data-ttu-id="abab7-121">Analysis Services データベースのドキュメントとスクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="abab7-121">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
 [<span data-ttu-id="abab7-122">Analysis Services データベースの変更または削除</span><span class="sxs-lookup"><span data-stu-id="abab7-122">Modify or Delete an Analysis Services Database</span></span>](modify-or-delete-an-analysis-services-database.md)  
  
 [<span data-ttu-id="abab7-123">Analysis Services データベースの移動</span><span class="sxs-lookup"><span data-stu-id="abab7-123">Move an Analysis Services Database</span></span>](move-an-analysis-services-database.md)  
  
 [<span data-ttu-id="abab7-124">多次元データベース名の変更 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="abab7-124">Rename a Multidimensional Database &#40;Analysis Services&#41;</span></span>](rename-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="abab7-125">多次元データベースの互換性レベルを設定する &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="abab7-125">Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;</span></span>](compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="abab7-126">多次元データベースのプロパティ設定 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="abab7-126">Set Multidimensional Database Properties &#40;Analysis Services&#41;</span></span>](set-multidimensional-database-properties-analysis-services.md)  
  
 [<span data-ttu-id="abab7-127">Analysis Services データベースの同期</span><span class="sxs-lookup"><span data-stu-id="abab7-127">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
 [<span data-ttu-id="abab7-128">Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え</span><span class="sxs-lookup"><span data-stu-id="abab7-128">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a><span data-ttu-id="abab7-129">参照</span><span class="sxs-lookup"><span data-stu-id="abab7-129">See Also</span></span>  
 <span data-ttu-id="abab7-130">[Analysis Services データベースへのオンラインモードでの接続](connect-in-online-mode-to-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="abab7-130">[Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="abab7-131">[SSDT&#41;&#40;Analysis Services プロジェクトを作成する](create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="abab7-131">[Create an Analysis Services Project &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md) </span></span>  
 [<span data-ttu-id="abab7-132">MDX による多次元データのクエリ</span><span class="sxs-lookup"><span data-stu-id="abab7-132">Querying Multidimensional Data with MDX</span></span>](mdx/querying-multidimensional-data-with-mdx.md)  
  
  
