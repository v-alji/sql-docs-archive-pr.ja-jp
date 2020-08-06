---
title: MSSQL_ENG021798 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 327b4a373c28376701ea12400215ab00367df66a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714170"
---
# <a name="mssql_eng021798"></a><span data-ttu-id="7ea8b-102">MSSQL_ENG021798</span><span class="sxs-lookup"><span data-stu-id="7ea8b-102">MSSQL_ENG021798</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7ea8b-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="7ea8b-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ea8b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7ea8b-104">Product Name</span></span>|<span data-ttu-id="7ea8b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ea8b-105">SQL Server</span></span>|  
|<span data-ttu-id="7ea8b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7ea8b-106">Event ID</span></span>|<span data-ttu-id="7ea8b-107">21798</span><span class="sxs-lookup"><span data-stu-id="7ea8b-107">21798</span></span>|  
|<span data-ttu-id="7ea8b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7ea8b-108">Event Source</span></span>|<span data-ttu-id="7ea8b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7ea8b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7ea8b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7ea8b-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7ea8b-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7ea8b-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7ea8b-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7ea8b-112">Message Text</span></span>|<span data-ttu-id="7ea8b-113">続行する前に、'%s' エージェント ジョブを '%s' から追加してください。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-113">The '%s' agent job must be added through '%s' before continuing.</span></span> <span data-ttu-id="7ea8b-114">'%s' については、マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7ea8b-115">説明</span><span class="sxs-lookup"><span data-stu-id="7ea8b-115">Explanation</span></span>  
 <span data-ttu-id="7ea8b-116">パブリケーションを作成するには、パブリッシャーの **sysadmin** 固定サーバー ロールのメンバーまたはパブリケーション データベースの **db_owner** 固定データベース ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-116">To create a publication, you must be a member of the **sysadmin** fixed server role on the Publisher or a member of the **db_owner** fixed database role in the publication database.</span></span> <span data-ttu-id="7ea8b-117">**db_owner** ロールのメンバーのときは、以下の場合にこのエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-117">If you are a member of the **db_owner** role, this error is raised if:</span></span>  
  
-   <span data-ttu-id="7ea8b-118">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]からスクリプトを実行する場合。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-118">You run scripts from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="7ea8b-119">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ではセキュリティ モデルが変更されたため、これらのスクリプトは更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-119">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   <span data-ttu-id="7ea8b-120">[sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) を実行する前に、ストアド プロシージャ **sp_addpublication** が実行される場合。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-120">The stored procedure **sp_addpublication** is executed before executing [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql).</span></span> <span data-ttu-id="7ea8b-121">これはすべてのトランザクション パブリケーションに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-121">This applies to all transactional publications.</span></span>  
  
-   <span data-ttu-id="7ea8b-122">[sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) を実行する前に、ストアド プロシージャ **sp_addpublication** が実行される場合。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-122">The stored procedure **sp_addpublication** is executed before executing [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql).</span></span> <span data-ttu-id="7ea8b-123">これは、キュー更新サブスクリプションに対して有効になっているトランザクションパブリケーションに適用され **@allow_queued_tran** ます ( **sp_addpublication**のパラメーターの値は TRUE です)。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-123">This applies to transactional publications that are enabled for queued updating subscriptions (a value of TRUE for the **@allow_queued_tran** parameter of **sp_addpublication**).</span></span>  
  
 <span data-ttu-id="7ea8b-124">ストアド プロシージャ **sp_addlogreader_agent** および **sp_addqreader_agent** は、それぞれエージェント ジョブを作成します。これにより、エージェントの実行に使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-124">The stored procedures **sp_addlogreader_agent** and **sp_addqreader_agent** each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="7ea8b-125">**sp_addlogreader_agent** および **sp_addqreader_agent** が実行されていない場合は、 **sysadmin** ロールのユーザーに対し、エージェント ジョブが暗黙的に作成されます。エージェントは、ディストリビューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-125">For users in the **sysadmin** role, agent jobs are created implicitly if **sp_addlogreader_agent** and **sp_addqreader_agent** are not executed; agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the Distributor.</span></span> <span data-ttu-id="7ea8b-126">**sysadmin** ロールでは、ユーザーは **sp_addlogreader_agent** および **sp_addqreader_agent** を必要としませんが、セキュリティ上、エージェントごとに異なるアカウントを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-126">Although **sp_addlogreader_agent** and **sp_addqreader_agent** are not required for users in the **sysadmin** role, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="7ea8b-127">詳細については、「 [レプリケーション エージェント セキュリティ モデル](security/replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-127">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7ea8b-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7ea8b-128">User Action</span></span>  
 <span data-ttu-id="7ea8b-129">正しい順序でプロシージャを実行してください。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-129">Ensure you execute procedures in the correct order.</span></span> <span data-ttu-id="7ea8b-130">詳細については、「[パブリケーションの作成](publish/create-a-publication.md)」を参照してください。以降のバージョンで必要なストアドプロシージャおよびパラメーターを含めるように、これらのスクリプトを更新してください [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-130">For more information, see [Create a Publication](publish/create-a-publication.md), update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="7ea8b-131">詳細については、「[レプリケーション スクリプトのアップグレード &#40;レプリケーション Transact-SQL プログラミング&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea8b-131">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea8b-132">参照</span><span class="sxs-lookup"><span data-stu-id="7ea8b-132">See Also</span></span>  
 [<span data-ttu-id="7ea8b-133">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="7ea8b-133">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
