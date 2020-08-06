---
title: ソリューション エクスプローラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- solutions [SQL Server Management Studio], about solutions
- SQL Server Management Studio [SQL Server], items
- items [SQL Server]
ms.assetid: 0df09843-0d4f-4925-bc6c-99265035a0c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa312f5e097fa1c59b9ba545709dc964a184c3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634766"
---
# <a name="solution-explorer"></a><span data-ttu-id="42f15-102">ソリューション エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="42f15-102">Solution Explorer</span></span>
  <span data-ttu-id="42f15-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のソリューション エクスプローラー ペインには、データベースのスクリプト、クエリ、データ接続、ファイルなどの項目を管理するための "プロジェクト" と呼ばれるコンテナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="42f15-103">The Solution Explorer pane in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides containers called projects for managing items such as database scripts, queries, data connections, and files.</span></span> <span data-ttu-id="42f15-104">互いに関連する 1 つまたは複数のプロジェクトは、"ソリューション" と呼ばれるコンテナーにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="42f15-104">One or more projects that are related to each other can be combined in a container called a solution.</span></span>  
  
 <span data-ttu-id="42f15-105">ソリューションには、1 つ以上のプロジェクトと、ソリューションを全体として定義するためのファイルおよびメタデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="42f15-105">A solution includes one or more projects, plus files and metadata that help define the solution as a whole.</span></span> <span data-ttu-id="42f15-106">プロジェクトとは、一式のファイルに、接続情報などの関連メタデータを加えたもののことです。</span><span class="sxs-lookup"><span data-stu-id="42f15-106">A project is a set of files, plus related metadata such as connection information.</span></span> <span data-ttu-id="42f15-107">ソリューションおよびプロジェクトには項目が含まれています。項目とは、データベース ソリューションの作成に必要なスクリプト、クエリ、接続情報、およびファイルを表しています。</span><span class="sxs-lookup"><span data-stu-id="42f15-107">Solutions and projects contain items that represent the scripts, queries, connection information and files that you need to create your database solution.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="benefits-of-using-solutions"></a><span data-ttu-id="42f15-108">ソリューションを使用する利点</span><span class="sxs-lookup"><span data-stu-id="42f15-108">Benefits of Using Solutions</span></span>  
 <span data-ttu-id="42f15-109">これらのコンテナーの用途は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="42f15-109">Use these containers to:</span></span>  
  
-   <span data-ttu-id="42f15-110">クエリおよびスクリプトに対するソース管理を実現します。</span><span class="sxs-lookup"><span data-stu-id="42f15-110">Implement source control on queries and scripts.</span></span>  
  
-   <span data-ttu-id="42f15-111">ソリューション全体の設定や個別のプロジェクトの設定を管理します。</span><span class="sxs-lookup"><span data-stu-id="42f15-111">Manage settings for your solution as a whole or for individual projects.</span></span>  
  
-   <span data-ttu-id="42f15-112">データベース ソリューションを構成する項目に注目しながらファイル管理の詳細を扱います。</span><span class="sxs-lookup"><span data-stu-id="42f15-112">Handle the details of file management while you focus on items that make up your database solution.</span></span>  
  
-   <span data-ttu-id="42f15-113">各プロジェクト内の項目を参照することなく、役立つ項目をソリューション内の複数のプロジェクトへ、あるいはソリューションへ追加します。</span><span class="sxs-lookup"><span data-stu-id="42f15-113">Add items that are useful to multiple projects in the solution or to the solution without referencing the item in each project.</span></span>  
  
-   <span data-ttu-id="42f15-114">ソリューションまたはプロジェクトに属さないその他のファイルも作業できます。</span><span class="sxs-lookup"><span data-stu-id="42f15-114">Work on miscellaneous files that are independent from solutions or projects.</span></span>  
  
 <span data-ttu-id="42f15-115">プロジェクトに含まれる項目は、プロジェクトの種類と、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用しているかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="42f15-115">The items contained in projects depend on the project type and whether you are using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="42f15-116">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="42f15-116">Related Tasks</span></span>  
 <span data-ttu-id="42f15-117">SQL Server のソリューションの基礎知識については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="42f15-117">Use the following topics to get started with SQL Server Solutions:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42f15-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="42f15-118">**Description**</span></span>|<span data-ttu-id="42f15-119">**トピック**</span><span class="sxs-lookup"><span data-stu-id="42f15-119">**Topic**</span></span>|  
|<span data-ttu-id="42f15-120">ソリューション内の 1 つまたは複数のプロジェクトを収集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42f15-120">Describes how to collect one or more projects in a solution.</span></span>|[<span data-ttu-id="42f15-121">ソリューション (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="42f15-121">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solutions-sql-server-management-studio.md)|  
|<span data-ttu-id="42f15-122">プロジェクトを作成し、スクリプトや接続などの項目を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42f15-122">Describes how to create a project and add items like scripts and connections.</span></span>|[<span data-ttu-id="42f15-123">プロジェクト (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="42f15-123">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)|  
|<span data-ttu-id="42f15-124">ソリューションまたは個々のプロジェクトをソース コード管理システムに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42f15-124">Describes how to integrate solutions or individual projects into a source code control system.</span></span>|[<span data-ttu-id="42f15-125">ソリューション エクスプローラーのソース管理</span><span class="sxs-lookup"><span data-stu-id="42f15-125">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)|  
|<span data-ttu-id="42f15-126">ソリューションおよびファイルを管理するために [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] によって使用されるファイルに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="42f15-126">Provides information about the files used by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage solutions and files.</span></span>|[<span data-ttu-id="42f15-127">ソリューションとプロジェクトを管理するためのファイル</span><span class="sxs-lookup"><span data-stu-id="42f15-127">Files That Manage Solutions and Projects</span></span>](files-that-manage-solutions-and-projects.md)|  
  
  
