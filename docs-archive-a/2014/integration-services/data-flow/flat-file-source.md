---
title: フラット ファイル ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Flat File
- text file reading [Integration Services]
- flat files
- Flat File source
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b1ca0f38c457256b3f2ed2ddb81bfbd0dc06b6c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742417"
---
# <a name="flat-file-source"></a><span data-ttu-id="6023f-102">フラット ファイル ソース</span><span class="sxs-lookup"><span data-stu-id="6023f-102">Flat File Source</span></span>
  <span data-ttu-id="6023f-103">フラット ファイル ソースは、テキスト ファイルからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="6023f-103">The Flat File source reads data from a text file.</span></span> <span data-ttu-id="6023f-104">テキスト ファイルには、Delimited 形式、FixedWidth 形式、または Mixed 形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6023f-104">The text file can be in delimited, fixed width, or mixed format.</span></span>  
  
-   <span data-ttu-id="6023f-105">Delimited 形式では、列区切り記号と行区切り記号を使用して、列と行が定義されます。</span><span class="sxs-lookup"><span data-stu-id="6023f-105">Delimited format uses column and row delimiters to define columns and rows.</span></span>  
  
-   <span data-ttu-id="6023f-106">FixedWidth 形式では、幅を使用して列と行を定義します。</span><span class="sxs-lookup"><span data-stu-id="6023f-106">Fixed width format uses width to define columns and rows.</span></span> <span data-ttu-id="6023f-107">またこの形式には、フィールドを幅いっぱいまで埋めるための文字も含まれています。</span><span class="sxs-lookup"><span data-stu-id="6023f-107">This format also includes a character for padding fields to their maximum width.</span></span>  
  
-   <span data-ttu-id="6023f-108">RaggedRight 形式では、幅を使用して最終列以外のすべての列を定義します。最終列は、行区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="6023f-108">Ragged right format uses width to define all columns, except for the last column, which is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="6023f-109">フラット ファイル ソースは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="6023f-109">You can configure the Flat File source in the following ways:</span></span>  
  
-   <span data-ttu-id="6023f-110">変換出力に列を追加します。列には、フラット ファイル ソースによるデータの抽出元となるテキスト ファイルの名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6023f-110">Add a column to the transformation output that contains the name of the text file from which the Flat File source extracts data.</span></span>  
  
