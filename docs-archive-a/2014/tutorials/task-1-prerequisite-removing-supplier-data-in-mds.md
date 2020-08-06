---
title: 'タスク 1 (前提条件): MDS で仕入先データを削除する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e78dc5ff04f95d42cf440e3f80b1b349e0315a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643661"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a><span data-ttu-id="ada64-102">タスク 1 (前提条件): MDS の仕入先データを削除する</span><span class="sxs-lookup"><span data-stu-id="ada64-102">Task 1 (Prerequisite): Removing Supplier Data in MDS</span></span>
  <span data-ttu-id="ada64-103">ここでは、MDS に格納されている仕入先データを削除します。</span><span class="sxs-lookup"><span data-stu-id="ada64-103">In this task, you remove the supplier data stored in MDS.</span></span> <span data-ttu-id="ada64-104">前のレッスンで**MDS Excel アドイン**を使用してデータを手動でアップロードしました。</span><span class="sxs-lookup"><span data-stu-id="ada64-104">You uploaded the data manually using **MDS Excel Add-in** in the previous lesson.</span></span> <span data-ttu-id="ada64-105">このレッスンで作成する SSIS パッケージは、MDS にデータを自動的にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="ada64-105">The SSIS package you create in this lesson will automatically upload the data to MDS for you.</span></span> <span data-ttu-id="ada64-106">したがって、SSIS パッケージをテストする前に、MDS からの仕入先データの削除、派生階層の削除、Supplier および State エンティティの削除、データのない Supplier エンティティの作成が必要となります。</span><span class="sxs-lookup"><span data-stu-id="ada64-106">Therefore, before testing the SSIS package, you need to remove the supplier data from MDS, remove the derived hierarchy, remove supplier and state entities, and create the supplier entity with no data.</span></span>  
  
