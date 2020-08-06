---
title: '[ODBC ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.errorhandling.f1
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a8e169875a26efbe0a7f1ac3d06856b393266eb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718561"
---
# <a name="odbc-source-editor-error-output-page"></a><span data-ttu-id="81566-102">[ODBC ソース エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="81566-102">ODBC Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="81566-103">**[ODBC 入力元エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="81566-103">Use the **Error Output** page of the **ODBC Source Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="81566-104">ODBC 入力元について詳しくは、「 [CDC ソース](data-flow/cdc-source.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="81566-104">To learn more about the ODBC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="81566-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="81566-105">Task List</span></span>  
 <span data-ttu-id="81566-106">**[ODBC 入力元エディター] の [エラー出力] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="81566-106">**To open the ODBC Source Editor Error Output Page**</span></span>  
  
-   <span data-ttu-id="81566-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、ODBC 入力元を含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="81566-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
-   <span data-ttu-id="81566-108">**[データ フロー]** タブで、ODBC 入力元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="81566-108">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
-   <span data-ttu-id="81566-109">**[ODBC 入力元エディター]** で、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81566-109">In the **ODBC Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="81566-110">オプション</span><span class="sxs-lookup"><span data-stu-id="81566-110">Options</span></span>  
  
### <a name="inputoutput"></a><span data-ttu-id="81566-111">[入力または出力]</span><span class="sxs-lookup"><span data-stu-id="81566-111">Input/Output</span></span>  
 <span data-ttu-id="81566-112">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="81566-112">View the name of the data source.</span></span>  
  
### <a name="column"></a><span data-ttu-id="81566-113">列</span><span class="sxs-lookup"><span data-stu-id="81566-113">Column</span></span>  
 <span data-ttu-id="81566-114">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="81566-114">Not used.</span></span>  
  
### <a name="error"></a><span data-ttu-id="81566-115">エラー</span><span class="sxs-lookup"><span data-stu-id="81566-115">Error</span></span>  
 <span data-ttu-id="81566-116">ODBC 入力元でフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="81566-116">Select how the ODBC source should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="truncation"></a><span data-ttu-id="81566-117">切り捨て</span><span class="sxs-lookup"><span data-stu-id="81566-117">Truncation</span></span>  
 <span data-ttu-id="81566-118">ODBC 入力元でフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="81566-118">Select how the ODBC source should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="description"></a><span data-ttu-id="81566-119">説明</span><span class="sxs-lookup"><span data-stu-id="81566-119">Description</span></span>  
 <span data-ttu-id="81566-120">使用しません。</span><span class="sxs-lookup"><span data-stu-id="81566-120">Not used.</span></span>  
  
### <a name="set-this-value-to-selected-cells"></a><span data-ttu-id="81566-121">[選択したセルに設定する値]</span><span class="sxs-lookup"><span data-stu-id="81566-121">Set this value to selected cells</span></span>  
 <span data-ttu-id="81566-122">エラーまたは切り捨てが発生した場合に、選択したすべてのセルを ODBC 入力元でどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="81566-122">Select how the ODBC source handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="apply"></a><span data-ttu-id="81566-123">適用</span><span class="sxs-lookup"><span data-stu-id="81566-123">Apply</span></span>  
 <span data-ttu-id="81566-124">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="81566-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="81566-125">エラー処理オプション</span><span class="sxs-lookup"><span data-stu-id="81566-125">Error Handling Options</span></span>  
 <span data-ttu-id="81566-126">ODBC 入力元でのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="81566-126">You use the following options to configure how the ODBC source handles errors and truncations.</span></span>  
  
### <a name="fail-component"></a><span data-ttu-id="81566-127">エラー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="81566-127">Fail Component</span></span>  
 <span data-ttu-id="81566-128">エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="81566-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="81566-129">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="81566-129">This is the default behavior.</span></span>  
  
### <a name="ignore-failure"></a><span data-ttu-id="81566-130">エラーを無視する</span><span class="sxs-lookup"><span data-stu-id="81566-130">Ignore Failure</span></span>  
 <span data-ttu-id="81566-131">エラーまたは切り捨ては無視されます。</span><span class="sxs-lookup"><span data-stu-id="81566-131">The error or the truncation is ignored.</span></span>  
  
### <a name="redirect-flow"></a><span data-ttu-id="81566-132">[フローのリダイレクト]</span><span class="sxs-lookup"><span data-stu-id="81566-132">Redirect Flow</span></span>  
 <span data-ttu-id="81566-133">エラーまたは切り捨てが ODBC 入力元のエラー出力に送られる原因となった行。</span><span class="sxs-lookup"><span data-stu-id="81566-133">The row that is causing the error or the truncation is directed to the error output of the ODBC source.</span></span> <span data-ttu-id="81566-134">詳しくは、「 [ODBC 入力元](data-flow/odbc-source.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="81566-134">For more information, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81566-135">参照</span><span class="sxs-lookup"><span data-stu-id="81566-135">See Also</span></span>  
 <span data-ttu-id="81566-136">[ODBC ソースエディター &#40;接続マネージャーのページ&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="81566-136">[ODBC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="81566-137">[[ODBC ソース エディター] &#40;[列] ページ&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="81566-137">[ODBC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)</span></span>  
  
  