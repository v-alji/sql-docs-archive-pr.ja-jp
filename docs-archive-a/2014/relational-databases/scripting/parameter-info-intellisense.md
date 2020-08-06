---
title: パラメーター ヒント (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
author: rothja
ms.author: jroth
ms.openlocfilehash: b7e5e7496753006808f75378182db0d3cb606d4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644421"
---
# <a name="parameter-info-intellisense"></a><span data-ttu-id="c630f-102">パラメーター ヒント (IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="c630f-102">Parameter Info (IntelliSense)</span></span>
  <span data-ttu-id="c630f-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense の **[パラメーター ヒント]** オプションを使用すると、パラメーター リストが表示され、関数またはストアド プロシージャで必要とされるパラメーターの数、名前、およびデータ型について確認できます。</span><span class="sxs-lookup"><span data-stu-id="c630f-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Parameter Info** option opens a parameters list that provides information about the number, names, and types of the parameters that are required by a function or stored procedure.</span></span> <span data-ttu-id="c630f-104">太字で表示されるパラメーターは、入力中の関数やストアド プロシージャで次に必要なパラメーターを示しています。</span><span class="sxs-lookup"><span data-stu-id="c630f-104">The parameter in bold indicates the next parameter that is required as you type a function or stored procedure.</span></span>  
  
 <span data-ttu-id="c630f-105">パラメーター リストは入れ子にされた関数についても表示されます。</span><span class="sxs-lookup"><span data-stu-id="c630f-105">The parameter list is also displayed for nested functions.</span></span> <span data-ttu-id="c630f-106">他の関数のパラメーターとして関数を入力する場合、パラメーター リストには内部関数のパラメーターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c630f-106">If you type a function as a parameter to another function, the parameter list displays the parameters for the inner function.</span></span> <span data-ttu-id="c630f-107">内部関数のパラメーター リストが完了すると、パラメーター リストには再び外部関数のパラメーターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c630f-107">Then, when the inner function parameter list is complete, the parameter list reverts to displaying the outer function parameters.</span></span>  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a><span data-ttu-id="c630f-108">関数またはストアド プロシージャのパラメーター ヒントを表示するには</span><span class="sxs-lookup"><span data-stu-id="c630f-108">To view Parameter Info for functions or stored procedures</span></span>  
  
1.  <span data-ttu-id="c630f-109">関数の場合、名前の後に、通常と同じように左かっこを入力すると、パラメーター リストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c630f-109">After the name of a function, type an open parenthesis as you usually type to open the parameters list.</span></span> <span data-ttu-id="c630f-110">ストアド プロシージャの場合、名前を入力した後に、通常と同じようにスペースを入力すると、プロシージャのパラメーターに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c630f-110">After you type the name of a stored procedure, type a space as you usually type to obtain information about the procedure parameters.</span></span>  
  
     <span data-ttu-id="c630f-111">IntelliSense は、関数の宣言全体またはストアド プロシージャのパラメーターをポップアップ ウィンドウとして挿入ポイントのすぐ下に表示します。</span><span class="sxs-lookup"><span data-stu-id="c630f-111">IntelliSense displays the complete declaration for the function or the parameters for a stored procedure in a pop-up window just under the insertion point.</span></span> <span data-ttu-id="c630f-112">リスト内の最初のパラメーターは太字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c630f-112">The first parameter in the list appears in bold.</span></span>  
  
2.  <span data-ttu-id="c630f-113">パラメーターを入力していくと、次に入力する必要のあるパラメーターに応じて太字が変わります。</span><span class="sxs-lookup"><span data-stu-id="c630f-113">As you type the parameters, the bold font changes to reflect the next parameter that you need to enter.</span></span>  
  
3.  <span data-ttu-id="c630f-114">Esc キーを押してリストを閉じるか、関数が完了するまで入力を続けます。</span><span class="sxs-lookup"><span data-stu-id="c630f-114">Press ESC at any time to close the list, or continue typing until you have completed the function.</span></span>  
  
     <span data-ttu-id="c630f-115">関数の場合、右かっこを入力するとパラメーター リストも閉じます。</span><span class="sxs-lookup"><span data-stu-id="c630f-115">For a function, if you type the closing parenthesis you also close the parameter list.</span></span>  
  
#### <a name="to-manually-start-parameter-info"></a><span data-ttu-id="c630f-116">パラメーター ヒントを手動で起動するには</span><span class="sxs-lookup"><span data-stu-id="c630f-116">To manually start Parameter Info</span></span>  
  
1.  <span data-ttu-id="c630f-117">**[編集]** メニューの **[IntelliSense]** をポイントし、 **[パラメーター ヒント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c630f-117">On the **Edit** menu, select **IntelliSense** and then select **Parameter Info**.</span></span>  
  
2.  <span data-ttu-id="c630f-118">Ctrl&lt;/localizedText&gt; キーと &lt;localizedText&gt;Shift&lt;/localizedText&gt; キーを押しながら &lt;localizedText&gt;Space&lt;/localizedText&gt; キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c630f-118">Press the CTRL+SHIFT+SPACE keyboard shortcut.</span></span>  
  
 <span data-ttu-id="c630f-119">詳細については、「[IntelliSense の構成 &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c630f-119">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c630f-120">**[パラメーター ヒント]** オプションは、[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターと XML クエリ エディターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c630f-120">The **Parameter Info** option is available only for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the XML Query Editor.</span></span>  
  
  
