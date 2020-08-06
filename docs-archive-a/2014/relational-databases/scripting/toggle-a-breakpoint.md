---
title: ブレークポイントの切り替え
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: rothja
ms.author: jroth
ms.openlocfilehash: 72e26e9b1d04bc2eced6bcb6d93d3c86a016d308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643760"
---
# <a name="toggle-a-breakpoint"></a><span data-ttu-id="153ed-102">ブレークポイントの切り替え</span><span class="sxs-lookup"><span data-stu-id="153ed-102">Toggle a Breakpoint</span></span>
  <span data-ttu-id="153ed-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント上でブレークポイントを設定することを、ブレークポイントの切り替えと呼びます。</span><span class="sxs-lookup"><span data-stu-id="153ed-103">The act of setting a breakpoint on a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is called toggling a breakpoint.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="153ed-104">ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="153ed-104">Breakpoints</span></span>  
 <span data-ttu-id="153ed-105">ブレークポイントが設定されると、ステートメントの左側の灰色のバーにアイコンとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="153ed-105">Once the breakpoint has been set, it is represented by an icon in the grey bar to the left of the statement.</span></span> <span data-ttu-id="153ed-106">このアイコンはブレークポイント グリフと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="153ed-106">The icon is called a breakpoint glyph.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="153ed-107">ブレークポイントは、完全な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに適用されます。</span><span class="sxs-lookup"><span data-stu-id="153ed-107">breakpoints are applied to a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="153ed-108">ブレークポイントが切り替えられると、デバッガーは、関連付けられている [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="153ed-108">When a breakpoint is toggled on, the debugger highlights the associated [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
 <span data-ttu-id="153ed-109">1 行に複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがある場合、ステートメントごとにブレークポイントを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="153ed-109">If there are multiple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on a line, you can toggle a breakpoint for each statement.</span></span> <span data-ttu-id="153ed-110">ウィンドウの左側にある灰色のバーをクリックすると、行の最初のステートメントのブレークポイントが切り替わります。</span><span class="sxs-lookup"><span data-stu-id="153ed-110">Clicking in the grey bar on the left of the window toggles a breakpoint on the first statement on the line.</span></span> <span data-ttu-id="153ed-111">ステートメントの任意の箇所を強調表示するか、ステートメント内にカーソルを移動してから、F9 キーを押すか、 **[デバッグ]** メニューの **[ブレークポイントの設定/解除]** をクリックすることにより、後続のステートメント内でブレークポイントを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="153ed-111">You can toggle a breakpoint in a subsequent statement by highlighting any part of the statement, or moving the cursor into the statement, and then either pressing F9 or clicking **Toggle Breakpoint** on the **Debug** menu.</span></span> <span data-ttu-id="153ed-112">1 行に複数のブレークポイントがある場合、左側の灰色のバーにブレークポイント グリフが 1 つだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="153ed-112">If you have multiple breakpoints on a line, there is only one breakpoint glyph in the grey bar on the left.</span></span>  
  
 <span data-ttu-id="153ed-113">ブレークポイントを切り替えた後に、ブレークポイントでプロパティの編集や一時的な無効化などさまざまな操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="153ed-113">After a breakpoint has been toggled, you can perform various actions on the breakpoint, such as editing its properties or temporarily disabling it.</span></span> <span data-ttu-id="153ed-114">詳細については、「 [Transact-SQL ブレークポイント](transact-sql-breakpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="153ed-114">For more information, see [Transact-SQL Breakpoints](transact-sql-breakpoints.md).</span></span>  
  
## <a name="toggle-a-breakpoint"></a><span data-ttu-id="153ed-115">ブレークポイントの切り替え</span><span class="sxs-lookup"><span data-stu-id="153ed-115">Toggle a Breakpoint</span></span>  
 <span data-ttu-id="153ed-116">**Transact-SQL ステートメントでブレークポイントを切り替えるには**</span><span class="sxs-lookup"><span data-stu-id="153ed-116">**To toggle a breakpoint on a Transact-SQL statement**</span></span>  
  
1.  <span data-ttu-id="153ed-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの左側にある灰色のバーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="153ed-117">Click the gray bar to the left side of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
2.  <span data-ttu-id="153ed-118">または、ステートメントの任意の箇所を強調表示するか、ステートメント内にカーソルを移動してから、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="153ed-118">Alternatively, either highlight any part of the statement or move the cursor to the statement, and then perform either action:</span></span>  
  
    -   <span data-ttu-id="153ed-119">F9 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="153ed-119">Press F9.</span></span>  
  
    -   <span data-ttu-id="153ed-120">**[デバッグ]** メニューの **[ブレークポイントの設定/解除]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="153ed-120">On the **Debug** menu, click **Toggle Breakpoint**.</span></span>  
  
  
