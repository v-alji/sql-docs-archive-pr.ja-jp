---
title: XML ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsource.f1
helpviewer_keywords:
- sources [Integration Services], XML
- XML source [Integration Services]
- XML Source Editor
ms.assetid: 68c27ea5-e93d-4e26-bfb2-d967ca0a5282
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13a1bf01729932eaa6b232ac7839d2e3001f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644033"
---
# <a name="xml-source"></a><span data-ttu-id="64f92-102">XML ソース</span><span class="sxs-lookup"><span data-stu-id="64f92-102">XML Source</span></span>
  <span data-ttu-id="64f92-103">XML ソースは XML データ ファイルを読み取り、ソース出力の列にデータを設定します。</span><span class="sxs-lookup"><span data-stu-id="64f92-103">The XML source reads an XML data file and populates the columns in the source output with the data.</span></span>  
  
 <span data-ttu-id="64f92-104">XML ファイルのデータには、多くの場合、階層リレーションシップが含まれます。</span><span class="sxs-lookup"><span data-stu-id="64f92-104">The data in XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="64f92-105">たとえば、XML データ ファイルはカタログおよびカタログ内のアイテムを表す場合があります。</span><span class="sxs-lookup"><span data-stu-id="64f92-105">For example, an XML data file can represent catalogs and items in catalogs.</span></span> <span data-ttu-id="64f92-106">データ フローにデータを入力できるようにするためには、XML データ ファイルの要素のリレーションシップを特定し、ファイル内部の各要素に対して出力を生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64f92-106">Before the data can enter the data flow, the relationship of the elements in XML data file must be determined, and an output must be generated for each element in the file.</span></span>  
  
## <a name="schemas"></a><span data-ttu-id="64f92-107">スキーマ</span><span class="sxs-lookup"><span data-stu-id="64f92-107">Schemas</span></span>  
 <span data-ttu-id="64f92-108">XML ソースは、スキーマを使用して XML データを解釈します。</span><span class="sxs-lookup"><span data-stu-id="64f92-108">The XML source uses a schema to interpret the XML data.</span></span> <span data-ttu-id="64f92-109">XML ソースでは、XML スキーマ定義 (XSD) ファイルまたはインライン スキーマを使用して、XML データを表形式に変換できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-109">The XML source supports use of a XML Schema Definition (XSD) file or inline schemas to translate the XML data into a tabular format.</span></span> <span data-ttu-id="64f92-110">**[XML ソース エディター]** ダイアログ ボックスを使用して XML ソースを構成する場合、ユーザー インターフェイスにより、指定した XML データ ファイルから XSD を生成できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-110">If you configure the XML source by using the **XML Source Editor** dialog box, the user interface can generate an XSD from the specified XML data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64f92-111">DTD はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="64f92-111">DTDs are not supported.</span></span>  
  
 <span data-ttu-id="64f92-112">スキーマでは、単一の名前空間のみがサポートされます。スキーマ コレクションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="64f92-112">The schemas can support a single namespace only; they do not support schema collections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64f92-113">XML ソースは、XML ファイルのデータを XSD に対して検証しません。</span><span class="sxs-lookup"><span data-stu-id="64f92-113">The XML source does not validate the data in the XML file against the XSD.</span></span>  
  
