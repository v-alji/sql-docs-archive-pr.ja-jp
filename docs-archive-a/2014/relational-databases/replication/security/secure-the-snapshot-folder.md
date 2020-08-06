---
title: スナップショット フォルダーのセキュリティ保護 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], security
ms.assetid: 3cd877d1-ffb8-48fd-a72b-98eb948aad27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c977936ad2aca6e5a98ee685a15662a00b625494
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643233"
---
# <a name="secure-the-snapshot-folder"></a><span data-ttu-id="ffccf-102">スナップショット フォルダーのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ffccf-102">Secure the Snapshot Folder</span></span>
  <span data-ttu-id="ffccf-103">スナップショット フォルダーは、スナップショット ファイルが格納されるディレクトリです。このディレクトリは、スナップショットの格納専用に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffccf-103">The snapshot folder is a directory that stores snapshot files; it is recommended that you dedicate the directory for snapshot storage.</span></span> <span data-ttu-id="ffccf-104">スナップショット エージェントにこのフォルダーへの書き込み権限を許可し、マージ エージェントまたはディストリビューション エージェントがこのフォルダーへのアクセスに使用する Windows アカウントにのみ読み取り権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="ffccf-104">Grant the Snapshot Agent write permission to the folder, and ensure that read permission is granted only to the Windows account that the Merge Agent or Distribution agent uses when accessing the folder.</span></span> <span data-ttu-id="ffccf-105">リモート コンピューターのスナップショット フォルダーにアクセスするには、エージェントに関連付けられている Windows アカウントがドメイン アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffccf-105">The Windows account associated with the agent must be a domain account to access a snapshot folder that is located on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffccf-106">管理者はユーザー アカウント制御 (UAC) を使用して、自身の昇格したユーザーの権利 ( *権限*とも呼ばれる) を管理できます。</span><span class="sxs-lookup"><span data-stu-id="ffccf-106">User Account Control (UAC)  helps administrators manage their elevated user rights (sometimes called *privileges*).</span></span> <span data-ttu-id="ffccf-107">UAC が有効になっているオペレーティング システムで実行する場合は、管理者は管理者自身の管理権限を使用しません。</span><span class="sxs-lookup"><span data-stu-id="ffccf-107">When running on operating systems that have UAC enabled, administrators do not use their administrative rights.</span></span> <span data-ttu-id="ffccf-108">代わりに、標準ユーザー (管理者以外のユーザー) としてほとんどの操作を実行し、必要な場合にのみ一時的に管理権限を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffccf-108">Instead, they perform most actions as standard (non-administrative) users, temporarily assuming their administrative rights only when it is required.</span></span> <span data-ttu-id="ffccf-109">UAC により、スナップショット共有への管理アクセスが妨げられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ffccf-109">UAC can prevent administrative access to the snapshot share.</span></span> <span data-ttu-id="ffccf-110">このため、スナップショット エージェント、ディストリビューション エージェント、およびマージ エージェントによって使用される Windows アカウントに、スナップショット共有の権限を明示的に与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffccf-110">You must therefore explicitly grant snapshot share permissions to the Windows accounts that are used by the Snapshot Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="ffccf-111">この操作は、Windows アカウントが Administrators グループのメンバーである場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="ffccf-111">You must do this even if the Windows accounts are members of the Administrators group.</span></span>  
  
 <span data-ttu-id="ffccf-112">ディストリビューションの構成ウィザードまたはパブリケーションの新規作成ウィザードを使用してディストリビューターを構成すると、スナップショット フォルダーの既定の場所は、X:\Program Files\Microsoft SQL Server\\ *\<instance>* \MSSQL\ReplData.</span><span class="sxs-lookup"><span data-stu-id="ffccf-112">When configuring a Distributor through the Configure Distribution Wizard or the New Publication Wizard, the snapshot folder defaults to a local path: X:\Program Files\Microsoft SQL Server\\*\<instance>* \MSSQL\ReplData.</span></span> <span data-ttu-id="ffccf-113">リモート ディストリビューターやプル サブスクリプションを使用する場合は、ローカル パスではなく UNC ネットワーク共有 (\\\\<*computername>* \snapshot など) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffccf-113">If you are using a remote Distributor or pull subscriptions, you must specify a UNC network share (such as \\\\<*computername>* \snapshot) rather than a local path.</span></span>  
  
 <span data-ttu-id="ffccf-114">スナップショット フォルダーへのアクセス許可を付与する方法は、フォルダーへのアクセス方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ffccf-114">When granting permissions to access the snapshot folder, you must grant them according to the way in which the folder is accessed.</span></span> <span data-ttu-id="ffccf-115">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Server 2003 では、次のダイアログ ボックス タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffccf-115">The following dialog box tabs are used in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003:</span></span>  
  
-   <span data-ttu-id="ffccf-116">ローカル パスを指定する場合は、フォルダーの **[プロパティ]** ダイアログ ボックスの **[セキュリティ]** タブを使用してアクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="ffccf-116">If you specify a local path, grant permissions through the **Security** tab of the **Properties** dialog box for the folder.</span></span>  
  
