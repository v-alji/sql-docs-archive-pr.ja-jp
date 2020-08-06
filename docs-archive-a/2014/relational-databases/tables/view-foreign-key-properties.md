---
title: 外部キーのプロパティの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5860a0cf26b983d75bab86862ee1e5fdd7737712
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632294"
---
# <a name="view-foreign-key-properties"></a><span data-ttu-id="6182a-102">外部キーのプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="6182a-102">View Foreign Key Properties</span></span>
  <span data-ttu-id="6182a-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のリレーションシップの外部キー属性を表示できます。</span><span class="sxs-lookup"><span data-stu-id="6182a-103">You can view the foreign key attributes of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6182a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6182a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6182a-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6182a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6182a-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6182a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6182a-107">**以下を使用して特定のテーブルの外部キーの属性を表示するには:**</span><span class="sxs-lookup"><span data-stu-id="6182a-107">**To view the foreign key attributes of a specific table, using:**</span></span>  
  
     [<span data-ttu-id="6182a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6182a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6182a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6182a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6182a-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="6182a-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6182a-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6182a-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6182a-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="6182a-112">Permissions</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="6182a-113">詳細については、「 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6182a-113">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6182a-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6182a-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="6182a-115">特定のテーブルに存在するリレーションシップの外部キーの属性を表示するには</span><span class="sxs-lookup"><span data-stu-id="6182a-115">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="6182a-116">表示する外部キーを含むテーブルのテーブル デザイナーを開き、テーブル デザイナー内を右クリックして、ショートカット メニューの **[リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6182a-116">Open the Table Designer for the table containing the foreign key you want to view, right-click in the Table Designer, and choose **Relationships** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="6182a-117">**[外部キーのリレーションシップ]** ダイアログ ボックスで、表示するプロパティを持つリレーションシップを選択します。</span><span class="sxs-lookup"><span data-stu-id="6182a-117">In the **Foreign Key Relationships** dialog box, select the relationship with properties you want to view.</span></span>  
  
 <span data-ttu-id="6182a-118">外部キー列が主キーに関連付けられている場合、 **テーブル デザイナー** では、主キー列が、行セレクターの主キーの記号によって示されます。</span><span class="sxs-lookup"><span data-stu-id="6182a-118">If the foreign key columns are related to a primary key, the primary key columns are identified in **Table Designer** by a primary key symbol in the row selector.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6182a-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6182a-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="6182a-120">特定のテーブルに存在するリレーションシップの外部キーの属性を表示するには</span><span class="sxs-lookup"><span data-stu-id="6182a-120">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="6182a-121">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6182a-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6182a-122">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6182a-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6182a-123">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6182a-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6182a-124">この例では、サンプル データベース内の `HumanResources.Employee` テーブルを対象に、すべての外部キーとそのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="6182a-124">The example returns all foreign keys and their properties for the table `HumanResources.Employee` in the sample database.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 <span data-ttu-id="6182a-125">詳細については、「[sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql)」および「[sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6182a-125">For more information, see [sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) and [sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
