---
title: Change Data Capture Service for Oracle のユーザーロール (添付 Unity |)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: be0ec384-e03b-4483-96ca-02b289804d6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e694da0cfd8645fe594b049b6dc2394b55d1bb55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720294"
---
# <a name="user-roles-for-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="291d4-102">Change Data Capture Service for Oracle by Attunity のユーザー ロール</span><span class="sxs-lookup"><span data-stu-id="291d4-102">User Roles for Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="291d4-103">ここでは、Change Data Capture Service for Oracle by Attunity のユーザー ロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="291d4-103">This section describes the user roles for the Change Data Capture Service for Oracle by Attunity.</span></span> <span data-ttu-id="291d4-104">ここで説明するロールは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ロール、Windows ロール、または Oracle データベース ロールです。</span><span class="sxs-lookup"><span data-stu-id="291d4-104">The roles described are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database roles, Windows roles, or Oracle database roles.</span></span>  
  
## <a name="windows-user-roles"></a><span data-ttu-id="291d4-105">Windows ユーザー ロール</span><span class="sxs-lookup"><span data-stu-id="291d4-105">Windows User Roles</span></span>  
 <span data-ttu-id="291d4-106">ここでは、Oracle CDC Service によって使用される Windows ユーザー ロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="291d4-106">The following describes the Windows user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="computer-administrator-oracle-cdc-service"></a><span data-ttu-id="291d4-107">コンピューターの管理者: Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="291d4-107">Computer Administrator: Oracle CDC Service</span></span>  
 <span data-ttu-id="291d4-108">コンピューターの管理者は、コンピューターでの CDC Service の作成とメンテナンスを担当する Windows ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="291d4-108">The computer administrator is a Windows user responsible for creating and maintaining the CDC Service on the computer.</span></span> <span data-ttu-id="291d4-109">このユーザーは、ローカル コンピューターの Administrators グループに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-109">This user must belong to the group of local machine administrators.</span></span>  
  
 <span data-ttu-id="291d4-110">Oracle CDC Service のコンピューターの管理者が実行するタスクには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="291d4-110">The tasks performed by the Oracle CDC Service Computer Administrator include:</span></span>  
  
-   <span data-ttu-id="291d4-111">CDC Service for Oracle ソフトウェアのインストール</span><span class="sxs-lookup"><span data-stu-id="291d4-111">Installing the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="291d4-112">Oracle CDC Windows サービスの作成</span><span class="sxs-lookup"><span data-stu-id="291d4-112">Creating an Oracle CDC Windows service</span></span>  
  
-   <span data-ttu-id="291d4-113">CDC Service から対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続の設定 (接続文字列と資格情報)</span><span class="sxs-lookup"><span data-stu-id="291d4-113">Setting up the CDC Service connection to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (connection string and credentials)</span></span>  
  
-   <span data-ttu-id="291d4-114">CDC Service のマスター パスワードによる Oracle ログ マイニングの資格情報の保護</span><span class="sxs-lookup"><span data-stu-id="291d4-114">Ensuring that the CDC Service Master Password with which Oracle log mining credentials are protected</span></span>  
  
-   <span data-ttu-id="291d4-115">CDC Service Windows サービスの削除</span><span class="sxs-lookup"><span data-stu-id="291d4-115">Deleting a CDC Service Windows service</span></span>  
  
-   <span data-ttu-id="291d4-116">CDC Service for Oracle ソフトウェアのアンインストール</span><span class="sxs-lookup"><span data-stu-id="291d4-116">Uninstalling the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="291d4-117">CDC Service for Oracle ソフトウェアのメンテナンス (更新プログラムのインストールなど)</span><span class="sxs-lookup"><span data-stu-id="291d4-117">Maintaining the CDC Service for Oracle software (for example, installing updates)</span></span>  
  
-   <span data-ttu-id="291d4-118">CDC Service Windows サービスの開始と停止</span><span class="sxs-lookup"><span data-stu-id="291d4-118">Starting and stopping a CDC Service Windows service</span></span>  
  
 <span data-ttu-id="291d4-119">Microsoft フェールオーバー クラスターなどの高可用性構成を使用している場合、コンピューターの管理者は、次のような追加の役割と権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-119">When working with high-availability configurations, such as Microsoft failover clusters, the computer administrator must have additional responsibilities and permissions such as:</span></span>  
  
