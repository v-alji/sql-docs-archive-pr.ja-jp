---
title: '[エラー一覧] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- error list window
- SQL Server Management Studio [SQL Server], error list window
ms.assetid: fae6327d-e268-44ae-a474-4a8f8f843129
author: rothja
ms.author: jroth
ms.openlocfilehash: 00455c339344b7b38a48500c49d139aa52df6116
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644968"
---
# <a name="error-list-window-management-studio"></a><span data-ttu-id="2f3af-102">[エラー一覧] ウィンドウ (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2f3af-102">Error List Window (Management Studio)</span></span>
  <span data-ttu-id="2f3af-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[エラー一覧]** には、[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターの IntelliSense コードによって生成された構文エラーとセマンティック エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Error List** displays the syntax and semantic errors that are generated from the IntelliSense code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="features-of-the-error-list"></a><span data-ttu-id="2f3af-104">[エラー一覧] の機能</span><span class="sxs-lookup"><span data-stu-id="2f3af-104">Features of the Error List</span></span>  
 <span data-ttu-id="2f3af-105">**[エラー一覧]** は、次の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-105">The **Error List** provides the following functionality:</span></span>  
  
-   <span data-ttu-id="2f3af-106">スクリプトを編集すると、 **クエリ エディターの IntelliSense によって生成されたエラーと警告が** [エラー一覧] [!INCLUDE[ssDE](../../includes/ssde-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-106">As you edit scripts, the **Error List** displays the errors and warnings produced by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="2f3af-107">任意のエラー メッセージ エントリをダブルクリックして、エラーを生成したスクリプト ファイルのタブにフォーカスを設定し、エラーの場所に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-107">You can double-click any error message entry to focus on the tab for the script file that generated the error, and move to the error location.</span></span>  
  
-   <span data-ttu-id="2f3af-108">どのエントリを表示するか、および各エントリにどの情報列を表示するかをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-108">You can filter which entries you want to display, and which columns of information you want appear for each entry.</span></span>  
  
-   <span data-ttu-id="2f3af-109">エラーを修正すると、そのエラー エントリが **[エラー一覧]** から削除されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-109">After you fix an error, the error entry is removed from the **Error List**.</span></span>  
  
-   <span data-ttu-id="2f3af-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルのタブを閉じると、そのファイルのエラーが **[エラー一覧]** から削除されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-110">When you close the tab for a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file, the errors for that file are removed from the **Error List**.</span></span>  
  
## <a name="working-with-the-error-list"></a><span data-ttu-id="2f3af-111">[エラー一覧] の操作</span><span class="sxs-lookup"><span data-stu-id="2f3af-111">Working with the Error List</span></span>  
 <span data-ttu-id="2f3af-112">**[エラー一覧]** を表示するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2f3af-112">To display the **Error List**, do one of the following:</span></span>  
  
-   <span data-ttu-id="2f3af-113">**[表示]** メニューの **[エラー一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f3af-113">On the **View** menu, click **Error List**.</span></span>  
  
-   <span data-ttu-id="2f3af-114">Ctrl キーを押しながら\\キーを押し、次に Ctrl キーを押しながら E キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-114">Enter the keyboard shortcut CTRL+\\, CTRL+E.</span></span>  
  
 <span data-ttu-id="2f3af-115">**[エラー一覧]** が開いたら、次の操作を行うことで表示をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-115">After you open the **Error List**, you can customize your view by performing the following actions:</span></span>  
  
-   <span data-ttu-id="2f3af-116">一覧を並べ替えるには、任意の列ヘッダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f3af-116">To sort the list, click any column header.</span></span> <span data-ttu-id="2f3af-117">並べ替えに使用する列を追加するには、&lt;localizedText&gt;Shift&lt;/localizedText&gt; キーを押しながら、他の列ヘッダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f3af-117">To sort again by an additional column, press and hold the SHIFT key, and then click another column header.</span></span>  
  
-   <span data-ttu-id="2f3af-118">表示する列と非表示にする列を選択するには、ショートカット メニューの **[列の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f3af-118">To select which columns are displayed and which are hidden, select **Show Columns** from the shortcut menu.</span></span>  
  
-   <span data-ttu-id="2f3af-119">列の表示順を変更するには、列ヘッダーを左右にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2f3af-119">To change the order in which columns are displayed, drag any column header to the left or right.</span></span>  
  
 <span data-ttu-id="2f3af-120">**[エラー一覧]** は特定のエラーに関する詳細情報にリンクしていません。</span><span class="sxs-lookup"><span data-stu-id="2f3af-120">The **Error List** does not link to additional information about specific errors.</span></span>  
  
## <a name="transact-sql-errors-in-management-studio"></a><span data-ttu-id="2f3af-121">Management Studio の Transact-SQL エラー</span><span class="sxs-lookup"><span data-stu-id="2f3af-121">Transact-SQL Errors in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="2f3af-122">では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトのエラーが次の場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-122">displays errors for [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in the following locations:</span></span>  
  
-   <span data-ttu-id="2f3af-123">**[エラー一覧]** には、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] エディターの IntelliSense によって検出されたすべての構文エラーとセマンティック エラーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-123">The **Error List** contains all syntax and semantic errors found by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor.</span></span> <span data-ttu-id="2f3af-124">このエラーの一覧は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトの編集に伴って動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-124">This list of errors is dynamically updated as you edit [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="2f3af-125">一覧には、各 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトでエディターが検出したすべてのエラーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-125">The list includes all errors that the editor has found in each [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="2f3af-126">エディターは、スクリプト内でエラーを検出した後に、ファイルの解析を停止しません。</span><span class="sxs-lookup"><span data-stu-id="2f3af-126">The editor does not stop parsing a file after encountering errors in a script.</span></span> <span data-ttu-id="2f3af-127">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] エディターの IntelliSense はすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文要素をサポートするわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2f3af-127">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="2f3af-128">**[エラー一覧]** には、IntelliSense がサポートする [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文のエラーのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-128">The **Error List** contains only errors from the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that is supported by IntelliSense.</span></span>  
  
-   <span data-ttu-id="2f3af-129">**クエリ エディター ウィンドウの下部にある** [メッセージ] [!INCLUDE[ssDE](../../includes/ssde-md.md)] タブには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] スクリプトの実行時に [!INCLUDE[tsql](../../includes/tsql-md.md)] から返されたすべてのエラーとメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-129">The **Messages** tab at the bottom of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window displays all errors and messages that are returned by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] when a [!INCLUDE[tsql](../../includes/tsql-md.md)] script is executed.</span></span> <span data-ttu-id="2f3af-130">この一覧は、スクリプトが再び実行されるまで変更されません。</span><span class="sxs-lookup"><span data-stu-id="2f3af-130">This list does not change until you execute the script again.</span></span> <span data-ttu-id="2f3af-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、1 つまたは 2 つのコンパイル エラーを検出すると、バッチの解析を停止します。そのため、 **[メッセージ]** タブにはスクリプトのすべてのエラーが一覧表示されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2f3af-131">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stops parsing a batch after it finds one or two compile errors; therefore, the **Messages** tab might not list all errors in a script.</span></span>  
  
 <span data-ttu-id="2f3af-132">エラーが両方の場所に一覧表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2f3af-132">Sometimes errors are listed in both locations.</span></span> <span data-ttu-id="2f3af-133">たとえば、 **[エラー一覧]** に表示されている構文エラーがスクリプト ファイルに含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2f3af-133">For example, a script file might have a syntax error that is listed in the **Error List**.</span></span> <span data-ttu-id="2f3af-134">このスクリプトを、エラーを修正する前に実行すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] パーサーが同じ状態を検出し、エラー メッセージの別のコピーを **[メッセージ]** タブに返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2f3af-134">If you execute the script before you correct the error, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] parser can detect the same condition and return another copy of the error message in the **Messages** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f3af-135">**[エラー一覧]** に表示されるのは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターからのエラーのみです。MDX、DMX、または XML/A エディターからのエラーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="2f3af-135">The **Error List** only displays errors from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor; it does not display errors from the MDX, DMX, or XML/A Editors.</span></span> <span data-ttu-id="2f3af-136">MDX、DMX、および XML/A のすべてのエラーは、それらのエディターの **[メッセージ]** タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-136">All MDX, DMX, and XML/A errors are displayed in the **Messages** tab in those editors.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="2f3af-137">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="2f3af-137">UI element list</span></span>  
 <span data-ttu-id="2f3af-138">**[エラー一覧]** を開くと、次の列に情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-138">When the **Error List** is open, the information is displayed in the following columns:</span></span>  
  
 <span data-ttu-id="2f3af-139">**[既定の順序]**</span><span class="sxs-lookup"><span data-stu-id="2f3af-139">**Default Order**</span></span>  
 <span data-ttu-id="2f3af-140">エントリの作成順を示す整数を表示します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-140">Displays an integer that indicates the order in which an entry was generated.</span></span>  
  
 <span data-ttu-id="2f3af-141">**説明**</span><span class="sxs-lookup"><span data-stu-id="2f3af-141">**Description**</span></span>  
 <span data-ttu-id="2f3af-142">エラー エントリのテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-142">Displays the text of the error entry.</span></span> <span data-ttu-id="2f3af-143">説明文が長い場合には、追加の行に折り返されます。</span><span class="sxs-lookup"><span data-stu-id="2f3af-143">Lengthy descriptions wrap onto additional lines.</span></span>  
  
 <span data-ttu-id="2f3af-144">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="2f3af-144">**File**</span></span>  
 <span data-ttu-id="2f3af-145">エラーを生成したスクリプト ファイルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-145">Displays the name of the script file that generated the error.</span></span>  
  
 <span data-ttu-id="2f3af-146">**線**</span><span class="sxs-lookup"><span data-stu-id="2f3af-146">**Line**</span></span>  
 <span data-ttu-id="2f3af-147">エラーを含むコード行を示す整数を表示します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-147">Displays an integer that indicates which line of the code includes the error.</span></span>  
  
 <span data-ttu-id="2f3af-148">**列**</span><span class="sxs-lookup"><span data-stu-id="2f3af-148">**Column**</span></span>  
 <span data-ttu-id="2f3af-149">コード行におけるエラーの位置を示す整数を表示します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-149">Displays an integer that indicates the position of the error in the line of code.</span></span>  
  
 <span data-ttu-id="2f3af-150">**プロジェクト**</span><span class="sxs-lookup"><span data-stu-id="2f3af-150">**Project**</span></span>  
 <span data-ttu-id="2f3af-151">スクリプト ファイルを含むプロジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="2f3af-151">Displays the name of the project that includes the script file.</span></span>  
