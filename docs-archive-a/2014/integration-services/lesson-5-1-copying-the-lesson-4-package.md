---
title: '手順 1: レッスン 4 のパッケージのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1140c0e7d26f11f79e18d42143c1ed084c4ff144
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645177"
---
# <a name="step-1-copying-the-lesson-4-package"></a><span data-ttu-id="9b375-102">手順 1:レッスン 4 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="9b375-102">Step 1: Copying the Lesson 4 Package</span></span>
  <span data-ttu-id="9b375-103">ここでは、レッスン 4 で作成した Lesson 4.dtsx パッケージのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b375-103">In this task, you will create a copy of the Lesson 4.dtsx package that you created in Lesson 4.</span></span> <span data-ttu-id="9b375-104">または、チュートリアルに含まれている、レッスン 4 を完了した状態のパッケージをプロジェクトに追加した後、コピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9b375-104">Alternatively, you can add the completed lesson 4 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="9b375-105">レッスン 5 の実習では、このパッケージの新しいコピーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b375-105">You will use this new copy throughout the rest of Lesson 5.</span></span>  
  
### <a name="to-copy-the-lesson-4-package"></a><span data-ttu-id="9b375-106">レッスン 4 のパッケージをコピーするには</span><span class="sxs-lookup"><span data-stu-id="9b375-106">To copy the Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="9b375-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server 2012]** の順にポイントして、 **[SQL Server Data Tools]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="9b375-108">[**ファイル**] メニューの [**開く**] をクリックし、[**プロジェクト/ソリューション**] をクリックします。次に、[ **ssis チュートリアル**] を選択し、[**開く**] をクリックして、[ **ssis チュートリアル. .sln**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-108">On the **File** menu, click **Open**, click **Project/Solution**, select **SSIS Tutorial** and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="9b375-109">ソリューション エクスプローラーで、 **Lesson 4.dtsx**を右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-109">In Solution Explorer, right-click **Lesson 4.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="9b375-110">ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**貼り付け**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="9b375-111">コピーしたパッケージの既定の名前は、Lesson 5.dtsx です。</span><span class="sxs-lookup"><span data-stu-id="9b375-111">By default, the copied package is named Lesson 5.dtsx.</span></span>  
  
5.  <span data-ttu-id="9b375-112">ソリューション エクスプローラーで **Lesson 5.dtsx** をダブルクリックして、このパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="9b375-112">In the Solution Explorer, double-click **Lesson 5.dtsx** to open the package.</span></span>  
  
6.  <span data-ttu-id="9b375-113">[**制御フロー** ] タブの背景の任意の場所を右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-113">Right-click anywhere in the background of the **Control Flow** tab then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="9b375-114">プロパティウィンドウで、 `Name` プロパティをに更新し `Lesson 5` ます。</span><span class="sxs-lookup"><span data-stu-id="9b375-114">In the Properties window, update the `Name` property to `Lesson 5`.</span></span>  
  
8.  <span data-ttu-id="9b375-115">[ **ID** ] プロパティのボックスをクリックし、ドロップダウン矢印をクリックして、[] をクリックし **\<Generate New ID>** ます。</span><span class="sxs-lookup"><span data-stu-id="9b375-115">Click the box for the **ID** property, then click the dropdown arrow, and then click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-4-package"></a><span data-ttu-id="9b375-116">レッスン 4 を完了した状態のパッケージを追加するには</span><span class="sxs-lookup"><span data-stu-id="9b375-116">To add the completed Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="9b375-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools を開き、SSIS Tutorial プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="9b375-117">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="9b375-118">ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**既存のパッケージの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="9b375-119">**[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]** で、 **[ファイル システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="9b375-120">参照ボタン **([...])** をクリックし、コンピューターの **.dtsx**に移動して、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-120">Click the browse **(...)** button, navigate to **Lesson 4.dtsx** on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="9b375-121">このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9b375-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="9b375-122">「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。</span><span class="sxs-lookup"><span data-stu-id="9b375-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="9b375-123">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="9b375-124">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b375-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="9b375-125">前の手順の手順 3 ～ 8 の説明に従って、レッスン 4 パッケージをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9b375-125">Copy and paste the Lesson 4 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9b375-126">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="9b375-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9b375-127">手順 2:パッケージ構成の有効化と構成</span><span class="sxs-lookup"><span data-stu-id="9b375-127">Step 2: Enabling and Configuring Package Configurations</span></span>](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
  
