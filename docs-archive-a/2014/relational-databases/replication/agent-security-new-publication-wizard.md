---
title: '[エージェント セキュリティ] (パブリケーションの新規作成ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a0da30cb49a73024ca83d8587a4f6477d21c49c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634420"
---
# <a name="agent-security-new-publication-wizard"></a><span data-ttu-id="be16d-102">[エージェント セキュリティ] (パブリケーションの新規作成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="be16d-102">Agent Security (New Publication Wizard)</span></span>
  <span data-ttu-id="be16d-103">**[エージェント セキュリティ]** ページを使用すると、次のエージェントを実行したり、レプリケーション トポロジ内のコンピューターに接続したりする際のアカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="be16d-103">The **Agent Security** page allows you to specify the accounts under which the following agents run and make connections to the computers in a replication topology:</span></span>  
  
-   <span data-ttu-id="be16d-104">すべてのパブリケーションに対応する、スナップショット エージェント。</span><span class="sxs-lookup"><span data-stu-id="be16d-104">The Snapshot Agent for all publications.</span></span>  
  
-   <span data-ttu-id="be16d-105">すべてのトランザクション パブリケーションに対応する、ログ リーダー エージェント。</span><span class="sxs-lookup"><span data-stu-id="be16d-105">The Log Reader Agent for all transactional publications.</span></span>  
  
