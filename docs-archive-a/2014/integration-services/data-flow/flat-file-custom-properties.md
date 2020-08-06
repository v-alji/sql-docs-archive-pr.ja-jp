---
title: フラット ファイルのカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b906e9268bf3a74ffcf5661953397ad7a24b77a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742421"
---
# <a name="flat-file-custom-properties"></a><span data-ttu-id="bfe93-102">フラット ファイルのカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="bfe93-102">Flat File Custom Properties</span></span>
  <span data-ttu-id="bfe93-103">**変換元のカスタム プロパティ**</span><span class="sxs-lookup"><span data-stu-id="bfe93-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="bfe93-104">フラット ファイル ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="bfe93-104">The Flat File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="bfe93-105">次の表は、フラット ファイル ソースのカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="bfe93-105">The following table describes the custom properties of the Flat File source.</span></span> <span data-ttu-id="bfe93-106">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="bfe93-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="bfe93-107">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="bfe93-107">Property name</span></span>|<span data-ttu-id="bfe93-108">データ型</span><span class="sxs-lookup"><span data-stu-id="bfe93-108">Data Type</span></span>|<span data-ttu-id="bfe93-109">説明</span><span class="sxs-lookup"><span data-stu-id="bfe93-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="bfe93-110">FileNameColumnName</span><span class="sxs-lookup"><span data-stu-id="bfe93-110">FileNameColumnName</span></span>|<span data-ttu-id="bfe93-111">String</span><span class="sxs-lookup"><span data-stu-id="bfe93-111">String</span></span>|<span data-ttu-id="bfe93-112">ファイル名を格納する出力列の名前。</span><span class="sxs-lookup"><span data-stu-id="bfe93-112">The name of an output column that contains the file name.</span></span> <span data-ttu-id="bfe93-113">名前が指定されていない場合、ファイル名を格納する出力列は生成されません。</span><span class="sxs-lookup"><span data-stu-id="bfe93-113">If no name is specified, no output column containing the file name will be generated.</span></span><br /><br /> <span data-ttu-id="bfe93-114">注: このプロパティは、 **フラット ファイル ソース エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="bfe93-114">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="bfe93-115">RetainNulls</span><span class="sxs-lookup"><span data-stu-id="bfe93-115">RetainNulls</span></span>|<span data-ttu-id="bfe93-116">Boolean</span><span class="sxs-lookup"><span data-stu-id="bfe93-116">Boolean</span></span>|<span data-ttu-id="bfe93-117">データ変換のパイプライン エンジンによってデータが処理される際に、ソース ファイルの NULL 値を NULL 値として保持するかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="bfe93-117">A value that specifies whether to retain Null values from the source file as Null values when the data is processed by the Data Transformation Pipeline engine.</span></span> <span data-ttu-id="bfe93-118">このプロパティの既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="bfe93-118">The default value of this property is `False`.</span></span>|  
  
 <span data-ttu-id="bfe93-119">フラット ファイル ソースの出力には、カスタム プロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="bfe93-119">The output of the Flat File source has no custom properties.</span></span>  
  
 <span data-ttu-id="bfe93-120">次の表は、フラット ファイル ソースの出力列のカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="bfe93-120">The following table describes the custom properties of the output columns of the Flat File source.</span></span> <span data-ttu-id="bfe93-121">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="bfe93-121">All properties are read/write.</span></span>  
  
|<span data-ttu-id="bfe93-122">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="bfe93-122">Property name</span></span>|<span data-ttu-id="bfe93-123">データ型</span><span class="sxs-lookup"><span data-stu-id="bfe93-123">Data Type</span></span>|<span data-ttu-id="bfe93-124">説明</span><span class="sxs-lookup"><span data-stu-id="bfe93-124">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="bfe93-125">FastParse</span><span class="sxs-lookup"><span data-stu-id="bfe93-125">FastParse</span></span>|<span data-ttu-id="bfe93-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="bfe93-126">Boolean</span></span>|<span data-ttu-id="bfe93-127">列の解析に、DTS が提供するロケール非依存型の高速な解析ルーチンを使用するか、またはロケール依存型の標準的な解析ルーチンを使用するかを示す値。</span><span class="sxs-lookup"><span data-stu-id="bfe93-127">A value that indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that DTS provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="bfe93-128">詳細については、「 [Fast Parse](../fast-parse.md) 」および「 [Standard Parse](../standard-parse.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfe93-128">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span> <span data-ttu-id="bfe93-129">このプロパティの既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="bfe93-129">The default value of this property is `False`.</span></span><br /><br /> <span data-ttu-id="bfe93-130">注: このプロパティは、 **フラット ファイル ソース エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="bfe93-130">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
  
 <span data-ttu-id="bfe93-131">詳細については、「 [フラット ファイル ソース](flat-file-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfe93-131">For more information, see [Flat File Source](flat-file-source.md).</span></span>  
  
 <span data-ttu-id="bfe93-132">**変換先のカスタム プロパティ**</span><span class="sxs-lookup"><span data-stu-id="bfe93-132">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="bfe93-133">フラット ファイル変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="bfe93-133">The Flat File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="bfe93-134">次の表は、フラット ファイル変換先のカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="bfe93-134">The following table describes the custom properties of the Flat File destination.</span></span> <span data-ttu-id="bfe93-135">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="bfe93-135">All properties are read/write.</span></span>  
  
|<span data-ttu-id="bfe93-136">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="bfe93-136">Property name</span></span>|<span data-ttu-id="bfe93-137">データ型</span><span class="sxs-lookup"><span data-stu-id="bfe93-137">Data Type</span></span>|<span data-ttu-id="bfe93-138">説明</span><span class="sxs-lookup"><span data-stu-id="bfe93-138">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="bfe93-139">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="bfe93-139">Header</span></span>|<span data-ttu-id="bfe93-140">String</span><span class="sxs-lookup"><span data-stu-id="bfe93-140">String</span></span>|<span data-ttu-id="bfe93-141">データが書き込まれる前にファイルに挿入される、テキストのブロック。</span><span class="sxs-lookup"><span data-stu-id="bfe93-141">A block of text that is inserted in the file before any data is written.</span></span><br /><br /> <span data-ttu-id="bfe93-142">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="bfe93-142">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="bfe93-143">Overwrite</span><span class="sxs-lookup"><span data-stu-id="bfe93-143">Overwrite</span></span>|<span data-ttu-id="bfe93-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="bfe93-144">Boolean</span></span>|<span data-ttu-id="bfe93-145">同じ名前の既存の変換先ファイルに対して、上書きまたは追加のどちらを実行するかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="bfe93-145">A value that specifies whether to overwrite or append to an existing destination file that has the same name.</span></span> <span data-ttu-id="bfe93-146">このプロパティの既定値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="bfe93-146">The default value of this property is `True`.</span></span>|  
  
 <span data-ttu-id="bfe93-147">フラット ファイル変換先の入力および入力列には、カスタム プロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="bfe93-147">The input and the input columns of the Flat File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="bfe93-148">詳細については、「 [フラット ファイル変換先](flat-file-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfe93-148">For more information, see [Flat File Destination](flat-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe93-149">参照</span><span class="sxs-lookup"><span data-stu-id="bfe93-149">See Also</span></span>  
 [<span data-ttu-id="bfe93-150">Common Properties</span><span class="sxs-lookup"><span data-stu-id="bfe93-150">Common Properties</span></span>](../common-properties.md)  
  
  
