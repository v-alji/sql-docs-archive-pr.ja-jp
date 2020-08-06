---
title: PowerPivot for SharePoint 2013 | の最小特権構成の例Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0188f314e4c354b33d03e6e7948aed1ba4cf8be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713597"
---
# <a name="example-of-a-minimum-privilege-configuration-for-powerpivot-for-sharepoint-2013"></a><span data-ttu-id="aff5f-102">Power Pivot for SharePoint 2013 向けに最小限の特権を構成する例</span><span class="sxs-lookup"><span data-stu-id="aff5f-102">Example of a Minimum-Privilege Configuration for PowerPivot for SharePoint 2013</span></span>
  <span data-ttu-id="aff5f-103">このトピックでは、最小限の特権を使用する PowerPivot for SharePoint 2013 構成の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-103">This topic describes an example PowerPivot for SharePoint 2013 configuration with minimum privileges.</span></span> <span data-ttu-id="aff5f-104">この構成では、3 種類のコンポーネントごとに個別のアカウントを使用します。各アカウントには最小レベルの特権を指定します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-104">The configuration utilizes a different account for each of the three components and each account has the minimum level of privileges.</span></span>  
  
## <a name="summary-of-accounts"></a><span data-ttu-id="aff5f-105">アカウントの概要</span><span class="sxs-lookup"><span data-stu-id="aff5f-105">Summary of Accounts</span></span>  
 <span data-ttu-id="aff5f-106">PowerPivot for SharePoint 2013 では、Analysis Services サービス アカウントに Network Service アカウントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="aff5f-106">PowerPivot for SharePoint 2013 supports the use of the Network Service account for the Analysis Services service account.</span></span> <span data-ttu-id="aff5f-107">Network Service アカウントは、SharePoint 2010 のシナリオではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="aff5f-107">The Network Service account is not a supported scenario with SharePoint 2010.</span></span> <span data-ttu-id="aff5f-108">サービスアカウントの詳細については、「 [Windows サービスアカウントと権限の構成](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)(」を参照してください https://msdn.microsoft.com/library/ms143504.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="aff5f-108">For more information on Service accounts, see [Configure Windows Service Accounts and Permissions](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (https://msdn.microsoft.com/library/ms143504.aspx).</span></span>  
  
 <span data-ttu-id="aff5f-109">次の表は、最小限の特権の構成の例で使用する 3 種類のアカウントをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="aff5f-109">The following table summarizes the three accounts used in this example of a minimum privileged configuration.</span></span>  
  
|<span data-ttu-id="aff5f-110">Scope</span><span class="sxs-lookup"><span data-stu-id="aff5f-110">Scope</span></span>|<span data-ttu-id="aff5f-111">名前</span><span class="sxs-lookup"><span data-stu-id="aff5f-111">Name</span></span>|  
|-----------|----------|  
|<span data-ttu-id="aff5f-112">SharePoint 管理者アカウント</span><span class="sxs-lookup"><span data-stu-id="aff5f-112">SharePoint Administrator account</span></span>|<span data-ttu-id="aff5f-113">**SPAdmin**</span><span class="sxs-lookup"><span data-stu-id="aff5f-113">**SPAdmin**</span></span>|  
|<span data-ttu-id="aff5f-114">SharePoint ファーム アカウント</span><span class="sxs-lookup"><span data-stu-id="aff5f-114">SharePoint Farm account</span></span>|<span data-ttu-id="aff5f-115">**SPFarm**</span><span class="sxs-lookup"><span data-stu-id="aff5f-115">**SPFarm**</span></span>|  
|<span data-ttu-id="aff5f-116">Analysis Services サービス アカウント</span><span class="sxs-lookup"><span data-stu-id="aff5f-116">Analysis Services service account</span></span>|<span data-ttu-id="aff5f-117">**SPsvc**</span><span class="sxs-lookup"><span data-stu-id="aff5f-117">**SPsvc**</span></span>|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a><span data-ttu-id="aff5f-118">SharePoint 管理者アカウント (SpAdmin)</span><span class="sxs-lookup"><span data-stu-id="aff5f-118">The SharePoint Administrator account (SpAdmin)</span></span>  
 <span data-ttu-id="aff5f-119">**SPAdmin** は、ファームのインストールと構成に使用するドメイン アカウントです。</span><span class="sxs-lookup"><span data-stu-id="aff5f-119">**SPAdmin** is a domain account you use to install and configure the farm.</span></span> <span data-ttu-id="aff5f-120">このアカウントは、SharePoint 構成ウィザードと SharePoint 2013 用 PowerPivot 構成ツールの実行に使用されます。 **Spadmin**アカウントは、ローカル管理者権限を必要とする唯一のアカウントです。</span><span class="sxs-lookup"><span data-stu-id="aff5f-120">It is the account used to run the SharePoint Configuration Wizard and the PowerPivot Configuration Tool for SharePoint 2013.The **SPAdmin** account is the only account that requires local Administrator rights.</span></span> <span data-ttu-id="aff5f-121">PowerPivot 構成ツールを実行する前に、SharePoint によってコンテンツデータベースと構成データベースが作成される SQL Server データベースインスタンスに、 **Spadmin**アカウントの特権を付与します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-121">Before running the PowerPivot Configuration tool, grant the **SPAdmin** account privileges to the SQL Server database instance where SharePoint creates content and configuration databases.</span></span> <span data-ttu-id="aff5f-122">最小限の特権のシナリオで SPAdmin アカウントを構成する場合、SPAdmin アカウントは **securityadmin** ロールと **dbcreator**ロールのメンバーにします。</span><span class="sxs-lookup"><span data-stu-id="aff5f-122">To configure the SPAdmin account in a minimum privilege scenario, it should be a member of the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-farm-account-spfarm"></a><span data-ttu-id="aff5f-123">ファーム アカウント (SPFarm)</span><span class="sxs-lookup"><span data-stu-id="aff5f-123">The Farm account (SPFarm)</span></span>  
 <span data-ttu-id="aff5f-124">**SPFarm** は、SharePoint Timer Service と全体管理用 Web アプリケーションが SharePoint コンテンツ データベースにアクセスするために使用するドメイン アカウントです。</span><span class="sxs-lookup"><span data-stu-id="aff5f-124">**SPFarm** is a domain account that the SharePoint Timer service and the web application for Central Administration use to access the SharePoint content database.</span></span> <span data-ttu-id="aff5f-125">このアカウントは、ローカル管理者である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aff5f-125">This account does not need to be a local administrator.</span></span> <span data-ttu-id="aff5f-126">SharePoint 構成ウィザードでは、バックエンドの SQL Server データベースで必要最小限の特権を付与します。SQL Server の特権の最小限の構成は **securityadmin** ロールと **dbcreator**ロールのメンバーシップです。</span><span class="sxs-lookup"><span data-stu-id="aff5f-126">The SharePoint configuration wizard grants the proper minimal privilege in the back-end SQL Server database.The minimum SQL Server privilege configuration is membership in the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-service-account-for-powerpivot-service-spsvc"></a><span data-ttu-id="aff5f-127">PowerPivot サービスのサービス アカウント (SPsvc)</span><span class="sxs-lookup"><span data-stu-id="aff5f-127">The Service Account for PowerPivot Service (SPsvc)</span></span>  
 <span data-ttu-id="aff5f-128">PowerPivot 構成ツールを実行する前に新しい SharePoint ファームが構成されていない場合、PowerPivot 構成ツールでは既定で以下のものを作成します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-128">If a new SharePoint farm is not configured before you run the PowerPivot Configuration tool, then by default the PowerPivot Configuration tool will create the following:</span></span>  
  
-   <span data-ttu-id="aff5f-129">PowerPivot サービス アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="aff5f-129">PowerPivot Service application.</span></span>  
  
-   <span data-ttu-id="aff5f-130">Excel Services アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="aff5f-130">Excel Services application.</span></span>  
  
-   <span data-ttu-id="aff5f-131">Secure Store アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="aff5f-131">Secure Store application.</span></span>  
  
 <span data-ttu-id="aff5f-132">PowerPivot 構成ツールは、既定のアプリケーション プールのサービス アプリケーション 3 つすべてを構成します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-132">The PowerPivot configuration tool configures all three of the service applications in the default application pool.</span></span> <span data-ttu-id="aff5f-133">このアプリケーション プールは通常、サービス アカウントが不要な多くのリソースにアクセスできる SPFarm アカウントとして実行されるように構成されます。最小限の特権環境にするには、適切なアプリケーション プールおよび Web アプリケーションで使用する新しいドメイン アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-133">That application pool is typically configured to run as the SPFarm account, which has access to many resources that a service account does not require.To make the environment a minimum-privileged environment, configure a new domain account to be use by the appropriate application pool and web application.</span></span>  
  
 <span data-ttu-id="aff5f-134">**SharePoint Service アカウントとして使用する新しいドメイン アカウント SPsvc を作成するには**</span><span class="sxs-lookup"><span data-stu-id="aff5f-134">**To create a new domain account SPsvc to be used as a SharePoint Service account:**</span></span>  
  
1.  <span data-ttu-id="aff5f-135">SharePoint サーバーの全体管理で、[**セキュリティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff5f-135">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="aff5f-136">[**サービスアカウントの構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff5f-136">Click **Configure Service Accounts**</span></span>  
  
3.  <span data-ttu-id="aff5f-137">[**新しい管理アカウントの登録**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff5f-137">Click **Register new managed account**.</span></span>  
  
 <span data-ttu-id="aff5f-138">**SPSvc** アカウントにはローカル管理者権限はなく、SharePoint データベースに関する権限もありません。</span><span class="sxs-lookup"><span data-stu-id="aff5f-138">The **SPSvc** account has no local administrator privileges and SPsvc will not have any privileges in the SharePoint database.</span></span> <span data-ttu-id="aff5f-139">SPsvc に必要な唯一の特権は、Analysis Services の PowerPivot インスタンスの管理権限です。</span><span class="sxs-lookup"><span data-stu-id="aff5f-139">The only privileges SPsvc requires is administrative rights to the PowerPivot Instance of the Analysis Services.</span></span>  
  
 <span data-ttu-id="aff5f-140">**SPsvc アカウントを使用する適切なアプリケーション プールを構成するには**</span><span class="sxs-lookup"><span data-stu-id="aff5f-140">**To configure the appropriate application pool to use the SPsvc account :**</span></span>  
  
1.  <span data-ttu-id="aff5f-141">SharePoint サーバーの全体管理で、[**セキュリティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff5f-141">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="aff5f-142">[**サービスアカウントの構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff5f-142">Click **Configure Service Accounts**.</span></span>  
  
3.  <span data-ttu-id="aff5f-143">PowerPivot サービス アプリケーションで使用するサービス アプリケーション プールを選択します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-143">Select the service application pool used by the PowerPivot Service application.</span></span> <span data-ttu-id="aff5f-144">次に、SPSvc アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-144">Then select the SPSvc account.</span></span>  
  
 <span data-ttu-id="aff5f-145">**PowerShell で Web アプリケーションへのアクセス権を付与するには**</span><span class="sxs-lookup"><span data-stu-id="aff5f-145">**To Grant access to the web application with PowerShell:**</span></span>  
  
1.  <span data-ttu-id="aff5f-146">管理者特権を使用して、SharePoint 2013 管理シェルを実行します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-146">Run the SharePoint 2013 Management Shell with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="aff5f-147">次の PowerShell コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="aff5f-147">Run the following PowerShell code:</span></span>  
  
    ```powershell
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")
    ```  
