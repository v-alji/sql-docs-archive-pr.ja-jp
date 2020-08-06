---
title: Kerberos 接続用のサービス プリンシパル名の登録 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SPNs
- network connections [SQL Server], SPNs
- registering SPNs
- Server Principal Names
- SPNs [SQL Server]
ms.assetid: e38d5ce4-e538-4ab9-be67-7046e0d9504e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4db1e8b86fca057acbce29491be9c2be91f0748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644140"
---
# <a name="register-a-service-principal-name-for-kerberos-connections"></a><span data-ttu-id="9cfce-102">Kerberos 接続用のサービス プリンシパル名の登録</span><span class="sxs-lookup"><span data-stu-id="9cfce-102">Register a Service Principal Name for Kerberos Connections</span></span>
  <span data-ttu-id="9cfce-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と Kerberos 認証を併用するには、次の両方の条件が満たされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-103">To use Kerberos authentication with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires both the following conditions to be true:</span></span>  
  
-   <span data-ttu-id="9cfce-104">クライアント コンピューターとサーバー コンピューターが、同じ Windows ドメインまたは信頼関係のあるドメインの一部であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-104">The client and server computers must be part of the same Windows domain, or in trusted domains.</span></span>  
  
-   <span data-ttu-id="9cfce-105">SPN (サービス プリンシパル名) は、Windows ドメインのキー配布センターの役割を担う Active Directory に登録されることが必要です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-105">A Service Principal Name (SPN) must be registered with Active Directory, which assumes the role of the Key Distribution Center in a Windows domain.</span></span> <span data-ttu-id="9cfce-106">SPN は、登録後に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス サービスを起動した Windows アカウントに対してマップされます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-106">The SPN, after it is registered, maps to the Windows account that started the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance service.</span></span> <span data-ttu-id="9cfce-107">SPN 登録がまだ実行されていないか失敗した場合、Windows セキュリティ レイヤーは、SPN に関連するアカウントを決定することができず、Kerberos 認証は使用されません。</span><span class="sxs-lookup"><span data-stu-id="9cfce-107">If the SPN registration has not been performed or fails, the Windows security layer cannot determine the account associated with the SPN, and Kerberos authentication will not be used.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9cfce-108">サーバーが SPN を自動的に登録できない場合、SPN を手動で登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-108">If the server cannot automatically register the SPN, the SPN must be registered manually.</span></span> <span data-ttu-id="9cfce-109">「 [SPN の手動登録](#Manual)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cfce-109">See [Manual SPN Registration](#Manual).</span></span>  
  
 <span data-ttu-id="9cfce-110">Kerberos を使用して接続しているかどうかを確認するには、sys.dm_exec_connections 動的管理ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-110">You can verify that a connection is using Kerberos by querying the sys.dm_exec_connections dynamic management view.</span></span> <span data-ttu-id="9cfce-111">次のクエリを実行して auth_scheme 列の値を確認します。Kerberos が有効な場合、この値は "KERBEROS" になります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-111">Run the following query and check the value of the auth_scheme column, which will be "KERBEROS" if Kerberos is enabled.</span></span>  
  
```  
SELECT auth_scheme FROM sys.dm_exec_connections WHERE session_id = @@spid ;  
```  
  
> [!TIP]  
>  <span data-ttu-id="9cfce-112">**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と Kerberos に関する接続性の問題のトラブルシューティングに役立つ診断ツールです。</span><span class="sxs-lookup"><span data-stu-id="9cfce-112">**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** is a diagnostic tool that helps troubleshoot Kerberos related connectivity issues with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9cfce-113">Kerberos 認証の詳細については、「 [Microsoft® Kerberos Configuration Manager for SQL Server®](https://www.microsoft.com/download/details.aspx?id=39046)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9cfce-113">For more information, see [Microsoft Kerberos Configuration Manager for SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).</span></span>  
  
##  <a name="the-role-of-the-spn-in-authentication"></a><a name="Role"></a> <span data-ttu-id="9cfce-114">認証での SPN の役割</span><span class="sxs-lookup"><span data-stu-id="9cfce-114">The Role of the SPN in Authentication</span></span>  
 <span data-ttu-id="9cfce-115">アプリケーションが接続されて Windows 認証を使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューター名、インスタンス名、およびオプションで SPN を渡します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-115">When an application opens a connection and uses Windows Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client passes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer name, instance name and, optionally, an SPN.</span></span> <span data-ttu-id="9cfce-116">接続の際に SPN が渡される場合、変更せずに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-116">If the connection passes an SPN it is used without any changes.</span></span>  
  
 <span data-ttu-id="9cfce-117">接続の際に SPN が渡されない場合、使用されたプロトコル、サーバー名、およびインスタンス名に基づいて既定の SPN が構築されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-117">If the connection does not pass an SPN, a default SPN is constructed based on the protocol used, server name, and the instance name.</span></span>  
  
 <span data-ttu-id="9cfce-118">前の両方のシナリオでは、SPN はキー配布センターに送信され、接続認証のためのセキュリティ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-118">In both of the preceding scenarios, the SPN is sent to the Key Distribution Center to obtain a security token for authenticating the connection.</span></span> <span data-ttu-id="9cfce-119">セキュリティ トークンを取得できない場合、NTLM 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-119">If a security token cannot be obtained, authentication uses NTLM.</span></span>  
  
 <span data-ttu-id="9cfce-120">サービス プリンシパル名 (SPN) は、クライアントがサービスのインスタンスを一意に識別するための名前です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-120">A service principal name (SPN) is the name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="9cfce-121">Kerberos 認証サービスでは、SPN を使用してサービスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-121">The Kerberos authentication service can use an SPN to authenticate a service.</span></span> <span data-ttu-id="9cfce-122">クライアントがサービスに接続するときに、サービスのインスタンスが検索され、そのインスタンスの SPN が構成されます。次に、サービスに接続され、認証のためにサービスの SPN が提示されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-122">When a client wants to connect to a service, it locates an instance of the service, composes an SPN for that instance, connects to the service, and presents the SPN for the service to authenticate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cfce-123">このトピックで提供する情報は、クラスタリングを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-123">The information that is provided in this topic also applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations that use clustering.</span></span>  
  
 <span data-ttu-id="9cfce-124">Windows 認証は、SQL Server を認証する場合にお勧めする方法です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-124">Windows Authentication is the preferred method for users to authenticate to SQL Server.</span></span> <span data-ttu-id="9cfce-125">Windows 認証を使用するクライアントは、NTLM または Kerberos のどちらかを使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-125">Clients that use Windows Authentication are authenticated by either using NTLM or Kerberos.</span></span> <span data-ttu-id="9cfce-126">Active Directory 環境では、常に Kerberos 認証が最初に試みられます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-126">In an Active Directory environment, Kerberos authentication is always attempted first.</span></span> <span data-ttu-id="9cfce-127">Kerberos 認証は、名前付きパイプを使用する [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] クライアントには使用できません。</span><span class="sxs-lookup"><span data-stu-id="9cfce-127">Kerberos authentication is not available for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] clients using named pipes.</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9cfce-128">Permissions</span><span class="sxs-lookup"><span data-stu-id="9cfce-128">Permissions</span></span>  
 <span data-ttu-id="9cfce-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスが起動すると、サービス プリンシパル名 (SPN) の登録が試みられます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-129">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service starts, it attempts to register the Service Principal Name (SPN).</span></span> <span data-ttu-id="9cfce-130">SQL Server を開始しているアカウントに、Active Directory Domain Services に SPN を登録する権限がない場合は、この呼び出しは失敗し、アプリケーション イベント ログと SQL Server エラー ログに警告メッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-130">If the account starting SQL Server doesn't have permission to register a SPN in Active Directory Domain Services, this call will fail and a warning message will be logged in the Application event log as well as the SQL Server error log.</span></span> <span data-ttu-id="9cfce-131">SPN を登録するには、ビルトイン アカウント (ローカル システム (非推奨) や NETWORK SERVICE など) または SPN を登録する権限を持つアカウント (ドメイン管理者アカウントなど) で [!INCLUDE[ssDE](../../includes/ssde-md.md)] が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-131">To register the SPN, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running under a built-in account, such as Local System (not recommended), or NETWORK SERVICE, or an account that has permission to register an SPN, such as a domain administrator account.</span></span> <span data-ttu-id="9cfce-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が  [!INCLUDE[win7](../../includes/win7-md.md)] または  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] オペレーティング システムで実行されている場合は、仮想アカウントまたは管理されたサービス アカウント (MSA) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the  [!INCLUDE[win7](../../includes/win7-md.md)] or  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating system, you can run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a virtual account or a managed service account (MSA).</span></span> <span data-ttu-id="9cfce-133">仮想アカウントと MSA の両方で SPN を登録できます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-133">Both virtual accounts and MSA's can register an SPN.</span></span> <span data-ttu-id="9cfce-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がこのいずれかのアカウントで実行されていない場合、SPN は起動時には登録されず、ドメイン管理者が SPN を手動で登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running under one of these accounts, the SPN is not registered at startup and the domain administrator must register the SPN manually.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cfce-135">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 機能レベルよりも低い機能レベルで Windows ドメインが実行されるように構成される場合は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サービスの SPN を登録するために必要な権限が、管理されたサービス アカウントに与えられません。</span><span class="sxs-lookup"><span data-stu-id="9cfce-135">When the Windows domain is configured to run at less than the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Windows Server 2008 R2 functional level, then the Managed Service Account will not have the necessary permissions to register the SPNs for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span> <span data-ttu-id="9cfce-136">Kerberos 認証が必要な場合は、ドメイン管理者が、管理されたサービス アカウントに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SPN を手動で登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-136">If Kerberos authentication is required, the Domain Administrator should manually register the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SPNs on the Managed Service Account.</span></span>  
  
 <span data-ttu-id="9cfce-137">ドメイン管理者ではないアカウントに SPN に対する読み取り権限または書き込み権限を許可する方法については、サポート技術情報の資料「 [SQL Server で Kerberos 認証を使用する方法](https://support.microsoft.com/kb/319723)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cfce-137">The KB article, [How to use Kerberos authentication in SQL Server](https://support.microsoft.com/kb/319723), contains information about how to grant read or write permission to an SPN for an account that is not a Domain Administrator.</span></span>  
  
 <span data-ttu-id="9cfce-138">その他の情報については、「 [SQL Server 2008 で Kerberos の制約付き委任を実装する方法](https://technet.microsoft.com/library/ee191523.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cfce-138">Additional information is available at [How to Implement Kerberos Constrained Delegation with SQL Server 2008](https://technet.microsoft.com/library/ee191523.aspx)</span></span>  
  
##  <a name="spn-formats"></a><a name="Formats"></a> <span data-ttu-id="9cfce-139">SPN の形式</span><span class="sxs-lookup"><span data-stu-id="9cfce-139">SPN Formats</span></span>  
 <span data-ttu-id="9cfce-140">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、TCP/IP、名前付きパイプ、および共有メモリで Kerberos 認証をサポートするために、SPN の形式が変更されています。</span><span class="sxs-lookup"><span data-stu-id="9cfce-140">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SPN format is changed in order to support Kerberos authentication on TCP/IP, named pipes, and shared memory.</span></span> <span data-ttu-id="9cfce-141">名前付きインスタンスおよび既定のインスタンスでサポートされている SPN の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cfce-141">The supported SPN formats for named and default instances are as follows.</span></span>  
  
 <span data-ttu-id="9cfce-142">**[名前付きインスタンス]**</span><span class="sxs-lookup"><span data-stu-id="9cfce-142">**Named instance**</span></span>  
  
-   <span data-ttu-id="9cfce-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_]。各要素の説明は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cfce-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_], where:</span></span>  
  
    -   <span data-ttu-id="9cfce-144">*MSSQLSvc* は、登録されるサービスです。</span><span class="sxs-lookup"><span data-stu-id="9cfce-144">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="9cfce-145">*FQDN*は、サーバーの完全修飾ドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-145">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="9cfce-146">*port*は、TCP ポート番号です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-146">*port* is the TCP port number.</span></span>  
  
    -   <span data-ttu-id="9cfce-147">*instancename*は、インスタンスの名前です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9cfce-147">*instancename* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="9cfce-148">**[既定のインスタンス]**</span><span class="sxs-lookup"><span data-stu-id="9cfce-148">**Default instance**</span></span>  
  
-   <span data-ttu-id="9cfce-149">*MSSQLSvc/fqdn*:_port_ **|** _MSSQLSvc/fqdn_。ここで、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-149">*MSSQLSvc/FQDN*:_port_**|**_MSSQLSvc/FQDN_, where:</span></span>  
  
    -   <span data-ttu-id="9cfce-150">*MSSQLSvc* は、登録されるサービスです。</span><span class="sxs-lookup"><span data-stu-id="9cfce-150">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="9cfce-151">*FQDN*は、サーバーの完全修飾ドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-151">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="9cfce-152">*port*は、TCP ポート番号です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-152">*port* is the TCP port number.</span></span>  
  
 <span data-ttu-id="9cfce-153">新しい SPN の形式では、ポート番号は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9cfce-153">The new SPN format does not require a port number.</span></span> <span data-ttu-id="9cfce-154">つまり、複数ポートのサーバーまたはポート番号を使用しないプロトコルで Kerberos 認証を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-154">This means that a multiple-port server or a protocol that does not use port numbers can use Kerberos authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cfce-155">TCP ポートが SPN に含まれている TCP/IP 接続の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Kerberos 認証を使用して接続するユーザー用に TCP プロトコルを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-155">In the case of a TCP/IP connection, where the TCP port is included in the SPN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must enable the TCP protocol for a user to connect by using Kerberos authentication.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cfce-156">MSSQLSvc/*fqdn: port*</span><span class="sxs-lookup"><span data-stu-id="9cfce-156">MSSQLSvc/*fqdn:port*</span></span>|<span data-ttu-id="9cfce-157">TCP が使用される場合にプロバイダーが生成する既定の SPN。</span><span class="sxs-lookup"><span data-stu-id="9cfce-157">The provider-generated, default SPN when TCP is used.</span></span> <span data-ttu-id="9cfce-158">*port* は、TCP ポート番号です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-158">*port* is a TCP port number.</span></span>|  
|<span data-ttu-id="9cfce-159">MSSQLSvc/*fqdn*</span><span class="sxs-lookup"><span data-stu-id="9cfce-159">MSSQLSvc/*fqdn*</span></span>|<span data-ttu-id="9cfce-160">TCP 以外のプロトコルが使用される場合に、既定のインスタンスに対してプロバイダーが生成する既定の SPN。</span><span class="sxs-lookup"><span data-stu-id="9cfce-160">The provider-generated, default SPN for a default instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="9cfce-161">*fqdn*は完全修飾ドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-161">*fqdn* is a fully-qualified domain name.</span></span>|  
|<span data-ttu-id="9cfce-162">MSSQLSvc/*fqdn: InstanceName*</span><span class="sxs-lookup"><span data-stu-id="9cfce-162">MSSQLSvc/*fqdn:InstanceName*</span></span>|<span data-ttu-id="9cfce-163">TCP 以外のプロトコルが使用される場合に、名前付きインスタンスに対してプロバイダーが生成する既定の SPN。</span><span class="sxs-lookup"><span data-stu-id="9cfce-163">The provider-generated, default SPN for a named instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="9cfce-164">*InstanceName*は、のインスタンスの名前です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9cfce-164">*InstanceName* is the name of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
##  <a name="automatic-spn-registration"></a><a name="Auto"></a> <span data-ttu-id="9cfce-165">SPN の自動登録</span><span class="sxs-lookup"><span data-stu-id="9cfce-165">Automatic SPN Registration</span></span>  
 <span data-ttu-id="9cfce-166">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスが開始すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに対する SPN の登録を試みます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-166">When an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to register the SPN for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="9cfce-167">インスタンスが停止すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は SPN の登録解除を試みます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-167">When the instance is stopped, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to unregister the SPN.</span></span> <span data-ttu-id="9cfce-168">TCP/IP 接続の場合、SPN は *MSSQLSvc/\<FQDN>* : *\<tcpport>* という形式で登録されます。名前付きインスタンスと既定のインスタンスは、どちらも *MSSQLSvc* として登録され、インスタンスの区別は *\<tcpport>* の値で行われます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-168">For a TCP/IP connection the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<tcpport>*.Both named instances and the default instance are registered as *MSSQLSvc*, relying on the *\<tcpport>* value to differentiate the instances.</span></span>  
  
 <span data-ttu-id="9cfce-169">Kerberos をサポートするその他の接続の場合、SPN は名前付きインスタンスの\*MSSQLSvc/ \<FQDN> \*: という形式で登録され *\<instancename>* ます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-169">For other connections that support Kerberos the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<instancename>* for a named instance.</span></span> <span data-ttu-id="9cfce-170">既定のインスタンスを登録する場合の形式は、*MSSQLSvc/\<FQDN>* です。</span><span class="sxs-lookup"><span data-stu-id="9cfce-170">The format for registering the default instance is *MSSQLSvc/\<FQDN>*.</span></span>  
  
 <span data-ttu-id="9cfce-171">SPN の登録または登録解除に必要な権限がサービス アカウントにない場合は、これらのアクションを手動で実行することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-171">Manual intervention might be required to register or unregister the SPN if the service account lacks the permissions that are required for these actions.</span></span>  
  
##  <a name="manual-spn-registration"></a><a name="Manual"></a> <span data-ttu-id="9cfce-172">SPN の手動登録</span><span class="sxs-lookup"><span data-stu-id="9cfce-172">Manual SPN Registration</span></span>  
 <span data-ttu-id="9cfce-173">SPN を手動で登録するには、管理者は Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] サポート ツールに付属する Setspn.exe ツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-173">To register the SPN manually, the administrator must use the Setspn.exe tool that is provided with the Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] Support Tools.</span></span> <span data-ttu-id="9cfce-174">詳細については、サポート技術情報の資料「 [Windows Server 2003 Service Pack 1 のサポート ツール](https://support.microsoft.com/kb/892777) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cfce-174">For more information, see the [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777) KB article.</span></span>  
  
 <span data-ttu-id="9cfce-175">Setspn.exe は、サービス プリンシパル名 (SPN) ディレクトリ プロパティの読み取り、変更、および削除を実行できるようにするコマンド ライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="9cfce-175">Setspn.exe is a command line tool that enables you to read, modify, and delete the Service Principal Names (SPN) directory property.</span></span> <span data-ttu-id="9cfce-176">このツールを使用すると、現在の SPN の表示、アカウントの既定の SPN の再設定、および補足 SPN の追加または削除も実行できます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-176">This tool also enables you to view the current SPNs, reset the account's default SPNs, and add or delete supplemental SPNs.</span></span>  
  
 <span data-ttu-id="9cfce-177">TCP/IP 接続の場合に SPN を手動で登録するために使用される構文例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-177">The following example illustrates the syntax used to register manually register an SPN for a TCP/IP connection.</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:1433 accountname  
```  
  
 <span data-ttu-id="9cfce-178">**注** SPN が既に存在する場合は、再登録する前に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-178">**Note** If an SPN already exists, it must be deleted before it can be reregistered.</span></span> <span data-ttu-id="9cfce-179">削除するには、 `setspn` スイッチを指定して `-D` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-179">You do this by using the `setspn` command together with the `-D` switch.</span></span> <span data-ttu-id="9cfce-180">次の例は、新しいインスタンス ベースの SPN を手動で登録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9cfce-180">The following examples illustrate how to manually register a new instance-based SPN.</span></span> <span data-ttu-id="9cfce-181">既定のインスタンスの場合は、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-181">For a default instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com accountname  
```  
  
 <span data-ttu-id="9cfce-182">名前付きインスタンスの場合は、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-182">For a named instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:instancename accountname  
```  
  
##  <a name="client-connections"></a><a name="Client"></a> <span data-ttu-id="9cfce-183">クライアント接続</span><span class="sxs-lookup"><span data-stu-id="9cfce-183">Client Connections</span></span>  
 <span data-ttu-id="9cfce-184">クライアント ドライバーでは、ユーザー指定の SPN がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9cfce-184">User-specified SPNs are supported in client drivers.</span></span> <span data-ttu-id="9cfce-185">ただし、SPN を指定しない場合は、クライアント接続の種類に基づいて SPN が自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-185">However, if an SPN is not provided, it will be generated automatically based on the type of a client connection.</span></span> <span data-ttu-id="9cfce-186">TCP 接続の場合は、名前付きインスタンスと既定のインスタンスの両方で、 *MSSQLSvc*/*FQDN*:[*port*] という形式の SPN が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-186">For a TCP connection, an SPN in the format *MSSQLSvc*/*FQDN*:[*port*] is used for both the named and default instances.</span></span>  
  
 <span data-ttu-id="9cfce-187">名前付きパイプおよび共有メモリ接続の場合、 *MSSQLSvc* / 名前付きインスタンスには MSSQLSvc*fqdn*:*instancename*という形式の SPN が使用され、 *MSSQLSvc* / *fqdn*は既定のインスタンスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-187">For named pipes and shared memory connections, an SPN in the format *MSSQLSvc*/*FQDN*:*instancename* is used for a named instance and *MSSQLSvc*/*FQDN* is used for the default instance.</span></span>  
  
 <span data-ttu-id="9cfce-188">**SPN としてのサービス アカウントの使用**</span><span class="sxs-lookup"><span data-stu-id="9cfce-188">**Using a service account as an SPN**</span></span>  
  
 <span data-ttu-id="9cfce-189">サービス アカウントを SPN として使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-189">Service accounts can be used as an SPN.</span></span> <span data-ttu-id="9cfce-190">サービス アカウントは、Kerberos 認証の接続属性を使用して次の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-190">They are specified through the connection attribute for the Kerberos authentication and take the following formats:</span></span>  
  
-   <span data-ttu-id="9cfce-191">**username@domain**ドメインユーザーアカウントの場合は**domain\username**</span><span class="sxs-lookup"><span data-stu-id="9cfce-191">**username@domain** or **domain\username** for a domain user account</span></span>  
  
-   <span data-ttu-id="9cfce-192">**machine$@domain** または **host\FQDN** (ローカル システムや NETWORK SERVICES などのコンピューター ドメイン アカウントの場合)</span><span class="sxs-lookup"><span data-stu-id="9cfce-192">**machine$@domain** or **host\FQDN** for a computer domain account such as Local System or NETWORK SERVICES.</span></span>  
  
 <span data-ttu-id="9cfce-193">接続の認証方法を確認するには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-193">To determine the authentication method of a connection, execute the following query.</span></span>  
  
```sql  
SELECT net_transport, auth_scheme   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
```  
  
##  <a name="authentication-defaults"></a><a name="Defaults"></a> <span data-ttu-id="9cfce-194">認証の既定</span><span class="sxs-lookup"><span data-stu-id="9cfce-194">Authentication Defaults</span></span>  
 <span data-ttu-id="9cfce-195">次の表では、SPN の登録シナリオに基づいて使用される認証の既定について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-195">The following table describes the authentication defaults that are used based on SPN registration scenarios.</span></span>  
  
|<span data-ttu-id="9cfce-196">シナリオ</span><span class="sxs-lookup"><span data-stu-id="9cfce-196">Scenario</span></span>|<span data-ttu-id="9cfce-197">認証方法</span><span class="sxs-lookup"><span data-stu-id="9cfce-197">Authentication method</span></span>|  
|--------------|---------------------------|  
|<span data-ttu-id="9cfce-198">SPN が正しいドメイン アカウント、仮想アカウント、MSA、またはビルトイン アカウントにマップされている場合</span><span class="sxs-lookup"><span data-stu-id="9cfce-198">The SPN maps to the correct domain account, virtual account, MSA, or built-in account.</span></span> <span data-ttu-id="9cfce-199">(ローカル システムや NETWORK SERVICE など)</span><span class="sxs-lookup"><span data-stu-id="9cfce-199">For example, Local System or NETWORK SERVICE.</span></span><br /><br /> <span data-ttu-id="9cfce-200">注: [修正] は、登録された SPN によってマップされたアカウントが、SQL Server サービスが実行されているアカウントであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-200">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="9cfce-201">ローカル接続では NTLM が使用され、リモート接続では Kerberos が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-201">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="9cfce-202">SPN が正しいドメイン アカウント、仮想アカウント、MSA、またはビルトイン アカウントである場合</span><span class="sxs-lookup"><span data-stu-id="9cfce-202">The SPN is the correct domain account, virtual account, MSA, or built-in account.</span></span><br /><br /> <span data-ttu-id="9cfce-203">注: [修正] は、登録された SPN によってマップされたアカウントが、SQL Server サービスが実行されているアカウントであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-203">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="9cfce-204">ローカル接続では NTLM が使用され、リモート接続では Kerberos が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-204">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="9cfce-205">SPN が正しくないドメイン アカウント、仮想アカウント、MSA、またはビルトイン アカウントにマップされている場合</span><span class="sxs-lookup"><span data-stu-id="9cfce-205">The SPN maps to an incorrect domain account, virtual account, MSA, or built-in account</span></span>|<span data-ttu-id="9cfce-206">認証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="9cfce-206">Authentication fails.</span></span>|  
|<span data-ttu-id="9cfce-207">SPN 参照が失敗したか、正しいドメイン アカウント、仮想アカウント、MSA、またはビルトイン アカウントにマップされていないか、正しいドメイン アカウント、仮想アカウント、MSA、またはビルトイン アカウントではない場合</span><span class="sxs-lookup"><span data-stu-id="9cfce-207">The SPN lookup fails or does not map to a correct domain account, virtual account, MSA, or built-in account, or is not a correct domain account, virtual account, MSA, or built-in account.</span></span>|<span data-ttu-id="9cfce-208">ローカル接続とリモート接続で NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-208">Local and remote connections use NTLM.</span></span>|  
  
##  <a name="comments"></a><a name="Comments"></a> <span data-ttu-id="9cfce-209">コメント</span><span class="sxs-lookup"><span data-stu-id="9cfce-209">Comments</span></span>  
 <span data-ttu-id="9cfce-210">専用管理者接続 (DAC) では、インスタンス名ベースの SPN が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-210">The Dedicated Administrator Connection (DAC) uses an instance name based SPN.</span></span> <span data-ttu-id="9cfce-211">その SPN が正常に登録されると、Kerberos 認証を DAC で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9cfce-211">Kerberos authentication can be used with a DAC if that SPN is registered successfully.</span></span> <span data-ttu-id="9cfce-212">また、ユーザーがアカウント名を SPN として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-212">As an alternative a user can specify the account name as an SPN.</span></span>  
  
 <span data-ttu-id="9cfce-213">起動中に SPN の登録が失敗した場合は、この失敗が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログに記録されて、起動が続行されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-213">If SPN registration fails during startup, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and startup continues.</span></span>  
  
 <span data-ttu-id="9cfce-214">シャットダウン中に SPN の登録解除が失敗した場合は、この失敗が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログに記録されて、シャットダウンが続行されます。</span><span class="sxs-lookup"><span data-stu-id="9cfce-214">If SPN de-registration fails during shutdown, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and shutdown continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfce-215">参照</span><span class="sxs-lookup"><span data-stu-id="9cfce-215">See Also</span></span>  
 <span data-ttu-id="9cfce-216">[クライアント接続でのサービス プリンシパル名 &#40;SPN&#41; のサポート](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span><span class="sxs-lookup"><span data-stu-id="9cfce-216">[Service Principal Name &#40;SPN&#41; Support in Client Connections](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span></span>  
 <span data-ttu-id="9cfce-217">[クライアント接続 &#40;OLE DB&#41; でのサービス プリンシパル名 &#40;SPNs&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="9cfce-217">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span></span>  
 <span data-ttu-id="9cfce-218">[クライアント接続 &#40;ODBC&#41; でのサービス プリンシパル名 &#40;SPNs&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="9cfce-218">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span></span>  
 <span data-ttu-id="9cfce-219">[SQL Server Native Client の機能](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="9cfce-219">[SQL Server Native Client Features](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span></span>  
 [<span data-ttu-id="9cfce-220">Reporting Services 環境における Kerberos 認証の問題の管理</span><span class="sxs-lookup"><span data-stu-id="9cfce-220">Manage Kerberos Authentication Issues in a Reporting Services Environment</span></span>](https://technet.microsoft.com/library/ff679930.aspx)  
  
  