-   <span data-ttu-id="291d4-120">すべてのクラスター ノード上の CDC Service for Oracle ソフトウェアのインストールとメンテナンス。</span><span class="sxs-lookup"><span data-stu-id="291d4-120">Installation and maintenance of the CDC Service for Oracle software on all cluster nodes.</span></span>  
  
-   <span data-ttu-id="291d4-121">さまざまなクラスター ノードでの CDC Service Windows サービスに対する汎用クラスター サービス リソースの定義。</span><span class="sxs-lookup"><span data-stu-id="291d4-121">Defining generic cluster service resources for the CDC Service' Windows service on the various cluster nodes.</span></span>  
  
-   <span data-ttu-id="291d4-122">CDC Service for Oracle がインストールされているコンピューターで管理者として承認されたコンピューターの管理者の業務遂行。</span><span class="sxs-lookup"><span data-stu-id="291d4-122">Acting as the computer administrator authorized as an administrator on the computer where the CDC Service for Oracle is installed.</span></span> <span data-ttu-id="291d4-123">この人物は、CDC Service for Oracle をインストールし、CDC Service 構成コンソールを使用して CDC Service for Oracle をローカル コンピューターで構成します。</span><span class="sxs-lookup"><span data-stu-id="291d4-123">This person installs the CDC Service for Oracle and uses the CDC Service Configuration Console to configure a CDC Service for Oracle on a local computer.</span></span>  
  
### <a name="service-account-oracle-cdc-service"></a><span data-ttu-id="291d4-124">サービス アカウント: Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="291d4-124">Service Account: Oracle CDC Service</span></span>  
 <span data-ttu-id="291d4-125">これは Oracle CDC Service Windows サービス アカウントで、Oracle CDC Service を実行するために使用する Windows アカウント (サービス アカウント) です。</span><span class="sxs-lookup"><span data-stu-id="291d4-125">This is Oracle CDC Service Windows Service Account is a Windows account used for running the Oracle CDC Service (the Service Account).</span></span>  
  
 <span data-ttu-id="291d4-126">サービス アカウントに必要な特権は、Oracle クライアントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC プロバイダーを使用するための特権だけです。</span><span class="sxs-lookup"><span data-stu-id="291d4-126">The only required privilege necessary for the service account is to be able to use the Oracle client and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client ODBC provider.</span></span> <span data-ttu-id="291d4-127">このアカウントは、特定のプロバイダーで必要な場合を除いて、ファイルにアクセスする必要はありません (たとえば、 **tnsnames.ora** ファイルで Oracle クライアントの接続文字列が Oracle データベース インスタンスを参照している場合、サービス アカウントにはそのファイルへの読み取りアクセス権が必要です)。</span><span class="sxs-lookup"><span data-stu-id="291d4-127">This account does not need to access files unless required by specific providers (for example, if the Oracle client connection string references Oracle database instances in a **tnsnames.ora** file, then that file must be read-accessible to the service account).</span></span>  
  
 <span data-ttu-id="291d4-128">Windows Vista または Windows Server 2008 で Oracle CDC Service を作成する場合、既定のサービス アカウントは NETWORK SERVICE アカウントです。</span><span class="sxs-lookup"><span data-stu-id="291d4-128">When creating an Oracle CDC Service on Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
 <span data-ttu-id="291d4-129">Windows 7 および Windows Server 2008 R2 以降では、既定のサービス アカウントは NT Service\\<service-name> です。</span><span class="sxs-lookup"><span data-stu-id="291d4-129">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
 <span data-ttu-id="291d4-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が、別のコンピューターで実行されているか、クラスター化された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスであって、サービスが Windows 認証を使用して対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する必要がある場合、サービス アカウントはドメイン アカウントにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-130">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on another machine or is a clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and there the service needs to connect to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows authentication, then the service account should be a domain account.</span></span>  
  
