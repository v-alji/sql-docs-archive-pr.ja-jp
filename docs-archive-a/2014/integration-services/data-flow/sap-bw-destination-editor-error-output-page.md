---
title: '[SAP BW 変換先エディター] ([エラー出力] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ffd58580865a71626252aa2d177530e41156537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712222"
---
# <a name="sap-bw-destination-editor-error-output-page"></a><span data-ttu-id="83c42-102">[SAP BW 変換先エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="83c42-102">SAP BW Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="83c42-103">**[SAP BW 変換先エディター]** の **[エラー出力]** ページを使用すると、エラー処理オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="83c42-103">Use the **Error Output** page of the **SAP BW Destination Editor** to specify error handling options.</span></span>  
  
 <span data-ttu-id="83c42-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換先の詳細については、「 [SAP BW 転送先](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83c42-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="83c42-105">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="83c42-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="83c42-106">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="83c42-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="83c42-107">**[エラー出力] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="83c42-107">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="83c42-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="83c42-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="83c42-109">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="83c42-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="83c42-110">**[SAP BW 変換先エディター]** で、 **[エラー出力]** をクリックして **[エラー出力]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="83c42-110">In the **SAP BW Destination Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="83c42-111">オプション</span><span class="sxs-lookup"><span data-stu-id="83c42-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83c42-112">変換先を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="83c42-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="83c42-113">**入力または出力**</span><span class="sxs-lookup"><span data-stu-id="83c42-113">**Input or Output**</span></span>  
 <span data-ttu-id="83c42-114">入力の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="83c42-114">View the name of the input.</span></span>  
  
 <span data-ttu-id="83c42-115">**列**</span><span class="sxs-lookup"><span data-stu-id="83c42-115">**Column**</span></span>  
 <span data-ttu-id="83c42-116">このオプションは使用されません。</span><span class="sxs-lookup"><span data-stu-id="83c42-116">This option is not used.</span></span>  
  
 <span data-ttu-id="83c42-117">**Error**</span><span class="sxs-lookup"><span data-stu-id="83c42-117">**Error**</span></span>  
 <span data-ttu-id="83c42-118">変換先が、エラーが発生した場合に障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="83c42-118">Specify what the destination should do when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="83c42-119">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="83c42-119">**Truncation**</span></span>  
 <span data-ttu-id="83c42-120">このオプションは使用されません。</span><span class="sxs-lookup"><span data-stu-id="83c42-120">This option is not used.</span></span>  
  
 <span data-ttu-id="83c42-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="83c42-121">**Description**</span></span>  
 <span data-ttu-id="83c42-122">操作の説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="83c42-122">View the description of the operation.</span></span>  
  
 <span data-ttu-id="83c42-123">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="83c42-123">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="83c42-124">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して変換先が障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="83c42-124">Specify what the destination should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="83c42-125">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="83c42-125">**Apply**</span></span>  
 <span data-ttu-id="83c42-126">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="83c42-126">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c42-127">参照</span><span class="sxs-lookup"><span data-stu-id="83c42-127">See Also</span></span>  
 <span data-ttu-id="83c42-128">[SAP BW 変換先エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="83c42-128">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="83c42-129">[SAP BW 変換先エディター &#40;[マッピング] ページ&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="83c42-129">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="83c42-130">[SAP BW 変換先エディター &#40;[詳細設定] ページ&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="83c42-130">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="83c42-131">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="83c42-131">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
