---
title: ORDER BY 句の列の別名をテーブル別名 | で始まることはできませんMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 44333d778753a2f8761d32d181681b798e3bc409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640456"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a><span data-ttu-id="c8aa2-102">ORDER BY 句の列の別名をテーブル別名によってプレフィックス指定できない</span><span class="sxs-lookup"><span data-stu-id="c8aa2-102">Column aliases in ORDER BY clause cannot be prefixed by table alias</span></span>
  <span data-ttu-id="c8aa2-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、ORDER BY 句の列の別名はテーブル別名によってプレフィックス指定できません。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, column aliases in the ORDER BY clause cannot be prefixed by the table alias.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c8aa2-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c8aa2-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c8aa2-105">説明</span><span class="sxs-lookup"><span data-stu-id="c8aa2-105">Description</span></span>  
 <span data-ttu-id="c8aa2-106">たとえば、次のクエリは [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では実行されますが、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-106">For example, the following query executes in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], but returns an error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 <span data-ttu-id="c8aa2-107">[!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)]では `p.l` 句の `ORDER BY` がテーブル内の有効な列に一致しません。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-107">The [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] does not match `p.l` in the `ORDER BY` clause to a valid column in the table.</span></span>  
  
### <a name="exception"></a><span data-ttu-id="c8aa2-108">例外</span><span class="sxs-lookup"><span data-stu-id="c8aa2-108">Exception</span></span>  
 <span data-ttu-id="c8aa2-109">ORDER BY 句で指定された、プレフィックスの付いた列の別名が、指定したテーブルの有効な列名であれば、クエリは問題なく実行されます。[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、ステートメントのセマンティクスが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-109">If the prefixed column alias that is specified in the ORDER BY clause is a valid column name in the specified table, the query executes without error; in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the semantics of the statement might be different.</span></span> <span data-ttu-id="c8aa2-110">たとえば、以下のステートメントで指定された列の別名 (`id`) が `sysobjects` テーブル内の有効な列名であるとします。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-110">For example, the column alias (`id`) specified in the following statement is a valid column name in the `sysobjects` table.</span></span> <span data-ttu-id="c8aa2-111">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ではステートメントが実行されると、結果セットが並べ替えられた後、`CAST` 演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-111">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], when the statement executes, the `CAST` operation is performed after the result set is sorted.</span></span> <span data-ttu-id="c8aa2-112">つまり、`name` 列が並べ替え操作で使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-112">This means the `name` column is used in the sort operation.</span></span> <span data-ttu-id="c8aa2-113">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では並べ替え操作の前に `CAST` 演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-113">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the `CAST` operation occurs before the sort operation.</span></span> <span data-ttu-id="c8aa2-114">つまり、テーブル内の `id` 列が並べ替え操作に使用され、結果セットが予期しない順序で返されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-114">This means the `id` column in the table is used in the sort operation and returns the result set in an unexpected order.</span></span>  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="c8aa2-115">修正措置</span><span class="sxs-lookup"><span data-stu-id="c8aa2-115">Corrective Action</span></span>  
 <span data-ttu-id="c8aa2-116">次の方法のいずれかを使用して、ORDER BY 句のテーブル別名によってプレフィックス指定された列の別名を使用するクエリを修正してください。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-116">Modify queries that use column aliases prefixed by table aliases in the ORDER BY clause in either of the following ways:</span></span>  
  
-   <span data-ttu-id="c8aa2-117">可能な限り、ORDER BY 句の列の別名をプレフィックス指定しない。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-117">Do not prefix the column alias in the ORDER BY clause, if possible.</span></span>  
  
-   <span data-ttu-id="c8aa2-118">列の別名を列名に置き換える。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-118">Replace the column alias with the column name.</span></span>  
  
 <span data-ttu-id="c8aa2-119">たとえば、次の両方のクエリは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では問題なく実行されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa2-119">For example, both of the following queries execute without error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8aa2-120">参照</span><span class="sxs-lookup"><span data-stu-id="c8aa2-120">See Also</span></span>  
 <span data-ttu-id="c8aa2-121">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c8aa2-121">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c8aa2-122">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="c8aa2-122">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
