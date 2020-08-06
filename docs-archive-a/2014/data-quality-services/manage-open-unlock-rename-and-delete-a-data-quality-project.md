---
title: データ品質プロジェクトの管理 (開く、ロック解除、名前の変更、および削除)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 216c95937676954c509890b879abdee8f55b778c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644636"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a><span data-ttu-id="f7e2d-102">データ品質プロジェクトの管理 (開く、ロック解除、名前の変更、および削除)</span><span class="sxs-lookup"><span data-stu-id="f7e2d-102">Manage (Open, Unlock, Rename, and Delete) a Data Quality Project</span></span>
  <span data-ttu-id="f7e2d-103">このトピックでは、データ品質プロジェクトを開く、ロック解除、名前の変更、削除などの、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] を使用したデータ品質プロジェクトの管理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-103">This topic describes how to manage a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] such as open, unlock, rename, and delete a data quality project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f7e2d-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="f7e2d-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="f7e2d-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f7e2d-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f7e2d-106">他のユーザーによって作成された、ロックされているプロジェクトは開くことができません。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-106">You cannot open a locked project that is created by another user.</span></span>  
  
-   <span data-ttu-id="f7e2d-107">他のユーザーによって作成されたデータ品質プロジェクトのロック解除、名前の変更、または削除はできません。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-107">You cannot unlock, rename, or delete a data quality project that is created by another user.</span></span>  
  
-   <span data-ttu-id="f7e2d-108">ロックされたデータ品質プロジェクトを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-108">You cannot delete a locked data quality project.</span></span> <span data-ttu-id="f7e2d-109">削除するには先にロックを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-109">You must first unlock it to delete.</span></span>  
  
-   <span data-ttu-id="f7e2d-110">自分が作成したデータ品質プロジェクトのみロックを解除することができます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-110">You can only unlock a data quality project that is created by you.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f7e2d-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="f7e2d-111">Prerequisites</span></span>  
 <span data-ttu-id="f7e2d-112">管理対象のデータ品質プロジェクトが少なくとも 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-112">You must have at least one data quality project to manage.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f7e2d-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f7e2d-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f7e2d-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="f7e2d-114">Permissions</span></span>  
 <span data-ttu-id="f7e2d-115">データ品質プロジェクトを管理するには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-115">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to manage a data quality project.</span></span>  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> <span data-ttu-id="f7e2d-116">データ品質プロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="f7e2d-116">Open a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="f7e2d-117">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-117">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="f7e2d-118">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-118">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="f7e2d-119">**[プロジェクトを開く]** 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-119">The **Open project** screen appears.</span></span>  
  
     <span data-ttu-id="f7e2d-120">または、 **[最近使用したデータ品質プロジェクト]** 領域の下に表示されるデータ品質プロジェクトをクリックして直接開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-120">Alternately, you can directly open a data quality project listed under **Recent data quality project** area by clicking it.</span></span>  
  
3.  <span data-ttu-id="f7e2d-121">**[プロジェクトを開く]** 画面で、開きたいデータ品質プロジェクトをクリックして選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-121">In the **Open project** screen, click to select the data quality project that you want to open, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="f7e2d-122">最後に閉じられたときと同じアクティビティの状態でデータ品質プロジェクトが開きます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-122">The data quality project opens at the same state of the activity where it was last closed.</span></span> <span data-ttu-id="f7e2d-123">データ品質プロジェクトには次の状態があります。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-123">A data quality project has the following states:</span></span>  
  
    -   <span data-ttu-id="f7e2d-124">**クレンジング**アクティビティでは、データ品質プロジェクトの状態は、**クレンジング-マップ**、**クレンジング-最適化**、クレンジング **-管理と結果の表示**、および**クレンジング-エクスポート**の状態になります。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-124">For the **Cleansing** activity, a data quality project can have the following states: **Cleansing - Map**, **Cleansing - Cleanse**, **Cleansing - Manage and View Results**, and **Cleansing - Export**.</span></span>  
  
    -   <span data-ttu-id="f7e2d-125">**照合**アクティビティでは、データ品質プロジェクトの状態は、"**一致-マップ** **"、"照合-一致"**、"**サバイバーシップ**"、および "**照合/エクスポート**" の各状態になります。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-125">For the **Matching** activity, a data quality project can have the following states: **Matching - Map**, **Matching - Matching**, **Matching - Survivorship**, and **Matching - Export**.</span></span>  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> <span data-ttu-id="f7e2d-126">データ品質プロジェクトのロック解除</span><span class="sxs-lookup"><span data-stu-id="f7e2d-126">Unlock a Data Quality Project</span></span>  
 <span data-ttu-id="f7e2d-127">データ品質プロジェクトを作成すると、プロジェクトは他のユーザーによる使用や変更を防ぐためにロック状態になります。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-127">When you create a data quality project, it is in a locked state to prevent usage or modification by other users.</span></span> <span data-ttu-id="f7e2d-128">他のユーザーがデータ品質プロジェクトを操作できるようにするには、作業を完了した後にデータ品質プロジェクトのロックを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-128">You must unlock the data quality project after you have completed your work if you want other users to work on your data quality project.</span></span> <span data-ttu-id="f7e2d-129">ロックされているプロジェクトには、ロック アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-129">A lock symbol is displayed for projects that are locked.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="f7e2d-130">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-130">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="f7e2d-131">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-131">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="f7e2d-132">**[プロジェクトを開く]** 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-132">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="f7e2d-133">**[プロジェクトを開く]** 画面で、自分が作成したロックされているデータ品質プロジェクトを右クリックし、ショートカット メニューの **[ロック解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-133">In the **Open project** screen, right-click a locked data quality project that is created by you, and then click **Unlock** in the shortcut menu.</span></span> <span data-ttu-id="f7e2d-134">緑のチェック マークがプロジェクトに表示され、ロックされていないことが示されます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-134">A green check mark is displayed for the project indicating that it is unlocked.</span></span>  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a> <span data-ttu-id="f7e2d-135">データ品質プロジェクトの名前の変更</span><span class="sxs-lookup"><span data-stu-id="f7e2d-135">Rename a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="f7e2d-136">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-136">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="f7e2d-137">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-137">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="f7e2d-138">**[プロジェクトを開く]** 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-138">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="f7e2d-139">**[プロジェクトを開く]** 画面で、自分が作成したデータ品質プロジェクトを右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-139">In the **Open project** screen, right-click a data quality project that is created by you, and then click **Rename** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="f7e2d-140">**[名前]** 列のデータ品質プロジェクト名が編集可能になります。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-140">The data quality project name becomes editable in the **Name** column.</span></span> <span data-ttu-id="f7e2d-141">新しい名前を入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-141">Type a new name, and then press Enter.</span></span>  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a> <span data-ttu-id="f7e2d-142">データ品質プロジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="f7e2d-142">Delete a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="f7e2d-143">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-143">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="f7e2d-144">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-144">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="f7e2d-145">**[プロジェクトを開く]** 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-145">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="f7e2d-146">**[プロジェクトを開く]** 画面で、自分が作成したロックされていないデータ品質プロジェクトを右クリックし、ショートカット メニューの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-146">In the **Open project** screen, right-click an unlocked data quality project that is created by you, and then click **Delete** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="f7e2d-147">確認メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-147">A confirmation message appears.</span></span> <span data-ttu-id="f7e2d-148">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e2d-148">Click **Yes**.</span></span>  
  
  
