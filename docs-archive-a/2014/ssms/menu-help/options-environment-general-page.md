---
title: '[オプション] ([環境]/[全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7712c568b478bd2ba958237ba3204246657b3a72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645973"
---
# <a name="options-environment-general-page"></a><span data-ttu-id="cdf85-102">[オプション] ([環境]-[全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="cdf85-102">Options (Environment-General Page)</span></span>
  <span data-ttu-id="cdf85-103">**[オプション]** ダイアログ ボックスを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] スタートアップ アクション、全般的なウィンドウ管理オプション、およびその他の全般設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-103">Use the **Options** dialog box to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] startup actions, general window management options, and other general settings.</span></span> <span data-ttu-id="cdf85-104">**[ツール]** メニューの **[オプション]** をクリックし、 **[環境]** フォルダーを展開して **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdf85-104">On the **Tools** menu, click **Options**, expand the **Environment** folder, and then click **General**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="cdf85-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="cdf85-105">UI element list</span></span>  
 <span data-ttu-id="cdf85-106">**[スタートアップ時]**</span><span class="sxs-lookup"><span data-stu-id="cdf85-106">**At startup**</span></span>  
 <span data-ttu-id="cdf85-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の起動時に実行されるアクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cdf85-107">Select the action for [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to perform when it is started.</span></span> <span data-ttu-id="cdf85-108">オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cdf85-108">The options are:</span></span>  
  
-   <span data-ttu-id="cdf85-109">**[オブジェクト エクスプローラーを開く]** 。接続を要求してからオブジェクト エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-109">**Open Object Explorer** prompts for a connection and then opens Object Explorer.</span></span>  
  
-   <span data-ttu-id="cdf85-110">**[新しいクエリ ウィンドウを開く]** 。接続を要求してから SQL クエリ エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-110">**Open new query window** prompts for a connection and then opens SQL Query Editor.</span></span>  
  
-   <span data-ttu-id="cdf85-111">**[オブジェクト エクスプローラーと新しいクエリを開く]** 。接続を要求してから、その接続でオブジェクト エクスプローラーおよび SQL クエリ エディターの両方を開きます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-111">**Open Object Explorer and new query** prompts for a connection, then opens both Object Explorer and SQL Query Editor with that connection.</span></span>  
  
-   <span data-ttu-id="cdf85-112">**[空の環境を開く]** 。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開きますが、[SQL クエリ エディター] ウィンドウを表示せず、オブジェクト エクスプローラーをサーバーに接続しません。</span><span class="sxs-lookup"><span data-stu-id="cdf85-112">**Open empty environment** opens [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] without a SQL Query editor window and without connecting Object Explorer to a server.</span></span>  
  
 <span data-ttu-id="cdf85-113">**[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]**</span><span class="sxs-lookup"><span data-stu-id="cdf85-113">**Hide system objects in Object Explorer**</span></span>  
 <span data-ttu-id="cdf85-114">このチェック ボックスをオンにすると、システム データベース、システム テーブル、システム ビュー、およびシステム ストアド プロシージャがオブジェクト エクスプローラーのツリー ビューから削除されます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-114">Select this check box to remove the system databases, system tables, system views, and system stored procedures from tree view in Object Explorer.</span></span> <span data-ttu-id="cdf85-115">システム関数およびシステム型は非表示になりません。</span><span class="sxs-lookup"><span data-stu-id="cdf85-115">System functions and system data types are not hidden.</span></span> <span data-ttu-id="cdf85-116">このオプションは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにのみ適用され、既にオブジェクト エクスプローラーに接続されているサーバーに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="cdf85-116">This option only applies to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and does not affect servers already connected in Object Explorer.</span></span>  
  
## <a name="environment-layout"></a><span data-ttu-id="cdf85-117">[環境レイアウト]</span><span class="sxs-lookup"><span data-stu-id="cdf85-117">Environment Layout</span></span>  
 <span data-ttu-id="cdf85-118">タブ付きドキュメントとマルチ ドキュメント インターフェイス (MDI) 環境モードを切り替えるには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を閉じてから再度開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdf85-118">You must close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change between tabbed document and multiple-document interface (MDI) environment mode.</span></span>  
  
 <span data-ttu-id="cdf85-119">**[タブ付きドキュメント]**</span><span class="sxs-lookup"><span data-stu-id="cdf85-119">**Tabbed documents**</span></span>  
 <span data-ttu-id="cdf85-120">このオプションをオンにすると、エディター内にタブの付いたドキュメント ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-120">Select this option to display document windows that are tabbed together within editors.</span></span> <span data-ttu-id="cdf85-121">タブ付きドキュメント ウィンドウは、開いている複数のドキュメントの編成と切り替えを行う場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cdf85-121">Tabbed document windows are useful for organizing and switching between multiple open documents.</span></span>  
  
 <span data-ttu-id="cdf85-122">**[MDI 環境]**</span><span class="sxs-lookup"><span data-stu-id="cdf85-122">**MDI environment**</span></span>  
 <span data-ttu-id="cdf85-123">このオプションをオンにすると、MDI 環境でドキュメントが開きます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-123">Select this option to open documents in a MDI environment.</span></span> <span data-ttu-id="cdf85-124">MDI ドキュメント ウィンドウの利点は、タブ付きドキュメント環境でタブによって占有される画面領域を空き領域として確保できることです。</span><span class="sxs-lookup"><span data-stu-id="cdf85-124">MDI document windows are useful for gaining the screen space that is otherwise taken up by the tabs in the tabbed documents environment.</span></span> <span data-ttu-id="cdf85-125">MDI モードでの作業時にドキュメントを切り替えるには、Ctrl + Tab キーを押すか、 **[ウィンドウ]** メニューのタイル オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="cdf85-125">When working in MDI mode, you can switch between documents by pressing CTRL+TAB, or you can use the tile options located on the **Window** menu.</span></span>  
  
## <a name="docked-tool-window-behavior"></a><span data-ttu-id="cdf85-126">[ドッキング ツール ウィンドウの動作]</span><span class="sxs-lookup"><span data-stu-id="cdf85-126">Docked Tool Window Behavior</span></span>  
 <span data-ttu-id="cdf85-127">**[[閉じる] ボタンを、アクティブになっているタブに対してのみ実行する]**</span><span class="sxs-lookup"><span data-stu-id="cdf85-127">**Close button affects active tab only**</span></span>  
 <span data-ttu-id="cdf85-128">このチェック ボックスがオンになっている場合は、ドッキングしたセット内のすべてのツール ウィンドウではなく、現在フォーカスのあるツール ウィンドウのみを閉じることを指定します。</span><span class="sxs-lookup"><span data-stu-id="cdf85-128">Specifies that when this check box is selected, only the tool window that has focus currently is closed and not all of the tool windows in the docked set.</span></span> <span data-ttu-id="cdf85-129">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="cdf85-129">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="cdf85-130">**[[自動的に隠す] ボタンを、アクティブになっているタブに対してのみ実行する]**</span><span class="sxs-lookup"><span data-stu-id="cdf85-130">**Auto Hide button affects active tab only**</span></span>  
 <span data-ttu-id="cdf85-131">このチェック ボックスがオンになっている場合は、ドッキングしたセット内のすべてのツール ウィンドウではなく、現在フォーカスのあるツール ウィンドウのみが自動的に非表示になることを指定します。</span><span class="sxs-lookup"><span data-stu-id="cdf85-131">Specifies that when this check box is selected, only the tool window that has focus currently is hidden automatically, not all of the tool windows in the docked set.</span></span> <span data-ttu-id="cdf85-132">既定では、このチェック ボックスはオフに設定されます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-132">By default, this check box is cleared.</span></span>  
  
## <a name="display"></a><span data-ttu-id="cdf85-133">表示</span><span class="sxs-lookup"><span data-stu-id="cdf85-133">Display</span></span>  
 <span data-ttu-id="cdf85-134">**[最近使用したファイルの一覧: n ファイルまで表示する]**</span><span class="sxs-lookup"><span data-stu-id="cdf85-134">**Display n files in recently used list**</span></span>  
 <span data-ttu-id="cdf85-135">**[ファイル]** メニューに表示される最新プロジェクトおよび最新ファイルの数をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="cdf85-135">Customizes the number of recent projects and recent files that appear on the **File** menu.</span></span> <span data-ttu-id="cdf85-136">1 ～ 24 の範囲の数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="cdf85-136">Type a number between 1 and 24.</span></span> <span data-ttu-id="cdf85-137">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="cdf85-137">The default is 4.</span></span> <span data-ttu-id="cdf85-138">最近使用したスクリプト プロジェクトやファイル、その他のスクリプト プロジェクトを簡単に表示できます。</span><span class="sxs-lookup"><span data-stu-id="cdf85-138">This is an easy way to retrieve recently used script projects and files and script projects.</span></span>  
  
  
