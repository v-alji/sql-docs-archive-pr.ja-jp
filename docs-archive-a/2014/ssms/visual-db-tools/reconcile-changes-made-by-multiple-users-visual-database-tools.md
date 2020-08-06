---
title: 複数のユーザーによる変更の調整 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table modifications [SQL Server], multiple users
- reconciling changes made by multiple users
- modifications made by multiple users
ms.assetid: fc7ed4f2-ad3d-47fc-a3ef-51e5bb069ef0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 337d505fce474a33301c18313fe6137f6bc0ec1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713653"
---
# <a name="reconcile-changes-made-by-multiple-users-visual-database-tools"></a><span data-ttu-id="fbb5c-102">複数のユーザーによる変更の調整 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fbb5c-102">Reconcile Changes Made by Multiple Users (Visual Database Tools)</span></span>
  <span data-ttu-id="fbb5c-103">マルチユーザー環境では、同一のオブジェクトに複数のユーザーが同時に変更を加える場合があります。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-103">In a multiuser environment, changes can be made on the same object by multiple users at once.</span></span> <span data-ttu-id="fbb5c-104">この現象は、テーブル デザイナーまたはデータベース ダイアグラム デザイナーでオブジェクトの構造を操作しているときに発生する可能性があります。また、クエリおよびビュー デザイナーの結果ペインに返された結果の値に、他のユーザーが変更を加えている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-104">This can happen when you're working on the structure of the object in the Table or Database Diagram designers or it can happen to values in the results returned in the Query and View designer's Results pane.</span></span> <span data-ttu-id="fbb5c-105">こうした現象により、解決を必要とする競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-105">This can cause conflicts that you'll want to resolve.</span></span>  
  
## <a name="conflicts-in-the-table-or-database-diagram-designers"></a><span data-ttu-id="fbb5c-106">テーブル デザイナーまたはデータベース ダイアグラム デザイナーでの競合</span><span class="sxs-lookup"><span data-stu-id="fbb5c-106">Conflicts in the Table or Database Diagram Designers</span></span>  
 <span data-ttu-id="fbb5c-107">たとえば、テーブル デザイナーでテーブルを操作しているときに、他のユーザーが同じテーブルまたは関連するテーブルを削除したり、名前を変更したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-107">For example, another user might delete or rename a table while you are working with the same or a related table in Table Designer.</span></span> <span data-ttu-id="fbb5c-108">テーブルを保存しようとすると、 [[データベースの変更を確認] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md) によって、テーブルを前回開いた後でデータベースが更新されたことが通知されます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-108">When you attempt to save your table, the [Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) notifies you that the database has been updated since you opened the table.</span></span>  
  
 <span data-ttu-id="fbb5c-109">このダイアログ ボックスには、テーブルを保存する結果として影響を受けるデータベース オブジェクトの一覧も表示されます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-109">This dialog box also displays a list of database objects that will be affected as a result of saving your table.</span></span> <span data-ttu-id="fbb5c-110">この時点で、次のいずれかの処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-110">At this point, you can take one of these actions:</span></span>  
  
-   <span data-ttu-id="fbb5c-111">**[はい]** をクリックして、一覧内のすべての変更内容をデータベースに反映させます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-111">Choose **Yes** to save your table and update the database with all the changes in the list.</span></span>  
  
     <span data-ttu-id="fbb5c-112">このアクションを実行すると、同じデータベース オブジェクトを共有しているテーブルが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-112">This action could affect tables that share the same database objects.</span></span> <span data-ttu-id="fbb5c-113">たとえば、 `au`テーブルの`id` _ `titleauthors` 列を編集しているときに、他のユーザーが、 `authors` 列によって `titleauthors` テーブルと関連付けられている `au`\_`id` テーブルを操作しているとします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-113">For example, suppose you edit the `au`_`id` column in the `titleauthors` table while another user is working on the `authors` table which is related to the `titleauthors` table by the `au`\_`id` column.</span></span> <span data-ttu-id="fbb5c-114">このテーブルを保存すると、他のユーザーのテーブルが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-114">Saving your table will affect the other user's table.</span></span> <span data-ttu-id="fbb5c-115">同様に、あるユーザーが `qty` テーブルの `sales` 列に CHECK 制約を定義したとします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-115">Similarly, suppose that another user defined a check constraint for the `qty` column in the `sales` table.</span></span> <span data-ttu-id="fbb5c-116">別のユーザーが `qty` 列を削除して `sales` テーブルを保存すると、最初のユーザーの CHECK 制約が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-116">If you delete the `qty` column and save the `sales` table, the other user's check constraint will be affected.</span></span>  
  
