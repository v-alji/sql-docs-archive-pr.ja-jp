---
title: 'タスク 9: マスターデータマネージャー | を使用して派生階層を作成するMicrosoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5c85750e4556722c6e6a5edbccb4a3c82c119a74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742678"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a><span data-ttu-id="bb5b2-102">タスク 9: マスター データ マネージャーを使用して派生階層を作成する</span><span class="sxs-lookup"><span data-stu-id="bb5b2-102">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>
  <span data-ttu-id="bb5b2-103">ここでは、マスター データ マネージャーを使用して派生階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-103">In this task, you create a derived hierarchy by using Master Data Manager.</span></span> <span data-ttu-id="bb5b2-104">この派生階層は、 **Supplier**エンティティと**State**エンティティ間のドメインベースの属性リレーションシップから派生します。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-104">This derived hierarchy is derived from the domain-based attribute relationships between the **Supplier** and **State** entities.</span></span>  
  
1.  <span data-ttu-id="bb5b2-105">ページの上部にある**SQL Server 2012 マスターデータサービス**をクリックして**マスターデータマネージャー**のメインページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-105">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
2.  <span data-ttu-id="bb5b2-106">[**管理タスク**] セクションで [**システム管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-106">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="bb5b2-107">メニューバーの [**管理**] の上にマウスポインターを移動し、[**派生階層**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-107">Hover the mouse over **Manage** on the menu bar, and click **Derived Hierarchies**.</span></span>  
  
     <span data-ttu-id="bb5b2-108">![[管理] メニュー - 派生階層が選択された状態](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "[管理] メニュー - 派生階層が選択された状態")</span><span class="sxs-lookup"><span data-stu-id="bb5b2-108">![Manage Menu - Derived Hierarchies Selected](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Manage Menu - Derived Hierarchies Selected")</span></span>  
  
4.  <span data-ttu-id="bb5b2-109">ツールバーの [**派生階層の追加] (+)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-109">Click **Add Derived Hierarchy (+)** button on the toolbar.</span></span>  
  
     <span data-ttu-id="bb5b2-110">![[派生階層の追加] ボタン](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "[派生階層の追加] ボタン")</span><span class="sxs-lookup"><span data-stu-id="bb5b2-110">![Add Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "Add Derived Hierarchy Button")</span></span>  
  
5.  <span data-ttu-id="bb5b2-111">**派生階層名**として「 **SuppliersInState** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-111">Type **SuppliersInState** for the **Derived hierarchy name**.</span></span>  
  
6.  <span data-ttu-id="bb5b2-112">ツールバーの [**保存**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-112">Click **Save** button on the toolbar.</span></span>  
  
     <span data-ttu-id="bb5b2-113">![[派生階層の保存] ボタン](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "[派生階層の保存] ボタン")</span><span class="sxs-lookup"><span data-stu-id="bb5b2-113">![Save Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "Save Derived Hierarchy Button")</span></span>  
  
7.  <span data-ttu-id="bb5b2-114">[**使用可能なレベル: SuppliersInState**から**現在のレベル: SuppliersInState**に**仕入先**をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-114">Drag **Supplier** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span>  
  
     <span data-ttu-id="bb5b2-115">![使用できるエンティティと階層から現在のレベルへ](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "使用できるエンティティと階層から現在のレベルへ")</span><span class="sxs-lookup"><span data-stu-id="bb5b2-115">![Avialble Entities and Hierarchies to Current Level](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "Avialble Entities and Hierarchies to Current Level")</span></span>  
  
8.  <span data-ttu-id="bb5b2-116">[**使用可能なレベル: SuppliersInState**から**現在のレベル: SuppliersInState**に**状態**をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-116">Drag **State** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span> <span data-ttu-id="bb5b2-117">画面には、次の図に示すように、**現在のレベル**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-117">The screen should have **Current Levels** as shown in the following picture.</span></span>  
  
     <span data-ttu-id="bb5b2-118">![現在のレベルと、派生階層のプレビュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "現在のレベルと、派生階層のプレビュー")</span><span class="sxs-lookup"><span data-stu-id="bb5b2-118">![Current Levels and Preview of Derived Hierarchy](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "Current Levels and Preview of Derived Hierarchy")</span></span>  
  
9. <span data-ttu-id="bb5b2-119">**プレビュー**ウィンドウで、[ **NY {New ニューヨーク}** ] を展開すると、前の図に示すように、その状態に1つの仕入先が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-119">In the **Preview** window, expand **NY { New York}** and you should see one supplier in that state as shown in the preceding image.</span></span>  
  
10. <span data-ttu-id="bb5b2-120">ページの上部にある**SQL Server 2012 マスターデータサービス**をクリックして**マスターデータマネージャー**のメインページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-120">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
11. <span data-ttu-id="bb5b2-121">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-121">Click **Explorer**.</span></span>  
  
12. <span data-ttu-id="bb5b2-122">**階層**上にマウスポインターを置き、[ **Derived: SuppliersInState**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-122">Hover the mouse over **Hierarchies** and click **Derived:SuppliersInState**.</span></span>  
  
     <span data-ttu-id="bb5b2-123">![階層 - 派生: SuppliersInState メニュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "階層 - 派生: SuppliersInState メニュー")</span><span class="sxs-lookup"><span data-stu-id="bb5b2-123">![Hierarchies - Derived:SuppliersInState Menu](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hierarchies - Derived:SuppliersInState Menu")</span></span>  
  
13. <span data-ttu-id="bb5b2-124">**ツリービュー**の任意の**状態**ノードをクリックすると、その状態にある仕入先が右ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb5b2-124">Click on any **state** node in the **tree view** and you should see the suppliers in that state in the right pane.</span></span>  
  
     <span data-ttu-id="bb5b2-125">![エクスプローラーでの派生階層](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "エクスプローラーでの派生階層")</span><span class="sxs-lookup"><span data-stu-id="bb5b2-125">![Derived Hierarchy in Explorer](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "Derived Hierarchy in Explorer")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="bb5b2-126">次の手順</span><span class="sxs-lookup"><span data-stu-id="bb5b2-126">Next Step</span></span>  
 [<span data-ttu-id="bb5b2-127">レッスン 5: SSIS を使用してクレンジングと照合を自動化する</span><span class="sxs-lookup"><span data-stu-id="bb5b2-127">Lesson 5: Automating the Cleansing and Matching using SSIS</span></span>](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
