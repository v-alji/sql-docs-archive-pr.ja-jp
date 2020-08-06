---
title: システムオブジェクトに対する列レベルの権限を変更するステートメントを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e55af3dca0c55c2babd09bc6cfc48ed0ddf3ad7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643113"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a><span data-ttu-id="bcaec-102">システム オブジェクトの列レベル権限を変更するステートメントを削除する</span><span class="sxs-lookup"><span data-stu-id="bcaec-102">Remove statements that modify column-level permissions on system objects</span></span>
  <span data-ttu-id="bcaec-103">アップグレード アドバイザーがシステム オブジェクトに対する標準以外の列レベル権限を検出しました。</span><span class="sxs-lookup"><span data-stu-id="bcaec-103">The Upgrade Advisor detected nonstandard column-level permissions on system objects.</span></span> <span data-ttu-id="bcaec-104">これらの権限の変更は、アップグレードすると維持されません。</span><span class="sxs-lookup"><span data-stu-id="bcaec-104">These permission changes will not be maintained when you upgrade.</span></span> <span data-ttu-id="bcaec-105">また、システム オブジェクトに対する列レベル権限はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bcaec-105">Additionally, column-level permissions on system objects are no longer supported.</span></span> <span data-ttu-id="bcaec-106">アプリケーションから、システム オブジェクトに対する列レベル権限を設定するステートメントを削除してください。</span><span class="sxs-lookup"><span data-stu-id="bcaec-106">Remove statements from your applications that set column-level permissions on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="bcaec-107">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bcaec-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="bcaec-108">修正措置</span><span class="sxs-lookup"><span data-stu-id="bcaec-108">Corrective Action</span></span>  
 <span data-ttu-id="bcaec-109">システム オブジェクトに対する列レベル権限を許可、拒否、または禁止するステートメントをアプリケーションから削除します。</span><span class="sxs-lookup"><span data-stu-id="bcaec-109">Remove statements from your application that grant, deny, or revoke column-level permissions on system objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcaec-110">参照</span><span class="sxs-lookup"><span data-stu-id="bcaec-110">See Also</span></span>  
 <span data-ttu-id="bcaec-111">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="bcaec-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="bcaec-112">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="bcaec-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
