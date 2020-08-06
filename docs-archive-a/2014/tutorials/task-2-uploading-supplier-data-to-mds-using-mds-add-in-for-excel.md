---
title: 'タスク 2: Excel 用 MDS アドインを使用して Supplier データを MDS にアップロードする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 16c5fa9db81649b30c12fae4d2e57afa8bf094e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631408"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a><span data-ttu-id="2f950-102">タスク 2: Excel 用 MDS アドインを使用して仕入先データを MDS にアップロードする</span><span class="sxs-lookup"><span data-stu-id="2f950-102">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>
  <span data-ttu-id="2f950-103">このタスクでは、 **Excel 用 MDS アドイン**を使用して、クレンジングおよび仕入先データを**MDS**に発行します。</span><span class="sxs-lookup"><span data-stu-id="2f950-103">In this task, you publish the cleansed and supplier data to **MDS** using the **MDS Add-in for Excel**.</span></span> <span data-ttu-id="2f950-104">**Supplier**という名前のエンティティを作成するには、前のレッスンで作成した**サプライヤー**モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f950-104">You create an entity named **Supplier** in the **Suppliers** model you created in the previous lesson.</span></span> <span data-ttu-id="2f950-105">エンティティは、Excel ファイルの各列に属性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="2f950-105">The entity will have an attribute for each column in the Excel file.</span></span> <span data-ttu-id="2f950-106">Supplier エンティティの Code 属性と Name 属性は、Excel の [**仕入**先] 列と [ **supplier name** ] 列に対応しています。</span><span class="sxs-lookup"><span data-stu-id="2f950-106">The Code and Name attributes of the Supplier entity correspond to the **SupplierID** and **Supplier Name** columns in Excel.</span></span>  
  
1.  <span data-ttu-id="2f950-107">クレンジングされ **、一致した Suppliers.xls**を**Excel**で開きます。</span><span class="sxs-lookup"><span data-stu-id="2f950-107">Open **Cleansed and Matched Suppliers.xls** in **Excel**.</span></span>  
  
2.  <span data-ttu-id="2f950-108">Ctrl キーを押し**ながら A**キーを押してデータ全体を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f950-108">Press **CTRL+A** to select entire data.</span></span> <span data-ttu-id="2f950-109">スプレッドシートでデータ全体を選択することが**重要**です。</span><span class="sxs-lookup"><span data-stu-id="2f950-109">It is **important** that you select the entire data in the spreadsheet.</span></span>  
  
