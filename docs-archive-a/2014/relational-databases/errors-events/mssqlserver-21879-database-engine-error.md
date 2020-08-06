---
title: MSSQLSERVER_21879 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21879 (Database Engine error)
ms.assetid: fcfab735-05ca-423a-89f1-fdee7e2ed8c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 08c5d4f45faf94d555ed7acedd90cc55ec4791ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718194"
---
# <a name="mssqlserver_21879"></a><span data-ttu-id="1967f-102">MSSQLSERVER_21879</span><span class="sxs-lookup"><span data-stu-id="1967f-102">MSSQLSERVER_21879</span></span>
    
## <a name="details"></a><span data-ttu-id="1967f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="1967f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1967f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="1967f-104">Product Name</span></span>|<span data-ttu-id="1967f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1967f-105">SQL Server</span></span>|  
|<span data-ttu-id="1967f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1967f-106">Event ID</span></span>|<span data-ttu-id="1967f-107">21879</span><span class="sxs-lookup"><span data-stu-id="1967f-107">21879</span></span>|  
|<span data-ttu-id="1967f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="1967f-108">Event Source</span></span>|<span data-ttu-id="1967f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1967f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1967f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1967f-110">Component</span></span>|<span data-ttu-id="1967f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1967f-111">SQLEngine</span></span>|  
|<span data-ttu-id="1967f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="1967f-112">Symbolic Name</span></span>|<span data-ttu-id="1967f-113">SQLErrorNum21879</span><span class="sxs-lookup"><span data-stu-id="1967f-113">SQLErrorNum21879</span></span>|  
|<span data-ttu-id="1967f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="1967f-114">Message Text</span></span>|<span data-ttu-id="1967f-115">元のパブリッシャー '%s' およびパブリッシャー データベース '%s' をリダイレクトされたサーバー '%s' でクエリできないため、リモート サーバーの名前を特定できません。エラー %d、エラー メッセージ '%s'。</span><span class="sxs-lookup"><span data-stu-id="1967f-115">Unable to query the redirected server '%s' for original publisher '%s' and publisher database '%s' to determine the name of the remote server; Error %d, Error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1967f-116">説明</span><span class="sxs-lookup"><span data-stu-id="1967f-116">Explanation</span></span>  
 <span data-ttu-id="1967f-117">`sp_validate_redirected_publisher` は、リモート サーバーの名前を検出するため、一時リンク サーバーを作成し、これを使用してリダイレクトされたパブリッシャーに接続します。</span><span class="sxs-lookup"><span data-stu-id="1967f-117">`sp_validate_redirected_publisher` uses a temporary linked server that it creates to connect to the redirected publisher in order to discover the name of the remote server.</span></span> <span data-ttu-id="1967f-118">リンク サーバー クエリが失敗すると、エラー 21879 が返されます。</span><span class="sxs-lookup"><span data-stu-id="1967f-118">Error 21879 is returned when the linked server query fails.</span></span> <span data-ttu-id="1967f-119">リモート サーバー名を要求する呼び出しは通常、一時リンク サーバーを最初に使用するため、接続の問題がある場合はこの呼び出しで初めて問題が現れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1967f-119">The call to request the remote server name is typically the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with this call.</span></span> <span data-ttu-id="1967f-120">このリモート呼び出しは単に、リモート サーバーで select `@@servername` を実行します。</span><span class="sxs-lookup"><span data-stu-id="1967f-120">This remote call simply executes select `@@servername` at the remote server.</span></span>  
  
 <span data-ttu-id="1967f-121">リダイレクトされたパブリッシャーにクエリを実行するために使用されるリンク サーバーは、元のパブリッシャーに対して `sp_adddistpublisher` を呼び出したときに指定したセキュリティ モード、ログイン、およびパスワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="1967f-121">The linked server used to query the redirected publisher uses the security mode, login, and password supplied when `sp_adddistpublisher` was called for the original publisher.</span></span>  
  
-   <span data-ttu-id="1967f-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した場合 (セキュリティ モード 0)、リモート サーバーへの接続には指定されたログインおよびパスワードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1967f-122">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication was used (security mode 0) then the login and password specified are used to connect to the remote server.</span></span>  
  
