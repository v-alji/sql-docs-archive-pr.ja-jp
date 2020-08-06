---
title: プラン ガイドを使用したクエリのパラメーター化動作の指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- PARAMETERIZATION FORCED option
- PARAMETERIZATION option
- PARAMETERIZATION SIMPLE option
- parameterization [SQL Server]
- overriding parameterization behavior
- plan guides [SQL Server], parameterization
- parameterized queries [SQL Server]
ms.assetid: f0f738ff-2819-4675-a8c8-1eb6c210a7e6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f595b9f0e0a6d7bceffc5cb283c60b6f40e025b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645566"
---
# <a name="specify-query-parameterization-behavior-by-using-plan-guides"></a><span data-ttu-id="523d4-102">プラン ガイドを使用したクエリのパラメーター化動作の指定</span><span class="sxs-lookup"><span data-stu-id="523d4-102">Specify Query Parameterization Behavior by Using Plan Guides</span></span>
  <span data-ttu-id="523d4-103">PARAMETERIZATION データベース オプションが SIMPLE に設定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーはクエリのパラメーター化を選択することがあります。</span><span class="sxs-lookup"><span data-stu-id="523d4-103">When the PARAMETERIZATION database option is set to SIMPLE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query optimizer may choose to parameterize the queries.</span></span> <span data-ttu-id="523d4-104">これは、クエリに含まれるリテラル値がすべてパラメーターに置き換えられることを意味します。</span><span class="sxs-lookup"><span data-stu-id="523d4-104">This means that any literal values that are contained in a query are substituted with parameters.</span></span> <span data-ttu-id="523d4-105">この処理を簡易パラメーター化と呼びます。</span><span class="sxs-lookup"><span data-stu-id="523d4-105">This process is referred to as simple parameterization.</span></span> <span data-ttu-id="523d4-106">簡易パラメーター化が有効であれば、クエリのパラメーター化を行う場合と行わない場合を制御することはできません。</span><span class="sxs-lookup"><span data-stu-id="523d4-106">When SIMPLE parameterization is in effect, you cannot control which queries are parameterized and which queries are not.</span></span> <span data-ttu-id="523d4-107">ただし、PARAMETERIZATION データベース オプションを FORCED に設定することにより、データベース内のすべてのクエリをパラメーター化するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="523d4-107">However, you can specify that all queries in a database be parameterized by setting the PARAMETERIZATION database option to FORCED.</span></span> <span data-ttu-id="523d4-108">この処理を強制パラメーター化と呼びます。</span><span class="sxs-lookup"><span data-stu-id="523d4-108">This process is referred to as forced parameterization.</span></span>  
  
 <span data-ttu-id="523d4-109">次のような方法でプラン ガイドを使用すると、データベースのパラメーター化の動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="523d4-109">You can override the parameterization behavior of a database by using plan guides in the following ways:</span></span>  
  
-   <span data-ttu-id="523d4-110">PARAMETERIZATION データベース オプションが SIMPLE に設定されている場合、ある種のクエリについては強制パラメーター化を行うように指定できます。</span><span class="sxs-lookup"><span data-stu-id="523d4-110">When the PARAMETERIZATION database option is set to SIMPLE, you can specify that forced parameterization is attempted on a certain class of queries.</span></span> <span data-ttu-id="523d4-111">これには、パラメーター化された形式のクエリの TEMPLATE プラン ガイドを作成し、 [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) ストアド プロシージャに PARAMETERIZATION FORCED クエリ ヒントを指定します。</span><span class="sxs-lookup"><span data-stu-id="523d4-111">You do this by creating a TEMPLATE plan guide on the parameterized form of the query, and specifying the PARAMETERIZATION FORCED query hint in the [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) stored procedure.</span></span> <span data-ttu-id="523d4-112">このようなプラン ガイドは、すべてのクエリではなく、ある種のクエリにのみパラメーター化を強制する方法と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="523d4-112">You can consider this kind of plan guide as a way to enable forced parameterization only on a certain class of queries, instead of all queries.</span></span>  
  
-   <span data-ttu-id="523d4-113">PARAMETERIZATION データベース オプションが FORCED に設定されている場合、ある種のクエリについては、強制パラメーター化ではなく簡易パラメーター化だけを行うように指定できます。</span><span class="sxs-lookup"><span data-stu-id="523d4-113">When the PARAMETERIZATION database option is set to FORCED, you can specify that for a certain class of queries, only simple parameterization is attempted, not forced parameterization.</span></span> <span data-ttu-id="523d4-114">これには、強制パラメーター化された形式のクエリの TEMPLATE プラン ガイドを作成し、 **sp_create_plan_guide**に PARAMETERIZATION SIMPLE クエリ ヒントを指定します。</span><span class="sxs-lookup"><span data-stu-id="523d4-114">You do this by creating a TEMPLATE plan guide on the force-parameterized form of the query, and specifying the PARAMETERIZATION SIMPLE query hint in **sp_create_plan_guide**.</span></span>  
  
 <span data-ttu-id="523d4-115">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを対象とした次のクエリについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="523d4-115">Consider the following query on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
FROM Production.ProductModel AS pm   
    INNER JOIN Production.ProductInventory AS pi   
        ON pm.ProductModelID = pi.ProductID   
