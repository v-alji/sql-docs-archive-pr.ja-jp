---
title: '[インフォパッケージの参照] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e45477e8faeed07faa114850e10a3bc4bbcf170
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715605"
---
# <a name="look-up-infopackage"></a><span data-ttu-id="97deb-102">[インフォパッケージの参照]</span><span class="sxs-lookup"><span data-stu-id="97deb-102">Look Up InfoPackage</span></span>
  <span data-ttu-id="97deb-103">SAP Netweaver BW システムで定義されたインフォパッケージを参照する場合、 **[インフォパッケージの参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="97deb-103">Use the **Look Up InfoPackage** dialog box to look up an InfoPackage that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="97deb-104">インフォパッケージの一覧が表示されたら、目的のインフォパッケージを選択します。変換先の関連するオプションに必要な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="97deb-104">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="97deb-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換先は、 **[プロセス チェーンの参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="97deb-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="97deb-106">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97deb-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97deb-107">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="97deb-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="97deb-108">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="97deb-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="97deb-109">**[インフォパッケージの参照] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="97deb-109">**To open the Look Up InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="97deb-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="97deb-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="97deb-111">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="97deb-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="97deb-112">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="97deb-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="97deb-113">**[接続マネージャー]** ページの **[インフォパッケージ/インフォソース]** で、 **[参照]** をクリックして **[インフォパッケージの参照]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="97deb-113">On the **Connection Manager** page, in the **InfoPackage/InfoSource** group box, click **Look up** to display the **Look Up InfoPackage** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="97deb-114">[参照] のオプション</span><span class="sxs-lookup"><span data-stu-id="97deb-114">Lookup Options</span></span>  
 <span data-ttu-id="97deb-115">参照フィールドで、アスタリスクのワイルドカード文字 (\*) を使用して、または部分的な文字列をアスタリスクのワイルドカード文字と組み合わせて使用して、結果をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="97deb-115">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="97deb-116">ただし、参照フィールドを空にした場合、参照操作は、フィールドの空の文字列のみを検索します。</span><span class="sxs-lookup"><span data-stu-id="97deb-116">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="97deb-117">**インフォパッケージ**</span><span class="sxs-lookup"><span data-stu-id="97deb-117">**InfoPackage**</span></span>  
 <span data-ttu-id="97deb-118">参照するインフォパッケージの名前、または部分的な名前をアスタリスクのワイルドカード文字 (\*) と入力します。</span><span class="sxs-lookup"><span data-stu-id="97deb-118">Enter the name of the InfoPackage that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="97deb-119">すべてのインフォパッケージを含めるには、アスタリスクのワイルドカード文字を単独で使用します。</span><span class="sxs-lookup"><span data-stu-id="97deb-119">Or, use the asterisk wildcard character alone to include all InfoPackages.</span></span>  
  
 <span data-ttu-id="97deb-120">**インフォソース**</span><span class="sxs-lookup"><span data-stu-id="97deb-120">**InfoSource**</span></span>  
 <span data-ttu-id="97deb-121">インフォソースの名前、または部分的な名前をアスタリスクのワイルドカード文字 (\*) と入力します。</span><span class="sxs-lookup"><span data-stu-id="97deb-121">Enter the name of the InfoSource, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="97deb-122">インフォソースにかからわずすべてのインフォパッケージを含めるには、アスタリスクのワイルドカード文字を単独で使用します。</span><span class="sxs-lookup"><span data-stu-id="97deb-122">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of InfoSource.</span></span>  
  
 <span data-ttu-id="97deb-123">**転送元システム**</span><span class="sxs-lookup"><span data-stu-id="97deb-123">**Source system**</span></span>  
 <span data-ttu-id="97deb-124">ソース システムの名前、または部分的な名前をアスタリスクのワイルドカード文字 (\*) と入力します。</span><span class="sxs-lookup"><span data-stu-id="97deb-124">Enter the name of the source system, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="97deb-125">ソース システムにかからわずすべてのインフォパッケージを含めるには、アスタリスクのワイルドカード文字を単独で使用します。</span><span class="sxs-lookup"><span data-stu-id="97deb-125">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of source systems.</span></span>  
  
 <span data-ttu-id="97deb-126">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="97deb-126">**Look up**</span></span>  
 <span data-ttu-id="97deb-127">SAP Netweaver BW システムで定義されている一致するインフォパッケージを参照します。</span><span class="sxs-lookup"><span data-stu-id="97deb-127">Look up matching InfoPackages that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="97deb-128">参照結果</span><span class="sxs-lookup"><span data-stu-id="97deb-128">Lookup Results</span></span>  
 <span data-ttu-id="97deb-129">[参照] ボタンをクリックすると、SAP Netweaver BW システムのインフォパッケージの一覧が、次の列見出しのテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="97deb-129">After you click the Look up button, a list of the InfoPackages in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="97deb-130">**インフォパッケージ**</span><span class="sxs-lookup"><span data-stu-id="97deb-130">**InfoPackage**</span></span>  
 <span data-ttu-id="97deb-131">SAP Netweaver BW システムで定義された InfoPackage の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="97deb-131">Displays the name of the InfoPackage that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="97deb-132">**Type**</span><span class="sxs-lookup"><span data-stu-id="97deb-132">**Type**</span></span>  
 <span data-ttu-id="97deb-133">インフォパッケージの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="97deb-133">Displays the type of the InfoPackage.</span></span> <span data-ttu-id="97deb-134">次の表に、種類として使用できる値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="97deb-134">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="97deb-135">値</span><span class="sxs-lookup"><span data-stu-id="97deb-135">Value</span></span>|<span data-ttu-id="97deb-136">説明</span><span class="sxs-lookup"><span data-stu-id="97deb-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="97deb-137">Trans.</span><span class="sxs-lookup"><span data-stu-id="97deb-137">Trans.</span></span>|<span data-ttu-id="97deb-138">トランザクション データ。</span><span class="sxs-lookup"><span data-stu-id="97deb-138">Transaction data.</span></span>|  
|<span data-ttu-id="97deb-139">Attr.</span><span class="sxs-lookup"><span data-stu-id="97deb-139">Attr.</span></span>|<span data-ttu-id="97deb-140">属性データ。</span><span class="sxs-lookup"><span data-stu-id="97deb-140">Attribute data.</span></span>|  
|<span data-ttu-id="97deb-141">テキスト</span><span class="sxs-lookup"><span data-stu-id="97deb-141">Texts</span></span>|<span data-ttu-id="97deb-142">テキスト。</span><span class="sxs-lookup"><span data-stu-id="97deb-142">Texts.</span></span>|  
  
 <span data-ttu-id="97deb-143">**説明**</span><span class="sxs-lookup"><span data-stu-id="97deb-143">**Description**</span></span>  
 <span data-ttu-id="97deb-144">インフォパッケージの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="97deb-144">Displays the description of the InfoPackage.</span></span>  
  
 <span data-ttu-id="97deb-145">**インフォソース**</span><span class="sxs-lookup"><span data-stu-id="97deb-145">**InfoSource**</span></span>  
 <span data-ttu-id="97deb-146">インフォパッケージに関連付けられているインフォソースの名前を表示します (ある場合)。</span><span class="sxs-lookup"><span data-stu-id="97deb-146">Displays the name of the InfoSource, if any, that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="97deb-147">**Source System**</span><span class="sxs-lookup"><span data-stu-id="97deb-147">**Source System**</span></span>  
 <span data-ttu-id="97deb-148">ソース システムの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="97deb-148">Displays the name of the source system.</span></span>  
  
 <span data-ttu-id="97deb-149">インフォパッケージの一覧が表示されたら、目的のインフォパッケージを選択します。変換先の関連するオプションに必要な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="97deb-149">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97deb-150">参照</span><span class="sxs-lookup"><span data-stu-id="97deb-150">See Also</span></span>  
 <span data-ttu-id="97deb-151">[SAP BW 変換先エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="97deb-151">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="97deb-152">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="97deb-152">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
