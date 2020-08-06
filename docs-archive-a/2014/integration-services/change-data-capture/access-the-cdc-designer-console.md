---
title: CDC デザイナー コンソールへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4f6e4df0a514cb29e36bcd1270b2537dc3ba68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741201"
---
# <a name="access-the-cdc-designer-console"></a><span data-ttu-id="93bf9-102">CDC デザイナー コンソールへのアクセス</span><span class="sxs-lookup"><span data-stu-id="93bf9-102">Access the CDC Designer Console</span></span>
  <span data-ttu-id="93bf9-103">CDC デザイナー コンソールには、コンソールをインストールしたコンピューターからアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="93bf9-103">You can access the CDC Designer Console from the computer where you installed the console.</span></span> <span data-ttu-id="93bf9-104">インストールの詳細については、インストールを参照してください。</span><span class="sxs-lookup"><span data-stu-id="93bf9-104">For more information about installation, see Installation.</span></span>  
  
 <span data-ttu-id="93bf9-105">CDC デザイナー コンソールを開くと、[SQL Server への接続] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="93bf9-105">When you open the CDC Designer Console, the Connect to SQL Server dialog box opens.</span></span>  
  
 <span data-ttu-id="93bf9-106">CDC デザイナーにアクセスする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインには、MSXDBCDC データベースに対する UPDATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="93bf9-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that accesses the CDC Designer must have UPDATE permissions on the MSXDBCDC database.</span></span> <span data-ttu-id="93bf9-107">また、新しい Oracle CDC インスタンスを作成するには、ログインが `dbcreator` 固定サーバー ロールを持っている必要もあります。</span><span class="sxs-lookup"><span data-stu-id="93bf9-107">In addition, the login must also have the `dbcreator` fixed-server role to create new Oracle CDC Instances.</span></span> <span data-ttu-id="93bf9-108">また、使用する CDC データベースへの SELECT アクセス権がログインに含まれていることも推奨されます。このアクセス権が含まれていない場合、ユーザーはそれらのデータベースの状態を表示できません。</span><span class="sxs-lookup"><span data-stu-id="93bf9-108">It is recommended that the login also have SELECT access to the CDC databases being used or the user will not be able to view the state of those databases.</span></span>  
  
 <span data-ttu-id="93bf9-109">[SQL Server への接続] ダイアログ ボックスに次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="93bf9-109">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="93bf9-110">サーバー名</span><span class="sxs-lookup"><span data-stu-id="93bf9-110">Server Name</span></span>  
 <span data-ttu-id="93bf9-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="93bf9-111">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="93bf9-112">認証</span><span class="sxs-lookup"><span data-stu-id="93bf9-112">Authentication</span></span>  
 <span data-ttu-id="93bf9-113">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="93bf9-113">Select one of the following:</span></span>  
  
-   <span data-ttu-id="93bf9-114">**[Windows 認証]**</span><span class="sxs-lookup"><span data-stu-id="93bf9-114">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="93bf9-115">**[SQL Server 認証]** : このオプションを選択する場合、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザーの **[ログイン]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93bf9-115">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="93bf9-116">ログインには、MSXCDCDB データベースへのアクセスを許可するデータベース ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="93bf9-116">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="93bf9-117">また、使用する追加のデータベースへのアクセスがログインに含まれていることも推奨されます。このアクセスが含まれていない場合、ユーザーはそれらのデータベース内のデータを表示できません。</span><span class="sxs-lookup"><span data-stu-id="93bf9-117">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
### <a name="options"></a><span data-ttu-id="93bf9-118">Options</span><span class="sxs-lookup"><span data-stu-id="93bf9-118">Options</span></span>  
 <span data-ttu-id="93bf9-119">矢印をクリックして、構成するオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="93bf9-119">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="93bf9-120">これらのオプションを既定値のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="93bf9-120">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="93bf9-121">使用可能なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="93bf9-121">The available options are:</span></span>  
  
 <span data-ttu-id="93bf9-122">**[接続タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="93bf9-122">**Connection Timeout**</span></span>  
 <span data-ttu-id="93bf9-123">CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。</span><span class="sxs-lookup"><span data-stu-id="93bf9-123">Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
 <span data-ttu-id="93bf9-124">**[実行タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="93bf9-124">**Execution Timeout**</span></span>  
 <span data-ttu-id="93bf9-125">Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。</span><span class="sxs-lookup"><span data-stu-id="93bf9-125">Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
 <span data-ttu-id="93bf9-126">**[暗号化接続]**</span><span class="sxs-lookup"><span data-stu-id="93bf9-126">**Encrypt Connection**</span></span>  
 <span data-ttu-id="93bf9-127">Oracle CDC Service とターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの間の暗号化された接続を使用した通信に対しては、 **[暗号化接続]** を選択します。 **[詳細設定]** : 必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="93bf9-127">Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="93bf9-128">**詳細**</span><span class="sxs-lookup"><span data-stu-id="93bf9-128">**Advanced**</span></span>  
 <span data-ttu-id="93bf9-129">必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="93bf9-129">Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="93bf9-130">[高度な接続プロパティ] ダイアログ ボックスの詳細については、「 [高度な接続プロパティ](advanced-connection-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93bf9-130">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bf9-131">参照</span><span class="sxs-lookup"><span data-stu-id="93bf9-131">See Also</span></span>  
 [<span data-ttu-id="93bf9-132">CDC デザイナーで使用する SQL Server 接続に必要なアクセス許可</span><span class="sxs-lookup"><span data-stu-id="93bf9-132">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
