---
title: '[外部ツール] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- adding external tools
- external tools [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], external tools
ms.assetid: ba797203-24d0-4922-9b97-8ab483f1db14
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5789dc150e45c1a0364b7acc0ea7fda443efcf17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717270"
---
# <a name="external-tools-dialog-box"></a><span data-ttu-id="576d3-102">[外部ツール] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="576d3-102">External Tools Dialog Box</span></span>
  <span data-ttu-id="576d3-103">**[外部ツール]** ダイアログ ボックスは、SQLCMD やメモ帳などの外部ツールを **[ツール]** メニューに追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="576d3-103">Use the **External Tools** dialog box to add external tools such as SQLCMD or Notepad to the **Tools** menu.</span></span> <span data-ttu-id="576d3-104">外部ツールを追加すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境で作業しながら、簡単に他のアプリケーションを起動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="576d3-104">Adding external tools allows you to easily launch other applications while working in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span> <span data-ttu-id="576d3-105">また、ツールを起動するときに引数や作業ディレクトリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="576d3-105">You can specify arguments and a working directory when launching the tool.</span></span> <span data-ttu-id="576d3-106">また、一部のツールからの出力を **[出力]** ウィンドウに表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="576d3-106">In addition, the output from some tools can be displayed in the **Output** window.</span></span> <span data-ttu-id="576d3-107">**[外部ツール]** ダイアログ ボックスは、 **[ツール]** メニューから使用できます。</span><span class="sxs-lookup"><span data-stu-id="576d3-107">The **External Tools** dialog box is available on the **Tools** menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="576d3-108">オプション</span><span class="sxs-lookup"><span data-stu-id="576d3-108">Options</span></span>  
 <span data-ttu-id="576d3-109">**[メニューの内容]**</span><span class="sxs-lookup"><span data-stu-id="576d3-109">**Menu contents**</span></span>  
 <span data-ttu-id="576d3-110">**[ツール]** メニューに現在追加されている項目のタイトルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="576d3-110">Lists the titles of the items currently added to the **Tools** menu.</span></span> <span data-ttu-id="576d3-111">メニューに表示される項目の順序を変更するには、 **[上へ移動]** と **[下へ移動]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="576d3-111">Use the **Move Up** and **Move Down** arrows to change the order the items that appear on the menu.</span></span> <span data-ttu-id="576d3-112">メニューから項目を削除するには、 **[削除]** ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="576d3-112">Use the **Delete** button to remove an item from the menu.</span></span>  
  
 <span data-ttu-id="576d3-113">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="576d3-113">**Move Up**</span></span>  
 <span data-ttu-id="576d3-114">**[ツール]** メニューで表示されるツールの一覧に、選択したツールを表示する位置を上へ移動します。</span><span class="sxs-lookup"><span data-stu-id="576d3-114">Move the selected tool higher in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="576d3-115">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="576d3-115">**Move Down**</span></span>  
 <span data-ttu-id="576d3-116">**[ツール]** メニューで表示されるツールの一覧に、選択したツールを表示する位置を下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="576d3-116">Move the selected tool lower in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="576d3-117">**追加**</span><span class="sxs-lookup"><span data-stu-id="576d3-117">**Add**</span></span>  
 <span data-ttu-id="576d3-118">新しいツールを指定できるようにテキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="576d3-118">Clear the text boxes so you can specify a new tool.</span></span>  
  
 <span data-ttu-id="576d3-119">**削除**</span><span class="sxs-lookup"><span data-stu-id="576d3-119">**Delete**</span></span>  
 <span data-ttu-id="576d3-120">**[メニューの内容]** の一覧および **[ツール]** メニューから、ツールまたはコマンドを削除します。</span><span class="sxs-lookup"><span data-stu-id="576d3-120">Remove the tool or command from the **Menu Contents** list as well as from the **Tools** menu.</span></span>  
  
 <span data-ttu-id="576d3-121">**Title**</span><span class="sxs-lookup"><span data-stu-id="576d3-121">**Title**</span></span>  
 <span data-ttu-id="576d3-122">**[ツール]** メニューの **[外部メニュー]** サブメニューに表示されるツールまたはコマンドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="576d3-122">Enter the name of the tool or command that will appear on the **External Tools** submenu of the **Tools** menu.</span></span> <span data-ttu-id="576d3-123">ツール名の 1 文字の前にアンパサンド (&) を付けて、その文字をキーボード ショートカットとして指定します。</span><span class="sxs-lookup"><span data-stu-id="576d3-123">Place an ampersand (&) before a letter in the name of the tool to specify that letter as a keyboard shortcut.</span></span> <span data-ttu-id="576d3-124">たとえば、"&SQLCMD" と指定した場合は、 **[ツール]** メニューに &SQLCMD が表示されます。</span><span class="sxs-lookup"><span data-stu-id="576d3-124">For example, "&SQLCMD" would display SQLCMD on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="576d3-125">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="576d3-125">**Command**</span></span>  
 <span data-ttu-id="576d3-126">起動するファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="576d3-126">Specify the path to the file to launch.</span></span>  
  
 <span data-ttu-id="576d3-127">**引数**</span><span class="sxs-lookup"><span data-stu-id="576d3-127">**Arguments**</span></span>  
 <span data-ttu-id="576d3-128">メニューでツールが選択されたときにツールに渡される変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="576d3-128">Specify the variables that are passed to the tool when the tool is selected on the menu.</span></span> <span data-ttu-id="576d3-129">引数によって、ツールやコマンドの起動時に渡す値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="576d3-129">Arguments can specify values that are passed to the tool or command when it is launched.</span></span> <span data-ttu-id="576d3-130">たとえば、ファイル名またはディレクトリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="576d3-130">For example, a value can specify a file name or directory.</span></span> <span data-ttu-id="576d3-131">矢印ボタンをクリックして表示される定義済みの引数の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="576d3-131">Use the arrow button to select from a list of predefined arguments.</span></span> <span data-ttu-id="576d3-132">複数の引数を追加できます。</span><span class="sxs-lookup"><span data-stu-id="576d3-132">You can add more than one.</span></span> <span data-ttu-id="576d3-133">定義済み引数および定義の完全な一覧については、「 [外部ツールの引数](menu-help/external-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="576d3-133">For a complete list of predefined arguments and their definitions, see [Arguments for External Tools](menu-help/external-tools.md).</span></span> <span data-ttu-id="576d3-134">使用するコマンドまたはツールに応じて、カスタム引数 (コマンド ライン スイッチなど) を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="576d3-134">You can also enter custom arguments (for example, command line switches), depending on the command or tool you use.</span></span>  
  
 <span data-ttu-id="576d3-135">**[出力ウィンドウを使用]**</span><span class="sxs-lookup"><span data-stu-id="576d3-135">**Use Output window**</span></span>  
 <span data-ttu-id="576d3-136">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] の出力ウィンドウを開いて、実行中のコマンドの出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="576d3-136">Opens the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Output window to display output of the command being run.</span></span> <span data-ttu-id="576d3-137">ツールによっては、出力ウィンドウに表示可能な形式の出力が提示されないものもあります。</span><span class="sxs-lookup"><span data-stu-id="576d3-137">Not all tools present output in a format that can be presented in the Output window.</span></span> <span data-ttu-id="576d3-138">詳細については、「 [[出力ウィンドウ]](../relational-databases/scripting/transact-sql-debugger-output-window.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="576d3-138">For more information, see [Output Window](../relational-databases/scripting/transact-sql-debugger-output-window.md).</span></span>  
  
 <span data-ttu-id="576d3-139">**[Unicode で出力を処理する]**</span><span class="sxs-lookup"><span data-stu-id="576d3-139">**Treat output as Unicode**</span></span>  
 <span data-ttu-id="576d3-140">出力を Unicode として解釈します。</span><span class="sxs-lookup"><span data-stu-id="576d3-140">Interprets the output as Unicode.</span></span>  
  
 <span data-ttu-id="576d3-141">**[初期ディレクトリ]**</span><span class="sxs-lookup"><span data-stu-id="576d3-141">**Initial directory**</span></span>  
 <span data-ttu-id="576d3-142">ツールの作業ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="576d3-142">Specify the working directory of the tool.</span></span> <span data-ttu-id="576d3-143">矢印ボタンを使用してディレクトリを選択します。</span><span class="sxs-lookup"><span data-stu-id="576d3-143">Use the arrow button to select directories.</span></span> <span data-ttu-id="576d3-144">複数のディレクトリを選択できます。</span><span class="sxs-lookup"><span data-stu-id="576d3-144">You can select more than one.</span></span>  
  
 <span data-ttu-id="576d3-145">**[起動時に引数を入力]**</span><span class="sxs-lookup"><span data-stu-id="576d3-145">**Prompt for arguments**</span></span>  
 <span data-ttu-id="576d3-146">外部ツールを起動するたびに **[引数]** ダイアログ ボックスを表示して、引数の値を入力したり編集したりできるようにします。</span><span class="sxs-lookup"><span data-stu-id="576d3-146">Display the **Arguments** dialog box to allow you to enter or edit values for the arguments each time you launch the external tool.</span></span>  
  
 <span data-ttu-id="576d3-147">**[終了時にウィンドウを閉じる]**</span><span class="sxs-lookup"><span data-stu-id="576d3-147">**Close on exit**</span></span>  
 <span data-ttu-id="576d3-148">ツールを閉じるときに、ツールを使用して開いたウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="576d3-148">Close the window opened by the tool when the tool is closed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="576d3-149">例</span><span class="sxs-lookup"><span data-stu-id="576d3-149">Example</span></span>  
 <span data-ttu-id="576d3-150">**[外部ツール]** ダイアログ ボックスに次の値を入力すると、"DAC" というラベルが付いたメニュー項目が作成されます。このメニュー項目を選択すると、コマンド プロンプトが開き、専用管理者接続を使用して **sqlcmd** ユーティリティが実行されます。</span><span class="sxs-lookup"><span data-stu-id="576d3-150">Entering the following values in the **External Tools** dialog box will create a menu item labeled "DAC" that when selected, opens a command prompt and runs the **sqlcmd** utility using the dedicated administrator connection.</span></span>  
  
|<span data-ttu-id="576d3-151">ボックス</span><span class="sxs-lookup"><span data-stu-id="576d3-151">Box</span></span>|<span data-ttu-id="576d3-152">値</span><span class="sxs-lookup"><span data-stu-id="576d3-152">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="576d3-153">**Title**</span><span class="sxs-lookup"><span data-stu-id="576d3-153">**Title**</span></span>|<span data-ttu-id="576d3-154">DAC (DAC)</span><span class="sxs-lookup"><span data-stu-id="576d3-154">DAC</span></span>|  
|<span data-ttu-id="576d3-155">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="576d3-155">**Command**</span></span>|[!INCLUDE[ssInstallPath](../includes/ssinstallpath-md.md)]<span data-ttu-id="576d3-156">Tools\Binn\SQLCMD.exe</span><span class="sxs-lookup"><span data-stu-id="576d3-156">Tools\Binn\SQLCMD.exe</span></span>|  
|<span data-ttu-id="576d3-157">**引数**</span><span class="sxs-lookup"><span data-stu-id="576d3-157">**Arguments**</span></span>|<span data-ttu-id="576d3-158">-A</span><span class="sxs-lookup"><span data-stu-id="576d3-158">-A</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="576d3-159">参照</span><span class="sxs-lookup"><span data-stu-id="576d3-159">See Also</span></span>  
 <span data-ttu-id="576d3-160">[外部ツールの引数](menu-help/external-tools.md) </span><span class="sxs-lookup"><span data-stu-id="576d3-160">[Arguments for External Tools](menu-help/external-tools.md) </span></span>  
 [<span data-ttu-id="576d3-161">一般的なユーザー インターフェイス要素</span><span class="sxs-lookup"><span data-stu-id="576d3-161">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
