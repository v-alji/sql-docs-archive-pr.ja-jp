---
title: SSIS パッケージの要点 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c58ddc13b5c149b84fa550f312782b02786d062
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718512"
---
# <a name="ssis-package-essentials"></a><span data-ttu-id="afc76-102">SSIS パッケージの基本事項</span><span class="sxs-lookup"><span data-stu-id="afc76-102">SSIS Package Essentials</span></span>
  <span data-ttu-id="afc76-103">パッケージは、データの抽出、変換、および読み込みを行うための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 機能が実装されているオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="afc76-103">A package is the object that implements [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] functionality to extract, transform, and load data.</span></span> <span data-ttu-id="afc76-104">パッケージは [!INCLUDE[ssIS](../includes/ssis-md.md)] で [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]デザイナーを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="afc76-104">You create a package by using the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="afc76-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザード、または [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 接続プロジェクト ウィザードを使用してもパッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="afc76-105">You can also create a package by running the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard or the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Connections Project Wizard.</span></span> <span data-ttu-id="afc76-106">詳細については、「SSIS デザイナーおよびプロジェクトの[インポートウィザード](../../2014/integration-services/import-project-wizard.md)で[SQL Server Data Tools でパッケージを作成する](create-packages-in-sql-server-data-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afc76-106">For more information, [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) in SSIS Designer and [Import Project Wizard](../../2014/integration-services/import-project-wizard.md).</span></span>  
  
 <span data-ttu-id="afc76-107">基本的なパッケージには次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="afc76-107">A basic package includes the following elements:</span></span>  
  
 <span data-ttu-id="afc76-108">**制御フロー要素**</span><span class="sxs-lookup"><span data-stu-id="afc76-108">**Control flow elements**</span></span>  
 <span data-ttu-id="afc76-109">制御フロー要素は必須要素で、さまざまな関数を実行し、構造を提供し、要素が実行される順序を制御します。</span><span class="sxs-lookup"><span data-stu-id="afc76-109">These required elements perform various functions, provide structure, and control the order in which elements run.</span></span> <span data-ttu-id="afc76-110">主な制御フロー要素は、タスク、コンテナー、および優先順位制約です。</span><span class="sxs-lookup"><span data-stu-id="afc76-110">The main control flow elements are tasks, containers, and precedence constraints.</span></span> <span data-ttu-id="afc76-111">パッケージには、制御フロー要素が少なくとも 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="afc76-111">There must be at least one control flow element in a package.</span></span>  
  
 <span data-ttu-id="afc76-112">詳細については、「 [Control Flow](control-flow/control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afc76-112">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="afc76-113">**データ フロー要素**</span><span class="sxs-lookup"><span data-stu-id="afc76-113">**Data flow elements**</span></span>  
 <span data-ttu-id="afc76-114">データ フロー要素は省略可能な要素で、データの抽出、変更、およびデータ ソースへの読み込みを行います。</span><span class="sxs-lookup"><span data-stu-id="afc76-114">These optional elements extract data, modify data, and load data into data sources.</span></span> <span data-ttu-id="afc76-115">主なデータ フロー要素は、変換元、変換、および変換先です。</span><span class="sxs-lookup"><span data-stu-id="afc76-115">The main data flow elements are sources, transformations, and destinations.</span></span> <span data-ttu-id="afc76-116">データ フロー要素はパッケージに含まれていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="afc76-116">There does not have to be any data flow elements in package.</span></span>  
  
 <span data-ttu-id="afc76-117">詳細については、「 [Data Flow](data-flow/data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afc76-117">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>  
  
 <span data-ttu-id="afc76-118">基本的なパッケージを作成する方法の例については、「[レッスン 1: プロジェクトと基本パッケージの作成](lesson-1-create-a-project-and-basic-package-with-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afc76-118">For an example of how to create a basic package, see [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="afc76-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="afc76-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="afc76-120">SQL Server データ ツールでのパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="afc76-120">Create Packages in SQL Server Data Tools</span></span>](create-packages-in-sql-server-data-tools.md)  
  
-   [<span data-ttu-id="afc76-121">制御フローのタスクまたはコンテナーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="afc76-121">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [<span data-ttu-id="afc76-122">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="afc76-122">Set the Properties of a Task or Container</span></span>](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [<span data-ttu-id="afc76-123">データ フローでコンポーネントを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="afc76-123">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a><span data-ttu-id="afc76-124">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="afc76-124">Related Content</span></span>  
  
1.  <span data-ttu-id="afc76-125">MSDN.Microsoft.com のビデオ「 [基本パッケージの作成 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=131023)」</span><span class="sxs-lookup"><span data-stu-id="afc76-125">Video, [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023), on MSDN.Microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc76-126">参照</span><span class="sxs-lookup"><span data-stu-id="afc76-126">See Also</span></span>  
 <span data-ttu-id="afc76-127">[SSIS&#41; パッケージ &#40;Integration Services](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="afc76-127">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="afc76-128">優先順位制約</span><span class="sxs-lookup"><span data-stu-id="afc76-128">Precedence Constraints</span></span>](control-flow/precedence-constraints.md)  
  
  
