---
title: '[ディストリビューション エージェント セキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72b5a52fbb3ddc11d0ea6f2c0b26786463e08eaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632383"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a><span data-ttu-id="1d58a-102">[ディストリビューション エージェント セキュリティ] (ピア ツー ピア レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="1d58a-102">Distribution Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="1d58a-103">**[ディストリビューション エージェント セキュリティ]** ページを使用すると、ディストリビューション エージェントを実行するアカウントの指定と、ピア ツー ピア テクノロジによるコンピューターへの接続の作成ができます。</span><span class="sxs-lookup"><span data-stu-id="1d58a-103">The **Distribution Agent Security** page allows you to specify the accounts under which the Distribution Agent runs and makes connections to the computers in a peer-to-peer topology.</span></span> <span data-ttu-id="1d58a-104">エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d58a-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d58a-105">サブスクリプションのディストリビューション エージェントが、このウィザードの以前の実行で既に構成されている場合、使用される資格情報をこのウィザードで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="1d58a-105">If the Distribution Agent for a subscription has already been configured in a previous run of this wizard, you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="1d58a-106">新しい資格情報を指定した場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1d58a-106">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="1d58a-107">資格情報を変更するには、 **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1d58a-107">To change credentials, use the **Subscription Properties** dialog box.</span></span> <span data-ttu-id="1d58a-108">詳細については、「 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d58a-108">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1d58a-109">Options</span><span class="sxs-lookup"><span data-stu-id="1d58a-109">Options</span></span>  
 <span data-ttu-id="1d58a-110">**[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスにアクセスするには、各サブスクライバーの行でプロパティ ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d58a-110">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** dialog box.</span></span> <span data-ttu-id="1d58a-111">**[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックすると、エージェントによって使用されるアカウントに必要な権限の詳細を参照できます。</span><span class="sxs-lookup"><span data-stu-id="1d58a-111">Click **Help** on the **Distribution Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="1d58a-112">ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d58a-112">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="1d58a-113">**[サブスクライバーのエージェント]**</span><span class="sxs-lookup"><span data-stu-id="1d58a-113">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="1d58a-114">各ピアの名前です。</span><span class="sxs-lookup"><span data-stu-id="1d58a-114">The name of each peer.</span></span>  
  
 <span data-ttu-id="1d58a-115">**[ピア データベース]**</span><span class="sxs-lookup"><span data-stu-id="1d58a-115">**Peer Database**</span></span>  
 <span data-ttu-id="1d58a-116">パブリケーション データ ベースとサブスクリプション データベースの両方に使用できるピアのデータベースです。</span><span class="sxs-lookup"><span data-stu-id="1d58a-116">The database at the peer that will serve as both a publication database and subscription database.</span></span>  
  
 <span data-ttu-id="1d58a-117">**[ディストリビューターへの接続]**</span><span class="sxs-lookup"><span data-stu-id="1d58a-117">**Connection to Distributor**</span></span>  
 <span data-ttu-id="1d58a-118">ディストリビューターに接続するコンテキストを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d58a-118">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="1d58a-119">ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="1d58a-119">Local connections are always made using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="1d58a-120">このウィザードではプッシュ サブスクリプションが作成されるため (ローカル接続はディストリビューターへの接続)、フィールドには常に以下が表示されます。 **['\<Domain>\\<Login\>' の権限を借用する]** 、または **['\<Computer>\\<Login\>' の権限を借用する]** 。</span><span class="sxs-lookup"><span data-stu-id="1d58a-120">This wizard creates push subscriptions (the local connection is the connection to the Distributor), so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="1d58a-121">**[サブスクライバーへの接続]**</span><span class="sxs-lookup"><span data-stu-id="1d58a-121">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="1d58a-122">サブスクライバーに接続するコンテキストを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d58a-122">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="1d58a-123">接続は、エージェントが実行する Windows アカウントのコンテキストの使用、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストによって作成できます。</span><span class="sxs-lookup"><span data-stu-id="1d58a-123">The connection can be made using the context of the Windows account under which the agent runs or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="1d58a-124">このフィールドには、次のいずれかが表示されます。 **[ログイン '\<Login>' を使用する]** 、 **['\<Domain>\\<Login\>' の権限を借用する]** 、または **['\<Computer>\\<Login\>' の権限を借用する]** 。</span><span class="sxs-lookup"><span data-stu-id="1d58a-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="1d58a-125">では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1d58a-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d58a-126">参照</span><span class="sxs-lookup"><span data-stu-id="1d58a-126">See Also</span></span>  
 <span data-ttu-id="1d58a-127">[ピア ツー ピア トポロジの管理 &#40;レプリケーション Transact-SQL プログラミング&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="1d58a-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="1d58a-128">ピア ツー ピア トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="1d58a-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
