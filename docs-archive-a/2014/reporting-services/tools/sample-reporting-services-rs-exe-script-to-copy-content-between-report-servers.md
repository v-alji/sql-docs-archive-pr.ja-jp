---
title: レポートサーバー間でコンテンツを移行するためのサンプル Reporting Services rs.exe スクリプト |Microsoft Docs
ms.custom: ''
ms.date: 07/27/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d81bb03a-a89e-4fc1-a62b-886fb5338150
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9dece153485e4c683df42a04b9301cf3a47c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715077"
---
# <a name="sample-reporting-services-rsexe-script-to-migrate-content-between-report-servers"></a><span data-ttu-id="c53e2-102">レポート サーバー間でコンテンツを移行するサンプル Reporting Services rs.exe スクリプト</span><span class="sxs-lookup"><span data-stu-id="c53e2-102">Sample Reporting Services rs.exe Script to Migrate Content between Report Servers</span></span>
  <span data-ttu-id="c53e2-103">このトピックでは、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RS.exe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span><span class="sxs-lookup"><span data-stu-id="c53e2-103">This topic includes and describes a sample [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RSS script that copies content items and settings from one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span></span> <span data-ttu-id="c53e2-104">RS.exe は、ネイティブ モードと SharePoint モードの両方で、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-104">RS.exe is installed with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], both native and SharePoint mode.</span></span> <span data-ttu-id="c53e2-105">このスクリプトは、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] アイテム (レポートやサブスクリプションなど) をサーバー間でコピーします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-105">The script copies [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] items, for example reports and subscriptions, from server to another server.</span></span> <span data-ttu-id="c53e2-106">スクリプトは SharePoint モードとネイティブ モードの両方のレポート サーバーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c53e2-106">The script supports both SharePoint mode and Native mode report servers.</span></span>  
  
||  
|-|  
|<span data-ttu-id="c53e2-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint モード &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブ モード</span><span class="sxs-lookup"><span data-stu-id="c53e2-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
##  <a name="in-this-topic"></a><a name="bkmk_top"></a><span data-ttu-id="c53e2-108">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="c53e2-108">In this Topic:</span></span>  
  
-   [<span data-ttu-id="c53e2-109">ssrs_migration.rss スクリプトをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="c53e2-109">To Download the ssrs_migration.rss Script</span></span>](#bkmk_download_script)  
  
-   [<span data-ttu-id="c53e2-110">サポートされるシナリオ</span><span class="sxs-lookup"><span data-stu-id="c53e2-110">Supported Scenarios</span></span>](#bkmk_supported_scenarios)  
  
-   [<span data-ttu-id="c53e2-111">スクリプトが移行するアイテムとリソース</span><span class="sxs-lookup"><span data-stu-id="c53e2-111">Items and resources the script migrates</span></span>](#bkmk_what_is_migrated)  
  
-   [<span data-ttu-id="c53e2-112">必要なアクセス許可</span><span class="sxs-lookup"><span data-stu-id="c53e2-112">Required Permissions</span></span>](#bkmk_required_permissions)  
  
-   [<span data-ttu-id="c53e2-113">スクリプトの使用方法</span><span class="sxs-lookup"><span data-stu-id="c53e2-113">How to use the script</span></span>](#bkmk_how_to_use_the_script)  
  
-   [<span data-ttu-id="c53e2-114">パラメーターの説明</span><span class="sxs-lookup"><span data-stu-id="c53e2-114">Parameter Description</span></span>](#bkmk_parameter_description)  
  
-   [<span data-ttu-id="c53e2-115">その他の例</span><span class="sxs-lookup"><span data-stu-id="c53e2-115">More Examples</span></span>](#bkmk_more_examples)  
  
    -   [<span data-ttu-id="c53e2-116">ネイティブ モード レポート サーバー間</span><span class="sxs-lookup"><span data-stu-id="c53e2-116">Native Mode Report Server to Native Mode Report Server</span></span>](#bkmk_native_2_native)  
  
    -   [<span data-ttu-id="c53e2-117">ネイティブモードから SharePoint モード (ルートサイト)</span><span class="sxs-lookup"><span data-stu-id="c53e2-117">Native Mode to SharePoint Mode - root site</span></span>](#bkmk_native_2_sharepoint_root)  
  
    -   [<span data-ttu-id="c53e2-118">ネイティブモードから SharePoint モード ("bi" サイトコレクション)</span><span class="sxs-lookup"><span data-stu-id="c53e2-118">Native mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_native_2_sharepoint_with_site)  
  
    -   [<span data-ttu-id="c53e2-119">SharePoint モードから SharePoint モード ("bi" サイトコレクション)</span><span class="sxs-lookup"><span data-stu-id="c53e2-119">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_sharepoint_2_sharepoint)  
  
    -   [<span data-ttu-id="c53e2-120">ネイティブモードからネイティブモード (Azure 仮想マシン)</span><span class="sxs-lookup"><span data-stu-id="c53e2-120">Native Mode to Native Mode - Azure Virtual Machine</span></span>](#bkmk_native_to_native_Azure_vm)  
  
    -   [<span data-ttu-id="c53e2-121">SharePoint モード-Azure 仮想マシン上のネイティブモードサーバーへの ' bi ' サイトコレクション</span><span class="sxs-lookup"><span data-stu-id="c53e2-121">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>](#bkmk_sharepoint_site_to_native_Azure_vm)  
  
-   [<span data-ttu-id="c53e2-122">確認</span><span class="sxs-lookup"><span data-stu-id="c53e2-122">Verification</span></span>](#bkmk_verification)  
  
-   [<span data-ttu-id="c53e2-123">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c53e2-123">Troubleshooting</span></span>](#bkmk_troubleshoot)  
  
##  <a name="to-download-the-ssrs_migrationrss-script"></a><a name="bkmk_download_script"></a><span data-ttu-id="c53e2-124">Ssrs_migration の rss スクリプトをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="c53e2-124">To Download the ssrs_migration.rss Script</span></span>  
 <span data-ttu-id="c53e2-125">CodePlex サイト「 [コンテンツを移行する Reporting Services RS.exe スクリプト](https://azuresql.codeplex.com/releases/view/115207) 」からローカル フォルダーにスクリプトをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-125">Download the script from the CodePlex site [Reporting Services RS.exe script migrates content](https://azuresql.codeplex.com/releases/view/115207) to a local folder.</span></span> <span data-ttu-id="c53e2-126">詳細については、「 [スクリプトの使用方法](#bkmk_how_to_use_the_script) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-126">See the section [How to use the script](#bkmk_how_to_use_the_script) in this topic for more information.</span></span>  
  
##  <a name="supported-scenarios"></a><a name="bkmk_supported_scenarios"></a><span data-ttu-id="c53e2-127">サポートされるシナリオ</span><span class="sxs-lookup"><span data-stu-id="c53e2-127">Supported Scenarios</span></span>  
 <span data-ttu-id="c53e2-128">スクリプトは SharePoint モードとネイティブ モードの両方のレポート サーバーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c53e2-128">The script supports both SharePoint mode and Native mode report servers.</span></span> <span data-ttu-id="c53e2-129">また、次のバージョンのレポート サーバーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c53e2-129">The script supports the following report server versions:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]  
  
 <span data-ttu-id="c53e2-130">スクリプトは同じモードまたは異なるモードのレポート サーバー間でコンテンツをコピーするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-130">The script can be used to copy content between report servers of the same mode or different modes.</span></span> <span data-ttu-id="c53e2-131">たとえば、スクリプトを実行して [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] ネイティブ モード レポート サーバーから [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint モード レポート サーバーにコンテンツをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-131">For example, you can run the script to copy content from a [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] native mode report server to a [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint mode report server.</span></span> <span data-ttu-id="c53e2-132">スクリプトは RS.exe がインストールされているいずれのサーバーからも実行できます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-132">You can run the script from any server where RS.exe is installed.</span></span> <span data-ttu-id="c53e2-133">たとえば、以下の配置では次のことが可能です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-133">For example, in the following deployment, you can:</span></span>  
  
-   <span data-ttu-id="c53e2-134">サーバー A **上で** RS.exe とスクリプトを実行する</span><span class="sxs-lookup"><span data-stu-id="c53e2-134">Run RS.exe and the script **ON** Server A.</span></span>  
  
-   <span data-ttu-id="c53e2-135">サーバー B **から** コンテンツを</span><span class="sxs-lookup"><span data-stu-id="c53e2-135">To copy content **FROM** Server B</span></span>  
  
-   <span data-ttu-id="c53e2-136">サーバー C**に** コピーする</span><span class="sxs-lookup"><span data-stu-id="c53e2-136">**TO** Server C</span></span>  
  
|<span data-ttu-id="c53e2-137">サーバー名</span><span class="sxs-lookup"><span data-stu-id="c53e2-137">Server name</span></span>|<span data-ttu-id="c53e2-138">[レポート サーバー モード]</span><span class="sxs-lookup"><span data-stu-id="c53e2-138">Report Server Mode</span></span>|  
|-----------------|------------------------|  
|<span data-ttu-id="c53e2-139">サーバー A</span><span class="sxs-lookup"><span data-stu-id="c53e2-139">Server A</span></span>|<span data-ttu-id="c53e2-140">ネイティブ</span><span class="sxs-lookup"><span data-stu-id="c53e2-140">Native</span></span>|  
|<span data-ttu-id="c53e2-141">コンテンツを</span><span class="sxs-lookup"><span data-stu-id="c53e2-141">Server B</span></span>|<span data-ttu-id="c53e2-142">SharePoint</span><span class="sxs-lookup"><span data-stu-id="c53e2-142">SharePoint</span></span>|  
|<span data-ttu-id="c53e2-143">コピーする</span><span class="sxs-lookup"><span data-stu-id="c53e2-143">Server C</span></span>|<span data-ttu-id="c53e2-144">SharePoint</span><span class="sxs-lookup"><span data-stu-id="c53e2-144">SharePoint</span></span>|  
  
 <span data-ttu-id="c53e2-145">RS.exe ユーティリティの詳細については、「 [RS.exe ユーティリティ &#40;SSRS&#41;](rs-exe-utility-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-145">For more information on the RS.exe utility, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
###  <a name="items-and-resources-the-script-migrates"></a><a name="bkmk_what_is_migrated"></a><span data-ttu-id="c53e2-146">スクリプトが移行するアイテムとリソース</span><span class="sxs-lookup"><span data-stu-id="c53e2-146">Items and resources the script migrates</span></span>  
 <span data-ttu-id="c53e2-147">スクリプトは同じ名前の既存のコンテンツ アイテムを上書きしません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-147">The script will not write over existing content items of the same name.</span></span>  <span data-ttu-id="c53e2-148">スクリプトが移行元サーバー上のアイテムと同じ名前のアイテムを移行先サーバーで検出した場合、個々のアイテムについて "FAILURE" メッセージが表示されますが、スクリプトは続行されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-148">If the script detects items with the same name on the destination server that are on the source server, the individual items will result in a "failure" message and the script will continue.</span></span> <span data-ttu-id="c53e2-149">次の表は、スクリプトを使用して移行先のモードのレポート サーバーに移行できるコンテンツとリソースの種類を示したものです。</span><span class="sxs-lookup"><span data-stu-id="c53e2-149">The following table lists the types of content and resources the script can migrate to target report server modes.</span></span>  
  
|<span data-ttu-id="c53e2-150">Item</span><span class="sxs-lookup"><span data-stu-id="c53e2-150">Item</span></span>|<span data-ttu-id="c53e2-151">移行対象</span><span class="sxs-lookup"><span data-stu-id="c53e2-151">Migrated</span></span>|<span data-ttu-id="c53e2-152">SharePoint</span><span class="sxs-lookup"><span data-stu-id="c53e2-152">SharePoint</span></span>|<span data-ttu-id="c53e2-153">説明</span><span class="sxs-lookup"><span data-stu-id="c53e2-153">Description</span></span>|  
|----------|--------------|----------------|-----------------|  
|<span data-ttu-id="c53e2-154">パスワード</span><span class="sxs-lookup"><span data-stu-id="c53e2-154">Passwords</span></span>|<span data-ttu-id="c53e2-155">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="c53e2-155">**No**</span></span>|<span data-ttu-id="c53e2-156">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="c53e2-156">**No**</span></span>|<span data-ttu-id="c53e2-157">パスワードは移行 **されません** 。</span><span class="sxs-lookup"><span data-stu-id="c53e2-157">Passwords are **NOT** migrated.</span></span> <span data-ttu-id="c53e2-158">コンテンツ アイテムの移行後、移行先サーバーで資格情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-158">After content items are migrated, update the credential information on the destination server.</span></span> <span data-ttu-id="c53e2-159">たとえば、保存された資格情報を使用するデータ ソースなどです。</span><span class="sxs-lookup"><span data-stu-id="c53e2-159">For example, data sources with stored credentials.</span></span>|  
|<span data-ttu-id="c53e2-160">個人用レポート</span><span class="sxs-lookup"><span data-stu-id="c53e2-160">My Reports</span></span>|<span data-ttu-id="c53e2-161">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="c53e2-161">**No**</span></span>|<span data-ttu-id="c53e2-162">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="c53e2-162">**No**</span></span>|<span data-ttu-id="c53e2-163">ネイティブ モードの "個人用レポート" 機能は個々のユーザー ログインに基づいているため、スクリプト作成サービスは、rss スクリプトに渡される **-u** パラメーターで指定されていないユーザーの "My Reports" フォルダー内のコンテンツにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-163">The Native mode "My Reports" feature is based on individual user logins therefore the scripting service does not have access to content in "My Reports" folders for users other than the **-u** parameter used to run the rss script.</span></span> <span data-ttu-id="c53e2-164">また、"個人用レポート" は sharepoint モードの機能ではなく、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] フォルダー内のアイテムを sharepoint 環境にコピーすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-164">Also, "My Reports" is not a feature of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode and items in the folders cannot be copied to a SharePoint environment.</span></span> <span data-ttu-id="c53e2-165">このため、スクリプトは、ソースネイティブモードのレポートサーバー上の "個人用レポート" フォルダーにあるレポートアイテムをコピーしません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-165">Therefore, the script does not copy report items that are in the "My Reports" folders on a source native mode report server.</span></span> <span data-ttu-id="c53e2-166">このスクリプトを使用して "個人用レポート" フォルダー内のコンテンツを移行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-166">To migrate the content in "My Reports" folders with this script, complete the following:</span></span><br /><br /> <span data-ttu-id="c53e2-167">1) レポートマネージャーで新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-167">1) Create new folder(s) in Report Manager.</span></span> <span data-ttu-id="c53e2-168">必要に応じて、各ユーザーのフォルダーやサブフォルダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-168">Optionally, you can create folders or subfolder for each user.</span></span><br /><br /> <span data-ttu-id="c53e2-169">2) "個人用レポート" コンテンツを持つユーザーの1人としてログインします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-169">2) Login as one of the users with "My Reports" content.</span></span><br /><br /> <span data-ttu-id="c53e2-170">3) レポートマネージャーで、**個人用レポート**フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-170">3) In Report Manager, click the **My Reports** folder.</span></span><br /><br /> <span data-ttu-id="c53e2-171">4) フォルダーの**詳細**ビューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-171">4) Click the **Details** view for the folder.</span></span><br /><br /> <span data-ttu-id="c53e2-172">5) コピーする各レポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-172">5) Select each report that you want to copy.</span></span><br /><br /> <span data-ttu-id="c53e2-173">6) レポートマネージャーツールバーの [**移動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-173">6) Click **Move** in the Report Manager toolbar.</span></span><br /><br /> <span data-ttu-id="c53e2-174">7) 目的の保存先フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-174">7) Select the desired destination folder.</span></span><br /><br /> <span data-ttu-id="c53e2-175">8) 各ユーザーに対して手順2-7 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-175">8) Repeat steps 2-7 for each user.</span></span><br /><br /> <span data-ttu-id="c53e2-176">9) スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-176">9) Run the script.</span></span>|  
|<span data-ttu-id="c53e2-177">履歴</span><span class="sxs-lookup"><span data-stu-id="c53e2-177">History</span></span>|<span data-ttu-id="c53e2-178">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="c53e2-178">**No**</span></span>|<span data-ttu-id="c53e2-179">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="c53e2-179">**No**</span></span>||  
|<span data-ttu-id="c53e2-180">履歴の設定</span><span class="sxs-lookup"><span data-stu-id="c53e2-180">History settings</span></span>|<span data-ttu-id="c53e2-181">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-181">Yes</span></span>|<span data-ttu-id="c53e2-182">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-182">Yes</span></span>|<span data-ttu-id="c53e2-183">履歴の設定は移行されますが、履歴の詳細は移行されません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-183">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="c53e2-184">スケジュール</span><span class="sxs-lookup"><span data-stu-id="c53e2-184">Schedules</span></span>|<span data-ttu-id="c53e2-185">可</span><span class="sxs-lookup"><span data-stu-id="c53e2-185">yes</span></span>|<span data-ttu-id="c53e2-186">可</span><span class="sxs-lookup"><span data-stu-id="c53e2-186">yes</span></span>|<span data-ttu-id="c53e2-187">スケジュールを移行するには、SQL Server エージェントがターゲット サーバーで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c53e2-187">To migrate schedules, it is required that SQL Server Agent is running on the target server.</span></span> <span data-ttu-id="c53e2-188">SQL Server エージェントが移行先で実行されていない場合は、次のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-188">If SQL Server Agent is not running on the target, you will see an error message similar to the following:</span></span><br /><br /> `Migrating schedules: 1 items found. Migrating schedule: theMondaySchedule ... FAILURE:  The SQL Agent service is not running. This operation requires the SQL Agent service. ---> Microsoft.ReportingServices.Diagnostics.Utilities.SchedulerNotResponding Exception: The SQL Agent service is not running. This operation requires the SQL Agent service.`|  
|<span data-ttu-id="c53e2-189">ロールとシステム ポリシー</span><span class="sxs-lookup"><span data-stu-id="c53e2-189">Roles and system policies</span></span>|<span data-ttu-id="c53e2-190">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-190">Yes</span></span>|<span data-ttu-id="c53e2-191">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-191">Yes</span></span>|<span data-ttu-id="c53e2-192">既定では、スクリプトはカスタム権限スキーマをサーバー間でコピーしません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-192">By default the script will not copy custom permission schema between servers.</span></span> <span data-ttu-id="c53e2-193">既定の動作では、"親のアクセス許可を継承する" フラグが TRUE に設定されている移行先サーバーに項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-193">The default behavior is the items will be coied to the destination server with the 'inherit parent permissions' flag set to TRUE.</span></span> <span data-ttu-id="c53e2-194">スクリプトで個々のアイテムの権限をコピーする場合は、SECURITY スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-194">If you want the script to copy permissions for individual items, use the SECURITY switch.</span></span><br /><br /> <span data-ttu-id="c53e2-195">ソース サーバーとターゲット サーバーが **同じレポート サーバー モードでない**場合、たとえばネイティブ モードから SharePoint モードへの移行のとき、スクリプトは、「 [Reporting Services のロールおよびタスクと SharePoint のグループおよび権限の比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)」トピックで説明している比較に基づいて、既定のロールとグループをマップしようとします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-195">If the source and target servers are **not the same report server mode**, for example from native mode to SharePoint mode, and you use the SECURITY switch, the script will attempt to map default roles and groups based on the comparison in the following topic [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span> <span data-ttu-id="c53e2-196">カスタムのロールとグループは移行先サーバーにコピーされません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-196">Custom roles and groups are not copied to the destination server.</span></span><br /><br /> <span data-ttu-id="c53e2-197">スクリプトが **同じモードの**サーバー間でコピーする場合は、SECURITY スイッチを使用してください。スクリプトは移行先サーバーで新しいロール (ネイティブ モード) またはグループ (SharePoint モード) を作成します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-197">When the script is copying between servers **that are the same mode**, and you use the SECURITY switch, the script will create new roles (native mode) or groups (SharePoint mode) on the destination server.</span></span><br /><br /> <span data-ttu-id="c53e2-198">ロールが移行先サーバーに既に存在する場合、スクリプトは次のような "FAILURE" メッセージを表示し、他のアイテムの移行を続行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-198">If a role already exists on the destination server, the script will create a "Failure" message similar to the following, and continue migrating other items.</span></span> <span data-ttu-id="c53e2-199">スクリプトの完了後、移行先サーバー上のロールがニーズを満たすように構成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-199">After the script completes, verify the roles on the destination server are configured to meet your needs.</span></span> <span data-ttu-id="c53e2-200">移行中のロール: 8 項目が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="c53e2-200">the Migrating roles: 8 items found.</span></span><br /><br /> `Migrating role: Browser ... FAILURE: The role 'Browser' already exists and cannot be created. ---> Microsoft.ReportingServices.Diagnostics.Utilities.RoleAlreadyExistsException: The role 'Browser' already exists and cannot be created.`<br /><br /> <span data-ttu-id="c53e2-201">詳細については、「[レポート サーバーへのユーザー アクセスを許可する &#40;レポート マネージャー&#41;](../security/grant-user-access-to-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-201">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md)</span></span><br /><br /> <span data-ttu-id="c53e2-202">**注:** 移行元サーバー上に存在するユーザーが移行先サーバーに存在しない場合、スクリプトは移行先サーバーでロールの割り当てを適用することはできません。SECURITY スイッチを使用している場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-202">**Note:** if a user that exists on the source server does not exist on the destination server, the script cannot apply role assignments on the destination server, the script cannot apply role assignments, even if the SECURITY switch is used.</span></span>|  
|<span data-ttu-id="c53e2-203">[共有データ ソース]</span><span class="sxs-lookup"><span data-stu-id="c53e2-203">Shared data source</span></span>|<span data-ttu-id="c53e2-204">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-204">Yes</span></span>|<span data-ttu-id="c53e2-205">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-205">Yes</span></span>|<span data-ttu-id="c53e2-206">スクリプトはターゲット サーバー上の既存のアイテムを上書きしません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-206">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="c53e2-207">同じ名前のアイテムがターゲット サーバーに既に存在する場合は、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-207">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating DataSource: /Data Sources/Aworks2012_oltp ... FAILURE:The item '/Data Sources/Aworks2012_oltp' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Data Source s/Aworks2012_oltp' already exists.`<br /><br /> <span data-ttu-id="c53e2-208">資格情報は、データ ソースの一部としてコピー **されません** 。</span><span class="sxs-lookup"><span data-stu-id="c53e2-208">Credentials are **NOT** copied over as part of the data source.</span></span> <span data-ttu-id="c53e2-209">コンテンツ アイテムの移行後、移行先サーバーで資格情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-209">After content items are migrated, update the credential information on the destination server.</span></span>|  
|<span data-ttu-id="c53e2-210">共有データセット</span><span class="sxs-lookup"><span data-stu-id="c53e2-210">Shared dataset</span></span>|<span data-ttu-id="c53e2-211">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-211">Yes</span></span>|<span data-ttu-id="c53e2-212">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-212">Yes</span></span>||  
|<span data-ttu-id="c53e2-213">Folder</span><span class="sxs-lookup"><span data-stu-id="c53e2-213">Folder</span></span>|<span data-ttu-id="c53e2-214">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-214">Yes</span></span>|<span data-ttu-id="c53e2-215">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-215">Yes</span></span>|<span data-ttu-id="c53e2-216">スクリプトはターゲット サーバー上の既存のアイテムを上書きしません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-216">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="c53e2-217">同じ名前のアイテムがターゲット サーバーに既に存在する場合は、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-217">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Folder: /Reports ... FAILURE: The item '/Reports' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports' already exists.`|  
|<span data-ttu-id="c53e2-218">レポート</span><span class="sxs-lookup"><span data-stu-id="c53e2-218">Report</span></span>|<span data-ttu-id="c53e2-219">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-219">Yes</span></span>|<span data-ttu-id="c53e2-220">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-220">Yes</span></span>|<span data-ttu-id="c53e2-221">スクリプトはターゲット サーバー上の既存のアイテムを上書きしません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-221">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="c53e2-222">同じ名前のアイテムがターゲット サーバーに既に存在する場合は、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-222">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Report: /Reports/testThe item '/Reports/test' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports/test' already exists.`|  
|<span data-ttu-id="c53e2-223">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c53e2-223">Parameters</span></span>|<span data-ttu-id="c53e2-224">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-224">Yes</span></span>|<span data-ttu-id="c53e2-225">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-225">Yes</span></span>||  
|<span data-ttu-id="c53e2-226">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="c53e2-226">Subscriptions</span></span>|<span data-ttu-id="c53e2-227">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-227">Yes</span></span>|<span data-ttu-id="c53e2-228">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-228">Yes</span></span>||  
|<span data-ttu-id="c53e2-229">履歴の設定</span><span class="sxs-lookup"><span data-stu-id="c53e2-229">History Settings</span></span>|<span data-ttu-id="c53e2-230">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-230">Yes</span></span>|<span data-ttu-id="c53e2-231">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-231">Yes</span></span>|<span data-ttu-id="c53e2-232">履歴の設定は移行されますが、履歴の詳細は移行されません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-232">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="c53e2-233">処理オプション</span><span class="sxs-lookup"><span data-stu-id="c53e2-233">processing options</span></span>|<span data-ttu-id="c53e2-234">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-234">Yes</span></span>|<span data-ttu-id="c53e2-235">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-235">Yes</span></span>||  
|<span data-ttu-id="c53e2-236">キャッシュ更新オプション</span><span class="sxs-lookup"><span data-stu-id="c53e2-236">cache refresh options</span></span>|<span data-ttu-id="c53e2-237">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-237">Yes</span></span>|<span data-ttu-id="c53e2-238">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-238">Yes</span></span>|<span data-ttu-id="c53e2-239">依存設定はカタログ アイテムの一部として移行されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-239">Dependent settings are migrated as part of a catalog item.</span></span> <span data-ttu-id="c53e2-240">次に示しているのは、スクリプトがレポート (.rdl) と関連設定 (キャッシュ更新オプションなど) を移行するときの出力例です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-240">The following is the sample out of the script as it migrates a report (.rdl) and related settings such as cache refresh options:</span></span><br /><br /> <span data-ttu-id="c53e2-241">Migrating parameters for report TitleOnly.rdl 0 items found.</span><span class="sxs-lookup"><span data-stu-id="c53e2-241">Migrating parameters for report TitleOnly.rdl 0 items found.</span></span><br /><br /> <span data-ttu-id="c53e2-242">Migrating subscriptions for report TitleOnly.rdl:1 items found.</span><span class="sxs-lookup"><span data-stu-id="c53e2-242">Migrating subscriptions for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="c53e2-243">サブスクリプションを移行する \\ と、\ web レポートにタイトルのみで保存...ブランド</span><span class="sxs-lookup"><span data-stu-id="c53e2-243">Migrating subscription Save in \\\server\public\savedreports as TitleOnly ... SUCCESS</span></span><br /><br /> <span data-ttu-id="c53e2-244">Migrating history settings for report TitleOnly.rdl ...SUCCESS</span><span class="sxs-lookup"><span data-stu-id="c53e2-244">Migrating history settings for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="c53e2-245">Migrating processing options for report TitleOnly.rdl ...0 items found.</span><span class="sxs-lookup"><span data-stu-id="c53e2-245">Migrating processing options for report TitleOnly.rdl ... 0 items found.</span></span><br /><br /> <span data-ttu-id="c53e2-246">Migrating cache refresh options for report TitleOnly.rdl ...SUCCESS</span><span class="sxs-lookup"><span data-stu-id="c53e2-246">Migrating cache refresh options for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="c53e2-247">Migrating cache refresh plans for report TitleOnly.rdl:1 items found.</span><span class="sxs-lookup"><span data-stu-id="c53e2-247">Migrating cache refresh plans for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="c53e2-248">Migrating cache refresh plan titleonly_refresh735amM2F ...SUCCESS</span><span class="sxs-lookup"><span data-stu-id="c53e2-248">Migrating cache refresh plan titleonly_refresh735amM2F ... SUCCESS</span></span>|  
|<span data-ttu-id="c53e2-249">キャッシュ更新計画</span><span class="sxs-lookup"><span data-stu-id="c53e2-249">Cache refresh plans</span></span>|<span data-ttu-id="c53e2-250">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-250">Yes</span></span>|<span data-ttu-id="c53e2-251">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-251">Yes</span></span>||  
|<span data-ttu-id="c53e2-252">イメージ</span><span class="sxs-lookup"><span data-stu-id="c53e2-252">Images</span></span>|<span data-ttu-id="c53e2-253">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-253">Yes</span></span>|<span data-ttu-id="c53e2-254">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-254">Yes</span></span>||  
|<span data-ttu-id="c53e2-255">レポート パーツ</span><span class="sxs-lookup"><span data-stu-id="c53e2-255">Report parts</span></span>|<span data-ttu-id="c53e2-256">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-256">Yes</span></span>|<span data-ttu-id="c53e2-257">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-257">Yes</span></span>||  
  
##  <a name="required-permissions"></a><a name="bkmk_required_permissions"></a> <span data-ttu-id="c53e2-258">必要な権限</span><span class="sxs-lookup"><span data-stu-id="c53e2-258">Required Permissions</span></span>  
 <span data-ttu-id="c53e2-259">アイテムやリソースの読み書きに必要な権限は、スクリプトで使用されるすべてのメソッドで同じではありません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-259">The permissions required to read or write items and resources is not the same for all of the methods used in the script.</span></span> <span data-ttu-id="c53e2-260">次の表は、各アイテムまたはリソースに使用するメソッドをまとめたもので、各メソッドはそれぞれ関連するコンテンツにリンクされています。</span><span class="sxs-lookup"><span data-stu-id="c53e2-260">The following table summarizes the methods used for each item or resource and links to related content.</span></span> <span data-ttu-id="c53e2-261">必要な権限を表示するには、個々のトピックに移動してください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-261">Navigate to the individual topic to see the required permissions.</span></span> <span data-ttu-id="c53e2-262">たとえば、ListChildren メソッドのトピックでは、必要な権限が次のように示されています。</span><span class="sxs-lookup"><span data-stu-id="c53e2-262">For example the ListChildren method topic notes the required permissions of:</span></span>  
  
-   <span data-ttu-id="c53e2-263">**ネイティブ モードで必要な権限:** アイテムに対する ReadProperties</span><span class="sxs-lookup"><span data-stu-id="c53e2-263">**Native Mode Required Permissions:** ReadProperties on Item</span></span>  
  
-   <span data-ttu-id="c53e2-264">**SharePoint モードで必要な権限:** ViewListItems</span><span class="sxs-lookup"><span data-stu-id="c53e2-264">**SharePoint Mode Required Permissions:** ViewListItems</span></span>  
  
|<span data-ttu-id="c53e2-265">アイテムまたはリソース</span><span class="sxs-lookup"><span data-stu-id="c53e2-265">Item or Resource</span></span>|<span data-ttu-id="c53e2-266">source</span><span class="sxs-lookup"><span data-stu-id="c53e2-266">Source</span></span>|<span data-ttu-id="c53e2-267">移行先</span><span class="sxs-lookup"><span data-stu-id="c53e2-267">Target</span></span>|  
|----------------------|------------|------------|  
|<span data-ttu-id="c53e2-268">カタログ アイテム</span><span class="sxs-lookup"><span data-stu-id="c53e2-268">Catalog items</span></span>|<xref:ReportService2010.ReportingService2010.ListChildren%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemLink%2A>|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.SetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataSource%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateLinkedItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateFolder%2A>|  
|<span data-ttu-id="c53e2-269">Role</span><span class="sxs-lookup"><span data-stu-id="c53e2-269">Role</span></span>|<xref:ReportService2010.ReportingService2010.ListRoles%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|  
|<span data-ttu-id="c53e2-270">システム ポリシー</span><span class="sxs-lookup"><span data-stu-id="c53e2-270">System Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|  
|<span data-ttu-id="c53e2-271">スケジュール</span><span class="sxs-lookup"><span data-stu-id="c53e2-271">Schedule</span></span>|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|  
|<span data-ttu-id="c53e2-272">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="c53e2-272">Subscription</span></span>|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|  
|<span data-ttu-id="c53e2-273">キャッシュ更新計画</span><span class="sxs-lookup"><span data-stu-id="c53e2-273">Cache refresh plan</span></span>|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|  
|<span data-ttu-id="c53e2-274">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c53e2-274">Parameters</span></span>|<xref:ReportService2010.ReportingService2010.GetItemParameters%2A>|<xref:ReportService2010.ReportingService2010.SetItemParameters%2A>|  
|<span data-ttu-id="c53e2-275">実行オプション</span><span class="sxs-lookup"><span data-stu-id="c53e2-275">Execution options</span></span>|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|  
|<span data-ttu-id="c53e2-276">[キャッシュ オプション]</span><span class="sxs-lookup"><span data-stu-id="c53e2-276">Cache options</span></span>|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|  
|<span data-ttu-id="c53e2-277">履歴の設定</span><span class="sxs-lookup"><span data-stu-id="c53e2-277">History settings</span></span>|<xref:ReportService2010.ReportingService2010.GetItemHistoryOptions%2A>|<xref:ReportService2010.ReportingService2010.SetItemHistoryOptions%2A>|  
|<span data-ttu-id="c53e2-278">アイテム ポリシー</span><span class="sxs-lookup"><span data-stu-id="c53e2-278">Item Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|  
  
 <span data-ttu-id="c53e2-279">詳しくは、「 [Reporting Services のロールおよびタスクと SharePoint のグループおよび権限の比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-279">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>  
  
##  <a name="how-to-use-the-script"></a><a name="bkmk_how_to_use_the_script"></a><span data-ttu-id="c53e2-280">スクリプトの使用方法</span><span class="sxs-lookup"><span data-stu-id="c53e2-280">How to use the script</span></span>  
  
1.  <span data-ttu-id="c53e2-281">スクリプト ファイルをローカル フォルダー (c: **\rss\ssrs_migration.rss**など) にダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-281">Download the script file to a local folder, for example **c:\rss\ssrs_migration.rss**.</span></span>  
  
2.  <span data-ttu-id="c53e2-282">**管理者特権で**コマンドプロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-282">Open a command prompt **with administrative privileges**.</span></span>  
  
3.  <span data-ttu-id="c53e2-283">ssrs_migration.rss ファイルのあるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-283">Navigate to the folder containing the ssrs_migration.rss file.</span></span>  
  
4.  <span data-ttu-id="c53e2-284">シナリオに適したパラメーターを指定してコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-284">Run the command with the parameters appropriate for your scenario.</span></span>  
  
 <span data-ttu-id="c53e2-285">**基本的な例 (ネイティブ モード レポート サーバー間):**</span><span class="sxs-lookup"><span data-stu-id="c53e2-285">**Basic Example, native mode report server to native mode report server:**</span></span>  
  
 <span data-ttu-id="c53e2-286">次の例では、ネイティブ モード **Sourceserver** からネイティブ モード **Targetserver**にコンテンツを移行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-286">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
 ```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"
```
  
 <span data-ttu-id="c53e2-287">**使用上の注意:**</span><span class="sxs-lookup"><span data-stu-id="c53e2-287">**Usage notes:**</span></span>  
  
-   <span data-ttu-id="c53e2-288">スクリプトは 2 つのステップで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-288">The script runs in two steps.</span></span>  
  
     <span data-ttu-id="c53e2-289">最初のステップは監査です。移行されるアイテムのリストが返されます。2 番目のステップは移行です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-289">The first step is an audit, to return a list of items that will be migrated and the second step is the migration process.</span></span>  
  
     <span data-ttu-id="c53e2-290">移行されるアイテムを一覧表示するのみ、またはパラメーターを変更するのみの場合は、最初の **ステップの後にスクリプトをキャンセル** できます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-290">You can **cancel the script after step** one if you only want to see the possible migration list or you want to modify the parameters.</span></span> <span data-ttu-id="c53e2-291">依存設定は最初のステップで一覧表示されません。</span><span class="sxs-lookup"><span data-stu-id="c53e2-291">Dependent settings are not listed in step one.</span></span> <span data-ttu-id="c53e2-292">たとえば、レポートのキャッシュ オプションは一覧表示されません。ただし、レポート自体は一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-292">For example, the cache options of a report are not listed but the report itself is.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="c53e2-293">単に 1 つのサーバーを監査する場合は、移行元および移行先として同じサーバーを使用し、ステップ 1 の後にキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-293">If you want to just audit a single server, use the same server for source and destination and cancel after step 1</span></span>  
  
     <span data-ttu-id="c53e2-294">最初のステップで一覧表示される監査情報は、移行元と移行先の両方のネイティブ モード サーバー上の既存のロールを確認するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-294">A good use of the step 1 audit information is to review existing roles on both the source and target Native mode server.</span></span> <span data-ttu-id="c53e2-295">次に示しているのは、最初のステップである監査で表示される一覧の例です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-295">The following is an example of the step one audit list.</span></span> <span data-ttu-id="c53e2-296">スイッチ -v security="True" を使用したため、一覧に "roles" セクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c53e2-296">Notice the list includes a "roles" section because the switch-v security="True" was used:</span></span>  
  
    -   `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: Model Item Browser`  
  
         `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: CustomRole`  
  
         `Role: Model Item Browser`  
  
         `Role: My Reports`  
  
         `Role: Publisher`  
  
         `Role: Report Builder`  
  
         `Role: System Administrator`  
  
         `Role: System User`  
  
         `Retrieving system policies:`  
  
         `Retrieving system policies:`  
  
         `System policy: BUILTIN\Administrators`  
  
         `System policy: domain\user1`  
  
         `System policy: domain\ueser2`  
  
         `Retrieving schedules:`  
  
         `Schedule: theMondaySchedule`  
  
         `Retrieving catalog items. This may take a while.`  
  
         `Folder: /Data Sources`  
  
         `DataSource: /Data Sources/Aworks2012_oltp`  
  
         `Folder: /images`  
  
         `Resource: /images/Boba Fett.png`  
  
         `Resource: /images/R2-D2.png`  
  
         `Folder: /Reports`  
  
         `Report: /Reports/products`  
  
         `Report: /Reports/test`  
  
         `Report: /Reports/TitleOnly`  
  
-   <span data-ttu-id="c53e2-297">SOURCE_URL と TARGET_URL は、移行元と移行先の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポート サーバーを参照する有効なレポート サーバー URL であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-297">The SOURCE_URL and TARGET_URL must be valid report server URLs that point to the source and target [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="c53e2-298">ネイティブ モードでは、レポート サーバー URL は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c53e2-298">In native mode, a report server URL looks like the following:</span></span>  
  
    -   `http://servername/reportserver`  
  
     <span data-ttu-id="c53e2-299">SharePoint モードでは、この URL は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c53e2-299">In SharePoint mode the URL looks like the following:</span></span>  
  
    -   `http://servername/_vti_bin/reportserver`  
  
-   <span data-ttu-id="c53e2-300">SharePoint でユーザーに表示される仮想フォルダー構造は、基になっている構造と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c53e2-300">The virtual folder structure presented to the user in SharePoint might be different than the underlying one.</span></span> <span data-ttu-id="c53e2-301">ブラウザーで `http://servername/_vti_bin/reportserver` または `http://servername/sites/site_name/_vti_bin/reportserver` を開き、非仮想フォルダー構造を確認してください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-301">Open `http://servername/_vti_bin/reportserver` or `http://servername/sites/site_name/_vti_bin/reportserver` in a browser to see the non-virtual folder structure.</span></span> <span data-ttu-id="c53e2-302">この情報は、SharePoint モード サーバーの移行元フォルダーと移行先フォルダーを "/" 以外に設定するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-302">This is helpful for setting source folder and target folder to something other than "/", for a server in SharePoint mode.</span></span>  
  
-   <span data-ttu-id="c53e2-303">パスワードは移行されないため、再入力する必要があります。たとえば、保存された資格情報を使用するデータ ソースなどです。</span><span class="sxs-lookup"><span data-stu-id="c53e2-303">Passwords are not migrated, and must be re-entered, for example data sources with stored credentials.</span></span>  
  
##  <a name="parameter-description"></a><a name="bkmk_parameter_description"></a><span data-ttu-id="c53e2-304">パラメーターの説明</span><span class="sxs-lookup"><span data-stu-id="c53e2-304">Parameter Description</span></span>  
  
|<span data-ttu-id="c53e2-305">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c53e2-305">Parameter</span></span>|<span data-ttu-id="c53e2-306">説明</span><span class="sxs-lookup"><span data-stu-id="c53e2-306">Description</span></span>|<span data-ttu-id="c53e2-307">必須</span><span class="sxs-lookup"><span data-stu-id="c53e2-307">Required</span></span>|  
|---------------|-----------------|--------------|  
|<span data-ttu-id="c53e2-308">**-s** Source_URL</span><span class="sxs-lookup"><span data-stu-id="c53e2-308">**-s** Source_URL</span></span>|<span data-ttu-id="c53e2-309">移行元レポート サーバーの URL。</span><span class="sxs-lookup"><span data-stu-id="c53e2-309">URL of the source report server</span></span>|<span data-ttu-id="c53e2-310">はい</span><span class="sxs-lookup"><span data-stu-id="c53e2-310">Yes</span></span>|  
|<span data-ttu-id="c53e2-311">**-u** Domain\password **-p** password</span><span class="sxs-lookup"><span data-stu-id="c53e2-311">**-u** Domain\password **-p** password</span></span>|<span data-ttu-id="c53e2-312">移行元サーバーの資格情報。</span><span class="sxs-lookup"><span data-stu-id="c53e2-312">Credentials for source server.</span></span>|<span data-ttu-id="c53e2-313">省略可能。省略した場合は既定の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-313">OPTIONAL, default credentials are used if missing</span></span>|  
|<span data-ttu-id="c53e2-314">**-v st**="SITE"</span><span class="sxs-lookup"><span data-stu-id="c53e2-314">**-v st**="SITE"</span></span>||<span data-ttu-id="c53e2-315">省略可能。</span><span class="sxs-lookup"><span data-stu-id="c53e2-315">OPTIONAL.</span></span> <span data-ttu-id="c53e2-316">このパラメーターは SharePoint モード レポート サーバーにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-316">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="c53e2-317">**- v f**="SOURCEFOLDER"</span><span class="sxs-lookup"><span data-stu-id="c53e2-317">**- v f**="SOURCEFOLDER"</span></span>|<span data-ttu-id="c53e2-318">すべての移行の場合は "/" に設定し、部分的な移行の場合は "/フォルダー/サブフォルダー" に設定します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-318">Set to "/" for migrating everything, or to something like "/folder/subfolder" for partial migration.</span></span> <span data-ttu-id="c53e2-319">指定したフォルダー内のすべてのコンテンツがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-319">Everything within this folder will be copied</span></span>|<span data-ttu-id="c53e2-320">省略可能。既定値は "/" です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-320">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="c53e2-321">**-v ts**="TARGET_URL"</span><span class="sxs-lookup"><span data-stu-id="c53e2-321">**-v ts**="TARGET_URL"</span></span>|<span data-ttu-id="c53e2-322">移行先 RS サーバーの URL。</span><span class="sxs-lookup"><span data-stu-id="c53e2-322">'URL of the target RS server"</span></span>||  
|<span data-ttu-id="c53e2-323">**-v tu**="domain\username" **-v tp**="password"</span><span class="sxs-lookup"><span data-stu-id="c53e2-323">**-v tu**="domain\username" **-v tp**="password"</span></span>|<span data-ttu-id="c53e2-324">ターゲット サーバーの資格情報。</span><span class="sxs-lookup"><span data-stu-id="c53e2-324">'Credentials for target server.</span></span>|<span data-ttu-id="c53e2-325">省略可能。省略した場合は既定の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-325">OPTIONAL, default credentials are used if missing.</span></span> <span data-ttu-id="c53e2-326">**注:** ユーザーは共有スケジュールの "作成者" およびレポート アイテムの "変更元" アカウントとしてターゲット サーバーで一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-326">**Note:** the user will be listed as the "creator" of shared schedules and "modified by" account for report items, in the target server.</span></span>|  
|<span data-ttu-id="c53e2-327">**-v tst**="SITE"</span><span class="sxs-lookup"><span data-stu-id="c53e2-327">**-v tst**="SITE"</span></span>||<span data-ttu-id="c53e2-328">省略可能。</span><span class="sxs-lookup"><span data-stu-id="c53e2-328">OPTIONAL.</span></span> <span data-ttu-id="c53e2-329">このパラメーターは SharePoint モード レポート サーバーにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-329">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="c53e2-330">**-v tf** ="TARGETFOLDER"</span><span class="sxs-lookup"><span data-stu-id="c53e2-330">**-v tf** ="TARGETFOLDER"</span></span>|<span data-ttu-id="c53e2-331">ルート レベルに移行する場合は "/" に設定します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-331">'Set to "/" for migrating into the root level.</span></span> <span data-ttu-id="c53e2-332">既存のフォルダーにコピーする場合は "/フォルダー/サブフォルダー" に設定します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-332">Set to "/folder/subfolder" to copy into a that already exists.</span></span> <span data-ttu-id="c53e2-333">"SOURCEFOLDER" 内のすべてのコンテンツが "TARGETFOLDER" にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-333">Everything within "SOURCEFOLDER" will be copied into "TARGETFOLDER.</span></span>|<span data-ttu-id="c53e2-334">省略可能。既定値は "/" です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-334">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="c53e2-335">**-v security**= "True/False"</span><span class="sxs-lookup"><span data-stu-id="c53e2-335">**-v security**= "True/False"</span></span>|<span data-ttu-id="c53e2-336">"False" に設定した場合、移行先カタログ アイテムには移行先システムの設定に従ってセキュリティ設定が継承されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-336">If set to "False", destination catalog items will inherit security setting according to the settings of the target system.</span></span> <span data-ttu-id="c53e2-337">この設定は、ネイティブ モードから SharePoint モードへなど、異なるモードのレポート サーバー間の移行にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-337">This is the recommended setting for migrations between different report server types, for example native mode to SharePoint mode.</span></span> <span data-ttu-id="c53e2-338">"True" に設定した場合、スクリプトはセキュリティ設定を移行しようとします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-338">If set to "True", the script attempts to migrate security settings.</span></span>|<span data-ttu-id="c53e2-339">省略可能。既定値は "False" です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-339">OPTIONAL, default is "False".</span></span>|  
  
##  <a name="more-examples"></a><a name="bkmk_more_examples"></a><span data-ttu-id="c53e2-340">その他の例</span><span class="sxs-lookup"><span data-stu-id="c53e2-340">More Examples</span></span>  
  
###  <a name="native-mode-report-server-to-native-mode-report-server"></a><a name="bkmk_native_2_native"></a><span data-ttu-id="c53e2-341">ネイティブモードのレポートサーバーからネイティブモードのレポートサーバーへ</span><span class="sxs-lookup"><span data-stu-id="c53e2-341">Native Mode Report Server to Native Mode Report Server</span></span>  
 <span data-ttu-id="c53e2-342">次の例では、ネイティブ モード **Sourceserver** からネイティブ モード **Targetserver**にコンテンツを移行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-342">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"  
```  
  
 <span data-ttu-id="c53e2-343">次の例では、security スイッチを追加します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-343">The following example adds the security switch:</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password" -v security="True"  
```  
  
###  <a name="native-mode-to-sharepoint-mode---root-site"></a><a name="bkmk_native_2_sharepoint_root"></a> <span data-ttu-id="c53e2-344">ネイティブ モードから SharePoint モード (ルート サイト)</span><span class="sxs-lookup"><span data-stu-id="c53e2-344">Native Mode to SharePoint Mode - root site</span></span>  
 <span data-ttu-id="c53e2-345">次の例では、ネイティブ モード **SourceServer** から SharePoint モード サーバー **TargetServer**上の "ルート サイト" にコンテンツを移行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-345">The following example migrates content from a native mode **SourceServer** to the "root site " on a SharePoint mode server **TargetServer**.</span></span> <span data-ttu-id="c53e2-346">ネイティブ モード サーバー上の "Reports" および "Data Sources" フォルダーは SharePoint 配置上の新しいライブラリとして移行されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-346">The "Reports" and "Data Sources" folders on the native mode server as migrated as new libraries on the SharePoint deployment.</span></span>  
  
 <span data-ttu-id="c53e2-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span><span class="sxs-lookup"><span data-stu-id="c53e2-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/_vti_bin/ReportServer" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_native_2_sharepoint_with_site"></a> <span data-ttu-id="c53e2-348">ネイティブ モードから SharePoint モード ("bi" サイト コレクション)</span><span class="sxs-lookup"><span data-stu-id="c53e2-348">Native mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="c53e2-349">次の例では、ネイティブ モード サーバーから、"sites/bi" サイト コレクションおよび共有ドキュメント ライブラリを含む SharePoint サーバーにコンテンツを移行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-349">The following example migrates content from a native mode server to a SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span> <span data-ttu-id="c53e2-350">スクリプトは移行先ドキュメント ライブラリ内にフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-350">The script creates folders in document the destination library.</span></span> <span data-ttu-id="c53e2-351">たとえば、移行先ドキュメント ライブラリ内に "Reports" および "Data Sources" フォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-351">For example, the script will create a "Reports" and "Data Sources" folders in the target document library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="sharepoint-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_sharepoint_2_sharepoint"></a> <span data-ttu-id="c53e2-352">SharePoint モードから SharePoint モード ("bi" サイト コレクション)</span><span class="sxs-lookup"><span data-stu-id="c53e2-352">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="c53e2-353">この例では、次のようにコンテンツを移行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-353">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="c53e2-354">"sites/bi" サイト コレクションおよび共有ドキュメント ライブラリを含む SharePoint サーバー **SourceServer** から。</span><span class="sxs-lookup"><span data-stu-id="c53e2-354">From a SharePoint server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="c53e2-355">"sites/bi" サイト コレクションおよび共有ドキュメント ライブラリを含む SharePoint サーバー **TargetServer** に。</span><span class="sxs-lookup"><span data-stu-id="c53e2-355">To a **TargetServer** SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/_vti_bin/reportserver -v st="sites/bi" -v f="Shared Documents" -u Domain\User1 -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-native-mode---azure-virtual-machine"></a><a name="bkmk_native_to_native_Azure_vm"></a><span data-ttu-id="c53e2-356">ネイティブモードからネイティブモード (Azure 仮想マシン)</span><span class="sxs-lookup"><span data-stu-id="c53e2-356">Native Mode to Native Mode - Azure Virtual Machine</span></span>  
 <span data-ttu-id="c53e2-357">この例では、次のようにコンテンツを移行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-357">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="c53e2-358">ネイティブ モード レポート サーバー **SourceServer**から。</span><span class="sxs-lookup"><span data-stu-id="c53e2-358">From a Native mode report server **SourceServer**.</span></span>  
  
-   <span data-ttu-id="c53e2-359">Azure 仮想マシン上で実行されているネイティブ モード レポート サーバー **TargetServer** に。</span><span class="sxs-lookup"><span data-stu-id="c53e2-359">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="c53e2-360">**TargetServer は Sourceserver**のドメインに参加して**SourceServer**おらず、 **User2**は Azure 仮想マシン**TargetServer**の管理者です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-360">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Password2"  
```  
  
> [!TIP]  
>  <span data-ttu-id="c53e2-361">Windows PowerShell を使用して Azure 仮想マシン上に [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポート サーバーを作成する方法については、「[PowerShell を使用したネイティブ モードのレポート サーバーを含む Azure VM の作成](https://msdn.microsoft.com/library/dn449661.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c53e2-361">For information on how to use Windows PowerShell to create [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report servers on Azure virtual machines, see [Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/dn449661.aspx).</span></span>  
  
##  <a name="sharepoint-mode--bi-site-collection-to-a-native-mode-server-on-azure-virtual-machine"></a><a name="bkmk_sharepoint_site_to_native_Azure_vm"></a><span data-ttu-id="c53e2-362">SharePoint モード-Azure 仮想マシン上のネイティブモードサーバーへの ' bi ' サイトコレクション</span><span class="sxs-lookup"><span data-stu-id="c53e2-362">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>  
 <span data-ttu-id="c53e2-363">この例では、次のようにコンテンツを移行します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-363">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="c53e2-364">"sites/bi" サイト コレクションおよび共有ドキュメント ライブラリを含む SharePoint モード レポート サーバー **SourceServer** から。</span><span class="sxs-lookup"><span data-stu-id="c53e2-364">From a SharePoint mode report server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="c53e2-365">Azure 仮想マシン上で実行されているネイティブ モード レポート サーバー **TargetServer** に。</span><span class="sxs-lookup"><span data-stu-id="c53e2-365">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="c53e2-366">**TargetServer は Sourceserver**のドメインに参加して**SourceServer**おらず、 **User2**は Azure 仮想マシン**TargetServer**の管理者です。</span><span class="sxs-lookup"><span data-stu-id="c53e2-366">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://uetesta02/_vti_bin/reportserver -u user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Passowrd2"  
```  
  
##  <a name="verification"></a><a name="bkmk_verification"></a><span data-ttu-id="c53e2-367">段階</span><span class="sxs-lookup"><span data-stu-id="c53e2-367">Verification</span></span>  
 <span data-ttu-id="c53e2-368">このセクションは、コンテンツとポリシーが正常に移行されたことを確認するために移行先サーバーで実行する一部の手順をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="c53e2-368">The section summarizes some of the steps to take on the destination server to verify content and policies were successfully migrated.</span></span>  
  
### <a name="schedules"></a><span data-ttu-id="c53e2-369">スケジュール</span><span class="sxs-lookup"><span data-stu-id="c53e2-369">Schedules</span></span>  
 <span data-ttu-id="c53e2-370">ターゲット サーバーでスケジュールを確認するには:</span><span class="sxs-lookup"><span data-stu-id="c53e2-370">To verify schedules on the target server:</span></span>  
  
 <span data-ttu-id="c53e2-371">**ネイティブモード**</span><span class="sxs-lookup"><span data-stu-id="c53e2-371">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="c53e2-372">移行先サーバーでレポート マネージャーを参照します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-372">Browse to Report Manager on the destination server.</span></span>  
  
2.  <span data-ttu-id="c53e2-373">トップ メニューの **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-373">Click **Site Settings** on the top menu.</span></span>  
  
3.  <span data-ttu-id="c53e2-374">左ペインで **[スケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-374">Click **Schedules** in the left pane.</span></span>  
  
 <span data-ttu-id="c53e2-375">**SharePoint モード:**</span><span class="sxs-lookup"><span data-stu-id="c53e2-375">**SharePoint Mode:**</span></span>  
  
1.  <span data-ttu-id="c53e2-376">**[サイトの設定]** を参照します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-376">Browse to **Site settings**.</span></span>  
  
2.  <span data-ttu-id="c53e2-377">**[Reporting Services]** グループで、 **[共有スケジュールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-377">In the **Reporting Services** group, click **Manage Shared Schedules**.</span></span>  
  
### <a name="roles-and-groups"></a><span data-ttu-id="c53e2-378">ロールとグループ</span><span class="sxs-lookup"><span data-stu-id="c53e2-378">Roles and Groups</span></span>  
 <span data-ttu-id="c53e2-379">**ネイティブモード**</span><span class="sxs-lookup"><span data-stu-id="c53e2-379">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="c53e2-380">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、ネイティブ モード レポート サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-380">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to your native mode report server.</span></span>  
  
2.  <span data-ttu-id="c53e2-381">**オブジェクトエクスプローラー** [**セキュリティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-381">In **Object Explorer** click **Security**.</span></span>  
  
3.  <span data-ttu-id="c53e2-382">**[ロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-382">Click **Roles**.</span></span>  
  
##  <a name="troubleshooting"></a><a name="bkmk_troubleshoot"></a> <span data-ttu-id="c53e2-383">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c53e2-383">Troubleshooting</span></span>  
 <span data-ttu-id="c53e2-384">より詳細な情報が表示されるようにするには、トレース フラグ **-t** を使用します。</span><span class="sxs-lookup"><span data-stu-id="c53e2-384">Use the trace flag **-t** to receive more information.</span></span> <span data-ttu-id="c53e2-385">たとえば、スクリプトを実行し、次のようなメッセージが表示されたとします。</span><span class="sxs-lookup"><span data-stu-id="c53e2-385">For example, if you run the script and see a message similar to the following</span></span>  
  
-   <span data-ttu-id="c53e2-386">サーバーに接続できませんでした: http:// \<servername> /Reportserver2010.4 asmx</span><span class="sxs-lookup"><span data-stu-id="c53e2-386">Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx</span></span>  
  
 <span data-ttu-id="c53e2-387">**-T**フラグを使用してスクリプトをもう一度実行すると、次のようなメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c53e2-387">Run the script again with the **-t** flag, to see a message similar to the following:</span></span>  
  
-   <span data-ttu-id="c53e2-388">System.exception: サーバーに接続できませんでした: http:// \<servername> /Reportserver/Reportservice2010.4---> WebException: **http ステータス 401: 許可されていない要求が失敗しまし**た。</span><span class="sxs-lookup"><span data-stu-id="c53e2-388">System.Exception: Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx ---> System.Net.WebException: **The request failed with HTTP status 401: Unauthorized**.</span></span>   <span data-ttu-id="c53e2-389">System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse (SoapClientMessage メッセージ、WebResponse 応答、Stream responseStream, Boolean asyncCall) System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke (文字列であります。methodName、オブジェクトのパラメーター) (文字列 url 文字列のユーザー名、文字列パスワード Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService で Microsoft.SqlServer.ReportingServices2010.ReportingService2010.IsSSLRequired() で、文字列ドメイン、Int32 タイムアウト) で Microsoft.ReportingServices.ScriptHost.ScriptHost.DetermineServerUrlSecurity()---内部例外スタック トレースの終わり--</span><span class="sxs-lookup"><span data-stu-id="c53e2-389">at System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse(SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall)   at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke(String methodName, Object[] parameters)   at Microsoft.SqlServer.ReportingServices2010.ReportingService2010.IsSSLRequired()   at Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService(String url, String userName, String password, String domain, Int32 timeout)   at Microsoft.ReportingServices.ScriptHost.ScriptHost.DetermineServerUrlSecurity()   --- End of inner exception stack trace ---</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53e2-390">参照</span><span class="sxs-lookup"><span data-stu-id="c53e2-390">See Also</span></span>  
 <span data-ttu-id="c53e2-391">[RS.exe ユーティリティ &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c53e2-391">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span></span>  
 [<span data-ttu-id="c53e2-392">Reporting Services のロールおよびタスクと SharePoint のグループおよび権限の比較</span><span class="sxs-lookup"><span data-stu-id="c53e2-392">Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions</span></span>](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)  
