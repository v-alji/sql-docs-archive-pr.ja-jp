---
title: '[SAP BW 変換元エディター] ([エラー出力] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a4ad2d02d3f5ec5c1a786019e18fa01665fdc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712214"
---
# <a name="sap-bw-source-editor-error-output-page"></a><span data-ttu-id="fa96d-102">[SAP BW 変換元エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="fa96d-102">SAP BW Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="fa96d-103">**[SAP BW 変換元エディター]** の **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="fa96d-103">Use the **Error Output** page of the **SAP BW Source Editor** to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="fa96d-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元コンポーネントの詳細については、「 [SAP BW Source](sap-bw-source.md)」(SAP BW 変換元) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fa96d-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fa96d-105">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="fa96d-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="fa96d-106">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa96d-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fa96d-107">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="fa96d-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="fa96d-108">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="fa96d-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="fa96d-109">**[エラー出力] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="fa96d-109">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="fa96d-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa96d-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="fa96d-111">**[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa96d-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="fa96d-112">**[SAP BW 変換元エディター]** で、 **[エラー出力]** をクリックして **[エラー出力]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa96d-112">In the **SAP BW Source Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa96d-113">オプション</span><span class="sxs-lookup"><span data-stu-id="fa96d-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa96d-114">変換元を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="fa96d-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="fa96d-115">**入力または出力**</span><span class="sxs-lookup"><span data-stu-id="fa96d-115">**Input or Output**</span></span>  
 <span data-ttu-id="fa96d-116">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="fa96d-116">View the name of the data source.</span></span>  
  
 <span data-ttu-id="fa96d-117">**列**</span><span class="sxs-lookup"><span data-stu-id="fa96d-117">**Column**</span></span>  
 <span data-ttu-id="fa96d-118">**[SAP BW 変換元エディター]** ダイアログ ボックスの **[列]** ページで選択した外部 (ソース) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="fa96d-118">View the external (source) columns that you selected on the **Columns** page of the **SAP BW Source Editor** dialog box.</span></span> <span data-ttu-id="fa96d-119">このダイアログ ボックスの詳細については、「 [SAP BW 変換元エディター &#40;[列] ページ&#41;](sap-bw-source-editor-columns-page.md)」(SAP BW 変換元) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fa96d-119">For more information about this dialog box, see [SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="fa96d-120">**Error**</span><span class="sxs-lookup"><span data-stu-id="fa96d-120">**Error**</span></span>  
 <span data-ttu-id="fa96d-121">SAP BW 変換元コンポーネントが、エラーが発生した場合に障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fa96d-121">Specify what the SAP BW source component should do when there is an error: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fa96d-122">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="fa96d-122">**Truncation**</span></span>  
 <span data-ttu-id="fa96d-123">SAP BW 変換元コンポーネントが、切り捨てが発生した場合に障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fa96d-123">Specify what the SAP BW source component should do when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fa96d-124">**説明**</span><span class="sxs-lookup"><span data-stu-id="fa96d-124">**Description**</span></span>  
 <span data-ttu-id="fa96d-125">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="fa96d-125">View the description of the error.</span></span>  
  
 <span data-ttu-id="fa96d-126">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="fa96d-126">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="fa96d-127">SAP BW 変換元コンポーネントが、エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fa96d-127">Specify what the SAP BW source component should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fa96d-128">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="fa96d-128">**Apply**</span></span>  
 <span data-ttu-id="fa96d-129">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="fa96d-129">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa96d-130">参照</span><span class="sxs-lookup"><span data-stu-id="fa96d-130">See Also</span></span>  
 <span data-ttu-id="fa96d-131">[SAP BW ソース エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="fa96d-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="fa96d-132">[SAP BW ソース エディター ([列] ページ)](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="fa96d-132">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="fa96d-133">[SAP BW ソース エディター &#40;[詳細設定] ページ&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="fa96d-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="fa96d-134">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="fa96d-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
