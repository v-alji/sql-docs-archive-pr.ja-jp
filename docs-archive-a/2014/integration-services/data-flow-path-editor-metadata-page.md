---
title: '[データフローパスエディター] ([メタデータ] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.metadata.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: b30bb9d7-ebc0-4b1a-8d0f-ee006b32e841
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c2c314707d8baa2fb0f853438f6486acf2a10a37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713382"
---
# <a name="data-flow-path-editor-metadata-page"></a><span data-ttu-id="fdfec-102">[データ フロー パス エディター] ([メタデータ] ページ)</span><span class="sxs-lookup"><span data-stu-id="fdfec-102">Data Flow Path Editor (Metadata Page)</span></span>
  <span data-ttu-id="fdfec-103">**[データ フロー パス エディター]** ダイアログ ボックスの **[メタデータ]** ページを使用すると、パス列のメタデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-103">Use the **Metadata** page of the **Data Flow Path Editor** dialog box to view the metadata of the path columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fdfec-104">Options</span><span class="sxs-lookup"><span data-stu-id="fdfec-104">Options</span></span>  
 <span data-ttu-id="fdfec-105">**[パスのメタデータ]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-105">**Path metadata**</span></span>  
 <span data-ttu-id="fdfec-106">列のメタデータが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-106">Lists column metadata.</span></span> <span data-ttu-id="fdfec-107">列のデータを並べ替えるには、列ヘッダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fdfec-107">Click the column headings to sort column data.</span></span>  
  
 <span data-ttu-id="fdfec-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="fdfec-108">**Name**</span></span>  
 <span data-ttu-id="fdfec-109">列名が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-109">Lists the column name.</span></span>  
  
 <span data-ttu-id="fdfec-110">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-110">**Data Type**</span></span>  
 <span data-ttu-id="fdfec-111">列のデータ型が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-111">Lists the data type of the column.</span></span>  
  
 <span data-ttu-id="fdfec-112">**[精度]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-112">**Precision**</span></span>  
 <span data-ttu-id="fdfec-113">数値の桁数が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-113">Lists the number of digits in a numeric value.</span></span>  
  
 <span data-ttu-id="fdfec-114">**スケール**</span><span class="sxs-lookup"><span data-stu-id="fdfec-114">**Scale**</span></span>  
 <span data-ttu-id="fdfec-115">数値の中で小数点より右側の桁数が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-115">List the number of digits to the right of the decimal point in a numeric value.</span></span>  
  
 <span data-ttu-id="fdfec-116">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-116">**Length**</span></span>  
 <span data-ttu-id="fdfec-117">列の現在の長さが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-117">Lists the current length of the column.</span></span>  
  
 <span data-ttu-id="fdfec-118">**コードページ**</span><span class="sxs-lookup"><span data-stu-id="fdfec-118">**Code Page**</span></span>  
 <span data-ttu-id="fdfec-119">列のコード ページが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-119">Lists the code page of the column.</span></span> <span data-ttu-id="fdfec-120">値 **0** は、その列でコード ページが使用されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="fdfec-120">The value **0** indicates that the column does not use a code page.</span></span> <span data-ttu-id="fdfec-121">これは、データが Unicode であるか、数値、日付、または時刻のデータ型である場合です。</span><span class="sxs-lookup"><span data-stu-id="fdfec-121">This occurs when data is in Unicode, or has a numeric, date, or time data type.</span></span>  
  
 <span data-ttu-id="fdfec-122">**[並べ替えキーの位置]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-122">**Sort Key Position**</span></span>  
 <span data-ttu-id="fdfec-123">列の並べ替えキーの位置が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-123">Lists the sort key position of the column.</span></span> <span data-ttu-id="fdfec-124">値 **0** は、その列が並べ替えられないことを示します。</span><span class="sxs-lookup"><span data-stu-id="fdfec-124">The value **0** indicates the column is not sorted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fdfec-125">マイナス記号 (-) のプレフィックスは、列が降順で並べ替えられていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fdfec-125">A minus (-) prefix indicates the column is sorted in descending order.</span></span>  
  
 <span data-ttu-id="fdfec-126">**[比較フラグ]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-126">**Comparison Flags**</span></span>  
 <span data-ttu-id="fdfec-127">列に適用されている比較フラグが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-127">Lists the comparison flags that apply to the column.</span></span>  
  
 <span data-ttu-id="fdfec-128">**[基になるコンポーネント]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-128">**Source Component**</span></span>  
 <span data-ttu-id="fdfec-129">列の基になるデータ フロー コンポーネントが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-129">Lists the data flow component that is the source of the column.</span></span>  
  
 <span data-ttu-id="fdfec-130">**[クリップボードにコピー]**</span><span class="sxs-lookup"><span data-stu-id="fdfec-130">**Copy to Clipboard**</span></span>  
 <span data-ttu-id="fdfec-131">列のメタデータをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="fdfec-131">Copy the column metadata to the clipboard.</span></span> <span data-ttu-id="fdfec-132">既定では、すべてのメタデータ行が現在表示されている順序でコピーされます。</span><span class="sxs-lookup"><span data-stu-id="fdfec-132">By default, all metadata rows are copied as sorted in the order currently displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdfec-133">参照</span><span class="sxs-lookup"><span data-stu-id="fdfec-133">See Also</span></span>  
 <span data-ttu-id="fdfec-134">[データフローパスエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="fdfec-134">[Data Flow Path Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="fdfec-135">[データフローパスエディターの [データビューアー] ページ &#40;&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span><span class="sxs-lookup"><span data-stu-id="fdfec-135">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span></span>  
 <span data-ttu-id="fdfec-136">[データ フロー](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="fdfec-136">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="fdfec-137">パッケージで注釈を使用する</span><span class="sxs-lookup"><span data-stu-id="fdfec-137">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
