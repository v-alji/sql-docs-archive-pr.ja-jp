---
title: ディストリビューターのプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
- sql12.rep.configdistwizard.distproperties.general.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
ms.assetid: f643c7c3-f238-4835-b81e-2c2b3b53b23f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 501c7931d651498fea49749be38af374c02424ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632373"
---
# <a name="sql-server-replication-distributor-properties"></a><span data-ttu-id="74b65-102">SQL Server レプリケーションディストリビューターのプロパティ</span><span class="sxs-lookup"><span data-stu-id="74b65-102">SQL Server Replication Distributor Properties</span></span>
<span data-ttu-id="74b65-103">このトピックでは、[**ディストリビューターのプロパティ**] ウィンドウの **[全般**] ページ、[**パブリッシャー**] ページ、および [**ディストリビューションデータベース**] ページにあるプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="74b65-103">This topic discusses the properties found on the **General**, **Publishers**, and **Distribution Database** pages within the **Distributor Properties** window.</span></span> 

## <a name="general"></a><span data-ttu-id="74b65-104">全般</span><span class="sxs-lookup"><span data-stu-id="74b65-104">General</span></span>
  <span data-ttu-id="74b65-105">**[ディストリビューターのプロパティ]** ダイアログ ボックスの **[全般]** ページを使用すると、ディストリビューション データベースの追加と削除や、ディストリビューション データベースのプロパティの設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="74b65-105">The **General** page of the **Distributor Properties** dialog box allows you to add and delete distribution databases and set distribution database properties.</span></span>  
  
 <span data-ttu-id="74b65-106">ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションのトランザクションが格納されます。</span><span class="sxs-lookup"><span data-stu-id="74b65-106">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span> <span data-ttu-id="74b65-107">多くの場合、ディストリビューション データベースは 1 つで十分です。</span><span class="sxs-lookup"><span data-stu-id="74b65-107">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="74b65-108">ただし、複数のパブリッシャーが 1 つのディストリビューターを使用する場合、各パブリッシャーにディストリビューション データベースを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-108">But if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="74b65-109">これによって、各ディストリビューション データベースを経由するデータ フローが区別されます。</span><span class="sxs-lookup"><span data-stu-id="74b65-109">Doing so ensures that the data flowing through each distribution database is distinct.</span></span>  
  
