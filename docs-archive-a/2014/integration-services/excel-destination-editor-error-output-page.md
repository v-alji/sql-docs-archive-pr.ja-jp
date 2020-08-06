---
title: '[Excel 変換先エディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.erroroutput.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: 72ae01cc-1774-4a36-9674-a0f2b2bf8c42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bee679f563105cade3053a13eb122f6d482a7d86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641762"
---
# <a name="excel-destination-editor-error-output-page"></a><span data-ttu-id="c92ee-102">[Excel 変換先エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="c92ee-102">Excel Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="c92ee-103">**[Excel 変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、エラー処理オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c92ee-103">Use the **Advanced** page of the **Excel Destination Editor** dialog box to specify options for error handling.</span></span>  
  
 <span data-ttu-id="c92ee-104">Excel 変換先の詳細については、「 [Excel Destination](data-flow/excel-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c92ee-104">To learn more about the Excel destination, see [Excel Destination](data-flow/excel-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c92ee-105">Options</span><span class="sxs-lookup"><span data-stu-id="c92ee-105">Options</span></span>  
 <span data-ttu-id="c92ee-106">**入力または出力**</span><span class="sxs-lookup"><span data-stu-id="c92ee-106">**Input or Output**</span></span>  
 <span data-ttu-id="c92ee-107">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c92ee-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="c92ee-108">**列**</span><span class="sxs-lookup"><span data-stu-id="c92ee-108">**Column**</span></span>  
 <span data-ttu-id="c92ee-109">**[Excel ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ノードで選択されている外部 (ソース) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="c92ee-109">View the external (source) columns that you selected in the **Connection Manager** node of the **Excel Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="c92ee-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="c92ee-110">**Error**</span></span>  
 <span data-ttu-id="c92ee-111">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c92ee-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="c92ee-112">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="c92ee-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="c92ee-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="c92ee-113">**Truncation**</span></span>  
 <span data-ttu-id="c92ee-114">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c92ee-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="c92ee-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="c92ee-115">**Description**</span></span>  
 <span data-ttu-id="c92ee-116">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="c92ee-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="c92ee-117">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="c92ee-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="c92ee-118">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c92ee-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="c92ee-119">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="c92ee-119">**Apply**</span></span>  
 <span data-ttu-id="c92ee-120">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="c92ee-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92ee-121">参照</span><span class="sxs-lookup"><span data-stu-id="c92ee-121">See Also</span></span>  
 <span data-ttu-id="c92ee-122">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c92ee-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c92ee-123">[[Excel 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/excel-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="c92ee-123">[Excel Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="c92ee-124">[Excel 変換先エディターの [マッピング] ページ&#41;&#40;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="c92ee-124">[Excel Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="c92ee-125">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="c92ee-125">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
