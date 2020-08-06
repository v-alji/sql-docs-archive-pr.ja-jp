---
title: コードの書式設定の管理
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- indenting code [SQL Server]
- displaying URLs
- code formatting [SQL Server Management Studio]
- collapsing text
- formats [SQL Server], code formatting in SQL Server Management Studio
- hiding text
- formats [SQL Server]
- text [SQL Server], code formats
- automatic indentation
- converting text to lower case
- Query Editor [SQL Server Management Studio], managing code formats
- URL displayed in code [SQL Server Management Studio]
- converting text to upper case
- text [SQL Server]
- unindenting code
ms.assetid: ddbac4d2-6bdc-4467-a352-e869ec880eed
author: rothja
ms.author: jroth
ms.openlocfilehash: 873848c8aee575b47f7a3d8c31d8392cba5ed12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645486"
---
# <a name="manage-code-formatting"></a><span data-ttu-id="2e348-102">コードの書式設定の管理</span><span class="sxs-lookup"><span data-stu-id="2e348-102">Manage Code Formatting</span></span>
  <span data-ttu-id="2e348-103">エディターでは、コードに関して、インデント設定、テキストの非表示、URL などの書式設定を行えます。</span><span class="sxs-lookup"><span data-stu-id="2e348-103">With the Editor you can format your code with indenting, hidden text, URLs, and so forth.</span></span> <span data-ttu-id="2e348-104">スマート インジケーターを使用して、入力と同時にコードを自動的に書式設定することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2e348-104">You can also auto-format your code as you type by using Smart Indenting.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="2e348-105">インデント</span><span class="sxs-lookup"><span data-stu-id="2e348-105">Indenting</span></span>  
 <span data-ttu-id="2e348-106">テキストのインデントは、3 種類のスタイルから選択できます。</span><span class="sxs-lookup"><span data-stu-id="2e348-106">You can choose three different styles of text indenting.</span></span> <span data-ttu-id="2e348-107">また、1 つのインデントまたはタブのスペース数や、エディターでタブとスペースのどちらの文字を使用してインデントするかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2e348-107">You can also specify how many spaces compose a single indentation or tab, and whether the Editor uses tabs or space characters when indenting.</span></span>  
  
#### <a name="to-choose-an-indenting-style"></a><span data-ttu-id="2e348-108">インデントのスタイルを選択するには</span><span class="sxs-lookup"><span data-stu-id="2e348-108">To choose an indenting style</span></span>  
  
