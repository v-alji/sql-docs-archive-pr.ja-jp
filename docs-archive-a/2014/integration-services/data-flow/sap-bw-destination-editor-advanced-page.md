---
title: '[SAP BW 変換先エディター] ([詳細設定] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c5ca943b804ad39cc391cb1cf7f06e056ddbe56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641779"
---
# <a name="sap-bw-destination-editor-advanced-page"></a><span data-ttu-id="dbf19-102">[SAP BW 変換先エディター] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="dbf19-102">SAP BW Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="dbf19-103">パッケージのサイズやタイムアウトの情報などの詳細を設定するには、 **[SAP BW 変換先エディター]** の **[詳細設定]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="dbf19-103">Use the **Advanced** page of the **SAP BW Destination Editor** to set advanced settings such as package size and time-out information.</span></span>  
  
 <span data-ttu-id="dbf19-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換先の詳細については、「 [SAP BW 転送先](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf19-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dbf19-105">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="dbf19-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="dbf19-106">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf19-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="dbf19-107">**[詳細設定] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="dbf19-107">**To open the Advanced page**</span></span>  
  
1.  <span data-ttu-id="dbf19-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="dbf19-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="dbf19-109">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf19-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="dbf19-110">**[SAP BW 変換先エディター]** で、 **[詳細設定]** をクリックして **[詳細設定]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="dbf19-110">In the **SAP BW Destination Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dbf19-111">オプション</span><span class="sxs-lookup"><span data-stu-id="dbf19-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbf19-112">変換先を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="dbf19-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="dbf19-113">**パッケージのサイズ**</span><span class="sxs-lookup"><span data-stu-id="dbf19-113">**Package size**</span></span>  
 <span data-ttu-id="dbf19-114">一度に転送するデータの行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="dbf19-114">Specify how many rows of data will be transferred at a time.</span></span> <span data-ttu-id="dbf19-115">このパラメーターの最適な値は、SAP Netweaver BW システムおよび発生する可能性のあるデータの追加処理によって異なります。</span><span class="sxs-lookup"><span data-stu-id="dbf19-115">The optimal value for this parameter depends on the SAP Netweaver BW system and on additional processing of the data that might occur.</span></span> <span data-ttu-id="dbf19-116">通常は、2,000 ～ 20,000 の値のパフォーマンスが最適です。</span><span class="sxs-lookup"><span data-stu-id="dbf19-116">Typically, values between 2000 and 20000 offer the best performance.</span></span>  
  
 <span data-ttu-id="dbf19-117">**プロセス チェーンをトリガー**</span><span class="sxs-lookup"><span data-stu-id="dbf19-117">**Trigger process chain**</span></span>  
 <span data-ttu-id="dbf19-118">(省略可能) データの読み込みが完了した後にトリガーするプロセス チェーンの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dbf19-118">(Optional) Specify the name of a process chain to be triggered after the loading of data is completed.</span></span>  
  
 <span data-ttu-id="dbf19-119">**インフォパッケージ待機のタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="dbf19-119">**Timeout for waiting InfoPackage**</span></span>  
 <span data-ttu-id="dbf19-120">インフォパッケージの終了を待機する必要がある最大秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="dbf19-120">Specify the maximum number of seconds that the destination should wait for the InfoPackage to finish.</span></span>  
  
 <span data-ttu-id="dbf19-121">**データ転送の完了を待機する**</span><span class="sxs-lookup"><span data-stu-id="dbf19-121">**Wait for data transfer to finish**</span></span>  
 <span data-ttu-id="dbf19-122">SAP Netweaver BW システムがデータの読み込みを完了するまで、変換先が待機する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="dbf19-122">Specify whether the destination should wait until the SAP Netweaver BW system has finished loading the data.</span></span>  
  
 <span data-ttu-id="dbf19-123">**インフォパッケージを開始しない - 待機のみ**</span><span class="sxs-lookup"><span data-stu-id="dbf19-123">**No InfoPackage Start (Only Wait)**</span></span>  
 <span data-ttu-id="dbf19-124">変換先がインフォパッケージを開始せず、SAP Netweaver BW システムがデータの読み込みを開始した通知だけを待機することを指定します。</span><span class="sxs-lookup"><span data-stu-id="dbf19-124">Specify that the destination does not trigger an InfoPackage, but just waits for notification that the SAP Netweaver BW system has started loading the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf19-125">参照</span><span class="sxs-lookup"><span data-stu-id="dbf19-125">See Also</span></span>  
 <span data-ttu-id="dbf19-126">[SAP BW 変換先エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="dbf19-126">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="dbf19-127">[SAP BW 変換先エディター &#40;[マッピング] ページ&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="dbf19-127">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="dbf19-128">[SAP BW 変換先エディター &#40;[エラー出力] ページ&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="dbf19-128">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="dbf19-129">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="dbf19-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
