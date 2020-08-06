---
title: テーブルの定義の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53170a78a104bfce4b4e4177015461f2eb9093e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646085"
---
# <a name="view-the-table-definition"></a><span data-ttu-id="491c5-102">テーブルの定義の表示</span><span class="sxs-lookup"><span data-stu-id="491c5-102">View the Table Definition</span></span>
  <span data-ttu-id="491c5-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してテーブルのプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="491c5-103">You can display properties for a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="491c5-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="491c5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="491c5-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="491c5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="491c5-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="491c5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="491c5-107">**テーブルのプロパティを表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="491c5-107">**To display table properties, using:**</span></span>  
  
     [<span data-ttu-id="491c5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="491c5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="491c5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="491c5-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="491c5-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="491c5-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="491c5-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="491c5-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="491c5-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="491c5-112">Permissions</span></span>  
 <span data-ttu-id="491c5-113">ユーザーは、ユーザーが所有しているか権限が与えられているテーブルのプロパティのみを表示できます。</span><span class="sxs-lookup"><span data-stu-id="491c5-113">You can only see properties in a table if you either own the table or have been granted permissions to that table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="491c5-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="491c5-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a><span data-ttu-id="491c5-115">[プロパティ] ウィンドウにテーブルのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="491c5-115">To show table properties in the Properties window</span></span>  
  
1.  <span data-ttu-id="491c5-116">オブジェクト エクスプローラーで、プロパティを表示するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="491c5-116">In Object Explorer, select the table for which you want to show properties.</span></span>  
  
2.  <span data-ttu-id="491c5-117">テーブルを右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491c5-117">Right-click the table and choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="491c5-118">詳細については、「 [Table Properties](table-properties-ssms.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="491c5-118">For more information, see [Table Properties](table-properties-ssms.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="491c5-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="491c5-119">Using Transact-SQL</span></span>  
  
#### <a name="to-show-table-properties"></a><span data-ttu-id="491c5-120">テーブルのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="491c5-120">To show table properties</span></span>  
  
1.  <span data-ttu-id="491c5-121">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="491c5-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="491c5-122">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491c5-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="491c5-123">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491c5-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="491c5-124">次の例では、特定のオブジェクトの `sys.tables` カタログ ビューからすべての列が返されます。</span><span class="sxs-lookup"><span data-stu-id="491c5-124">The example returns all columns from the `sys.tables` catalog view for the specified object.</span></span>  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 <span data-ttu-id="491c5-125">詳細については、「[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="491c5-125">For more information, see [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
