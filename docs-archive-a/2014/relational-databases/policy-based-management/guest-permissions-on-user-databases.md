---
title: ユーザー データベースに対する guest の権限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 344c5fd0639876998f1585c32fac5f7599f664e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632442"
---
# <a name="guest-permissions-on-user-databases"></a><span data-ttu-id="b18d7-102">ユーザー データベースに対する guest の権限</span><span class="sxs-lookup"><span data-stu-id="b18d7-102">Guest Permissions on User Databases</span></span>
  <span data-ttu-id="b18d7-103">このルールでは、guest ユーザーがデータベースにアクセスする権限を持っているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="b18d7-103">This rule determines whether the guest user has permission to access the database.</span></span> <span data-ttu-id="b18d7-104">このルールはユーザー データベースにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b18d7-104">This rule applies to user databases only.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="b18d7-105">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="b18d7-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="b18d7-106">必要でない場合は、データベースにアクセスする権限を guest ユーザー権限から取り消します。</span><span class="sxs-lookup"><span data-stu-id="b18d7-106">Revoke the guest user permission to access the database if it is not required.</span></span>  
  
 <span data-ttu-id="b18d7-107">guest ユーザーは削除できませんが、master、tempdb、または msdb 以外のデータベースでは、REVOKE CONNECT FROM GUEST を実行して CONNECT 権限を取り消すことにより、guest ユーザーを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="b18d7-107">The guest user cannot be dropped, but guest user can be disabled by revoking its CONNECT permission by executing REVOKE CONNECT FROM GUEST within any database other than master, tempdb, or msdb.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="b18d7-108">詳細情報</span><span class="sxs-lookup"><span data-stu-id="b18d7-108">For More Information</span></span>  
 [<span data-ttu-id="b18d7-109">SQL Server の保護</span><span class="sxs-lookup"><span data-stu-id="b18d7-109">Securing SQL Server</span></span>](../security/securing-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b18d7-110">参照</span><span class="sxs-lookup"><span data-stu-id="b18d7-110">See Also</span></span>  
 [<span data-ttu-id="b18d7-111">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="b18d7-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
