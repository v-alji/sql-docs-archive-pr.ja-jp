---
title: '[オプション] ([テキストエディター]/[Transact-sql]/[タブ] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Tabs
dev_langs:
- TSQL
ms.assetid: a4499784-67f7-46ef-9f7c-2d0fdd117a52
author: rothja
ms.author: jroth
ms.openlocfilehash: 6caa659d13f8089fdd9f990a55e503657ef72a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642953"
---
# <a name="options-text-editor---transact-sql---tabs-page"></a><span data-ttu-id="ca40a-102">[オプション] ([テキストエディター]/[Transact-sql]/[タブ] ページ)</span><span class="sxs-lookup"><span data-stu-id="ca40a-102">Options (Text Editor - Transact-SQL - Tabs Page)</span></span>
  <span data-ttu-id="ca40a-103">このダイアログ ボックスを使用すると、[!INCLUDE[ssDE](../includes/ssde-md.md)] スクリプトのプログラミングに使用される[!INCLUDE[tsql](../includes/tsql-md.md)] クエリ エディターのタブの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ca40a-103">Use this dialog to change the tabbing behavior of the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor, which is used to program [!INCLUDE[tsql](../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="ca40a-104">この設定を表示するには、**[ツール]** メニューの **[オプション]** をクリックして、**[テキスト エディター]** フォルダーを展開し、さらに **[Transact-SQL]** サブフォルダーを展開して、**[タブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca40a-104">To display these settings, click **Options** on the **Tools** menu, expand the **Text Editor** folder, expand the **Transact-SQL** subfolder and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="ca40a-105">複数の場所でのオプション設定</span><span class="sxs-lookup"><span data-stu-id="ca40a-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="ca40a-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターのオプションは、**[すべての言語] の [タブ]** ダイアログで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ca40a-106">Options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor can also be set in the **All Languages Tabs** dialog.</span></span> <span data-ttu-id="ca40a-107">ただし、DMX エディターや MDX エディターなど、他の **エディターに対し、** [すべての言語] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のダイアログを使用して異なるオプションを設定する場合は、ここで紹介したダイアログを使用して [!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターのオプションを設定し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca40a-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="ca40a-108">インデント</span><span class="sxs-lookup"><span data-stu-id="ca40a-108">Indenting</span></span>  
 <span data-ttu-id="ca40a-109">**なし**</span><span class="sxs-lookup"><span data-stu-id="ca40a-109">**None**</span></span>  
 <span data-ttu-id="ca40a-110">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、インデントされません。</span><span class="sxs-lookup"><span data-stu-id="ca40a-110">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="ca40a-111">カーソルは、新しい行の 1 列目に置かれます。</span><span class="sxs-lookup"><span data-stu-id="ca40a-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="ca40a-112">**ブロック**</span><span class="sxs-lookup"><span data-stu-id="ca40a-112">**Block**</span></span>  
 <span data-ttu-id="ca40a-113">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、直前の行と同じ位置まで自動的にインデントされます。</span><span class="sxs-lookup"><span data-stu-id="ca40a-113">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line.</span></span>  
  
 <span data-ttu-id="ca40a-114">**[スマート]**</span><span class="sxs-lookup"><span data-stu-id="ca40a-114">**Smart**</span></span>  
 <span data-ttu-id="ca40a-115">このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ca40a-115">This option is unavailable.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="ca40a-116">タブ</span><span class="sxs-lookup"><span data-stu-id="ca40a-116">Tabs</span></span>  
 <span data-ttu-id="ca40a-117">**[タブ サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ca40a-117">**Tab size**</span></span>  
 <span data-ttu-id="ca40a-118">タブ ストップ間の間隔をスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="ca40a-118">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="ca40a-119">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="ca40a-119">The default is four spaces.</span></span>  
  
 <span data-ttu-id="ca40a-120">**[インデント サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ca40a-120">**Indent size**</span></span>  
 <span data-ttu-id="ca40a-121">自動インデントのサイズをスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="ca40a-121">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="ca40a-122">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="ca40a-122">The default is four spaces.</span></span> <span data-ttu-id="ca40a-123">指定されたサイズになるように、タブ文字、スペース文字、またはその両方が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ca40a-123">Tab characters, space characters, or both are inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="ca40a-124">**[空白の挿入]**</span><span class="sxs-lookup"><span data-stu-id="ca40a-124">**Insert spaces**</span></span>  
 <span data-ttu-id="ca40a-125">このオプションを選択すると、タブ文字を使用せずにスペース文字だけを挿入してインデントします。</span><span class="sxs-lookup"><span data-stu-id="ca40a-125">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="ca40a-126">たとえば、[**インデントサイズ**] が5に設定されている場合、tab キーを押すか、メインウィンドウのツールバーの [**インデント**] ボタンをクリックするたびに、5つのスペース文字が挿入され [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ca40a-126">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar in the main [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] window.</span></span>  
  
 <span data-ttu-id="ca40a-127">**[タブの保持]**</span><span class="sxs-lookup"><span data-stu-id="ca40a-127">**Keep tabs**</span></span>  
 <span data-ttu-id="ca40a-128">このオプションを選択すると、インデントするときにできる限り多くのタブ文字を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ca40a-128">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="ca40a-129">それぞれのタブ文字が、[ **タブ サイズ**] で指定された数のスペースを満たします。</span><span class="sxs-lookup"><span data-stu-id="ca40a-129">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="ca40a-130">[ **インデント サイズ** ] が [ **タブ サイズ**] の倍数でない場合は、その差を埋めるためにスペース文字が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ca40a-130">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
