---
title: '[SAP BW 変換先エディター] ([マッピング] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dfa1f1d6-6b64-4331-bdc5-eaa8b7aa41a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c4c2803be3e2649f7425a2974dae8ac0a80fae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712221"
---
# <a name="sap-bw-destination-editor-mappings-page"></a><span data-ttu-id="136c1-102">[SAP BW 変換先エディター] ([マッピング] ページ)</span><span class="sxs-lookup"><span data-stu-id="136c1-102">SAP BW Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="136c1-103">**[SAP BW 変換先エディター]** ダイアログ ボックスの **[マッピング]** ページを使用すると、入力列を変換先列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="136c1-103">Use the **Mappings** page of the **SAP BW Destination Editor** to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="136c1-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換先の詳細については、「 [SAP BW 転送先](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="136c1-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="136c1-105">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="136c1-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="136c1-106">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="136c1-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="136c1-107">**[マッピング] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="136c1-107">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="136c1-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="136c1-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="136c1-109">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="136c1-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="136c1-110">**[SAP BW 変換先エディター]** で、 **[マッピング]** をクリックして **[マッピング]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="136c1-110">In the **SAP BW Destination Editor**, click **Mappings** to open the **Mappings** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="136c1-111">オプション</span><span class="sxs-lookup"><span data-stu-id="136c1-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="136c1-112">変換先を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="136c1-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="136c1-113">**[SAP BW 変換先エディター]** の **[マッピング]** ページは、次の 2 種類のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="136c1-113">The **Mappings** page of the **SAP BW Destination Editor consists** of two sections:</span></span>  
  
-   <span data-ttu-id="136c1-114">上側のセクションには、使用できる入力列と変換先列が表示され、これらの 2 種類の列の間のマッピングを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="136c1-114">The upper section shows the available input and destination columns and lets you create mappings between these two types of columns.</span></span>  
  
-   <span data-ttu-id="136c1-115">下側のセクションは、出力列にマップされた入力列のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="136c1-115">The lower section is a table that lists which input columns have been mapped to which output columns.</span></span>  
  
### <a name="upper-section-options"></a><span data-ttu-id="136c1-116">上側のセクションのオプション</span><span class="sxs-lookup"><span data-stu-id="136c1-116">Upper Section Options</span></span>  
 <span data-ttu-id="136c1-117">上側のセクションには次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="136c1-117">The upper section has the following options:</span></span>  
  
 <span data-ttu-id="136c1-118">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="136c1-118">**Available Input Columns**</span></span>  
 <span data-ttu-id="136c1-119">使用できる入力列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="136c1-119">View the list of available input columns.</span></span>  
  
 <span data-ttu-id="136c1-120">変換先列に入力列をマップするには、 **[使用できる変換先列]** の一覧の列に、 **[使用できる入力列]** の一覧から列をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="136c1-120">To map an input column to a destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="136c1-121">**使用できる変換先列**</span><span class="sxs-lookup"><span data-stu-id="136c1-121">**Available Destination Columns**</span></span>  
 <span data-ttu-id="136c1-122">使用できる変換先列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="136c1-122">View the list of available destination columns.</span></span>  
  
 <span data-ttu-id="136c1-123">変換先列に入力列をマップするには、 **[使用できる変換先列]** の一覧の列に、 **[使用できる入力列]** の一覧から列をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="136c1-123">To map an input column to destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="136c1-124">上側のセクションには、背景を右クリックすると開くことができるコンテキスト メニューがあります。</span><span class="sxs-lookup"><span data-stu-id="136c1-124">The upper section also has a context menu that you can open by right-clicking on the background.</span></span> <span data-ttu-id="136c1-125">このコンテキスト メニューでは次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="136c1-125">This context menu contains the following options:</span></span>  
  
-   <span data-ttu-id="136c1-126">**すべてのマッピングを選択**</span><span class="sxs-lookup"><span data-stu-id="136c1-126">**Select All Mappings**</span></span>  
  
-   <span data-ttu-id="136c1-127">**選択したマッピングの削除**</span><span class="sxs-lookup"><span data-stu-id="136c1-127">**Delete Selected Mappings**</span></span>  
  
-   <span data-ttu-id="136c1-128">**一致する名前でアイテムをマップする**</span><span class="sxs-lookup"><span data-stu-id="136c1-128">**Map Items by Matching Names**</span></span>  
  
### <a name="lower-section-columns"></a><span data-ttu-id="136c1-129">下側のセクションの列</span><span class="sxs-lookup"><span data-stu-id="136c1-129">Lower Section Columns</span></span>  
 <span data-ttu-id="136c1-130">下側のセクションはマッピング テーブルで、次の列があります。</span><span class="sxs-lookup"><span data-stu-id="136c1-130">The lower section is a table of the mappings, and has the following columns:</span></span>  
  
 <span data-ttu-id="136c1-131">**入力列**</span><span class="sxs-lookup"><span data-stu-id="136c1-131">**Input Column**</span></span>  
 <span data-ttu-id="136c1-132">選択した入力列を表示します。</span><span class="sxs-lookup"><span data-stu-id="136c1-132">View the input columns that you have selected.</span></span>  
  
 <span data-ttu-id="136c1-133">同じマップ先の列に別の入力列をマップするには、リストで別の入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="136c1-133">To map a different input column to the same destination column, select a different input column in the list.</span></span> <span data-ttu-id="136c1-134">マッピングを削除するには、 **[\<ignore>]** を選択して、出力から入力列を除外します。</span><span class="sxs-lookup"><span data-stu-id="136c1-134">To remove a mapping, select **\<ignore>** to exclude the input column from the output.</span></span>  
  
 <span data-ttu-id="136c1-135">**変換先列**</span><span class="sxs-lookup"><span data-stu-id="136c1-135">**Destination Column**</span></span>  
 <span data-ttu-id="136c1-136">マップされているかどうかにかかわらず、使用できる変換先列を表示します。</span><span class="sxs-lookup"><span data-stu-id="136c1-136">View each available destination column, regardless of whether that column is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136c1-137">参照</span><span class="sxs-lookup"><span data-stu-id="136c1-137">See Also</span></span>  
 <span data-ttu-id="136c1-138">[SAP BW 変換先エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="136c1-138">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="136c1-139">[SAP BW 変換先エディター &#40;[エラー出力] ページ&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="136c1-139">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="136c1-140">[SAP BW 変換先エディター &#40;[詳細設定] ページ&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="136c1-140">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="136c1-141">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="136c1-141">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
