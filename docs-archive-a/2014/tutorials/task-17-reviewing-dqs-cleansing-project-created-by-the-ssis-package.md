---
title: '作業 17: SSIS パッケージによって作成された DQS クレンジングプロジェクトを確認する |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0876a0b727e810f8834fcf5445958bf9884a87f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711169"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a><span data-ttu-id="53c69-102">タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する</span><span class="sxs-lookup"><span data-stu-id="53c69-102">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>
  <span data-ttu-id="53c69-103">ここでは、DQS クライアントで SSIS パッケージにより作成された DQS プロジェクトを開き、クレンジング プロセスの結果を確認し、必要に応じてインタラクティブなクレンジングを実行し、結果をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="53c69-103">In this task, you open the DQS project created by the SSIS package in DQS Client, review the results from the cleansing process, and optionally perform interactive cleansing and export the results.</span></span>  
  
1.  <span data-ttu-id="53c69-104">**Data Quality Client**を起動します。</span><span class="sxs-lookup"><span data-stu-id="53c69-104">Launch **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="53c69-105">[**管理**] ウィンドウで [**アクティビティの監視**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53c69-105">Click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
3.  <span data-ttu-id="53c69-106">**アクティビティの開始時刻**に基づいて一覧を並べ替え、最新のレコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="53c69-106">Sort the list based on **Activity Start Time** to see the latest record.</span></span>  
  
4.  <span data-ttu-id="53c69-107">プロジェクトの名前が次の形式で表示されていることに注意してください: **Cleansupplier Data. GUID**。</span><span class="sxs-lookup"><span data-stu-id="53c69-107">Notice that you see a name of the project in the following format: **CleanseAndCurate.Cleanse Supplier Data.GUID**.</span></span>  
  
     <span data-ttu-id="53c69-108">![SSIS パッケージによって作成された DQS クレンジング プロジェクト](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "SSIS パッケージによって作成された DQS クレンジング プロジェクト")</span><span class="sxs-lookup"><span data-stu-id="53c69-108">![DQS Cleansing Project Created by SSIS Package](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "DQS Cleansing Project Created by SSIS Package")</span></span>  
  
5.  <span data-ttu-id="53c69-109">[**アクティブ**] フィールドの値が [**アクティブ**] になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="53c69-109">Notice that the value in the **Is Active** field is **Active**.</span></span>  
  
6.  <span data-ttu-id="53c69-110">下のペインの [**プロファイラー** ] タブをクリックすると、SSIS パッケージによって実行されたクレンジングアクティビティのプロファイラーの統計情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="53c69-110">Click **Profiler** tab in the bottom pane to see profiler statistics for the Cleansing activity that the SSIS package performed.</span></span>  
  
7.  <span data-ttu-id="53c69-111">[**閉じる**] をクリックして、**管理**画面を閉じます。</span><span class="sxs-lookup"><span data-stu-id="53c69-111">Click **Close** to close the **Administration** screen.</span></span>  
  
8.  <span data-ttu-id="53c69-112">**DQS クライアント**のメインページで、[**データ品質プロジェクト**] ペインの [**データ品質プロジェクトを開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53c69-112">In the main page of **DQS Client**, click **Open Data Quality Project** in the **Data Quality Projects** pane.</span></span>  
  
9. <span data-ttu-id="53c69-113">プロジェクトの一覧で、SSIS DQS クレンジング コンポーネントによって作成されたプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="53c69-113">In the list of projects, select the project created by SSIS DQS Cleansing component.</span></span> <span data-ttu-id="53c69-114">プロジェクトの名前は、次の形式で指定する必要があります: **Cleanseandcurate。 (赤)**。</span><span class="sxs-lookup"><span data-stu-id="53c69-114">The name of the project should be in format:  **CleanseAndCurate.Cleanse Supplier Data.GUID (in red color)**.</span></span> <span data-ttu-id="53c69-115">[**作成日**] 列に基づいて一覧を並べ替え、最新のレコードを検索することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="53c69-115">You may need to sort the list based on **Date Created** column and look for the latest record.</span></span>  
  
10. <span data-ttu-id="53c69-116">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53c69-116">Click **Next**.</span></span>  
  
11. <span data-ttu-id="53c69-117">[**結果の管理と表示**] ページは、このチュートリアルの前の手順で行った対話型のクレンジングから理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="53c69-117">The **Manage and View Results** page should be familiar to you from the interactive cleansing you did earlier in this tutorial.</span></span>  
  
12. <span data-ttu-id="53c69-118">クレンジングの結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="53c69-118">Review the cleansing results.</span></span> <span data-ttu-id="53c69-119">また、インタラクティブなクレンジングを実行し、Excel ファイルや次のページのデータベースに結果をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="53c69-119">You can also perform interactive cleansing and export results to an Excel file or to a database in the next page.</span></span>  
  
13. <span data-ttu-id="53c69-120">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53c69-120">Click **Next**.</span></span> <span data-ttu-id="53c69-121">この**エクスポート**ページでは、excel ファイル、CSV ファイル、または SQL データベースに結果をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="53c69-121">In this **Export** page, you can export results to an excel file, CSV file, or to a SQL database.</span></span>  
  
14. <span data-ttu-id="53c69-122">[**完了**] をクリックして活動を終了します。</span><span class="sxs-lookup"><span data-stu-id="53c69-122">Click **Finish** to finish the activity.</span></span>  
  
15. <span data-ttu-id="53c69-123">**DQS クライアント**のメインページで、[**管理**] ウィンドウの [**アクティビティの監視**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53c69-123">In the main page of **DQS Client**, click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
16. <span data-ttu-id="53c69-124">プロジェクトの**IsActive**フィールドの値が [**終了**] になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="53c69-124">Notice that the value of **IsActive** field for the project is **Ended** now.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="53c69-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="53c69-125">Next Step</span></span>  
 [<span data-ttu-id="53c69-126">まとめ</span><span class="sxs-lookup"><span data-stu-id="53c69-126">Conclusion</span></span>](../../2014/tutorials/conclusion.md)  
  
  
