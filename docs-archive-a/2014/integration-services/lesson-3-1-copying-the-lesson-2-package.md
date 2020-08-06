---
title: '手順 1: レッスン 2 のパッケージのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39bfc965febc401bd66b1077388021b8ccf52aed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715565"
---
# <a name="step-1-copying-the-lesson-2-package"></a><span data-ttu-id="cfc2f-102">手順 1:レッスン 2 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="cfc2f-102">Step 1: Copying the Lesson 2 Package</span></span>
  <span data-ttu-id="cfc2f-103">ここでは、レッスン 2 で作成した Lesson 2.dtsx パッケージのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-103">In this task, you will create a copy of the Lesson 2.dtsx package that you created in Lesson 2.</span></span> <span data-ttu-id="cfc2f-104">または、チュートリアルに含まれている、レッスン 2 を完了した状態のパッケージをプロジェクトに追加した後、コピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-104">Alternatively, you can add the completed lesson 2 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="cfc2f-105">レッスン 3 の実習では、このパッケージの新しいコピーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-105">You will use this new copy throughout the rest of Lesson 3.</span></span>  
  
### <a name="to-create-the-lesson-3-package"></a><span data-ttu-id="cfc2f-106">レッスン 3 のパッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="cfc2f-106">To create the Lesson 3 package</span></span>  
  
1.  <span data-ttu-id="cfc2f-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server 2012]** の順にポイントして、 **[SQL Server Data Tools]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="cfc2f-108">[**ファイル**] メニューの [**開く**] をクリックし、[**プロジェクト/ソリューション**] をクリックします。次に、[ **ssis チュートリアル**] を選択し、[**開く**] をクリックして、[ **ssis チュートリアル. .sln**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-108">On the **File** menu, click **Open**, click **Project/Solution**, select **SSIS Tutorial** and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="cfc2f-109">ソリューション エクスプローラーで、 **Lesson 2.dtsx**を右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-109">In Solution Explorer, right-click **Lesson 2.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="cfc2f-110">ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**貼り付け**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="cfc2f-111">コピーしたパッケージの既定の名前は、Lesson 3.dtsx です。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-111">By default, the copied package is named Lesson 3.dtsx.</span></span>  
  
5.  <span data-ttu-id="cfc2f-112">ソリューションエクスプローラーで、 **.dtsx**をダブルクリックしてパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-112">In Solution Explorer, double-click **Lesson 3.dtsx** to open the package.</span></span>  
  
6.  <span data-ttu-id="cfc2f-113">**[制御フロー]** タブの背景上で任意の場所を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-113">Right-click anywhere in the background of the **Control Flow** tab and click **Properties**.</span></span>  
  
7.  <span data-ttu-id="cfc2f-114">プロパティウィンドウで、 `Name` プロパティをに更新し `Lesson 3` ます。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-114">In the Properties window, update the `Name` property to `Lesson 3`.</span></span>  
  
8.  <span data-ttu-id="cfc2f-115">**[ID]** プロパティのボックスをクリックし、一覧で **[\<Generate New ID>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-115">Click the box for the **ID** property, and then in the list, click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson2-package"></a><span data-ttu-id="cfc2f-116">レッスン 2 を完了した状態のパッケージを追加するには</span><span class="sxs-lookup"><span data-stu-id="cfc2f-116">To add the completed Lesson2 package</span></span>  
  
1.  <span data-ttu-id="cfc2f-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を開いて、SSIS Tutorial プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="cfc2f-118">ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**既存のパッケージの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="cfc2f-119">**[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]** で、 **[ファイル システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="cfc2f-120">参照ボタン **[...]** をクリックし、コンピューター上の **Lesson 2.dtsx** に移動して、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-120">Click the browse **(...)** button, navigate to **Lesson 2.dtsx** on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="cfc2f-121">このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="cfc2f-122">「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="cfc2f-123">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="cfc2f-124">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="cfc2f-125">前の手順の手順 3 ～ 8 の説明に従って、レッスン 3 のパッケージをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="cfc2f-125">Copy and paste the Lesson 3 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="cfc2f-126">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="cfc2f-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="cfc2f-127">手順 2:ログ機能の追加と設定</span><span class="sxs-lookup"><span data-stu-id="cfc2f-127">Step 2: Adding and Configuring Logging</span></span>](lesson-3-2-adding-and-configuring-logging.md)  
  
  
