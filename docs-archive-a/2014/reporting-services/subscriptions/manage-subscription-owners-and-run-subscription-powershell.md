---
title: PowerShell を使用して Reporting Services サブスクリプションの所有者を変更および一覧表示し、サブスクリプションを実行する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0fa6cb36-68fc-4fb8-b1dc-ae4f12bf6ff0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b274dc190d8830a2cf7b55110f15267a00c581e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641429"
---
# <a name="use-powershell-to-change-and-list-reporting-services-subscription-owners-and-run-a-subscription"></a><span data-ttu-id="14095-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a subscription</span><span class="sxs-lookup"><span data-stu-id="14095-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription</span></span>
  <span data-ttu-id="14095-103">[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 以降では、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サブスクリプションの所有権をプログラムによってユーザー間で譲渡できます。</span><span class="sxs-lookup"><span data-stu-id="14095-103">Starting with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] you can programmatically transfer the ownership of a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription from one user to another.</span></span> <span data-ttu-id="14095-104">このトピックでは、サブスクリプションの所有権を変更または単純に一覧表示するために使用可能な、いくつかの Windows PowerShell スクリプトを説明します。</span><span class="sxs-lookup"><span data-stu-id="14095-104">This topic provides several Windows PowerShell scripts you can use to change or simply list subscription ownership.</span></span> <span data-ttu-id="14095-105">各サンプルには、ネイティブ モードと SharePoint モードの両方のサンプル構文が含まれています。</span><span class="sxs-lookup"><span data-stu-id="14095-105">Each sample includes sample syntax for both Native mode and SharePoint mode.</span></span> <span data-ttu-id="14095-106">サブスクリプションの所有者を変更した後で、サブスクリプションは新しい所有者のセキュリティ コンテキストで実行され、レポート内の User!UserID フィールドには新しい所有者の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="14095-106">After you change the subscription owner, the subscription will then execute in the security context of the new owner, and the User!UserID field in the report will display the value of new owner.</span></span> <span data-ttu-id="14095-107">PowerShell のサンプルが呼び出すオブジェクト モデルの詳細については、「 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="14095-107">For more information on the object model the PowerShell samples call, see <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>

 <span data-ttu-id="14095-108">![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")</span><span class="sxs-lookup"><span data-stu-id="14095-108">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

||
|-|
|<span data-ttu-id="14095-109">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="14095-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="14095-110">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="14095-110">**In this topic:**</span></span>

-   [<span data-ttu-id="14095-111">スクリプトの使用方法</span><span class="sxs-lookup"><span data-stu-id="14095-111">How to use the scripts</span></span>](#bkmk_how_to)

-   [<span data-ttu-id="14095-112">スクリプト:すべてのサブスクリプションの所有権を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="14095-112">Script: List the ownership of all subscriptions</span></span>](#bkmk_list_ownership_all)

-   [<span data-ttu-id="14095-113">スクリプト:特定のユーザーが所有するすべてのサブスクリプションを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="14095-113">Script: List all subscriptions owned by a specific user</span></span>](#bkmk_list_all_one_user)

-   [<span data-ttu-id="14095-114">スクリプト:特定のユーザーが所有するすべてのサブスクリプションの所有権を変更する</span><span class="sxs-lookup"><span data-stu-id="14095-114">Script: Change ownership for all subscriptions owned by a specific user</span></span>](#bkmk_change_all)

-   [<span data-ttu-id="14095-115">スクリプト:特定のレポートに関連付けられたすべてのサブスクリプションを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="14095-115">Script: List all subscriptions associated with a specific report</span></span>](#bkmk_list_for_1_report)

-   [<span data-ttu-id="14095-116">スクリプト:特定のサブスクリプションの所有権を変更する</span><span class="sxs-lookup"><span data-stu-id="14095-116">Script: Change ownership of a specific subscription</span></span>](#bkmk_change_all_1_subscription)

-   [<span data-ttu-id="14095-117">スクリプト:1 つのサブスクリプションを実行 (起動) する</span><span class="sxs-lookup"><span data-stu-id="14095-117">Script: Run (fire) a single subscription</span></span>](#bkmk_run_1_subscription)

##  <a name="how-to-use-the-scripts"></a><a name="bkmk_how_to"></a> <span data-ttu-id="14095-118">スクリプトの使用方法</span><span class="sxs-lookup"><span data-stu-id="14095-118">How to use the scripts</span></span>

### <a name="permissions"></a><span data-ttu-id="14095-119">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="14095-119">Permissions</span></span>
 <span data-ttu-id="14095-120">このセクションでは、ネイティブ モードと SharePoint モードの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]向けの各メソッドを使用するのに必要な権限レベルを要約します。</span><span class="sxs-lookup"><span data-stu-id="14095-120">This section summarizes the permission levels required to use each of the methods for both Native and SharePoint mode [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="14095-121">このトピック内のスクリプトは次の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="14095-121">The scripts in this topic use the following [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] methods:</span></span>

-   [<span data-ttu-id="14095-122">ReportingService2010.ListSubscriptions メソッド</span><span class="sxs-lookup"><span data-stu-id="14095-122">ReportingService2010.ListSubscriptions Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listsubscriptions.aspx)

-   [<span data-ttu-id="14095-123">ReportingService2010.ChangeSubscriptionOwner メソッド</span><span class="sxs-lookup"><span data-stu-id="14095-123">ReportingService2010.ChangeSubscriptionOwner Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.changesubscriptionowner.aspx)

-   [<span data-ttu-id="14095-124">ReportingService2010.ListChildren</span><span class="sxs-lookup"><span data-stu-id="14095-124">ReportingService2010.ListChildren</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listchildren.aspx)

-   <span data-ttu-id="14095-125">[ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) メソッドは、特定のサブスクリプションをトリガーして実行するために、最後のスクリプトでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="14095-125">The method [ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) is only used in the last script to trigger a specific subscription to run.</span></span> <span data-ttu-id="14095-126">そのスクリプトを使用する計画がない場合、FireEvent メソッドの権限要件を無視できます。</span><span class="sxs-lookup"><span data-stu-id="14095-126">If you do not plan to use that script you can ignore the permission requirements for the FireEvent method.</span></span>

 <span data-ttu-id="14095-127">**ネイティブ モード:**</span><span class="sxs-lookup"><span data-stu-id="14095-127">**Native mode:**</span></span>

-   <span data-ttu-id="14095-128">サブスクリプションの一覧表示: (HYPERLINK " https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx " レポートの readsubscription と、ユーザーがサブスクリプションの所有者であるか、または ReadAnySubscription)</span><span class="sxs-lookup"><span data-stu-id="14095-128">List Subscriptions: ( HYPERLINK "https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx" ReadSubscription on the report AND the user is the subscription owner) OR ReadAnySubscription</span></span>

-   <span data-ttu-id="14095-129">サブスクリプションを変更する:ユーザーは、BUILTIN\Administrators グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="14095-129">Change Subscriptions: The user must be a member of the BUILTIN\Administrators group</span></span>

-   <span data-ttu-id="14095-130">子を一覧表示する:アイテムに対する ReadProperties</span><span class="sxs-lookup"><span data-stu-id="14095-130">List Children: ReadProperties on Item</span></span>

-   <span data-ttu-id="14095-131">イベントを起動する:GenerateEvents (システム)</span><span class="sxs-lookup"><span data-stu-id="14095-131">Fire Event: GenerateEvents (System)</span></span>

 <span data-ttu-id="14095-132">**SharePoint モード:**</span><span class="sxs-lookup"><span data-stu-id="14095-132">**SharePoint mode:**</span></span>

-   <span data-ttu-id="14095-133">サブスクリプションの一覧表示: ManageAlerts または (HYPERLINK " https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx " レポートに対する createalerts、ユーザーはサブスクリプションの所有者で、サブスクリプションは時間指定のサブスクリプションです)。</span><span class="sxs-lookup"><span data-stu-id="14095-133">List Subscriptions: ManageAlerts OR ( HYPERLINK "https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx" CreateAlerts on the report AND the user is the subscription owner and the subscription is a timed subscription).</span></span>

-   <span data-ttu-id="14095-134">サブスクリプションを変更する:ManageWeb</span><span class="sxs-lookup"><span data-stu-id="14095-134">Change Subscriptions: ManageWeb</span></span>

-   <span data-ttu-id="14095-135">子を一覧表示する:ViewListItems</span><span class="sxs-lookup"><span data-stu-id="14095-135">List Children: ViewListItems</span></span>

-   <span data-ttu-id="14095-136">イベントを起動する:ManageWeb</span><span class="sxs-lookup"><span data-stu-id="14095-136">Fire Event: ManageWeb</span></span>

 <span data-ttu-id="14095-137">詳しくは、「 [Reporting Services のロールおよびタスクと SharePoint のグループおよび権限の比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="14095-137">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>

### <a name="script-usage"></a><span data-ttu-id="14095-138">スクリプトの使用法</span><span class="sxs-lookup"><span data-stu-id="14095-138">Script usage</span></span>
 <span data-ttu-id="14095-139">**スクリプトファイル (.ps1) の作成**</span><span class="sxs-lookup"><span data-stu-id="14095-139">**Create Script files (.ps1)**</span></span>

1.  <span data-ttu-id="14095-140">**c:\scripts**という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="14095-140">Create a folder named **c:\scripts**.</span></span> <span data-ttu-id="14095-141">異なるフォルダーを選択する場合、例のコマンド ライン構文ステートメントで使用されているフォルダー名を変更します。</span><span class="sxs-lookup"><span data-stu-id="14095-141">If you choose a different folder then modify the folder name used in the example command line syntax statements.</span></span>

2.  <span data-ttu-id="14095-142">各スクリプトに対してテキスト ファイルを作成し、ファイルを c:\scripts フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="14095-142">Create a text file for each script and save the files to the c:\scripts folder.</span></span> <span data-ttu-id="14095-143">.ps1 ファイルを作成する際、各例のコマンド ライン構文の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="14095-143">When you create the .ps1 files, use the name from each example command line syntax.</span></span>

3.  <span data-ttu-id="14095-144">管理特権でコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="14095-144">Open a command prompt with administrative privileges.</span></span>

4.  <span data-ttu-id="14095-145">各例に示されているサンプルのコマンド ライン構文を使用して、各スクリプト ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="14095-145">Run each script file, using the sample command line syntax provided with each example.</span></span>

 <span data-ttu-id="14095-146">**テスト済みの環境**</span><span class="sxs-lookup"><span data-stu-id="14095-146">**Tested environments**</span></span>

 <span data-ttu-id="14095-147">このトピックのスクリプトは PowerShell バージョン 3 および以下のバージョンの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]を使用してテスト済みです。</span><span class="sxs-lookup"><span data-stu-id="14095-147">The scripts in this topic were tested on PowerShell version 3 and with the following versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:</span></span>

-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]

-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]

-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]

##  <a name="script-list-the-ownership-of-all-subscriptions"></a><a name="bkmk_list_ownership_all"></a> <span data-ttu-id="14095-148">スクリプト:すべてのサブスクリプションの所有権を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="14095-148">Script: List the ownership of all subscriptions</span></span>
 <span data-ttu-id="14095-149">このスクリプトはサイト上のすべてのサブスクリプションを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="14095-149">This script lists all of the subscriptions on a site.</span></span> <span data-ttu-id="14095-150">このスクリプトを使用して、接続のテストまたは他のスクリプトで使用するためのレポート パスとサブスクリプション ID の検証を実施できます。</span><span class="sxs-lookup"><span data-stu-id="14095-150">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="14095-151">これは存在するサブスクリプションの内容と所有者を単に監査するのにも役立つスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="14095-151">This is also a useful script to simply audit what subscriptions exist and who owns them.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="14095-152">ネイティブモードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-152">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="14095-153">SharePoint モードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-153">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="14095-154">スクリプト</span><span class="sxs-lookup"><span data-stu-id="14095-154">Script</span></span>

```powershell
# Parameters
#    server   - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)

Param(
    [string]$server,
    [string]$site
   )

$rs2010 += New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site); # use "/" for default native mode site

Write-Host " "
Write-Host "----- $server's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted, Status
```

> [!TIP]
>  <span data-ttu-id="14095-155">SharePoint モードのサイト URLS を検証するには、SharePoint コマンドレット **Get-SPSite**を使用します。</span><span class="sxs-lookup"><span data-stu-id="14095-155">To verify site URLS in SharePoint mode, use the SharePoint cmdlet **Get-SPSite**.</span></span> <span data-ttu-id="14095-156">詳細については、「 [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14095-156">For more information, see [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx).</span></span>

##  <a name="script-list-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_list_all_one_user"></a> <span data-ttu-id="14095-157">スクリプト:特定のユーザーが所有するすべてのサブスクリプションを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="14095-157">Script: List all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="14095-158">このスクリプトは特定のユーザーが所有するすべてのサブスクリプションを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="14095-158">This script lists all of the subscriptions owned by a specific user.</span></span> <span data-ttu-id="14095-159">このスクリプトを使用して、接続のテストまたは他のスクリプトで使用するためのレポート パスとサブスクリプション ID の検証を実施できます。</span><span class="sxs-lookup"><span data-stu-id="14095-159">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="14095-160">このスクリプトは、組織内のだれかが離任したときに、所有していたサブスクリプションを検証して、所有者を変更したり、サブスクリプションを削除したりする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="14095-160">This script is useful when someone in your organization leaves and you want to verify what subscriptions they owned so you can change the owner or delete the subscription.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="14095-161">ネイティブモードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-161">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]" "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="14095-162">SharePoint モードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-162">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]"  "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="14095-163">スクリプト</span><span class="sxs-lookup"><span data-stu-id="14095-163">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
Param(
    [string]$currentOwner,
    [string]$server,
    [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $currentOwner's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.owner -eq $currentOwner}
```

##  <a name="script-change-ownership-for-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_change_all"></a> <span data-ttu-id="14095-164">スクリプト:特定のユーザーが所有するすべてのサブスクリプションの所有権を変更する</span><span class="sxs-lookup"><span data-stu-id="14095-164">Script: Change ownership for all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="14095-165">このスクリプトは、特定のユーザーが所有するすべてのサブスクリプションの所有権を新しい所有者のパラメーターに変更します。</span><span class="sxs-lookup"><span data-stu-id="14095-165">This script changes the ownership for all subscriptions owned by a specific user to the new owner parameter.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="14095-166">ネイティブモードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-166">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\current owner]" "[Domain]\[new owner]" "[server]/reportserver"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="14095-167">SharePoint モードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-167">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\{current owner]" "[Domain]\[new owner]" "[server]/_vti_bin/reportserver"
```

### <a name="script"></a><span data-ttu-id="14095-168">スクリプト</span><span class="sxs-lookup"><span data-stu-id="14095-168">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    newOwner      - DOMAIN\USER that will own the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver, myserver/reportserver_db2, myserver/_vti_bin/reportserver)

Param(
    [string]$currentOwner,
    [string]$newOwner,
    [string]$server
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$items = $rs2010.ListChildren("/", $true);

$subscriptions = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $curRepSubs = $rs2010.ListSubscriptions($item.Path);
        ForEach ($curRepSub in $curRepSubs)
        {
            if ($curRepSub.Owner -eq $currentOwner)
            {
                $subscriptions += $curRepSub;
            }
        }
    }
}

Write-Host " "
Write-Host " "
Write-Host -foregroundcolor "green" "-----  $currentOwner's Subscriptions changing ownership to $newOwner : "
$subscriptions | select SubscriptionID, Owner, Path, Description,  Status  | format-table -AutoSize

ForEach ($sub in $subscriptions)
{
    $rs2010.ChangeSubscriptionOwner($sub.SubscriptionID, $newOwner);
}

$subs2 = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $subs2 += $rs2010.ListSubscriptions($item.Path);
    }
}
```

##  <a name="script-list-all-subscriptions-associated-with-a-specific-report"></a><a name="bkmk_list_for_1_report"></a> <span data-ttu-id="14095-169">スクリプト:特定のレポートに関連付けられたすべてのサブスクリプションを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="14095-169">Script: List all subscriptions associated with a specific report</span></span>
 <span data-ttu-id="14095-170">このスクリプトは特定のレポートに関連付けられたすべてのサブスクリプションを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="14095-170">This script lists all of the subscriptions associated with a specific report.</span></span> <span data-ttu-id="14095-171">レポート パス構文は、完全な URL を必要とする、異なる SharePoint モードです。</span><span class="sxs-lookup"><span data-stu-id="14095-171">The report path syntax is different SharePoint mode which requires a full URL.</span></span> <span data-ttu-id="14095-172">構文例で使用されているレポート名 "title only" には空白が含まれているため、レポート名を単一引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="14095-172">In the syntax examples, the report name used is "title only", which contains a space and therefore requires the single quotes around the report name.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="14095-173">ネイティブモードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-173">Native mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/reportserver" "'/reports/title only'" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="14095-174">SharePoint モードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-174">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/_vti_bin/reportserver"  "'http://[server]/shared documents/title only.rdl'" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="14095-175">スクリプト</span><span class="sxs-lookup"><span data-stu-id="14095-175">Script</span></span>

```powershell
# Parameters:
#    server      - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    reportpath  - path to report in the report server, including report name e.g. /reports/test report >> pass in  "'/reports/title only'"
#    site        - use "/" for default native mode site
Param
(
      [string]$server,
      [string]$reportpath,
      [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $reportpath 's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.path -eq $reportpath}
```

##  <a name="script-change-ownership-of-a-specific-subscription"></a><a name="bkmk_change_all_1_subscription"></a> <span data-ttu-id="14095-176">スクリプト:特定のサブスクリプションの所有権を変更する</span><span class="sxs-lookup"><span data-stu-id="14095-176">Script: Change ownership of a specific subscription</span></span>
 <span data-ttu-id="14095-177">このスクリプトは特定のサブスクリプションの所有権を変更します。</span><span class="sxs-lookup"><span data-stu-id="14095-177">This script changes the ownership for a specific subscription.</span></span> <span data-ttu-id="14095-178">サブスクリプションは、スクリプトに渡す SubscriptionID によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="14095-178">The subscription is identified by the SubscriptionID that you pass into the script.</span></span> <span data-ttu-id="14095-179">サブスクリプションを一覧表示するスクリプトのいずれかを使用して、正しい SubscriptionID を判別できます。</span><span class="sxs-lookup"><span data-stu-id="14095-179">You can use one of the list subscription scripts to determine the correct SubscriptionID.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="14095-180">ネイティブモードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-180">Native mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/reportserver" "/" "ac5637a1-9982-4d89-9d69-a72a9c3b3150"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="14095-181">SharePoint モードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-181">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/_vti_bin/reportserver" "http://[server]" "9660674b-f020-453f-b1e3-d9ba37624519"
```

### <a name="script"></a><span data-ttu-id="14095-182">スクリプト</span><span class="sxs-lookup"><span data-stu-id="14095-182">Script</span></span>

```powershell
# Parameters:
#    newOwner       - DOMAIN\USER that will own the subscriptions you wish to change
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
#    subscriptionID - guid for the single subscription to change

Param(
    [string]$newOwner,
    [string]$server,
    [string]$site,
    [string]$subscriptionid
   )
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;

$subscription += $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid};

Write-Host " "
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status

$rs2010.ChangeSubscriptionOwner($subscription.SubscriptionID, $newOwner)

#refresh the list
$subscription = $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid}; # use "/" for default native mode site
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status
```

##  <a name="script-run-fire-a-single-subscription"></a><a name="bkmk_run_1_subscription"></a> <span data-ttu-id="14095-183">スクリプト:1 つのサブスクリプションを実行 (起動) する</span><span class="sxs-lookup"><span data-stu-id="14095-183">Script: Run (fire) a single subscription</span></span>
 <span data-ttu-id="14095-184">このスクリプトは、FireEvent メソッドを使用して特定のサブスクリプションを実行します。</span><span class="sxs-lookup"><span data-stu-id="14095-184">This script will run a specific subscription using the FireEvent method.</span></span> <span data-ttu-id="14095-185">このスクリプトは、サブスクリプションに対して構成されたスケジュールに関係なく、すぐにサブスクリプションを実行します。</span><span class="sxs-lookup"><span data-stu-id="14095-185">The script will immediately run the subscription regardless of the schedule configured for the subscription.</span></span> <span data-ttu-id="14095-186">EventType は、レポート サーバー構成ファイル **rsreportserver.config** で定義されている既知のイベントのセットと照合されます。スクリプトは標準サブスクリプションに対する以下のイベントの種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="14095-186">The EventType is matched against the known set of events that are defined in the report server configuration file **rsreportserver.config** The script uses the following event type for standard subscriptions:</span></span>

 `<Event>`

 `<Type>TimedSubscription</Type>`

 `</Event>`

 <span data-ttu-id="14095-187">構成ファイルの詳細については、「 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14095-187">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>

 <span data-ttu-id="14095-188">スクリプトには遅延ロジック `Start-Sleep -s 6` が含まれているので、イベントの起動後に時間があり、更新されたステータスが ListSubscription メソッドによって使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="14095-188">The script includes delay logic "`Start-Sleep -s 6`" so there is time after the event fires, for the updated status to be available with the ListSubscription method.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="14095-189">ネイティブモードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-189">Native mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/reportserver" $null "70366e82-2d3c-4edd-a216-b97e51e26de9"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="14095-190">SharePoint モードの構文</span><span class="sxs-lookup"><span data-stu-id="14095-190">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/_vti_bin/reportserver" "http://[server]" "c3425c72-580d-423e-805a-41cf9799fd25"
```

### <a name="script"></a><span data-ttu-id="14095-191">スクリプト</span><span class="sxs-lookup"><span data-stu-id="14095-191">Script</span></span>

```powershell
# Parameters
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site           - use $null for a native mode server
#    subscriptionid - subscription guid

Param(
  [string]$server,
  [string]$site,
  [string]$subscriptionid
  )

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
#event type is case sensative to what is in the rsreportserver.config
$rs2010.FireEvent("TimedSubscription",$subscriptionid,$site)

Write-Host " "
Write-Host "----- Subscription ($subscriptionid) status: "
#get list of subscriptions and filter to the specific ID to see the Status and LastExecuted
Start-Sleep -s 6 # slight delay in processing so ListSubscription returns the updated Status and LastExecuted
$subscriptions = $rs2010.ListSubscriptions($site); 
$subscriptions | select Status, Path, report, Description, Owner, SubscriptionID, EventType, lastexecuted | where {$_.SubscriptionID -eq $subscriptionid}
```

## <a name="see-also"></a><span data-ttu-id="14095-192">参照</span><span class="sxs-lookup"><span data-stu-id="14095-192">See Also</span></span>
 <span data-ttu-id="14095-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="14095-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span> 
 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 
 <xref:ReportService2010.ReportingService2010.FireEvent%2A>
