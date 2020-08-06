---
title: '[サーバーへの接続](Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.reportserver.f1
ms.assetid: ef81b658-8eb5-4636-ac81-eead10cc7b9f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 10c613af00e343f1f147c4ad293dfa300a95b50d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740356"
---
# <a name="connect-to-server-reporting-services"></a><span data-ttu-id="a7001-102">[サーバーへの接続] (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="a7001-102">Connect to Server (Reporting Services)</span></span>
  <span data-ttu-id="a7001-103">このダイアログを使用すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] に接続するときのオプションを表示または指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7001-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7001-104">Options</span><span class="sxs-lookup"><span data-stu-id="a7001-104">Options</span></span>  
 <span data-ttu-id="a7001-105">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="a7001-105">**Server type**</span></span>  
 <span data-ttu-id="a7001-106">**オブジェクトエクスプローラー**からサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../includes/ssde-md.md)] 、Analysis Services、Reporting Services、または Integration Services) を選択します。</span><span class="sxs-lookup"><span data-stu-id="a7001-106">When registering a server from **Object Explorer**, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="a7001-107">ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7001-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="a7001-108">**登録済みサーバー**からサーバーを登録する場合、[**サーバーの種類**] ボックスは読み取り専用になり、[**登録済みサーバー** ] コンポーネントに表示されているサーバーの種類と一致します。</span><span class="sxs-lookup"><span data-stu-id="a7001-108">When registering a server from **Registered Servers**, the **Server type** box is read-only, and matches the type of server displayed in the **Registered Servers** component.</span></span> <span data-ttu-id="a7001-109">別の種類のサーバーを登録するには、 [!INCLUDE[ssDE](../includes/ssde-md.md)] 新しいサーバーの登録を開始する前に、[**登録済みサーバー** ] ツールバーの []、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a7001-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="a7001-110">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="a7001-110">**Server name**</span></span>  
 <span data-ttu-id="a7001-111">接続するレポート サーバー インスタンスのサーバー モードによって、入力する必要がある値が決まります。</span><span class="sxs-lookup"><span data-stu-id="a7001-111">The server mode of the report server instance you are connecting to determines the value you must enter.</span></span>  
  
 <span data-ttu-id="a7001-112">ネイティブ モードで実行されているレポート サーバーの場合、接続するレポート サーバー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7001-112">For a report server that runs in native mode, specify the report server instance to connect to.</span></span> <span data-ttu-id="a7001-113">既定のインスタンスを使用する場合、サーバー名はコンピューターの名前であるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="a7001-113">If you are using the default instance, the server name is typically the name of the computer.</span></span> <span data-ttu-id="a7001-114">名前付きインスタンスをインストールした場合は、<InstanceName という形式でサーバー名にインスタンス名を追加し \<servername> \\ \> ます。</span><span class="sxs-lookup"><span data-stu-id="a7001-114">If you installed a named instance, append the instance name to the server name in this format: \<servername>\\<InstanceName\>.</span></span> <span data-ttu-id="a7001-115">Reporting Services では、円記号を使用してインスタンス名を区切ります。</span><span class="sxs-lookup"><span data-stu-id="a7001-115">Reporting Services uses the backslash character to delimit the instance name.</span></span>  
  
 <span data-ttu-id="a7001-116">SharePoint 統合モードで実行されているレポート サーバーの場合、SharePoint サイトを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7001-116">For a report server that runs in SharePoint integrated mode, you must specify a SharePoint site.</span></span> <span data-ttu-id="a7001-117">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]と統合されているサイト コレクション内の任意のサイトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7001-117">You can specify any site in a site collection that is integrated with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="a7001-118">指定する URL には、HTTP プレフィックスまたは HTTPS プレフィックスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7001-118">The URL that you provide must include the HTTP or HTTPS prefix.</span></span> <span data-ttu-id="a7001-119">Management Studio で SharePoint サイトに接続するには、SharePoint サイトにアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7001-119">You must have permission to access the SharePoint site in order to connect to it in Management Studio.</span></span> <span data-ttu-id="a7001-120">割り当てられている権限レベルによって、表示および管理できるアイテムが決まります。</span><span class="sxs-lookup"><span data-stu-id="a7001-120">The permission level you are assigned to will determine which items you can view and manage.</span></span> <span data-ttu-id="a7001-121">詳細については、「[Management Studio でレポート サーバーに接続する](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7001-121">For more information, see [Connect to a Report Server in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md).</span></span>  
  
 <span data-ttu-id="a7001-122">**認証**</span><span class="sxs-lookup"><span data-stu-id="a7001-122">**Authentication**</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="a7001-123">を、指定したカスタム認証拡張機能によって処理する Windows 認証要求またはフォーム認証要求を受け入れるように構成できます。</span><span class="sxs-lookup"><span data-stu-id="a7001-123">can be configured to accept Windows Authentication requests or Forms authentication requests that are handled by a custom authentication extension that you provide.</span></span> <span data-ttu-id="a7001-124">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]に接続する際に、次のいずれかの認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="a7001-124">Select from one of the following authentication modes when connecting to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="a7001-125">**Windows 認証モード ([Windows 認証])**</span><span class="sxs-lookup"><span data-stu-id="a7001-125">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="a7001-126">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 資格情報を使用して、レポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a7001-126">Connect to the report server instance using your [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows credentials.</span></span>  
  
 <span data-ttu-id="a7001-127">**基本認証**</span><span class="sxs-lookup"><span data-stu-id="a7001-127">**Basic Authentication**</span></span>  
 <span data-ttu-id="a7001-128">Reporting Services をインストールしたときに、基本認証を使用するように構成している場合は、 **基本認証** を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="a7001-128">Connect using **Basic Authentication** if your Reporting Services installation is configured to use Basic Authentication.</span></span>  
  
 <span data-ttu-id="a7001-129">**フォーム認証**</span><span class="sxs-lookup"><span data-stu-id="a7001-129">**Forms Authentication**</span></span>  
 <span data-ttu-id="a7001-130">Reporting Services をインストールしたときに、カスタム認証拡張機能を使用するように構成している場合は、 **フォーム認証** を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="a7001-130">Connect using **Forms Authentication** if your Reporting Services installation is configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="a7001-131">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="a7001-131">**User Name**</span></span>  
 <span data-ttu-id="a7001-132">接続に使用するログイン名を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7001-132">Enter the login name to use for the connection.</span></span> <span data-ttu-id="a7001-133">このオプションは、 **[基本認証]** または **[フォーム認証]** を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7001-133">This option is only available if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="a7001-134">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="a7001-134">**Password**</span></span>  
 <span data-ttu-id="a7001-135">ユーザー名に対応するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="a7001-135">Enter the password for the user name.</span></span> <span data-ttu-id="a7001-136">このオプションは、 **[基本認証]** または **[フォーム認証]** を選択した場合にのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="a7001-136">This option is only editable if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="a7001-137">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="a7001-137">**Connect**</span></span>  
 <span data-ttu-id="a7001-138">クリックすると、上記で選択したサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a7001-138">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="a7001-139">**Options**</span><span class="sxs-lookup"><span data-stu-id="a7001-139">**Options**</span></span>  
 <span data-ttu-id="a7001-140">クリックすると、サーバーの登録やパスワードの保存など、追加のサーバー接続オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7001-140">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7001-141">参照</span><span class="sxs-lookup"><span data-stu-id="a7001-141">See Also</span></span>  
 <span data-ttu-id="a7001-142">[SSRS Configuration Manager &#40;レポートサーバーデータベース接続の構成&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a7001-142">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="a7001-143">[Management Studio でレポートサーバーに接続する](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a7001-143">[Connect to a Report Server in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="a7001-144">レポート サーバーでの認証</span><span class="sxs-lookup"><span data-stu-id="a7001-144">Authentication with the Report Server</span></span>](../reporting-services/security/authentication-with-the-report-server.md)  
  
  
