---
title: FOR XML AUTO クエリは、90以降の互換性モードで派生テーブル参照を返します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 702cb2ca1d437dff03cee09c98d72082500709d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646009"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a><span data-ttu-id="5ac89-102">互換性モード 90 以上では FOR XML AUTO クエリが派生テーブルの参照を返す</span><span class="sxs-lookup"><span data-stu-id="5ac89-102">FOR XML AUTO queries return derived table references in 90 or later compatibility modes</span></span>
  <span data-ttu-id="5ac89-103">データベースの互換性レベルが 90 以上に設定されている場合、AUTO モードで実行する FOR XML クエリは派生テーブルの別名への参照を返します。</span><span class="sxs-lookup"><span data-stu-id="5ac89-103">When the database compatibility level is set to 90 or later, FOR XML queries that execute in AUTO mode return references to derived table aliases.</span></span> <span data-ttu-id="5ac89-104">互換性レベルが 80 に設定されている場合、FOR XML AUTO クエリは派生テーブルを定義するベース テーブルへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="5ac89-104">When the compatibility level is set to 80, FOR XML AUTO queries return references to the base tables that define a derived table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="5ac89-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5ac89-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="5ac89-106">説明</span><span class="sxs-lookup"><span data-stu-id="5ac89-106">Description</span></span>  
 <span data-ttu-id="5ac89-107">たとえば、次のテーブルについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="5ac89-107">For example, consider the following table:</span></span>  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 <span data-ttu-id="5ac89-108">次のクエリには派生テーブルが含まれており、互換性レベル 80 と 90 以上では異なる結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5ac89-108">The following query, which includes a derived table, produces different results under compatibility levels 80, 90, or later:</span></span>  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 <span data-ttu-id="5ac89-109">互換性レベル 80 では、クエリは次の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="5ac89-109">Under compatibility level 80, the query returns the following results.</span></span> <span data-ttu-id="5ac89-110">この結果は、派生テーブルの別名ではなく、派生テーブルのベース テーブルの別名 `a` と `b` を参照しています。</span><span class="sxs-lookup"><span data-stu-id="5ac89-110">The results reference the base table aliases `a` and `b` of the derived table instead of the derived table alias.</span></span>  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 <span data-ttu-id="5ac89-111">互換性レベル 90 以上では、クエリは派生テーブルのベース テーブルへの参照ではなく、派生テーブルの別名 `DerivedTest` への参照を返します。</span><span class="sxs-lookup"><span data-stu-id="5ac89-111">Under compatibility level 90 or later, the query returns references to the derived table alias `DerivedTest` instead of to the derived table's base tables.</span></span>  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="5ac89-112">修正措置</span><span class="sxs-lookup"><span data-stu-id="5ac89-112">Corrective Action</span></span>  
 <span data-ttu-id="5ac89-113">派生テーブルを含んでいる FOR XML AUTO クエリのうち、互換性レベル 90 以上で実行されるクエリの結果が変化している場合、必要に応じてアプリケーションを修正してください。</span><span class="sxs-lookup"><span data-stu-id="5ac89-113">Modify your application as required to account for the changes in results of FOR XML AUTO queries that include derived tables and that run under compatibility level 90 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac89-114">参照</span><span class="sxs-lookup"><span data-stu-id="5ac89-114">See Also</span></span>  
 <span data-ttu-id="5ac89-115">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="5ac89-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="5ac89-116">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="5ac89-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
