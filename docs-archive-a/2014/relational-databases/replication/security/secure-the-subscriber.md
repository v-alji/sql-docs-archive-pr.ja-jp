---
title: サブスクライバーのセキュリティ保護 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], security
- Subscribers [SQL Server replication], security
- security [SQL Server replication], Subscribers
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f03b9a202c3c49f147368460518a579f28dc850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643232"
---
# <a name="secure-the-subscriber"></a><span data-ttu-id="51712-102">サブスクライバーのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="51712-102">Secure the Subscriber</span></span>
  <span data-ttu-id="51712-103">マージ エージェントとディストリビューション エージェントはサブスクライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="51712-103">Merge Agents and Distribution Agents connect to the Subscriber.</span></span> <span data-ttu-id="51712-104">これらの接続は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインまたは Windows ログインのコンテキスト下で行われます。</span><span class="sxs-lookup"><span data-stu-id="51712-104">These connections can be made under the context of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login or a Windows login.</span></span> <span data-ttu-id="51712-105">最低限必要な権限のみを与え、かつ、すべてのパスワードの格納を保護するという原則に従って、これらの各エージェントに対し適切なログインを提供することが重要です。</span><span class="sxs-lookup"><span data-stu-id="51712-105">It is important to provide an appropriate login for these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords.</span></span> <span data-ttu-id="51712-106">各エージェントに必要な権限の詳細については、「 [Replication Agent Security Model](replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51712-106">For information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
## <a name="distribution-agent"></a><span data-ttu-id="51712-107">ディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="51712-107">Distribution Agent</span></span>  
 <span data-ttu-id="51712-108">サブスクリプションごとに 1 つのディストリビューション エージェント (パブリケーションの新規作成ウィザードで既定で作成される独立したエージェント)、またはパブリケーション データベースとサブスクリプション データベースのペアごとに 1 つのディストリビューション エージェント (共有エージェント) があります。</span><span class="sxs-lookup"><span data-stu-id="51712-108">There is either one Distribution Agent per subscription (an independent agent, the default for publications created in the New Publication Wizard) or one Distribution Agent per publication database and subscription database pair (a shared agent).</span></span> <span data-ttu-id="51712-109">T</span><span class="sxs-lookup"><span data-stu-id="51712-109">T</span></span>  
  
 <span data-ttu-id="51712-110">プッシュ サブスクリプションの接続情報を指定する場合は、「[プッシュ サブスクリプションの作成](../create-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51712-110">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="51712-111">プル サブスクリプションの接続情報を指定する場合は、「[プル サブスクリプションの作成](../create-a-pull-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51712-111">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md)</span></span>  
  
## <a name="merge-agent"></a><span data-ttu-id="51712-112">[マージ エージェント]</span><span class="sxs-lookup"><span data-stu-id="51712-112">Merge Agent</span></span>  
 <span data-ttu-id="51712-113">マージ サブスクリプションごとにマージ エージェントがあり、パブリッシャーとサブスクライバーの両方に接続し、更新します。</span><span class="sxs-lookup"><span data-stu-id="51712-113">Each merge subscription has its own Merge Agent that connects to and updates both the Publisher and the Subscriber.</span></span>  
  
 <span data-ttu-id="51712-114">プッシュ サブスクリプションの接続情報を指定する場合は、「[プッシュ サブスクリプションの作成](../create-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51712-114">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="51712-115">プル サブスクリプションの接続情報を指定する場合は、「[プル サブスクリプションの作成](../create-a-pull-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51712-115">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md).</span></span>  
  
## <a name="immediate-updating-subscriptions"></a><span data-ttu-id="51712-116">即時更新サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="51712-116">Immediate Updating Subscriptions</span></span>  
 <span data-ttu-id="51712-117">即時更新サブスクリプションを構成する場合は、パブリッシャーに接続する際のアカウントをサブスクライバーで指定します。</span><span class="sxs-lookup"><span data-stu-id="51712-117">When you configure an immediate updating subscription, you specify an account at the Subscriber under which connections to the Publisher are made.</span></span> <span data-ttu-id="51712-118">接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="51712-118">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="51712-119">接続の種類として、3 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="51712-119">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="51712-120">レプリケーションが作成するリンク サーバー。構成時に指定した資格情報を使用して接続が行われます。</span><span class="sxs-lookup"><span data-stu-id="51712-120">A linked server that replication creates; the connection is made with the credentials you specify at configuration time.</span></span>  
  
-   <span data-ttu-id="51712-121">レプリケーションによって作成されるリンク サーバー。サブスクライバーで変更を行うユーザーの資格情報を使用して接続を行います。</span><span class="sxs-lookup"><span data-stu-id="51712-121">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
-   <span data-ttu-id="51712-122">定義済みのリンク サーバーまたはリモート サーバー。</span><span class="sxs-lookup"><span data-stu-id="51712-122">A linked server or remote server that you have already defined.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51712-123">接続情報を指定する場合は、ストアド プロシージャ [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="51712-123">To specify connection information, use the stored procedure [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="51712-124">サブスクリプションの新規作成ウィザードの **[更新可能なサブスクリプション用のログイン]** を使用して、 **sp_link_publication**を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="51712-124">You can also use the **Login for Updatable Subscriptions** page of the New Subscription Wizard, which calls **sp_link_publication**.</span></span> <span data-ttu-id="51712-125">特定の条件下で、サブスクライバーが [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 以降を実行し、パブリッシャーがそれよりも前のバージョンを実行している場合、このストアド プロシージャは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="51712-125">Under certain conditions, this stored procedure can fail if the Subscriber is running [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) or later, and the Publisher is running an earlier version.</span></span> <span data-ttu-id="51712-126">このシナリオでストアド プロシージャが失敗する場合は、パブリッシャーを [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 以降にアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="51712-126">If the stored procedure fails in this scenario, upgrade the Publisher to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 or later.</span></span>  
  
 <span data-ttu-id="51712-127">詳細については、「[トランザクション パブリケーションの更新可能なサブスクリプションの作成](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)」および「[レプリケーションのセキュリティ設定の表示および変更](view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51712-127">For more information, see [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51712-128">接続用に指定するアカウントには、レプリケーションによってパブリケーション データベース内に作成されるビューのデータの挿入、更新、および削除だけを実行できる権限を与える必要があります。それ以外の権限は与えないでください。</span><span class="sxs-lookup"><span data-stu-id="51712-128">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="51712-129">各サブスクライバーで構成したアカウントに、**syncobj_** _\<HexadecimalNumber>_ の形式で名前が指定されたパブリケーション データベース内のビューに対する権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="51712-129">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
## <a name="queued-updating-subscriptions"></a><span data-ttu-id="51712-130">キュー更新サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="51712-130">Queued Updating Subscriptions</span></span>  
 <span data-ttu-id="51712-131">キュー更新サブスクリプションを構成する際には、セキュリティに関して、以下の 2 点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="51712-131">When you configure queued updating subscriptions, there are two areas to keep in mind that relate to security:</span></span>  
  
-   <span data-ttu-id="51712-132">各ディストリビューターには、キュー リーダー エージェントが 1 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="51712-132">There is only one Queue Reader Agent for each Distributor.</span></span> <span data-ttu-id="51712-133">ディストリビューターごとに、キュー更新サブスクリプションを有効にしたパブリケーションを 1 つだけ構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="51712-133">It is recommended that for each Distributor, you configure at most one publication that is enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="51712-134">キュー リーダー エージェントは、ディストリビューター、パブリッシャー、および各サブスクライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="51712-134">The Queue Reader agent makes connections to the Distributor, Publisher, and each Subscriber:</span></span>  
  
    -   <span data-ttu-id="51712-135">エージェントの実行とディストリビューターへの接続で使用するアカウントは、エージェントを作成する際に指定します (パブリケーションの新規作成ウィザードを使用する場合は、更新サブスクリプションを有効にしたパブリケーションを作成する際にエージェントが作成されます)。</span><span class="sxs-lookup"><span data-stu-id="51712-135">The account under which the agent runs and makes connections to the Distributor is specified when you create the agent (if you use the New Publication Wizard, the agent is created when you create a publication that is enabled for updating subscriptions).</span></span>  
  
    -   <span data-ttu-id="51712-136">エージェントがパブリッシャーに接続する際に使用するアカウントは、パブリッシャーのディストリビューションを構成する際に指定します。</span><span class="sxs-lookup"><span data-stu-id="51712-136">The account under which the agent makes connections to the Publisher is specified when you configure distribution for a Publisher.</span></span> <span data-ttu-id="51712-137">エージェントの実行で使用する Windows アカウントか [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントを指定してください。</span><span class="sxs-lookup"><span data-stu-id="51712-137">Specify the Windows account under which the agent runs or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account.</span></span>  
  
    -   <span data-ttu-id="51712-138">エージェントがサブスクライバーに接続する際に使用するアカウントは、サブスクリプションを作成する際に指定します。</span><span class="sxs-lookup"><span data-stu-id="51712-138">The account under which the agent makes connections to the Subscriber is specified when you create the subscription.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="51712-139">サブスクライバーへの接続には [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用し、各サブスクライバーへの接続にはそれぞれ異なるアカウントを指定してください。</span><span class="sxs-lookup"><span data-stu-id="51712-139">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication for connections to Subscribers, and specify a different account for the connection to each Subscriber.</span></span> <span data-ttu-id="51712-140">プル サブスクリプションを使用する場合は、レプリケーションによって、常に Windows 認証を使用するように接続が設定されます (プル サブスクリプションでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証が必要なサブスクライバーのメタデータにレプリケーションからアクセスすることはできません)。</span><span class="sxs-lookup"><span data-stu-id="51712-140">If you use a pull subscription, replication always sets the connection to use Windows Authentication (for pull subscriptions, replication cannot access metadata at the Subscriber required to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication).</span></span> <span data-ttu-id="51712-141">その場合、サブスクリプションを構成した後に、接続で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用するように変更してください。</span><span class="sxs-lookup"><span data-stu-id="51712-141">In this case, change the connection to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication after the subscription is configured.</span></span>  
  
     <span data-ttu-id="51712-142">詳細については、トランザクション パブリケーションに対して更新可能なサブスクリプションを作成する方法 (SQL Server Management Studio) および「[レプリケーションのセキュリティ設定の表示および変更](view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51712-142">For more information, see How to: Create an Updating Subscription to a Transactional Publication (SQL Server Management Studio) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51712-143">参照</span><span class="sxs-lookup"><span data-stu-id="51712-143">See Also</span></span>  
 <span data-ttu-id="51712-144">[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="51712-144">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="51712-145">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="51712-145">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="51712-146">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="51712-146">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
