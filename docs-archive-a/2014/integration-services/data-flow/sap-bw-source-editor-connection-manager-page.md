---
title: SAP BW 変換元エディター ([接続マネージャー] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2a6dc531-85ca-43c5-a65f-3ad3f7d537c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c6b1782daf8c00b3b3d3a7d13b5ffa00adeeba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712218"
---
# <a name="sap-bw-source-editor-connection-manager-page"></a><span data-ttu-id="2c189-102">[SAP BW ソース エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="2c189-102">SAP BW Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="2c189-103">**[SAP BW ソース エディター]** の **[接続マネージャー]** ページを使用すると、SAP BW 変換元の SAP BW 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2c189-103">Use the **Connection Manager** page of the **SAP BW Source Editor** to select the SAP BW connection manager for the SAP BW source.</span></span> <span data-ttu-id="2c189-104">このページでは、実行モードと SAP Netweaver BW システムからデータを抽出するためのパラメーターも選択します。</span><span class="sxs-lookup"><span data-stu-id="2c189-104">On this page, you also select the execution mode and the parameters for extracting the data from the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="2c189-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元コンポーネントの詳細については、「 [SAP BW Source](sap-bw-source.md)」(SAP BW 変換元) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c189-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c189-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="2c189-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="2c189-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c189-108">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="2c189-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="2c189-109">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="2c189-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="2c189-110">**[接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="2c189-110">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="2c189-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c189-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="2c189-112">**[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c189-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="2c189-113">**[SAP BW 変換元エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c189-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="2c189-114">静的オプション</span><span class="sxs-lookup"><span data-stu-id="2c189-114">Static Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c189-115">変換元を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-115">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="2c189-116">**SAP BW 接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="2c189-116">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="2c189-117">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2c189-117">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="2c189-118">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="2c189-118">**New**</span></span>  
 <span data-ttu-id="2c189-119">**[SAP BW 接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c189-119">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="2c189-120">このダイアログ ボックスの詳細については、「 [SAP BW 接続マネージャー エディター](../sap-bw-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-120">For more information about this dialog box, see [SAP BW Connection Manager Editor](../sap-bw-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="2c189-121">**OHS 転送先**</span><span class="sxs-lookup"><span data-stu-id="2c189-121">**OHS destination**</span></span>  
 <span data-ttu-id="2c189-122">ソースからデータを抽出するためのオープン ハブ サービス (OHS) 転送先を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c189-122">Select the Open Hub Service (OHS) destination to use to extract data from the source.</span></span>  
  
 <span data-ttu-id="2c189-123">**実行モード**</span><span class="sxs-lookup"><span data-stu-id="2c189-123">**Execution mode**</span></span>  
 <span data-ttu-id="2c189-124">ソースからデータを抽出する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c189-124">Specify the method for extracting data from the source.</span></span>  
  
|<span data-ttu-id="2c189-125">オプション</span><span class="sxs-lookup"><span data-stu-id="2c189-125">Option</span></span>|<span data-ttu-id="2c189-126">説明</span><span class="sxs-lookup"><span data-stu-id="2c189-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2c189-127">**P - プロセス チェーンをトリガー**</span><span class="sxs-lookup"><span data-stu-id="2c189-127">**P - Trigger Process Chain**</span></span>|<span data-ttu-id="2c189-128">プロセス チェーンをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="2c189-128">Trigger a process chain.</span></span> <span data-ttu-id="2c189-129">この場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージが抽出プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="2c189-129">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>|  
|<span data-ttu-id="2c189-130">**W - 通知を待機**</span><span class="sxs-lookup"><span data-stu-id="2c189-130">**W - Wait for Notify**</span></span>|<span data-ttu-id="2c189-131">SAP Netweaver BW システムから、データ抽出の開始する通知を待ちます。</span><span class="sxs-lookup"><span data-stu-id="2c189-131">Wait for notification from the SAP Netweaver BW system to begin extracting the data.</span></span> <span data-ttu-id="2c189-132">この場合、SAP Netweaver BW システムが抽出プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="2c189-132">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>|  
|<span data-ttu-id="2c189-133">**E - 抽出のみ**</span><span class="sxs-lookup"><span data-stu-id="2c189-133">**E - Extract Only**</span></span>|<span data-ttu-id="2c189-134">特定の要求 ID に関連付けられたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="2c189-134">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="2c189-135">この場合、SAP Netweaver BW システムが内部テーブルにデータを既に抽出済みで、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージはデータを読み取るだけです。</span><span class="sxs-lookup"><span data-stu-id="2c189-135">In this case, the SAP Netweaver BW system has already extracted the data into an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>|  
  
 <span data-ttu-id="2c189-136">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="2c189-136">**Preview**</span></span>  
 <span data-ttu-id="2c189-137">結果をプレビューする **[プレビュー]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c189-137">Open the **Preview** dialog box in which you can preview results.</span></span> <span data-ttu-id="2c189-138">詳細については、「 [プレビュー](preview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-138">For more information, see [Preview](preview.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c189-139">**[プレビュー]** オプションは [SAP BW ソース エディター] の **[接続マネージャー]** ページで使用でき、実際にデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="2c189-139">The **Preview** option, that is available on the **Connection Manager** page of the SAP BW Source Editor, actually extracts data.</span></span> <span data-ttu-id="2c189-140">前の抽出以降に変更されたデータのみを抽出するように SAP Netweaver BW を構成している場合、 **[プレビュー]** を選択すると、次の抽出からプレビュー データを除外します。</span><span class="sxs-lookup"><span data-stu-id="2c189-140">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="2c189-141">**[プレビュー]** をクリックすると、 **[要求のログ]** ダイアログ ボックスも開きます。</span><span class="sxs-lookup"><span data-stu-id="2c189-141">When you click **Preview**, you also open the **Request Log** dialog box.</span></span> <span data-ttu-id="2c189-142">サンプル データの SAP Netweaver BW システムに対する要求中にログに記録するイベントを表示するには、このダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c189-142">You can use this dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="2c189-143">詳細については、「 [要求のログ](request-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-143">For more information, see [Request Log](request-log.md).</span></span>  
  
## <a name="execution-mode-dynamic-options"></a><span data-ttu-id="2c189-144">実行モードの動的オプション</span><span class="sxs-lookup"><span data-stu-id="2c189-144">Execution Mode Dynamic Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c189-145">変換元を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-145">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
### <a name="execution-mode--p---trigger-process-chain"></a><span data-ttu-id="2c189-146">実行モードが [P - プロセス チェーンをトリガー] の場合</span><span class="sxs-lookup"><span data-stu-id="2c189-146">Execution Mode = P - Trigger Process Chain</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="2c189-147">RFC 転送先に関するオプション</span><span class="sxs-lookup"><span data-stu-id="2c189-147">RFC Destination Options</span></span>  
 <span data-ttu-id="2c189-148">これらの値は、あらかじめ調べて入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c189-148">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="2c189-149">**[参照]** ボタンを使用して、適切な RFC 転送先を探して選択します。</span><span class="sxs-lookup"><span data-stu-id="2c189-149">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="2c189-150">RFC 転送先を選択すると、これらのオプションに対する適切な値が入力されます。</span><span class="sxs-lookup"><span data-stu-id="2c189-150">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="2c189-151">**ゲートウェイ ホスト**</span><span class="sxs-lookup"><span data-stu-id="2c189-151">**Gateway host**</span></span>  
 <span data-ttu-id="2c189-152">ゲートウェイ ホストのサーバー名または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="2c189-152">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="2c189-153">通常、IP アドレスの名前は、SAP アプリケーション サーバーの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="2c189-153">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="2c189-154">**ゲートウェイ サービス**</span><span class="sxs-lookup"><span data-stu-id="2c189-154">**Gateway service**</span></span>  
 <span data-ttu-id="2c189-155">`sapgwNN` という形式でゲートウェイ サービスの名前を入力します。`NN` はシステム番号です。</span><span class="sxs-lookup"><span data-stu-id="2c189-155">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="2c189-156">**プログラム ID**</span><span class="sxs-lookup"><span data-stu-id="2c189-156">**Program ID**</span></span>  
 <span data-ttu-id="2c189-157">RFC 転送先に関連付けられているプログラム ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="2c189-157">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="2c189-158">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="2c189-158">**Look up**</span></span>  
 <span data-ttu-id="2c189-159">**[RFC 転送先の参照]** ダイアログ ボックスを使用して、RFC 転送先を参照します。</span><span class="sxs-lookup"><span data-stu-id="2c189-159">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="2c189-160">このダイアログ ボックスの詳細については、「 [RFC 転送先の参照](look-up-rfc-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-160">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
#### <a name="process-chain-options"></a><span data-ttu-id="2c189-161">プロセス チェーンに関するオプション</span><span class="sxs-lookup"><span data-stu-id="2c189-161">Process Chain Options</span></span>  
 <span data-ttu-id="2c189-162">これらの値は、あらかじめ調べて入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c189-162">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="2c189-163">**[参照]** ボタンを使用して、適切なプロセス チェーンを探して選択します。</span><span class="sxs-lookup"><span data-stu-id="2c189-163">Use the **Look up** button to find and select the appropriate process chain.</span></span> <span data-ttu-id="2c189-164">プロセス チェーンを選択すると、これらのオプションに対する適切な値が入力されます。</span><span class="sxs-lookup"><span data-stu-id="2c189-164">After you select a process chain, the component enters the appropriate value for the option.</span></span>  
  
 <span data-ttu-id="2c189-165">**プロセス チェーン**</span><span class="sxs-lookup"><span data-stu-id="2c189-165">**Process chain**</span></span>  
 <span data-ttu-id="2c189-166">ソースがトリガーするプロセス チェーンの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2c189-166">Enter the name of the process chain to be triggered by the source.</span></span>  
  
 <span data-ttu-id="2c189-167">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="2c189-167">**Look up**</span></span>  
 <span data-ttu-id="2c189-168">**[プロセス チェーンの参照]** ダイアログ ボックスを使用して、プロセス チェーンを参照します。</span><span class="sxs-lookup"><span data-stu-id="2c189-168">Look up the process chain by using the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="2c189-169">このダイアログ ボックスの詳細については、「 [プロセス チェーンの参照](look-up-process-chain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-169">For more information about this dialog box, see [Look Up Process Chain](look-up-process-chain.md).</span></span>  
  
### <a name="execution-mode--w---wait-for-notify"></a><span data-ttu-id="2c189-170">実行モードが [W - 通知を待機] の場合</span><span class="sxs-lookup"><span data-stu-id="2c189-170">Execution Mode = W - Wait for Notify</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="2c189-171">RFC 転送先に関するオプション</span><span class="sxs-lookup"><span data-stu-id="2c189-171">RFC Destination Options</span></span>  
 <span data-ttu-id="2c189-172">これらの値は、あらかじめ調べて入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c189-172">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="2c189-173">**[参照]** ボタンを使用して、適切な RFC 転送先を探して選択します。</span><span class="sxs-lookup"><span data-stu-id="2c189-173">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="2c189-174">RFC 転送先を選択すると、これらのオプションに対する適切な値が入力されます。</span><span class="sxs-lookup"><span data-stu-id="2c189-174">After you select an RFC destination, the component enters the appropriate values for the options.</span></span>  
  
 <span data-ttu-id="2c189-175">**ゲートウェイ ホスト**</span><span class="sxs-lookup"><span data-stu-id="2c189-175">**Gateway host**</span></span>  
 <span data-ttu-id="2c189-176">ゲートウェイ ホストのサーバー名または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="2c189-176">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="2c189-177">通常、IP アドレスの名前は、SAP アプリケーション サーバーの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="2c189-177">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="2c189-178">**ゲートウェイ サービス**</span><span class="sxs-lookup"><span data-stu-id="2c189-178">**Gateway service**</span></span>  
 <span data-ttu-id="2c189-179">`sapgwNN` という形式でゲートウェイ サービスの名前を入力します。`NN` はシステム番号です。</span><span class="sxs-lookup"><span data-stu-id="2c189-179">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="2c189-180">**プログラム ID**</span><span class="sxs-lookup"><span data-stu-id="2c189-180">**Program ID**</span></span>  
 <span data-ttu-id="2c189-181">RFC 転送先に関連付けられているプログラム ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="2c189-181">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="2c189-182">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="2c189-182">**Look up**</span></span>  
 <span data-ttu-id="2c189-183">**[RFC 転送先の参照]** ダイアログ ボックスを使用して、RFC 転送先を参照します。</span><span class="sxs-lookup"><span data-stu-id="2c189-183">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="2c189-184">このダイアログ ボックスの詳細については、「 [RFC 転送先の参照](look-up-rfc-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c189-184">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="execution-mode--e---extract-only"></a><span data-ttu-id="2c189-185">実行モードが [E - 抽出のみ] の場合</span><span class="sxs-lookup"><span data-stu-id="2c189-185">Execution Mode = E - Extract Only</span></span>  
 <span data-ttu-id="2c189-186">**要求 ID**</span><span class="sxs-lookup"><span data-stu-id="2c189-186">**Request ID**</span></span>  
 <span data-ttu-id="2c189-187">抽出に関連付けられている要求 ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="2c189-187">Enter the Request ID that is associated with the extraction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c189-188">参照</span><span class="sxs-lookup"><span data-stu-id="2c189-188">See Also</span></span>  
 <span data-ttu-id="2c189-189">[SAP BW ソース エディター ([列] ページ)](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="2c189-189">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="2c189-190">[SAP BW ソース エディター &#40;[エラー出力] ページ&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="2c189-190">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="2c189-191">[SAP BW ソース エディター &#40;[詳細設定] ページ&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="2c189-191">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="2c189-192">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="2c189-192">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
