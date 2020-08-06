---
title: '[クエリオプション] の [結果] ([グリッド] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
author: rothja
ms.author: jroth
ms.openlocfilehash: bf300dd5071128b0259230ae788a27595bd8d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644126"
---
# <a name="query-options-results-grid-page"></a><span data-ttu-id="ab0f2-102">[クエリ オプション] の [結果] ([グリッド] ページ)</span><span class="sxs-lookup"><span data-stu-id="ab0f2-102">Query Options Results (Grid Page)</span></span>
  <span data-ttu-id="ab0f2-103">このページを使用すると、クエリ結果セットをグリッド形式で表示するためのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-103">Use this page to specify the options for displaying a query result set in grid format.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab0f2-104">Options</span><span class="sxs-lookup"><span data-stu-id="ab0f2-104">Options</span></span>  
 <span data-ttu-id="ab0f2-105">**[結果セットにクエリを含める]**</span><span class="sxs-lookup"><span data-stu-id="ab0f2-105">**Include the query in the result set**</span></span>  
 <span data-ttu-id="ab0f2-106">クエリのテキストを結果セットの一部として返します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-106">Returns the text of the query as part of the result set.</span></span>  
  
 <span data-ttu-id="ab0f2-107">**[結果のコピーまたは保存時に列のヘッダーを含める]**</span><span class="sxs-lookup"><span data-stu-id="ab0f2-107">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="ab0f2-108">結果をクリップボードにコピーしたりファイルに保存したりするときに、列のヘッダー (タイトル) を含めます。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-108">Include column headers (titles) when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="ab0f2-109">保存またはコピーされる結果データに列の見出しを含めずに、データだけ保存またはコピーするには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-109">Clear this check box if you do not want saved or copied result data to have only the data, and not the column headings.</span></span>  
  
 <span data-ttu-id="ab0f2-110">**[実行後に結果を破棄する]**</span><span class="sxs-lookup"><span data-stu-id="ab0f2-110">**Discard results after execution**</span></span>  
 <span data-ttu-id="ab0f2-111">画面表示がクエリ結果を受け取った後にクエリ結果を破棄することによって、メモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-111">Free memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="ab0f2-112">**[結果を別のタブに表示する]**</span><span class="sxs-lookup"><span data-stu-id="ab0f2-112">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="ab0f2-113">結果セットを、クエリ ドキュメント ウィンドウの下部ではなく、新しいドキュメント ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-113">Display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="ab0f2-114">**[クエリ実行後に [結果] タブに切り替える]**</span><span class="sxs-lookup"><span data-stu-id="ab0f2-114">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="ab0f2-115">画面のフォーカスを自動的に結果セットに設定します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-115">Automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="ab0f2-116">**[取得される最大文字数]**</span><span class="sxs-lookup"><span data-stu-id="ab0f2-116">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="ab0f2-117">**XML 以外のデータ**:</span><span class="sxs-lookup"><span data-stu-id="ab0f2-117">**Non XML data**:</span></span>  
  
 <span data-ttu-id="ab0f2-118">1 ～ 65,535 の値を入力して、各セルに表示される最大文字数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-118">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab0f2-119">大きな文字数を指定すると、結果セット内のデータが切り捨てられたように見える場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-119">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="ab0f2-120">各セルに表示される最大文字数は、フォントのサイズに依存します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-120">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="ab0f2-121">大きな結果セットが返された場合、このボックスに大きな値を指定していると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のメモリ上での実行速度が低下したり、システムのパフォーマンスに悪影響が及んだりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-121">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="ab0f2-122">**XML データ**:</span><span class="sxs-lookup"><span data-stu-id="ab0f2-122">**XML data**:</span></span>  
  
 <span data-ttu-id="ab0f2-123">**[1 MB]**、 **[2 MB]**、または **[5 MB]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-123">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="ab0f2-124">すべての文字を取得する場合は、 **[無制限]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-124">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="ab0f2-125">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="ab0f2-125">**Reset to Default**</span></span>  
 <span data-ttu-id="ab0f2-126">このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="ab0f2-126">Resets all values on this page to the original default values.</span></span>  
  
  
