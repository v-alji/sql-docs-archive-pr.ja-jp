---
title: ミラー化メディア セットへのバックアップ (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 255a3c190139c029f5211dcab9780b6d07d975a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641699"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a><span data-ttu-id="7c940-102">ミラー化メディア セットへのバックアップ (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7c940-102">Back Up to a Mirrored Media Set (Transact-SQL)</span></span>
  <span data-ttu-id="7c940-103">このトピックでは、BACKUP ステートメントを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql)データベースのバックアップ時にミラー化メディアセットを指定する方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7c940-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to specify a mirrored media set when backing up a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="7c940-104">BACKUP ステートメントの TO 句で最初のミラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="7c940-104">In your BACKUP statement, specify the first mirror in the TO clause.</span></span> <span data-ttu-id="7c940-105">次に、このステートメントの MIRROR TO 句で各ミラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="7c940-105">Then, specify each mirror in its own MIRROR TO clause.</span></span> <span data-ttu-id="7c940-106">TO 句および MIRROR TO 句では、同じ数と種類のバックアップ デバイスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c940-106">The TO and MIRROR TO clauses must specify the same number and type of backup devices.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c940-107">例</span><span class="sxs-lookup"><span data-stu-id="7c940-107">Example</span></span>  
 <span data-ttu-id="7c940-108">次の例では、上の図のミラー化メディア セットを作成し、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを両方のミラーにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="7c940-108">The following example creates the mirrored media set illustrated in the previous illustration and backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to both mirrors.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="7c940-109">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="7c940-109">Related Tasks</span></span>  
 <span data-ttu-id="7c940-110">**ミラー化バックアップから復元するには**</span><span class="sxs-lookup"><span data-stu-id="7c940-110">**To restore from a mirrored backup**</span></span>  
  
-   [<span data-ttu-id="7c940-111">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7c940-111">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="7c940-112">参照</span><span class="sxs-lookup"><span data-stu-id="7c940-112">See Also</span></span>  
 <span data-ttu-id="7c940-113">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7c940-113">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="7c940-114">ミラー化バックアップ メディア セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7c940-114">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
