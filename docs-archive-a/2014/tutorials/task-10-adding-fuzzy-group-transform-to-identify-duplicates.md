---
title: 'タスク 10: あいまいグループ化変換を追加して重複を識別する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 086625197850fdfd6381e9c0a4a7deac8ce3ae45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714889"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a><span data-ttu-id="ea2ac-102">タスク 10: あいまいグループ化変換を追加して重複を識別する</span><span class="sxs-lookup"><span data-stu-id="ea2ac-102">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>
  <span data-ttu-id="ea2ac-103">ここでは、あいまいグループ化変換をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-103">In this task, you add a Fuzzy Group Transform to the data flow.</span></span> <span data-ttu-id="ea2ac-104">あいまいグループ化変換は、変換元データの重複を識別する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-104">The Fuzzy Group transformation can help identify duplicates in the source data.</span></span> <span data-ttu-id="ea2ac-105">詳細については、「[あいまいグループ化変換](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-105">See [Fuzzy Grouping Transformation](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) for more details.</span></span>  
  
1.  <span data-ttu-id="ea2ac-106">**SSIS ツールボックス**の [**その他の変換**] にある [**あいまいグループ化**変換] を [**データフロー** ] タブにドラッグアンドドロップします。 [**正しいレコードと修正**されたレコードを結合します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-106">Drag-drop **Fuzzy Group** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Combine Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="ea2ac-107">[**データフロー** ] タブの [**あいまいグループ化**変換] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-107">Right-click **Fuzzy Group** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="ea2ac-108">「 **Id が一致するグループ仕入先**」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-108">Type **Group Suppliers with matching IDs** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="ea2ac-109">Blue コネクタを使用して、**適切なレコードと修正**されたレコードを結合し、 **id が一致する仕入先をグループ化**します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-109">Connect **Combine Correct and Corrected Records** to **Group Suppliers with matching IDs** using the blue connector.</span></span>  
  
     <span data-ttu-id="ea2ac-110">![ID が一致するグループ仕入先への接続](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "ID が一致するグループ仕入先への接続")</span><span class="sxs-lookup"><span data-stu-id="ea2ac-110">![Connection to Group Suppliers with Matching IDs](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Connection to Group Suppliers with Matching IDs")</span></span>  
  
4.  <span data-ttu-id="ea2ac-111">[ **Id が一致するグループ仕入先] を**ダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-111">Double-click **Group Suppliers with matching IDs**.</span></span>  
  
5.  <span data-ttu-id="ea2ac-112">[**あいまいグループ化変換エディター**] で、[ **OLE DB 接続マネージャー** ] ボックスの一覧の [**新規作成**] をクリックして、[ **OLE DB 接続マネージャーの構成**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-112">In the **Fuzzy Group Transformation Editor**, click **New** next to **OLE DB Connection Manager drop-down list** to launch **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
6.  <span data-ttu-id="ea2ac-113">ダイアログボックスで、[**新規**] をクリックして [**接続マネージャー** ] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-113">In the dialog box, click **New** to launch **Connection Manager** dialog box.</span></span>  
  
7.  <span data-ttu-id="ea2ac-114">サーバー名として「 **(local)** 」または「**ピリオド**(.)」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-114">Type **(local)** or **period** (.) for the Server name.</span></span>  
  
8.  <span data-ttu-id="ea2ac-115">**[データベース名の選択または入力**] フィールドに [ **MDS** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-115">Select **MDS** for **Select or enter a database name** field.</span></span> <span data-ttu-id="ea2ac-116">MDS データベースは、**あいまいグループ化変換**の一時ストレージとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-116">You will use the MDS database as the temporary storage for the **Fuzzy Group Transform**.</span></span> <span data-ttu-id="ea2ac-117">**あいまいグループ化**変換では、SQL Server のインスタンスに接続して、変換アルゴリズムで処理を行うために必要な一時 SQL Server テーブルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-117">The **Fuzzy Grouping** transformation requires a connection to an instance of SQL Server to create the temporary SQL Server tables that the transformation algorithm requires to do its work.</span></span> <span data-ttu-id="ea2ac-118">これを行うには、データベースを作成するか、別の既存のデータベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-118">You can create a database or use another existing database for this purpose.</span></span>  
  
9. <span data-ttu-id="ea2ac-119">[**接続テスト**] をクリックして接続をテストし、メッセージボックスの [ **OK** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-119">Click **Test Connection** to test the connection and click **OK** on the message box.</span></span>  
  
10. <span data-ttu-id="ea2ac-120">[**接続マネージャー** ] ダイアログボックスで、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-120">In the **Connection Manager** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="ea2ac-121">[ **(ローカル)] を選択します。MDS** (または**localhost。\*\*\*\*データ接続の一覧**から MDS) をクリックし、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-121">Select **(local).MDS** (or **localhost.MDS**) from the **list of Data Connections** and click **OK**.</span></span>  
  
12. <span data-ttu-id="ea2ac-122">[**あいまいグループ化変換エディター**] で、[(ローカル)] を確認し**ます。MDS**または**localhost。** **OLE DB 接続マネージャー**に対して MDS が選択されています。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-122">In the **Fuzzy Grouping Transformation Editor**, confirm that **(local).MDS** or **localhost.MDS** is selected for the **OLE DB Connection Manager**.</span></span>  
  
13. <span data-ttu-id="ea2ac-123">[**列**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-123">Switch to the **Columns** tab.</span></span>  
  
14. <span data-ttu-id="ea2ac-124">**使用できる入力列**の一覧から [(チェックボックス) **SupplierID_Output**を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-124">Select (check box) **SupplierID_Output** from the list of **Available Input Columns**.</span></span> <span data-ttu-id="ea2ac-125">変換を構成するには、重複部分を識別する際に使用する入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-125">To configure the transformation, select the input columns to use when identifying duplicates.</span></span> <span data-ttu-id="ea2ac-126">わかりやすくするために、この手順では SupplierID のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-126">To keep it simple, you only use the SupplierID in this step.</span></span>  
  
     <span data-ttu-id="ea2ac-127">![あいまいグループ化変換エディター](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "あいまいグループ化変換エディター")</span><span class="sxs-lookup"><span data-stu-id="ea2ac-127">![Fuzzy Grouping Transformation Editor](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Fuzzy Grouping Transformation Editor")</span></span>  
  
15. <span data-ttu-id="ea2ac-128">[ **OK]** をクリックして、[**あいまいグループ化変換エディター**] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="ea2ac-128">Click **OK** to close the **Fuzzy Group Transformation Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ea2ac-129">次の手順</span><span class="sxs-lookup"><span data-stu-id="ea2ac-129">Next Step</span></span>  
 [<span data-ttu-id="ea2ac-130">タスク 11: 条件分割変換を追加して重複をフィルターする</span><span class="sxs-lookup"><span data-stu-id="ea2ac-130">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
