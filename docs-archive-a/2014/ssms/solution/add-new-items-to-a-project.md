---
title: プロジェクトへの新規項目の追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: c73c58952c7801b3a0e2c86652feb461292cf37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645291"
---
# <a name="add-new-items-to-a-project"></a><span data-ttu-id="d9dba-102">プロジェクトへの新規項目の追加</span><span class="sxs-lookup"><span data-stu-id="d9dba-102">Add New Items to a Project</span></span>
  <span data-ttu-id="d9dba-103">プロジェクトに新しい項目を追加して、アプリケーションの機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="d9dba-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="d9dba-104">新しい項目にできるのは、クエリまたは接続です。</span><span class="sxs-lookup"><span data-stu-id="d9dba-104">A new item can be a query or a connection.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="d9dba-105">には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトおよび Analysis Services スクリプト プロジェクトという 2 種類のプロジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="d9dba-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="d9dba-106">プロジェクトの種類によって、プロジェクトに追加できるアイテムが決まります。</span><span class="sxs-lookup"><span data-stu-id="d9dba-106">The project type determines the items that you can add to the project.</span></span> <span data-ttu-id="d9dba-107">たとえば、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ (拡張子が .sql のファイル) は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトには追加できますが、Analysis Services スクリプト プロジェクトには追加できません。</span><span class="sxs-lookup"><span data-stu-id="d9dba-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="d9dba-108">では、プロジェクト内にフォルダーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d9dba-108">does not allow you to create folders within projects.</span></span> <span data-ttu-id="d9dba-109">作業を整理するには、ソリューション内に複数のプロジェクトを作成してください。</span><span class="sxs-lookup"><span data-stu-id="d9dba-109">To organize your work, create multiple projects within the solution.</span></span>  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a><span data-ttu-id="d9dba-110">既存のプロジェクトに新しいクエリを追加するには</span><span class="sxs-lookup"><span data-stu-id="d9dba-110">To add a new query to an existing project</span></span>  
  
1.  <span data-ttu-id="d9dba-111">ソリューション エクスプローラーで、対象のプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9dba-111">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="d9dba-112">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9dba-112">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="d9dba-113">**[新しい項目の追加]** ダイアログ ボックスの左側のペインで、カテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9dba-113">In the **Add New Item** dialog box, select a category in the left pane.</span></span>  
  
4.  <span data-ttu-id="d9dba-114">右側のペインでクエリ テンプレートを選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9dba-114">Select a query template in the right pane, and then click **Add**.</span></span> <span data-ttu-id="d9dba-115">新しいクエリがプロジェクトの **[クエリ]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d9dba-115">The new query is added in the **Queries** folder of the project.</span></span>  
  
5.  <span data-ttu-id="d9dba-116">**[データベース エンジンへの接続]** ダイアログ ボックスで、新しいクエリの接続を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9dba-116">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="d9dba-117">新しいクエリに接続を関連付けたくない場合は、接続ダイアログの **[キャンセル]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d9dba-117">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the new query.</span></span>  
  
6.  <span data-ttu-id="d9dba-118">必要に応じて、ソリューション エクスプローラーでクエリの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="d9dba-118">Rename the query in Solution Explorer if you wish.</span></span>  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a><span data-ttu-id="d9dba-119">既存のプロジェクトに新しい接続を追加するには</span><span class="sxs-lookup"><span data-stu-id="d9dba-119">To add a new connection to an existing project</span></span>  
  
1.  <span data-ttu-id="d9dba-120">ソリューション エクスプローラーで、対象のプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9dba-120">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="d9dba-121">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9dba-121">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="d9dba-122">左ペインで **[接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d9dba-122">Select **Connection** in the left pane.</span></span>  
  
4.  <span data-ttu-id="d9dba-123">右側のペインで **[新しい接続]** を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9dba-123">Select **New Connection** in the right pane, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="d9dba-124">**[データベース エンジンへの接続]** ダイアログ ボックスで、新しいクエリの接続を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9dba-124">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="d9dba-125">新しい接続がプロジェクトの **[接続]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d9dba-125">The new connection gets added in the **Connections** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9dba-126">参照</span><span class="sxs-lookup"><span data-stu-id="d9dba-126">See Also</span></span>  
 <span data-ttu-id="d9dba-127">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="d9dba-127">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="d9dba-128">[ファイル拡張子をコードエディターに関連付ける](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span><span class="sxs-lookup"><span data-stu-id="d9dba-128">[Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span></span>  
 <span data-ttu-id="d9dba-129">[既存の項目をプロジェクトに追加する](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="d9dba-129">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="d9dba-130">アイテムやプロジェクトのクリアまたは削除</span><span class="sxs-lookup"><span data-stu-id="d9dba-130">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
