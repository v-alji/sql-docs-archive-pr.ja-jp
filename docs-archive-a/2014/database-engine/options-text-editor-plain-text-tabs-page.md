---
title: '[オプション] ([テキストエディター]/[テキスト形式]/[タブ] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
ms.assetid: 07d82d10-bca9-4b37-abbb-58ef9bfb264b
author: rothja
ms.author: jroth
ms.openlocfilehash: 705210c12582723c107283ca00a5cb885ea3ce98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642960"
---
# <a name="options-text-editor---plain-text---tabs-page"></a><span data-ttu-id="ce3a9-102">[オプション] ([テキスト エディター]/[テキスト形式]/[タブ] ページ)</span><span class="sxs-lookup"><span data-stu-id="ce3a9-102">Options (Text Editor - Plain Text - Tabs Page)</span></span>
  <span data-ttu-id="ce3a9-103">特定の開発言語に関連付けられていないドキュメントを編集するときには、テキスト エディターが使用されます。このダイアログ ボックスを使用すると、テキスト エディターのタブの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-103">Use this dialog to change the tabbing behavior of the Text Editor, which is used to edit a document not associated with a particular development language.</span></span> <span data-ttu-id="ce3a9-104">この設定を表示するには、**[ツール]** メニューの **[オプション]** をクリックして、**[テキスト エディター]** フォルダーを展開し、さらに **[テキスト形式]** を展開して、**[タブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-104">To display these settings, click **Options** on the **Tools** menu, expand **Text Editor**, expand **Plain Text**, and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="ce3a9-105">複数の場所でのオプション設定</span><span class="sxs-lookup"><span data-stu-id="ce3a9-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="ce3a9-106">テキスト形式エディターのオプションは、[すべての言語] の [全般] \*\*\*\* ダイアログで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-106">Options for the Plain Text Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="ce3a9-107">ただし、DMX エディターや MDX エディターなど、他の **エディターに対し、** [すべての言語] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のダイアログを使用して異なるオプションを設定する場合は、ここで紹介したダイアログを使用してテキスト形式エディターのオプションを設定し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the Plain Text Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="ce3a9-108">インデント</span><span class="sxs-lookup"><span data-stu-id="ce3a9-108">Indenting</span></span>  
 <span data-ttu-id="ce3a9-109">**なし**</span><span class="sxs-lookup"><span data-stu-id="ce3a9-109">**None**</span></span>  
 <span data-ttu-id="ce3a9-110">Enter キーを押したときに作成される新しい行はインデントされません。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-110">Do not indent the new line created when you press ENTER.</span></span> <span data-ttu-id="ce3a9-111">カーソルは、新しい行の 1 列目に置かれます。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="ce3a9-112">**ブロック**</span><span class="sxs-lookup"><span data-stu-id="ce3a9-112">**Block**</span></span>  
 <span data-ttu-id="ce3a9-113">Enter キーを押したときに作成される新しい行が、直前のインデントされている行と同じ位置までインデントされます。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-113">Indent the new line created when you press ENTER the same distance as the previous line was indented.</span></span>  
  
 <span data-ttu-id="ce3a9-114">**[スマート]**</span><span class="sxs-lookup"><span data-stu-id="ce3a9-114">**Smart**</span></span>  
 <span data-ttu-id="ce3a9-115">プレーンテキスト エディターではこの種の書式設定はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-115">The plain text editor does not support this type of formatting.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="ce3a9-116">タブ</span><span class="sxs-lookup"><span data-stu-id="ce3a9-116">Tabs</span></span>  
 <span data-ttu-id="ce3a9-117">**[タブ サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ce3a9-117">**Tab size**</span></span>  
 <span data-ttu-id="ce3a9-118">タブ ストップ間の間隔をスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-118">Set the distance in spaces between tab stops.</span></span> <span data-ttu-id="ce3a9-119">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-119">The default is four spaces.</span></span>  
  
 <span data-ttu-id="ce3a9-120">**[インデント サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ce3a9-120">**Indent size**</span></span>  
 <span data-ttu-id="ce3a9-121">自動インデントのサイズをスペース数で設定します。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-121">Set the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="ce3a9-122">既定値は、スペースが 4 つです。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-122">The default is four spaces.</span></span> <span data-ttu-id="ce3a9-123">指定されたサイズになるように、タブ文字、スペース文字、またはその両方が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-123">Tab characters, space characters, or both will be inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="ce3a9-124">**[空白の挿入]**</span><span class="sxs-lookup"><span data-stu-id="ce3a9-124">**Insert spaces**</span></span>  
 <span data-ttu-id="ce3a9-125">タブ文字を使用せずにスペース文字だけを挿入してインデントします。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-125">Insert only space characters, not tab characters, when indenting.</span></span> <span data-ttu-id="ce3a9-126">たとえば **[インデント サイズ]** が 5 に設定されている場合、Tab キーを押すか、**[書式設定]** ツール バーの **[インデント]** ボタンを押すごとに、5 つのスペース文字が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-126">If **Indent size** is set to 5, for example, five space characters are inserted whenever you press the TAB key or the **Increase Indent** button on the **Formatting** toolbar.</span></span>  
  
 <span data-ttu-id="ce3a9-127">**[タブの保持]**</span><span class="sxs-lookup"><span data-stu-id="ce3a9-127">**Keep tabs**</span></span>  
 <span data-ttu-id="ce3a9-128">インデントするときにできる限り多くのタブ文字を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-128">Insert as many tab characters as possible when indenting.</span></span> <span data-ttu-id="ce3a9-129">それぞれのタブ文字が、[ **タブ サイズ**] で指定された数のスペースを満たします。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-129">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="ce3a9-130">**[インデント サイズ]** が **[タブ サイズ]** 値の倍数でない場合は、その差を埋めるためにスペース文字が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ce3a9-130">If **Indent size** is not an even multiple of the **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
