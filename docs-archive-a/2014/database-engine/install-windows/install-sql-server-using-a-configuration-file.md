---
title: 構成ファイルを使用して SQL Server 2014 をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: a832153a-6775-4bed-83f0-55790766d885
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a2f09ad6253762fe5b525f6c918931f4806c84c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713437"
---
# <a name="install-sql-server-2014-using-a-configuration-file"></a><span data-ttu-id="90e72-102">構成ファイルを使用した SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="90e72-102">Install SQL Server 2014 Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90e72-103">セットアップには、システムの既定値および実行時入力に基づいて構成ファイルを生成する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="90e72-103">Setup provides the ability to generate a configuration file based upon the system default and run-time inputs.</span></span> <span data-ttu-id="90e72-104">構成ファイルを使用すると、同じ構成の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を企業全体に配置できます。</span><span class="sxs-lookup"><span data-stu-id="90e72-104">You can use the configuration file to deploy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] throughout the enterprise with the same configuration.</span></span> <span data-ttu-id="90e72-105">また、Setup.exe を起動するバッチ ファイルを作成して、企業全体で手動によるインストールを標準化することもできます。</span><span class="sxs-lookup"><span data-stu-id="90e72-105">You can also standardize manual installations throughout the enterprise, by creating a batch file that launches Setup.exe.</span></span>  
  
 <span data-ttu-id="90e72-106">セットアップでは、コマンド プロンプトからのみ構成ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="90e72-106">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="90e72-107">以下に、構成ファイルを使用する際のパラメーターの処理順序について説明します。</span><span class="sxs-lookup"><span data-stu-id="90e72-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="90e72-108">構成ファイルによって、パッケージの既定値が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="90e72-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="90e72-109">コマンド ライン値によって、構成ファイル内の値が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="90e72-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="90e72-110">構成ファイルを使用すると、インストールごとにパラメーターおよび値を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="90e72-110">The configuration file can be used to track the parameters and values for each installation.</span></span> <span data-ttu-id="90e72-111">したがって、インストールを確認および監査する場合に構成ファイルが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="90e72-111">This makes the configuration file useful for verifying and auditing the installations.</span></span>  
  
## <a name="configuration-file-structure"></a><span data-ttu-id="90e72-112">構成ファイルの構造</span><span class="sxs-lookup"><span data-stu-id="90e72-112">Configuration File Structure</span></span>  
 <span data-ttu-id="90e72-113">ConfigurationFile.ini ファイルは、パラメーター (名前と値のペア) と説明のコメントが含まれるテキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="90e72-113">The ConfigurationFile.ini file is a text file with parameters (name/value pair) and descriptive comments.</span></span>  
  
 <span data-ttu-id="90e72-114">次に、ConfigurationFile.ini ファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="90e72-114">The following is an example of a ConfigurationFile.ini file:</span></span>  
  
```  
; Microsoft SQL Server Configuration file  
[OPTIONS]  
; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE.   
; This is a required parameter.   
ACTION="Install"  
; Specifies features to install, uninstall, or upgrade.   
; The list of top-level features include SQL, AS, RS, IS, and Tools.   
; The SQL feature will install the database engine, replication, and full-text.   
; The Tools feature will install Management Tools, Books online,   
; SQL Server Data Tools, and other shared components.   
FEATURES=SQL,Tools  
```  
  
#### <a name="how-to-generate-a-configuration-file"></a><span data-ttu-id="90e72-115">構成ファイルを生成する方法</span><span class="sxs-lookup"><span data-stu-id="90e72-115">How to generate a configuration file</span></span>  
  
1.  <span data-ttu-id="90e72-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアを挿入します。</span><span class="sxs-lookup"><span data-stu-id="90e72-116">Insert the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="90e72-117">ルート フォルダーの Setup.exe をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="90e72-117">From the root folder, double-click Setup.exe.</span></span> <span data-ttu-id="90e72-118">ネットワーク共有からインストールするには、ネットワーク共有上のルート フォルダーに移動し、Setup.exe をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="90e72-118">To install from a network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90e72-119">Express Edition のセットアップでは、構成ファイルは自動的に作成されません。</span><span class="sxs-lookup"><span data-stu-id="90e72-119">Express Edition setup does not create a configuration file automatically.</span></span> <span data-ttu-id="90e72-120">次のコマンドを実行すると、セットアップが開始され、構成ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="90e72-120">The following command will start  setup and create a configuration file.</span></span>  
    >   
    >  <span data-ttu-id="90e72-121">SETUP.exe /UIMODE=Normal /ACTION=INSTALL</span><span class="sxs-lookup"><span data-stu-id="90e72-121">SETUP.exe /UIMODE=Normal /ACTION=INSTALL</span></span>  
  
