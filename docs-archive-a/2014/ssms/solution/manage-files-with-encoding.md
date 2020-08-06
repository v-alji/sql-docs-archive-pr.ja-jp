---
title: エンコーディングによるファイルの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9b0aaa123001fed3f6ad42ea9d642e4007e2640f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645957"
---
# <a name="manage-files-with-encoding"></a><span data-ttu-id="d3638-102">エンコーディングによるファイルの管理</span><span class="sxs-lookup"><span data-stu-id="d3638-102">Manage Files with Encoding</span></span>
  <span data-ttu-id="d3638-103">特定の言語や特定のプラットフォームでコードを正しく表示するために、特定の文字エンコードをファイルに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d3638-103">To facilitate the display of your code in a particular language and on a particular platform, you can associate a particular character encoding with a file.</span></span>  
  
## <a name="opening-files"></a><span data-ttu-id="d3638-104">ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="d3638-104">Opening Files</span></span>  
 <span data-ttu-id="d3638-105">ファイルの編集に使用するエディターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d3638-105">You can choose the editor you want to use to edit the file.</span></span>  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a><span data-ttu-id="d3638-106">特定のエディターでファイルを開くには</span><span class="sxs-lookup"><span data-stu-id="d3638-106">To open a file with a specific editor</span></span>  
  
1.  <span data-ttu-id="d3638-107">**[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3638-107">On the **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="d3638-108">**[ファイルを開く]** ダイアログ ボックスでファイル名を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3638-108">In the **Open File** dialog box, select the file name.</span></span>  
  
3.  <span data-ttu-id="d3638-109">**[開く]** ボタンの横にある矢印をクリックし、表示されるメニューから **[ファイルを開くアプリケーションの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3638-109">Click the arrow next to the **Open** button, and then click**Open With** from the menu that appears.</span></span>  
  
4.  <span data-ttu-id="d3638-110">**[このファイルを開くのに使用するプログラムを選択してください]** 一覧でエディターを選択し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3638-110">In the **Select a program to open** list, select an editor, and then click **Open**.</span></span> <span data-ttu-id="d3638-111">特定のエンコードでファイルを開くには、SQL クエリ エディター (エンコード付き)、XML エディター (エンコード付き) など、エンコード サポート付きのエディターを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3638-111">To open the file with a particular encoding, select an editor with encoding support, such as SQL Query Editor with Encoding or XML Editor with Encoding.</span></span>  
  
## <a name="saving-files"></a><span data-ttu-id="d3638-112">ファイルの保存</span><span class="sxs-lookup"><span data-stu-id="d3638-112">Saving Files</span></span>  
 <span data-ttu-id="d3638-113">西ヨーロッパ言語や東ヨーロッパ言語など、さまざまな言語をサポートするために、Unicode エンコードまたは他のコード ページを指定してコードを保存することができます。</span><span class="sxs-lookup"><span data-stu-id="d3638-113">You can also save your code with a Unicode encoding or a different code page to support various languages, such as Western European or Eastern European.</span></span> <span data-ttu-id="d3638-114">特定の言語でコードを正しく表示するためにその文字エンコードをファイルに関連付けることや、特定のオペレーティング システムをサポートするために行終端文字の種類を選択することも可能です。</span><span class="sxs-lookup"><span data-stu-id="d3638-114">You can associate a particular character encoding with a file to facilitate the display of your code in that language, as well as a line-ending type to support a particular operating system.</span></span> <span data-ttu-id="d3638-115">また、ファイル名に使用する一部の文字は、Unicode エンコード付きでないと保存できません。</span><span class="sxs-lookup"><span data-stu-id="d3638-115">Also, some characters, when used in file names, cannot be saved unless they are saved with Unicode encoding.</span></span>  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a><span data-ttu-id="d3638-116">他のエンコードまたは行終端文字の種類を指定してファイルを保存するには</span><span class="sxs-lookup"><span data-stu-id="d3638-116">To save a file with a different encoding or line ending type</span></span>  
  
1.  <span data-ttu-id="d3638-117">**[ファイル]** メニューの **[名前を付けて \<filename> を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3638-117">On the **File** menu, click **Save \<filename> As**.</span></span>  
  
2.  <span data-ttu-id="d3638-118">**[ファイル名を付けて保存]** ダイアログ ボックスで、 **[保存]** ボタンを展開し、 **[エンコード付きで保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3638-118">In the **Save File As** dialog, expand the **Save** button, and then click **Save with Encoding**.</span></span>  
  
3.  <span data-ttu-id="d3638-119">**[保存オプションの詳細設定]** ダイアログ ボックスの **[エンコード]** 一覧から目的のエンコードを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3638-119">In the **Advanced Save Options** dialog box, select the encoding you want from the **Encoding** list.</span></span>  
  
4.  <span data-ttu-id="d3638-120">**[行の終わり]** 一覧から目的の行終端文字の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3638-120">From the **Line Endings**list, select the type of line ending you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3638-121">Unicode エンコードを指定してファイルを保存した場合は、そのファイルをバイナリ ファイルとして [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe にチェックインする必要があります。Visual SourceSafe は、Unicode で保存したファイルのマージ、比較、差分の表示をサポートしていないからです。</span><span class="sxs-lookup"><span data-stu-id="d3638-121">If you save your file your file with Unicode encoding, the file should be checked into [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe as a binary file because Visual SourceSafe does not support merging, comparing, and showing differences between files that are saved as Unicode.</span></span>  
  
 <span data-ttu-id="d3638-122">Visual SourceSafe を使用して ANSI、UTF8、または Unicode のファイルを格納している場合は、次の制限事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d3638-122">If you are using Visual SourceSafe to store files with ANSI, UTF8, or Unicode, be aware of the following limitations for each:</span></span>  
  
-   <span data-ttu-id="d3638-123">ANSI ファイルでは、現在のコード ページでサポートされている文字だけを使用できます。完全には対応できない言語があります。</span><span class="sxs-lookup"><span data-stu-id="d3638-123">ANSI files allow only characters that are supported in the current code page, which limits international use.</span></span>  
  
-   <span data-ttu-id="d3638-124">Unicode ファイルはバイナリ ファイルとして処理されるので、共有チェックアウト、差分チェック、マージの各機能を使用できません。</span><span class="sxs-lookup"><span data-stu-id="d3638-124">Unicode files cannot use shared checkout, difference checking, or merging functionality because they are handled as binary files.</span></span> <span data-ttu-id="d3638-125">この形式は、さまざまな言語のファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3638-125">You can use this format in international files.</span></span>  
  
-   <span data-ttu-id="d3638-126">UTF8 ファイルは、Visual SourceSafe で安全に動作しません。チェックイン、チェックアウト、差分チェック、マージの実行時に、UTF8 ファイル エディターで問題を起こす原因になる変更が加えられるためです。</span><span class="sxs-lookup"><span data-stu-id="d3638-126">UTF8 files do not work safely with Visual SourceSafe because changes that cause problems for UTF8 file editors are made during check in, check out, difference checking, and merging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3638-127">参照</span><span class="sxs-lookup"><span data-stu-id="d3638-127">See Also</span></span>  
 <span data-ttu-id="d3638-128">[ソリューションとプロジェクトを管理するファイル](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="d3638-128">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 [<span data-ttu-id="d3638-129">ファイル拡張子をコード エディターに関連付ける方法</span><span class="sxs-lookup"><span data-stu-id="d3638-129">Associate File Extensions to a Code Editor</span></span>](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
  
  
