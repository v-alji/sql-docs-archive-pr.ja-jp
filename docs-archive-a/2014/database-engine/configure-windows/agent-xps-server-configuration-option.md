---
title: Agent XP サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 541c81ea8d9f782a9c1ea391824b90a6fee772d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642311"
---
# <a name="agent-xps-server-configuration-option"></a><span data-ttu-id="ed634-102">Agent XP サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="ed634-102">Agent XPs Server Configuration Option</span></span>
  <span data-ttu-id="ed634-103">**Agent XPs** オプションは、このサーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを有効にする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ed634-103">Use the **Agent XPs** option to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures on this server.</span></span> <span data-ttu-id="ed634-104">このオプションを有効にしないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオブジェクト エクスプローラーに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] エージェントのノードが表示されません。</span><span class="sxs-lookup"><span data-stu-id="ed634-104">When this option is not enabled, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer.</span></span>  
  
 <span data-ttu-id="ed634-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ツールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを開始すると、これらの拡張ストアド プロシージャは自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="ed634-105">When you use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tool to start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, these extended stored procedures are enabled automatically.</span></span> <span data-ttu-id="ed634-106">詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed634-106">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="ed634-107">のオブジェクト エクスプローラーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスの状態にかかわらず、これらの拡張ストアド プロシージャを有効にしない限り、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのノードのコンテンツは表示されません。</span><span class="sxs-lookup"><span data-stu-id="ed634-107">Object Explorer does not display the contents of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent node unless these extended stored procedures are enabled regardless of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service state.</span></span>  
  
 <span data-ttu-id="ed634-108">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="ed634-108">The possible values are:</span></span>  
  
-   <span data-ttu-id="ed634-109">**0**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを使用できないことを示します (既定)。</span><span class="sxs-lookup"><span data-stu-id="ed634-109">**0**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are not available (the default).</span></span>  
  
-   <span data-ttu-id="ed634-110">**1**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="ed634-110">**1**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are available.</span></span>  
  
 <span data-ttu-id="ed634-111">この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="ed634-111">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ed634-112">例</span><span class="sxs-lookup"><span data-stu-id="ed634-112">Examples</span></span>  
 <span data-ttu-id="ed634-113">次の例では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ed634-113">The following example enables the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed634-114">参照</span><span class="sxs-lookup"><span data-stu-id="ed634-114">See Also</span></span>  
 <span data-ttu-id="ed634-115">[管理タスクの自動化 &#40;SQL Server エージェント&#41;](../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="ed634-115">[Automated Administration Tasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="ed634-116">SQL Server エージェント サービスの開始、停止、または一時停止</span><span class="sxs-lookup"><span data-stu-id="ed634-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