2.  <span data-ttu-id="90e72-122">ウィザードに従って **[インストールの準備完了]** ページまで進みます。</span><span class="sxs-lookup"><span data-stu-id="90e72-122">Follow the wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="90e72-123">構成ファイルのパスは、 **[インストールの準備完了]** ページの [構成ファイルのパス] セクションで指定します。</span><span class="sxs-lookup"><span data-stu-id="90e72-123">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span> <span data-ttu-id="90e72-124">のインストール方法の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「インストール[ウィザードから SQL Server 2014 をインストールする」 &#40;セットアップ&#41;](install-sql-server-from-the-installation-wizard-setup.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90e72-124">For more information about how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="90e72-125">INI ファイルを生成するには、インストールを実際に完了しなくてもセットアップを取り消します。</span><span class="sxs-lookup"><span data-stu-id="90e72-125">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="90e72-126">セットアップ インフラストラクチャは、パスワードなどの機密情報を除き、実行したアクションに対してすべての適切なパラメーターを書き出します。</span><span class="sxs-lookup"><span data-stu-id="90e72-126">The setup infrastructure writes out all the appropriate parameters for the actions that were run, with the exception of sensitive information such as passwords.</span></span> <span data-ttu-id="90e72-127">/IAcceptSQLServerLicenseTerms パラメーターは構成ファイルに書き出されないので、構成ファイルに変更を加えるか、コマンド プロンプトで値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e72-127">The /IAcceptSQLServerLicenseTerms parameter is also not written out to the configuration file and requires either a modification of the configuration file or a value to be supplied at the command prompt.</span></span> <span data-ttu-id="90e72-128">詳細については、「[コマンド プロンプトからの SQL Server 2014 のインストール](install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90e72-128">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="90e72-129">また、値が通常はコマンド プロンプトで指定されないブール型パラメーターの場合は、値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="90e72-129">In addition, a value is included for Boolean parameters where a value is usually not supplied through the command prompt.</span></span>  
  
## <a name="using-the-configuration-file-to-install-ssnoversion"></a><span data-ttu-id="90e72-130">構成ファイルを使用した SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90e72-130">Using the Configuration File to Install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="90e72-131">コマンド ライン インストールでのみ構成ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="90e72-131">You can only use the configuration file on command-line installations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90e72-132">構成ファイルに変更を加える必要がある場合は、コピーを作成して、コピーを変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90e72-132">If you need to make changes to the configuration file, we recommend that you make a copy and work with the copy.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-install-a-stand-alone-ssnoversion-instance"></a><span data-ttu-id="90e72-133">構成ファイルを使用してスタンドアロンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="90e72-133">How to use a configuration file to install a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance</span></span>  
  
-   <span data-ttu-id="90e72-134">コマンド プロンプトからインストールを実行し、 *ConfigurationFile* パラメーターを使用して ConfigurationFile.ini を指定します。</span><span class="sxs-lookup"><span data-stu-id="90e72-134">Run the installation through the command prompt and supply the ConfigurationFile.ini using the *ConfigurationFile* parameter.</span></span>  
  
#### <a name="how-to-use-a-configuration-file-to-prepare-and-complete-an-image-of-a-stand-alone-ssnoversion-instance-sysprep"></a><span data-ttu-id="90e72-135">構成ファイルを使用してスタンドアロン [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのイメージの準備と完了を行う方法 (SysPrep)</span><span class="sxs-lookup"><span data-stu-id="90e72-135">How to use a configuration file to prepare and complete an image of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (SysPrep)</span></span>  
  
1.  <span data-ttu-id="90e72-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つまたは複数のインスタンスを準備し、同じコンピューター上で構成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="90e72-136">To prepare one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and configure them on the same machine.</span></span>  
  
    -   <span data-ttu-id="90e72-137">[インストール センター] の **[詳細設定]** ページで、 **[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスのイメージの準備]** を実行し、イメージ準備用構成ファイルをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90e72-137">Run **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="90e72-138">さらに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを準備するには、同じイメージ準備用構成ファイルをテンプレートとして使用します。</span><span class="sxs-lookup"><span data-stu-id="90e72-138">Use the same prepare image configuration file as a template to prepare more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="90e72-139">[インストール センター] の **[詳細設定]** ページで、 **[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の準備済みスタンドアロン インスタンスのイメージの完了]** を実行し、コンピューター上で準備済みのインスタンスを構成します。</span><span class="sxs-lookup"><span data-stu-id="90e72-139">Run **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center to configure a prepared instances on the machine.</span></span>  
  
2.  <span data-ttu-id="90e72-140">Windows SysPrep ツールを使用して、未構成の準備済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを含むオペレーティング システムのイメージを準備するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="90e72-140">To prepare an image of the operating system including an unconfigured prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], using Windows SysPrep tool.</span></span>  
  
    -   <span data-ttu-id="90e72-141">[インストール センター] の [詳細設定] ページで、 **[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスのイメージの準備]** を実行し、イメージ準備用構成ファイルをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90e72-141">Run the **Image preparation of a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the Advanced page of the Installation Center and capture the prepare image configuration file.</span></span>  
  
    -   <span data-ttu-id="90e72-142">[インストール センター] の **[詳細設定]** ページで、 **[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の準備済みスタンドアロン インスタンスのイメージの完了]** を実行します。ただし、完了用構成ファイルをキャプチャしたら、 **[イメージの完了の準備]** ページで処理をキャンセルしてください。</span><span class="sxs-lookup"><span data-stu-id="90e72-142">Run the **Image completion of a prepared stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** from the **Advanced** page of the Installation Center, but cancel it on the **Ready to Complete** page after capturing the complete configuration file.</span></span>  
  
    -   <span data-ttu-id="90e72-143">イメージ完了用構成ファイルは、準備済みのインスタンスの構成を自動化するために、Windows イメージと共に保存できます。</span><span class="sxs-lookup"><span data-stu-id="90e72-143">The complete image configuration file can be stored with the Windows image for automating the configuration of the prepared instances.</span></span>  
  
