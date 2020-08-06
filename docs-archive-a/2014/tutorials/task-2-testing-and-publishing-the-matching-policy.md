---
title: 'タスク 2: 照合ポリシーをテストして発行する |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 88bed2e91ca1fee3eab6136fb94df0d13328dc80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643660"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a><span data-ttu-id="08de7-102">タスク 2: 照合ポリシーをテストおよびパブリッシュする</span><span class="sxs-lookup"><span data-stu-id="08de7-102">Task 2: Testing and Publishing the Matching Policy</span></span>
  <span data-ttu-id="08de7-103">このタスクでは、[**重複する仕入先を削除**する] ポリシーをテストして発行します。</span><span class="sxs-lookup"><span data-stu-id="08de7-103">In this task, you test and publish the **Remove Duplicate Suppliers** matching policy.</span></span>  
  
1.  <span data-ttu-id="08de7-104">[**照合結果**] ページで、[**開始**] をクリックしてポリシー全体をテストします。</span><span class="sxs-lookup"><span data-stu-id="08de7-104">In the **Matching Results** page, click **Start** to test the entire policy.</span></span> <span data-ttu-id="08de7-105">この場合は、ポリシーに存在するルールが 1 つだけであるため、ルールとポリシーのテスト結果が同じになります。</span><span class="sxs-lookup"><span data-stu-id="08de7-105">In your case, you have only rule in the policy, so the results from testing the rule and the policy should be the same.</span></span>  
  
2.  <span data-ttu-id="08de7-106">リスト ボックスのすべての一致レコードと照合スコアを確認します。</span><span class="sxs-lookup"><span data-stu-id="08de7-106">Review all the matched records and their matching score in the list box.</span></span> <span data-ttu-id="08de7-107">**緑色**のアイコンが関連付けられているレコードは、その前にあるピボットレコードと重複しています。</span><span class="sxs-lookup"><span data-stu-id="08de7-107">A record that has a **Green** icon associated with it is a duplicate of the pivot record that precedes it.</span></span> <span data-ttu-id="08de7-108">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="08de7-108">Here are couple of examples:</span></span>  
  
    1.  <span data-ttu-id="08de7-109">レコード**id: 1000005**のレコードは、レコード**id が 1000004**のレコードと、**スコア: 100%** で一致します。これは、両方のレコードの値が、**仕入先 (前提条件)**、 **Supplier Name**、および ContactEmailAddress の各**列**に対して同じであるためです。</span><span class="sxs-lookup"><span data-stu-id="08de7-109">The record with **Record ID: 1000005** is a match of the record with **Record Id: 1000004** with **Score: 100%** because both the records have the same values for **SupplierID (prerequisite)**, **Supplier Name**, and **ContactEmailAddress columns**.</span></span> <span data-ttu-id="08de7-110">DQS はクラスターのピボット レコードとしてレコードをランダムに選択します。</span><span class="sxs-lookup"><span data-stu-id="08de7-110">DQS randomly picks a record as the pivot record for a cluster.</span></span>  
  
    2.  <span data-ttu-id="08de7-111">レコード**1000023**は、レコード**1000022**と照合スコア: 93% の一致と見なされます。これは、2つのレコードの値が**仕入先 (前提条件)** および**Supplier Name**列の値と同じでも、 **ContactEmailAddress**列の値が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="08de7-111">The record **1000023** is a match of the record **1000022** with the matching score: 93% because the two records have the same values for **SupplierID (prerequisite)** and **Supplier Name** columns, but different values for the **ContactEmailAddress** column.</span></span>  
  
    3.  <span data-ttu-id="08de7-112">一覧の一番下までスクロールすると、レコード Id が**1000051**と**1000052**の2つのレコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08de7-112">Scroll to the bottom of the list to see two records with records IDs: **1000051** and **1000052**.</span></span> <span data-ttu-id="08de7-113">レコード**1000052**は照合スコア**91%** と一致していると見なされます。これは、2つのレコードの**仕入**先列と**ContactEmailAddress**列の値が同じでも、 **Supplier Name**列の値が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="08de7-113">Record **1000052** is considered a match with matching score **91%** because the two records have the same values for the **SupplierID** and **ContactEmailAddress** columns, but different values for the **Supplier Name** column.</span></span>  
  
     <span data-ttu-id="08de7-114">![ポリシーの定義 - ポリシーの結果](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "ポリシーの定義 - ポリシーの結果")</span><span class="sxs-lookup"><span data-stu-id="08de7-114">![Policy Definition - Policy Results](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "Policy Definition - Policy Results")</span></span>  
  
