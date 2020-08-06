---
title: '[列エクスポート変換エディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 404b404e2328228049ae46fb1c3089b0b4089f0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634579"
---
# <a name="export-column-transformation-editor-columns-page"></a><span data-ttu-id="bb6dd-102">[列エクスポート変換エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="bb6dd-102">Export Column Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="bb6dd-103">**[列エクスポート変換エディター]** ダイアログ ボックスの **[列]** ページを使用すると、ファイルに抽出するデータ フロー内の列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-103">Use the **Columns** page of the **Export Column Transformation Editor** dialog box to specify columns in the data flow to extract to files.</span></span> <span data-ttu-id="bb6dd-104">列エクスポート変換でファイルにデータを追加するか、既存のファイルを上書きするかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-104">You can specify whether the Export Column transformation appends data to a file or overwrites an existing file.</span></span>  
  
 <span data-ttu-id="bb6dd-105">列エクスポート変換の詳細については、「 [Export Column Transformation](data-flow/transformations/export-column-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-105">To learn more about the Export Column transformation, see [Export Column Transformation](data-flow/transformations/export-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bb6dd-106">Options</span><span class="sxs-lookup"><span data-stu-id="bb6dd-106">Options</span></span>  
 <span data-ttu-id="bb6dd-107">**[列の抽出]**</span><span class="sxs-lookup"><span data-stu-id="bb6dd-107">**Extract Column**</span></span>  
 <span data-ttu-id="bb6dd-108">テキストまたは画像データを持つ入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-108">Select from the list of input columns that contain text or image data.</span></span> <span data-ttu-id="bb6dd-109">すべての行には、 **[列の抽出]** と **[ファイル パス列]** の定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-109">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="bb6dd-110">**[ファイル パス列]**</span><span class="sxs-lookup"><span data-stu-id="bb6dd-110">**File Path Column**</span></span>  
 <span data-ttu-id="bb6dd-111">ファイル パスとファイル名を持つ入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-111">Select from the list of input columns that contain file paths and file names.</span></span> <span data-ttu-id="bb6dd-112">すべての行には、 **[列の抽出]** と **[ファイル パス列]** の定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-112">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="bb6dd-113">**[追加の許可]**</span><span class="sxs-lookup"><span data-stu-id="bb6dd-113">**Allow Append**</span></span>  
 <span data-ttu-id="bb6dd-114">変換により、既存のファイルにデータを追加するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-114">Specify whether the transformation appends data to existing files.</span></span> <span data-ttu-id="bb6dd-115">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-115">The default is `false`.</span></span>  
  
 <span data-ttu-id="bb6dd-116">**[強制的に切り捨て]**</span><span class="sxs-lookup"><span data-stu-id="bb6dd-116">**Force Truncate**</span></span>  
 <span data-ttu-id="bb6dd-117">変換により、データを書き込む前に既存のファイルの内容を削除するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-117">Specify whether the transformation deletes the contents of existing files before writing data.</span></span> <span data-ttu-id="bb6dd-118">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-118">The default is `false`.</span></span>  
  
 <span data-ttu-id="bb6dd-119">**[バイト順マークの書き込み]**</span><span class="sxs-lookup"><span data-stu-id="bb6dd-119">**Write BOM**</span></span>  
 <span data-ttu-id="bb6dd-120">バイト順マーク (BOM) をファイルに書き込むかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-120">Specify whether to write a byte-order mark (BOM) to the file.</span></span> <span data-ttu-id="bb6dd-121">BOM は、データが `DT_NTEXT` または DT_WSTR のデータ型を持つ場合にのみ書き込まれ、既存のデータ ファイルには追加されません。</span><span class="sxs-lookup"><span data-stu-id="bb6dd-121">A BOM is only written if the data has the `DT_NTEXT` or DT_WSTR data type and is not appended to an existing data file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6dd-122">参照</span><span class="sxs-lookup"><span data-stu-id="bb6dd-122">See Also</span></span>  
 <span data-ttu-id="bb6dd-123">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bb6dd-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bb6dd-124">[[列エクスポート変換エディター] &#40;[エラー出力] ページ&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="bb6dd-124">[Export Column Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)</span></span>  
  
  
