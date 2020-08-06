---
title: 'タスク 6: クレンジング業者リストプロジェクトから値をインポートする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b674cfb42ddf31c3b903a465d1be1b04e9a355ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632841"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a><span data-ttu-id="4ec62-102">タスク 6: Cleanse Supplier List プロジェクトから値をインポートする</span><span class="sxs-lookup"><span data-stu-id="4ec62-102">Task 6: Importing Values from the Cleanse Supplier List Project</span></span>
  <span data-ttu-id="4ec62-103">ここでは、クレンジング プロセスで収集したデータ品質ナレッジをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-103">In this task, you import the data quality knowledge gathered during the cleansing process.</span></span> <span data-ttu-id="4ec62-104">詳細について[は、「ドメインへのクレンジングプロジェクトの値のインポート](https://msdn.microsoft.com/library/hh479581.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ec62-104">See [Importing Cleansing Project Values into a Domain](https://msdn.microsoft.com/library/hh479581.aspx) topic for more details.</span></span> <span data-ttu-id="4ec62-105">また、更新された**サプライヤー**ナレッジベースを公開する前に、ナレッジベースを DQS ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-105">You also export the knowledge base into a DQS file before publishing the updated **Suppliers** knowledge base.</span></span>  
  
1.  <span data-ttu-id="4ec62-106">**DQS クライアント**のメインページで、[**最近使用したナレッジベース**] の [**仕入先**] の横に**ある右矢印**をクリックし、[**ドメイン管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-106">In the main page of **DQS Client**, click **right-arrow** next to **Suppliers** under **Recent Knowledge Bases** and click **Domain Management**.</span></span>  
  
2.  <span data-ttu-id="4ec62-107">ドメインの一覧で [**連絡先の電子メール**] をクリックし、右ペインの [**ドメイン値**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4ec62-107">Click **Contact Email** in the list of domains, and switch to the **Domain Values** tab in the right pane.</span></span>  
  
3.  <span data-ttu-id="4ec62-108">ツールバーの [値の**インポート**] アイコンの横に**ある下矢印**をクリックし、[**プロジェクト値のインポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-108">Click **down arrow** next to the **Import Values** icon on the toolbar and click **Import Project Values**.</span></span>  
  
     <span data-ttu-id="4ec62-109">![[プロジェクトの値のインポート] ツール バー ボタン](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "[プロジェクトの値のインポート] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="4ec62-109">![Import Project Values Toolbar Button](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "Import Project Values Toolbar Button")</span></span>  
  
4.  <span data-ttu-id="4ec62-110">[**プロジェクト値のインポート**] ダイアログボックスで、[**仕入先リストのクレンジング**] プロジェクトを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-110">In the **Import Project Values** dialog box, select the **Cleanse Supplier List** project, and click **OK**.</span></span>  
  
5.  <span data-ttu-id="4ec62-111">すべての電子メールが、インタラクティブなクレンジングで行った 2 つの修正と共にインポートされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4ec62-111">Notice that all the emails are imported along with the two corrections you did during interactive cleansing.</span></span> <span data-ttu-id="4ec62-112">スクロールして 2 つの修正を確認します。</span><span class="sxs-lookup"><span data-stu-id="4ec62-112">Scroll to see the two corrections.</span></span>  
  
    |<span data-ttu-id="4ec62-113">値</span><span class="sxs-lookup"><span data-stu-id="4ec62-113">Value</span></span>|<span data-ttu-id="4ec62-114">次に修正</span><span class="sxs-lookup"><span data-stu-id="4ec62-114">Correct To</span></span>|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  <span data-ttu-id="4ec62-115">**Country**ドメインのプロジェクト値をインポートする前の手順を繰り返し、**米国**を修正するために新しいエントリが追加されていることを確認します (を使用して**米国**)。</span><span class="sxs-lookup"><span data-stu-id="4ec62-115">Repeat the previous step of importing project values for the **Country** domain and notice that a new entry is added for correcting **United State** to **United States** (with 's').</span></span>  
  
    |<span data-ttu-id="4ec62-116">値</span><span class="sxs-lookup"><span data-stu-id="4ec62-116">Value</span></span>|<span data-ttu-id="4ec62-117">次に修正</span><span class="sxs-lookup"><span data-stu-id="4ec62-117">Correct To</span></span>|  
    |-----------|----------------|  
    |<span data-ttu-id="4ec62-118">United State</span><span class="sxs-lookup"><span data-stu-id="4ec62-118">United State</span></span>|<span data-ttu-id="4ec62-119">United States</span><span class="sxs-lookup"><span data-stu-id="4ec62-119">United States</span></span>|  
  
7.  <span data-ttu-id="4ec62-120">古いドメイン値を表示するには、[**新規のみ表示**] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-120">To see the old domain values, clear **Show Only New** checkbox.</span></span>  
  
8.  <span data-ttu-id="4ec62-121">**Supplier Name**ドメインのプロジェクト値をインポートする前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="4ec62-121">Repeat the previous step of importing project values for the **Supplier Name** domain.</span></span> <span data-ttu-id="4ec62-122">インポート後は、既定で新しい値だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ec62-122">By default, after importing, you will only see the new values.</span></span> <span data-ttu-id="4ec62-123">すべての値を表示するには、[**新規のみ表示**] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-123">To see all the values, clear **Show Only New** check box.</span></span> <span data-ttu-id="4ec62-124">ここでは、クレンジングアクティビティから学習した内容に基づいて、**サプライヤー**のナレッジベースを強化しました。</span><span class="sxs-lookup"><span data-stu-id="4ec62-124">You have enriched the **Suppliers** knowledge base with what you learned from the cleansing activity.</span></span> <span data-ttu-id="4ec62-125">ナレッジ ベースが充実するほど、クレンジング結果が向上します。</span><span class="sxs-lookup"><span data-stu-id="4ec62-125">The stronger the knowledge base is, the better the cleansing results are.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4ec62-126">複合ドメインの値をインポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4ec62-126">It is not possible import values for a composite domain.</span></span>  
  
9. <span data-ttu-id="4ec62-127">ツールバーの [**ナレッジベースのエクスポート**] アイコンをクリックし、[**ナレッジベースのエクスポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-127">Click **Export Knowledge Base** icon on the toolbar and then click **Export Knowledge Base**.</span></span>  
  
     <span data-ttu-id="4ec62-128">![[ナレッジ ベースのエクスポート] メニュー](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "[ナレッジ ベースのエクスポート] メニュー")</span><span class="sxs-lookup"><span data-stu-id="4ec62-128">![Export Knowledge Base Menu](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Export Knowledge Base Menu")</span></span>  
  
10. <span data-ttu-id="4ec62-129">チュートリアルフォルダーに移動し、**ファイル名**として「「**仕入先**」と入力して、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-129">Navigate to the Tutorial folder, type **Suppliers.dqs** for the **file name**, and click **Save**.</span></span> <span data-ttu-id="4ec62-130">この DQS ファイルを使用して、これに基づく新しいナレッジ ベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4ec62-130">You can use this DQS file to create a new knowledge base based on it.</span></span>  
  
11. <span data-ttu-id="4ec62-131">[ **OK]** をクリックして、[**ナレッジベースのエクスポート-サプライヤー** ] メッセージボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4ec62-131">Click **OK** to close the **Export Knowledge Base - Suppliers** message box.</span></span>  
  
12. <span data-ttu-id="4ec62-132">[**完了**] をクリックして活動を終了します。</span><span class="sxs-lookup"><span data-stu-id="4ec62-132">Click **Finish** to finish the activity.</span></span>  
  
13. <span data-ttu-id="4ec62-133">**[発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-133">Click **Publish**.</span></span>  
  
14. <span data-ttu-id="4ec62-134">メッセージボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ec62-134">Click **OK** on the message box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="4ec62-135">次の手順</span><span class="sxs-lookup"><span data-stu-id="4ec62-135">Next Step</span></span>  
 [<span data-ttu-id="4ec62-136">レッスン 3: データを照合して仕入先の一覧から重複を削除する</span><span class="sxs-lookup"><span data-stu-id="4ec62-136">Lesson 3: Matching Data to Remove Duplicates from Supplier List</span></span>](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  
