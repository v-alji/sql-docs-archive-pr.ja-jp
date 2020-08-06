---
title: '[オプション] ([テキストエディター]: [エディターのタブとステータスバー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.editorcontextsettings
- VS.ToolsOptionsPages.Text_Editor.EditorTabAndStatusBar
ms.assetid: e4815678-7885-4631-878f-c6a2b857ee05
author: rothja
ms.author: jroth
ms.openlocfilehash: 920b7d48b5f7a2472a521af21c8217b1adba486a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644136"
---
# <a name="options-text-editor-editor-tab-and-status-bar-page"></a><span data-ttu-id="83623-102">オプション ([テキスト エディター]: [エディターのタブとステータス バー] ページ)</span><span class="sxs-lookup"><span data-stu-id="83623-102">Options (Text Editor: Editor Tab and Status Bar Page)</span></span>
  <span data-ttu-id="83623-103">**[エディターのタブとステータス バー]** ページでは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] クエリ エディターによって表示される情報をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="83623-103">The **Editor Tab and Status Bar Page** lets you customize the information displayed by the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Query Editors.</span></span> <span data-ttu-id="83623-104">クエリ エディター ウィンドウのタブおよびステータス バーに表示される情報のレベル、およびステータス バーをエディター ウィンドウの上部と下部のどちらに表示するかを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="83623-104">You can specify the level of information displayed in the tab and status bar of the Query Editor window, and whether the status bar appears at the top or bottom of the editor window.</span></span>  
  
## <a name="option-settings-by-editor"></a><span data-ttu-id="83623-105">エディターのオプション設定</span><span class="sxs-lookup"><span data-stu-id="83623-105">Option Settings by Editor</span></span>  
 <span data-ttu-id="83623-106">エディターのタブとステータス バーはすべての [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] エディターで使用できますが、機能のレベルには差があります。</span><span class="sxs-lookup"><span data-stu-id="83623-106">The editor tab and the status bar are available in all of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, but have different levels of functionality.</span></span>  
  
 <span data-ttu-id="83623-107">データベース エンジン クエリ エディターは、サーバー グループに接続できます。その場合、サーバー グループ内のすべてのインスタンスへの接続が開かれ、それぞれの接続に対して同じクエリを同時に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="83623-107">The Database Engine Query Editor can connect to a server group, in which case it opens connections to all the instances in the Server Group and can simultaneously run the same query on each connection.</span></span> <span data-ttu-id="83623-108">1 つのインスタンスではなく複数のインスタンスに接続する場合は、このダイアログを使用して、ステータス バーにさまざまな色を指定することができます。マルチ サーバーの場合の結果のオプションを変更するには、[[オプション] ([クエリ結果]/[SQL Server]/[マルチ サーバー])](../../2014/database-engine/options-query-results-sql-server-multi-server.md) ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="83623-108">You can use this dialog to specify that the status bar has different colors when connected to multiple instances rather than one instance.To change the multi-server results options, use the [Options (Query Results/SQL Server/Multi-Server)](../../2014/database-engine/options-query-results-sql-server-multi-server.md) page.</span></span>  
  
