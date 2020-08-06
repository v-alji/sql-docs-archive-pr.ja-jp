---
title: 'タスク 1: 照合ポリシーを定義する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f89a720-fce5-4f60-bef3-a159bbc9f25c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bb2556874174939c46d91c6d89e797393d590914
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632221"
---
# <a name="task-1-defining-a-matching-policy"></a><span data-ttu-id="1267e-102">タスク 1: 照合ポリシーを定義する</span><span class="sxs-lookup"><span data-stu-id="1267e-102">Task 1: Defining a Matching Policy</span></span>
  <span data-ttu-id="1267e-103">ここでは、1 つのルールを持つ照合ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1267e-103">In this task, you create a matching policy with one rule in it.</span></span> <span data-ttu-id="1267e-104">このルールには、 **SUPPLIER id**という1つの前提条件があります。これは、ルール内の他のドメインを使用する前に、業者 id が一致する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1267e-104">The rule will have one prerequisite: **Supplier ID**, which means that the Supplier IDs must match before using the other domains in the rule.</span></span> <span data-ttu-id="1267e-105">このルールでは、2つの他のドメインを使用します。 "**類似性**" の値が**70%** に設定されている**Supplier Name** 、および**類似性**の値が**30%** に設定されている**連絡先の電子メール**</span><span class="sxs-lookup"><span data-stu-id="1267e-105">The rule uses two other domains: **Supplier Name** with **Similarity** value set to **70%** and **Contact Email** with **Similarity** value set to **30%**.</span></span>  
  
