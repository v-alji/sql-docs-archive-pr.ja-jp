---
title: '[オプション] ([テキストエディター]/[XML]/[全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 46a9f913-d0b9-40ff-b382-9bbdec7461a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 70d7f3130342a6b8ac7e92e1eaf3e89869ff4148
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711010"
---
# <a name="options-text-editor---xml---general-page"></a><span data-ttu-id="aa0e0-102">[オプション] ([テキスト エディター]/[XML]/[全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="aa0e0-102">Options (Text Editor - XML - General Page)</span></span>
  <span data-ttu-id="aa0e0-103">このダイアログ ボックスを使用すると、XML ドキュメントの編集に使用される XML エディターの全般的な編集の動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-103">Use this dialog to change the general editing behavior of the XML Editor, which is used to edit XML documents.</span></span> <span data-ttu-id="aa0e0-104">これらの設定を変更するには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[XML]** サブフォルダーを展開します。次に、 **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-104">To display these settings, click **Options** on the **Tools** menu, expand the **XML** subfolder, and then click **General**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="aa0e0-105">複数の場所でのオプション設定</span><span class="sxs-lookup"><span data-stu-id="aa0e0-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="aa0e0-106">XML エディターのオプションは、[すべての言語] の [全般] \*\*\*\* ダイアログで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-106">Options for the XML Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="aa0e0-107">ただし、DMX エディターや MDX エディターなど、他の **エディターに対し、** [すべての言語] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のダイアログを使用して異なるオプションを設定する場合は、ここで紹介したダイアログを使用して XML エディターのオプションを設定し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the XML Editor options using this dialog.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="aa0e0-108">[入力候補]</span><span class="sxs-lookup"><span data-stu-id="aa0e0-108">Statement Completion</span></span>  
 <span data-ttu-id="aa0e0-109">**[自動メンバー表示]**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-109">**Auto list members**</span></span>  
 <span data-ttu-id="aa0e0-110">このチェック ボックスがオンの場合、エディターでの入力に合わせて、使用できるメンバー、プロパティ、値、またはメソッドの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-110">When this check box is selected, lists of available members, properties, values, or methods are displayed as you type in the editor.</span></span> <span data-ttu-id="aa0e0-111">ポップアップ リストから項目を選択してコードに挿入します。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-111">Choose any item from the pop-up list to insert it into your code.</span></span>  
  
 <span data-ttu-id="aa0e0-112">**[メンバーの詳細を非表示]**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-112">**Hide advanced members**</span></span>  
 <span data-ttu-id="aa0e0-113">このチェック ボックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-113">This check box is unavailable.</span></span>  
  
 <span data-ttu-id="aa0e0-114">**パラメーター情報**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-114">**Parameter information**</span></span>  
 <span data-ttu-id="aa0e0-115">このチェック ボックスがオンの場合、エディター内の挿入ポイントの左側に、現在の宣言またはプロシージャの完全な構文が、使用可能なすべてのパラメーターと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-115">When this check box is selected, the complete syntax for the current declaration or procedure is displayed to the left of the insertion point in the editor, with all of its available parameters.</span></span> <span data-ttu-id="aa0e0-116">割り当て可能な次のパラメーターは、太字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-116">The next parameter you can assign is displayed in bold.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="aa0e0-117">設定</span><span class="sxs-lookup"><span data-stu-id="aa0e0-117">Settings</span></span>  
 <span data-ttu-id="aa0e0-118">**[仮想空間を使用]**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-118">**Enable virtual space**</span></span>  
 <span data-ttu-id="aa0e0-119">このチェック ボックスがオンの場合、各コード行の末尾にスペースが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-119">When this check box is selected, spaces are inserted at the end of each line of code.</span></span> <span data-ttu-id="aa0e0-120">コードの横の一定の場所にコメントを記述する場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-120">Select this check box to position comments at a consistent point next to your code.</span></span>  
  
 <span data-ttu-id="aa0e0-121">**右端で折り返す**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-121">**Word wrap**</span></span>  
 <span data-ttu-id="aa0e0-122">このチェック ボックスがオンの場合、表示可能なエディター領域の幅からはみ出した行を次の行に折り返して表示します。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-122">When this check box is selected, any portion of a line that extends horizontally beyond the viewable editor area is automatically displayed on the next line.</span></span> <span data-ttu-id="aa0e0-123">このチェック ボックスをオンにすると、 **[右端の折り返しの記号を表示する]** チェック ボックスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-123">Selecting this check box enables the **Show visual glyphs for word wrap** check box.</span></span>  
  
 <span data-ttu-id="aa0e0-124">**[右端の折り返しの記号を表示する]**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-124">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="aa0e0-125">このチェック ボックスがオンの場合、改行が行われている箇所に矢印形の改行インジケーターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-125">When this check box is selected, a return-arrow indicator is displayed where a long line wraps onto a second line.</span></span> <span data-ttu-id="aa0e0-126">このインジケーターを表示しないようにするには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-126">Clear this check box if you prefer not to display these indicators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa0e0-127">改行インジケーターはコードに追加されているわけではないので、印刷されません。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-127">These reminder arrows are not added to your code, and they do not print.</span></span> <span data-ttu-id="aa0e0-128">これは単に表示用です。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-128">They are for reference only.</span></span>  
  
 <span data-ttu-id="aa0e0-129">**[選択領域がない場合は、切り取りまたはコピー コマンドを空白行に適用する]**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-129">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="aa0e0-130">このチェック ボックスは、空白行にカーソルを置き、何も選択していない状態で **[コピー]** または **[切り取り]** をクリックしたときのエディターの動作を設定します。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-130">This check box sets the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="aa0e0-131">このチェック ボックスがオンの場合、空白行がコピーまたは切り取られます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-131">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="aa0e0-132">その後で **[貼り付け]** をクリックすると、新しい空白行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-132">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="aa0e0-133">このチェック ボックスがオフの場合、何もコピーまたは切り取られません。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-133">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="aa0e0-134">その後で **[貼り付け]** をクリックすると、最後にコピーした内容が貼り付けられます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-134">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="aa0e0-135">それまでに何もコピーされていない場合は、何も貼り付けられません。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-135">If nothing has been copied previously, nothing is pasted.</span></span>  
  
 <span data-ttu-id="aa0e0-136">行が空白でない場合、 **[コピー]** または **[切り取り]** の動作はこの設定の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-136">This setting has no effect on **Copy** or **Cut** when a line is not blank.</span></span> <span data-ttu-id="aa0e0-137">何も選択されていない場合、行全体がコピーまたは切り取られます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-137">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="aa0e0-138">その後で **[貼り付け]** をクリックすると、行全体のテキストと行末文字が貼り付けられます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-138">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="aa0e0-139">表示</span><span class="sxs-lookup"><span data-stu-id="aa0e0-139">Display</span></span>  
 <span data-ttu-id="aa0e0-140">**行番号**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-140">**Line numbers**</span></span>  
 <span data-ttu-id="aa0e0-141">このチェック ボックスがオンの場合、各コード行の横に行番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-141">When this check box is selected, a line number appears next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa0e0-142">この行番号はコードに追加されているわけではないので、印刷されません。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-142">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="aa0e0-143">これは単に表示用です。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-143">They are for reference only.</span></span>  
  
 <span data-ttu-id="aa0e0-144">**[シングル クリックでの URL ナビゲーションを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-144">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="aa0e0-145">このチェック ボックスがオンの場合、エディター内で URL 上にカーソルを移動すると、カーソルが指差しカーソルに変わります。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-145">When this check box is selected, the cursor changes to a pointing hand as it passes over a URL in the editor.</span></span> <span data-ttu-id="aa0e0-146">URL をクリックすると、該当するページが Web ブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-146">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="aa0e0-147">**ナビゲーションバー**</span><span class="sxs-lookup"><span data-stu-id="aa0e0-147">**Navigation bar**</span></span>  
 <span data-ttu-id="aa0e0-148">このチェック ボックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa0e0-148">This check box is unavailable.</span></span>  
  
  