## <a name="status-bar-content"></a><span data-ttu-id="83623-109">ステータス バーの内容</span><span class="sxs-lookup"><span data-stu-id="83623-109">Status Bar Content</span></span>  
 <span data-ttu-id="83623-110">クエリ エディターのステータス バーに表示される情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="83623-110">Specifies the information that appears in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="83623-111">**[実行時間を表示する]**</span><span class="sxs-lookup"><span data-stu-id="83623-111">**Display execution time**</span></span>  
 <span data-ttu-id="83623-112">スクリプトの実行時間を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-112">Includes the script execution time.</span></span> <span data-ttu-id="83623-113">設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="83623-113">The settings are as follows:</span></span>  
  
 <span data-ttu-id="83623-114">**なし**</span><span class="sxs-lookup"><span data-stu-id="83623-114">**None**</span></span>  
 <span data-ttu-id="83623-115">ステータス バーには時間の情報が表示されません。</span><span class="sxs-lookup"><span data-stu-id="83623-115">The status bar displays no time information.</span></span>  
  
 <span data-ttu-id="83623-116">**End**</span><span class="sxs-lookup"><span data-stu-id="83623-116">**End**</span></span>  
 <span data-ttu-id="83623-117">スクリプトの実行中はステータス バーに現在の時刻が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-117">The status bar displays the current time of day while the script is running.</span></span> <span data-ttu-id="83623-118">スクリプトが完了すると、スクリプトが完了した時刻が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-118">When the script completes, the display shows the time of day that the script completed.</span></span>  
  
 <span data-ttu-id="83623-119">**切れる**</span><span class="sxs-lookup"><span data-stu-id="83623-119">**Elapsed**</span></span>  
 <span data-ttu-id="83623-120">ステータス バーにスクリプトの実行時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-120">The status bar displays the length of time that the script has been running.</span></span> <span data-ttu-id="83623-121">スクリプトが完了すると、スクリプトの実行にかかった時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-121">When the script completes, the display shows how much time was taken to run the script.</span></span>  
  
 <span data-ttu-id="83623-122">**[データベース名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-122">**Include database name**</span></span>  
 <span data-ttu-id="83623-123">接続に使用されている現在のデータベースの名前を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-123">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="83623-124">クエリ エディターを最初に開くと、ログインの既定のデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-124">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="83623-125">このデータベース コンテキストは、後で Transact-SQL の USE ステートメントを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="83623-125">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="83623-126">**[ログイン名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-126">**Include login name**</span></span>  
 <span data-ttu-id="83623-127">ログイン名を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-127">Includes the login name.</span></span>  
  
 <span data-ttu-id="83623-128">**[行数を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-128">**Include row count**</span></span>  
 <span data-ttu-id="83623-129">現在実行されているスクリプトによって処理された行の数を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-129">Includes a count of the rows that have been processed by the script that is currently executing.</span></span>  
  
 <span data-ttu-id="83623-130">**[サーバー名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-130">**Include server name**</span></span>  
 <span data-ttu-id="83623-131">サーバー名を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-131">Includes the server name.</span></span> <span data-ttu-id="83623-132">ローカル接続の場合、これはインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="83623-132">For local connections, this is the instance name.</span></span> <span data-ttu-id="83623-133">リモート接続の場合、これはリモート コンピューター名とインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="83623-133">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="status-bar-layout-and-colors"></a><span data-ttu-id="83623-134">ステータス バーのレイアウトと色</span><span class="sxs-lookup"><span data-stu-id="83623-134">Status Bar Layout and Colors</span></span>  
 <span data-ttu-id="83623-135">クエリ エディターのステータス バーの項目の色を指定します。</span><span class="sxs-lookup"><span data-stu-id="83623-135">Specifies the colors for items in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="83623-136">**[グループ接続]**</span><span class="sxs-lookup"><span data-stu-id="83623-136">**Group connections**</span></span>  
 <span data-ttu-id="83623-137">クエリ エディターが複数の接続を保持している場合のステータス バーの色を設定します。</span><span class="sxs-lookup"><span data-stu-id="83623-137">Set the color of the status bar when the Query Editor has more than one connection.</span></span>  
  
 <span data-ttu-id="83623-138">**[単一のサーバー接続]**</span><span class="sxs-lookup"><span data-stu-id="83623-138">**Single server connections**</span></span>  
 <span data-ttu-id="83623-139">クエリ エディターが単一の接続を保持している場合のステータス バーの色を設定します。</span><span class="sxs-lookup"><span data-stu-id="83623-139">Set the color of the status bar when the Query Editor has one connection.</span></span>  
  
 <span data-ttu-id="83623-140">**[ステータス バーの位置]**</span><span class="sxs-lookup"><span data-stu-id="83623-140">**Status bar location**</span></span>  
 <span data-ttu-id="83623-141">ステータス バーの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="83623-141">Specifies the location of the status bar.</span></span> <span data-ttu-id="83623-142">設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="83623-142">The settings are as follows:</span></span>  
  
 <span data-ttu-id="83623-143">**上位**</span><span class="sxs-lookup"><span data-stu-id="83623-143">**Top**</span></span>  
 <span data-ttu-id="83623-144">ステータス バーは、クエリ エディター ウィンドウの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-144">The status bar appears at the top of the Query Editor window.</span></span>  
  
 <span data-ttu-id="83623-145">**下**</span><span class="sxs-lookup"><span data-stu-id="83623-145">**Bottom**</span></span>  
 <span data-ttu-id="83623-146">ステータス バーは、クエリ エディター ウィンドウの下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-146">The status bar appears at the bottom of the Query Editor window.</span></span>  
  
## <a name="tab-text"></a><span data-ttu-id="83623-147">タブのテキスト</span><span class="sxs-lookup"><span data-stu-id="83623-147">Tab Text</span></span>  
 <span data-ttu-id="83623-148">クエリ エディター ウィンドウの上部のタブに表示されるテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="83623-148">Specifies the text that appears in the tab at the top of a Query Editor window.</span></span> <span data-ttu-id="83623-149">テキストが長すぎて表示されない場合は、タブ上にマウス ポインターを移動すると表示されるツールヒントに完全な文字列を表示できます。</span><span class="sxs-lookup"><span data-stu-id="83623-149">If the text is too long to display, you can view the full string in a tooltip that is displayed if you hover over the tab.</span></span>  
  
 <span data-ttu-id="83623-150">**[データベース名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-150">**Include database name**</span></span>  
 <span data-ttu-id="83623-151">接続に使用されている現在のデータベースの名前を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-151">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="83623-152">クエリ エディターを最初に開くと、ログインの既定のデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83623-152">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="83623-153">このデータベース コンテキストは、後で Transact-SQL の USE ステートメントを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="83623-153">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="83623-154">**[ファイル名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-154">**Include file name**</span></span>  
 <span data-ttu-id="83623-155">スクリプトが保存されているファイルの名前を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-155">Includes the name of the file where the script is stored.</span></span>  
  
 <span data-ttu-id="83623-156">**[フォルダー名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-156">**Include folder name**</span></span>  
 <span data-ttu-id="83623-157">スクリプト ファイルが保存されているフォルダーのパスを含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-157">Includes the path of the folder where the script file is stored.</span></span>  
  
 <span data-ttu-id="83623-158">**[ログイン名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-158">**Include login name**</span></span>  
 <span data-ttu-id="83623-159">ログイン名を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-159">Includes the login name.</span></span>  
  
 <span data-ttu-id="83623-160">**[サーバー名を含める]**</span><span class="sxs-lookup"><span data-stu-id="83623-160">**Include server name**</span></span>  
 <span data-ttu-id="83623-161">サーバー名を含めます。</span><span class="sxs-lookup"><span data-stu-id="83623-161">Includes the server name.</span></span> <span data-ttu-id="83623-162">ローカル接続の場合、これはインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="83623-162">For local connections, this is the instance name.</span></span> <span data-ttu-id="83623-163">リモート接続の場合、これはリモート コンピューター名とインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="83623-163">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83623-164">参照</span><span class="sxs-lookup"><span data-stu-id="83623-164">See Also</span></span>  
 <span data-ttu-id="83623-165">[オプション &#40;環境: [フォントおよび色] ページ&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span><span class="sxs-lookup"><span data-stu-id="83623-165">[Options &#40;Environment: Fonts and Colors Page&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span></span>  
 [<span data-ttu-id="83623-166">クエリ エディターでのコードの色分け</span><span class="sxs-lookup"><span data-stu-id="83623-166">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
