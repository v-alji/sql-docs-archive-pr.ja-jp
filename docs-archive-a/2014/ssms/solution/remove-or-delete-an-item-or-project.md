---
title: アイテムやプロジェクトのクリアまたは削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 679911f15d6c47f4274180602a5376c4ec03c77b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634771"
---
# <a name="remove-or-delete-an-item-or-project"></a><span data-ttu-id="67f23-102">アイテムやプロジェクトのクリアまたは削除</span><span class="sxs-lookup"><span data-stu-id="67f23-102">Remove or Delete an Item or Project</span></span>
  <span data-ttu-id="67f23-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] プロジェクトに含まれるプロジェクト アイテムには、クエリ、接続、およびその他のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="67f23-103">Project items in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] projects are Queries, Connections, and Miscellaneous files.</span></span> <span data-ttu-id="67f23-104">プロジェクトのクエリとその他のファイルは、記憶域に残したままソリューションからクリアできます。</span><span class="sxs-lookup"><span data-stu-id="67f23-104">You can remove project queries and miscellaneous files from your solution without erasing the files from storage.</span></span> <span data-ttu-id="67f23-105">現在のソリューションでは使用せずに、別のソリューションで使用する場合は、プロジェクトやアイテムをクリアします。</span><span class="sxs-lookup"><span data-stu-id="67f23-105">Remove a project or item when it is not useful in the current solution but you want to include it in another solution.</span></span>  
  
### <a name="to-remove-a-project-item"></a><span data-ttu-id="67f23-106">プロジェクト アイテムをクリアするには</span><span class="sxs-lookup"><span data-stu-id="67f23-106">To remove a project item</span></span>  
  
1.  <span data-ttu-id="67f23-107">ソリューション エクスプローラーで、クリアするプロジェクト アイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="67f23-107">In Solution Explorer, select the project item you want to remove.</span></span>  
  
2.  <span data-ttu-id="67f23-108">**[編集]** メニューの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67f23-108">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="67f23-109">確認ダイアログで **[削除]** をクリックすると、プロジェクトからアイテムが削除されます。</span><span class="sxs-lookup"><span data-stu-id="67f23-109">On the confirmation dialog, click **Remove** to remove the item from the project.</span></span>  
  
 <span data-ttu-id="67f23-110">クリアしたアイテムは、ファイル システムにまだ存在しています。</span><span class="sxs-lookup"><span data-stu-id="67f23-110">A removed item still exists on the file system.</span></span> <span data-ttu-id="67f23-111">したがって、クリアしたアイテムは、元のソリューションまたは別のソリューションに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="67f23-111">Therefore, you can add a removed item to its original solution or to another solution.</span></span>  
  
#### <a name="to-remove-a-project"></a><span data-ttu-id="67f23-112">プロジェクトをクリアするには</span><span class="sxs-lookup"><span data-stu-id="67f23-112">To remove a project</span></span>  
  
1.  <span data-ttu-id="67f23-113">ソリューション エクスプローラーで、クリアするプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="67f23-113">In Solution Explorer, select the project you want to remove.</span></span>  
  
2.  <span data-ttu-id="67f23-114">**[編集]** メニューの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67f23-114">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="67f23-115">確認ダイアログで **[OK]** をクリックします。ソリューションからプロジェクトがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="67f23-115">On the confirmation dialog, click **OK**, to remove the project from the solution.</span></span>  
  
 <span data-ttu-id="67f23-116">プロジェクトは完全に削除できますが、最初に [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ソリューションからプロジェクトへの参照をすべてクリアし、次に [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows エクスプローラーを使用して、関連付けられているファイルを記憶域から完全に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67f23-116">You can delete a project permanently, but you first need to remove any references to the project from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solutions, and then use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Explorer to permanently delete the associated files from storage.</span></span>  
  
#### <a name="to-delete-a-project"></a><span data-ttu-id="67f23-117">プロジェクトを削除するには</span><span class="sxs-lookup"><span data-stu-id="67f23-117">To delete a project</span></span>  
  
1.  <span data-ttu-id="67f23-118">ソリューション エクスプローラーで、ソリューションから削除するプロジェクトをクリアします。</span><span class="sxs-lookup"><span data-stu-id="67f23-118">In Solution Explorer, remove the project you want to delete from the solution.</span></span>  
  
2.  <span data-ttu-id="67f23-119">Windows エクスプローラーで、削除するプロジェクトまたはアイテムに関連付けられているファイルを検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="67f23-119">In Windows Explorer, locate and select the files associated with the project or item you want to delete.</span></span>  
  
3.  <span data-ttu-id="67f23-120">**[ファイル]** メニューの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67f23-120">On the **File** menu, click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f23-121">参照</span><span class="sxs-lookup"><span data-stu-id="67f23-121">See Also</span></span>  
 <span data-ttu-id="67f23-122">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="67f23-122">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="67f23-123">[プロジェクトに新しい項目を追加する](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="67f23-123">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="67f23-124">既存の項目をプロジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="67f23-124">Add Existing Items to a Project</span></span>](add-existing-items-to-a-project.md)  
  
  
