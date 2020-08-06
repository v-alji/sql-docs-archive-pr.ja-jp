---
title: ソリューションとプロジェクトをソース管理に追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], source controls
- solutions [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], solutions
- source controls [SQL Server Management Studio], projects
ms.assetid: 3eaed80e-6f55-42ea-a964-aca31c09d055
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5256795677f4e8ce4249737d25d3ded1c4cd69c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714590"
---
# <a name="add-solutions-and-projects-to-source-control"></a><span data-ttu-id="63ec6-102">ソース管理へのソリューションとプロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="63ec6-102">Add Solutions and Projects to Source Control</span></span>
  <span data-ttu-id="63ec6-103">ソース管理にソリューションを追加すると、そのソリューションは動的バージョン管理アーカイブに組み込まれます。動的バージョン管理アーカイブの作成と保守には、ソース管理プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="63ec6-103">When you add a solution to source control, the solution becomes part of a dynamic versioning archive created and maintained by the source control provider.</span></span> <span data-ttu-id="63ec6-104">だれかが新しいバージョンのソリューションをチェックインすると、そのバージョンがアーカイブに組み込まれ、他のソース管理ユーザーからの利用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="63ec6-104">Each time someone checks in a new version of the solution, that version becomes part of the archive and is available to other source control users.</span></span>  
  
 <span data-ttu-id="63ec6-105">ソース管理にソリューションを追加すると、ファイル管理システムを集中化することにもなります。</span><span class="sxs-lookup"><span data-stu-id="63ec6-105">Adding a solution to source control also starts a system of centralized file management.</span></span> <span data-ttu-id="63ec6-106">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe などのソース管理プロバイダーがソース管理の対象項目に対するアクセスを制御するので、ソース管理クライアントは、ファイルをチェックアウトしない限り、ソース管理の対象ファイルへの書き込みを行えなくなります。</span><span class="sxs-lookup"><span data-stu-id="63ec6-106">Source control providers, such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, control access to source-controlled items; source control clients cannot write to local copies of source-controlled files without checking them out.</span></span>  
  
 <span data-ttu-id="63ec6-107">このトピックでは、次の内容について紹介します。</span><span class="sxs-lookup"><span data-stu-id="63ec6-107">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="63ec6-108">トピック</span><span class="sxs-lookup"><span data-stu-id="63ec6-108">Topic</span></span>|<span data-ttu-id="63ec6-109">説明</span><span class="sxs-lookup"><span data-stu-id="63ec6-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="63ec6-110">ソース管理へのソリューションの追加</span><span class="sxs-lookup"><span data-stu-id="63ec6-110">Add Solutions to Source Control</span></span>](../../2014/database-engine/add-solutions-to-source-control.md)|<span data-ttu-id="63ec6-111">追加できるプロジェクトの種類を示し、ソース管理にソリューションを追加するための手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="63ec6-111">Describes the project types you can add, and provides instructions on how to add a solution to source control.</span></span>|  
|[<span data-ttu-id="63ec6-112">ソース管理へのプロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="63ec6-112">Add Projects to Source Control</span></span>](../../2014/database-engine/add-projects-to-source-control.md)|<span data-ttu-id="63ec6-113">ソリューションにプロジェクトを追加するための手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="63ec6-113">Provides instructions on how to add a project to a solution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63ec6-114">参照</span><span class="sxs-lookup"><span data-stu-id="63ec6-114">See Also</span></span>  
 [<span data-ttu-id="63ec6-115">ソース管理からソリューションやプロジェクトを開く方法</span><span class="sxs-lookup"><span data-stu-id="63ec6-115">Open Solutions and Projects from Source Control</span></span>](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)  
  
  
