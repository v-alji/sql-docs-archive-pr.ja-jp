---
title: ReportViewer を使用してパラメーターを含むドリルスルー (.RDLC) レポートを作成する (SSRS チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02864ea8bdd80d6f46b7aad552fa30241322370c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738034"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a><span data-ttu-id="e8977-102">ReportViewer を使用してパラメーターを含む詳細 (RDLC) レポートを作成する (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="e8977-102">Create a Drillthrough (RDLC) Report with Parameters using ReportViewer (SSRS Tutorial)</span></span>
  <span data-ttu-id="e8977-103">[詳細](https://technet.microsoft.com/library/ff519554.aspx) レポートは、ユーザーが別のレポート内のリンクをクリックすることで開かれるレポートのことです。</span><span class="sxs-lookup"><span data-stu-id="e8977-103">A [drillthrough](https://technet.microsoft.com/library/ff519554.aspx) report is a report that a user opens by clicking a link within another report.</span></span> <span data-ttu-id="e8977-104">詳細レポートには、通常、元の要約レポートに含まれるアイテムについての詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e8977-104">Drillthrough reports commonly contain details about an item that is contained in an original summary report.</span></span> <span data-ttu-id="e8977-105">このチュートリアルでは、次のレッスンを通じて、[ローカル モード レポート](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)でパラメーターとクエリを使用した詳細レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8977-105">This tutorial will walk you through the following lessons of creating a drillthrough report with parameters and a query, in [local mode reporting](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8977-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="e8977-106">Requirements</span></span>  
 <span data-ttu-id="e8977-107">このチュートリアルを使用するには、 **AdventureWorks2008**サンプルデータベースへのアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="e8977-107">To use this walkthrough, you must have access to the **AdventureWorks2008** sample database.</span></span> <span data-ttu-id="e8977-108">このチュートリアルで使用するクエリは、 **AdventureWorks2012** database でも動作します。</span><span class="sxs-lookup"><span data-stu-id="e8977-108">The query used in this walkthrough will also work with **AdventureWorks2012** database.</span></span> <span data-ttu-id="e8977-109">**AdventureWorks2008**サンプルデータベースを取得する方法の詳細については、「チュートリアル: Microsoft Visual Studio 2010 用の[AdventureWorks データベースのインストール](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8977-109">For more information about how to get the **AdventureWorks2008** sample database, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) for Microsoft Visual Studio 2010.</span></span>  
  
 <span data-ttu-id="e8977-110">このチュートリアルでは、Transaction-SQL クエリおよび ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) および [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) オブジェクトを理解していることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="e8977-110">This walkthrough assumes that you are familiar with Transaction-SQL queries and ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) and [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) objects.</span></span>  
  
 <span data-ttu-id="e8977-111">Visual Studio 2010 または Visual Studio 2012 と ASP.NET Web サイト テンプレートを使用して、ReportViewer コントロールを含む ASP.NET Web ページを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8977-111">Use Visual Studio 2010, or Visual Studio 2012, and the ASP.NET website template to create an ASP.NET webpage with a ReportViewer control.</span></span> <span data-ttu-id="e8977-112">このコントロールは、ここで作成するレポートを表示するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="e8977-112">The control is configured to view a report that you create.</span></span> <span data-ttu-id="e8977-113">このチュートリアルでは、Microsoft Visual C# でアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8977-113">For this walkthrough, you create the application in Microsoft Visual C#.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="e8977-114">タスク</span><span class="sxs-lookup"><span data-stu-id="e8977-114">Tasks</span></span>  
 <span data-ttu-id="e8977-115">[レッスン 1: 新しい Web サイトを作成する](../reporting-services/lesson-1-create-a-new-web-site.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-115">[Lesson 1: Create a New Web Site](../reporting-services/lesson-1-create-a-new-web-site.md) </span></span>  
 <span data-ttu-id="e8977-116">[レッスン 2: 親レポートのデータ接続とデータテーブルを定義する](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-116">[Lesson 2: Define a Data Connection and Data Table for Parent Report](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span></span>  
 <span data-ttu-id="e8977-117">[レッスン 3: レポートウィザードを使用して親レポートをデザインする](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-117">[Lesson 3: Design the Parent Report using the Report Wizard](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="e8977-118">[レッスン 4: 子レポートのデータ接続とデータテーブルを定義する](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-118">[Lesson 4: Define a Data Connection and Data Table for Child Report](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span></span>  
 <span data-ttu-id="e8977-119">[レッスン 5: レポートウィザードを使用して子レポートをデザインする](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-119">[Lesson 5: Design the Child Report using the Report Wizard](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="e8977-120">[レッスン 6: アプリケーションに ReportViewer コントロールを追加する](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-120">[Lesson 6: Add a ReportViewer Control to the Application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span></span>  
 <span data-ttu-id="e8977-121">[レッスン 7: 親レポートにドリルスルーアクションを追加する](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-121">[Lesson 7: Add Drillthrough Action on Parent Report](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span></span>  
 <span data-ttu-id="e8977-122">[レッスン 8: データフィルターを作成する](../reporting-services/lesson-8-create-a-data-filter.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-122">[Lesson 8: Create a Data Filter](../reporting-services/lesson-8-create-a-data-filter.md) </span></span>  
 [<span data-ttu-id="e8977-123">レッスン 9: アプリケーションをビルドして実行する</span><span class="sxs-lookup"><span data-stu-id="e8977-123">Lesson 9: Build and Run the Application</span></span>](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="e8977-124">参照</span><span class="sxs-lookup"><span data-stu-id="e8977-124">See Also</span></span>  
 <span data-ttu-id="e8977-125">[SSRS&#41;&#40;チュートリアル Reporting Services](../reporting-services/reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e8977-125">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="e8977-126">レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e8977-126">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
