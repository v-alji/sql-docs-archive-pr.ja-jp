---
title: '[SAP BW 変換元エディター] ([詳細設定] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c78d40555a30031bf39abda18048fda9c648d01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740195"
---
# <a name="sap-bw-source-editor-advanced-page"></a><span data-ttu-id="e3d78-102">[SAP BW 変換元エディター] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="e3d78-102">SAP BW Source Editor (Advanced Page)</span></span>
  <span data-ttu-id="e3d78-103">文字列の変換規則とタイムアウト期間を指定し、特定の要求 ID の状態をリセットするには、 **[SAP BW 変換元エディター]** の **[詳細設定]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-103">Use the **Advanced** page of the **SAP BW Source Editor** to specify the string conversion rule and the time-out period, and also to reset the status of a particular Request ID.</span></span>  
  
 <span data-ttu-id="e3d78-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元コンポーネントの詳細については、「 [SAP BW Source](sap-bw-source.md)」(SAP BW 変換元) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e3d78-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e3d78-105">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e3d78-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="e3d78-106">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3d78-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e3d78-107">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="e3d78-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="e3d78-108">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="e3d78-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="e3d78-109">**[接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="e3d78-109">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="e3d78-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="e3d78-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="e3d78-111">**[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3d78-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="e3d78-112">**[SAP BW 変換元エディター]** で、 **[詳細設定]** をクリックして **[詳細設定]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="e3d78-112">In the **SAP BW Source Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e3d78-113">オプション</span><span class="sxs-lookup"><span data-stu-id="e3d78-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3d78-114">変換元を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="e3d78-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="e3d78-115">**文字列変換**</span><span class="sxs-lookup"><span data-stu-id="e3d78-115">**String Conversion**</span></span>  
 <span data-ttu-id="e3d78-116">文字列変換に適用するルールを指定します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-116">Specify the rule to apply for string conversion.</span></span>  
  
|<span data-ttu-id="e3d78-117">オプション</span><span class="sxs-lookup"><span data-stu-id="e3d78-117">Option</span></span>|<span data-ttu-id="e3d78-118">説明</span><span class="sxs-lookup"><span data-stu-id="e3d78-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e3d78-119">**自動文字列変換**</span><span class="sxs-lookup"><span data-stu-id="e3d78-119">**Automatic string conversion**</span></span>|<span data-ttu-id="e3d78-120">SAP Netweaver BW システムが Unicode システムの場合に、`nvarchar` にすべての文字列を変換します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-120">Convert all strings to `nvarchar` when the SAP Netweaver BW system is a Unicode system.</span></span> <span data-ttu-id="e3d78-121">それ以外の場合は `varchar` にすべての文字列を変換します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-121">Otherwise, convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="e3d78-122">**文字列を varchar に変換**</span><span class="sxs-lookup"><span data-stu-id="e3d78-122">**Convert strings to varchar**</span></span>|<span data-ttu-id="e3d78-123">`varchar` にすべての文字列を変換します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-123">Convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="e3d78-124">**文字列を nvarchar に変換**</span><span class="sxs-lookup"><span data-stu-id="e3d78-124">**Convert strings to nvarchar**</span></span>|<span data-ttu-id="e3d78-125">`nvarchar` にすべての文字列を変換します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-125">Convert all strings to `nvarchar`.</span></span>|  
  
 <span data-ttu-id="e3d78-126">**タイムアウト (秒)**</span><span class="sxs-lookup"><span data-stu-id="e3d78-126">**Timeout (seconds)**</span></span>  
 <span data-ttu-id="e3d78-127">ソースが待機する最大秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-127">Specify the maximum number of seconds that the source should wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3d78-128">このオプションは、エディターの **[接続マネージャー]** ページの **[実行モード]** の値として **[W - 通知を待機]** を選択した場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="e3d78-128">This option is only valid if you have selected **W - Wait for Notify** as the value of **Execution Mode** on the **Connection Manager** page of the editor.</span></span> <span data-ttu-id="e3d78-129">詳細については、「 [SAP BW ソース エディター ([接続マネージャー] ページ)](sap-bw-source-editor-connection-manager-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3d78-129">For more information, see [SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md).</span></span>  
  
 <span data-ttu-id="e3d78-130">**要求 ID**</span><span class="sxs-lookup"><span data-stu-id="e3d78-130">**Request ID**</span></span>  
 <span data-ttu-id="e3d78-131">**[リセット]** をクリックしたときに状態を "G - Green" にリセットする要求 ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="e3d78-131">Specify the Request ID whose status you want to reset to "G - Green" when you click **Reset**.</span></span>  
  
 <span data-ttu-id="e3d78-132">**リセット**</span><span class="sxs-lookup"><span data-stu-id="e3d78-132">**Reset**</span></span>  
 <span data-ttu-id="e3d78-133">確認後に、指定した要求 ID の状態を "G - Green" リセットできます。</span><span class="sxs-lookup"><span data-stu-id="e3d78-133">Lets you reset the status of the specified Request ID to "G - Green", after prompting you for confirmation.</span></span> <span data-ttu-id="e3d78-134">これは、問題が発生し、SAP Netweaver BW システムが要求に黄色または赤の状態フラグを設定した便利です。</span><span class="sxs-lookup"><span data-stu-id="e3d78-134">This can be useful when a problem has occurred, and the SAP Netweaver BW system has flagged the request with a yellow or red status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d78-135">参照</span><span class="sxs-lookup"><span data-stu-id="e3d78-135">See Also</span></span>  
 <span data-ttu-id="e3d78-136">[SAP BW ソース エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="e3d78-136">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="e3d78-137">[SAP BW ソース エディター ([列] ページ)](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e3d78-137">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e3d78-138">[SAP BW ソース エディター &#40;[エラー出力] ページ&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e3d78-138">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="e3d78-139">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="e3d78-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