## <a name="xml-source-editor"></a><span data-ttu-id="64f92-114">[XML ソース エディター]</span><span class="sxs-lookup"><span data-stu-id="64f92-114">XML Source Editor</span></span>  
 <span data-ttu-id="64f92-115">XML ファイルのデータには、多くの場合、階層リレーションシップが含まれます。</span><span class="sxs-lookup"><span data-stu-id="64f92-115">The data in the XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="64f92-116">**[XML ソース エディター]** ダイアログ ボックスでは、指定したスキーマを使用して XML ソース出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="64f92-116">The **XML Source Editor** dialog box uses the specified schema to generate the XML source outputs.</span></span> <span data-ttu-id="64f92-117">XSD ファイルの指定、インライン スキーマの使用、または、指定した XML データ ファイルからの XSD の生成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="64f92-117">You can specify an XSD file, use an inline schema, or generate an XSD from the specified XML data file.</span></span> <span data-ttu-id="64f92-118">スキーマは、デザイン時に使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="64f92-118">The schema must be available at design time.</span></span>  
  
 <span data-ttu-id="64f92-119">XML ソースは、XML ファイル内の別の要素が含まれる各要素の出力を作成し、XML データから表形式構造を生成します。</span><span class="sxs-lookup"><span data-stu-id="64f92-119">The XML source generates tabular structures from the XML data by creating an output for every element that contains other elements in the XML files.</span></span> <span data-ttu-id="64f92-120">たとえば、XML データがカタログおよびカタログ内のアイテムを表している場合、XML ソースはカタログの出力、および、カタログに含まれる各種類のアイテムに対する出力を作成します。</span><span class="sxs-lookup"><span data-stu-id="64f92-120">For example, if the XML data represents catalogs and items in catalogs, the XML source creates an output for catalogs and an output for each type of item that the catalogs contain.</span></span> <span data-ttu-id="64f92-121">各アイテムの出力には、そのアイテムの属性に対する出力列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="64f92-121">The output of each item will contain output columns for the attributes of that item.</span></span>  
  
 <span data-ttu-id="64f92-122">出力内のデータの階層リレーションシップに関する情報を提供するため、XML ソースは、各子要素に対する親要素を識別する列を出力に追加します。</span><span class="sxs-lookup"><span data-stu-id="64f92-122">To provide information about the hierarchical relationship of the data in the outputs, the XML source adds a column in the outputs that identifies the parent element for each child element.</span></span> <span data-ttu-id="64f92-123">異なる種類のアイテムを持つカタログの場合、各アイテムは、アイテムが属するカタログを識別する列の値を持つことになります。</span><span class="sxs-lookup"><span data-stu-id="64f92-123">Using the example of catalogs with different types of items, each item would have a column value that identifies the catalog to which it belongs.</span></span>  
  
 <span data-ttu-id="64f92-124">XML ソースは各要素に対して出力を作成しますが、すべての出力を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="64f92-124">The XML source creates an output for every element, but it is not required that you use all the outputs.</span></span> <span data-ttu-id="64f92-125">使用しない出力を削除したり、下流コンポーネントに出力を連結しないようにできます。</span><span class="sxs-lookup"><span data-stu-id="64f92-125">You can delete any output that you do not want to use, or just not connect it to a downstream component.</span></span>  
  
 <span data-ttu-id="64f92-126">また、XML ソースは、明確な名前を持つ出力名を生成します。</span><span class="sxs-lookup"><span data-stu-id="64f92-126">The XML source also generates the output names, to ensure that the names are unambiguous.</span></span> <span data-ttu-id="64f92-127">これらの名前は、長すぎて、出力を識別するには役に立たない場合があります。</span><span class="sxs-lookup"><span data-stu-id="64f92-127">These names may be long and may not identify the outputs in a way that is useful to you.</span></span> <span data-ttu-id="64f92-128">出力名は、一意である限り変更できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-128">You can rename the outputs, as long as their names remain unique.</span></span> <span data-ttu-id="64f92-129">また、出力列のデータ型や長さも変更できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-129">You can also modify the data type and the length of output columns.</span></span>  
  
 <span data-ttu-id="64f92-130">各出力に対し、XML ソースはエラー出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="64f92-130">For every output, the XML source adds an error output.</span></span> <span data-ttu-id="64f92-131">既定では、エラー出力の列は、長さ 255 文字の Unicode 文字列データ型 (DT_WSTR) です。ただし、データ型と長さを変更して、エラー出力の列を構成できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-131">By default the columns in error outputs have Unicode string data type (DT_WSTR) with a length of 255, but you can configure the columns in the error outputs by modifying their data type and length.</span></span>  
  
 <span data-ttu-id="64f92-132">XML データ ファイルに、XSD に存在しない要素が含まれる場合、これらの要素は無視され、出力が生成されません。</span><span class="sxs-lookup"><span data-stu-id="64f92-132">If the XML data file contains elements that are not in the XSD, these elements are ignored and no output is generated for them.</span></span> <span data-ttu-id="64f92-133">これに対し、XML データ ファイルに XSD で表されている要素がない場合、出力には NULL 値の列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="64f92-133">On the other hand, if the XML data file is missing elements that are represented in the XSD, the output will contain columns with null values.</span></span>  
  
 <span data-ttu-id="64f92-134">データが XML データ ファイルから抽出されると、そのデータは [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="64f92-134">When the data is extracted from the XML data file, it is converted to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="64f92-135">ただし、XML ソースは XML データを DT_TIME2 データ型または DT_DBTIMESTAMP2 データ型に変換することはできません。これらのデータ型をサポートしていないためです。</span><span class="sxs-lookup"><span data-stu-id="64f92-135">However, the XML source cannot convert the XML data to the DT_TIME2 or DT_DBTIMESTAMP2 data types because the source does not support these data types.</span></span> <span data-ttu-id="64f92-136">詳細については、「 [Integration Services Data Types](integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f92-136">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="64f92-137">XSD またはインライン スキーマで要素のデータ型を指定することもできますが、指定しない場合は **[XML ソース エディター]** ダイアログ ボックスで出力の要素が含まれる列に Unicode 文字列データ型 (DT_WSTR) が割り当てられ、その列の長さが 255 文字に設定されます。</span><span class="sxs-lookup"><span data-stu-id="64f92-137">The XSD or inline schema may specify the data type for elements, but if it does not, the **XML Source Editor** dialog box assigns the Unicode string data type (DT_WSTR) to the column in the output that contains the element, and sets the column length to 255 characters.</span></span>  
  
 <span data-ttu-id="64f92-138">スキーマで要素の最大長を指定する場合、出力列の長さはこの値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="64f92-138">If the schema specifies the maximum length of an element, the length of output column is set to this value.</span></span> <span data-ttu-id="64f92-139">最大長が、要素の変換後の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型でサポートされている長さよりも大きい場合、データはデータ型の最大長に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="64f92-139">If the maximum length is greater than the length supported by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to which the element is converted, then the data is truncated to the maximum length of the data type.</span></span> <span data-ttu-id="64f92-140">たとえば、長さ 5,000 の文字列の場合、DT_WSTR データ型の最大長は 4,000 文字であるため、4,000 文字に切り捨てられます。同様に、バイト データは DT_BYTES データ型の最大長である 8,000 文字に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="64f92-140">For example, if a string has a length of 5000, it is truncated to 4000 characters because the maximum length of the DT_WSTR data type is 4000 characters; likewise, byte data is truncated to 8000 characters, the maximum length of the DT_BYTES data type.</span></span> <span data-ttu-id="64f92-141">スキーマで最大長を指定しない場合、どのデータ型でも列の既定の長さは 255 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="64f92-141">If the schema specifies no maximum length, the default length of columns with either data type is set to 255.</span></span> <span data-ttu-id="64f92-142">XML ソースのデータの切り捨ては、他のデータ フロー コンポーネントでの切り捨てと同様に処理されます。</span><span class="sxs-lookup"><span data-stu-id="64f92-142">Data truncation in the XML source is handled the same way as truncation in other data flow components.</span></span> <span data-ttu-id="64f92-143">詳細については、「 [データのエラー処理](error-handling-in-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f92-143">For more information, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="64f92-144">データ型と列の長さは変更できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-144">You can modify the data type and the column length.</span></span> <span data-ttu-id="64f92-145">詳細については、「 [Integration Services Data Types](integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f92-145">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="configuration-of-the-xml-source"></a><span data-ttu-id="64f92-146">XML ソースの構成</span><span class="sxs-lookup"><span data-stu-id="64f92-146">Configuration of the XML Source</span></span>  
 <span data-ttu-id="64f92-147">XML ソースでは、3 つの異なるデータ アクセス モードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="64f92-147">The XML source supports three different data access modes.</span></span> <span data-ttu-id="64f92-148">XML データ ファイルのファイルの場所、ファイルの場所を含む変数、または XML データを含む変数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-148">You can specify the file location of the XML data file, the variable that contains the file location, or the variable that contains the XML data.</span></span>  
  
 <span data-ttu-id="64f92-149">XML ソースには、パッケージの読み込み時にプロパティ式で更新できる、`XMLData` カスタム プロパティと `XMLSchemaDefinition` カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="64f92-149">The XML source includes the `XMLData` and `XMLSchemaDefinition` custom properties that can be updated by property expressions when the package is loaded.</span></span> <span data-ttu-id="64f92-150">詳細については、「[Integration Services (SSIS) の式](../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../expressions/use-property-expressions-in-packages.md)」、および「[XML 入力元のカスタム プロパティ](xml-source-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f92-150">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [XML Source Custom Properties](xml-source-custom-properties.md).</span></span>  
  
 <span data-ttu-id="64f92-151">XML ソースでは、複数の標準出力と複数のエラー出力がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="64f92-151">The XML source supports multiple regular outputs and multiple error outputs.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="64f92-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、XML ソースを構成するための **[XML ソース エディター]** ダイアログ ボックスがあります。</span><span class="sxs-lookup"><span data-stu-id="64f92-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes the **XML Source Edito**r dialog box for configuring the XML source.</span></span> <span data-ttu-id="64f92-153">このダイアログ ボックスは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから利用できます。</span><span class="sxs-lookup"><span data-stu-id="64f92-153">This dialog box is available in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="64f92-154">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="64f92-154">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="64f92-155">**[XML ソース エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f92-155">For more information about the properties that you can set in the **XML Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="64f92-156">[[XML ソース エディター] &#40;[接続マネージャー] ページ&#41;](../xml-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="64f92-156">[XML Source Editor &#40;Connection Manager Page&#41;](../xml-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="64f92-157">[[XML ソース エディター] &#40;[列] ページ&#41;](../xml-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="64f92-157">[XML Source Editor &#40;Columns Page&#41;](../xml-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="64f92-158">[XML ソース エディター &#40;[エラー出力] ページ&#41;](../xml-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="64f92-158">[XML Source Editor &#40;Error Output Page&#41;](../xml-source-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="64f92-159">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="64f92-159">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="64f92-160">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f92-160">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="64f92-161">Common Properties</span><span class="sxs-lookup"><span data-stu-id="64f92-161">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="64f92-162">XML 入力元のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="64f92-162">XML Source Custom Properties</span></span>](xml-source-custom-properties.md)  
  
 <span data-ttu-id="64f92-163">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f92-163">For more information about how to set the properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="64f92-164">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="64f92-164">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="64f92-165">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="64f92-165">Related Tasks</span></span>  
 [<span data-ttu-id="64f92-166">XML ソースを使用してデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="64f92-166">Extract Data by Using the XML Source</span></span>](xml-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="64f92-167">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="64f92-167">Related Content</span></span>  
 <span data-ttu-id="64f92-168">[XML ファイルを使用して SSIS パッケージを構成する](https://www.sqlshack.com/using-xml-file-configure-ssis-package/)技術記事。</span><span class="sxs-lookup"><span data-stu-id="64f92-168">Technical article, [Using an XML file to configure an SSIS package](https://www.sqlshack.com/using-xml-file-configure-ssis-package/).</span></span>  
  
  
