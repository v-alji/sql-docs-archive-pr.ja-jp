---
title: '[ODBC 変換先エディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.errorhandling.f1
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 475a2e00d67b221ddf05fdd273317fbab5248cd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718579"
---
# <a name="odbc-destination-editor-error-output-page"></a><span data-ttu-id="7cb18-102">ODBC 変換先エディター ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="7cb18-102">ODBC Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="7cb18-103">**[ODBC 入力先エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7cb18-103">Use the **Error Output** page of the **ODBC Destination Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="7cb18-104">ODBC 入力先の詳細については、「 [ODBC Destination](data-flow/odbc-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cb18-104">To learn more about the ODBC destination, see [ODBC Destination](data-flow/odbc-destination.md).</span></span>  
  
 <span data-ttu-id="7cb18-105">**[ODBC 入力先エディター] の [エラー出力] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="7cb18-105">**To open the ODBC Destination Editor Error Output Page**</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="7cb18-106">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="7cb18-106">Task List</span></span>  
  
-   <span data-ttu-id="7cb18-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、ODBC 入力先を含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="7cb18-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC destination.</span></span>  
  
-   <span data-ttu-id="7cb18-108">**[データ フロー]** タブで、ODBC 入力先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cb18-108">On the **Data Flow** tab, double-click the ODBC destination.</span></span>  
  
-   <span data-ttu-id="7cb18-109">**[ODBC 入力先エディター]** で、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cb18-109">In the **ODBC Destination Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7cb18-110">オプション</span><span class="sxs-lookup"><span data-stu-id="7cb18-110">Options</span></span>  
  
### <a name="inputoutput"></a><span data-ttu-id="7cb18-111">[入力または出力]</span><span class="sxs-lookup"><span data-stu-id="7cb18-111">Input/Output</span></span>  
 <span data-ttu-id="7cb18-112">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-112">View the name of the data source.</span></span>  
  
### <a name="column"></a><span data-ttu-id="7cb18-113">列</span><span class="sxs-lookup"><span data-stu-id="7cb18-113">Column</span></span>  
 <span data-ttu-id="7cb18-114">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="7cb18-114">Not used.</span></span>  
  
### <a name="error"></a><span data-ttu-id="7cb18-115">エラー</span><span class="sxs-lookup"><span data-stu-id="7cb18-115">Error</span></span>  
 <span data-ttu-id="7cb18-116">ODBC 入力先でフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-116">Select how the ODBC destination should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="truncation"></a><span data-ttu-id="7cb18-117">切り捨て</span><span class="sxs-lookup"><span data-stu-id="7cb18-117">Truncation</span></span>  
 <span data-ttu-id="7cb18-118">ODBC 入力先でフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-118">Select how the ODBC destination should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="description"></a><span data-ttu-id="7cb18-119">説明</span><span class="sxs-lookup"><span data-stu-id="7cb18-119">Description</span></span>  
 <span data-ttu-id="7cb18-120">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-120">View a description of the error.</span></span>  
  
### <a name="set-this-value-to-selected-cells"></a><span data-ttu-id="7cb18-121">[選択したセルに設定する値]</span><span class="sxs-lookup"><span data-stu-id="7cb18-121">Set this value to selected cells</span></span>  
 <span data-ttu-id="7cb18-122">エラーまたは切り捨てが発生した場合に、選択したすべてのセルを ODBC 入力先でどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-122">Select how the ODBC destination handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="apply"></a><span data-ttu-id="7cb18-123">適用</span><span class="sxs-lookup"><span data-stu-id="7cb18-123">Apply</span></span>  
 <span data-ttu-id="7cb18-124">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="7cb18-125">エラー処理オプション</span><span class="sxs-lookup"><span data-stu-id="7cb18-125">Error Handling Options</span></span>  
 <span data-ttu-id="7cb18-126">ODBC 入力先でのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-126">You use the following options to configure how the ODBC destination handles errors and truncations.</span></span>  
  
### <a name="fail-component"></a><span data-ttu-id="7cb18-127">エラー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7cb18-127">Fail Component</span></span>  
 <span data-ttu-id="7cb18-128">エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="7cb18-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="7cb18-129">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="7cb18-129">This is the default behavior.</span></span>  
  
### <a name="ignore-failure"></a><span data-ttu-id="7cb18-130">エラーを無視する</span><span class="sxs-lookup"><span data-stu-id="7cb18-130">Ignore Failure</span></span>  
 <span data-ttu-id="7cb18-131">エラーまたは切り捨ては無視されます。</span><span class="sxs-lookup"><span data-stu-id="7cb18-131">The error or the truncation is ignored.</span></span>  
  
### <a name="redirect-flow"></a><span data-ttu-id="7cb18-132">[フローのリダイレクト]</span><span class="sxs-lookup"><span data-stu-id="7cb18-132">Redirect Flow</span></span>  
 <span data-ttu-id="7cb18-133">エラーまたは切り捨てが ODBC 入力先のエラー出力に送られる原因となった行。</span><span class="sxs-lookup"><span data-stu-id="7cb18-133">The row that is causing the error or the truncation is directed to the error output of the ODBC destination.</span></span> <span data-ttu-id="7cb18-134">詳細については、「ODBC 入力先」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cb18-134">For more information, see ODBC Destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb18-135">参照</span><span class="sxs-lookup"><span data-stu-id="7cb18-135">See Also</span></span>  
 <span data-ttu-id="7cb18-136">[ODBC 変換先エディター &#40;接続マネージャーページ&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="7cb18-136">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="7cb18-137">[ODBC 変換先エディター &#40;[マッピング] ページ&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="7cb18-137">[ODBC Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md)</span></span>  
  
  
