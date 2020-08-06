---
title: 'レッスン 5: レポート ウィザードを使用して子レポートを設計する | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f188a914fc2a2bb8370843191a31474a54c02aa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632971"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="09421-102">レッスン 5: レポート ウィザードを使用して子レポートを設計する</span><span class="sxs-lookup"><span data-stu-id="09421-102">Lesson 5: Design the Child Report using the Report Wizard</span></span>
  <span data-ttu-id="09421-103">子レポートのデータ接続とデータ テーブルを作成した後は、レポート デザイナーのレポート ウィザードを使用して子レポートを設計します。</span><span class="sxs-lookup"><span data-stu-id="09421-103">After you create a data connection and data table for the child report, your next step is to design the child report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="09421-104">レポート デザイナーの詳細については、「[レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09421-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="09421-105">レポート ウィザードを使用して子レポートを設計するには</span><span class="sxs-lookup"><span data-stu-id="09421-105">To design the child report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="09421-106">**ソリューション エクスプローラー**でトップレベル Web サイトが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="09421-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="09421-107">Web サイトを右クリックし、 **[新しい項目の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="09421-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="09421-108">[**新しい項目の追加**] ダイアログボックスで、[**レポートウィザード**] をクリックし、レポートファイルの名前を入力して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="09421-108">In the **Add New Item** dialog box, click **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="09421-109">これにより、レポート ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="09421-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="09421-110">[データ**セットのプロパティ**] ページの [**データソース**] ボックスで、[ **DataSet2**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="09421-110">In the **Dataset Properties** page, in the **Data source** box, click **DataSet2**.</span></span>  
  
     <span data-ttu-id="09421-111">作成した DataTable で **[使用できるデータセット]** ボックスが自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="09421-111">The **Available datasets** box is automatically updated with the DataTable you created.</span></span>  
  
5.  <span data-ttu-id="09421-112">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="09421-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="09421-113">**[フィールドの配置]** ページで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="09421-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="09421-114">**[ProductID]** 、 **[PurchaseOrderID]** 、 **[PurchaseOrderDetailID]** 、 **[OrderQty]** 、 **[ReceivedQty]** 、 **[RejectedQty]** 、および **[StockedQty]** を、 **[使用できるフィールド]** から **[値]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="09421-114">Drag **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**, and **StockedQty** from **Available Fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="09421-115">[ **Sum (ProductID)**]、[ **sum (PurchaseOrderID)**]、[ **sum (PurchaseOrderDetailID)**]、[sum ( **OrderQty)**]、[ **Sum (ReceivedQty)**]、[Sum **(RejectedQty)**]、および [ **sum (StockedQty)** ] の横にある矢印をクリックし、**合計**の選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="09421-115">Click the arrow next to **Sum(ProductID)**, **Sum(PurchaseOrderID)**, **Sum(PurchaseOrderDetailID)**, **Sum(OrderQty)**, **Sum(ReceivedQty)**, **Sum(RejectedQty)**, and **Sum(StockedQty)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="09421-116">[**次へ**] を2回クリックし、[**完了**] をクリックして**レポートウィザード**を閉じます。</span><span class="sxs-lookup"><span data-stu-id="09421-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="09421-117">これで .rdlc ファイルが作成されました。</span><span class="sxs-lookup"><span data-stu-id="09421-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="09421-118">このファイルはレポート デザイナーで開くことができます。</span><span class="sxs-lookup"><span data-stu-id="09421-118">The file opens in Report Designer.</span></span> <span data-ttu-id="09421-119">設計した Tablix がデザイン画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="09421-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="09421-120">.rdlc ファイルが開かれた状態で、次の手順を実行してパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="09421-120">With the .rdlc file open, add a parameter by doing the following:</span></span>  
  
    1.  <span data-ttu-id="09421-121">**レポートデータ**ペインで [**パラメーター** ] をクリックし、[**パラメーターの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="09421-121">Click **Parameters** in the **Report Data** pane, and then click **Add Parameters**.</span></span>  
  
    2.  <span data-ttu-id="09421-122">**[名前]** ボックスに **productid** を入力します。</span><span class="sxs-lookup"><span data-stu-id="09421-122">Enter **productid** in the **Name** box.</span></span>  
  
    3.  <span data-ttu-id="09421-123">**[データ型]** リスト ボックスで **[整数]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="09421-123">Confirm that **Integer** is selected in the **Data Type** list box.</span></span>  
  
    4.  <span data-ttu-id="09421-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="09421-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="09421-125">.rdlc ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="09421-125">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="09421-126">次の作業</span><span class="sxs-lookup"><span data-stu-id="09421-126">Next Task</span></span>  
 <span data-ttu-id="09421-127">これで、レポート ウィザードを使用して子レポートを設計できました。</span><span class="sxs-lookup"><span data-stu-id="09421-127">You have successfully designed the child report by using the Report Wizard.</span></span> <span data-ttu-id="09421-128">次は、Web サイト アプリケーションに ReportViewer コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="09421-128">Next, you will add a ReportViewer control to the website application.</span></span>  
  
  
