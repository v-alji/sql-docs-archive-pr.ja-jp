---
title: SAP BW 変換元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 749afb64-3567-4dc9-8431-783d650c25db
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d64af5e0d881e3b7dbbd2cc4e005aa3dbef3c43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644080"
---
# <a name="sap-bw-source"></a><span data-ttu-id="50c74-102">SAP BW 転送元</span><span class="sxs-lookup"><span data-stu-id="50c74-102">SAP BW Source</span></span>
  <span data-ttu-id="50c74-103">SAP BW 変換元は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の変換元コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="50c74-103">The SAP BW source is the source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="50c74-104">そのため、SAP BW 変換元により SAP Netweaver BW Version 7 システムからデータが抽出され、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フローにこのデータが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="50c74-104">Thus, the SAP BW source extracts data from an SAP Netweaver BW version 7 system and makes this data available to the data flow in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="50c74-105">この変換は、1 つの出力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="50c74-105">This source has one output and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50c74-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="50c74-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="50c74-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50c74-108">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="50c74-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="50c74-109">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="50c74-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="50c74-110">SAP BW 変換元を使用するには、次の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="50c74-110">To use the SAP BW source, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="50c74-111">SAP Netweaver BW オブジェクトを準備する</span><span class="sxs-lookup"><span data-stu-id="50c74-111">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="50c74-112">SAP Netweaver BW システムに接続する</span><span class="sxs-lookup"><span data-stu-id="50c74-112">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="50c74-113">SAP BW 変換元を構成する</span><span class="sxs-lookup"><span data-stu-id="50c74-113">Configure the SAP BW source</span></span>](#bkmk_Configure_Source)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-source-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="50c74-114">変換元に必要な SAP Netweaver BW オブジェクトの準備</span><span class="sxs-lookup"><span data-stu-id="50c74-114">Preparing the SAP Netweaver BW Objects That the Source Requires</span></span>  
 <span data-ttu-id="50c74-115">SAP BW 変換元を使用する前に、特定のオブジェクトを SAP Netweaver BW システムに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="50c74-115">The SAP BW source requires that certain objects are in the SAP Netweaver BW system before the source can function.</span></span> <span data-ttu-id="50c74-116">これらのオブジェクトがまだ存在しない場合は、これらの手順に従って SAP Netweaver BW システムで作成および構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50c74-116">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50c74-117">これらのオブジェクトと構成手順の詳細については、SAP Netweaver BW のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-117">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="50c74-118">SAP の GUI から SAP Netweaver BW にログインしてトランザクション コード SM59 を入力し、RFC 変換先を作成します。</span><span class="sxs-lookup"><span data-stu-id="50c74-118">Log on to SAP Netweaver BW through the SAP GUI, enter transaction code SM59, and create an RFC destination:</span></span>  
  
    1.  <span data-ttu-id="50c74-119">**[接続の種類]** の **[TCP/IP]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-119">For **Connection Type**, select **TCP/IP**.</span></span>  
  
    2.  <span data-ttu-id="50c74-120">**[アクティブ化の種類]** の **[登録済みサーバーのプログラム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-120">For **Activation Type**, select **Registered Server Program**.</span></span>  
  
    3.  <span data-ttu-id="50c74-121">**[対象のシステムを使用している通信の種類]** の **[非 Unicode (非アクティブな MDMP の設定)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-121">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    4.  <span data-ttu-id="50c74-122">適切なプログラム ID を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="50c74-122">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="50c74-123">オープン ハブ転送先を作成します。</span><span class="sxs-lookup"><span data-stu-id="50c74-123">Create an Open Hub Destination:</span></span>  
  
    1.  <span data-ttu-id="50c74-124">Administrator Workbench (トランザクション コード RSA1) に移動し、左ペインで **[オープン ハブ転送先]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-124">Go to the Administrator Workbench (transaction code RSA1) and, in the left pane, select **Open Hub Destination**.</span></span>  
  
    2.  <span data-ttu-id="50c74-125">中央のペインで、InfoArea を右クリックし、 **["オープン ハブ転送先の作成"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-125">In the middle pane, right-click an InfoArea, and then select **"Create Open Hub Destination"**.</span></span>  
  
    3.  <span data-ttu-id="50c74-126">**[変換先の種類]** で、 **["サード パーティ ツール"]** を選択し、作成済みの RFC 変換先を入力します。</span><span class="sxs-lookup"><span data-stu-id="50c74-126">For **Destination Type**, select **"Third Party Tool"**, and then enter the previously created RFC Destination.</span></span>  
  
    4.  <span data-ttu-id="50c74-127">新しいオープン ハブ転送先を保存してアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="50c74-127">Save and activate the new Open Hub Destination.</span></span>  
  
3.  <span data-ttu-id="50c74-128">データ転送プロセス (DTP) を作成します。</span><span class="sxs-lookup"><span data-stu-id="50c74-128">Create a Data Transfer Process (DTP):</span></span>  
  
    1.  <span data-ttu-id="50c74-129">InfoArea の中央のペインで、作成済みの変換先を右クリックし、 **[データ転送プロセスの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-129">In the middle pane of the InfoArea, right-click the previously created destination, and then select **"Create data transfer process"**.</span></span>  
  
    2.  <span data-ttu-id="50c74-130">DTP を構成、保存、およびアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="50c74-130">Configure, save, and activate the DTP.</span></span>  
  
    3.  <span data-ttu-id="50c74-131">メニューで、パーティションをクリックし、 **[移動]** をクリックして、 **[バッチ マネージャーの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50c74-131">On the menu, click **Goto**, and then click **Settings for Batch Manager**.</span></span>  
  
    4.  <span data-ttu-id="50c74-132">順次処理用に **[プロセス数]** を 1 に更新します。</span><span class="sxs-lookup"><span data-stu-id="50c74-132">Update **Number of processes** to 1 for serial processing.</span></span>  
  
4.  <span data-ttu-id="50c74-133">プロセス チェーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="50c74-133">Create a process chain:</span></span>  
  
    1.  <span data-ttu-id="50c74-134">プロセス チェーンを構成する場合、 **[メタデータ チェーンまたは API の使用を開始する]** を **[処理の開始]** の **[スケジュール設定のオプション]** として選択し、作成済みの DTP を後続のノードとして追加します。</span><span class="sxs-lookup"><span data-stu-id="50c74-134">When configuring the process chain, select the **Start Using Metadata Chain or API** as the **Scheduling Options** of the **Start Process**, and then add the previously created DTP as the subsequent node.</span></span>  
  
    2.  <span data-ttu-id="50c74-135">プロセス チェーンを保存し、アクティブにします。</span><span class="sxs-lookup"><span data-stu-id="50c74-135">Save and activate the process chain.</span></span>  
  
     <span data-ttu-id="50c74-136">SAP BW 変換元は、データ転送プロセスをアクティブにするプロセス チェーンを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="50c74-136">The SAP BW source can call the process chain to activate the data transfer process.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="50c74-137">SAP Netweaver BW システムへの接続</span><span class="sxs-lookup"><span data-stu-id="50c74-137">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="50c74-138">SAP Netweaver BW Version 7 システムに接続するため、SAP BW 変換元は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW パッケージの一部である SAP BW 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="50c74-138">To connect to the SAP Netweaver BW version 7 system, the SAP BW source uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="50c74-139">SAP BW 接続マネージャーは、SAP BW 変換元が使用できる唯一の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 接続マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="50c74-139">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW source can use.</span></span>  
  
 <span data-ttu-id="50c74-140">SAP BW 接続マネージャーの詳細については、「 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-140">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-source"></a><a name="bkmk_Configure_Source"></a> <span data-ttu-id="50c74-141">SAP BW 変換元の構成</span><span class="sxs-lookup"><span data-stu-id="50c74-141">Configuring the SAP BW Source</span></span>  
 <span data-ttu-id="50c74-142">SAP BW 変換元は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="50c74-142">You can configure the SAP BW source in the following ways:</span></span>  
  
-   <span data-ttu-id="50c74-143">データを抽出するためのオープン ハブ サービス (OHS) 転送先を探して選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-143">Look up and select the Open Hub Service (OHS) destination to use to extract data.</span></span>  
  
-   <span data-ttu-id="50c74-144">データを抽出するため次のいずれかの方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="50c74-144">Select one of the following methods for extracting data:</span></span>  
  
    -   <span data-ttu-id="50c74-145">プロセス チェーンをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="50c74-145">Trigger a process chain.</span></span> <span data-ttu-id="50c74-146">この場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージが抽出プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="50c74-146">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="50c74-147">SAP Netweaver BW システムからのデータ抽出開始通知を待ちます。</span><span class="sxs-lookup"><span data-stu-id="50c74-147">Wait for notification from the SAP Netweaver BW system to begin an extraction.</span></span> <span data-ttu-id="50c74-148">この場合、SAP Netweaver BW システムが抽出プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="50c74-148">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="50c74-149">特定の要求 ID に関連付けられたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="50c74-149">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="50c74-150">この場合、SAP Netweaver BW システムが内部テーブルにデータを既に抽出済みで、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージはデータを読み取るだけです。</span><span class="sxs-lookup"><span data-stu-id="50c74-150">In this case, the SAP Netweaver BW system has already extracted the data to an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>  
  
-   <span data-ttu-id="50c74-151">データの抽出方法に応じて、次の追加情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="50c74-151">Depending on the method selected for extracting data, provide the following additional information:</span></span>  
  
    -   <span data-ttu-id="50c74-152">**[P - プロセス チェーンをトリガー]** オプションでは、RFC 変換先のゲートウェイ ホスト名、ゲートウェイ サービス名、プログラム ID、およびプロセス チェーンの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="50c74-152">For the **P - Trigger Process Chain** option, provide the gateway host name, gateway service name, program ID for the RFC destination, and name of the process chain.</span></span>  
  
    -   <span data-ttu-id="50c74-153">**[W - 通知を待機]** オプションでは、RFC 変換先のゲートウェイ ホスト名、ゲートウェイ サーバー名、およびプログラム ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="50c74-153">For the **W - Wait for Notify** option, provide the gateway host name, the gateway server name, and the program ID for the RFC destination.</span></span> <span data-ttu-id="50c74-154">タイムアウト値も指定できます (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="50c74-154">You can also specify the timeout (in seconds).</span></span> <span data-ttu-id="50c74-155">タイムアウトは、変換元が通知を待機する最大時間です。</span><span class="sxs-lookup"><span data-stu-id="50c74-155">The timeout is the maximum period of time that the source will wait to be notified.</span></span>  
  
    -   <span data-ttu-id="50c74-156">**[E - 抽出のみ]** オプションでは、要求 ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="50c74-156">For the **E - Extract Only** option, provide the Request ID.</span></span>  
  
-   <span data-ttu-id="50c74-157">文字列変換のルールを指定します</span><span class="sxs-lookup"><span data-stu-id="50c74-157">Specify rules for string conversion.</span></span> <span data-ttu-id="50c74-158">(たとえば、すべての文字列を SAP Netweaver BW システムが Unicode であるかどうかに応じて変換するか、`varchar` または `nvarchar` に変換するかどうか)。</span><span class="sxs-lookup"><span data-stu-id="50c74-158">(For example, convert all strings depending on whether the SAP Netweaver BW system is Unicode or not, or convert all strings to `varchar` or `nvarchar`).</span></span>  
  
-   <span data-ttu-id="50c74-159">選択したオプションを使用して、抽出するデータをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="50c74-159">Use the options that you have selected to preview the data to be extracted.</span></span>  
  
 <span data-ttu-id="50c74-160">変換元が呼び出す RFC 関数のログを有効にすることもできます</span><span class="sxs-lookup"><span data-stu-id="50c74-160">You can also enable logging of RFC function calls by the source.</span></span> <span data-ttu-id="50c74-161">(このログは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで有効にできる、省略可能なログとは異なります)。変換元が使用する SAP BW 接続マネージャーを構成する際に、RFC 関数呼び出しのログ記録を有効にします。</span><span class="sxs-lookup"><span data-stu-id="50c74-161">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the source will use.</span></span> <span data-ttu-id="50c74-162">SAP BW 接続マネージャーを構成する方法の詳細については、「 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-162">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="50c74-163">変換元を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-163">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="50c74-164">SAP BW 接続マネージャー、変換元、変換先の構成および使用方法の詳細については、ホワイト ペーパー「 [SAP BI 7.0 を使用した SQL Server 2008 Integration Services](https://go.microsoft.com/fwlink/?LinkID=137090)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-164">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="50c74-165">このホワイト ペーパーには、SAP BW で必要なオブジェクトの構成方法についても説明されています。</span><span class="sxs-lookup"><span data-stu-id="50c74-165">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="50c74-166">SSIS デザイナーを使用してソースを構成する</span><span class="sxs-lookup"><span data-stu-id="50c74-166">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="50c74-167">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できる SAP BW 変換元のプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-167">For more information about the properties of the SAP BW source that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="50c74-168">[SAP BW ソース エディター ([接続マネージャー] ページ)](sap-bw-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="50c74-168">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="50c74-169">[SAP BW ソース エディター ([列] ページ)](sap-bw-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="50c74-169">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="50c74-170">[SAP BW ソース エディター ([エラー出力] ページ)](sap-bw-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="50c74-170">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md)</span></span>  
  
-   <span data-ttu-id="50c74-171">[SAP BW ソース エディター ([詳細設定] ページ)](sap-bw-source-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="50c74-171">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="50c74-172">SAP BW 変換元を構成するときに、SAP Netweaver BW オブジェクトを参照したり、ソース データをプレビューしたりするためにさまざまなダイアログ ボックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="50c74-172">While you are configuring the SAP BW source, you can also use various dialog boxes to look up SAP Netweaver BW objects or to preview the source data.</span></span> <span data-ttu-id="50c74-173">これらのダイアログ ボックスの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c74-173">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="50c74-174">RFC 転送先の参照</span><span class="sxs-lookup"><span data-stu-id="50c74-174">Look Up RFC Destination</span></span>](look-up-rfc-destination.md)  
  
-   [<span data-ttu-id="50c74-175">プロセス チェーンの参照</span><span class="sxs-lookup"><span data-stu-id="50c74-175">Look Up Process Chain</span></span>](look-up-process-chain.md)  
  
-   [<span data-ttu-id="50c74-176">要求のログ</span><span class="sxs-lookup"><span data-stu-id="50c74-176">Request Log</span></span>](request-log.md)  
  
-   [<span data-ttu-id="50c74-177">プレビュー</span><span class="sxs-lookup"><span data-stu-id="50c74-177">Preview</span></span>](preview.md)  
  
## <a name="see-also"></a><span data-ttu-id="50c74-178">参照</span><span class="sxs-lookup"><span data-stu-id="50c74-178">See Also</span></span>  
 [<span data-ttu-id="50c74-179">Microsoft Connector 1.1 for SAP BW のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="50c74-179">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
