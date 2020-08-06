---
title: 'タスク 7: DQS クレンジング変換をデータフローに追加する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 887bc361a51b61e9137404e054bd52e2b630ca5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632835"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a><span data-ttu-id="2c889-102">タスク 7: DQS クレンジング変換をデータ フローに追加する</span><span class="sxs-lookup"><span data-stu-id="2c889-102">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>
  <span data-ttu-id="2c889-103">ここでは、DQS クレンジング変換をデータ フローに追加して、入力済みの仕入先データを DQS を使用してクレンジングします。</span><span class="sxs-lookup"><span data-stu-id="2c889-103">In this task, you add DQS Cleansing Transform to the data flow to cleanse the input supplier data by using DQS.</span></span> <span data-ttu-id="2c889-104">変換の詳細については、「 **[DQS クレンジング変換](https://msdn.microsoft.com/library/ee677619.aspx)**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c889-104">See **[DQS Cleansing Transform](https://msdn.microsoft.com/library/ee677619.aspx)** for more details about the transform.</span></span>  
  
1.  <span data-ttu-id="2c889-105">[**データフロー** ] タブで [ **DQS クレンジング**] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c889-105">Right-click **DQS Cleansing** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="2c889-106">「**クレンジング Supplier Data**」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2c889-106">Type **Cleanse Supplier Data**, and press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="2c889-107">[ **Excel ファイルから Supplier データを読み取る**] を選択します。blue コネクタをドラッグして、**仕入先データをクレンジング**します。</span><span class="sxs-lookup"><span data-stu-id="2c889-107">Select **Read Supplier Data from Excel File**; drag the blue connector to **Cleanse Supplier Data**.</span></span> <span data-ttu-id="2c889-108">これでコンポーネントが接続されました。</span><span class="sxs-lookup"><span data-stu-id="2c889-108">The components are now connected.</span></span>  
  
     <span data-ttu-id="2c889-109">![Supplier データの読み取り-Supplier データのクレンジング >](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "仕入先データの読み取り -> 仕入先データのクレンジング")</span><span class="sxs-lookup"><span data-stu-id="2c889-109">![Read Supplier Data -> Cleanse Supplier Data](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Read Supplier Data -> Cleanse Supplier Data")</span></span>  
  
3.  <span data-ttu-id="2c889-110">[**仕入先データのクレンジング**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c889-110">Double-click **Cleanse Supplier Data**.</span></span>  
  
4.  <span data-ttu-id="2c889-111">[ **DQS クレンジング変換エディター**] で、[**データ品質接続マネージャー] ボックスの一覧**の横にある [**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c889-111">In the **DQS Cleansing Transformation Editor**, click **New** next to the **Data Quality Connection Manager drop-down list**.</span></span>  
  
5.  <span data-ttu-id="2c889-112">[ **DQS クレンジング接続マネージャー** ] ダイアログボックスで、ローカルサーバーに接続する場合は「 **(local)** 」または「**ピリオド**(.)」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2c889-112">In the **DQS Cleansing Connection Manager** dialog box, type **(local)** or **period** (.) to connect to the local server.</span></span> <span data-ttu-id="2c889-113">このレッスンは、ローカル サーバーに DQS がインストールされていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="2c889-113">This lesson assumes that you have DQS installed on a local server.</span></span>  
  
6.  <span data-ttu-id="2c889-114">[**テスト接続**] をクリックして DQS サーバーへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="2c889-114">Click **Test Connection** to test the connection to DQS server.</span></span>  
  
7.  <span data-ttu-id="2c889-115">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2c889-115">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="2c889-116">**データ品質ナレッジベース**の [**仕入先**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c889-116">Select **Suppliers** for the **Data Quality Knowledge Base**.</span></span>  
  
     <span data-ttu-id="2c889-117">![DQS クレンジング変換エディター - 仕入先 KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS クレンジング変換エディター - 仕入先 KB")</span><span class="sxs-lookup"><span data-stu-id="2c889-117">![DQS Cleansing Transformation Editor - Suppliers KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS Cleansing Transformation Editor - Suppliers KB")</span></span>  
  
9. <span data-ttu-id="2c889-118">上部の [**マッピング**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="2c889-118">Switch to the **Mapping** tab at the top.</span></span>  
  
10. <span data-ttu-id="2c889-119">[**使用できる入力列**] で、チェックボックスをオンにして [ **Supplier Name**]、[ **ContactEmailAddress**]、[ **Address Line** **]、[\*\*\*\*市区町村**]、[ **Country**]、[**郵便**番号] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c889-119">From **Available Input Columns**, select **Supplier Name**, **ContactEmailAddress**, **Address Line**, **City**, **State**, **Country**, and **Zip Code** by selecting the check boxes.</span></span>  
  
     <span data-ttu-id="2c889-120">![DQS クレンジング変換エディター - マッピング](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS クレンジング変換エディター - マッピング")</span><span class="sxs-lookup"><span data-stu-id="2c889-120">![DQS Cleansing Transformation Editor - Mappings](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS Cleansing Transformation Editor - Mappings")</span></span>  
  
11. <span data-ttu-id="2c889-121">下のペインで、[**ドメイン**] 列のドロップダウンリストを使用してこれらの列をマップします。</span><span class="sxs-lookup"><span data-stu-id="2c889-121">In the bottom pane, map these columns by using drop-down lists in the **Domain** column:</span></span>  
  
    |<span data-ttu-id="2c889-122">列</span><span class="sxs-lookup"><span data-stu-id="2c889-122">Column</span></span>|<span data-ttu-id="2c889-123">Domain</span><span class="sxs-lookup"><span data-stu-id="2c889-123">Domain</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="2c889-124">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="2c889-124">Supplier Name</span></span>|<span data-ttu-id="2c889-125">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="2c889-125">Supplier Name</span></span>|  
    |<span data-ttu-id="2c889-126">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="2c889-126">ContactEmailAddress</span></span>|<span data-ttu-id="2c889-127">連絡先のメール アドレス</span><span class="sxs-lookup"><span data-stu-id="2c889-127">Contact Email</span></span>|  
    |<span data-ttu-id="2c889-128">Address Line</span><span class="sxs-lookup"><span data-stu-id="2c889-128">Address Line</span></span>|<span data-ttu-id="2c889-129">Address Line</span><span class="sxs-lookup"><span data-stu-id="2c889-129">Address Line</span></span>|  
    |<span data-ttu-id="2c889-130">City</span><span class="sxs-lookup"><span data-stu-id="2c889-130">City</span></span>|<span data-ttu-id="2c889-131">City</span><span class="sxs-lookup"><span data-stu-id="2c889-131">City</span></span>|  
    |<span data-ttu-id="2c889-132">State</span><span class="sxs-lookup"><span data-stu-id="2c889-132">State</span></span>|<span data-ttu-id="2c889-133">State</span><span class="sxs-lookup"><span data-stu-id="2c889-133">State</span></span>|  
    |<span data-ttu-id="2c889-134">国</span><span class="sxs-lookup"><span data-stu-id="2c889-134">Country</span></span>|<span data-ttu-id="2c889-135">国</span><span class="sxs-lookup"><span data-stu-id="2c889-135">Country</span></span>|  
    |<span data-ttu-id="2c889-136">Zip Code</span><span class="sxs-lookup"><span data-stu-id="2c889-136">Zip Code</span></span>|<span data-ttu-id="2c889-137">Zip</span><span class="sxs-lookup"><span data-stu-id="2c889-137">Zip</span></span>|  
  
12. <span data-ttu-id="2c889-138">[ **OK]** をクリックして [ **DQS クレンジング変換エディター** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2c889-138">Click **OK** to close the **DQS Cleansing Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2c889-139">次の手順</span><span class="sxs-lookup"><span data-stu-id="2c889-139">Next Step</span></span>  
 [<span data-ttu-id="2c889-140">タスク 8: 条件分割変換を追加してクレンジング出力を分割する</span><span class="sxs-lookup"><span data-stu-id="2c889-140">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
