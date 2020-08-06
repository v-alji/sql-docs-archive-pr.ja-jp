---
title: ディストリビューターのセキュリティ保護 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Distributors
- Distributors [SQL Server replication], security
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d55f5e214f89b678367124da8342ec9801ab686a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630890"
---
# <a name="secure-the-distributor"></a><span data-ttu-id="3acf8-102">ディストリビューターのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3acf8-102">Secure the Distributor</span></span>
  <span data-ttu-id="3acf8-103">レプリケーション エージェントのうち、ログ リーダー エージェント、スナップショット エージェント、キュー リーダー エージェント、ディストリビューション エージェント、およびマージ エージェントは、ディストリビューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="3acf8-103">The following replication agents connect to the Distributor: the Log Reader Agent, Snapshot Agent, Queue Reader Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="3acf8-104">最低限必要な権限のみを与え、かつすべてのパスワードの格納を保護するという原則に従って、これらの各エージェントに対し適切なログインを指定することは重要です。</span><span class="sxs-lookup"><span data-stu-id="3acf8-104">It is important to provide an appropriate login for each of these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords:</span></span>  
  
-   <span data-ttu-id="3acf8-105">ログインとパスワードの管理の詳細については、「[レプリケーションのログインとパスワードの管理](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3acf8-105">For information about managing logins and passwords, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="3acf8-106">各エージェントで必要な権限の詳細については、「 [Replication Agent Security Model](replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3acf8-106">For detailed information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="3acf8-107">ログインとパスワードの適切な管理に加えて、リモート サーバー リンク **repl_distributor** 、および **distributor_admin** アカウントのロールを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="3acf8-107">In addition to managing logins and passwords appropriately, it is important to understand the role of the **repl_distributor** remote server link and the **distributor_admin** account.</span></span>  
  
## <a name="securing-the-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="3acf8-108">パブリッシャーからディストリビューターへの接続の保護</span><span class="sxs-lookup"><span data-stu-id="3acf8-108">Securing the Connection from the Publisher to the Distributor</span></span>  
 <span data-ttu-id="3acf8-109">管理用のストアド プロシージャをパブリッシャーで実行し、ディストリビューターで情報を更新するために必要な通信をサポートするため、レプリケーションでは、リモート サーバー **repl_distributor**が自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="3acf8-109">To support the communication necessary when administrative stored procedures execute at the Publisher and update information at the Distributor, replication automatically configures the remote server **repl_distributor**.</span></span> <span data-ttu-id="3acf8-110">リモート サーバー エントリ **repl_distributor** は、ディストリビューション データベースがパブリッシャー インスタンス (ローカル ディストリビューター) 内に含まれるか、リモートの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス (リモート ディストリビューター) に存在するかにかかわらず、ディストリビューション データベースへの接続に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3acf8-110">The **repl_distributor** remote server entry is used for communication to the distribution database regardless of whether the distribution database is contained within the Publisher instance (a local Distributor) or resides within a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance (a remote Distributor).</span></span>  
  
 <span data-ttu-id="3acf8-111">ディストリビューション データベースがローカル インスタンスに含まれる場合は、ランダムなパスワードが生成され自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="3acf8-111">When the distribution database is contained on a local instance, a random password is generated and configured automatically.</span></span> <span data-ttu-id="3acf8-112">ディストリビューション データベースがリモート インスタンスにある場合は、パブリッシャーとディストリビューターのセットアップ時に管理者が共有パスワードを構成します。このパスワードは、 **repl_distributor** リンク上を流れるトラフィックの認証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3acf8-112">When the distribution database is located on a remote instance, the administrator configures a shared password during setup of the Publisher and Distributor; this password is then used to provide authentication of traffic that traverses the **repl_distributor** link.</span></span>  
  
 <span data-ttu-id="3acf8-113">ディストリビューターは、実行時にリモート サーバー エントリ **repl_distributor** を使用して、呼び出し元のサーバーがディストリビューターでパブリッシャーとして構成されていることを検証します。次に、パブリッシャーから渡されたパスワードを検証して、ストアド プロシージャがレプリケーション ストアド プロシージャであることを検証します。</span><span class="sxs-lookup"><span data-stu-id="3acf8-113">The Distributor uses the **repl_distributor** remote server entry to verify that the calling server is configured as a Publisher at the Distributor, validates the password supplied by the Publisher, and validates that the stored procedure is a replication stored procedure during execution.</span></span>  
  
 <span data-ttu-id="3acf8-114">セットアップ時にリモート サーバー エントリ **repl_distributor** に対して構成されたパスワードは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログイン **distributor_admin**と関連付けられます。このログインは、ディストリビューター上で固定サーバー ロール **sysadmin** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="3acf8-114">The password configured for the **repl_distributor** remote server entry during setup is associated with a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login, **distributor_admin**, which is added to the **sysadmin** fixed server role at the Distributor.</span></span> <span data-ttu-id="3acf8-115">**distributor_admin** ログインは、ディストリビューターに接続するときに、レプリケーション ストアド プロシージャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="3acf8-115">The **distributor_admin** login is used by replication stored procedures when connecting to the Distributor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3acf8-116">**distributor_admin** のパスワードを手動で変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3acf8-116">Do not change the password for the **distributor_admin** manually.</span></span> <span data-ttu-id="3acf8-117">パスワードの変更は、必ず **sp_changedistributor_password** ストアド プロシージャか、 **の** [ディストリビューターのプロパティ] **または** [レプリケーション パスワードの更新] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスで行ってください。これにより、パスワードの変更がローカル パブリケーションに自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="3acf8-117">Always use the **sp_changedistributor_password** stored procedure, or the **Distributor Properties** or **Update Replication Passwords** dialog boxes in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], because password changes are then applied to local publications automatically.</span></span>  
  
## <a name="snapshot-folder-security"></a><span data-ttu-id="3acf8-118">スナップショット フォルダーのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="3acf8-118">Snapshot Folder Security</span></span>  
 <span data-ttu-id="3acf8-119">スナップショット共有には、マージ エージェント (マージ レプリケーションの場合) またはディストリビューション エージェント (スナップショット レプリケーションまたはトランザクション レプリケーションの場合) の実行に使用するアカウントに読み取りアクセスが許可され、スナップショット エージェントの実行に使用するアカウントに書き込みアクセスが許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3acf8-119">Ensure that the snapshot share has read access granted to the account under which the Merge Agent (for merge replication) or Distribution Agent (for snapshot or transactional replication) runs and write access granted to the account under which the Snapshot Agent runs.</span></span> <span data-ttu-id="3acf8-120">スナップショット フォルダーの詳細については、「[スナップショット フォルダーのセキュリティ保護](secure-the-snapshot-folder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3acf8-120">For more information about the snapshot folder, see [Secure the Snapshot Folder](secure-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3acf8-121">参照</span><span class="sxs-lookup"><span data-stu-id="3acf8-121">See Also</span></span>  
 <span data-ttu-id="3acf8-122">[レプリケーションのセキュリティ設定の表示および変更](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="3acf8-122">[View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="3acf8-123">[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="3acf8-123">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="3acf8-124">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="3acf8-124">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="3acf8-125">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="3acf8-125">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
