---
title: エラー出力を構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configureerroroutput.f1
ms.assetid: 5f8da390-fab5-44f8-b268-d8fa313ce4b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de1a5908c6075438599f4108e9780f5591b042c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642240"
---
# <a name="configure-error-output"></a><span data-ttu-id="158bc-102">[エラー出力の構成]</span><span class="sxs-lookup"><span data-stu-id="158bc-102">Configure Error Output</span></span>
  <span data-ttu-id="158bc-103">**[エラー出力の構成]** ダイアログ ボックスを使用すると、エラー出力をサポートするデータ フロー変換のエラー処理オプションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="158bc-103">Use the **Configure Error Output** dialog box to configure error handling options for data flow transformations that support an error output.</span></span>  
  
 <span data-ttu-id="158bc-104">エラー出力の操作の詳細については、「 [データのエラー処理](data-flow/error-handling-in-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="158bc-104">To learn more about working with error outputs, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="158bc-105">Options</span><span class="sxs-lookup"><span data-stu-id="158bc-105">Options</span></span>  
 <span data-ttu-id="158bc-106">**入力または出力**</span><span class="sxs-lookup"><span data-stu-id="158bc-106">**Input or Output**</span></span>  
 <span data-ttu-id="158bc-107">出力の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="158bc-107">View the name of the output.</span></span>  
  
 <span data-ttu-id="158bc-108">**列**</span><span class="sxs-lookup"><span data-stu-id="158bc-108">**Column**</span></span>  
 <span data-ttu-id="158bc-109">変換エディターのダイアログ ボックスで選択した出力列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="158bc-109">View the output columns that you selected in the transformation editor dialog box.</span></span>  
  
 <span data-ttu-id="158bc-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="158bc-110">**Error**</span></span>  
 <span data-ttu-id="158bc-111">必要に応じて、エラーが発生した場合に障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="158bc-111">If applicable, specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="158bc-112">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="158bc-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="158bc-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="158bc-113">**Truncation**</span></span>  
 <span data-ttu-id="158bc-114">必要に応じて、切り捨てが発生した場合に障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="158bc-114">If applicable, specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="158bc-115">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="158bc-115">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="158bc-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="158bc-116">**Description**</span></span>  
 <span data-ttu-id="158bc-117">操作の説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="158bc-117">View the description of the operation.</span></span>  
  
 <span data-ttu-id="158bc-118">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="158bc-118">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="158bc-119">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="158bc-119">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="158bc-120">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="158bc-120">**Apply**</span></span>  
 <span data-ttu-id="158bc-121">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="158bc-121">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158bc-122">参照</span><span class="sxs-lookup"><span data-stu-id="158bc-122">See Also</span></span>  
 [<span data-ttu-id="158bc-123">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="158bc-123">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
