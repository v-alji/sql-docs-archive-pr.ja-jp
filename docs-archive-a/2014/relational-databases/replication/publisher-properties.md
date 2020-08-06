---
title: SQL Server レプリケーションパブリッシャーのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
- sql12.rep.configdistwizard.pubproperties.general.f1
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
- sql12.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e14f82e855cc29f83859d85dfdaaf85a1bda37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716253"
---
# <a name="sql-server-replication-publisher-properties"></a><span data-ttu-id="9df1e-102">SQL Server レプリケーションパブリッシャーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="9df1e-102">SQL Server Replication Publisher Properties</span></span>
  <span data-ttu-id="9df1e-103">ここでは、ディストリビューターおよびパブリッシャーで使用できるパブリッシャープロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-103">This section contains information on Publisher properties available at the Distributor and the Publisher.</span></span> 

## <a name="general"></a><span data-ttu-id="9df1e-104">全般</span><span class="sxs-lookup"><span data-stu-id="9df1e-104">General</span></span>  
  <span data-ttu-id="9df1e-105">**[パブリッシャーのプロパティ]** ダイアログ ボックスの **[全般]** ページでは、パブリッシャーが使用するディストリビューターおよびディストリビューション データベースの読み取り専用情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-105">The **General** page of the **Publisher Properties** dialog box displays read-only information on the Distributor and distribution database that the Publisher uses.</span></span> <span data-ttu-id="9df1e-106">パブリッシャーのディストリビューターまたはディストリビューション データベースを変更するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9df1e-106">To change the Distributor or distribution database for a Publisher:</span></span>  
  
1.  <span data-ttu-id="9df1e-107">パブリッシャーでのパブリッシングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9df1e-107">Disable publishing on the Publisher.</span></span> <span data-ttu-id="9df1e-108">詳細については、「[パブリッシングの無効化と配布](disable-publishing-and-distribution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9df1e-108">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>    
2.  <span data-ttu-id="9df1e-109">パブリッシングおよびディストリビューションを再構成します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-109">Reconfigure publishing and distribution.</span></span> <span data-ttu-id="9df1e-110">詳細については、「 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="9df1e-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  

## <a name="distributor"></a><span data-ttu-id="9df1e-111">ディストリビューター</span><span class="sxs-lookup"><span data-stu-id="9df1e-111">Distributor</span></span>
  <span data-ttu-id="9df1e-112">**[パブリッシャーのプロパティ]** ダイアログ ボックスを使用すると、パブリッシャーとそのディストリビューター間のリレーションシップに関連するプロパティの表示と修正を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9df1e-112">The **Publisher Properties** dialog box allows you to view and modify properties associated with the relationship between the Publisher and its Distributor.</span></span>  
  
### <a name="options"></a><span data-ttu-id="9df1e-113">Options</span><span class="sxs-lookup"><span data-stu-id="9df1e-113">Options</span></span>  
 <span data-ttu-id="9df1e-114">**[パブリッシャーへのエージェント接続]**</span><span class="sxs-lookup"><span data-stu-id="9df1e-114">**Agent Connection to the Publisher**</span></span>  
 <span data-ttu-id="9df1e-115">次のエージェントがディストリビューターからパブリッシャーへの接続を確立するためのコンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-115">Specify the context under which the following agents make connections from the Distributor to the Publisher:</span></span>  
  
-   <span data-ttu-id="9df1e-116">キュー リーダー エージェント (キュー更新サブスクリプションを許可するトランザクション パブリケーション用)</span><span class="sxs-lookup"><span data-stu-id="9df1e-116">The Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="9df1e-117">スナップショット エージェントとログ リーダー エージェント (Oracle パブリケーション用)</span><span class="sxs-lookup"><span data-stu-id="9df1e-117">The Snapshot Agent and Log Reader Agent for Oracle publications.</span></span>  
  
 <span data-ttu-id="9df1e-118">**[エージェント プロセス アカウントを借用する]** を選択して、これらのエージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してパブリッシャーへの接続を作成するか、 **[SQL Server 認証]** を指定して、 **[ログイン]** と **[パスワード]** に値を入力します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-118">Select **Impersonate agent process account** to make connections to the Publisher using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which these agents run, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> <span data-ttu-id="9df1e-119">**[エージェント プロセス アカウントを借用する]** を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9df1e-119">It is recommended that you select **Impersonate agent process account**.</span></span> <span data-ttu-id="9df1e-120">エージェントのセキュリティの詳細については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9df1e-120">For more information on agent security, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="9df1e-121">これらのエージェントを実行する Windows アカウントは、パブリケーションの新規作成ウィザードで指定します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-121">The Windows accounts under which these agents run are specified in the New Publication Wizard.</span></span> <span data-ttu-id="9df1e-122">これらのアカウントは次のダイアログ ボックスで変更できます。</span><span class="sxs-lookup"><span data-stu-id="9df1e-122">These accounts can be changed:</span></span>  
  
-   <span data-ttu-id="9df1e-123">**[ディストリビューターのプロパティ]** ダイアログ ボックス (キュー リーダー エージェント)</span><span class="sxs-lookup"><span data-stu-id="9df1e-123">In the **Distributor Properties** dialog box for the Queue Reader Agent.</span></span>  
  