-   <span data-ttu-id="be16d-106">更新可能なサブスクリプションを許容するトランザクション パブリケーションに対応する、キュー リーダー エージェント。</span><span class="sxs-lookup"><span data-stu-id="be16d-106">The Queue Reader Agent for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="be16d-107">**[パブリケーションの種類]** ページで **[更新可能なサブスクリプションを含むトランザクション パブリケーション]** を指定した場合、使用する更新可能なサブスクリプションの種類に関係なく、このエージェント向けの [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブが作成されます。</span><span class="sxs-lookup"><span data-stu-id="be16d-107">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job for this agent is created if you specified **Transactional publication with updatable subscriptions** on the **Publication Type** page, regardless of the type of updatable subscriptions you use.</span></span> <span data-ttu-id="be16d-108">更新可能なサブスクリプションの詳細については、「 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be16d-108">For more information about updatable subscriptions, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="be16d-109">エージェントで必要とされる権限と、レプリケーションのセキュリティに関する推奨事項については、「 [Replication Agent Security Model](security/replication-agent-security-model.md) 」および「 [Replication Security Best Practices](security/replication-security-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be16d-109">For information about permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="be16d-110">Options</span><span class="sxs-lookup"><span data-stu-id="be16d-110">Options</span></span>  
 <span data-ttu-id="be16d-111">**スナップショット エージェント**</span><span class="sxs-lookup"><span data-stu-id="be16d-111">**Snapshot Agent**</span></span>  
 <span data-ttu-id="be16d-112">すべてのパブリケーションで表示されます。</span><span class="sxs-lookup"><span data-stu-id="be16d-112">Displayed for all publications.</span></span> <span data-ttu-id="be16d-113">**[セキュリティ設定]** をクリックすると、 **[スナップショット エージェントのセキュリティ]** ダイアログ ボックスでセキュリティ設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="be16d-113">Click **Security Settings** to specify security settings in the **Snapshot Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="be16d-114">スナップショット エージェントで使用されるアカウントに必要な権限の詳細については、 **[スナップショット エージェントのセキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="be16d-114">Click **Help** on the **Snapshot Agent Security** dialog box for more information about the permissions required for accounts used by the Snapshot Agent.</span></span>  
  
 <span data-ttu-id="be16d-115">**ログ リーダー エージェント**</span><span class="sxs-lookup"><span data-stu-id="be16d-115">**Log Reader Agent**</span></span>  
 <span data-ttu-id="be16d-116">すべてのトランザクション パブリケーションで表示されます。</span><span class="sxs-lookup"><span data-stu-id="be16d-116">Displayed for all transactional publications.</span></span> <span data-ttu-id="be16d-117">**[セキュリティ設定]** をクリックすると、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスでセキュリティ設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="be16d-117">Click **Security Settings** to specify security settings in the **Log Reader Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="be16d-118">ログ リーダー エージェントで使用されるアカウントに必要な権限の詳細については、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="be16d-118">Click **Help** on the **Log Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Log Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be16d-119">トランザクション レプリケーションを使用してパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントが存在します。</span><span class="sxs-lookup"><span data-stu-id="be16d-119">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="be16d-120">データベースにトランザクション パブリケーションが既に存在している場合、セキュリティ設定は読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="be16d-120">If a transactional publication already exists in the database, the security settings are read-only.</span></span> <span data-ttu-id="be16d-121">セキュリティ設定は **[パブリケーションのプロパティ]** ダイアログ ボックスを使用して変更できますが、この変更はデータベース内のすべてのトランザクション パブリケーションに反映されます。</span><span class="sxs-lookup"><span data-stu-id="be16d-121">You can change the settings in the **Publication Properties** dialog box, but changes affect all transactional publications in the database.</span></span>  
  
 <span data-ttu-id="be16d-122">**キュー リーダー エージェント**</span><span class="sxs-lookup"><span data-stu-id="be16d-122">**Queue Reader Agent**</span></span>  
 <span data-ttu-id="be16d-123">更新可能なサブスクリプションを許容するトランザクション パブリケーションで表示されます。</span><span class="sxs-lookup"><span data-stu-id="be16d-123">Displayed for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="be16d-124">**[セキュリティ設定]** をクリックすると、 **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスでセキュリティ設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="be16d-124">Click **Security Settings** to specify security settings in the **Queue Reader Agent Security** dialog box.</span></span> <span data-ttu-id="be16d-125">このウィザードが完了すると、キュー更新サブスクリプションを作成するかどうかには関係なく、キュー リーダー エージェント ジョブが作成されます。</span><span class="sxs-lookup"><span data-stu-id="be16d-125">A Queue Reader Agent job is created when this wizard completes; it does not depend on you creating any queued updating subscriptions.</span></span> <span data-ttu-id="be16d-126">キュー更新サブスクリプションを作成しない場合には、このジョブを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="be16d-126">If you do not plan to create any queued updating subscriptions, you can disable the job.</span></span> <span data-ttu-id="be16d-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの **[ジョブ]** フォルダーで、ジョブ ( *[\<Publisher>].\<integer>* . という名前になります) を右クリックし、 **[無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be16d-127">Right-click the job (named in the form: *[\<Publisher>].\<integer>*.) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **Jobs** folder, and then click **Disable**.</span></span>  
  
 <span data-ttu-id="be16d-128">キュー リーダー エージェントで使用されるアカウントに必要な権限の詳細については、 **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="be16d-128">Click **Help** on the **Queue Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Queue Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be16d-129">ディストリビューション データベース (および、それを使用するすべてのパブリッシャー) には、それぞれに対応するキュー リーダー エージェントが 1 つずつ存在します。</span><span class="sxs-lookup"><span data-stu-id="be16d-129">There is one Queue Reader Agent for each distribution database (and all Publishers that it serves).</span></span> <span data-ttu-id="be16d-130">指定されたディストリビューション データベースを使用するパブリッシャーのいずれかに、キュー更新サブスクリプションを許容するトランザクション パブリケーションが既に存在する場合、セキュリティ設定は読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="be16d-130">If a transactional publication that allows queued updating subscriptions already exists on any of the Publishers that use a given distribution database, the security settings are read-only.</span></span> <span data-ttu-id="be16d-131">**[ディストリビューターのプロパティ]** ダイアログ ボックスで、キュー リーダー エージェントの実行と接続に使用されるアカウントを変更できますが、この変更はディストリビューション データベースを使用するすべてのパブリッシャーのパブリケーションに反映されます。</span><span class="sxs-lookup"><span data-stu-id="be16d-131">You can change the account under which the Queue Reader Agent runs and makes connections in the **Distributor Properties** dialog box, but changes affect publications at all Publishers that use the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be16d-132">参照</span><span class="sxs-lookup"><span data-stu-id="be16d-132">See Also</span></span>  
 <span data-ttu-id="be16d-133">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="be16d-133">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="be16d-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="be16d-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="be16d-135">[View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="be16d-135">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 <span data-ttu-id="be16d-136">[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="be16d-136">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="be16d-137">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="be16d-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="be16d-138">[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="be16d-138">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="be16d-139">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="be16d-139">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