3.  <span data-ttu-id="08de7-115">一致したレコード (緑色のアイコン) を右クリックし、[**詳細の表示**] をクリックすると、照合スコア全体に対する各フィールドスコアの貢献度などの照合に関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="08de7-115">Right-click on any matched record (with green icon) and click **View Details** to see more details about the matching such as contribution of each field score to the overall matching score.</span></span>  
  
     <span data-ttu-id="08de7-116">![[照合スコアの詳細] ダイアログ ボックス](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "[照合スコアの詳細] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="08de7-116">![Matching Score Details Dialog Box](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "Matching Score Details Dialog Box")</span></span>  
  
4.  <span data-ttu-id="08de7-117">[**閉じる**] をクリックして、[**照合スコアの詳細**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="08de7-117">Click **Close** to close the **Matching Score Details** dialog box.</span></span>  
  
5.  <span data-ttu-id="08de7-118">ページの下部にある [**照合結果**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="08de7-118">Click **Matching Results** tab at the bottom of the page.</span></span> <span data-ttu-id="08de7-119">このタブには、一致レコードの数、不一致レコードの数、一致レコードを持つクラスターの数、平均クラスター サイズ、最小クラスター サイズ、最大クラスター サイズなどの詳細が示されます。</span><span class="sxs-lookup"><span data-stu-id="08de7-119">This tab gives you detail such as number of matched records, number of unmatched records, number of clusters with matched records, the average cluster size, minimum cluster size, and maximum cluster size.</span></span> <span data-ttu-id="08de7-120">詳細について[は、「照合ポリシーの作成](https://msdn.microsoft.com/library/hh270290.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08de7-120">See [Create a Matching Policy](https://msdn.microsoft.com/library/hh270290.aspx) for more details.</span></span> <span data-ttu-id="08de7-121">このアクティビティの結果をエクスポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="08de7-121">You cannot export results from this activity.</span></span> <span data-ttu-id="08de7-122">サンプル データに対してルールおよびポリシーをテストするためにサンプル データを使用することで、照合ポリシーを定義するだけです。</span><span class="sxs-lookup"><span data-stu-id="08de7-122">You are just defining a matching policy by using the sample data to test rules and the policy against the sample data.</span></span>  
  
     <span data-ttu-id="08de7-123">![[照合結果] タブ](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "[照合結果] タブ")</span><span class="sxs-lookup"><span data-stu-id="08de7-123">![Matching Results Tab](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "Matching Results Tab")</span></span>  
  
6.  <span data-ttu-id="08de7-124">照合ポリシーの作成を完了するには、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08de7-124">Click **Finish** to finish creating the matching policy.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08de7-125">ここでは、照合ポリシーを定義しました。したがって、結果を出力ファイルにエクスポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="08de7-125">You have defined the matching policy here; therefore you cannot export results to an output file.</span></span> <span data-ttu-id="08de7-126">基本的には、ポリシーを定義する目的でサンプル入力ファイルを使用し、ルールを作成し、サンプル データに対してルールおよびポリシーをテストしました。</span><span class="sxs-lookup"><span data-stu-id="08de7-126">You basically used a sample input file, created rules, and tested the rules and policy against the sample data with the goal of defining the policy.</span></span>  
  
7.  <span data-ttu-id="08de7-127">[SQL Server Data Quality Services] ダイアログボックスで [**発行**] をクリックし、メッセージボックスの [ **OK** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08de7-127">In the SQL Server Data Quality Services dialog box, click **Publish** and click **OK** on the message box.</span></span> <span data-ttu-id="08de7-128">これで、定義した照合ポリシーが**サプライヤー**ナレッジベースに発行されます。</span><span class="sxs-lookup"><span data-stu-id="08de7-128">Now, the matching policy you defined is published into the **Suppliers** Knowledge Base.</span></span> <span data-ttu-id="08de7-129">このナレッジ ベースを使用して、入力ファイルに対して照合プロセスを実行し、重複を特定および削除できます。</span><span class="sxs-lookup"><span data-stu-id="08de7-129">You can use the knowledge base to run the matching process against an input file to identify and remove duplicates.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="08de7-130">次の手順</span><span class="sxs-lookup"><span data-stu-id="08de7-130">Next Step</span></span>  
 [<span data-ttu-id="08de7-131">タスク 3: 照合するデータ品質プロジェクトを作成および実行する</span><span class="sxs-lookup"><span data-stu-id="08de7-131">Task 3: Creating and Running a Data Quality Project for Matching</span></span>](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  
