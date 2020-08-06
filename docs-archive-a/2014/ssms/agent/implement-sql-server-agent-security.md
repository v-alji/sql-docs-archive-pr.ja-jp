---
title: SQL Server エージェントのセキュリティの実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, security
- security [SQL Server Agent], about security
- security [SQL Server Agent]
- security [SQL Server], SQL Server Agent
ms.assetid: d770d35c-c8de-4e00-9a85-7d03f45a0f0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b70449ace66d4e33a547eca1c0b19eafabde5a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715030"
---
# <a name="implement-sql-server-agent-security"></a><span data-ttu-id="af9c1-102">SQL Server エージェントのセキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="af9c1-102">Implement SQL Server Agent Security</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="af9c1-103">エージェントを使用すると、データベース管理者は、各ジョブ ステップをそのジョブ ステップの実行に必要な権限だけがあるセキュリティ コンテキスト内で実行できます。適切なセキュリティ コンテキストは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシによって決まります。</span><span class="sxs-lookup"><span data-stu-id="af9c1-103">Agent lets the database administrator run each job step in a security context that has only the permissions required to perform that job step, which is determined by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy.</span></span> <span data-ttu-id="af9c1-104">特定のジョブ ステップに対応する権限を設定するには、必要な権限のあるプロキシを作成し、そのプロキシをジョブ ステップに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-104">To set the permissions for a particular job step, you create a proxy that has the required permissions and then assign that proxy to the job step.</span></span> <span data-ttu-id="af9c1-105">プロキシは、複数のジョブ ステップに対して指定できます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-105">A proxy can be specified for more than one job step.</span></span> <span data-ttu-id="af9c1-106">同じ権限を必要とするジョブ ステップに対しては、同じプロキシを使用します。</span><span class="sxs-lookup"><span data-stu-id="af9c1-106">For job steps that require the same permissions, you use the same proxy.</span></span>  
  
 <span data-ttu-id="af9c1-107">次のセクションでは、ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してジョブを作成または実行するために、許可する必要のあるデータベース ロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="af9c1-107">The following section explains what database role you must grant to users so they can create or execute jobs by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="granting-access-to-sql-server-agent"></a><span data-ttu-id="af9c1-108">SQL Server エージェントへのアクセスの許可</span><span class="sxs-lookup"><span data-stu-id="af9c1-108">Granting Access to SQL Server Agent</span></span>  
 <span data-ttu-id="af9c1-109">ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用するには、次の 1 つ以上の固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="af9c1-109">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, users must be a member of one or more of the following fixed database roles:</span></span>  
  
-   <span data-ttu-id="af9c1-110">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="af9c1-110">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="af9c1-111">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="af9c1-111">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="af9c1-112">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="af9c1-112">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="af9c1-113">上記のロールは、 **msdb** データベースに格納されています。</span><span class="sxs-lookup"><span data-stu-id="af9c1-113">These roles are stored in the **msdb** database.</span></span> <span data-ttu-id="af9c1-114">既定では、これらのデータベース ロールのメンバーであるユーザーはいません。</span><span class="sxs-lookup"><span data-stu-id="af9c1-114">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="af9c1-115">これらのロールのメンバーシップは、明示的に許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af9c1-115">Membership in these roles must be granted explicitly.</span></span> <span data-ttu-id="af9c1-116">**sysadmin** 固定サーバー ロールのメンバーであるユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントへのフル アクセスが許可されているので、上記の固定データベース ロールのメンバーでなくても [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-116">Users who are members of the **sysadmin** fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and do not need to be a member of these fixed database roles to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="af9c1-117">上記のいずれかのデータベース ロールまたは **sysadmin** ロールのメンバーでないユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する際に、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェント ノードを使用できません。</span><span class="sxs-lookup"><span data-stu-id="af9c1-117">If a user is not a member of one of these database roles or of the **sysadmin** role, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available to them when they connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="af9c1-118">これらのデータベース ロールのメンバーは、自身が所有するジョブの表示および実行に加えて、既存のプロキシ アカウントとして実行するジョブ ステップの作成を行えます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-118">Members of these database roles can view and execute jobs that they own, and create job steps that run as an existing proxy account.</span></span> <span data-ttu-id="af9c1-119">これらの各ロールに関連付けられている特定の権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af9c1-119">For more information about the specific permissions that are associated with each of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="af9c1-120">**sysadmin** 固定サーバー ロールのメンバーには、プロキシ アカウントを作成、変更、および削除する権限があります。</span><span class="sxs-lookup"><span data-stu-id="af9c1-120">Members of the **sysadmin** fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="af9c1-121">**sysadmin** ロールのメンバーには、プロキシを指定せずに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントとして実行するジョブ ステップを作成する権限があります。このアカウントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの起動に使用されるアカウントです。</span><span class="sxs-lookup"><span data-stu-id="af9c1-121">Members of the **sysadmin** role have permission to create job steps that do not specify a proxy, but instead run as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, which is the account that is used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="af9c1-122">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="af9c1-122">Guidelines</span></span>  
 <span data-ttu-id="af9c1-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのセキュリティを向上するには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="af9c1-123">Follow these guidelines to improve the security of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent implementation:</span></span>  
  
