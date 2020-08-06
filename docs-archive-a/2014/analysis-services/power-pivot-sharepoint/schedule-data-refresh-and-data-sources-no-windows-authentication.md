---
title: データ更新と Windows 認証をサポートしていないデータソースをスケジュールする (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63e37dec6f334395c0c1812c6f76d750c16c53ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641282"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a><span data-ttu-id="55bcc-102">定期データ更新と Windows 認証をサポートしないデータ ソース (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="55bcc-102">Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="55bcc-103">このトピックでは、Windows 認証を**サポートしない**データ ソースを使用できる PowerPivot for SharePoint 定期データ更新のワークフローについて説明します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-103">This topic describes a workflow of PowerPivot for SharePoint schedule data fresh that can use data sources that do **NOT** support Windows Authentication.</span></span> <span data-ttu-id="55bcc-104">たとえば、Oracle データ ソースまたは IDM DB2 データ ソースが該当します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-104">For example Oracle or IDM DB2 data sources.</span></span> <span data-ttu-id="55bcc-105">このトピックにある図と手順では、Oracle データ ソースを参照していますが、他のデータ ソースにも同じワークフローが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="55bcc-105">The illustrations and steps in this topic reference Oracle data sources but the same workflow applies to other data sources.</span></span>  
  
||  
|-|  
|<span data-ttu-id="55bcc-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2010 &#124; SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="55bcc-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 &#124; SharePoint 2013.</span></span>|  
  
 <span data-ttu-id="55bcc-107">**概要:** 2 つの Secure Store ターゲット アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-107">**Overview:** Create two Secure Store Target Applications.</span></span> <span data-ttu-id="55bcc-108">1 つ目のターゲット アプリケーション (PowerPivotDataRefresh) を、Windows 資格情報を使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-108">Configure the first target application (PowerPivotDataRefresh) to use Windows credentials.</span></span> <span data-ttu-id="55bcc-109">2 つ目のターゲット アプリケーションを、Windows 認証をサポートしていないデータ ソース (Oracle データベースなど) の資格情報を使用して構成します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-109">Configure the second target application with the credentials for a data source that does not support windows authentication, for example, an Oracle database.</span></span> <span data-ttu-id="55bcc-110">さらに、2 つ目のターゲット アプリケーションでは、自動データ更新アカウントに 1 つ目のターゲット アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-110">The second target application also uses the first target application for the unattended data refresh account.</span></span>  
  
 <span data-ttu-id="55bcc-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span><span class="sxs-lookup"><span data-stu-id="55bcc-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span></span>  
  
-   <span data-ttu-id="55bcc-112">**(1) PowerPivotDatarefresh:** Windows 認証で設定される Secure Store ターゲット アプリケーション ID。</span><span class="sxs-lookup"><span data-stu-id="55bcc-112">**(1) PowerPivotDatarefresh:** A Secure Store Target Application ID that is set with windows authentication.</span></span>  
  
-   <span data-ttu-id="55bcc-113">**(2) OracleAuthentication:** Oracle 資格情報で設定される Secure Store ターゲット アプリケーション ID。</span><span class="sxs-lookup"><span data-stu-id="55bcc-113">**(2) OracleAuthentication:** A Secure Store Target Application ID that is set with Oracle credentials.</span></span>  
  
-   <span data-ttu-id="55bcc-114">**(3)** PowerPivot サービスアプリケーションは、**自動データ更新アカウント**にターゲットアプリケーション "PowerPivotDataRefresh" を使用するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="55bcc-114">**(3)** The PowerPivot Service application is configure to use the target application "PowerPivotDataRefresh" for the **Unattended Data Refresh Account**.</span></span>  
  
-   <span data-ttu-id="55bcc-115">**(4)** PowerPivot ブックでは Oracle データが使用されます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-115">**(4)** PowerePivot Workbook uses Oracle data.</span></span> <span data-ttu-id="55bcc-116">ブックの更新設定では、データ ソースへの接続で、資格情報にターゲット アプリケーション **(2)** を使用するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-116">The workbook refresh settings specify the data source connection to use the target application **(2)** for credentials.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="55bcc-117">前提条件</span><span class="sxs-lookup"><span data-stu-id="55bcc-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="55bcc-118">PowerPivot サービス アプリケーションがある。</span><span class="sxs-lookup"><span data-stu-id="55bcc-118">A PowerPivot Service Application exists.</span></span>  
  
-   <span data-ttu-id="55bcc-119">Secure Store Service アプリケーションがある。</span><span class="sxs-lookup"><span data-stu-id="55bcc-119">A Secure Store Service Application exists.</span></span>  
  
-   <span data-ttu-id="55bcc-120">PowerPivot データ モデルを含む Excel ブックがある。</span><span class="sxs-lookup"><span data-stu-id="55bcc-120">An Excel workbook with a PowerPivot data model exists.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a><span data-ttu-id="55bcc-121">Windows 認証を使用するターゲット アプリケーション ID を作成するには</span><span class="sxs-lookup"><span data-stu-id="55bcc-121">To Create a Target Application ID that uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="55bcc-122">SharePoint サーバーの全体管理で、[**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-122">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="55bcc-123">Secure Store Service アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-123">Click the name of your secure store service application.</span></span>  
  
3.  <span data-ttu-id="55bcc-124">**[管理]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-124">On the **Manage** page, click **New**.</span></span> <span data-ttu-id="55bcc-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span><span class="sxs-lookup"><span data-stu-id="55bcc-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span></span>  
  
4.  <span data-ttu-id="55bcc-126">**[Secure Store のターゲット アプリケーションを新規に作成します]** ページで、次の値を構成します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-126">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="55bcc-127">**ターゲット アプリケーション ID:** PowerPivotDataRefresh</span><span class="sxs-lookup"><span data-stu-id="55bcc-127">**Target Application ID:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="55bcc-128">**表示名:** PowerPivotDataRefresh</span><span class="sxs-lookup"><span data-stu-id="55bcc-128">**Display Name:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="55bcc-129">**連絡先の電子メール:** ?</span><span class="sxs-lookup"><span data-stu-id="55bcc-129">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="55bcc-130">**ターゲット アプリケーションの種類:** グループ</span><span class="sxs-lookup"><span data-stu-id="55bcc-130">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="55bcc-131">**ターゲット アプリケーション ページの URL:** なし</span><span class="sxs-lookup"><span data-stu-id="55bcc-131">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="55bcc-132">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-132">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="55bcc-133">[資格情報] ページで、 **[Windows ユーザー名]** と **[Windows パスワード]** の 2 つのフィールド名とフィールドの種類は既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-133">On the Credentials page, leave the two default field names and field types for **Windows User Name** and **Windows Password**.</span></span>  
  
7.  <span data-ttu-id="55bcc-134">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-134">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="55bcc-135">**[メンバーシップの設定]** ページで、 **[ターゲット アプリケーションの管理者]** に 1 人以上を追加し、ターゲット アプリケーションへのアクセスが必要なメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-135">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="55bcc-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-136">Click **OK**.</span></span>  
  
10. <span data-ttu-id="55bcc-137">新しいターゲット アプリケーション ID が一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-137">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="55bcc-138">ターゲットアプリケーション ID を選択し、[**資格情報の設定**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-138">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="55bcc-139">Windows ユーザー名と Windows パスワードを入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-139">Type the Windows User Name and Windows Password and then click **OK**.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a><span data-ttu-id="55bcc-140">Oracle 資格情報を使用するターゲット アプリケーション ID を作成するには</span><span class="sxs-lookup"><span data-stu-id="55bcc-140">To Create a Target Application ID that uses Oracle credentials</span></span>  
  
1.  <span data-ttu-id="55bcc-141">SharePoint サーバーの全体管理で、[**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-141">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="55bcc-142">Secure Store Service アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-142">Click the name of your Secure Store Service application.</span></span>  
  
3.  <span data-ttu-id="55bcc-143">[**管理**] ページで、[**新しい**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-143">On the **Manage** page, click **New**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application").</span></span>  
  
4.  <span data-ttu-id="55bcc-144">**[Secure Store のターゲット アプリケーションを新規に作成します]** ページで、次の値を構成します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-144">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="55bcc-145">**ターゲット アプリケーション ID:** OracleAuthentication</span><span class="sxs-lookup"><span data-stu-id="55bcc-145">**Target Application ID:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="55bcc-146">**表示名:** OracleAuthentication</span><span class="sxs-lookup"><span data-stu-id="55bcc-146">**Display Name:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="55bcc-147">**連絡先の電子メール:** ?</span><span class="sxs-lookup"><span data-stu-id="55bcc-147">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="55bcc-148">**ターゲット アプリケーションの種類:** グループ</span><span class="sxs-lookup"><span data-stu-id="55bcc-148">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="55bcc-149">**ターゲット アプリケーション ページの URL:** なし</span><span class="sxs-lookup"><span data-stu-id="55bcc-149">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="55bcc-150">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-150">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="55bcc-151">[**資格情報**] ページで、最初のフィールド名をに変更 `Oracle User ID` し、**フィールドの種類**をに変更し `User Name` ます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-151">On the **Credentials** page, change the first field name to `Oracle User ID` and change the **Field Type** to `User Name`.</span></span>  
  
     <span data-ttu-id="55bcc-152">2番目のフィールド名をに変更し、 `Oracle Password` **フィールドの種類**をに変更し `Password` ます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-152">Change the second field name to `Oracle Password` and the **Field Type** to `Password`.</span></span>  
  
7.  <span data-ttu-id="55bcc-153">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-153">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="55bcc-154">**[メンバーシップの設定]** ページで、 **[ターゲット アプリケーションの管理者]** に 1 人以上を追加し、ターゲット アプリケーションへのアクセスが必要なメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-154">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="55bcc-155">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-155">Click **OK**.</span></span>  
  
10. <span data-ttu-id="55bcc-156">新しいターゲット アプリケーション ID が一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-156">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="55bcc-157">ターゲットアプリケーション ID を選択し、[**資格情報の設定**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-157">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="55bcc-158">Oracle ユーザー ID と Oracle パスワードを入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-158">Type the Oracle User ID and Oracle Password and then click **OK**.</span></span>  
  
 <span data-ttu-id="55bcc-159">詳細については、「 [SQL Server 認証での Secure Store の使用 (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) 」の「SQL Server 認証用のターゲットアプリケーションを作成するには」を参照してください https://technet.microsoft.com/library/gg298949.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="55bcc-159">For more information, see section "To Create a target application for SQL Server Authentication" in [Use Secure Store with SQL Server Authentication (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) (https://technet.microsoft.com/library/gg298949.aspx).</span></span>  
  
## <a name="to-configure-the-powerpivot-service-application"></a><span data-ttu-id="55bcc-160">PowerPivot サービス アプリケーションを構成するには</span><span class="sxs-lookup"><span data-stu-id="55bcc-160">To Configure the PowerPivot Service Application</span></span>  
  
1.  <span data-ttu-id="55bcc-161">SharePoint サーバーの全体管理で [サービス アプリケーションの管理] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-161">In SharePoint central administration, click Manage Service Applications.</span></span>  
  
2.  <span data-ttu-id="55bcc-162">PowerPivot サービスアプリケーションの名前 ("既定の PowerPivot サービスアプリケーション" など) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-162">Click the name of your PowerPivot Service Application, for example "Default PowerPivot Service Application".</span></span>  
  
3.  <span data-ttu-id="55bcc-163">[アクション] で **[サービス アプリケーションの設定の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-163">Click **Configure service application settings** in the Actions section.</span></span>  
  
4.  <span data-ttu-id="55bcc-164">[**データ更新**] セクションで、 **PowerPivot 自動データ更新アカウント**をに設定し、 `PowerPivotDataRefresh` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-164">In the **Data Refresh** section, set the **PowerPivot Unattended Data Refresh Account**to`PowerPivotDataRefresh` and then click **OK**.</span></span>  
  
     <span data-ttu-id="55bcc-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span><span class="sxs-lookup"><span data-stu-id="55bcc-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span></span>  
  
## <a name="to-configure-the-workbook"></a><span data-ttu-id="55bcc-166">ブックを構成するには</span><span class="sxs-lookup"><span data-stu-id="55bcc-166">To configure the workbook</span></span>  
  
1.  <span data-ttu-id="55bcc-167">PowerPivot ギャラリーでブックを参照し、[**データ更新の管理**]![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh")をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-167">Browse to your workbook in the PowerPivot Gallery and click **Manage Data Refresh**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").</span></span>  
  
2.  <span data-ttu-id="55bcc-168">**[データ更新の履歴]** ページが表示されたら、 **[スケジュールの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-168">If you see the **Data Refresh History** page, click **Configure Schedule**.</span></span>  
  
3.  <span data-ttu-id="55bcc-169">**[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-169">Click **Enable**.</span></span>  
  
4.  <span data-ttu-id="55bcc-170">**[さらに、できるだけ早く更新を行います]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-170">Click **Also Refresh as soon as possible**.</span></span>  
  
5.  <span data-ttu-id="55bcc-171">**[資格情報]** で、 **[管理者によって構成されたデータ更新アカウントを使用します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-171">In the **Credentials** section, click **Use the Data refresh account configured by the administrator**.</span></span>  
  
6.  <span data-ttu-id="55bcc-172">**[すべてのデータ ソース]** をクリアします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-172">Clear **All data sources**.</span></span>  
  
7.  <span data-ttu-id="55bcc-173">Oracle データを使用するデータ ソースに対して **[最新の情報に更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-173">Select **Refresh** for the data source that uses the Oracle data.</span></span> <span data-ttu-id="55bcc-174">データ ソース名は、Microsoft Excel で、 **[データ]** タブの **[接続]** で **[プロパティ]** をクリックすると変更できます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-174">The name of the data source name can be changed in Microsoft Excel in the **Data**, **Connections**, **Properties** menu.</span></span>  
  
8.  <span data-ttu-id="55bcc-175">お使いのデータベース ソースで **[既定のスケジュールを使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-175">Under your data source, Select **Use Default Schedule**.</span></span>  
  
9. <span data-ttu-id="55bcc-176">**[Secure Store Service (SSS) に保存された資格情報を使用してデータ ソースにログオンします。資格情報を参照するための ID を SSS ID ボックスに入力してください]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-176">Select **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source. Enter the ID used to look up the credentials in the SSS ID box**.</span></span>  
  
10. <span data-ttu-id="55bcc-177">[ **ID:** ] ボックスに、「」と入力 `OracleAuthentication` します。</span><span class="sxs-lookup"><span data-stu-id="55bcc-177">In the **ID:** box, type `OracleAuthentication`.</span></span>  
  
11. <span data-ttu-id="55bcc-178">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55bcc-178">Click **OK**.</span></span>  
  
     <span data-ttu-id="55bcc-179">" `The provided Secure Store target application is either incorrectly configured or does not exist`" のようなエラー メッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="55bcc-179">If you see an error message similar to: `The provided Secure Store target application is either incorrectly configured or does not exist`.</span></span>  
  
     <span data-ttu-id="55bcc-180">一般的な解決方法として、次の 2 つが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-180">The two common solutions are:</span></span>  
  
    -   <span data-ttu-id="55bcc-181">ターゲット アプリケーション ID が正しいことを確認する。</span><span class="sxs-lookup"><span data-stu-id="55bcc-181">Verify that the Target Application ID is correct.</span></span>  
  
    -   <span data-ttu-id="55bcc-182">ターゲット アプリケーションの資格情報を設定したことを確認する。</span><span class="sxs-lookup"><span data-stu-id="55bcc-182">Verify that you set credentials for the Target Application.</span></span>  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a><span data-ttu-id="55bcc-183">新しい認証を使用したデータ更新を確認するには</span><span class="sxs-lookup"><span data-stu-id="55bcc-183">To Verify Data Refresh with the new authentication</span></span>  
 <span data-ttu-id="55bcc-184">**[OK]** をクリックすると、 **[更新の履歴]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-184">When you click **ok**, you see the **Refresh History** page.</span></span> <span data-ttu-id="55bcc-185">前の手順で **[さらに、できるだけ早く更新を行います]** を選択したため、数分以内に、新しい項目が更新の履歴に表示されます。</span><span class="sxs-lookup"><span data-stu-id="55bcc-185">Within a few minutes, you should see a new item in the refresh history because in the previous steps you selected **Also Refresh as soon as possible**.</span></span> <span data-ttu-id="55bcc-186">タイマー ジョブ "**PowerPivot データ更新タイマー ジョブ**" の既定値は 1 分です。</span><span class="sxs-lookup"><span data-stu-id="55bcc-186">The default value for the timer job **PowerPivot Data Refresh Timer Job** is 1 minute.</span></span> <span data-ttu-id="55bcc-187">履歴の更新に新しい項目が表示されない場合は、しばらく待ってから、ブラウザーを更新してください。</span><span class="sxs-lookup"><span data-stu-id="55bcc-187">If you do not see a new item in the refresh history, wait a few minutes and refresh your browser.</span></span> <span data-ttu-id="55bcc-188">それでも新しい項目が表示されない場合は、タイマー ジョブの現在の値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="55bcc-188">If you still do not see the new item, verify the current value of the timer job.</span></span>  
  
## <a name="more-information"></a><span data-ttu-id="55bcc-189">説明</span><span class="sxs-lookup"><span data-stu-id="55bcc-189">More Information</span></span>  
  
-   <span data-ttu-id="55bcc-190">[SharePoint 2013 で Secure Store Service を構成する](https://technet.microsoft.com/library/ee806866.aspx)。</span><span class="sxs-lookup"><span data-stu-id="55bcc-190">[Configure the Secure Store Service in SharePoint 2013](https://technet.microsoft.com/library/ee806866.aspx).</span></span>  
  
-   <span data-ttu-id="55bcc-191">「 [SharePoint 2013 での PowerPivot データ更新」と「SQL Server 2012 SP1」 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh)の「定期データ更新」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="55bcc-191">See the "Scheduled Data Refresh" section of [PowerPivot Data Refresh with SharePoint 2013 and SQL Server 2012 SP1 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh).</span></span>  
  
  
