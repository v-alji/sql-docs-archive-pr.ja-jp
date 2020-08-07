---
title: データベース ダイアグラムの所有権について (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 21d0f6f006328d8843bbbe12ee066a8564fb722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719298"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a><span data-ttu-id="9c247-102">データベース ダイアグラムの所有権について (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9c247-102">Understand Database Diagram Ownership (Visual Database Tools)</span></span>
  <span data-ttu-id="9c247-103">データベース ダイアグラム デザイナーを使用するには、db_owner ロール ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのロール) のメンバーが、ダイアグラムへのアクセスを制御するようにあらかじめ設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c247-103">To use Database Diagram Designer it must first be set up by a member of the db_owner role (a role of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases) to control access to diagrams.</span></span> <span data-ttu-id="9c247-104">各ダイアグラムの所有者は 1 人だけで、ダイアグラムを作成したユーザーが所有者になります。</span><span class="sxs-lookup"><span data-stu-id="9c247-104">Each diagram has one and only one owner, the user who created it.</span></span> <span data-ttu-id="9c247-105">ダイアグラムの設定の詳細については、「[データベースダイアグラムデザイナー &#40;Visual Database Tools&#41;のセットアップ](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c247-105">For more information on setting up diagramming see [Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="9c247-106">ダイアグラムの所有権については、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9c247-106">Some points to keep in mind about diagram ownership:</span></span>  
  
-   <span data-ttu-id="9c247-107">データベースへのアクセス権を持つユーザーであればだれでもダイアグラムを作成できますが、作成されたダイアグラムを表示できるユーザーは、ダイアグラムの作成者と db_owner ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="9c247-107">Although any user with access to a database can create a diagram, once the diagram has been created, the only users who can see it are the diagram's creator and any member of the db_owner role.</span></span>  
  
-   <span data-ttu-id="9c247-108">ダイアグラムの所有権は、db_owner ロールのメンバーだけに移譲できます。</span><span class="sxs-lookup"><span data-stu-id="9c247-108">Ownership of diagrams can only be transferred to members of the db_owner role.</span></span> <span data-ttu-id="9c247-109">移譲できるのは、ダイアグラムの前の所有者がデータベースから削除された場合だけです。</span><span class="sxs-lookup"><span data-stu-id="9c247-109">This is only possible if the previous owner of the diagram has been removed from the database.</span></span>  
  
-   <span data-ttu-id="9c247-110">ダイアグラムの所有者がデータベースから削除されても、db_owner ロールのメンバーが開こうとするまでダイアグラムはデータベース内に残ります。</span><span class="sxs-lookup"><span data-stu-id="9c247-110">If the owner of a diagram has been removed from the database, the diagram will remain in the database until a member of the db_owner role attempts to open it.</span></span> <span data-ttu-id="9c247-111">ダイアグラムを開く時点で、db_owner メンバーはダイアグラムの所有権を継承するかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9c247-111">At that point the db_owner member can choose to take over ownership of the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c247-112">参照</span><span class="sxs-lookup"><span data-stu-id="9c247-112">See Also</span></span>  
 <span data-ttu-id="9c247-113">[データベースダイアグラムの使用 &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9c247-113">[Work with Database Diagrams &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9c247-114">データベース ダイアグラム デザイナーの設定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9c247-114">Set Up Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
