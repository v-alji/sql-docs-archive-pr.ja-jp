---
title: フルテキスト フィルター デーモン ランチャーのサービス アカウントの設定 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], FDHOST Launcher (MSSQLFDLauncher) service account
- FDHOST Launcher (MSSQLFDLauncher) [SQL Server]
ms.assetid: 3ab1d101-7ae0-488f-9b57-468e2517b737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d69e68f0b00e760c4b11d1f842f22911ac8dd2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633036"
---
# <a name="set-the-service-account-for-the-full-text-filter-daemon-launcher"></a><span data-ttu-id="0220c-102">フルテキスト フィルター デーモン ランチャーのサービス アカウントの設定</span><span class="sxs-lookup"><span data-stu-id="0220c-102">Set the Service Account for the Full-text Filter Daemon Launcher</span></span>
  <span data-ttu-id="0220c-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、SQL フルテキスト フィルター デーモン ランチャー サービス (MSSQLFDLauncher) のサービス アカウントを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0220c-103">This topic describes how to set the service account for the SQL Full-text Filter Daemon Launcher service (MSSQLFDLauncher) by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="0220c-104">SQL フルテキスト フィルター デーモン ランチャー サービスは、ssNoVersion のフルテキスト検索でフィルター処理や単語区切りを行うフィルター デーモン ホスト プロセスを開始するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0220c-104">The SQL Full-text Filter Daemon Launcher service is used by full-text search ssNoVersionto start the filter daemon host process, which handles full-text search filtering and word breaking.</span></span> <span data-ttu-id="0220c-105">フルテキスト検索を使用するには、このサービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0220c-105">This service must be running to use full-text search.</span></span>  
  
 <span data-ttu-id="0220c-106">SQL フルテキスト フィルター デーモン ランチャー サービスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のインスタンスに関連付けられているインスタンス対応のサービスです。</span><span class="sxs-lookup"><span data-stu-id="0220c-106">The SQL Full-text Filter Daemon Launcher service is an instance-aware service that is associated with a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0220c-107">SQL フルテキスト フィルター デーモン ランチャー サービスにより、各フィルター デーモン ホスト プロセスにサービス アカウント情報が反映されます。</span><span class="sxs-lookup"><span data-stu-id="0220c-107">The SQL Full-text Filter Daemon Launcher service propagates the service account information to each filter daemon host process.</span></span>  
  
  
##  <a name="setting-the-service-account"></a><a name="setting"></a><span data-ttu-id="0220c-108">サービスアカウントの設定</span><span class="sxs-lookup"><span data-stu-id="0220c-108">Setting the Service Account</span></span>  
  
#### <a name="to-set-the-sql-full-text-filter-daemon-launcher-service-account-for-full-text-search"></a><span data-ttu-id="0220c-109">フルテキスト検索の SQL フルテキスト フィルター デーモン ランチャー サービス アカウントを設定するには</span><span class="sxs-lookup"><span data-stu-id="0220c-109">To set the SQL Full-text Filter Daemon Launcher service account for full-text search</span></span>  
  
1.  <span data-ttu-id="0220c-110">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0220c-110">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="0220c-111">**SQL Server 構成マネージャー**で、[**サービスの SQL Server**] をクリックし、 **SQL フルテキストフィルターデーモンランチャー ( *`instance name`* )** を右クリックして、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0220c-111">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click **SQL Full-text Filter Daemon Launcher (*`instance name`*)**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0220c-112">ダイアログ ボックスの **[ログオン]** タブをクリックし、SQL フルテキスト フィルター デーモン ランチャー サービスによって作成される各プロセスについて、その実行に使用するアカウントを選択または入力します。</span><span class="sxs-lookup"><span data-stu-id="0220c-112">Click the **Log On** tab of the dialog box, and then select or enter the account under which to run each process created by the SQL Full-text Filter Daemon Launcher service.</span></span>  
  
4.  <span data-ttu-id="0220c-113">ダイアログ ボックスを閉じた後、 **[再起動]** をクリックすると、SQL フルテキスト フィルター デーモン ランチャー サービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="0220c-113">After you close the dialog box, click **Restart** to restart the SQL Full-text Filter Daemon Launcher service.</span></span>  
  
  
##  <a name="if-the-sql-full-text-filter-daemon-launcher-service-does-not-start"></a><a name="error"></a><span data-ttu-id="0220c-114">SQL フルテキストフィルターデーモンランチャーサービスが開始されない場合</span><span class="sxs-lookup"><span data-stu-id="0220c-114">If the SQL Full-text Filter Daemon Launcher Service Does Not Start</span></span>  
 <span data-ttu-id="0220c-115">SQL フルテキスト フィルター デーモン ランチャー サービスが開始されない場合は、次の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="0220c-115">If the SQL Full-text Filter Daemon Launcher service does not start, one or more of the following might be the cause:</span></span>  
  
-   <span data-ttu-id="0220c-116">SQL フルテキスト フィルター デーモン ランチャー サービスのアカウントに関連付けられたパスワードの期限が切れている。</span><span class="sxs-lookup"><span data-stu-id="0220c-116">The password associated with the SQL Full-text Filter Daemon Launcher service account has expired.</span></span>  
  
     <span data-ttu-id="0220c-117">SQL フルテキスト フィルター デーモン ランチャー サービスにローカル ユーザー アカウントを使用している場合にパスワードの期限が切れたときは、次の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0220c-117">If you use a local user account for the SQL Full-text Filter Daemon Launcher service and your password expires, you need to:</span></span>  
  
    1.  <span data-ttu-id="0220c-118">アカウントに新しい Windows パスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="0220c-118">Set a new Windows password for the account.</span></span>  
  
    2.  <span data-ttu-id="0220c-119">新しいパスワードが使用されるように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで SQL フルテキスト フィルター デーモン ランチャー サービスを更新します。</span><span class="sxs-lookup"><span data-stu-id="0220c-119">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, update the SQL Full-text Filter Daemon Launcher service to use the new password.</span></span>  
  
