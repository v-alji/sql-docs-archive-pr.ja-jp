---
title: インデントの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d0b7ee8819f98df5e5658321a3d950ca31083b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642466"
---
# <a name="adding-indentation"></a><span data-ttu-id="e462e-102">インデントの追加</span><span class="sxs-lookup"><span data-stu-id="e462e-102">Adding Indentation</span></span>
  <span data-ttu-id="e462e-103">クエリ エディターでは、大規模なコードのセクションに一括してインデントを適用できるほか、インデント幅を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e462e-103">Query Editor allows you to indent large sections of code with a single step, and you can change the amount of the indentation.</span></span>  
  
## <a name="indenting-code"></a><span data-ttu-id="e462e-104">コードへのインデントの適用</span><span class="sxs-lookup"><span data-stu-id="e462e-104">Indenting Code</span></span>  
  
#### <a name="to-indent-multiple-lines-of-code"></a><span data-ttu-id="e462e-105">複数行のコードにインデントを適用するには</span><span class="sxs-lookup"><span data-stu-id="e462e-105">To indent multiple lines of code</span></span>  
  
1.  <span data-ttu-id="e462e-106">ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e462e-106">On the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="e462e-107">ここでは、 **Person**スキーマの **Person**テーブルから、 **BusinessEntityID** 、FirstName、 **MiddleName** 、 **LastName** の各列を選択する新しいクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e462e-107">Create a second query that selects the **BusinessEntityID**, FirstName, **MiddleName**, and **LastName** columns from the **Person** table of the **Person** schema.</span></span> <span data-ttu-id="e462e-108">次のようにコードを入力します。各列を別々の行に入力してください。</span><span class="sxs-lookup"><span data-stu-id="e462e-108">Place each column on a separate line so the code looks like this:</span></span>  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  <span data-ttu-id="e462e-109">`BusinessEntityID` から `LastName`までのテキストをすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="e462e-109">Select all text from `BusinessEntityID` to `LastName`.</span></span>  
  
4.  <span data-ttu-id="e462e-110">**[SQL エディター]** ツール バーの **[インデント]** をクリックし、すべての行に一括してインデントを適用します。</span><span class="sxs-lookup"><span data-stu-id="e462e-110">On the **SQL Editor** toolbar, click **Increase Indent** to indent all the lines at once.</span></span>  
  
#### <a name="to-change-the-default-indentation"></a><span data-ttu-id="e462e-111">既定のインデントを変更するには</span><span class="sxs-lookup"><span data-stu-id="e462e-111">To change the default indentation</span></span>  
  
1.  <span data-ttu-id="e462e-112">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e462e-112">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="e462e-113">**[テキスト エディター]**、 **[すべての言語]** の順に展開し、 **[タブ]** をクリックして、適切なインデント幅を設定します。</span><span class="sxs-lookup"><span data-stu-id="e462e-113">Expand **Text Editor**, expand **All Languages**, and click **Tabs** , and set indentation values as appropriate.</span></span> <span data-ttu-id="e462e-114">インデント幅とタブのサイズを変更できるほか、タブをスペースに変換するかどうかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="e462e-114">Note that you can change the size of the indent as well as the size of tabs, and whether tabs are converted to spaces.</span></span>  
  
     <span data-ttu-id="e462e-115">![[タブ] オプション ([オプション] ダイアログ ボックス)](media/tabsdialog.gif "[タブ] オプション ([オプション] ダイアログ ボックス)")</span><span class="sxs-lookup"><span data-stu-id="e462e-115">![Appearance of the Tabs dialog box](media/tabsdialog.gif "Appearance of the Tabs dialog box")</span></span>  
  
3.  <span data-ttu-id="e462e-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e462e-116">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e462e-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="e462e-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e462e-118">クエリ エディターの最大化</span><span class="sxs-lookup"><span data-stu-id="e462e-118">Maximizing Query Editor</span></span>](lesson-2-3-maximizing-query-editor.md)  
  
  
