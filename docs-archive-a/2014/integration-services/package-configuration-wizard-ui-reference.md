---
title: パッケージ構成ウィザードの UI リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.configwizard.selectobjects.f1
- sql12.dts.configwizard.selecconfigtype.f1
- sql12.dts.configwizard.finishdtsconfiguration.f1
- sql12.dts.configwizard.welcome.f1
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 222c5f58ca4e942dd23909b433ab346c500fceed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644547"
---
# <a name="package-configuration-wizard-ui-reference"></a><span data-ttu-id="cb9fd-102">パッケージ構成ウィザードの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="cb9fd-102">Package Configuration Wizard UI Reference</span></span>
  <span data-ttu-id="cb9fd-103">**パッケージ構成ウィザード** を使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージとそのオブジェクトのプロパティを実行時に更新する構成を作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-103">Use the **Package Configuration Wizard** to create configurations that update the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its objects at run time.</span></span> <span data-ttu-id="cb9fd-104">このウィザードは、 **[パッケージ構成オーガナイザー]** ダイアログ ボックスで新しい構成を追加するか既存の構成を変更するときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-104">This wizard runs when you add a new configuration or modify an existing one in the **Package Configurations Organizer** dialog box.</span></span> <span data-ttu-id="cb9fd-105">**[パッケージ構成オーガナイザー]** ダイアログ ボックスを開くには、 **で** [SSIS] **メニューの** [パッケージ構成] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-105">To open the **Package Configurations Organizer** dialog box, select **Package Configurations** on the **SSIS** menu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="cb9fd-106">詳細については、「 [パッケージ構成を作成する](../../2014/integration-services/create-package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-106">For more information, see [Create Package Configurations](../../2014/integration-services/create-package-configurations.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb9fd-107">パッケージ配置モデルの構成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-107">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="cb9fd-108">パラメーターは、プロジェクト配置モデルの構成の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-108">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="cb9fd-109">プロジェクト配置モデルを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-109">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="cb9fd-110">配置モデルの詳細については、「 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-110">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="cb9fd-111">ここでは、ウィザードの各ページについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-111">The following sections describe pages of the Wizard.</span></span>  
  
## <a name="welcome-to-the-package-configuration-wizard-page"></a><span data-ttu-id="cb9fd-112">[パッケージ構成ウィザードへようこそ] ページ</span><span class="sxs-lookup"><span data-stu-id="cb9fd-112">Welcome to the Package Configuration Wizard Page</span></span>  
 <span data-ttu-id="cb9fd-113">**SSIS 構成ウィザード** を使用すると、パッケージとそのオブジェクトのプロパティを実行時に更新する構成を作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-113">Use the **SSIS Configuration Wizard** to create configurations that update the properties of a package and its objects at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="cb9fd-114">Options</span><span class="sxs-lookup"><span data-stu-id="cb9fd-114">Options</span></span>  
 <span data-ttu-id="cb9fd-115">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-115">**Don't show this page again**</span></span>  
 <span data-ttu-id="cb9fd-116">次回ウィザードを起動するときに、ようこそページをスキップします。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-116">Skip the welcome page the next time you open the wizard.</span></span>  
  
 <span data-ttu-id="cb9fd-117">**Next**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-117">**Next**</span></span>  
 <span data-ttu-id="cb9fd-118">ウィザードの次のページへ移動します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-118">Go the next page in the wizard.</span></span>  
  
## <a name="select-configuration-type-page"></a><span data-ttu-id="cb9fd-119">[構成の種類の選択] ページ</span><span class="sxs-lookup"><span data-stu-id="cb9fd-119">Select Configuration Type Page</span></span>  
 <span data-ttu-id="cb9fd-120">**[構成の種類の選択]** ページを使用すると、作成する構成を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-120">Use the **Select Configuration Type** page to specify the type of configuration to create.</span></span>  
  
 <span data-ttu-id="cb9fd-121">どの種類の構成を使用するか決定するための詳細な情報については、「 [パッケージ構成](../../2014/integration-services/package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-121">If you need additional information to determine which type of configuration to use, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="cb9fd-122">静的オプション</span><span class="sxs-lookup"><span data-stu-id="cb9fd-122">Static Options</span></span>  
 <span data-ttu-id="cb9fd-123">**構成の種類**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-123">**Configuration type**</span></span>  
 <span data-ttu-id="cb9fd-124">次のオプションを使用して、構成を格納するソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-124">Select the type of source in which to store the configuration, using the following options:</span></span>  
  
|<span data-ttu-id="cb9fd-125">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-125">Value</span></span>|<span data-ttu-id="cb9fd-126">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-127">**XML 構成ファイル**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-127">**XML configuration file**</span></span>|<span data-ttu-id="cb9fd-128">構成を XML ファイルとして格納します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-128">Store the configuration as an XML file.</span></span> <span data-ttu-id="cb9fd-129">この値を選択すると、セクション **[構成の種類]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-129">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="cb9fd-130">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-130">**Environment variable**</span></span>|<span data-ttu-id="cb9fd-131">構成を環境変数の 1 つに格納します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-131">Store the configuration in one of the environment variables.</span></span> <span data-ttu-id="cb9fd-132">この値を選択すると、セクション **[構成の種類]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-132">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="cb9fd-133">**レジストリ エントリ**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-133">**Registry entry**</span></span>|<span data-ttu-id="cb9fd-134">構成をレジストリに格納します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-134">Store the configuration in the Registry.</span></span> <span data-ttu-id="cb9fd-135">この値を選択すると、セクション **[構成の種類]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-135">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="cb9fd-136">**親パッケージ変数**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-136">**Parent package variable**</span></span>|<span data-ttu-id="cb9fd-137">構成をタスクを含むパッケージに変数として格納します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-137">Store the configuration as a variable in the package that contains the task.</span></span>  <span data-ttu-id="cb9fd-138">この値を選択すると、セクション **[構成の種類]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-138">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="cb9fd-139">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-139">**SQL Server**</span></span>|<span data-ttu-id="cb9fd-140">構成を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のテーブルに格納します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-140">Store the configuration in a table in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cb9fd-141">この値を選択すると、セクション **[構成の種類]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-141">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
  
 <span data-ttu-id="cb9fd-142">**Next**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-142">**Next**</span></span>  
 <span data-ttu-id="cb9fd-143">ウィザードのシーケンスの次のページを表示します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-143">View the next page in the wizard sequence.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="cb9fd-144">動的オプション</span><span class="sxs-lookup"><span data-stu-id="cb9fd-144">Dynamic Options</span></span>  
  
#### <a name="configuration-type-option--xml-configuration-file"></a><span data-ttu-id="cb9fd-145">[構成の種類] オプション = [XML 構成ファイル]</span><span class="sxs-lookup"><span data-stu-id="cb9fd-145">Configuration Type Option = XML Configuration File</span></span>  
 <span data-ttu-id="cb9fd-146">**[構成設定を直接指定する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-146">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="cb9fd-147">設定を直接指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-147">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="cb9fd-148">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-148">Value</span></span>|<span data-ttu-id="cb9fd-149">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-150">**[構成ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-150">**Configuration file name**</span></span>|<span data-ttu-id="cb9fd-151">ウィザードで生成する構成ファイルのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-151">Type the path of the configuration file that the wizard generates.</span></span>|  
|<span data-ttu-id="cb9fd-152">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-152">**Browse**</span></span>|<span data-ttu-id="cb9fd-153">**[構成ファイルの場所の選択]** ダイアログ ボックスを使用して、ウィザードで生成する構成ファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-153">Use the **Select Configuration File Location** dialog box to specify the path of the configuration file that the wizard generates.</span></span> <span data-ttu-id="cb9fd-154">指定したファイルが存在しない場合、ウィザードによってファイルが新しく作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-154">If the file does not exist, it is created by the wizard.</span></span>|  
  
 <span data-ttu-id="cb9fd-155">**[構成の場所を環境変数に格納する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-155">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="cb9fd-156">構成を格納する環境変数を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-156">Use to specify the environment variable in which to store the configuration.</span></span>  
  
|<span data-ttu-id="cb9fd-157">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-157">Value</span></span>|<span data-ttu-id="cb9fd-158">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-158">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-159">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-159">**Environment variable**</span></span>|<span data-ttu-id="cb9fd-160">一覧から環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-160">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--environment-variable"></a><span data-ttu-id="cb9fd-161">[構成の種類] オプション = [環境変数]</span><span class="sxs-lookup"><span data-stu-id="cb9fd-161">Configuration Type Option = Environment Variable</span></span>  
 <span data-ttu-id="cb9fd-162">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-162">**Environment variable**</span></span>  
 <span data-ttu-id="cb9fd-163">構成情報を格納する環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-163">Select the environment variable that contains the configuration information.</span></span>  
  
#### <a name="configuration-type-option--registry-entry"></a><span data-ttu-id="cb9fd-164">[構成の種類] オプション = [レジストリ エントリ]</span><span class="sxs-lookup"><span data-stu-id="cb9fd-164">Configuration Type Option = Registry Entry</span></span>  
 <span data-ttu-id="cb9fd-165">**[構成設定を直接指定する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-165">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="cb9fd-166">設定を直接指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-166">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="cb9fd-167">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-167">Value</span></span>|<span data-ttu-id="cb9fd-168">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-169">**レジストリ エントリ**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-169">**Registry entry**</span></span>|<span data-ttu-id="cb9fd-170">構成情報を格納するレジストリ キーを入力します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-170">Type the Registry key that contains the configuration information.</span></span> <span data-ttu-id="cb9fd-171">形式は \<registry key> です。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-171">The format is \<registry key>.</span></span><br /><br /> <span data-ttu-id="cb9fd-172">Value という名前の値を持つレジストリ キーが、あらかじめ HKEY_CURRENT_USER に存在していることが必要です。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-172">The Registry key must already exist in HKEY_CURRENT_USER and have a value named Value.</span></span> <span data-ttu-id="cb9fd-173">この値には、DWORD または文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-173">The value can be a DWORD or a string.</span></span><br /><br /> <span data-ttu-id="cb9fd-174">HKEY_CURRENT_USER のルートにないレジストリ キーを使用する場合は、\<Registry key\registry key\\...> の形式を使用してキーを識別します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-174">If you want to use a Registry key is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span>|  
  
 <span data-ttu-id="cb9fd-175">**[構成の場所を環境変数に格納する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-175">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="cb9fd-176">構成を格納する環境変数を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-176">Use to specify the environment variable to store the configuration in.</span></span>  
  
|<span data-ttu-id="cb9fd-177">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-177">Value</span></span>|<span data-ttu-id="cb9fd-178">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-179">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-179">**Environment variable**</span></span>|<span data-ttu-id="cb9fd-180">一覧から環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-180">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--parent-package-variable"></a><span data-ttu-id="cb9fd-181">[構成の種類] オプション = [親パッケージ変数]</span><span class="sxs-lookup"><span data-stu-id="cb9fd-181">Configuration Type Option = Parent Package Variable</span></span>  
 <span data-ttu-id="cb9fd-182">**[構成設定を直接指定する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-182">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="cb9fd-183">設定を直接指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-183">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="cb9fd-184">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-184">Value</span></span>|<span data-ttu-id="cb9fd-185">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-185">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-186">**[親変数]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-186">**Parent variable**</span></span>|<span data-ttu-id="cb9fd-187">構成情報を格納する親パッケージ内の変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-187">Specify the variable in the parent package that contains the configuration information.</span></span>|  
  
 <span data-ttu-id="cb9fd-188">**[構成の場所を環境変数に格納する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-188">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="cb9fd-189">構成を格納する環境変数を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-189">Use to specify the environment variable that stores the configuration.</span></span>  
  
|<span data-ttu-id="cb9fd-190">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-190">Value</span></span>|<span data-ttu-id="cb9fd-191">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-191">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-192">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-192">**Environment variable**</span></span>|<span data-ttu-id="cb9fd-193">一覧から環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-193">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-options--sql-server"></a><span data-ttu-id="cb9fd-194">[構成の種類] オプション = [SQL Server]</span><span class="sxs-lookup"><span data-stu-id="cb9fd-194">Configuration Type Options = SQL Server</span></span>  
 <span data-ttu-id="cb9fd-195">**[構成設定を直接指定する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-195">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="cb9fd-196">設定を直接指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-196">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="cb9fd-197">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-197">Value</span></span>|<span data-ttu-id="cb9fd-198">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-198">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-199">**接続**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-199">**Connection**</span></span>|<span data-ttu-id="cb9fd-200">一覧から接続を選択するか、 **[新規作成]** をクリックし、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-200">Select a connection from the list, or click **New** to create a new connection.</span></span>|  
|<span data-ttu-id="cb9fd-201">**[構成テーブル]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-201">**Configuration table**</span></span>|<span data-ttu-id="cb9fd-202">既存のテーブルを選択するか、 **[新規作成]** をクリックし、新しいテーブルを作成する SQL ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-202">Select an existing table, or click **New** to write a SQL statement that creates a new table.</span></span>|  
|<span data-ttu-id="cb9fd-203">**[構成フィルター]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-203">**Configuration filter**</span></span>|<span data-ttu-id="cb9fd-204">既存の構成名を選択するか、新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-204">Select an existing configuration name or type a new name.</span></span><br /><br /> <span data-ttu-id="cb9fd-205">多くの SQL Server の構成は同じテーブルに格納でき、各構成には複数の構成アイテムを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-205">Many SQL Server configurations can be stored in the same table, and each configuration can include multiple configuration items.</span></span><br /><br /> <span data-ttu-id="cb9fd-206">このユーザー定義の値はテーブルに格納され、特定の構成に属する構成アイテムの識別に使用されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-206">This user-defined value is stored in the table to identify configuration items that belong to a particular configuration</span></span>|  
  
 <span data-ttu-id="cb9fd-207">**[構成の場所を環境変数に格納する]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-207">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="cb9fd-208">構成を格納する環境変数を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-208">Use to specify the environment variable where the configuration is stored.</span></span>  
  
|<span data-ttu-id="cb9fd-209">値</span><span class="sxs-lookup"><span data-stu-id="cb9fd-209">Value</span></span>|<span data-ttu-id="cb9fd-210">説明</span><span class="sxs-lookup"><span data-stu-id="cb9fd-210">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb9fd-211">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-211">**Environment variable**</span></span>|<span data-ttu-id="cb9fd-212">一覧から環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-212">Select an environment variable from the list.</span></span>|  
  
## <a name="select-objects-to-export-page"></a><span data-ttu-id="cb9fd-213">[エクスポートするオブジェクトの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="cb9fd-213">Select Objects to Export Page</span></span>  
 <span data-ttu-id="cb9fd-214">**[対象になるプロパティの選択]** ページまたは [エクスポートするプロパティの選択] ページを使用すると、構成に含まれるオブジェクト プロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-214">Use the **Select Target Property or Select Properties to Export** page to specify the object properties that the configuration contains.</span></span> <span data-ttu-id="cb9fd-215">XML 構成の種類を選択した場合のみ、複数のプロパティを選択する機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-215">The ability to select multiple properties is available only if you select the XML configuration type.</span></span>  
  
### <a name="options"></a><span data-ttu-id="cb9fd-216">Options</span><span class="sxs-lookup"><span data-stu-id="cb9fd-216">Options</span></span>  
 <span data-ttu-id="cb9fd-217">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-217">**Objects**</span></span>  
 <span data-ttu-id="cb9fd-218">パッケージ階層を展開して、エクスポートするプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-218">Expand the package hierarchy and select the properties to export.</span></span>  
  
 <span data-ttu-id="cb9fd-219">**[プロパティ属性]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-219">**Property attributes**</span></span>  
 <span data-ttu-id="cb9fd-220">プロパティの属性を表示します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-220">View the attributes of a property.</span></span>  
  
 <span data-ttu-id="cb9fd-221">**Next**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-221">**Next**</span></span>  
 <span data-ttu-id="cb9fd-222">ウィザードの次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-222">Go to the next page in the wizard.</span></span>  
  
## <a name="completing-the-wizard-page"></a><span data-ttu-id="cb9fd-223">[ウィザードの完了] ページ</span><span class="sxs-lookup"><span data-stu-id="cb9fd-223">Completing the Wizard Page</span></span>  
 <span data-ttu-id="cb9fd-224">**[ウィザードの完了]** ページを使用すると、構成の名前を指定し、構成を作成するためにウィザードが使用する設定を表示できます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-224">Use the **Completing the Wizard** page to provide a name for the configuration and view settings used by the wizard to create the configuration.</span></span> <span data-ttu-id="cb9fd-225">ウィザードが完了すると、パッケージのすべての構成が一覧表示される **[パッケージ構成オーガナイザー]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-225">After the wizard completes, the **Package Configurations Organizer** is displayed, which lists all configurations for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="cb9fd-226">Options</span><span class="sxs-lookup"><span data-stu-id="cb9fd-226">Options</span></span>  
 <span data-ttu-id="cb9fd-227">**[構成名]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-227">**Configuration name**</span></span>  
 <span data-ttu-id="cb9fd-228">構成の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-228">Type the name of the configuration.</span></span>  
  
 <span data-ttu-id="cb9fd-229">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-229">**Preview**</span></span>  
 <span data-ttu-id="cb9fd-230">構成を作成するためにウィザードが使用する設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-230">View the settings used by the wizard to create the configuration.</span></span>  
  
 <span data-ttu-id="cb9fd-231">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="cb9fd-231">**Finish**</span></span>  
 <span data-ttu-id="cb9fd-232">構成を作成して **[パッケージ構成ウィザード]** を終了します。</span><span class="sxs-lookup"><span data-stu-id="cb9fd-232">Create the configuration and exit the **Package Configuration Wizard**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9fd-233">参照</span><span class="sxs-lookup"><span data-stu-id="cb9fd-233">See Also</span></span>  
 [<span data-ttu-id="cb9fd-234">パッケージ構成を作成する</span><span class="sxs-lookup"><span data-stu-id="cb9fd-234">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