-   <span data-ttu-id="fbb5c-117">保存を取り消すには、 **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-117">Choose **No** to cancel the save action.</span></span>  
  
     <span data-ttu-id="fbb5c-118">その後、保存せずにテーブルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-118">You can then close the table without saving it.</span></span> <span data-ttu-id="fbb5c-119">テーブルを再度開くと、そのテーブルにはデータベースの現在の内容が反映されています。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-119">When you reopen the table it will match what is in the database.</span></span>  
  
-   <span data-ttu-id="fbb5c-120">変更内容の一覧を保存するには、 **[テキスト ファイルを保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-120">Choose **Save Text File** to save a list of the changes.</span></span>  
  
     <span data-ttu-id="fbb5c-121">**[データベースの変更を確認]** ダイアログ ボックスに表示されているデータベースの変更内容の一覧をテキスト ファイルに保存すると、他のユーザーによる変更の原因を調査できます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-121">You can save the list of database changes shown in the **Database Changes Detected** dialog box to a text file so that you can investigate the cause of other users' changes.</span></span> <span data-ttu-id="fbb5c-122">たとえば、削除することにしたテーブルを他のユーザーが編集していた場合、データベースを更新する前にテーブルを削除する必要があるかどうかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-122">For example, if another user edited a table that you marked for deletion, you may want to research whether the table should be deleted before updating the database.</span></span>  
  
## <a name="conflicts-in-the-query-and-view-designer"></a><span data-ttu-id="fbb5c-123">クエリおよびビュー デザイナーでの競合</span><span class="sxs-lookup"><span data-stu-id="fbb5c-123">Conflicts in the Query and View Designer</span></span>  
 <span data-ttu-id="fbb5c-124">クエリを実行するか、ビューの結果を返すと、 [結果ペイン](results-pane-visual-database-tools.md)にデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-124">If you run a query or return the results of a view, the data is shown in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="fbb5c-125">複数のユーザーが同じデータセットを同時に操作すると、競合が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-125">Multiple users can work on the same set of data at the same time, which can cause conflicts.</span></span>  
  
 <span data-ttu-id="fbb5c-126">たとえば、他のユーザーと同時に `titleauthors` テーブルの全データを表示するクエリを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-126">For example, lets say you and a colleague each run a query to show all the data in the `titleauthors` table.</span></span> <span data-ttu-id="fbb5c-127">他のユーザーが、最初に返されるレコードの名前を Barb から Barbara に変更するとします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-127">Your colleague changes the first name in the first record returned from Barb to Barbara.</span></span> <span data-ttu-id="fbb5c-128">この時点で、データベースの該当するフィールドの値は Barbara ですが、こちら側に表示されている結果セットは Barb のままです。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-128">At this point the database has Barbara in that field, while your result set still shows Barb.</span></span> <span data-ttu-id="fbb5c-129">ここで、Barbara と入力して、その行から移動するとします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-129">Now you type in Barbara and click off of the row.</span></span> <span data-ttu-id="fbb5c-130">すると、競合の解決方法をたずねるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-130">You will receive a message asking you how you want to resolve the conflict.</span></span>  
  
-   <span data-ttu-id="fbb5c-131">データベースに変更内容を反映させるには、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-131">Click **Yes** to update the database with your changes.</span></span>  
  
     <span data-ttu-id="fbb5c-132">他のユーザーの変更をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-132">This will override your colleague's changes.</span></span>  
  
-   <span data-ttu-id="fbb5c-133">データベースの現在の内容に結果セットを更新するには、 **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-133">Click **No** to have your result set updated to what's currently in the database.</span></span>  
  
     <span data-ttu-id="fbb5c-134">こちら側の変更が他のユーザーの変更によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-134">This will override your changes with those of your colleague's.</span></span>  
  
-   <span data-ttu-id="fbb5c-135">競合を解決せずに編集を続行するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-135">Click **Cancel** to continue to edit without resolving the conflict.</span></span>  
  
     <span data-ttu-id="fbb5c-136">この場合、変更を加えてもデータベースにコミットできなくなります。</span><span class="sxs-lookup"><span data-stu-id="fbb5c-136">In this case you will not be able to commit your changes to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb5c-137">参照</span><span class="sxs-lookup"><span data-stu-id="fbb5c-137">See Also</span></span>  
 <span data-ttu-id="fbb5c-138">[[データベースの変更を確認] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="fbb5c-138">[Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md)</span></span>  
  
  
