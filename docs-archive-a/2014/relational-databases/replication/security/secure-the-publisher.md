---
title: パブリッシャーのセキュリティ保護 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- Publishers [SQL Server replication], security
- publications [SQL Server replication], security
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dca3f704c43a97c2c34921007341b9bd613676ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643236"
---
# <a name="secure-the-publisher"></a><span data-ttu-id="99e48-102">パブリッシャーのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="99e48-102">Secure the Publisher</span></span>
  <span data-ttu-id="99e48-103">次のレプリケーション エージェントはパブリッシャーに接続します。</span><span class="sxs-lookup"><span data-stu-id="99e48-103">The following replication agents connect to the Publisher:</span></span>  
  
-   <span data-ttu-id="99e48-104">ログ リーダー エージェント (Log Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="99e48-104">Log Reader Agent</span></span>  
  
-   <span data-ttu-id="99e48-105">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="99e48-105">Snapshot Agent</span></span>  
  
-   <span data-ttu-id="99e48-106">キュー リーダー エージェント (Queue Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="99e48-106">Queue Reader Agent</span></span>  
  
-   <span data-ttu-id="99e48-107">[マージ エージェント]</span><span class="sxs-lookup"><span data-stu-id="99e48-107">Merge Agent</span></span>  
  
 <span data-ttu-id="99e48-108">最低限必要な権限のみを与え、かつ、すべてのパスワードの格納を保護するという原則に従って、これらの各エージェントに対し適切なログインを提供することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="99e48-108">We recommend that you provide an appropriate login for these agents, follow the principle of granting the minimal rights that are required, and protect the storage of all passwords.</span></span> <span data-ttu-id="99e48-109">各エージェントに必要な権限の詳細については、「 [Replication Agent Security Model](replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e48-109">For information about the permissions that are required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="99e48-110">ログインとパスワードの適切な管理以外にも、パブリケーション アクセス リスト (PAL) の役割を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e48-110">Besides appropriately managing logins and passwords, you should understand the role of the publication access list (PAL).</span></span> <span data-ttu-id="99e48-111">PAL は、パブリッシャーのデータベースへのアドホック アクセスを制限すると同時に、ログインしてパブリケーション データへのアクセスを可能にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="99e48-111">The PAL is used to enable logins to access to publication data while restricting ad hoc access to the database at the Publisher.</span></span>  
  
## <a name="publication-access-list"></a><span data-ttu-id="99e48-112">パブリケーション アクセス リスト</span><span class="sxs-lookup"><span data-stu-id="99e48-112">Publication Access List</span></span>  
 <span data-ttu-id="99e48-113">PAL は、パブリッシャーでパブリケーションの安全を確保する主要なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="99e48-113">The PAL is the primary mechanism for securing publications at the Publisher.</span></span> <span data-ttu-id="99e48-114">PAL は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のアクセス制御リストによく似た機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="99e48-114">The PAL functions similarly to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows access control list.</span></span> <span data-ttu-id="99e48-115">パブリケーションを作成すると、レプリケーションによってそのパブリケーションから PAL が作成されます。</span><span class="sxs-lookup"><span data-stu-id="99e48-115">When you create a publication, replication creates a PAL for the publication.</span></span> <span data-ttu-id="99e48-116">PAL は、パブリケーションへのアクセスを許可されているログインとグループのリストを含めるように構成できます。</span><span class="sxs-lookup"><span data-stu-id="99e48-116">The PAL can be configured to contain a list of logins and groups that are granted access to the publication.</span></span> <span data-ttu-id="99e48-117">エージェントがパブリッシャーまたはディストリビューターに接続し、パブリケーションへのアクセスを要求すると、PAL 内の認証情報が、エージェントによって提供されるパブリッシャー ログインと比較されます。</span><span class="sxs-lookup"><span data-stu-id="99e48-117">When an agent connects to the Publisher or Distributor and requests access to a publication, the authentication information in the PAL is compared to the Publisher login that the agent provides.</span></span> <span data-ttu-id="99e48-118">このプロセスでは、クライアント ツールがパブリッシャーとディストリビューターのログインを使用してパブリッシャー側で直接変更を行う危険性を回避できるので、パブリッシャーのセキュリティを向上できます。</span><span class="sxs-lookup"><span data-stu-id="99e48-118">This process provides additional security for the Publisher by preventing the Publisher and Distributor login from being used by a client tool to perform modifications on the Publisher directly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99e48-119">PAL のメンバーに含めるため、レプリケーションによって、各パブリケーションに対してパブリッシャー上にロールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="99e48-119">Replication creates a role on the Publisher for each publication to enforce PAL membership.</span></span> <span data-ttu-id="99e48-120">ロールには、マージ レプリケーションの場合は **Msmerge_** _\<PublicationID>_ という形式、トランザクション レプリケーションとスナップショット レプリケーションの場合は **MSReplPAL_** _\<PublicationDatabaseID>_ **_** _\<PublicationID>_ という形式で名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="99e48-120">The role has a name in the form **Msmerge_**_\<PublicationID>_ for merge replication and **MSReplPAL_**_\<PublicationDatabaseID>_**_**_\<PublicationID>_ for transactional and snapshot replication.</span></span>  
  
 <span data-ttu-id="99e48-121">既定で PAL に含まれるログインは、パブリケーションが作成された時点の **sysadmin** 固定サーバー ロールのメンバー、およびパブリケーションを作成するために使用されるログインです。</span><span class="sxs-lookup"><span data-stu-id="99e48-121">By default, the following logins are included in the PAL: the members of the **sysadmin** fixed server role at the time the publication is created and the login that is used to create the publication.</span></span> <span data-ttu-id="99e48-122">既定で、パブリケーション データベース上の **sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーであるすべてのログインは、明示的に PAL に追加しなくても、パブリケーションに対してサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="99e48-122">By default, all logins that are members of the **sysadmin** fixed server role or the **db_owner** fixed database role on the publication database can subscribe to a publication without being explicitly added to the PAL.</span></span>  
  
 <span data-ttu-id="99e48-123">PAL を使用する場合は、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="99e48-123">When you are using the PAL, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="99e48-124">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインを PAL に追加する前に、そのログインをパブリケーション データベースのデータベース ユーザーに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e48-124">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before adding the login to the PAL.</span></span>  
  
-   <span data-ttu-id="99e48-125">最小特権の原則に従って、PAL 内のログインに、レプリケーション タスクを実行するために必要な権限のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="99e48-125">Follow the principle of least privilege by allowing logins in the PAL only the permissions the logins must have to perform replication tasks.</span></span> <span data-ttu-id="99e48-126">レプリケーションに必要のない固定データベース ロールやサーバー ロールに、ログインを追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="99e48-126">Do not add the logins to any fixed database roles or server roles that are not required for replication.</span></span> <span data-ttu-id="99e48-127">必要な権限の詳細については、「 [Replication Agent Security Model](replication-agent-security-model.md) 」および「 [Replication Security Best Practices](replication-security-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e48-127">For more information about the permissions that are required, see [Replication Agent Security Model](replication-agent-security-model.md) and [Replication Security Best Practices](replication-security-best-practices.md).</span></span>  
  
-   <span data-ttu-id="99e48-128">リモート ディストリビューターを使用する場合、PAL 内のアカウントは、パブリッシャーとディストリビューターの両方で使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e48-128">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="99e48-129">このアカウントは、どちらのサーバーでも定義されているドメイン アカウントまたはローカル アカウントにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e48-129">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="99e48-130">両方のログインに関連付けられているパスワードは、同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e48-130">The passwords associated with both logins must be the same.</span></span>  
  
-   <span data-ttu-id="99e48-131">PAL に Windows アカウントが含まれており、ドメインで Active Directory が使用されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行する際に使用するアカウントが Active Directory から読み取りを行う権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e48-131">If the PAL contains Windows accounts and the domain uses Active Directory, the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs must have permissions to read from Active Directory.</span></span> <span data-ttu-id="99e48-132">Windows アカウントに関する問題が発生した場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行する際に使用するアカウントが十分な権限を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="99e48-132">If you experience issues with Windows accounts, make sure that the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs has sufficient permissions.</span></span> <span data-ttu-id="99e48-133">詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e48-133">For more information, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="99e48-134">PAL を管理する場合は、「[パブリケーション アクセス リストのログインの管理](manage-logins-in-the-publication-access-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e48-134">To manage the PAL, see [Manage Logins in the Publication Access List](manage-logins-in-the-publication-access-list.md).</span></span>  
  
## <a name="snapshot-agent"></a><span data-ttu-id="99e48-135">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="99e48-135">Snapshot Agent</span></span>  
 <span data-ttu-id="99e48-136">パブリケーションごとに 1 つのスナップショット エージェントがあります。</span><span class="sxs-lookup"><span data-stu-id="99e48-136">There is one Snapshot Agent for each publication.</span></span> <span data-ttu-id="99e48-137">詳しくは、「 [パブリケーションを作成](../publish/create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99e48-137">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="ftp-snapshot-delivery"></a><span data-ttu-id="99e48-138">FTP スナップショット配信</span><span class="sxs-lookup"><span data-stu-id="99e48-138">FTP Snapshot Delivery</span></span>  
 <span data-ttu-id="99e48-139">UNC 共有ではなく FTP 共有によりスナップショットを使用できるように指定する場合、FTP アクセスの構成時にログインおよびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e48-139">If you specify that snapshots should be made available through an FTP share rather than a UNC share, you must specify a login and password when configuring FTP access.</span></span> <span data-ttu-id="99e48-140">詳細については、「[FTP でのスナップショットの配信](../publish/deliver-a-snapshot-through-ftp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e48-140">For more information, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
## <a name="log-reader-agent"></a><span data-ttu-id="99e48-141">ログ リーダー エージェント (Log Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="99e48-141">Log Reader Agent</span></span>  
 <span data-ttu-id="99e48-142">トランザクション レプリケーション用にパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントがあります。</span><span class="sxs-lookup"><span data-stu-id="99e48-142">There is one Log Reader Agent for each database published for transactional replication.</span></span> <span data-ttu-id="99e48-143">詳しくは、「 [パブリケーションを作成](../publish/create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99e48-143">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="queue-reader-agent"></a><span data-ttu-id="99e48-144">キュー リーダー エージェント (Queue Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="99e48-144">Queue Reader Agent</span></span>  
 <span data-ttu-id="99e48-145">あるディストリビューターに関連付けられたすべてのパブリッシャーおよびパブリケーション (キュー更新サブスクリプションを許可するパブリケーション) に対し、1 つのキュー リーダー エージェントがあります。</span><span class="sxs-lookup"><span data-stu-id="99e48-145">There is one Queue Reader Agent for all Publishers and publications (that allow queued updating subscriptions) associated with a given Distributor.</span></span> <span data-ttu-id="99e48-146">詳細については、「[トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../publish/enable-updating-subscriptions-for-transactional-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e48-146">For more information, see [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e48-147">参照</span><span class="sxs-lookup"><span data-stu-id="99e48-147">See Also</span></span>  
 <span data-ttu-id="99e48-148">[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="99e48-148">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="99e48-149">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="99e48-149">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="99e48-150">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="99e48-150">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
