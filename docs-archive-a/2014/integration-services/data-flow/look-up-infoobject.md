---
title: '[インフォオブジェクトの参照] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7f4c132-a5ec-49d8-a964-45775432731f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1616b4fcb368afc9e3f1157a3fc2511d4a7e8cce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715606"
---
# <a name="look-up-infoobject"></a><span data-ttu-id="451c3-102">[インフォオブジェクトの参照]</span><span class="sxs-lookup"><span data-stu-id="451c3-102">Look Up InfoObject</span></span>
  <span data-ttu-id="451c3-103">SAP Netweaver BW システムで定義されたインフォオブジェクトを参照する場合、 **[インフォオブジェクトの参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="451c3-103">Use the **Look Up InfoObject** dialog box to look up an InfoObject that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="451c3-104">使用できるインフォオブジェクトの一覧が表示されたら目的のインフォオブジェクトを選択すると、SAP BW 変換先で関連するオプションに必要な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="451c3-104">When the list of available InfoObjects appears, select the InfoObject that you want, and the SAP BW destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="451c3-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換先は、 **[インフォオブジェクトの参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="451c3-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up InfoObject** dialog box.</span></span> <span data-ttu-id="451c3-106">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="451c3-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="451c3-107">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="451c3-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="451c3-108">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="451c3-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="451c3-109">**[インフォオブジェクトの参照] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="451c3-109">**To open the Look Up InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="451c3-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="451c3-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="451c3-111">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="451c3-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="451c3-112">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="451c3-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="451c3-113">**[接続マネージャー]** ページの **[SAP BW オブジェクトの作成]** で、以下のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="451c3-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select one of the following options:</span></span>  
  
    1.  <span data-ttu-id="451c3-114">**[インフォキューブ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="451c3-114">Select **InfoCube**.</span></span> <span data-ttu-id="451c3-115">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="451c3-115">Then, click **Create**.</span></span> <span data-ttu-id="451c3-116">**[トランザクション データのインフォキューブの作成]** ダイアログ ボックスで、一覧のいずれかの行から **[IObject]** 列の **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="451c3-116">In the **Create InfoCube for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="451c3-117">各行は、パッケージのデータ フローの列を表します。</span><span class="sxs-lookup"><span data-stu-id="451c3-117">Each row represents a column in the data flow of the package.</span></span>  
  
    2.  <span data-ttu-id="451c3-118">**[インフォソース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="451c3-118">Select **InfoSource**.</span></span> <span data-ttu-id="451c3-119">**[Create]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="451c3-119">Then click **Create**.</span></span> <span data-ttu-id="451c3-120">**[インフォソースの作成]** ダイアログ ボックスで、 **[トランザクション データ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="451c3-120">In the **Create InfoSource** dialog box, select **Transaction data**.</span></span> <span data-ttu-id="451c3-121">**[トランザクション データのインフォソースの作成]** ダイアログ ボックスで、一覧のいずれかの行から **[IObject]** 列の **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="451c3-121">In the **Create InfoSource for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="451c3-122">各行は、パッケージのデータ フローの列を表します。</span><span class="sxs-lookup"><span data-stu-id="451c3-122">Each row represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="451c3-123">**[インフォソース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="451c3-123">Select **InfoSource**.</span></span> <span data-ttu-id="451c3-124">**[Create]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="451c3-124">Then click **Create**.</span></span> <span data-ttu-id="451c3-125">**[インフォソースの作成]** ダイアログ ボックスで、 **[マスター データ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="451c3-125">In the **Create InfoSource** dialog box, select **Master data**.</span></span> <span data-ttu-id="451c3-126">**[マスター データのインフォソースの作成]** ダイアログ ボックスで、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="451c3-126">In the **Create InfoSource for Master Data** dialog box, click **Look up**.</span></span>  
  
 <span data-ttu-id="451c3-127">**[インフォオブジェクトの参照]** ダイアログ ボックスは、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスの **[属性]** セクションで **[追加]** をクリックして開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="451c3-127">You can also open the **Look Up InfoObject** dialog box by clicking **Add** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="451c3-128">[参照] のオプション</span><span class="sxs-lookup"><span data-stu-id="451c3-128">Lookup Options</span></span>  
 <span data-ttu-id="451c3-129">参照フィールドで、アスタリスクのワイルドカード文字 (\*) を使用して、または部分的な文字列をアスタリスクのワイルドカード文字と組み合わせて使用して、結果をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="451c3-129">In the lookup field text boxes, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="451c3-130">ただし、参照フィールドを空にした場合、参照処理は、フィールドの空の文字列のみを検索します。</span><span class="sxs-lookup"><span data-stu-id="451c3-130">However, if you leave a lookup field empty, the lookup process will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="451c3-131">**特性**</span><span class="sxs-lookup"><span data-stu-id="451c3-131">**Characteristics**</span></span>  
 <span data-ttu-id="451c3-132">特性を表すインフォオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="451c3-132">Look up InfoObjects that represent characteristics.</span></span>  
  
 <span data-ttu-id="451c3-133">**単位**</span><span class="sxs-lookup"><span data-stu-id="451c3-133">**Units**</span></span>  
 <span data-ttu-id="451c3-134">単位を表すインフォオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="451c3-134">Look up InfoObjects that represent units.</span></span>  
  
 <span data-ttu-id="451c3-135">**主要データ**</span><span class="sxs-lookup"><span data-stu-id="451c3-135">**Key figures**</span></span>  
 <span data-ttu-id="451c3-136">主要データを表すインフォオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="451c3-136">Look up InfoObjects that represent key figures.</span></span>  
  
 <span data-ttu-id="451c3-137">**時間の特性**</span><span class="sxs-lookup"><span data-stu-id="451c3-137">**Time characteristics**</span></span>  
 <span data-ttu-id="451c3-138">時間の特性を表すインフォオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="451c3-138">Look up InfoObjects that represent time characteristics.</span></span>  
  
 <span data-ttu-id="451c3-139">**Name**</span><span class="sxs-lookup"><span data-stu-id="451c3-139">**Name**</span></span>  
 <span data-ttu-id="451c3-140">参照するインフォオブジェクトの名前、または部分的な名前をアスタリスクのワイルドカード文字 (\*) と入力します。</span><span class="sxs-lookup"><span data-stu-id="451c3-140">Enter the name of the InfoObject that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="451c3-141">すべてのインフォオブジェクトを含めるには、アスタリスクのワイルドカード文字を単独で使用します。</span><span class="sxs-lookup"><span data-stu-id="451c3-141">Or, use the asterisk wildcard character alone to include all InfoObjects.</span></span>  
  
 <span data-ttu-id="451c3-142">**説明**</span><span class="sxs-lookup"><span data-stu-id="451c3-142">**Description**</span></span>  
 <span data-ttu-id="451c3-143">アスタリスクのワイルドカード文字 (\*) と一緒に説明、または部分的な説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="451c3-143">Enter the description, or a partial description with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="451c3-144">説明にかからわずすべてのインフォオブジェクトを含めるには、アスタリスクのワイルドカード文字を単独で使用します。</span><span class="sxs-lookup"><span data-stu-id="451c3-144">Or, use the asterisk wildcard character alone to include all InfoObjects regardless of description.</span></span>  
  
 <span data-ttu-id="451c3-145">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="451c3-145">**Look up**</span></span>  
 <span data-ttu-id="451c3-146">SAP Netweaver BW システムで定義されている一致するインフォオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="451c3-146">Look up matching InfoObjects that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="451c3-147">参照結果</span><span class="sxs-lookup"><span data-stu-id="451c3-147">Lookup Results</span></span>  
 <span data-ttu-id="451c3-148">[参照] ボタンをクリックすると、SAP Netweaver BW システムのインフォオブジェクトの一覧が、次の列見出しのテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="451c3-148">After you click the Look up button, a list of the InfoObjects in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="451c3-149">**インフォオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="451c3-149">**InfoObject**</span></span>  
 <span data-ttu-id="451c3-150">SAP Netweaver BW システムで定義されたインフォオブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="451c3-150">Displays the name of the InfoObject that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="451c3-151">**テキスト (短い)**</span><span class="sxs-lookup"><span data-stu-id="451c3-151">**Text (short)**</span></span>  
 <span data-ttu-id="451c3-152">インフォオブジェクトに関連付けられた短いテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="451c3-152">Displays the short text that is associated with the InfoObject.</span></span>  
  
 <span data-ttu-id="451c3-153">使用できるインフォオブジェクトの一覧が表示されたら目的のインフォオブジェクトを選択すると、変換先で関連するオプションに必要な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="451c3-153">When the list of available InfoObjects appears, select the InfoObject that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="451c3-154">参照</span><span class="sxs-lookup"><span data-stu-id="451c3-154">See Also</span></span>  
 <span data-ttu-id="451c3-155">[[トランザクション データのインフォキューブの作成]](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="451c3-155">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="451c3-156">[[インフォソースの作成]](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="451c3-156">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="451c3-157">[トランザクション データのインフォソースの作成](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="451c3-157">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="451c3-158">[マスター データのインフォソースの作成](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="451c3-158">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 <span data-ttu-id="451c3-159">[新しいインフォオブジェクトの作成](create-new-infoobject.md) </span><span class="sxs-lookup"><span data-stu-id="451c3-159">[Create New InfoObject](create-new-infoobject.md) </span></span>  
 <span data-ttu-id="451c3-160">[SAP BW 変換先エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="451c3-160">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="451c3-161">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="451c3-161">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
