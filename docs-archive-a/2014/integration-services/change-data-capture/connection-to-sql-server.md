---
title: SQL Server への接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6639118b3bd531e5cece8899eb0d68e00e566186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633275"
---
# <a name="connection-to-sql-server"></a><span data-ttu-id="f704f-102">SQL Server への接続</span><span class="sxs-lookup"><span data-stu-id="f704f-102">Connection to SQL Server</span></span>
  <span data-ttu-id="f704f-103">MSXDBCDC データベースに対する書き込み権限を含むデータベース ロール ( **db_owner** ロールなど) を持たないログインが Oracle CDC インスタンスの作成を試みると、[SQL Server への接続] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f704f-103">When a login without a database role that includes write permission (for example the **db_owner** role) to the MSXDBCDC database attempts to create an Oracle CDC instanced, the Connect to SQL Server dialog box is displayed.</span></span>  
  
 <span data-ttu-id="f704f-104">新しい Oracle CDC インスタンスを作成するには、このダイアログ ボックスに、 **db_owner** データベース ロールなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f704f-104">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role to create the new Oracle CDC instance.</span></span>  
  
 <span data-ttu-id="f704f-105">[SQL Server への接続] ダイアログ ボックスに次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="f704f-105">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="f704f-106">サーバー名</span><span class="sxs-lookup"><span data-stu-id="f704f-106">Server Name</span></span>  
 <span data-ttu-id="f704f-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f704f-107">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="f704f-108">認証</span><span class="sxs-lookup"><span data-stu-id="f704f-108">Authentication</span></span>  
 <span data-ttu-id="f704f-109">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="f704f-109">Select one of the following:</span></span>  
  
-   <span data-ttu-id="f704f-110">[Windows 認証]</span><span class="sxs-lookup"><span data-stu-id="f704f-110">Windows Authentication</span></span>  
  
-   <span data-ttu-id="f704f-111">**[SQL Server 認証]** : このオプションを選択する場合、接続先の **のユーザーの** [ログイン] **と** [パスワード] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f704f-111">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
### <a name="options"></a><span data-ttu-id="f704f-112">オプション</span><span class="sxs-lookup"><span data-stu-id="f704f-112">Options</span></span>  
 <span data-ttu-id="f704f-113">矢印をクリックして、構成するオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="f704f-113">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="f704f-114">これらのオプションを既定値のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f704f-114">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="f704f-115">使用可能なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f704f-115">The available options are:</span></span>  
  
-   <span data-ttu-id="f704f-116">**[接続タイムアウト]** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続が確立されるまでプログラムが待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウト エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f704f-116">**Connection Timeout**: Type the time (in seconds) the program waits for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection to be established before producing a timeout error.</span></span> <span data-ttu-id="f704f-117">既定値は **15**です。</span><span class="sxs-lookup"><span data-stu-id="f704f-117">The default value is **15**.</span></span>  
  
-   <span data-ttu-id="f704f-118">**[実行タイムアウト]** : SQL コマンドの実行が完了するまでプログラムが待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウト エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f704f-118">**Execution Timeout**: Type the time (in seconds) that the program waits for SQL command execution to finish before producing a timeout error.</span></span> <span data-ttu-id="f704f-119">既定値は、 **30**です。</span><span class="sxs-lookup"><span data-stu-id="f704f-119">The default value is **30**.</span></span>  
  
-   <span data-ttu-id="f704f-120">**[暗号化接続]** : 確立する **への接続を暗号化してプライバシーを保証するには、** [暗号化接続] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f704f-120">**Encrypt Connection**: Select **Encrypt Connection** to ensure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection that being established is encrypted to guarantee privacy.</span></span>  
  
-   <span data-ttu-id="f704f-121">**[詳細設定]** : 必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="f704f-121">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f704f-122">参照</span><span class="sxs-lookup"><span data-stu-id="f704f-122">See Also</span></span>  
 [<span data-ttu-id="f704f-123">CDC Service で使用する SQL Server 接続に必要なアクセス許可</span><span class="sxs-lookup"><span data-stu-id="f704f-123">SQL Server Connection Required Permissions for the CDC Service</span></span>](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
