---
title: アップグレードアドバイザーの実行 (コマンドプロンプト) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a968f9d70788e1100af263f3ef9947493b4bd0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631484"
---
# <a name="running-upgrade-advisor-command-prompt"></a><span data-ttu-id="7a457-102">アップグレード アドバイザーの実行 (コマンド プロンプト)</span><span class="sxs-lookup"><span data-stu-id="7a457-102">Running Upgrade Advisor (Command Prompt)</span></span>
  <span data-ttu-id="7a457-103">**UpgradeAdvisorWizardCmd**ユーティリティを使用して、コマンドプロンプトからアップグレードアドバイザーを実行します。</span><span class="sxs-lookup"><span data-stu-id="7a457-103">Use the **UpgradeAdvisorWizardCmd** utility to run Upgrade Advisor from the command prompt.</span></span> <span data-ttu-id="7a457-104">結果を XML 形式で受け取るか、コンマ区切り値のファイルで受け取るかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7a457-104">You can choose to receive results in XML format or in a file with comma-separated values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a457-105">構文</span><span class="sxs-lookup"><span data-stu-id="7a457-105">Syntax</span></span>  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="7a457-106">引数</span><span class="sxs-lookup"><span data-stu-id="7a457-106">Arguments</span></span>  
 <span data-ttu-id="7a457-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="7a457-107">**-?**</span></span>  
 <span data-ttu-id="7a457-108">コマンドの構文を表示します。</span><span class="sxs-lookup"><span data-stu-id="7a457-108">Displays the command syntax.</span></span>  
  
 <span data-ttu-id="7a457-109">**-ConfigFile** _ファイル名_</span><span class="sxs-lookup"><span data-stu-id="7a457-109">**-ConfigFile** _filename_</span></span>  
 <span data-ttu-id="7a457-110">**UpgradeAdvisorWizardCmd**ユーティリティを実行するときに使用する設定を含む XML ファイルのパス名とファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-110">Is the path name and file name of an XML file that contains settings to use when you run the **UpgradeAdvisorWizardCmd** utility.</span></span>  
  
 <span data-ttu-id="7a457-111">*<server_info>*</span><span class="sxs-lookup"><span data-stu-id="7a457-111">*<server_info>*</span></span>  
 <span data-ttu-id="7a457-112">分析するコンピューターとインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-112">Specifies which computer and instance to analyze.</span></span> <span data-ttu-id="7a457-113">構成ファイルを使用していない場合に、これらのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a457-113">Use these options if you are not using a configuration file.</span></span>  
  
 <span data-ttu-id="7a457-114">*<server_info>* は、次の4つの引数の任意の組み合わせにすることができます。</span><span class="sxs-lookup"><span data-stu-id="7a457-114">*<server_info>* can be any combination of the following four arguments:</span></span>  
  
 <span data-ttu-id="7a457-115">**-サーバー** _server_name_</span><span class="sxs-lookup"><span data-stu-id="7a457-115">**-Server** _server_name_</span></span>  
 <span data-ttu-id="7a457-116">分析するコンピューターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-116">Specifies the name of the computer to analyze.</span></span> <span data-ttu-id="7a457-117">ローカル コンピューター (既定値) またはリモート コンピューターのどちらでも指定できます。</span><span class="sxs-lookup"><span data-stu-id="7a457-117">This can be the local computer, which is the default value, or a remote computer.</span></span>  
  
 <span data-ttu-id="7a457-118">**-インスタンス** _instance_name_</span><span class="sxs-lookup"><span data-stu-id="7a457-118">**-Instance** _instance_name_</span></span>  
 <span data-ttu-id="7a457-119">分析するインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-119">Specifies the name of the instance to analyze.</span></span> <span data-ttu-id="7a457-120">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-120">There is no default value.</span></span> <span data-ttu-id="7a457-121">このパラメーターを指定しない場合、は [!INCLUDE[ssDE](../../includes/ssde-md.md)] スキャンされません。</span><span class="sxs-lookup"><span data-stu-id="7a457-121">If you do not specify this parameter, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not scanned.</span></span> <span data-ttu-id="7a457-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスの値は MSSQLSERVER です。</span><span class="sxs-lookup"><span data-stu-id="7a457-122">The value for a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is MSSQLSERVER.</span></span> <span data-ttu-id="7a457-123">名前付きインスタンスの場合は、インスタンス名を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a457-123">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="7a457-124">**-Asinstance**  _AS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="7a457-124">**-ASInstance**  _AS_instance_name_</span></span>  
 <span data-ttu-id="7a457-125">分析する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-125">Specifies the name of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="7a457-126">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-126">There is no default value.</span></span> <span data-ttu-id="7a457-127">この値を指定しない場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はスキャンされません。</span><span class="sxs-lookup"><span data-stu-id="7a457-127">If you do not specify this value, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="7a457-128">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既定のインスタンスの値は MSSQLServerOLAPService です。</span><span class="sxs-lookup"><span data-stu-id="7a457-128">The value for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is MSSQLServerOLAPService.</span></span> <span data-ttu-id="7a457-129">名前付きインスタンスの場合は、インスタンス名を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a457-129">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="7a457-130">**-Rsinstance**  _RS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="7a457-130">**-RSInstance**  _RS_instance_name_</span></span>  
 <span data-ttu-id="7a457-131">分析する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-131">Specifies the name of the instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="7a457-132">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-132">There is no default value.</span></span> <span data-ttu-id="7a457-133">この値を指定しない場合、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はスキャンされません。</span><span class="sxs-lookup"><span data-stu-id="7a457-133">If you do not specify this value, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="7a457-134">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の既定のインスタンスの値は ReportServer です。</span><span class="sxs-lookup"><span data-stu-id="7a457-134">The value for a default instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is ReportServer.</span></span> <span data-ttu-id="7a457-135">名前付きインスタンスの場合は、インスタンス名を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a457-135">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="7a457-136">**-Sqluser** _login_id_</span><span class="sxs-lookup"><span data-stu-id="7a457-136">**-SqlUser** _login_id_</span></span>  
 <span data-ttu-id="7a457-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、この値に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。アップグレード アドバイザーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続にこのログインを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a457-137">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, this value is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that Upgrade Advisor will use to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7a457-138">ログインを指定しないと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に Windows 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a457-138">If you do not specify a login, Windows Authentication is used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="7a457-139">**-Sqlpassword** _パスワード_</span><span class="sxs-lookup"><span data-stu-id="7a457-139">**-SqlPassword** _password_</span></span>  
 <span data-ttu-id="7a457-140">**-Sqluser**引数を使用する場合は、この引数を使用してログインのパスワードを指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7a457-140">If you use the **-SqlUser** argument, use this argument to specify the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="7a457-141">**-CSV**</span><span class="sxs-lookup"><span data-stu-id="7a457-141">**-CSV**</span></span>  
 <span data-ttu-id="7a457-142">標準的な XML の結果に加え、コンマ区切り値の結果を .csv ファイルに出力する場合に指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-142">Specifies to provide results as comma-separated values to a .csv file in addition to the standard XML results.</span></span> <span data-ttu-id="7a457-143">結果は My Documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports フォルダーに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="7a457-143">Results are written to the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports folder.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="7a457-144">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a457-144">Return Values</span></span>  
 <span data-ttu-id="7a457-145">次の表は、 **UpgradeAdvisorWizardCmd**が返す値を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a457-145">The following table shows the values that **UpgradeAdvisorWizardCmd** returns.</span></span>  
  
