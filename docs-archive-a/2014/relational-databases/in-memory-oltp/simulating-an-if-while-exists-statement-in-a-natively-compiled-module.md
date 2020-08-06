---
title: ネイティブコンパイルストアドプロシージャでの EXISTS 句のシミュレーション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b16491b9a3729ad4df71c7ddceaee6db21777ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742054"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a><span data-ttu-id="55d85-102">ネイティブ コンパイル ストアド プロシージャ内の EXISTS 句のシミュレーション</span><span class="sxs-lookup"><span data-stu-id="55d85-102">Simulating an EXISTS Clause in a Natively Compiled Stored Procedure</span></span>
  <span data-ttu-id="55d85-103">ネイティブ コンパイル ストアド プロシージャでは `EXISTS` 句はサポートされませんが、対応策があります。</span><span class="sxs-lookup"><span data-stu-id="55d85-103">Natively compiled stored procedures do not support the `EXISTS` clause, but there is a workaround:</span></span>  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a><span data-ttu-id="55d85-104">参照</span><span class="sxs-lookup"><span data-stu-id="55d85-104">See Also</span></span>  
 <span data-ttu-id="55d85-105">[ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="55d85-105">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="55d85-106">インメモリ OLTP でサポートされていない Transact-SQL の構造</span><span class="sxs-lookup"><span data-stu-id="55d85-106">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
