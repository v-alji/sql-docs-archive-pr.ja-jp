---
title: 用語参照変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookuptrans.f1
helpviewer_keywords:
- extracting data [Integration Services]
- match extracted terms [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- lookups [Integration Services]
- counting extracted items
- Term Lookup transformation
ms.assetid: 3c0fa2f8-cb6a-4371-b184-7447be001de1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a679f9e191b2b1ec54d982a715085fe5b6bddfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738533"
---
# <a name="term-lookup-transformation"></a><span data-ttu-id="68405-102">用語参照変換</span><span class="sxs-lookup"><span data-stu-id="68405-102">Term Lookup Transformation</span></span>
  <span data-ttu-id="68405-103">用語参照変換は、変換入力列内のテキストから抽出された用語を、参照テーブルの用語と照合します。</span><span class="sxs-lookup"><span data-stu-id="68405-103">The Term Lookup transformation matches terms extracted from text in a transformation input column with terms in a reference table.</span></span> <span data-ttu-id="68405-104">次に、入力データセットで参照テーブル内の用語が検出された回数をカウントし、その数を参照テーブルの用語と共に変換出力の列に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="68405-104">It then counts the number of times a term in the lookup table occurs in the input data set, and writes the count together with the term from the reference table to columns in the transformation output.</span></span> <span data-ttu-id="68405-105">この変換は、単語の使用頻度を示す統計付きのユーザー定義の単語一覧を、入力テキストから作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="68405-105">This transformation is useful for creating a custom word list based on the input text, complete with word frequency statistics.</span></span>  
  
 <span data-ttu-id="68405-106">用語参照変換は、用語抽出変換と同じ次の方法を使用して、参照を実行する前に入力列のテキストから単語を抽出します。</span><span class="sxs-lookup"><span data-stu-id="68405-106">Before the Term Lookup transformation performs a lookup, it extracts words from the text in an input column using the same method as the Term Extraction transformation:</span></span>  
  
-   <span data-ttu-id="68405-107">テキストは文に分けられます。</span><span class="sxs-lookup"><span data-stu-id="68405-107">Text is broken into sentences.</span></span>  
  
-   <span data-ttu-id="68405-108">文は単語に分けられます。</span><span class="sxs-lookup"><span data-stu-id="68405-108">Sentences are broken into words.</span></span>  
  
-   <span data-ttu-id="68405-109">単語は正規化されます。</span><span class="sxs-lookup"><span data-stu-id="68405-109">Words are normalized.</span></span>  
  
 <span data-ttu-id="68405-110">用語の照合方法を詳細にカスタマイズするには、大文字と小文字を区別して照合するように用語参照変換を構成できます。</span><span class="sxs-lookup"><span data-stu-id="68405-110">To further customize which terms to match, the Term Lookup transformation can be configured to perform a case-sensitive match.</span></span>  
  
## <a name="matches"></a><span data-ttu-id="68405-111">次と一致する</span><span class="sxs-lookup"><span data-stu-id="68405-111">Matches</span></span>  
 <span data-ttu-id="68405-112">用語参照変換は参照を実行し、次の規則を使用して値を返します。</span><span class="sxs-lookup"><span data-stu-id="68405-112">The Term Lookup performs a lookup and returns a value using the following rules:</span></span>  
  
-   <span data-ttu-id="68405-113">大文字と小文字を区別して照合するように変換が構成されている場合、大文字と小文字を比較して一致しない場合は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="68405-113">If the transformation is configured to perform case-sensitive matches, matches that fail a case-sensitive comparison are discarded.</span></span> <span data-ttu-id="68405-114">たとえば、 *student* と *STUDENT* は別の単語として扱われます。</span><span class="sxs-lookup"><span data-stu-id="68405-114">For example, *student* and *STUDENT* are treated as separate words.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="68405-115">文の先頭で 1 文字目が大文字になっている単語は小文字の単語と見なされます。</span><span class="sxs-lookup"><span data-stu-id="68405-115">A non-capitalized word can be matched with a word that is capitalized at the beginning of a sentence.</span></span> <span data-ttu-id="68405-116">たとえば、 *Student* が文の最初の単語である場合、 *student* と *Student* の照合は成功します。</span><span class="sxs-lookup"><span data-stu-id="68405-116">For example, the match between *student* and *Student* succeeds when *Student* is the first word in a sentence.</span></span>  
  
-   <span data-ttu-id="68405-117">名詞または名詞句の複数形が参照テーブルに存在する場合、参照により一致するのは、名詞または名詞句の複数形のみです。</span><span class="sxs-lookup"><span data-stu-id="68405-117">If a plural form of the noun or noun phrase exists in the reference table, the lookup matches only the plural form of the noun or noun phrase.</span></span> <span data-ttu-id="68405-118">たとえば、 *students* のすべてのインスタンスは、 *student*のインスタンスとは別にカウントされます。</span><span class="sxs-lookup"><span data-stu-id="68405-118">For example, all instances of *students* would be counted separately from the instances of *student*.</span></span>  
  
-   <span data-ttu-id="68405-119">単語の単数形のみが参照テーブルにある場合、単語または語句の単数形および複数形の両方が単数形と一致します。</span><span class="sxs-lookup"><span data-stu-id="68405-119">If only the singular form of the word is found in the reference table, both the singular and the plural forms of the word or phrase are matched to the singular form.</span></span> <span data-ttu-id="68405-120">たとえば、参照テーブルに *student*が含まれ、変換が *student* と *students*を検出した場合、両方の単語が、参照用語の *student*に一致するものとしてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="68405-120">For example, if the lookup table contains *student*, and the transformation finds the words *student* and *students*, both words would be counted as a match for the lookup term *student*.</span></span>  
  
-   <span data-ttu-id="68405-121">入力列のテキストが、見出し語付きの名詞句の場合、名詞句の最後の単語のみが正規化されます。</span><span class="sxs-lookup"><span data-stu-id="68405-121">If the text in the input column is a lemmatized noun phrase, only the last word in the noun phrase is affected by normalization.</span></span> <span data-ttu-id="68405-122">たとえば、 *doctors appointments* の見出し語付き名詞句は、 *doctors appointment*になります。</span><span class="sxs-lookup"><span data-stu-id="68405-122">For example, the lemmatized version of *doctors appointments* is *doctors appointment*.</span></span>  
  
 <span data-ttu-id="68405-123">参照セット内で重複している用語が参照項目に含まれる場合、つまりサブ用語が複数の参照レコード内に存在する場合、用語参照変換は参照結果を 1 つだけ返します。</span><span class="sxs-lookup"><span data-stu-id="68405-123">When a lookup item contains terms that overlap in the reference set-that is, a sub-term is found in more than one reference record-the Term Lookup transformation returns only one lookup result.</span></span> <span data-ttu-id="68405-124">次の例は、重複するサブ用語が参照項目に含まれる場合の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="68405-124">The following example shows the result when a lookup item contains an overlapping sub-term.</span></span> <span data-ttu-id="68405-125">この場合、重複するサブ用語は *Windows*で、2 つの参照用語内に存在します。</span><span class="sxs-lookup"><span data-stu-id="68405-125">The overlapping sub-term in this case is *Windows*, which is found within two reference terms.</span></span> <span data-ttu-id="68405-126">ただし、変換は結果を 2 つ返さず、参照用語の 1 つ *Windows*のみを返します。</span><span class="sxs-lookup"><span data-stu-id="68405-126">However, the transformation does not return two results, but returns only a single reference term, *Windows*.</span></span> <span data-ttu-id="68405-127">2 番目の参照用語である *Windows 7 Professional*は返されません。</span><span class="sxs-lookup"><span data-stu-id="68405-127">The second reference term, *Windows 7 Professional*, is not returned.</span></span>  
  
|<span data-ttu-id="68405-128">アイテム</span><span class="sxs-lookup"><span data-stu-id="68405-128">Item</span></span>|<span data-ttu-id="68405-129">値</span><span class="sxs-lookup"><span data-stu-id="68405-129">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="68405-130">入力用語</span><span class="sxs-lookup"><span data-stu-id="68405-130">Input term</span></span>|<span data-ttu-id="68405-131">Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="68405-131">Windows 7 Professional</span></span>|  
|<span data-ttu-id="68405-132">参照用語</span><span class="sxs-lookup"><span data-stu-id="68405-132">Reference terms</span></span>|<span data-ttu-id="68405-133">Windows, Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="68405-133">Windows, Windows 7 Professional</span></span>|  
|<span data-ttu-id="68405-134">Output</span><span class="sxs-lookup"><span data-stu-id="68405-134">Output</span></span>|<span data-ttu-id="68405-135">Windows</span><span class="sxs-lookup"><span data-stu-id="68405-135">Windows</span></span>|  
  
 <span data-ttu-id="68405-136">用語参照変換は、特殊文字が含まれる名詞および名詞句を照合でき、参照テーブルのデータにもこれらの文字を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="68405-136">The Term Lookup transformation can match nouns and noun phrases that contain special characters, and the data in the reference table may include these characters.</span></span> <span data-ttu-id="68405-137">特殊文字とは、%, @, &, $, #, \*、:、;、.、 **、** 、!、?、\<, >、+、=、^、~、|、\\、/、(、)、[、]、{、}、"、' です。</span><span class="sxs-lookup"><span data-stu-id="68405-137">The special characters are as follows: %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="68405-138">データ型</span><span class="sxs-lookup"><span data-stu-id="68405-138">Data Types</span></span>  
 <span data-ttu-id="68405-139">用語参照変換で使用できる列は、DT_WSTR または DT_NTEXT データ型のどちらかの列のみです。</span><span class="sxs-lookup"><span data-stu-id="68405-139">The Term Lookup transformation can only use a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="68405-140">列にテキストが含まれていても、これらのデータ型ではない場合、データ変換の変換では、DT_WSTR または DT_NTEXT データ型の列をデータ フローに追加し、列の値を新しい列にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="68405-140">If a column contains text, but does not have one of these data types, the Data Conversion transformation can add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="68405-141">その後、データ変換の変換からの出力を、用語参照変換への入力として使用できます。</span><span class="sxs-lookup"><span data-stu-id="68405-141">The output from the Data Conversion transformation can then be used as the input to the Term Lookup transformation.</span></span> <span data-ttu-id="68405-142">詳細については、「 [Data Conversion Transformation](data-conversion-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68405-142">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="configuration-the-term-lookup-transformation"></a><span data-ttu-id="68405-143">用語参照変換の構成</span><span class="sxs-lookup"><span data-stu-id="68405-143">Configuration the Term Lookup Transformation</span></span>  
 <span data-ttu-id="68405-144">用語参照変換の入力列には、InputColumnType プロパティが含まれ、このプロパティにより、列の使用方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="68405-144">The Term Lookup transformation input columns includes the InputColumnType property, which indicates the use of the column.</span></span> <span data-ttu-id="68405-145">InputColumnType は次の値を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="68405-145">InputColumnType can contain the following values:</span></span>  
  
-   <span data-ttu-id="68405-146">値 0 は、列が出力のみに渡され、参照で使用されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="68405-146">The value 0 indicates the column is passed through to the output only and is not used in the lookup.</span></span>  
  
-   <span data-ttu-id="68405-147">値 1 は、列が参照のみで使用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="68405-147">The value 1 indicates the column is used in the lookup only.</span></span>  
  
-   <span data-ttu-id="68405-148">値 2 は、列が出力に渡され、参照内でも使用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="68405-148">The value 2 indicates the column is passed through to the output, and is also used in the lookup.</span></span>  
  
 <span data-ttu-id="68405-149">変換出力列の InputColumnType プロパティが 0 または 2 に設定されている場合、1 つの列に CustomLineageID プロパティが含まれます。このプロパティには、上流のデータ フロー コンポーネントによって列に割り当てられた、系列 ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="68405-149">Transformation output columns whose InputColumnType property is set to 0 or 2 include the CustomLineageID property for a column, which contains the lineage identifier assigned to the column by an upstream data flow component.</span></span>  
  
 <span data-ttu-id="68405-150">用語参照変換は、`Term` と `Frequency` という既定の名前野付いた 2 つの列を変換出力に追加します。</span><span class="sxs-lookup"><span data-stu-id="68405-150">The Term Lookup transformation adds two columns to the transformation output, named by default `Term` and `Frequency`.</span></span> <span data-ttu-id="68405-151">`Term` 列には参照テーブルからの用語が含まれ、`Frequency` 列には、入力データセットで参照テーブル内の用語が検出された回数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="68405-151">`Term` contains a term from the lookup table and `Frequency` contains the number of times the term in the reference table occurs in the input data set.</span></span> <span data-ttu-id="68405-152">これらの列には、CustomLineageID プロパティは含まれません。</span><span class="sxs-lookup"><span data-stu-id="68405-152">These columns do not include the CustomLineageID property.</span></span>  
  
 <span data-ttu-id="68405-153">参照テーブルは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または Access データベースのテーブルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="68405-153">The lookup table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="68405-154">用語抽出変換の出力がテーブルに保存されている場合、このテーブルを参照テーブルとして使用できます。ただし、他のテーブルを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="68405-154">If the output of the Term Extraction transformation is saved to a table, this table can be used as the reference table, but other tables can also be used.</span></span> <span data-ttu-id="68405-155">フラット ファイルのテキスト、Excel ブック、または他の変換元を用語参照変換で使用するには、これらを、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースまたは Access データベースにインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68405-155">Text in flat files, Excel workbooks or other sources must be imported to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database or an Access database before you can use the Term Lookup transformation.</span></span>  
  
 <span data-ttu-id="68405-156">用語参照変換は、個別の OLE DB 接続を使用して、参照テーブルに接続します。</span><span class="sxs-lookup"><span data-stu-id="68405-156">The Term Lookup transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="68405-157">詳細については、「 [OLE DB 接続マネージャー](../../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68405-157">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="68405-158">用語参照変換は、完全な事前キャッシュ モードで動作します。</span><span class="sxs-lookup"><span data-stu-id="68405-158">The Term Lookup transformation works in a fully precached mode.</span></span> <span data-ttu-id="68405-159">用語参照変換は、実行時に参照テーブルの用語を読み取って独自のメモリに格納してから、変換入力行を処理します。</span><span class="sxs-lookup"><span data-stu-id="68405-159">At run time, the Term Lookup transformation reads the terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
 <span data-ttu-id="68405-160">入力列の行の用語は繰り返して使用する場合があるため、用語参照変換の出力には、通常、変換入力よりも多くの行があります。</span><span class="sxs-lookup"><span data-stu-id="68405-160">Because the terms in an input column row may repeat, the output of the Term Lookup transformation typically has more rows than the transformation input.</span></span>  
  
 <span data-ttu-id="68405-161">この変換は、1 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="68405-161">The transformation has one input and one output.</span></span> <span data-ttu-id="68405-162">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="68405-162">It does not support error outputs.</span></span>  
  
 <span data-ttu-id="68405-163">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="68405-163">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="68405-164">**[用語参照変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68405-164">For more information about the properties that you can set in the **Term Lookup Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="68405-165">[用語参照変換エディター ([参照テーブル] タブ)](../../term-lookup-transformation-editor-reference-table-tab.md)</span><span class="sxs-lookup"><span data-stu-id="68405-165">[Term Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../term-lookup-transformation-editor-reference-table-tab.md)</span></span>  
  
-   <span data-ttu-id="68405-166">[[用語参照変換エディター] &#40;[用語参照] タブ&#41;](../../term-lookup-transformation-editor-term-lookup-tab.md)</span><span class="sxs-lookup"><span data-stu-id="68405-166">[Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;](../../term-lookup-transformation-editor-term-lookup-tab.md)</span></span>  
  
-   <span data-ttu-id="68405-167">[用語参照変換エディター ([詳細設定] タブ)](../../term-lookup-transformation-editor-advanced-tab.md)</span><span class="sxs-lookup"><span data-stu-id="68405-167">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../term-lookup-transformation-editor-advanced-tab.md)</span></span>  
  
 <span data-ttu-id="68405-168">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68405-168">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="68405-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="68405-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="68405-170">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="68405-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="68405-171">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68405-171">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