|<span data-ttu-id="7a457-146">値</span><span class="sxs-lookup"><span data-stu-id="7a457-146">Value</span></span>|<span data-ttu-id="7a457-147">説明</span><span class="sxs-lookup"><span data-stu-id="7a457-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7a457-148">0</span><span class="sxs-lookup"><span data-stu-id="7a457-148">0</span></span>|<span data-ttu-id="7a457-149">分析が正常に完了し、アップグレードの問題は見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="7a457-149">Analysis succeeded, no upgrade issues found.</span></span>|  
|<span data-ttu-id="7a457-150">正の整数</span><span class="sxs-lookup"><span data-stu-id="7a457-150">positive integer</span></span>|<span data-ttu-id="7a457-151">分析が正常に完了し、アップグレードの問題が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="7a457-151">Analysis succeeded, upgrade issues found.</span></span>|  
|<span data-ttu-id="7a457-152">負の整数</span><span class="sxs-lookup"><span data-stu-id="7a457-152">negative integer</span></span>|<span data-ttu-id="7a457-153">分析が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="7a457-153">Analysis failed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a457-154">解説</span><span class="sxs-lookup"><span data-stu-id="7a457-154">Remarks</span></span>  
 <span data-ttu-id="7a457-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のユーザー名とパスワード以外は、分析の実行に必要なすべての情報を XML 構成ファイルに出力できます。</span><span class="sxs-lookup"><span data-stu-id="7a457-155">All information that is required to run the analysis, other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user names and passwords, can be provided in an XML configuration file.</span></span> <span data-ttu-id="7a457-156">この XML 構成ファイルはテンプレートに記述されています。</span><span class="sxs-lookup"><span data-stu-id="7a457-156">This XML configuration file is documented in the template.</span></span> <span data-ttu-id="7a457-157">構成ファイルを使用しない場合は、既定の設定でコンピューター名とインスタンス名を指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにインストールされているコンポーネントすべてを分析できます。</span><span class="sxs-lookup"><span data-stu-id="7a457-157">If you do not use a configuration file, you can analyze all installed components in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using default settings by specifying computer names and instance names.</span></span> <span data-ttu-id="7a457-158">既定の構成ファイル設定の詳細については、「要素の説明」の一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a457-158">See the "Element Descriptions" table later in this topic for a description of the default configuration file settings.</span></span>  
  
