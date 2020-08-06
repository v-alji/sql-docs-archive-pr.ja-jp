---
title: '[OData ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.erroroutput.f1
ms.assetid: 9a81e2ce-aee6-4c4c-8495-6501d715aca2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c5a4bf7a96af872f2e12665a1f4a071e0537e4c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640126"
---
# <a name="odata-source-editor-error-output-page"></a><span data-ttu-id="343dc-102">[OData ソース エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="343dc-102">OData Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="343dc-103">**[OData ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="343dc-103">Use the **Error Output** page of the **OData Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="343dc-104">Options</span><span class="sxs-lookup"><span data-stu-id="343dc-104">Options</span></span>  
 <span data-ttu-id="343dc-105">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="343dc-105">**Input/Output**</span></span>  
 <span data-ttu-id="343dc-106">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="343dc-106">View the name of the data source.</span></span>  
  
 <span data-ttu-id="343dc-107">**列**</span><span class="sxs-lookup"><span data-stu-id="343dc-107">**Column**</span></span>  
 <span data-ttu-id="343dc-108">**[ODBC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択されている外部 (変換元) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="343dc-108">View the external (source) columns that you selected on the **Connection Manager** page of the **OData Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="343dc-109">**Error**</span><span class="sxs-lookup"><span data-stu-id="343dc-109">**Error**</span></span>  
 <span data-ttu-id="343dc-110">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="343dc-110">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="343dc-111">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="343dc-111">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="343dc-112">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="343dc-112">**Truncation**</span></span>  
 <span data-ttu-id="343dc-113">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="343dc-113">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="343dc-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="343dc-114">**Description**</span></span>  
 <span data-ttu-id="343dc-115">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="343dc-115">View the description of the error.</span></span>  
  
 <span data-ttu-id="343dc-116">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="343dc-116">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="343dc-117">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="343dc-117">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="343dc-118">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="343dc-118">**Apply**</span></span>  
 <span data-ttu-id="343dc-119">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="343dc-119">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343dc-120">参照</span><span class="sxs-lookup"><span data-stu-id="343dc-120">See Also</span></span>  
 <span data-ttu-id="343dc-121">[OData ソースエディター &#40;接続ページ&#41;](../../2014/integration-services/odata-source-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="343dc-121">[OData Source Editor &#40;Connection Page&#41;](../../2014/integration-services/odata-source-editor-connection-page.md) </span></span>  
 <span data-ttu-id="343dc-122">[OData ソースエディター &#40;列のページ&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="343dc-122">[OData Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="343dc-123">[OData ソース](data-flow/odata-source.md) </span><span class="sxs-lookup"><span data-stu-id="343dc-123">[OData Source](data-flow/odata-source.md) </span></span>  
 [<span data-ttu-id="343dc-124">OData 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="343dc-124">OData Connection Manager</span></span>](connection-manager/odata-connection-manager.md)  
  
  
