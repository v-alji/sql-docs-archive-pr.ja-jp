---
title: '[サーバーへの接続] (データベース エンジン) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectoserverunknownservertype.f1
- sql12.swb.connection.login.sqlserver.f1
- sql12.swb.connection.login.sqlce.f1
- sql12.swb.manageSS2k.f1
- sql12.swb.connecttoce.f1
- sql12.swb.connecttoce.connectionproperties.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca227d1a3bbc13160962ba2fcad23ff011c950f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717258"
---
# <a name="connect-to-server-database-engine"></a><span data-ttu-id="4f29f-102">[サーバーへの接続] (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="4f29f-102">Connect to Server (Database Engine)</span></span>
  <span data-ttu-id="4f29f-103">このダイアログを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] に接続するときのオプションを表示または指定できます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="4f29f-104">ほとんどの場合、 **[サーバー名]** ボックスにデータベース サーバーのコンピューター名を入力し、 **[接続]** をクリックすることで接続できます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-104">In most cases, you can connect by entering the computer name of the database server in the **Server name** box and then clicking **Connect**.</span></span> <span data-ttu-id="4f29f-105">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]に接続している場合、コンピューター名の後に **\sqlexpress**を付けて使用します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-105">If you are connecting to [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], use the computer name followed by **\sqlexpress**.</span></span>  
  
 <span data-ttu-id="4f29f-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続する機能に影響する要因は多数あります。</span><span class="sxs-lookup"><span data-stu-id="4f29f-106">Many factors can affect your ability to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="4f29f-107">Options</span><span class="sxs-lookup"><span data-stu-id="4f29f-107">Options</span></span>  
 <span data-ttu-id="4f29f-108">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="4f29f-108">**Server type**</span></span>  
 <span data-ttu-id="4f29f-109">オブジェクト エクスプローラーからサーバーを登録するときは、接続するサーバーの種類 ( [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、または [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]) を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-109">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="4f29f-110">ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-110">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="4f29f-111">[登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-111">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="4f29f-112">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../../includes/ssde-md.md)]]、[ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]]、[ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]]、[ [!INCLUDE[ssEW](../../includes/ssew-md.md)]]、または [ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f29f-112">To register a different type of server, select [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)], or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="4f29f-113">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="4f29f-113">**Server name**</span></span>  
 <span data-ttu-id="4f29f-114">接続するサーバー インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-114">Select the server instance to connect to.</span></span> <span data-ttu-id="4f29f-115">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-115">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f29f-116">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のアクティブなユーザー インスタンスに接続するには、パイプ名を指定した名前付きパイプ プロトコル (np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query など) を使用して接続します。詳細については、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f29f-116">To connect to an active user instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] connect using named pipes protocol specifying the pipe name, such as np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query For more information, see the [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="4f29f-117">**認証**</span><span class="sxs-lookup"><span data-stu-id="4f29f-117">**Authentication**</span></span>  
 <span data-ttu-id="4f29f-118">のインスタンスに接続するときに、2つの認証モードを使用でき [!INCLUDE[ssDE](../../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-118">Two authentication modes are available when connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="4f29f-119">**Windows 認証モード ([Windows 認証])**</span><span class="sxs-lookup"><span data-stu-id="4f29f-119">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="4f29f-120">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-120">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="4f29f-121">**SQL Server 認証**</span><span class="sxs-lookup"><span data-stu-id="4f29f-121">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="4f29f-122">指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="4f29f-122">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="4f29f-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログイン アカウントが設定されていない場合、認証は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-123">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4f29f-124">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-124">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="4f29f-125">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="4f29f-125">**User name**</span></span>  
 <span data-ttu-id="4f29f-126">接続に使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-126">Enter the user name to connect with.</span></span> <span data-ttu-id="4f29f-127">このオプションは、Windows 認証を使用した接続を選択した場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-127">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="4f29f-128">**Login**</span><span class="sxs-lookup"><span data-stu-id="4f29f-128">**Login**</span></span>  
 <span data-ttu-id="4f29f-129">接続に使用するログインを入力します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-129">Enter the login to connect with.</span></span> <span data-ttu-id="4f29f-130">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続が指定されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-130">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="4f29f-131">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="4f29f-131">**Password**</span></span>  
 <span data-ttu-id="4f29f-132">ログインのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-132">Enter the password for the login.</span></span> <span data-ttu-id="4f29f-133">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合のみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-133">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="4f29f-134">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="4f29f-134">**Connect**</span></span>  
 <span data-ttu-id="4f29f-135">クリックすると、上記で選択したサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="4f29f-135">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="4f29f-136">**Options**</span><span class="sxs-lookup"><span data-stu-id="4f29f-136">**Options**</span></span>  
 <span data-ttu-id="4f29f-137">クリックすると、サーバーの登録やパスワードの保存など、追加のサーバー接続オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f29f-137">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
