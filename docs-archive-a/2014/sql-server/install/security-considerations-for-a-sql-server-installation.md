---
title: SQL Server インストールにおけるセキュリティの考慮事項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [SQL Server]
- server message blocks [SQL Server]
- disabling protocols
- security [SQL Server], installations
- protocols [SQL Server], disabling
- NetBIOS [SQL Server]
- services [SQL Server], security
- SMB [SQL Server]
- isolating services [SQL Server]
- Setup [SQL Server], security
- low SQL Server installation privileges
- NTFS [SQL Server]
- physical security [SQL Server]
- file system security [SQL Server]
- installing SQL Server, security
ms.assetid: cf96155f-30a8-48b7-8d6b-24ce90dafdc7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed0cd42d51c2b4db96778182c60f1ad3d13a098c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643099"
---
# <a name="security-considerations-for-a-sql-server-installation"></a><span data-ttu-id="04dbf-102">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="04dbf-102">Security Considerations for a SQL Server Installation</span></span>
  <span data-ttu-id="04dbf-103">セキュリティは、あらゆる製品、あらゆる企業にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="04dbf-103">Security is important for every product and every business.</span></span> <span data-ttu-id="04dbf-104">単純なベスト プラクティスに従うことで、多くのセキュリティの脆弱性を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-104">By following simple best practices, you can avoid many security vulnerabilities.</span></span> <span data-ttu-id="04dbf-105">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールする前と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールした後の両方で考慮する必要があるセキュリティのベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-105">This topic discusses some security best practices that you should consider both before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="04dbf-106">特定の機能のセキュリティについては、その機能の参照トピックで説明しています。</span><span class="sxs-lookup"><span data-stu-id="04dbf-106">Security guidance for specific features is included in the reference topics for those features.</span></span>  
  
## <a name="before-installing-ssnoversion"></a><span data-ttu-id="04dbf-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  をインストールする前に</span><span class="sxs-lookup"><span data-stu-id="04dbf-107">Before Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="04dbf-108">サーバー環境をセットアップする場合、次のベスト プラクティスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-108">Follow these best practices when you set up the server environment:</span></span>  
  