WHERE pi.ProductID = 101   
GROUP BY pi.ProductID, pi.Quantity HAVING SUM(pi.Quantity) > 50;  
```  
  
 <span data-ttu-id="523d4-116">ここでは、データベース管理者が、データベースのすべてのクエリにパラメーター化を強制しないことに決定しました。</span><span class="sxs-lookup"><span data-stu-id="523d4-116">As a database administrator, you have determined that you do not want to enable forced parameterization on all queries in the database.</span></span> <span data-ttu-id="523d4-117">ただし、前のクエリと定数リテラル値だけが異なり、構文は同じクエリすべてにコンパイル コストが発生するのは避けたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="523d4-117">However, you do want to avoid compilation costs on all queries that are syntactically equivalent to the previous query, but differ only in their constant literal values.</span></span> <span data-ttu-id="523d4-118">つまり、クエリをパラメーター化し、この種のクエリのクエリ プランを再利用できるように考えています。</span><span class="sxs-lookup"><span data-stu-id="523d4-118">In other words, you want the query to be parameterized so that a query plan for this kind of query is reused.</span></span> <span data-ttu-id="523d4-119">このような場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="523d4-119">In this case, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="523d4-120">パラメーター化された形式のクエリを取得します。</span><span class="sxs-lookup"><span data-stu-id="523d4-120">Retrieve the parameterized form of the query.</span></span> <span data-ttu-id="523d4-121">**sp_create_plan_guide** で使用するためにこの値を安全に取得する唯一の方法は、 [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) システム ストアド プロシージャを使う方法です。</span><span class="sxs-lookup"><span data-stu-id="523d4-121">The only safe way to obtain this value for use in **sp_create_plan_guide** is by using the [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) system stored procedure.</span></span>  
  
2.  <span data-ttu-id="523d4-122">パラメーター化された形式のクエリのプラン ガイドを作成し、PARAMETERIZATION FORCED クエリ ヒントを指定します。</span><span class="sxs-lookup"><span data-stu-id="523d4-122">Create the plan guide on the parameterized form of the query, specifying the PARAMETERIZATION FORCED query hint.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="523d4-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はクエリのパラメーター化処理の一環として、リテラルの値とサイズに従って、リテラル値を置き換えるパラメーターにデータ型を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="523d4-123">As part of parameterizing a query, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns a data type to the parameters that replace the literal values, depending on the value and size of the literal.</span></span> <span data-ttu-id="523d4-124">**@stmt** **Sp_get_query_template**の出力パラメーターに渡される定数リテラルの値に対しても同じ処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="523d4-124">The same process occurs to the value of the constant literals passed to the **@stmt** output parameter of **sp_get_query_template**.</span></span> <span data-ttu-id="523d4-125">Sp_create_plan_guide の引数で指定されたデータ型は、 **@params** によってパラメーター化されるクエリと一致する必要があるため**sp_create_plan_guide** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、クエリに使用できるパラメーター値の完全な範囲をカバーするために、複数のプランガイドを作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="523d4-125">Because the data type specified in the **@params** argument of **sp_create_plan_guide** must match that of the query as it is parameterized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you may have to create more than one plan guide to cover the complete range of possible parameter values for the query.</span></span>  
  
 <span data-ttu-id="523d4-126">次のスクリプトを使用すると、パラメーター化クエリの取得と、このクエリのプラン ガイドの作成の両方の処理を行えます。</span><span class="sxs-lookup"><span data-stu-id="523d4-126">The following script can be used both to obtain the parameterized query and then create a plan guide on it:</span></span>  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total   
      FROM Production.ProductModel AS pm   
      INNER JOIN Production.ProductInventory AS pi ON pm.ProductModelID = pi.ProductID   
      WHERE pi.ProductID = 101   
      GROUP BY pi.ProductID, pi.Quantity   
      HAVING sum(pi.Quantity) > 50',  
    @stmt OUTPUT,   
    @params OUTPUT;  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 <span data-ttu-id="523d4-127">同様に、強制パラメーター化が既に有効になっているデータベースでは、サンプルのクエリや、構文が同じでも定数リテラル値が異なるその他のクエリが、簡易パラメーター化のルールに従ってパラメーター化されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="523d4-127">Similarly, in a database in which forced parameterization is already enabled, you can make sure that the sample query, and others that are syntactically equivalent, except for their constant literal values, are parameterized according to the rules of simple parameterization.</span></span> <span data-ttu-id="523d4-128">この場合は、OPTION 句に PARAMETERIZATION FORCED ではなく PARAMETERIZATION SIMPLE を指定します。</span><span class="sxs-lookup"><span data-stu-id="523d4-128">To do this, specify PARAMETERIZATION SIMPLE instead of PARAMETERIZATION FORCED in the OPTION clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="523d4-129">TEMPLATE プラン ガイドは、ステートメントと、単一のステートメントのみで構成されるバッチにより送信されるクエリとを対応付けます。</span><span class="sxs-lookup"><span data-stu-id="523d4-129">TEMPLATE plan guides match statements to queries submitted in batches that consist of a single statement only.</span></span> <span data-ttu-id="523d4-130">複数のステートメントで構成されるバッチ内のステートメントは、TEMPLATE プラン ガイドで対応付けできません。</span><span class="sxs-lookup"><span data-stu-id="523d4-130">Statements inside multistatement batches are not eligible to be matched by TEMPLATE plan guides.</span></span>  
  
  
