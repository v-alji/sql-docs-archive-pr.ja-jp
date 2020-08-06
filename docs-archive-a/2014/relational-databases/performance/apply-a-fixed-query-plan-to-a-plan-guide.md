---
title: プラン ガイドへの固定クエリ プランの適用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 318955c4d0550e311873d8b4a6f79f72e04ac8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713066"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a><span data-ttu-id="c9d8d-102">プラン ガイドへの固定クエリ プランの適用</span><span class="sxs-lookup"><span data-stu-id="c9d8d-102">Apply a Fixed Query Plan to a Plan Guide</span></span>
  <span data-ttu-id="c9d8d-103">OBJECT 型または SQL 型のプラン ガイドには固定クエリ プランを適用できます。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-103">You can apply a fixed query plan to a plan guide of type OBJECT or SQL.</span></span> <span data-ttu-id="c9d8d-104">特定のクエリに対してオプティマイザーによって選択された実行プランよりもパフォーマンスの高い既存の実行プランがわかっている場合は、固定クエリ プランを適用するプラン ガイドを使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-104">Plan guides that apply a fixed query plan are useful when you know about an existing execution plan that performs better than the one selected by the optimizer for a particular query.</span></span>  
  
 <span data-ttu-id="c9d8d-105">次の例では、単純なアドホック SQL ステートメントのプラン ガイドを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-105">The following example creates a plan guide for a simple ad hoc SQL statement.</span></span> <span data-ttu-id="c9d8d-106">このステートメントの目的のクエリ プランは、クエリの XML プラン表示を `@hints` パラメーターで直接指定することにより、プラン ガイドで提供されます。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-106">The desired query plan for this statement is provided in the plan guide by specifying the XML Showplan for the query directly in the `@hints` parameter.</span></span> <span data-ttu-id="c9d8d-107">最初に SQL ステートメントを実行して、プラン キャッシュ内にプランを生成します。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-107">The example first executes the SQL statement to generate a plan in the plan cache.</span></span> <span data-ttu-id="c9d8d-108">この例では、生成されたプランが目的のプランであり、追加のクエリ チューニングが不要であると想定しています。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-108">For the purposes of this example, it is assumed that the generated plan is the desired plan and no additional query tuning is required.</span></span> <span data-ttu-id="c9d8d-109">クエリの XML プラン表示は、 `sys.dm_exec_query_stats`、 `sys.dm_exec_sql_text`、および `sys.dm_exec_text_query_plan` の各動的管理ビューをクエリすることにより取得され、 `@xml_showplan` 変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-109">The XML Showplan for the query is obtained by querying the `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`, and `sys.dm_exec_text_query_plan` dynamic management views and is assigned to the `@xml_showplan` variable.</span></span> <span data-ttu-id="c9d8d-110">次に `@xml_showplan` 変数が、 `sp_create_plan_guide` パラメーターで `@hints` ステートメントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-110">The `@xml_showplan` variable is then passed to the `sp_create_plan_guide` statement in the `@hints` parameter.</span></span> <span data-ttu-id="c9d8d-111">または、 [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) ストアド プロシージャを使用して、プラン キャッシュ内のクエリ プランからプラン ガイドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9d8d-111">Or, you can create a plan guide from a query plan in the plan cache by using the [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  
