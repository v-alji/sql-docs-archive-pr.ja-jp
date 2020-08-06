---
title: パラメーター化クエリのプラン ガイドの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- parameterized queries, plan guides for
- plan guides [SQL Server], parameterized queries
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 565610826f704274724ea05d821205a5b3391060
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645574"
---
# <a name="create-a-plan-guide-for-parameterized-queries"></a><span data-ttu-id="7b43e-102">パラメーター化クエリのプラン ガイドの作成</span><span class="sxs-lookup"><span data-stu-id="7b43e-102">Create a Plan Guide for Parameterized Queries</span></span>
  <span data-ttu-id="7b43e-103">TEMPLATE プラン ガイドでは、指定した形式にパラメーター化されたスタンドアロン クエリが照合されます。</span><span class="sxs-lookup"><span data-stu-id="7b43e-103">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span>  
  
 <span data-ttu-id="7b43e-104">次の例では、指定されたフォームにパラメーター化されるクエリに適合するプラン ガイドを作成し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対してクエリのパラメーター化を強制的に実行させます。</span><span class="sxs-lookup"><span data-stu-id="7b43e-104">The following example creates a plan guide that matches any query that parameterizes to a specified form, and directs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to force parameterization of the query.</span></span> <span data-ttu-id="7b43e-105">次の 2 つのクエリは構文的には同じですが、定数リテラル値のみが異なります。</span><span class="sxs-lookup"><span data-stu-id="7b43e-105">The following two queries are syntactically equivalent, but differ only in their constant literal values.</span></span>  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 <span data-ttu-id="7b43e-106">パラメーター化形式のクエリに対するプラン ガイドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7b43e-106">Here is the plan guide on the parameterized form of the query:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 <span data-ttu-id="7b43e-107">この例では、 `@stmt` パラメーターの値は、パラメーター化形式のクエリになっています。</span><span class="sxs-lookup"><span data-stu-id="7b43e-107">In the previous example, the value for the `@stmt` parameter is the parameterized form of the query.</span></span> <span data-ttu-id="7b43e-108">この値を取得して sp_create_plan_guide で使用できるようにするには、 [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) システム ストアド プロシージャを使用するのが唯一信頼できる方法です。</span><span class="sxs-lookup"><span data-stu-id="7b43e-108">The only reliable way to obtain this value for use in sp_create_plan_guide is to use the [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) system stored procedure.</span></span> <span data-ttu-id="7b43e-109">次のスクリプトを使用すると、パラメーター化クエリを取得してそのクエリに対してプラン ガイドを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7b43e-109">The following script can be used both to obtain the parameterized query and then create a plan guide on it.</span></span>  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b43e-110">`@stmt` に渡される `sp_get_query_template` パラメーターの定数リテラルの値は、リテラルを置き換えるパラメーターで選択されるデータ型に影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b43e-110">The value of the constant literals in the `@stmt` parameter passed to `sp_get_query_template` might affect the data type that is chosen for the parameter that replaces the literal.</span></span> <span data-ttu-id="7b43e-111">この値は、プラン ガイドの適合にも影響します。</span><span class="sxs-lookup"><span data-stu-id="7b43e-111">This will affect plan guide matching.</span></span> <span data-ttu-id="7b43e-112">場合によっては、異なるパラメーター値範囲に対応する複数のプラン ガイドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b43e-112">You may have to create more than one plan guide to handle different parameter value ranges.</span></span>  
  
 <span data-ttu-id="7b43e-113">TEMPLATE プラン ガイドを SQL プラン ガイドと併用することもできます。</span><span class="sxs-lookup"><span data-stu-id="7b43e-113">You can also use TEMPLATE plan guides together with SQL plan guides.</span></span> <span data-ttu-id="7b43e-114">たとえば、TEMPLATE プラン ガイドを作成することで、特定のクラスのクエリについて確実にパラメーター化を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7b43e-114">For example, you can create a TEMPLATE plan guide to make sure that a class of queries is parameterized.</span></span> <span data-ttu-id="7b43e-115">これにより、そのパラメーター化された形式のクエリに対して SQL プラン ガイドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7b43e-115">You can then create an SQL plan guide on the parameterized form of that query.</span></span>  
  
  
