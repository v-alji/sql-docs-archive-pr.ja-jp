---
title: '[トランザクション データのインフォソースの作成] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e3a60bb93da17e79087982473e92c35fa0856d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712237"
---
# <a name="create-infosource-for-transaction-data"></a><span data-ttu-id="76bca-102">[トランザクション データのインフォソースの作成]</span><span class="sxs-lookup"><span data-stu-id="76bca-102">Create InfoSource for Transaction Data</span></span>
  <span data-ttu-id="76bca-103">SAP Netweaver BW システムでトランザクション データ用の新しいインフォソースを作成するには、 **[トランザクション データのインフォソースの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="76bca-103">Use the **Create InfoSource for Transaction Data** dialog box to create a new InfoSource for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="76bca-104">**[トランザクション データのインフォソースの作成]** ダイアログ ボックスは、 **[SAP BW 変換先エディター]** の **[接続マネージャー]** ページから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="76bca-104">You can open the **Create InfoSource for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="76bca-105">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76bca-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="76bca-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="76bca-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="76bca-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="76bca-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="76bca-108">**[トランザクション データのインフォソースの作成] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="76bca-108">**To open the Create InfoSource for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="76bca-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="76bca-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="76bca-110">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="76bca-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="76bca-111">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="76bca-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="76bca-112">**[接続マネージャー]** ページの **[SAP BW オブジェクトの作成]** で、 **[インフォソース]** を選択し、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76bca-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="76bca-113">**[インフォソースの作成]** ダイアログ ボックスで、 **[トランザクション データ]** を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76bca-113">In the **Create InfoSource** dialog box, select **Transaction data**, and then click **OK**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="76bca-114">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="76bca-114">General Options</span></span>  
 <span data-ttu-id="76bca-115">**インフォソースの名前**</span><span class="sxs-lookup"><span data-stu-id="76bca-115">**InfoSource name**</span></span>  
 <span data-ttu-id="76bca-116">新しいインフォソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="76bca-116">Enter a name for the new InfoSource.</span></span>  
  
 <span data-ttu-id="76bca-117">**簡単な説明**</span><span class="sxs-lookup"><span data-stu-id="76bca-117">**Short description**</span></span>  
 <span data-ttu-id="76bca-118">新しいインフォソースの短い説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="76bca-118">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="76bca-119">**長い説明**</span><span class="sxs-lookup"><span data-stu-id="76bca-119">**Long description**</span></span>  
 <span data-ttu-id="76bca-120">新しいインフォソースの長い説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="76bca-120">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="76bca-121">**転送元システム**</span><span class="sxs-lookup"><span data-stu-id="76bca-121">**Source system**</span></span>  
 <span data-ttu-id="76bca-122">インフォソースに関連付けられた転送元システムを選択します。</span><span class="sxs-lookup"><span data-stu-id="76bca-122">Select the source system associated with the InfoSource.</span></span>  
  
 <span data-ttu-id="76bca-123">**保存と有効化**</span><span class="sxs-lookup"><span data-stu-id="76bca-123">**Save & Activate**</span></span>  
 <span data-ttu-id="76bca-124">新しいインフォソースを保存してアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="76bca-124">Save and activate the new InfoSource.</span></span>  
  
## <a name="infosource-transfer-structure-options"></a><span data-ttu-id="76bca-125">[インフォソース転送構造] のオプション</span><span class="sxs-lookup"><span data-stu-id="76bca-125">InfoSource Transfer Structure Options</span></span>  
 <span data-ttu-id="76bca-126">[インフォソース転送構造] では、データ フローの列をインフォソースに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="76bca-126">The InfoSource transfer structure lets you associate data flow columns to InfoSources.</span></span>  
  
 <span data-ttu-id="76bca-127">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="76bca-127">**PipelineElement**</span></span>  
 <span data-ttu-id="76bca-128">SAP BW 変換先に接続されているデータ フローの出力の列を表示します。</span><span class="sxs-lookup"><span data-stu-id="76bca-128">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="76bca-129">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="76bca-129">**PipelineDataType**</span></span>  
 <span data-ttu-id="76bca-130">データ フロー列の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型を表示します。</span><span class="sxs-lookup"><span data-stu-id="76bca-130">Displays the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type of the data flow column.</span></span>  
  
 <span data-ttu-id="76bca-131">**Iobject - 検索**</span><span class="sxs-lookup"><span data-stu-id="76bca-131">**Iobject - Search**</span></span>  
 <span data-ttu-id="76bca-132">既存のインフォオブジェクトを現在の行のデータ フロー列に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="76bca-132">Associate an existing InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="76bca-133">関連付けを行うには、 **[検索]** をクリックし、 **[インフォオブジェクトの参照]** ダイアログ ボックスを使用して既存のインフォオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="76bca-133">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="76bca-134">このダイアログ ボックスの詳細については、「 [インフォオブジェクトの参照](look-up-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76bca-134">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="76bca-135">既存のインフォオブジェクトを選択すると、選択した値が **[インフォオブジェクト]** 列と **[種類]** 列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="76bca-135">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="76bca-136">**Iobject - 新規**</span><span class="sxs-lookup"><span data-stu-id="76bca-136">**Iobject - New**</span></span>  
 <span data-ttu-id="76bca-137">新しいインフォオブジェクトを作成し、現在の行のデータ フロー列に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="76bca-137">Create a new InfoObject and associate this new InfoObect to the data flow column in the current row.</span></span> <span data-ttu-id="76bca-138">新しいインフォオブジェクトを作成するには、 **[新規作成]** をクリックし、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを使用してインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="76bca-138">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="76bca-139">このダイアログ ボックスの詳細については、「 [[新しいインフォオブジェクトの作成]](create-new-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76bca-139">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="76bca-140">新しいインフォオブジェクトを作成すると、新しい値が **[インフォオブジェクト]** 列と **[種類]** 列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="76bca-140">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="76bca-141">**Iobject - 削除**</span><span class="sxs-lookup"><span data-stu-id="76bca-141">**Iobject - Remove**</span></span>  
 <span data-ttu-id="76bca-142">インフォオブジェクトと現在の行のデータ フロー列との関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="76bca-142">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="76bca-143">関連付けを削除するには、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76bca-143">To remove this association, click **Remove**.</span></span>  
  
 <span data-ttu-id="76bca-144">**インフォオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="76bca-144">**InfoObject**</span></span>  
 <span data-ttu-id="76bca-145">データ フロー列に関連付けられているインフォオブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="76bca-145">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="76bca-146">**Type**</span><span class="sxs-lookup"><span data-stu-id="76bca-146">**Type**</span></span>  
 <span data-ttu-id="76bca-147">データ フロー列に関連付けられているインフォオブジェクトの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="76bca-147">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="76bca-148">次の表に、種類として使用できる値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="76bca-148">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="76bca-149">値</span><span class="sxs-lookup"><span data-stu-id="76bca-149">Value</span></span>|<span data-ttu-id="76bca-150">説明</span><span class="sxs-lookup"><span data-stu-id="76bca-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76bca-151">CHA</span><span class="sxs-lookup"><span data-stu-id="76bca-151">CHA</span></span>|<span data-ttu-id="76bca-152">特性</span><span class="sxs-lookup"><span data-stu-id="76bca-152">Characteristics</span></span>|  
|<span data-ttu-id="76bca-153">UNI</span><span class="sxs-lookup"><span data-stu-id="76bca-153">UNI</span></span>|<span data-ttu-id="76bca-154">Units</span><span class="sxs-lookup"><span data-stu-id="76bca-154">Units</span></span>|  
|<span data-ttu-id="76bca-155">KYF</span><span class="sxs-lookup"><span data-stu-id="76bca-155">KYF</span></span>|<span data-ttu-id="76bca-156">主要データ</span><span class="sxs-lookup"><span data-stu-id="76bca-156">Key figures</span></span>|  
|<span data-ttu-id="76bca-157">TIM</span><span class="sxs-lookup"><span data-stu-id="76bca-157">TIM</span></span>|<span data-ttu-id="76bca-158">時間の特性</span><span class="sxs-lookup"><span data-stu-id="76bca-158">Time characteristics</span></span>|  
  
 <span data-ttu-id="76bca-159">**単位フィールド**</span><span class="sxs-lookup"><span data-stu-id="76bca-159">**Unit Field**</span></span>  
 <span data-ttu-id="76bca-160">InfoObject が使用する単位を指定します。</span><span class="sxs-lookup"><span data-stu-id="76bca-160">Specify the units that the InfoObject will use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76bca-161">参照</span><span class="sxs-lookup"><span data-stu-id="76bca-161">See Also</span></span>  
 <span data-ttu-id="76bca-162">[[インフォソースの作成]](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="76bca-162">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="76bca-163">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="76bca-163">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
