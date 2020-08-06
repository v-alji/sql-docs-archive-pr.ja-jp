---
title: '[フラットファイルソースエディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b0249b2b17d50fdef4b5cf4aff70a1318614257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632605"
---
# <a name="flat-file-source-editor-columns-page"></a><span data-ttu-id="8fc8b-102">[フラット ファイル ソース エディター]\ ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="8fc8b-102">Flat File Source Editor (Columns Page)</span></span>
  <span data-ttu-id="8fc8b-103">**[フラット ファイル ソース エディター]** ダイアログ ボックスの **[列]** ノードを使用すると、出力列を各外部 (変換元) 列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-103">Use the **Columns** node of the **Flat File Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8fc8b-104">フラットファイル `FileNameColumnName` ソースのプロパティおよび `FastParse` その出力列のプロパティは、[**フラットファイルソースエディター**] では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-104">The `FileNameColumnName` property of the Flat File source and the `FastParse` property of its output columns are not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="8fc8b-105">これらのプロパティの詳細については、「 [Flat File Custom Properties](data-flow/flat-file-custom-properties.md)」の「フラット ファイル ソース」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-105">For more information on these properties, see the Flat File Source section of [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="8fc8b-106">フラット ファイル ソースの詳細については、「 [Flat File Source](data-flow/flat-file-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-106">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8fc8b-107">Options</span><span class="sxs-lookup"><span data-stu-id="8fc8b-107">Options</span></span>  
 <span data-ttu-id="8fc8b-108">**使用できる外部列**</span><span class="sxs-lookup"><span data-stu-id="8fc8b-108">**Available External Columns**</span></span>  
 <span data-ttu-id="8fc8b-109">データ ソース内の使用できる外部列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-109">View the list of available external columns in the data source.</span></span> <span data-ttu-id="8fc8b-110">このテーブルを使用して列を追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-110">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="8fc8b-111">**[外部列]**</span><span class="sxs-lookup"><span data-stu-id="8fc8b-111">**External Column**</span></span>  
 <span data-ttu-id="8fc8b-112">タスクで外部 (変換元) 列を読み取る順序を表示します。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-112">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="8fc8b-113">この順序を変更するには、テーブルで選択した列を消去してから、別の順序で一覧から外部列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-113">You can change this order by first clearing the selected columns in the table, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="8fc8b-114">**出力列**</span><span class="sxs-lookup"><span data-stu-id="8fc8b-114">**Output Column**</span></span>  
 <span data-ttu-id="8fc8b-115">各出力列の一意な名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-115">Provide a unique name for each output column.</span></span> <span data-ttu-id="8fc8b-116">既定では選択された外部 (変換元) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-116">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="8fc8b-117">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8fc8b-117">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc8b-118">参照</span><span class="sxs-lookup"><span data-stu-id="8fc8b-118">See Also</span></span>  
 <span data-ttu-id="8fc8b-119">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8fc8b-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="8fc8b-120">[[フラットファイルソースエディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="8fc8b-120">[Flat File Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="8fc8b-121">[フラットファイルソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="8fc8b-121">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="8fc8b-122">フラット ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="8fc8b-122">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
