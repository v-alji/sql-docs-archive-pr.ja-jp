---
title: ソリューション (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- solutions [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d06a8a05-7201-4055-8cf3-21bcb4e82c25
author: stevestein
ms.author: sstein
ms.openlocfilehash: 836d3b3002d72541ad88ae55eac6d951530e0ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634764"
---
# <a name="solutions-sql-server-management-studio"></a><span data-ttu-id="10ba5-102">ソリューション (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="10ba5-102">Solutions (SQL Server Management Studio)</span></span>
  <span data-ttu-id="10ba5-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ソリューションは、1 つまたは複数の関連プロジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="10ba5-103">A [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution is a collection of one or more related projects.</span></span> <span data-ttu-id="10ba5-104">プロジェクトは、一般的に使用される管理スクリプトなどの関連ファイルを編成するために開発者が使用できるコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="10ba5-104">Projects are containers that developers use to organize related files, such as sets of commonly used administration scripts.</span></span>  
  
## <a name="solution-overview"></a><span data-ttu-id="10ba5-105">ソリューションの概要</span><span class="sxs-lookup"><span data-stu-id="10ba5-105">Solution Overview</span></span>  
 <span data-ttu-id="10ba5-106">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のスクリプト開発プラットフォームとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="10ba5-106">You can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] as a script development platform for [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="10ba5-107">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] コード エディターでは、リレーショナル データベースや多次元データベースのスクリプトおよびクエリを開発し、プロジェクト内で関連するスクリプトおよびクエリをまとめて収集することができます。</span><span class="sxs-lookup"><span data-stu-id="10ba5-107">Use the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] code editors to develop scripts and queries for relational and multidimensional databases, and collect related scripts and queries together in projects.</span></span>  
  
 <span data-ttu-id="10ba5-108">プロジェクトには以下を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="10ba5-108">Projects can contain:</span></span>  
  
-   <span data-ttu-id="10ba5-109">実稼働プロセスを実装するクエリとスクリプト</span><span class="sxs-lookup"><span data-stu-id="10ba5-109">Queries and scripts that implement production processes.</span></span>  
  
-   <span data-ttu-id="10ba5-110">クエリおよびスクリプトで使用される接続情報およびファイル</span><span class="sxs-lookup"><span data-stu-id="10ba5-110">Connection information and files used by the queries and scripts.</span></span>  
  
 <span data-ttu-id="10ba5-111">ソリューションに 1 つまたは複数の関連プロジェクトを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="10ba5-111">One or more related projects can be combined in a solution.</span></span> <span data-ttu-id="10ba5-112">ソリューションおよびプロジェクトは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のエクスプ ローラー ウィンドウを使用して管理できます</span><span class="sxs-lookup"><span data-stu-id="10ba5-112">Solutions and projects can be managed by using the Solution Explorer pane in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="10ba5-113">開発変更の追跡とライフサイクル管理のために、ソリューションおよびプロジェクトを [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe (VSS) データベースまたは他のサードパーティのソース管理プロバイダーに統合できます。</span><span class="sxs-lookup"><span data-stu-id="10ba5-113">Solutions and projects can be integrated into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe (VSS) database or other third-party source control providers, for development change tracking and life-cycle management.</span></span>  
  
## <a name="solution-tasks"></a><span data-ttu-id="10ba5-114">ソリューション タスク</span><span class="sxs-lookup"><span data-stu-id="10ba5-114">Solution Tasks</span></span>  
  
|<span data-ttu-id="10ba5-115">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="10ba5-115">Task Description</span></span>|<span data-ttu-id="10ba5-116">トピック</span><span class="sxs-lookup"><span data-stu-id="10ba5-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="10ba5-117">1 つまたは複数のプロジェクトを含めるために使用できる新しいソリューションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-117">Describes how to create a new solution that can then be used to contain one or more projects.</span></span>|[<span data-ttu-id="10ba5-118">新しいソリューションの作成</span><span class="sxs-lookup"><span data-stu-id="10ba5-118">Create a New Solution</span></span>](create-a-new-solution.md)|  
|<span data-ttu-id="10ba5-119">ソリューション エクスプローラーで既存のソリューションを開く方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-119">Describes how to open an existing solution in Solution Explorer.</span></span>|[<span data-ttu-id="10ba5-120">既存のソリューションを開く</span><span class="sxs-lookup"><span data-stu-id="10ba5-120">Open an Existing Solution</span></span>](open-an-existing-solution.md)|  
|<span data-ttu-id="10ba5-121">ソリューションを閉じる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-121">Describes how to close a solution.</span></span>|[<span data-ttu-id="10ba5-122">ソリューションを閉じる</span><span class="sxs-lookup"><span data-stu-id="10ba5-122">Close a Solution</span></span>](close-a-solution.md)|  
|<span data-ttu-id="10ba5-123">ソリューションを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-123">Describes how to delete a solution.</span></span>|[<span data-ttu-id="10ba5-124">ソリューションを削除する</span><span class="sxs-lookup"><span data-stu-id="10ba5-124">Delete a Solution</span></span>](delete-a-solution.md)|  
|<span data-ttu-id="10ba5-125">プロジェクト間で項目をコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-125">Describes how to copy items between projects.</span></span>|[<span data-ttu-id="10ba5-126">ソリューションの項目のコピー</span><span class="sxs-lookup"><span data-stu-id="10ba5-126">Copy Items in a Solution</span></span>](copy-items-in-a-solution.md)|  
|<span data-ttu-id="10ba5-127">プロジェクト内の項目またはプロジェクト全体を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-127">Describes how to delete items in a project, or an entire project.</span></span>|[<span data-ttu-id="10ba5-128">アイテムやプロジェクトのクリアまたは削除</span><span class="sxs-lookup"><span data-stu-id="10ba5-128">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)|  
|<span data-ttu-id="10ba5-129">ソリューション内のプロジェクト間で項目を移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-129">Describes how to move items between projects in a solution.</span></span>|[<span data-ttu-id="10ba5-130">ソリューションのアイテムの移動</span><span class="sxs-lookup"><span data-stu-id="10ba5-130">Move Items in a Solution</span></span>](move-items-in-a-solution.md)|  
|<span data-ttu-id="10ba5-131">ソリューションまたはソリューション内の項目の名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10ba5-131">Describes how to rename a solution or the items in the solution.</span></span>|[<span data-ttu-id="10ba5-132">ソリューションとプロジェクト アイテムの名前変更</span><span class="sxs-lookup"><span data-stu-id="10ba5-132">Rename Solutions and Project Items</span></span>](rename-solutions-and-project-items.md)|  
  
## <a name="see-also"></a><span data-ttu-id="10ba5-133">参照</span><span class="sxs-lookup"><span data-stu-id="10ba5-133">See Also</span></span>  
 <span data-ttu-id="10ba5-134">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="10ba5-134">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="10ba5-135">[プロジェクト &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="10ba5-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="10ba5-136">ソリューション エクスプローラーのソース管理</span><span class="sxs-lookup"><span data-stu-id="10ba5-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
