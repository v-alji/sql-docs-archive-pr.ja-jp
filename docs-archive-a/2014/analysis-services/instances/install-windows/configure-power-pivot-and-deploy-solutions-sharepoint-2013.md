---
title: PowerPivot の構成とソリューションの配置 (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7eaea7f9c490fd320d6dbd0777519eeca218b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713641"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a><span data-ttu-id="8254b-102">PowerPivot の構成とソリューションの配置 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="8254b-102">Configure PowerPivot and Deploy Solutions (SharePoint 2013)</span></span>
  <span data-ttu-id="8254b-103">このトピックでは、PowerPivot ギャラリー、定期データ更新、管理ダッシュボード、データ プロバイダーなどの [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] の PowerPivot 機能への中間層機能強化の展開および構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="8254b-103">This topics describes the deployment and configuration of middle-tier enhancements to the PowerPivot features in [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] including PowerPivot Gallery, Schedule data refresh, Management Dashboard, and data providers.</span></span> <span data-ttu-id="8254b-104">**PowerPivot for SharePoint 2013 の構成** ツールを実行して、以下を完了します。</span><span class="sxs-lookup"><span data-stu-id="8254b-104">Run **PowerPivot for SharePoint 2013 Configuration** tool to complete the following:</span></span>  
  
-   <span data-ttu-id="8254b-105">SharePoint ソリューション ファイルを配置する。</span><span class="sxs-lookup"><span data-stu-id="8254b-105">Deploy SharePoint solution files.</span></span>  
  
-   <span data-ttu-id="8254b-106">PowerPivot サービス アプリケーションを作成する。</span><span class="sxs-lookup"><span data-stu-id="8254b-106">Create a PowerPivot service application.</span></span>  
  
-   <span data-ttu-id="8254b-107">Excel Services アプリケーションが SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーを使用するように構成する。</span><span class="sxs-lookup"><span data-stu-id="8254b-107">Configure an Excel Services Application to use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="8254b-108">バックエンドサービスと、SharePoint モードでのサーバーのインストールの詳細につい [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ては、「 [PowerPivot for SharePoint 2013 のインストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8254b-108">For information on backend services and installing a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
 <span data-ttu-id="8254b-109">PowerPivot for SharePoint 2013 構成ツールのインストールの詳細については、「 [SharePoint 2013 &#40;PowerPivot for SharePoint アドインをインストールまたはアンインストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)する」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="8254b-109">For information on installing the PowerPivot for SharePoint 2013 Configuration tool, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span></span>  
  
 <span data-ttu-id="8254b-110">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="8254b-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="8254b-111">PowerPivot for SharePoint 2013 の構成の実行</span><span class="sxs-lookup"><span data-stu-id="8254b-111">Run PowerPivot for SharePoint 2013 configuration</span></span>](#bkmk_run_configuration_tool)  
  
 [<span data-ttu-id="8254b-112">PowerPivot の構成の確認</span><span class="sxs-lookup"><span data-stu-id="8254b-112">Verify PowerPivot Configuration</span></span>](#bkmk_verify_powerpivot)  
  
 [<span data-ttu-id="8254b-113">問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8254b-113">Troubleshoot Issues</span></span>](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a><span data-ttu-id="8254b-114">PowerPivot for SharePoint 2013 構成の実行</span><span class="sxs-lookup"><span data-stu-id="8254b-114">Run PowerPivot for SharePoint 2013 configuration</span></span>  
 <span data-ttu-id="8254b-115">**注:**[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] セットアップ ウィザードでは、 [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)]の 2 種類の構成ツールがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8254b-115">**Note:** The [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] setup wizard installs two different configuration tools for [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)].</span></span> <span data-ttu-id="8254b-116">これらのツールはそれぞれ異なるバージョンの SharePoint をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8254b-116">They each support a different version of SharePoint.</span></span>  
  
|<span data-ttu-id="8254b-117">名前</span><span class="sxs-lookup"><span data-stu-id="8254b-117">Name</span></span>|<span data-ttu-id="8254b-118">説明</span><span class="sxs-lookup"><span data-stu-id="8254b-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="8254b-119">PowerPivot for SharePoint 2013 の構成</span><span class="sxs-lookup"><span data-stu-id="8254b-119">PowerPivot for SharePoint 2013 Configuration</span></span>|<span data-ttu-id="8254b-120">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8254b-120">SharePoint 2013</span></span>|  
|<span data-ttu-id="8254b-121">PowerPivot 構成ツール</span><span class="sxs-lookup"><span data-stu-id="8254b-121">PowerPivot Configuration Tool</span></span>|<span data-ttu-id="8254b-122">SharePoint 2010 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="8254b-122">SharePoint 2010 with SharePoint 2010 Service Pack 1 (SP1)</span></span>|  
  
 <span data-ttu-id="8254b-123">**注:** 次の手順を実行するには、ファーム管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8254b-123">**Note:** To complete the following steps, you must be a farm administrator.</span></span> <span data-ttu-id="8254b-124">次のようなエラー メッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8254b-124">If you see an error message similar to the following:</span></span>  
  
-   <span data-ttu-id="8254b-125">"ユーザーはファームの管理者ではありません。</span><span class="sxs-lookup"><span data-stu-id="8254b-125">"The user is not a farm administrator.</span></span> <span data-ttu-id="8254b-126">検証エラーを修正して、再試行してください。"</span><span class="sxs-lookup"><span data-stu-id="8254b-126">Please address the validation failures and try again."</span></span>  
  
 <span data-ttu-id="8254b-127">SharePoint のインストール時に使用したアカウントでログインするか、SharePoint サーバーの全体管理サイトのプライマリ管理者としてセットアップ アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="8254b-127">Either login as the account that installed SharePoint or configure the setup account as the primary administrator of the SharePoint Central Administration Site.</span></span>  
  
1.  <span data-ttu-id="8254b-128">**[スタート]** メニューの **[すべてのプログラム]** をクリックし、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]] をクリックします。次に、 **[構成ツール]** をクリックし、 **[PowerPivot For SharePoint 2013 の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-128">On the **Start** menu, click **All Programs**, and then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click **PowerPivot For SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="8254b-129">ツールは、PowerPivot for SharePoint がローカル サーバーにインストールされている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="8254b-129">Toold is listed only when PowerPivot for SharePoint is installed on the local server.</span></span>  
  
2.  <span data-ttu-id="8254b-130">**[PowerPivot for SharePoint の構成または修復]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-130">Click **Configure or Repair PowerPivot for SharePoint** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="8254b-131">このツールでは、PowerPivot の現在の状態と構成を完了するために必要な手順を確認するための検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="8254b-131">The tool runs validation to verify the current state of PowerPivot and what steps are required to complete configuration.</span></span> <span data-ttu-id="8254b-132">ウィンドウを最大化します。</span><span class="sxs-lookup"><span data-stu-id="8254b-132">Expand the window to full size.</span></span> <span data-ttu-id="8254b-133">ウィンドウの下部に **[検証]**、 **[実行]**、および **[終了]** の各コマンドを含むボタン バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8254b-133">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="8254b-134">**[パラメーター]** タブで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8254b-134">On the **Parameters** tab:</span></span>  
  
    1.  <span data-ttu-id="8254b-135">**[既定のアカウント ユーザー名]:** 既定のアカウントのドメイン ユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="8254b-135">**Default Account UserName**: Enter a domain user account for the default account.</span></span> <span data-ttu-id="8254b-136">このアカウントは、PowerPivot サービス アプリケーション プールなどのサービスを準備する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="8254b-136">This account will be used to provision services, including the PowerPivot service application pool.</span></span> <span data-ttu-id="8254b-137">Network Service や Local System などのビルトイン アカウントは指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="8254b-137">Do not specify a built-in account such as Network Service or Local System.</span></span> <span data-ttu-id="8254b-138">ビルトイン アカウントを指定する構成はブロックされます。</span><span class="sxs-lookup"><span data-stu-id="8254b-138">The tool blocks configurations that specify built-in accounts.</span></span>  
  
    2.  <span data-ttu-id="8254b-139">**[データベース サーバー]:** SharePoint ファームでサポートされている SQL Server データベース エンジンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8254b-139">**Database Server**: You can use SQL Server Database engine that is supported for the SharePoint farm.</span></span>  
  
    3.  <span data-ttu-id="8254b-140">**[パスフレーズ]:** パスフレーズを入力します。</span><span class="sxs-lookup"><span data-stu-id="8254b-140">**Passphrase**: Enter a passphrase.</span></span> <span data-ttu-id="8254b-141">新しい SharePoint ファームを作成する場合、SharePoint ファームにサーバーまたはアプリケーションを追加するたびにこのパスフレーズが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8254b-141">If you are creating a new SharePoint farm, the passphrase is used whenever you add a server or application to the SharePoint farm.</span></span> <span data-ttu-id="8254b-142">ファームが既に存在する場合、ファームにサーバー アプリケーションを追加するためのパスフレーズを入力してください。</span><span class="sxs-lookup"><span data-stu-id="8254b-142">If the farm already exists, enter the passphrase that allows you to add a server application to the farm.</span></span>  
  
    4.  <span data-ttu-id="8254b-143">**[Excel Services 用 PowerPivot サーバー]:** SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8254b-143">**PowerPivot Server for Excel Services**: Type the name of an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server.</span></span> <span data-ttu-id="8254b-144">シングル サーバー配置では、データベース サーバーと同じサーバーです。</span><span class="sxs-lookup"><span data-stu-id="8254b-144">In a single-server deployment, it is the same as the database server.</span></span> `[ServerName]\powerpivot`  
  
    5.  <span data-ttu-id="8254b-145">左側のウィンドウで **[サイト コレクションの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-145">Click **Create Site Collection** in the left window.</span></span> <span data-ttu-id="8254b-146">**[サイトの URL]** をメモしておくと、この後の手順で参照できます。</span><span class="sxs-lookup"><span data-stu-id="8254b-146">Note **Site URL** so you can reference it in later steps.</span></span> <span data-ttu-id="8254b-147">SharePoint サーバーがまだ構成されていない場合、構成ウィザードでは Web アプリケーションとサイト コレクション URL のルートは既定で `http://[ServerName]`になります。</span><span class="sxs-lookup"><span data-stu-id="8254b-147">If the SharePoint server is not already configured, then the configuration wizard defaults the web application, and site collection URLs to the root of `http://[ServerName]`.</span></span> <span data-ttu-id="8254b-148">既定値を変更するには、左側のウィンドウの **[既定の Web アプリケーションの作成]** ページおよび **[Web アプリケーション ソリューションの配置]** ページを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-148">To modify the defaults review the following pages in the left window: **Create Default Web application** and **Deploy Web Application Solution**</span></span>  
  
5.  <span data-ttu-id="8254b-149">必要に応じて、各アクションを完了するために使用された残りの入力値を確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-149">Optionally, review the remaining input values used to complete each action.</span></span> <span data-ttu-id="8254b-150">左側のウィンドウで各アクションをクリックして、アクションの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-150">Click each action in the left window to see and review the details of the action.</span></span> <span data-ttu-id="8254b-151">それぞれの詳細については、このトピックの「 [&#41;&#40;PowerPivot 構成ツールの構成または修復 2010 PowerPivot for SharePoint](../../configure-repair-powerpivot-sharepoint-2010.md)でのサーバーの構成に使用する入力値」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8254b-151">For more information about each one, see the section "Input values used to configure the server in [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) in this topic.</span></span>  
  
6.  <span data-ttu-id="8254b-152">必要に応じて、今回は処理しないすべてのアクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="8254b-152">Optionally, remove any actions that you do not want to process at this time.</span></span> <span data-ttu-id="8254b-153">たとえば、Secure Store Service を後で構成する場合は、 **[Secure Store Service の構成]** をクリックし、 **[この操作をタスク一覧に含めます]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8254b-153">For example, if you want to configure Secure Store Service later, click **Configure Secure Store Service**, and then clear the checkbox **Include this action in the task list**.</span></span>  
  
7.  <span data-ttu-id="8254b-154">**[検証]** をクリックして、一覧のアクションを処理するための十分な情報があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-154">Click **Validate** to check whether the tool has sufficient information to process the actions in the list.</span></span> <span data-ttu-id="8254b-155">検証エラーがある場合は、左ペインで警告をクリックして検証エラーの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-155">If you see validation errors, click the warnings in the left pane to see details of the validation error.</span></span> <span data-ttu-id="8254b-156">検証エラーを修正し、もう一度 **[検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-156">Correct any validation errors and then click **Validate** again.</span></span>  
  
8.  <span data-ttu-id="8254b-157">**[実行]** をクリックして、タスクの一覧にあるすべてのアクションを処理します。</span><span class="sxs-lookup"><span data-stu-id="8254b-157">Click **Run** to process all of the actions in the task list.</span></span> <span data-ttu-id="8254b-158">**[実行]** は、アクションの検証後に有効になります。</span><span class="sxs-lookup"><span data-stu-id="8254b-158">Note that **Run** becomes available after you validate the actions.</span></span> <span data-ttu-id="8254b-159">**[実行]** が有効になっていない場合は、まず **[検証]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="8254b-159">If **Run** is not enabled, click **Validate** first.</span></span>  
  
 <span data-ttu-id="8254b-160">詳細については、「 [PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツールの構成または修復](../../configure-repair-powerpivot-sharepoint-2010.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="8254b-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span></span>  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a><span data-ttu-id="8254b-161">PowerPivot の構成の確認</span><span class="sxs-lookup"><span data-stu-id="8254b-161">Verify PowerPivot Configuration</span></span>  
 <span data-ttu-id="8254b-162">**サービス**</span><span class="sxs-lookup"><span data-stu-id="8254b-162">**Services:**</span></span>  
  
1.  <span data-ttu-id="8254b-163">サーバーの全体管理で、[システム設定] の [**サーバーのサービスの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-163">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="8254b-164">**SQL Server Analysis Services** と **SQL Server PowerPivot System サービス** が開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-164">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
 <span data-ttu-id="8254b-165">**ファーム機能**</span><span class="sxs-lookup"><span data-stu-id="8254b-165">**Farm Feature:**</span></span>  
  
1.  <span data-ttu-id="8254b-166">サーバーの全体管理で、[システム設定] の **[ファーム機能の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-166">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
2.  <span data-ttu-id="8254b-167">**[PowerPivot 統合機能]** が **[アクティブ]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-167">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
 <span data-ttu-id="8254b-168">**サイト コレクション機能**</span><span class="sxs-lookup"><span data-stu-id="8254b-168">**Site Collection Feature:**</span></span>  
  
1.  <span data-ttu-id="8254b-169">構成ツールによって作成されたサイトの URL を参照します。</span><span class="sxs-lookup"><span data-stu-id="8254b-169">Browse to your site URL that was created by the Configuration tool.</span></span>  
  
     <span data-ttu-id="8254b-170">[**設定**] [![SharePoint の設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")] の順にクリックし、[**サイトの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-170">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings"), and then click **Site Settings**.</span></span>  
  
     <span data-ttu-id="8254b-171">**[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-171">Click **Site Collection Features**.</span></span>  
  
2.  <span data-ttu-id="8254b-172">**[サイト コレクションの PowerPivot 機能の統合]** が **[アクティブ]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-172">Verify that **PowerPivot Feature Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="8254b-173">**PowerPivot サービスアプリケーション:**</span><span class="sxs-lookup"><span data-stu-id="8254b-173">**PowerPivot Service Application:**</span></span>  
  
1.  <span data-ttu-id="8254b-174">サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-174">In Central Administration, in the **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="8254b-175">サービス アプリケーションの状態が **[開始済み]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-175">Verify the service application status is **started**.</span></span> <span data-ttu-id="8254b-176">既定の名前は、"**既定の PowerPivot サービスアプリケーション**" です。</span><span class="sxs-lookup"><span data-stu-id="8254b-176">The default name is **Default PowerPivot Service Application**.</span></span>  
  
     <span data-ttu-id="8254b-177">サービス アプリケーションの名前をクリックして、このサービス アプリケーションの PowerPivot 管理ダッシュボードを開きます。</span><span class="sxs-lookup"><span data-stu-id="8254b-177">Click the name of the services application to open the PowerPivot Management Dashboard for the service application opens.</span></span> <span data-ttu-id="8254b-178">最初に使用するときは、ダッシュボードの読み込みに数分かかります。</span><span class="sxs-lookup"><span data-stu-id="8254b-178">On first use, the dashboard takes several minutes to load.</span></span>  
  
 <span data-ttu-id="8254b-179">詳細については、「 [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8254b-179">For more information, see [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).</span></span>  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a><span data-ttu-id="8254b-180">問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8254b-180">Troubleshoot Issues</span></span>  
 <span data-ttu-id="8254b-181">問題のトラブルシューティングに役立てるために、診断ログを有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8254b-181">To assist in troubleshooting issues, it is a good idea to verify the diagnostic logging is enabled.</span></span>  
  
1.  <span data-ttu-id="8254b-182">SharePoint サーバーの全体管理で、 **[監視]** をクリックし、 **[使用状況と正常性のデータ収集の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-182">In SharePoint Central Administration, click **Monitoring** and then click **Configure usage and health data collection**.</span></span>  
  
2.  <span data-ttu-id="8254b-183">**[使用状況データ収集を有効にする]** チェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-183">Verify **Enable usage data collection** is selected.</span></span>  
  
3.  <span data-ttu-id="8254b-184">次のイベントが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-184">Verify the following events are selected:</span></span>  
  
    -   <span data-ttu-id="8254b-185">学歴利用統計情報の使用状況フィールドの定義</span><span class="sxs-lookup"><span data-stu-id="8254b-185">Definition of usage fields for Education telemetry</span></span>  
  
    -   <span data-ttu-id="8254b-186">PowerPivot 接続</span><span class="sxs-lookup"><span data-stu-id="8254b-186">PowerPivot Connects</span></span>  
  
    -   <span data-ttu-id="8254b-187">PowerPivot 読み込みデータの使用状況</span><span class="sxs-lookup"><span data-stu-id="8254b-187">PowerPivot Load Data Usage</span></span>  
  
    -   <span data-ttu-id="8254b-188">PowerPivot クエリの使用状況</span><span class="sxs-lookup"><span data-stu-id="8254b-188">PowerPivot Query Usage</span></span>  
  
    -   <span data-ttu-id="8254b-189">PowerPivot アンロード データの使用状況</span><span class="sxs-lookup"><span data-stu-id="8254b-189">PowerPivot Unload Data Usage</span></span>  
  
4.  <span data-ttu-id="8254b-190">**[正常性データの収集を有効にする]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8254b-190">Verify **Enable health data collection** is selected.</span></span>  
  
5.  <span data-ttu-id="8254b-191">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8254b-191">Click **OK**.</span></span>  
  
 <span data-ttu-id="8254b-192">データ更新のトラブルシューティングの詳細については、「 [PowerPivot データ更新のトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx)」 (を参照してください https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="8254b-192">For more information on trouble shooting data refresh, see [Troubleshooting PowerPivot Data Refresh](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).</span></span>  
  
 <span data-ttu-id="8254b-193">構成ツールの詳細については、「 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8254b-193">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>  
  
  