-   <span data-ttu-id="af9c1-124">プロキシ専用のユーザー アカウントを作成し、ジョブ ステップの実行にはこれらのプロキシ ユーザー アカウントのみを使用します。</span><span class="sxs-lookup"><span data-stu-id="af9c1-124">Create dedicated user accounts specifically for proxies, and only use these proxy user accounts for running job steps.</span></span>  
  
-   <span data-ttu-id="af9c1-125">プロキシ ユーザー アカウントに対し、必要な権限のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="af9c1-125">Only grant the necessary permissions to proxy user accounts.</span></span> <span data-ttu-id="af9c1-126">特定のプロキシ アカウントに割り当てられたジョブ ステップの実行に実際に求められる権限だけを許可してください。</span><span class="sxs-lookup"><span data-stu-id="af9c1-126">Grant only those permissions actually required to run the job steps that are assigned to a given proxy account.</span></span>  
  
-   <span data-ttu-id="af9c1-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、Windows **Administrators** グループのメンバーである Microsoft Windows アカウントで実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="af9c1-127">Do not run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under a Microsoft Windows account that is a member of the Windows **Administrators** group.</span></span>  
  
-   <span data-ttu-id="af9c1-128">プロキシの安全性は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報ストアと同程度です。</span><span class="sxs-lookup"><span data-stu-id="af9c1-128">Proxies are only as secure as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential store.</span></span>  
  
-   <span data-ttu-id="af9c1-129">ユーザーの書き込み操作で NT イベント ログへの書き込みが可能な場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを介して警告を発行できます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-129">If user write operations can write to the NT Event log, they can raise alerts via [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="af9c1-130">NT Admin アカントを、サービス アカウントまたはプロキシ アカウントとして指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="af9c1-130">Do not specify the NT Admin account as a service account or proxy account.</span></span>  
  
-   <span data-ttu-id="af9c1-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、他方の資産にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-131">Note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent have access to each other's assets.</span></span> <span data-ttu-id="af9c1-132">この 2 つのサービスは単一の処理領域を共有し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの sysadmin になります。</span><span class="sxs-lookup"><span data-stu-id="af9c1-132">The two services share a single process space and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is a sysadmin on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="af9c1-133">TSX が MSX で参加する場合、MSX の sysadmin が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の TSX インスタンスを完全に制御します。</span><span class="sxs-lookup"><span data-stu-id="af9c1-133">When a TSX enlists with an MSX, the MSX sysadmins gets total control over the TSX instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="af9c1-134">ACE は拡張機能であり、それ自体を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="af9c1-134">ACE is an extension and cannot invoke itself.</span></span> <span data-ttu-id="af9c1-135">ACE は Chainer ScenarioEngine.exe (別名 Microsoft.SqlServer.Chainer.Setup.exe) によって呼び出されるか、別のホスト プロセスによって呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-135">ACE is invoked by Chainer ScenarioEngine.exe - also known as Microsoft.SqlServer.Chainer.Setup.exe - or it can be invoked by another host process.</span></span>  
  
-   <span data-ttu-id="af9c1-136">ACE は、SSDP によって所有される次の構成 DLL に依存します。理由は、これらの DLL の API は ACE によって呼び出されるためです。</span><span class="sxs-lookup"><span data-stu-id="af9c1-136">ACE depends on the following configuration DLL's owned by SSDP, because those API's of DLL's are called by ACE:</span></span>  
  
    -   <span data-ttu-id="af9c1-137">**SCO**: Microsoft.SqlServer.Configuration.Sco.dll。仮想アカウント用の新しい SCO 検証が含まれます。</span><span class="sxs-lookup"><span data-stu-id="af9c1-137">**SCO** - Microsoft.SqlServer.Configuration.Sco.dll, including new SCO validations for virtual accounts</span></span>  
  
    -   <span data-ttu-id="af9c1-138">**Cluster**: Microsoft.SqlServer.Configuration.Cluster.dll</span><span class="sxs-lookup"><span data-stu-id="af9c1-138">**Cluster** - Microsoft.SqlServer.Configuration.Cluster.dll</span></span>  
  
    -   <span data-ttu-id="af9c1-139">**SFC**: Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span><span class="sxs-lookup"><span data-stu-id="af9c1-139">**SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span></span>  
  
    -   <span data-ttu-id="af9c1-140">**Extension**: Microsoft.SqlServer.Configuration.ConfigExtension.dll</span><span class="sxs-lookup"><span data-stu-id="af9c1-140">**Extension** - Microsoft.SqlServer.Configuration.ConfigExtension.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9c1-141">参照</span><span class="sxs-lookup"><span data-stu-id="af9c1-141">See Also</span></span>  
 <span data-ttu-id="af9c1-142">[定義済みロール](../../reporting-services/security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="af9c1-142">[Predefined Roles](../../reporting-services/security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="af9c1-143">[sp_addrolemember &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af9c1-143">[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span></span>  
 <span data-ttu-id="af9c1-144">[sp_droprolemember &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af9c1-144">[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span></span>  
 [<span data-ttu-id="af9c1-145">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="af9c1-145">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
