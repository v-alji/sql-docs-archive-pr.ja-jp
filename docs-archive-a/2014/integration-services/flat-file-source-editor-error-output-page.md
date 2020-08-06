---
title: '[フラットファイルソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.errorhandling.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: c50500e7-0c74-42a0-865f-301f03feffab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 096de22c65d605fc1beea06cbb6ad5909788b408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632603"
---
# <a name="flat-file-source-editor-error-output-page"></a><span data-ttu-id="52f6c-102">[フラット ファイル ソース エディター]\ ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="52f6c-102">Flat File Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="52f6c-103">**[フラット ファイル ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページでは、エラー処理オプションの選択や、エラー出力列に対するプロパティの設定を行えます。</span><span class="sxs-lookup"><span data-stu-id="52f6c-103">Use the **Error Output** page of the **Flat File Source Editor** dialog box to select error-handling options and to set properties on error output columns.\</span></span>  
  
 <span data-ttu-id="52f6c-104">フラット ファイル ソースの詳細については、「 [Flat File Source](data-flow/flat-file-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52f6c-104">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="52f6c-105">Options</span><span class="sxs-lookup"><span data-stu-id="52f6c-105">Options</span></span>  
 <span data-ttu-id="52f6c-106">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="52f6c-106">**Input/Output**</span></span>  
 <span data-ttu-id="52f6c-107">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="52f6c-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="52f6c-108">**列**</span><span class="sxs-lookup"><span data-stu-id="52f6c-108">**Column**</span></span>  
 <span data-ttu-id="52f6c-109">**[フラット ファイル ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (変換元) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="52f6c-109">View the external (source) columns that you selected on the **Connection Manager** page of the **Flat File Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="52f6c-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="52f6c-110">**Error**</span></span>  
 <span data-ttu-id="52f6c-111">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="52f6c-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="52f6c-112">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="52f6c-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="52f6c-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="52f6c-113">**Truncation**</span></span>  
 <span data-ttu-id="52f6c-114">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="52f6c-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="52f6c-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="52f6c-115">**Description**</span></span>  
 <span data-ttu-id="52f6c-116">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="52f6c-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="52f6c-117">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="52f6c-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="52f6c-118">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="52f6c-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="52f6c-119">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="52f6c-119">**Apply**</span></span>  
 <span data-ttu-id="52f6c-120">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="52f6c-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f6c-121">参照</span><span class="sxs-lookup"><span data-stu-id="52f6c-121">See Also</span></span>  
 <span data-ttu-id="52f6c-122">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="52f6c-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="52f6c-123">[[フラットファイルソースエディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="52f6c-123">[Flat File Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="52f6c-124">[[フラットファイルソースエディター] &#40;[列] ページ&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="52f6c-124">[Flat File Source Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="52f6c-125">フラット ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="52f6c-125">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  