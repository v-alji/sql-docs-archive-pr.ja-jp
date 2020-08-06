---
title: '[CDC ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b39532304fddfa90fabe8cafe2a6caf5b1fb5c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644590"
---
# <a name="cdc-source-editor-error-output-page"></a><span data-ttu-id="75fa5-102">[CDC ソース エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="75fa5-102">CDC Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="75fa5-103">**[CDC ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="75fa5-103">Use the **Error Output** page of the **CDC Source Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="75fa5-104">CDC ソースの詳細については、「 [CDC Source](data-flow/cdc-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75fa5-104">To learn more about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="75fa5-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="75fa5-105">Task List</span></span>  
 <span data-ttu-id="75fa5-106">**[CDC ソース エディター] の [エラー出力] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="75fa5-106">**To open the CDC Source Editor Error Output Page**</span></span>  
  
1.  <span data-ttu-id="75fa5-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、CDC ソースを含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="75fa5-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="75fa5-108">**[データ フロー]** タブで、CDC ソースをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="75fa5-108">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="75fa5-109">**[CDC ソース エディター]** で、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75fa5-109">In the **CDC Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="75fa5-110">オプション</span><span class="sxs-lookup"><span data-stu-id="75fa5-110">Options</span></span>  
 <span data-ttu-id="75fa5-111">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="75fa5-111">**Input/Output**</span></span>  
 <span data-ttu-id="75fa5-112">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-112">View the name of the data source.</span></span>  
  
 <span data-ttu-id="75fa5-113">**列**</span><span class="sxs-lookup"><span data-stu-id="75fa5-113">**Column**</span></span>  
 <span data-ttu-id="75fa5-114">**[CDC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (ソース) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-114">View the external (source) columns that you selected on the **Connection Manager** page of the **CDC Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="75fa5-115">**Error**</span><span class="sxs-lookup"><span data-stu-id="75fa5-115">**Error**</span></span>  
 <span data-ttu-id="75fa5-116">CDC ソースでフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-116">Select how the CDC source should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="75fa5-117">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="75fa5-117">**Truncation**</span></span>  
 <span data-ttu-id="75fa5-118">CDC ソースでフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-118">Select how the CDC source should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="75fa5-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="75fa5-119">**Description**</span></span>  
 <span data-ttu-id="75fa5-120">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="75fa5-120">Not used.</span></span>  
  
 <span data-ttu-id="75fa5-121">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="75fa5-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="75fa5-122">エラーまたは切り捨てが発生した場合に、選択したすべてのセルを CDC ソースでどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-122">Select how the CDC source handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="75fa5-123">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="75fa5-123">**Apply**</span></span>  
 <span data-ttu-id="75fa5-124">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="75fa5-125">エラー処理オプション</span><span class="sxs-lookup"><span data-stu-id="75fa5-125">Error Handling Options</span></span>  
 <span data-ttu-id="75fa5-126">CDC ソースでのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-126">You use the following options to configure how the CDC source handles errors and truncations.</span></span>  
  
 <span data-ttu-id="75fa5-127">**エラー コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="75fa5-127">**Fail Component**</span></span>  
 <span data-ttu-id="75fa5-128">エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="75fa5-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="75fa5-129">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="75fa5-129">This is the default behavior.</span></span>  
  
 <span data-ttu-id="75fa5-130">**エラーを無視する**</span><span class="sxs-lookup"><span data-stu-id="75fa5-130">**Ignore Failure**</span></span>  
 <span data-ttu-id="75fa5-131">エラーまたは切り捨ては無視され、データ行は CDC ソース出力に送られます。</span><span class="sxs-lookup"><span data-stu-id="75fa5-131">The error or the truncation is ignored and the data row is directed to the CDC source output.</span></span>  
  
 <span data-ttu-id="75fa5-132">**[フローのリダイレクト]**</span><span class="sxs-lookup"><span data-stu-id="75fa5-132">**Redirect Flow**</span></span>  
 <span data-ttu-id="75fa5-133">エラーまたは切り捨てのデータ行は、CDC ソースのエラー出力に送られます。</span><span class="sxs-lookup"><span data-stu-id="75fa5-133">The error or the truncation data row is directed to the error output of the CDC source.</span></span> <span data-ttu-id="75fa5-134">この場合は、CDC ソースのエラー処理が使用されます。</span><span class="sxs-lookup"><span data-stu-id="75fa5-134">In this case the CDC source error handling is used.</span></span> <span data-ttu-id="75fa5-135">詳細については、「 [CDC ソース](data-flow/cdc-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75fa5-135">For more information, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fa5-136">参照</span><span class="sxs-lookup"><span data-stu-id="75fa5-136">See Also</span></span>  
 <span data-ttu-id="75fa5-137">[CDC ソース エディター &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="75fa5-137">[CDC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="75fa5-138">[[CDC ソース エディター] &#40;[列] ページ&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="75fa5-138">[CDC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)</span></span>  
  
  
