---
title: インフォパッケージの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95f6ddce4e97c0c21d9f77c432231d414770dbce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712249"
---
# <a name="create-infopackage"></a><span data-ttu-id="7da93-102">インフォパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="7da93-102">Create InfoPackage</span></span>
  <span data-ttu-id="7da93-103">SAP Netweaver BW システムで新しいインフォパッケージを作成するには、 **[インフォパッケージの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7da93-103">Use the **Create InfoPackage** dialog box to create a new InfoPackage in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="7da93-104">**[インフォパッケージの作成]** ダイアログ ボックスは、 **[SAP BW 変換先エディター]** の **[接続マネージャー]** ページから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="7da93-104">You can open the **Create InfoPackage** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="7da93-105">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7da93-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7da93-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="7da93-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="7da93-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7da93-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="7da93-108">**[インフォパッケージの作成] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="7da93-108">**To open the Create InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="7da93-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="7da93-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="7da93-110">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7da93-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="7da93-111">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="7da93-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="7da93-112">**[接続マネージャー]** ページの **[SAP BW オブジェクトの作成]** で、 **[インフォパッケージ]** を選択し、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7da93-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoPackage**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7da93-113">オプション</span><span class="sxs-lookup"><span data-stu-id="7da93-113">Options</span></span>  
 <span data-ttu-id="7da93-114">**インフォソース**</span><span class="sxs-lookup"><span data-stu-id="7da93-114">**InfoSource**</span></span>  
 <span data-ttu-id="7da93-115">新しいインフォパッケージの基にするインフォソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="7da93-115">Enter the name of the InfoSource on which the new InfoPackage should be based.</span></span>  
  
 <span data-ttu-id="7da93-116">**簡単な説明**</span><span class="sxs-lookup"><span data-stu-id="7da93-116">**Short description**</span></span>  
 <span data-ttu-id="7da93-117">新しいインフォパッケージの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="7da93-117">Enter a description for the new InfoPackage.</span></span>  
  
 <span data-ttu-id="7da93-118">**転送元システム**</span><span class="sxs-lookup"><span data-stu-id="7da93-118">**Source system**</span></span>  
 <span data-ttu-id="7da93-119">インフォパッケージに関連付けるソース システムを選択します。</span><span class="sxs-lookup"><span data-stu-id="7da93-119">Select the source system with which the new InfoPackage should be associated.</span></span>  
  
 <span data-ttu-id="7da93-120">**属性**</span><span class="sxs-lookup"><span data-stu-id="7da93-120">**Attributes**</span></span>  
 <span data-ttu-id="7da93-121">インフォパッケージが属性データを読み込むことを示します。</span><span class="sxs-lookup"><span data-stu-id="7da93-121">Indicates that the InfoPackage will load attribute data.</span></span>  
  
 <span data-ttu-id="7da93-122">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="7da93-122">**Texts**</span></span>  
 <span data-ttu-id="7da93-123">インフォパッケージがテキスト データを読み込むことを示します。</span><span class="sxs-lookup"><span data-stu-id="7da93-123">Indicates that the InfoPackage will load text data.</span></span>  
  
 <span data-ttu-id="7da93-124">**トランザクション**</span><span class="sxs-lookup"><span data-stu-id="7da93-124">**Transaction**</span></span>  
 <span data-ttu-id="7da93-125">インフォパッケージがトランザクション データを読み込むことを示します。</span><span class="sxs-lookup"><span data-stu-id="7da93-125">Indicates that the InfoPackage will load transaction data.</span></span>  
  
 <span data-ttu-id="7da93-126">**保存と有効化**</span><span class="sxs-lookup"><span data-stu-id="7da93-126">**Save & Activate**</span></span>  
 <span data-ttu-id="7da93-127">新しいインフォパッケージを保存してアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="7da93-127">Save and activate the new InfoPackage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da93-128">参照</span><span class="sxs-lookup"><span data-stu-id="7da93-128">See Also</span></span>  
 [<span data-ttu-id="7da93-129">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="7da93-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
