---
title: インフォソースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7db233b-5464-43de-9d26-6dd24c7ac1b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9620d3170310322c79679e8298ffe465067ae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712233"
---
# <a name="create-infosource"></a><span data-ttu-id="e832f-102">[インフォソースの作成]</span><span class="sxs-lookup"><span data-stu-id="e832f-102">Create InfoSource</span></span>
  <span data-ttu-id="e832f-103">**[インフォソースの作成]** ダイアログ ボックスを使用すると、新しいインフォソースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e832f-103">Use the **Create InfoSource** dialog box to create a new InfoSource.</span></span> <span data-ttu-id="e832f-104">新しいインフォソースを作成するには、 **[トランザクション データのインフォソースの作成]** または **[マスター データのインフォソースの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e832f-104">To create the new InfoSource, you use either the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span>  
  
 <span data-ttu-id="e832f-105">**[インフォソースの作成]** ダイアログ ボックスは、 **[SAP BW 変換先エディター]** の **[接続マネージャー]** ページから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="e832f-105">You can open the **Create InfoSource** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="e832f-106">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e832f-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e832f-107">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e832f-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="e832f-108">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e832f-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="e832f-109">**[インフォソースの作成] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="e832f-109">**To open the Create InfoSource dialog box**</span></span>  
  
1.  <span data-ttu-id="e832f-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="e832f-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="e832f-111">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e832f-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="e832f-112">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="e832f-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="e832f-113">**[接続マネージャー]** ページの **[SAP BW オブジェクトの作成]** で、 **[インフォソース]** を選択し、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e832f-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e832f-114">オプション</span><span class="sxs-lookup"><span data-stu-id="e832f-114">Options</span></span>  
 <span data-ttu-id="e832f-115">**トランザクション データ**</span><span class="sxs-lookup"><span data-stu-id="e832f-115">**Transaction data**</span></span>  
 <span data-ttu-id="e832f-116">トランザクション データの新しいインフォソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="e832f-116">Create a new InfoSource for transaction data.</span></span>  
  
 <span data-ttu-id="e832f-117">このオプションを選択した場合、 **[トランザクション データのインフォソースの作成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e832f-117">If you select this option, the **Create InfoSource for Transaction Data** dialog box opens.</span></span> <span data-ttu-id="e832f-118">新しいインフォソースを作成するには、 **[トランザクション データのインフォソースの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e832f-118">You use the **Create InfoSource for Transaction Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="e832f-119">このダイアログ ボックスの詳細については、「 [[トランザクション データのインフォソースの作成]](create-infosource-for-transaction-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e832f-119">For more information about this dialog box, see [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md).</span></span>  
  
 <span data-ttu-id="e832f-120">**マスター データ**</span><span class="sxs-lookup"><span data-stu-id="e832f-120">**Master data**</span></span>  
 <span data-ttu-id="e832f-121">マスター データの新しいインフォソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="e832f-121">Create a new InfoSource for master data.</span></span>  
  
 <span data-ttu-id="e832f-122">このオプションを選択した場合、 **[マスター データのインフォソースの作成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e832f-122">If you select this option, the **Create InfoSource for Master Data** dialog box opens.</span></span> <span data-ttu-id="e832f-123">新しいインフォソースを作成するには、 **[マスター データのインフォソースの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e832f-123">You use the **Create InfoSource for Master Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="e832f-124">このダイアログ ボックスの詳細については、「 [[マスター データのインフォソースの作成]](create-infosource-for-master-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e832f-124">For more information about this dialog box, see [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e832f-125">参照</span><span class="sxs-lookup"><span data-stu-id="e832f-125">See Also</span></span>  
 [<span data-ttu-id="e832f-126">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="e832f-126">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