1.  <span data-ttu-id="1267e-106">**DQS クライアント**のメインページで、[**仕入先**のナレッジベース] の横に**ある右矢印**をクリックし、[**照合ポリシー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1267e-106">In the main page of **DQS Client**, click **right-arrow** next to **Suppliers** knowledge base, and select **Matching Policy**.</span></span>  
  
     <span data-ttu-id="1267e-107">![メイン ページでの [照合ポリシー] メニュー](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "メイン ページでの [照合ポリシー] メニュー")</span><span class="sxs-lookup"><span data-stu-id="1267e-107">![Matching Policy Menu on Main Page](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "Matching Policy Menu on Main Page")</span></span>  
  
2.  <span data-ttu-id="1267e-108">[**マップ**] ページで、[**データソース**用の**Excel ファイル**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1267e-108">On the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
3.  <span data-ttu-id="1267e-109">[**参照**] をクリックして、[フィルター] が [ **Excel ブック**] に設定されていることを確認し、クレンジングアクティビティの実行後にエクスポートした [クレンジングされた**Supplier List.xls**ファイル] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1267e-109">Click **Browse**, ensure that filter is set to **Excel Workbook**, and select **Cleansed Supplier List.xls** file that you exported after you perform the cleansing activity.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1267e-110">このアクティビティは照合ポリシーの定義を主な目的としています。このため、このアクティビティの最後に結果をエクスポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1267e-110">At the end of this activity, you cannot export results because this activity is primarily focused on defining a matching policy.</span></span> <span data-ttu-id="1267e-111">次のレッスンでは、照合アクティビティ用のデータ品質プロジェクトを作成し、この照合ポリシーを使用して仕入先の一覧から重複を削除します。</span><span class="sxs-lookup"><span data-stu-id="1267e-111">You will create a Data Quality Project for the Matching activity and run it to remove duplicates from the supplier list by using this matching policy in the next lesson.</span></span>  
  
4.  <span data-ttu-id="1267e-112">[**仕入先** **ID**ドメイン]、[ **supplier name** ] 列を [supplier **name** domain] にマップし、[ **ContactEmailAddress** ] 列を [ **Contact Email** domain] にマップします。</span><span class="sxs-lookup"><span data-stu-id="1267e-112">Map **SupplierID** column to **Supplier ID** domain, **Supplier Name** column to **Supplier Name** domain, **ContactEmailAddress** column to **Contact Email** domain.</span></span> <span data-ttu-id="1267e-113">照合ポリシーの定義で使用するドメインのみにソース列をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1267e-113">You only need to map source columns to domains that you want to use in defining the matching policy.</span></span> <span data-ttu-id="1267e-114">このレッスンでは、照合ポリシー アクティビティで使用するための Supplier ID、Supplier Name、および Contact Email ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="1267e-114">In this case, you are making the Supplier ID, Supplier Name, and Contact Email domains available for the matching policy activity.</span></span>  
  
     <span data-ttu-id="1267e-115">![照合ポリシーの定義処理のマップ ページ](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "照合ポリシーの定義処理のマップ ページ")</span><span class="sxs-lookup"><span data-stu-id="1267e-115">![Map Page of Matching Policy Definition Process](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "Map Page of Matching Policy Definition Process")</span></span>  
  
5.  <span data-ttu-id="1267e-116">[**次へ**] をクリックして [**照合ポリシー** ] ページに移動します。このページでは、1つのルールを含む照合ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="1267e-116">Click **Next** to move to the **Matching Policy** page where you will be defining a matching policy with one rule in it.</span></span>  
  
6.  <span data-ttu-id="1267e-117">ツールバーの [**照合ルールの作成**] ボタンをクリックして、ポリシーにルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="1267e-117">Click **Create a matching rule** button on the toolbar to create a rule in the policy.</span></span>  
  
     <span data-ttu-id="1267e-118">![[照合ルールを作成します] ツール バー ボタン](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "[照合ルールを作成します] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="1267e-118">![Create a Matching Rule Toolbar Button](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "Create a Matching Rule Toolbar Button")</span></span>  
  
7.  <span data-ttu-id="1267e-119">右側の**ルールの詳細**ウィンドウで、[**ルール名**] に「**重複する仕入先を削除**する」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1267e-119">In the **Rule Details** pane on the right, enter **Remove Duplicate Suppliers** for the **Rule name**.</span></span>  
  
8.  <span data-ttu-id="1267e-120">右ペインのツールバーで、[**新しいドメイン要素の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1267e-120">Click **Add a new domain element** in the toolbar in the right pane.</span></span>  
  
     <span data-ttu-id="1267e-121">![規則の詳細-[新しいドメイン要素の追加] ボタン](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "規則の詳細-[新しいドメイン要素の追加] ボタン")</span><span class="sxs-lookup"><span data-stu-id="1267e-121">![Rule Details - Add a New Domain Element Button](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "Rule Details - Add a New Domain Element Button")</span></span>  
  
9. <span data-ttu-id="1267e-122">**ドメイン**の [ **Supplier ID** ] を選択し、[**前提条件**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1267e-122">Select **Supplier ID** for the **domain** and select the **Prerequisite** check box.</span></span> <span data-ttu-id="1267e-123">**類似性**が自動的に**Exact**に設定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1267e-123">Notice that **Similarity** is automatically set to **Exact**.</span></span> <span data-ttu-id="1267e-124">**SUPPLIER ID**を**前提条件**として設定することにより、2つのレコードのこのフィールドの値が100% の一致を返す必要があることを指定します。そうしないと、レコードは一致と見なされず、ルール内の他の句は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1267e-124">By setting **Supplier ID** as the **Prerequisite**, you specify that the values for this field in the two records must return a 100% match, else the records are not considered a match and the other clauses in the rule are disregarded.</span></span>  
  
     <span data-ttu-id="1267e-125">![重複する仕入先を削除するルールの定義](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "重複する仕入先を削除するルールの定義")</span><span class="sxs-lookup"><span data-stu-id="1267e-125">![Remove Duplicate Suppliers Rule Definition](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "Remove Duplicate Suppliers Rule Definition")</span></span>  
  
10. <span data-ttu-id="1267e-126">ツールバーの [**新しいドメイン要素の追加**] をもう一度クリックします。</span><span class="sxs-lookup"><span data-stu-id="1267e-126">Click **Add a new domain element** from the toolbar again.</span></span>  
  
11. <span data-ttu-id="1267e-127">[ **Supplier Name** domain] を選択し、[**類似性**] で [**類似**] を選択し、[**重み**] に「 **70** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1267e-127">Select **Supplier Name** domain, select **Similar** for **Similarity**, and Type **70** for the **Weight**.</span></span>  <span data-ttu-id="1267e-128">ここでは、レコードが一致と見なされるためには仕入先名が類似しているだけでよいこと、つまり完全に一致しなくてもよいことを指定しています。</span><span class="sxs-lookup"><span data-stu-id="1267e-128">Here, you are specifying that supplier names do not need to be identical but can be similar for the records to be considered as a match.</span></span> <span data-ttu-id="1267e-129">重みは、このフィールドのスコアが全体的な照合スコアにどのように影響するかを示します。</span><span class="sxs-lookup"><span data-stu-id="1267e-129">The weight indicates the contribution of this field's score to the overall matching score.</span></span>  
  
12. <span data-ttu-id="1267e-130">前の2つの手順を繰り返し**て、連絡先の電子メール**ドメインを、その**重み**に**30**を追加します。</span><span class="sxs-lookup"><span data-stu-id="1267e-130">Repeat previous two steps to add **Contact Email** domain with **30** for the **Weight**.</span></span>  
  
13. <span data-ttu-id="1267e-131">**最小照合スコア**が**80%** に設定されていることに注意してください。これは、 **DQS 管理**の [**構成**] ページの **[全般**] タブに表示される値です。</span><span class="sxs-lookup"><span data-stu-id="1267e-131">Notice that the **min matching score** is set to **80%**, which is the value you see in the **General** tab of the **Configuration** page of **DQS Administration**.</span></span> <span data-ttu-id="1267e-132">このスコアは、しきい値より大きな値に増やすことだけができます。</span><span class="sxs-lookup"><span data-stu-id="1267e-132">You can only increase this score above this threshold value here.</span></span>  
  
14. <span data-ttu-id="1267e-133">[**重複するクラスター** ] オプションが選択されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1267e-133">Notice that **Overlapping Clusters** option is selected.</span></span> <span data-ttu-id="1267e-134">このオプションを使用すると、レコードを複数のクラスターに表示できます。</span><span class="sxs-lookup"><span data-stu-id="1267e-134">With this option, a record can show up in multiple clusters.</span></span> <span data-ttu-id="1267e-135">[重複しないクラスター] に設定を変更すると、共通のレコードを持つクラスターが 1 つのクラスターに結合されます。</span><span class="sxs-lookup"><span data-stu-id="1267e-135">If you change the setting to Non-Overlapping Clusters, the clusters that have common records are combined into one single cluster.</span></span>  
  
15. <span data-ttu-id="1267e-136">このページの [**開始**] ボタンを使用すると、ポリシー内の各ルールを個別にテストできます。一方、次のページの [開始] ボタンをクリックすると、ポリシー全体 (ポリシー内のすべてのルール) をテストできます。</span><span class="sxs-lookup"><span data-stu-id="1267e-136">The **Start** button on this page allows you to test each rule in the policy separately, whereas, the Start button in the next page allows you to test entire policy (all the rules in the policy).</span></span>  
  
16. <span data-ttu-id="1267e-137">[**次へ**] をクリックして、[**照合結果**] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="1267e-137">Click **Next** to switch to the **Matching Results** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1267e-138">次の手順</span><span class="sxs-lookup"><span data-stu-id="1267e-138">Next Step</span></span>  
 [<span data-ttu-id="1267e-139">タスク 2: 照合ポリシーをテストおよびパブリッシュする</span><span class="sxs-lookup"><span data-stu-id="1267e-139">Task 2: Testing and Publishing the Matching Policy</span></span>](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  
