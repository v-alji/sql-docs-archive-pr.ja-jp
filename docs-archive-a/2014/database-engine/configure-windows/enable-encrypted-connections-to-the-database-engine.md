---
title: データベースエンジンへの暗号化接続を有効にします (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1653df929e3f8bc67158a0685ce07b8ba65de6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741242"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a><span data-ttu-id="b7977-102">データベース エンジンへの暗号化接続の有効化 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="b7977-102">Enable Encrypted Connections to the Database Engine (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="b7977-103">このトピックでは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 構成マネージャーを使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] の証明書を指定することにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの暗号化接続を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7977-103">This topic describes how to enable encrypted connections for an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] by specifying a certificate for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="b7977-104">サーバー コンピューターには証明書を提供し、クライアント マシンは証明書のルート機関を信頼するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7977-104">The server computer must have a certificate provisioned, and the client machine must be set up to trust the certificate's root authority.</span></span> <span data-ttu-id="b7977-105">提供は、証明書を Windows にインポートすることでインストールする処理です。</span><span class="sxs-lookup"><span data-stu-id="b7977-105">Provisioning is the process of installing a certificate by importing it into Windows.</span></span>  
  
 <span data-ttu-id="b7977-106">**サーバー認証**用の証明書が発行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7977-106">The certificate must be issued for **Server Authentication**.</span></span> <span data-ttu-id="b7977-107">証明書の名前は、コンピューターの完全修飾ドメイン名 (FQDN) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7977-107">The name of the certificate must be the fully qualified domain name (FQDN) of the computer.</span></span>  
  
 <span data-ttu-id="b7977-108">証明書は、コンピューター上のユーザーにローカルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b7977-108">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="b7977-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用するための証明書をインストールするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスと同じユーザー アカウントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを実行する必要があります。ただし、LocalSystem、NetworkService、または LocalService でサービスが実行されていて、管理者アカウントを使用している場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="b7977-109">To install a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service unless the service is running as LocalSystem, NetworkService, or LocalService, in which case you may use an administrative account.</span></span>  
  
 <span data-ttu-id="b7977-110">クライアントは、サーバーが使用する証明書の所有権を検証できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7977-110">The client must be able to verify the ownership of the certificate used by the server.</span></span> <span data-ttu-id="b7977-111">サーバー証明書に署名した証明機関の公開キー証明書をクライアントが持っている場合は、それ以上の構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b7977-111">If the client has the public key certificate of the certification authority that signed the server certificate, no further configuration is necessary.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b7977-112">Windows には、多くの証明機関の公開キー証明書が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7977-112">Windows includes the public key certificates of many certification authorities.</span></span> <span data-ttu-id="b7977-113">サーバー証明書に署名した公的または私的な証明機関に対する公開キー証明書をクライアントが持っていない場合は、サーバー証明書に署名した証明機関の公開キー証明書をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7977-113">If the server certificate was signed by a public or private certification authority for which the client does not have the public key certificate, you must install the public key certificate of the certification authority that signed the server certificate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7977-114">フェールオーバー クラスターで暗号化を使用する場合、フェールオーバー クラスター内のすべてのノードに対して、仮想サーバーの完全修飾 DNS 名を使用してサーバー証明書をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7977-114">To use encryption with a failover cluster, you must install the server certificate with the fully qualified DNS name of the virtual server on all nodes in the failover cluster.</span></span> <span data-ttu-id="b7977-115">たとえば、"test1." という名前のノードを持つ2ノードクラスターがあると *\<your company>* します。com と *\<your company>* test2.また、仮想サーバーを仮想サーバーとして使用している場合は、仮想サーバーをインストールする必要があり *\<your company>* ます。両方のノードの com。</span><span class="sxs-lookup"><span data-stu-id="b7977-115">For example, if you have a two-node cluster, with nodes named test1.*\<your company>*.com and test2.*\<your company>*.com, and you have a virtual server named virtsql, you need to install a certificate for virtsql.*\<your company>*.com on both nodes.</span></span> <span data-ttu-id="b7977-116">**[ForceEncryption]** オプションの値を **[はい]** に設定できます。</span><span class="sxs-lookup"><span data-stu-id="b7977-116">You can set the value of the **ForceEncryption**option to **Yes**.</span></span>  
  
 <span data-ttu-id="b7977-117">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b7977-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b7977-118">**暗号化された接続を有効にするには:**</span><span class="sxs-lookup"><span data-stu-id="b7977-118">**To enable encrypted connections:**</span></span>  
  
     [<span data-ttu-id="b7977-119">サーバーに証明書を提供 (インストール) する</span><span class="sxs-lookup"><span data-stu-id="b7977-119">Provision (install) a certificate on the server</span></span>](#Provision)  
  
     [<span data-ttu-id="b7977-120">サーバー証明書をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="b7977-120">Export the server certificate</span></span>](#Export)  
  
     [<span data-ttu-id="b7977-121">暗号化された接続を許可するサーバーを構成する</span><span class="sxs-lookup"><span data-stu-id="b7977-121">Configure the server to accept encrypted connections</span></span>](#ConfigureServerConnections)  
  
     [<span data-ttu-id="b7977-122">暗号化された接続を要求するようにクライアントを構成する</span><span class="sxs-lookup"><span data-stu-id="b7977-122">Configure the client to request encrypted connections</span></span>](#ConfigureClientConnections)  
  
     [<span data-ttu-id="b7977-123">SQL Server Management Studio から接続を暗号化する</span><span class="sxs-lookup"><span data-stu-id="b7977-123">Encrypt a connection from SQL Server Management Studio</span></span>](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="to-provision-install-a-certificate-on-the-server"></a><a name="Provision"></a> <span data-ttu-id="b7977-124">サーバーに証明書を提供 (インストール) するには</span><span class="sxs-lookup"><span data-stu-id="b7977-124">To provision (install) a certificate on the server</span></span>  
  
1.  <span data-ttu-id="b7977-125">[**スタート**] メニューの [ファイルの**実行**] をクリックし、[**名前**] ボックスに「」と入力して、 `MMC` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-125">On the **Start** menu, click **Run**, and in the **Open** box, type `MMC` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="b7977-126">MMC コンソールの **[ファイル]** メニューで、 **[スナップインの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-126">In the MMC console, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="b7977-127">**[スナップインの追加と削除]** ダイアログ ボックスで **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-127">In the **Add/Remove Snap-in** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="b7977-128">**[スタンドアロン スナップインの追加]** ダイアログ ボックスで **[証明書]** をクリックし、次に **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-128">In the **Add Standalone Snap-in** dialog box, click **Certificates**, click **Add**.</span></span>  
  
5.  <span data-ttu-id="b7977-129">**[証明書スナップイン]** ダイアログ ボックスで **[コンピューター アカウント]** をクリックし、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-129">In the **Certificates snap-in** dialog box, click **Computer account**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="b7977-130">**[スタンドアロン スナップインの追加]** ダイアログ ボックスで **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-130">In the **Add Standalone Snap-in** dialog box, click **Close.**</span></span>  
  
7.  <span data-ttu-id="b7977-131">**[スナップインの追加と削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-131">In the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="b7977-132">**[証明書]** スナップインで、 **[証明書]** 、 **[個人]** の順に展開し、 **[証明書]** を右クリックします。次に **[すべてのタスク]** をポイントし、 **[インポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-132">In the **Certificates** snap-in, expand **Certificates**, expand **Personal**, and then right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
9. <span data-ttu-id="b7977-133">**[証明書のインポート ウィザード]** を完了して証明書をコンピューターに追加し、MMC コンソールを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b7977-133">Complete the **Certificate Import Wizard**, to add a certificate to the computer, and close the MMC console.</span></span> <span data-ttu-id="b7977-134">コンピューターへの証明書の追加の詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7977-134">For more information about adding a certificate to a computer, see your Windows documentation.</span></span>  
  
###  <a name="to-export-the-server-certificate"></a><a name="Export"></a> <span data-ttu-id="b7977-135">サーバー証明書をエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="b7977-135">To export the server certificate</span></span>  
  
1.  <span data-ttu-id="b7977-136">**[証明書]** スナップインで、 **[証明書]**  /  **[個人]** フォルダーで証明書を探し、 **[証明書]** を右クリックします。次に **[すべてのタスク]** をポイントし、 **[エクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-136">From the **Certificates** snap-in, locate the certificate in the **Certificates** / **Personal** folder, right-click the **Certificate**, point to **All Tasks**, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="b7977-137">**証明書のエクスポート ウィザード**を実行して、証明書ファイルを使いやすい場所に格納します。</span><span class="sxs-lookup"><span data-stu-id="b7977-137">Complete the **Certificate Export Wizard**, storing the certificate file in a convenient location.</span></span>  
  
###  <a name="to-configure-the-server-to-accept-encrypted-connections"></a><a name="ConfigureServerConnections"></a> <span data-ttu-id="b7977-138">暗号化された接続を許可するサーバーを構成するには</span><span class="sxs-lookup"><span data-stu-id="b7977-138">To configure the server to accept encrypted connections</span></span>  
  
1.  <span data-ttu-id="b7977-139">**SQL Server 構成マネージャー**で、 **[SQL Server ネットワークの構成]** を展開し、 **[ _\<server instance>_ のプロトコル]** を右クリックします。次に **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-139">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** _\<server instance>_, and then select**Properties**.</span></span>  
  
2.  <span data-ttu-id="b7977-140">[プロパティ**のプロトコル** _\<instance name>_ **Properties** ] ダイアログボックスの [**証明書**] タブで、[**証明**書] ボックスの一覧から目的の証明書を選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-140">In the **Protocols for**_\<instance name>_ **Properties** dialog box, on the **Certificate** tab, select the desired certificate from the drop down for the **Certificate** box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b7977-141">**[フラグ]** タブの **[ForceEncryption]** ボックスの一覧の **[はい]** をクリックし、 **[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b7977-141">On the **Flags** tab, in the **ForceEncryption** box, select **Yes**, and then click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="b7977-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="b7977-142">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
###  <a name="to-configure-the-client-to-request-encrypted-connections"></a><a name="ConfigureClientConnections"></a> <span data-ttu-id="b7977-143">暗号化された接続を要求するクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="b7977-143">To configure the client to request encrypted connections</span></span>  
  
1.  <span data-ttu-id="b7977-144">元の証明書ファイルまたはエクスポートした証明書ファイルを、クライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b7977-144">Copy either the original certificate or the exported certificate file to the client computer.</span></span>  
  
2.  <span data-ttu-id="b7977-145">クライアント コンピューターで、 **証明書** スナップインを使用して、ルート証明書またはエクスポートした証明書ファイルをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b7977-145">On the client computer, use the **Certificates** snap-in to install either the root certificate or the exported certificate file.</span></span>  
  
3.  <span data-ttu-id="b7977-146">コンソール ペインで **[SQL Server Native Client の構成]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-146">In the console pane, right-click **SQL Server Native Client Configuration**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b7977-147">**[フラグ]** ページの **[プロトコルの暗号化を設定する]** ボックスで、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-147">On the **Flags** page, in the **Force protocol encryption** box, click **Yes**.</span></span>  
  
###  <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a><a name="EncryptConnection"></a><span data-ttu-id="b7977-148">SQL Server Management Studio からの接続を暗号化するには</span><span class="sxs-lookup"><span data-stu-id="b7977-148">To encrypt a connection from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b7977-149">オブジェクト エクスプローラー ツール バーで **[接続]** をクリックし、 **[データベース エンジン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-149">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="b7977-150">**[サーバーへの接続]** ダイアログ ボックスで接続情報を入力し、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-150">In the **Connect to Server** dialog box, complete the connection information, and then click **Options**.</span></span>  
  
3.  <span data-ttu-id="b7977-151">**[接続のプロパティ]** タブで **[暗号化接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7977-151">On the **Connection Properties** tab, click **Encrypt connection**.</span></span>  
  
  
