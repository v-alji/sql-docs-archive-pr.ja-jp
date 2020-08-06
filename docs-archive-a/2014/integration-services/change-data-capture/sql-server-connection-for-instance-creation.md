---
title: インスタンスの作成のための SQL Server 接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cdff17b763257c2a3280981c1f5c16040cc61413
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633270"
---
# <a name="sql-server-connection-for-instance-creation"></a><span data-ttu-id="a30ce-102">インスタンスの作成のための SQL サーバー接続</span><span class="sxs-lookup"><span data-stu-id="a30ce-102">SQL Server Connection for Instance Creation</span></span>
  <span data-ttu-id="a30ce-103">Oracle CDC インスタンスを作成するときの最初の手順の 1 つは、ターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CDC データベースを作成することです。</span><span class="sxs-lookup"><span data-stu-id="a30ce-103">One of the first steps when creating an Oracle CDC Instance is the creation of a CDC database on the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="a30ce-104">この CDC データベースは、SQL Server CDC に対して有効になります。このように有効にするには、ログインが `sysadmin` 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a30ce-104">This CDC database is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="a30ce-105">**Oracle CDC インスタンスの作成** ウィザードを開始したユーザーが `sysadmin` 固定サーバー ロールのメンバーではない場合、 **[SQL Server への接続]** ダイアログ ボックスが表示され、SQL Server CDC に対してデータベースを有効にするタスクを実行するために `sysadmin` ロールのメンバーの資格情報を入力するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="a30ce-105">When a user that starts the **Create an Oracle CDC Instance** wizard is not a member of the `sysadmin` fixed-server role, the **Connect to SQL Server** dialog box opens and requests the credentials for a member of the `sysadmin` role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="a30ce-106">CDC データベースが作成されると、 `sysadmin` ログインは破棄され、Oracle デザイナー コンソールが入力されたときに使用された元の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインで作業が再開されます。</span><span class="sxs-lookup"><span data-stu-id="a30ce-106">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="a30ce-107">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="a30ce-107">Task List</span></span>  
 <span data-ttu-id="a30ce-108">**[SQL Server への接続]** ダイアログ ボックスに次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="a30ce-108">Enter the following information in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="a30ce-109">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="a30ce-109">**Server Name**</span></span>  
 <span data-ttu-id="a30ce-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a30ce-110">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
 <span data-ttu-id="a30ce-111">**認証**</span><span class="sxs-lookup"><span data-stu-id="a30ce-111">**Authentication**</span></span>  
 <span data-ttu-id="a30ce-112">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="a30ce-112">Select one of the following:</span></span>  
  
-   <span data-ttu-id="a30ce-113">**[Windows 認証]**</span><span class="sxs-lookup"><span data-stu-id="a30ce-113">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="a30ce-114">**[SQL Server 認証]** : このオプションを選択する場合、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザーの **[ログイン]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a30ce-114">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="a30ce-115">ログインには、MSXCDCDB データベースへのアクセスを許可するデータベース ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="a30ce-115">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="a30ce-116">また、使用する追加のデータベースへのアクセスがログインに含まれていることも推奨されます。このアクセスが含まれていない場合、ユーザーはそれらのデータベース内のデータを表示できません。</span><span class="sxs-lookup"><span data-stu-id="a30ce-116">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
 <span data-ttu-id="a30ce-117">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="a30ce-117">**Options**</span></span>  
 <span data-ttu-id="a30ce-118">矢印をクリックして、構成するオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="a30ce-118">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="a30ce-119">これらのオプションを既定値のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a30ce-119">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="a30ce-120">使用可能なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a30ce-120">The available options are:</span></span>  
  
-   <span data-ttu-id="a30ce-121">**[接続タイムアウト]** : CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。</span><span class="sxs-lookup"><span data-stu-id="a30ce-121">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="a30ce-122">**[実行タイムアウト]** : Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。</span><span class="sxs-lookup"><span data-stu-id="a30ce-122">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="a30ce-123">**[暗号化接続]** : Oracle CDC Service とターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの間の暗号化された接続を使用した通信に対しては、 **[暗号化接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a30ce-123">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="a30ce-124">**[詳細設定]** :必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="a30ce-124">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
     <span data-ttu-id="a30ce-125">[高度な接続プロパティ] ダイアログ ボックスの詳細については、「 [高度な接続プロパティ](advanced-connection-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a30ce-125">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30ce-126">参照</span><span class="sxs-lookup"><span data-stu-id="a30ce-126">See Also</span></span>  
 <span data-ttu-id="a30ce-127">[SQL Server 変更データベースの作成](create-the-sql-server-change-database.md) </span><span class="sxs-lookup"><span data-stu-id="a30ce-127">[Create the SQL Server Change Database](create-the-sql-server-change-database.md) </span></span>  
 [<span data-ttu-id="a30ce-128">CDC デザイナーで使用する SQL Server 接続に必要なアクセス許可</span><span class="sxs-lookup"><span data-stu-id="a30ce-128">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
