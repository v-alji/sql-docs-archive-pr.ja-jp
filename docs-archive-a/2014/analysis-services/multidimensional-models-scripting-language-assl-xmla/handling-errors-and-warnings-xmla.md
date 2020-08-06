---
title: エラーと警告の処理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07b88d800237e5b4b06af0c1ff11cbd0af846600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639737"
---
# <a name="handling-errors-and-warnings-xmla"></a><span data-ttu-id="62e75-102">エラーおよび警告の処理 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="62e75-102">Handling Errors and Warnings (XMLA)</span></span>
  <span data-ttu-id="62e75-103">エラー処理は、XML for Analysis (XMLA) の[Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)または[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドの呼び出しが実行されず、正常に実行されるがエラーまたは警告が生成される場合、または正常に実行されてもエラーを含む結果が返される場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="62e75-103">Error handling is required when an XML for Analysis (XMLA) [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) or [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method call does not run, runs successfully but generates errors or warnings, or runs successfully but returns results that contain errors.</span></span>  
  
|<span data-ttu-id="62e75-104">エラー</span><span class="sxs-lookup"><span data-stu-id="62e75-104">Error</span></span>|<span data-ttu-id="62e75-105">レポーティング</span><span class="sxs-lookup"><span data-stu-id="62e75-105">Reporting</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="62e75-106">XMLA メソッド呼び出しを実行できない</span><span class="sxs-lookup"><span data-stu-id="62e75-106">The XMLA method call does not run</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="62e75-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エラーの詳細を含む SOAP エラーメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="62e75-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns a SOAP fault message that contains the details of the failure.</span></span><br /><br /> <span data-ttu-id="62e75-108">詳細については、「 [SOAP エラーの処理](#handling_soap_faults)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62e75-108">For more information, see the section, [Handling SOAP Faults](#handling_soap_faults).</span></span>|  
|<span data-ttu-id="62e75-109">メソッド呼び出しは成功したが、エラーまたは警告が発生した</span><span class="sxs-lookup"><span data-stu-id="62e75-109">Errors or warnings on a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="62e75-110">では、各エラーまたは警告について、メソッド呼び出しの結果を含む[ルート](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)要素の[Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)プロパティに、[エラー](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)または[警告](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla)の要素がそれぞれ含まれています。</span><span class="sxs-lookup"><span data-stu-id="62e75-110">includes an [error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) or [warning](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) element for each error or warning, respectively, in the [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) property of the [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) element that contains the results of the method call.</span></span><br /><br /> <span data-ttu-id="62e75-111">詳細については、「[エラーと警告の処理](#handling_errors_and_warnings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62e75-111">For more information, see the section, [Handling Errors and Warnings](#handling_errors_and_warnings).</span></span>|  
|<span data-ttu-id="62e75-112">メソッド呼び出しは成功したが、結果にエラーが含まれる</span><span class="sxs-lookup"><span data-stu-id="62e75-112">Errors in the result for a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="62e75-113">には、 `error` `warning` メソッド呼び出しの結果の適切な[セル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)または[行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla)要素内に、エラーまたは警告のインラインまたは要素がそれぞれ含まれています。</span><span class="sxs-lookup"><span data-stu-id="62e75-113">includes an inline `error` or `warning` element for the error or warning, respectively, within the appropriate [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) or [row](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) element of the results of the method call.</span></span><br /><br /> <span data-ttu-id="62e75-114">詳細については、「[インラインエラーと警告の処理](#handling_inline_errors_and_warnings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62e75-114">For more information, see the section, [Handling Inline Errors and Warnings](#handling_inline_errors_and_warnings).</span></span>|  
  
##  <a name="handling-soap-faults"></a><a name="handling_soap_faults"></a><span data-ttu-id="62e75-115">SOAP エラーの処理</span><span class="sxs-lookup"><span data-stu-id="62e75-115">Handling SOAP Faults</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="62e75-116">は、以下の状況が発生した場合に、SOAP エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="62e75-116">returns a SOAP fault when the following situations occur:</span></span>  
  
-   <span data-ttu-id="62e75-117">XMLA メソッドを含む SOAP メッセージが、整形式でないか、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって検証できなかった。</span><span class="sxs-lookup"><span data-stu-id="62e75-117">The SOAP message that contains the XMLA method was not well-formed or could not be validated by the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="62e75-118">XMLA メソッドを含む SOAP メッセージに関係する通信エラーまたはその他のエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="62e75-118">A communications or other error occurred involving the SOAP message that contains the XMLA method.</span></span>  
  
-   <span data-ttu-id="62e75-119">XMLA メソッドが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで実行できなかった。</span><span class="sxs-lookup"><span data-stu-id="62e75-119">The XMLA method did not run on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="62e75-120">XMLA の SOAP エラー コードは、"XMLForAnalysis" で始まり、その後にピリオドと 16 進数の HRESULT 結果コードが続きます。</span><span class="sxs-lookup"><span data-stu-id="62e75-120">The SOAP fault codes for XMLstartA start with "XMLForAnalysis", followed by a period and the hexadecimal HRESULT result code.</span></span> <span data-ttu-id="62e75-121">たとえば、エラー コード "`0x80000005`" は "`XMLForAnalysis.0x80000005`" という形式になります。</span><span class="sxs-lookup"><span data-stu-id="62e75-121">For example, an error code of "`0x80000005`" is formatted as "`XMLForAnalysis.0x80000005`".</span></span> <span data-ttu-id="62e75-122">SOAP エラー形式の詳細については、W3C による『Simple Object Access Protocol (SOAP) 1.1』の「Soap Fault」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62e75-122">For more information about the SOAP fault format, see Soap Fault in the W3C Simple Object Access Protocol (SOAP) 1.1.</span></span>  
  
### <a name="fault-code-information"></a><span data-ttu-id="62e75-123">エラー コード情報</span><span class="sxs-lookup"><span data-stu-id="62e75-123">Fault Code Information</span></span>  
 <span data-ttu-id="62e75-124">次の表は、SOAP 応答の詳細セクションに含まれる XMLA エラー コード情報を示しています。</span><span class="sxs-lookup"><span data-stu-id="62e75-124">The following table shows the XMLA fault code information that is contained in the detail section of the SOAP response.</span></span> <span data-ttu-id="62e75-125">列は、SOAP エラーの詳細セクションに含まれるエラーの属性です。</span><span class="sxs-lookup"><span data-stu-id="62e75-125">The columns are the attributes of an error in the detail section of a SOAP fault.</span></span>  
  
|<span data-ttu-id="62e75-126">列名</span><span class="sxs-lookup"><span data-stu-id="62e75-126">Column name</span></span>|<span data-ttu-id="62e75-127">Type</span><span class="sxs-lookup"><span data-stu-id="62e75-127">Type</span></span>|<span data-ttu-id="62e75-128">説明</span><span class="sxs-lookup"><span data-stu-id="62e75-128">Description</span></span>|<span data-ttu-id="62e75-129">Null 値が許可されます<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="62e75-129">Null allowed<sup>1</sup></span></span>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|<span data-ttu-id="62e75-130">メソッドの成功または失敗を示すリターン コード。</span><span class="sxs-lookup"><span data-stu-id="62e75-130">Return code that indicates the success or failure of the method.</span></span> <span data-ttu-id="62e75-131">16 進数値は、`UnsignedInt` の値に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62e75-131">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="62e75-132">いいえ</span><span class="sxs-lookup"><span data-stu-id="62e75-132">No</span></span>|  
|`WarningCode`|`UnsignedInt`|<span data-ttu-id="62e75-133">警告の状況を示すリターン コード。</span><span class="sxs-lookup"><span data-stu-id="62e75-133">Return code that indicates a warning condition.</span></span> <span data-ttu-id="62e75-134">16 進数値は、`UnsignedInt` の値に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62e75-134">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="62e75-135">はい</span><span class="sxs-lookup"><span data-stu-id="62e75-135">Yes</span></span>|  
|`Description`|`String`|<span data-ttu-id="62e75-136">エラーを生成したコンポーネントによって返されたエラーまたは警告のテキストと説明。</span><span class="sxs-lookup"><span data-stu-id="62e75-136">Error or warning text and description returned by the component that generated the error.</span></span>|<span data-ttu-id="62e75-137">はい</span><span class="sxs-lookup"><span data-stu-id="62e75-137">Yes</span></span>|  
|`Source`|`String`|<span data-ttu-id="62e75-138">エラーまたは警告を生成したコンポーネントの名前。</span><span class="sxs-lookup"><span data-stu-id="62e75-138">Name of the component that generated the error or warning.</span></span>|<span data-ttu-id="62e75-139">はい</span><span class="sxs-lookup"><span data-stu-id="62e75-139">Yes</span></span>|  
|`HelpFile`|`String`|<span data-ttu-id="62e75-140">エラーまたは警告について説明しているファイルまたはトピックへのパス、または URL。</span><span class="sxs-lookup"><span data-stu-id="62e75-140">Path or URL to the Help file or topic that describes the error or warning.</span></span>|<span data-ttu-id="62e75-141">はい</span><span class="sxs-lookup"><span data-stu-id="62e75-141">Yes</span></span>|  
  
 <span data-ttu-id="62e75-142"><sup>1</sup>は、データが必須であり、返される必要があるかどうか、またはデータが省略可能であり、列が適用されない場合は null 文字列が許可されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="62e75-142"><sup>1</sup> Indicates whether the data is required and must be returned, or whether the data is optional and a null string is allowed if the column does not apply.</span></span>  
  
 <span data-ttu-id="62e75-143">次は、メソッド呼び出しが失敗した場合に発生した SOAP エラーの例です。</span><span class="sxs-lookup"><span data-stu-id="62e75-143">The following is an example of a SOAP fault that occurred when a method call failed:</span></span>  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling-errors-and-warnings"></a><a name="handling_errors_and_warnings"></a><span data-ttu-id="62e75-144">エラーと警告の処理</span><span class="sxs-lookup"><span data-stu-id="62e75-144">Handling Errors and Warnings</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="62e75-145">は、コマンドの実行後に以下の状況が発生した場合、`Messages` 要素内に `root` プロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="62e75-145">returns the `Messages` property in the `root` element for a command if the following situations occur after that command runs:</span></span>  
  
-   <span data-ttu-id="62e75-146">メソッド自体は失敗しなかったが、メソッドが成功した後に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="62e75-146">The method itself did not fail, but a failure occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the method call succeeded.</span></span>  
  
-   <span data-ttu-id="62e75-147">コマンドが成功したときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって警告が返される。</span><span class="sxs-lookup"><span data-stu-id="62e75-147">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance returns a warning when the command is successful.</span></span>  
  
 <span data-ttu-id="62e75-148">`Messages` プロパティは、`root` 要素に含まれる他のすべてのプロパティの後に続きます。このプロパティには、1 つ以上の `Message` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="62e75-148">The `Messages` property follows all other properties that are contained by the `root` element, and can contain one or more `Message` elements.</span></span> <span data-ttu-id="62e75-149">さらに、各 `Message` 要素には、指定されたコマンドで発生したエラーまたは警告についてそれぞれ説明する 1 つの `error` または `warning` 要素のいずれかが含まれます。</span><span class="sxs-lookup"><span data-stu-id="62e75-149">In turn, each `Message` element can contain either a single `error` or `warning` element describing any errors or warnings, respectively, that occurred for the specified command.</span></span>  
  
 <span data-ttu-id="62e75-150">プロパティに含まれるエラーと警告の詳細につい `Messages` ては、「 [Messages 要素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62e75-150">For more information about errors and warnings that are contained in the `Messages` property, see [Messages Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).</span></span>  
  
### <a name="handling-errors-during-serialization"></a><span data-ttu-id="62e75-151">シリアル化実行時のエラーの処理</span><span class="sxs-lookup"><span data-stu-id="62e75-151">Handling Errors During Serialization</span></span>  
 <span data-ttu-id="62e75-152">インスタンスが正常に実行されたコマンドの出力のシリアル化を既に開始した後にエラーが発生した場合 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エラーの時点で別の名前空間の[Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla)要素を返します。</span><span class="sxs-lookup"><span data-stu-id="62e75-152">If an error occurs after the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance has already begun serializing the output of a successfully run command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) element in a different namespace at the point of the error.</span></span> <span data-ttu-id="62e75-153">その後 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、クライアントに送信する XML ドキュメントが有効なドキュメントになるように、開いている要素をすべて閉じます。</span><span class="sxs-lookup"><span data-stu-id="62e75-153">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance then closes all open elements so that the XML document sent to the client is a valid document.</span></span> <span data-ttu-id="62e75-154">インスタンスは、エラーの説明を含む `Messages` 要素も返します。</span><span class="sxs-lookup"><span data-stu-id="62e75-154">The instance also returns a `Messages` element that contains the description of the error.</span></span>  
  
##  <a name="handling-inline-errors-and-warnings"></a><a name="handling_inline_errors_and_warnings"></a><span data-ttu-id="62e75-155">インラインエラーと警告の処理</span><span class="sxs-lookup"><span data-stu-id="62e75-155">Handling Inline Errors and Warnings</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="62e75-156">は、XMLA メソッド自体は失敗しなかったものの、XMLA メソッド呼び出しが成功した後に、メソッドによって返された結果内のデータ要素に固有のエラーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで発生した場合、インライン `error` または `warning` を返します。</span><span class="sxs-lookup"><span data-stu-id="62e75-156">returns an inline `error` or `warning` for a command if the XMLA method itself did not fail, but an error specific to a data element in the results returned by the method occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the XMLA method call succeeded.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="62e75-157">セルに `error` `warning` 固有の問題、または mddataset データ型を使用して要素内に含まれるその他のデータに固有の問題がある場合は、インライン要素と要素を提供し `root` ます。たとえば、セキュリティエラーやセルの書式設定エラーなどです。 [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla)</span><span class="sxs-lookup"><span data-stu-id="62e75-157">supplies inline `error` and `warning` elements if issues specific to a cell or to other data that are contained within a `root` element using the [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) data type occur, such as a security error or formatting error for a cell.</span></span> <span data-ttu-id="62e75-158">そのような場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、エラーまたは警告を含む `error` または `warning` 要素に、`Cell` または `row` 要素をそれぞれ返します。</span><span class="sxs-lookup"><span data-stu-id="62e75-158">In these cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an `error` or `warning` element in the `Cell` or `row` element that contains the error or warning, respectively.</span></span>  
  
 <span data-ttu-id="62e75-159">次の例では、 `Execute` [ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを使用して、メソッドから返された行セットのエラーを含む結果セットを示します。</span><span class="sxs-lookup"><span data-stu-id="62e75-159">The following example illustrates a result set that contains an error in the rowset returned from an `Execute` method using the [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command.</span></span>  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a><span data-ttu-id="62e75-160">参照</span><span class="sxs-lookup"><span data-stu-id="62e75-160">See Also</span></span>  
 [<span data-ttu-id="62e75-161">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="62e75-161">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
