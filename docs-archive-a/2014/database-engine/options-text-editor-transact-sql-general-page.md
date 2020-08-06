---
title: '[オプション] ([テキストエディター]/[Transact-sql]/[全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.General
dev_langs:
- TSQL
ms.assetid: 7021ecb7-8fb5-4d8c-b984-3d34fcde8be2
author: rothja
ms.author: jroth
ms.openlocfilehash: f008d0d84a15cfbf0bfa988232015e6619f4f5c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642959"
---
# <a name="options-text-editor---transact-sql--general-page"></a><span data-ttu-id="48708-102">[オプション] ([テキストエディター]/[Transact-sql]/[全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="48708-102">Options (Text Editor - Transact-SQL- General Page)</span></span>
  <span data-ttu-id="48708-103">[オプション] の **[全般]** ダイアログ ボックスを使用すると、 [!INCLUDE[ssDE](../includes/ssde-md.md)] スクリプトの編集に使用される [!INCLUDE[tsql](../includes/tsql-md.md)] クエリ エディターの全般的な編集の動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="48708-103">Use the **General** options dialog box to change the general editing behavior of the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor, which is used to edit [!INCLUDE[tsql](../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="48708-104">これらの設定を表示するには、**[ツール]** メニューの **[オプション]** をクリックし、**[Transact-SQL]** サブフォルダーを展開して、**[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48708-104">To display these settings, click **Options** on the **Tools** menu, expand the **Transact-SQL** subfolder, and then click **General**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="48708-105">複数の場所でのオプション設定</span><span class="sxs-lookup"><span data-stu-id="48708-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="48708-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターのオプションは、[すべての言語] の [全般] \*\*\*\* ダイアログで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="48708-106">Options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="48708-107">ただし、DMX エディターや MDX エディターなど、他の **エディターに対し、** [すべての言語] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のダイアログを使用して異なるオプションを設定する場合は、ここで紹介したダイアログを使用して [!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターのオプションを設定し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="48708-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor options using this dialog.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="48708-108">[入力候補]</span><span class="sxs-lookup"><span data-stu-id="48708-108">Statement Completion</span></span>  
 <span data-ttu-id="48708-109">**[自動メンバー表示]**</span><span class="sxs-lookup"><span data-stu-id="48708-109">**Auto list members**</span></span>  
 <span data-ttu-id="48708-110">このチェック ボックスがオンの場合、エディターでの入力に合わせて、使用できるデータベースとスキーマ オブジェクト、列、テーブル値関数、または関数の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48708-110">When this check box is selected, lists of available database and schema objects, columns, table-valued functions, or functions are displayed as you type in the editor.</span></span> <span data-ttu-id="48708-111">ポップアップ リストから項目を選択してコードに挿入します。</span><span class="sxs-lookup"><span data-stu-id="48708-111">Choose any item from the pop-up list to insert it into your code.</span></span>  
  
 <span data-ttu-id="48708-112">**[メンバーの詳細を非表示]**</span><span class="sxs-lookup"><span data-stu-id="48708-112">**Hide advanced members**</span></span>  
 <span data-ttu-id="48708-113">このチェック ボックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="48708-113">This check box is unavailable.</span></span>  
  
 <span data-ttu-id="48708-114">**パラメーター情報**</span><span class="sxs-lookup"><span data-stu-id="48708-114">**Parameter information**</span></span>  
 <span data-ttu-id="48708-115">このチェック ボックスがオンの場合、挿入ポイント (カーソル) のすぐ左側にあるストアド プロシージャまたは関数のパラメーター情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48708-115">When this check box is selected, parameter information is displayed for a stored procedure or function that is immediately to the left of the insertion point (cursor).</span></span> <span data-ttu-id="48708-116">この情報には、使用可能なパラメーターの名前とデータ型の一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48708-116">The information includes a list of the available parameters with their names and data types.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="48708-117">設定</span><span class="sxs-lookup"><span data-stu-id="48708-117">Settings</span></span>  
 <span data-ttu-id="48708-118">**[仮想空間を使用]**</span><span class="sxs-lookup"><span data-stu-id="48708-118">**Enable virtual space**</span></span>  
 <span data-ttu-id="48708-119">このチェック ボックスがオンの場合、コード行の末尾を越える任意の場所をクリックしてコメントを入力できます。</span><span class="sxs-lookup"><span data-stu-id="48708-119">When this check box is selected, you can click anywhere beyond the end of a line of code and type.</span></span> <span data-ttu-id="48708-120">コードの横の一定の場所にコメントを記述する場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="48708-120">Select this check box to position comments at a consistent point next to your code.</span></span> <span data-ttu-id="48708-121">このチェック ボックスをオンにすると、 **[右端で折り返す]** チェック ボックスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="48708-121">Selecting this check box disables the **Word wrap** check box.</span></span>  
  
 <span data-ttu-id="48708-122">**右端で折り返す**</span><span class="sxs-lookup"><span data-stu-id="48708-122">**Word wrap**</span></span>  
 <span data-ttu-id="48708-123">このチェック ボックスがオンの場合、表示可能なエディター領域の幅からはみ出した行を次の行に折り返して表示します。</span><span class="sxs-lookup"><span data-stu-id="48708-123">When this check box is selected, any portion of a line that extends horizontally beyond the viewable editor area is automatically displayed on the next line.</span></span> <span data-ttu-id="48708-124">このチェック ボックスをオンにすると、 **[右端の折り返しの記号を表示する]** チェック ボックスが有効になり、 **[仮想空間を使用]** チェック ボックスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="48708-124">Selecting this check box enables the **Show visual glyphs for word wrap** check box and disables the **Enable virtual space** check box.</span></span>  
  
 <span data-ttu-id="48708-125">**[右端の折り返しの記号を表示する]**</span><span class="sxs-lookup"><span data-stu-id="48708-125">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="48708-126">このチェック ボックスがオンの場合、長い行が次の行に折り返される場所に改行インジケーターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48708-126">When this check box is selected, a return arrow indicator is displayed where a long line wraps to the next line.</span></span>  
  
 <span data-ttu-id="48708-127">**[選択領域がない場合は、切り取りまたはコピー コマンドを空白行に適用する]**</span><span class="sxs-lookup"><span data-stu-id="48708-127">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="48708-128">このチェック ボックスは、空白行にカーソルを置き、何も選択していない状態で **[コピー]** または **[切り取り]** をクリックしたときのエディターの動作を設定します。</span><span class="sxs-lookup"><span data-stu-id="48708-128">This check box sets the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="48708-129">このチェック ボックスがオンの場合、空白行がコピーまたは切り取られます。</span><span class="sxs-lookup"><span data-stu-id="48708-129">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="48708-130">その後で **[貼り付け]** をクリックすると、新しい空白行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="48708-130">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="48708-131">このチェック ボックスがオフの場合、何もコピーまたは切り取られません。</span><span class="sxs-lookup"><span data-stu-id="48708-131">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="48708-132">その後で **[貼り付け]** をクリックすると、最後にコピーした内容が貼り付けられます。</span><span class="sxs-lookup"><span data-stu-id="48708-132">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="48708-133">それまでに何もコピーされていない場合は、何も貼り付けられません。</span><span class="sxs-lookup"><span data-stu-id="48708-133">If nothing has been copied previously, nothing is pasted.</span></span>  
  
 <span data-ttu-id="48708-134">行が空白でない場合、 **[コピー]** または **[切り取り]** の動作はこの設定の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="48708-134">This setting has no effect on **Copy** or **Cut** when a line is not blank.</span></span> <span data-ttu-id="48708-135">何も選択されていない場合、行全体がコピーまたは切り取られます。</span><span class="sxs-lookup"><span data-stu-id="48708-135">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="48708-136">その後で **[貼り付け]** をクリックすると、行全体のテキストと行末文字が貼り付けられます。</span><span class="sxs-lookup"><span data-stu-id="48708-136">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="48708-137">表示</span><span class="sxs-lookup"><span data-stu-id="48708-137">Display</span></span>  
 <span data-ttu-id="48708-138">**行番号**</span><span class="sxs-lookup"><span data-stu-id="48708-138">**Line numbers**</span></span>  
 <span data-ttu-id="48708-139">このチェック ボックスがオンの場合、各コード行の横に行番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48708-139">When this check box is selected, a line number appears next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48708-140">この行番号はコードに追加されているわけではないので、印刷されません。</span><span class="sxs-lookup"><span data-stu-id="48708-140">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="48708-141">これは単に表示用です。</span><span class="sxs-lookup"><span data-stu-id="48708-141">They are for reference only.</span></span>  
  
 <span data-ttu-id="48708-142">**[シングル クリックでの URL ナビゲーションを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="48708-142">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="48708-143">このチェック ボックスがオンの場合、エディター内で URL 上にカーソルを移動すると、カーソルが指差しカーソルに変わります。</span><span class="sxs-lookup"><span data-stu-id="48708-143">When this check box is selected, the cursor changes to a pointing hand as it passes over a URL in the editor.</span></span> <span data-ttu-id="48708-144">URL をクリックすると、該当するページが Web ブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="48708-144">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="48708-145">**ナビゲーションバー**</span><span class="sxs-lookup"><span data-stu-id="48708-145">**Navigation bar**</span></span>  
 <span data-ttu-id="48708-146">このチェック ボックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="48708-146">This check box is unavailable.</span></span>  
  
  
