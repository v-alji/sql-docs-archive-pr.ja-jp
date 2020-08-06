---
title: '[フラットファイル変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledestadapter.connection.f1
helpviewer_keywords:
- Flat File Destination Editor
ms.assetid: b01571fa-bc19-4742-8eed-ac163172a919
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6997b72851c2b7bfc56445e6ddb01cfe6e9b04cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632608"
---
# <a name="flat-file-destination-editor-connection-manager-page"></a><span data-ttu-id="1446d-102">[フラット ファイル変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="1446d-102">Flat File Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="1446d-103">**[フラット ファイル変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、変換先のフラット ファイル接続を選択したり、既存の変換先ファイルに対して上書きまたは追加のどれを実行するかを指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="1446d-103">Use the **Connection Manager** page of the **Flat File Destination Editor** dialog box to select the flat file connection for the destination, and to specify whether to overwrite or append to the existing destination file.</span></span> <span data-ttu-id="1446d-104">フラット ファイル変換先は、データをテキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1446d-104">The flat file destination writes data to a text file.</span></span> <span data-ttu-id="1446d-105">テキスト ファイルには、区切り形式、固定幅形式、行区切り記号付き固定幅形式、または幅合わせしない形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1446d-105">This text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.</span></span>  
  
 <span data-ttu-id="1446d-106">フラット ファイル変換先の詳細については、「 [Flat File Destination](data-flow/flat-file-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1446d-106">To learn more about the Flat File destination, see [Flat File Destination](data-flow/flat-file-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1446d-107">オプション</span><span class="sxs-lookup"><span data-stu-id="1446d-107">Options</span></span>  
 <span data-ttu-id="1446d-108">**フラット ファイル接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="1446d-108">**Flat File connection manager**</span></span>  
 <span data-ttu-id="1446d-109">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1446d-109">Select an existing connection manager by using the list box, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="1446d-110">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="1446d-110">**New**</span></span>  
 <span data-ttu-id="1446d-111">**[フラット ファイル形式]** および **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1446d-111">Create a new connection by using the **Flat File Format** and **Flat File Connection Manager Editor** dialog boxes.</span></span>  
  
 <span data-ttu-id="1446d-112">標準のフラット ファイル形式である、区切り形式、固定幅形式、および幅合わせしない形式に加えて、 **[フラット ファイル形式]** ダイアログ ボックスには 4 つ目のオプションとして **[行区切り記号付きの固定幅]** が用意されています。</span><span class="sxs-lookup"><span data-stu-id="1446d-112">In addition to the standard flat file formats of delimited, fixed width, and ragged right, the **Flat File Format** dialog box has a fourth option, **Fixed width with row delimiters**.</span></span> <span data-ttu-id="1446d-113">このオプションは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] がデータの最終列としてダミー列を追加する、特殊な幅合わせしない形式を表します。</span><span class="sxs-lookup"><span data-stu-id="1446d-113">This option represents a special case of the ragged-right format in which [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] adds a dummy column as the final column of data.</span></span> <span data-ttu-id="1446d-114">このダミー列によって、最終列が固定幅であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="1446d-114">This dummy column ensures that the final column has a fixed width.</span></span>  
  
 <span data-ttu-id="1446d-115">**[フラット ファイル接続マネージャー エディター]** では **[行区切り記号付きの固定幅]** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="1446d-115">The **Fixed width with row delimiters** option is not available in the **Flat File Connection Manager Editor**.</span></span> <span data-ttu-id="1446d-116">必要に応じて、エディターでこのオプションをエミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="1446d-116">If necessary, you can emulate this option in the editor.</span></span> <span data-ttu-id="1446d-117">このオプションをエミュレートするには、 **[フラット ファイル接続マネージャー エディター]** の **[全般]** ページにある **[形式]** で、 **[幅合わせしない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1446d-117">To emulate this option, on the **General** page of the **Flat File Connection Manager Editor**, for **Format**, select **Ragged right**.</span></span> <span data-ttu-id="1446d-118">次に、エディターの **[詳細設定]** ページで、データの最終列として新しいダミー列を追加します。</span><span class="sxs-lookup"><span data-stu-id="1446d-118">Then on the **Advanced** page of the editor, add a new dummy column as the final column of data.</span></span>  
  
 <span data-ttu-id="1446d-119">**[ファイル内のデータを上書きする]**</span><span class="sxs-lookup"><span data-stu-id="1446d-119">**Overwrite data in the file**</span></span>  
 <span data-ttu-id="1446d-120">既存のファイルを上書きするか、データを追加するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1446d-120">Indicate whether to overwrite an existing file, or to append data to it.</span></span>  
  
 <span data-ttu-id="1446d-121">**ヘッダー**</span><span class="sxs-lookup"><span data-stu-id="1446d-121">**Header**</span></span>  
 <span data-ttu-id="1446d-122">データが書き込まれる前にファイルに挿入するテキストのブロックを入力します。</span><span class="sxs-lookup"><span data-stu-id="1446d-122">Type a block of text to insert into the file before any data is written.</span></span> <span data-ttu-id="1446d-123">このオプションをオンにすると、列見出しなどの追加情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1446d-123">Use this option to include additional information, such as column headings.</span></span>  
  
 <span data-ttu-id="1446d-124">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="1446d-124">**Preview**</span></span>  
 <span data-ttu-id="1446d-125">**[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="1446d-125">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="1446d-126">プレビューでは、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="1446d-126">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1446d-127">参照</span><span class="sxs-lookup"><span data-stu-id="1446d-127">See Also</span></span>  
 <span data-ttu-id="1446d-128">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1446d-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1446d-129">[[フラット ファイル変換先エディター] &#40;[マッピング] ページ&#41;](../../2014/integration-services/flat-file-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="1446d-129">[Flat File Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/flat-file-destination-editor-mappings-page.md)</span></span>  
  
  
