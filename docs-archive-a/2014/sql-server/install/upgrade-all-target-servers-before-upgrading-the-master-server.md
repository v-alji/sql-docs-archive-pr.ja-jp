---
title: マスターサーバーをアップグレードする前にすべての対象サーバーをアップグレードする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 031fedc4af4b058704cef1da8df846397b235305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632276"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a><span data-ttu-id="db018-102">マスター サーバーをアップグレードする前にすべてのターゲット サーバーをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="db018-102">Upgrade all target servers before upgrading the master server</span></span>
  <span data-ttu-id="db018-103">マスター サーバーをアップグレードする前に、ターゲット サーバーとして構成され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているすべてのコンピューターをアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="db018-103">Before you upgrade the master server, upgrade all computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are configured as target servers.</span></span>  
  
## <a name="component"></a><span data-ttu-id="db018-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="db018-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db018-105">エージェント</span><span class="sxs-lookup"><span data-stu-id="db018-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="db018-106">説明</span><span class="sxs-lookup"><span data-stu-id="db018-106">Description</span></span>  
 <span data-ttu-id="db018-107">マルチサーバー環境で管理を自動化するには、マスター サーバーとターゲット サーバーが少なくとも 1 台ずつ必要です。</span><span class="sxs-lookup"><span data-stu-id="db018-107">To automate administration in multiserver environments, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="db018-108">マスター サーバーは、ターゲット サーバーに対してジョブを分散し、ターゲット サーバーからイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="db018-108">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="db018-109">また、マスター サーバーは、ターゲット サーバーで実行されるジョブについて、ジョブ定義の中央コピーも保存します。</span><span class="sxs-lookup"><span data-stu-id="db018-109">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span>  
  
 <span data-ttu-id="db018-110">現在のサーバーがマスター サーバーとして構成されている場合、最初にすべてのターゲット サーバーをアップグレードしてから、マスター サーバーをアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="db018-110">If the current server is configured as a master server, upgrade all of your target servers first before you upgrade the master server.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="db018-111">修正措置</span><span class="sxs-lookup"><span data-stu-id="db018-111">Corrective Action</span></span>  
 <span data-ttu-id="db018-112">マスター サーバーをアップグレードする前に、すべてのターゲット サーバーをアップグレードできない場合は、アップグレード後に、すべてのターゲット サーバーの参加を解除してからもう一度参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="db018-112">If you cannot upgrade all target servers before you upgrade the master server, you must defect all target servers and reenlist them after you upgrade.</span></span>  
  
 <span data-ttu-id="db018-113">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックのトピック「エンタープライズ全体の管理の自動化」、「マスター サーバーからターゲット サーバーの参加を解除する方法」、および「マスター サーバーにターゲット サーバーを参加させる方法」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db018-113">For more information, see the topics "Automating Administration across an Enterprise," "How to: Defect a Target Server from a Master Server," and "How to: Enlist a Target Server to a Master" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db018-114">参照</span><span class="sxs-lookup"><span data-stu-id="db018-114">See Also</span></span>  
 <span data-ttu-id="db018-115">[SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="db018-115">[SQL Server Agent Upgrade Issues](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="db018-116">SQL Server エージェントのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="db018-116">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
