---
title: '[ADO NET 変換先エディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.erroroutput.f1
ms.assetid: 1a56c3cf-fb6a-416d-a62c-bb19fe441ae5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cfd69d3adec2aa617f5e9d3add35a1a6923804
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641198"
---
# <a name="ado-net-destination-editor-error-output-page"></a><span data-ttu-id="18631-102">[ADO NET 変換先エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="18631-102">ADO NET Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="18631-103">**[ADO NET 変換先エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="18631-103">Use the **Error Output** page of the **ADO NET Destination Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="18631-104">ADO NET 変換先の詳細については、「 [ADO NET Destination](data-flow/ado-net-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18631-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="18631-105">**[エラー出力] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="18631-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="18631-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換先を含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="18631-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="18631-107">**[データ フロー]** タブで、ADO NET 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="18631-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="18631-108">**[ADO NET 変換先エディター]** で、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18631-108">In the **ADO NET Destination Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="18631-109">Options</span><span class="sxs-lookup"><span data-stu-id="18631-109">Options</span></span>  
 <span data-ttu-id="18631-110">**入力または出力**</span><span class="sxs-lookup"><span data-stu-id="18631-110">**Input or Output**</span></span>  
 <span data-ttu-id="18631-111">入力の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="18631-111">View the name of the input.</span></span>  
  
 <span data-ttu-id="18631-112">**列**</span><span class="sxs-lookup"><span data-stu-id="18631-112">**Column**</span></span>  
 <span data-ttu-id="18631-113">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="18631-113">Not used.</span></span>  
  
 <span data-ttu-id="18631-114">**Error**</span><span class="sxs-lookup"><span data-stu-id="18631-114">**Error**</span></span>  
 <span data-ttu-id="18631-115">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="18631-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="18631-116">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="18631-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="18631-117">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="18631-117">**Truncation**</span></span>  
 <span data-ttu-id="18631-118">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="18631-118">Not used.</span></span>  
  
 <span data-ttu-id="18631-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="18631-119">**Description**</span></span>  
 <span data-ttu-id="18631-120">操作の説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="18631-120">View the description of the operation.</span></span>  
  
 <span data-ttu-id="18631-121">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="18631-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="18631-122">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="18631-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="18631-123">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="18631-123">**Apply**</span></span>  
 <span data-ttu-id="18631-124">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="18631-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18631-125">参照</span><span class="sxs-lookup"><span data-stu-id="18631-125">See Also</span></span>  
 <span data-ttu-id="18631-126">[[ADO NET 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="18631-126">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="18631-127">[[ADO NET 変換先エディター] &#40;[マッピング] ページ&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="18631-127">[ADO NET Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md)</span></span>  
  
  
