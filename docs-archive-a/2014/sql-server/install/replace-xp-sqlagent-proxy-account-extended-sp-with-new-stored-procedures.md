---
title: Xp_sqlagent_proxy_account 拡張ストアドプロシージャの使用を新しいストアドプロシージャに置き換える |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xp_sqlagent_proxy_account
ms.assetid: 0e3cc931-6237-41dd-bf0d-0c03f4d8fff2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d124ab73f4b4315550134f28ffad232b4a1c0ec2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643100"
---
# <a name="replace-usage-of-the-xp_sqlagent_proxy_account-extended-stored-procedure-with-new-stored-procedures"></a><span data-ttu-id="3fecd-102">xp_sqlagent_proxy_account 拡張ストアド プロシージャの代わりに新しいストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="3fecd-102">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3fecd-103">エージェントは複数のプロキシをサポートします。</span><span class="sxs-lookup"><span data-stu-id="3fecd-103">Agent supports multiple proxies.</span></span> <span data-ttu-id="3fecd-104">これらのプロキシは新しい一連のストアド プロシージャを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="3fecd-104">You define these proxies by using a new set of stored procedures.</span></span> <span data-ttu-id="3fecd-105">新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのストアド プロシージャの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fecd-105">For more information about the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   <span data-ttu-id="3fecd-106">「sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-106">"sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-107">「sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-107">"sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-108">「sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-108">"sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-109">「sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-109">"sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-110">「sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-110">"sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-111">「sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-111">"sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-112">「sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-112">"sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-113">「sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-113">"sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-114">「sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-114">"sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-115">「sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-115">"sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="3fecd-116">「sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])」</span><span class="sxs-lookup"><span data-stu-id="3fecd-116">"sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3fecd-117">にアップグレードした後 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 、 **xp_sqlagent_proxy_account**の拡張ストアドプロシージャを使用するステートメントは機能しません。</span><span class="sxs-lookup"><span data-stu-id="3fecd-117">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], any statements that use the **xp_sqlagent_proxy_account** extended stored procedure will not work.</span></span> <span data-ttu-id="3fecd-118">**Xp_cmdshell**にプロキシを設定するには、 **xp_sqlagent_proxy_account**ではなく**sp_xp_cmdshell_proxy_account**を使用します。</span><span class="sxs-lookup"><span data-stu-id="3fecd-118">Use **sp_xp_cmdshell_proxy_account** instead of **xp_sqlagent_proxy_account** to set the proxy for **xp_cmdshell**.</span></span>  
  
## <a name="component"></a><span data-ttu-id="3fecd-119">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3fecd-119">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3fecd-120">エージェント</span><span class="sxs-lookup"><span data-stu-id="3fecd-120">Agent</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fecd-121">参照</span><span class="sxs-lookup"><span data-stu-id="3fecd-121">See Also</span></span>  
 [<span data-ttu-id="3fecd-122">SQL Server エージェントのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="3fecd-122">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
