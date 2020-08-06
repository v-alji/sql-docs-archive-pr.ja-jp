---
title: 'レッスン 6: アプリケーションに ReportViewer コントロールを追加する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb04008fa47801f0500de711592a3cec45ca3dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644840"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="830f8-102">レッスン 6: アプリケーションに ReportViewer コントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="830f8-102">Lesson 6: Add a ReportViewer Control to the Application</span></span>
  <span data-ttu-id="830f8-103">レポート ウィザードを使用して子レポートを設計した後は、Web サイト アプリケーションに ReportViewer コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="830f8-103">After you design the child report by using the Report Wizard, your next step is to add a ReportViewer control to the website application.</span></span>  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="830f8-104">アプリケーションに ReportViewer コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="830f8-104">To add a ReportViewer control to the application</span></span>  
  
1.  <span data-ttu-id="830f8-105">**ソリューション エクスプローラー**で、 **Default.aspx**を右クリックし、 **[ビュー デザイナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="830f8-105">In **Solution Explorer**, right-click **Default.aspx**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="830f8-106">[**ツールボックス**] ウィンドウの [ **AJAX Extensions** ] グループから、 **ScriptManager**コントロールをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="830f8-106">From the **AJAX Extensions** group in the **Toolbox** window, drag a **ScriptManager** control to the design surface.</span></span>  
  
3.  <span data-ttu-id="830f8-107">**[レポート]** から **ReportViewer** コントロールをデザイン画面の **ScriptManager** コントロールの下にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="830f8-107">From the **Reporting** group, drag a **ReportViewer** control to the design surface below the **ScriptManager** control.</span></span>  
  
4.  <span data-ttu-id="830f8-108">**ReportViewer** コントロールの右上にある矢印をクリックして、 **[ReportViewer タスク]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="830f8-108">Open the **ReportViewer Tasks** window by clicking the arrow in the top right-hand corner of the **ReportViewer** control.</span></span>  
  
5.  <span data-ttu-id="830f8-109">[**レポートの選択**] ボックスで、作成した親レポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="830f8-109">In the **Choose Report** box, select Parent report you created.</span></span>  
  
     <span data-ttu-id="830f8-110">レポートを選択すると、レポートで使用されているデータ ソースのインスタンスが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="830f8-110">When you select a report, instances of data sources used in the report are created automatically.</span></span> <span data-ttu-id="830f8-111">それぞれの DataTable (とその [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) コンテナーを) をインスタンス化するためのコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="830f8-111">Code is generated to instantiate each DataTable (and its [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) container).</span></span> <span data-ttu-id="830f8-112">レポートで使用されているそれぞれのデータ ソースに対応する [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) コントロールがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="830f8-112">An [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) control is added to the design surface, corresponding to each data source used in the report.</span></span> <span data-ttu-id="830f8-113">このデータ ソース コントロールは自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="830f8-113">This data source control is configured automatically.</span></span>  
  
     <span data-ttu-id="830f8-114">Microsoft Visual Studio 2012 を使用している場合は、ObjectDataSource コントロールがプロジェクトの名前空間で完全に修飾されている DataSet1 にバインドされていることを確認してください ([**ビジネスオブジェクトの選択**] ボックスの一覧に完全修飾名が表示されている場合) (たとえば、DataSet1TableAdapters)。</span><span class="sxs-lookup"><span data-stu-id="830f8-114">If you're using Microsoft Visual Studio 2012, make sure that the ObjectDataSource control is bound with DataSet1 that is fully qualified with the project namespace, if the fully qualified name is listed in the **Choose your business object** drop-down list box (for example, Projectnamespace.DataSet1TableAdapters.ProductTableAdapter).</span></span> <span data-ttu-id="830f8-115">リストボックスにアクセスするには、ObjectDataSource を右クリックし、[**データソースの構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="830f8-115">You access the list box by right-clicking ObjectDataSource, and then clicking **Configure Data Source**.</span></span>  
  
6.  <span data-ttu-id="830f8-116">[ビルド] メニューの [Web サイトのビルド] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="830f8-116">On the Build menu, click Build website.</span></span>  
  
     <span data-ttu-id="830f8-117">レポートがコンパイルされ、レポート式の構文エラーなどのエラーが **[エラー一覧]** 領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="830f8-117">The report is compiled and any errors such as a syntax error in a report expression appear in the **Error List** area.</span></span> <span data-ttu-id="830f8-118">**[エラー一覧]** 領域を表示するには、Visual Studio ウィンドウの下部にある **[エラー一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="830f8-118">Click **Error List** at the bottom of the Visual Studio window to display the **Error List** area.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="830f8-119">次の作業</span><span class="sxs-lookup"><span data-stu-id="830f8-119">Next Task</span></span>  
 <span data-ttu-id="830f8-120">これで、Web サイト アプリケーションに ReportViewer コントロールを追加できました。</span><span class="sxs-lookup"><span data-stu-id="830f8-120">You have successfully added a ReportViewer control to the website application.</span></span> <span data-ttu-id="830f8-121">次は、親レポートにドリルスルー アクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="830f8-121">Next, you will add a drillthrough action on the parent report.</span></span>  
  
  
