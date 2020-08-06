---
title: '手順 1: レッスン 1 のパッケージのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43e117d82983bdaca8959fe7af8940d248ded97b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641072"
---
# <a name="step-1-copying-the-lesson-1-package"></a><span data-ttu-id="104a4-102">手順 1:レッスン 1 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="104a4-102">Step 1: Copying the Lesson 1 Package</span></span>
  <span data-ttu-id="104a4-103">ここでは、レッスン 1 で作成した Lesson 1.dtsx パッケージのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="104a4-103">In this task, you will create a copy of the Lesson 1.dtsx package that you created in Lesson 1.</span></span> <span data-ttu-id="104a4-104">レッスン 1 を終了していない場合は、チュートリアルに含まれている、レッスン 1 を完了した状態のパッケージをプロジェクトに追加した後、コピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="104a4-104">If you did not complete Lesson 1, you can add the completed lesson 1 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="104a4-105">レッスン 2 の実習では、このパッケージの新しいコピーを使用します。</span><span class="sxs-lookup"><span data-stu-id="104a4-105">You will use this new copy throughout the rest of Lesson 2.</span></span>  
  
### <a name="to-create-the-lesson-2-package"></a><span data-ttu-id="104a4-106">レッスン 2 のパッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="104a4-106">To create the Lesson 2 package</span></span>  
  
1.  <span data-ttu-id="104a4-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server 2012]** の順にポイントして、 **[SQL Server Data Tools]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="104a4-108">**[ファイル]** メニューの **[開く]** をクリックし、 **[プロジェクト/ソリューション]** をクリックします。次に、 **SSIS Tutorial** フォルダーをクリックして **[開く]** をクリックし、 **SSIS Tutorial.sln**をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-108">On the **File** menu, click **Open**, click **Project/Solution**, click the **SSIS Tutorial** folder and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="104a4-109">ソリューション エクスプローラーで、 **Lesson 1.dtsx**を右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-109">In Solution Explorer, right-click **Lesson 1.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="104a4-110">ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**貼り付け**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="104a4-111">既定では、コピーしたパッケージの名前は Lesson 2.dtsx になります。</span><span class="sxs-lookup"><span data-stu-id="104a4-111">By default, the copied package will be named Lesson 2.dtsx.</span></span>  
  
5.  <span data-ttu-id="104a4-112">ソリューションエクスプローラーで、[**レッスン 2. .dtsx** ] をダブルクリックしてパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="104a4-112">In Solution Explorer, double-click **Lesson 2.dtsx** to open the package</span></span>  
  
6.  <span data-ttu-id="104a4-113">**[制御フロー]** デザイン画面の背景上で任意の場所を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-113">Right-click anywhere in the background of the **Control Flow** design surface and click **Properties**.</span></span>  
  
7.  <span data-ttu-id="104a4-114">プロパティウィンドウで、 `Name` プロパティをに更新し `Lesson 2` ます。</span><span class="sxs-lookup"><span data-stu-id="104a4-114">In the Properties window, update the `Name` property to `Lesson 2`.</span></span>  
  
8.  <span data-ttu-id="104a4-115">**ID** プロパティのボックスをクリックし、ドロップダウン矢印をクリックし、 **\<Generate New ID>** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-115">Click the box for the **ID** property, click the dropdown arrow and then click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-1-package"></a><span data-ttu-id="104a4-116">レッスン 1 を完了した状態のパッケージを追加するには</span><span class="sxs-lookup"><span data-stu-id="104a4-116">To add the completed Lesson 1 package</span></span>  
  
1.  <span data-ttu-id="104a4-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools を開き、SSIS Tutorial プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="104a4-117">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="104a4-118">ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**既存のパッケージの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="104a4-119">**[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]** で、 **[ファイル システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="104a4-120">参照ボタン **[...]** をクリックし、コンピューター上の **Lesson 1.dtsx** に移動して、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-120">Click the browse **(...)** button, navigate to **Lesson 1.dtsx** on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="104a4-121">このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="104a4-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="104a4-122">「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。</span><span class="sxs-lookup"><span data-stu-id="104a4-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="104a4-123">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="104a4-124">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="104a4-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="104a4-125">前の手順の手順 3 ～ 8 の説明に従って、レッスン 3 のパッケージをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="104a4-125">Copy and paste the Lesson 1 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="104a4-126">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="104a4-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="104a4-127">手順 2:Foreach ループ コンテナーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="104a4-127">Step 2: Adding and Configuring the Foreach Loop Container</span></span>](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
  
