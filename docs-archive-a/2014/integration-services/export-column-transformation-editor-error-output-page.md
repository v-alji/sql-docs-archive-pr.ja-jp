---
title: '[列エクスポート変換エディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.errorhandling.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: 260be463-01a9-460c-9c98-e5265cb2b1e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04a9c277bb4aaa28933d443bd12e6c2b39ed844e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743390"
---
# <a name="export-column-transformation-editor-error-output-page"></a><span data-ttu-id="a5a36-102">[列エクスポート変換エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="a5a36-102">Export Column Transformation Editor (Error Output Page)</span></span>
  <span data-ttu-id="a5a36-103">**[列エクスポート変換エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラーをどのように処理するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a5a36-103">Use the **Error Output** page of the **Export Column Transformation Editor** dialog box to specify how to handle errors.</span></span>  
  
 <span data-ttu-id="a5a36-104">列エクスポート変換の詳細については、「 [Export Column Transformation](data-flow/transformations/export-column-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5a36-104">To learn more about the Export Column transformation, see [Export Column Transformation](data-flow/transformations/export-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a5a36-105">Options</span><span class="sxs-lookup"><span data-stu-id="a5a36-105">Options</span></span>  
 <span data-ttu-id="a5a36-106">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="a5a36-106">**Input/Output**</span></span>  
 <span data-ttu-id="a5a36-107">出力の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a5a36-107">View the name of the output.</span></span> <span data-ttu-id="a5a36-108">名前をクリックすると、ビューを展開して列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a5a36-108">Click the name to expand the view to include columns.</span></span>  
  
 <span data-ttu-id="a5a36-109">**列**</span><span class="sxs-lookup"><span data-stu-id="a5a36-109">**Column**</span></span>  
 <span data-ttu-id="a5a36-110">**[列エクスポート変換エディター]** ダイアログ ボックスの **[列]** ページで選択された出力列を表示します。</span><span class="sxs-lookup"><span data-stu-id="a5a36-110">View the output columns that you selected on the **Columns** page of the **Export Column Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="a5a36-111">**エラー**</span><span class="sxs-lookup"><span data-stu-id="a5a36-111">**Error**</span></span>  
 <span data-ttu-id="a5a36-112">エラーが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="a5a36-112">Specify what you want to happen if an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a5a36-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="a5a36-113">**Truncation**</span></span>  
 <span data-ttu-id="a5a36-114">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="a5a36-114">Specify what you want to happen if a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a5a36-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="a5a36-115">**Description**</span></span>  
 <span data-ttu-id="a5a36-116">操作の説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="a5a36-116">View the description of the operation.</span></span>  
  
 <span data-ttu-id="a5a36-117">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="a5a36-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="a5a36-118">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a5a36-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a5a36-119">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="a5a36-119">**Apply**</span></span>  
 <span data-ttu-id="a5a36-120">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="a5a36-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a36-121">参照</span><span class="sxs-lookup"><span data-stu-id="a5a36-121">See Also</span></span>  
 <span data-ttu-id="a5a36-122">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a5a36-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a5a36-123">[列エクスポート変換エディター ([列] ページ)](../../2014/integration-services/export-column-transformation-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="a5a36-123">[Export Column Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/export-column-transformation-editor-columns-page.md)</span></span>  
  
  
