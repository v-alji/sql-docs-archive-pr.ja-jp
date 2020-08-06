---
title: テーブルのスクリプト作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 247c839d83768756c57297d47f952401a1c8fd46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634757"
---
# <a name="script-a-table"></a><span data-ttu-id="8769c-102">テーブルのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="8769c-102">Script a Table</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8769c-103">では、テーブルを選択、挿入、更新、削除するスクリプト、およびストアド プロシージャを作成、変更、削除、または実行するスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8769c-103">can create scripts to select, insert, update, and delete tables, and to create, alter, drop, or execute stored procedures.</span></span>  
  
 <span data-ttu-id="8769c-104">プロシージャを削除した後でプロシージャを作成したり、テーブルを作成した後でテーブルを変更するなど、1 つのスクリプトで複数のオプションを実行させたい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8769c-104">Sometimes you want a script with multiple options, such as drop a procedure and then create a procedure, or create a table then alter a table.</span></span> <span data-ttu-id="8769c-105">複合的なスクリプトを作成するには、1 番目のスクリプトをクエリ エディター ウィンドウに保存し、2 番目のスクリプトをクリップボードに保存します。次に、クエリ エディター ウィンドウで、1 番目のスクリプトの後ろに 2 番目のスクリプトを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8769c-105">To create combined scripts, save the first script to a Query Editor window and the second to the clipboard so you can paste it into the window after the first script.</span></span>  
  
## <a name="creating-an-update-script"></a><span data-ttu-id="8769c-106">更新スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="8769c-106">Creating an Update Script</span></span>  
  
#### <a name="to-create-the-insert-script-for-a-table"></a><span data-ttu-id="8769c-107">テーブルの挿入スクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="8769c-107">To create the insert script for a table</span></span>  
  
1.  <span data-ttu-id="8769c-108">オブジェクト エクスプローラーでサーバーを展開し、 **[データベース]**、[ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]]、 **[テーブル]** の順に展開します。次に、 **[HumanResources.Employee]** を右クリックし、 **[テーブルをスクリプト化]** をポイントします。</span><span class="sxs-lookup"><span data-stu-id="8769c-108">In Object Explorer, expand your server, expand **Databases**, expand [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], expand **Tables**, right-click **HumanResources.Employee**, and then point to **Script Table As**.</span></span>  
  
2.  <span data-ttu-id="8769c-109">ショートカット メニューには、 **[新規作成]**、 **[削除]**、 **[削除および作成]**、 **[検索]**、 **[データ登録]**、 **[データ更新]**、 **[データ削除]** という 7 つの使用可能なスクリプト オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="8769c-109">The shortcut menu has seven available scripting options: **CREATE To**, **DROP To**, **DROP and CREATE To**, **SELECT To**, **INSERT To**, **UPDATE To**, and **DELETE To**.</span></span> <span data-ttu-id="8769c-110">**[データ更新]** をポイントし、 **[新しいクエリ エディター ウィンドウ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8769c-110">Point to **UPDATE To**, and then click **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="8769c-111">新しいクエリ エディター ウィンドウが開き、接続が確立され、更新ステートメント全体が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8769c-111">A new Query Editor window opens, makes a connection, and presents the entire update statement.</span></span>  
  
     <span data-ttu-id="8769c-112">この実習では、テーブルやストアド プロシージャを作成する以外にスクリプト機能でどのようなことを実行できるのかを学習します。</span><span class="sxs-lookup"><span data-stu-id="8769c-112">This exercise demonstrates how the scripting feature can do more than just script the creation of a table or stored procedure.</span></span> <span data-ttu-id="8769c-113">この新機能により、データ操作スクリプトをプロジェクトにすばやく追加し、スクリプトによるストアド プロシージャの実行を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8769c-113">This new feature can help you quickly add data manipulation scripts to your project and easily script execution of stored procedures.</span></span> <span data-ttu-id="8769c-114">多数のフィールドを持つテーブルやプロシージャでは、時間を大幅に節約できます。</span><span class="sxs-lookup"><span data-stu-id="8769c-114">This can be a big timesaver for tables and procedures with many fields.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8769c-115">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="8769c-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8769c-116">まとめ : Transact-SQL の記述</span><span class="sxs-lookup"><span data-stu-id="8769c-116">Summary: Writing Transact-SQL</span></span>](../../tutorials/summary-writing-transact-sql.md)  
  
  
