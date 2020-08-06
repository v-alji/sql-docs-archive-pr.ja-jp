---
title: パッケージの構成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package configuration syntax [Integration Services]
- SQL Server Integration Services packages, configurations
- SSIS packages, configurations
- XML [Integration Services]
- Integration Services packages, configurations
- configuration syntax [Integration Services]
- indirect configurations [Integration Services]
- configurations [Integration Services]
- direct configurations [Integration Services]
- packages [Integration Services], configurations
ms.assetid: d20e0311-1fc9-4ddc-a381-6d127cf11b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d22dbfedcf4cf7084e1667586f9774926f3b2a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645739"
---
# <a name="package-configurations"></a><span data-ttu-id="e04e0-102">[パッケージ構成]</span><span class="sxs-lookup"><span data-stu-id="e04e0-102">Package Configurations</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e04e0-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、プロパティの値を実行時に更新するためのパッケージ構成が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e04e0-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides package configurations that you can use to update the values of properties at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e04e0-104">パッケージ配置モデルの構成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="e04e0-105">パラメーターは、プロジェクト配置モデルの構成の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="e04e0-106">プロジェクト配置モデルを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e04e0-107">配置モデルの詳細については、「 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e04e0-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="e04e0-108">1 つの構成は、完了した状態のパッケージに追加するプロパティと値のペアで定義されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-108">A configuration is a property/value pair that you add to a completed package.</span></span> <span data-ttu-id="e04e0-109">通常、パッケージの開発中にパッケージ オブジェクトにプロパティを設定したパッケージを作成し、そのパッケージに構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-109">Typically, you create a package set properties on the package objects during package development, and then add the configuration to the package.</span></span> <span data-ttu-id="e04e0-110">パッケージの実行時に、構成からこのプロパティの新しい値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-110">When the package runs, it gets the new values of the property from the configuration.</span></span> <span data-ttu-id="e04e0-111">たとえば、構成を使用して、接続マネージャーの接続文字列を変更したり、変数の値を更新したりできます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-111">For example, by using a configuration, you can change the connection string of a connection manager, or update the value of a variable.</span></span>  
  
 <span data-ttu-id="e04e0-112">パッケージの構成には、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-112">Package configurations provide the following benefits:</span></span>  
  
-   <span data-ttu-id="e04e0-113">構成を使用すると、開発環境から運用環境へのパッケージの移行が容易になります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-113">Configurations make it easier to move packages from a development environment to a production environment.</span></span> <span data-ttu-id="e04e0-114">たとえば、ある構成を使用して、ソース ファイルのパスを更新したり、データベースやサーバーの名前を変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-114">For example, a configuration can update the path of a source file, or change the name of a database or server.</span></span>  
  
-   <span data-ttu-id="e04e0-115">構成は、パッケージを多くの異なるサーバーに配置する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e04e0-115">Configurations are useful when you deploy packages to many different servers.</span></span> <span data-ttu-id="e04e0-116">たとえば、配置されたパッケージごとの構成の変数に、異なるディスク容量値を格納できます。また、使用できるディスク容量がこの値に満たない場合、パッケージは実行されません。</span><span class="sxs-lookup"><span data-stu-id="e04e0-116">For example, a variable in the configuration for each deployed package can contain a different disk space value, and if the available disk space does not meet this value, the package does not run.</span></span>  
  
-   <span data-ttu-id="e04e0-117">構成を使用すると、パッケージの柔軟性が高まります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-117">Configurations make packages more flexible.</span></span> <span data-ttu-id="e04e0-118">たとえば、構成を使用すると、プロパティ式に使用されている変数の値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-118">For example, a configuration can update the value of a variable that is used in a property expression.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e04e0-119">では、XML ファイル、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース内のテーブル、および環境変数およびパッケージ変数など、パッケージ構成を格納するための複数の異なる方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e04e0-119">supports several different methods of storing package configurations, such as XML files, tables in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and environment and package variables.</span></span>  
  
 <span data-ttu-id="e04e0-120">それぞれの構成は、プロパティと値のペアで定義されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-120">Each configuration is a property/value pair.</span></span> <span data-ttu-id="e04e0-121">XML 構成ファイルと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成の種類には、複数の構成を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-121">The XML configuration file and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration types can include multiple configurations.</span></span>  
  
 <span data-ttu-id="e04e0-122">構成は、パッケージをインストールするためのパッケージ配置ユーティリティを作成したときに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-122">The configurations are included when you create a package deployment utility for installing packages.</span></span> <span data-ttu-id="e04e0-123">パッケージをインストールするときに、パッケージのインストールの 1 つの手順として構成を更新できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-123">When you install the packages, the configurations can be updated as a step in the package installation.</span></span>  
  
