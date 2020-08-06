---
title: 外部結合演算子 *= および = は、* 90 以降の互換性モードではサポートされていません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 357c729e6d53cc17f2e4c169dd66613b6cfd2f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720865"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a><span data-ttu-id="73cb2-102">互換性モード 90 以上では外部結合演算子 \*= および =\* がサポートされない</span><span class="sxs-lookup"><span data-stu-id="73cb2-102">Outer join operators \*= and =\* are not supported in 90 or later compatibility modes</span></span>
  <span data-ttu-id="73cb2-103">アップグレードアドバイザーによって、外部結合演算子 = および = が使用されたことが検出されました \* \* 。</span><span class="sxs-lookup"><span data-stu-id="73cb2-103">Upgrade Advisor detected the use of outer join operators \*= and =\*.</span></span> <span data-ttu-id="73cb2-104">このような演算子は互換性モード 90 以上ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="73cb2-104">These operators are not supported in 90 or later compatibility modes.</span></span> <span data-ttu-id="73cb2-105">アップグレードすると、ユーザー データベースでは互換性モードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="73cb2-105">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="73cb2-106">これらの演算子を使用するステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="73cb2-106">Statements that use these operators will fail.</span></span>  
  
## <a name="component"></a><span data-ttu-id="73cb2-107">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="73cb2-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="73cb2-108">修正措置</span><span class="sxs-lookup"><span data-stu-id="73cb2-108">Corrective Action</span></span>  
 <span data-ttu-id="73cb2-109">データベース互換性モードを90以降に変更する前に、外部結合演算子 = および = を使用するステートメントを、 \* \* 同等の外部結合キーワードを使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="73cb2-109">Before you change the database compatibility mode to 90 or later, modify statements that use the outer join operators \*= and =\* to use equivalent OUTER JOIN keywords.</span></span> <span data-ttu-id="73cb2-110">次の例では、`\*=` 演算子を使用するクエリと、`LEFT OUTER JOIN` キーワードを使用する同等のクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="73cb2-110">The following example shows a query that uses the `\*=` operator and an equivalent query that uses the `LEFT OUTER JOIN` keywords.</span></span>  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 <span data-ttu-id="73cb2-111">詳細については、SQL Server オンライン ブックの「外部結合の使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73cb2-111">For more information about outer joins, see "Using Outer Joins" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cb2-112">参照</span><span class="sxs-lookup"><span data-stu-id="73cb2-112">See Also</span></span>  
 <span data-ttu-id="73cb2-113">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="73cb2-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="73cb2-114">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="73cb2-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
