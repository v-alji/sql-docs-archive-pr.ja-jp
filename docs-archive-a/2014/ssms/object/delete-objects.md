---
title: '[オブジェクトの削除] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7b20d1eee3e48c5531b6b788e125b943f7606d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630776"
---
# <a name="delete-objects"></a><span data-ttu-id="38aa0-102">[オブジェクトの削除]</span><span class="sxs-lookup"><span data-stu-id="38aa0-102">Delete Objects</span></span>
  <span data-ttu-id="38aa0-103">このダイアログ ボックスを使用すると、データベースまたはデータベース オブジェクトを削除できます。</span><span class="sxs-lookup"><span data-stu-id="38aa0-103">Use this dialog box to delete a database or database object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="38aa0-104">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="38aa0-104">UI element list</span></span>  
 <span data-ttu-id="38aa0-105">**[削除されるオブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="38aa0-105">**Object to be deleted**</span></span>  
 <span data-ttu-id="38aa0-106">削除するオブジェクトの名前、種類、所有者、および状態を、実行中のエラーに関するメッセージと一緒に表示します。</span><span class="sxs-lookup"><span data-stu-id="38aa0-106">Displays the names, types, owners, and status of the objects that are about to be deleted, as well as any messages about errors during execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38aa0-107">データベース上で **[削除]** を実行することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)]の DROP DATABASE を発行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="38aa0-107">Running **Delete** on a database is equivalent to issuing DROP DATABASE in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="38aa0-108">**[依存関係の表示]**</span><span class="sxs-lookup"><span data-stu-id="38aa0-108">**Show Dependencies**</span></span>  
 <span data-ttu-id="38aa0-109">クリックすると、現在選択されているオブジェクトに依存するオブジェクトと、現在のオブジェクトが依存しているオブジェクトの両方のオブジェクト (上位依存関係と下位依存関係) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="38aa0-109">Click to display both the objects that are dependent on the currently selected object and objects that the current object is dependent on (upward and downward dependency).</span></span> <span data-ttu-id="38aa0-110">**[依存関係の表示]** ダイアログ ボックスに表示される情報は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="38aa0-110">The information displayed in the **Show Dependencies** dialog box is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38aa0-111">**[依存関係の表示]** ボタンは、すべての種類のデータベース オブジェクトに対して表示されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="38aa0-111">The **Show Dependencies** button does not appear for all types of database objects.</span></span> <span data-ttu-id="38aa0-112">**[依存関係の表示]** ボタンが表示されていないときに依存関係を表示するには、オブジェクト エクスプローラーでオブジェクトを右クリックし、 **[依存関係の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38aa0-112">To view dependencies when the **Show Dependencies** button is not available, right-click the object in Object Explorer, and then click **View Dependencies**.</span></span>  
  
 <span data-ttu-id="38aa0-113">**[バックアップを削除し、データベースの履歴情報を復元する]**</span><span class="sxs-lookup"><span data-stu-id="38aa0-113">**Delete backup and restore history information for databases**</span></span>  
 <span data-ttu-id="38aa0-114">データベースが削除されるときにだけ表示されます。このチェック ボックスを使用すると、サブジェクト データベースのバックアップおよび復元履歴が **msdb** データベースから削除されます。</span><span class="sxs-lookup"><span data-stu-id="38aa0-114">Only appears when a database is deleted, this check box causes the backup and restore history for the subject database to be deleted from the **msdb** database.</span></span>  
  
 <span data-ttu-id="38aa0-115">**[既存の接続を閉じる]**</span><span class="sxs-lookup"><span data-stu-id="38aa0-115">**Close existing connections**</span></span>  
 <span data-ttu-id="38aa0-116">データベースが削除されるときにだけ表示されます。このチェック ボックスを使用すると、サブジェクト データベースへの接続を終了できます。</span><span class="sxs-lookup"><span data-stu-id="38aa0-116">Only appears when a database is deleted, this check box terminates connections to the subject database.</span></span>  
  
  