### <a name="options"></a><span data-ttu-id="74b65-110">Options</span><span class="sxs-lookup"><span data-stu-id="74b65-110">Options</span></span>  
 <span data-ttu-id="74b65-111">**データベース**</span><span class="sxs-lookup"><span data-stu-id="74b65-111">**Databases**</span></span>  
 <span data-ttu-id="74b65-112">**[データベース]** プロパティ グリッドには、ディストリビューターのディストリビューション データベースの名前と保有期間のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="74b65-112">The **Databases** property grid shows the name and retention properties of the distribution databases on the Distributor.</span></span> <span data-ttu-id="74b65-113">**[トランザクションの保有期間]** は、トランザクションがトランザクション レプリケーションに格納される期間です (トランザクションの保有期間は、ディストリビューションの保有期間でもあります)。</span><span class="sxs-lookup"><span data-stu-id="74b65-113">**Transaction Retention** is the length of time transactions are stored for transactional replication (transaction retention is also known as distribution retention).</span></span> <span data-ttu-id="74b65-114">**[履歴の保有期間]** は、履歴メタデータがすべての種類のレプリケーションに格納される期間です。</span><span class="sxs-lookup"><span data-stu-id="74b65-114">**History Retention** is the length of time history metadata is stored for all types of replication.</span></span> <span data-ttu-id="74b65-115">ディストリビューション保有期間の詳細については、「[Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」 (サブスクリプションの有効期限と非アクティブ化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-115">For more information about distribution retention, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="74b65-116">**[ディストリビューション データベースのプロパティ]** ダイアログ ボックスを表示するには、 **[データベース]** プロパティ グリッドのプロパティ ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74b65-116">Click the properties button (**...**) in the **Databases** property grid to launch the **Distribution Database Properties** dialog box.</span></span>  
  
 <span data-ttu-id="74b65-117">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="74b65-117">**New**</span></span>  
 <span data-ttu-id="74b65-118">新しいディストリビューション データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="74b65-118">Click to create a new distribution database.</span></span>  
  
 <span data-ttu-id="74b65-119">**削除**</span><span class="sxs-lookup"><span data-stu-id="74b65-119">**Delete**</span></span>  
 <span data-ttu-id="74b65-120">**[データベース]** プロパティ グリッドで既存のディストリビューション データベースを選択し、 **[削除]** をクリックしてデータベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="74b65-120">Select an existing distribution database in the **Databases** property grid, and click **Delete** to delete the database.</span></span> <span data-ttu-id="74b65-121">ディストリビューターは少なくとも 1 つのディストリビューション データベースを持つ必要があるため、データベースが 1 つだけの場合はディストリビューション データベースを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="74b65-121">You cannot delete the distribution database if there is only one such database; each Distributor must have at least one distribution database.</span></span> <span data-ttu-id="74b65-122">すべてのディストリビューション データベースを削除するには、コンピューターでディストリビューションを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="74b65-122">To delete all distribution databases, you must disable distribution on the computer.</span></span> <span data-ttu-id="74b65-123">詳細については、「[パブリッシングの無効化と配布](disable-publishing-and-distribution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-123">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="74b65-124">**[プロファイルの既定値]**</span><span class="sxs-lookup"><span data-stu-id="74b65-124">**Profile Defaults**</span></span>  
 <span data-ttu-id="74b65-125">**[エージェント プロファイル]** ダイアログ ボックスのレプリケーション エージェント プロファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="74b65-125">Click to access replication agent profiles in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="74b65-126">プロファイルの詳細については、「 [Replication Agent Profiles](agents/replication-agent-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-126">For more information about profiles, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  

## <a name="publishers"></a><span data-ttu-id="74b65-127">[ディストリビューターのプロパティ]</span><span class="sxs-lookup"><span data-stu-id="74b65-127">Publishers</span></span>

  <span data-ttu-id="74b65-128">**[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページを使用すると、パブリッシャーでこのディストリビューターを使用できるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="74b65-128">The **Publishers** page of the **Distributor Properties** dialog box allows you to enable Publishers to use this Distributor.</span></span> <span data-ttu-id="74b65-129">さらに、このパブリッシャーに関連付けられているプロパティも設定できます。</span><span class="sxs-lookup"><span data-stu-id="74b65-129">You can also set properties associated with those Publishers.</span></span> <span data-ttu-id="74b65-130">パブリッシャーがサーバーをパブリッシャーのリモート ディストリビューターとして使用しても、そのサーバーがパブリッシャーにならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-130">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="74b65-131">パブリッシャーに接続し、パブリッシュするための構成を行って、このサーバーをディストリビューターとして選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74b65-131">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="74b65-132">パブリケーションの新規作成ウィザードを使用して、パブリッシャーを構成し、ディストリビューターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="74b65-132">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="74b65-133">Options</span><span class="sxs-lookup"><span data-stu-id="74b65-133">Options</span></span>  
 <span data-ttu-id="74b65-134">**配布**</span><span class="sxs-lookup"><span data-stu-id="74b65-134">**Publishers**</span></span>  
 <span data-ttu-id="74b65-135">このディストリビューターの使用を許可するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="74b65-135">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="74b65-136">追加のプロパティを表示および設定するには、パブリッシャーの横にあるプロパティボタン ([. **..])** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74b65-136">Click the Properties button **(...)** next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="74b65-137">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="74b65-137">**Add**</span></span>  
 <span data-ttu-id="74b65-138">許可するサーバーが一覧に表示されていない場合には、**[追加]** をクリックして、使用できるパブリッシャーの一覧に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたは Oracle パブリッシャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="74b65-138">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span> <span data-ttu-id="74b65-139">追加したサーバーが、最初にこのディストリビューターをリモート ディストリビューターとして使用するサーバーである場合、管理用リンク パスワードを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="74b65-139">If the server you add is the first server to use this Distributor as a remote Distributor, you are prompted to provide an administrative link password.</span></span>  
  
 <span data-ttu-id="74b65-140">**[管理用リンク パスワード]**</span><span class="sxs-lookup"><span data-stu-id="74b65-140">**Administrative link password**</span></span>  
 <span data-ttu-id="74b65-141">レプリケーションにより **distributor_admin** ログインを使用してパブリッシャーとリモート ディストリビューター間に作成される接続のパスワードを指定したり、更新したりできます。</span><span class="sxs-lookup"><span data-stu-id="74b65-141">Use to specify or update the password for the connection replication makes between the Publisher and the remote Distributor using the **distributor_admin** login:</span></span>  
  
-   <span data-ttu-id="74b65-142">ディストリビューターがローカル ディストリビューターとしてのみ動作する場合、このパスワードはランダムに生成され、自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="74b65-142">If the Distributor serves only as a local Distributor, this password is randomly generated and automatically configured.</span></span>  
-   <span data-ttu-id="74b65-143">既にディストリビューターにリモート パブリッシャーがある場合、パスワードはディストリビューションの構成ウィザードのこのページまたは **[ディストリビューター パスワード]** ページで最初に指定されています。</span><span class="sxs-lookup"><span data-stu-id="74b65-143">If the Distributor already has a remote Publisher, a password was initially supplied on this page or the **Distributor Password** page of the Configure Distribution Wizard.</span></span>    
-   <span data-ttu-id="74b65-144">このディストリビューターの最初のリモート パブリッシャーを有効にすると、パスワードを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="74b65-144">If you enable the first remote Publisher for this Distributor, you are prompted to enter a password.</span></span>  
  
 <span data-ttu-id="74b65-145">ディストリビューターのセキュリティの詳細については、「[ディストリビューターのセキュリティ保護](security/secure-the-distributor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-145">For more information on security for Distributors, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  

## <a name="distribution-database"></a><span data-ttu-id="74b65-146">ディストリビューション データベース</span><span class="sxs-lookup"><span data-stu-id="74b65-146">Distribution Database</span></span>
 <span data-ttu-id="74b65-147">**[ディストリビューション データベースのプロパティ]** ダイアログ ボックスを使用すると、多数のプロパティを表示でき、データベースにおけるトランザクションの保有期間と履歴の保有期間を設定できます。</span><span class="sxs-lookup"><span data-stu-id="74b65-147">The **Distribution Database Properties** dialog box allows you to view a number of properties and to set the transaction retention period and history retention period for the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="74b65-148">Options</span><span class="sxs-lookup"><span data-stu-id="74b65-148">Options</span></span>  
 <span data-ttu-id="74b65-149">**名前**</span><span class="sxs-lookup"><span data-stu-id="74b65-149">**Name**</span></span>  
 <span data-ttu-id="74b65-150">ディストリビューション データベースの名前です。既定の名前は "distribution" です (読み取り専用)。</span><span class="sxs-lookup"><span data-stu-id="74b65-150">The name of the distribution database, which defaults to 'distribution' (read-only).</span></span>  
  
 <span data-ttu-id="74b65-151">**ファイルの場所**</span><span class="sxs-lookup"><span data-stu-id="74b65-151">**File locations**</span></span>  
 <span data-ttu-id="74b65-152">データベース ファイルとログ ファイルの場所です (読み取り専用)。</span><span class="sxs-lookup"><span data-stu-id="74b65-152">The location of the database file and the log file (read-only).</span></span>  
  
 <span data-ttu-id="74b65-153">**トランザクションの保有期間**</span><span class="sxs-lookup"><span data-stu-id="74b65-153">**Transaction retention period**</span></span>  
 <span data-ttu-id="74b65-154">ディストリビューション保有期間とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="74b65-154">Also known as the distribution retention period.</span></span> <span data-ttu-id="74b65-155">トランザクション レプリケーションで格納されるトランザクションの期間の長さです。</span><span class="sxs-lookup"><span data-stu-id="74b65-155">The length of time transactions are stored for transactional replication.</span></span> <span data-ttu-id="74b65-156">詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-156">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="74b65-157">**[履歴の保有期間]**</span><span class="sxs-lookup"><span data-stu-id="74b65-157">**History retention period**</span></span>  
 <span data-ttu-id="74b65-158">すべての種類のレプリケーションで格納される、履歴メタデータの期間の長さです。</span><span class="sxs-lookup"><span data-stu-id="74b65-158">The length of time history metadata is stored for all types of replication.</span></span>  
  
 <span data-ttu-id="74b65-159">**キューリーダーエージェントのセキュリティ**</span><span class="sxs-lookup"><span data-stu-id="74b65-159">**Queue Reader Agent security**</span></span>  
 <span data-ttu-id="74b65-160">キュー リーダー エージェントは、トランザクション レプリケーションのキュー更新サブスクリプションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="74b65-160">The Queue Reader Agent is used by transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="74b65-161">パブリケーションの新規作成ウィザードの **[パブリケーションの種類]** ページで **[更新可能なサブスクリプションを含むトランザクション パブリケーション]** を選択すると、キュー リーダー エージェントが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="74b65-161">A Queue Reader Agent is created automatically if you select **Transactional publication with updating subscriptions** on the **Publication Type** page of the New Publication Wizard.</span></span> <span data-ttu-id="74b65-162">エージェントの実行や、ディストリビューターへの接続の作成に使用するアカウントを変更するには、**[セキュリティ設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74b65-162">Click **Security Settings...** to change the account under which the agent runs and makes connections to the Distributor.</span></span>  
  
 <span data-ttu-id="74b65-163">キュー リーダー エージェントは、このページの **[キュー リーダー エージェントを作成する]** を選択することでも作成できます (キュー リーダー エージェントが既に作成されている場合、このオプションは無効になります)。</span><span class="sxs-lookup"><span data-stu-id="74b65-163">A Queue Reader Agent can also be created by selecting **Create Queue Reader Agent** on this page (this option is disabled if the agent has already been created).</span></span>  
  
 <span data-ttu-id="74b65-164">キュー リーダー エージェントのその他の接続情報は、次の 2 つの場所で指定されます。</span><span class="sxs-lookup"><span data-stu-id="74b65-164">Additional connection information for the Queue Reader Agent is specified in two places:</span></span>    
-   <span data-ttu-id="74b65-165">**[パブリッシャーのプロパティ]** ダイアログ ボックス。エージェントは、このダイアログ ボックスで指定された資格情報を使用してパブリッシャーに接続します。このダイアログ ボックスは、 **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページから開きます。</span><span class="sxs-lookup"><span data-stu-id="74b65-165">The agent connects to the Publisher using the credentials specified in the **Publisher Properties** dialog box, which is available from the **Publishers** page of the **Distributor Properties** dialog box.</span></span>    
-   <span data-ttu-id="74b65-166">サブスクリプションの新規作成ウィザードの [ディストリビューション エージェント]。エージェントは、ここで指定された資格情報を使用してサブスクライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="74b65-166">The agent connects to the Subscriber using the credentials specified for the Distribution Agent in the New Subscription Wizard.</span></span>  
  
 <span data-ttu-id="74b65-167">詳細については、「 \\ [レプリケーションエージェントのセキュリティモデル](security/replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b65-167">For more information, see  \\[Replication Agent Security Model](security/replication-agent-security-model.md).</span></span> 

  
## <a name="see-also"></a><span data-ttu-id="74b65-168">参照</span><span class="sxs-lookup"><span data-stu-id="74b65-168">See Also</span></span>  
 <span data-ttu-id="74b65-169">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="74b65-169">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="74b65-170">ディストリビューターとパブリッシャーのプロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="74b65-170">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
