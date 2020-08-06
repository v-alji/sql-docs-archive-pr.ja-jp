---
title: '[コマンド] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: rothja
ms.author: jroth
ms.openlocfilehash: c766ed5408de96b6a2305ce377f9031947618a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644415"
---
# <a name="command-window"></a><span data-ttu-id="74a50-102">[コマンド] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="74a50-102">Command Window</span></span>
  <span data-ttu-id="74a50-103">**[コマンド]** ウィンドウを使用すると、現在デバッグ中の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディター ウィンドウのコードに対してデバッグ コマンドや編集コマンドなどのコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="74a50-103">Use the **CommandWindow** to run commands, such as debug and edit commands, against the code in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor window that is currently being debugged.</span></span> <span data-ttu-id="74a50-104">**[コマンド]** ウィンドウを使用するには、デバッグ モードである必要があります。</span><span class="sxs-lookup"><span data-stu-id="74a50-104">You must be in debug mode to use the **Command Window**.</span></span> <span data-ttu-id="74a50-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **[コマンド]** ウィンドウでもサポートされているコマンドの多くをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="74a50-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports many of the commands that are also supported in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window.</span></span> <span data-ttu-id="74a50-106">詳細については、 [Visual Studio のコマンド ウィンドウに関するページ](https://go.microsoft.com/fwlink/?LinkId=112007)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74a50-106">For more information, see [Visual Studio Command Window](https://go.microsoft.com/fwlink/?LinkId=112007).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="74a50-107">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="74a50-107">Task List</span></span>  
 <span data-ttu-id="74a50-108">**[コマンド] ウィンドウにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="74a50-108">**To access the Command Window**</span></span>  
  
-   <span data-ttu-id="74a50-109">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74a50-109">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
 <span data-ttu-id="74a50-110">**変数の値を出力するには**</span><span class="sxs-lookup"><span data-stu-id="74a50-110">**To print the value of a variable**</span></span>  
  
-   <span data-ttu-id="74a50-111">**コマンドウィンドウ**で、「 \*\*Debug. Print \<VariableName> \*\*」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="74a50-111">In the **CommandWindow**, type **Debug.Print \<VariableName>**, and then press ENTER.</span></span>  
  
 <span data-ttu-id="74a50-112">**現在のスレッドに関する情報を一覧表示するには**</span><span class="sxs-lookup"><span data-stu-id="74a50-112">**To list information about the current thread**</span></span>  
  
-   <span data-ttu-id="74a50-113">**コマンドウィンドウ**で、「」と入力し、enter `Debug.ListThread` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="74a50-113">In the **CommandWindow**, type `Debug.ListThread`, and then press ENTER.</span></span>  
  
 <span data-ttu-id="74a50-114">**[クイック ウォッチ] ウィンドウに変数を追加するには**</span><span class="sxs-lookup"><span data-stu-id="74a50-114">**To add a variable to the QuickWatch window**</span></span>  
  
-   <span data-ttu-id="74a50-115">**コマンドウィンドウ**で、「 \*\*Debug. クイックウォッチ \<VariableName> \*\*」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="74a50-115">In the **CommandWindow**, type **Debug.QuickWatch \<VariableName>**, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a50-116">参照</span><span class="sxs-lookup"><span data-stu-id="74a50-116">See Also</span></span>  
 [<span data-ttu-id="74a50-117">Transact-SQL デバッガー</span><span class="sxs-lookup"><span data-stu-id="74a50-117">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
