---
title: PowerPivot for SharePoint 2013 のインストール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74d0e1cc78b4004a832a312f9f8ae8deb23904f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713629"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a><span data-ttu-id="4bbca-102">PowerPivot for SharePoint 2013 のインストール</span><span class="sxs-lookup"><span data-stu-id="4bbca-102">PowerPivot for SharePoint 2013 Installation</span></span>
  <span data-ttu-id="4bbca-103">このトピックでは、SharePoint 配置モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーのシングル サーバー インストールの手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-103">The procedures in this topic guide you through a single server installation of a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint deployment mode.</span></span> <span data-ttu-id="4bbca-104">手順には、SQL Server インストール ウィザードの実行と、SharePoint 2013 サーバーの全体管理を使用する構成タスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint 2013 Central Administration.</span></span>  
  
 <span data-ttu-id="4bbca-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 |SharePoint 201</span><span class="sxs-lookup"><span data-stu-id="4bbca-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 201</span></span>  
  
 <span data-ttu-id="4bbca-106">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="4bbca-106">**In this topic:**</span></span>  
  
 [<span data-ttu-id="4bbca-107">背景</span><span class="sxs-lookup"><span data-stu-id="4bbca-107">Background</span></span>](#bkmk_background)  
  
 [<span data-ttu-id="4bbca-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="4bbca-108">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="4bbca-109">手順 1. PowerPivot for SharePoint のインストール</span><span class="sxs-lookup"><span data-stu-id="4bbca-109">Step 1: Install PowerPivot for SharePoint</span></span>](#InstallSQL)  
  
 [<span data-ttu-id="4bbca-110">手順 2. 基本的な Analysis Services SharePoint 統合の構成</span><span class="sxs-lookup"><span data-stu-id="4bbca-110">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="4bbca-111">手順 3. 統合の確認</span><span class="sxs-lookup"><span data-stu-id="4bbca-111">Step 3: Verify the Integration</span></span>](#bkmk_verify)  
  
 [<span data-ttu-id="4bbca-112">Analysis Services のアクセスを許可するための Windows ファイアウォールの構成</span><span class="sxs-lookup"><span data-stu-id="4bbca-112">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](#bkmk_firewall)  
  
 [<span data-ttu-id="4bbca-113">ブックのアップグレードと定期データ更新</span><span class="sxs-lookup"><span data-stu-id="4bbca-113">Upgrade Workbooks and Scheduled Data Refresh</span></span>](#bkmk_upgrade_workbook)  
  
 [<span data-ttu-id="4bbca-114">シングルサーバーインストール以外-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="4bbca-114">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>](#bkmk_multiple_servers)  
  
##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="4bbca-115">背景情報</span><span class="sxs-lookup"><span data-stu-id="4bbca-115">Background</span></span>  
 <span data-ttu-id="4bbca-116">PowerPivot for SharePoint は、SharePoint 2013 ファームでの PowerPivot データ アクセスを提供する中間層のバックエンド サービスです。</span><span class="sxs-lookup"><span data-stu-id="4bbca-116">PowerPivot for SharePoint is a collection of middle-tier and backend services that provide PowerPivot data access in a SharePoint 2013 farm.</span></span>  
  
-   <span data-ttu-id="4bbca-117">**バックエンド サービス:** PowerPivot for Excel を使用して分析データが含まれたブックを作成した場合、サーバー環境でそのデータにアクセスするには PowerPivot for SharePoint が必要です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-117">**Backend services:** If you use PowerPivot for Excel to create workbooks that contain analytical data, you must have PowerPivot for SharePoint to access that data in a server environment.</span></span> <span data-ttu-id="4bbca-118">SQL Server セットアップは、SharePoint Server 2013 がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-118">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="4bbca-119">Analysis Services には、SharePoint との依存関係はありません。</span><span class="sxs-lookup"><span data-stu-id="4bbca-119">Analysis Services does not have any dependencies on SharePoint.</span></span>  
  
     <span data-ttu-id="4bbca-120">**注:** このトピックでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーおよびバックエンド サービスのインストールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-120">**Note:** This topic describes the installation of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server and the backend services.</span></span>  
  
-   <span data-ttu-id="4bbca-121">**中間層:** PowerPivot ギャラリー、定期データ更新、管理ダッシュボード、データ プロバイダーなどの SharePoint の PowerPivot エクスペリエンスを強化します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-121">**Middle-tier:** Enhancements to the PowerPivot experiences in SharePoint including PowerPivot Gallery, Schedule data refresh, Management dashboard, and data providers.</span></span> <span data-ttu-id="4bbca-122">中間層のインストールと構成の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-122">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
    -   [<span data-ttu-id="4bbca-123">SharePoint 2013 &#40;PowerPivot for SharePoint アドインをインストールまたはアンインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="4bbca-123">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
    -   [<span data-ttu-id="4bbca-124">SharePoint 2013&#41;での PowerPivot の構成とソリューションの配置 &#40;</span><span class="sxs-lookup"><span data-stu-id="4bbca-124">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="4bbca-125">前提条件</span><span class="sxs-lookup"><span data-stu-id="4bbca-125">Prerequisites</span></span>  
  
1.  <span data-ttu-id="4bbca-126">SQL Server セットアップを実行するには、ローカル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-126">You must be a local administrator to run SQL Server Setup.</span></span>  
  
2.  <span data-ttu-id="4bbca-127">PowerPivot for SharePoint には SharePoint Server 2013 Enterprise Edition が必要です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-127">SharePoint Server 2013 enterprise edition is required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="4bbca-128">評価版の Enterprise Edition を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-128">You can also use the evaluation enterprise edition.</span></span>  
  
3.  <span data-ttu-id="4bbca-129">コンピューターは、Excel Services と同じ Active Directory フォレストのドメインに参加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-129">The computer must be joined to a domain in the same Active Directory forest as Excel Services.</span></span>  
  
4.  <span data-ttu-id="4bbca-130">PowerPivot インスタンスの名前を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-130">The PowerPivot instance name must be available.</span></span> <span data-ttu-id="4bbca-131">PowerPivot 名前付きインスタンスが既に存在するコンピューターに、SharePoint モードの Analysis Services をインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4bbca-131">You cannot have an existing PowerPivot-named instance on the computer on which you are installing Analysis Services in SharePoint mode.</span></span>  
  
5.  <span data-ttu-id="4bbca-132">[SharePoint モードの Analysis Services Server のハードウェアとソフトウェアの要件 &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-132">Review [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>  
  
6.  <span data-ttu-id="4bbca-133">リリースノートについては[SQL Server 2012 Service Pack 1 のリリースノート](https://go.microsoft.com/fwlink/?LinkID=248389)() を参照して https://go.microsoft.com/fwlink/?LinkID=248389) ください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-133">Review the release notes at [SQL Server 2012 Service Pack 1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
###  <a name="sql-server-edition-requirements"></a><a name="bkmk_sqleditions"></a> <span data-ttu-id="4bbca-134">SQL Server エディションの要件</span><span class="sxs-lookup"><span data-stu-id="4bbca-134">SQL Server Edition Requirements</span></span>  
 <span data-ttu-id="4bbca-135">ビジネス インテリジェンス機能は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のすべてのエディションで利用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="4bbca-135">Business intelligence features are not all available in all editions of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="4bbca-136">詳細については、「 [SQL Server 2012 の各エディションが https://go.microsoft.com/fwlink/?linkid=232473) サポートする機能」 (](https://go.microsoft.com/fwlink/?linkid=232473)および[SQL Server 2014 の各エディションとコンポーネント](../../../sql-server/editions-and-components-of-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-136">For details, see [Features Supported by the Editions of SQL Server 2012 (https://go.microsoft.com/fwlink/?linkid=232473)](https://go.microsoft.com/fwlink/?linkid=232473) and [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="4bbca-137">最新のリリースノートについては、 [SQL Server 2012 SP1 リリースノート](https://go.microsoft.com/fwlink/?LinkID=248389)() を参照して https://go.microsoft.com/fwlink/?LinkID=248389) ください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-137">The current release notes can be found at [SQL Server 2012 SP1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
 <span data-ttu-id="4bbca-138">[Microsoft SQL Server 2012 リリースノート ( https://go.microsoft.com/fwlink/?LinkId=236893) ](https://go.microsoft.com/fwlink/?LinkId=236893).</span><span class="sxs-lookup"><span data-stu-id="4bbca-138">[Microsoft SQL Server 2012 Release Notes (https://go.microsoft.com/fwlink/?LinkId=236893)](https://go.microsoft.com/fwlink/?LinkId=236893).</span></span>  
  
##  <a name="step-1-install-powerpivot-for-sharepoint"></a><a name="InstallSQL"></a><span data-ttu-id="4bbca-139">手順 1: PowerPivot for SharePoint をインストールする</span><span class="sxs-lookup"><span data-stu-id="4bbca-139">Step 1: Install PowerPivot for SharePoint</span></span>  
 <span data-ttu-id="4bbca-140">この手順では、SQL Server セットアップを実行して、SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-140">In this step, you run SQL Server Setup to install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="4bbca-141">後の手順で、このサーバーをブックのデータ モデルで使用するように Excel Services を構成します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-141">In a subsequent step, you configure Excel Services to use this server for workbook data models.</span></span>  
  
1.  <span data-ttu-id="4bbca-142">SQL Server インストール ウィザード (Setup.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-142">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="4bbca-143">左側のナビゲーション ウィンドウで、 **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-143">Click **Installation** in the left navigation.</span></span>  
  
3.  <span data-ttu-id="4bbca-144">**[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-144">Click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
4.  <span data-ttu-id="4bbca-145">**[プロダクト キー]** ページが表示されたら、Evaluation Edition を指定するか、Enterprise Edition のライセンス コピーのプロダクト キーを入力します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-145">If you see the **Product Key** page, specify the evaluation edition or enter a product key for a licensed copy of the enterprise edition.</span></span> <span data-ttu-id="4bbca-146">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-146">Click **Next**.</span></span> <span data-ttu-id="4bbca-147">エディションの詳細については、「 [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-147">For more information on editions, see [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
5.  <span data-ttu-id="4bbca-148">マイクロソフト ソフトウェア ライセンス条項を確認して同意し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-148">Review and accept the Microsoft Software License Terms of agreement, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="4bbca-149">**[グローバル ルール]** ページが表示されたら、セットアップ ウィザードに表示されるすべてのルールの情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-149">If you see the **Global Rules** page, review any rules information the setup wizard displays.</span></span>  
  
7.  <span data-ttu-id="4bbca-150">**[Microsoft Update]** ページで、Microsoft Update を使用して更新プログラムを確認することをお勧めします。確認したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-150">On the **Microsoft Update** page, it is recommended you use Microsoft Update to check for updates, then click **Next**.</span></span>  
  
8.  <span data-ttu-id="4bbca-151">**[セットアップ ファイルのインストール]** ページが数分間実行されます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-151">The **Install Setup Files** page runs for several minutes.</span></span> <span data-ttu-id="4bbca-152">ルールの警告または失敗したルールを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-152">Review any rule warnings or failed rules, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="4bbca-153">別の **[セットアップ サポート ルール]** が表示されたら、警告を確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-153">If you see another **Setup Support Rules**, review any warnings and click **Next**.</span></span>  
  
     <span data-ttu-id="4bbca-154">**注:** Windows ファイアウォールが有効になっているため、ポートを開いてリモート アクセスを有効にするよう求める警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-154">**Note:** Because Windows Firewall is enabled, you see a warning to open ports to enable remote access.</span></span>  
  
10. <span data-ttu-id="4bbca-155">**[セットアップ ロール]** ページで、 **[SQL Server PowerPivot for SharePoint]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-155">On the **Setup Role** page, select **SQL Server PowerPivot for SharePoint**.</span></span> <span data-ttu-id="4bbca-156">このオプションを選択すると、SharePoint モードの Analysis Services がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-156">This option installs Analysis Services in SharePoint mode.</span></span>  
  
     <span data-ttu-id="4bbca-157">オプションで、データベース エンジンのインスタンスをインストールに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-157">Optionally, you can add an instance of the Database Engine to your installation.</span></span> <span data-ttu-id="4bbca-158">新しいファームを設定するときにデータベースエンジンを追加し、ファームの構成データベースとコンテンツデータベースを実行するためにデータベースサーバーが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-158">You might add the Database Engine when setting up a new farm and need a database server to run the farm's configuration and content databases.</span></span> <span data-ttu-id="4bbca-159">このオプションでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]もインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-159">This option also installs [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="4bbca-160">データベース エンジンを追加した場合は、 **PowerPivot** 名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-160">If you add the Database Engine, it is installed as a **PowerPivot** named instance.</span></span> <span data-ttu-id="4bbca-161">このインスタンスへの接続を指定するには、データベース名を [`servername`]\PowerPivot の形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-161">Whenever you specify a connection to this instance, enter the database name in this format: [`servername`]\PowerPivot.</span></span>  
  
     <span data-ttu-id="4bbca-162">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-162">Click **Next**.</span></span>  
  
     <span data-ttu-id="4bbca-163">![セットアップ ロール](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "セットアップ ロール")</span><span class="sxs-lookup"><span data-stu-id="4bbca-163">![Setup Role](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Setup Role")</span></span>  
  
11. <span data-ttu-id="4bbca-164">[機能の選択] に、機能の一覧が表示されます。この一覧は情報提供を目的としており、読み取り専用になっています。</span><span class="sxs-lookup"><span data-stu-id="4bbca-164">In Feature Selection, a read-only list of the features is displayed for informational purposes.</span></span> <span data-ttu-id="4bbca-165">このロールに対してあらかじめ選択されている項目を、追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="4bbca-165">You cannot add or remove items the preselected items for this role.</span></span> <span data-ttu-id="4bbca-166">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-166">Click **Next**.</span></span>  
  
12. <span data-ttu-id="4bbca-167">**[インスタンスの構成]** ページに、"PowerPivot" というインスタンス名が表示されます。この名前は情報として示されており、読み取り専用になっています。</span><span class="sxs-lookup"><span data-stu-id="4bbca-167">On the **Instance Configuration** page, a read-only instance name of 'PowerPivot' is displayed for informational purposes.</span></span> <span data-ttu-id="4bbca-168">このインスタンス名は必須であり、変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="4bbca-168">This instance name is required and it cannot be modified.</span></span> <span data-ttu-id="4bbca-169">ただし、ディレクトリ名とレジストリ キーをわかりやすく示した独自のインスタンス ID を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-169">However, you can enter a unique Instance ID to specify a descriptive directory name and registry keys.</span></span> <span data-ttu-id="4bbca-170">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-170">Click **Next**.</span></span>  
  
13. <span data-ttu-id="4bbca-171">**[サーバー構成]** のページで、すべてのサービスの **[スタートアップの種類]** を [自動] に設定します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-171">On the **Server Configuration** page, configure all of the services for Automatic **Startup Type**.</span></span> <span data-ttu-id="4bbca-172">**SQL Server Analysis Services**に必要なドメイン アカウントとパスワードを指定します。次の図の **(1)** です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-172">Specify the desired domain account and password for **SQL Server Analysis Services**, **(1)** in the following diagram.</span></span>  
  
    -   <span data-ttu-id="4bbca-173">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]では、 **ドメイン ユーザー** アカウントまたは **NetworkService** アカウントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-173">For [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can use a **domain user** account or **NetworkService** account.</span></span> <span data-ttu-id="4bbca-174">LocalSystem アカウントまたは LocalService アカウントは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-174">Do not use LocalSystem or LocalService accounts.</span></span>  
  
    -   <span data-ttu-id="4bbca-175">SQL Server データベース エンジンと SQL Server エージェントを追加した場合は、サービスがドメイン ユーザー アカウントまたは既定の仮想アカウントで実行されるように構成できます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-175">If you added the SQL Server Database Engine and SQL Server Agent, you can configure the services to run under domain user accounts or under the default virtual account.</span></span>  
  
    -   <span data-ttu-id="4bbca-176">サービス アカウントには自分のドメイン ユーザー アカウントを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-176">Never provision service accounts with your own domain user account.</span></span> <span data-ttu-id="4bbca-177">このようなアカウントを使用すると、ネットワークのリソースに対して持っている権限と同じ権限をサーバーに付与することになります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-177">Doing so grants the server the same permissions that you have to the resources in your network.</span></span> <span data-ttu-id="4bbca-178">悪意のあるユーザーがサーバーに侵入した場合、そのユーザーは管理者のドメイン資格情報を使用してログオンします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-178">If a malicious user compromises the server, that user is logged in under your domain credentials.</span></span> <span data-ttu-id="4bbca-179">そのユーザーは、管理者と同じデータやアプリケーションをダウンロードしたり使用したりする権限を持ちます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-179">The user has the permissions to download or use the same data and applications that you do.</span></span>  
  
     <span data-ttu-id="4bbca-180">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-180">Click **Next**.</span></span>  
  
     <span data-ttu-id="4bbca-181">![SSAS Server 構成](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server 構成")</span><span class="sxs-lookup"><span data-stu-id="4bbca-181">![SSAS Server Configuration](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server Configuration")</span></span>  
  
14. <span data-ttu-id="4bbca-182">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]をインストールする場合は、 **[データベース エンジンの構成]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-182">If you are installing the [!INCLUDE[ssDE](../../../includes/ssde-md.md)], the **Database Engine Configuration** page appears.</span></span> <span data-ttu-id="4bbca-183">[ [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の構成] で、 **[現在のユーザーの追加]** をクリックして、データベース エンジン インスタンスに対する管理者権限をユーザー アカウントに付与します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-183">In [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Configuration, click **Add Current User** to grant your user account administrator permissions on the Database Engine instance.</span></span>  
  
     <span data-ttu-id="4bbca-184">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-184">Click **Next**.</span></span>  
  
15. <span data-ttu-id="4bbca-185">**[Analysis Services の構成]** ページで、 **[現在のユーザーの追加]** をクリックして、ユーザー アカウントに管理権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-185">On the **Analysis Services Configuration** page, click **Add Current User** to grant your user account administrative permissions.</span></span> <span data-ttu-id="4bbca-186">セットアップの完了後にサーバーを構成するには、管理権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-186">You will need administrative permission to configure the server after Setup is finished.</span></span>  
  
    -   <span data-ttu-id="4bbca-187">同じページで、同じく管理権限が必要なユーザーの Windows ユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-187">In the same page, add the Windows user account of any person who also requires administrative permissions.</span></span> <span data-ttu-id="4bbca-188">たとえば、データベース接続の問題のトラブルシューティングを行うために、 [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] インスタンスに接続するユーザーには、システム管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-188">For example, any user who wants to connect to the [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] instance in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to troubleshoot database connection problems must have system administrator permissions.</span></span> <span data-ttu-id="4bbca-189">サーバーのトラブルシューティングや管理を担当する可能性があるユーザーのユーザー アカウントをここで追加しておきます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-189">Add the user account of any person who might need to troubleshoot or administer the server now.</span></span>  
  
    -   > [!NOTE]  
        >  <span data-ttu-id="4bbca-190">Analysis Services サーバー インスタンスにアクセスする必要があるすべてのサービス アプリケーションに、Analysis Services 管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-190">All service applications that require access to the Analysis Services server instance need to have Analysis Services Administrative permissions.</span></span> <span data-ttu-id="4bbca-191">たとえば、Excel Services、Power View、Performance Point Services のサービス アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-191">For example, add the service accounts for Excel Services, Power View, and Performance Point Services.</span></span> <span data-ttu-id="4bbca-192">また、サーバーの全体管理をホストする Web アプリケーションの ID として使用される SharePoint ファーム アカウントも追加します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-192">Also, add the SharePoint farm account, which is used as the identity of the web application that hosts Central Administration.</span></span>  
  
     <span data-ttu-id="4bbca-193">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-193">Click **Next**.</span></span>  
  
16. <span data-ttu-id="4bbca-194">**[エラー レポート]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-194">On the **Error Reporting** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="4bbca-195">[**インストールの準備完了**] ページで、[**インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-195">On the **Ready to Install** page, click **Install**.</span></span>  
  
18. <span data-ttu-id="4bbca-196">**[コンピューターの再起動が必要です]** ダイアログ ボックスが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-196">If you see the dialog **Computer Restart Required**, click **OK**.</span></span>  
  
19. <span data-ttu-id="4bbca-197">インストールが完了したら、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-197">When the installation is complete, click **Close**.</span></span>  
  
20. <span data-ttu-id="4bbca-198">コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-198">Restart the computer.</span></span>  
  
21. <span data-ttu-id="4bbca-199">環境内にファイアウォールがある場合は、SQL Server オンライン ブックの「 [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md)」を確認します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-199">If you have a firewall in your environment, review the SQL Server Books Online topic, [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
### <a name="verify-the-sql-server-installation"></a><span data-ttu-id="4bbca-200">SQL Server のインストールの確認</span><span class="sxs-lookup"><span data-stu-id="4bbca-200">Verify the SQL Server Installation</span></span>  
 <span data-ttu-id="4bbca-201">Analysis Services サービスが実行されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-201">Verify that the Analysis Services Service is running.</span></span>  
  
1.  <span data-ttu-id="4bbca-202">Windows の **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をクリックして、 **[Microsoft SQL Server 2012]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-202">In Microsoft Windows click **Start**, click **All Programs**, and click the **Microsoft SQL Server 2012** group.</span></span>  
  
2.  <span data-ttu-id="4bbca-203">**[SQL Server Management Studio]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-203">Click **SQL Server Management Studio**.</span></span>  
  
3.  <span data-ttu-id="4bbca-204">Analysis Services インスタンス (たとえば、 **[サーバー名]\POWERPIVOT**) に接続します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-204">Connect to the Analysis Services instance, for example **[your server name]\POWERPIVOT**.</span></span> <span data-ttu-id="4bbca-205">インスタンスに接続できたら、サービスが実行されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-205">If you can connect to the instance, you have verified the Service is running.</span></span>  
  
##  <a name="step-2-configure-basic-analysis-services-sharepoint-integration"></a><a name="bkmk_config"></a><span data-ttu-id="4bbca-206">手順 2: 基本的な Analysis Services SharePoint 統合を構成する</span><span class="sxs-lookup"><span data-stu-id="4bbca-206">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>  
 <span data-ttu-id="4bbca-207">SharePoint ドキュメント ライブラリ内で Excel の高度なデータ モデルを操作できるようにするには、次の手順を実行して構成を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-207">The following steps describe configuration changes needed so you can interact with Excel advanced data models inside a SharePoint document library.</span></span> <span data-ttu-id="4bbca-208">これらの手順は、SharePoint Server 2013 と SQL Server Analysis Services をインストールしてから実行します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-208">Complete these steps after you install SharePoint Server 2013 and SQL Server Analysis Services.</span></span>  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a><span data-ttu-id="4bbca-209">Excel Services への Analysis Services に対するサーバー管理権限の付与</span><span class="sxs-lookup"><span data-stu-id="4bbca-209">Grant Excel Services Server Administration Rights on Analysis Services</span></span>  
 <span data-ttu-id="4bbca-210">Analysis Services のインストール時に、Analysis Services 管理者として Excel Services アプリケーションのサービス アカウントを追加した場合は、このセクションの手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4bbca-210">You do not need to complete this section if during the Analysis Services installation; you added the Excel Services Application service account as an Analysis Services administrator.</span></span>  
  
1.  <span data-ttu-id="4bbca-211">Analysis Services サーバーで、SQL Server Management Studio を起動し、Analysis Services インスタンス (たとえば、`[MyServer]\POWERPIVOT`) に接続します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-211">On the Analysis Services server, start SQL Server Management Studio and connect to the Analysis Services instance, for example `[MyServer]\POWERPIVOT`.</span></span>  
  
2.  <span data-ttu-id="4bbca-212">オブジェクト エクスプローラーで、インスタンス名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-212">In Object Explorer, Right-click the instance name and click **Properties**.</span></span>  
  
     <span data-ttu-id="4bbca-213">![SSAS サーバーのプロパティを表示](../../../sql-server/install/media/as-ssms-proeprties.gif "SSAS サーバーのプロパティを表示")</span><span class="sxs-lookup"><span data-stu-id="4bbca-213">![View Properties of an SSAS server](../../../sql-server/install/media/as-ssms-proeprties.gif "View Properties of an SSAS server")</span></span>  
  
3.  <span data-ttu-id="4bbca-214">左ペインで、 **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-214">In the left pane, click **Security**.</span></span> <span data-ttu-id="4bbca-215">手順 1. で Excel Services アプリケーション用に構成したドメイン ログインを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-215">Add the domain login you configured for the Excel Services Application in step 1.</span></span>  
  
     <span data-ttu-id="4bbca-216">![SSAS サーバーのセキュリティ設定](../../../sql-server/install/media/as-ssms-security.gif "SSAS サーバーのセキュリティ設定")</span><span class="sxs-lookup"><span data-stu-id="4bbca-216">![Security Settings of an SSAS Server](../../../sql-server/install/media/as-ssms-security.gif "Security Settings of an SSAS Server")</span></span>  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a><span data-ttu-id="4bbca-217">Analysis Services 統合のための Excel Services の構成</span><span class="sxs-lookup"><span data-stu-id="4bbca-217">Configure Excel Services for Analysis Services integration</span></span>  
  
1.  <span data-ttu-id="4bbca-218">SharePoint サーバーの全体管理で、[アプリケーション管理] グループの [**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-218">In SharePoint Central Administration, in the Application Management group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="4bbca-219">サービス アプリケーションの名前をクリックします。既定の名前は **"Excel Services アプリケーション"** です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-219">Click the name of your service application, the default is **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="4bbca-220">**[Excel Services アプリケーションの管理]** ページで、 **[データ モデルの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-220">On the **Manage Excel Services Application page**, click **Data Model Settings**.</span></span>  
  
4.  <span data-ttu-id="4bbca-221">**[サーバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-221">Click **Add Server**.</span></span>  
  
5.  <span data-ttu-id="4bbca-222">**[サーバー名]** に、Analysis Services サーバー名と PowerPivot インスタンス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-222">In **Server Name**, type the Analysis Services server name and the PowerPivot instance name.</span></span> <span data-ttu-id="4bbca-223">たとえば、「 `MyServer\POWERPIVOT` 」のように指定します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-223">For example `MyServer\POWERPIVOT`.</span></span> <span data-ttu-id="4bbca-224">PowerPivot インスタンス名は必須です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-224">The PowerPivot instance name is required.</span></span>  
  
     <span data-ttu-id="4bbca-225">説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-225">Type a description.</span></span>  
  
6.  <span data-ttu-id="4bbca-226">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-226">Click **Ok**.</span></span>  
  
7.  <span data-ttu-id="4bbca-227">変更は数分で有効になりますが、 **Excel Calculation Services** サービスを **停止** および **開始**することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-227">The changes will take effect in a few minutes or you can **Stop** and **Start** the service **Excel Calculation Services**.</span></span> <span data-ttu-id="4bbca-228">ターゲット</span><span class="sxs-lookup"><span data-stu-id="4bbca-228">To</span></span>  
  
     <span data-ttu-id="4bbca-229">別の方法として、管理者特権でコマンド プロンプトを開き、「 `iisreset /noforce`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-229">Another option is to open a command prompt with administrative privileges, and type `iisreset /noforce`.</span></span>  
  
     <span data-ttu-id="4bbca-230">ULS ログのエントリを確認することで、サーバーが Excel Services によって認識されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-230">You can verify the server is recognized by Excel Services by reviewing entries in the ULS log.</span></span> <span data-ttu-id="4bbca-231">実際のエントリの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-231">You will see entries similar to the following:</span></span>  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="step-3-verify-the-integration"></a><a name="bkmk_verify"></a><span data-ttu-id="4bbca-232">手順 3: 統合を確認する</span><span class="sxs-lookup"><span data-stu-id="4bbca-232">Step 3: Verify the Integration</span></span>  
 <span data-ttu-id="4bbca-233">ここでは、Analysis Services 統合を確認するために、新しいブックを作成し、アップロードする手順を示します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-233">The following steps walk you through creating and uploading a new workbook to verify the Analysis Services integration.</span></span> <span data-ttu-id="4bbca-234">この手順を実行するには、SQL Server データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-234">You will need a SQL Server database to complete the steps.</span></span>  
  
1.  <span data-ttu-id="4bbca-235">**注:** スライサーやフィルターが含まれた高度なブックが既にある場合は、そのブックを SharePoint ドキュメント ライブラリにアップロードし、ドキュメント ライブラリ ビューからスライサーとフィルターを操作できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-235">**Note:** If you already have an advanced workbook with slicers or filters, you can upload it to your SharePoint document library and verify you are able to interact with the slicers and filters from the document library view.</span></span>  
  
2.  <span data-ttu-id="4bbca-236">Excel で新しいブックを開きます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-236">Start a new workbook in Excel.</span></span>  
  
3.  <span data-ttu-id="4bbca-237">[データ] タブの **[外部データの取り込み]** で、 **[その他のデータ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-237">On the Data tab, click **From Other Sources** on the ribbon in the **Get External Data**.</span></span>  
  
4.  <span data-ttu-id="4bbca-238">**[SQL Server]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-238">Select **From SQL Server**.</span></span>  
  
5.  <span data-ttu-id="4bbca-239">**データ接続ウィザード**で、使用するデータベースがある SQL Server インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-239">In the **Data Connection Wizard**, enter the name of the SQL Server instance that has the database you want to use.</span></span>  
  
6.  <span data-ttu-id="4bbca-240">または、ログオン資格情報を入力し、 **[Windows 認証を使用する]** が選択されていることを確認して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-240">or Log on credentials, verify that **Use Windows Authentication** is selected, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="4bbca-241">使用するデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-241">Select the database you want to use.</span></span>  
  
8.  <span data-ttu-id="4bbca-242">**[指定したテーブルに接続]** チェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-242">Verify that the **Connect to specific table** checkbox is selected.</span></span>  
  
9. <span data-ttu-id="4bbca-243">**[複数のテーブルの選択を有効にし、テーブルを Excel データ モデルに追加する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-243">Click the **Enable selection of multiple tables and add tables to the Excel Data Model** checkbox.</span></span>  
  
10. <span data-ttu-id="4bbca-244">インポートするテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-244">Select the tables you want to import.</span></span>  
  
11. <span data-ttu-id="4bbca-245">**[選択したテーブル間のリレーションシップをインポートする]** チェック ボックスをオンにし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-245">Click the checkbox **Import relationships between selected tables**, and then click **Next**.</span></span> <span data-ttu-id="4bbca-246">リレーショナル データベースから複数のテーブルをインポートすると、既に関連付けられているテーブルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-246">Importing multiple tables from a relational database lets you work with tables that are already related.</span></span> <span data-ttu-id="4bbca-247">リレーションシップを手動で作成する必要がないため、手間を省くことができます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-247">You save steps because you don't have to build the relationships manually.</span></span>  
  
12. <span data-ttu-id="4bbca-248">ウィザードの **[データ接続ファイルを保存して終了]** ページで、接続の名前を入力し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-248">In the **Save Data Connection File and Finish** page of the wizard,, type a dame for your connection and click **Finish**.</span></span>  
  
13. <span data-ttu-id="4bbca-249">**[データのインポート]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-249">The **Import Data** dialog box will appear.</span></span> <span data-ttu-id="4bbca-250">**[ピボットテーブル レポート]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-250">Choose **PivotTable Report**, and then click **Ok**.</span></span>  
  
14. <span data-ttu-id="4bbca-251">ブックにピボットテーブル フィールド リストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-251">A PivotTable Field List appears in the workbook.</span></span>   
    <span data-ttu-id="4bbca-252">フィールド リストで、 **[すべて]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-252">On the field list, click the **All** tab</span></span>  
  
15. <span data-ttu-id="4bbca-253">フィールド リストの [行]、[列]、[値] の各領域にフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-253">Add fields to the Row, Columns, and Value areas in the field list.</span></span>  
  
16. <span data-ttu-id="4bbca-254">ピボットテーブルにスライサーまたはフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-254">Add a slicer or a filter to the PivotTable.</span></span> <span data-ttu-id="4bbca-255">**この手順は省略しないで**ください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-255">**Do not skip this step**.</span></span> <span data-ttu-id="4bbca-256">スライサーまたはフィルターは、Analysis Services のインストールの確認に役立つ要素です。</span><span class="sxs-lookup"><span data-stu-id="4bbca-256">A slicer or filter is the element that will help you verify your Analysis Services installation.</span></span>  
  
17. <span data-ttu-id="4bbca-257">Excel Services が構成されている SharePoint Server 2013 のドキュメント ライブラリにブックを保存します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-257">Save the workbook to a document library on a SharePoint Server 2013 that has Excel Services configured.</span></span> <span data-ttu-id="4bbca-258">また、ブックをファイル共有に保存し、SharePoint Server 2013 ドキュメント ライブラリにアップロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-258">You can also save the workbook to a file share and then upload it to the SharePoint Server 2013 document library.</span></span>  
  
18. <span data-ttu-id="4bbca-259">ブックの名前をクリックして SharePoint で表示し、スライサーをクリックするか、以前に追加したフィルターを変更します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-259">Click the name of your workbook to view it in SharePoint and click the slicer or change the filter that you previously added.</span></span> <span data-ttu-id="4bbca-260">データ更新が行われたら、Analysis Services がインストールされ、Excel Services で利用できることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-260">If a data update occurs, you know that Analysis Services is installed and available to Excel Services.</span></span> <span data-ttu-id="4bbca-261">ブックを Excel で開いた場合は、Analysis Services サーバーではなく、キャッシュ コピーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-261">If you open the workbook in Excel you will be using a cached copy and not using the Analysis Services server.</span></span>  
  
##  <a name="configure-the-windows-firewall-to-allow-analysis-services-access"></a><a name="bkmk_firewall"></a><span data-ttu-id="4bbca-262">Analysis Services アクセスを許可するように Windows ファイアウォールを構成する</span><span class="sxs-lookup"><span data-stu-id="4bbca-262">Configure the Windows Firewall to Allow Analysis Services Access</span></span>  
 <span data-ttu-id="4bbca-263">「 [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) 」では、Analysis Services または PowerPivot for SharePoint へのアクセスを許可するためにファイアウォールのポートのブロックを解除する必要があるかどうかを判断するための情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-263">Use the information in the topic [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) to determine whether you need to unblock ports in a firewall to allow access to Analysis Services or PowerPivot for SharePoint.</span></span> <span data-ttu-id="4bbca-264">このトピックに示された手順に従って、ポートとファイアウォールを構成できます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-264">You can follow the steps provided in the topic to configure both port and firewall settings.</span></span> <span data-ttu-id="4bbca-265">実際に Analysis Services サーバーへのアクセスを許可するためには、これらの手順を組み合わせて実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-265">In practice, you should perform these steps together to allow access to your Analysis Services server.</span></span>  
  
##  <a name="upgrade-workbooks-and-scheduled-data-refresh"></a><a name="bkmk_upgrade_workbook"></a><span data-ttu-id="4bbca-266">ブックのアップグレードと定期データ更新</span><span class="sxs-lookup"><span data-stu-id="4bbca-266">Upgrade Workbooks and Scheduled Data Refresh</span></span>  
 <span data-ttu-id="4bbca-267">PowerPivot の以前のバージョンで作成したブックのアップグレードに必要な手順は、そのブックを作成した PowerPivot のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="4bbca-267">The steps required to upgrade workbooks created in previous versions of PowerPivot depend on what version of PowerPivot created the workbook.</span></span> <span data-ttu-id="4bbca-268">詳細については、「 [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-268">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>  
  
##  <a name="beyond-the-single-server-installation--powerpivot-for-microsoft-sharepoint"></a><a name="bkmk_multiple_servers"></a><span data-ttu-id="4bbca-269">シングルサーバーインストール以外-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="4bbca-269">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>  
 <span data-ttu-id="4bbca-270">**Web フロントエンド (WFE)** または **中間層:**[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーを大規模な SharePoint ファームで SharePoint モードで使用したり、ファームに PowerPivot の追加機能をインストールしたりするには、各 SharePoint サーバーで **spPowerPivot.msi** インストーラー パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-270">**Web front-end (WFE)** or **Middle-tier:**: To use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode in a larger SharePoint farm and to install additional PowerPivot features into the farm, run the installer package **spPowerPivot.msi** on each of the SharePoint servers.</span></span> <span data-ttu-id="4bbca-271">spPowerPivot.msi では、必要なデータ プロバイダーと PowerPivot for SharePoint 2013 の構成ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4bbca-271">The spPowerPivot.msi installs required data providers and the PowerPivot for SharePoint 2013 Configuration tool.</span></span>  
  
 <span data-ttu-id="4bbca-272">中間層のインストールと構成の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-272">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
-   [<span data-ttu-id="4bbca-273">SharePoint 2013 &#40;PowerPivot for SharePoint アドインをインストールまたはアンインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="4bbca-273">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
-   <span data-ttu-id="4bbca-274">.msi をダウンロードするには、「 [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bbca-274">To download the .msi, see [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)</span></span>  
  
-   [<span data-ttu-id="4bbca-275">SharePoint 2013&#41;での PowerPivot の構成とソリューションの配置 &#40;</span><span class="sxs-lookup"><span data-stu-id="4bbca-275">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
 <span data-ttu-id="4bbca-276">**冗長性とサーバー負荷:** 2 台目またはそれ以上の [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーを SharePoint モードでインストールすると、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバー機能の冗長性が実現します。</span><span class="sxs-lookup"><span data-stu-id="4bbca-276">**Redundancy and server load:** Installing a second, or more [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] servers in SharePoint mode will provide redundancy of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server functionality.</span></span> <span data-ttu-id="4bbca-277">サーバーを追加すると、サーバー間の負荷分散も行われます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-277">Additional servers will also spread the load across servers.</span></span> <span data-ttu-id="4bbca-278">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="4bbca-278">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="4bbca-279">[Excel Services でデータモデルを処理するための Analysis Services の構成](https://technet.microsoft.com/library/jj614437\(v=office.15\)) https://technet.microsoft.com/library/jj614437(v=office.15)) ()</span><span class="sxs-lookup"><span data-stu-id="4bbca-279">[Configure Analysis Services for processing data models in Excel Services](https://technet.microsoft.com/library/jj614437\(v=office.15\)) (https://technet.microsoft.com/library/jj614437(v=office.15)).</span></span>  
  
-   <span data-ttu-id="4bbca-280">[Excel Services のデータモデルの設定を管理する (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\)) ( https://technet.microsoft.com/library/jj219780(v=office.15)) 。</span><span class="sxs-lookup"><span data-stu-id="4bbca-280">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\)) (https://technet.microsoft.com/library/jj219780(v=office.15)).</span></span>  
  
 <span data-ttu-id="4bbca-281">![SharePoint の設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")[では Microsoft SQL Server Connect () を使用してフィードバックと連絡先情報を送信し](https://connect.microsoft.com/SQLServer/Feedback) https://connect.microsoft.com/SQLServer/Feedback) ます。</span><span class="sxs-lookup"><span data-stu-id="4bbca-281">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") [Submit feedback and contact information through Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbca-282">参照</span><span class="sxs-lookup"><span data-stu-id="4bbca-282">See Also</span></span>  
 <span data-ttu-id="4bbca-283">[PowerPivot から SharePoint への移行2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="4bbca-283">[Migrate PowerPivot to SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span></span>  
 <span data-ttu-id="4bbca-284">[SharePoint 2013 &#40;PowerPivot for SharePoint アドインをインストールまたはアンインストール&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="4bbca-284">[Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span></span>  
 [<span data-ttu-id="4bbca-285">SharePoint 2013&#41;&#40;のブックのアップグレードと定期データ更新</span><span class="sxs-lookup"><span data-stu-id="4bbca-285">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)  
  
  
