---
title: '[Excel ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.erroroutput.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 8d14019e-cb60-4bc1-b71e-7f2326de8317
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 37b2291844aa690cfe4cd412a14569057adb9e85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641757"
---
# <a name="excel-source-editor-error-output-page"></a><span data-ttu-id="faf0d-102">[Excel ソース エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="faf0d-102">Excel Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="faf0d-103">**[Excel ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="faf0d-103">Use the **Error Output** page of the **Excel Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="faf0d-104">Excel ソースの詳細については、「 [Excel Source](data-flow/excel-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="faf0d-104">To learn more about the Excel source, see [Excel Source](data-flow/excel-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="faf0d-105">Options</span><span class="sxs-lookup"><span data-stu-id="faf0d-105">Options</span></span>  
 <span data-ttu-id="faf0d-106">**入力または出力**</span><span class="sxs-lookup"><span data-stu-id="faf0d-106">**Input or Output**</span></span>  
 <span data-ttu-id="faf0d-107">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="faf0d-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="faf0d-108">**列**</span><span class="sxs-lookup"><span data-stu-id="faf0d-108">**Column**</span></span>  
 <span data-ttu-id="faf0d-109">**[Excel ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (変換元) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="faf0d-109">View the external (source) columns that you selected on the **Connection Manager** page of the **Excel Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="faf0d-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="faf0d-110">**Error**</span></span>  
 <span data-ttu-id="faf0d-111">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="faf0d-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="faf0d-112">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="faf0d-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="faf0d-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="faf0d-113">**Truncation**</span></span>  
 <span data-ttu-id="faf0d-114">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="faf0d-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="faf0d-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="faf0d-115">**Description**</span></span>  
 <span data-ttu-id="faf0d-116">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="faf0d-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="faf0d-117">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="faf0d-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="faf0d-118">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="faf0d-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="faf0d-119">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="faf0d-119">**Apply**</span></span>  
 <span data-ttu-id="faf0d-120">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="faf0d-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf0d-121">参照</span><span class="sxs-lookup"><span data-stu-id="faf0d-121">See Also</span></span>  
 <span data-ttu-id="faf0d-122">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="faf0d-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="faf0d-123">[Excel ソースエディター &#40;接続マネージャーのページ&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="faf0d-123">[Excel Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="faf0d-124">[Excel ソースエディター &#40;[列] ページ&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="faf0d-124">[Excel Source Editor &#40;Columns Page&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="faf0d-125">[Excel 接続マネージャー](connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="faf0d-125">[Excel Connection Manager](connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="faf0d-126">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="faf0d-126">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
