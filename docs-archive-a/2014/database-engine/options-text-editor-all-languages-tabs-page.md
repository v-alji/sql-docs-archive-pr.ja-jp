---
title: '[オプション] ([テキストエディター]/[すべての言語]/[タブ] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 13f791e34b2099e8c0492c25886ee6b37ef1a1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644134"
---
# <a name="options-text-editor---all-languages--tabs-page"></a><span data-ttu-id="33349-102">[オプション] ([テキスト エディター]/[すべての言語] - [タブ] ページ)</span><span class="sxs-lookup"><span data-stu-id="33349-102">Options (Text Editor - All Languages -Tabs Page)</span></span>
  <span data-ttu-id="33349-103">このダイアログ ボックスを使用すると、全部で 5 つある [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のすべてのエディターのタブの動作を設定できます。</span><span class="sxs-lookup"><span data-stu-id="33349-103">Use this dialog box to set the tabbing behavior in all five of the editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="33349-104">これらのオプションを表示するには、**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33349-104">To display these options, click **Options** on the **Tools** menu.</span></span> <span data-ttu-id="33349-105">**[テキスト エディター]** フォルダーを選択し、**[すべての言語]** フォルダーを展開して、**[タブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33349-105">Select the **Text Editor** folder, expand the **All Languages** folder and then click **Tabs**.</span></span>  
  
## <a name="tabbing-options-by-editor"></a><span data-ttu-id="33349-106">エディターごとのタブ関連オプション</span><span class="sxs-lookup"><span data-stu-id="33349-106">Tabbing Options by Editor</span></span>  
 <span data-ttu-id="33349-107">DMX エディター、MDX エディター、および SQL Server Compact エディターに対するオプションは、**[すべての言語]** ダイアログを使用して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33349-107">You must use the **All Languages** dialogs to set options for the DMX, MDX, and SQL Server Compact editors.</span></span> <span data-ttu-id="33349-108">ここで設定したオプションは、テキスト形式、Transact-SQL、および XML の各エディターにも適用されます。ただし、対応する言語のサブフォルダーを展開し、そのオプション ページを選択すると、個々のエディター単位でオプションを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="33349-108">Options set here are also applied to the Plain Text, Transact-SQL, and XML editors, but you can set options separately for those editors by expanding the subfolders for those languages and selecting their option pages.</span></span> <span data-ttu-id="33349-109">タブ関連のオプションがサポートされない言語もあります。</span><span class="sxs-lookup"><span data-stu-id="33349-109">Some languages do not support all of the tabbing options.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="33349-110">このダイアログを使用してオプションを設定する場合で、なおかつプレーンテキスト、Transact-SQL、XML の各エディターに対して異なる設定を使用する必要がある場合は、**[すべての言語]** ダイアログで必要な設定を適用したうえで、それぞれのエディターのオプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33349-110">If you set an option using this dialog, but want a different setting for the Plain Text, Transact-SQL, or XML editors, you must set the options for those editors after applying your selections in the **All Languages** dialog.</span></span>  
  
 <span data-ttu-id="33349-111">特定のエディターに対して異なる設定が選択された場合、"個々のテキスト形式のインデントの設定が競合しています" または "個々のテキスト形式のタブの設定が競合しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33349-111">The message "The indentation (or tab) settings for individual text formats conflict with each other" is displayed when different settings have been selected for particular editors.</span></span> <span data-ttu-id="33349-112">たとえば、**[テキスト形式]** では **[ブロック]** オプションが選択されているが、**[XML]** では **[なし]** が選択されている場合、このメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33349-112">For example, this reminder is displayed if the **Block indenting** option is selected for **Plain Text**, but **None** is selected for **XML**.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="33349-113">インデント</span><span class="sxs-lookup"><span data-stu-id="33349-113">Indenting</span></span>  
 <span data-ttu-id="33349-114">**なし**</span><span class="sxs-lookup"><span data-stu-id="33349-114">**None**</span></span>  
 <span data-ttu-id="33349-115">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、インデントされません。</span><span class="sxs-lookup"><span data-stu-id="33349-115">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="33349-116">カーソルは、新しい行の 1 列目に置かれます。</span><span class="sxs-lookup"><span data-stu-id="33349-116">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="33349-117">**ブロック**</span><span class="sxs-lookup"><span data-stu-id="33349-117">**Block**</span></span>  
 <span data-ttu-id="33349-118">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、直前の行のインデントと同じ位置まで自動的にインデントされます。</span><span class="sxs-lookup"><span data-stu-id="33349-118">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line was indented.</span></span>  
  
 <span data-ttu-id="33349-119">**[スマート]**</span><span class="sxs-lookup"><span data-stu-id="33349-119">**Smart**</span></span>  
 <span data-ttu-id="33349-120">このオプションが選択されている場合、Enter キーを押したときに作成される新しい行の位置は、コンテキストに応じて決定されます。</span><span class="sxs-lookup"><span data-stu-id="33349-120">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="33349-121">タブ</span><span class="sxs-lookup"><span data-stu-id="33349-121">Tabs</span></span>  
 <span data-ttu-id="33349-122">**[タブ サイズ]**</span><span class="sxs-lookup"><span data-stu-id="33349-122">**Tab size**</span></span>  
 <span data-ttu-id="33349-123">タブ ストップ間の間隔をスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="33349-123">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="33349-124">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="33349-124">The default is four spaces.</span></span>  
  
 <span data-ttu-id="33349-125">**[インデント サイズ]**</span><span class="sxs-lookup"><span data-stu-id="33349-125">**Indent size**</span></span>  
 <span data-ttu-id="33349-126">自動インデントのサイズをスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="33349-126">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="33349-127">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="33349-127">The default is four spaces.</span></span> <span data-ttu-id="33349-128">指定されたサイズになるように、タブ文字、スペース文字、またはその両方が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="33349-128">Tab characters, space characters, or both will be inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="33349-129">**[空白の挿入]**</span><span class="sxs-lookup"><span data-stu-id="33349-129">**Insert spaces**</span></span>  
 <span data-ttu-id="33349-130">このオプションを選択すると、タブ文字を使用せずにスペース文字だけを挿入してインデントします。</span><span class="sxs-lookup"><span data-stu-id="33349-130">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="33349-131">たとえば **[インデント サイズ]** が 5 に設定されている場合、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のメイン ウィンドウで Tab キーを押すか、ツール バーの **[インデント]** ボタンを押すごとに、5 つのスペース文字が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="33349-131">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] main window.</span></span>  
  
 <span data-ttu-id="33349-132">**[タブの保持]**</span><span class="sxs-lookup"><span data-stu-id="33349-132">**Keep tabs**</span></span>  
 <span data-ttu-id="33349-133">このオプションを選択すると、インデントするときにできる限り多くのタブ文字を挿入します。</span><span class="sxs-lookup"><span data-stu-id="33349-133">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="33349-134">それぞれのタブ文字が、[ **タブ サイズ**] で指定された数のスペースを満たします。</span><span class="sxs-lookup"><span data-stu-id="33349-134">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="33349-135">[ **インデント サイズ** ] が [ **タブ サイズ**] の倍数でない場合は、その差を埋めるためにスペース文字が追加されます。</span><span class="sxs-lookup"><span data-stu-id="33349-135">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
