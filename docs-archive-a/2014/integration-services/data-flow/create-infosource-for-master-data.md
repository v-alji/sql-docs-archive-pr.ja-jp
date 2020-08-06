---
title: '[マスター データのインフォソースの作成] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b52a9a89-8380-4a02-8a83-dcfb46ae860e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bb90bc5cf27f37dc89df236b765db98088a5804a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712245"
---
# <a name="create-infosource-for-master-data"></a><span data-ttu-id="3b7b0-102">[マスター データのインフォソースの作成]</span><span class="sxs-lookup"><span data-stu-id="3b7b0-102">Create InfoSource for Master Data</span></span>
  <span data-ttu-id="3b7b0-103">SAP Netweaver BW システムでマスター データ用の新しいインフォソースを作成するには、 **[マスター データのインフォソースの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-103">Use the **Create InfoSource for Master Data** dialog box to create a new InfoSource for master data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="3b7b0-104">**[マスター データのインフォソースの作成]** ダイアログ ボックスは、 **[SAP BW 変換先エディター]** の **[接続マネージャー]** ページから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-104">You can open the **Create InfoSource for Master Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="3b7b0-105">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3b7b0-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="3b7b0-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="3b7b0-108">**[マスター データのインフォソースの作成] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-108">**To open the Create InfoSource for Master Data dialog box**</span></span>  
  
1.  <span data-ttu-id="3b7b0-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="3b7b0-110">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="3b7b0-111">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="3b7b0-112">**[接続マネージャー]** ページの **[SAP BW オブジェクトの作成]** で、 **[インフォソース]** を選択し、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="3b7b0-113">**[インフォソースの作成]** ダイアログ ボックスで、 **[マスター データ]** を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-113">In the **Create InfoSource** dialog box, select **Master data**, and then click **OK**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3b7b0-114">オプション</span><span class="sxs-lookup"><span data-stu-id="3b7b0-114">Options</span></span>  
 <span data-ttu-id="3b7b0-115">**インフォオブジェクトの名前**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-115">**InfoObject name**</span></span>  
 <span data-ttu-id="3b7b0-116">新しいインフォソースの基にするインフォオブジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-116">Enter the name of the InfoObject on which the new InfoSource should be based.</span></span>  
  
 <span data-ttu-id="3b7b0-117">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-117">**Look up**</span></span>  
 <span data-ttu-id="3b7b0-118">インフォオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-118">Look up the InfoObject.</span></span> <span data-ttu-id="3b7b0-119">このオプションは、インフォオブジェクトを選択できる **[インフォオブジェクトの参照]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-119">This option opens the **Look Up InfoObject** dialog box in which you can select the InfoObject.</span></span> <span data-ttu-id="3b7b0-120">このダイアログ ボックスの詳細については、「 [インフォオブジェクトの参照](look-up-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-120">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="3b7b0-121">インフォオブジェクトを選択すると、選択したインフォオブジェクトの名前が **[インフォオブジェクトの名前]** ボックスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-121">After you select an InfoObject, the component populates the **InfoObject name** text box with the name of the selected InfoObject.</span></span>  
  
 <span data-ttu-id="3b7b0-122">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-122">**New**</span></span>  
 <span data-ttu-id="3b7b0-123">新しいインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-123">Create a new InfoObject.</span></span> <span data-ttu-id="3b7b0-124">このオプションでは、新しいインフォオブジェクトを作成できる **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-124">This option opens the **Create New InfoObject** dialog box in which you can create the new InfoObject.</span></span> <span data-ttu-id="3b7b0-125">このダイアログ ボックスの詳細については、「 [[新しいインフォオブジェクトの作成]](create-new-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-125">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="3b7b0-126">インフォオブジェクトを作成すると、新しいインフォオブジェクトの名前が **[インフォオブジェクトの名前]** ボックスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-126">After you create an InfoObject, the component populates the **InfoObject name** text box with the name of the new InfoObject.</span></span>  
  
 <span data-ttu-id="3b7b0-127">**簡単な説明**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-127">**Short description**</span></span>  
 <span data-ttu-id="3b7b0-128">新しいインフォソースの短い説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-128">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="3b7b0-129">**長い説明**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-129">**Long description**</span></span>  
 <span data-ttu-id="3b7b0-130">新しいインフォソースの長い説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-130">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="3b7b0-131">**転送元システム**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-131">**Source system**</span></span>  
 <span data-ttu-id="3b7b0-132">新しいインフォソースに関連付ける転送元システムを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-132">Select the source system to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="3b7b0-133">**Application**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-133">**Application**</span></span>  
 <span data-ttu-id="3b7b0-134">新しいインフォソースに関連付けるアプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-134">Enter the name of the application to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="3b7b0-135">**属性**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-135">**Attributes**</span></span>  
 <span data-ttu-id="3b7b0-136">マスター データが複数の属性で構成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-136">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="3b7b0-137">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-137">**Texts**</span></span>  
 <span data-ttu-id="3b7b0-138">マスター データが複数の属性で構成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-138">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="3b7b0-139">**保存と有効化**</span><span class="sxs-lookup"><span data-stu-id="3b7b0-139">**Save & Activate**</span></span>  
 <span data-ttu-id="3b7b0-140">新しいインフォソースを保存してアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="3b7b0-140">Save and activate the new InfoSource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7b0-141">参照</span><span class="sxs-lookup"><span data-stu-id="3b7b0-141">See Also</span></span>  
 <span data-ttu-id="3b7b0-142">[[インフォソースの作成]](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="3b7b0-142">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="3b7b0-143">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="3b7b0-143">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
