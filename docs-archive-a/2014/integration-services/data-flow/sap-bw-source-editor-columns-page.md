---
title: '[SAP BW ソース エディター] ([列] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba605360d01abc520cedfbc457dd89319ed83c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738551"
---
# <a name="sap-bw-source-editor-columns-page"></a><span data-ttu-id="ad6ff-102">[SAP BW ソース エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="ad6ff-102">SAP BW Source Editor (Columns Page)</span></span>
  <span data-ttu-id="ad6ff-103">**[SAP BW 変換元エディター]** の **[列]** ページを使用すると、出力列をそれぞれの外部 (ソース) 列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-103">Use the **Columns** page of the **SAP BW Source Editor** to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="ad6ff-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元コンポーネントの詳細については、「 [SAP BW Source](sap-bw-source.md)」(SAP BW 変換元) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ad6ff-105">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="ad6ff-106">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ad6ff-107">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="ad6ff-108">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="ad6ff-109">**[列] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="ad6ff-109">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="ad6ff-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="ad6ff-111">**[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="ad6ff-112">**[SAP BW 変換元エディター]** で、 **[列]** をクリックして **[列]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-112">In the **SAP BW Source Editor**, click **Columns** to open the **Columns** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ad6ff-113">オプション</span><span class="sxs-lookup"><span data-stu-id="ad6ff-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad6ff-114">変換元を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="ad6ff-115">**使用できる外部列**</span><span class="sxs-lookup"><span data-stu-id="ad6ff-115">**Available External Columns**</span></span>  
 <span data-ttu-id="ad6ff-116">データ ソース内の使用可能な外部列の一覧を表示し、データ フローに含める列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-116">View the list of available external columns in the data source, and then select the columns to be included in the data flow.</span></span>  
  
 <span data-ttu-id="ad6ff-117">列をデータ フローに含めるには、列名のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-117">To include a column in the data flow, select the check box that corresponds to that column.</span></span> <span data-ttu-id="ad6ff-118">チェック ボックスをオンにする順序は、列が出力される順序を決定します。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-118">The order in which you select the check boxes determines the order in which columns will be output.</span></span> <span data-ttu-id="ad6ff-119">つまり、オンにした最初のチェック ボックスは、最初の出力列、2 番目のチェック ボックスは 2 番目の出力列となります。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-119">That is, the first check box that you select will be the first output column, the second check box will be the second output columns, and so on.</span></span>  
  
 <span data-ttu-id="ad6ff-120">**[外部列]**</span><span class="sxs-lookup"><span data-stu-id="ad6ff-120">**External Column**</span></span>  
 <span data-ttu-id="ad6ff-121">選択した外部 (ソース) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-121">View the selected external (source) columns.</span></span> <span data-ttu-id="ad6ff-122">選択した列は、この変換元からのデータを使用する下流コンポーネントを構成するときの表示順と同じ順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-122">The selected columns appear in the order in which you will see their corresponding output columns when you configure downstream components that consume data from this source.</span></span>  
  
 <span data-ttu-id="ad6ff-123">列の順序を変更するには、 **[使用できる外部列]** の一覧で、すべての列のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-123">To change the order of the columns, in the **Available External Columns** list, clear the check boxes for all columns.</span></span> <span data-ttu-id="ad6ff-124">それから、表示したい順に列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-124">Then, select the columns in the order that you want them to appear.</span></span>  
  
 <span data-ttu-id="ad6ff-125">**出力列**</span><span class="sxs-lookup"><span data-stu-id="ad6ff-125">**Output Column**</span></span>  
 <span data-ttu-id="ad6ff-126">各出力列の一意な名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-126">Provide a unique name for each output column.</span></span> <span data-ttu-id="ad6ff-127">既定では選択された外部 (ソース) 列の名前です。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-127">The default is the name of the selected external (source) column.</span></span> <span data-ttu-id="ad6ff-128">ただし、一意のわかりやすい名前を入力できます。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-128">However, you can enter any unique, descriptive name.</span></span> [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="ad6ff-129">デザイナーで、このソースのデータを使用する下流コンポーネントを構成するときに、 **[出力列]** の名前が列に対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-129">Designer will display the **Output Column** names for the columns when you configure downstream components that consume data from this source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6ff-130">参照</span><span class="sxs-lookup"><span data-stu-id="ad6ff-130">See Also</span></span>  
 <span data-ttu-id="ad6ff-131">[SAP BW ソース エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="ad6ff-132">[SAP BW ソース エディター &#40;[エラー出力] ページ&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-132">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="ad6ff-133">[SAP BW ソース エディター &#40;[詳細設定] ページ&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="ad6ff-134">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="ad6ff-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
