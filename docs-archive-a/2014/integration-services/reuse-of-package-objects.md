---
title: パッケージ オブジェクトの再利用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b7612cb2684bb842108068b062e54fbe9dee4327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713266"
---
# <a name="reuse-of-package-objects"></a><span data-ttu-id="6d08d-102">パッケージ オブジェクトの再利用</span><span class="sxs-lookup"><span data-stu-id="6d08d-102">Reuse of Package Objects</span></span>
  <span data-ttu-id="6d08d-103">多くの場合、パッケージには、再利用できるような機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6d08d-103">Frequently packages functionality that you want to reuse.</span></span> <span data-ttu-id="6d08d-104">たとえば、一連のタスクを作成した場合、それらのアイテムを合わせてグループとして再利用したり、別の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトで作成した接続マネージャーのように、1 つのアイテムを再利用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6d08d-104">For example, if you created a set of tasks, you might want to reuse the items together as a group, or you might want to reuse a single item such as a connection manager that you created in a different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
## <a name="copy-and-paste"></a><span data-ttu-id="6d08d-105">コピーと貼り付け</span><span class="sxs-lookup"><span data-stu-id="6d08d-105">Copy and Paste</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="6d08d-106">と [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでは、制御フロー アイテム、データ フロー アイテム、接続マネージャーなど、パッケージ オブジェクトのコピーと貼り付けがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6d08d-106">and [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer support copying and pasting package objects, which can include control flow items, data flow items, and connection managers.</span></span> <span data-ttu-id="6d08d-107">コピーと貼り付けは、プロジェクト間およびパッケージ間で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d08d-107">You can copy and paste between projects and between packages.</span></span> <span data-ttu-id="6d08d-108">複数のプロジェクトがソリューションに含まれている場合、プロジェクト間でコピーを実行でき、それらのプロジェクトの種類は異なってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="6d08d-108">If the solution contains multiple projects you can copy between projects, and the projects can be of different types.</span></span>  
  
 <span data-ttu-id="6d08d-109">1 つのソリューションに複数のパッケージが含まれている場合、それらのパッケージ間でコピーと貼り付けを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d08d-109">If a solution contains multiple packages, you can copy and paste between them.</span></span> <span data-ttu-id="6d08d-110">パッケージは、同じ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトに含まれていても、異なる Integration Services プロジェクトに含まれていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="6d08d-110">The packages can be in the same or different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="6d08d-111">ただし、パッケージ オブジェクトは他のオブジェクトに依存し、その依存関係がなければ成立しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d08d-111">However, package objects may have dependencies on other objects, without which they are not valid.</span></span> <span data-ttu-id="6d08d-112">たとえば、SQL 実行タスクは接続マネージャーを使用します。タスクを正しく機能させるには、この接続マネージャーもコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d08d-112">For example, an Execute SQL task uses a connection manager, which you must copy as well to make the task work.</span></span> <span data-ttu-id="6d08d-113">また、パッケージ オブジェクトによっては、特定のオブジェクトが既にパッケージに含まれている必要があるものもあります。このオブジェクトがなければ、コピーしたオブジェクトをパッケージに正常に貼り付けることができません。</span><span class="sxs-lookup"><span data-stu-id="6d08d-113">Also, some package objects require that the package already contain a certain object, and without this object you cannot successfully paste the copied objects into a package.</span></span> <span data-ttu-id="6d08d-114">たとえば、1 つもデータ フロー タスクを含まないパッケージには、データ フローを貼り付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="6d08d-114">For example, you cannot paste a data flow into a package that does not have at least one Data Flow task.</span></span>  
  
 <span data-ttu-id="6d08d-115">同じパッケージを何度もコピーして使用する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6d08d-115">You may find that you copy the same packages repeatedly.</span></span> <span data-ttu-id="6d08d-116">このようなコピー プロセスを回避するには、そのパッケージをテンプレートとして指定すれば、新しいパッケージを作成するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d08d-116">To avoid the copy process, you can designate these packages as templates and use them when you create new packages.</span></span>  
  
 <span data-ttu-id="6d08d-117">パッケージ オブジェクトをコピーすると、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] により、新しい GUID が新しいオブジェクトの `ID` プロパティに自動的に割り当てられ、`Name` プロパティが自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="6d08d-117">When you copy a package object, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatically assigns a new GUID to the `ID` property of the new object and updates the `Name` property.</span></span>  
  
 <span data-ttu-id="6d08d-118">変数はコピーできません。</span><span class="sxs-lookup"><span data-stu-id="6d08d-118">You cannot copy variables.</span></span> <span data-ttu-id="6d08d-119">タスクなどのオブジェクトで変数が使用される場合は、コピー先のパッケージにその変数を再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d08d-119">If an object such as a task uses variables, then you must re-create the variables in the destination package.</span></span> <span data-ttu-id="6d08d-120">これに対して、パッケージ全体をコピーした場合は、パッケージの変数もコピーされます。</span><span class="sxs-lookup"><span data-stu-id="6d08d-120">In contrast, if you copy the entire package, then the variables in the package are also copied.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6d08d-121">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6d08d-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="6d08d-122">パッケージ オブジェクトをコピーする</span><span class="sxs-lookup"><span data-stu-id="6d08d-122">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
-   [<span data-ttu-id="6d08d-123">プロジェクト アイテムをコピーする</span><span class="sxs-lookup"><span data-stu-id="6d08d-123">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
-   [<span data-ttu-id="6d08d-124">パッケージをパッケージ テンプレートとして保存する</span><span class="sxs-lookup"><span data-stu-id="6d08d-124">Save a Package as a Package Template</span></span>](../../2014/integration-services/save-a-package-as-a-package-template.md)  
  
  