## <a name="sql-server-user-roles"></a><span data-ttu-id="291d4-131">SQL Server ユーザー ロール</span><span class="sxs-lookup"><span data-stu-id="291d4-131">SQL Server User Roles</span></span>  
 <span data-ttu-id="291d4-132">ここでは、Oracle CDC Service によって使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー ロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="291d4-132">The following describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="oracle-cdc-service-administrator"></a><span data-ttu-id="291d4-133">Oracle CDC Service の管理者</span><span class="sxs-lookup"><span data-stu-id="291d4-133">Oracle CDC Service Administrator</span></span>  
 <span data-ttu-id="291d4-134">CDC Service の管理者は、対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの Oracle CDC Service アーティファクトを完全に制御できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="291d4-134">The CDC Service Administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user with full control over the Oracle CDC Service artifacts in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="291d4-135">CDC Service の管理者は、Oracle CDC デザイナー コンソールを使用して Oracle CDC インスタンスを設計します。</span><span class="sxs-lookup"><span data-stu-id="291d4-135">The CDC Service Administrator uses the Oracle CDC Designer Console to design Oracle CDC Instances.</span></span>  
  
 <span data-ttu-id="291d4-136">CDC Service の管理者には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定サーバー ロールの **public** と **dbcreator**が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-136">The CDC Service Administrator should be granted the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fixed server roles **public** and **dbcreator**.</span></span>  
  
 <span data-ttu-id="291d4-137">CDC Service の管理者が実行するタスクには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="291d4-137">The tasks performed by the CDC Service Administrator include:</span></span>  
  
-   <span data-ttu-id="291d4-138">Oracle CDC インスタンス ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース) をホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの準備。</span><span class="sxs-lookup"><span data-stu-id="291d4-138">Preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host Oracle CDC Instances (which are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases).</span></span> <span data-ttu-id="291d4-139">このタスクでは、MSXDBCDC と呼ばれる特別なデータベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに作成します。</span><span class="sxs-lookup"><span data-stu-id="291d4-139">In this task, a special database called MSXDBCDC is created in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="291d4-140">Oracle CDC インスタンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの作成。</span><span class="sxs-lookup"><span data-stu-id="291d4-140">Creating an Oracle CDC Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="291d4-141">このタスクには、新しく作成した CDC 用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの有効化が含まれます。これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者 (**sysadmin**) が行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-141">Task includes enabling the newly created [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for CDC, which requires a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (**sysadmin**).</span></span>  
  
-   <span data-ttu-id="291d4-142">Oracle CDC インスタンスの設計。</span><span class="sxs-lookup"><span data-stu-id="291d4-142">Designing an Oracle CDC Instance.</span></span> <span data-ttu-id="291d4-143">このタスクには、ソース Oracle データベースとキャプチャ対象テーブルについての情報の提供が含まれます。これは、Oracle データベース管理者が行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-143">This task includes providing information about the source Oracle database and captured tables, which requires an Oracle database administrator.</span></span>  
  
-   <span data-ttu-id="291d4-144">長期にわたる Oracle CDC インスタンスのメンテナンス。キャプチャ インスタンスの追加と削除や構成の更新などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="291d4-144">Maintaining the Oracle CDC Instance over time, which includes adding/removing capture instances and updating configuration.</span></span>  
  
-   <span data-ttu-id="291d4-145">Oracle CDC インスタンスの有効化または無効化。</span><span class="sxs-lookup"><span data-stu-id="291d4-145">Enabling or disabling an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="291d4-146">Oracle CDC インスタンスの状態の監視。</span><span class="sxs-lookup"><span data-stu-id="291d4-146">Monitoring the state of an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="291d4-147">Oracle CDC インスタンスに影響する問題のトラブルシューティング。</span><span class="sxs-lookup"><span data-stu-id="291d4-147">Troubleshooting issues that affect the Oracle CDC Instance.</span></span>  
  
 <span data-ttu-id="291d4-148">CDC Service の管理者は、少なくとも最初は、Oracle CDC インスタンスに関連付けられた **CDC データベース用の** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定データベース ロールに属しています。</span><span class="sxs-lookup"><span data-stu-id="291d4-148">The CDC Service Administrator is, at least initially, in the **db_owner** fixed database role for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database associated with the Oracle CDC Instance.</span></span> <span data-ttu-id="291d4-149">そのため、CDC Service の管理者は、CDC データベースに格納されている変更データにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="291d4-149">This gives the CDC Service Administrator access to the change data stored in the CDC database.</span></span> <span data-ttu-id="291d4-150">CDC データベースの **db_owner** ロールを作成したら別のユーザーに割り当てることができ、このユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの準備と別の Oracle CDC インスタンスの作成を除く上記のすべてのタスクを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="291d4-150">Once created, the **db_owner** role of the CDC database can be assigned to a different user who can carry out all of the tasks listed above except for preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and creating another Oracle CDC Instance).</span></span>  
  
 <span data-ttu-id="291d4-151">CDC Service の管理者は、Oracle CDC Windows サービスの作成時に指定されたマスター パスワードを把握しておく必要はありません。</span><span class="sxs-lookup"><span data-stu-id="291d4-151">The CDC Service Administrator does not need to know the master password specified with the creation of the Oracle CDC Windows service.</span></span>  
  
