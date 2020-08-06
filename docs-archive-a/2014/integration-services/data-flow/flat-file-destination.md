---
title: フラット ファイル変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a961b7528b13a4eaa3297343e91f1deaf2fa3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742418"
---
# <a name="flat-file-destination"></a><span data-ttu-id="bcee1-102">フラット ファイル変換先</span><span class="sxs-lookup"><span data-stu-id="bcee1-102">Flat File Destination</span></span>
  <span data-ttu-id="bcee1-103">フラット ファイル変換先は、データをテキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-103">The Flat File destination writes data to a text file.</span></span> <span data-ttu-id="bcee1-104">テキスト ファイルには、区切り形式、固定幅形式、行区切り記号を使用した固定幅形式、または幅合わせしない形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-104">The text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.</span></span>  
  
 <span data-ttu-id="bcee1-105">フラット ファイル変換先は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-105">You can configure the Flat File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="bcee1-106">データが書き込まれる前にファイルに挿入される、テキストのブロックを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcee1-106">Provide a block of text that is inserted in the file before any data is written.</span></span> <span data-ttu-id="bcee1-107">このテキストには、列見出しなどの情報を設定できます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-107">The text can provide information such as column headings.</span></span>  
  
-   <span data-ttu-id="bcee1-108">同じ名前の変換先ファイルにあるデータを上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcee1-108">Specify whether to overwrite a data in a destination file that has the same name.</span></span>  
  
 <span data-ttu-id="bcee1-109">この変換先では、フラット ファイル接続マネージャーを使用してテキスト ファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="bcee1-109">This destination uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="bcee1-110">フラット ファイル変換先が使用するフラット ファイル接続マネージャーでプロパティを設定することにより、フラット ファイル変換先がテキスト ファイルをフォーマットする方法と書き込む方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-110">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="bcee1-111">フラット ファイル接続マネージャーを構成する際には、ファイルおよびファイル内の各列に関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-111">When you configure the Flat File connection manager, you specify information about the file and about each column in the file.</span></span> <span data-ttu-id="bcee1-112">たとえば、ファイルの列と行を区切る文字や、各列のデータ型や長さを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-112">For example, you specify the characters that delimit columns and rows in the file, and you specify the data type and the length of each column.</span></span> <span data-ttu-id="bcee1-113">詳しくは、「 [フラット ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bcee1-113">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="bcee1-114">フラット ファイル変換先には、Header カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="bcee1-114">The Flat File destination includes the Header custom property.</span></span> <span data-ttu-id="bcee1-115">このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="bcee1-116">詳しくは、「[Integration Services &#40;SSIS&#41; の式](../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../expressions/use-property-expressions-in-packages.md)」、および「[フラット ファイルのカスタム プロパティ](flat-file-custom-properties.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bcee1-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [Flat File Custom Properties](flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="bcee1-117">この変換先は 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="bcee1-117">This destination has one output.</span></span> <span data-ttu-id="bcee1-118">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bcee1-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-destination"></a><span data-ttu-id="bcee1-119">フラット ファイル変換先の構成</span><span class="sxs-lookup"><span data-stu-id="bcee1-119">Configuration of the Flat File Destination</span></span>  
 <span data-ttu-id="bcee1-120">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="bcee1-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bcee1-121">**[フラット ファイル ソース エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcee1-121">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="bcee1-122">[[フラット ファイル変換先エディター] &#40;[接続マネージャー] ページ&#41;](../flat-file-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="bcee1-122">[Flat File Destination Editor &#40;Connection Manager Page&#41;](../flat-file-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="bcee1-123">[[フラット ファイル変換先エディター] &#40;[マッピング] ページ&#41;](../flat-file-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="bcee1-123">[Flat File Destination Editor &#40;Mappings Page&#41;](../flat-file-destination-editor-mappings-page.md)</span></span>  
  
 <span data-ttu-id="bcee1-124">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="bcee1-124">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="bcee1-125">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcee1-125">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="bcee1-126">Common Properties</span><span class="sxs-lookup"><span data-stu-id="bcee1-126">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="bcee1-127">フラット ファイルのカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="bcee1-127">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="bcee1-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bcee1-128">Related Tasks</span></span>  
 <span data-ttu-id="bcee1-129">データ フロー コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bcee1-129">For information about how to set the properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcee1-130">参照</span><span class="sxs-lookup"><span data-stu-id="bcee1-130">See Also</span></span>  
 <span data-ttu-id="bcee1-131">[フラット ファイル ソース](flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="bcee1-131">[Flat File Source](flat-file-source.md) </span></span>  
 [<span data-ttu-id="bcee1-132">データ フロー</span><span class="sxs-lookup"><span data-stu-id="bcee1-132">Data Flow</span></span>](data-flow.md)  
  
  
