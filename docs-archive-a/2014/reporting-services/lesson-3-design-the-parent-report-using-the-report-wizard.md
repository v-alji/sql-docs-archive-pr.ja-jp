---
title: 'レッスン 3: レポート ウィザードを使用して親レポートを設計する | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3cb6a0972a2bb63e82e80c02b3ce90912ba01c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632977"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="4e40e-102">レッスン 3: レポート ウィザードを使用して親レポートを設計する</span><span class="sxs-lookup"><span data-stu-id="4e40e-102">Lesson 3: Design the Parent Report using the Report Wizard</span></span>
  <span data-ttu-id="4e40e-103">親レポートのデータ接続とデータ テーブルを作成した後は、レポート デザイナーのレポート ウィザードを使用して親レポートを設計します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-103">After you create a data connection and a data table for the parent report, your next step is to design the parent report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="4e40e-104">レポート デザイナーの詳細については、「[レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e40e-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="4e40e-105">レポート ウィザードを使用して親レポートを設計するには</span><span class="sxs-lookup"><span data-stu-id="4e40e-105">To design the parent report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="4e40e-106">**ソリューション エクスプローラー**でトップレベル Web サイトが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="4e40e-107">Web サイトを右クリックし、 **[新しい項目の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="4e40e-108">[**新しい項目の追加**] ダイアログボックスで [**レポートウィザード**] を選択し、レポートファイルの名前を入力して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e40e-108">In the **Add New Item** dialog box, select **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="4e40e-109">これにより、レポート ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="4e40e-110">**[データセットのプロパティ]** ページの **[データ ソース]** ボックスで、「 **レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する** 」で作成した [DataSet1](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-110">On the **Dataset Properties** page, in the **Data source** box, select the **DataSet1** you created in [Lesson 2: Define a Data Connection and Data Table for Parent Report](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).</span></span>  
    <span data-ttu-id="4e40e-111">上の手順で作成した **DataTable** で **[使用できるデータセット]** ボックスが自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="4e40e-111">The **Available datasets** box is automatically updated with the **DataTable** you created above.</span></span>  
  
5.  <span data-ttu-id="4e40e-112">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e40e-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="4e40e-113">**[フィールドの配置]** ページで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4e40e-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="4e40e-114">**[ProductID]** 、 **[Name]** 、 **[ProductNumber]** 、 **[SafetyStockLevel]** 、および **[ReorderLevel]** を、 **[使用できるフィールド]** から **&gt;[値]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4e40e-114">Drag **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**, and **ReorderLevel** from **Available fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="4e40e-115">**Sum (ProductID)**、 **sum (saf**)、sum **(ReorderLevel)** の横にある矢印をクリックし、**合計**の選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-115">Click the arrow next to **Sum(ProductID)**, **Sum(SafetyStockLevel)**, **Sum(ReorderLevel)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="4e40e-116">[**次へ**] を2回クリックし、[**完了**] をクリックして**レポートウィザード**を閉じます。</span><span class="sxs-lookup"><span data-stu-id="4e40e-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="4e40e-117">これで .rdlc ファイルが作成されました。</span><span class="sxs-lookup"><span data-stu-id="4e40e-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="4e40e-118">このファイルはレポート デザイナーで開くことができます。</span><span class="sxs-lookup"><span data-stu-id="4e40e-118">The file opens in Report Designer.</span></span> <span data-ttu-id="4e40e-119">設計した Tablix がデザイン画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e40e-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="4e40e-120">.rdlc ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-120">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="4e40e-121">次の作業</span><span class="sxs-lookup"><span data-stu-id="4e40e-121">Next Task</span></span>  
 <span data-ttu-id="4e40e-122">これで、レポート ウィザードを使用して親レポートを設計できました。</span><span class="sxs-lookup"><span data-stu-id="4e40e-122">You have successfully designed the parent report using the Report Wizard.</span></span> <span data-ttu-id="4e40e-123">次は、子レポートのデータ接続とデータ テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e40e-123">Next, you will create a data connection and a data table for the child report.</span></span>  
  
  
