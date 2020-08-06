---
title: '手順 1: レッスン 5 のパッケージのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a25fcc13-987e-4f3d-8f0c-76f7e6e59920
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b30ec927084548a2371f22d857d5302e5dc84c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645745"
---
# <a name="step-1-copying-the-lesson-5-package"></a><span data-ttu-id="f016f-102">手順 1:レッスン 5 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="f016f-102">Step 1: Copying the Lesson 5 Package</span></span>
  <span data-ttu-id="f016f-103">ここでは、レッスン 5 で作成した Lesson 5.dtsx パッケージのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f016f-103">In this task, you will create a copy of the Lesson 5.dtsx package that you created in Lesson 5.</span></span> <span data-ttu-id="f016f-104">または、チュートリアルに含まれている、レッスン 5 を完了した状態のパッケージをプロジェクトに追加した後、コピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f016f-104">Alternatively, you can add the completed lesson 5 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="f016f-105">レッスン 6 の実習では、このパッケージの新しいコピーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f016f-105">You will use this new copy throughout the rest of Lesson 6.</span></span>  
  
### <a name="to-copy-the-lesson-5-package"></a><span data-ttu-id="f016f-106">レッスン 5 のパッケージをコピーするには</span><span class="sxs-lookup"><span data-stu-id="f016f-106">To copy the Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="f016f-107">SQL Server Data Tools がまだ開いていない場合は、[スタート] ボタンをクリックし、[すべてのプログラム]、[Microsoft SQL Server 2012] の順にポイントして、[SQL Server Data Tools] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-107">If SQL Server Data Tools is not already open, click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Server Data Tools.</span></span>  
  
2.  <span data-ttu-id="f016f-108">[ファイル] メニューの [開く] をクリックし、[プロジェクト/ソリューション] をクリックします。次に、[SSIS Tutorial] フォルダーをクリックして [開く] をクリックした後、SSIS Tutorial.sln をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-108">On the File menu, click Open, click Project/Solution, select SSIS Tutorial and click Open, and then double-click SSIS Tutorial.sln.</span></span>  
  
3.  <span data-ttu-id="f016f-109">ソリューション エクスプローラーで、Lesson 5.dtsx を右クリックし、[コピー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-109">In Solution Explorer, right-click Lesson 5.dtsx, and then click Copy.</span></span>  
  
4.  <span data-ttu-id="f016f-110">ソリューション エクスプローラーで [SSIS パッケージ] を右クリックし、[貼り付け] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-110">In Solution Explorer, right-click SSIS Packages, and then click Paste.</span></span>  
  
     <span data-ttu-id="f016f-111">コピーしたパッケージの既定の名前は、Lesson 6.dtsx です。</span><span class="sxs-lookup"><span data-stu-id="f016f-111">By default, the copied package is named Lesson 6.dtsx.</span></span>  
  
5.  <span data-ttu-id="f016f-112">ソリューション エクスプローラーで Lesson 6.dtsx をダブルクリックして、このパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="f016f-112">In the Solution Explorer, double-click Lesson 6.dtsx to open the package.</span></span>  
  
6.  <span data-ttu-id="f016f-113">[制御フロー] タブの背景上で任意の場所を右クリックし、[プロパティ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-113">Right-click anywhere in the background of the Control Flow tab then click Properties.</span></span>  
  
7.  <span data-ttu-id="f016f-114">[プロパティ] ウィンドウで、[Name] プロパティを「Lesson 6」に変更します。</span><span class="sxs-lookup"><span data-stu-id="f016f-114">In the Properties window, update the Name property to Lesson 6.</span></span>  
  
8.  <span data-ttu-id="f016f-115">[ID] プロパティのボックスをクリックし、ドロップダウン矢印をクリックし、 \<Generate New ID>をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-115">Click the box for the ID property, then click the dropdown arrow, and then click \<Generate New ID>.</span></span>  
  
### <a name="to-add-the-completed-lesson-5-package"></a><span data-ttu-id="f016f-116">レッスン 5 を完了した状態のパッケージを追加するには</span><span class="sxs-lookup"><span data-stu-id="f016f-116">To add the completed Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="f016f-117">SQL Server Data Tools を開き、SSIS Tutorial プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="f016f-117">Open SQL Server Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="f016f-118">ソリューション エクスプローラーで [SSIS パッケージ] を右クリックし、[既存のパッケージを追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-118">In Solution Explorer, right-click SSIS Packages, and click Add Existing Package.</span></span>  
  
3.  <span data-ttu-id="f016f-119">[既存のパッケージのコピーを追加] ダイアログ ボックスの [パッケージの場所] で、[ファイル システム] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-119">In the Add Copy of Existing Package dialog box, in Package location, select File system.</span></span>  
  
4.  <span data-ttu-id="f016f-120">参照ボタン ([...]) をクリックし、コンピューター上の Lesson 5.dtsx に移動して、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-120">Click the browse (...) button, Lesson 5.dtsx on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="f016f-121">このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f016f-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="f016f-122">「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。</span><span class="sxs-lookup"><span data-stu-id="f016f-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="f016f-123">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="f016f-124">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="f016f-125">前の手順の手順 3. ～ 8. の説明に従って、レッスン 5 パッケージをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f016f-125">Copy and paste the Lesson 5 package as described in steps 3-8 in the previous procedure.</span></span>  
  
     <span data-ttu-id="f016f-126">レッスン 5 パッケージをコピーした後で、ソリューション内に前のレッスンで使用したパッケージが現在存在している場合は、レッスン 1 ～ 5 の各パッケージを右クリックし、[プロジェクトから除外] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f016f-126">After copying the Lesson 5 package, if you currently have the packages from the previous lessons in your solution, right-click each package from lessons 1-5 and click Exclude From Project.</span></span> <span data-ttu-id="f016f-127">作業完了後は、ソリューション内にの Lesson 6.dtsx のみが存在しています。</span><span class="sxs-lookup"><span data-stu-id="f016f-127">When done you should have only Lesson 6.dtsx in your solution.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f016f-128">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="f016f-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f016f-129">手順 2:プロジェクトをプロジェクト配置モデルに変換する</span><span class="sxs-lookup"><span data-stu-id="f016f-129">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
  
