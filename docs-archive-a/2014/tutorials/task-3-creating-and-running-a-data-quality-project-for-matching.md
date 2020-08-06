---
title: 'タスク 3: 照合用のデータ品質プロジェクトを作成して実行する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 221d6d583c61ee035c20fcb63f0ed5278f2b8678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632850"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a><span data-ttu-id="83ec0-102">タスク 3: 照合するデータ品質プロジェクトを作成および実行する</span><span class="sxs-lookup"><span data-stu-id="83ec0-102">Task 3: Creating and Running a Data Quality Project for Matching</span></span>
  <span data-ttu-id="83ec0-103">ここでは、照合アクティビティ用のデータ品質プロジェクトを作成し、クレンジングされた仕入先データで照合プロセスを実行して、データ内の重複部分を削除します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-103">In this task, you create a Data Quality Project for the matching activity and run the matching process on cleansed supplier data to remove any duplicates in the data.</span></span>

1.  <span data-ttu-id="83ec0-104">**DQS クライアント**のメインページで、[**新しいデータ品質プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83ec0-104">On the main page of **DQS Client**, click **New Data Quality Project**.</span></span>

2.  <span data-ttu-id="83ec0-105">「**削除業者の重複**を**プロジェクトの名前**から削除」と入力します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-105">Type **Remove Supplier Duplicates** from the **Name of the project**.</span></span>

3.  <span data-ttu-id="83ec0-106">[**ナレッジベースを使用**] フィールドの kb の一覧から [**仕入先**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-106">Select **Suppliers** from the list of KBs for the **Use Knowledge Base** field.</span></span> <span data-ttu-id="83ec0-107">前のレッスンでは、このナレッジ ベースの照合ポリシーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="83ec0-107">You have created a matching policy in this knowledge base in the previous lesson.</span></span>

4.  <span data-ttu-id="83ec0-108">右下のペインで、**アクティビティの一覧**から [**照合**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-108">Select **Matching** from the **list of activities** from the bottom-right pane.</span></span>

     <span data-ttu-id="83ec0-109">![新しいデータ品質プロジェクト - 照合が選択された状態](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "新しいデータ品質プロジェクト - 照合が選択された状態")</span><span class="sxs-lookup"><span data-stu-id="83ec0-109">![New Data Quality Project - Matching Selected](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "New Data Quality Project - Matching Selected")</span></span>

5.  <span data-ttu-id="83ec0-110">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83ec0-110">Click **Next**.</span></span>

6.  <span data-ttu-id="83ec0-111">**[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-111">In the **Map** page, select **Excel File** for **Data Source**.</span></span>

7.  <span data-ttu-id="83ec0-112">[**参照**] をクリックし、クレンジングアクティビティの出力ファイルである [クレンジングされた**Supplier List.xls**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-112">Click **Browse** and select **Cleansed Supplier List.xls**, which is the output file from the cleansing activity.</span></span>

8.  <span data-ttu-id="83ec0-113">[**仕入先** **ID** ] ドメイン、[ **supplier name** ] 列を [supplier **Name** domain] にマップし、 **ContactEmailAddress**列を [ **Contact Email** domain] にマップします。</span><span class="sxs-lookup"><span data-stu-id="83ec0-113">Map **SupplierID** source column to the **Supplier ID** domain, **Supplier Name** column to **Supplier Name** domain, and **ContactEmailAddress** column to **Contact Email** domain.</span></span>

9. <span data-ttu-id="83ec0-114">[**次へ**] をクリックして、**一致**するページに移動します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-114">Click **Next** to switch to the **Matching** page.</span></span>

10. <span data-ttu-id="83ec0-115">[**開始**] をクリックして照合プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-115">Click **Start** to start the matching process.</span></span> <span data-ttu-id="83ec0-116">照合ポリシーを定義する際に同じ入力ファイルを使用したため、前のタスクの結果と同様の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83ec0-116">You should see results similar to those from the previous task because you used the same input file for defining the matching policy.</span></span>

11. <span data-ttu-id="83ec0-117">リスト ボックスのすべての一致レコードと照合スコアを確認します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-117">Review all the matched records and their matching score in the list box.</span></span> <span data-ttu-id="83ec0-118">この結果は、前のタスクで表示された結果と同じになります。</span><span class="sxs-lookup"><span data-stu-id="83ec0-118">The results should be same as the ones you saw in the previous task.</span></span> <span data-ttu-id="83ec0-119">この照合アクティビティの結果を解析するには、前のタスクの手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83ec0-119">See the steps in the previous task to analyze the results from this matching activity.</span></span>

12. <span data-ttu-id="83ec0-120">[**次へ**] をクリックして、[**エクスポート**] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="83ec0-120">Click **Next** to switch to the **Export** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="83ec0-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="83ec0-121">Next Step</span></span>
 [<span data-ttu-id="83ec0-122">タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="83ec0-122">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)


