---
title: Oracle CDC Service の作成と編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 10cd612e-d8f1-4af2-97d3-a0c22e1e2326
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3325e272285895e813f01d50a1c312e75472919b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634596"
---
# <a name="create-and-edit-an-oracle-cdc-service"></a><span data-ttu-id="bb285-102">Oracle CDC Service の作成と編集</span><span class="sxs-lookup"><span data-stu-id="bb285-102">Create and Edit an Oracle CDC Service</span></span>
  <span data-ttu-id="bb285-103">新しい Oracle CDC Windows Service の作成と編集は CDC Service 構成コンソールで行います。</span><span class="sxs-lookup"><span data-stu-id="bb285-103">You create and edit a new Oracle CDC Windows Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="bb285-104">新しい Oracle CDC Windows Service を作成するには、左側のペインで **[ローカルの CDC Service]** を選択し、 **[アクション]** ペインで **[新しいサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb285-104">To create a new Oracle CDC Windows service, select **Local CDC Services** from the left pane, then click **New Service** from the **Actions** pane.</span></span> <span data-ttu-id="bb285-105">**[ローカルの CDC Service]** を右クリックして **[新しいサービス]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb285-105">You can also right-click **Local CDC Services** and select **New Service**.</span></span> <span data-ttu-id="bb285-106">[新しい Oracle CDC Windows Service] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb285-106">The New Oracle CDC Windows Service dialog box opens.</span></span>  
  
 <span data-ttu-id="bb285-107">**OR**</span><span class="sxs-lookup"><span data-stu-id="bb285-107">**OR**</span></span>  
  
 <span data-ttu-id="bb285-108">CDC Service のプロパティを編集するには、プロパティを編集するサービスを選択し、 **[アクション]** ペインの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb285-108">To edit the CDC service properties, select the service that you want to edit the properties for and click **Properties** from the **Actions** pane.</span></span> <span data-ttu-id="bb285-109">操作するサービスを右クリックし、 **[プロパティ]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb285-109">You can also right-click the service you are working with and select **Properties**.</span></span> <span data-ttu-id="bb285-110">[CDC Service のプロパティ] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb285-110">The CDC Service Properties dialog box opens.</span></span>  
  
 <span data-ttu-id="bb285-111">[新しい Oracle CDC Windows Service] ダイアログ ボックスまたは [CDC Service のプロパティ] ダイアログ ボックスに次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb285-111">Enter the following information in the New Oracle CDC Windows Service dialog box or the CDC Service Properties dialog box.</span></span>  
  
 <span data-ttu-id="bb285-112">サービス名</span><span class="sxs-lookup"><span data-stu-id="bb285-112">Service Name</span></span>  
 <span data-ttu-id="bb285-113">新しい Oracle CDC Windows Service の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb285-113">Type the name of the new Oracle CDC Windows Service.</span></span> <span data-ttu-id="bb285-114">可能な限り長い名前は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="bb285-114">You should not use long names, if possible.</span></span> <span data-ttu-id="bb285-115">/ 文字および \ 文字はサービス名で使用できません。</span><span class="sxs-lookup"><span data-stu-id="bb285-115">The characters / and \ cannot be used in the service name.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="bb285-116">このオプションは、サービスを編集するときは使用できません。</span><span class="sxs-lookup"><span data-stu-id="bb285-116">This option is not available when editing the service.</span></span> <span data-ttu-id="bb285-117">既に存在する Windows サービスの名前を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="bb285-117">You cannot change the name of a Windows service that already exists.</span></span>  
  
 <span data-ttu-id="bb285-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="bb285-118">**Description**</span></span>  
 <span data-ttu-id="bb285-119">サービスを識別するのに役立つ説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb285-119">Type a description of the service to help identify it.</span></span>  
  
 <span data-ttu-id="bb285-120">**[サービス アカウント]**</span><span class="sxs-lookup"><span data-stu-id="bb285-120">**Service Account**</span></span>  
 <span data-ttu-id="bb285-121">次のいずれかを選択して、サービスを実行するアカウントを決定します。</span><span class="sxs-lookup"><span data-stu-id="bb285-121">Select one of the following to determine under which account to run the service:</span></span>  
  
-   <span data-ttu-id="bb285-122">**ローカル システム アカウント**</span><span class="sxs-lookup"><span data-stu-id="bb285-122">**Local System Account**</span></span>  
  
     <span data-ttu-id="bb285-123">このオプションはサービスに与える権限が多すぎるため、お勧めしません。</span><span class="sxs-lookup"><span data-stu-id="bb285-123">This is not recommended because it gives too many permissions to the service.</span></span>  
  
-   <span data-ttu-id="bb285-124">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="bb285-124">**This Account**</span></span>  
  
     <span data-ttu-id="bb285-125">Windows Vista または Windows Server 2008 では、既定のサービス アカウントは NETWORK SERVICE アカウントです。</span><span class="sxs-lookup"><span data-stu-id="bb285-125">On Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
     <span data-ttu-id="bb285-126">Windows 7 および Windows Server 2008 R2 以降では、既定のサービス アカウントは NT Service\\<service-name> です。</span><span class="sxs-lookup"><span data-stu-id="bb285-126">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
     <span data-ttu-id="bb285-127">これらのアカウントにはパスワードが不要なため、これらのアカウントを使用すると、パスワードを使用せずに作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bb285-127">Using these accounts lets you work without using passwords because a password is not necessary for these accounts.</span></span> <span data-ttu-id="bb285-128">さらにこれらのアカウントは、Oracle CDC Service の実行に必要な権限のみを提供します。</span><span class="sxs-lookup"><span data-stu-id="bb285-128">In addition these accounts provide only the necessary permissions required for the Oracle CDC Service to run.</span></span>  
  
     <span data-ttu-id="bb285-129">ローカルまたはドメインの Windows アカウントをサービス アカウントに使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb285-129">You can use a local or domain Windows account for the service account.</span></span> <span data-ttu-id="bb285-130">この場合、アカウントの **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb285-130">In this case, you must enter the **Password** for that account.</span></span> <span data-ttu-id="bb285-131">このアカウントは、ローカル ホストまたはドメイン アカウント用にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bb285-131">This account can be for the local host or a domain account.</span></span> <span data-ttu-id="bb285-132">パスワードが変更されたときは、必ず Windows のコントロール パネルのローカル サービスを使用してパスワードを更新します。</span><span class="sxs-lookup"><span data-stu-id="bb285-132">Be sure to update the password when it is changed using Local Services in the Windows Control Panel.</span></span>  
  
 <span data-ttu-id="bb285-133">**[サーバー名]** : 接続先となる対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを選択します (例: **\\\\<コンピューター名>\\<インスタンス名>** )。</span><span class="sxs-lookup"><span data-stu-id="bb285-133">**Server name**: Select the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to connect to (for example, **\\\\<computer_name>\\<instance_name>**).</span></span> <span data-ttu-id="bb285-134">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb285-134">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="bb285-135">**認証**</span><span class="sxs-lookup"><span data-stu-id="bb285-135">**Authentication**</span></span>  
 <span data-ttu-id="bb285-136">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="bb285-136">Select one of the following:</span></span>  
  
-   <span data-ttu-id="bb285-137">**[Windows 認証]** :このオプションを選択した場合、Oracle CDC Service はサービス アカウント ID を使用して対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bb285-137">**Windows Authentication**: If you select this option, the Oracle CDC service connects to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using the service account identity.</span></span> <span data-ttu-id="bb285-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが異なるコンピューターで実行されている場合、Windows 認証をドメイン アカウントと共に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb285-138">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is running on a different computer, Windows Authentication must be used with domain accounts.</span></span>  
  
-   <span data-ttu-id="bb285-139">**[SQL Server 認証]** : このオプションを選択する場合、使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの **[ユーザー名]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb285-139">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login you want to use.</span></span> <span data-ttu-id="bb285-140">Oracle CDC Service は、対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続するときに、これらの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="bb285-140">The Oracle CDC service uses these credentials when connecting to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="bb285-141">Oracle CDC Service によって使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、public 固定サーバー ロールのメンバーであることだけが必要です。その他の権限は不要です。</span><span class="sxs-lookup"><span data-stu-id="bb285-141">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="bb285-142">新しい Oracle CDC インスタンスが追加されると、そのログインには、関連付けられている **CDC データベースへの** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アクセスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="bb285-142">Once new Oracle CDC Instances are added, that login will gain **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
 <span data-ttu-id="bb285-143">Oracle CDC Windows Service の定義を作成するには、プログラムに、関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の MSXDBCDC データベースに対する更新アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="bb285-143">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="bb285-144">**[OK]** をクリックすると、MSXDBCDC データベースに対する更新アクセスを持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを入力するためのダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb285-144">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="bb285-145">[SQL Server への接続] ダイアログ ボックスに入力するデータについては、「 [Connection to SQL Server](connection-to-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb285-145">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
 <span data-ttu-id="bb285-146">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="bb285-146">**Options**</span></span>  
 <span data-ttu-id="bb285-147">矢印をクリックして、構成するオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="bb285-147">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="bb285-148">これらのオプションを既定値のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb285-148">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="bb285-149">使用可能なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bb285-149">The available options are:</span></span>  
  
-   <span data-ttu-id="bb285-150">**[接続タイムアウト]** : CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。</span><span class="sxs-lookup"><span data-stu-id="bb285-150">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="bb285-151">**[実行タイムアウト]** : Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。</span><span class="sxs-lookup"><span data-stu-id="bb285-151">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="bb285-152">**[暗号化接続]** : Oracle CDC Service とターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの間の暗号化された接続を使用した通信に対しては、 **[暗号化接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb285-152">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="bb285-153">**[詳細設定]** :必要に応じて、追加の接続プロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="bb285-153">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
 <span data-ttu-id="bb285-154">**[マスター パスワード]**</span><span class="sxs-lookup"><span data-stu-id="bb285-154">**Master Password**</span></span>  
 <span data-ttu-id="bb285-155">Oracle CDC Windows Service によって Oracle のログ マイニング資格情報を保護するために使用されるパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="bb285-155">Enter a password to be used by the Oracle CDC Windows Service to protect the Oracle log-mining credentials.</span></span>  
  
 <span data-ttu-id="bb285-156">高可用性構成で同じサービスの他のインスタンスがクラスターの他のノードで構成されている場合、同じマスター パスワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb285-156">The same master password must also be used when other instances of the same service are configured on other nodes on a cluster in high-availability configuration.</span></span> <span data-ttu-id="bb285-157">マスター パスワードを紛失または変更した場合、Oracle CDC インスタンス データベースに格納されているすべてのログ マイニング パスワードを、CDC デザイナー コンソールを使用して再入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb285-157">If you lose or modify the master password, all log mining passwords stored in Oracle CDC Instance databases must be re-entered using the CDC Designer console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb285-158">参照</span><span class="sxs-lookup"><span data-stu-id="bb285-158">See Also</span></span>  
 [<span data-ttu-id="bb285-159">CDC Service を作成および編集する方法</span><span class="sxs-lookup"><span data-stu-id="bb285-159">How to Create and Edit a CDC Service</span></span>](how-to-create-and-edit-a-cdc-service.md)  
  
  
