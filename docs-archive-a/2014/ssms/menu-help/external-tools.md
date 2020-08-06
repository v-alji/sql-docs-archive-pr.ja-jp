---
title: '[外部ツール] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- External Tools dialog box
ms.assetid: d7dae88f-0781-4162-96cd-d3a3a4d82035
author: stevestein
ms.author: sstein
ms.openlocfilehash: a39cd0d139e81c02a7d2a58fae4e74221be7f78e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715933"
---
# <a name="external-tools"></a><span data-ttu-id="e26ce-102">[外部ツール]</span><span class="sxs-lookup"><span data-stu-id="e26ce-102">External Tools</span></span>
  <span data-ttu-id="e26ce-103">このダイアログ ボックスを使用すると、SQL Server 構成マネージャーやメモ帳などの外部ツールを **[ツール]** メニューに追加できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-103">Use this dialog box to add external tools, such as SQL Server Configuration Manager or Notepad, to the **Tools** menu.</span></span> <span data-ttu-id="e26ce-104">外部ツールを追加することにより、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で作業している間に他のアプリケーションを簡単に起動できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-104">Adding external tools allows you to easily launch other applications while working in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e26ce-105">また、ツールを起動するときに引数や作業ディレクトリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-105">You can specify arguments and a working directory when launching the tool.</span></span> <span data-ttu-id="e26ce-106">さらに、一部のツールの出力は [出力] ウィンドウに表示できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-106">In addition, the outputs from some tools can be displayed in the Output window.</span></span> <span data-ttu-id="e26ce-107">**[外部ツール]** ダイアログ ボックスは、 **[ツール]** メニューから使用できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-107">The **External Tools** dialog box is available on the **Tools** menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e26ce-108">オプション</span><span class="sxs-lookup"><span data-stu-id="e26ce-108">Options</span></span>  
 <span data-ttu-id="e26ce-109">**[メニューの内容]**</span><span class="sxs-lookup"><span data-stu-id="e26ce-109">**Menu Contents**</span></span>  
 <span data-ttu-id="e26ce-110">**[ツール]** メニューに現在追加されている項目のタイトルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-110">Lists the titles of the items currently added to the **Tools** menu.</span></span> <span data-ttu-id="e26ce-111">メニューに表示される項目の順序を変更するには、 **[上へ移動]** と **[下へ移動]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-111">Use the **Move Up** and **Move Down** arrows to change the order the items that appear on the menu.</span></span> <span data-ttu-id="e26ce-112">メニューから項目を削除するには、 **[削除]** ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-112">Use the **Delete** button to remove an item from the menu.</span></span>  
  
 <span data-ttu-id="e26ce-113">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="e26ce-113">**Move Up**</span></span>  
 <span data-ttu-id="e26ce-114">**[ツール]** メニューで表示されるツールの一覧に、選択したツールを表示する位置を上へ移動します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-114">Move the selected tool higher in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="e26ce-115">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="e26ce-115">**Move Down**</span></span>  
 <span data-ttu-id="e26ce-116">**[ツール]** メニューで表示されるツールの一覧に、選択したツールを表示する位置を下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-116">Move the selected tool lower in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="e26ce-117">**追加**</span><span class="sxs-lookup"><span data-stu-id="e26ce-117">**Add**</span></span>  
 <span data-ttu-id="e26ce-118">新しいツールを指定できるようにテキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="e26ce-118">Clear the text boxes so you can specify a new tool.</span></span>  
  
 <span data-ttu-id="e26ce-119">**削除**</span><span class="sxs-lookup"><span data-stu-id="e26ce-119">**Delete**</span></span>  
 <span data-ttu-id="e26ce-120">**[メニューの内容]** の一覧および **[ツール]** メニューから、ツールまたはコマンドを削除します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-120">Remove the tool or command from the **Menu Contents** list as well as from the **Tools** menu.</span></span>  
  
 <span data-ttu-id="e26ce-121">**Title**</span><span class="sxs-lookup"><span data-stu-id="e26ce-121">**Title**</span></span>  
 <span data-ttu-id="e26ce-122">**[ツール]** メニューの **[外部メニュー]** サブメニューに表示されるツールまたはコマンドの名前です。</span><span class="sxs-lookup"><span data-stu-id="e26ce-122">The name of the tool or command that will appear on the **External Tools** submenu of the **Tools** menu.</span></span> <span data-ttu-id="e26ce-123">ツールの名前の中でツールのアクセス キーとして使用する文字の前にアンパサンドを配置します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-123">Place an ampersand before a letter in the name of the tool to use that letter as an accelerator key for the tool.</span></span> <span data-ttu-id="e26ce-124">たとえば、 `&Spy++` は **[ツール]** メニューの **[Spy++]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-124">For example, `&Spy++` would display **Spy++** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="e26ce-125">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="e26ce-125">**Command**</span></span>  
 <span data-ttu-id="e26ce-126">起動する .exe、.com、.pif、.bat、.cmd などのファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-126">Specify the path to the .exe, .com, .pif, .bat, .cmd, or other file that you intend to launch.</span></span> <span data-ttu-id="e26ce-127">`.bat`[出力ウィンドウを使用] `.com`チェック ボックスがオンになっている場合は、 **や** などのファイルからの出力を [出力] ウィンドウに表示できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-127">The output from `.bat`, `.com`, and other files can be viewed in the Output window if you select the **Use output window** check box.</span></span>  
  
 <span data-ttu-id="e26ce-128">**引数**</span><span class="sxs-lookup"><span data-stu-id="e26ce-128">**Arguments**</span></span>  
 <span data-ttu-id="e26ce-129">メニューでツールが選択されたときにツールに渡される変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-129">Specify the variables that are passed to the tool when the tool is selected on the menu.</span></span> <span data-ttu-id="e26ce-130">引数によって、ツールやコマンドの起動時に渡す値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-130">Arguments can specify values that are passed to the tool or command when it is launched.</span></span> <span data-ttu-id="e26ce-131">たとえば、ファイル名またはディレクトリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-131">For example, a value can specify a file name or directory.</span></span> <span data-ttu-id="e26ce-132">**矢印** ボタンを使用して、定義済み引数の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-132">Use the **Arrow** button to select from a list of predefined arguments.</span></span> <span data-ttu-id="e26ce-133">複数の引数を追加できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-133">You can add more than one.</span></span> <span data-ttu-id="e26ce-134">定義済み引数および定義の完全な一覧については、「 [外部ツールの引数](external-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e26ce-134">For a complete list of predefined arguments and their definitions, see [Arguments for External Tools](external-tools.md).</span></span> <span data-ttu-id="e26ce-135">また、使用するコマンドやツールによっては、command-prompt スイッチなどのカスタム引数を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-135">You can also enter custom arguments (command-prompt switches, for example), depending on the command or tool you use.</span></span>  
  
 <span data-ttu-id="e26ce-136">**[初期ディレクトリ]**</span><span class="sxs-lookup"><span data-stu-id="e26ce-136">**Initial directory**</span></span>  
 <span data-ttu-id="e26ce-137">ツールの作業ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-137">Specify the working directory of the tool.</span></span> <span data-ttu-id="e26ce-138">**矢印** ボタンを使用してディレクトリを選択します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-138">Use the **Arrow** button to select directories.</span></span> <span data-ttu-id="e26ce-139">複数のディレクトリを選択できます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-139">You can select more than one.</span></span>  
  
 <span data-ttu-id="e26ce-140">**Use output Window**</span><span class="sxs-lookup"><span data-stu-id="e26ce-140">**Use output Window**</span></span>  
 <span data-ttu-id="e26ce-141">ツールからの結果を [出力] ウィンドウに表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-141">Specify whether or not results from the tool are displayed in the Output window.</span></span> <span data-ttu-id="e26ce-142">このオプションは、.bat や .com などのファイルの場合のみ使用できます。通常は、コマンド プロンプト ウィンドウ内に出力されます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-142">This option is only available for files, such as .bat and .com files, that normally display output in the command prompt window.</span></span> <span data-ttu-id="e26ce-143">このオプションをオンにすると、ツールの進捗状況を確認するときにウィンドウ管理が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="e26ce-143">When enabled, this option eases window management when you are following the progress of a tool.</span></span>  
  
 <span data-ttu-id="e26ce-144">**[起動時に引数を入力]**</span><span class="sxs-lookup"><span data-stu-id="e26ce-144">**Prompt for arguments**</span></span>  
 <span data-ttu-id="e26ce-145">外部ツールを起動するたびに引数の値を入力または編集できるように、 **[引数]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-145">Display the **Arguments** dialog box to enable you to enter or edit values for the arguments each time you launch the external tool.</span></span>  
  
 <span data-ttu-id="e26ce-146">**[Unicode で出力を処理する]**</span><span class="sxs-lookup"><span data-stu-id="e26ce-146">**Treat output as Unicode**</span></span>  
 <span data-ttu-id="e26ce-147">[出力] ウィンドウで Unicode を許可できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e26ce-147">Allow the Output window to accept Unicode.</span></span>  
  
 <span data-ttu-id="e26ce-148">**[終了時にウィンドウを閉じる]**</span><span class="sxs-lookup"><span data-stu-id="e26ce-148">**Close On Exit**</span></span>  
 <span data-ttu-id="e26ce-149">ツールを閉じるときに、ツールを使用して開いたウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e26ce-149">Close the window opened by the tool when the tool is closed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e26ce-150">例</span><span class="sxs-lookup"><span data-stu-id="e26ce-150">Example</span></span>  
  
