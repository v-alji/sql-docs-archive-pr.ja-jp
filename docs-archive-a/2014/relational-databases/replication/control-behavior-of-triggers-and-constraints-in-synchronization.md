---
title: 同期中にトリガーと制約の動作を制御する (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88176f43295fe2ab1f5f5643a46db1ce6132c5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631829"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a><span data-ttu-id="92cc3-102">同期中にトリガーと制約の動作を制御する (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="92cc3-102">Control the Behavior of Triggers and Constraints During Synchronization (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="92cc3-103">同期中、レプリケートされるテーブルでは、[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)、[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)、[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) の各ステートメントがレプリケーション エージェントによって実行され、これらのテーブルに対して設定されていたデータ操作言語 (DML) のトリガーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="92cc3-103">During synchronization, replication agents execute [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql), and [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) statements on replicated tables, which can cause data manipulation language (DML) triggers on these tables to be executed.</span></span> <span data-ttu-id="92cc3-104">同期中はこれらのトリガーが起動しないようにしたり、制約が適用されないようにすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="92cc3-104">There are cases when you may need to prevent these triggers from firing or constraints from being enforced during synchronization.</span></span> <span data-ttu-id="92cc3-105">このときの動作は、トリガーまたは制約がどのように作成されたかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="92cc3-105">This behavior depends on how the trigger or constraint is created.</span></span>  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a><span data-ttu-id="92cc3-106">同期中にトリガーが実行されないようにするには</span><span class="sxs-lookup"><span data-stu-id="92cc3-106">To prevent triggers from executing during synchronization</span></span>  
  
1.  <span data-ttu-id="92cc3-107">新しいトリガーを作成する場合は、[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) の NOT FOR REPLICATION オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="92cc3-107">When creating a new trigger, specify the NOT FOR REPLICATION option of [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
2.  <span data-ttu-id="92cc3-108">既存のトリガーの場合は、[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) の NOT FOR REPLICATION オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="92cc3-108">For an existing trigger, specify the NOT FOR REPLICATION option of [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql).</span></span>  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a><span data-ttu-id="92cc3-109">同期中に制約が適用されないようにするには</span><span class="sxs-lookup"><span data-stu-id="92cc3-109">To prevent constraints from being enforced during synchronization</span></span>  
  
1.  <span data-ttu-id="92cc3-110">CHECK 制約または FOREIGN KEY 制約を新たに作成する場合は、 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) の制約定義で、CHECK NOT FOR REPLICATION オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="92cc3-110">When creating a new CHECK or FOREIGN KEY constraint, specify CHECK NOT FOR REPLICATION option in the constraint definition of [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92cc3-111">参照</span><span class="sxs-lookup"><span data-stu-id="92cc3-111">See Also</span></span>  
 [<span data-ttu-id="92cc3-112">テーブルの作成 &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="92cc3-112">Create Tables &#40;Database Engine&#41;</span></span>](../tables/create-tables-database-engine.md)  
  
  
