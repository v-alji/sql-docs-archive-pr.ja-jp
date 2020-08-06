---
title: '[XML ソースエディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.columns.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: 5162c400-b2fc-4711-af0f-609132fbaaad
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b9433b7a2c4f08f9e0c70d568f8fc037ceb7c6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736504"
---
# <a name="xml-source-editor-columns-page"></a><span data-ttu-id="371f1-102">[XML ソース エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="371f1-102">XML Source Editor (Columns Page)</span></span>
  <span data-ttu-id="371f1-103">**[XML ソース エディター]** ダイアログ ボックスの **[列]** ノードを使用して、出力列を外部 (変換元) 列にマップします。</span><span class="sxs-lookup"><span data-stu-id="371f1-103">Use the **Columns** node of the **XML Source Editor** dialog box to map an output column to an external (source) column.</span></span>  
  
 <span data-ttu-id="371f1-104">XML ソースの詳細については、「 [XML Source](data-flow/xml-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="371f1-104">For more information about the XML source, see [XML Source](data-flow/xml-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="371f1-105">Options</span><span class="sxs-lookup"><span data-stu-id="371f1-105">Options</span></span>  
 <span data-ttu-id="371f1-106">**使用できる外部列**</span><span class="sxs-lookup"><span data-stu-id="371f1-106">**Available External Columns**</span></span>  
 <span data-ttu-id="371f1-107">データ ソース内の使用できる外部列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="371f1-107">View the list of available external columns in the data source.</span></span> <span data-ttu-id="371f1-108">このテーブルを使用して列を追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="371f1-108">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="371f1-109">**[外部列]**</span><span class="sxs-lookup"><span data-stu-id="371f1-109">**External Column**</span></span>  
 <span data-ttu-id="371f1-110">タスクで外部 (変換元) 列を読み取る順序を表示します。</span><span class="sxs-lookup"><span data-stu-id="371f1-110">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="371f1-111">この順序を変更するには、最初にエディターに表示されているテーブル内で選択されている列を選択解除してから、一覧から外部列を別の順で選択します。</span><span class="sxs-lookup"><span data-stu-id="371f1-111">You can change this order by first clearing the selected columns in the table displayed in the editor, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="371f1-112">**出力列**</span><span class="sxs-lookup"><span data-stu-id="371f1-112">**Output Column**</span></span>  
 <span data-ttu-id="371f1-113">各出力列の一意な名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="371f1-113">Provide a unique name for each output column.</span></span> <span data-ttu-id="371f1-114">既定では選択された外部 (変換元) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="371f1-114">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="371f1-115">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="371f1-115">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="371f1-116">参照</span><span class="sxs-lookup"><span data-stu-id="371f1-116">See Also</span></span>  
 <span data-ttu-id="371f1-117">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="371f1-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="371f1-118">[[XML ソースエディター &#40;接続マネージャー] ページ&#41;](../../2014/integration-services/xml-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="371f1-118">[XML Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/xml-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="371f1-119">[XML ソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="371f1-119">[XML Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="371f1-120">XML ソースを使用してデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="371f1-120">Extract Data by Using the XML Source</span></span>](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
