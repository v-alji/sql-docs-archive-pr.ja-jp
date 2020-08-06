---
title: '[データベースの変更を確認] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91d58e812b93f207d592d245d094b0fbeddcce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714933"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a><span data-ttu-id="77394-102">[データベースの変更を確認] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="77394-102">Database Changes Detected Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="77394-103">このダイアログは、データベース ダイアグラムまたは選択したテーブルを保存しようとしたときに、保存によって影響を受けるデータベース オブジェクトの一部がデータベースの最新の内容と異なる場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="77394-103">This dialog appears if you attempt to save a database diagram or selected tables but some of the database objects that will be affected by the save action are out of date with the database.</span></span> <span data-ttu-id="77394-104">このダイアログ ボックスに表示された変更を受け入れると、ダイアグラムに一致するようにデータベースが更新され、他のユーザーが加えた変更が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="77394-104">Accepting the changes shown in this dialog box updates the database to match your diagram and overwrites other users' changes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77394-105">テーブルやデータベース ダイアグラムに加えた変更を元に戻すことはできませんが、テーブルやダイアグラムを保存するまでは、変更はデータベースに保存されません。</span><span class="sxs-lookup"><span data-stu-id="77394-105">Although you cannot undo changes made to a table or database diagram, the changes are not saved to the database until you save the table or diagram.</span></span> <span data-ttu-id="77394-106">**[いいえ]** を選択して、すべての開いているダイアグラムの変更を保存せずに閉じると、まだ保存していない変更を破棄できます。</span><span class="sxs-lookup"><span data-stu-id="77394-106">You can discard any unsaved changes by choosing **No** and closing all open diagrams without saving them.</span></span>  
  
## <a name="options"></a><span data-ttu-id="77394-107">オプション</span><span class="sxs-lookup"><span data-stu-id="77394-107">Options</span></span>  
 <span data-ttu-id="77394-108">**[相違点の検出に関する警告]**</span><span class="sxs-lookup"><span data-stu-id="77394-108">**Warn about difference detection**</span></span>  
 <span data-ttu-id="77394-109">データベース ダイアグラムまたは選択したテーブルを次に保存しようとするときにこのダイアログ ボックスを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="77394-109">Specify whether this dialog box appears the next time you attempt to save a database diagram or selected tables.</span></span> <span data-ttu-id="77394-110">このチェック ボックスをオンにすると、データベースの最新の内容と異なるダイアグラムやテーブルを保存しようとするたびにダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77394-110">Checked means that the dialog box continues to appear each time you save a diagram or table that is out of date with the database.</span></span> <span data-ttu-id="77394-111">オフにすると、ダイアログ ボックスが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="77394-111">Unchecked means that the dialog box does not appear.</span></span> <span data-ttu-id="77394-112">既定では、このチェック ボックスはオンです。</span><span class="sxs-lookup"><span data-stu-id="77394-112">By default, this box is checked.</span></span> <span data-ttu-id="77394-113">このオプションをオフにした場合は、 **[オプション]** ダイアログ ボックスで再びオンにできます。</span><span class="sxs-lookup"><span data-stu-id="77394-113">If you uncheck this option, you can recheck it in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="77394-114">**はい**</span><span class="sxs-lookup"><span data-stu-id="77394-114">**Yes**</span></span>  
 <span data-ttu-id="77394-115">一覧に表示されているすべての変更を適用してデータベースを更新します。</span><span class="sxs-lookup"><span data-stu-id="77394-115">Update the database with all the changes shown in the list.</span></span>  
  
 <span data-ttu-id="77394-116">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="77394-116">**No**</span></span>  
 <span data-ttu-id="77394-117">保存操作を取り消します。</span><span class="sxs-lookup"><span data-stu-id="77394-117">Cancel the save action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77394-118">データベースに一致するようにダイアグラムを最新表示するには、変更を保存せずにダイアグラムを閉じて、サーバー エクスプローラーでダイアグラムを右クリックし、[最新の情報に更新] をクリックして、ダイアグラムを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="77394-118">To refresh your diagram to match the database, close it without saving changes, right-click the diagram in Server Explorer and click Refresh, and then reopen the diagram.</span></span>  
  
 <span data-ttu-id="77394-119">**[テキスト ファイルを保存]**</span><span class="sxs-lookup"><span data-stu-id="77394-119">**Save Text File**</span></span>  
 <span data-ttu-id="77394-120">**[名前を付けて保存]** ダイアログ ボックスが表示され、データベースへの変更の一覧を保存するテキスト ファイルの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="77394-120">Display the **Save As** dialog box, letting you specify a location for a text file containing a list of the database changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77394-121">参照</span><span class="sxs-lookup"><span data-stu-id="77394-121">See Also</span></span>  
 <span data-ttu-id="77394-122">[変更されたデータベースを使用してデータベースダイアグラムを調整する &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="77394-122">[Reconcile a Database Diagram with a Modified Database &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="77394-123">マルチユーザー環境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="77394-123">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](multiuser-environments-visual-database-tools.md)  
  
  
