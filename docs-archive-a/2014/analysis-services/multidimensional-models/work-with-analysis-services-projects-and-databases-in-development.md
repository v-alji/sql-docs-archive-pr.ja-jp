---
title: 開発段階での Analysis Services プロジェクトとデータベースの操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762ea6f33a94f65e7dd6895cd038d4a52d40d43e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641312"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a><span data-ttu-id="60331-102">開発段階における Analysis Services プロジェクトおよびデータベースの操作</span><span class="sxs-lookup"><span data-stu-id="60331-102">Working with Analysis Services Projects and Databases During the Development Phase</span></span>
  <span data-ttu-id="60331-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] をプロジェクト モードまたはオンライン モードで使用すると、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースを開発できます。</span><span class="sxs-lookup"><span data-stu-id="60331-103">You can develop an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode.</span></span>  
  
## <a name="single-developer"></a><span data-ttu-id="60331-104">開発者が 1 人の場合</span><span class="sxs-lookup"><span data-stu-id="60331-104">Single Developer</span></span>  
 <span data-ttu-id="60331-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース全体とそれを構成するすべてのオブジェクトを 1 人の開発者が開発する場合、この開発者はビジネス インテリジェンス ソリューションのライフサイクル中はいつでも、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をプロジェクト モードまたはオンライン モードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="60331-105">When only a single developer is developing the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and all of its constituent objects, the developer can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode at any time during the lifecycle of the business intelligence solution.</span></span> <span data-ttu-id="60331-106">開発者が 1 人しかいない場合、どのモードを選択するかは特に重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="60331-106">In the case of a single developer, the choice of modes is not particularly critical.</span></span> <span data-ttu-id="60331-107">オフライン プロジェクト ファイルの管理をソース管理システムと統合すると、アーカイブやロールバックなどのメリットが多数あります。</span><span class="sxs-lookup"><span data-stu-id="60331-107">The maintenance of an offline project file integrated with a source control system has many benefits, such as archiving and rollback.</span></span> <span data-ttu-id="60331-108">ただし、開発者が 1 人の場合は、変更内容を他の開発者に伝達する際の問題が生じません。</span><span class="sxs-lookup"><span data-stu-id="60331-108">However, with a single developer you will not have the problem of communicating changes with another developer.</span></span>  
  
## <a name="multiple-developers"></a><span data-ttu-id="60331-109">開発者が複数いる場合</span><span class="sxs-lookup"><span data-stu-id="60331-109">Multiple Developers</span></span>  
 <span data-ttu-id="60331-110">同じビジネス インテリジェンス ソリューションに複数の開発者が取り組んでいる場合は、開発者がほとんどすべての状況においてプロジェクト モードでソース管理を行わないと、問題が生じます。</span><span class="sxs-lookup"><span data-stu-id="60331-110">When multiple developers are working on a business intelligence solution, problems will arise if the developers do not work in project mode with source control under most, if not all circumstances.</span></span> <span data-ttu-id="60331-111">ソース管理を行うと、2 人の開発者によって同じオブジェクトに同時に変更が加えられるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="60331-111">Source control ensures that two developers are not making changes to the same object at the same time.</span></span>  
  
 <span data-ttu-id="60331-112">たとえば、ある開発者がプロジェクト モードで作業し、特定のオブジェクトに変更を加えています。</span><span class="sxs-lookup"><span data-stu-id="60331-112">For example, suppose a developer is working in project mode and making changes to selected objects.</span></span> <span data-ttu-id="60331-113">この開発者が変更を加えている間に、配置済みのデータベースが別の開発者によってオンライン モードで変更されたとします。</span><span class="sxs-lookup"><span data-stu-id="60331-113">While the developer is making these changes, suppose that another developer makes a change to the deployed database in online mode.</span></span> <span data-ttu-id="60331-114">この場合は、最初の開発者が変更後の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置しようとすると問題が生じます。</span><span class="sxs-lookup"><span data-stu-id="60331-114">A problem will arise when the first developer attempts to deploy his or her modified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="60331-115">つまり、配置済みデータベース内でオブジェクトが変更されたことが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって検出され、データベース全体を上書きして、2 番目の開発者が加えた変更を上書きするように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="60331-115">Namely, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] will detect that objects have changed within the deployed database and prompt the developer to overwrite the entire database, overwriting the changes of the second developer.</span></span> <span data-ttu-id="60331-116">ただし、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース インスタンスと上書き対象プロジェクト内のオブジェクトとの間で変更内容を解決する機能が用意されていません。したがって、最初の開発者に残された選択肢は、自分が加えた変更をすべて破棄し、最新バージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに基づいて新規のプロジェクトを作成し直すことだけです。</span><span class="sxs-lookup"><span data-stu-id="60331-116">Since [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] has no means of resolving the changes between the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database instance and the objects in the project about to be overwritten, the only real choice the first developer has is to discard all of his or her changes and starting anew from a new project based on the current version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
  