#### <a name="how-to-install-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="90e72-144">構成ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="90e72-144">How to install a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="90e72-145">統合インストール方法は次のとおりです (ノードに単一ノードのフェールオーバー クラスターを作成し、追加ノードでは AddNode を実行します)。</span><span class="sxs-lookup"><span data-stu-id="90e72-145">Integrated Install option (create a single node failover cluster on a node and for additional nodes, run AddNode on them):</span></span>  
  
    -   <span data-ttu-id="90e72-146">[フェールオーバー クラスターをインストールする] オプションを実行して、すべてのインストール設定の一覧を示す構成ファイルをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90e72-146">Run the "Install a Failover Cluster" option and capture the configuration file that lists all the installation settings.</span></span>  
  
    -   <span data-ttu-id="90e72-147">*ConfigurationFile* パラメーターを指定して、コマンド ライン フェールオーバー クラスターのインストールを実行します。</span><span class="sxs-lookup"><span data-stu-id="90e72-147">Run the command-line failover cluster install by supplying the *ConfigurationFile* parameter.</span></span>  
  
    -   <span data-ttu-id="90e72-148">追加するノードで、AddNode を実行して既存のフェールオーバー クラスターに適用できる ConfigurationFile.ini ファイルをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90e72-148">On an additional node to be added, run AddNode to capture the ConfigurationFile.ini file applicable to the existing failover cluster.</span></span>  
  
    -   <span data-ttu-id="90e72-149">同じ構成ファイルを指定して ConfigurationFile パラメーターを使用することによって、フェールオーバー クラスターを結合するすべての追加ノードでコマンド ライン AddNode を実行します。</span><span class="sxs-lookup"><span data-stu-id="90e72-149">Run the command-line AddNode on all the additional nodes that will join the failover cluster, by supplying the same configuration file using the ConfigurationFile parameter.</span></span>  
  
