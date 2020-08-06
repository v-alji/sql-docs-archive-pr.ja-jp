---
title: レポート サーバーのサービス プリンシパル名 (SPN) の登録 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 502170f16aad66757e8f44419ccbac3017072449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645394"
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a><span data-ttu-id="a9597-102">レポート サーバーのサービス プリンシパル名 (SPN) の登録</span><span class="sxs-lookup"><span data-stu-id="a9597-102">Register a Service Principal Name (SPN) for a Report Server</span></span>
  <span data-ttu-id="a9597-103">相互認証に Kerberos プロトコルを使用するネットワークに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を配置する場合に、レポート サーバー サービスをドメイン ユーザー アカウントとして実行するように構成するには、レポート サーバー サービスのサービス プリンシパル名 (SPN) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9597-103">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses the Kerberos protocol for mutual authentication, you must create a Service Principal Name (SPN) for the Report Server service if you configure it to run as a domain user account.</span></span>  
  
## <a name="about-spns"></a><span data-ttu-id="a9597-104">SPN について</span><span class="sxs-lookup"><span data-stu-id="a9597-104">About SPNs</span></span>  
 <span data-ttu-id="a9597-105">SPN は、Kerberos 認証を使用するネットワークでのサービスの一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="a9597-105">An SPN is a unique identifier for a service on a network that uses Kerberos authentication.</span></span> <span data-ttu-id="a9597-106">SPN は、サービス クラス、ホスト名、およびポートで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a9597-106">It consists of a service class, a host name, and a port.</span></span> <span data-ttu-id="a9597-107">Kerberos 認証を使用するネットワークでは、ビルトイン コンピューター アカウント (NetworkService や LocalSystem など) またはユーザー アカウントにサーバーの SPN を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9597-107">On a network that uses Kerberos authentication, an SPN for the server must be registered under either a built-in computer account (such as NetworkService or LocalSystem) or user account.</span></span> <span data-ttu-id="a9597-108">ビルトイン アカウントには、自動的に SPN が登録されます。</span><span class="sxs-lookup"><span data-stu-id="a9597-108">SPNs are registered for built-in accounts automatically.</span></span> <span data-ttu-id="a9597-109">一方、ドメイン ユーザー アカウントでサービスを実行する場合は、使用するアカウントに手動で SPN を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9597-109">However, when you run a service under a domain user account, you must manually register the SPN for the account you want to use.</span></span>  
  
 <span data-ttu-id="a9597-110">SPN を作成するには、 **SetSPN** コマンド ライン ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9597-110">To create an SPN, you can use the **SetSPN** command line utility.</span></span> <span data-ttu-id="a9597-111">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="a9597-111">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="a9597-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) ( https://technet.microsoft.com/library/cc731241(WS.10).aspx) .</span><span class="sxs-lookup"><span data-stu-id="a9597-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx).</span></span>  
  
-   <span data-ttu-id="a9597-113">[サービスプリンシパル名 (spn) SetSPN の構文 (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) ( https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="a9597-113">[Service Principal Names (SPNs) SetSPN Syntax (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).</span></span>  
  
 <span data-ttu-id="a9597-114">このユーティリティをドメイン コントローラーで実行するには、ドメイン管理者であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a9597-114">You must be a domain administrator to run the utility on the domain controller.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9597-115">構文</span><span class="sxs-lookup"><span data-stu-id="a9597-115">Syntax</span></span>  
 <span data-ttu-id="a9597-116">SetSPN ユーティリティを使用してレポート サーバーの SPN を作成する場合は、次のようなコマンド構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="a9597-116">The command syntax for using SetSPN utility to create an SPN for the report server resembles the following:</span></span>  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 <span data-ttu-id="a9597-117">**SetSPN** は、Windows Server で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a9597-117">**SetSPN** is available with Windows Server.</span></span> <span data-ttu-id="a9597-118">`-s` 引数は、重複する SPN がないことを検証してから、SPN を追加します。</span><span class="sxs-lookup"><span data-stu-id="a9597-118">The `-s` argument adds a SPN after validating no duplicate exists.</span></span> <span data-ttu-id="a9597-119">**注: -s** は Windows Server 2008 以降の Windows Server で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a9597-119">**NOTE:-s** is available in Windows Server starting with Windows Server 2008.</span></span>  
  
 <span data-ttu-id="a9597-120">`HTTP` はサービス クラスです。</span><span class="sxs-lookup"><span data-stu-id="a9597-120">`HTTP` is the service class.</span></span> <span data-ttu-id="a9597-121">レポート サーバー Web サービスは、HTTP.SYS で実行されます。</span><span class="sxs-lookup"><span data-stu-id="a9597-121">The Report Server Web service runs in HTTP.SYS.</span></span> <span data-ttu-id="a9597-122">HTTP 用に SPN を作成すると、副次的に、HTTP.SYS で実行される同じコンピューター上のすべての Web アプリケーション (IIS でホストされるアプリケーションを含む) に対して、ドメイン ユーザー アカウントに基づいてチケットが付与されます。</span><span class="sxs-lookup"><span data-stu-id="a9597-122">A by-product of creating an SPN for HTTP is that all Web applications on the same computer that run in HTTP.SYS (including applications hosted in IIS) will be granted tickets based on the domain user account.</span></span> <span data-ttu-id="a9597-123">これらのサービスを別のアカウントで実行すると、認証要求が失敗します。</span><span class="sxs-lookup"><span data-stu-id="a9597-123">If those services run under a different account, the authentication requests will fail.</span></span> <span data-ttu-id="a9597-124">この問題を回避するには、すべての HTTP アプリケーションが同じアカウントで実行されるように構成するか、またはアプリケーションごとにホスト ヘッダーを作成し、作成したホスト ヘッダーごとに個別の SPN を作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a9597-124">To avoid this problem, be sure to configure all HTTP applications to run under the same account, or consider creating host headers for each application and then creating separate SPNs for each host header.</span></span> <span data-ttu-id="a9597-125">ホスト ヘッダーを構成する場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成にかかわらず DNS を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9597-125">When you configure host headers, DNS changes are required regardless of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration.</span></span>  
  
 <span data-ttu-id="a9597-126">、、およびに指定する値によって、 \<*computername*> \<*domainname*> \<*port*> レポートサーバーをホストするコンピューターの一意のネットワークアドレスが識別されます。</span><span class="sxs-lookup"><span data-stu-id="a9597-126">The values that you specify for \<*computername*>, \<*domainname*>, and \<*port*> identify the unique network address of the computer that hosts the report server.</span></span> <span data-ttu-id="a9597-127">これは、ローカル ホスト名にすることも、完全修飾ドメイン名 (FQDN) にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a9597-127">This can be a local host name or a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="a9597-128">ドメインが1つしかなく、かつポート80を使用している場合は、 \<*domainname*> コマンドラインからとを省略でき \<*port*> ます。</span><span class="sxs-lookup"><span data-stu-id="a9597-128">If you only have one domain and are using port 80, you can omit \<*domainname*> and \<*port*> from your command line.</span></span> <span data-ttu-id="a9597-129">\<*domain-user-account*>は、レポートサーバーサービスを実行するユーザーアカウントであり、SPN を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9597-129">\<*domain-user-account*> is the user account under which the Report Server service runs and for which the SPN must be registered.</span></span>  
  
## <a name="register-an-spn-for-domain-user-account"></a><span data-ttu-id="a9597-130">ドメイン ユーザー アカウントに対する SPN の登録</span><span class="sxs-lookup"><span data-stu-id="a9597-130">Register an SPN for Domain User Account</span></span>  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a><span data-ttu-id="a9597-131">ドメイン ユーザーとして実行されるレポート サーバー サービスの SPN を登録するには</span><span class="sxs-lookup"><span data-stu-id="a9597-131">To register an SPN for a Report Server service running as a domain user</span></span>  
  
1.  <span data-ttu-id="a9597-132">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールし、レポート サーバー サービスをドメイン ユーザー アカウントとして実行するように構成します。</span><span class="sxs-lookup"><span data-stu-id="a9597-132">Install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and configure the Report Server service to run as a domain user account.</span></span> <span data-ttu-id="a9597-133">この手順が完了しないと、ユーザーはレポート サーバーに接続できないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="a9597-133">Note that users will not be able to connect to the report server until you complete the following steps.</span></span>  
  
2.  <span data-ttu-id="a9597-134">ドメイン コントローラーにドメイン管理者としてログオンします。</span><span class="sxs-lookup"><span data-stu-id="a9597-134">Log on to the domain controller as domain administrator.</span></span>  
  
3.  <span data-ttu-id="a9597-135">コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="a9597-135">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="a9597-136">次のコマンドをコピーし、プレースホルダーの値を実際のネットワークで有効な値で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a9597-136">Copy the following command, replacing placeholder values with actual values that are valid for your network:</span></span>  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     <span data-ttu-id="a9597-137">例: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span><span class="sxs-lookup"><span data-stu-id="a9597-137">For example: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span></span>  
  
5.  <span data-ttu-id="a9597-138">コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a9597-138">Run the command.</span></span>  
  
6.  <span data-ttu-id="a9597-139">**RsReportServer.config** ファイルを開き、 `<AuthenticationTypes>` セクションを探します。</span><span class="sxs-lookup"><span data-stu-id="a9597-139">Open the **RsReportServer.config** file and locate the `<AuthenticationTypes>` section.</span></span>  
  
7.  <span data-ttu-id="a9597-140">このセクションの最初のエントリとして `<RSWindowsNegotiate/>` を追加して、NTLM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a9597-140">Add `<RSWindowsNegotiate/>` as the first entry in this section to enable NTLM.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9597-141">参照</span><span class="sxs-lookup"><span data-stu-id="a9597-141">See Also</span></span>  
 <span data-ttu-id="a9597-142">[SSRS Configuration Manager &#40;サービスアカウントを構成&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a9597-142">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="a9597-143">[レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a9597-143">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="a9597-144">Reporting Services ネイティブ モードのレポート サーバーの管理</span><span class="sxs-lookup"><span data-stu-id="a9597-144">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
