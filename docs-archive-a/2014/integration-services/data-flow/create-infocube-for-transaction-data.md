---
title: '[トランザクション データのインフォキューブの作成] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a20fe051cfdd3e6afe285279996fcf696a83c21b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712253"
---
# <a name="create-infocube-for-transaction-data"></a><span data-ttu-id="b07c1-102">[トランザクション データのインフォキューブの作成]</span><span class="sxs-lookup"><span data-stu-id="b07c1-102">Create InfoCube for Transaction Data</span></span>
  <span data-ttu-id="b07c1-103">SAP Netweaver BW システムでトランザクション データ用の新しいインフォキューブを作成するには、 **[トランザクション データのインフォキューブの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-103">Use the **Create InfoCube for Transaction Data** dialog box to create a new InfoCube for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="b07c1-104">**[トランザクション データのインフォキューブの作成]** ダイアログ ボックスは、 **[SAP BW 変換先エディター]** の **[接続マネージャー]** ページから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-104">You can open the **Create InfoCube for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="b07c1-105">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07c1-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b07c1-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b07c1-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="b07c1-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07c1-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="b07c1-108">**[トランザクション データのインフォキューブの作成] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="b07c1-108">**To open the Create InfoCube for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="b07c1-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="b07c1-110">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b07c1-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="b07c1-111">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="b07c1-112">**[接続マネージャー]** ページの **[SAP BW オブジェクトの作成]** で、 **[インフォキューブ]** を選択し、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b07c1-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoCube**, and then click **Create**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="b07c1-113">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="b07c1-113">General Options</span></span>  
 <span data-ttu-id="b07c1-114">**インフォキューブの名前**</span><span class="sxs-lookup"><span data-stu-id="b07c1-114">**InfoCube name**</span></span>  
 <span data-ttu-id="b07c1-115">新しいインフォキューブの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-115">Enter a name for the new InfoCube.</span></span>  
  
 <span data-ttu-id="b07c1-116">**長い説明**</span><span class="sxs-lookup"><span data-stu-id="b07c1-116">**Long description**</span></span>  
 <span data-ttu-id="b07c1-117">新しいインフォキューブの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-117">Enter a description for the new InfoCube.</span></span>  
  
 <span data-ttu-id="b07c1-118">**保存と有効化**</span><span class="sxs-lookup"><span data-stu-id="b07c1-118">**Save & Activate**</span></span>  
 <span data-ttu-id="b07c1-119">新しいインフォキューブを保存してアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-119">Save and activate the new InfoCube.</span></span>  
  
## <a name="infocube-transfer-structure-options"></a><span data-ttu-id="b07c1-120">[インフォキューブ転送構造] のオプション</span><span class="sxs-lookup"><span data-stu-id="b07c1-120">InfoCube Transfer Structure Options</span></span>  
 <span data-ttu-id="b07c1-121">[インフォキューブ転送構造] セクションでは、データ フローの列をインフォオブジェクトに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-121">The InfoCube transfer structure section lets you associate data flow columns to InfoObjects.</span></span>  
  
 <span data-ttu-id="b07c1-122">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="b07c1-122">**PipelineElement**</span></span>  
 <span data-ttu-id="b07c1-123">SAP BW 変換先に接続されているデータ フローの出力の列を表示します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-123">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="b07c1-124">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="b07c1-124">**PipelineDataType**</span></span>  
 <span data-ttu-id="b07c1-125">データ フロー列のデータ型を表示します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-125">Displays the data type of the data flow column.</span></span>  
  
 <span data-ttu-id="b07c1-126">**インフォオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="b07c1-126">**InfoObject**</span></span>  
 <span data-ttu-id="b07c1-127">データ フロー列に関連付けられているインフォオブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-127">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="b07c1-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="b07c1-128">**Type**</span></span>  
 <span data-ttu-id="b07c1-129">データ フロー列に関連付けられているインフォオブジェクトの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-129">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="b07c1-130">次の表に、種類として使用できる値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-130">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="b07c1-131">値</span><span class="sxs-lookup"><span data-stu-id="b07c1-131">Value</span></span>|<span data-ttu-id="b07c1-132">説明</span><span class="sxs-lookup"><span data-stu-id="b07c1-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b07c1-133">CHA</span><span class="sxs-lookup"><span data-stu-id="b07c1-133">CHA</span></span>|<span data-ttu-id="b07c1-134">特性</span><span class="sxs-lookup"><span data-stu-id="b07c1-134">Characteristics</span></span>|  
|<span data-ttu-id="b07c1-135">UNI</span><span class="sxs-lookup"><span data-stu-id="b07c1-135">UNI</span></span>|<span data-ttu-id="b07c1-136">Units</span><span class="sxs-lookup"><span data-stu-id="b07c1-136">Units</span></span>|  
|<span data-ttu-id="b07c1-137">KYF</span><span class="sxs-lookup"><span data-stu-id="b07c1-137">KYF</span></span>|<span data-ttu-id="b07c1-138">主要データ</span><span class="sxs-lookup"><span data-stu-id="b07c1-138">Key figures</span></span>|  
|<span data-ttu-id="b07c1-139">TIM</span><span class="sxs-lookup"><span data-stu-id="b07c1-139">TIM</span></span>|<span data-ttu-id="b07c1-140">時間の特性</span><span class="sxs-lookup"><span data-stu-id="b07c1-140">Time characteristics</span></span>|  
  
 <span data-ttu-id="b07c1-141">**Iobject - 検索**</span><span class="sxs-lookup"><span data-stu-id="b07c1-141">**Iobject - Search**</span></span>  
 <span data-ttu-id="b07c1-142">既存のインフォオブジェクトを現在の行のデータ フロー列に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-142">Associate an existing InfoObject to the data flow column for the current row.</span></span> <span data-ttu-id="b07c1-143">関連付けを行うには、 **[検索]** をクリックし、 **[インフォオブジェクトの参照]** ダイアログ ボックスを使用して既存のインフォオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-143">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="b07c1-144">このダイアログ ボックスの詳細については、「 [インフォオブジェクトの参照](look-up-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07c1-144">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="b07c1-145">既存のインフォオブジェクトを選択すると、選択した値が **[インフォオブジェクト]** 列と **[種類]** 列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-145">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="b07c1-146">**Iobject - 新規**</span><span class="sxs-lookup"><span data-stu-id="b07c1-146">**Iobject - New**</span></span>  
 <span data-ttu-id="b07c1-147">新しいインフォオブジェクトを作成し、現在の行のデータ フロー列に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-147">Create a new InfoObject and associate this new InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="b07c1-148">新しいインフォオブジェクトを作成するには、 **[新規作成]** をクリックし、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを使用してインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-148">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="b07c1-149">このダイアログ ボックスの詳細については、「 [[新しいインフォオブジェクトの作成]](create-new-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07c1-149">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="b07c1-150">新しいインフォオブジェクトを作成すると、新しい値が **[インフォオブジェクト]** 列と **[種類]** 列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b07c1-150">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="b07c1-151">**Iobject - 削除**</span><span class="sxs-lookup"><span data-stu-id="b07c1-151">**Iobject - Remove**</span></span>  
 <span data-ttu-id="b07c1-152">インフォオブジェクトと現在の行のデータ フロー列との関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="b07c1-152">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="b07c1-153">関連付けを削除するには、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b07c1-153">To remove this association, click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07c1-154">参照</span><span class="sxs-lookup"><span data-stu-id="b07c1-154">See Also</span></span>  
 [<span data-ttu-id="b07c1-155">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="b07c1-155">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
