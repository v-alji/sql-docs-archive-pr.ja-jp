---
title: ブレークポイントの位置の編集
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: rothja
ms.author: jroth
ms.openlocfilehash: 919e62d53d5c9e8898bf1d49c4b5e5aa4c0ed107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630872"
---
# <a name="edit-a-breakpoint-location"></a><span data-ttu-id="23171-102">ブレークポイントの位置の編集</span><span class="sxs-lookup"><span data-stu-id="23171-102">Edit a Breakpoint Location</span></span>
  <span data-ttu-id="23171-103">ブレークポイントの位置では、ブレークポイントを設定する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイル内の行や文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="23171-103">The breakpoint location specifies the line and character where the breakpoint resides in a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="23171-104">ブレークポイントの位置を編集して、ブレークポイントを別の位置や別のスクリプトに移動できます。</span><span class="sxs-lookup"><span data-stu-id="23171-104">You can edit the breakpoint location to move the breakpoint to another location in the script, or to a different script.</span></span>  
  
## <a name="editing-a-location"></a><span data-ttu-id="23171-105">位置の編集</span><span class="sxs-lookup"><span data-stu-id="23171-105">Editing a Location</span></span>  
 <span data-ttu-id="23171-106">ブレークポイントの位置を編集すると、ブレークポイントはヒット カウント、条件などの既存のすべてのプロパティと共に新しい位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="23171-106">When you edit a breakpoint location, the breakpoint moves to the new location, carrying with it all of the existing properties, such as a hit count or condition.</span></span>  
  
#### <a name="to-edit-a-breakpoint-location"></a><span data-ttu-id="23171-107">ブレークポイントの位置を編集するには</span><span class="sxs-lookup"><span data-stu-id="23171-107">To Edit a Breakpoint Location</span></span>  
  
1.  <span data-ttu-id="23171-108">エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23171-108">In the editor window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="23171-109">または</span><span class="sxs-lookup"><span data-stu-id="23171-109">-or-</span></span>  
  
     <span data-ttu-id="23171-110">**[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23171-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="23171-111">**[ファイルのブレークポイント]** ダイアログ ボックスで、新しいファイルを指定するには **[ファイル]** 、新しい行を指定するには **[行]** 、行内の新しい場所を指定するには **[文字]** の各項目を編集します。</span><span class="sxs-lookup"><span data-stu-id="23171-111">In the **File Breakpoint** dialog box, edit **File** to specify a new file, **Line** to specify a new line, or **Character** to specify a new location within the line.</span></span> <span data-ttu-id="23171-112">指定した新しいファイルがクエリ エディター ウィンドウで既に開いている場合は、ブレークポイントがそのエディター ウィンドウに移動します。</span><span class="sxs-lookup"><span data-stu-id="23171-112">If the new file you specify is already open in a query editor window, the breakpoint is moved to that editor window.</span></span> <span data-ttu-id="23171-113">ファイルが開いていない場合は、新しいクエリ エディター ウィンドウが開き、そのファイルが読み込まれ、ブレークポイントが新しい位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="23171-113">If the file is not opened, a new editor window is opened, the file is loaded in, and the breakpoint moved to the new location.</span></span>  
  
     <span data-ttu-id="23171-114">**をデバッグする場合、** [元のバージョンと異なるソース コードを許可する] [!INCLUDE[tsql](../../includes/tsql-md.md)]オプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="23171-114">The **Allow the source code to be different from the original version** option has no effect when debugging [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23171-115">参照</span><span class="sxs-lookup"><span data-stu-id="23171-115">See Also</span></span>  
 <span data-ttu-id="23171-116">[ヒットカウントの指定](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="23171-116">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 <span data-ttu-id="23171-117">[ブレークポイントアクションの指定](specify-a-breakpoint-action.md) </span><span class="sxs-lookup"><span data-stu-id="23171-117">[Specify a Breakpoint Action](specify-a-breakpoint-action.md) </span></span>  
 <span data-ttu-id="23171-118">[ブレークポイント条件の指定](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="23171-118">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="23171-119">ブレークポイント フィルターの指定</span><span class="sxs-lookup"><span data-stu-id="23171-119">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)  
