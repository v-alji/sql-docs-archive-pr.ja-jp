---
title: '作業 12: 派生列変換を追加して MDS で必要な列を追加する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a4a70dd4d288e425beb2821f6b2aaf440b1d1930
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719058"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a><span data-ttu-id="0e563-102">タスク 12: 派生列変換を追加して MDS で必要な列を追加する</span><span class="sxs-lookup"><span data-stu-id="0e563-102">Task 12: Adding Derived Column Transform to Add Columns Required by MDS</span></span>
  <span data-ttu-id="0e563-103">ここでは、派生列変換をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="0e563-103">In this task, you add the Derive Column Transform to the data flow.</span></span> <span data-ttu-id="0e563-104">この変換に渡されるレコードには、 **Importtype**と**batchtag**という2つの派生列を追加します。</span><span class="sxs-lookup"><span data-stu-id="0e563-104">You add two derived columns, **ImportType** and **BatchTag**, to the records passed to this transform.</span></span> <span data-ttu-id="0e563-105">MDS のステージング テーブルにデータをアップロードする前に、これらの列を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e563-105">You should add these columns before uploading the data to staging tables in MDS.</span></span> <span data-ttu-id="0e563-106">これら 2 つは、MDS のステージング テーブルに必要な列です。</span><span class="sxs-lookup"><span data-stu-id="0e563-106">These two are required columns for the staging tables in MDS.</span></span> <span data-ttu-id="0e563-107">詳細については、「[リーフメンバーステージングテーブル](../master-data-services/leaf-member-staging-table-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e563-107">See [Leaf Member Staging Tables](../master-data-services/leaf-member-staging-table-master-data-services.md) for more details.</span></span>  
  
1.  <span data-ttu-id="0e563-108">**SSIS ツールボックス**の [**共通**] セクションから [**データフロー** ] タブに、**派生列変換**をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="0e563-108">Drag-drop **Derived Column transform** from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="0e563-109">[**データフロー** ] タブで [**派生列**変換] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e563-109">Right-click **Derived Column** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="0e563-110">「 **MDS で必要な列**を追加 **」** と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0e563-110">Type **Add Columns Required by MDS** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="0e563-111">接続**フィルター**を使用して、blue コネクタを使用して**MDS で必要な列を追加**します。</span><span class="sxs-lookup"><span data-stu-id="0e563-111">Connect **Filter Duplicates** to **Add Columns Required by MDS** using the blue connector.</span></span> <span data-ttu-id="0e563-112">[**入力出力の選択**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e563-112">You should see the **Input Output Selection** dialog box.</span></span>  
  
4.  <span data-ttu-id="0e563-113">[**入力出力の選択**] ダイアログボックスで、[**一意のレコード**] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e563-113">In the **Input Output Selection** dialog box, select **Unique Records**, and click **OK**.</span></span>  
  
     <span data-ttu-id="0e563-114">![[入出力の選択] ダイアログ ボックス](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "[入出力の選択] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="0e563-114">![Input Output Selection Dialog Box](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "Input Output Selection Dialog Box")</span></span>  
  
5.  <span data-ttu-id="0e563-115">メニューバーの [ **SSIS** ] をクリックし、[**変数**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e563-115">Click **SSIS** on the menu bar and click **Variables**.</span></span>  
  
6.  <span data-ttu-id="0e563-116">[**変数**] ウィンドウで、ツールバーの [**変数の追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e563-116">In the **Variables** window, click **Add Variable** button on the toolbar.</span></span>  
  
     <span data-ttu-id="0e563-117">![[SSIS 変数] ウィンドウ](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "[SSIS 変数] ウィンドウ")</span><span class="sxs-lookup"><span data-stu-id="0e563-117">![SSIS Variables Window](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS Variables Window")</span></span>  
  
7.  <span data-ttu-id="0e563-118">[**名前**] に「 **importtype** 」と入力し、**値**に「 **2** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0e563-118">Type **ImportType** for the **Name** and **2** for the **value**.</span></span> <span data-ttu-id="0e563-119">MDS のエンティティに新しいメンバーを追加するため、値には 2 を指定します。</span><span class="sxs-lookup"><span data-stu-id="0e563-119">You specify the value as 2 because you want to add new members to an entity in MDS.</span></span> <span data-ttu-id="0e563-120">このパラメーターの詳細については、「[リーフメンバーステージングテーブル](../master-data-services/leaf-member-staging-table-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e563-120">For details about this parameter, see [Leaf Member Staging Table](../master-data-services/leaf-member-staging-table-master-data-services.md).</span></span>  
  
8.  <span data-ttu-id="0e563-121">[**変数の追加**] ツールバーボタンをもう一度クリックします。</span><span class="sxs-lookup"><span data-stu-id="0e563-121">Click **Add Variable** toolbar button again.</span></span>  
  
9. <span data-ttu-id="0e563-122">[**名前**] に「 **batchtag** 」と入力し **、データ型**として [**文字列**] を選択し、[**値**] に「 **eimbatch** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0e563-122">Type **BatchTag** for the **Name**, select **String** for the **Data type**, and **EIMBatch** for the **Value**.</span></span> <span data-ttu-id="0e563-123">**Batchtag**は、MDS に送信するバッチの一意の名前にすぎません。</span><span class="sxs-lookup"><span data-stu-id="0e563-123">**BatchTag** is just a unique name for the batch you will be submitting to MDS.</span></span>  
  
10. <span data-ttu-id="0e563-124">[**データフロー** ] タブで、[ **MDS に必要な列の追加**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e563-124">In the **Data Flow** tab, double-click **Add Columns Required by MDS**.</span></span>  
  
11. <span data-ttu-id="0e563-125">[**派生列変換エディター** ] ダイアログボックスの**下部ペインにあるリストボックス**で、**派生列名**として「 **importtype** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0e563-125">In the **Derived Column Transformation Editor** dialog box, in the **list box in the bottom pane**, type **ImportType** for the **Derived Column Name**.</span></span>  
  
12. <span data-ttu-id="0e563-126">左上のペインで [**変数とパラメーター** ] を展開し、 **User:: Importtype**を [**式**] 列にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="0e563-126">Expand **Variables and Parameters** in the top-left pane, drag-drop **User::ImportType** to the **Expression** column.</span></span>  
  
     <span data-ttu-id="0e563-127">![派生列変換エディター](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "派生列変換エディター")</span><span class="sxs-lookup"><span data-stu-id="0e563-127">![Derived Column Transformation Editor](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "Derived Column Transformation Editor")</span></span>  
  
13. <span data-ttu-id="0e563-128">**派生列の名前**として、次の行に「 **batchtag** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0e563-128">Type **BatchTag** in the next row for the **Derived Column Name**.</span></span>  
  
14. <span data-ttu-id="0e563-129">**ユーザー:: BatchTag**を**変数およびパラメーター**から [**式**] 列にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="0e563-129">Drag-drop **User::BatchTag** from **Variables and Parameters** to the **Expression** column.</span></span>  
  
15. <span data-ttu-id="0e563-130">[ **OK** ] をクリックして、[**派生列変換**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0e563-130">Click **OK** to close the **Derived Column Transformation** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="0e563-131">次の手順</span><span class="sxs-lookup"><span data-stu-id="0e563-131">Next Step</span></span>  
 [<span data-ttu-id="0e563-132">タスク 13: データを書き込む OLE DB 変換先を MDS ステージング テーブルに追加する</span><span class="sxs-lookup"><span data-stu-id="0e563-132">Task 13: Adding OLE DB Destination to Write Data to MDS Staging Table</span></span>](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
