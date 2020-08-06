---
title: '[XML ソースエディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e40ca6ef2d8fbcd10b756a2ce15f33730c367d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645168"
---
# <a name="xml-source-editor-connection-manager-page"></a><span data-ttu-id="e78b1-102">[XML ソース エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="e78b1-102">XML Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="e78b1-103">**[XML ソース エディター]** の **[接続マネージャー]** ページを使用すると、XML ファイルと、XML データを変換する XSD を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e78b1-103">Use the **Connection Manager** page of the **XML Source Editor** to specify an XML file and the XSD that transforms the XML data.</span></span>  
  
 <span data-ttu-id="e78b1-104">XML ソースの詳細については、「 [XML Source](data-flow/xml-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e78b1-104">For more information about the XML source, see [XML Source](data-flow/xml-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="e78b1-105">静的オプション</span><span class="sxs-lookup"><span data-stu-id="e78b1-105">Static Options</span></span>  
 <span data-ttu-id="e78b1-106">**[データ アクセス モード]**</span><span class="sxs-lookup"><span data-stu-id="e78b1-106">**Data access mode**</span></span>  
 <span data-ttu-id="e78b1-107">ソースからデータを選択する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-107">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="e78b1-108">値</span><span class="sxs-lookup"><span data-stu-id="e78b1-108">Value</span></span>|<span data-ttu-id="e78b1-109">説明</span><span class="sxs-lookup"><span data-stu-id="e78b1-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e78b1-110">[XML ファイルの場所]</span><span class="sxs-lookup"><span data-stu-id="e78b1-110">XML file location</span></span>|<span data-ttu-id="e78b1-111">XML ファイルからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-111">Retrieve data from an XML file.</span></span>|  
|<span data-ttu-id="e78b1-112">[変数からの XML ファイル]</span><span class="sxs-lookup"><span data-stu-id="e78b1-112">XML file from variable</span></span>|<span data-ttu-id="e78b1-113">XML ファイルの名前を変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-113">Specify the XML file name in a variable.</span></span><br /><br /> <span data-ttu-id="e78b1-114">**関連情報**: [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="e78b1-114">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="e78b1-115">[変数からの XML データ]</span><span class="sxs-lookup"><span data-stu-id="e78b1-115">XML data from variable</span></span>|<span data-ttu-id="e78b1-116">変数から XML データを取得します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-116">Retrieve XML data from a variable.</span></span>|  
  
 <span data-ttu-id="e78b1-117">**[インライン スキーマを使用する]**</span><span class="sxs-lookup"><span data-stu-id="e78b1-117">**Use inline schema**</span></span>  
 <span data-ttu-id="e78b1-118">XML ソース データ自体に、その構造とデータを定義して検証する XSD スキーマを含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-118">Specify whether the XML source data itself contains the XSD schema that defines and validates its structure and data.</span></span>  
  
 <span data-ttu-id="e78b1-119">**[XSD の場所]**</span><span class="sxs-lookup"><span data-stu-id="e78b1-119">**XSD location**</span></span>  
 <span data-ttu-id="e78b1-120">XSD スキーマ ファイルのパスと名前を入力するか、 **[参照]** をクリックしてファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-120">Type the path and file name of the XSD schema file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="e78b1-121">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="e78b1-121">**Browse**</span></span>  
 <span data-ttu-id="e78b1-122">**[開く]** ダイアログ ボックスを使用して、XSD スキーマ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-122">Use the **Open** dialog box to locate the XSD schema file.</span></span>  
  
 <span data-ttu-id="e78b1-123">**[XSD の生成]**</span><span class="sxs-lookup"><span data-stu-id="e78b1-123">**Generate XSD**</span></span>  
 <span data-ttu-id="e78b1-124">**[名前を付けて保存]** ダイアログ ボックスを使用して、XSD スキーマ ファイルが自動生成される場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-124">Use the **Save As** dialog box to select a location for the auto-generated XSD schema file.</span></span> <span data-ttu-id="e78b1-125">スキーマは XML データの構造から推測されます。</span><span class="sxs-lookup"><span data-stu-id="e78b1-125">The editor infers the schema from the structure of the XML data.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="e78b1-126">データ アクセス モードの動的オプション</span><span class="sxs-lookup"><span data-stu-id="e78b1-126">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--xml-file-location"></a><span data-ttu-id="e78b1-127">[データ アクセス モード] が [XML ファイルの場所] の場合</span><span class="sxs-lookup"><span data-stu-id="e78b1-127">Data access mode = XML file location</span></span>  
 <span data-ttu-id="e78b1-128">**[XML の場所]**</span><span class="sxs-lookup"><span data-stu-id="e78b1-128">**XML location**</span></span>  
 <span data-ttu-id="e78b1-129">XML データ ファイルのパスと名前を入力するか、 **[参照]** をクリックしてファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-129">Type the path and file name of the XML data file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="e78b1-130">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="e78b1-130">**Browse**</span></span>  
 <span data-ttu-id="e78b1-131">**[開く]** ダイアログ ボックスを使用して、XML データ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-131">Use the **Open** dialog box to locate the XML data file.</span></span>  
  
### <a name="data-access-mode--xml-file-from-variable"></a><span data-ttu-id="e78b1-132">[データ アクセス モード] が [変数からの XML ファイル] の場合</span><span class="sxs-lookup"><span data-stu-id="e78b1-132">Data access mode = XML file from variable</span></span>  
 <span data-ttu-id="e78b1-133">**変数名**</span><span class="sxs-lookup"><span data-stu-id="e78b1-133">**Variable name**</span></span>  
 <span data-ttu-id="e78b1-134">XML ファイルのパスとファイル名を含む変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-134">Select the variable that contains the path and file name of the XML file.</span></span>  
  
### <a name="data-access-mode--xml-data-from-variable"></a><span data-ttu-id="e78b1-135">[データ アクセス モード] が [変数からの XML データ] の場合</span><span class="sxs-lookup"><span data-stu-id="e78b1-135">Data access mode = XML data from variable</span></span>  
 <span data-ttu-id="e78b1-136">**変数名**</span><span class="sxs-lookup"><span data-stu-id="e78b1-136">**Variable name**</span></span>  
 <span data-ttu-id="e78b1-137">XML データを含む変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="e78b1-137">Select the variable that contains the XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78b1-138">参照</span><span class="sxs-lookup"><span data-stu-id="e78b1-138">See Also</span></span>  
 <span data-ttu-id="e78b1-139">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e78b1-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e78b1-140">[[XML ソースエディター &#40;列] ページ&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e78b1-140">[XML Source Editor &#40;Columns Page&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e78b1-141">[XML ソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e78b1-141">[XML Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="e78b1-142">XML ソースを使用してデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="e78b1-142">Extract Data by Using the XML Source</span></span>](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
