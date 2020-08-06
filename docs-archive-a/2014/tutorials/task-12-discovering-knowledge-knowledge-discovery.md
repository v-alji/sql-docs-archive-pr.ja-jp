---
title: 'タスク 12: ナレッジの検出 (ナレッジ検出) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2dee66f94f1df609701f92d591f2c31863702465
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714886"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a><span data-ttu-id="b0da0-102">タスク 12: ナレッジを検出する (ナレッジ検出)</span><span class="sxs-lookup"><span data-stu-id="b0da0-102">Task 12: Discovering Knowledge (Knowledge Discovery)</span></span>
  <span data-ttu-id="b0da0-103">このタスクでは、 **SUPPLIER ID**および**supplier Name**ドメインで**ナレッジ検出**アクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-103">In this task, you perform the **Knowledge Discovery** activity on **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="b0da0-104">このシナリオでは、ナレッジ検出プロセスにより主にこれら 2 つのドメインの値をインポートします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-104">In this scenario, the knowledge discovery process mainly imports values for these two domains.</span></span>  
  
 <span data-ttu-id="b0da0-105">このチュートリアルでは、ナレッジ ベースを最初から作成しました。</span><span class="sxs-lookup"><span data-stu-id="b0da0-105">In this tutorial, you started building knowledge base from scratch.</span></span> <span data-ttu-id="b0da0-106">さらに、ナレッジ検出アクティビティを実行してナレッジ ベースを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-106">You can also start creating a knowledge base by performing a knowledge discovery activity.</span></span> <span data-ttu-id="b0da0-107">メインページで [**ナレッジベースの作成**] をクリックすると、DQS クライアントは、アクティビティに対して選択された**ドメイン管理**アクティビティを含むページに移動します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-107">When you click **Create a Knowledge Base** in the main page, DQS client takes you to a page with **Domain Management** activity selected for the activity.</span></span> <span data-ttu-id="b0da0-108">**アクティビティ**を**ナレッジ検出**に変更し、次のページでナレッジ検出プロセスの一部としてドメインを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-108">You can change the **activity** to **Knowledge Discovery** and then in the next page you can create domains as part of the knowledge discovery process.</span></span> <span data-ttu-id="b0da0-109">詳細については、「[ナレッジ検出の実行](https://msdn.microsoft.com/library/hh510398.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0da0-109">See [Perform Knowledge Discovery](https://msdn.microsoft.com/library/hh510398.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="b0da0-110">DQS クライアントのメインページの [**最近使用したナレッジベース**] セクションで、[**サプライヤー** ] ナレッジベースの横に**ある右矢印**をクリックし、[**ナレッジ検出**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-110">In the main page of DQS Client, in the **Recent Knowledge Base** section, click **right-arrow** next to the **Suppliers** knowledge base and click **Knowledge Discovery**.</span></span> <span data-ttu-id="b0da0-111">または、[**ナレッジベースを開く**] をクリックし、**ナレッジベースの一覧**から [**仕入先**] を選択して、[**ナレッジ検出**] を**アクティビティ**として選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-111">Alternatively, you can click **Open Knowledge Base**, select **Suppliers** from the **list of knowledge bases**, select **Knowledge Discovery** as **activity** and click **Next**.</span></span>  
  
     <span data-ttu-id="b0da0-112">![メイン ページでの [ナレッジ検出] メニュー](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "メイン ページでの [ナレッジ検出] メニュー")</span><span class="sxs-lookup"><span data-stu-id="b0da0-112">![Knowledge Discovery Menu on Main Page](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Knowledge Discovery Menu on Main Page")</span></span>  
  
2.  <span data-ttu-id="b0da0-113">**データソース**として**Excel ファイル**を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-113">Select **Excel File** for **Data Source**.</span></span>  
  
3.  <span data-ttu-id="b0da0-114">[**参照**] をクリックし、[ **Suppliers.xls**] をクリックして、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-114">Click **Browse**, navigate and select **Suppliers.xls**, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="b0da0-115">**ワークシート**の**検出のためのサプライヤー**を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-115">Select **Suppliers for Discovery** for **Worksheet**.</span></span>  
  
5.  <span data-ttu-id="b0da0-116">[**マッピング**] セクションで、**ドロップダウンリスト**を使用して、仕入先の列を**Excel**ファイル**から supplier** **ID** **ドメインおよび supplier name 列\*\*\*\*にマップし**ます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-116">In the **Mappings** section, map **SupplierID** column from the **Excel** file to the **Supplier ID** domain and **Supplier Name** column to the **Supplier Name** domain by using **drop-down lists**.</span></span> <span data-ttu-id="b0da0-117">Excel ファイルには、 **SUPPLIER ID**および**supplier Name**ドメインのサンプルデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0da0-117">The Excel file has sample data for the **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="b0da0-118">検出プロセスでは、値を検出するドメインを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-118">In the discovery process, you can select the domains for which you want to discover the values.</span></span> <span data-ttu-id="b0da0-119">このページでドメインを作成し、これらのドメインにソース列をマップできます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-119">You can create domains on this page and then map the source columns to those domains.</span></span> <span data-ttu-id="b0da0-120">ドメイン管理アクティビティ中にドメインを作成する代わりに、ナレッジ検出アクティビティ中にドメインを作成することは一般的でありません。</span><span class="sxs-lookup"><span data-stu-id="b0da0-120">It is not uncommon to create domains during knowledge discovery activity instead of creating domains during domain management activity.</span></span>  
  
     <span data-ttu-id="b0da0-121">![検出プロセスの [マップ] ページ](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "検出プロセスの [マップ] ページ")</span><span class="sxs-lookup"><span data-stu-id="b0da0-121">![Map Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Map Page of Discovery Process")</span></span>  
  
6.  <span data-ttu-id="b0da0-122">[**次へ**] をクリックして、[**検出**] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-122">Click **Next** to switch to the **Discover** page.</span></span>  
  
7.  <span data-ttu-id="b0da0-123">[**検出**] ページで、[**開始**] をクリックして検出プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-123">On the **Discover** page, click **Start** to start the discovery process.</span></span> <span data-ttu-id="b0da0-124">検出は、 **Suppliers.xls**ファイルの列の**仕入\*\*\*\*先名と仕入先名**に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-124">Discovery is performed on the columns **SupplierID** and **Supplier Name** in the **Suppliers.xls** file.</span></span> <span data-ttu-id="b0da0-125">**SUPPLIER ID**および**supplier Name**ドメインには、検出から得られたナレッジが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0da0-125">The **Supplier ID** and **Supplier Name** domains should be populated with the knowledge drawn from the discovery.</span></span>  
  
     <span data-ttu-id="b0da0-126">![検出プロセスの [検出] ページ](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "検出プロセスの [検出] ページ")</span><span class="sxs-lookup"><span data-stu-id="b0da0-126">![Discover Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "Discover Page of Discovery Process")</span></span>  
  
8.  <span data-ttu-id="b0da0-127">分析が完了したら、ページの下部にある [**プロファイラー] タブ**で**ソースの統計**を確認します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-127">After the analysis has completed, review the **Source Statistics** in the **Profiler tab** at the bottom of the page.</span></span> <span data-ttu-id="b0da0-128">合計20個の値 (**仕入\*\*\*\*先名と仕入先名\*\*\*\*の値) を**含む10個の新しいレコードが検出されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b0da0-128">Notice that 10 new records with total 20 values (**SupplierID** and **Supplier Name** values from the **Excel worksheet**) were discovered.</span></span> <span data-ttu-id="b0da0-129">さらに、これらの値のうちいくつが、新しい値、一意の値、新しい一意の値、および有効な値であるかがわかります。</span><span class="sxs-lookup"><span data-stu-id="b0da0-129">You will also see how many of the values are new, unique, new and unique, and valid.</span></span> <span data-ttu-id="b0da0-130">右側のリスト ボックスには、検出プロセスに使用された各ドメインの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-130">In the list box to the right, you can see more details for each domain involved in the discovery process.</span></span> <span data-ttu-id="b0da0-131">[完全] 列のステータス バーにマウス ポインターを合わせると、ソースの列に不足値があるかどうかを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-131">If you hover the mouse over the status bar in the Completeness column, you can see if there are any missing values in the columns in the source.</span></span>  
  
     <span data-ttu-id="b0da0-132">![ナレッジ検出の結果](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "ナレッジ検出の結果")</span><span class="sxs-lookup"><span data-stu-id="b0da0-132">![Knowledge Discovery Results](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "Knowledge Discovery Results")</span></span>  
  
9. <span data-ttu-id="b0da0-133">[**次へ**] をクリックして、[**ドメイン値の管理**] ページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-133">Click **Next** to switch to the **Manage Domain Values** page.</span></span>  
  
10. <span data-ttu-id="b0da0-134">[**ドメイン値の管理**] ページで、ドメインの一覧から [ **Supplier Name** Domain] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-134">In the **Manage Domain Values** page, click **Supplier Name** domain from the list of domains.</span></span>  
  
11. <span data-ttu-id="b0da0-135">右側のウィンドウで、[ **Lazy Country Storex** (最後に ' x ' に注意してください)] を右クリックし、[ **lazy country Store**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-135">In the right pane, right-click **Lazy Country Storex** (notice 'x' at the end), and select **Lazy Country Store**.</span></span> <span data-ttu-id="b0da0-136">DQS により、ドメインに対するスペル チェッカーの実行後、この変更内容が提案されます。</span><span class="sxs-lookup"><span data-stu-id="b0da0-136">DQS suggests this change after running the spell checker on the domain.</span></span> <span data-ttu-id="b0da0-137">既定では、作成するドメインに対するスペル チェックが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="b0da0-137">By default, speller is enabled on the domains you create.</span></span>  
  
     <span data-ttu-id="b0da0-138">![適切な仕入先名 - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "適切な仕入先名 - Lazy Country Store")</span><span class="sxs-lookup"><span data-stu-id="b0da0-138">![Correct Supplier Name - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "Correct Supplier Name - Lazy Country Store")</span></span>  
  
12. <span data-ttu-id="b0da0-139">[ドメイン値] ボックスの一覧で、lazy country **Storex**が修正として**レイジー country store**でエラー (赤い**X**マーク) として設定されていること、また、 **lazy country ストア**も有効な値として追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0da0-139">In the domain values list, confirm that the value **Lazy Country Storex** is set as an error (red **X** mark) with **Lazy Country Store** as the correction and also the **Lazy Country Store** is also added as a valid value.</span></span>  
  
     <span data-ttu-id="b0da0-140">![ドメイン値と [次に修正] の値](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "ドメイン値と [次に修正] の値")</span><span class="sxs-lookup"><span data-stu-id="b0da0-140">![Domain Value and Correct To Value](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "Domain Value and Correct To Value")</span></span>  
  
13. <span data-ttu-id="b0da0-141">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-141">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="b0da0-142">**SQL Server Data Quality Services** ] ダイアログボックスで、[**発行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-142">On **SQL Server Data Quality Services** dialog box, click **Publish**.</span></span>  
  
15. <span data-ttu-id="b0da0-143">成功メッセージボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0da0-143">Click **OK** on the success message box.</span></span>  
  
     <span data-ttu-id="b0da0-144">これで、チュートリアルの最初のレッスンを完了しました。</span><span class="sxs-lookup"><span data-stu-id="b0da0-144">You have completed the first lesson of the tutorial.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b0da0-145">次の手順</span><span class="sxs-lookup"><span data-stu-id="b0da0-145">Next Step</span></span>  
 [<span data-ttu-id="b0da0-146">レッスン 2: Suppliers ナレッジ ベースを使用して仕入先データをクレンジングする</span><span class="sxs-lookup"><span data-stu-id="b0da0-146">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