### <a name="system-administrator"></a><span data-ttu-id="291d4-152">システム管理者</span><span class="sxs-lookup"><span data-stu-id="291d4-152">System Administrator</span></span>  
 <span data-ttu-id="291d4-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーで、Oracle CDC Service に関連付けられた **インスタンスの** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定サーバー ロールが付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-153">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user and should be granted the fixed server **sysadmin** role on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance associated with the Oracle CDC Service(s).</span></span>  
  
 <span data-ttu-id="291d4-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者が行う Oracle CDC に固有のタスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 用の Oracle CDC インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの有効化だけです。</span><span class="sxs-lookup"><span data-stu-id="291d4-154">There is only one Oracle CDC specific task that carried out with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System Administrator and that is to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for an Oracle CDC Instance for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC.</span></span> <span data-ttu-id="291d4-155">このタスクは、新しい Oracle CDC インスタンスを作成するときに、Oracle CDC デザイナー コンソールを使用して実行します。</span><span class="sxs-lookup"><span data-stu-id="291d4-155">This task is performed using the Oracle CDC Designer console when creating a new Oracle CDC Instance.</span></span>  
  
### <a name="oracle-cdc-service-user"></a><span data-ttu-id="291d4-156">Oracle CDC Service ユーザー</span><span class="sxs-lookup"><span data-stu-id="291d4-156">Oracle CDC Service User</span></span>  
 <span data-ttu-id="291d4-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service ユーザーは、このサービスで処理される MSXDBCDC およびすべての Oracle CDC インスタンス (CDC データベース) に対する作業を実行するために Oracle CDC Service によって使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインです。</span><span class="sxs-lookup"><span data-stu-id="291d4-157">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login which is used by the Oracle CDC Service to perform its work against the MSXDBCDC and all of the Oracle CDC Instances (CDC databases) handled by this service.</span></span>  
  
 <span data-ttu-id="291d4-158">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service ユーザーには、以下が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-158">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user should be granted the following:</span></span>  
  
-   <span data-ttu-id="291d4-159">サーバーで処理されるすべての CDC データベースの固定データベース ロール **db_dlladmin**、 **db_datareader**、および **db_datawriter** のメンバー。</span><span class="sxs-lookup"><span data-stu-id="291d4-159">Member of the fixed database roles **db_dlladmin**, **db_datareader**, and **db_datawriter** for all CDC databases handled by the server.</span></span>  
  
-   <span data-ttu-id="291d4-160">MSXDBCDC データベースの固定データベース ロール **db_datareader** および **db_datawriter** のメンバー。</span><span class="sxs-lookup"><span data-stu-id="291d4-160">Member of the fixed database roles **db_datareader** and **db_datawriter** for the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="291d4-161">Oracle CDC Service は、単一の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用してすべての CDC データベースおよび MSXDBCDC データベースを処理するので、このログインをこれらすべてのデータベースでマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="291d4-161">Because the Oracle CDC Service uses a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to work with all CDC databases and the MSXDBCDC database, this login should be mapped in all of these databases.</span></span>  
  
### <a name="oracle-cdc-change-consumer"></a><span data-ttu-id="291d4-162">Oracle CDC 変更コンシューマー</span><span class="sxs-lookup"><span data-stu-id="291d4-162">Oracle CDC Change Consumer</span></span>  
 <span data-ttu-id="291d4-163">Oracle CDC 変更コンシューマーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC インスタンス データベースの CDC テーブルに格納されている変更を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="291d4-163">The Oracle CDC Change Consumer is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user that consumes changes stored in the CDC tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database.</span></span>  
  
 <span data-ttu-id="291d4-164">このユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC インフラストラクチャによって生成される CDC 関数を使用して各 CDC テーブルにアクセスするために必要なユーザー ロールを決定します。</span><span class="sxs-lookup"><span data-stu-id="291d4-164">This user determines the user role that is required for accessing each of the CDC tables through the CDC functions generated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC infrastructure.</span></span> <span data-ttu-id="291d4-165">キャプチャ インスタンスの指定時にユーザー ロールを指定しない場合は、変更へのアクセスが CDC データベースの **db_owner** 固定データベース ロールのメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="291d4-165">If no user role is specified when a capture instance is specified, access to the changes is limited to the member of the **db_owner** fixed database role of the CDC database.</span></span>  
  
