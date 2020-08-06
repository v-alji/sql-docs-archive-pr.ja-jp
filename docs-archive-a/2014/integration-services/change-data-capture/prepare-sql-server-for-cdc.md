---
title: CDC 用の SQL Server の準備 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dafa29d9bdb0c27decb605398a6d1cfe383427e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633272"
---
# <a name="prepare-sql-server-for-cdc"></a><span data-ttu-id="4fd37-102">CDC 用の SQL Server の準備</span><span class="sxs-lookup"><span data-stu-id="4fd37-102">Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="4fd37-103">Oracle CDC サービスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのターゲット インスタンスに MSXDBCDC データベースが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fd37-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="4fd37-104">このデータベースを作成するには、CDC Service 構成コンソールの "SQL Server の準備" アクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4fd37-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.</span></span> <span data-ttu-id="4fd37-105">これによって作成される特別なスクリプトを実行すると、このデータベースに必要なテーブル、ストアド プロシージャ、およびその他のアーティファクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4fd37-105">This creates a special script that is run to create the required tables, stored procedures, and other required artifacts for this database.</span></span> <span data-ttu-id="4fd37-106">このタスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各ターゲット インスタンスに対して一度だけ実行します。</span><span class="sxs-lookup"><span data-stu-id="4fd37-106">This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="4fd37-107">MSXDBCDC データベースの詳細については、「MSXDBCDC データベース」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fd37-107">For more information about the MSXDBCDC database, see The MSXDBCDC Database.</span></span>  
  
 <span data-ttu-id="4fd37-108">CDC Service 構成コンソールで **[SQLServer の準備]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4fd37-108">In the CDC Service Configuration Console, click **Prepare SQL Server**.</span></span> <span data-ttu-id="4fd37-109">このオプションを利用できない場合は、コンソールの左ペインで **[ローカルの CDC Service]** が選択されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4fd37-109">If this option is not available, make sure that **Local CDC Services** is selected in the left pane of the console.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4fd37-110">Options</span><span class="sxs-lookup"><span data-stu-id="4fd37-110">Options</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="4fd37-111">サーバー名</span><span class="sxs-lookup"><span data-stu-id="4fd37-111">Server Name</span></span>  
 <span data-ttu-id="4fd37-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4fd37-112">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="4fd37-113">認証</span><span class="sxs-lookup"><span data-stu-id="4fd37-113">Authentication</span></span>  
 <span data-ttu-id="4fd37-114">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="4fd37-114">Select one of the following:</span></span>  
  
-   <span data-ttu-id="4fd37-115">**[Windows 認証]**</span><span class="sxs-lookup"><span data-stu-id="4fd37-115">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="4fd37-116">**[SQL Server 認証]** : このオプションを選択する場合、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fd37-116">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="4fd37-117">Oracle CDC 用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備するには、ログインが MSXDBCDC データベースに対する書き込み権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fd37-117">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="4fd37-118">`sysasmin` ロールのメンバーなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="4fd37-118">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
### <a name="options"></a><span data-ttu-id="4fd37-119">Options</span><span class="sxs-lookup"><span data-stu-id="4fd37-119">Options</span></span>  
 <span data-ttu-id="4fd37-120">矢印をクリックして、構成するオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="4fd37-120">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="4fd37-121">これらのオプションを既定値のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4fd37-121">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="4fd37-122">使用可能なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4fd37-122">The available options are:</span></span>  
  
-   <span data-ttu-id="4fd37-123">**[接続タイムアウト]** : CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。</span><span class="sxs-lookup"><span data-stu-id="4fd37-123">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="4fd37-124">**[実行タイムアウト]** : Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。</span><span class="sxs-lookup"><span data-stu-id="4fd37-124">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="4fd37-125">**[暗号化接続]** : Oracle CDC Service とターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの間の暗号化された接続を使用した通信に対しては、 **[暗号化接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4fd37-125">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="4fd37-126">**[詳細設定]** :必要に応じて、追加の接続プロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="4fd37-126">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
### <a name="view-script"></a><span data-ttu-id="4fd37-127">[スクリプトの表示]</span><span class="sxs-lookup"><span data-stu-id="4fd37-127">View Script</span></span>  
 <span data-ttu-id="4fd37-128">セットアップ スクリプトの読み取り専用バージョンを表示するには、 **[スクリプトの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4fd37-128">Click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="4fd37-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム管理者は、必要に応じて、SQL Server 管理コンソールにこのスクリプトをコピーして編集することができます。</span><span class="sxs-lookup"><span data-stu-id="4fd37-129">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the SQL Server Management Console to edit it, if necessary.</span></span> <span data-ttu-id="4fd37-130">SQL Server スクリプトの準備については、「 [Oracle CDC 表示スクリプト用の SQL Server の準備](prepare-sql-server-for-oracle-cdc-view-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fd37-130">For more information about the Prepare SQL Server Script, see [Prepare SQL Server for Oracle CDC-View Script](prepare-sql-server-for-oracle-cdc-view-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd37-131">参照</span><span class="sxs-lookup"><span data-stu-id="4fd37-131">See Also</span></span>  
 <span data-ttu-id="4fd37-132">[CDC Service の操作方法](work-with-cdc-services.md) </span><span class="sxs-lookup"><span data-stu-id="4fd37-132">[How to Work with CDC Services](work-with-cdc-services.md) </span></span>  
 [<span data-ttu-id="4fd37-133">CDC 用に SQL Server を準備する方法</span><span class="sxs-lookup"><span data-stu-id="4fd37-133">How to Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