-   [<span data-ttu-id="04dbf-109">物理的なセキュリティの強化</span><span class="sxs-lookup"><span data-stu-id="04dbf-109">Enhance physical security</span></span>](#physical_security)  
  
-   [<span data-ttu-id="04dbf-110">ファイアウォールの使用</span><span class="sxs-lookup"><span data-stu-id="04dbf-110">Use firewalls</span></span>](#firewalls)  
  
-   [<span data-ttu-id="04dbf-111">サービスの分離</span><span class="sxs-lookup"><span data-stu-id="04dbf-111">Isolate services</span></span>](#isolated_services)  
  
-   [<span data-ttu-id="04dbf-112">安全なファイル システムの構成</span><span class="sxs-lookup"><span data-stu-id="04dbf-112">Configure a secure file system</span></span>](#sa_with_least_privileges)  
  
-   [<span data-ttu-id="04dbf-113">NetBIOS とサーバー メッセージ ブロックの無効化</span><span class="sxs-lookup"><span data-stu-id="04dbf-113">Disable NetBIOS and server message block</span></span>](#disabled_protocols)  
  
-   [<span data-ttu-id="04dbf-114">ドメイン コントローラーへの SQL Server のインストール</span><span class="sxs-lookup"><span data-stu-id="04dbf-114">Installing SQL Server on a domain controller</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md#Install_DC)  
  
###  <a name="enhance-physical-security"></a><a name="physical_security"></a> <span data-ttu-id="04dbf-115">Enhance Physical Security</span><span class="sxs-lookup"><span data-stu-id="04dbf-115">Enhance Physical Security</span></span>  
 <span data-ttu-id="04dbf-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセキュリティは、物理的な分離と論理的な分離に基づいています。</span><span class="sxs-lookup"><span data-stu-id="04dbf-116">Physical and logical isolation make up the foundation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="04dbf-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールの物理的なセキュリティを強化するには、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-117">To enhance the physical security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, do the following tasks:</span></span>  
  
-   <span data-ttu-id="04dbf-118">無許可の人が入れない部屋にサーバーを配置します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-118">Place the server in a room accessible only to authorized persons.</span></span>  
  
-   <span data-ttu-id="04dbf-119">データベースをホストするコンピューターを物理的に保護された場所に配置します。水位報知器および火災報知器や消火システムによって監視された、鍵がかかるコンピューター ルームが理想的です。</span><span class="sxs-lookup"><span data-stu-id="04dbf-119">Place computers that host a database in a physically protected location, ideally a locked computer room with monitored flood detection and fire detection or suppression systems.</span></span>  
  
-   <span data-ttu-id="04dbf-120">データベースは、企業イントラネットの安全なゾーンにインストールします。SQL Server をインターネットに直接接続しないでください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-120">Install databases in the secure zone of the corporate intranet and do not connect your SQL Servers directly to the Internet.</span></span>  
  
-   <span data-ttu-id="04dbf-121">すべてのデータを定期的にバックアップし、バックアップを安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-121">Back up all data regularly and secure the backups in an off-site location.</span></span>  
  
###  <a name="use-firewalls"></a><a name="firewalls"></a> <span data-ttu-id="04dbf-122">Use Firewalls</span><span class="sxs-lookup"><span data-stu-id="04dbf-122">Use Firewalls</span></span>  
 <span data-ttu-id="04dbf-123">ファイアウォールは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールのセキュリティを確保するために重要です。</span><span class="sxs-lookup"><span data-stu-id="04dbf-123">Firewalls are important to help secure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="04dbf-124">次のガイドラインに従った場合、ファイアウォールが最も効果的になります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-124">Firewalls will be most effective if you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="04dbf-125">ファイアウォールをサーバーとインターネットの間に配置します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-125">Put a firewall between the server and the Internet.</span></span> <span data-ttu-id="04dbf-126">ファイアウォールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="04dbf-126">Enable your firewall.</span></span> <span data-ttu-id="04dbf-127">ファイアウォールがオフになっている場合はオンにします。</span><span class="sxs-lookup"><span data-stu-id="04dbf-127">If your firewall is turned off, turn it on.</span></span> <span data-ttu-id="04dbf-128">ファイアウォールがオンになっている場合は、オフにしないでください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-128">If your firewall is turned on, do not turn it off.</span></span>  
  
-   <span data-ttu-id="04dbf-129">ファイアウォールでネットワークをセキュリティ ゾーンに分割します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-129">Divide the network into security zones separated by firewalls.</span></span> <span data-ttu-id="04dbf-130">すべてのトラフィックをブロックした後、必要なトラフィックのみを選択的に許可します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-130">Block all traffic, and then selectively admit only what is required.</span></span>  
  
-   <span data-ttu-id="04dbf-131">多層環境では、複数のファイアウォールを使用してスクリーン サブネットを作成します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-131">In a multi-tier environment, use multiple firewalls to create screened subnets.</span></span>  
  
-   <span data-ttu-id="04dbf-132">Windows ドメイン内にサーバーをインストールする場合は、Windows 認証を可能にする内部ファイアウォールを構成します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-132">When you are installing the server inside a Windows domain, configure interior firewalls to allow Windows Authentication.</span></span>  
  
-   <span data-ttu-id="04dbf-133">アプリケーションで分散トランザクションを使用する場合は、別々の MS DTC インスタンスの間で [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) トラフィックが許可されるように、ファイアウォールの構成が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-133">If your application uses distributed transactions, you might have to configure the firewall to allow [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) traffic to flow between separate MS DTC instances.</span></span> <span data-ttu-id="04dbf-134">また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]などのリソース マネージャーと MS DTC の間でトラフィックが許可されるようにファイアウォールを構成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-134">You will also have to configure the firewall to allow traffic to flow between the MS DTC and resource managers such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="04dbf-135">Windows ファイアウォールの既定の設定に関する詳細と、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に影響する TCP ポートの説明については、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-135">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
###  <a name="isolate-services"></a><a name="isolated_services"></a> <span data-ttu-id="04dbf-136">Isolate Services</span><span class="sxs-lookup"><span data-stu-id="04dbf-136">Isolate Services</span></span>  
 <span data-ttu-id="04dbf-137">サービスを分離すると、いずれかのサービスが停止した場合でも、その他のサービスに影響が及ぶのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-137">Isolating services reduces the risk that one compromised service could be used to compromise others.</span></span> <span data-ttu-id="04dbf-138">サービスを分離する場合は、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-138">To isolate services, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="04dbf-139">各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを個別の Windows アカウントで実行します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-139">Run separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services under separate Windows accounts.</span></span> <span data-ttu-id="04dbf-140">可能な場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスごとに権限の低い個別の Windows またはローカル ユーザー アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-140">Whenever possible, use separate, low-rights Windows or Local user accounts for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="04dbf-141">詳細については、「 [Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-141">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
###  <a name="configure-a-secure-file-system"></a><a name="sa_with_least_privileges"></a> <span data-ttu-id="04dbf-142">Configure a Secure File System</span><span class="sxs-lookup"><span data-stu-id="04dbf-142">Configure a Secure File System</span></span>  
 <span data-ttu-id="04dbf-143">正しいファイル システムを使用することで、セキュリティは向上します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-143">Using the correct file system increases security.</span></span> <span data-ttu-id="04dbf-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールには、次の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-144">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, you should do the following tasks:</span></span>  
  
-   <span data-ttu-id="04dbf-145">NTFS ファイル システム (NTFS) を使用します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-145">Use the NTFS file system (NTFS).</span></span> <span data-ttu-id="04dbf-146">NTFS は、FAT ファイル システムに比べて安定性と復旧性が高いことから、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールのファイル システムとして推奨されています。</span><span class="sxs-lookup"><span data-stu-id="04dbf-146">NTFS is the preferred file system for installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because it is more stable and recoverable than FAT file systems.</span></span> <span data-ttu-id="04dbf-147">また、NTFS では、ファイルとディレクトリのアクセス制御リスト (ACL) や暗号化ファイル システム (EFS) によるファイル暗号化などのセキュリティ オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-147">NTFS also enables security options like file and directory access control lists (ACLs) and Encrypting File System (EFS) file encryption.</span></span> <span data-ttu-id="04dbf-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時に NTFS が検出されると、レジストリ キーとファイルに対して適切な ACL が設定されます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-148">During installation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will set appropriate ACLs on registry keys and files if it detects NTFS.</span></span> <span data-ttu-id="04dbf-149">これらの権限は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-149">These permissions should not be changed.</span></span> <span data-ttu-id="04dbf-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のリリースでは、FAT ファイル システムを使用するコンピューターへのインストールはサポートされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-150">Future releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support installation on computers with FAT file systems.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="04dbf-151">EFS を使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行しているアカウントの ID でデータベース ファイルが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-151">If you use EFS, database files will be encrypted under the identity of the account running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="04dbf-152">ファイルの暗号化を解除できるのはこのアカウントだけです。</span><span class="sxs-lookup"><span data-stu-id="04dbf-152">Only this account will be able to decrypt the files.</span></span> <span data-ttu-id="04dbf-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行するアカウントを変更する場合は、まず以前のアカウントでファイルの暗号化を解除してから、新しいアカウントでそれらのファイルを再度暗号化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-153">If you must change the account that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should first decrypt the files under the old account and then re-encrypt them under the new account.</span></span>  
  
-   <span data-ttu-id="04dbf-154">重要なデータ ファイルには、RAID (Redundant Array of Independent Disks) を使用します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-154">Use a redundant array of independent disks (RAID) for critical data files.</span></span>  
  
###  <a name="disable-netbios-and-server-message-block"></a><a name="disabled_protocols"></a> <span data-ttu-id="04dbf-155">Disable NetBIOS and Server Message Block</span><span class="sxs-lookup"><span data-stu-id="04dbf-155">Disable NetBIOS and Server Message Block</span></span>  
 <span data-ttu-id="04dbf-156">境界領域ネットワーク内のサーバーでは、NetBIOS とサーバー メッセージ ブロック (SMB) を含め、不要なプロトコルをすべて無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-156">Servers in the perimeter network should have all unnecessary protocols disabled, including NetBIOS and server message block (SMB).</span></span>  
  
 <span data-ttu-id="04dbf-157">NetBIOS には次のポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-157">NetBIOS uses the following ports:</span></span>  
  
-   <span data-ttu-id="04dbf-158">UDP/137 (NetBIOS ネーム サービス)</span><span class="sxs-lookup"><span data-stu-id="04dbf-158">UDP/137 (NetBIOS name service)</span></span>  
  
-   <span data-ttu-id="04dbf-159">UDP/138 (NetBIOS データグラム サービス)</span><span class="sxs-lookup"><span data-stu-id="04dbf-159">UDP/138 (NetBIOS datagram service)</span></span>  
  
-   <span data-ttu-id="04dbf-160">TCP/139 (NetBIOS セッション サービス)</span><span class="sxs-lookup"><span data-stu-id="04dbf-160">TCP/139 (NetBIOS session service)</span></span>  
  
 <span data-ttu-id="04dbf-161">SMB には次のポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-161">SMB uses the following ports:</span></span>  
  
-   <span data-ttu-id="04dbf-162">TCP/139</span><span class="sxs-lookup"><span data-stu-id="04dbf-162">TCP/139</span></span>  
  
-   <span data-ttu-id="04dbf-163">TCP/445</span><span class="sxs-lookup"><span data-stu-id="04dbf-163">TCP/445</span></span>  
  
 <span data-ttu-id="04dbf-164">Web サーバーとドメイン ネーム システム (DNS) サーバーは NetBIOS と SMB をいずれも必要としません。</span><span class="sxs-lookup"><span data-stu-id="04dbf-164">Web servers and Domain Name System (DNS) servers do not require NetBIOS or SMB.</span></span> <span data-ttu-id="04dbf-165">これらのサーバーでは、両方のプロトコルを無効にしてユーザー列挙の脅威を緩和します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-165">On these servers, disable both protocols to reduce the threat of user enumeration.</span></span>  
  
###  <a name="installing-ssnoversion-on-a-domain-controller"></a><a name="Install_DC"></a> <span data-ttu-id="04dbf-166">ドメイン コントローラーへの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール</span><span class="sxs-lookup"><span data-stu-id="04dbf-166">Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a domain controller</span></span>  
 <span data-ttu-id="04dbf-167">セキュリティ上の理由から、ドメイン コントローラーには [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="04dbf-167">For security reasons, we recommend that you do not install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a domain controller.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="04dbf-168">のセットアップ時にインストールが中止されることはありませんが、次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-168">Setup will not block installation on a computer that is a domain controller, but the following limitations apply:</span></span>  
  
-   <span data-ttu-id="04dbf-169">ローカル サービス アカウントを使用して、ドメイン コントローラー上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="04dbf-169">You cannot run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on a domain controller under a local service account.</span></span>  
  
-   <span data-ttu-id="04dbf-170">コンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールした後で、そのコンピューターをドメイン メンバーからドメイン コントローラーに変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="04dbf-170">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain member to a domain controller.</span></span> <span data-ttu-id="04dbf-171">ホスト コンピューターをドメイン コントローラーに変更する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-171">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain controller.</span></span>  
  
-   <span data-ttu-id="04dbf-172">コンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールした後で、そのコンピューターをドメイン コントローラーからドメイン メンバーに変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="04dbf-172">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain controller to a domain member.</span></span> <span data-ttu-id="04dbf-173">ホスト コンピューターをドメイン メンバーに変更する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-173">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain member.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="04dbf-174">フェールオーバー クラスター インスタンスは、クラスター ノードがドメイン コントローラーの場合はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="04dbf-174">failover cluster instances are not supported where cluster nodes are domain controllers.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="04dbf-175">セットアップでは、読み取り専用ドメイン コントローラーにセキュリティ グループを作成したり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントを準備したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="04dbf-175">Setup cannot create security groups or provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts on a read-only domain controller.</span></span> <span data-ttu-id="04dbf-176">この場合、セットアップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-176">In this scenario, Setup will fail.</span></span>  
  
## <a name="during-or-after-installation-of-ssnoversion"></a><span data-ttu-id="04dbf-177">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  のインストール中またはインストール後</span><span class="sxs-lookup"><span data-stu-id="04dbf-177">During or After Installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="04dbf-178">インストール後にアカウントと認証モードに関する次のベスト プラクティスに従うと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールのセキュリティを強化できます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-178">After installation, you can enhance the security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation by following these best practices regarding accounts and authentication modes:</span></span>  
  
 <span data-ttu-id="04dbf-179">**サービス アカウント**</span><span class="sxs-lookup"><span data-stu-id="04dbf-179">**Service accounts**</span></span>  
  
-   <span data-ttu-id="04dbf-180">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスは、可能な限り低い権限で実行します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-180">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services by using the lowest possible permissions.</span></span>  
  
-   <span data-ttu-id="04dbf-181">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを、権限の低い Windows ローカル ユーザー アカウントまたはドメイン ユーザー アカウントに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-181">Associate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services with low privileged Windows local user accounts, or domain user accounts.</span></span>  
  
-   <span data-ttu-id="04dbf-182">詳細については、「 [Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-182">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
 <span data-ttu-id="04dbf-183">**認証モード**</span><span class="sxs-lookup"><span data-stu-id="04dbf-183">**Authentication mode**</span></span>  
  
-   <span data-ttu-id="04dbf-184">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との接続には Windows 認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="04dbf-184">Require Windows Authentication for connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="04dbf-185">Kerberos 認証を使用する。</span><span class="sxs-lookup"><span data-stu-id="04dbf-185">Use Kerberos authentication.</span></span> <span data-ttu-id="04dbf-186">詳細については、「 [Kerberos 接続用のサービス プリンシパル名の登録](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04dbf-186">For more information, see [Register a Service Principal Name for Kerberos Connections](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).</span></span>  
  
 <span data-ttu-id="04dbf-187">**強力なパスワード**</span><span class="sxs-lookup"><span data-stu-id="04dbf-187">**Strong passwords**</span></span>  
  
-   <span data-ttu-id="04dbf-188">`sa` アカウントには、必ず強力なパスワードを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-188">Always assign a strong password to the `sa` account.</span></span>  
  
-   <span data-ttu-id="04dbf-189">パスワードの強度と有効期限に関するパスワード ポリシー チェックを必ず有効にします。</span><span class="sxs-lookup"><span data-stu-id="04dbf-189">Always enable password policy checking for password strength and expiration.</span></span>  
  
-   <span data-ttu-id="04dbf-190">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに、必ず強力なパスワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="04dbf-190">Always use strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="04dbf-191">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のセットアップ時に、ログインは BUILTIN\Users グループに追加されます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-191">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="04dbf-192">これにより、コンピューターの認証されたすべてのユーザーが public ロールのメンバーとして [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のインスタンスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="04dbf-192">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="04dbf-193">BUILTIN\Users ログインを安全に削除して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] アクセスを、個別のログインを持つコンピューター ユーザーまたはログインを持つ他の Windows グループのメンバーに制限できます。</span><span class="sxs-lookup"><span data-stu-id="04dbf-193">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04dbf-194">参照</span><span class="sxs-lookup"><span data-stu-id="04dbf-194">See Also</span></span>  
 <span data-ttu-id="04dbf-195">[SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="04dbf-195">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 <span data-ttu-id="04dbf-196">[ネットワーク プロトコルとネットワーク ライブラリ](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="04dbf-196">[Network Protocols and Network Libraries](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 [<span data-ttu-id="04dbf-197">Kerberos 接続用のサービス プリンシパル名の登録</span><span class="sxs-lookup"><span data-stu-id="04dbf-197">Register a Service Principal Name for Kerberos Connections</span></span>](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)  
  
  
