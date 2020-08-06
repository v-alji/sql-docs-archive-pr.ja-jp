---
title: '[フルテキスト インデックスの列] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f1cd2c94739a13e1820d8c05b338abd91d8a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741530"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="79142-102">[フルテキスト インデックスの列] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="79142-102">Full-Text Index Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="79142-103">このダイアログ ボックスには、テーブル デザイナーで開いたテーブルのテキスト インデックスに含まれる列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="79142-103">This dialog box lists the columns participating in the full-text index for the table open in Table Designer.</span></span> <span data-ttu-id="79142-104">このダイアログ ボックスにアクセスするには、テーブル デザイナーのテーブルを右クリックして **[フルテキスト インデックス]** を選択すると表示される **[フルテキスト インデックス]** ダイアログ ボックスで、表示または編集する列のインデックスをクリックし、右のグリッドの **[列]** フィールドをクリックして、省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79142-104">To access this dialog box, right-click the table in Table Designer, choose **Full-Text Index**, and in the **Full-Text Index** dialog box, click the index with columns you want to view or edit, click the **Columns** field in the grid to the right, and click the ellipses (**...**).</span></span>  
  
## <a name="options"></a><span data-ttu-id="79142-105">オプション</span><span class="sxs-lookup"><span data-stu-id="79142-105">Options</span></span>  
 <span data-ttu-id="79142-106">**列**</span><span class="sxs-lookup"><span data-stu-id="79142-106">**Column**</span></span>  
 <span data-ttu-id="79142-107">フルテキスト インデックスに指定されている列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="79142-107">Shows the names of columns participating in the full-text index.</span></span> <span data-ttu-id="79142-108">列を追加するには、最初の空のセルの中をクリックし、ドロップダウン リストから列を選択します。</span><span class="sxs-lookup"><span data-stu-id="79142-108">To add a column, click in the first empty cell and choose a column from the drop-down list.</span></span> <span data-ttu-id="79142-109">テキスト ベースのデータ型の列または画像データ型の列だけが選択できます。</span><span class="sxs-lookup"><span data-stu-id="79142-109">Only columns with either text-based or image data types will be accessible.</span></span>  
  
 <span data-ttu-id="79142-110">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="79142-110">**Data Type**</span></span>  
 <span data-ttu-id="79142-111">各列のデータ型を表示します。</span><span class="sxs-lookup"><span data-stu-id="79142-111">Shows the data type for each column.</span></span> <span data-ttu-id="79142-112">これは、読み取り専用プロパティです。</span><span class="sxs-lookup"><span data-stu-id="79142-112">This is a read-only property.</span></span> <span data-ttu-id="79142-113">データ型を変更するには、テーブル デザイナーでテーブルを開き、列をクリックして、 **[列のプロパティ]** タブでデータ型を編集します。</span><span class="sxs-lookup"><span data-stu-id="79142-113">To change a data type, open the table in Table Designer, click the column, and edit the data type in the **Column Properties** tab.</span></span>  
  
 <span data-ttu-id="79142-114">**[列による型付け]**</span><span class="sxs-lookup"><span data-stu-id="79142-114">**Typed by Column**</span></span>  
 <span data-ttu-id="79142-115">データ型が `image` の列だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="79142-115">Applies only to columns with the data type `image`.</span></span> <span data-ttu-id="79142-116">ドロップダウン リストが表示され、現在の列のデータ型を表す他の列のデータ型を選択できます。</span><span class="sxs-lookup"><span data-stu-id="79142-116">Provides a drop-down list from which you can choose which of the other columns represent the data type of this column.</span></span> <span data-ttu-id="79142-117">現在の列が `image` データ型でない場合、値は [なし] になります。</span><span class="sxs-lookup"><span data-stu-id="79142-117">If this column is not of the `image` data type the value will be None.</span></span>  
  
 <span data-ttu-id="79142-118">データ型が `image` の列は、Microsoft Office ファイル (.doc、.xls、および .ppt ファイル)、テキスト ファイル (.txt ファイル)、HTML ファイル (.htm ファイル) を格納でき、その列のデータ型を image に設定することで、ファイルの中身を検索するフルテキスト検索ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="79142-118">Columns with the data type `image` can contain Microsoft Office files (.doc, .xls, and .ppt files), text files (.txt files), and HTML files (.htm files), and setting the data type of that column to image allows the full-text search to search the contents of the files.</span></span>  
  
 <span data-ttu-id="79142-119">**Language**</span><span class="sxs-lookup"><span data-stu-id="79142-119">**Language**</span></span>  
 <span data-ttu-id="79142-120">使用できる言語を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="79142-120">Lists available languages.</span></span> <span data-ttu-id="79142-121">列データに適した言語をドロップダウン リストから選択してください。</span><span class="sxs-lookup"><span data-stu-id="79142-121">Choose the language from the drop-down list appropriate for your column data.</span></span> <span data-ttu-id="79142-122">たとえば、英語のオペレーティング システムを使用している場合に、ドイツ語のテキストを含む列にインデックスを設定するときは、ドロップダウン リストからドイツ語を選択することによりインデックスのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="79142-122">For example, if you are using an English operating system, but you want to index a column that contains German text, choose German from the drop-down list to improve the index's performance.</span></span>  
  
 <span data-ttu-id="79142-123">**[統計的セマンティクス]**</span><span class="sxs-lookup"><span data-stu-id="79142-123">**Statistical Semantics**</span></span>  
 <span data-ttu-id="79142-124">選択されている列に対するセマンティック インデックスを有効にするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="79142-124">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="79142-125">詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79142-125">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="79142-126">**[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、 **[統計的セマンティクス]** チェック ボックスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="79142-126">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="79142-127">**[言語]** を選択する前に **[統計的セマンティクス]** を選択した場合、ドロップダウン コンボ ボックスで使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。</span><span class="sxs-lookup"><span data-stu-id="79142-127">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79142-128">参照</span><span class="sxs-lookup"><span data-stu-id="79142-128">See Also</span></span>  
 <span data-ttu-id="79142-129">[[フルテキスト インデックス] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="79142-129">[Full-Text Index Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md)</span></span>  
  
  
