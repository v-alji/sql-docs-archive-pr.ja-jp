---
title: SharePoint サービスアプリケーション Reporting Services のバックアップと復元 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dfb4ed77-90e5-4273-b690-89a945508ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488659d269542381be9bcf1b1b6115acf89f8a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640777"
---
# <a name="backup-and-restore-reporting-services-sharepoint-service-applications"></a><span data-ttu-id="90909-102">Reporting Services SharePoint サービス アプリケーションのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="90909-102">Backup and Restore Reporting Services SharePoint Service Applications</span></span>
  <span data-ttu-id="90909-103">このトピックでは、SharePoint サーバーの全体管理または PowerShell を使用して、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションをバックアップおよび復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90909-103">This topic describes how to backup and restore a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services application using SharePoint Central Administration or PowerShell.</span></span> <span data-ttu-id="90909-104">このトピックの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="90909-104">The topic contains:</span></span>  
  
-   [<span data-ttu-id="90909-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="90909-105">Limitations and Restrictions</span></span>](#bkmk_Restrictions)  
  
-   [<span data-ttu-id="90909-106">サービスアプリケーションのバックアップ</span><span class="sxs-lookup"><span data-stu-id="90909-106">Backup The Service application</span></span>](#bkmk_backup)  
  
-   [<span data-ttu-id="90909-107">サービス アプリケーションの復元</span><span class="sxs-lookup"><span data-stu-id="90909-107">Restore the Service Application</span></span>](#bkmk_restore)  
  
##  <a name="before-you-begin"></a><a name="bkmk_BeforeYouBegin"></a> <span data-ttu-id="90909-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="90909-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="bkmk_Restrictions"></a> <span data-ttu-id="90909-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="90909-109">Limitations and Restrictions</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="90909-110">サービス アプリケーションは、SharePoint のバックアップおよび復元機能を使用して、部分的にバックアップおよび復元できます。</span><span class="sxs-lookup"><span data-stu-id="90909-110">service applications can partially be backed up and restored using the SharePoint backup and restore functionality.</span></span> <span data-ttu-id="90909-111">これには**追加の手順が必要** であり、その手順はこのトピック内に記載されています。</span><span class="sxs-lookup"><span data-stu-id="90909-111">**Additional steps are required** and the steps are documented in this topic.</span></span> <span data-ttu-id="90909-112">現在、バックアップ プロセスでは、自動実行アカウント (UEA) または Windows 認証用の暗号化キーと資格情報は **データベースにバックアップ** されません [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="90909-112">Currently the backup process **does not** backup encryption keys and credentials for unattended execution accounts (UEA) or windows authentication to the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] database.</span></span>  
  
###  <a name="recommendations"></a><a name="bkmk_recommendations"></a> <span data-ttu-id="90909-113">推奨事項</span><span class="sxs-lookup"><span data-stu-id="90909-113">Recommendations</span></span>  
  
-   <span data-ttu-id="90909-114">SharePoint のバックアップを開始する前に、暗号化キーをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="90909-114">Backup the encryption keys before starting the SharePoint backup.</span></span> <span data-ttu-id="90909-115">暗号化キーをバックアップしなかった場合は、サービス アプリケーションの復元後に、暗号化されたデータへアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="90909-115">If you do not backup the encryption keys, then you will not be able to access your encrypted data, following the restore of the service application.</span></span> <span data-ttu-id="90909-116">その場合、暗号化されたデータを削除する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="90909-116">You will need to delete your encrypted data.</span></span>  
  
-   <span data-ttu-id="90909-117">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションがデータベースへのアクセス用に UEA または Windows 認証を使用しているかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90909-117">Verify if your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application is using UEA or Windows authentication for database access.</span></span> <span data-ttu-id="90909-118">これらのいずれかを使用している場合は、復元プロセス後にサービス アプリケーションを正しく構成できるよう、適切な資格情報を確認してください。</span><span class="sxs-lookup"><span data-stu-id="90909-118">If it is using either, verify what the proper credentials are so you can correctly configure the service application after the restore process.</span></span>  
  
-   <span data-ttu-id="90909-119">SharePoint のバックアップ ログが、バックアップ ファイルと同じフォルダーに作成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90909-119">Review the SharePoint backup log is created in the same folder as the backup file.</span></span> <span data-ttu-id="90909-120">このファイルは通常、 **spbackup.log**という名前になります。</span><span class="sxs-lookup"><span data-stu-id="90909-120">The file is typically named **spbackup.log**</span></span>  
  
##  <a name="backup-the-service-application"></a><a name="bkmk_backup"></a> <span data-ttu-id="90909-121">サービス アプリケーションのバックアップ</span><span class="sxs-lookup"><span data-stu-id="90909-121">Backup The Service application</span></span>  
 <span data-ttu-id="90909-122">次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90909-122">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="90909-123">暗号化キーをバックアップします</span><span class="sxs-lookup"><span data-stu-id="90909-123">Backup the encryption keys</span></span>  
  
2.  <span data-ttu-id="90909-124">サービス アプリケーションのバックアップ</span><span class="sxs-lookup"><span data-stu-id="90909-124">Backup the Service application</span></span>  
  
3.  <span data-ttu-id="90909-125">サービス アプリケーションがデータベースへのアクセス用に UEA または Windows 認証を使用しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="90909-125">Verify if you service application uses an UEA or Windows authentication for database access.</span></span> <span data-ttu-id="90909-126">使用している場合は、復元後にサービス アプリケーションを正しく構成できるよう、必要な資格情報をメモします。</span><span class="sxs-lookup"><span data-stu-id="90909-126">If it does, make a note of the credentials so you can use them to configure the service application after it is restored.</span></span>  
  
### <a name="backup-the-encryption-keys-using-central-administration"></a><span data-ttu-id="90909-127">サーバーの全体管理を使用して暗号化キーをバックアップする</span><span class="sxs-lookup"><span data-stu-id="90909-127">Backup the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="90909-128">暗号化キーのバックアップの詳細につい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ては、「 [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)」の「暗号化キー」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90909-128">For information on backing up the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
###  <a name="backup-the-service-application-using-sharepoint-central-administration"></a><a name="bkmk_centraladmin"></a><span data-ttu-id="90909-129">SharePoint サーバーの全体管理を使用してサービスアプリケーションをバックアップする</span><span class="sxs-lookup"><span data-stu-id="90909-129">Backup the Service application Using SharePoint Central Administration</span></span>  
 <span data-ttu-id="90909-130">サービス アプリケーションをバックアップするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90909-130">To back up the Service Application, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="90909-131">SharePoint サーバーの全体管理で、 **[バックアップおよび復元]** グループの **[バックアップの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-131">In SharePoint Central Administration Click **Perform a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="90909-132">**[共有サービス]** ノードで、 **[共有サービス アプリケーション]** を展開し、サービス アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="90909-132">Under the **Shared Services** node, expand **Shared Service Applications** and select your service application.</span></span> <span data-ttu-id="90909-133">種類は **[SQL Server Reporting Services サービス アプリケーション]** になります。</span><span class="sxs-lookup"><span data-stu-id="90909-133">It will have a type of **SQL Server Reporting Services Service Application**.</span></span>  
  
3.  <span data-ttu-id="90909-134">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="90909-135">**[バックアップの場所]** にパスを入力し、 **[バックアップの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-135">Type the path for the **Backup location:** and click **Start Backup**</span></span>  
  
5.  <span data-ttu-id="90909-136">上記のプロセスを繰り返します。ただし、サービス アプリケーションを選択する代わりに、 **[共有サービス プロキシ]** ノードを展開し、サービス アプリケーション プロキシを選択します。</span><span class="sxs-lookup"><span data-stu-id="90909-136">Repeat the process above but instead of selecting the service application, expand the **Shared Services Proxies** node, and select service application proxy.</span></span> <span data-ttu-id="90909-137">種類は **[SQL Server Reporting Services サービス アプリケーション プロキシ]** になります。</span><span class="sxs-lookup"><span data-stu-id="90909-137">It will have a type of **SQL Server Reporting Services Service Application Proxy**.</span></span>  
  
 <span data-ttu-id="90909-138">詳細については、 SharePoint のドキュメントの次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90909-138">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="90909-139">[サービス アプリケーションのバックアップ (SharePoint Foundation 2010) (SharePoint ドキュメント)](https://msdn.microsoft.com/library/ee748601.aspx)。</span><span class="sxs-lookup"><span data-stu-id="90909-139">[Back up a service application (SharePoint Foundation 2010) in the SharePoint documenttation](https://msdn.microsoft.com/library/ee748601.aspx).</span></span>  
  
 [<span data-ttu-id="90909-140">サービス アプリケーションのバックアップ (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="90909-140">Back up a service application (SharePoint Server 2010)</span></span>](https://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a><span data-ttu-id="90909-141">実行アカウントとデータベース認証の確認</span><span class="sxs-lookup"><span data-stu-id="90909-141">Verify Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="90909-142">**実行アカウント** : サービス アプリケーションが実行アカウントを使用しているかどうかを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90909-142">**Execution Account:** To verify if your service application is using an execution account:</span></span>  
  
1.  <span data-ttu-id="90909-143">SharePoint サーバーの全体管理で、[**アプリケーション管理**] グループの [**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-143">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="90909-144">サービスアプリケーションの名前をクリックし、SharePoint リボンの [**管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-144">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="90909-145">**[実行アカウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-145">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="90909-146">実行アカウントが構成されている場合は、サービス アプリケーションのバックアップを復元する際に資格情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="90909-146">If an execution account is configured, you need to know the credentials when it is time to restore the service application backup.</span></span> <span data-ttu-id="90909-147">必ず、正しい資格情報を確認してからバックアップおよび復元の手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="90909-147">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
 <span data-ttu-id="90909-148">**データベース認証** : サービス アプリケーションがデータベース認証用に Windows 認証を使用しているかどうかを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90909-148">**Database Authentication:** To verify if your service application is using Windows Authentication for the database authentication:</span></span>  
  
1.  <span data-ttu-id="90909-149">SharePoint サーバーの全体管理で、[**アプリケーション管理**] グループの [**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-149">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="90909-150">サービス アプリケーションの名前をクリックし、SharePoint リボンで **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-150">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="90909-151">**[Reporting Services (SSRS) サービス データベース]** セクションの内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="90909-151">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="90909-152">Windows 認証が構成されている場合は、サービス アプリケーションを復元後に構成する際、資格情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="90909-152">If Windows Authentication is configured, you need to know the credentials so you can configure the service application after you restore it.</span></span> <span data-ttu-id="90909-153">必ず、正しい資格情報を確認してからバックアップおよび復元の手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="90909-153">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
##  <a name="restore-the-service-application"></a><a name="bkmk_restore"></a><span data-ttu-id="90909-154">サービスアプリケーションを復元する</span><span class="sxs-lookup"><span data-stu-id="90909-154">Restore the Service Application</span></span>  
 <span data-ttu-id="90909-155">次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90909-155">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="90909-156">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションを復元します。</span><span class="sxs-lookup"><span data-stu-id="90909-156">Restore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="90909-157">暗号化キーを復元します。</span><span class="sxs-lookup"><span data-stu-id="90909-157">Restore the encryption keys</span></span>  
  
3.  <span data-ttu-id="90909-158">サービス アプリケーションがデータベースへのアクセス用に実行アカウントまたは Windows 認証を使用していた場合は、資格情報を構成します。</span><span class="sxs-lookup"><span data-stu-id="90909-158">If your service application was using an execution account or Windows authentication for database access, configure the credentials.</span></span>  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a><span data-ttu-id="90909-159">SharePoint サーバーの全体管理を使用してサービス アプリケーションを復元する</span><span class="sxs-lookup"><span data-stu-id="90909-159">Restore the Service application Using SharePoint Central Administration</span></span>  
  
1.  <span data-ttu-id="90909-160">SharePoint サーバーの全体管理で、 **[バックアップおよび復元]** グループの **[バックアップからの復元を実行する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-160">In SharePoint Central Administration Click **Restore from a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="90909-161">**[バックアップ ディレクトリの場所]** ボックスにバックアップ ファイルのパスを入力し、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-161">Type the path to your backup file in **Backup Directory Location** box and click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="90909-162">**[トップ コンポーネント]** ボックスの一覧からサービス アプリケーションのバックアップを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-162">Select your service application backup from the **Top Component** list and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="90909-163">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アプリケーションを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-163">Select your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="90909-164">**[ログイン名とパスワード]** セクションで、ログイン名のパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="90909-164">In the **Login Names and Passwords** section type the password for the login name.</span></span> <span data-ttu-id="90909-165">ログイン名ボックスには、サービス アプリケーションがバックアップ以前に使用していたログインが自動入力されます。</span><span class="sxs-lookup"><span data-stu-id="90909-165">The login name box should be populated with the login the service application was using prior to the backup.</span></span>  
  
6.  <span data-ttu-id="90909-166">**[復元の開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-166">Click **Start Restore**.</span></span>  
  
7.  <span data-ttu-id="90909-167">上記のプロセスを繰り返します。ただし、サービス アプリケーションを復元する代わりに、 **[共有サービス]** ノードを展開し、 **[共有サービス アプリケーション]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="90909-167">Repeat the process above but instead of restoring the service application, expand the **Shared Services** node and then expand the **Shared Service Applications** node.</span></span>  
  
 <span data-ttu-id="90909-168">詳細については、 SharePoint のドキュメントの次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90909-168">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="90909-169">[サービス アプリケーションを復元する (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx)。</span><span class="sxs-lookup"><span data-stu-id="90909-169">[Restore a service application (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx).</span></span>  
  
 <span data-ttu-id="90909-170">[サービス アプリケーションを復元する (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx)。</span><span class="sxs-lookup"><span data-stu-id="90909-170">[Restore a service application (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx).</span></span>  
  
### <a name="restore-the-encryption-keys-using-central-administration"></a><span data-ttu-id="90909-171">サーバーの全体管理を使用して暗号化キーを復元する</span><span class="sxs-lookup"><span data-stu-id="90909-171">Restore the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="90909-172">暗号化キーの復元の詳細につい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ては、「 [Reporting Services SharePoint サービスアプリケーションの管理](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)」の「暗号化キー」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90909-172">For information on restoring the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
### <a name="configure-the-execution-account-and-database-authentication"></a><span data-ttu-id="90909-173">実行アカウントとデータベース認証の構成</span><span class="sxs-lookup"><span data-stu-id="90909-173">Configure the Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="90909-174">**実行アカウント** : サービス アプリケーションが実行アカウントを使用していた場合は、次の手順を実行して実行アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="90909-174">**Execution Account:** If your service application was using an execution account complete the following steps to configure it:</span></span>  
  
1.  <span data-ttu-id="90909-175">SharePoint サーバーの全体管理で、[**アプリケーション管理**] グループの [**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-175">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="90909-176">サービスアプリケーションの名前をクリックし、SharePoint リボンの [**管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-176">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="90909-177">**[実行アカウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-177">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="90909-178">アカウントとパスワードを入力し、 **[実行アカウントの指定]** ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="90909-178">Type the account, password, and select the **Specify and Execution Account** box.</span></span>  
  
5.  <span data-ttu-id="90909-179">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-179">Click **OK**.</span></span>  
  
 <span data-ttu-id="90909-180">**データベース認証** : サービス アプリケーションがデータベース認証用に Windows 認証を使用していた場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90909-180">**Database Authentication:** If your service application was using Windows Authentication for the database authentication complete the following steps:</span></span>  
  
1.  <span data-ttu-id="90909-181">SharePoint サーバーの全体管理で、[**アプリケーション管理**] グループの [**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-181">In SharePoint Central Administration click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="90909-182">サービス アプリケーションの名前をクリックし、SharePoint リボンで **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-182">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="90909-183">**[Reporting Services (SSRS) サービス データベース]** セクションの内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="90909-183">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="90909-184">**[Windows 認証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-184">Select **Windows Authentication**.</span></span>  
  
5.  <span data-ttu-id="90909-185">アカウントとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="90909-185">Type the account and password.</span></span> <span data-ttu-id="90909-186">必要に応じて、 **[Windows 資格情報として使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90909-186">Select **Use as Windows Credentials** if appropriate.</span></span>  
  
6.  <span data-ttu-id="90909-187">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90909-187">Click **Ok**</span></span>  
  
  
