---
title: 休止 SQL Server 6.5 ログインをアップグレードすることはできません |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640442"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a><span data-ttu-id="8792c-102">休止している SQL Server 6.5 ログインはアップグレードできない</span><span class="sxs-lookup"><span data-stu-id="8792c-102">Dormant SQL Server 6.5 logins cannot be upgraded</span></span>
  <span data-ttu-id="8792c-103">アップグレード アドバイザーによって、パスワードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に直接アップグレードできない [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ログインが検出されました。</span><span class="sxs-lookup"><span data-stu-id="8792c-103">Upgrade Advisor detected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login whose password cannot be directly upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="8792c-104">このログインを有効にするには、パスワードをリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8792c-104">To enable this login, you must reset its password.</span></span> <span data-ttu-id="8792c-105">パスワードをリセットするには、ALTER LOGIN を使用します。</span><span class="sxs-lookup"><span data-stu-id="8792c-105">You can reset the password by using ALTER LOGIN.</span></span>  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 <span data-ttu-id="8792c-106">新しいパスワードがシステムのパスワード複雑性ポリシーを満たしているか検証されます。ポリシーのチェックが無効になっている場合は検証が行われません。</span><span class="sxs-lookup"><span data-stu-id="8792c-106">The new password will be validated against your system's password complexity policy, unless policy checking is disabled.</span></span> <span data-ttu-id="8792c-107">複雑なパスワードを使用し、ポリシーのチェックを無効にしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8792c-107">We recommend that you use complex passwords and not disable policy checking.</span></span> <span data-ttu-id="8792c-108">MUST_CHANGE オプションを使用すると、新しいパスワードの選択がユーザーに強制されます。</span><span class="sxs-lookup"><span data-stu-id="8792c-108">The MUST_CHANGE option forces the user to select a new password.</span></span> <span data-ttu-id="8792c-109">これは必須ではありませんが、推奨されています。</span><span class="sxs-lookup"><span data-stu-id="8792c-109">This is not required, but it is recommended.</span></span>  
  
 <span data-ttu-id="8792c-110">次のクエリを使用すると、休止ログインを特定できます。</span><span class="sxs-lookup"><span data-stu-id="8792c-110">You can identify dormant logins by using the following query:</span></span>  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8792c-111">参照</span><span class="sxs-lookup"><span data-stu-id="8792c-111">See Also</span></span>  
 <span data-ttu-id="8792c-112">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="8792c-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="8792c-113">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="8792c-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
