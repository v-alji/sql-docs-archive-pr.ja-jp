---
title: SharePoint サービスとサービスアプリケーションの Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5654764f7913002cdae58d3264848250a292c585
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646022"
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a><span data-ttu-id="1e820-102">Reporting Services の SharePoint サービスとサービス アプリケーション</span><span class="sxs-lookup"><span data-stu-id="1e820-102">Reporting Services SharePoint Service and Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="1e820-103">SharePoint モードは、SharePoint サービス アーキテクチャ上に構築されており、SharePoint サービスと一対多のサービス アプリケーションを利用します。</span><span class="sxs-lookup"><span data-stu-id="1e820-103">SharePoint mode is architected on the SharePoint service architecture and utilizes a SharePoint service and one to many service applications.</span></span> <span data-ttu-id="1e820-104">サービス アプリケーションを作成すると、サービスが使用可能になり、サービス アプリケーション データベースが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1e820-104">Creating a service application makes the service available and generates the service application database.</span></span> <span data-ttu-id="1e820-105">複数の Reporting Services サービス アプリケーションを作成することができますが、ほとんどの配置シナリオではサービス アプリケーションは 1 つで十分です。</span><span class="sxs-lookup"><span data-stu-id="1e820-105">You can create multiple Reporting Services service applications but one service application is sufficient for most deployment scenarios.</span></span>  
  
 <span data-ttu-id="1e820-106">このトピックの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1e820-106">This topic covers the following information:</span></span>  
  