-   <span data-ttu-id="0220c-120">サービス アカウントのユーザー アカウントまたはパスワードが正しくない。</span><span class="sxs-lookup"><span data-stu-id="0220c-120">The user account or password of the service account is incorrect.</span></span>  
  
     <span data-ttu-id="0220c-121">SQL フルテキスト フィルター デーモン ランチャー サービスが、正しくないユーザー アカウントおよびパスワードでログインしようとしている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0220c-121">The SQL Full-text Filter Daemon Launcher service might attempt to log in with an incorrect user account and password.</span></span> <span data-ttu-id="0220c-122">上記の手順に従って、サービスのユーザー アカウントが変更されていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0220c-122">Follow the procedures above to verify that the user account for the service has not been changed.</span></span>  
  
-   <span data-ttu-id="0220c-123">サービスへのログインに使用されるアカウントに権限がない。</span><span class="sxs-lookup"><span data-stu-id="0220c-123">The account used to log in to the service does not have privileges.</span></span>  
  
     <span data-ttu-id="0220c-124">サーバー インスタンスがインストールされているコンピューターに対するログイン権限のないアカウントを使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0220c-124">You might be using an account that does not have login privileges on the computer where the server instance is installed.</span></span> <span data-ttu-id="0220c-125">ローカル コンピューターのユーザー権利および権限を持つアカウントでログインしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0220c-125">Verify that you are logging in with an account that has User rights and permissions on the local computer.</span></span>  
  
-   <span data-ttu-id="0220c-126">同じ名前付きパイプの別のインスタンスが既に実行されている。</span><span class="sxs-lookup"><span data-stu-id="0220c-126">Another instance of the same named pipe is already running.</span></span>  
  
     <span data-ttu-id="0220c-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスは、SQL フルテキスト フィルター デーモン ランチャー サービス クライアントの名前付きパイプ サーバーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="0220c-127">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service acts as a named pipe server for the SQL Full-text Filter Daemon Launcher service client.</span></span> <span data-ttu-id="0220c-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が開始される前に名前付きパイプが別のプロセスで作成されていると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと Windows イベント ログにエラーが記録され、フルテキスト検索を使用できません。</span><span class="sxs-lookup"><span data-stu-id="0220c-128">If the named pipe was already created by another process before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts, an error will be logged in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the Windows Event Log, and full-text search will not be available.</span></span>  <span data-ttu-id="0220c-129">同じ名前付きパイプを使用しようとしているプロセスまたはアプリケーションを特定し、そのアプリケーションを停止してください。</span><span class="sxs-lookup"><span data-stu-id="0220c-129">Determine what process or application is attempting to use the same named pipe and stop the application.</span></span>  
  
-   <span data-ttu-id="0220c-130">フルテキスト検索で SQL フルテキスト フィルター デーモン ランチャー サービスが正しく構成されていない。</span><span class="sxs-lookup"><span data-stu-id="0220c-130">The SQL Full-text Filter Daemon Launcher service is not configured correctly.</span></span>  
  
     <span data-ttu-id="0220c-131">サービスが、ローカル コンピューターで正しく構成されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0220c-131">The service may not be configured correctly on the local computer.</span></span>  
  
     <span data-ttu-id="0220c-132">名前付きパイプの機能がローカル コンピューターで無効になっているか、既定の名前付きパイプ以外の名前付きパイプを使用するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が構成されていると、SQL フルテキスト フィルター デーモン ランチャー サービスが開始されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="0220c-132">If named pipes functionality has been disabled on the local computer, or if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been configured to use a named pipe other than the default named pipe, the SQL Full-text Filter Daemon Launcher service might not start.</span></span>  
  
-   <span data-ttu-id="0220c-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループに、SQL フルテキスト フィルター デーモン ランチャー サービスを開始する権限がない。</span><span class="sxs-lookup"><span data-stu-id="0220c-133">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group does not have permission to start SQL Full-text Filter Daemon Launcher service.</span></span>  
  
     <span data-ttu-id="0220c-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインストール時、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループには、SQL フルテキスト フィルター デーモン ランチャー サービスを管理、クエリ、および開始する既定の権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="0220c-134">During the installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group is granted default permission to manage, query, and start the SQL Full-text Filter Daemon Launcher service.</span></span> <span data-ttu-id="0220c-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール後に SQL フルテキスト フィルター デーモン ランチャー サービス アカウントに対する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループの権限が削除されている場合、SQL フルテキスト フィルター デーモン ランチャー サービスは開始されず、フルテキスト検索は無効になります。</span><span class="sxs-lookup"><span data-stu-id="0220c-135">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group permissions to the SQL Full-text Filter Daemon Launcher service account have been removed after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, the SQL Full-text Filter Daemon Launcher service will not start, and full-text search will be disabled.</span></span> <span data-ttu-id="0220c-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループに、SQL フルテキスト フィルター デーモン ランチャー サービス アカウントに対する権限があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0220c-136">Make certain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group has permissions to the SQL Full-text Filter Daemon Launcher service account.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="0220c-137">参照</span><span class="sxs-lookup"><span data-stu-id="0220c-137">See Also</span></span>  
 [<span data-ttu-id="0220c-138">サービスの管理方法に関するトピック &#40;SQL Server 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="0220c-138">Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;</span></span>](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)  
 [<span data-ttu-id="0220c-139">フルテキスト検索のアップグレード</span><span class="sxs-lookup"><span data-stu-id="0220c-139">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)  
  
  
