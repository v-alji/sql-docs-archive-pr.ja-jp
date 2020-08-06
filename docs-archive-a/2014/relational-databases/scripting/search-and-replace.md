---
title: 検索と置換
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- match case [SQL Server]
- undo operations
- searches [SQL Server Management Studio]
- replacing text
- quick search and replaces [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], undo
- Query Editor [SQL Server Management Studio], searching
- regular expressions [SQL Server Management Studio]
- finding text [SQL Server Management Studio]
- text [SQL Server], search and replace operations
- finding [SQL Server Management Studio]
- locating text
- Query Editor [SQL Server Management Studio], replacing text
- Find and Replace dialog box
- wildcard options [SQL Server Management Studio]
- match whole word [SQL Server]
- searches [SQL Server Management Studio], replacing
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
author: rothja
ms.author: jroth
ms.openlocfilehash: 55422fa7201213477426c7bc25c45ff05acf8945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633049"
---
# <a name="search-and-replace"></a><span data-ttu-id="d2df3-102">検索と置換</span><span class="sxs-lookup"><span data-stu-id="d2df3-102">Search and Replace</span></span>
  <span data-ttu-id="d2df3-103">テキストの検索と置換にはいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="d2df3-103">There are several different ways to find and replace text.</span></span> <span data-ttu-id="d2df3-104">**[編集]** メニューの **[検索と置換]** には、 **[クイック検索]** 、 **[クイック置換]** 、 **[フォルダーを指定して検索]** 、 **[フォルダーを指定して置換]** という 4 つのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d2df3-104">On the **Edit** menu, **Find and Replace** offers four choices: **Quick Find**, **Quick Replace**, **Find in Files**, or **Replace in Files**.</span></span> <span data-ttu-id="d2df3-105">各オプションを選択すると、各バージョンの **[検索と置換]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2df3-105">Each of these opens versions of the **Find and Replace** dialog box.</span></span> <span data-ttu-id="d2df3-106">ダイアログ ボックスを使用しないで、インクリメンタル検索キーボード ショートカット キーによって検索することも可能です。</span><span class="sxs-lookup"><span data-stu-id="d2df3-106">You can also search without a dialog box by using incremental search keyboard shortcut keys.</span></span> <span data-ttu-id="d2df3-107">これらの方法によって、検索と置換の範囲を設定することや、検索一致項目や置換項目を確認する方法を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="d2df3-107">These techniques allow you to control the scope of find and replace, and choose the method of reviewing search matches and replacements.</span></span>  
  
 <span data-ttu-id="d2df3-108">テキストの検索と置換に関する注意点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2df3-108">You should consider the following when you search and replace text:</span></span>  
  
-   <span data-ttu-id="d2df3-109">**[検索と置換]** ダイアログ ボックスで設定したオプションは、すべての検索操作に影響します。</span><span class="sxs-lookup"><span data-stu-id="d2df3-109">Options set in the **Find and Replace** dialog box affect all the searches.</span></span> <span data-ttu-id="d2df3-110">具体的には、 **[大文字と小文字を区別する]** 、 **[単語単位]** 、 **[上へ検索]** 、 **[非表示のテキストを検索]** 、 **[ワイルドカード]** 、 **[正規表現]** 、 **[検索対象: すべての開かれているドキュメント]** 、 **[検索対象: 現在のプロジェクト]** の各オプションです。</span><span class="sxs-lookup"><span data-stu-id="d2df3-110">These options include **Match case**, **Match whole word**, **Search up**, **Search hidden text**, **Wildcards**, **Regular Expressions**, **Look in All Open Documents**, and **Look in Current Project**.</span></span> <span data-ttu-id="d2df3-111">すべてのバージョンの **[検索と置換]** ダイアログ ボックスですべてのオプションを使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d2df3-111">All options are not available in all versions of the **Find and Replace** dialog box.</span></span>  
  
-   <span data-ttu-id="d2df3-112">**[元に戻す]** を使用できるのは、置換操作後に開いたままにしておいたドキュメントに限られます。</span><span class="sxs-lookup"><span data-stu-id="d2df3-112">**Undo** is available only for documents left open after a replace operation.</span></span>  
  
-   <span data-ttu-id="d2df3-113">複数のファイルを対象にした **[すべて置換]** 操作に対して **[元に戻す]** を使用すると、すべての対象ファイルに対して一括処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="d2df3-113">**Undo** for a **Replace All** operation that spans more than one file is considered a single, bulk action across all the affected files.</span></span> <span data-ttu-id="d2df3-114">つまり、一部のファイルの変更を元に戻し、他のファイルの変更をそのまま残す、ということはできません。</span><span class="sxs-lookup"><span data-stu-id="d2df3-114">That is, you cannot undo the change in some files while retaining the change in other files.</span></span>  
  
 <span data-ttu-id="d2df3-115">一般に、グラフィカル ビューを持つ項目の検索はできません。</span><span class="sxs-lookup"><span data-stu-id="d2df3-115">Generally, you cannot search items with graphical views.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2df3-116">参照</span><span class="sxs-lookup"><span data-stu-id="d2df3-116">See Also</span></span>  
 <span data-ttu-id="d2df3-117">[アクティブ ドキュメントのインクリメンタル検索](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="d2df3-117">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="d2df3-118">[ドキュメントの対話形式の検索](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="d2df3-118">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="d2df3-119">[結果一覧を使用してドキュメントを検索する方法](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="d2df3-119">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="d2df3-120">[ワイルドカードを使用したテキスト検索](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="d2df3-120">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="d2df3-121">正規表現によるテキストの検索</span><span class="sxs-lookup"><span data-stu-id="d2df3-121">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
