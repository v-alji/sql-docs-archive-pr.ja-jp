---
title: 変更されたデータベースを使用したデータベースダイアグラムの調整 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e5e5127ab613a6f791919a98899e40caa2ddac20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713657"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a><span data-ttu-id="a3188-102">データベース ダイアグラムへのデータベースの変更の反映 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a3188-102">Reconcile a Database Diagram with a Modified Database (Visual Database Tools)</span></span>
  <span data-ttu-id="a3188-103">データベース ダイアグラムは、ダイアグラムと一致するようにデータベースを更新する準備ができた段階で保存します。</span><span class="sxs-lookup"><span data-stu-id="a3188-103">You save your database diagram when you are ready to update the database to match your diagram.</span></span> <span data-ttu-id="a3188-104">ただし、ダイアグラムを開いた後で別のユーザーがデータベースを更新した場合は、変更内容によって自分のダイアグラムが影響を受けることがあります。また、別のユーザーがデータベースを開いた後で自分がデータベースを更新した場合は、相手のダイアグラムが影響を受けることもあります。</span><span class="sxs-lookup"><span data-stu-id="a3188-104">However, if other users have updated the database since you opened your diagram, their changes might affect your diagram and vice versa.</span></span>  
  
 <span data-ttu-id="a3188-105">ダイアグラムを保存すると、他のユーザーの変更が上書きされ、データベースにダイアグラムの内容が反映されます。そのため、データベースはダイアグラムと一致します。</span><span class="sxs-lookup"><span data-stu-id="a3188-105">Saving your diagram will reconcile the database with your diagram by overwriting other users' changes so that the database will match your diagram.</span></span>  
  
### <a name="to-update-a-database-to-match-your-diagram"></a><span data-ttu-id="a3188-106">ダイアグラムに一致するようにデータベースを更新するには</span><span class="sxs-lookup"><span data-stu-id="a3188-106">To update a database to match your diagram</span></span>  
  
1.  <span data-ttu-id="a3188-107">データベース ダイアグラムを保存します。</span><span class="sxs-lookup"><span data-stu-id="a3188-107">Save your database diagram.</span></span>  
  
     <span data-ttu-id="a3188-108">ダイアグラムを初めて保存する場合は、 **[新しいデータベース ダイアグラムの保存]** ダイアログ ボックスにダイアグラム名を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3188-108">If you have not previously saved your diagram, type a name for the diagram in the **Save New Database Diagram** dialog box and choose **OK**.</span></span>  
  
2.  <span data-ttu-id="a3188-109">ダイアグラムを保存するときに影響を受けるテーブルが **[上書き保存]** ダイアログ ボックスに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3188-109">The **Save** dialog box lists the tables that will be affected when you save your diagram.</span></span> <span data-ttu-id="a3188-110">**[はい]** をクリックして次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="a3188-110">Choose **Yes** to continue.</span></span>  
  
3.  <span data-ttu-id="a3188-111">他のユーザーによって変更されたオブジェクトのうち、ダイアグラムの内容に合うように再度変更されるオブジェクトが、 **[データベースの変更を確認]** ダイアログ ボックスに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3188-111">The **Database Changes Detected** dialog box lists the objects that were modified and will be changed to match your diagram.</span></span> <span data-ttu-id="a3188-112">**[はい]** をクリックしてダイアグラムを保存し、変更一覧を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="a3188-112">Choose **Yes** to save the diagram and accept the list of changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3188-113">データベースで削除されたテーブルや列がダイアグラムに含まれている場合は、ダイアグラムを保存すると、テーブルや列の定義だけがデータベースに再度作成されます。</span><span class="sxs-lookup"><span data-stu-id="a3188-113">If your diagram contains tables and columns that were deleted in the database, only their definitions are recreated in the database when you save your diagram.</span></span> <span data-ttu-id="a3188-114">削除前にオブジェクトに存在していたデータは復元されません。</span><span class="sxs-lookup"><span data-stu-id="a3188-114">This process does not restore any data that existed in these objects before their deletion.</span></span>  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a><span data-ttu-id="a3188-115">変更されたデータベースに一致するようにダイアグラムを更新するには</span><span class="sxs-lookup"><span data-stu-id="a3188-115">To update your diagram to match a modified database</span></span>  
  
1.  <span data-ttu-id="a3188-116">変更を保存せずにダイアグラムを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a3188-116">Close your diagram without saving changes.</span></span>  
  
2.  <span data-ttu-id="a3188-117">オブジェクト エクスプローラーでダイアグラムを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="a3188-117">Right-click the diagram in Object Explorer.</span></span>  
  
3.  <span data-ttu-id="a3188-118">ショートカット メニューの **[最新の情報に更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3188-118">From the shortcut menu click **Refresh**.</span></span>  
  
4.  <span data-ttu-id="a3188-119">ダイアグラムを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="a3188-119">Reopen the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3188-120">参照</span><span class="sxs-lookup"><span data-stu-id="a3188-120">See Also</span></span>  
 [<span data-ttu-id="a3188-121">データベース ダイアグラムの使用 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a3188-121">Work with Database Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