3.  <span data-ttu-id="2f950-110">メニューバーの [**マスターデータ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f950-110">Click **Master Data** on the menu bar.</span></span>  
  
4.  <span data-ttu-id="2f950-111">リボンの [**エンティティの作成**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f950-111">Click **Create Entity** button on the ribbon.</span></span>  
  
     <span data-ttu-id="2f950-112">![Excel - [マスター データ] タブ - [エンティティの作成] ボタン](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - [マスター データ] タブ - [エンティティの作成] ボタン")</span><span class="sxs-lookup"><span data-stu-id="2f950-112">![Excel - Master Data Tab - Create Entity Button](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - Master Data Tab - Create Entity Button")</span></span>  
  
5.  <span data-ttu-id="2f950-113">[**接続の管理**] ダイアログボックスで、[**既存の接続**] に [**ローカル MDS サーバー**への接続] が表示されない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2f950-113">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="2f950-114">[**新しい接続の作成**] を選択し、[**新規**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f950-114">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="2f950-115">[**新しい接続の追加**] ダイアログボックスで、[**説明**] に「**ローカル MDS サーバー** 」と入力し、 **mds サーバーアドレス**には**http: \/ /localhost/MDS**を入力し、[ **OK** ] をクリックしてダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2f950-115">In the **Add New Connection** dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="2f950-116">[**接続の管理**] ダイアログボックスで [**ローカル MDS サーバー** ()] を選択し `http://localhost/MDS` 、[**テスト**] をクリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="2f950-116">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="2f950-117">メッセージボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f950-117">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="2f950-118">[**接続**] をクリックして MDS サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="2f950-118">Click **Connect** to connect to the MDS server.</span></span>  
  
8.  <span data-ttu-id="2f950-119">[**エンティティの作成**] ダイアログボックスで、**モデル**の [**仕入先**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f950-119">In the **Create Entity** dialog box, select **Suppliers** for the **Model**.</span></span>  
  
9. <span data-ttu-id="2f950-120">**VERSION_1**が**バージョン**に対して選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2f950-120">Ensure that **VERSION_1** is selected for **Version**.</span></span>  
  
10. <span data-ttu-id="2f950-121">**新しいエンティティ名**として「 **Supplier** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2f950-121">Enter **Supplier** for **New entity name**.</span></span>  
  
11. <span data-ttu-id="2f950-122">**一意の識別子フィールドを含む列**の [**仕入**先] を選択します (コードを自動的に生成することもできます)。</span><span class="sxs-lookup"><span data-stu-id="2f950-122">Select **SupplierID** for **the column that contains a unique identifier** field (you can also generate a code automatically).</span></span> <span data-ttu-id="2f950-123">基本的には、 **Excel**の **"仕入先" 列を** **Supplier**エンティティの**Code**属性にマップします。</span><span class="sxs-lookup"><span data-stu-id="2f950-123">You are essentially mapping the **SupplierID** column in **Excel** to the **Code** attribute of **Supplier** entity.</span></span>  
  
12. <span data-ttu-id="2f950-124">[名前] フィールド**が含まれている列**の [ **Supplier Name** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f950-124">Select **Supplier Name** for **the column that contains names** field.</span></span> <span data-ttu-id="2f950-125">基本的には、 **Excel**の**supplier Name**列を**supplier**エンティティの**name**属性にマップします。</span><span class="sxs-lookup"><span data-stu-id="2f950-125">You are essentially mapping the **Supplier Name** column in **Excel** to the **Name** attribute of the **Supplier** entity.</span></span> <span data-ttu-id="2f950-126">**Code**属性と**Name**属性は、MDS のエンティティの必須属性です。</span><span class="sxs-lookup"><span data-stu-id="2f950-126">The **Code** and **Name** attributes are mandatory attributes for an entity in MDS.</span></span>  
  
     <span data-ttu-id="2f950-127">![[エンティティの作成] ダイアログ ボックス](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "[エンティティの作成] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="2f950-127">![Create Entity Dialog Box](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Create Entity Dialog Box")</span></span>  
  
13. <span data-ttu-id="2f950-128">[ **OK]** をクリックして MDS にエンティティを作成し、マスターデータをエンティティにパブリッシュして、[**エンティティの作成**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2f950-128">Click **OK** to create the entity on MDS, publish the master data to the entity, and close **Create Entity** dialog box.</span></span>  
  
14. <span data-ttu-id="2f950-129">これで、" **Supplier**" という名前の新しいシートが表示されます。これは、Excel スプレッドシートに追加され、ワークシートの上部に、ワークシートが MDS サーバーに接続されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="2f950-129">Now, you should see a new sheet titled **Supplier**, which is the name of the entity, added to your Excel spreadsheet and at the top of the worksheet you should see that the worksheet is connected to the MDS server.</span></span> <span data-ttu-id="2f950-130">元のワークシート ( **Sheet1**) は依然として存在することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2f950-130">Notice that the original worksheet (titled **Sheet1**) still exists.</span></span>  
  
     <span data-ttu-id="2f950-131">![Excel - [仕入先] と [Sheet1] タブ](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - [仕入先] と [Sheet1] タブ")</span><span class="sxs-lookup"><span data-stu-id="2f950-131">![Excel - Supplier and Sheet1 Tabs](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - Supplier and Sheet1 Tabs")</span></span>  
  
     <span data-ttu-id="2f950-132">![Excel - MDS 接続の詳細の表示](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - MDS 接続の詳細の表示")</span><span class="sxs-lookup"><span data-stu-id="2f950-132">![Excel - Showing MDS Connection Details](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - Showing MDS Connection Details")</span></span>  
  
15. <span data-ttu-id="2f950-133">**Excel**を開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="2f950-133">Keep **Excel** open.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="2f950-134">次の作業</span><span class="sxs-lookup"><span data-stu-id="2f950-134">Next Task</span></span>  
 [<span data-ttu-id="2f950-135">タスク 3: マスター データ マネージャーのデータを確認する</span><span class="sxs-lookup"><span data-stu-id="2f950-135">Task 3: Verifying the Data in Master Data Manager</span></span>](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
