---
title: クエリとプロジェクト内の接続との関連付け | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], query associations
- projects [SQL Server Management Studio], connections
- projects [SQL Server Management Studio], query connections
- query associations [SQL Server Management Studio]
ms.assetid: c9625ae0-29c1-4179-a709-51b7e2f9e23d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b05715dc6680148a8ae673c73cfc36c96a55c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717186"
---
# <a name="associate-a-query-with-a-connection-in-a-project"></a><span data-ttu-id="e7bb4-102">クエリとプロジェクト内の接続との関連付け</span><span class="sxs-lookup"><span data-stu-id="e7bb4-102">Associate a Query with a Connection in a Project</span></span>
  <span data-ttu-id="e7bb4-103">クエリを接続の指定なしで作成した場合、またはクエリを別のプロジェクトに移動する場合は、そのクエリは現在のプロジェクト内の接続に関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="e7bb4-103">If a query was created without a connection, or if a query is moved from one project to another it will not be associated with a connection in the current project.</span></span>  
  
### <a name="to-associate-a-query-with-a-connection-in-a-project"></a><span data-ttu-id="e7bb4-104">クエリをプロジェクト内の接続に関連付けるには</span><span class="sxs-lookup"><span data-stu-id="e7bb4-104">To associate a query with a connection in a project</span></span>  
  
1.  <span data-ttu-id="e7bb4-105">クエリをクエリ エディターで開いている場合は、クエリ エディターの空白部分を右クリックして **[接続]** をポイントし、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7bb4-105">If the query is open in query editor, right-click a blank area of query editor, point to **Connection**, and then click **Connect**.</span></span> <span data-ttu-id="e7bb4-106">クエリが開いていない場合は、ソリューション エクスプローラーでクエリをダブルクリックし、クエリを接続します。</span><span class="sxs-lookup"><span data-stu-id="e7bb4-106">If the query is not open, double-click the query in Solution Explorer to connect the query.</span></span>  
  
2.  <span data-ttu-id="e7bb4-107">**[データベース エンジンへの接続]** ダイアログ ボックスで、接続情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7bb4-107">In the **Connect to Database Engine** dialog box, provide the connection information.</span></span> <span data-ttu-id="e7bb4-108">接続情報が既存の接続に一致すると、クエリはその接続に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="e7bb4-108">If the connection information matches an existing connection, the query will be associated with that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bb4-109">参照</span><span class="sxs-lookup"><span data-stu-id="e7bb4-109">See Also</span></span>  
 <span data-ttu-id="e7bb4-110">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="e7bb4-110">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="e7bb4-111">[クエリに関連付けられている接続を変更する](change-the-connection-associated-with-a-query.md) </span><span class="sxs-lookup"><span data-stu-id="e7bb4-111">[Change the Connection Associated with a Query](change-the-connection-associated-with-a-query.md) </span></span>  
 [<span data-ttu-id="e7bb4-112">プロジェクト内の接続のプロパティを表示または変更する方法</span><span class="sxs-lookup"><span data-stu-id="e7bb4-112">View or Change the Properties of a Connection in a Project</span></span>](view-or-change-the-properties-of-a-connection-in-a-project.md)  
  
  
