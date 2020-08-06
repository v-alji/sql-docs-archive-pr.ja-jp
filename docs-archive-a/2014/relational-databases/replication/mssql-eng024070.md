---
title: MSSQL_ENG024070 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fcfcb96b284d46d46f63af4a650f925ef2de73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714166"
---
# <a name="mssql_eng024070"></a><span data-ttu-id="348d6-102">MSSQL_ENG024070</span><span class="sxs-lookup"><span data-stu-id="348d6-102">MSSQL_ENG024070</span></span>
    
## <a name="message-details"></a><span data-ttu-id="348d6-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="348d6-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="348d6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="348d6-104">Product Name</span></span>|<span data-ttu-id="348d6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="348d6-105">SQL Server</span></span>|  
|<span data-ttu-id="348d6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="348d6-106">Event ID</span></span>|<span data-ttu-id="348d6-107">24070</span><span class="sxs-lookup"><span data-stu-id="348d6-107">24070</span></span>|  
|<span data-ttu-id="348d6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="348d6-108">Event Source</span></span>|<span data-ttu-id="348d6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="348d6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="348d6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="348d6-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="348d6-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="348d6-111">Symbolic Name</span></span>||  
|<span data-ttu-id="348d6-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="348d6-112">Message Text</span></span>|<span data-ttu-id="348d6-113">クライアントには必要な特権がありません。</span><span class="sxs-lookup"><span data-stu-id="348d6-113">A required privilege is not held by the client.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="348d6-114">説明</span><span class="sxs-lookup"><span data-stu-id="348d6-114">Explanation</span></span>  
 <span data-ttu-id="348d6-115">このエラーは、レプリケーションが使用されたかどうかにかかわらず発生する一般エラーです。</span><span class="sxs-lookup"><span data-stu-id="348d6-115">This is a general error that can be raised regardless of whether replication is being used.</span></span> <span data-ttu-id="348d6-116">一般に、レプリケーション トポロジ内のサーバーでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーではなく [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービス コントロール マネージャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントが変更された場合に、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="348d6-116">For a server in a replication topology, the error is typically raised because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account is changed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Service Control Manager instead of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="348d6-117">サービス アカウントの変更後にエージェント ジョブを実行しようとすると、次のようなエラー メッセージが表示されてジョブが失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="348d6-117">When you try to run an agent job after changing the service account, the job might fail with an error message that is similar to the following:</span></span>  
  
 <span data-ttu-id="348d6-118">"ユーザーとして実行されました: \<UserAccount> 。</span><span class="sxs-lookup"><span data-stu-id="348d6-118">"Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="348d6-119">レプリケーション-レプリケーションスナップショットサブシステム: エージェントが \<AgentName> 失敗しました。</span><span class="sxs-lookup"><span data-stu-id="348d6-119">Replication-Replication Snapshot Subsystem: agent \<AgentName> failed.</span></span> <span data-ttu-id="348d6-120">ユーザー \<UserAccount> として実行:</span><span class="sxs-lookup"><span data-stu-id="348d6-120">Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="348d6-121">クライアントには必要な特権がありません。</span><span class="sxs-lookup"><span data-stu-id="348d6-121">A required privilege is not held by the client.</span></span> <span data-ttu-id="348d6-122">ステップは失敗しました。</span><span class="sxs-lookup"><span data-stu-id="348d6-122">The step failed.</span></span> <span data-ttu-id="348d6-123">`[SQLSTATE 42000] (Error 14151)`.</span><span class="sxs-lookup"><span data-stu-id="348d6-123">`[SQLSTATE 42000] (Error 14151)`.</span></span> <span data-ttu-id="348d6-124">ステップは失敗しました。"</span><span class="sxs-lookup"><span data-stu-id="348d6-124">The step failed."</span></span>  
  
 <span data-ttu-id="348d6-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの新しいサービス アカウントに必要な権限を Windows サービス コントロール マネージャーが付与できないので、この問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="348d6-125">This problem occurs because the Windows Service Control Manager cannot grant the required permissions to the new service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="348d6-126">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="348d6-126">User Action</span></span>  
 <span data-ttu-id="348d6-127">今後この問題を回避するには、サービス アカウントおよびパスワードを変更する場合に、Windows サービス コントロール マネージャーではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを必ず使用してください。</span><span class="sxs-lookup"><span data-stu-id="348d6-127">To avoid this problem in the future, always use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager instead of the Windows Service Control Manager to change service accounts and passwords.</span></span>  
  
 <span data-ttu-id="348d6-128">この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、サービス アカウントを元のアカウントに戻します。</span><span class="sxs-lookup"><span data-stu-id="348d6-128">To resolve this problem, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change the service account back to the original account.</span></span> <span data-ttu-id="348d6-129">その後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、新しいアカウントに変更します。</span><span class="sxs-lookup"><span data-stu-id="348d6-129">Then, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change to the new account.</span></span> <span data-ttu-id="348d6-130">このとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、新しいアカウントを次のセキュリティ グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="348d6-130">When you do this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager adds the new account to the following security group:</span></span>  
  
 <span data-ttu-id="348d6-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span><span class="sxs-lookup"><span data-stu-id="348d6-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span></span>  
  
 <span data-ttu-id="348d6-132">このセキュリティ グループのメンバーになると、レプリケーション エージェント ジョブを実行するために必要な権限が新しいアカウントに付与されます。</span><span class="sxs-lookup"><span data-stu-id="348d6-132">Being a member of this security group grants to the new account the required permissions to run the replication agent job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348d6-133">参照</span><span class="sxs-lookup"><span data-stu-id="348d6-133">See Also</span></span>  
 <span data-ttu-id="348d6-134">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="348d6-134">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="348d6-135">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="348d6-135">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 [<span data-ttu-id="348d6-136">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="348d6-136">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
