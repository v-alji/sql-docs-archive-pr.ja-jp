---
title: 固定サーバーロール名と一致するログイン名を変更する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 296ae4d4051e79e3c5d3bc158ef3e87c9164ecd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720840"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a><span data-ttu-id="e9c7d-102">固定サーバー ロール名と一致するログイン名を変更する</span><span class="sxs-lookup"><span data-stu-id="e9c7d-102">Rename logins matching fixed server role names</span></span>
  <span data-ttu-id="e9c7d-103">アップグレード アドバイザーによって、固定サーバー ロール名と一致する 1 つ以上のユーザー定義ログイン名が検出されました。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-103">Upgrade Advisor detected one or more user-defined login names that match the names of fixed server roles.</span></span> <span data-ttu-id="e9c7d-104">固定サーバー ロール名は予約されています。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-104">Fixed server role names are reserved.</span></span> <span data-ttu-id="e9c7d-105">アップグレードする前に、ログイン名を変更してください。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-105">Rename the login before you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="e9c7d-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e9c7d-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="e9c7d-107">説明</span><span class="sxs-lookup"><span data-stu-id="e9c7d-107">Description</span></span>  
 <span data-ttu-id="e9c7d-108">以下の固定サーバー ロール名は予約されているため、ユーザー定義ログイン名として使用できません。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-108">The following fixed server role names are reserved and cannot be used as user-defined login names.</span></span>  
  
-   <span data-ttu-id="e9c7d-109">**sysadmin**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-109">**sysadmin**</span></span>  
  
-   <span data-ttu-id="e9c7d-110">**serveradmin**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-110">**serveradmin**</span></span>  
  
-   <span data-ttu-id="e9c7d-111">**setupadmin**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-111">**setupadmin**</span></span>  
  
-   <span data-ttu-id="e9c7d-112">**securityadmin**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-112">**securityadmin**</span></span>  
  
-   <span data-ttu-id="e9c7d-113">**processadmin**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-113">**processadmin**</span></span>  
  
-   <span data-ttu-id="e9c7d-114">**dbcreator**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-114">**dbcreator**</span></span>  
  
-   <span data-ttu-id="e9c7d-115">**diskadmin**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-115">**diskadmin**</span></span>  
  
-   <span data-ttu-id="e9c7d-116">**bulkadmin**</span><span class="sxs-lookup"><span data-stu-id="e9c7d-116">**bulkadmin**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="e9c7d-117">修正措置</span><span class="sxs-lookup"><span data-stu-id="e9c7d-117">Corrective Action</span></span>  
 <span data-ttu-id="e9c7d-118">アップグレードする前に、次の操作を行ってください。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-118">Before upgrading, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="e9c7d-119">次のステートメントを実行することによって、ログインのセキュリティ識別子 (SID) を記録します。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-119">Record the security identifiers (SIDs) of the logins by executing the following statement.</span></span>  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  <span data-ttu-id="e9c7d-120">ログイン名を削除します。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-120">Drop the logins.</span></span>  
  
3.  <span data-ttu-id="e9c7d-121">新しいログインを作成するには、 **sp_addlogin**システムプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-121">Use the **sp_addlogin** system procedure to create new logins.</span></span> <span data-ttu-id="e9c7d-122">対応する各ログインの\*\* \@ sid\*\*パラメーターに、手順 1. で返された sid を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9c7d-122">Specify the SID returned in step 1 in the **\@sid** parameter for each corresponding login.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c7d-123">参照</span><span class="sxs-lookup"><span data-stu-id="e9c7d-123">See Also</span></span>  
 <span data-ttu-id="e9c7d-124">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="e9c7d-124">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="e9c7d-125">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="e9c7d-125">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
