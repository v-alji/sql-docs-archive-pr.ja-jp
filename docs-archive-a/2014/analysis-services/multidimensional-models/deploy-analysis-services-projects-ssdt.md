---
title: Analysis Services プロジェクトの配置 (SSDT) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5317eea19d088a8d3f9d8bfb86da4e0429d62c3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641344"
---
# <a name="deploy-analysis-services-projects-ssdt"></a><span data-ttu-id="17a29-102">Analysis Services プロジェクトの配置 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="17a29-102">Deploy Analysis Services Projects (SSDT)</span></span>
  <span data-ttu-id="17a29-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトを開発するにあたっては、プロジェクトによって定義された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを作成するために、プロジェクトを開発サーバーに配置することが頻繁に行われます。</span><span class="sxs-lookup"><span data-stu-id="17a29-103">During development of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you frequently deploy the project to a development server in order to create the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database defined by the project.</span></span> <span data-ttu-id="17a29-104">このことは、キューブ内のセルの参照、ディメンション メンバーの参照、主要業績評価指標 (KPI) 式の検証など、プロジェクトをテストする際に必要となります。</span><span class="sxs-lookup"><span data-stu-id="17a29-104">This is required to test the project; for example, to browse cells in the cube, browse dimension members, or verify key performance indicators (KPIs) formulas.</span></span>  
  
## <a name="deploying-a-project"></a><span data-ttu-id="17a29-105">プロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="17a29-105">Deploying a Project</span></span>  
 <span data-ttu-id="17a29-106">プロジェクトは個別に配置することも、ソリューション内のプロジェクトをすべてまとめて配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="17a29-106">You can deploy a project independently, or you can deploy all of the projects within the solution.</span></span> <span data-ttu-id="17a29-107">プロジェクトを配置すると、いくつかの処理が連続して行われます。</span><span class="sxs-lookup"><span data-stu-id="17a29-107">When you deploy a project, several things happen in sequence.</span></span> <span data-ttu-id="17a29-108">まず、プロジェクトが構築されます。</span><span class="sxs-lookup"><span data-stu-id="17a29-108">First, the project is built.</span></span> <span data-ttu-id="17a29-109">この段階では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースとそれを構成するオブジェクトを定義した出力ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="17a29-109">This step creates the output files that define the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and its constituent objects.</span></span> <span data-ttu-id="17a29-110">次に、配置先サーバーが検証されます。</span><span class="sxs-lookup"><span data-stu-id="17a29-110">Next, the destination server is validated.</span></span> <span data-ttu-id="17a29-111">最後に、配置先データベースとそのオブジェクトが配置先サーバーで作成されます。</span><span class="sxs-lookup"><span data-stu-id="17a29-111">Finally, the destination database and its objects are created on the destination server.</span></span> <span data-ttu-id="17a29-112">配置が行われると、プロジェクトのコンテンツが前の展開時にプロジェクトによって作成されたものでない限り、配置エンジンによって既存のデータベースがこれらのオブジェクトで完全に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="17a29-112">During deployment, the deployment engine totally replaces any pre-existing database with the contents of the project unless those objects were created by the project during a previous deployment.</span></span>  
  
 <span data-ttu-id="17a29-113">初期デプロイの後、\ obj フォルダーに IncrementalSnapshot.xml ファイルが生成され \<Project Name> ます。</span><span class="sxs-lookup"><span data-stu-id="17a29-113">After an initial deployment, an IncrementalSnapshot.xml file is generated in the \<Project Name>\obj folder.</span></span> <span data-ttu-id="17a29-114">このファイルは、配置先サーバーのデータベースまたはそのオブジェクトがプロジェクトの外部で変更されたかどうかを判断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="17a29-114">This file is used to determine if the database or its objects on the destination server have changed outside of the project.</span></span> <span data-ttu-id="17a29-115">変更されている場合は、配置先データベースのすべてのオブジェクトを上書きするように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17a29-115">If so, you will be prompted to overwrite all objects in the destination database.</span></span> <span data-ttu-id="17a29-116">すべての変更がプロジェクト内で行われたものであり、プロジェクトが増分配置用に構成されている場合は、変更内容だけが配置先サーバーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="17a29-116">If all changes were made within the project and the project is configured for incremental deployment, only the changes will be deployed to the destination server.</span></span>  
  
 <span data-ttu-id="17a29-117">プロジェクトの配置に使用される配置プロパティは、プロジェクト構成とそれに関連付けられた設定によって決められます。</span><span class="sxs-lookup"><span data-stu-id="17a29-117">The project configuration and its associated settings determine the deployment properties that will be used to deploy the project.</span></span> <span data-ttu-id="17a29-118">共有プロジェクトの場合、各開発者は独自の構成とプロジェクト構成オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="17a29-118">For a shared project, each developer can use their own configuration with their own project configuration options.</span></span> <span data-ttu-id="17a29-119">たとえば、各開発者が別々のテスト サーバーを指定することによって、他の開発者から分離された環境で作業することができます。</span><span class="sxs-lookup"><span data-stu-id="17a29-119">For example, each developer can specify a different test server to work in isolation from other developers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a29-120">参照</span><span class="sxs-lookup"><span data-stu-id="17a29-120">See Also</span></span>  
 [<span data-ttu-id="17a29-121">Analysis Services プロジェクトの作成 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="17a29-121">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](create-an-analysis-services-project-ssdt.md)  
  
  
