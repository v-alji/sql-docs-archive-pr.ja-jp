---
title: テーブル内の列の順序の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d162f9dc793ceb9ea423d94922f7358f1729712e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640844"
---
# <a name="change-column-order-in-a-table"></a><span data-ttu-id="7beef-102">テーブル内の列の順序の変更</span><span class="sxs-lookup"><span data-stu-id="7beef-102">Change Column Order in a Table</span></span>
  <span data-ttu-id="7beef-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、テーブル デザイナーで列の順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="7beef-103">You can change the order of columns in Table Designer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7beef-104">テーブルの列の順序を変更すると、特定の列の順序に依存するコードやアプリケーションに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7beef-104">Changing the column order of a table may affect code and applications that depend on the specific order of columns.</span></span> <span data-ttu-id="7beef-105">これには、クエリ、ビュー、ストアド プロシージャ、ユーザー定義関数、およびクライアント アプリケーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7beef-105">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="7beef-106">列の順序に変更を加える場合は、十分注意して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7beef-106">Carefully consider any changes you want to make to column order before making it.</span></span> <span data-ttu-id="7beef-107">列が返される順序をアプリケーションおよびクエリ レベルで指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7beef-107">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="7beef-108">テーブルで定義されている順序に基づいて、すべての列が予想される順序で返されるようにするために、SELECT \* の使用に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="7beef-108">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="7beef-109">クエリまたはアプリケーションでは必ず、表示される順序で列の名前を指定してください。</span><span class="sxs-lookup"><span data-stu-id="7beef-109">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
 <span data-ttu-id="7beef-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="7beef-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7beef-111">**列の順序を変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="7beef-111">**To change the column order, using:**</span></span>  
  
     [<span data-ttu-id="7beef-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7beef-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7beef-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7beef-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7beef-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7beef-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-column-order"></a><span data-ttu-id="7beef-115">列の順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="7beef-115">To change the column order</span></span>  
  
1.  <span data-ttu-id="7beef-116">**オブジェクト エクスプローラー**で、並べ替える列が含まれているテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-116">In **Object Explorer**, right-click the table with columns you want to reorder and click **Design**.</span></span>  
  
2.  <span data-ttu-id="7beef-117">順序を変更する列の名前の左側にあるボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="7beef-117">Select the box to the left of the column name that you want to reorder.</span></span>  
  
3.  <span data-ttu-id="7beef-118">その列をテーブル内の別の場所にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7beef-118">Drag the column to another location within the table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7beef-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7beef-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="7beef-120">**列の順序を変更するには**</span><span class="sxs-lookup"><span data-stu-id="7beef-120">**To change the column order**</span></span>  
  
 <span data-ttu-id="7beef-121">Transact-SQL ステートメントを使用して、このタスクを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="7beef-121">This task cannot be performed using Transact-SQL statements.</span></span>  
  
###  <a name="TsqlExample"></a>  