-   [<span data-ttu-id="1e820-107">Reporting Services サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="1e820-107">Creating a Reporting Services Service Application</span></span>](#bkmk_createapp)  
  
-   [<span data-ttu-id="1e820-108">プロキシ グループを使用したサービス アプリケーションの関連付けの変更</span><span class="sxs-lookup"><span data-stu-id="1e820-108">Modify the Associations of the Service Application with a proxy group</span></span>](#bkmk_associations)  
  
-   [<span data-ttu-id="1e820-109">サービスアプリケーションのプロパティの編集</span><span class="sxs-lookup"><span data-stu-id="1e820-109">Edit Service Application Properties</span></span>](#bkmk_editserviceapplication)  
  
-   [<span data-ttu-id="1e820-110">PowerShell を使用して Reporting Services サービス アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="1e820-110">To create a Reporting Services Service Application using PowerShell</span></span>](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [<span data-ttu-id="1e820-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1e820-111">Related Tasks</span></span>](#bkmk_related)  
  
##  <a name="creating-a-reporting-services-service-application"></a><a name="bkmk_createapp"></a><span data-ttu-id="1e820-112">Reporting Services サービスアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="1e820-112">Creating a Reporting Services Service Application</span></span>  
 <span data-ttu-id="1e820-113">SharePoint サーバーの全体管理または PowerShell スクリプトを使用して、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1e820-113">You can use SharePoint Central Administration or PowerShell scripts to create the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services applications.</span></span> <span data-ttu-id="1e820-114">SharePoint サーバーの全体管理を使用する方法の詳細については、「[SharePoint 2010 用 Reporting Services の SharePoint モードのインストール](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」の「Reporting Services サービス アプリケーションの作成」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e820-114">For more information on using SharePoint Central Administration, see the "Create a Reporting Services Service Application" section in [Install Reporting Services SharePoint Mode for SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span> <span data-ttu-id="1e820-115">サービス アプリケーションを作成するための PowerShell スクリプトの例は、このトピックの後半の PowerShell のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e820-115">See the PowerShell section later in this topic for a sample PowerShell script for creating service applications.</span></span>  
  
##  <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a><a name="bkmk_associations"></a><span data-ttu-id="1e820-116">プロキシグループを使用したサービスアプリケーションの関連付けの変更</span><span class="sxs-lookup"><span data-stu-id="1e820-116">Modify the Associations of the Service Application with a proxy group</span></span>  
 <span data-ttu-id="1e820-117">サービス アプリケーションを作成するための [新規作成] ページには、 **[Web アプリケーションの関連付け]** セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="1e820-117">The New page for creating a services application contains the section **Web Application Association**.</span></span> <span data-ttu-id="1e820-118">このセクションでは、サービス アプリケーションの作成時に関連付けを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1e820-118">The section allows you to associate your service application as you create it.</span></span> <span data-ttu-id="1e820-119">関連付けを変更してカスタム構成をサービス アプリケーションに割り当てるには、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="1e820-119">Use the following steps to change the association and assign a customer configuration to the service application.</span></span> <span data-ttu-id="1e820-120">同じ一般的なプロセスは、サービス アプリケーションとカスタム グループとの関連付けを変更せずに、プロキシを既定のグループに追加する場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e820-120">The same general process can also be used to add the proxy to the default group rather than changing the association of the service application to a custom group.</span></span>  
  
1.  <span data-ttu-id="1e820-121">SharePoint サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの関連付けの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e820-121">In SharePoint Central Administration, in the Application Management, click **Configure Service Application Associations**.</span></span>  
  
2.  <span data-ttu-id="1e820-122">[サービス アプリケーションの関連付け] ページで、ビューを **[サービス アプリケーション]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e820-122">On the Service application Associations page, change the view to **Service Applications**.</span></span>  
  
3.  <span data-ttu-id="1e820-123">新しい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前を探してクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e820-123">Find and click the name of your new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Service application.</span></span> <span data-ttu-id="1e820-124">アプリケーション プロキシ グループ名 **[既定]** をクリックして、次の手順を完了せずに、プロキシを既定のグループに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="1e820-124">You could also click the application proxy group name **default** to add the proxy to default group rather than completing the following steps.</span></span>  
  
4.  <span data-ttu-id="1e820-125">**[編集する接続グループ]** 選択ボックスで、 **[カスタム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e820-125">Select **Custom** in the selection box **Edit the following group of connections**.</span></span>  
  
5.  <span data-ttu-id="1e820-126">プロキシのチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e820-126">Check the box for your proxy and click **Ok**.</span></span>  
  
##  <a name="edit-service-application-properties"></a><a name="bkmk_editserviceapplication"></a> <span data-ttu-id="1e820-127">サービス アプリケーションのプロパティの編集</span><span class="sxs-lookup"><span data-stu-id="1e820-127">Edit Service Application Properties</span></span>  
 <span data-ttu-id="1e820-128">サービス アプリケーションのプロパティ ページを開き直してプロパティを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="1e820-128">You can reopen the property page of the service application to modify the properties.</span></span>  
  
1.  <span data-ttu-id="1e820-129">SharePoint サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e820-129">In SharePoint Central Administration, in the Application Management group, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="1e820-130">サービス アプリケーションを選択するには、型列をクリックして行全体を選択します。</span><span class="sxs-lookup"><span data-stu-id="1e820-130">Select the service application by clicking the type column to select the entire row.</span></span> <span data-ttu-id="1e820-131">アプリケーションの名前をクリックすると、サービス アプリケーションのプロパティが開く代わりに、サービスの管理オプション ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="1e820-131">If you click the name of the application it, the Management options page for the service opens instead of opening the properties of the service application.</span></span>  
  
3.  <span data-ttu-id="1e820-132">[サービス アプリケーション] リボンで、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e820-132">In the Service Applications ribbon, click **Properties**.</span></span>  
  
##  <a name="to-create-a-reporting-services-service-application-using-powershell"></a><a name="bkmk_powershell_create_ssrs_serviceapp"></a><span data-ttu-id="1e820-133">PowerShell を使用して Reporting Services サービスアプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="1e820-133">To create a Reporting Services Service Application using PowerShell</span></span>  
 <span data-ttu-id="1e820-134">PowerShell を使用して Service アプリケーションとプロキシを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1e820-134">You can use PowerShell to create the Service application and proxy.</span></span> <span data-ttu-id="1e820-135">次のサンプルでは、使用するサービス アプリケーションをどのアプリケーション プールに構成するかがわかっていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="1e820-135">The sample below assumes that you know what application pool you want to configure the service application to use.</span></span>  
  
1.  <span data-ttu-id="1e820-136">アプリケーション プール名のアプリケーション プール オブジェクトを、New アクションに渡される変数に追加します。</span><span class="sxs-lookup"><span data-stu-id="1e820-136">Add the application pool object of your application pool name to a variable that is passed into the New action.</span></span>  
  
    ```powershell
    $appPoolName = Get-SPServiceApplicationPool "<application pool name>"  
    ```  
  
2.  <span data-ttu-id="1e820-137">指定した名前とアプリケーション プール名を使用してサービス アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e820-137">Create the service application with a name and application pool name you provide.</span></span>  
  
    ```powershell
    New-SPRSServiceApplication -Name 'MyServiceApplication' -ApplicationPool $appPoolName -DatabaseName 'MyServiceApplicationDatabase' -DatabaseServer '<Server Name>'  
    ```  
  
3.  <span data-ttu-id="1e820-138">新しいサービス アプリケーション オブジェクトを取得し、新しいプロキシ コマンドレットにオブジェクトをパイプします。</span><span class="sxs-lookup"><span data-stu-id="1e820-138">Get the new service application object, and pipe the object into the Pipe the new proxy cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication -name MyServiceApplication | New-SPRSServiceApplicationProxy "MyServiceApplicationProxy"  
    ```  
  
##  <a name="related-tasks"></a><a name="bkmk_related"></a> <span data-ttu-id="1e820-139">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1e820-139">Related Tasks</span></span>  
  
|<span data-ttu-id="1e820-140">タスク</span><span class="sxs-lookup"><span data-stu-id="1e820-140">Task</span></span>|<span data-ttu-id="1e820-141">Link</span><span class="sxs-lookup"><span data-stu-id="1e820-141">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="1e820-142">サービス アプリケーションの設定を管理する</span><span class="sxs-lookup"><span data-stu-id="1e820-142">Manage the settings of your Service Application.</span></span>|[<span data-ttu-id="1e820-143">Reporting Services SharePoint サービスアプリケーションの管理</span><span class="sxs-lookup"><span data-stu-id="1e820-143">Manage a Reporting Services SharePoint Service Application</span></span>](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)|  
|<span data-ttu-id="1e820-144">サービス アプリケーションと関連コンポーネント (暗号化キーやプロキシなど) をバックアップおよび復元する</span><span class="sxs-lookup"><span data-stu-id="1e820-144">Backup and restore the service application and related components such as encryption keys and proxy.</span></span>|[<span data-ttu-id="1e820-145">Reporting Services SharePoint サービス アプリケーションのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="1e820-145">Backup and Restore Reporting Services SharePoint Service Applications</span></span>](../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
