---
title: ソリューションのアイテムの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd0a8a89686c62b4d4d00aea5479bb956fe3011f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714970"
---
# <a name="move-items-in-a-solution"></a><span data-ttu-id="2b179-102">ソリューションのアイテムの移動</span><span class="sxs-lookup"><span data-stu-id="2b179-102">Move Items in a Solution</span></span>
  <span data-ttu-id="2b179-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] プロジェクトに含まれるプロジェクト アイテムには、クエリ、接続、およびその他のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="2b179-103">Project items in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] projects are Queries, Connections, and Miscellaneous files.</span></span> <span data-ttu-id="2b179-104">クエリとその他のファイルはソリューション エクスプローラーで別のプロジェクトに移動することができますが、接続は移動できません。</span><span class="sxs-lookup"><span data-stu-id="2b179-104">You can move Queries and Miscellaneous Files between projects in Solution Explorer, but Connections cannot be moved.</span></span>  
  
### <a name="to-move-items-in-solution-explorer"></a><span data-ttu-id="2b179-105">ソリューション エクスプローラーでアイテムを移動するには</span><span class="sxs-lookup"><span data-stu-id="2b179-105">To move items in Solution Explorer</span></span>  
  
1.  <span data-ttu-id="2b179-106">ソリューション エクスプローラーで、移動するアイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="2b179-106">In Solution Explorer, select the item you want to move.</span></span>  
  
2.  <span data-ttu-id="2b179-107">**[編集]** メニューの **[切り取り]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b179-107">On the **Edit** menu, click **Cut**.</span></span>  
  
3.  <span data-ttu-id="2b179-108">ソリューション エクスプローラーで、移動先を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b179-108">In Solution Explorer, select the destination.</span></span>  
  
4.  <span data-ttu-id="2b179-109">**[編集]** メニューの **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b179-109">On the **Edit** menu, click **Paste**.</span></span>  
  
 <span data-ttu-id="2b179-110">ソリューション エクスプローラー内でクエリやその他のファイルをドラッグして、アイテムを移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b179-110">You can move items by dragging Query and Miscellaneous files within Solution Explorer.</span></span> <span data-ttu-id="2b179-111">アイテムをドラッグする場合は、ドラッグ操作の結果を目で見て確認できます。</span><span class="sxs-lookup"><span data-stu-id="2b179-111">Dragging allows you to see the outcome of the drag operation.</span></span> <span data-ttu-id="2b179-112">クエリを別の種類のプロジェクトに移動する場合、そのクエリが移動先のプロジェクトでその他のファイルと見なされることがあります。</span><span class="sxs-lookup"><span data-stu-id="2b179-112">Moving queries from one project type to another may cause queries to be considered as miscellaneous files in the target project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b179-113">接続を指定したクエリを移動しても、接続は移動先のプロジェクトに移動しません。</span><span class="sxs-lookup"><span data-stu-id="2b179-113">Moving a connected query does not move the connection to the target project.</span></span> <span data-ttu-id="2b179-114">クエリを別のプロジェクトに移動すると、接続の設定は消去されます。</span><span class="sxs-lookup"><span data-stu-id="2b179-114">The query will lose its connection after it is moved to the target project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b179-115">参照</span><span class="sxs-lookup"><span data-stu-id="2b179-115">See Also</span></span>  
 <span data-ttu-id="2b179-116">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="2b179-116">[Solution Explorer](solution-explorer.md) </span></span>  
 [<span data-ttu-id="2b179-117">ソリューションの項目のコピー</span><span class="sxs-lookup"><span data-stu-id="2b179-117">Copy Items in a Solution</span></span>](copy-items-in-a-solution.md)  
  
  