## <a name="understanding-how-package-configurations-are-applied-at-run-time"></a><span data-ttu-id="e04e0-124">実行時にパッケージ構成が適用されるしくみについて</span><span class="sxs-lookup"><span data-stu-id="e04e0-124">Understanding How Package Configurations Are Applied at Run Time</span></span>  
 <span data-ttu-id="e04e0-125">**dtexec** コマンド プロンプト ユーティリティ (dtexec.exe) を使用して配置されたパッケージを実行する場合、パッケージ構成が 2 回適用されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-125">When you use the **dtexec** command prompt utility (dtexec.exe) to run a deployed package, the utility applies package configurations twice.</span></span> <span data-ttu-id="e04e0-126">コマンド ラインで指定したオプションの適用前と適用後の両方に構成が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-126">The utility applies configurations both before and after it applies the options that you specified on command line.</span></span>  
  
 <span data-ttu-id="e04e0-127">パッケージを読み込んで実行すると、次の順序でイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-127">As the utility loads and runs the package, events occur in the following order:</span></span>  
  
1.  <span data-ttu-id="e04e0-128">**dtexec** ユーティリティでパッケージが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-128">The **dtexec** utility loads the package.</span></span>  
  
2.  <span data-ttu-id="e04e0-129">デザイン時にパッケージに指定された構成が、パッケージに指定されている順序で適用されます</span><span class="sxs-lookup"><span data-stu-id="e04e0-129">The utility applies the configurations that were specified in the package at design time and in the order that is specified in the package.</span></span> <span data-ttu-id="e04e0-130">(唯一の例外は、親パッケージ変数の構成です。</span><span class="sxs-lookup"><span data-stu-id="e04e0-130">(The one exception to this is the Parent Package Variables configurations.</span></span> <span data-ttu-id="e04e0-131">これらの構成は後から一度だけ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="e04e0-131">The utility applies these configurations only once and later in the process.)</span></span>  
  
3.  <span data-ttu-id="e04e0-132">次に、コマンド ラインで指定したすべてのオプションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-132">The utility then applies any options that you specified on the command line.</span></span>  
  
4.  <span data-ttu-id="e04e0-133">デザイン時にパッケージに指定された構成が、パッケージに指定されている順序で再読み込みされます</span><span class="sxs-lookup"><span data-stu-id="e04e0-133">The utility then reloads the configurations that were specified in the package at design time and in the order specified in the package.</span></span> <span data-ttu-id="e04e0-134">(この場合も唯一の例外は、親パッケージ変数の構成です)。</span><span class="sxs-lookup"><span data-stu-id="e04e0-134">(Again, the exception to this rule is the Parent Package Variables configurations).</span></span> <span data-ttu-id="e04e0-135">指定されたすべてのコマンド ライン オプションを使用して構成が再読み込みされます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-135">The utility uses any command-line options that were specified to reload the configurations.</span></span> <span data-ttu-id="e04e0-136">したがって、異なる値が異なる場所から再読み込みされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-136">Therefore, different values might be reloaded from a different location.</span></span>  
  
5.  <span data-ttu-id="e04e0-137">親パッケージ変数の構成が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-137">The utility applies the Parent Package Variable configurations.</span></span>  
  
6.  <span data-ttu-id="e04e0-138">パッケージが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-138">The utility runs the package.</span></span>  
  
 <span data-ttu-id="e04e0-139">**dtexec** ユーティリティでの構成の適用方法は、次のコマンド ライン オプションに影響します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-139">The way in which the **dtexec** utility applies configurations affects the following command-line options:</span></span>  
  
-   <span data-ttu-id="e04e0-140">実行時に **/Connection** または **/Set** オプションを使用すると、デザイン時に指定した場所とは別の場所からパッケージ構成を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-140">You can use the **/Connection** or **/Set** option at run time to load package configurations from a location other than the location that you specified at design time.</span></span>  
  
-   <span data-ttu-id="e04e0-141">**/ConfigFile** オプションを使用すると、デザイン時に指定しなかった追加の構成を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-141">You can use the **/ConfigFile** option to load additional configurations that you did not specify at design time.</span></span>  
  
 <span data-ttu-id="e04e0-142">ただし、これらのコマンド ライン オプションには制限事項がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-142">However, these command-line options do have some restrictions:</span></span>  
  
-   <span data-ttu-id="e04e0-143">**/Set** または **/Connection** オプションを使用して、構成で設定されている単一の値をオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e04e0-143">You cannot use the **/Set** or the **/Connection** option to override single values that are also set by a configuration.</span></span>  
  
-   <span data-ttu-id="e04e0-144">**/ConfigFile** オプションを使用して、デザイン時に指定した構成を置き換える構成を読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="e04e0-144">You cannot use the **/ConfigFile** option to load configurations that replace the configurations that you specified at design time.</span></span>  
  
 <span data-ttu-id="e04e0-145">これらのオプションの詳細と、と以前のバージョンでのこれらのオプションの動作の違いについて [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] は、「 [SQL Server 2014 の Integration Services 機能に対する動作の変更](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e04e0-145">For more information about these options, and how the behavior of these options differs between [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] and earlier versions, see [Behavior Changes to Integration Services Features in SQL Server 2014](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
## <a name="package-configuration-types"></a><span data-ttu-id="e04e0-146">パッケージの構成の種類</span><span class="sxs-lookup"><span data-stu-id="e04e0-146">Package Configuration Types</span></span>  
 <span data-ttu-id="e04e0-147">パッケージの構成の種類を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-147">The following table describes the package configuration types.</span></span>  
  
|<span data-ttu-id="e04e0-148">Type</span><span class="sxs-lookup"><span data-stu-id="e04e0-148">Type</span></span>|<span data-ttu-id="e04e0-149">説明</span><span class="sxs-lookup"><span data-stu-id="e04e0-149">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e04e0-150">XML 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="e04e0-150">XML configuration file</span></span>|<span data-ttu-id="e04e0-151">XML ファイルに構成を格納します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-151">An XML file contains the configurations.</span></span> <span data-ttu-id="e04e0-152">XML ファイルは、複数の構成を格納できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-152">The XML file can include multiple configurations.</span></span>|  
|<span data-ttu-id="e04e0-153">環境変数</span><span class="sxs-lookup"><span data-stu-id="e04e0-153">Environment variable</span></span>|<span data-ttu-id="e04e0-154">環境変数に構成を格納します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-154">An environment variable contains the configuration.</span></span>|  
|<span data-ttu-id="e04e0-155">レジストリ エントリ</span><span class="sxs-lookup"><span data-stu-id="e04e0-155">Registry entry</span></span>|<span data-ttu-id="e04e0-156">レジストリ エントリに構成を格納します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-156">A Registry entry contains the configuration.</span></span>|  
|<span data-ttu-id="e04e0-157">親パッケージ変数</span><span class="sxs-lookup"><span data-stu-id="e04e0-157">Parent package variable</span></span>|<span data-ttu-id="e04e0-158">パッケージの変数に構成を格納します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-158">A variable in the package contains the configuration.</span></span> <span data-ttu-id="e04e0-159">通常、この構成の種類は、子パッケージ内のプロパティを更新するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-159">This configuration type is typically used to update properties in child packages.</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e04e0-160">テーブル</span><span class="sxs-lookup"><span data-stu-id="e04e0-160">table</span></span>|<span data-ttu-id="e04e0-161">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース内のテーブルに構成を格納します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-161">A table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database contains the configuration.</span></span> <span data-ttu-id="e04e0-162">テーブルは、複数の構成を格納できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-162">The table can include multiple configurations.</span></span>|  
  
### <a name="xml-configuration-files"></a><span data-ttu-id="e04e0-163">XML 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="e04e0-163">XML Configuration Files</span></span>  
 <span data-ttu-id="e04e0-164">構成の種類として **[XML 構成ファイル]** を選択した場合は、新しい構成ファイルを作成したり、既存のファイルを再利用して新しい構成を追加できます。また、既存のファイルを再利用しながら既存のファイルの内容を上書きすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-164">If you select the **XML configuration file** configuration type, you can create a new configuration file, reuse an existing file and add new configurations, or reuse an existing file but overwrite existing file content.</span></span>  
  
 <span data-ttu-id="e04e0-165">XML 構成ファイルには、2 つのセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-165">An XML configuration file includes two sections:</span></span>  
  
-   <span data-ttu-id="e04e0-166">この構成ファイルに関する情報が記載された見出し。</span><span class="sxs-lookup"><span data-stu-id="e04e0-166">A heading that contains information about the configuration file.</span></span> <span data-ttu-id="e04e0-167">この要素には、ファイルの作成日やファイルの作成者の名前などの属性があります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-167">This element includes attributes such as when the file was created and the name of the person who generated the file.</span></span>  
  
-   <span data-ttu-id="e04e0-168">それぞれの構成に関する情報が格納された構成要素。</span><span class="sxs-lookup"><span data-stu-id="e04e0-168">Configuration elements that contain information about each configuration.</span></span> <span data-ttu-id="e04e0-169">この要素には、プロパティ パスやプロパティの構成値などの属性があります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-169">This element includes attributes such as the property path and the configured value of a property.</span></span>  
  
 <span data-ttu-id="e04e0-170">次の XML コードは、XML 構成ファイルの構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="e04e0-170">The following XML code demonstrates the syntax of an XML configuration file.</span></span> <span data-ttu-id="e04e0-171">この例では、 `MyVar`という名前の整数変数の Value プロパティの構成を示します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-171">This example shows a configuration for the Value property of an integer variable named `MyVar`.</span></span>  
  
```  
<?xml version="1.0"?>  
<DTSConfiguration>  
   <DTSConfigurationHeading>  
      <DTSConfigurationFileInfo  
          GeneratedBy="DomainName\UserName"  
          GeneratedFromPackageName="Package"  
          GeneratedFromPackageID="{2AF06766-817A-4E28-9878-0DE37A150648}"  
          GeneratedDate="2/01/2005 5:58:09 PM"/>  
   </DTSConfigurationHeading>  
   <Configuration ConfiguredType="Property" Path="\Package.Variables[User::MyVar].Value" ValueType="Int32">  
      <ConfiguredValue>0</ConfiguredValue>  
   </Configuration>  
</DTSConfiguration>  
  
```  
  
### <a name="registry-entry"></a><span data-ttu-id="e04e0-172">レジストリ エントリ</span><span class="sxs-lookup"><span data-stu-id="e04e0-172">Registry Entry</span></span>  
 <span data-ttu-id="e04e0-173">レジストリ エントリを使用して構成を格納する場合は、既存のキーを使用するか、HKEY_CURRENT_USER で新しいキーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-173">If you want to use a Registry entry to store the configuration, you can either use an existing key or create a new key in HKEY_CURRENT_USER.</span></span> <span data-ttu-id="e04e0-174">使用するレジストリ キーには、`Value` という名前の値が必要です。</span><span class="sxs-lookup"><span data-stu-id="e04e0-174">The Registry key that you use must have a value named `Value`.</span></span> <span data-ttu-id="e04e0-175">この値には、DWORD または文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-175">The value can be a DWORD or a string.</span></span>  
  
 <span data-ttu-id="e04e0-176">構成の種類として **[レジストリ エントリ]** を選択した場合は、[レジストリ エントリ] ボックスにレジストリ キーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-176">If you select the **Registry entry** configuration type, you type the name of the Registry key in the Registry entry box.</span></span> <span data-ttu-id="e04e0-177">形式は \<registry key> です。</span><span class="sxs-lookup"><span data-stu-id="e04e0-177">The format is \<registry key>.</span></span> <span data-ttu-id="e04e0-178">HKEY_CURRENT_USER のルートにないレジストリ キーを使用する場合は、\<Registry key\registry key\\...> の形式を使用してキーを識別します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-178">If you want to use a Registry key that is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span> <span data-ttu-id="e04e0-179">たとえば、SSISPackages にある MyPackage キーを使用する場合は、「`SSISPackages\MyPackage`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-179">For example, to use the MyPackage key located in SSISPackages, type `SSISPackages\MyPackage`.</span></span>  
  
### <a name="sql-server"></a><span data-ttu-id="e04e0-180">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e04e0-180">SQL Server</span></span>  
 <span data-ttu-id="e04e0-181">構成の種類として **[SQL Server]** を選択した場合は、構成を格納する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースへの接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-181">If you select the **SQL Server** configuration type, you specify the connection to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database in which you want to store the configurations.</span></span> <span data-ttu-id="e04e0-182">構成は、既存のテーブルに保存することも、指定したデータベース内に新しいテーブルを作成して保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-182">You can save the configurations to an existing table or create a new table in the specified database.</span></span>  
  
 <span data-ttu-id="e04e0-183">次の SQL ステートメントは、パッケージ構成ウィザードで提供される既定の CREATE TABLE ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="e04e0-183">The following SQL statement shows the default CREATE TABLE statement that the Package Configuration Wizard provides.</span></span>  
  
```  
CREATE TABLE [dbo].[SSIS Configurations]  
(  
ConfigurationFilter NVARCHAR(255) NOT NULL,  
ConfiguredValue NVARCHAR(255) NULL,  
PackagePath NVARCHAR(255) NOT NULL,  
ConfiguredValueType NVARCHAR(20) NOT NULL  
)  
  
```  
  
 <span data-ttu-id="e04e0-184">構成に指定される名前は、 **ConfigurationFilter** 列に格納されている値です。</span><span class="sxs-lookup"><span data-stu-id="e04e0-184">The name that you provide for the configuration is the value stored in the **ConfigurationFilter** column.</span></span>  
  
## <a name="direct-and-indirect-configurations"></a><span data-ttu-id="e04e0-185">直接構成および間接構成</span><span class="sxs-lookup"><span data-stu-id="e04e0-185">Direct and Indirect Configurations</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e04e0-186">では、直接構成と間接構成があります。</span><span class="sxs-lookup"><span data-stu-id="e04e0-186">provides direct and indirect configurations.</span></span> <span data-ttu-id="e04e0-187">構成を直接指定した場合、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、構成アイテムとパッケージ オブジェクト プロパティとの間に直接リンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="e04e0-187">If you specify configurations directly, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] creates a direct link between the configuration item and the package object property.</span></span> <span data-ttu-id="e04e0-188">直接構成は、ソースの位置が変化しない場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="e04e0-188">Direct configurations are a better choice when the location of the source does not change.</span></span> <span data-ttu-id="e04e0-189">たとえば、パッケージ内のすべての配置で同じファイル パスが必ず使用される場合は、XML 構成ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-189">For example, if you are sure that all deployments in the package use the same file path, you can specify an XML configuration file.</span></span>  
  
 <span data-ttu-id="e04e0-190">間接構成では、環境変数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-190">Indirect configurations use environment variables.</span></span> <span data-ttu-id="e04e0-191">構成設定を直接指定する代わりに、構成値を格納する環境変数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e04e0-191">Instead of specifying the configuration setting directly, the configuration points to an environment variable, which in turn contains the configuration value.</span></span> <span data-ttu-id="e04e0-192">間接構成は、パッケージのそれぞれの配置に対して構成の位置が変更される可能性がある場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="e04e0-192">Using indirect configurations is a better choice when the location of the configuration can change for each deployment of a package.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e04e0-193">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e04e0-193">Related Tasks</span></span>  
 [<span data-ttu-id="e04e0-194">パッケージ構成を作成する</span><span class="sxs-lookup"><span data-stu-id="e04e0-194">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
## <a name="related-content"></a><span data-ttu-id="e04e0-195">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e04e0-195">Related Content</span></span>  
  
-   <span data-ttu-id="e04e0-196">msdn.microsoft.com の技術記事「 [Integration Services パッケージ構成について](https://go.microsoft.com/fwlink/?LinkId=165643)」</span><span class="sxs-lookup"><span data-stu-id="e04e0-196">Technical article, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="e04e0-197">Www.sqlis.com のブログ記事「[コードパッケージ構成でのパッケージの作成](https://go.microsoft.com/fwlink/?LinkId=217663)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e04e0-197">Blog entry, [Creating packages in code - Package Configurations](https://go.microsoft.com/fwlink/?LinkId=217663), on www.sqlis.com.</span></span>  
  
-   <span data-ttu-id="e04e0-198">ブログ記事「 [API サンプル-プログラムによるパッケージへの構成ファイルの追加](https://go.microsoft.com/fwlink/?LinkId=217664)」 (blogs.msdn.com) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e04e0-198">Blog entry, [API Sample - Programmatically add a configuration file to a package](https://go.microsoft.com/fwlink/?LinkId=217664), on blogs.msdn.com.</span></span>  
  
  
