---
title: 'タスク 4 (省略可能): 新しいデータセットを結合、照合、およびパブリッシュする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13a13f03-b307-4555-8e33-6d98c459d994
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ddcec19fa8b957bf77b6ea5269b4d033779bdf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632202"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a><span data-ttu-id="3c0f5-102">タスク 4 (オプション): 新しいデータ セットを結合、照合、およびパブリッシュする</span><span class="sxs-lookup"><span data-stu-id="3c0f5-102">Task 4 (Optional): Combining, Matching, and Publishing New Set of Data</span></span>
  <span data-ttu-id="3c0f5-103">後で、MDS リポジトリにさらにデータを追加する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="3c0f5-104">データを追加する前に、新しいデータを MDS で既に管理されているデータと比較して、重複していないデータや不正確なデータを追加していないことを確認すると便利です。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure that you are not adding duplicate or inaccurate data.</span></span> <span data-ttu-id="3c0f5-105">Excel 用マスター データ サービス アドインを使用すると、データを MDS にパブリッシュする前に、2 つのワークシートのデータを結合し、データを比較することで重複を識別して削除できます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-105">In the Master Data Services Add-in for Excel, you can combine data from two worksheets and the compare the data to identify and remove duplicates before publishing the data to MDS.</span></span> <span data-ttu-id="3c0f5-106">MDS Excel アドインの照合機能は、データの一致を識別するための DQS 照合機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-106">The matching feature of MDS Excel Add-in uses the DQS matching functionality to identify matches in the data.</span></span> <span data-ttu-id="3c0f5-107">ここでは、MDS にパブリッシュする前に、2 つのワークシートのデータを 1 つに結合し、重複を識別して削除するための照合作業を行います。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-107">In this task, you will combine data from a two worksheets into one and then perform the matching activity to identify and remove duplicates before publishing to MDS.</span></span> <span data-ttu-id="3c0f5-108">詳細については、「Excel 用 MDS アドインと[データの結合](https://msdn.microsoft.com/library/hh548680.aspx)」トピックの「[データ品質照合](https://msdn.microsoft.com/library/hh548681.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-108">See [Data Quality Matching in the MDS Add-in for Excel](https://msdn.microsoft.com/library/hh548681.aspx) and [Combine Data](https://msdn.microsoft.com/library/hh548680.aspx) topics for more details.</span></span>  
  
1.  <span data-ttu-id="3c0f5-109">**Excel**の新しいインスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-109">Launch new instance of **Excel**.</span></span> <span data-ttu-id="3c0f5-110">[**スタート**] をクリックし、[**実行**] をポイントして「 **Excel**」と入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-110">Click **Start**, point to **Run**, type **Excel**, and click **OK**.</span></span>  
  
2.  <span data-ttu-id="3c0f5-111">メニューバーの [**マスターデータ**] をクリックして、[**マスターデータ**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-111">Switch to the **Master Data** tab by clicking **Master Data** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="3c0f5-112">[**接続と読み込み**] グループのリボンで [**接続**] をクリックして、 **MDS サーバー**に接続します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-112">Click **Connect** on the ribbon in the **Connect and Load** group to connect to the **MDS server**.</span></span> <span data-ttu-id="3c0f5-113">この接続は、このレッスンの前の手順で構成しました。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-113">You have configured this connection earlier in this lesson.</span></span>  
  
     <span data-ttu-id="3c0f5-114">![Excel - [マスター データ] タブの [エクスプローラーの表示] ボタン](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - [マスター データ] タブの [エクスプローラーの表示] ボタン")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-114">![Excel - Show Explorer Button on Master Data Tabl](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - Show Explorer Button on Master Data Tabl")</span></span>  
  
4.  <span data-ttu-id="3c0f5-115">右側に [**マスターデータエクスプローラー** ] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-115">You should see the **Master Data Explorer** pane to the right.</span></span> <span data-ttu-id="3c0f5-116">マスターデータエクスプローラーが表示されない場合は、リボンの [**エクスプローラーの表示**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-116">If you do not see the Master Data Explorer, click **Show Explorer** button on the ribbon.</span></span>  
  
5.  <span data-ttu-id="3c0f5-117">[**マスターデータエクスプローラー** ] ウィンドウで、**モデル**のドロップダウンリストから [**仕入先**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-117">In the **Master Data Explorer** Window, select **Suppliers** in the drop-down list for the **Model**.</span></span> <span data-ttu-id="3c0f5-118">モデルには**Supplier**というエンティティが1つあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-118">You should see that the model has one entity: **Supplier**.</span></span>  
  
     <span data-ttu-id="3c0f5-119">![Excel - [マスター データ エクスプローラー] ウィンドウ](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - [マスター データ エクスプローラー] ウィンドウ")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-119">![Excel - Master Data Explorer Window](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - Master Data Explorer Window")</span></span>  
  
6.  <span data-ttu-id="3c0f5-120">[エンティティ] ボックスの一覧の [ **Supplier** ] をダブルクリックして、エンティティメンバーを Excel ワークシートに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-120">Double-click **Supplier** in the entity list to load the entity members into the Excel worksheet.</span></span>  
  
7.  <span data-ttu-id="3c0f5-121">下部にある [ **sheet2** ] をクリックして、[ **sheet2** ] タブに切り替えます。[ **Sheet2**] が表示されない場合は、新しいワークシートを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-121">Click **Sheet2** at the bottom to switch to the **Sheet2** tab. If you do not see **Sheet2**, add a new worksheet.</span></span>  
  
8.  <span data-ttu-id="3c0f5-122">**Suppliers.xls**ファイル (チュートリアルファイルに含まれている元の入力ファイル) を開き、連結の**eandクレンジング**ワークシートのすべての (3 行) を**Sheet2**にコピーします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-122">Open **Suppliers.xls** file (the original input file that is included in the tutorial files) and copy all (three) rows from the **CombineAndCleanse** worksheet to **Sheet2**.</span></span>  
  
9. <span data-ttu-id="3c0f5-123">**MDS**に接続されている、(クレンジングされた**仕入先リスト**Excel ではなく) **Microsoft Excel ブック**の**Supplier**シートに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-123">Switch back to the **Supplier** sheet in the **Book 1 - Microsoft Excel** (not the **Cleansed and Matched Supplier List** Excel) that is connected to **MDS**.</span></span>  
  
10. <span data-ttu-id="3c0f5-124">メニューバーの [**マスターデータ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-124">Click **Master Data** on the menu bar.</span></span>  
  
11. <span data-ttu-id="3c0f5-125">リボンの [**データの結合**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-125">Click **Combine Data** on the ribbon.</span></span> <span data-ttu-id="3c0f5-126">[**データの結合**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-126">You will see the **Combine Data** dialog box.</span></span>  
  
12. <span data-ttu-id="3c0f5-127">[**データの結合**] ダイアログボックスで、次の図のように [**範囲を MDS データと結合する範囲**] ボックスの横にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-127">In the **Combine Data** dialog box, click the button next to **Range to combine with MDS data** text box as shown in the following image.</span></span>  
  
     <span data-ttu-id="3c0f5-128">![Excel - [データの結合] ダイアログ ボックス](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - [データの結合] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-128">![Excel - Combine Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - Combine Data Dialog Box")</span></span>  
  
13. <span data-ttu-id="3c0f5-129">これで、ダイアログ ボックスは圧縮表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-129">You should see the shrunken dialog box now.</span></span> <span data-ttu-id="3c0f5-130">次に、[ **sheet2** ] をクリックして、4つの行 (ヘッダー行を含む) を持つ新しい仕入先データを含む [ **sheet2** ] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-130">Now, click **Sheet2** to switch to the **Sheet2** tab that has the new supplier data with 4 rows (including one header row).</span></span>  
  
14. <span data-ttu-id="3c0f5-131">**Sheet2**で、**ヘッダー行を含むすべての行**を選択します (既に選択されているように見える場合でも)。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-131">In the **Sheet2**, select **all rows including the header row** (even if they seem to be already selected).</span></span> <span data-ttu-id="3c0f5-132">**MDS データと結合する範囲**が自動的に更新されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-132">You should see the **Range to combine with MDS data** is automatically updated.</span></span>  
  
     <span data-ttu-id="3c0f5-133">![Excel - [データの結合] ダイアログ ボックス - 最小化](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - [データの結合] ダイアログ ボックス - 最小化")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-133">![Excel - Combine Data Dialog Box - Minimized](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - Combine Data Dialog Box - Minimized")</span></span>  
  
15. <span data-ttu-id="3c0f5-134">[**データの結合**] ダイアログボックスを閉じずに、[**仕入先**] タブに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-134">Switch back to the **Suppliers** tab without closing the **Combine Data** dialog box.</span></span>  
  
16. <span data-ttu-id="3c0f5-135">**テキストボックス**の横にある**ボタン**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-135">Click the **button** next to the **text box**.</span></span> <span data-ttu-id="3c0f5-136">これで、ダイアログ ボックスは展開表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-136">You should see that the dialog box is expanded now.</span></span> <span data-ttu-id="3c0f5-137">**Supplier** MDS**エンティティ**の列間のすべてのマッピングが**Excel**列に自動的に設定されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-137">You should see all the mappings between columns of the **Supplier** MDS **entity** to **Excel** columns are automatically populated.</span></span>  
  
     <span data-ttu-id="3c0f5-138">![Excel-データが入力された [データの結合] ダイアログボックス](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel-データが入力された [データの結合] ダイアログボックス")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-138">![Excel - Combine Data Dialog Box Filled with Data](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - Combine Data Dialog Box Filled with Data")</span></span>  
  
17. <span data-ttu-id="3c0f5-139">**Code**エンティティ列がワークシートの [**仕入**先] 列にマップされ、[**郵便**番号] エンティティ列がワークシートの [**郵便**番号] 列にマップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-139">Ensure that **Code** entity column is mapped to the **SupplierID** column in the worksheet and **Zip Code** entity column is mapped to the **Zip Code** column in the worksheet.</span></span>  
  
18. <span data-ttu-id="3c0f5-140">[**データの結合**] ダイアログボックスで、[**結合**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-140">On the **Combine Data** dialog box, click **Combine**.</span></span>  
  
19. <span data-ttu-id="3c0f5-141">3 つのデータ行がワークシートの下部に追加され、色分けされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-141">Confirm that three data rows are added to the bottom of the worksheet and they should be color coded.</span></span>  
  
     <span data-ttu-id="3c0f5-142">![Excel - 結合後の新しい要素](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - 結合後の新しい要素")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-142">![Excel - New Elements after Combining](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - New Elements after Combining")</span></span>  
  
20. <span data-ttu-id="3c0f5-143">リボンの [**数値演算データ**] をクリックして、重複を識別します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-143">Click **Math Data** on the ribbon to identify duplicates.</span></span> <span data-ttu-id="3c0f5-144">この機能は、DQS の照合機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-144">This feature uses the matching functionality of DQS.</span></span>  
  
21. <span data-ttu-id="3c0f5-145">[**データの照合**] ダイアログボックスで、[ **DQS ナレッジベース**の**サプライヤー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-145">In the **Match Data** dialog box, select **Suppliers** for **DQS Knowledge Base**.</span></span>  
  
     <span data-ttu-id="3c0f5-146">![Excel - [データの照合] ダイアログ ボックス](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - [データの照合] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-146">![Excel - Match Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - Match Data Dialog Box")</span></span>  
  
22. <span data-ttu-id="3c0f5-147">次の表のようにワークシートの列をドメインにマップします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-147">Map worksheet columns to domains as shown in the following table.</span></span>  
  
    |<span data-ttu-id="3c0f5-148">ワークシートの列</span><span class="sxs-lookup"><span data-stu-id="3c0f5-148">Worksheet Column</span></span>|<span data-ttu-id="3c0f5-149">Domain</span><span class="sxs-lookup"><span data-stu-id="3c0f5-149">Domain</span></span>|  
    |----------------------|------------|  
    |<span data-ttu-id="3c0f5-150">Code (MDS の Supplier エンティティ用にコードとしてアップロードした仕入先の ID)</span><span class="sxs-lookup"><span data-stu-id="3c0f5-150">Code (you uploaded Supplier ID as the Code for the Supplier entity in MDS)</span></span>|<span data-ttu-id="3c0f5-151">Supplier ID</span><span class="sxs-lookup"><span data-stu-id="3c0f5-151">Supplier ID</span></span>|  
    |<span data-ttu-id="3c0f5-152">Name (Supplier エンティティの名前として MDS にアップロードした仕入先の名前)</span><span class="sxs-lookup"><span data-stu-id="3c0f5-152">Name (you uploaded Supplier Name as the Name for the Supplier entity to MDS)</span></span>|<span data-ttu-id="3c0f5-153">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="3c0f5-153">Supplier Name</span></span>|  
    |<span data-ttu-id="3c0f5-154">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="3c0f5-154">ContactEmailAddress</span></span>|<span data-ttu-id="3c0f5-155">ContactEmail</span><span class="sxs-lookup"><span data-stu-id="3c0f5-155">ContactEmail</span></span>|  
  
23. <span data-ttu-id="3c0f5-156">**コード**列マッピングの**前提条件**を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-156">Select **Prerequisite** for the **Code** column mapping.</span></span>  
  
24. <span data-ttu-id="3c0f5-157">図に示されているように、**仕入**先の名前の**重み**として「 **70%** 」を、**連絡先の電子メール**の**重み**として「 **30%** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-157">Enter **70%** as the **weight** for **Supplier Name** and **30%** as the **weight** for **Contact Email** as shown in the image.</span></span>  
  
25. <span data-ttu-id="3c0f5-158">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-158">Click **OK**.</span></span>  
  
26. <span data-ttu-id="3c0f5-159">照合プロセスでは、**コード: S1**を使用して、業者の重複を識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-159">The matching process should identify one duplicate for the supplier with **Code: S1**.</span></span>  
  
     <span data-ttu-id="3c0f5-160">![Excel - 照合結果](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - 照合結果")</span><span class="sxs-lookup"><span data-stu-id="3c0f5-160">![Excel - Matching Results](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - Matching Results")</span></span>  
  
27. <span data-ttu-id="3c0f5-161">重複する**行 (オレンジ色)** を選択して右クリックし、[**削除**] をクリックして行を削除します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-161">Select the **duplicate row (orange)**, right-click, and click **Delete** to delete the row.</span></span>  
  
28. <span data-ttu-id="3c0f5-162">不要になったため、 **CLUSTER_ID**列を削除します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-162">Delete the **CLUSTER_ID** column since you don't need it anymore.</span></span>  
  
29. <span data-ttu-id="3c0f5-163">[**発行**] をクリックして、S66 および**S57**という**コード**を使用して、他の2つの新しいレコードを MDS に発行します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-163">Click **Publish** to publish the other two new records with **Codes S66** and **S57** to MDS.</span></span>  
  
30. <span data-ttu-id="3c0f5-164">[**パブリッシュと注釈**設定] ダイアログボックスで、**注釈**を追加し、[**発行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-164">In the **Publish and Annotate** dialog box, add an **annotation**, and click **Publish**.</span></span>  
  
31. <span data-ttu-id="3c0f5-165">**マスターデータマネージャー Web アプリケーション**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-165">Switch to the **Master Data Manager Web application**.</span></span>  
  
32. <span data-ttu-id="3c0f5-166">[ホーム] ページで、[**仕入先**] が**モデル**に対して選択されていることを確認し、[**エクスプローラー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-166">On the home page, ensure that **Suppliers** is selected for the **Model**, and click **Explorer**.</span></span> <span data-ttu-id="3c0f5-167">**エクスプローラー**が既に開いている場合は、インターネットブラウザーを最新の状態に更新します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-167">If you already have the **Explorer** open, refresh the internet browser.</span></span>  
  
33. <span data-ttu-id="3c0f5-168">**コード**によってリストを**並べ替え**、コードとして**S57**と**S66**のレコードを検索します。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-168">**Sort** the list by **Code** and look for records with **S57** and **S66** as codes.</span></span> <span data-ttu-id="3c0f5-169">また、ツールバーの [**フィルター** ] ボタンを使用して、一覧内の特定のレコードを検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-169">You can also use the **Filter** button on the toolbar to search for a specific record in the list.</span></span>  
  
34. <span data-ttu-id="3c0f5-170">次に、ファイルを保存せずに**Book1-Microsoft Excel**ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3c0f5-170">Now, close **Book1 - Microsoft Excel** window without saving the file.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="3c0f5-171">次の手順</span><span class="sxs-lookup"><span data-stu-id="3c0f5-171">Next Step</span></span>  
 [<span data-ttu-id="3c0f5-172">タスク 5: Excel からドメイン ベースの属性を作成する</span><span class="sxs-lookup"><span data-stu-id="3c0f5-172">Task 5: Creating a Domain-Based Attribute from Excel</span></span>](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