-   <span data-ttu-id="9df1e-124">**[パブリケーションのプロパティ]** ダイアログ ボックス (スナップショット エージェントとログ リーダー エージェント)</span><span class="sxs-lookup"><span data-stu-id="9df1e-124">In the **Publication Properties** dialog box for the Snapshot Agent and Log Reader Agent.</span></span>  
  
 <span data-ttu-id="9df1e-125">**その他**</span><span class="sxs-lookup"><span data-stu-id="9df1e-125">**Miscellaneous**</span></span>  
 <span data-ttu-id="9df1e-126">**[パブリッシャーの種類]** プロパティと **[ディストリビューション データベース名]** プロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="9df1e-126">The properties **Publisher Type** and **Distribution Database Name** are read-only.</span></span> <span data-ttu-id="9df1e-127">**[既定のスナップショット フォルダー]** プロパティは変更できます。</span><span class="sxs-lookup"><span data-stu-id="9df1e-127">The property **Default Snapshot Folder** can be changed.</span></span> <span data-ttu-id="9df1e-128">スナップショット フォルダーの詳細については、「[スナップショット フォルダーのセキュリティ保護](security/secure-the-snapshot-folder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9df1e-128">For more information about the snapshot folder, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  

## <a name="publication-databases"></a><span data-ttu-id="9df1e-129">パブリケーション データベース</span><span class="sxs-lookup"><span data-stu-id="9df1e-129">Publication Databases</span></span>
  <span data-ttu-id="9df1e-130">**[パブリッシャーのプロパティ]** ダイアログ ボックスの **[パブリケーション データベース]** ページを使用すると、**sysadmin** 固定サーバー ロール内のユーザーはデータベースをレプリケーションに対して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9df1e-130">The **Publication Databases** page of the **Publisher Properties** dialog box allows a user in the **sysadmin** fixed server role to enable databases for replication.</span></span> <span data-ttu-id="9df1e-131">データベースを有効にした場合、データベースはパブリッシュされませんが、そのデータベースの **db_owner** 固定データベース ロール内のすべてのユーザーが 1 つ以上のパブリケーションをデータベース上で作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9df1e-131">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications on the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="9df1e-132">Options</span><span class="sxs-lookup"><span data-stu-id="9df1e-132">Options</span></span>  
 <span data-ttu-id="9df1e-133">**トランザクション**</span><span class="sxs-lookup"><span data-stu-id="9df1e-133">**Transactional**</span></span>  
 <span data-ttu-id="9df1e-134">このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、スナップショット パブリケーションまたはトランザクション パブリケーションをそのデータベースに作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9df1e-134">Select this check box to allow users in the **db_owner** fixed database role to create snapshot publications or transactional publications in the database.</span></span> 
  
 <span data-ttu-id="9df1e-135">**[マージ]**</span><span class="sxs-lookup"><span data-stu-id="9df1e-135">**Merge**</span></span>  
 <span data-ttu-id="9df1e-136">このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、マージ パブリケーションをそのデータベースに作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9df1e-136">Select this check box to allow users in the **db_owner** fixed database role to create merge publications in the database.</span></span>  

## <a name="subscribers"></a><span data-ttu-id="9df1e-137">[サブスクライバー]</span><span class="sxs-lookup"><span data-stu-id="9df1e-137">Subscribers</span></span>

  <span data-ttu-id="9df1e-138">**[パブリッシャーのプロパティ]** ダイアログ ボックスの **[サブスクライバー]** ページは、 以前の [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されているパブリッシャーで使用します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-138">The **Subscribers** page of the **Publisher Properties** dialog box is used for Publishers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="9df1e-139">このページを使用すると、サブスクライバーがこのパブリッシャー上のパブリケーションからデータを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9df1e-139">The page allows you to enable Subscribers to receive data from publications on this Publisher.</span></span> <span data-ttu-id="9df1e-140">サブスクライバーがこのパブリッシャーからデータを受け取るだけでは、このパブリッシャー上のパブリケーションへのサブスクリプションは作成できません。</span><span class="sxs-lookup"><span data-stu-id="9df1e-140">Enabling a Subscriber to receive data from this Publisher does not create subscriptions to publications on this Publisher.</span></span> <span data-ttu-id="9df1e-141">サブスクリプションを作成するには、サブスクリプションの新規作成ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9df1e-141">To create a subscription, you must use the New Subscription Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="9df1e-142">Options</span><span class="sxs-lookup"><span data-stu-id="9df1e-142">Options</span></span>  
 <span data-ttu-id="9df1e-143">**[サブスクライバー]**</span><span class="sxs-lookup"><span data-stu-id="9df1e-143">**Subscribers**</span></span>  
 <span data-ttu-id="9df1e-144">**[サブスクライバー]** プロパティ グリッドには、このパブリッシャー上のパブリケーションからデータを受け取るように設定されているサブスクライバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9df1e-144">The **Subscribers** property grid shows Subscribers that are enabled to receive data from publications on this Publisher.</span></span> <span data-ttu-id="9df1e-145">その他のプロパティを表示し、設定するには、サブスクライバーの横にあるプロパティ ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9df1e-145">Click the properties button (**...**) next to a Subscriber to view and set additional properties.</span></span>  
  
 <span data-ttu-id="9df1e-146">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="9df1e-146">**Add**</span></span>  
 <span data-ttu-id="9df1e-147">サブスクライバーを追加するには、 **[追加]** をクリックしてから、 **[SQL Server サブスクライバーの追加]** または **[SQL Server 以外のサブスクライバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9df1e-147">Click **Add** to add a Subscriber, and then click **Add SQL Server Subscriber** or **Add Non-SQL Server Subscriber**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="9df1e-148">参照</span><span class="sxs-lookup"><span data-stu-id="9df1e-148">See Also</span></span>  
 [<span data-ttu-id="9df1e-149">ディストリビューターとパブリッシャーのプロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="9df1e-149">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