## <a name="oracle-user-roles"></a><span data-ttu-id="291d4-166">Oracle ユーザー ロール</span><span class="sxs-lookup"><span data-stu-id="291d4-166">Oracle User Roles</span></span>  
 <span data-ttu-id="291d4-167">ここでは、Oracle CDC Service によって使用される Oracle ユーザー ロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="291d4-167">The following describes the Oracle user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="database-administrator-dba"></a><span data-ttu-id="291d4-168">データベース管理者 (DBA)</span><span class="sxs-lookup"><span data-stu-id="291d4-168">Database Administrator (DBA)</span></span>  
 <span data-ttu-id="291d4-169">Oracle データベース管理者 (DBA) は、Oracle データベース ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="291d4-169">The Oracle database administrator (DBA) is an Oracle database user.</span></span> <span data-ttu-id="291d4-170">Oracle DBA が実行するタスクには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="291d4-170">The tasks performed by the Oracle DBA include:</span></span>  
  
-   <span data-ttu-id="291d4-171">ソース Oracle データベースを ARCHIVELOG モードで動作させるための設定。</span><span class="sxs-lookup"><span data-stu-id="291d4-171">Setting the source Oracle database to work in ARCHIVELOG mode.</span></span>  
  
-   <span data-ttu-id="291d4-172">必要な権限を持つログ マイニング ユーザーの設定。</span><span class="sxs-lookup"><span data-stu-id="291d4-172">Setting up a log mining user with the required permissions.</span></span>  
  
-   <span data-ttu-id="291d4-173">キャプチャ対象テーブルの補足ログの設定。</span><span class="sxs-lookup"><span data-stu-id="291d4-173">Setting supplemental logging for captured tables.</span></span>  
  
-   <span data-ttu-id="291d4-174">使用できなくなったアーカイブ済みのトランザクション ログ ファイルを処理できるように復元するための支援。</span><span class="sxs-lookup"><span data-stu-id="291d4-174">Helping to restore archived transaction log files no longer available so they can be processed.</span></span>  
  
 <span data-ttu-id="291d4-175">Oracle データベース管理者は、実行する必要がある Oracle SQL スクリプトを取得して、その実行前に評価することができます。</span><span class="sxs-lookup"><span data-stu-id="291d4-175">The Oracle database administrator can get Oracle SQL scripts that need to run so they can be evaluated before running them.</span></span> <span data-ttu-id="291d4-176">また、Oracle SQL スクリプトを Oracle CDC デザイナー コンソールから直接実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="291d4-176">The Oracle database administrator can also directly run Oracle SQL scripts from the Oracle CDC Designer console.</span></span>  
  
 <span data-ttu-id="291d4-177">Oracle データベース管理者が Oracle CDC Designer コンソールの使用を選択した場合、管理者の資格情報は保持されません。ただし、資格情報が使用されたコンテキスト (ダイアログ) は除きます。</span><span class="sxs-lookup"><span data-stu-id="291d4-177">If the Oracle database administrator chooses to use the Oracle CDC Designer console, administrator's credentials are not kept except for the context (dialog) in which they were used.</span></span>  
  
 <span data-ttu-id="291d4-178">Oracle データベース管理者は、Oracle CDC Service の管理者と連携して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC インスタンスを構成します。</span><span class="sxs-lookup"><span data-stu-id="291d4-178">The Oracle database administrator works in coordination with the Oracle CDC Service administrator on the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instances.</span></span>  
  
### <a name="log-mining-user"></a><span data-ttu-id="291d4-179">ログ マイニング ユーザー</span><span class="sxs-lookup"><span data-stu-id="291d4-179">Log Mining User</span></span>  
 <span data-ttu-id="291d4-180">Oracle Log Miner ユーザーは、Oracle トランザクション ログにアクセスして処理するために必要な特権が付与された特殊な Oracle データベース ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="291d4-180">The Oracle Log Miner user is a special Oracle database user that is granted the required privileges for accessing and processing the Oracle transaction logs.</span></span>  
  
 <span data-ttu-id="291d4-181">このユーザーの資格情報は、非対称キー暗号化を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC インスタンス データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="291d4-181">The credentials for this user are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database using asymmetric key encryption.</span></span> <span data-ttu-id="291d4-182">その資格情報には Oracle CDC Service のみがアクセスでき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC インスタンス データベースの所有者はアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="291d4-182">They are accessible only to the Oracle CDC Service but not to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database owner.</span></span>  
  
 <span data-ttu-id="291d4-183">ログ マイニング ユーザーに付与されている必要がある特権を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="291d4-183">The following list describes the required privileges of the log mining user should be granted:</span></span>  
  