1.  <span data-ttu-id="2e348-109">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="2e348-110">**[テキスト エディター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-110">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="2e348-111">すべての言語のインデントを設定するために **[すべての言語]** フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-111">Click the folder, and select **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="2e348-112">**[タブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-112">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="2e348-113">以下のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-113">Click one of the following options:</span></span>  
  
    -   <span data-ttu-id="2e348-114">**なし**。</span><span class="sxs-lookup"><span data-stu-id="2e348-114">**None**.</span></span> <span data-ttu-id="2e348-115">カーソルは次の行の先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="2e348-115">The cursor goes to the beginning of the next line.</span></span>  
  
    -   <span data-ttu-id="2e348-116">**[ブロック]** 。</span><span class="sxs-lookup"><span data-stu-id="2e348-116">**Block**.</span></span> <span data-ttu-id="2e348-117">次行のインデントは前行に合わせて設定されます。</span><span class="sxs-lookup"><span data-stu-id="2e348-117">The cursor aligns the next line with the previous line.</span></span>  
  
    -   <span data-ttu-id="2e348-118">**[スマート]** (既定)。</span><span class="sxs-lookup"><span data-stu-id="2e348-118">**Smart** (Default).</span></span> <span data-ttu-id="2e348-119">適切なインデント スタイルが言語サービスによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="2e348-119">The language service determines the appropriate indenting style to use.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e348-120">一部の言語では、3 種類のインデント オプションがすべて用意されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2e348-120">Some languages do not offer all three indenting options.</span></span>  
  
#### <a name="to-change-indent-tab-settings"></a><span data-ttu-id="2e348-121">インデントのタブの設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="2e348-121">To change indent tab settings</span></span>  
  
1.  <span data-ttu-id="2e348-122">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-122">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="2e348-123">**[テキスト エディター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-123">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="2e348-124">すべての言語のインデントを設定するために **[すべての言語]** フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-124">Select the folder for **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="2e348-125">**[タブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-125">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="2e348-126">タブ操作とインデント操作でタブ文字を使用するように指定するには、 **[タブの保持]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-126">To specify tab characters for tab and indent operations, click **Keep tabs**.</span></span> <span data-ttu-id="2e348-127">スペース文字を使用するように指定するには、 **[空白の挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-127">To specify space characters, select **Insert spaces**.</span></span>  
  
     <span data-ttu-id="2e348-128">**[空白の挿入]** をクリックした場合は、各タブまたはインデントに相当するスペース文字の数を **[タブ サイズ]** または **[インデント サイズ]** に入力します。</span><span class="sxs-lookup"><span data-stu-id="2e348-128">If you select **Insert Spaces**, enter the number of space characters each tab or indent represents under **Tab Size** or **Indent Size**, respectively.</span></span>  
  
#### <a name="to-indent-code"></a><span data-ttu-id="2e348-129">コードにインデントを設定するには</span><span class="sxs-lookup"><span data-stu-id="2e348-129">To indent code</span></span>  
  
1.  <span data-ttu-id="2e348-130">インデントを設定するテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="2e348-130">Select the text you want to indent.</span></span>  
  
2.  <span data-ttu-id="2e348-131">Tab キーを押すか、標準ツール バーの **[インデント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-131">Press TAB, or click the **Indent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-unindent-code"></a><span data-ttu-id="2e348-132">コードのインデントを解除するには</span><span class="sxs-lookup"><span data-stu-id="2e348-132">To unindent code</span></span>  
  
1.  <span data-ttu-id="2e348-133">インデントを解除するテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="2e348-133">Select the text you want to unindent.</span></span>  
  
2.  <span data-ttu-id="2e348-134">Shift キーを押しながら Tab キーを押すか、標準ツール バーの **[インデントの解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-134">Press SHIFT+TAB, or click the **Unindent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-automatically-indent-all-of-your-code"></a><span data-ttu-id="2e348-135">すべてのコードに自動的にインデントを設定するには</span><span class="sxs-lookup"><span data-stu-id="2e348-135">To automatically indent all of your code</span></span>  
  
1.  <span data-ttu-id="2e348-136">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-136">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="2e348-137">**[テキスト エディター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-137">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="2e348-138">**[すべての言語]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-138">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="2e348-139">**[タブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-139">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="2e348-140">**[スマート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-140">Click **Smart**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e348-141">一部の言語では、 **[スマート]** オプションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="2e348-141">The **Smart** option is not available for some languages.</span></span>  
  
#### <a name="to-convert-white-space-to-tabs"></a><span data-ttu-id="2e348-142">スペースをタブに変換するには</span><span class="sxs-lookup"><span data-stu-id="2e348-142">To convert white space to tabs</span></span>  
  
1.  <span data-ttu-id="2e348-143">スペースをタブに変換するテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="2e348-143">Select the text whose white space you want to convert to tabs.</span></span>  
  
2.  <span data-ttu-id="2e348-144">**[編集]** メニューの **[詳細設定]** をポイントし、 **[選択行にタブを設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-144">On the **Edit** menu, point to **Advanced**, and click **Tabify Selection**.</span></span>  
  
#### <a name="to-convert-tabs-to-spaces"></a><span data-ttu-id="2e348-145">タブをスペースに変換するには</span><span class="sxs-lookup"><span data-stu-id="2e348-145">To convert tabs to spaces</span></span>  
  
1.  <span data-ttu-id="2e348-146">タブをスペースに変換するテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="2e348-146">Select the text whose tabs you want to convert to spaces.</span></span>  
  
2.  <span data-ttu-id="2e348-147">**[編集]** メニューの **[詳細設定]** をポイントし、 **[選択行のタブの設定を解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-147">On the **Edit** menu, point to **Advanced**, and click **Untabify Selection**.</span></span>  
  
 <span data-ttu-id="2e348-148">これらのコマンドの動作は、 **[オプション]** ダイアログ ボックスのタブ設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="2e348-148">The behavior of these commands depends on the tab settings in the **Options** dialog box.</span></span> <span data-ttu-id="2e348-149">たとえば、タブ設定が 4 の場合、 **[選択行にタブを設定]** をクリックすると 4 つの連続したスペースに対して 1 つのタブが作成され、 **[選択行のタブの設定を解除]** をクリックすると 1 つのタブに対して 4 つのスペースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e348-149">For example, if the tab setting is 4, **Tabify Selection** creates a tab for every 4 contiguous spaces, and **Untabify Selection** creates 4 spaces for every tab.</span></span>  
  
## <a name="converting-text-to-upper-and-lower-case"></a><span data-ttu-id="2e348-150">大文字のテキストまたは小文字のテキストへの変換</span><span class="sxs-lookup"><span data-stu-id="2e348-150">Converting Text to Upper and Lower Case</span></span>  
 <span data-ttu-id="2e348-151">テキストをすべて大文字または小文字に変換するためのコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e348-151">You can use commands to convert text to all uppercase or lower case.</span></span>  
  
#### <a name="to-switch-text-to-upper-or-lower-case"></a><span data-ttu-id="2e348-152">テキストを大文字または小文字に切り替えるには</span><span class="sxs-lookup"><span data-stu-id="2e348-152">To switch text to upper or lower case</span></span>  
  
1.  <span data-ttu-id="2e348-153">変換するテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="2e348-153">Select the text you want to convert.</span></span>  
  
2.  <span data-ttu-id="2e348-154">テキストを大文字に変換するには、Ctrl キーと Shift キーを押しながら U キーを押すか、 **[編集]** メニューの **[詳細設定]** サブメニューの **[大文字に変換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-154">To convert text to uppercase, press CTRL+SHIFT+U, or click **Make Uppercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
3.  <span data-ttu-id="2e348-155">テキストを小文字に変換するには、Ctrl キーと Shift キーを押しながら L キーを押すか、 **[編集]** メニューの **[詳細設定]** サブメニューの **[小文字に変換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-155">To convert text to lowercase, press CTRL+SHIFT+L, or click **Make Lowercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e348-156">キーボード ショートカット キーの完全な一覧については、「 [SQL Server Management Studio のキーボード ショートカット](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e348-156">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="displaying-and-linking-to-urls"></a><span data-ttu-id="2e348-157">URL の表示とリンクの設定</span><span class="sxs-lookup"><span data-stu-id="2e348-157">Displaying and Linking to URLs</span></span>  
 <span data-ttu-id="2e348-158">クリック可能な URL をコード内に作成して、表示できます。</span><span class="sxs-lookup"><span data-stu-id="2e348-158">You can create and display clickable URLs in your code.</span></span> <span data-ttu-id="2e348-159">URL の既定の設定は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2e348-159">By default, the URLs:</span></span>  
  
-   <span data-ttu-id="2e348-160">下線が付きます。</span><span class="sxs-lookup"><span data-stu-id="2e348-160">Are underlined.</span></span>  
  
-   <span data-ttu-id="2e348-161">マウスのポインターを URL の上に置くと、ポインターが手の形に変わります。</span><span class="sxs-lookup"><span data-stu-id="2e348-161">Change the mouse pointer to a hand when you move over them.</span></span>  
  
-   <span data-ttu-id="2e348-162">URL が有効な場合は、クリックするとその URL が開きます。</span><span class="sxs-lookup"><span data-stu-id="2e348-162">Open the URL when clicked, if the URL is valid.</span></span>  
  
#### <a name="to-display-a-clickable-url"></a><span data-ttu-id="2e348-163">クリック可能な URL を表示するには</span><span class="sxs-lookup"><span data-stu-id="2e348-163">To display a clickable URL</span></span>  
  
1.  <span data-ttu-id="2e348-164">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-164">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="2e348-165">**[テキスト エディター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-165">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="2e348-166">1 つの言語のオプションだけを変更する場合は、その言語のフォルダーをクリックし、 **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-166">To change the option for only one language, click that language folder and then click **General**.</span></span> <span data-ttu-id="2e348-167">すべての言語のオプションを変更する場合は、 **[すべての言語]** 、 **[全般]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e348-167">To change the option for all languages, click **All Languages** and then click **General**.</span></span>  
  
4.  <span data-ttu-id="2e348-168">**[シングルクリックでの URL ナビゲーションを有効にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="2e348-168">Select **Enable single-click URL navigation**.</span></span>  
  
  
