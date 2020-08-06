---
title: SAP BW 転送先 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a612ed91-b89b-4173-a0b1-0bce381e1e28
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a0d7c5b75da89e665dbe60bbd7e29ce74da67db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642943"
---
# <a name="sap-bw-destination"></a><span data-ttu-id="c8b20-102">SAP BW 転送先</span><span class="sxs-lookup"><span data-stu-id="c8b20-102">SAP BW Destination</span></span>
  <span data-ttu-id="c8b20-103">SAP BW 変換先は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の変換先コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="c8b20-103">The SAP BW destination is the destination component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="c8b20-104">SAP BW 変換先は、SAP Netweaver BW Version 7 システムに [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フローのデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-104">Thus, the SAP BW destination loads data from the data flow in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package into an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="c8b20-105">変換先は 1 つの入力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="c8b20-105">This destination has one input and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c8b20-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="c8b20-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="c8b20-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="c8b20-108">SAP BW 変換先を使用するには、次の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8b20-108">To use the SAP BW destination, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="c8b20-109">SAP Netweaver BW オブジェクトを準備する</span><span class="sxs-lookup"><span data-stu-id="c8b20-109">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="c8b20-110">SAP Netweaver BW システムに接続する</span><span class="sxs-lookup"><span data-stu-id="c8b20-110">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="c8b20-111">SAP BW 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="c8b20-111">Configure the SAP BW destination</span></span>](#bkmk_Configure_Destination)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-destination-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="c8b20-112">変換先に必要な SAP Netweaver BW オブジェクトの準備</span><span class="sxs-lookup"><span data-stu-id="c8b20-112">Preparing the SAP Netweaver BW Objects That the Destination Requires</span></span>  
 <span data-ttu-id="c8b20-113">SAP BW 変換先を使用する前に、特定のオブジェクトを SAP Netweaver BW システムに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8b20-113">The SAP BW destination requires that certain objects are in the SAP Netweaver BW system before the destination can function.</span></span> <span data-ttu-id="c8b20-114">これらのオブジェクトがまだ存在しない場合は、これらの手順に従って SAP Netweaver BW システムで作成および構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8b20-114">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8b20-115">これらのオブジェクトと構成手順の詳細については、SAP Netweaver BW のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-115">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="c8b20-116">新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-116">Create a new Source System:</span></span>  
  
    1.  <span data-ttu-id="c8b20-117">種類として **["サード パーティ/ステージング BAPI"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-117">Select the type, **"Third Party/Staging BAPIs"**.</span></span>  
  
    2.  <span data-ttu-id="c8b20-118">**[対象のシステムを使用している通信の種類]** の **[非 Unicode (非アクティブな MDMP の設定)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-118">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    3.  <span data-ttu-id="c8b20-119">適切なプログラム ID を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-119">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="c8b20-120">インフォソースにソース システムを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-120">Assign the Source System to an InfoSource.</span></span>  
  
3.  <span data-ttu-id="c8b20-121">インフォパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-121">Create an InfoPackage.</span></span>  
  
     <span data-ttu-id="c8b20-122">インフォパッケージは、SAP BW 変換先に必要な最も重要なオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c8b20-122">The InfoPackage is the most important object that is required by the SAP BW destination.</span></span>  
  
 <span data-ttu-id="c8b20-123">また、SAP Netweaver BW システムにデータの読み込みをサポートするために必要な、追加のインフォオブジェクト、インフォキューブ、インフォソース、およびインフォパッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-123">You can also create additional InfoObjects, InfoCubes, InfoSources, and InfoPackages that are required to support loading data into the SAP Netweaver BW system.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="c8b20-124">SAP Netweaver BW システムへの接続</span><span class="sxs-lookup"><span data-stu-id="c8b20-124">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="c8b20-125">SAP Netweaver BW Version 7 システムに接続するため、SAP BW 変換先は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW パッケージの一部である SAP BW 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-125">To connect to the SAP Netweaver BW version 7 system, the SAP BW destination uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="c8b20-126">SAP BW 接続マネージャーは、SAP BW 変換先が使用できる唯一の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 接続マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="c8b20-126">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW destination can use.</span></span>  
  
 <span data-ttu-id="c8b20-127">SAP BW 接続マネージャーの詳細については、「 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-127">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-destination"></a><a name="bkmk_Configure_Destination"></a> <span data-ttu-id="c8b20-128">SAP BW 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="c8b20-128">Configuring the SAP BW Destination</span></span>  
 <span data-ttu-id="c8b20-129">SAP BW 変換先は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-129">You can configure the SAP BW destination in the following ways:</span></span>  
  
-   <span data-ttu-id="c8b20-130">データの読み込みに使用するインフォパッケージを探して参照します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-130">Look up and select the InfoPackage to use to load data.</span></span>  
  
-   <span data-ttu-id="c8b20-131">インフォパッケージの適切なインフォオブジェクトへのデータ フロー内の各列をマップします。</span><span class="sxs-lookup"><span data-stu-id="c8b20-131">Map each column in the data flow to the appropriate InfoObject in the InfoPackage.</span></span>  
  
-   <span data-ttu-id="c8b20-132">`PackageSize` プロパティを構成して、一度に転送するデータの行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-132">Specify how many rows of data will be transferred at a time by configuring the `PackageSize` property.</span></span>  
  
-   <span data-ttu-id="c8b20-133">データの読み込みが SAP Netweaver BW システムで完了するまで待機することを選択します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-133">Choose to wait until the loading of data is completed by the SAP Netweaver BW system.</span></span>  
  
-   <span data-ttu-id="c8b20-134">インフォパッケージを開始せず、SAP Netweaver BW システムがデータの読み込みを開始した通知を待機することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-134">Choose not to trigger the InfoPackage, but to wait for notification that the SAP Netweaver BW system has started the loading of data.</span></span>  
  
-   <span data-ttu-id="c8b20-135">必要に応じて、データの読み込みが完了した後に別のプロセス チェーンを発生させます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-135">Optionally, trigger another process chain after the loading of data is completed.</span></span>  
  
-   <span data-ttu-id="c8b20-136">必要に応じて、変換先に必要な SAP Netweaver BW オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8b20-136">Optionally, create the SAP Netweaver BW objects that are required by the destination.</span></span> <span data-ttu-id="c8b20-137">これには、インフォオブジェクト、インフォキューブ、インフォソース、およびインフォパッケージの作成も含まれます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-137">This includes creating InfoObjects, InfoCubes, InfoSources, and InfoPackages.</span></span>  
  
-   <span data-ttu-id="c8b20-138">選択したオプションで、データの読み込みをテストします。</span><span class="sxs-lookup"><span data-stu-id="c8b20-138">Test the loading of data with the options that you have selected.</span></span>  
  
 <span data-ttu-id="c8b20-139">変換先が呼び出す RFC 関数のログを有効にすることもできます</span><span class="sxs-lookup"><span data-stu-id="c8b20-139">You can also enable logging of RFC function calls by the destination.</span></span> <span data-ttu-id="c8b20-140">(このログは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで有効にできる、省略可能なログとは異なります)。変換先が使用する SAP BW 接続マネージャーを構成する際に、RFC 関数呼び出しのログ記録を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c8b20-140">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the destination will use.</span></span> <span data-ttu-id="c8b20-141">SAP BW 接続マネージャーを構成する方法の詳細については、「 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-141">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c8b20-142">変換先を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-142">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="c8b20-143">SAP BW 接続マネージャー、変換元、変換先の構成および使用方法の詳細については、ホワイト ペーパー「 [SAP BI 7.0 を使用した SQL Server 2008 Integration Services](https://go.microsoft.com/fwlink/?LinkID=137090)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-143">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="c8b20-144">このホワイト ペーパーには、SAP BW で必要なオブジェクトの構成方法についても説明されています。</span><span class="sxs-lookup"><span data-stu-id="c8b20-144">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-destination"></a><span data-ttu-id="c8b20-145">SSIS デザイナーを使用して変換先を構成する</span><span class="sxs-lookup"><span data-stu-id="c8b20-145">Using the SSIS Designer to Configure the Destination</span></span>  
 <span data-ttu-id="c8b20-146">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できる SAP BW 変換先のプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-146">For more information about the properties of the SAP BW destination that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="c8b20-147">[SAP BW 変換先エディター ([接続マネージャー] ページ)](sap-bw-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="c8b20-147">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="c8b20-148">[SAP BW 変換先エディター ([マッピング] ページ)](sap-bw-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="c8b20-148">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="c8b20-149">[SAP BW 変換先エディター ([エラー出力] ページ)](sap-bw-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="c8b20-149">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md)</span></span>  
  
-   <span data-ttu-id="c8b20-150">[SAP BW 変換先エディター ([詳細設定] ページ)](sap-bw-destination-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="c8b20-150">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="c8b20-151">SAP BW 変換先を構成するときに、SAP Netweaver BW オブジェクトを参照または作成するためにさまざまなダイアログ ボックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8b20-151">While you are configuring the SAP BW destination, you can also use various dialog boxes to look up or to create SAP Netweaver BW objects.</span></span> <span data-ttu-id="c8b20-152">これらのダイアログ ボックスの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b20-152">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c8b20-153">インフォパッケージの参照</span><span class="sxs-lookup"><span data-stu-id="c8b20-153">Look Up InfoPackage</span></span>](look-up-infopackage.md)  
  
-   [<span data-ttu-id="c8b20-154">新しいインフォオブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c8b20-154">Create New InfoObject</span></span>](create-new-infoobject.md)  
  
-   [<span data-ttu-id="c8b20-155">トランザクション データのインフォキューブの作成</span><span class="sxs-lookup"><span data-stu-id="c8b20-155">Create InfoCube for Transaction Data</span></span>](create-infocube-for-transaction-data.md)  
  
-   [<span data-ttu-id="c8b20-156">インフォオブジェクトの参照</span><span class="sxs-lookup"><span data-stu-id="c8b20-156">Look Up InfoObject</span></span>](look-up-infoobject.md)  
  
-   [<span data-ttu-id="c8b20-157">インフォソースの作成</span><span class="sxs-lookup"><span data-stu-id="c8b20-157">Create InfoSource</span></span>](create-infosource.md)  
  
-   [<span data-ttu-id="c8b20-158">トランザクション データのインフォソースの作成</span><span class="sxs-lookup"><span data-stu-id="c8b20-158">Create InfoSource for Transaction Data</span></span>](create-infosource-for-transaction-data.md)  
  
-   [<span data-ttu-id="c8b20-159">マスター データのインフォソースの作成</span><span class="sxs-lookup"><span data-stu-id="c8b20-159">Create InfoSource for Master Data</span></span>](create-infosource-for-master-data.md)  
  
-   [<span data-ttu-id="c8b20-160">インフォパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="c8b20-160">Create InfoPackage</span></span>](create-infopackage.md)  
  
## <a name="see-also"></a><span data-ttu-id="c8b20-161">参照</span><span class="sxs-lookup"><span data-stu-id="c8b20-161">See Also</span></span>  
 [<span data-ttu-id="c8b20-162">Microsoft Connector 1.1 for SAP BW のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="c8b20-162">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
