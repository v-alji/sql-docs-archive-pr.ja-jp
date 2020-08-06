---
title: 列エクスポート変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exportcolumntrans.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7ed2bef02d75b72870514e2333d2fa58720fb60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633238"
---
# <a name="export-column-transformation"></a><span data-ttu-id="8f888-102">列エクスポート変換</span><span class="sxs-lookup"><span data-stu-id="8f888-102">Export Column Transformation</span></span>
  <span data-ttu-id="8f888-103">列エクスポート変換は、データ フローのデータを読み取り、そのデータをファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="8f888-103">The Export Column transformation reads data in a data flow and inserts the data into a file.</span></span> <span data-ttu-id="8f888-104">たとえば、データ フローに、各製品の写真などの製品情報が含まれる場合、列エクスポート変換を使用して、その画像をファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="8f888-104">For example, if the data flow contains product information, such as a picture of each product, you could use the Export Column transformation to save the images to files.</span></span>  
  
## <a name="append-and-truncate-options"></a><span data-ttu-id="8f888-105">追加オプションと切り捨てオプション</span><span class="sxs-lookup"><span data-stu-id="8f888-105">Append and Truncate Options</span></span>  
 <span data-ttu-id="8f888-106">次の表では、追加オプションと切り捨てオプションが結果に与える影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="8f888-106">The following table describes how the settings for the append and truncate options affect results.</span></span>  
  
|<span data-ttu-id="8f888-107">Append</span><span class="sxs-lookup"><span data-stu-id="8f888-107">Append</span></span>|<span data-ttu-id="8f888-108">Truncate</span><span class="sxs-lookup"><span data-stu-id="8f888-108">Truncate</span></span>|<span data-ttu-id="8f888-109">ファイルが存在するか</span><span class="sxs-lookup"><span data-stu-id="8f888-109">File exists</span></span>|<span data-ttu-id="8f888-110">[結果]</span><span class="sxs-lookup"><span data-stu-id="8f888-110">Results</span></span>|  
|------------|--------------|-----------------|-------------|  
|<span data-ttu-id="8f888-111">False</span><span class="sxs-lookup"><span data-stu-id="8f888-111">False</span></span>|<span data-ttu-id="8f888-112">False</span><span class="sxs-lookup"><span data-stu-id="8f888-112">False</span></span>|<span data-ttu-id="8f888-113">いいえ</span><span class="sxs-lookup"><span data-stu-id="8f888-113">No</span></span>|<span data-ttu-id="8f888-114">新しいファイルが作成され、そのファイルにデータが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8f888-114">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="8f888-115">True</span><span class="sxs-lookup"><span data-stu-id="8f888-115">True</span></span>|<span data-ttu-id="8f888-116">False</span><span class="sxs-lookup"><span data-stu-id="8f888-116">False</span></span>|<span data-ttu-id="8f888-117">いいえ</span><span class="sxs-lookup"><span data-stu-id="8f888-117">No</span></span>|<span data-ttu-id="8f888-118">新しいファイルが作成され、そのファイルにデータが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8f888-118">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="8f888-119">False</span><span class="sxs-lookup"><span data-stu-id="8f888-119">False</span></span>|<span data-ttu-id="8f888-120">True</span><span class="sxs-lookup"><span data-stu-id="8f888-120">True</span></span>|<span data-ttu-id="8f888-121">いいえ</span><span class="sxs-lookup"><span data-stu-id="8f888-121">No</span></span>|<span data-ttu-id="8f888-122">新しいファイルが作成され、そのファイルにデータが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8f888-122">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="8f888-123">True</span><span class="sxs-lookup"><span data-stu-id="8f888-123">True</span></span>|<span data-ttu-id="8f888-124">True</span><span class="sxs-lookup"><span data-stu-id="8f888-124">True</span></span>|<span data-ttu-id="8f888-125">いいえ</span><span class="sxs-lookup"><span data-stu-id="8f888-125">No</span></span>|<span data-ttu-id="8f888-126">デザイン時の検証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="8f888-126">The transformation fails design time validation.</span></span> <span data-ttu-id="8f888-127">両方のプロパティに `true` を設定するのは無効です。</span><span class="sxs-lookup"><span data-stu-id="8f888-127">It is not valid to set both properties to `true`.</span></span>|  
|<span data-ttu-id="8f888-128">False</span><span class="sxs-lookup"><span data-stu-id="8f888-128">False</span></span>|<span data-ttu-id="8f888-129">False</span><span class="sxs-lookup"><span data-stu-id="8f888-129">False</span></span>|<span data-ttu-id="8f888-130">はい</span><span class="sxs-lookup"><span data-stu-id="8f888-130">Yes</span></span>|<span data-ttu-id="8f888-131">実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8f888-131">A run-time error occurs.</span></span> <span data-ttu-id="8f888-132">ファイルは存在しますが、そのファイルに書き込めません。</span><span class="sxs-lookup"><span data-stu-id="8f888-132">The file exists, but the transformation cannot write to it.</span></span>|  
|<span data-ttu-id="8f888-133">False</span><span class="sxs-lookup"><span data-stu-id="8f888-133">False</span></span>|<span data-ttu-id="8f888-134">True</span><span class="sxs-lookup"><span data-stu-id="8f888-134">True</span></span>|<span data-ttu-id="8f888-135">はい</span><span class="sxs-lookup"><span data-stu-id="8f888-135">Yes</span></span>|<span data-ttu-id="8f888-136">ファイルが削除されて再作成され、データが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8f888-136">The transformation deletes and re-creates the file and writes the data to the file.</span></span>|  
|<span data-ttu-id="8f888-137">True</span><span class="sxs-lookup"><span data-stu-id="8f888-137">True</span></span>|<span data-ttu-id="8f888-138">False</span><span class="sxs-lookup"><span data-stu-id="8f888-138">False</span></span>|<span data-ttu-id="8f888-139">はい</span><span class="sxs-lookup"><span data-stu-id="8f888-139">Yes</span></span>|<span data-ttu-id="8f888-140">ファイルが開かれ、そのファイルの終わりにデータが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8f888-140">The transformation opens the file and writes the data at the end of the file.</span></span>|  
|<span data-ttu-id="8f888-141">True</span><span class="sxs-lookup"><span data-stu-id="8f888-141">True</span></span>|<span data-ttu-id="8f888-142">True</span><span class="sxs-lookup"><span data-stu-id="8f888-142">True</span></span>|<span data-ttu-id="8f888-143">はい</span><span class="sxs-lookup"><span data-stu-id="8f888-143">Yes</span></span>|<span data-ttu-id="8f888-144">デザイン時の検証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="8f888-144">The transformation fails design time validation.</span></span> <span data-ttu-id="8f888-145">両方のプロパティに `true` を設定するのは無効です。</span><span class="sxs-lookup"><span data-stu-id="8f888-145">It is not valid to set both properties to `true`.</span></span>|  
  
