---
title: 'チェックリスト: PowerShell を使用して PowerPivot for SharePoint | を確認するMicrosoft Docs'
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 73a13f05-3450-411f-95f9-4b6167cc7607
author: minewiskan
ms.author: owend
ms.openlocfilehash: 001b3fae82851b9ec08b0383bb3db9e6d011ae32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713638"
---
# <a name="checklist-use-powershell-to-verify-powerpivot-for-sharepoint"></a><span data-ttu-id="93123-102">チェック リスト: PowerShell を使用して PowerPivot for SharePoint を確認する</span><span class="sxs-lookup"><span data-stu-id="93123-102">CheckList: Use PowerShell to Verify PowerPivot for SharePoint</span></span>
  <span data-ttu-id="93123-103">[!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] のインストール操作や復旧操作を完了するには、信頼性の高い検証テストに合格する必要があります。このテストでは、サービスとデータが操作可能であるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="93123-103">No [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation or recovery operation is complete without a solid verification test pass that confirms your services and data are operational.</span></span> <span data-ttu-id="93123-104">この記事では、Windows PowerShell を使用してこのテストの手順を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93123-104">In this article, we show you how to perform these steps using Windows PowerShell.</span></span> <span data-ttu-id="93123-105">各手順は個別のセクションで説明されています。これにより、特定のタスクを直接参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="93123-105">We put each step into its own section so that you can go straight to specific tasks.</span></span> <span data-ttu-id="93123-106">たとえば、メンテナンスやバックアップでサービス アプリケーションとコンテンツ データベースの名前の確認をスケジュールする必要がある場合は、このトピックの「 [データベース](#bkmk_databases) 」セクションのスクリプトを実行し、これらの名前を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="93123-106">For example, run the script in the [Databases](#bkmk_databases) section of this topic to verify the name of the service application and content databases if you want to schedule them for maintenance or backup.</span></span>

|||
|-|-|
|<span data-ttu-id="93123-107">![PowerShell 関連コンテンツ](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")</span><span class="sxs-lookup"><span data-stu-id="93123-107">![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>|<span data-ttu-id="93123-108">完全な PowerShell スクリプトは、トピックの最後に記載されています。</span><span class="sxs-lookup"><span data-stu-id="93123-108">A full PowerShell script is included at the bottom of the topic.</span></span> <span data-ttu-id="93123-109">[!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] の完全な配置を監査するためのカスタム スクリプトを構築するには、完全なスクリプトをひな形として使用します。</span><span class="sxs-lookup"><span data-stu-id="93123-109">Use the full script as a starting point to build a custom script for auditing your full [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] deployment.</span></span>|

||
|-|
|<span data-ttu-id="93123-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]** Sharepoint 2013 &#124; sharepoint 2010</span><span class="sxs-lookup"><span data-stu-id="93123-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="93123-111">**このトピックについて**: 次の目次に含まれている箇条書きの行頭文字が付いた項目は、ダイアグラムの各エリアに対応しています。</span><span class="sxs-lookup"><span data-stu-id="93123-111">**In this topic**: The lettered items in the following the TOC correspond to areas of the diagram.</span></span> <span data-ttu-id="93123-112">ダイアグラムでは、次を説明します。</span><span class="sxs-lookup"><span data-stu-id="93123-112">The diagram illustrates the</span></span>

|||
|-|-|
|[<span data-ttu-id="93123-113">PowerShell 環境を準備する</span><span class="sxs-lookup"><span data-stu-id="93123-113">Prepare your PowerShell environment</span></span>](#bkmk_prerequisites)<br /><br /> [<span data-ttu-id="93123-114">現象と推奨される操作</span><span class="sxs-lookup"><span data-stu-id="93123-114">Symptoms and Recommended Actions</span></span>](#bkmk_symptoms)<br /><br /> <span data-ttu-id="93123-115">**(A)** [Analysis Services の Windows サービス](#bkmk_windows_service)</span><span class="sxs-lookup"><span data-stu-id="93123-115">**(A)** [Analysis Services Windows Service](#bkmk_windows_service)</span></span><br /><br /> <span data-ttu-id="93123-116">**(B)** [get-powerpivotsystemservice と get-powerpivotengineservice](#bkmk_engine_and_system_service)</span><span class="sxs-lookup"><span data-stu-id="93123-116">**(B)** [PowerPivotSystemService and PowerPivotEngineService](#bkmk_engine_and_system_service)</span></span><br /><br /> <span data-ttu-id="93123-117">**(C)** [PowerPivot サービス アプリケーションとプロキシ](#bkmk_powerpivot_service_application)</span><span class="sxs-lookup"><span data-stu-id="93123-117">**(C)** [PowerPivot Service Application(s) and proxies](#bkmk_powerpivot_service_application)</span></span><br /><br /> <span data-ttu-id="93123-118">**(D)** [データベース](#bkmk_databases)</span><span class="sxs-lookup"><span data-stu-id="93123-118">**(D)** [Databases](#bkmk_databases)</span></span><br /><br /> [<span data-ttu-id="93123-119">SharePoint 機能</span><span class="sxs-lookup"><span data-stu-id="93123-119">SharePoint Features</span></span>](#bkmk_features)<br /><br /> [<span data-ttu-id="93123-120">タイマージョブ</span><span class="sxs-lookup"><span data-stu-id="93123-120">Timer Jobs</span></span>](#bkmk_timer_jobs)<br /><br /> [<span data-ttu-id="93123-121">正常性ルール</span><span class="sxs-lookup"><span data-stu-id="93123-121">Health Rules</span></span>](#bkmk_health_rules)<br /><br /> <span data-ttu-id="93123-122">**(E)** [Windows と ULS のログ](#bkmk_logs)</span><span class="sxs-lookup"><span data-stu-id="93123-122">**(E)** [Windows and ULS Logs](#bkmk_logs)</span></span><br /><br /> [<span data-ttu-id="93123-123">MSOLAP プロバイダー</span><span class="sxs-lookup"><span data-stu-id="93123-123">MSOLAP Provider</span></span>](#bkmk_msolap)<br /><br /> [<span data-ttu-id="93123-124">ADOMD.Net クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="93123-124">ADOMD.Net client Library</span></span>](#bkmk_adomd)<br /><br /> [<span data-ttu-id="93123-125">正常性データの収集ルール</span><span class="sxs-lookup"><span data-stu-id="93123-125">Health Data Collection Rules</span></span>](#bkmk_health_collection)<br /><br /> [<span data-ttu-id="93123-126">'83'5c</span><span class="sxs-lookup"><span data-stu-id="93123-126">Solutions</span></span>](#bkmk_solutions)<br /><br /> [<span data-ttu-id="93123-127">手動による検証手順</span><span class="sxs-lookup"><span data-stu-id="93123-127">Manual Verification Steps</span></span>](#bkmk_manual)<br /><br /> [<span data-ttu-id="93123-128">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="93123-128">More Resources</span></span>](#bkmk_more_resources)<br /><br /> [<span data-ttu-id="93123-129">完全な PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="93123-129">Full PowerShell Script</span></span>](#bkmk_full_script)|<span data-ttu-id="93123-130">![PowerPivot の PowerShell による検証](../../../sql-server/install/media/ssas-powershell-component-verification.png "PowerPivot の PowerShell による検証")</span><span class="sxs-lookup"><span data-stu-id="93123-130">![powershell verification of powerpivot](../../../sql-server/install/media/ssas-powershell-component-verification.png "powershell verification of powerpivot")</span></span>|

##  <a name="prepare-your-powershell-environment"></a><a name="bkmk_prerequisites"></a> <span data-ttu-id="93123-131">PowerShell 環境を準備する</span><span class="sxs-lookup"><span data-stu-id="93123-131">Prepare your PowerShell environment</span></span>
 <span data-ttu-id="93123-132">このセクションの手順では、PowerShell 環境を準備します。</span><span class="sxs-lookup"><span data-stu-id="93123-132">The steps in this section prepare your PowerShell environment.</span></span> <span data-ttu-id="93123-133">この手順は必須ではありませんが、スクリプト環境が現在どのように構成されているかに応じて必要になります。</span><span class="sxs-lookup"><span data-stu-id="93123-133">The steps may not be required, depending on how your scripting environment is currently configured.</span></span>

 <span data-ttu-id="93123-134">**PowerShell の権限**</span><span class="sxs-lookup"><span data-stu-id="93123-134">**PowerShell Permissions**</span></span>

 <span data-ttu-id="93123-135">**管理者特権**を使用して、PowerShell ウィンドウまたは PowerShell ISE (Integrated Scripting Environment) を開きます。</span><span class="sxs-lookup"><span data-stu-id="93123-135">Open a Powershell window or the PowerShell ISE (Integrated Scripting Environment) with **administrative privileges**.</span></span> <span data-ttu-id="93123-136">コマンドの実行時に管理者特権がないと、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="93123-136">If you do not have administrative privileges when you run commands, you will see an error message similar to the following:</span></span>

 <span data-ttu-id="93123-137">Get-SPLogEvent: このコマンドレットを実行するには、コンピューター **管理者の権限** が必要です。</span><span class="sxs-lookup"><span data-stu-id="93123-137">Get-SPLogEvent : You need to have Machine **administrator privileges** to run this cmdlet.</span></span>

 <span data-ttu-id="93123-138">**SharePoint および [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** モジュール</span><span class="sxs-lookup"><span data-stu-id="93123-138">**SharePoint and [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** Module</span></span>

 <span data-ttu-id="93123-139">SharePoint 関連のコマンドレットを実行したときに次のようなエラー メッセージが表示された場合は、Add-PSSnapin コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="93123-139">If you see an error message similar to the following when you run SharePoint related cmdlets, run the Add-PSSnapin command:</span></span>

 <span data-ttu-id="93123-140">用語 'Get-PowerPivotSystemService' **は、コマンドレット**、関数、スクリプト ファイル、または操作可能なプログラムの名前として認識されません。</span><span class="sxs-lookup"><span data-stu-id="93123-140">The term 'Get-PowerPivotSystemService' **is not recognized as the name of a cmdlet**, function, script file, or operable program.</span></span> <span data-ttu-id="93123-141">名前が正しく記述されていることを確認し、パスが含まれている場合はそのパスが正しいことを確認してから、再試行してください。</span><span class="sxs-lookup"><span data-stu-id="93123-141">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>

```
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0
```

 <span data-ttu-id="93123-142">**Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="93123-142">**Windows PowerShell**</span></span>

 <span data-ttu-id="93123-143">PowerShell ISE の詳細については、「 [Windows PowerShell ISE の概要](https://technet.microsoft.com/library/dd315244.aspx) 」と「 [Windows Powershell を使用して SharePoint 2013 を管理する](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-143">For more information on the PowerShell ISE, see [Introducing the Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx) and [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx).</span></span>

|||
|-|-|
|<span data-ttu-id="93123-144">![SharePoint アプリケーションの全般設定での PowerPivot](../../../sql-server/install/media/ssas-powerpivot-logo.png "SharePoint アプリケーションの全般設定での PowerPivot")</span><span class="sxs-lookup"><span data-stu-id="93123-144">![powerpivot in sharepoint general application set](../../../sql-server/install/media/ssas-powerpivot-logo.png "powerpivot in sharepoint general application set")</span></span>|<span data-ttu-id="93123-145">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理ダッシュボードを使用することで、サーバーの全体管理の大半のコンポーネントを必要に応じて確認できます。</span><span class="sxs-lookup"><span data-stu-id="93123-145">You can optionally verify a majority of the components in Central Administration, using the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] management dashboard.</span></span> <span data-ttu-id="93123-146">サーバーの全体管理でダッシュボードを開くには、 **[アプリケーションの全般設定]** をクリックし、 **[PowerPivot]** の **[管理ダッシュボード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="93123-146">To open the dashboard in Central Administration, click **General Application Settings**, and then click **Management Dashboard** in the **PowerPivot**.</span></span> <span data-ttu-id="93123-147">ダッシュボードの詳細については、「 [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-147">For more information on the dashboard, see [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).</span></span>|

##  <a name="symptoms-and-recommended-actions"></a><a name="bkmk_symptoms"></a> <span data-ttu-id="93123-148">現象と推奨される操作</span><span class="sxs-lookup"><span data-stu-id="93123-148">Symptoms and Recommended Actions</span></span>
 <span data-ttu-id="93123-149">次の表は、現象や問題、および問題解決に役立つこのトピックの推奨されるセクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="93123-149">The following table is a list of symptoms or issues and the suggested section of this topic to consult to help you resolve the issue.</span></span>

|<span data-ttu-id="93123-150">症状</span><span class="sxs-lookup"><span data-stu-id="93123-150">Symptom</span></span>|<span data-ttu-id="93123-151">参照セクション</span><span class="sxs-lookup"><span data-stu-id="93123-151">See section</span></span>|
|-------------|-----------------|
|<span data-ttu-id="93123-152">データ更新が実行されていない</span><span class="sxs-lookup"><span data-stu-id="93123-152">Data refresh is not running</span></span>|<span data-ttu-id="93123-153">「 [Timer Jobs](#bkmk_timer_jobs) 」のセクションを参照して、 **"Online PowerPivot Data Refresh Timer Job"** がオンラインになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-153">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Online PowerPivot Data Refresh Timer Job** is online.</span></span>|
|<span data-ttu-id="93123-154">管理ダッシュボードのデータが古くなっている</span><span class="sxs-lookup"><span data-stu-id="93123-154">Management dashboard data is old</span></span>|<span data-ttu-id="93123-155">「 [タイマー ジョブ](#bkmk_timer_jobs) 」のセクションを参照して、 **"Management Dashboard Processing Timer Job"** がオンラインになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-155">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Management Dashboard Processing Timer Job** is online.</span></span>|
|<span data-ttu-id="93123-156">管理ダッシュボードの一部の機能に関する問題</span><span class="sxs-lookup"><span data-stu-id="93123-156">Some portions of the Management Dashboard</span></span>|<span data-ttu-id="93123-157">(Excel Services または PowerPivot for SharePoint のない) サーバーの全体管理のトポロジを持つファームに PowerPivot for SharePoint をインストールする場合に、PowerPivot 管理ダッシュボードの組み込みレポートへのフル アクセスが必要なときは、Microsoft ADOMD.NET クライアント ライブラリをダウンロードしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93123-157">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, you must download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="93123-158">ダッシュボードの一部のレポートでは、ADOMD.NET を使用して、ファームの PowerPivot クエリ処理およびサーバーの状態に関するレポート データを提供する内部データにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="93123-158">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span> <span data-ttu-id="93123-159">セクション「 [ADOMD.Net クライアント ライブラリ](#bkmk_adomd) 」およびトピック「 [サーバーの全体管理を実行している Web フロントエンド サーバーに ADOMD.NET をインストールする方法](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-159">See the section [ADOMD.Net client Library](#bkmk_adomd) and the topic [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>|
|\<future content>||

##  <a name="analysis-services-windows-service"></a><a name="bkmk_windows_service"></a> <span data-ttu-id="93123-160">Analysis Services の Windows サービス</span><span class="sxs-lookup"><span data-stu-id="93123-160">Analysis Services Windows Service</span></span>
 <span data-ttu-id="93123-161">このセクションのスクリプトでは、SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスを検証します。</span><span class="sxs-lookup"><span data-stu-id="93123-161">The script in this section verifies the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="93123-162">サービスが **実行されている**ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-162">Verify the service is **running**.</span></span>

```powershell
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name              DisplayName                                Status
----              -----------                                ------
MSOLAP$POWERPIVOT SQL Server Analysis Services (POWERPIVOT) Running
```

##  <a name="powerpivotsystemservice-and-powerpivotengineservice"></a><a name="bkmk_engine_and_system_service"></a><span data-ttu-id="93123-163">Get-powerpivotsystemservice と Get-powerpivotengineservice</span><span class="sxs-lookup"><span data-stu-id="93123-163">PowerPivotSystemService and PowerPivotEngineService</span></span>
 <span data-ttu-id="93123-164">このセクションのスクリプトでは、 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] System サービスを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-164">The scripts in this section verify the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] system services.</span></span> <span data-ttu-id="93123-165">SharePoint 2013 の配置では 1 つのシステム サービスが存在し、SharePoint 2010 の配置では 2 つサービスが存在します。</span><span class="sxs-lookup"><span data-stu-id="93123-165">There is one system service for a SharePoint 2013 deployment and two services for a SharePoint 2010 deployment.</span></span>

 <span data-ttu-id="93123-166">**PowerPivotSystemService**</span><span class="sxs-lookup"><span data-stu-id="93123-166">**PowerPivotSystemService**</span></span>

 <span data-ttu-id="93123-167">状態が**オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-167">Verify the Status is **Online**.</span></span>

```powershell
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                  Status Applications                             Farm
--------                                  ------ ------------                             ----
SQL Server PowerPivot Service Application Online {Default PowerPivot Service Application} SPFarm Name=SharePoint_Config_77d8ab0744a34e8aa27c806a2b8c760c
```

 <span data-ttu-id="93123-168">**Get-powerpivotengineservice**</span><span class="sxs-lookup"><span data-stu-id="93123-168">**PowerPivotEngineService**</span></span>

> [!NOTE]
>  <span data-ttu-id="93123-169">SharePoint 2013 を使用している場合は、**このセクションを省略してください** 。</span><span class="sxs-lookup"><span data-stu-id="93123-169">**Skip this script if** you are using SharePoint 2013.</span></span> <span data-ttu-id="93123-170">PowerPivotEngineService は、SharePoint 2013 の配置には含まれません。</span><span class="sxs-lookup"><span data-stu-id="93123-170">The PowerPivotEngineService is not part of a SharePoint 2013 deployment.</span></span> <span data-ttu-id="93123-171">SharePoint 2013 で Get PowerPivot**Engine**Service コマンドレットを実行すると、次のようなエラーメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="93123-171">If you run the Get-PowerPivot**Engine**Service cmdlet on SharePoint 2013, you will see an error message similar to the following.</span></span> <span data-ttu-id="93123-172">このエラー メッセージは、このトピックの前提条件に関するセクションで説明されている Add-PSSnapin コマンドを実行した場合でも返されます。</span><span class="sxs-lookup"><span data-stu-id="93123-172">This error message is returned even if you have run the Add-PSSnapin command described in the prerequisites section of this topic.</span></span>
> 
>  <span data-ttu-id="93123-173">用語 'Get-PowerPivotEngineService' は、コマンドレットの名前として認識されません</span><span class="sxs-lookup"><span data-stu-id="93123-173">The term 'Get-PowerPivotEngineService' is not recognized as the name of a cmdlet</span></span>

 <span data-ttu-id="93123-174">SharePoint 2010 の配置では、状態が **オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-174">In a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName  : SQL Server Analysis Services
Status    : Online
Name      : MSOLAP$POWERPIVOT
Instances : {POWERPIVOT}
Farm      : SPFarm Name=SharePoint_Config
```

##  <a name="powerpivot-service-applications-and-proxies"></a><a name="bkmk_powerpivot_service_application"></a><span data-ttu-id="93123-175">PowerPivot サービスアプリケーションとプロキシ</span><span class="sxs-lookup"><span data-stu-id="93123-175">PowerPivot Service Application(s) and proxies</span></span>
 <span data-ttu-id="93123-176">状態が **オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-176">Verify the status is **Online**.</span></span> <span data-ttu-id="93123-177">Excel Services アプリケーションはサービス アプリケーション データベースを使用しないため、コマンドレットはデータベース名を返しません。</span><span class="sxs-lookup"><span data-stu-id="93123-177">The Excel Services Application does not use a service application database and therefore the cmdlet does not return a database name.</span></span> <span data-ttu-id="93123-178">このトピックのデータベースに関するセクションでデータベースがオンラインであることを確認できるように、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーションで使用されているデータベースを把握しておいてください。</span><span class="sxs-lookup"><span data-stu-id="93123-178">Note the database used by the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application so you can verify the database is online in the database section later in this topic.</span></span>

 <span data-ttu-id="93123-179">**PowerPivot サービス アプリケーションと Excel サービス アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="93123-179">**PowerPivot and Excel Service Application(s)**</span></span>

 <span data-ttu-id="93123-180">SharePoint 2010 の配置では、状態が **オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-180">For a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename, DisplayName, status
```

```Output
TypeName          : PowerPivot Service Application
Name              : PowerPivotServiceApplication1
Status            : Online
UnattendedAccount : PowerPivotUnattendedAccount
ApplicationPool   : SPIisWebServiceApplicationPool Name=sqlbi_serviceapp
Farm              : SPFarm Name=SharePoint_Config
Database          : GeminiServiceDatabase Name=PowerPivotServiceApplication1_19648f3f2c944e27acdc6c20aab8487a

TypeName    : Excel Services Application Web Service Application
DisplayName : Excel Services Application
Status      : Online
```

 <span data-ttu-id="93123-181">**サービスアプリケーションプール**</span><span class="sxs-lookup"><span data-stu-id="93123-181">**Service Application Pool**</span></span>

> [!NOTE]
>  <span data-ttu-id="93123-182">次のコード サンプルでは、最初に既定の [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] サービス アプリケーションの applicationpool プロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="93123-182">The following code sample first returns the applicationpool property of the default [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] service application.</span></span> <span data-ttu-id="93123-183">文字列から名前が解析され、その名前を使用して、アプリケーション プール オブジェクトの状態が取得されます。</span><span class="sxs-lookup"><span data-stu-id="93123-183">The name is parsed from the string and used to get the status of the application pool object.</span></span>
> 
>  <span data-ttu-id="93123-184">状態が**オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-184">Verify the Status is **Online**.</span></span> <span data-ttu-id="93123-185">状態がオンラインでない場合、またはサイトを参照するときに "http エラー" が表示される場合は、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] IIS アプリケーションプールの id 資格情報が正しいことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="93123-185">If the status is not Online or you see "http error" when you browse the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] site, verify the identity credentials in the IIS application pools are still correct.</span></span> <span data-ttu-id="93123-186">IIS のプール名は、Get-SPServiceApplicationPool コマンドによって返された ID プロパティの値になります。</span><span class="sxs-lookup"><span data-stu-id="93123-186">The IIS pool name will is the value of the ID property returned by the Get-SPServiceApplicationPool command.</span></span>

```powershell
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)

Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                           Status ProcessAccountName Id
----                           ------ ------------------ ------- 
SharePoint Web Services System Online DOMAIN\account     89b50ec3-49e3-4de7-881a-2cec4b8b73ea
```

 ![メモ](../../../reporting-services/media/rs-fyinote.png "注意")アプリケーションプールは、サーバーの全体管理ページで [**サービスアプリケーションの管理**] で確認することもできます。 <span data-ttu-id="93123-188">サービス アプリケーションの名前をクリックし、リボンで **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="93123-188">Click the name of the service application and then click **properties** in the ribbon.</span></span>

 <span data-ttu-id="93123-189">**PowerPivot サービス アプリケーションと Excel サービス アプリケーションのプロキシ**</span><span class="sxs-lookup"><span data-stu-id="93123-189">**PowerPivot and Excel Service Application proxies**</span></span>

 <span data-ttu-id="93123-190">状態が**オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-190">Verify the Status is **Online**.</span></span>

```powershell
Get-SPServiceApplicationProxy | Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -Like "*powerpivot*" -Or $_.TypeName -Like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                                 Status UnattendedAccount           DisplayName
--------                                                 ------ -----------------           -----------
PowerPivot Service Application Proxy                     Online PowerPivotUnattendedAccount PowerPivotServiceApplication1
Excel Services Application Web Service Application Proxy Online                             Excel Services Application
```

##  <a name="databases"></a><a name="bkmk_databases"></a> <span data-ttu-id="93123-191">データベース</span><span class="sxs-lookup"><span data-stu-id="93123-191">Databases</span></span>
 <span data-ttu-id="93123-192">次のスクリプトは、サービス アプリケーション データベースとすべてのコンテンツ データベースの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="93123-192">The following script returns the status of the service application databases and all content databases.</span></span> <span data-ttu-id="93123-193">状態が **オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-193">Verify the status is **Online**.</span></span>

```powershell
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -Or $_.TypeName -Like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                                                                       Status Server                  TypeName 
----                                                                       ------ ------                  -------- 
DefaultPowerPivotServiceApplicationDB-38422181-2b68-4ab2-b2bb-9c00c39e5a5e Online SPServer Name=TESTSERVER Microsoft.AnalysisServices.SPAddin.GeminiServiceDatabase
DefaultWebApplicationDB-f0db1a8e-4c22-408c-b9b9-153bd74b0312               Online TESTSERVER\POWERPIVOT    Content Database 
SharePoint_Admin_3cadf0b098bf49e0bb15abd487f5c684                          Online TESTSERVER\POWERPIVOT    Content Database
```

##  <a name="sharepoint-features"></a><a name="bkmk_features"></a><span data-ttu-id="93123-194">SharePoint の機能</span><span class="sxs-lookup"><span data-stu-id="93123-194">SharePoint Features</span></span>
 <span data-ttu-id="93123-195">サイト、Web、ファームの各機能がオンラインであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-195">Verify the site, web, and farm features are online.</span></span>

```powershell
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
DisplayName     Status Scope Farm                         
-----------     ------ ----- ----                         
PowerPivotSite  Online  Site SPFarm Name=SharePoint_Config
PowerPivotAdmin Online   Web SPFarm Name=SharePoint_Config
PowerPivot      Online  Farm SPFarm Name=SharePoint_Config
```

##  <a name="timer-jobs"></a><a name="bkmk_timer_jobs"></a> <span data-ttu-id="93123-196">タイマー ジョブ</span><span class="sxs-lookup"><span data-stu-id="93123-196">Timer Jobs</span></span>
 <span data-ttu-id="93123-197">タイマー ジョブが **オンライン**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-197">Verify the Time Jobs are **Online**.</span></span> <span data-ttu-id="93123-198">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService は SharePoint 2013 にはインストールされないので、スクリプトを使用しても、SharePoint 2013 の配置における EngineService タイマー ジョブは表示されません。</span><span class="sxs-lookup"><span data-stu-id="93123-198">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService is not installed on SharePoint 2013, therefore the script will not list EngineService timer jobs in a SharePoint 2013 deployment.</span></span>

```powershell
Get-SPTimerJob | Where {$_.service -Like "*power*" -Or $_.service -Like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default
```

```Output
      Status DisplayName                                                                          LastRunTime          Service                             
------ -----------                                                                          -----------          -------                             
Online Health Analysis Job (Daily, SQL Server Analysis Services, All Servers)               4/9/2014 12:00:01 AM EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Hourly, SQL Server Analysis Services, All Servers)              4/9/2014 1:00:01 PM  EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Weekly, SQL Server Analysis Services, All Servers)              4/6/2014 12:00:10 AM EngineService Name=MSOLAP$POWERPIVOT
Online PowerPivot Management Dashboard Processing Timer Job                                 4/8/2014 3:45:38 AM  MidTierService
Online PowerPivot Health Statistics Collector Timer Job                                     4/9/2014 1:00:12 PM  MidTierService
Online PowerPivot Data Refresh Timer Job                                                    4/9/2014 1:09:36 PM  MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, All Servers)  4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, Any Server)   4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, All Servers) 4/6/2014 12:00:03 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, Any Server)  4/6/2014 12:00:03 AM MidTierService
Online PowerPivot Setup Extension Timer Job                                                 4/1/2014 1:40:31 AM  MidTierService
```

##  <a name="health-rules"></a><a name="bkmk_health_rules"></a> <span data-ttu-id="93123-199">正常性ルール</span><span class="sxs-lookup"><span data-stu-id="93123-199">Health Rules</span></span>
 <span data-ttu-id="93123-200">SharePoint 2013 の配置では、ルールの数が少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="93123-200">There are fewer rules in a SharePoint 2013 deployment.</span></span> <span data-ttu-id="93123-201">各 SharePoint 環境のルールの完全な一覧と、ルールの使用方法の説明については、「 [PowerPivot の正常性ルール-構成](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-201">For a full list of rules for each SharePoint environment and an explanation of how to use the rules, see [PowerPivot Health Rules - Configure](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md).</span></span>

```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                          Enabled Summary
----                          ------- -------         
SecondaryLogonHealthRule         True PowerPivot:  Secondary Logon service (seclogon) is disabled
DataRefreshTimerJobHealthRule    True PowerPivot: The PowerPivot Data Refresh timer job is disabled.
ASUsageLoadHealthRule            True PowerPivot: The ratio of load events to connections is too high.
ASMiniDumpHealthRule             True PowerPivot: One or more minidump files were found in the Logs directory, indicating a program crash
ASUsageCubeRule                  True PowerPivot: Usage data is not getting updated at the expected frequency.
ASADOMDNETHealthRule             True PowerPivot: ADOMD.NET is not installed on a standalone WFE that is configured for central admin
MidTierAcctReadPermissionRule    True PowerPivot: MidTier process account should have 'Full Read' permission on all associated SPWebApplications.
```

##  <a name="windows-and-uls-logs"></a><a name="bkmk_logs"></a> <span data-ttu-id="93123-202">Windows と ULS のログ</span><span class="sxs-lookup"><span data-stu-id="93123-202">Windows and ULS Logs</span></span>
 <span data-ttu-id="93123-203">**Windows イベントログ**</span><span class="sxs-lookup"><span data-stu-id="93123-203">**Windows event log**</span></span>

 <span data-ttu-id="93123-204">次のコマンドは、SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスに関連するイベントの Windows イベント ログを検索します。</span><span class="sxs-lookup"><span data-stu-id="93123-204">The following command will search the windows event log for events related to the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="93123-205">イベントの無効化やイベントレベルの変更の詳細については、「 [SharePoint ログファイルと診断ログの構成と表示」 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-205">For information on disabling events or changing the event level, see [Configure and View SharePoint Log Files  and Diagnostic Logging &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md).</span></span>

 <span data-ttu-id="93123-206">**サービス名:** MSOLAP$POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="93123-206">**Service Name:** MSOLAP$POWERPIVOT</span></span>

 <span data-ttu-id="93123-207">**Windows サービスでの表示名:** SQL Server Analysis Services (POWERPIVOT)</span><span class="sxs-lookup"><span data-stu-id="93123-207">**Display name in Windows Services:** SQL Server Analysis Services (POWERPIVOT)</span></span>

```powershell
Get-EventLog "application" | Where-Object {$_.source -Like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -property * -AutoSize | Out-Default
```

```Output
TimeGenerated           EntryType Source            Message
-------------           --------- ------            -------
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Service started. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM 12.0.1997.5.
4/16/2014 1:45:18 PM  Information MSOLAP$POWERPIVOT The flight recorder was started.
4/14/2014 6:45:37 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
```

 <span data-ttu-id="93123-208">**SharePoint ULS ログ、過去 48 時間**</span><span class="sxs-lookup"><span data-stu-id="93123-208">**SharePoint ULS Log, last 48 hours**</span></span>

 <span data-ttu-id="93123-209">次のコマンドは、過去 48 時間に作成された ULS ログから [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] メッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="93123-209">The following command will return [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] messages from the ULS log that were created in the last 48 hours.</span></span> <span data-ttu-id="93123-210">addhours パラメーターは必要に応じて調整してください。</span><span class="sxs-lookup"><span data-stu-id="93123-210">Adjust the addhours parameter for your need.</span></span>

```powershell
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid,level, message | Format-Table -Property * -AutoSize | Out-Default
```

 <span data-ttu-id="93123-211">次のコマンドのバリエーションは、 **データ更新** カテゴリのログ イベントのみを返します。</span><span class="sxs-lookup"><span data-stu-id="93123-211">The following variation of the command only returns log events for the **data refresh** category.</span></span>

```powershell
Get-SPLogEvent -starttime(Get-Date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message
```

```Output
Timestamp   : 4/14/2014 7:15:01 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 43
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : The following error occurred when working with the service application, Default PowerPivot Service Application. Skipping the service application..

Timestamp   : 4/14/2014 7:15:02 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 99
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : EXCEPTION: System.TimeoutException: The request channel timed out while waiting for a reply after 00:00:47.0625313. Increase the timeout value passed to 
              the call to Request or increase the SendTimeout value on the Binding. The time allotted to this operation may have been a portion of a longer timeout. 
              ---> System.TimeoutException: The HTTP request to 'http://localhost:32843/SecurityTokenServiceApplication/securitytoken.svc/actas' has exceeded the 
              allotted timeout of 00:00:54.5930000. The time allotted to this operation may have been a portion of a longer timeout. ---> System.Net.WebException: The 
              operation has timed out     at System.Net.HttpWebRequest.GetResponse()     at 
              System.ServiceModel.Channels.HttpChannelFactory`1.HttpRequestChannel.HttpChannelRequest.WaitForReply(TimeSpan timeout...
```

##  <a name="msolap-provider"></a><a name="bkmk_msolap"></a> <span data-ttu-id="93123-212">MSOLAP プロバイダー</span><span class="sxs-lookup"><span data-stu-id="93123-212">MSOLAP Provider</span></span>
 <span data-ttu-id="93123-213">プロバイダーが MSOLAP プロバイダーであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-213">Verify the provider MSOLAP provider.</span></span> [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<span data-ttu-id="93123-214">およびには [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] MSOLAP. 5 が必要です。</span><span class="sxs-lookup"><span data-stu-id="93123-214">and [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] require MSOLAP.5.</span></span>

```powershell
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default
```

```Output
ProviderId ProviderType Description
---------- ------------ -----------
MSOLAP     Oledb        Microsoft OLE DB Provider for OLAP Services     
MSOLAP.3   Oledb        Microsoft OLE DB Provider for OLAP Services 9.0 
MSOLAP.4   Oledb        Microsoft OLE DB Provider for OLAP Services 10.0
MSOLAP.5   Oledb        Microsoft OLE DB Provider for OLAP Services 11.0
```

 <span data-ttu-id="93123-215">詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) 」および「 [Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加](https://technet.microsoft.com/library/hh758436.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-215">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) and [Add MSOLAP.5 as a Trusted Data Provider in Excel Services](https://technet.microsoft.com/library/hh758436.aspx).</span></span>

##  <a name="adomdnet-client-library"></a><a name="bkmk_adomd"></a><span data-ttu-id="93123-216">ADOMD.Net クライアントライブラリ</span><span class="sxs-lookup"><span data-stu-id="93123-216">ADOMD.Net client Library</span></span>

```powershell
Get-WMIObject -Class win32_product | Where-Object {$_.name -Like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | out-default
```

```Output
name                                                  version      vendor
----                                                  -------      ------
Microsoft SQL Server 2008 Analysis Services ADOMD.NET 10.1.2531.0  Microsoft Corporation
Microsoft SQL Server 2005 Analysis Services ADOMD.NET 9.00.1399.06 Microsoft Corporation
```

 <span data-ttu-id="93123-217">詳細については、「 [サーバーの全体管理を実行している Web フロントエンド サーバーに ADOMD.NET をインストールする方法](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-217">For more information, see [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>

##  <a name="health-data-collection-rules"></a><a name="bkmk_health_collection"></a> <span data-ttu-id="93123-218">正常性データの収集ルール</span><span class="sxs-lookup"><span data-stu-id="93123-218">Health Data Collection Rules</span></span>
 <span data-ttu-id="93123-219">**"Status"** がオンラインであり、 **"Enabled"** が True であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-219">Verify the **Status** is Online and **Enabled** is True.</span></span>

```powershell
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -Like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                         Status Enabled TableName                   DaysToKeepDetailedData
----                         ------ ------- ---------                   ----------------------
PowerPivot Connections       OnlineTrue AnalysisServicesConnections  14
PowerPivot Load Data Usage   Online    True AnalysisServicesLoads                           14
PowerPivot Query Usage       Online    True AnalysisServicesRequests                        14
PowerPivot Unload Data Usage Online    True AnalysisServicesUnloads                         14
```

 <span data-ttu-id="93123-220">詳細については、「 [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-220">For more information, see [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md).</span></span>

##  <a name="solutions"></a><a name="bkmk_solutions"></a><span data-ttu-id="93123-221">'83'5c</span><span class="sxs-lookup"><span data-stu-id="93123-221">Solutions</span></span>
 <span data-ttu-id="93123-222">他のコンポーネントがオンラインになっている場合は、ソリューションの確認をスキップできます。</span><span class="sxs-lookup"><span data-stu-id="93123-222">If the other components are online then you can skip verifying the solutions.</span></span> <span data-ttu-id="93123-223">ただし正常性ルールがない場合は、2 つのソリューションが存在し表示されることを確認します。また、2 つの PowerPivot ソリューションが **オンライン** になっており、 **配置済み**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="93123-223">If however the Health rules are missing, verify the two solutions exist and showed Verify the two PowerPivot solutions are **Online** and **Deployed**.</span></span>

```powershell
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

<span data-ttu-id="93123-224">SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="93123-224">SharePoint 2013:</span></span>

```Output
Name                                 Status Deployed        DeploymentState DeployedServers
----                                 ------ --------        --------------- ---------------
powerpivotfarm14solution.wsp         Online     True         GlobalDeployed {UETESTA00}
powerpivotfarmsolution.wsp           Online     True         GlobalDeployed {UETESTA00}
powerpivotwebapplicationsolution.wsp Online     True WebApplicationDeployed {UETESTA00}
```

<span data-ttu-id="93123-225">SharePoint 2010:</span><span class="sxs-lookup"><span data-stu-id="93123-225">SharePoint 2010:</span></span>

```Output
Name                 Status Deployed        DeploymentState DeployedServers 
----                 ------ --------        --------------- --------------- 
powerpivotfarm.wsp   Online     True         GlobalDeployed {uesql11spoint2}
powerpivotwebapp.wsp Online     True WebApplicationDeployed {uesql11spoint2}
```

 <span data-ttu-id="93123-226">SharePoint ソリューションを配置する方法については、「 [ソリューション パッケージを展開する (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-226">For more information on how to deploy SharePoint solutions, see [Deploy solution packages (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx).</span></span>

##  <a name="manual-verification-steps"></a><a name="bkmk_manual"></a> <span data-ttu-id="93123-227">手動による検証手順</span><span class="sxs-lookup"><span data-stu-id="93123-227">Manual Verification Steps</span></span>
 <span data-ttu-id="93123-228">このセクションでは、PowerShell コマンドレットでは実行できない検証手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="93123-228">This section describes verification steps that cannot be completed with PowerShell cmdlets.</span></span>

 <span data-ttu-id="93123-229">**定期データ更新:** ブックの更新スケジュールを構成します ( **[さらに、できるだけ早く更新を行います]** を設定)。</span><span class="sxs-lookup"><span data-stu-id="93123-229">**Scheduled Data Refresh:** Configure the refresh schedule a workbook to **Also refresh as soon as possible**.</span></span>  <span data-ttu-id="93123-230">詳細については、「[データ更新のスケジュール」と「Windows 認証をサポートしていないデータソース &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md)」の「データ更新の検証」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="93123-230">For more information, see the "Verify Data Refresh" section of [Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md).</span></span>

##  <a name="more-resources"></a><a name="bkmk_more_resources"></a><span data-ttu-id="93123-231">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="93123-231">More Resources</span></span>
 <span data-ttu-id="93123-232">[Windows PowerShell での Web サーバー (IIS) の管理コマンドレット](https://technet.microsoft.com/library/ee790599.aspx)</span><span class="sxs-lookup"><span data-stu-id="93123-232">[Web Server (IIS) Administration Cmdlets in Windows PowerShell](https://technet.microsoft.com/library/ee790599.aspx).</span></span>

 <span data-ttu-id="93123-233">[SharePoint でサービス、IIS サイト、アプリケーション プールの状態を確認する PowerShell](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0)</span><span class="sxs-lookup"><span data-stu-id="93123-233">[PowerShell to check services, IIS sites and Application Pool status in SharePoint](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).</span></span>

 <span data-ttu-id="93123-234">[Windows PowerShell for SharePoint 2013 リファレンス](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="93123-234">[Windows PowerShell for SharePoint 2013 reference](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span></span>

 <span data-ttu-id="93123-235">[Windows PowerShell for SharePoint Foundation 2010 リファレンス](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="93123-235">[Windows PowerShell for SharePoint Foundation 2010 reference](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span></span>

 <span data-ttu-id="93123-236">[Windows PowerShell を使用して Excel Services を管理する (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="93123-236">[Manage Excel Services with Windows PowerShell (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span></span>

 [<span data-ttu-id="93123-237">SQL Server セットアップ ログ ファイルの表示と読み取り</span><span class="sxs-lookup"><span data-stu-id="93123-237">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)

 [<span data-ttu-id="93123-238">Get-Eventlog コマンドレットの使用</span><span class="sxs-lookup"><span data-stu-id="93123-238">Use the Get-EvenLog cmdlet</span></span>](https://technet.microsoft.com/library/ee176846.aspx)

##  <a name="full-powershell-script"></a><a name="bkmk_full_script"></a><span data-ttu-id="93123-239">完全な PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="93123-239">Full PowerShell Script</span></span>
 <span data-ttu-id="93123-240">次のスクリプトには、上記の各セクションのコマンドがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="93123-240">The Following script contains all of the commands from the previous sections.</span></span> <span data-ttu-id="93123-241">スクリプトでは、このトピックに示した順序でコマンドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="93123-241">The script runs the commands in the same order as they are presented in this topic.</span></span> <span data-ttu-id="93123-242">またスクリプトには、このトピックで説明したコマンドのバリエーションが含まれています。追加のフィルターが必要になった場合に、状況に応じて使用してください。</span><span class="sxs-lookup"><span data-stu-id="93123-242">The script contains some optional variations of the commands noted in this topic in case you need additional filtering.</span></span> <span data-ttu-id="93123-243">バリエーションは、コメント文字 (#) によって無効になっています。</span><span class="sxs-lookup"><span data-stu-id="93123-243">The variations are disabled with a comment character (#).</span></span> <span data-ttu-id="93123-244">スクリプトには、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の SharePoint モードを確認するためのステートメントも含まれています。</span><span class="sxs-lookup"><span data-stu-id="93123-244">The script also includes some statements for verifying [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="93123-245">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ステートメントは、コメント文字 (#) によって無効になっています。</span><span class="sxs-lookup"><span data-stu-id="93123-245">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] statements are disabled with a comment character (#).</span></span>

```powershell
# This script audits services related to PowerPivot for SharePoint
$starttime = Get-Date
write-host -foregroundcolor DarkGray StartTime $starttime

Write-Host  "Import the SharePoint PowerShell snappin"
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0

Write-Host -ForegroundColor Green "Analysis Services Windows Service"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "PowerPivotEngineService and PowerPivotSystemService"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"

Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotSystemService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotEngineService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

#Write-Host -ForegroundColor Green "Service Instances - optional if you want to associate services with the server"
#Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
#Get-SPServiceInstance | select typename, status, server, service, instance | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel*" -or $_.TypeName -like "*Analysis Services*"} | format-table -property * -autosize | out-default
#Get-PowerPivotEngineServiceInstance  | select typename, ASServername, status, server, service, instance
#Get-PowerPivotSystemServiceInstance  | select typename, ASSServerName, status, server, service, instance

Write-Host -ForegroundColor Green "PowerPivot And Excel Service Applications"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename,  DisplayName, status

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot Service Application pool"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
# the following assumes there is only 1 PowerPivot Service Application, and returns that application's pool name.  if you have more than one, use the 2nd version
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)
Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot and Excel Service Application Proxy"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPServiceApplicationProxy |  Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPServiceApplicationProxy |  select typename, status, unattendedaccount, displayname | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*Reporting Services*" -or $_.TypeName -like "*excel services*"} | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "DATABASES"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPDatabase | select name, status, server, typename | where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*" -or $_.TypeName -like "*ReportingServices*"}

Write-Host -ForegroundColor Green "features"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPFeature | select displayname, status, scope, farm | where {$_.displayName -like "*powerpivot*" -or $_.displayName -like "*ReportServer*"}  | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "Timer Jobs (Job Definitions) -- list is the same as seen in the 'Review timer job definitions' section of the management dashboard"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPTimerJob | Where {$_.service -like "*power*" -or $_.service -like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "health rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "Windows Event Log data MSSQL$POWERPIVOT and "
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -Property * -autosize | Out-Default
#The following is the same command but with the Inforamtion events filtered out.
#Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*" -and ($_.entrytype -match "error" -or $_.entrytype -match "critical" -or $_.entrytype -match "warning")}  |select timegenerated, entrytype , source, message | format-table -property * -autosize | out-default

#Write-Host ""
Write-Host -ForegroundColor Green "ULS Log data"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message | Format-Table -Property * -AutoSize | Out-Default
#the following example filters for the category 'data refresh'
#Get-SPLogEvent -starttime(get-date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | select timestamp, area, category, eventid, level, correlation, message

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "MSOLAP data provider for Excel Servivces, service application"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "ADOMD.net client library"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-WMIObject -Class win32_product | Where-Object {$_.name -like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Usage Data Rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Solutions"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time
```
