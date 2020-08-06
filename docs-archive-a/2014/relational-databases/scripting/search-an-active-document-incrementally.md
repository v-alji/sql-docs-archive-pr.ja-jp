---
title: アクティブ ドキュメントのインクリメンタル検索
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
author: rothja
ms.author: jroth
ms.openlocfilehash: aefc2f0b7abff5992a8f4f7817e564ef1b72009d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633052"
---
# <a name="search-an-active-document-incrementally"></a><span data-ttu-id="eb980-102">アクティブ ドキュメントのインクリメンタル検索</span><span class="sxs-lookup"><span data-stu-id="eb980-102">Search an Active Document Incrementally</span></span>
  <span data-ttu-id="eb980-103">テキストを入力して、1 つのドキュメント内またはウィンドウ内のインクリメンタル検索を実行できます。</span><span class="sxs-lookup"><span data-stu-id="eb980-103">You can search a single document or window incrementally by entering text.</span></span> <span data-ttu-id="eb980-104">検索操作では、ドキュメント内またはウィンドウ内のインクリメンタル検索の対象として入力した文字の最初の一致項目のセットが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-104">The search operation highlights the first set of characters that matches the characters entered during the incremental search in the document or window.</span></span> <span data-ttu-id="eb980-105">インクリメンタル検索では、ドキュメント内またはウィンドウ内のテキストのうち、非表示になっているテキストが検索対象から自動的に除外されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-105">Incremental search automatically searches all of the text within a document or window except for text that has been hidden.</span></span>  
  
 <span data-ttu-id="eb980-106">インクリメンタル検索の場合、 **[大文字と小文字を区別する]** オプションに関しては、直前の検索の基準がそのまま使用されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-106">For the **Match case** option, incremental search uses the criteria from your previous search.</span></span> <span data-ttu-id="eb980-107">たとえば、 **[フォルダーを指定して検索]** ダイアログ ボックスを使用して複数のファイルの検索を実行したときに **[大文字と小文字を区別する]** をオンにしていれば、次回のインクリメンタル検索でも大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-107">For example, if you searched across multiple files using the **Find in Files** dialog box and select **Match Case**, and you next search incrementally, the search will be case-sensitive.</span></span>  
  
### <a name="to-search-incrementally"></a><span data-ttu-id="eb980-108">インクリメンタル検索を実行するには</span><span class="sxs-lookup"><span data-stu-id="eb980-108">To search incrementally</span></span>  
  
1.  <span data-ttu-id="eb980-109">検索するファイルまたはウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="eb980-109">Open the file or window to you want to search.</span></span>  
  
2.  <span data-ttu-id="eb980-110">**[編集]** メニューの **[詳細設定]** をポイントし、 **[インクリメンタル検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb980-110">On the **Edit** menu, point to **Advanced**, and then click **Incremental Search**.</span></span>  
  
     <span data-ttu-id="eb980-111">カーソルのアイコンが、検索方向を示す矢印の付いた双眼鏡に変わり、ステータス バーに [インクリメンタル検索] と表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-111">The cursor icon changes to a binocular with an arrow, indicating the search direction, and the status bar displays "Incremental Search."</span></span>  
  
3.  <span data-ttu-id="eb980-112">テキスト文字列の入力を始めます。</span><span class="sxs-lookup"><span data-stu-id="eb980-112">Begin typing the text string.</span></span>  
  
     <span data-ttu-id="eb980-113">入力しているテキストがステータス バーに表示され、そのテキストの最初の一致項目がエディターで強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-113">The status bar displays the text you are entering while the editor highlights the first occurrence that matches the text.</span></span> <span data-ttu-id="eb980-114">入力を続けると、エディターでは次の一致項目に移動して、その項目が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-114">As you continue typing, the editor moves to the next match and highlights it.</span></span> <span data-ttu-id="eb980-115">一致項目がない場合は、ステータス バーに以下のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb980-115">If no matches are available, the status bar displays the following.</span></span>  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 <span data-ttu-id="eb980-116">インクリメンタル検索は、ドキュメント内の現在の位置を起点として、上から下へ、左から右へと進んでいきます。</span><span class="sxs-lookup"><span data-stu-id="eb980-116">Incremental searches are performed from the current location in the document downwards from left to right.</span></span> <span data-ttu-id="eb980-117">キーボード ショートカット キーを使用してインクリメンタル検索を実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="eb980-117">Incremental searches can be done using keyboard shortcut keys.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb980-118">キーボード ショートカット キーの完全な一覧については、「 [SQL Server Management Studio のキーボード ショートカット](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb980-118">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb980-119">参照</span><span class="sxs-lookup"><span data-stu-id="eb980-119">See Also</span></span>  
 <span data-ttu-id="eb980-120">[検索と置換](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="eb980-120">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="eb980-121">[ドキュメントの対話形式の検索](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="eb980-121">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="eb980-122">[結果一覧を使用してドキュメントを検索する方法](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="eb980-122">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="eb980-123">[ワイルドカードを使用したテキスト検索](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="eb980-123">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="eb980-124">正規表現によるテキストの検索</span><span class="sxs-lookup"><span data-stu-id="eb980-124">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