-   <span data-ttu-id="6023f-111">フラット ファイル ソースで、列にある長さ 0 の文字列を NULL 値として解釈するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6023f-111">Specify whether the Flat File source interprets zero-length strings in columns as null values.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6023f-112">長さ 0 の文字列を NULL として解釈するには、フラット ファイル ソースで使用するフラット ファイル接続マネージャーを、Delimited 形式を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6023f-112">The Flat File connection manager that the Flat File source uses must be configured to use a delimited format to interpret zero-length strings as nulls.</span></span> <span data-ttu-id="6023f-113">フラット ファイル接続マネージャーで FixedWidth 形式または RaggedRight 形式が使用される場合、空白文字で構成されるデータを NULL 値として解釈できません。</span><span class="sxs-lookup"><span data-stu-id="6023f-113">If the connection manager uses the fixed width or ragged right formats, data that consists of spaces cannot be interpreted as null values.</span></span>  
  
 <span data-ttu-id="6023f-114">フラット ファイル ソースの出力にある出力列には、FastParse プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6023f-114">The output columns in the output of the Flat File source include the FastParse property.</span></span> <span data-ttu-id="6023f-115">FastParse は、列が、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に用意されているロケール非依存型の高速な解析ルーチンを使用するか、ロケール依存型の標準的な解析ルーチンを使用するかを示します。</span><span class="sxs-lookup"><span data-stu-id="6023f-115">FastParse indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="6023f-116">詳細については、「 [Fast Parse](../fast-parse.md) 」および「 [Standard Parse](../standard-parse.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6023f-116">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span>  
  
 <span data-ttu-id="6023f-117">出力列には、UseBinaryFormat プロパティも含まれます。</span><span class="sxs-lookup"><span data-stu-id="6023f-117">Output columns also include the UseBinaryFormat property.</span></span> <span data-ttu-id="6023f-118">このプロパティを使用して、パック 10 進形式を使用するデータなど、バイナリ データのサポートをファイルに実装します。</span><span class="sxs-lookup"><span data-stu-id="6023f-118">You use this property to implement support for binary data, such as data with the packed decimal format, in files.</span></span> <span data-ttu-id="6023f-119">既定では、UseBinaryFormat はに設定されて `false` います。</span><span class="sxs-lookup"><span data-stu-id="6023f-119">By default UseBinaryFormat is set to `false`.</span></span> <span data-ttu-id="6023f-120">バイナリ形式を使用する場合は、UseBinaryFormat をに設定 `true` し、出力列のデータ型をに設定し `DT_BYTES` ます。</span><span class="sxs-lookup"><span data-stu-id="6023f-120">If you want to use a binary format, set UseBinaryFormat to `true` and the data type on the output column to `DT_BYTES`.</span></span> <span data-ttu-id="6023f-121">この設定を行った場合、フラット ファイル ソースはデータ変換をスキップし、データを出力列にそのまま渡します。</span><span class="sxs-lookup"><span data-stu-id="6023f-121">When you do this, the Flat File source skips the data conversion and passes the data to the output column as is.</span></span> <span data-ttu-id="6023f-122">この場合は、派生列変換またはデータ変換などの変換を使用して `DT_BYTES` データを別のデータ型にキャストするか、スクリプト変換でカスタム スクリプトを記述してデータを解釈できます。</span><span class="sxs-lookup"><span data-stu-id="6023f-122">You can then use a transformation such as the Derived Column or Data Conversion to cast the `DT_BYTES` data to a different data type, or you can write custom script in a Script transformation to interpret the data.</span></span> <span data-ttu-id="6023f-123">また、カスタム データ フロー コンポーネントを記述してデータを解釈することもできます。</span><span class="sxs-lookup"><span data-stu-id="6023f-123">You can also write a custom data flow component to interpret the data.</span></span> <span data-ttu-id="6023f-124">キャストできるデータ型の詳細については `DT_BYTES` 、「 [CAST &#40;SSIS 式&#41;](../expressions/cast-ssis-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6023f-124">For more information about which data types you can cast `DT_BYTES` to, see [Cast &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="6023f-125">フラット ファイル ソースは、フラット ファイル接続マネージャーを使用してテキスト ファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6023f-125">This source uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="6023f-126">フラット ファイル接続マネージャーでプロパティを設定することにより、ファイルおよびファイルの各列に関する情報を提供して、フラット ファイル ソースで、テキスト ファイルのデータをどのように処理するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6023f-126">By setting properties on the Flat File connection manager, you can provide information about the file and each column in it, and specify how the Flat File source should handle the data in the text file.</span></span> <span data-ttu-id="6023f-127">たとえば、ファイルの列と行を区切る文字や、各列のデータ型や長さを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6023f-127">For example, you can specify the characters that delimit columns and rows in the file, and the data type and the length of each column.</span></span> <span data-ttu-id="6023f-128">詳しくは、「 [フラット ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6023f-128">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="6023f-129">この変換は、1 つの出力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="6023f-129">This source has one output and one error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-source"></a><span data-ttu-id="6023f-130">フラット ファイル ソースの構成</span><span class="sxs-lookup"><span data-stu-id="6023f-130">Configuration of the Flat File Source</span></span>  
 <span data-ttu-id="6023f-131">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="6023f-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="6023f-132">**[フラット ファイル ソース エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6023f-132">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="6023f-133">[フラット ファイル ソース エディター &#40;[接続マネージャー] ページ&#41;](../flat-file-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="6023f-133">[Flat File Source Editor &#40;Connection Manager Page&#41;](../flat-file-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="6023f-134">[フラット ファイル ソース エディター ([列] ページ)](../flat-file-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="6023f-134">[Flat File Source Editor &#40;Columns Page&#41;](../flat-file-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="6023f-135">[フラット ファイル ソース エディター ([エラー出力] ページ)](../flat-file-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="6023f-135">[Flat File Source Editor &#40;Error Output Page&#41;](../flat-file-source-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="6023f-136">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="6023f-136">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="6023f-137">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6023f-137">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="6023f-138">Common Properties</span><span class="sxs-lookup"><span data-stu-id="6023f-138">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="6023f-139">フラット ファイルのカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="6023f-139">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="6023f-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6023f-140">Related Tasks</span></span>  
 <span data-ttu-id="6023f-141">データ フロー コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6023f-141">For details about how to set properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6023f-142">参照</span><span class="sxs-lookup"><span data-stu-id="6023f-142">See Also</span></span>  
 <span data-ttu-id="6023f-143">[フラット ファイル変換先](flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="6023f-143">[Flat File Destination](flat-file-destination.md) </span></span>  
 [<span data-ttu-id="6023f-144">データ フロー</span><span class="sxs-lookup"><span data-stu-id="6023f-144">Data Flow</span></span>](data-flow.md)  
  
  