-   <span data-ttu-id="ffccf-117">ネットワーク共有を指定する場合は、フォルダーの **[プロパティ]** ダイアログ ボックスの **[共有]** タブを使用してアクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="ffccf-117">If you specify a network share, grant permissions through the **Sharing** tab of the **Properties** dialog box for the folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ffccf-118">ディストリビューター上でレプリケーション エージェントを実行する場合は、フォルダーの **[プロパティ]** ダイアログ ボックスの **[セキュリティ]** タブを使用して、エージェントの実行に使用する Windows アカウントにアクセス許可を付与してください。</span><span class="sxs-lookup"><span data-stu-id="ffccf-118">If the replication agent runs on the Distributor, use the **Security** tab of the **Properties** dialog box for the folder to grant permissions to the Windows account used to run the agent.</span></span> <span data-ttu-id="ffccf-119">ネットワーク共有を使用する場合も、この操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ffccf-119">Do this even when a network share is used.</span></span> <span data-ttu-id="ffccf-120">また、パブリッシャーとディストリビューターが同じコンピューター上にある場合は、プッシュ サブスクリプションのマージ エージェントとディストリビューション エージェント、およびスナップショット エージェントに対してもこの操作を行ってください。</span><span class="sxs-lookup"><span data-stu-id="ffccf-120">This applies to the Merge Agent and Distribution Agent for a push subscription and to the Snapshot Agent when the Publisher and Distributor are on the same computer.</span></span>  
  
 <span data-ttu-id="ffccf-121">ローカル パスおよびネットワーク共有のアクセス許可の設定の詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffccf-121">For more information about setting permissions for local paths and network shares, see the Windows documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffccf-122">パブリケーションが削除された場合、レプリケーションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストでスナップショット フォルダーを削除しようとします。</span><span class="sxs-lookup"><span data-stu-id="ffccf-122">If a publication is dropped, replication attempts to remove the snapshot folder under the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account.</span></span> <span data-ttu-id="ffccf-123">このアカウントに十分な権限がない場合は、十分な権限を持つアカウントでログインして、手動でフォルダーを削除してください。</span><span class="sxs-lookup"><span data-stu-id="ffccf-123">If this account does not have sufficient privileges, log in with an account that does have sufficient privileges and remove the folder manually.</span></span> <span data-ttu-id="ffccf-124">フォルダーを削除するには、ローカル パスの場合は **変更** 特権が、ネットワーク共有の場合は **フル コントロール** 特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="ffccf-124">Removing a folder requires the **Modify** privilege if the folder is a local path or the **Full Control** privilege if the folder is a network path.</span></span>  
  
## <a name="delivering-snapshots-through-ftp"></a><span data-ttu-id="ffccf-125">FTP によるスナップショットの配信</span><span class="sxs-lookup"><span data-stu-id="ffccf-125">Delivering Snapshots Through FTP</span></span>  
 <span data-ttu-id="ffccf-126">セキュリティの観点から、スナップショットは UNC 共有に格納することをお勧めします。ただし、スナップショットを FTP 共有に格納して、FTP を使ってサブスクライバーに配信することもできます。</span><span class="sxs-lookup"><span data-stu-id="ffccf-126">It is recommended as a security best practice that snapshots be stored in a UNC share, but snapshots can be stored in an FTP share and then delivered to a Subscriber through FTP.</span></span> <span data-ttu-id="ffccf-127">FTP サーバーを構成する際には、仮想ディレクトリが公開する UNC 共有で、パブリケーションのスナップショット エージェントによる書き込みアクセスが許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ffccf-127">When configuring the FTP server, ensure that the virtual directory exposes an underlying UNC share that permits write access by the Snapshot Agent for the publication.</span></span>  
  
 <span data-ttu-id="ffccf-128">FTP でスナップショットを取得するようにサブスクライバーを構成するには、まず FTP サーバーで FTP のログインとパスワードを設定し、スナップショット ファイルをダウンロードできるようにサブスクライバーに読み取りアクセス ("get") を許可します。</span><span class="sxs-lookup"><span data-stu-id="ffccf-128">To configure a Subscriber to retrieve the Snapshot via FTP, first set up an FTP server with an FTP login and password that allows Subscribers read (or "get") access to allow the snapshot files to be downloaded.</span></span>  
  
 <span data-ttu-id="ffccf-129">FTP でスナップショットを配信する場合は、「[FTP でのスナップショットの配信](../publish/deliver-a-snapshot-through-ftp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffccf-129">To deliver snapshots through FTP, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
 <span data-ttu-id="ffccf-130">FTP でスナップショットにアクセスするためのパスワードの設定と変更については、「 [Secure the Publisher](secure-the-publisher.md)」の「FTP スナップショット配信」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffccf-130">For information about setting and changing the password for access to snapshots through FTP, see the section "FTP Snapshot Delivery" in the topic [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffccf-131">参照</span><span class="sxs-lookup"><span data-stu-id="ffccf-131">See Also</span></span>  
 <span data-ttu-id="ffccf-132">[代替スナップショットフォルダーの場所](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="ffccf-132">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="ffccf-133">[Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](../initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="ffccf-133">[Initialize a Subscription with a Snapshot](../initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="ffccf-134">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="ffccf-134">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="ffccf-135">[SQL Server レプリケーションのセキュリティ](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="ffccf-135">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="ffccf-136">FTP によるスナップショットの転送</span><span class="sxs-lookup"><span data-stu-id="ffccf-136">Transfer Snapshots Through FTP</span></span>](../transfer-snapshots-through-ftp.md)  
  
  