## <a name="configuration-file-template"></a><span data-ttu-id="7a457-159">構成ファイルのテンプレート</span><span class="sxs-lookup"><span data-stu-id="7a457-159">Configuration File Template</span></span>  
 <span data-ttu-id="7a457-160">独自の構成ファイルを作成する場合は、次の XML をテンプレートとして使用してください。</span><span class="sxs-lookup"><span data-stu-id="7a457-160">Use the following XML as a template for creating your own configuration files.</span></span> <span data-ttu-id="7a457-161">テンプレートは必要に応じて変更できます。</span><span class="sxs-lookup"><span data-stu-id="7a457-161">You can modify the template to meet the needs of your organization.</span></span>  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a><span data-ttu-id="7a457-162">要素の説明</span><span class="sxs-lookup"><span data-stu-id="7a457-162">Element Descriptions</span></span>  
  
|<span data-ttu-id="7a457-163">タグ</span><span class="sxs-lookup"><span data-stu-id="7a457-163">Tag</span></span>|<span data-ttu-id="7a457-164">定義</span><span class="sxs-lookup"><span data-stu-id="7a457-164">Definition</span></span>|<span data-ttu-id="7a457-165">個数</span><span class="sxs-lookup"><span data-stu-id="7a457-165">Occurrence</span></span>|  
|---------|----------------|----------------|  
|`Configuration`|<span data-ttu-id="7a457-166">アップグレード アドバイザー構成ファイルの親要素です。</span><span class="sxs-lookup"><span data-stu-id="7a457-166">Parent element for Upgrade Advisor configuration file.</span></span>|<span data-ttu-id="7a457-167">必須。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-167">Required once per configuration file.</span></span>|  
|`Server`|<span data-ttu-id="7a457-168">分析するサーバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="7a457-168">Name of the server to analyze.</span></span>|<span data-ttu-id="7a457-169">省略可。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-169">Optional once per configuration file.</span></span> <span data-ttu-id="7a457-170">既定値はローカル コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="7a457-170">The default value is the local computer.</span></span>|  
|`Instance`|<span data-ttu-id="7a457-171">分析する[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="7a457-171">Name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance to analyze.</span></span>|<span data-ttu-id="7a457-172">省略可。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-172">Optional once per configuration file.</span></span> <span data-ttu-id="7a457-173">既定値は既定のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="7a457-173">The default value is the default instance.</span></span><br /><br /> <span data-ttu-id="7a457-174">サーバー上に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要素または `IntegrationServices` 要素が存在する場合は必須。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-174">Required once per configuration file, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] element or an `IntegrationServices` element is present on the server.</span></span>|  
|`Components`|<span data-ttu-id="7a457-175">分析するコンポーネントを指定する要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-175">Contains elements that specify which components to analyze.</span></span>|<span data-ttu-id="7a457-176">必須。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-176">Required once per configuration file.</span></span>|  
|`SQLServer`|<span data-ttu-id="7a457-177">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスの分析設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-177">Contains analysis settings for an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|<span data-ttu-id="7a457-178">省略可。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-178">Optional once per configuration file.</span></span> <span data-ttu-id="7a457-179">指定しないと、[!INCLUDE[ssDE](../../includes/ssde-md.md)] データベースが分析されません。</span><span class="sxs-lookup"><span data-stu-id="7a457-179">If not specified, [!INCLUDE[ssDE](../../includes/ssde-md.md)] databases are not analyzed.</span></span>|  
|<span data-ttu-id="7a457-180">`Databases` 要素の `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="7a457-180">`Databases` for `SQLServer` element</span></span>|<span data-ttu-id="7a457-181">分析するデータベースの一覧を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-181">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="7a457-182">省略可能。要素ごとに1回 `SQLServer` です。</span><span class="sxs-lookup"><span data-stu-id="7a457-182">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="7a457-183">この要素が存在しない場合、インスタンスのすべてのデータベースが分析されます。</span><span class="sxs-lookup"><span data-stu-id="7a457-183">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="7a457-184">`Database` 要素の `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="7a457-184">`Database` for `SQLServer` element</span></span>|<span data-ttu-id="7a457-185">分析するデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-185">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="7a457-186">必須。`Databases` 要素が存在する場合に 1 個以上。</span><span class="sxs-lookup"><span data-stu-id="7a457-186">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="7a457-187">`Database` 要素に値 "\*" が含まれている場合は、インスタンスのすべてのデータベースが分析されます。</span><span class="sxs-lookup"><span data-stu-id="7a457-187">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="7a457-188">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-188">There is no default value.</span></span>|  
|`TraceFiles`|<span data-ttu-id="7a457-189">分析するトレース ファイルの一覧を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-189">Contains a list of trace files to analyze.</span></span>|<span data-ttu-id="7a457-190">省略可能。要素ごとに1回 `SQLServer` です。</span><span class="sxs-lookup"><span data-stu-id="7a457-190">Optional once per `SQLServer` element.</span></span>|  
|`TraceFile`|<span data-ttu-id="7a457-191">分析するトレース ファイルのパスと名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-191">Specifies the path and name of a trace file to analyze.</span></span>|<span data-ttu-id="7a457-192">必須。`TraceFiles` 要素が存在する場合に 1 個以上。</span><span class="sxs-lookup"><span data-stu-id="7a457-192">Required once or more if the `TraceFiles` element is present.</span></span> <span data-ttu-id="7a457-193">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-193">There is no default value.</span></span>|  
|`BatchFiles`|<span data-ttu-id="7a457-194">分析するバッチ ファイルの一覧を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-194">Contains a list of batch files to analyze.</span></span>|<span data-ttu-id="7a457-195">省略可能。要素ごとに1回 `SQLServer` です。</span><span class="sxs-lookup"><span data-stu-id="7a457-195">Optional once per `SQLServer` element.</span></span>|  
|`BatchFile`|<span data-ttu-id="7a457-196">分析するバッチ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-196">Specifies a batch file to analyze.</span></span> <span data-ttu-id="7a457-197">複数指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a457-197">Can be multiple.</span></span>|<span data-ttu-id="7a457-198">必須。`BatchFiles` 要素が存在する場合に 1 個以上。</span><span class="sxs-lookup"><span data-stu-id="7a457-198">Required once or more if the `BatchFiles` element is present.</span></span> <span data-ttu-id="7a457-199">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-199">There is no default value.</span></span>|  
|`BatchSeparator`|<span data-ttu-id="7a457-200">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バッチ ファイルに使用されるバッチ区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-200">Specifies the batch separator used in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch files.</span></span>|<span data-ttu-id="7a457-201">省略可能。要素ごとに1回 `SQLServer` です。</span><span class="sxs-lookup"><span data-stu-id="7a457-201">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="7a457-202">既定値は GO です。</span><span class="sxs-lookup"><span data-stu-id="7a457-202">The default value is GO.</span></span>|  
|`AnalysisServices`|<span data-ttu-id="7a457-203">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の分析設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-203">Contains analysis settings for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="7a457-204">省略可。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-204">Optional once per configuration file.</span></span> <span data-ttu-id="7a457-205">指定しないと、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースが分析されません。</span><span class="sxs-lookup"><span data-stu-id="7a457-205">If not specified, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases are not analyzed.</span></span>|  
|`ASInstance`|<span data-ttu-id="7a457-206">のインスタンスの名前を指定し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7a457-206">Specifies the name of an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="7a457-207">必須。`AnalysisServices` 要素につき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-207">Required once per `AnalysisServices` element.</span></span> <span data-ttu-id="7a457-208">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-208">There is no default value.</span></span>|  
|<span data-ttu-id="7a457-209">`Databases` 要素の `Analysis Services`</span><span class="sxs-lookup"><span data-stu-id="7a457-209">`Databases` for `Analysis Services` element</span></span>|<span data-ttu-id="7a457-210">分析するデータベースの一覧を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-210">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="7a457-211">省略可能。要素ごとに1回 `AnalysisServices` です。</span><span class="sxs-lookup"><span data-stu-id="7a457-211">Optional once per `AnalysisServices` element.</span></span> <span data-ttu-id="7a457-212">この要素が存在しない場合、インスタンスのすべてのデータベースが分析されます。</span><span class="sxs-lookup"><span data-stu-id="7a457-212">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="7a457-213">`Database` 要素の `AnalysisServices`</span><span class="sxs-lookup"><span data-stu-id="7a457-213">`Database` for `AnalysisServices` element</span></span>|<span data-ttu-id="7a457-214">分析するデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-214">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="7a457-215">必須。`Databases` 要素が存在する場合に 1 個以上。</span><span class="sxs-lookup"><span data-stu-id="7a457-215">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="7a457-216">`Database` 要素に値 "\*" が含まれている場合は、インスタンスのすべてのデータベースが分析されます。</span><span class="sxs-lookup"><span data-stu-id="7a457-216">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="7a457-217">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-217">There is no default value.</span></span>|  
|`ReportingServices`|<span data-ttu-id="7a457-218">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して分析を実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-218">Specifies to run analysis against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="7a457-219">省略可。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-219">Optional once per configuration file.</span></span> <span data-ttu-id="7a457-220">指定しなかった場合、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は分析されません。</span><span class="sxs-lookup"><span data-stu-id="7a457-220">If not specified, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not analyzed.</span></span>|  
|`RSInstance`|<span data-ttu-id="7a457-221">のインスタンスの名前を指定し [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7a457-221">Specifies the name of an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="7a457-222">必須。`ReportingServices` 要素につき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-222">Required once per `ReportingServices` element.</span></span> <span data-ttu-id="7a457-223">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-223">There is no default value.</span></span>|  
|`IntegrationServices`|<span data-ttu-id="7a457-224">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の分析設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="7a457-224">Contains analysis settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|<span data-ttu-id="7a457-225">省略可。構成ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="7a457-225">Optional once per configuration file.</span></span> <span data-ttu-id="7a457-226">指定しなかった場合、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は分析されません。</span><span class="sxs-lookup"><span data-stu-id="7a457-226">If not specified, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is not analyzed.</span></span>|  
|`PackagePath`|<span data-ttu-id="7a457-227">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのセットのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-227">Specifies the path of a set of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>|<span data-ttu-id="7a457-228">省略可能。要素ごとに1回 `IntegrationServices` です。</span><span class="sxs-lookup"><span data-stu-id="7a457-228">Optional once per `IntegrationServices` element.</span></span> <span data-ttu-id="7a457-229">この要素が存在しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対して分析が行われ、外部に格納されたパッケージは分析されません。</span><span class="sxs-lookup"><span data-stu-id="7a457-229">If this element is not present, analysis occurs on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and no externally stored packages are analyzed.</span></span> <span data-ttu-id="7a457-230">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="7a457-230">There is no default value.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="7a457-231">例</span><span class="sxs-lookup"><span data-stu-id="7a457-231">Examples</span></span>  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a><span data-ttu-id="7a457-232">A.</span><span class="sxs-lookup"><span data-stu-id="7a457-232">A.</span></span> <span data-ttu-id="7a457-233">構成ファイルを使用したアップグレード アドバイザーの実行</span><span class="sxs-lookup"><span data-stu-id="7a457-233">Run Upgrade Advisor Using a Configuration File</span></span>  
 <span data-ttu-id="7a457-234">次の例は、分析対象を指定する構成ファイルを使用したコマンド プロンプトからのアップグレード アドバイザーの実行方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a457-234">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file that specifies what to analyze.</span></span> <span data-ttu-id="7a457-235">この例では、Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="7a457-235">This example uses Windows Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a><span data-ttu-id="7a457-236">B.</span><span class="sxs-lookup"><span data-stu-id="7a457-236">B.</span></span> <span data-ttu-id="7a457-237">既定の構成設定を使用したアップグレード アドバイザーの実行</span><span class="sxs-lookup"><span data-stu-id="7a457-237">Run Upgrade Advisor Using Default Configuration Settings</span></span>  
 <span data-ttu-id="7a457-238">次の例は、既定の構成設定と Windows 認証を使用したコマンド プロンプトからのアップグレード アドバイザーの実行方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a457-238">The following example shows how to run Upgrade Advisor from the command prompt by using default configuration settings and Windows Authentication.</span></span>  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a><span data-ttu-id="7a457-239">C.</span><span class="sxs-lookup"><span data-stu-id="7a457-239">C.</span></span> <span data-ttu-id="7a457-240">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用したアップグレード アドバイザーの実行</span><span class="sxs-lookup"><span data-stu-id="7a457-240">Run Upgrade Advisor Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication</span></span>  
 <span data-ttu-id="7a457-241">次の例は、構成ファイルを使用したコマンド プロンプトからのアップグレード アドバイザーの実行方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a457-241">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file.</span></span> <span data-ttu-id="7a457-242">この例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a457-242">This example specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name and password to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a457-243">参照</span><span class="sxs-lookup"><span data-stu-id="7a457-243">See Also</span></span>  
 <span data-ttu-id="7a457-244">[アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="7a457-244">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="7a457-245">[アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="7a457-245">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="7a457-246">アップグレードアドバイザー &#40;ユーザーインターフェイス&#41;を実行しています</span><span class="sxs-lookup"><span data-stu-id="7a457-246">Running Upgrade Advisor &#40;User Interface&#41;</span></span>](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
