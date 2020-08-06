---
title: エディターと表示モードの管理
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], managing window behavior
- workbench view modes [SQL Server Management Studio]
- full screen mode [SQL Server Management Studio]
- fonts [SQL Server Management Studio]
- word wraps [SQL Server Management Studio]
- virtual space mode [SQL Server Management Studio]
- splitting document views
- displaying line numbers
- view modes [SQL Server Management Studio]
ms.assetid: 25c58a14-9f94-4296-9770-7d84c6bc3969
author: rothja
ms.author: jroth
ms.openlocfilehash: 36788b1fe831a6c15c4aa0668d1759c088fcaa73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644428"
---
# <a name="manage-the-editor-and-view-mode"></a><span data-ttu-id="899a2-102">エディターと表示モードの管理</span><span class="sxs-lookup"><span data-stu-id="899a2-102">Manage the Editor and View Mode</span></span>
  <span data-ttu-id="899a2-103">エディターには、コードの表示を制御するさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="899a2-103">The Editor gives you a number of ways to control the view of your code.</span></span>  
  
## <a name="changing-the-view-mode"></a><span data-ttu-id="899a2-104">表示モードの変更</span><span class="sxs-lookup"><span data-stu-id="899a2-104">Changing the View Mode</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="899a2-105">には、 **タブ付きドキュメント**という表示モードが用意されています。タブ付きドキュメントにより、複数のエディターやドキュメントを同時に開くことができ、エディター上部のタブを利用してこれらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="899a2-105">features a view mode called **Tabbed Documents**, which allows you to open multiple editors and documents simultaneously and access them through tabs at the top of the Editor.</span></span> <span data-ttu-id="899a2-106">また、マルチドキュメント インターフェイス (MDI) モードで [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開くこともできます。この場合は、タブなしでウィンドウが統合され、各ウィンドウを並べて表示したり、最小化したりすることが可能になります。</span><span class="sxs-lookup"><span data-stu-id="899a2-106">You can alternatively open the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] environment in Multiple Document Interface (MDI) mode, which joins windows without the tabs, and allows each window to be tiled, minimized, and so on.</span></span>  
  
#### <a name="to-switch-between-view-modes"></a><span data-ttu-id="899a2-107">表示モードを切り替えるには</span><span class="sxs-lookup"><span data-stu-id="899a2-107">To switch between view modes</span></span>  
  
