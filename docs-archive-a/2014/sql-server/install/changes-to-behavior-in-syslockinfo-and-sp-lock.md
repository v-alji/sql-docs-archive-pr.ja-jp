---
title: Syslockinfo および sp_lock での動作の変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65ace190004cab911dd8996642720620eba94935
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640483"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a><span data-ttu-id="aa695-102">syslockinfo および sp_lock の動作に対する変更</span><span class="sxs-lookup"><span data-stu-id="aa695-102">Changes to behavior in syslockinfo and sp_lock</span></span>
  <span data-ttu-id="aa695-103">**syslockinfo**と**sp_lock**は、予期しない値を返すことがあります。</span><span class="sxs-lookup"><span data-stu-id="aa695-103">**syslockinfo** and **sp_lock** may return unexpected values.</span></span> <span data-ttu-id="aa695-104">また、追加の行が返される場合もあります。一方、 **syslockinfo**と**sp_lock**の以前のバージョンでは、ロックリソースあたり最大2行が返されていました。</span><span class="sxs-lookup"><span data-stu-id="aa695-104">They may also return additional rows, whereas previous versions of **syslockinfo** and **sp_lock** returned a maximum of two rows per lock resource.</span></span>  
  
 <span data-ttu-id="aa695-105">**Syslockinfo**から情報にアクセスしたり、 **sp_lock**を実行したりするには、サーバーに対する VIEW server STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="aa695-105">To access information from **syslockinfo** or execute **sp_lock** requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="component"></a><span data-ttu-id="aa695-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="aa695-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="aa695-107">説明</span><span class="sxs-lookup"><span data-stu-id="aa695-107">Description</span></span>  
 <span data-ttu-id="aa695-108">では [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 、 **syslockinfo**の**rsc_objid**列と**rsc_indid**列、および**sp_lock**の**OBJID**列と**indid**列は、常にオブジェクト ID とインデックス ID を返します。</span><span class="sxs-lookup"><span data-stu-id="aa695-108">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the **rsc_objid** and **rsc_indid** columns in **syslockinfo** and the **objid** and **indid** columns in **sp_lock** consistently return the object ID and index ID.</span></span> <span data-ttu-id="aa695-109">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、値 0 が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="aa695-109">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a value of 0 may be returned.</span></span>  
  
 <span data-ttu-id="aa695-110">では [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 、 **syslockinfo**と**sp_lock**は、1つのトランザクション内の特定のロックリソースに対して最大で2つの行を返します。</span><span class="sxs-lookup"><span data-stu-id="aa695-110">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** and **sp_lock** return a maximum of two rows for any given lock resource in a single transaction.</span></span> <span data-ttu-id="aa695-111">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、ロックのパーティション分割が有効である場合、1 つのトランザクションで実行している同じリソースに対して複数行が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="aa695-111">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], when lock partitioning is enabled, multiple rows for the same resource running under one transaction may be returned.</span></span> <span data-ttu-id="aa695-112">返される行は最大 N + 1 行である場合があります。ここで、N は Cpu の数です。</span><span class="sxs-lookup"><span data-stu-id="aa695-112">There may be up to N + 1 rows returned, where N is the number of CPUs.</span></span> <span data-ttu-id="aa695-113">さらに、同じリソースに対する GRANTED 要求および WAITING 要求を表示できます。[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、それらの要求を表示できませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa695-113">Also, it is now possible to have GRANTED and WAITING requests displayed for the same resource, which was not possible in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="aa695-114">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="aa695-114">Permissions</span></span>  
 <span data-ttu-id="aa695-115">サーバーに対する VIEW SERVER STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="aa695-115">Requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa695-116">参照</span><span class="sxs-lookup"><span data-stu-id="aa695-116">See Also</span></span>  
 <span data-ttu-id="aa695-117">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="aa695-117">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="aa695-118">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="aa695-118">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
