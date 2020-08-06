---
title: '[要求のログ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 024012878ae94c5ba6276648e289e6e6f7c93d7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633915"
---
# <a name="request-log"></a><span data-ttu-id="3c3fd-102">[要求のログ]</span><span class="sxs-lookup"><span data-stu-id="3c3fd-102">Request Log</span></span>
  <span data-ttu-id="3c3fd-103">サンプル データの SAP Netweaver BW システムに対する要求中にログに記録されたイベントを表示するには、 **[要求のログ]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-103">Use the **Request Log** dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="3c3fd-104">この情報は、SAP BW 変換元の構成をトラブルシューティングする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-104">This information can be useful if you have to troubleshoot your configuration of the SAP BW source.</span></span>  
  
 <span data-ttu-id="3c3fd-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元コンポーネントの詳細については、「 [SAP BW Source](sap-bw-source.md)」(SAP BW 変換元) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c3fd-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="3c3fd-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c3fd-108">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="3c3fd-109">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="3c3fd-110">**[要求のログ] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="3c3fd-110">**To open the Request Log dialog box**</span></span>  
  
1.  <span data-ttu-id="3c3fd-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="3c3fd-112">**[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="3c3fd-113">**[SAP BW 変換元エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="3c3fd-114">SAP BW 変換元を構成した後、 **[要求のログ]** ダイアログ ボックスでイベントをプレビューするには **[プレビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-114">After you configure the SAP BW source, click **Preview** to preview the events in the **Request Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c3fd-115">**[プレビュー]** をクリックすると、 **[プレビュー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-115">Clicking **Preview** also opens the **Preview** dialog box.</span></span> <span data-ttu-id="3c3fd-116">このダイアログ ボックスの詳細については、「 [プレビュー](preview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-116">For more information about this dialog box, see [Preview](preview.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c3fd-117">オプション</span><span class="sxs-lookup"><span data-stu-id="3c3fd-117">Options</span></span>  
 <span data-ttu-id="3c3fd-118">**Time**</span><span class="sxs-lookup"><span data-stu-id="3c3fd-118">**Time**</span></span>  
 <span data-ttu-id="3c3fd-119">イベントが記録された時刻を表示します。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-119">Displays the time that the event that was logged.</span></span>  
  
 <span data-ttu-id="3c3fd-120">**Type**</span><span class="sxs-lookup"><span data-stu-id="3c3fd-120">**Type**</span></span>  
 <span data-ttu-id="3c3fd-121">記録されたイベントの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-121">Displays the type of the event that was logged.</span></span> <span data-ttu-id="3c3fd-122">次の表は、使用可能なイベントの種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-122">The following table lists the possible event types.</span></span>  
  
|<span data-ttu-id="3c3fd-123">値</span><span class="sxs-lookup"><span data-stu-id="3c3fd-123">Value</span></span>|<span data-ttu-id="3c3fd-124">説明</span><span class="sxs-lookup"><span data-stu-id="3c3fd-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3c3fd-125">S</span><span class="sxs-lookup"><span data-stu-id="3c3fd-125">S</span></span>|<span data-ttu-id="3c3fd-126">成功メッセージ</span><span class="sxs-lookup"><span data-stu-id="3c3fd-126">Success message.</span></span>|  
|<span data-ttu-id="3c3fd-127">E</span><span class="sxs-lookup"><span data-stu-id="3c3fd-127">E</span></span>|<span data-ttu-id="3c3fd-128">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="3c3fd-128">Error message</span></span>|  
|<span data-ttu-id="3c3fd-129">W</span><span class="sxs-lookup"><span data-stu-id="3c3fd-129">W</span></span>|<span data-ttu-id="3c3fd-130">警告メッセージ。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-130">Warning message.</span></span>|  
|<span data-ttu-id="3c3fd-131">I</span><span class="sxs-lookup"><span data-stu-id="3c3fd-131">I</span></span>|<span data-ttu-id="3c3fd-132">情報メッセージです。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-132">Informational message.</span></span>|  
|<span data-ttu-id="3c3fd-133">A</span><span class="sxs-lookup"><span data-stu-id="3c3fd-133">A</span></span>|<span data-ttu-id="3c3fd-134">操作が中止されました。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-134">The operation was aborted.</span></span>|  
  
 <span data-ttu-id="3c3fd-135">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="3c3fd-135">**Message**</span></span>  
 <span data-ttu-id="3c3fd-136">記録されたイベントに関連付けられたメッセージ テキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="3c3fd-136">Displays the message text that is associated with the logged event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3fd-137">参照</span><span class="sxs-lookup"><span data-stu-id="3c3fd-137">See Also</span></span>  
 <span data-ttu-id="3c3fd-138">[SAP BW ソース エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="3c3fd-138">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="3c3fd-139">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="3c3fd-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
