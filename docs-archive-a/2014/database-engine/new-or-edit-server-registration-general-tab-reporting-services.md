---
title: 新規または編集サーバーの登録 ([全般] タブ) (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.reportserver.f1
ms.assetid: 5f899a8e-52ef-46b5-b7a9-f200ccd9f724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 195756498dcefe4686d4b06e758dba9919c0b304
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644624"
---
# <a name="new-or-edit-server-registration-general-tab-reporting-services"></a><span data-ttu-id="0231e-102">[新規サーバーの登録] または [サーバー登録プロパティの編集] ([全般] タブ) (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="0231e-102">New or Edit Server Registration (General Tab) (Reporting Services)</span></span>
  <span data-ttu-id="0231e-103">このタブを使用すると、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のインスタンスを登録するときのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0231e-103">Use this tab to specify options when registering an instance of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0231e-104">このページにアクセスするには、[登録済みサーバー] で、 **[登録済みサーバー]** ツール バーの **[Reporting Services]** をクリックし、登録済みサーバー グループ ( **[Reporting Services]** など) を右クリックして、 **[新規作成]** をポイントし、 **[サーバーの登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0231e-104">To access this page, in Registered Servers, click **Reporting Services** on the **Registered Servers** toolbar, right-click any registered servers group such as **Reporting Services**, point to **New**, and then click **Server Registration**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0231e-105">Options</span><span class="sxs-lookup"><span data-stu-id="0231e-105">Options</span></span>  
 <span data-ttu-id="0231e-106">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="0231e-106">**Server type**</span></span>  
 <span data-ttu-id="0231e-107">サーバーが登録済みサーバーから登録されている場合、[**サーバーの種類**] ボックスは読み取り専用になり、[**登録済みサーバー** ] ペインに表示されているサーバーの種類と一致します。</span><span class="sxs-lookup"><span data-stu-id="0231e-107">When a server is registered from Registered Servers, the **Server type** box is read-only, and it matches the type of server displayed in the **Registered Servers** pane.</span></span> <span data-ttu-id="0231e-108">別の種類のサーバーを登録するには、 **[登録済みサーバー]** ツール バーで目的のサーバーをクリックした後で、新しいサーバーの登録を開始します。</span><span class="sxs-lookup"><span data-stu-id="0231e-108">To register a different type of server, click the server you want on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="0231e-109">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="0231e-109">**Server name**</span></span>  
 <span data-ttu-id="0231e-110">接続先のレポート サーバー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="0231e-110">Specify the report server instance to connect to.</span></span> <span data-ttu-id="0231e-111">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]では、インスタンス名を使用してレポート サーバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0231e-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], you can access a report server through its instance name.</span></span> <span data-ttu-id="0231e-112">インストールする各 SQL Server インスタンスに対して、1 つのレポート サーバー インスタンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0231e-112">You can have one report server instance for each SQL Server instance that you install.</span></span> <span data-ttu-id="0231e-113">既定のインスタンスを使用する場合は、SQL Server インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0231e-113">If you are using the default instance, type the name of the SQL Server instance.</span></span> <span data-ttu-id="0231e-114">名前付きのインスタンスを使用する場合は、レポート サーバーに接続するための名前付きインスタンスを MSSQL$InstanceName の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="0231e-114">If you are using a named instance, specify the named instance to connect to the report server in the format MSSQL$InstanceName.</span></span>  
  
 <span data-ttu-id="0231e-115">**認証**</span><span class="sxs-lookup"><span data-stu-id="0231e-115">**Authentication**</span></span>  
 <span data-ttu-id="0231e-116">レポート サーバーへの認証は、インターネット インフォメーション サービス (IIS) によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="0231e-116">Authentication to a report server is made through Internet Information Services (IIS).</span></span> <span data-ttu-id="0231e-117">Reporting Services に接続する際に、次のいずれかの認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="0231e-117">Select from one of the following authentication modes when connecting to Reporting Services:</span></span>  
  
 <span data-ttu-id="0231e-118">**Windows 認証モード ([Windows 認証])**</span><span class="sxs-lookup"><span data-stu-id="0231e-118">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="0231e-119">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 資格情報を使用して、レポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0231e-119">Connect to the report server instance using your [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows credentials.</span></span>  
  
 <span data-ttu-id="0231e-120">**基本認証**</span><span class="sxs-lookup"><span data-stu-id="0231e-120">**Basic Authentication**</span></span>  
 <span data-ttu-id="0231e-121">Reporting Services をインストールしたときに、基本認証を使用するように構成している場合は、 **基本認証** を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="0231e-121">Connect using **Basic Authentication** if your Reporting Services installation is configured to use Basic Authentication.</span></span>  
  
 <span data-ttu-id="0231e-122">**フォーム認証**</span><span class="sxs-lookup"><span data-stu-id="0231e-122">**Forms Authentication**</span></span>  
 <span data-ttu-id="0231e-123">Reporting Services をインストールしたときに、カスタム認証拡張機能を使用するように構成している場合は、 **フォーム認証** を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="0231e-123">Connect using **Forms Authentication** if your Reporting Services installation is configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="0231e-124">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="0231e-124">**User Name**</span></span>  
 <span data-ttu-id="0231e-125">接続に使用するログイン名を入力します。</span><span class="sxs-lookup"><span data-stu-id="0231e-125">Enter the login name to use for the connection.</span></span> <span data-ttu-id="0231e-126">このオプションは、 **[基本認証]** または **[フォーム認証]** を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0231e-126">This option is only available if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="0231e-127">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="0231e-127">**Password**</span></span>  
 <span data-ttu-id="0231e-128">ユーザー名に対応するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="0231e-128">Enter the password for the user name.</span></span> <span data-ttu-id="0231e-129">このオプションは、 **[基本認証]** または **[フォーム認証]** を選択した場合にのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="0231e-129">This option is only editable if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="0231e-130">**パスワードの記録**</span><span class="sxs-lookup"><span data-stu-id="0231e-130">**Remember password**</span></span>  
 <span data-ttu-id="0231e-131">入力したパスワードを保存します。</span><span class="sxs-lookup"><span data-stu-id="0231e-131">Store the password you have entered.</span></span> <span data-ttu-id="0231e-132">このオプションは、 **[基本認証]** または **[フォーム認証]** をクリックした場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0231e-132">This option is only available if you have clicked **Basic** or **Forms Authentication**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0231e-133"> いったんパスワードを保存した後に、パスワードが保存されないようにするには、このチェック ボックスをオフにしてから **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0231e-133">If you have stored the password and want to stop storing it, clear this check box and then click **Save**.</span></span>  
  
 <span data-ttu-id="0231e-134">**[登録済みサーバーの名前]**</span><span class="sxs-lookup"><span data-stu-id="0231e-134">**Registered server name**</span></span>  
 <span data-ttu-id="0231e-135">[登録済みサーバー] に表示する名前です。</span><span class="sxs-lookup"><span data-stu-id="0231e-135">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="0231e-136">この名前は、 **[サーバー名]** ボックスの名前と同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0231e-136">This name does not have to match the name in the **Server name** box.</span></span>  
  
 <span data-ttu-id="0231e-137">**[登録済みサーバーの説明]**</span><span class="sxs-lookup"><span data-stu-id="0231e-137">**Registered server description**</span></span>  
 <span data-ttu-id="0231e-138">サーバーの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="0231e-138">Enter an optional description of the server.</span></span>  
  
 <span data-ttu-id="0231e-139">**テスト**</span><span class="sxs-lookup"><span data-stu-id="0231e-139">**Test**</span></span>  
 <span data-ttu-id="0231e-140">クリックすると、 **[サーバー名]** で選択されたサーバーへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="0231e-140">Click to test the connection to the server selected in **Server name**.</span></span>  
  
 <span data-ttu-id="0231e-141">**および**</span><span class="sxs-lookup"><span data-stu-id="0231e-141">**Save**</span></span>  
 <span data-ttu-id="0231e-142">クリックすると、登録済みサーバーの設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="0231e-142">Click to save the registered server settings.</span></span>  
  
  
