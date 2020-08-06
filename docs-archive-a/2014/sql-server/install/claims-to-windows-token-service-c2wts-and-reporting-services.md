---
title: Windows トークンサービスに対するクレーム (C2WTS) と Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cf2e245dfae17556bdb906c134ba0d53898a8631
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640472"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a><span data-ttu-id="b598c-102">Claims to Windows Token Service (C2WTS) と Reporting Services</span><span class="sxs-lookup"><span data-stu-id="b598c-102">Claims to Windows Token Service (C2WTS) and Reporting Services</span></span>
  <span data-ttu-id="b598c-103">Sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ファームの外部にあるデータソースに対して windows 認証を使用する場合、sharepoint モードでは、Windows トークンサービスに対する Sharepoint クレーム (c2WTS) が必要です。</span><span class="sxs-lookup"><span data-stu-id="b598c-103">The SharePoint Claims to Windows Token Service (c2WTS) is required with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode if you want to use windows authentication for Data Sources that are outside the SharePoint farm.</span></span> <span data-ttu-id="b598c-104">これは、Web フロントエンド (WFE) と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービス間の通信が常に要求認証になるため、ユーザーが Windows 認証を使用してデータ ソースにアクセスする場合にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="b598c-104">This is true even if the user accesses the data sources with Windows Authentication because the communication between the web front-end (WFE) and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service will always be Claims authentication.</span></span>  
  
 <span data-ttu-id="b598c-105">c2WTS は、データ ソースが共有サービスと同じコンピューター上にある場合でも必要です。</span><span class="sxs-lookup"><span data-stu-id="b598c-105">c2WTS is needed even if your data source(s) are on the same computer as the shared service.</span></span> <span data-ttu-id="b598c-106">ただし、このシナリオでは、制約付き委任は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b598c-106">However in this scenario, constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="b598c-107">c2WTS によって作成されたトークンは、制約付き委任 (特定のサービスへの制約) と "認証プロトコルの使用" 構成オプションでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="b598c-107">The tokens created by c2WTS will only work with constrained delegation (constrains to specific services) and the configuration option "using any authentication protocol".</span></span> <span data-ttu-id="b598c-108">既に述べたとおり、データ ソースが共有サービスと同じコンピューター上にある場合は、制約付き委任は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b598c-108">As noted earlier, if your data sources are on the same computer as the shared service, then constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="b598c-109">Kerberos の制約付き委任を使用する環境では、SharePoint Server サービスと外部データ ソースが同じ Windows ドメインに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b598c-109">If your environment will use Kerberos constrained delegation, then the SharePoint Server service and external data sources need to reside in the same Windows domain.</span></span> <span data-ttu-id="b598c-110">Claims to Windows Token Service (c2WTS) に依存する任意のサービスでは、Kerberos の **制約付き** 委任を使用して、c2WTS が Kerberos プロトコル遷移を使用して要求を Windows 資格情報に変換できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b598c-110">Any service that relies on the Claims to Windows token service (c2WTS) must use Kerberos **constrained** delegation to allow c2WTS to use Kerberos protocol transition to translate claims into Windows credentials.</span></span> <span data-ttu-id="b598c-111">これらの要件は、すべての SharePoint 共有サービスに共通です。</span><span class="sxs-lookup"><span data-stu-id="b598c-111">These requirements are true for all SharePoint Shared Services.</span></span> <span data-ttu-id="b598c-112">詳細については、「 [Microsoft SharePoint 2010 製品の Kerberos 認証の https://technet.microsoft.com/library/gg502594.aspx) 概要」 (](https://technet.microsoft.com/library/gg502594.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b598c-112">For more information, see [Overview of Kerberos authentication for Microsoft SharePoint 2010 Products  (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx).</span></span>  
  
 <span data-ttu-id="b598c-113">このトピックでは、手順をまとめています。</span><span class="sxs-lookup"><span data-stu-id="b598c-113">The procedure is summarized in this topic.</span></span>  
  
||  
|-|  
|<span data-ttu-id="b598c-114">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; sharepoint 2010</span><span class="sxs-lookup"><span data-stu-id="b598c-114">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="b598c-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="b598c-115">Prerequisites</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b598c-116">注: 構成手順によっては、変更されたり、特定のファーム トポロジで機能しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b598c-116">Note: Some of the configuration steps may change, or may not work in certain farm topologies.</span></span> <span data-ttu-id="b598c-117">たとえば、シングル サーバー インストールでは Windows Identity Foundation c2WTS サービスをサポートしていないため、Windows トークンに対するクレームの委任シナリオは、このファーム構成では可能でありません。</span><span class="sxs-lookup"><span data-stu-id="b598c-117">For instance, a single server install does not support the Windows Identity Foundation c2WTS services so claims to windows token delegation scenarios are not possible with this farm configuration.</span></span>  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a><span data-ttu-id="b598c-118">c2WTS の構成に必要な基本的な手順</span><span class="sxs-lookup"><span data-stu-id="b598c-118">Basic steps needed to configure c2WTS</span></span>  
  
1.  <span data-ttu-id="b598c-119">c2WTS サービス アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="b598c-119">Configure the c2WTS service account.</span></span> <span data-ttu-id="b598c-120">c2WTS を実行する各アプリケーション サーバーのローカルの Administrators グループにサービス アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b598c-120">Add the service account to the local Administrators group on each application server running c2WTS.</span></span> <span data-ttu-id="b598c-121">さらに、アカウントに次のローカル セキュリティ ポリシー権限があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b598c-121">In addition, verify that the account has the following local security policy rights:</span></span>  
  
    -   <span data-ttu-id="b598c-122">オペレーティング システムの一部として機能</span><span class="sxs-lookup"><span data-stu-id="b598c-122">Act as part of the operating system</span></span>  
  
    -   <span data-ttu-id="b598c-123">認証後にクライアントを借用する</span><span class="sxs-lookup"><span data-stu-id="b598c-123">Impersonate a client after authentication</span></span>  
  
    -   <span data-ttu-id="b598c-124">サービスとしてログオン</span><span class="sxs-lookup"><span data-stu-id="b598c-124">Log on as a service</span></span>  
  
     <span data-ttu-id="b598c-125">C2WTS に使用するアカウントは、プロトコル遷移を使用した制約付き委任用に構成する必要があります。また、通信に必要なサービス (SQL Server エンジン、SQL Server Analysis Services) に委任するためのアクセス許可が必要です。委任を構成するには、Active Directory ユーザーとコンピューターのスナップインを使用します。</span><span class="sxs-lookup"><span data-stu-id="b598c-125">The account you use for c2WTS also needs to be configured for Constrained Delegation with Protocol Transitioning and needs permissions to delegate to the Services it is required to communicate with (i.e. SQL Server Engine, SQL Server Analysis Services).To configure delegation you can use the Active Directory Users and Computer snap-in.</span></span>  
  
    1.  <span data-ttu-id="b598c-126">各サービス アカウントを右クリックして、プロパティ ダイアログを開きます。</span><span class="sxs-lookup"><span data-stu-id="b598c-126">Right-click each service account and open the properties dialog.</span></span> <span data-ttu-id="b598c-127">ダイアログで **[委任]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b598c-127">In the dialog click the **Delegation** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b598c-128">注: 委任タブは、オブジェクトに SPN が割り当てられている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="b598c-128">Note: the delegation tab is only visible if the object has an SPN assigned to it.</span></span> <span data-ttu-id="b598c-129">c2WTS では、c2WTS アカウントに SPN は必要ありませんが、SPN がない場合、[**委任**] タブは表示されません。</span><span class="sxs-lookup"><span data-stu-id="b598c-129">c2WTS does not require an SPN on the c2WTS Account, however, without an SPN, the **Delegation** tab will not be visible.</span></span> <span data-ttu-id="b598c-130">制約付き委任を構成する別の方法として、 **ADSIEdit**などのユーティリティを使用するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="b598c-130">An alternative way to configure constrained delegation is to use a utility such as **ADSIEdit**.</span></span>  
  
    2.  <span data-ttu-id="b598c-131">委任タブで重要な構成オプションは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b598c-131">Key configuration options on the delegation tab are the following:</span></span>  
  
        -   <span data-ttu-id="b598c-132">[指定されたサービスへの委任でのみこのユーザーを信頼する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b598c-132">Select "Trust this user for delegation to specified services only"</span></span>  
  
        -   <span data-ttu-id="b598c-133">[任意の認証プロトコルを使用する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b598c-133">Select "Use any authentication protocol"</span></span>  
  
         <span data-ttu-id="b598c-134">詳細については、ホワイトペーパー「 [SharePoint 2010 および SQL Server 2008 R2 製品の kerberos 認証の構成](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)」の「コンピューターとサービスアカウント用に kerberos の制約付き委任を構成する」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b598c-134">For more information, see the "configure Kerberos constrained delegation for computers and service accounts" section of the following white paper, [Configuring Kerberos authentication for SharePoint 2010 and SQL Server 2008 R2 products](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)</span></span>  
  
2.  <span data-ttu-id="b598c-135">C2WTS ' AllowedCallers 元 ' を構成します</span><span class="sxs-lookup"><span data-stu-id="b598c-135">Configure c2WTS 'AllowedCallers'</span></span>  
  
     <span data-ttu-id="b598c-136">c2WTS では、構成ファイルに明示的にリストされている ' 呼び出し元 ' id が必要です**c2wtshost.exe.config**。c2WTS は、そのように構成されている場合を除き、システム内のすべての認証済みユーザーからの要求を受け入れません。</span><span class="sxs-lookup"><span data-stu-id="b598c-136">c2WTS requires the 'callers' identities explicitly listed in the configuration file, **c2wtshost.exe.config**. c2WTS does not accept requests from all authenticated users in the system unless it is configured to do so.</span></span> <span data-ttu-id="b598c-137">この場合、"呼び出し元" は WSS_WPG Windows グループです。</span><span class="sxs-lookup"><span data-stu-id="b598c-137">In this case the 'caller' is the WSS_WPG Windows group.</span></span> <span data-ttu-id="b598c-138">c2wtshost.exe.confi ファイルは次の場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="b598c-138">The c2wtshost.exe.confi file is saved in the following location:</span></span>  
  
     <span data-ttu-id="b598c-139">**Files\Windows の Id Foundation\v3.5\c2wtshost.exe.config**</span><span class="sxs-lookup"><span data-stu-id="b598c-139">**\Program Files\Windows Identity Foundation\v3.5\c2wtshost.exe.config**</span></span>  
  
     <span data-ttu-id="b598c-140">構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b598c-140">The following is an example of the configuration file:</span></span>  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  <span data-ttu-id="b598c-141">オペレーティング システム c2WTS サービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="b598c-141">Start the operating system c2WTS service:</span></span>  
  
    1.  <span data-ttu-id="b598c-142">前の手順で構成したサービス アカウントを使用するようにサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="b598c-142">Configure the service to use the service account you configured in the previous step.</span></span>  
  
    2.  <span data-ttu-id="b598c-143">[スタートアップの種類] を [**自動**] に変更し、サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="b598c-143">Change the Startup type to "**Automatic**" and start the service.</span></span>  
  
4.  <span data-ttu-id="b598c-144">SharePoint の [Windows トークンサービスに対する要求] を開始する: [**サーバーのサービスの管理**] ページで、sharepoint サーバーの全体管理を使用して、Windows トークンサービスに対するクレームを開始します。</span><span class="sxs-lookup"><span data-stu-id="b598c-144">Start the SharePoint 'Claims to Windows Token Service': Start the Claims to Windows Token Service through SharePoint Central Administration on the **Manage Services on Server** page.</span></span> <span data-ttu-id="b598c-145">このサービスは、アクションを実行するサーバーで起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b598c-145">The service should be started on the server that will be performing the action.</span></span> <span data-ttu-id="b598c-146">たとえば、WFE サーバーと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスを実行しているアプリケーション サーバーを持っている場合は、アプリケーション サーバーで c2WTS を起動するだけでかまいません。</span><span class="sxs-lookup"><span data-stu-id="b598c-146">For example if you have a server that is a WFE and another server that is an Application Server that has the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service running, you only need to start c2WTS on the Application Server.</span></span> <span data-ttu-id="b598c-147">c2WTS は WFE では必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b598c-147">c2WTS is not needed on the WFE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b598c-148">参照</span><span class="sxs-lookup"><span data-stu-id="b598c-148">See Also</span></span>  
 <span data-ttu-id="b598c-149">[Windows トークンサービスに対するクレーム (c2WTS) の概要 (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span><span class="sxs-lookup"><span data-stu-id="b598c-149">[Claims to Windows Token Service (c2WTS) Overview (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span></span>  
 [<span data-ttu-id="b598c-150">Microsoft SharePoint 2010 製品の Kerberos 認証の概要 (https://technet.microsoft.com/library/gg502594.aspx)</span><span class="sxs-lookup"><span data-stu-id="b598c-150">Overview of Kerberos authentication for Microsoft SharePoint 2010 Products (https://technet.microsoft.com/library/gg502594.aspx)</span></span>](https://technet.microsoft.com/library/gg502594.aspx)  
  