1.  <span data-ttu-id="899a2-108">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-108">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="899a2-109">**[環境]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-109">Click **Environment**.</span></span> <span data-ttu-id="899a2-110">**[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-110">Click **General**.</span></span>  
  
3.  <span data-ttu-id="899a2-111">**[タブ付きドキュメント]** または **[MDI 環境]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-111">Click **Tabbed documents** or **MDI environment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="899a2-112">変更内容を有効にするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="899a2-112">The changes will not take effect until [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is restarted.</span></span>  
  
## <a name="splitting-the-view"></a><span data-ttu-id="899a2-113">表示の分割</span><span class="sxs-lookup"><span data-stu-id="899a2-113">Splitting the View</span></span>  
 <span data-ttu-id="899a2-114">編集をしやすくするために、エディター ウィンドウを 2 つに分割することもできます。</span><span class="sxs-lookup"><span data-stu-id="899a2-114">An Editor window can be split into two separate parts for easier editing.</span></span>  
  
#### <a name="to-split-a-window"></a><span data-ttu-id="899a2-115">ウィンドウを分割するには</span><span class="sxs-lookup"><span data-stu-id="899a2-115">To split a window</span></span>  
  
1.  <span data-ttu-id="899a2-116">スクロール バーの上にある分割バーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-116">Click the splitter bar (located above the scroll bar).</span></span>  
  
2.  <span data-ttu-id="899a2-117">分割バーを下にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="899a2-117">Drag the splitter bar downward.</span></span>  
  
3.  <span data-ttu-id="899a2-118">単一のペインに戻すには、2 つのペインに分割している分割バーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-118">To go back to a single pane, double-click the splitter bar dividing the two panes.</span></span>  
  
 <span data-ttu-id="899a2-119">新しいペインには同じドキュメントが含まれているので、そのペインにドキュメント内の同じ場所が表示されている間は、1 つのペインに対して行われた変更が他のペインに反映されます。</span><span class="sxs-lookup"><span data-stu-id="899a2-119">The new pane contains the same document, and any changes made to one pane are reflected in the other pane as long as that pane displays the same place in the document.</span></span>  
  
## <a name="word-wrap"></a><span data-ttu-id="899a2-120">右端で折り返す</span><span class="sxs-lookup"><span data-stu-id="899a2-120">Word Wrap</span></span>  
 <span data-ttu-id="899a2-121">[右端で折り返す] を有効にすると、水平スクロール バーが取り除かれ、エディターのウィンドウ幅を超えるコード行は、自動的に折り返されて次の行に表示されるので、表示できない部分がウィンドウの端に隠れてしまうことはありません。</span><span class="sxs-lookup"><span data-stu-id="899a2-121">When you activate Word Wrap, the horizontal scrollbar is removed and lines of code that exceed the width of the Editor's window size automatically wraps to the next displayed line rather than scrolling off the side of the window.</span></span>  
  
#### <a name="to-activate-word-wrap"></a><span data-ttu-id="899a2-122">右端で折り返す機能を有効にするには</span><span class="sxs-lookup"><span data-stu-id="899a2-122">To activate word wrap</span></span>  
  
1.  <span data-ttu-id="899a2-123">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-123">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="899a2-124">**[テキスト エディター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-124">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="899a2-125">適切な言語フォルダーを開きます (または **[すべての言語]** ですべての言語を対象にします)。</span><span class="sxs-lookup"><span data-stu-id="899a2-125">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="899a2-126">**[右端で折り返す]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="899a2-126">Select **Word wrap**.</span></span>  
  
## <a name="enabling-virtual-space-mode"></a><span data-ttu-id="899a2-127">仮想空間モードの有効化</span><span class="sxs-lookup"><span data-stu-id="899a2-127">Enabling Virtual Space Mode</span></span>  
 <span data-ttu-id="899a2-128">**仮想空間** モードの場合、エディターは、各行の終わり以降の空間が無数のスペースで埋められているかのような処理を行い、コード行は画面の表示可能領域を超えて 1 行で表示されます。</span><span class="sxs-lookup"><span data-stu-id="899a2-128">In **Virtual Space** mode, the Editor acts as if the space past the end of each line is filled with an infinite number of spaces, allowing code lines to continue off the side of the visible screen area.</span></span>  
  
#### <a name="to-enable-virtual-space-mode"></a><span data-ttu-id="899a2-129">仮想空間モードを有効にするには</span><span class="sxs-lookup"><span data-stu-id="899a2-129">To enable Virtual Space mode</span></span>  
  
1.  <span data-ttu-id="899a2-130">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-130">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="899a2-131">**[テキスト エディター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-131">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="899a2-132">適切な言語フォルダーを開きます (または **[すべての言語]** ですべての言語を対象にします)。</span><span class="sxs-lookup"><span data-stu-id="899a2-132">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="899a2-133">**[仮想空間を使用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="899a2-133">Select **Enable virtual space**.</span></span>  
  
 <span data-ttu-id="899a2-134">仮想空間モードが無効な場合、カーソルは、ある行の最後から次の行の最初の文字に折り返されます。逆の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="899a2-134">When Virtual Space mode is not enabled, the cursor wraps from the end of one line to the first character of the next line and vice-versa.</span></span>  
  
## <a name="displaying-line-numbers"></a><span data-ttu-id="899a2-135">行番号の表示</span><span class="sxs-lookup"><span data-stu-id="899a2-135">Displaying Line Numbers</span></span>  
 <span data-ttu-id="899a2-136">コード行に行番号を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="899a2-136">You can turn on line numbering in your code.</span></span> <span data-ttu-id="899a2-137">行番号は、コード内を移動する際に便利です。</span><span class="sxs-lookup"><span data-stu-id="899a2-137">Line numbers are useful for navigating code.</span></span> <span data-ttu-id="899a2-138">詳細については、「 [コード内とテキスト内の移動](navigate-code-and-text.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="899a2-138">For more information, see [Navigate Code and Text](navigate-code-and-text.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="899a2-139">行番号を有効にしても、ドキュメントの印刷時に行番号が印刷されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="899a2-139">Turning on line numbering does not mean that the document will print with line numbers.</span></span> <span data-ttu-id="899a2-140">行番号を印刷するには、 **[ファイル]** メニューの **[ページ設定]** コマンドを選択し、 **[行番号]** チェック ボックスをオンにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="899a2-140">For line numbers to print, you must select the **Line numbers** check box in the **Page Setup** command on the **File** menu.</span></span>  
  
#### <a name="to-display-line-numbers-in-code"></a><span data-ttu-id="899a2-141">コードの行番号を表示するには</span><span class="sxs-lookup"><span data-stu-id="899a2-141">To display line numbers in code</span></span>  
  
1.  <span data-ttu-id="899a2-142">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-142">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="899a2-143">**[テキスト エディター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-143">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="899a2-144">**[すべての言語]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-144">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="899a2-145">**[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="899a2-145">Click **General**.</span></span>  
  
5.  <span data-ttu-id="899a2-146">**[行番号]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="899a2-146">Select **Line numbers**.</span></span>  
  
 <span data-ttu-id="899a2-147">一部のプログラミング言語のみで行番号を指定するには、該当する言語フォルダーの **[行番号]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="899a2-147">To specify line numbering for only some programming languages, select **Line Numbers** in the appropriate folder.</span></span>  
  
## <a name="enabling-full-screen-mode"></a><span data-ttu-id="899a2-148">全画面モードの有効化</span><span class="sxs-lookup"><span data-stu-id="899a2-148">Enabling Full Screen Mode</span></span>  
 <span data-ttu-id="899a2-149">全画面モードを有効にすると、すべてのツール ウィンドウが隠れて、ドキュメント ウィンドウだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="899a2-149">You can choose to hide all tool windows and view only document windows by enabling Full Screen mode.</span></span>  
  
#### <a name="to-enable-full-screen-mode"></a><span data-ttu-id="899a2-150">全画面モードを有効にするには</span><span class="sxs-lookup"><span data-stu-id="899a2-150">To enable Full Screen mode</span></span>  
  
1.  <span data-ttu-id="899a2-151">Alt キーと Shift キーを押しながら Enter キーを押すと、全画面モードが有効または無効になります。</span><span class="sxs-lookup"><span data-stu-id="899a2-151">Press ALT+SHIFT+ENTER to toggle Full Screen mode.</span></span>  
  
## <a name="using-auto-hide-all"></a><span data-ttu-id="899a2-152">[すべて自動的に隠す] の使用</span><span class="sxs-lookup"><span data-stu-id="899a2-152">Using Auto Hide All</span></span>  
  
#### <a name="to-hide-all-the-tool-windows-at-once"></a><span data-ttu-id="899a2-153">すべてのツール ウィンドウを一度に隠すには</span><span class="sxs-lookup"><span data-stu-id="899a2-153">To hide all the tool windows at once</span></span>  
  
1.  <span data-ttu-id="899a2-154">**[ウィンドウ]** メニューの **[すべて自動的に隠す]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="899a2-154">Select **Auto Hide All** on the **Window** menu.</span></span>  
  
  
