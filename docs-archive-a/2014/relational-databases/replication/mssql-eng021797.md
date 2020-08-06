---
title: MSSQL_ENG021797 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021797 error
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d33ade7e7eea9fa9e95453a5b232447f7b222b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714174"
---
# <a name="mssql_eng021797"></a><span data-ttu-id="5743e-102">MSSQL_ENG021797</span><span class="sxs-lookup"><span data-stu-id="5743e-102">MSSQL_ENG021797</span></span>
    
## <a name="message-details"></a><span data-ttu-id="5743e-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="5743e-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5743e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5743e-104">Product Name</span></span>|<span data-ttu-id="5743e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5743e-105">SQL Server</span></span>|  
|<span data-ttu-id="5743e-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5743e-106">Event ID</span></span>|<span data-ttu-id="5743e-107">21797</span><span class="sxs-lookup"><span data-stu-id="5743e-107">21797</span></span>|  
|<span data-ttu-id="5743e-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5743e-108">Event Source</span></span>|<span data-ttu-id="5743e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5743e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5743e-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5743e-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="5743e-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5743e-111">Symbolic Name</span></span>||  
|<span data-ttu-id="5743e-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5743e-112">Message Text</span></span>|<span data-ttu-id="5743e-113">'%s' には 'MACHINE\Login' または 'DOMAIN\Login' の形式で有効な Windows ログインを指定してください。</span><span class="sxs-lookup"><span data-stu-id="5743e-113">'%s' must be a valid Windows Login in the form: 'MACHINE\Login' or 'DOMAIN\Login'.</span></span> <span data-ttu-id="5743e-114">'%s' については、マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5743e-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5743e-115">説明</span><span class="sxs-lookup"><span data-stu-id="5743e-115">Explanation</span></span>  
 <span data-ttu-id="5743e-116">このエラーは、パラメーターに指定された値が null または無効である場合に、次のレプリケーションストアドプロシージャによって発生 **@job_login** します。</span><span class="sxs-lookup"><span data-stu-id="5743e-116">This error is raised by the following replication stored procedures if the value specified for the **@job_login** parameter is null or not valid.</span></span> <span data-ttu-id="5743e-117">このエラーは、 **db_owner** 固定データベース ロールのメンバーが、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのスクリプトを実行すると発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5743e-117">This error can occur if a member of the **db_owner** fixed database role runs scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5743e-118">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ではセキュリティ モデルが変更されたため、これらのスクリプトは更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5743e-118">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   [<span data-ttu-id="5743e-119">sp_addlogreader_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-119">sp_addlogreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)  
  
-   [<span data-ttu-id="5743e-120">sp_addqreader_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-120">sp_addqreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql)  
  
-   [<span data-ttu-id="5743e-121">sp_addpublication_snapshot &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-121">sp_addpublication_snapshot &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)  
  
-   [<span data-ttu-id="5743e-122">sp_addpushsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-122">sp_addpushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="5743e-123">sp_addpullsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-123">sp_addpullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="5743e-124">sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-124">sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="5743e-125">sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-125">sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)  
  
 <span data-ttu-id="5743e-126">これらのストアド プロシージャは、適切なサーバー上の **sysadmin** 固定サーバー ロールのメンバー、または適切なデータベース内の **db_owner** 固定データベース ロールのメンバーにより実行されます。</span><span class="sxs-lookup"><span data-stu-id="5743e-126">These stored procedures can be executed by a member of the **sysadmin** fixed server role on the appropriate server or a member of the **db_owner** fixed database role in the appropriate database.</span></span> <span data-ttu-id="5743e-127">ストアド プロシージャはそれぞれエージェント ジョブを作成します。これにより、エージェントの実行に使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5743e-127">The stored procedures each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="5743e-128">**sysadmin** ロールのユーザーに対し、エージェント ジョブは、Windows アカウントが指定されていなくても (アカウントが指定されている場合、そのアカウントは有効である必要があります)、暗黙的に作成されます。エージェントは、適切なサーバーでの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのコンテキストの下で実行されます。</span><span class="sxs-lookup"><span data-stu-id="5743e-128">For users in the **sysadmin** role, agent jobs are created implicitly even if a Windows account is not specified (if an account is specified, it must be valid); agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the appropriate server.</span></span> <span data-ttu-id="5743e-129">アカウントは必要ありませんが、セキュリティ上、エージェントごとに異なるアカウントを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5743e-129">Although the account is not required, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="5743e-130">詳細については、「 [レプリケーション エージェント セキュリティ モデル](security/replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5743e-130">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5743e-131">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5743e-131">User Action</span></span>  
 <span data-ttu-id="5743e-132">各プロシージャのパラメーターに有効な Windows アカウントが指定されていることを確認してください **@job_login** 。</span><span class="sxs-lookup"><span data-stu-id="5743e-132">Ensure you specify a valid Windows account for the **@job_login** parameter of each procedure.</span></span> <span data-ttu-id="5743e-133">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのレプリケーション スクリプトがある場合は、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]に必要なストアド プロシージャやパラメーターをこれらのスクリプトに含めるように更新します。</span><span class="sxs-lookup"><span data-stu-id="5743e-133">If you have replication scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="5743e-134">詳細については、「[レプリケーション スクリプトのアップグレード &#40;レプリケーション Transact-SQL プログラミング&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5743e-134">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5743e-135">参照</span><span class="sxs-lookup"><span data-stu-id="5743e-135">See Also</span></span>  
 [<span data-ttu-id="5743e-136">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="5743e-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