2.  <span data-ttu-id="90e72-150">詳細なインストール方法は次のとおりです (すべてのフェールオーバー クラスター ノードでフェールオーバー クラスターを準備し、次にすべてのノードを準備した後、共有ディスクを所有するノードで完了操作を実行します)。</span><span class="sxs-lookup"><span data-stu-id="90e72-150">Advanced install option (prepare failover cluster on all failover cluster nodes, then, after preparing all the nodes, run complete on the node that owns the shared disk):</span></span>  
  
    -   <span data-ttu-id="90e72-151">いずれかのノードで **[準備]** を実行して、ConfigurationFile.ini ファイルをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90e72-151">Run **Prepare** on one of the nodes, and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="90e72-152">準備するフェールオーバー クラスターのすべてのノードで、設定する同じ ConfigurationFile.ini ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="90e72-152">Supply the same ConfigurationFile.ini file to Setup on all the nodes that will be prepared for the failover cluster.</span></span>  
  
    -   <span data-ttu-id="90e72-153">すべてのノードを準備した後、共有ディスクを所有するノードでフェールオーバー クラスターの完了操作を実行して、ConfigurationFile.ini ファイルをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90e72-153">After all the nodes have been prepared, run a complete failover cluster operation on the node that owns the shared disk and capture the ConfigurationFile.ini file.</span></span>  
  
    -   <span data-ttu-id="90e72-154">この ConfigurationFile.ini ファイルを指定すると、フェールオーバー クラスターを完了できます。</span><span class="sxs-lookup"><span data-stu-id="90e72-154">You can then supply this ConfigurationFile.ini file to complete the failover cluster.</span></span>  
  
#### <a name="how-to-add-or-remove-a-node-to-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="90e72-155">構成ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターにノードを追加または削除する方法</span><span class="sxs-lookup"><span data-stu-id="90e72-155">How to add or remove a node to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
-   <span data-ttu-id="90e72-156">フェールオーバー クラスターにノードを追加したり、フェールオーバー クラスターからノードを削除したりするために以前使用した構成ファイルがある場合は、同じファイルを再利用してノードの追加や削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="90e72-156">If you have a configuration file that was previously used to add a node to or remove a node from a failover cluster, you can reuse that same file to add or remove additional nodes.</span></span>  
  
#### <a name="how-to-upgrade-a-ssnoversion-failover-cluster-using-the-configuration-file"></a><span data-ttu-id="90e72-157">構成ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアップグレードする方法</span><span class="sxs-lookup"><span data-stu-id="90e72-157">How to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster using the configuration file</span></span>  
  
1.  <span data-ttu-id="90e72-158">パッシブ ノードでアップグレードを実行して、ConfigurationFile.ini ファイルをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90e72-158">Run upgrade on the passive node and capture the ConfigurationFile.ini file.</span></span> <span data-ttu-id="90e72-159">それには、実際のアップグレードを実行するか、または実際のアップグレードを実行しないで最後に終了します。</span><span class="sxs-lookup"><span data-stu-id="90e72-159">You can do this either by performing the actual upgrade, or exiting at the end without doing the actual upgrade.</span></span>  
  
2.  <span data-ttu-id="90e72-160">アップグレードするすべての追加ノードで、ConfigurationFile.ini ファイルを指定して処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="90e72-160">On all the additional nodes to be upgraded, supply the ConfigurationFile.ini file to complete the process.</span></span>  
  
## <a name="sample-syntax"></a><span data-ttu-id="90e72-161">サンプル構文</span><span class="sxs-lookup"><span data-stu-id="90e72-161">Sample Syntax</span></span>  
 <span data-ttu-id="90e72-162">次に、構成ファイルの使用方法の例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="90e72-162">Following are some examples on how to use the configuration file:</span></span>  
  
-   <span data-ttu-id="90e72-163">コマンド プロンプトで構成ファイルを指定するには</span><span class="sxs-lookup"><span data-stu-id="90e72-163">To specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /ConfigurationFile=MyConfigurationFile.INI  
```  
  
-   <span data-ttu-id="90e72-164">構成ファイルの代わりにコマンド プロンプトでパスワードを指定するには</span><span class="sxs-lookup"><span data-stu-id="90e72-164">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
```  
Setup.exe /SQLSVCPASSWORD="************" /AGTSVCPASSWORD="************" /ASSVCPASSWORD="************" /ISSVCPASSWORD="************" /RSSVCPASSWORD="************" /ConfigurationFile=MyConfigurationFile.INI  
```  
  
## <a name="see-also"></a><span data-ttu-id="90e72-165">参照</span><span class="sxs-lookup"><span data-stu-id="90e72-165">See Also</span></span>  
 <span data-ttu-id="90e72-166">[コマンドプロンプトから SQL Server 2014 をインストールする](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="90e72-166">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="90e72-167">[SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span><span class="sxs-lookup"><span data-stu-id="90e72-167">[SQL Server Failover Cluster Installation](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) </span></span>  
 [<span data-ttu-id="90e72-168">SQL Server フェールオーバー クラスターのアップグレード</span><span class="sxs-lookup"><span data-stu-id="90e72-168">Upgrade a SQL Server Failover Cluster</span></span>](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
