---
title: '[プロセス チェーンの参照] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f6303ea4-fbbf-4cba-bc60-828df62be8c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e0d3743071d018a8a82f60eeaf04fd86dec3e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715602"
---
# <a name="look-up-process-chain"></a><span data-ttu-id="42f1b-102">[プロセス チェーンの参照]</span><span class="sxs-lookup"><span data-stu-id="42f1b-102">Look Up Process Chain</span></span>
  <span data-ttu-id="42f1b-103">SAP Netweaver BW システムで定義されたプロセス チェーンを参照する場合、 **[プロセス チェーンの参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-103">Use the **Look Up Process Chain** dialog box to look up a process chain that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="42f1b-104">使用できるプロセス チェーンの一覧が表示されたら目的のチェーンを選択すると、関連するオプションに必要な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="42f1b-104">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="42f1b-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元は、 **[プロセス チェーンの参照]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-105">The SAP BW source of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="42f1b-106">SAP BW 変換元の詳細については、「 [SAP BW Source](sap-bw-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42f1b-106">To learn more about the SAP BW source, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="42f1b-107">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="42f1b-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="42f1b-108">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="42f1b-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="42f1b-109">**[プロセス チェーンの参照] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="42f1b-109">**To open the Look Up Process Chain dialog box**</span></span>  
  
1.  <span data-ttu-id="42f1b-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="42f1b-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="42f1b-111">**[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="42f1b-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="42f1b-112">**[SAP BW 変換元エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="42f1b-112">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="42f1b-113">**[プロセス チェーン]** で、 **[プロセス チェーンの参照]** ダイアログ ボックスを表示するには、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42f1b-113">In the **Process Chain** group box, click **Look up** to display the **Look Up Process Chain** dialog box.</span></span>  
  
     <span data-ttu-id="42f1b-114">**[プロセス チェーン]** は、 **[実行モード]** の値が **[P - プロセス チェーンをトリガー]** の場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="42f1b-114">The **Process Chain** group box appears only if the value for **Execution mode** is **P - Trigger process chain**.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="42f1b-115">[参照] のオプション</span><span class="sxs-lookup"><span data-stu-id="42f1b-115">Lookup Options</span></span>  
 <span data-ttu-id="42f1b-116">参照フィールドで、アスタリスクのワイルドカード文字 (\*) を使用して、または部分的な文字列をアスタリスクのワイルドカード文字と組み合わせて使用して、結果をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="42f1b-116">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="42f1b-117">ただし、参照フィールドを空にした場合、参照操作は、フィールドの空の文字列のみを検索します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-117">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="42f1b-118">**プロセス チェーン**</span><span class="sxs-lookup"><span data-stu-id="42f1b-118">**Process chain**</span></span>  
 <span data-ttu-id="42f1b-119">参照するプロセス チェーンの名前、または部分的な名前をアスタリスクのワイルドカード文字 (\*) と入力します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-119">Enter the name of the process chain that you want to look up, or enter a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="42f1b-120">すべてのプロセス チェーンを含めるには、アスタリスクのワイルドカード文字を単独で使用します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-120">Or, use the asterisk wildcard character alone to include all process chains.</span></span>  
  
 <span data-ttu-id="42f1b-121">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="42f1b-121">**Look up**</span></span>  
 <span data-ttu-id="42f1b-122">SAP Netweaver BW システムで定義されている一致するプロセス チェーンを参照します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-122">Look up matching process chains that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="42f1b-123">参照結果</span><span class="sxs-lookup"><span data-stu-id="42f1b-123">Lookup Results</span></span>  
 <span data-ttu-id="42f1b-124">[参照] ボタンをクリックすると、SAP Netweaver BW システムのプロセス チェーンの一覧が、次の列見出しのテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="42f1b-124">After you click the Look up button, a list of the process chains in the SAP Netweaver BW system appears in a table with the following column headings:</span></span>  
  
 <span data-ttu-id="42f1b-125">**[プロセス チェーン]**</span><span class="sxs-lookup"><span data-stu-id="42f1b-125">**Process Chain**</span></span>  
 <span data-ttu-id="42f1b-126">SAP Netweaver BW システムで定義されたプロセス チェーンの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-126">Displays the name of the process chain that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="42f1b-127">**説明**</span><span class="sxs-lookup"><span data-stu-id="42f1b-127">**Description**</span></span>  
 <span data-ttu-id="42f1b-128">プロセス チェーンの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="42f1b-128">Displays the description of the process chain.</span></span>  
  
 <span data-ttu-id="42f1b-129">使用できるプロセス チェーンの一覧が表示されたら目的のチェーンを選択すると、関連するオプションに必要な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="42f1b-129">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f1b-130">参照</span><span class="sxs-lookup"><span data-stu-id="42f1b-130">See Also</span></span>  
 <span data-ttu-id="42f1b-131">[SAP BW ソース エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="42f1b-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="42f1b-132">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="42f1b-132">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