#### <a name="to-add-sql-server-configuration-manager-to-the-tools-menu"></a><span data-ttu-id="e26ce-151">SQL Server 構成マネージャーを [ツール] メニューに追加するには</span><span class="sxs-lookup"><span data-stu-id="e26ce-151">To add SQL Server Configuration Manager to the Tools menu</span></span>  
  
1.  <span data-ttu-id="e26ce-152">**[ツール]** メニューの **[外部ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e26ce-152">On the **Tools** menu, click **External Tools**.</span></span>  
  
2.  <span data-ttu-id="e26ce-153">**[タイトル]** ボックスで、「 **SQL Server 構成マネージャー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-153">In the **Title** box, type **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="e26ce-154">[**コマンド**] ボックスに、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソールの実行可能ファイルへのパス (など) を入力します。`C:\WINNT\system32\mmc.exe`</span><span class="sxs-lookup"><span data-stu-id="e26ce-154">In the **Command** box, type the path to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console executable, such as `C:\WINNT\system32\mmc.exe`</span></span>  
  
4.  <span data-ttu-id="e26ce-155">[**引数**] ボックスに、.msc ファイルへのパス (など) を入力します。`"C:\WINNT\system32\SQLServerManager.msc"`</span><span class="sxs-lookup"><span data-stu-id="e26ce-155">In the **Arguments** box, type the path to the .msc file, such as `"C:\WINNT\system32\SQLServerManager.msc"`</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e26ce-156">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [スタート] **メニューで** ショートカットのプロパティを表示して、コンピューター上のファイルの場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="e26ce-156">View the properties of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] shortcut on the **Start** menu to confirm the location of the files on your computer.</span></span>  