## <a name="configuration-of-the-export-column-transformation"></a><span data-ttu-id="8f888-146">列エクスポート変換の構成</span><span class="sxs-lookup"><span data-stu-id="8f888-146">Configuration of the Export Column Transformation</span></span>  
 <span data-ttu-id="8f888-147">列エクスポート変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="8f888-147">You can configure the Export Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="8f888-148">データ列と、データの書き込み先のファイルのパスが含まれる列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8f888-148">Specify the data columns and the columns that contain the path of files to which to write the data.</span></span>  
  
-   <span data-ttu-id="8f888-149">データ挿入の操作の際に既存のファイルを追加するか、または切り捨てるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8f888-149">Specify whether the data-insertion operation appends or truncates existing files.</span></span>  
  
-   <span data-ttu-id="8f888-150">バイト順マーク (BOM) をファイルに書き込むかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8f888-150">Specify whether a byte-order mark (BOM) is written to the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f888-151">BOM は、データが既存のファイルに追加されず、DT_NTEXT データ型の場合にのみ書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8f888-151">A BOM is written only when the data is not appended to an existing file and the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="8f888-152">この変換では、ファイル名が含まれる入力列と、データが含まれる入力列の組を使用します。</span><span class="sxs-lookup"><span data-stu-id="8f888-152">The transformation uses pairs of input columns: One column contains a file name, and the other column contains data.</span></span> <span data-ttu-id="8f888-153">データセットの各行では、異なるファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8f888-153">Each row in the data set can specify a different file.</span></span> <span data-ttu-id="8f888-154">この変換により行が処理されると、データは指定したファイルに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="8f888-154">As the transformation processes a row, the data is inserted into the specified file.</span></span> <span data-ttu-id="8f888-155">実行時に既存のファイルがない場合、変換によりファイルが作成され、そのファイルにデータが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8f888-155">At run time, the transformation creates the files, if they do not already exist, and then the transformation writes the data to the files.</span></span> <span data-ttu-id="8f888-156">書き込まれるデータは、DT_TEXT、DT_NTEXT、または DT_IMAGE データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f888-156">The data to be written must have a DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="8f888-157">詳細については、「 [Integration Services Data Types](../integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f888-157">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="8f888-158">この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="8f888-158">This transformation has one input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="8f888-159">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="8f888-159">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="8f888-160">**[列エクスポート変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「[[列エクスポート変換エディター] ([列] ページ)](../../export-column-transformation-editor-columns-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f888-160">For more information about the properties that you can set in the **Export Column Transformation Editor** dialog box, see [Export Column Transformation Editor &#40;Columns Page&#41;](../../export-column-transformation-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="8f888-161">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="8f888-161">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="8f888-162">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f888-162">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="8f888-163">Common Properties</span><span class="sxs-lookup"><span data-stu-id="8f888-163">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="8f888-164">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="8f888-164">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="8f888-165">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f888-165">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
