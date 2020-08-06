---
title: 中断された復元操作の再開 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6fa09ce66865d61c8f3a86feedc04eaf8deec2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712053"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a><span data-ttu-id="bd0e0-102">中断された復元操作の再開 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bd0e0-102">Restart an Interrupted Restore Operation (Transact-SQL)</span></span>
  <span data-ttu-id="bd0e0-103">このトピックでは、中断された復元操作を再開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd0e0-103">This topic explains how to restart an interrupted restore operation.</span></span>  
  
### <a name="to-restart-an-interrupted-restore-operation"></a><span data-ttu-id="bd0e0-104">中断された復元操作を再開するには</span><span class="sxs-lookup"><span data-stu-id="bd0e0-104">To restart an interrupted restore operation</span></span>  
  
1.  <span data-ttu-id="bd0e0-105">次の項目を指定して、中断された RESTORE ステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="bd0e0-105">Execute the interrupted RESTORE statement again, specifying:</span></span>  
  
    -   <span data-ttu-id="bd0e0-106">元の RESTORE ステートメントで使用したものと同じ句</span><span class="sxs-lookup"><span data-stu-id="bd0e0-106">The same clauses used in the original RESTORE statement.</span></span>  
  
    -   <span data-ttu-id="bd0e0-107">RESTART 句</span><span class="sxs-lookup"><span data-stu-id="bd0e0-107">The RESTART clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd0e0-108">例</span><span class="sxs-lookup"><span data-stu-id="bd0e0-108">Example</span></span>  
 <span data-ttu-id="bd0e0-109">この例では、中断された復元操作を再開します。</span><span class="sxs-lookup"><span data-stu-id="bd0e0-109">This example restarts an interrupted restore operation.</span></span>  
  
```sql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd0e0-110">参照</span><span class="sxs-lookup"><span data-stu-id="bd0e0-110">See Also</span></span>  
 <span data-ttu-id="bd0e0-111">[データベースの全体復元 &#40;完全復旧モデル&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="bd0e0-111">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="bd0e0-112">[データベースの全体復元 &#40;単純復旧モデル&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="bd0e0-112">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="bd0e0-113">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bd0e0-113">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
