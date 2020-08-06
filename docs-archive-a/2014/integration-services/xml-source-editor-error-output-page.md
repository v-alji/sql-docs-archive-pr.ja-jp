---
title: '[XML ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.erroroutput.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: 2ddb97c2-1e43-478f-8872-b6efd41b931e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4842442ca798c53c9b5352491959a62314a3cd73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736492"
---
# <a name="xml-source-editor-error-output-page"></a><span data-ttu-id="1fb6e-102">[XML ソース エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="1fb6e-102">XML Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="1fb6e-103">**[XML ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-103">Use the **Error Output** page of the **XML Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="1fb6e-104">XML ソースの詳細については、「 [XML Source](data-flow/xml-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-104">For more information about the XML source, see [XML Source](data-flow/xml-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1fb6e-105">Options</span><span class="sxs-lookup"><span data-stu-id="1fb6e-105">Options</span></span>  
 <span data-ttu-id="1fb6e-106">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-106">**Input/Output**</span></span>  
 <span data-ttu-id="1fb6e-107">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="1fb6e-108">**列**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-108">**Column**</span></span>  
 <span data-ttu-id="1fb6e-109">**[XML ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (ソース) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-109">View the external (source) columns that you selected on the **Connection Manager** page of the **XML Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="1fb6e-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-110">**Error**</span></span>  
 <span data-ttu-id="1fb6e-111">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1fb6e-112">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="1fb6e-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="1fb6e-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-113">**Truncation**</span></span>  
 <span data-ttu-id="1fb6e-114">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1fb6e-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-115">**Description**</span></span>  
 <span data-ttu-id="1fb6e-116">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="1fb6e-117">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="1fb6e-118">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1fb6e-119">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-119">**Apply**</span></span>  
 <span data-ttu-id="1fb6e-120">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb6e-121">参照</span><span class="sxs-lookup"><span data-stu-id="1fb6e-121">See Also</span></span>  
 <span data-ttu-id="1fb6e-122">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1fb6e-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1fb6e-123">[[XML ソースエディター &#40;接続マネージャー] ページ&#41;](../../2014/integration-services/xml-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="1fb6e-123">[XML Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/xml-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="1fb6e-124">[[XML ソースエディター &#40;列] ページ&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="1fb6e-124">[XML Source Editor &#40;Columns Page&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="1fb6e-125">XML ソースを使用してデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="1fb6e-125">Extract Data by Using the XML Source</span></span>](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
