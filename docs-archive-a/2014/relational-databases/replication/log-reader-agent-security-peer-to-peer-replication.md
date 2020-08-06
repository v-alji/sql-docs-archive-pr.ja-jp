---
title: '[ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dfef98adb622f9da922af0c1cdbb1cf8b7a07da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643255"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a><span data-ttu-id="f9e77-102">[ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="f9e77-102">Log Reader Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="f9e77-103">**[ログ リーダー エージェントのセキュリティ]** ページを使用すると、各ピアでログ リーダー エージェントが実行され、接続するときに使用されるアカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f9e77-103">The **Log Reader Agent Security** page allows you to specify the accounts under which the Log Reader Agent at each peer runs and makes connections.</span></span> <span data-ttu-id="f9e77-104">エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e77-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9e77-105">トランザクション レプリケーションを使用してパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントが存在します。</span><span class="sxs-lookup"><span data-stu-id="f9e77-105">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="f9e77-106">データベースにログ リーダー エージェントが既に設定されている場合 (このウィザードを以前に実行したときのパブリケーション、または同じデータベースにある他のトランザクション パブリケーションで)、使用されている資格情報をこのウィザードで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="f9e77-106">If the Log Reader Agent for a database has already been configured (either for a publication in a previous run of this wizard or for another transactional publication in the same database), you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="f9e77-107">新しい資格情報を指定した場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f9e77-107">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="f9e77-108">資格情報を変更するには、 **[パブリケーションのプロパティ]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e77-108">To change credentials, use the **Publication Properties** dialog box.</span></span> <span data-ttu-id="f9e77-109">詳細については、「 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e77-109">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9e77-110">Options</span><span class="sxs-lookup"><span data-stu-id="f9e77-110">Options</span></span>  
 <span data-ttu-id="f9e77-111">各ピアの行にあるプロパティ ボタン ( **[...]** ) をクリックすると、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f9e77-111">Click the properties button (**...**) in the row for each peer to access the **Log Reader Agent Security** dialog box.</span></span> <span data-ttu-id="f9e77-112">エージェントで使用されるアカウントに必要な権限の詳細については、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスを開いて **[ヘルプ]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="f9e77-112">Click **Help** on the **Log Reader Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="f9e77-113">このダイアログ ボックスに設定値を入力すると、サブスクライバーへの接続情報がグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9e77-113">After settings have been entered in the dialog box, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="f9e77-114">**[パブリッシャーのエージェント]**</span><span class="sxs-lookup"><span data-stu-id="f9e77-114">**Agents for Publisher**</span></span>  
 <span data-ttu-id="f9e77-115">各ピア サーバー インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="f9e77-115">The name of each peer server instance.</span></span>  
  
 <span data-ttu-id="f9e77-116">**[ピア データベース]**</span><span class="sxs-lookup"><span data-stu-id="f9e77-116">**Peer Database**</span></span>  
 <span data-ttu-id="f9e77-117">各ピアでパブリケーション データベースおよびサブスクリプション データベースとして機能するデータベースです。</span><span class="sxs-lookup"><span data-stu-id="f9e77-117">The database that serves as the publication database and subscription database at each peer.</span></span>  
  
 <span data-ttu-id="f9e77-118">**[ディストリビューターへの接続]**</span><span class="sxs-lookup"><span data-stu-id="f9e77-118">**Connection to Distributor**</span></span>  
 <span data-ttu-id="f9e77-119">ディストリビューターに接続するコンテキストを作成します。</span><span class="sxs-lookup"><span data-stu-id="f9e77-119">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="f9e77-120">ディストリビューターへのローカル接続は常に、エージェントの実行に使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用して作成されます。そのため、このフィールドには常に **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9e77-120">The local connection to the Distributor is always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs, so this field will always display **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="f9e77-121">**[パブリッシャーへの接続]**</span><span class="sxs-lookup"><span data-stu-id="f9e77-121">**Connection to Publisher**</span></span>  
 <span data-ttu-id="f9e77-122">パブリッシャーへの接続が作成されるときのコンテキストです。</span><span class="sxs-lookup"><span data-stu-id="f9e77-122">The context under which the connection to the Publisher is made.</span></span> <span data-ttu-id="f9e77-123">パブリッシャーへの接続は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用して、またはエージェントが実行される Windows アカウントのコンテキストを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="f9e77-123">The connection to the Publisher can be made using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="f9e77-124">このフィールドには、次のいずれかが表示されます。 **[ログイン '\<Login>' を使用する]** 、 **['\<Domain>\\<Login\>' の権限を借用する]** 、または **['\<Computer>\\<Login\>' の権限を借用する]** 。</span><span class="sxs-lookup"><span data-stu-id="f9e77-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="f9e77-125">では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f9e77-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e77-126">参照</span><span class="sxs-lookup"><span data-stu-id="f9e77-126">See Also</span></span>  
 <span data-ttu-id="f9e77-127">[ピア ツー ピア トポロジの管理 &#40;レプリケーション Transact-SQL プログラミング&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="f9e77-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="f9e77-128">ピア ツー ピア トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="f9e77-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
