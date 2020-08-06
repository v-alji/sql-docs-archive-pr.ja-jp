---
title: Controller および Client のサービス アカウントの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62a054749f1d53323bde5c9d05a1e7632b1dda85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719268"
---
# <a name="modify-the-controller-and-client-services-accounts"></a><span data-ttu-id="a9130-102">Controller および Client のサービス アカウントの変更</span><span class="sxs-lookup"><span data-stu-id="a9130-102">Modify the Controller and Client Services Accounts</span></span>
  <span data-ttu-id="a9130-103">このトピックでは、分散再生コントローラーと分散再生クライアントのサービス アカウントを変更し、アクセス制御リスト (ACL) を再度適用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9130-103">In this topic, you will learn how to modify the Distributed Replay controller and client service accounts, and then reapply the access control lists (ACLs).</span></span>  
  
### <a name="to-start-or-stop-the-distributed-replay-services-using-computer-management"></a><span data-ttu-id="a9130-104">[コンピューターの管理] を使用して 分散再生サービスを開始または停止するには</span><span class="sxs-lookup"><span data-stu-id="a9130-104">To start or stop the Distributed Replay services using Computer Management</span></span>  
  
1.  <span data-ttu-id="a9130-105">分散再生サービスがインストールされているコンピューターで、コマンド プロンプトから、「`dcomcnfg`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9130-105">On the computer on which the Distributed Replay services are installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
2.  <span data-ttu-id="a9130-106">[**サービス**] をダブルクリックし、下へスクロールして [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生 \<service name> **] を右クリックし、[**開始**] または [**停止\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-106">Double-click **Services**, scroll down and right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name>**, and then click **Start** or **Stop**.</span></span>  
  
### <a name="to-modify-the-distributed-replay-controller-service"></a><span data-ttu-id="a9130-107">分散再生コントローラー サービスを変更するには</span><span class="sxs-lookup"><span data-stu-id="a9130-107">To modify the Distributed Replay controller service</span></span>  
  
1.  <span data-ttu-id="a9130-108">コントローラー コンピューターで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生コントローラー サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="a9130-108">On the controller computer, stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="a9130-109">**[サービス]** で、 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生コントローラー**を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-109">Under **Services**, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller**, and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="a9130-110">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生コントローラーのプロパティ** ウィンドウの **[ログオン]** タブで、 **[このアカウント]** を選択して、新しいログオン アカウントを入力するか、 **[参照]** をクリックして新しいログオン アカウントを指定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-110">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a9130-111">**重要**:分散再生コントローラーを構成するとき、分散再生クライアント サービスの実行に使用する 1 つ以上のユーザー アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a9130-111">**Important**: When you configure Distributed Replay Controller, you can specify one or more user accounts that will be used to run the Distributed Replay Client services.</span></span> <span data-ttu-id="a9130-112">サポートされているアカウントの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a9130-112">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="a9130-113">ドメイン ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="a9130-113">Domain user account</span></span>  
  
    -   <span data-ttu-id="a9130-114">ユーザーによって作成されたローカル ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="a9130-114">User created local user account</span></span>  
  
    -   <span data-ttu-id="a9130-115">管理者</span><span class="sxs-lookup"><span data-stu-id="a9130-115">Administrator</span></span>  
  
    -   <span data-ttu-id="a9130-116">仮想アカウントおよび管理されたサービス アカウント (MSA)</span><span class="sxs-lookup"><span data-stu-id="a9130-116">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="a9130-117">ネットワーク サービス、ローカル サービス、およびシステム</span><span class="sxs-lookup"><span data-stu-id="a9130-117">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="a9130-118">グループ アカウント (ローカルまたはドメイン) およびその他の組み込みのアカウント (Everyone など) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="a9130-118">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
4.  <span data-ttu-id="a9130-119">分散再生コントローラー サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="a9130-119">Start the Distributed Replay controller service.</span></span>  
  
### <a name="to-modify-the-distributed-replay-client-service"></a><span data-ttu-id="a9130-120">分散再生クライアント サービスを変更するには</span><span class="sxs-lookup"><span data-stu-id="a9130-120">To modify the Distributed Replay client service</span></span>  
  
1.  <span data-ttu-id="a9130-121">分散再生クライアント サービスを変更する前に、変更する分散再生クライアントのサービス アカウントが、セットアップ時にコントローラー コンピューターの CTLRUSERS パラメーターに指定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a9130-121">Before you modify the Distributed Replay client service, make sure the client service account you are changing was specified during setup (in the CTLRUSERS parameter on the controller computer).</span></span> <span data-ttu-id="a9130-122">変更する分散再生クライアントのサービス アカウントがセットアップ時に指定されていない場合は、先に次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9130-122">If the client service account you are changing was not specified during setup, you must perform the following steps first:</span></span>  
  
    1.  <span data-ttu-id="a9130-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生コントローラー サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="a9130-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
    2.  <span data-ttu-id="a9130-124">分散再生コントローラー サービスがインストールされているコントローラー コンピューターで、コマンド プロンプトから、「`dcomcnfg`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9130-124">On the controller computer on which the controller service is installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
    3.  <span data-ttu-id="a9130-125">**[コンポーネント サービス]** ウィンドウで、 **[コンソール ルート]、[コンポーネント サービス]、[コンピューター]、[マイ コンピューター]、[DCOM 構成]、[DReplayController]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="a9130-125">In the **Component Services** window, navigate to **Console Root -> Component Services -> Computers -> My Computer -> DCOM Config ->DReplayController**.</span></span>  
  
    4.  <span data-ttu-id="a9130-126">**[DReplayController]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-126">Right-click **DReplayController**, and then click **Properties**.</span></span>  
  
    5.  <span data-ttu-id="a9130-127">**[DReplayController のプロパティ]** ウィンドウの **[セキュリティ]** タブで、 **[起動とアクティブ化のアクセス許可]** セクションの **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-127">In the **DReplayController Properties** window, on the **Security** tab, click **Edit** in the **Launch and Activation Permissions** section.</span></span>  
  
    6.  <span data-ttu-id="a9130-128">新しいクライアント サービス ログオン アカウントに **ローカルとリモートからのアクティブ化** 権限を与え、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-128">Grant the new client service logon account **Local and Remote activation** permissions, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="a9130-129">**[アクセス許可]** セクションの **[編集]** をクリックし、新しいクライアント サービス ログオン アカウントに **ローカルとリモートのアクセス権限** を与え、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-129">Click **Edit** in the **Access Permissions** section, and grant the new client service logon account **Local and Remote access** permissions, and then click **OK**.</span></span>  
  
    8.  <span data-ttu-id="a9130-130">**[OK]** をクリックして、 **[DReplayController のプロパティ]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a9130-130">Click **OK** to close the **DReplayController Properties** window.</span></span>  
  
    9. <span data-ttu-id="a9130-131">コントローラー コンピューターで、変更したクライアント サービス ログオン アカウントを **Distributed COM Users** グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="a9130-131">On the controller computer, add the changed client service logon account to the **Distributed COM Users** group.</span></span>  
  
    10. <span data-ttu-id="a9130-132">SQL Server 分散再生コントローラー サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="a9130-132">Start the SQL Server Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="a9130-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生クライアント サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="a9130-133">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service.</span></span>  
  
3.  <span data-ttu-id="a9130-134">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生クライアントのプロパティ** ウィンドウの **[ログオン]** タブで、 **[このアカウント]** を選択して、新しいログオン アカウントを入力するか、 **[参照]** をクリックして新しいログオン アカウントを指定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9130-134">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="a9130-135">分散再生クライアント サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="a9130-135">Start the Distributed Replay client service.</span></span>  
  
  