-   <span data-ttu-id="291d4-184">\<any-captured-table> に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-184">SELECT on \<any-captured-table></span></span>  
  
-   <span data-ttu-id="291d4-185">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="291d4-185">SELECT ANY TRANSACTION</span></span>  
  
-   <span data-ttu-id="291d4-186">DBMS_LOGMNR に対する EXECUTE</span><span class="sxs-lookup"><span data-stu-id="291d4-186">EXECUTE on DBMS_LOGMNR</span></span>  
  
-   <span data-ttu-id="291d4-187">V$LOGMNR_CONTENTS に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-187">SELECT on V$LOGMNR_CONTENTS</span></span>  
  
-   <span data-ttu-id="291d4-188">V$ARCHIVED_LOG に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-188">SELECT on V$ARCHIVED_LOG</span></span>  
  
-   <span data-ttu-id="291d4-189">V$LOG に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-189">SELECT on V$LOG</span></span>  
  
-   <span data-ttu-id="291d4-190">V$LOGFILE に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-190">SELECT on V$LOGFILE</span></span>  
  
-   <span data-ttu-id="291d4-191">V$DATABASE に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-191">SELECT on V$DATABASE</span></span>  
  
-   <span data-ttu-id="291d4-192">V$THREAD に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-192">SELECT on V$THREAD</span></span>  
  
-   <span data-ttu-id="291d4-193">V$PARAMETER に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-193">SELECT on V$PARAMETER</span></span>  
  
-   <span data-ttu-id="291d4-194">DBA_REGISTRY に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-194">SELECT on DBA_REGISTRY</span></span>  
  
-   <span data-ttu-id="291d4-195">ALL_INDEXES に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-195">SELECT on ALL_INDEXES</span></span>  
  
-   <span data-ttu-id="291d4-196">ALL_OBJECTS に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-196">SELECT on ALL_OBJECTS</span></span>  
  
-   <span data-ttu-id="291d4-197">DBA_OBJECTS に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-197">SELECT on DBA_OBJECTS</span></span>  
  
-   <span data-ttu-id="291d4-198">ALL_TABLES に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="291d4-198">SELECT on ALL_TABLES</span></span>  
  
 <span data-ttu-id="291d4-199">これらの特権を V$xxx に付与できないときは、V $xxx に付与してください。</span><span class="sxs-lookup"><span data-stu-id="291d4-199">If any of these privileges cannot be granted to a V$xxx, then they should be granted to the V $xxx.</span></span>  
  
### <a name="schema-user"></a><span data-ttu-id="291d4-200">スキーマ ユーザー</span><span class="sxs-lookup"><span data-stu-id="291d4-200">Schema User</span></span>  
 <span data-ttu-id="291d4-201">Oracle スキーマ ユーザーは、キャプチャする Oracle テーブルのスキーマへの読み取りアクセスが可能な Oracle ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="291d4-201">The Oracle Schema User is an Oracle user with read access to the schema of the Oracle tables to be captured.</span></span> <span data-ttu-id="291d4-202">このユーザーは、Oracle CDC デザイナー コンソールを操作して Oracle スキーマ、キャプチャするテーブル、その列、インデックス、およびキーの一覧を取得するときに必要です。</span><span class="sxs-lookup"><span data-stu-id="291d4-202">This user is necessary when working with the Oracle CDC Designer console to retrieve the list of Oracle schema, tables to be captured and their columns, indexes and keys.</span></span>  
  
 <span data-ttu-id="291d4-203">このユーザーの資格情報は格納されません。</span><span class="sxs-lookup"><span data-stu-id="291d4-203">The credentials for this user are never stored.</span></span> <span data-ttu-id="291d4-204">必要になるたびに CDC デザイナー コンソールによって要求され、残りの UI セッションの間保持されます。</span><span class="sxs-lookup"><span data-stu-id="291d4-204">They are requested by the CDC Designer console each time they are needed and they are kept for the rest of the UI sessions.</span></span>  
  
  
