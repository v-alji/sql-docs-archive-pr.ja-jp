---
title: プレビュー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a795338122c1e7a37a23fdb6af6153f74b927e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633925"
---
# <a name="preview"></a><span data-ttu-id="10f6f-102">プレビュー</span><span class="sxs-lookup"><span data-stu-id="10f6f-102">Preview</span></span>
  <span data-ttu-id="10f6f-103">SAP BW 変換元が抽出するデータをプレビューするには、 **[プレビュー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="10f6f-103">Use the **Preview** dialog box to preview the data that the SAP BW source will extract.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="10f6f-104">**[プレビュー]** オプションは **[SAP BW 変換元エディター]** の **[接続マネージャー]** ページで使用でき、実際にデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="10f6f-104">The **Preview** option, that is available on the **Connection Manager** page of the **SAP BW Source Editor**, actually extracts data.</span></span> <span data-ttu-id="10f6f-105">前の抽出以降に変更されたデータのみを抽出するように SAP Netweaver BW を構成している場合、 **[プレビュー]** を選択すると、次の抽出からプレビュー データを除外します。</span><span class="sxs-lookup"><span data-stu-id="10f6f-105">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="10f6f-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元コンポーネントの詳細については、「 [SAP BW Source](sap-bw-source.md)」(SAP BW 変換元) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="10f6f-106">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="10f6f-107">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="10f6f-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="10f6f-108">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10f6f-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="10f6f-109">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="10f6f-109">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="10f6f-110">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="10f6f-110">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="10f6f-111">**[プレビュー] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="10f6f-111">**To open the Preview dialog box**</span></span>  
  
1.  <span data-ttu-id="10f6f-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="10f6f-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="10f6f-113">**[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="10f6f-113">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="10f6f-114">**[SAP BW 変換元エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="10f6f-114">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="10f6f-115">SAP BW 変換元を構成します。</span><span class="sxs-lookup"><span data-stu-id="10f6f-115">Configure the SAP BW source.</span></span>  
  
5.  <span data-ttu-id="10f6f-116">SAP BW 変換元を構成したら、 **[接続マネージャー]** ページで **[プレビュー]** をクリックし、 **[プレビュー]** ダイアログ ボックスでデータをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="10f6f-116">After you configure the SAP BW source, on the **Connection Manager** page, click **Preview** to preview the data in the **Preview** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="10f6f-117">**[プレビュー]** をクリックすると、 **[要求のログ]** ダイアログ ボックスも表示されます。</span><span class="sxs-lookup"><span data-stu-id="10f6f-117">Clicking **Preview** also opens the **Request Log** dialog box.</span></span> <span data-ttu-id="10f6f-118">このダイアログ ボックスの詳細については、「 [Request Log](request-log.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="10f6f-118">For more information about this dialog box, see [Request Log](request-log.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="10f6f-119">Options</span><span class="sxs-lookup"><span data-stu-id="10f6f-119">Options</span></span>  
 <span data-ttu-id="10f6f-120">**[プレビュー]** ダイアログ ボックスには、SAP Netweaver BW システムから要求された行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="10f6f-120">The **Preview** dialog box displays the rows that are requested from the SAP Netweaver BW system.</span></span> <span data-ttu-id="10f6f-121">表示される列は、ソース データで定義された列です。</span><span class="sxs-lookup"><span data-stu-id="10f6f-121">The columns that are displayed are the columns that are defined in the source data.</span></span>  
  
 <span data-ttu-id="10f6f-122">このダイアログ ボックスに他のオプションはありません。</span><span class="sxs-lookup"><span data-stu-id="10f6f-122">There are no other options in this dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f6f-123">参照</span><span class="sxs-lookup"><span data-stu-id="10f6f-123">See Also</span></span>  
 <span data-ttu-id="10f6f-124">[SAP BW ソース エディター &#40;[接続マネージャー] ページ&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="10f6f-124">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="10f6f-125">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="10f6f-125">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
