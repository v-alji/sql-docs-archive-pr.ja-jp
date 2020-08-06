---
title: '[オプション] ([テキストエディター]: [XML]: [タブ] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 3047d6c05ffb88d07a4bf2e5b1d4143412046c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711001"
---
# <a name="options-text-editorxmltabs-page"></a><span data-ttu-id="6205f-102">[オプション] ([テキスト エディター]: [XML]: [タブ] ページ)</span><span class="sxs-lookup"><span data-stu-id="6205f-102">Options (Text Editor:XML:Tabs Page)</span></span>
  <span data-ttu-id="6205f-103">このダイアログ ボックスを使用すると、XML ドキュメントの編集に使用される XML エディターのタブの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="6205f-103">This dialog box lets you change the tabbing behavior of the XML Editor, which is used to edit XML documents.</span></span> <span data-ttu-id="6205f-104">この設定を表示するには、[ **ツール** ] メニューの [ **オプション** ] をクリックして、[ **テキスト エディター** ] フォルダーを展開し、さらに [ **XML** ] サブフォルダーを展開して、[ **タブ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6205f-104">To display these settings, click **Options** on the **Tools** menu, expand the **Text Editor** folder, expand the **XML** subfolder and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="6205f-105">複数の場所でのオプション設定</span><span class="sxs-lookup"><span data-stu-id="6205f-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="6205f-106">XML エディターのオプションは、[すべての言語] の [全般] \*\*\*\* ダイアログで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="6205f-106">Options for the XML Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="6205f-107">ただし、DMX エディターや MDX エディターなど、他の **エディターに対し、** [すべての言語] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のダイアログを使用して異なるオプションを設定する場合は、ここで紹介したダイアログを使用して XML エディターのオプションを設定し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6205f-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the XML Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="6205f-108">インデント</span><span class="sxs-lookup"><span data-stu-id="6205f-108">Indenting</span></span>  
 <span data-ttu-id="6205f-109">**なし**</span><span class="sxs-lookup"><span data-stu-id="6205f-109">**None**</span></span>  
 <span data-ttu-id="6205f-110">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、インデントされません。</span><span class="sxs-lookup"><span data-stu-id="6205f-110">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="6205f-111">カーソルは、新しい行の 1 列目に置かれます。</span><span class="sxs-lookup"><span data-stu-id="6205f-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="6205f-112">**ブロック**</span><span class="sxs-lookup"><span data-stu-id="6205f-112">**Block**</span></span>  
 <span data-ttu-id="6205f-113">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、直前の行と同じ位置まで自動的にインデントされます。</span><span class="sxs-lookup"><span data-stu-id="6205f-113">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line.</span></span>  
  
 <span data-ttu-id="6205f-114">**[スマート]**</span><span class="sxs-lookup"><span data-stu-id="6205f-114">**Smart**</span></span>  
 <span data-ttu-id="6205f-115">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行の位置は、コンテキストに応じて決定されます。</span><span class="sxs-lookup"><span data-stu-id="6205f-115">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span> <span data-ttu-id="6205f-116">たとえば、左中かっこ ({) の後では、かっこで囲まれる行は自動的にタブ 1 個を追加してインデントされます。</span><span class="sxs-lookup"><span data-stu-id="6205f-116">For example, after an opening brace ({), the included lines are automatically indented an extra tab stop.</span></span> <span data-ttu-id="6205f-117">対応する右中かっこ (}) は、左中かっこに合わせた位置に置かれます。</span><span class="sxs-lookup"><span data-stu-id="6205f-117">The matching closing brace (}) is realigned with its opening brace.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="6205f-118">タブ</span><span class="sxs-lookup"><span data-stu-id="6205f-118">Tabs</span></span>  
 <span data-ttu-id="6205f-119">**[タブ サイズ]**</span><span class="sxs-lookup"><span data-stu-id="6205f-119">**Tab size**</span></span>  
 <span data-ttu-id="6205f-120">タブ ストップ間の間隔をスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="6205f-120">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="6205f-121">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="6205f-121">The default is four spaces.</span></span>  
  
 <span data-ttu-id="6205f-122">**[インデント サイズ]**</span><span class="sxs-lookup"><span data-stu-id="6205f-122">**Indent size**</span></span>  
 <span data-ttu-id="6205f-123">自動インデントのサイズをスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="6205f-123">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="6205f-124">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="6205f-124">The default is four spaces.</span></span> <span data-ttu-id="6205f-125">指定されたサイズになるように、タブ文字、スペース文字、またはその両方が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="6205f-125">Tab characters, space characters, or both are inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="6205f-126">**[空白の挿入]**</span><span class="sxs-lookup"><span data-stu-id="6205f-126">**Insert spaces**</span></span>  
 <span data-ttu-id="6205f-127">このオプションを選択すると、タブ文字を使用せずにスペース文字だけを挿入してインデントします。</span><span class="sxs-lookup"><span data-stu-id="6205f-127">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="6205f-128">たとえば、[**インデントサイズ**] が5に設定されている場合、tab キーを押すか、メインウィンドウのツールバーの [**インデント**] ボタンをクリックするたびに、5つのスペース文字が挿入され [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6205f-128">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar in the main [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] window.</span></span>  
  
 <span data-ttu-id="6205f-129">**[タブの保持]**</span><span class="sxs-lookup"><span data-stu-id="6205f-129">**Keep tabs**</span></span>  
 <span data-ttu-id="6205f-130">このオプションを選択すると、インデントするときにできる限り多くのタブ文字を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6205f-130">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="6205f-131">それぞれのタブ文字が、[ **タブ サイズ**] で指定された数のスペースを満たします。</span><span class="sxs-lookup"><span data-stu-id="6205f-131">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="6205f-132">[ **インデント サイズ** ] が [ **タブ サイズ**] の倍数でない場合は、その差を埋めるためにスペース文字が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6205f-132">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
