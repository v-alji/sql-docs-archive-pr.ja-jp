---
title: SAP BW 変換先エディター ([接続マネージャー] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd628f1a0fec09490e0d3720610d1232882ed92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712230"
---
# <a name="sap-bw-destination-editor-connection-manager-page"></a><span data-ttu-id="24628-102">[SAP BW 変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="24628-102">SAP BW Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="24628-103">**[SAP BW 変換先エディター]** の **[接続マネージャー]** ページを使用すると、SAP BW 変換先が使用する SAP BW 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="24628-103">Use the **Connection Manager** page of the **SAP BW Destination Editor** to select the SAP BW connection manager that the SAP BW destination will use.</span></span> <span data-ttu-id="24628-104">このページでは、SAP Netweaver BW システムにデータを読み込むためのパラメーターも選択します。</span><span class="sxs-lookup"><span data-stu-id="24628-104">On this page, you also select the parameters for loading the data into the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="24628-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換先の詳細については、「 [SAP BW 転送先](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-105">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="24628-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="24628-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="24628-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="24628-108">**[接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="24628-108">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="24628-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="24628-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="24628-110">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="24628-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="24628-111">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="24628-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="24628-112">オプション</span><span class="sxs-lookup"><span data-stu-id="24628-112">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24628-113">変換先を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="24628-113">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="24628-114">**SAP BW 接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="24628-114">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="24628-115">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="24628-115">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="24628-116">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="24628-116">**New**</span></span>  
 <span data-ttu-id="24628-117">**[SAP BW 接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="24628-117">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="24628-118">**テスト読み込み**</span><span class="sxs-lookup"><span data-stu-id="24628-118">**Test Load**</span></span>  
 <span data-ttu-id="24628-119">選択した設定とゼロ行を読み込む設定を使用して、読み込みプロセスのテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="24628-119">Perform a test of the loading process that uses the settings that you have selected and loads zero rows.</span></span>  
  
### <a name="infopackageinfosource-options"></a><span data-ttu-id="24628-120">インフォパッケージ/インフォソースのオプション</span><span class="sxs-lookup"><span data-stu-id="24628-120">InfoPackage/InfoSource Options</span></span>  
 <span data-ttu-id="24628-121">これらの値は、あらかじめ調べて入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="24628-121">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="24628-122">**[参照]** ボタンを使用して、適切なインフォパッケージを探して選択します。</span><span class="sxs-lookup"><span data-stu-id="24628-122">Use the **Look up** button to find and select the appropriate InfoPackage.</span></span> <span data-ttu-id="24628-123">インフォパッケージを選択すると、これらのオプションに対する適切な値が入力されます。</span><span class="sxs-lookup"><span data-stu-id="24628-123">After you select an InfoPackage, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="24628-124">**インフォパッケージ**</span><span class="sxs-lookup"><span data-stu-id="24628-124">**InfoPackage**</span></span>  
 <span data-ttu-id="24628-125">インフォパッケージの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="24628-125">Enter the name of the InfoPackage.</span></span>  
  
 <span data-ttu-id="24628-126">**インフォソース**</span><span class="sxs-lookup"><span data-stu-id="24628-126">**InfoSource**</span></span>  
 <span data-ttu-id="24628-127">インフォソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="24628-127">Enter the name of the InfoSource.</span></span>  
  
 <span data-ttu-id="24628-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="24628-128">**Type**</span></span>  
 <span data-ttu-id="24628-129">インフォソースの種類を識別する 1 文字を入力します。</span><span class="sxs-lookup"><span data-stu-id="24628-129">Enter the single-character that identifies the type of the InfoSource.</span></span> <span data-ttu-id="24628-130">指定できる 1 文字の値の一覧を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="24628-130">The following table lists the acceptable single-character values.</span></span>  
  
|<span data-ttu-id="24628-131">値</span><span class="sxs-lookup"><span data-stu-id="24628-131">Value</span></span>|<span data-ttu-id="24628-132">説明</span><span class="sxs-lookup"><span data-stu-id="24628-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24628-133">**D**</span><span class="sxs-lookup"><span data-stu-id="24628-133">**D**</span></span>|<span data-ttu-id="24628-134">トランザクション データ</span><span class="sxs-lookup"><span data-stu-id="24628-134">Transaction data</span></span>|  
|<span data-ttu-id="24628-135">**M**</span><span class="sxs-lookup"><span data-stu-id="24628-135">**M**</span></span>|<span data-ttu-id="24628-136">マスター データ</span><span class="sxs-lookup"><span data-stu-id="24628-136">Master data</span></span>|  
|<span data-ttu-id="24628-137">**T**</span><span class="sxs-lookup"><span data-stu-id="24628-137">**T**</span></span>|<span data-ttu-id="24628-138">テキスト</span><span class="sxs-lookup"><span data-stu-id="24628-138">Texts</span></span>|  
|<span data-ttu-id="24628-139">**H**</span><span class="sxs-lookup"><span data-stu-id="24628-139">**H**</span></span>|<span data-ttu-id="24628-140">Hierarchy データ</span><span class="sxs-lookup"><span data-stu-id="24628-140">Hierarchy data</span></span>|  
  
 <span data-ttu-id="24628-141">**論理システム**</span><span class="sxs-lookup"><span data-stu-id="24628-141">**Logical system**</span></span>  
 <span data-ttu-id="24628-142">インフォパッケージに関連付けられている論理システムの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="24628-142">Enter the name of the logical system that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="24628-143">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="24628-143">**Look up**</span></span>  
 <span data-ttu-id="24628-144">**[インフォパッケージの参照]** ダイアログ ボックスを使用して、インフォパッケージを参照します。</span><span class="sxs-lookup"><span data-stu-id="24628-144">Look up the InfoPackage by using the **Look Up InfoPackage** dialog box.</span></span> <span data-ttu-id="24628-145">このダイアログ ボックスの詳細については、「 [インフォパッケージの参照](look-up-infopackage.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-145">For more information about this dialog box, see [Look Up InfoPackage](look-up-infopackage.md).</span></span>  
  
### <a name="rfc-destination-options"></a><span data-ttu-id="24628-146">RFC 転送先に関するオプション</span><span class="sxs-lookup"><span data-stu-id="24628-146">RFC Destination Options</span></span>  
 <span data-ttu-id="24628-147">これらの値は、あらかじめ調べて入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="24628-147">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="24628-148">**[参照]** ボタンを使用して、適切な RFC 転送先を探して選択します。</span><span class="sxs-lookup"><span data-stu-id="24628-148">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="24628-149">RFC 転送先を選択すると、これらのオプションに対する適切な値が入力されます。</span><span class="sxs-lookup"><span data-stu-id="24628-149">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="24628-150">**ゲートウェイ ホスト**</span><span class="sxs-lookup"><span data-stu-id="24628-150">**Gateway host**</span></span>  
 <span data-ttu-id="24628-151">ゲートウェイ ホストのサーバー名または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="24628-151">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="24628-152">通常、IP アドレスの名前は、SAP アプリケーション サーバーの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="24628-152">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="24628-153">**ゲートウェイ サービス**</span><span class="sxs-lookup"><span data-stu-id="24628-153">**Gateway service**</span></span>  
 <span data-ttu-id="24628-154">`sapgwNN` という形式でゲートウェイ サービスの名前を入力します。`NN` はシステム番号です。</span><span class="sxs-lookup"><span data-stu-id="24628-154">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="24628-155">**プログラム ID**</span><span class="sxs-lookup"><span data-stu-id="24628-155">**Program ID**</span></span>  
 <span data-ttu-id="24628-156">RFC 転送先に関連付けられているプログラム ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="24628-156">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="24628-157">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="24628-157">**Look up**</span></span>  
 <span data-ttu-id="24628-158">**[RFC 転送先の参照]** ダイアログ ボックスを使用して、RFC 転送先を参照します。</span><span class="sxs-lookup"><span data-stu-id="24628-158">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="24628-159">このダイアログ ボックスの詳細については、「 [RFC 転送先の参照](look-up-rfc-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-159">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="create-sap-bw-objects-options"></a><span data-ttu-id="24628-160">SAP BW オブジェクトの作成のオプション</span><span class="sxs-lookup"><span data-stu-id="24628-160">Create SAP BW Objects Options</span></span>  
 <span data-ttu-id="24628-161">**オブジェクトの種類を選択**</span><span class="sxs-lookup"><span data-stu-id="24628-161">**Select object type**</span></span>  
 <span data-ttu-id="24628-162">SAP Netweaver BW オブジェクトの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="24628-162">Select the type of SAP Netweaver BW object that you want to create.</span></span> <span data-ttu-id="24628-163">以下のいずれかの種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="24628-163">You can select one of the following types:</span></span>  
  
-   <span data-ttu-id="24628-164">インフォオブジェクト</span><span class="sxs-lookup"><span data-stu-id="24628-164">InfoObject</span></span>  
  
-   <span data-ttu-id="24628-165">インフォキューブ</span><span class="sxs-lookup"><span data-stu-id="24628-165">InfoCube</span></span>  
  
-   <span data-ttu-id="24628-166">インフォソース</span><span class="sxs-lookup"><span data-stu-id="24628-166">InfoSource</span></span>  
  
-   <span data-ttu-id="24628-167">インフォパッケージ</span><span class="sxs-lookup"><span data-stu-id="24628-167">InfoPackage</span></span>  
  
 <span data-ttu-id="24628-168">**作成**</span><span class="sxs-lookup"><span data-stu-id="24628-168">**Create**</span></span>  
 <span data-ttu-id="24628-169">選択した種類の SAP Netweaver BW オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="24628-169">Create the selected type of SAP Netweaver BW object.</span></span>  
  
|<span data-ttu-id="24628-170">[オブジェクトの種類]</span><span class="sxs-lookup"><span data-stu-id="24628-170">Object Type</span></span>|<span data-ttu-id="24628-171">結果</span><span class="sxs-lookup"><span data-stu-id="24628-171">Result</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="24628-172">**インフォオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="24628-172">**InfoObject**</span></span>|<span data-ttu-id="24628-173">**[新しいインフォオブジェクトの作成]** ダイアログ ボックスを使用して、新しいインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="24628-173">Create a new InfoObject by using the **Create New InfoObject** dialog box.</span></span> <span data-ttu-id="24628-174">このダイアログ ボックスの詳細については、「 [[新しいインフォオブジェクトの作成]](create-new-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-174">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>|  
|<span data-ttu-id="24628-175">**インフォキューブ**</span><span class="sxs-lookup"><span data-stu-id="24628-175">**InfoCube**</span></span>|<span data-ttu-id="24628-176">**[トランザクション データのインフォキューブの作成]** ダイアログ ボックスを使用して、新しいインフォキューブを作成します。</span><span class="sxs-lookup"><span data-stu-id="24628-176">Create a new InfoCube by using the **Create InfoCube for Transaction Data** dialog box.</span></span> <span data-ttu-id="24628-177">このダイアログ ボックスの詳細については、「 [トランザクション データのインフォキューブの作成](create-infocube-for-transaction-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-177">For more information about this dialog box, see [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md).</span></span>|  
|<span data-ttu-id="24628-178">**インフォソース**</span><span class="sxs-lookup"><span data-stu-id="24628-178">**InfoSource**</span></span>|<span data-ttu-id="24628-179">**[インフォソースの作成]** ダイアログ ボックスを使用してから、 **[トランザクション データのインフォソースの作成]** または **[マスター データのインフォソースの作成]** ダイアログ ボックスを使用して、新しいインフォソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="24628-179">Create a new InfoSource by using the **Create InfoSource** dialog box, and then by using the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span> <span data-ttu-id="24628-180">これらのダイアログ ボックスに関する詳細については、「 [インフォソースの作成](create-infosource.md)」、「 [トランザクション データのインフォソースの作成](create-infosource-for-transaction-data.md) 」、「 [マスター データのインフォソースの作成](create-infosource-for-master-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-180">For more information about these dialog boxes, see [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) and [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>|  
|<span data-ttu-id="24628-181">**インフォパッケージ**</span><span class="sxs-lookup"><span data-stu-id="24628-181">**InfoPackage**</span></span>|<span data-ttu-id="24628-182">**[インフォパッケージの作成]** ダイアログ ボックスを使用して、新しいインフォパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="24628-182">Create a new InfoPackage by using the **Create InfoPackage** dialog box.</span></span> <span data-ttu-id="24628-183">このダイアログ ボックスの詳細については、「 [インフォパッケージの作成](create-infopackage.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24628-183">For more information about this dialog box, see [Create InfoPackage](create-infopackage.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24628-184">参照</span><span class="sxs-lookup"><span data-stu-id="24628-184">See Also</span></span>  
 <span data-ttu-id="24628-185">[SAP BW 変換先エディター &#40;[マッピング] ページ&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="24628-185">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="24628-186">[SAP BW 変換先エディター &#40;[エラー出力] ページ&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="24628-186">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="24628-187">[SAP BW 変換先エディター &#40;[詳細設定] ページ&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="24628-187">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="24628-188">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="24628-188">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
