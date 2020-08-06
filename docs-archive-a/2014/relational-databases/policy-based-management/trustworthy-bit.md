---
title: 信頼可能なビット | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 062a63dd52f4641a0ddfcbc20cb9bad3cce6dc61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634455"
---
# <a name="trustworthy-bit"></a><span data-ttu-id="abadd-102">信頼可能なビット</span><span class="sxs-lookup"><span data-stu-id="abadd-102">Trustworthy Bit</span></span>
  <span data-ttu-id="abadd-103">このルールでは、sysadmin 固定サーバー ロールにデータベースの dbo ロールが割り当てられているかどうか、およびデータベースの信頼可能なビットがオンに設定されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="abadd-103">This rule determines whether the dbo role for a database is assigned to the sysadmin fixed server role and the database has its trustworthy bit set to ON.</span></span>  
  
 <span data-ttu-id="abadd-104">これらの条件が満たされている場合、権限のあるデータベース ユーザーは、特権を sysadmin ロールに昇格させることができます。</span><span class="sxs-lookup"><span data-stu-id="abadd-104">If these conditions are met, a privileged database user can elevate privileges to the sysadmin role.</span></span> <span data-ttu-id="abadd-105">このロールでは、ユーザーはシステムを危険にさらす安全ではないアセンブリを作成して実行できます。</span><span class="sxs-lookup"><span data-stu-id="abadd-105">In this role, the user can create and run unsafe assemblies that compromise the system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="abadd-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="abadd-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="abadd-107">信頼可能なビットをオフにするか、dbo データベース ロールから sysadmin 権限を取り消します。</span><span class="sxs-lookup"><span data-stu-id="abadd-107">Turn off the trustworthy bit or revoke sysadmin permissions from the dbo database role.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="abadd-108">詳細情報</span><span class="sxs-lookup"><span data-stu-id="abadd-108">For More Information</span></span>  
 [<span data-ttu-id="abadd-109">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="abadd-109">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="abadd-110">参照</span><span class="sxs-lookup"><span data-stu-id="abadd-110">See Also</span></span>  
 [<span data-ttu-id="abadd-111">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="abadd-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
