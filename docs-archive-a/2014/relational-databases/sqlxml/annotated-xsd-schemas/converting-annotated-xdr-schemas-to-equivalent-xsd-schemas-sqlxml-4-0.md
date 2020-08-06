---
title: 注釈付き XDR スキーマから同等の XSD スキーマへの変換 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
author: rothja
ms.author: jroth
ms.openlocfilehash: c36eb17aacb61a47fad0f389de9a3c216202827d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642690"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a><span data-ttu-id="b4ace-102">注釈付き XDR スキーマから同等の XSD スキーマへの変換 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b4ace-102">Converting Annotated XDR Schemas to Equivalent XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="b4ace-103">XML スキーマ定義 (XSD) 言語は、XML-Data Reduced (XDR) スキーマ定義言語に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="b4ace-103">The XML Schema Definition (XSD) language is the successor to the XML-Data Reduced (XDR) schema definition language.</span></span> <span data-ttu-id="b4ace-104">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 では XSD サポートが導入され、新しい注釈付きスキーマの作成には XSD を使用することになりました。</span><span class="sxs-lookup"><span data-stu-id="b4ace-104">With the introduction of XSD support in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, it is assumed that new annotated schemas are created using XSD.</span></span> <span data-ttu-id="b4ace-105">SQLXML 4.0 には XDR から XSD への変換ツールが用意されており、既存の注釈付き XDR スキーマを同等の XSD スキーマに簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="b4ace-105">SQLXML 4.0 includes an XDR to XSD converter tool that is designed to help you convert your existing annotated XDR schemas to equivalent XSD schemas.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b4ace-106">このツールは、SQLXML 4.0 で、注釈付き XDR スキーマを XSD スキーマに変換する場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="b4ace-106">Use this tool only when you want to convert annotated XDR schemas to XSD for use with SQLXML 4.0.</span></span> <span data-ttu-id="b4ace-107">これは XDR を XSD に変換する汎用ツールではありません。</span><span class="sxs-lookup"><span data-stu-id="b4ace-107">This is not a general purpose XDR to XSD converter tool.</span></span> <span data-ttu-id="b4ace-108">変換された XSD スキーマを別の環境で使用した場合、元の XDR スキーマと同じように動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b4ace-108">The converted XSD schemas may not behave the same as the original XDR schemas when used in other environments.</span></span>  
  
 <span data-ttu-id="b4ace-109">入力 XDR ファイルで XML 宣言内にエンコードが指定されている場合、このエンコードが、生成される XSD 出力ファイルのエンコードになります。</span><span class="sxs-lookup"><span data-stu-id="b4ace-109">If the input XDR file specifies the encoding within the XML declaration, this becomes the encoding of the XSD output file that is generated.</span></span>  
  
 <span data-ttu-id="b4ace-110">変換ツール (Cvtschema.exe) は Program Files\SQLXML 4.0\bin フォルダーにインストールされており、コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="b4ace-110">The converter tool (Cvtschema.exe) is installed in the Program Files\SQLXML 4.0\bin folder and is executed at the command prompt.</span></span>  
  
 <span data-ttu-id="b4ace-111">一般的な構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b4ace-111">This is the general syntax:</span></span>  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 <span data-ttu-id="b4ace-112">この場合、</span><span class="sxs-lookup"><span data-stu-id="b4ace-112">Where:</span></span>  
  
 <span data-ttu-id="b4ace-113">XDRFileName</span><span class="sxs-lookup"><span data-stu-id="b4ace-113">XDRFileName</span></span>  
 <span data-ttu-id="b4ace-114">XSD に変換する XDR ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4ace-114">Is the name of the XDR file that is to be converted to XSD.</span></span> <span data-ttu-id="b4ace-115">このツールでは入力 XDR ファイルが読み取られ、現在の作業ディレクトリに XSD 出力ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b4ace-115">The tool reads the input XDR file and creates an XSD output file in the current working directory.</span></span> <span data-ttu-id="b4ace-116">入力ファイルに拡張子 .xdr または .xml が付けられている場合、出力 XSD ファイルは同じ名前で拡張子が .xsd に変更されます。</span><span class="sxs-lookup"><span data-stu-id="b4ace-116">If the input file has an .xdr or .xml extension, the output XSD file is created with the same name but with an .xsd extension.</span></span> <span data-ttu-id="b4ace-117">入力ファイルの拡張子が .xml または .xdr 以外の場合、または拡張子がない場合、出力ファイルは同じ名前で作成され、拡張子 .xsd が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b4ace-117">If the input file extension is other than .xml or .xdr (or if the extension is missing), the output file is created with the same name and the .xsd extension is appended to the input file name.</span></span> <span data-ttu-id="b4ace-118">たとえば、入力 XDR ファイル名が SampleFile.abc の場合、出力される XSD ファイルは SampleFile.abc.xsd になります。</span><span class="sxs-lookup"><span data-stu-id="b4ace-118">For example, if the input XDR file name is SampleFile.abc, the resulting XSD is saved as SampleFile.abc.xsd.</span></span>  
  
 <span data-ttu-id="b4ace-119">-y</span><span class="sxs-lookup"><span data-stu-id="b4ace-119">-y</span></span>  
 <span data-ttu-id="b4ace-120">(省略可) 既存の XSD ファイルを、変換ツールで生成される XSD ファイルで上書きします。</span><span class="sxs-lookup"><span data-stu-id="b4ace-120">(Optional) Overwrites the existing XSD file with the XSD file that is generated by the converter tool.</span></span> <span data-ttu-id="b4ace-121">このフラグを指定しない場合は、既存の XSD ファイルを上書きするかどうかを確認するメッセージが表示され、このときに出力ファイル名を変更できます。</span><span class="sxs-lookup"><span data-stu-id="b4ace-121">If the flag is not specified, the tool prompts you to specify whether you want to overwrite the existing XSD file and gives you the option to change the output file name.</span></span>  
  
 <span data-ttu-id="b4ace-122">-w</span><span class="sxs-lookup"><span data-stu-id="b4ace-122">-w</span></span>  
 <span data-ttu-id="b4ace-123">(省略可) ツールによる変換処理で発生する、致命的でない警告を返します。</span><span class="sxs-lookup"><span data-stu-id="b4ace-123">(Optional) Returns nonfatal warnings that are generated in the conversion process by the tool.</span></span> <span data-ttu-id="b4ace-124">既定では、致命的なエラーだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4ace-124">By default, the tool displays messages only for fatal errors.</span></span>  
  
 <span data-ttu-id="b4ace-125">-?</span><span class="sxs-lookup"><span data-stu-id="b4ace-125">-?</span></span>  
 <span data-ttu-id="b4ace-126">`cvtschema` で指定できるオプションの一覧とその説明を返します。</span><span class="sxs-lookup"><span data-stu-id="b4ace-126">Returns a list of options that you can specify with `cvtschema`, along with an explanation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ace-127">参照</span><span class="sxs-lookup"><span data-stu-id="b4ace-127">See Also</span></span>  
 <span data-ttu-id="b4ace-128">[XSD データ型から XPath データ型へのマッピング &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="b4ace-128">[Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="b4ace-129">&#40;SQLXML 4.0&#41;の XSD 注釈</span><span class="sxs-lookup"><span data-stu-id="b4ace-129">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](../../sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