1.  <span data-ttu-id="ada64-107">**マスターデータマネージャー**を起動するに `http://localhost/MDS` は、または MDS の構成時に指定した web サイトとアプリケーションに移動します。</span><span class="sxs-lookup"><span data-stu-id="ada64-107">Launch **Master Data Manager** by navigating to `http://localhost/MDS` or the website and application you specified when configuring MDS.</span></span> <span data-ttu-id="ada64-108">**マスターデータマネージャー**を開いたままにしている場合は、上部にある**SQL Server 2012 マスターデータサービス**をクリックして、**ホームページ**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ada64-108">If you kept the **Master Data Manager** open, click **SQL Server 2012 Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="ada64-109">[**管理タスク**] セクションで [**システム管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-109">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="ada64-110">メニューの [**管理**] にマウスポインターを合わせ、[**派生階層**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-110">Hover the mouse over **Manage** on the menu and click **Derived Hierarchies**.</span></span> <span data-ttu-id="ada64-111">**サプライヤー**モデル内のエンティティを削除する前に、派生階層の**SuppliersInState**を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ada64-111">You need to delete the derived hierarchy **SuppliersInState** before deleting the entities in the **Suppliers** model.</span></span>  
  
4.  <span data-ttu-id="ada64-112">[**派生階層**] ボックスの一覧の [ **SuppliersInState** ] を選択し、ツールバーの [ **X] (削除)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-112">Select **SuppliersInState** from the **Derived Hierarchy** list and click **X (Delete)** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="ada64-113">[ **OK** ] をクリックして削除を確定します。</span><span class="sxs-lookup"><span data-stu-id="ada64-113">Click **OK** to confirm deletion.</span></span>  
  
6.  <span data-ttu-id="ada64-114">メニューの [**管理**] の上にマウスポインターを置き、[**エンティティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-114">Hover the mouse over **Manage** on the menu and click **Entities**.</span></span>  
  
7.  <span data-ttu-id="ada64-115">[ **Supplier** ] をクリックし、ツールバーの [**削除] (X)** ボタンをクリックしてエンティティを削除します。</span><span class="sxs-lookup"><span data-stu-id="ada64-115">Click **Supplier** and click **Delete (X)** button on toolbar to delete the entity.</span></span> <span data-ttu-id="ada64-116">メッセージボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-116">Click **OK** on message boxes.</span></span>  
  
8.  <span data-ttu-id="ada64-117">前の手順を繰り返して、 **State**エンティティを削除します。</span><span class="sxs-lookup"><span data-stu-id="ada64-117">Repeat the previous step to delete **State** entity.</span></span>  
  
9. <span data-ttu-id="ada64-118">**マスターデータマネージャー**を閉じないでください。</span><span class="sxs-lookup"><span data-stu-id="ada64-118">Don't close **Master Data Manager**.</span></span>  
  
10. <span data-ttu-id="ada64-119">クレンジングされ、一致したファイル**Suppliers.xls**ファイルを開いた Excel ウィンドウに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ada64-119">Switch to the Excel window that has **Cleansed and Matched Suppliers.xls** file open.</span></span> <span data-ttu-id="ada64-120">下部にある [ **Sheet1** ] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ada64-120">Switch to the **Sheet1** tab at the bottom.</span></span>  
  
11. <span data-ttu-id="ada64-121">**ヘッダーが含まれている最初の行**のみを選択します。</span><span class="sxs-lookup"><span data-stu-id="ada64-121">Select only the **first row with headers**.</span></span> <span data-ttu-id="ada64-122">他の行は選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="ada64-122">Don't select any other row.</span></span> <span data-ttu-id="ada64-123">データをアップロードするのではなく、Excel の列に基づいてエンティティを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="ada64-123">You want to create the entities based on the Excel columns but don't want to upload any data.</span></span> <span data-ttu-id="ada64-124">したがって、行見出しがある先頭行のみを選択することになります。</span><span class="sxs-lookup"><span data-stu-id="ada64-124">Therefore you select only the first row with the headers.</span></span>  
  
12. <span data-ttu-id="ada64-125">メニューバーの [**マスターデータ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-125">Click **Master Data** on the menu bar.</span></span>  
  
13. <span data-ttu-id="ada64-126">リボンで [**エンティティの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-126">Click **Create Entity** from the ribbon.</span></span>  
  
14. <span data-ttu-id="ada64-127">[**接続の管理**] ダイアログボックスで、[**既存の接続**] に [**ローカル MDS サーバー**への接続] が表示されない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ada64-127">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="ada64-128">[**新しい接続の作成**] を選択し、[**新規**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-128">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="ada64-129">[新しい接続の追加] ダイアログボックスで、[**説明**] に「**ローカル MDS サーバー** 」と入力し、 **mds サーバーアドレス**には**http: \/ /localhost/MDS**を入力し、[ **OK** ] をクリックしてダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ada64-129">In the Add New Connection dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="ada64-130">[**接続の管理**] ダイアログボックスで [**ローカル MDS サーバー** ()] を選択し `http://localhost/MDS` 、[**テスト**] をクリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="ada64-130">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="ada64-131">メッセージボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-131">Click **OK** on the message box.</span></span>  
  
16. <span data-ttu-id="ada64-132">[**接続**] をクリックして、MDS サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="ada64-132">Click **Connect** to make a connection to the MDS server.</span></span>  
  
17. <span data-ttu-id="ada64-133">[**エンティティの作成**] ダイアログボックスで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ada64-133">In the **Create Entity** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="ada64-134">**範囲**が **$ 1: $** 1 に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ada64-134">Confirm that **Range** is set to **$1:$1**.</span></span>  
  
    2.  <span data-ttu-id="ada64-135">**モデル**の**仕入先**を選択します。</span><span class="sxs-lookup"><span data-stu-id="ada64-135">Select **Suppliers** for **Model**.</span></span>  
  
    3.  <span data-ttu-id="ada64-136">[**バージョン**] で [ **VERSION_1** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ada64-136">Select **VERSION_1** for **Version**.</span></span>  
  
    4.  <span data-ttu-id="ada64-137">**新しいエンティティ名**として「 **Supplier** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ada64-137">Type **Supplier** for **New entity name**.</span></span>  
  
    5.  <span data-ttu-id="ada64-138">[**コード**の**仕入**先] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ada64-138">Select **SupplierID** for **Code**.</span></span>  
  
    6.  <span data-ttu-id="ada64-139">[**名前**] に [ **Supplier name** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ada64-139">Select **Supplier Name** for **Name**.</span></span>  
  
    7.  <span data-ttu-id="ada64-140">[ **OK** ] をクリックしてエンティティを作成し、ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ada64-140">Click **OK** to create the entity and close the dialog box.</span></span>  
  
18. <span data-ttu-id="ada64-141">**Excel**を閉じ、ファイルを**保存しません**。</span><span class="sxs-lookup"><span data-stu-id="ada64-141">Close **Excel** and **do not save** the file.</span></span>  
  
19. <span data-ttu-id="ada64-142">**マスターデータマネージャー**で、インターネットブラウザーを更新し、 **Supplier**エンティティが一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ada64-142">In **Master Data Manager**, refresh the internet browser and confirm that **Supplier** entity is displayed in the list.</span></span>  
  
20. <span data-ttu-id="ada64-143">上部にある**SQL Server 2012 マスターデータサービス**をクリックして、**ホームページ**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ada64-143">Switch to the **home page** by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
21. <span data-ttu-id="ada64-144">[**モデル**] に [**仕入先**モデル] が選択されており、[**バージョン**] に [ **VERSION_1** ] が選択されていることを確認</span><span class="sxs-lookup"><span data-stu-id="ada64-144">Confirm that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**.</span></span>  
  
22. <span data-ttu-id="ada64-145">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ada64-145">Click **Explorer**.</span></span> <span data-ttu-id="ada64-146">すべての属性を持つ**Supplier**エンティティが、**値なし**で作成されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ada64-146">Notice that the **Supplier** entity with all the attributes is created with **no values**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ada64-147">次の手順</span><span class="sxs-lookup"><span data-stu-id="ada64-147">Next Step</span></span>  
 [<span data-ttu-id="ada64-148">タスク 2 &#40;オプションの&#41;: マスターデータマネージャーを使用した MDS サブスクリプションビューの作成</span><span class="sxs-lookup"><span data-stu-id="ada64-148">Task 2 &#40;Optional&#41;: Creating a MDS Subscription View using Master Data Manager</span></span>](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
