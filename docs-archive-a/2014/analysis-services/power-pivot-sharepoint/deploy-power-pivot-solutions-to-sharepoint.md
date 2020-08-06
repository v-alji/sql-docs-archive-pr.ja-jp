---
title: SharePoint への PowerPivot ソリューションの配置 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
ms.openlocfilehash: 043647988598f932b70cc06e6bb5492d66864372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642975"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a><span data-ttu-id="14a8e-102">SharePoint への PowerPivot ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="14a8e-102">Deploy PowerPivot Solutions to SharePoint</span></span>
  <span data-ttu-id="14a8e-103">SharePoint Server 2010 環境に PowerPivot 機能を追加する 2 つのソリューション パッケージを手動で配置するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="14a8e-103">Use the following instructions to manually deploy two solution packages that add PowerPivot features to a SharePoint Server 2010 environment.</span></span> <span data-ttu-id="14a8e-104">ソリューションの配置は、SharePoint 2010 サーバー上で PowerPivot for SharePoint を構成するために必要な手順です。</span><span class="sxs-lookup"><span data-stu-id="14a8e-104">Deploying the solutions is a required step for configuring PowerPivot for SharePoint on a SharePoint 2010 server.</span></span> <span data-ttu-id="14a8e-105">必要な手順の完全な一覧については、「[サーバーの全体管理での PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14a8e-105">To view the complete list of required steps, see [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md).</span></span>  
  
 <span data-ttu-id="14a8e-106">ソリューションの配置には、PowerPivot 構成ツールを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-106">Alternatively, you can use the PowerPivot Configuration Tool to deploy the solutions.</span></span> <span data-ttu-id="14a8e-107">シングル サーバー インストールでは構成ツールを使用するのが簡単で効率的ですが、使い慣れたツールを使用したい場合や、複数の機能を同時に構成する場合は、サーバーの全体管理と PowerShell を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-107">Using the configuration tool is easier and more efficient for a single server installation, but you might want to use Central Administration and PowerShell if you prefer using a familiar tool or if you are configuring multiple features at the same time.</span></span> <span data-ttu-id="14a8e-108">構成ツールの使用方法の詳細については、「 [PowerPivot 構成ツール](power-pivot-configuration-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14a8e-108">For more information about using the configuration tool, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
 <span data-ttu-id="14a8e-109">ソリューションを配置する前に、まず、SQL Server 2012 インストール メディアを使用して、PowerPivot for SharePoint をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a8e-109">Before deploying the solutions, you must first install PowerPivot for SharePoint using the SQL Server 2012 installation media.</span></span> <span data-ttu-id="14a8e-110">SQL Server セットアップでは、配置しようとしているソリューション パッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-110">SQL Server Setup installs the solution packages that you are about to deploy.</span></span>  
  
 <span data-ttu-id="14a8e-111">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="14a8e-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="14a8e-112">前提条件: Web アプリケーションでクラシックモード認証が使用されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="14a8e-112">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>](#bkmk_classic)  
  
 [<span data-ttu-id="14a8e-113">手順 1: ファーム ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="14a8e-113">Step 1: Deploy the Farm Solution</span></span>](#bkmk_farm)  
  
 [<span data-ttu-id="14a8e-114">手順 2: サーバーの全体管理への PowerPivot Web アプリケーション ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="14a8e-114">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>](#deployCA)  
  
 [<span data-ttu-id="14a8e-115">手順 3: 他の Web アプリケーションへの PowerPivot Web アプリケーション ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="14a8e-115">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>](#deployUI)  
  
 [<span data-ttu-id="14a8e-116">ソリューションの再配置または取り消し</span><span class="sxs-lookup"><span data-stu-id="14a8e-116">Redeploy or retract the Solution</span></span>](#retract)  
  
 [<span data-ttu-id="14a8e-117">PowerPivot ソリューションについて</span><span class="sxs-lookup"><span data-stu-id="14a8e-117">About the PowerPivot Solutions</span></span>](#intro)  
  
##  <a name="prerequisite-verify-the-web-application-uses-classic-mode-authentication"></a><a name="bkmk_classic"></a> <span data-ttu-id="14a8e-118">前提条件: Web アプリケーションでクラシック モード認証が使用されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="14a8e-118">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>  
 <span data-ttu-id="14a8e-119">PowerPivot for SharePoint は、Windows クラシック モード認証を使用する Web アプリケーションでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-119">PowerPivot for SharePoint is only supported for web applications that use Windows-classic mode authentication.</span></span> <span data-ttu-id="14a8e-120">アプリケーションでクラシックモードが使用されているかどうかを確認するには、 **sharepoint 2010 管理シェル**から次の PowerShell コマンドレットを実行し `http://<top-level site name>` ます。の部分は、実際の sharepoint サイトの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="14a8e-120">To check whether the application uses Classic mode, run the following PowerShell cmdlet from the **SharePoint 2010 Management Shell**, replacing `http://<top-level site name>` with the name of your SharePoint site:</span></span>  
  
```powershell
Get-SPWebApplication http://<top-level site name> | Format-List UseClaimsAuthentication  
```  
  
 <span data-ttu-id="14a8e-121">戻り値が **false**になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a8e-121">The return value should be **false**.</span></span> <span data-ttu-id="14a8e-122">**True**の場合、この web アプリケーションを使用して PowerPivot データにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="14a8e-122">If it is **true**, you cannot access PowerPivot data with this web application.</span></span>  
  
##  <a name="step-1-deploy-the-farm-solution"></a><a name="bkmk_farm"></a><span data-ttu-id="14a8e-123">手順 1: ファームソリューションを配置する</span><span class="sxs-lookup"><span data-stu-id="14a8e-123">Step 1: Deploy the Farm Solution</span></span>  
 <span data-ttu-id="14a8e-124">このセクションでは、PowerShell を使用したソリューションの配置方法を紹介しますが、同じタスクを PowerPivot 構成ツールを使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-124">This section shows you how to deploy solutions using PowerShell, but you can also use the PowerPivot Configuration Tool to complete this task.</span></span> <span data-ttu-id="14a8e-125">詳細については、「 [PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツール&#41;の構成または修復](../configure-repair-powerpivot-sharepoint-2010.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14a8e-125">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="14a8e-126">このタスクは、PowerPivot for SharePoint をインストールした後で、一度だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a8e-126">This task only needs to be performed once, after you install PowerPivot for SharePoint.</span></span>  
  
1.  <span data-ttu-id="14a8e-127">PowerPivot for SharePoint がインストールされているサーバーで、[**管理者として実行**] オプションを使用して SharePoint 2010 管理シェルを開きます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-127">On a server that has an installation of PowerPivot for SharePoint, open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="14a8e-128">次のコマンドレットを実行してファーム ソリューションを追加します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-128">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="14a8e-129">コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-129">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="14a8e-130">次の手順では、ソリューションを配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-130">In the next step, you will deploy the solution.</span></span>  
  
3.  <span data-ttu-id="14a8e-131">次のコマンドレットを実行してファーム ソリューションを配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-131">Run the next cmdlet to deploy the farm solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="step-2-deploy-the-powerpivot-web-application-solution-to-central-administration"></a><a name="deployCA"></a><span data-ttu-id="14a8e-132">手順 2: サーバーの全体管理に PowerPivot Web アプリケーションソリューションを配置する</span><span class="sxs-lookup"><span data-stu-id="14a8e-132">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>  
 <span data-ttu-id="14a8e-133">ファーム ソリューションを配置した後で、サーバーの全体管理に Web アプリケーション ソリューションを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a8e-133">After you deploy the farm solution, you must deploy the Web application solution to Central Administration.</span></span> <span data-ttu-id="14a8e-134">この手順によって、サーバーの全体管理に PowerPivot 管理ダッシュボードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-134">This step adds the PowerPivot Management Dashboard to Central Administration.</span></span>  
  
1.  <span data-ttu-id="14a8e-135">**[管理者として実行]** オプションを使用して SharePoint 2010 管理シェルを開きます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-135">Open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="14a8e-136">次のコマンドレットを実行して、サーバーの全体管理への参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-136">Run the following cmdlet to create a reference to Central Administration:</span></span>  
  
    ```powershell
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  <span data-ttu-id="14a8e-137">次のコマンドレットを実行してファーム ソリューションを追加します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-137">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     <span data-ttu-id="14a8e-138">コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-138">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="14a8e-139">次の手順では、ソリューションを配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-139">In the next step, you will deploy the solution.</span></span>  
  
4.  <span data-ttu-id="14a8e-140">次のコマンドレットを実行して、サーバーの全体管理に Web アプリケーション ソリューションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-140">Run the next cmdlet to install the web application solution to Central Administration.</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 <span data-ttu-id="14a8e-141">これで Web アプリケーション ソリューションがサーバーの全体管理に配置されたので、残りのすべての構成手順は、サーバーの全体管理を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-141">Now that the web application solution is deployed to Central Administration, you can use Central Administration to complete all remaining configuration steps.</span></span>  
  
##  <a name="step-3-deploy-the-powerpivot-web-application-solution-to-other-web-applications"></a><a name="deployUI"></a><span data-ttu-id="14a8e-142">手順 3: PowerPivot Web アプリケーションソリューションを他の Web アプリケーションに配置する</span><span class="sxs-lookup"><span data-stu-id="14a8e-142">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>  
 <span data-ttu-id="14a8e-143">前のタスクでは、Powerpivotwebapp.wsp をサーバーの全体管理に配置しました。</span><span class="sxs-lookup"><span data-stu-id="14a8e-143">In the previous task, you deployed Powerpivotwebapp.wsp to Central Administration.</span></span> <span data-ttu-id="14a8e-144">ここでは、PowerPivot データ アクセスをサポートする既存の各 Web アプリケーションに powerpivotwebapp.wsp を配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-144">In this section, you deploy the powerpivotwebapp.wsp on each existing web application that supports PowerPivot data access.</span></span> <span data-ttu-id="14a8e-145">後でさらに Web アプリケーションを追加する場合は、それらの追加の Web アプリケーションに対して、この手順を繰り返してください。</span><span class="sxs-lookup"><span data-stu-id="14a8e-145">If you add more web applications later, be sure to repeat this step for those additional web applications.</span></span>  
  
1.  <span data-ttu-id="14a8e-146">サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-146">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="14a8e-147">[ **Powerpivotwebapp.wsp**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-147">Click **powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="14a8e-148">**[ソリューションの配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-148">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="14a8e-149">[**配置先**] で、PowerPivot 機能のサポートを追加する SharePoint web アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-149">In **Deploy To?**, select the SharePoint web application for which you want to add PowerPivot feature support.</span></span>  
  
5.  <span data-ttu-id="14a8e-150">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="14a8e-151">PowerPivot データ アクセスをサポートする他の SharePoint Web アプリケーションに対して、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-151">Repeat for other SharePoint web applications that will also support PowerPivot data access.</span></span>  
  
##  <a name="redeploy-or-retract-the-solution"></a><a name="retract"></a><span data-ttu-id="14a8e-152">ソリューションの再配置または取り消し</span><span class="sxs-lookup"><span data-stu-id="14a8e-152">Redeploy or retract the Solution</span></span>  
 <span data-ttu-id="14a8e-153">SharePoint サーバーの全体管理でソリューションの取り消しを実行できますが、インストールや修正プログラムの配置に関する問題のトラブルシューティングを体系的に行う場合を除いて、powerpivotwebapp.wsp ファイルを取り消す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="14a8e-153">Although SharePoint Central Administration provides solution retraction, you do not need to retract the powerpivotwebapp.wsp file unless you are systematically troubleshooting an installation or patch deployment problem.</span></span>  
  
1.  <span data-ttu-id="14a8e-154">SharePoint 2010 サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-154">In SharePoint 2010 Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="14a8e-155">**[powerpivotwebapp.wsp]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-155">Click **Powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="14a8e-156">**[ソリューションの取り消し]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-156">Click **Retract Solution**.</span></span>  
  
 <span data-ttu-id="14a8e-157">ファームソリューションに対してトレースバックするサーバー配置の問題が発生した場合は、PowerPivot 構成ツールで [**修復**] オプションを実行して再配置できます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-157">If you encounter server deployment issues that you trace back to the farm solution, you can redeploy it by running the **Repair** option in the PowerPivot Configuration Tool.</span></span> <span data-ttu-id="14a8e-158">手動の手順が少なくて済むため、修復操作を行うときはこのツールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="14a8e-158">Repair operations via the tool is preferred because it requires fewer steps on your part.</span></span> <span data-ttu-id="14a8e-159">詳細については、「 [PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツール&#41;の構成または修復](../configure-repair-powerpivot-sharepoint-2010.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14a8e-159">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="14a8e-160">すべてのソリューションを再配置する場合は、次の順序で実行してください。</span><span class="sxs-lookup"><span data-stu-id="14a8e-160">If you still want to re-deploy all solutions, be sure to do so in this order:</span></span>  
  
1.  <span data-ttu-id="14a8e-161">PowerPivot Web アプリケーション ソリューションを使用しているすべての SharePoint Web アプリケーションでそのソリューションを取り消します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-161">Retract the PowerPivot Web application solution from all SharePoint web applications that use it.</span></span>  
  
2.  <span data-ttu-id="14a8e-162">PowerPivot ファーム ソリューションを取り消します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-162">Retract the PowerPivot farm solution.</span></span>  
  
3.  <span data-ttu-id="14a8e-163">PowerPivot ファーム ソリューションを再配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-163">Redeploy the PowerPivot farm solution.</span></span>  
  
4.  <span data-ttu-id="14a8e-164">PowerPivot Web アプリケーション ソリューションをすべての SharePoint Web アプリケーションに再配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-164">Redeploy the PowerPivot Web application solution to all SharePoint web applications.</span></span>  
  
##  <a name="about-the-powerpivot-solutions"></a><a name="intro"></a><span data-ttu-id="14a8e-165">PowerPivot ソリューションについて</span><span class="sxs-lookup"><span data-stu-id="14a8e-165">About the PowerPivot Solutions</span></span>  
 <span data-ttu-id="14a8e-166">PowerPivot for SharePoint では、2 つのソリューション パッケージを使用して、アプリケーション ページとプログラム ファイルをファームおよび個々の Web アプリケーションに配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-166">PowerPivot for SharePoint uses two solution packages to deploy its application pages and program files to the farm and to individual web applications.</span></span>  
  
-   <span data-ttu-id="14a8e-167">ファーム ソリューションはグローバルです。</span><span class="sxs-lookup"><span data-stu-id="14a8e-167">The farm solution is global.</span></span> <span data-ttu-id="14a8e-168">このソリューションは一度配置するだけで、後でファームに追加する新しい PowerPivot for SharePoint サーバーで自動的に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="14a8e-168">It is deployed once and then becomes automatically available to any new PowerPivot for SharePoint servers that you add to the farm later.</span></span>  
  
-   <span data-ttu-id="14a8e-169">Web アプリケーション ソリューションはアプリケーション固有であり、サーバーの全体管理 Web アプリケーションを含め、ファーム内の各 Web アプリケーションに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a8e-169">The web application solution is application-specific and must be deployed to each web application in the farm, including the Central Administration web application.</span></span>  
  
 <span data-ttu-id="14a8e-170">各ソリューションは別々に配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-170">Each solution is deployed differently.</span></span>  <span data-ttu-id="14a8e-171">ファーム ソリューションは、最初の PowerPivot for SharePoint インスタンスのインストール後に一度だけ配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-171">The farm solution is deployed once, after the first PowerPivot for SharePoint instance is installed.</span></span> <span data-ttu-id="14a8e-172">ファーム ソリューションを配置するには、PowerPivot 構成ツールか PowerShell コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-172">To deploy the farm solution, you use the PowerPivot Configuration Tool or PowerShell cmdlets.</span></span>  
  
 <span data-ttu-id="14a8e-173">最初に Web アプリケーション ソリューションをサーバーの全体管理に配置し、その後で、PowerPivot データに対する要求をサポートする追加の Web アプリケーションに後のソリューションを配置します。</span><span class="sxs-lookup"><span data-stu-id="14a8e-173">The web application solution is initially deployed to Central Administration, followed by subsequent solution deployments to any additional web applications that will support requests for PowerPivot data.</span></span> <span data-ttu-id="14a8e-174">サーバーの全体管理に web アプリケーションソリューションを配置するには、PowerPivot 構成ツールまたは PowerShell コマンドレットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a8e-174">To deploy the web application solution to Central Administration, you must use the PowerPivot Configuration Tool or PowerShell cmdlet.</span></span> <span data-ttu-id="14a8e-175">その他すべての Web アプリケーションには、サーバーの全体管理または PowerShell を使用して、Web アプリケーション ソリューションを手動で配置できます。</span><span class="sxs-lookup"><span data-stu-id="14a8e-175">For all other web applications, you can deploy the web application solution manually using Central Administration or PowerShell.</span></span>  
  
|<span data-ttu-id="14a8e-176">解決策</span><span class="sxs-lookup"><span data-stu-id="14a8e-176">Solution</span></span>|<span data-ttu-id="14a8e-177">説明</span><span class="sxs-lookup"><span data-stu-id="14a8e-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="14a8e-178">powerpivotfarm.wsp</span><span class="sxs-lookup"><span data-stu-id="14a8e-178">Powerpivotfarm.wsp</span></span>|<span data-ttu-id="14a8e-179">Microsoft.AnalysisServices.SharePoint.Integration.dll をグローバル アセンブリに追加する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-179">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="14a8e-180">Microsoft.AnalysisServices.ChannelTransport.dll をグローバル アセンブリに追加する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-180">Adds Microsoft.AnalysisServices.ChannelTransport.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="14a8e-181">機能とリソース ファイルをインストールし、コンテンツ タイプを登録する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-181">Installs features and resources files, and registers content types.</span></span><br /><br /> <span data-ttu-id="14a8e-182">PowerPivot ギャラリー ライブラリやデータ フィード ライブラリのライブラリ テンプレートを追加する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-182">Adds library templates for PowerPivot Gallery and Data Feed libraries.</span></span><br /><br /> <span data-ttu-id="14a8e-183">サービス アプリケーションの構成、PowerPivot 管理ダッシュボード、データ更新、および PowerPivot ギャラリー用のアプリケーション ページを追加する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-183">Adds application pages for service application configuration, PowerPivot Management Dashboard, data refresh, and PowerPivot Gallery.</span></span>|  
|<span data-ttu-id="14a8e-184">[powerpivotwebapp.wsp]</span><span class="sxs-lookup"><span data-stu-id="14a8e-184">Powerpivotwebapp.wsp</span></span>|<span data-ttu-id="14a8e-185">Web フロントエンドの Web サーバー拡張機能フォルダーに Microsoft.AnalysisServices.SharePoint.Integration.dll リソース ファイルを追加する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-185">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll resources files to the web server extensions folder on the Web front-end.</span></span><br /><br /> <span data-ttu-id="14a8e-186">Web フロントエンドに PowerPivot Web サービスを追加する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-186">Adds PowerPivot Web service to the Web-front end.</span></span><br /><br /> <span data-ttu-id="14a8e-187">PowerPivot ギャラリーのサムネイル画像生成を追加する。</span><span class="sxs-lookup"><span data-stu-id="14a8e-187">Adds thumbnail image generation for PowerPivot Gallery.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14a8e-188">参照</span><span class="sxs-lookup"><span data-stu-id="14a8e-188">See Also</span></span>  
 <span data-ttu-id="14a8e-189">[PowerPivot for SharePoint のアップグレード](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="14a8e-189">[Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="14a8e-190">[サーバーの全体管理での PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="14a8e-190">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 [<span data-ttu-id="14a8e-191">Windows PowerShell を使用した PowerPivot の構成</span><span class="sxs-lookup"><span data-stu-id="14a8e-191">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