-   <span data-ttu-id="1967f-123">Windows 認証を使用した場合 (セキュリティ モード 1)、接続にはセキュリティ接続が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1967f-123">If Windows authentication was used (security mode 1) a trusted connection is used for the connection.</span></span>  
  
    -   <span data-ttu-id="1967f-124">`sp_validate_redirected_publisher` がユーザーによって明示的に呼び出された場合、接続にはユーザーが実行している Windows ログインが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1967f-124">If `sp_validate_redirected_publisher` is called explicitly by a user, the Windows login that the user is running under is used for the connection.</span></span>  
  
    -   <span data-ttu-id="1967f-125">`sp_validate_redirected_`publisher がレプリケーション エージェントによって `sp_get_redirected_publisher` から呼び出された場合、エージェントに関連付けられている Windows ログインが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1967f-125">If `sp_validate_redirected_`publisher is called by a replication agent from `sp_get_redirected_publisher`, the Windows login associated with the agent is used.</span></span>  
  
 <span data-ttu-id="1967f-126">エラー 21879 は、リダイレクトされた対象のパブリッシャーで認識されないログインを使用して `sp_validate_redirected_publisher` が呼び出されたことを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1967f-126">Error 21879 can indicate that `sp_validate_redirected_publisher` was called using a login that is not known at the redirected target publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1967f-127">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="1967f-127">User Action</span></span>  
 <span data-ttu-id="1967f-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインまたは Windows 認証ログインが可用性グループ レプリカのすべてで有効であり、パブリッシャー データベースのサブスクリプション メタデータ テーブル (syssubscriptions および sysmergesubscriptions) にアクセスするための十分な権限があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1967f-128">Make certain that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication login or the Windows authentication login is valid at all of the availability group replicas and has sufficient authorization to access the subscription metadata tables (syssubscriptions and sysmergesubscriptions) in the publisher database.</span></span>  
  
 <span data-ttu-id="1967f-129">ディストリビューター以外のノードで実行されているレプリケーション エージェント (サブスクライバーで実行されているマージ エージェントなど) によって開始された `sp_get_redirected_publisher` に対する呼び出しからエラー 21879 が返される場合、特別な注意事項があります。</span><span class="sxs-lookup"><span data-stu-id="1967f-129">There are special considerations when error 21879 is returned from a call to `sp_get_redirected_publisher` that is initiated by a replication agent running on a node other that the distributor; such as a merge agent running at a subscriber.</span></span> <span data-ttu-id="1967f-130">リダイレクトされたパブリッシャーへの接続に Windows 認証が使用される場合、接続を正常に確立するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に Kerberos 認証を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1967f-130">If Windows authentication is used for the connection to the redirected publisher, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured for Kerberos authentication for the connection to be successfully established.</span></span> <span data-ttu-id="1967f-131">Windows 認証が使用され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に Kerberos 認証が構成されていない場合、サブスクライバーで実行されているマージ エージェントは、'NT AUTHORITY\ANONYMOUS LOGON' ログインが失敗したことを示すエラー 18456 を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1967f-131">When Windows authentication is used and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not configured for Kerberos authentication, error 18456 indicating that the 'NT AUTHORITY\ANONYMOUS LOGON' login failed, is received by a merge agent running at a subscriber.</span></span> <span data-ttu-id="1967f-132">この問題を解決するには、以下の 3 種類の方法があります。</span><span class="sxs-lookup"><span data-stu-id="1967f-132">There are three possible ways to address this issue:</span></span>  
  
-   <span data-ttu-id="1967f-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に Kerberos 認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="1967f-133">Configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Kerberos authentication.</span></span> <span data-ttu-id="1967f-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「**Kerberos 認証と SQL Server**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1967f-134">See **Kerberos Authentication and SQL Server** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="1967f-135">を使用して、 `sp_changedistpublisher` MSdistpublishers の元のパブリッシャーに関連付けられているセキュリティモードを変更すると共に、接続に使用するログインとパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="1967f-135">Use `sp_changedistpublisher` to change the security mode associated with the original publisher in MSdistpublishers, as well as to specify a login and password to use for the connection.</span></span>  
  
-   <span data-ttu-id="1967f-136">マージエージェントコマンドラインでコマンドラインパラメーター *BypassPublisherValidation*を指定すると、 `sp_get_redirected_publisher` ディストリビューターでが呼び出されたときに検証がバイパスされます。</span><span class="sxs-lookup"><span data-stu-id="1967f-136">Specify the command line parameter *BypassPublisherValidation* on the merge agent command line to bypass validation when `sp_get_redirected_publisher` is called at the distributor.</span></span>  
  
  
