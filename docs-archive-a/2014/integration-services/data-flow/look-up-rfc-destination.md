---
title: '[RFC 転送先の参照] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 397298fce16509e667aa4baccaee62c6ff0f5cca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741150"
---
# <a name="look-up-rfc-destination"></a><span data-ttu-id="1f9eb-102">[RFC 転送先の参照]</span><span class="sxs-lookup"><span data-stu-id="1f9eb-102">Look Up RFC Destination</span></span>
  <span data-ttu-id="1f9eb-103">SAP Netweaver BW システムで定義された RFC 転送先を参照する場合、 **[RFC 転送先の参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-103">Use the **Look Up RFC Destination** dialog box to look up an RFC destination that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="1f9eb-104">使用できる RFC 転送先の一覧が表示されたら目的の転送先を選択すると、関連するオプションに必要な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-104">When the list of available RFC destinations appears, select the destination that you want, and the component will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="1f9eb-105">SAP BW 変換元と SAP BW 変換先は両方とも、 **[RFC 転送先の参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-105">Both the SAP BW source and the SAP BW destination use the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="1f9eb-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW のコンポーネントの詳細については、「 [SAP BW Source](sap-bw-source.md) 」(SAP BW 変換元) および「 [SAP BW Destination](sap-bw-destination.md)」(SAP BW 変換先) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-106">For more information about these components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md) and [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1f9eb-107">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="1f9eb-108">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="1f9eb-109">**[RFC 転送先の参照] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="1f9eb-109">**To open the Look Up RFC Destination dialog box**</span></span>  
  
1.  <span data-ttu-id="1f9eb-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元または変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source or destination.</span></span>  
  
2.  <span data-ttu-id="1f9eb-111">**[データ フロー]** タブで、SAP BW 変換元または変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-111">On the **Data Flow** tab, double-click the SAP BW source or destination.</span></span>  
  
3.  <span data-ttu-id="1f9eb-112">**[SAP BW 変換元エディター]** または **[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-112">In the **SAP BW Source Editor** or the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="1f9eb-113">**[接続マネージャー]** ページの **[RFC 転送先]** で、 **[参照]** をクリックして **[RFC 転送先の参照]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-113">On the **Connection Manager** page, in the **RFC Destination** group box, click **Look up** to display the **Look Up RFC Destination** dialog box.</span></span>  
  
     <span data-ttu-id="1f9eb-114">**[SAP BW 変換元エディター]** で、 **[RFC 転送先]** は、 **[実行モード]** の値が **[P - プロセス チェーンをトリガー]** または **[W - 通知を待機]** である場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-114">In the **SAP BW Source Editor**, the **RFC Destination** group box appears only if the value for **Execution mode** is **P - Trigger process chain** or **W - Wait for notify**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1f9eb-115">オプション</span><span class="sxs-lookup"><span data-stu-id="1f9eb-115">Options</span></span>  
 <span data-ttu-id="1f9eb-116">**宛先**</span><span class="sxs-lookup"><span data-stu-id="1f9eb-116">**Destination**</span></span>  
 <span data-ttu-id="1f9eb-117">SAP Netweaver BW システムで定義された RFC 転送先の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-117">View the name of the RFC destination that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="1f9eb-118">**ゲートウェイ ホスト**</span><span class="sxs-lookup"><span data-stu-id="1f9eb-118">**Gateway Host**</span></span>  
 <span data-ttu-id="1f9eb-119">ゲートウェイ ホストのサーバー名または IP アドレスを表示します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-119">View the server name or IP address of the gateway host.</span></span> <span data-ttu-id="1f9eb-120">通常、IP アドレスの名前は、SAP アプリケーション サーバーの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-120">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="1f9eb-121">**ゲートウェイ サービス**</span><span class="sxs-lookup"><span data-stu-id="1f9eb-121">**Gateway Service**</span></span>  
 <span data-ttu-id="1f9eb-122">`sapgwNN` という形式でゲートウェイ サービスの名前を表示します。`NN` はシステム番号です。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-122">View the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="1f9eb-123">**プログラム ID**</span><span class="sxs-lookup"><span data-stu-id="1f9eb-123">**Program ID**</span></span>  
 <span data-ttu-id="1f9eb-124">RFC 転送先に関連付けられているプログラム ID を表示します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-124">View the Program ID that is associated with the RFC destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9eb-125">参照</span><span class="sxs-lookup"><span data-stu-id="1f9eb-125">See Also</span></span>  
 <span data-ttu-id="1f9eb-126">[SAP BW ソース エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="1f9eb-126">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="1f9eb-127">[SAP BW 変換先エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="1f9eb-127">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="1f9eb-128">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="1f9eb-128">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
