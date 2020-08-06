---
title: 権限借用オプションの設定 (SSAS-多次元) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.impersonationinfo.f1
helpviewer_keywords:
- Impersonation Information dialog box
ms.assetid: 8e127f72-ef23-44ad-81e6-3dd58981770e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b9a8526ff4b8a6dd6f68d13817e427ec70d1953
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642982"
---
# <a name="set-impersonation-options-ssas---multidimensional"></a><span data-ttu-id="fbb1c-102">権限借用オプションの設定 (SSAS - 多次元)</span><span class="sxs-lookup"><span data-stu-id="fbb1c-102">Set Impersonation Options (SSAS - Multidimensional)</span></span>
  <span data-ttu-id="fbb1c-103">Analysis Services モデルで`data source` オブジェクトを作成するときに構成する必要がある設定の 1 つに、権限借用オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-103">When creating a `data source` object in an Analysis Services model, one of the settings that you must configure is an impersonation option.</span></span> <span data-ttu-id="fbb1c-104">このオプションでは、接続関連のローカルの操作 (OLE DB データ プロバイダーの読み込みや、移動プロファイルをサポートする環境でのユーザー プロファイル情報の解決など) を実行するときに、Analysis Services で特定の Windows ユーザー アカウントの ID を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-104">This option determines whether Analysis Services assumes the identity of a specific Windows user account when performing local operations related to the connection, such as loading an OLE DB data provider or resolving user profile information in environments that support roaming profiles.</span></span>  
  
 <span data-ttu-id="fbb1c-105">Windows 認証を使用する接続の場合、権限借用オプションにより、外部データ ソースに対するクエリを実行する際のユーザー ID も決まります。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-105">For connections that use Windows authentication, the impersonation option also determines the user identity under which queries execute on the external data source.</span></span> <span data-ttu-id="fbb1c-106">たとえば、権限借用オプションを **contoso\dbuser**に設定した場合、処理時にデータの取得に使用されるクエリはデータベース サーバーの **contoso\dbuser** として実行されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-106">For example, if you set the impersonation option to **contoso\dbuser**, queries used to retrieve data during processing will execute as **contoso\dbuser** on the database server.</span></span>  
  
 <span data-ttu-id="fbb1c-107">このトピックでは、データ ソース オブジェクトの構成時に **[権限借用情報]** ダイアログ ボックスで権限借用オプションを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-107">This topic explains how to set impersonation options in the **Impersonation Information** dialog box when configuring a data source object.</span></span>  
  
## <a name="set-impersonation-options-in-sql-server-data-tools"></a><span data-ttu-id="fbb1c-108">SQL Server Data Tools での権限借用オプションの設定</span><span class="sxs-lookup"><span data-stu-id="fbb1c-108">Set impersonation options in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="fbb1c-109">ソリューション エクスプローラーでデータ ソースをダブルクリックして、データ ソース デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-109">Double-click a data source in Solution Explorer to open Data Source Designer.</span></span>  
  
2.  <span data-ttu-id="fbb1c-110">データ ソース デザイナーの **[権限借用情報]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-110">Click the **Impersonation Information** tab in Data Source Designer.</span></span>  
  
3.  <span data-ttu-id="fbb1c-111">このトピックの「 [権限借用のオプション](#bkmk_options) 」で説明するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-111">Choose an option described in [Impersonation options](#bkmk_options) in this topic.</span></span>  
  
## <a name="set-impersonation-options-in-management-studio"></a><span data-ttu-id="fbb1c-112">Management Studio での権限借用オプションの設定</span><span class="sxs-lookup"><span data-stu-id="fbb1c-112">Set impersonation options in Management Studio</span></span>  
 <span data-ttu-id="fbb1c-113">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、次のダイアログ ボックスのプロパティの参照ボタン ( **[...]** ) をクリックして、**[権限借用情報]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-113">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open the **Impersonation Information** dialog box by clicking the ellipsis (**...**) button for the following properties of these dialog boxes:</span></span>  
  
-   <span data-ttu-id="fbb1c-114">**[データベースのプロパティ]** ダイアログ ボックスの、[データ ソースの権限借用情報] プロパティ。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-114">**Database Properties** dialog box, through the Data Source Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="fbb1c-115">**[データ ソースのプロパティ]** ダイアログ ボックスの、[権限借用情報] プロパティ。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-115">**Data Source Properties** dialog box, through the Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="fbb1c-116">**[アセンブリのプロパティ]** ダイアログ ボックスの、[権限借用情報] プロパティ。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-116">**Assembly Properties** dialog box, through the Impersonation Info property.</span></span>  
  
##  <a name="impersonation-options"></a><a name="bkmk_options"></a> <span data-ttu-id="fbb1c-117">権限借用のオプション</span><span class="sxs-lookup"><span data-stu-id="fbb1c-117">Impersonation options</span></span>  
 <span data-ttu-id="fbb1c-118">ダイアログ ボックスのすべてのオプションを使用できますが、すべてのオプションが各シナリオに適しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-118">All options are available in the dialog box, but not all options are appropriate for every scenario.</span></span> <span data-ttu-id="fbb1c-119">以下の情報を参考にして、シナリオに最適なオプションを判断してください。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-119">Use the following information to determine the best option for your scenario.</span></span>  
  
 <span data-ttu-id="fbb1c-120">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="fbb1c-120">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="fbb1c-121">このオプションを選択すると、オブジェクトは、と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] いう形式で指定された Windows ユーザーアカウントのセキュリティ資格情報を使用します *\<Domain name>***\\***\<User account name>* 。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-121">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of a Windows user account specified in this format: *\<Domain name>***\\***\<User account name>*.</span></span>  
  
 <span data-ttu-id="fbb1c-122">データ アクセスのために特別に作成した専用の最小特権 Windows ユーザー ID を使用する場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-122">Choose this option to use a dedicated, least-privilege Windows user identity that you have created specifically for data access purposes.</span></span> <span data-ttu-id="fbb1c-123">たとえば、レポートで使用されるデータを取得するための汎用アカウントを定期的に作成している場合は、ここでそのアカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-123">For example, if you routinely create a general purpose account for retrieving data used in reports, you can specify that account here.</span></span>  
  
 <span data-ttu-id="fbb1c-124">多次元データベースの場合、処理、ROLAP クエリ、不一致バインド、ローカル キューブ、マイニング モデル、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に、指定した資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-124">For multidimensional databases, the specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="fbb1c-125">表形式データベースの場合、処理、リレーショナル データ ストアに対して (DirectQuery を使用して) 実行されるクエリ、不一致バインド、リモート パーティション、ターゲットからソースへの同期に、指定した資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-125">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), out-of-line bindings, remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="fbb1c-126">DMX OPENQUERY ステートメントの場合、このオプションは無視され、指定したユーザーのアカウントではなく現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-126">For DMX OPENQUERY statements, this option is ignored and the credentials of the current user will be used rather than the specified user account.</span></span>  
  
 <span data-ttu-id="fbb1c-127">**[サービス アカウントを使用する]**</span><span class="sxs-lookup"><span data-stu-id="fbb1c-127">**Use the service account**</span></span>  
 <span data-ttu-id="fbb1c-128">このオプションを選択すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを管理する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスに関連付けられているセキュリティ資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-128">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="fbb1c-129">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-129">This is the default option.</span></span> <span data-ttu-id="fbb1c-130">以前のリリースでは、これが、使用できる唯一のオプションでした。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-130">In previous releases, this was the only option you could use.</span></span> <span data-ttu-id="fbb1c-131">個々のユーザー アカウントではなく、サービス レベルでデータ アクセスを監視する場合は、このオプションを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-131">You might prefer this option to monitor data access at the service level rather than individual user accounts.</span></span>  
  
 <span data-ttu-id="fbb1c-132">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、使用しているオペレーティング システムに応じて、サービス アカウントとして NetworkService または特定の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス用に作成された組み込み仮想アカウントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-132">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], depending on the operating system you are using, the service account might be NetworkService or a built-in virtual account created for a specific [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="fbb1c-133">Windows 認証を使用する接続にサービス アカウントを使用する場合は、処理時にデータの取得に使用されるため、このアカウント用のデータベース ログインを忘れずに作成して読み取り権限を付与してください。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-133">If you choose the service account for a connection that uses Windows authentication, remember to create a database login for this account and grant read permissions, as it will be used to retrieve data during processing.</span></span> <span data-ttu-id="fbb1c-134">サービス アカウントの詳細については、「 [Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-134">For more information about the service account, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbb1c-135">データベース認証を使用する際、Analysis Services の専用の仮想アカウントでサービスを実行する場合は、 **[サービス アカウントを使用する]** 権限借用オプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-135">When using database authentication, you should choose the **Use the service account** impersonation option if the service is running under the dedicated virtual account for Analysis Services.</span></span> <span data-ttu-id="fbb1c-136">このアカウントには、ローカル ファイルにアクセスする権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-136">This account will have permissions to access local files.</span></span> <span data-ttu-id="fbb1c-137">一方、サービスを NetworkService として実行する場合は、 **[ローカル ログオンを許可する]** 権限を持つ最小特権の Windows ユーザー アカウントを使用する方が適しています。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-137">If the service runs as NetworkService, a better alternative is to use a least privilege Windows user account that has **Allow log on locally** permissions.</span></span> <span data-ttu-id="fbb1c-138">指定するアカウントによっては、Analysis Services プログラム フォルダーに対するファイル アクセスの権限も付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-138">Depending on the account you provide, you might also need to grant file access permissions on the Analysis Services program folder.</span></span>  
  
 <span data-ttu-id="fbb1c-139">多次元データベースの場合、処理、ROLAP クエリ、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に、サービス アカウント資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-139">For multidimensional databases, the service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="fbb1c-140">表形式データベースの場合、処理、リレーショナル データ ストアに対して (DirectQuery を使用して) 実行されるクエリ、リモート パーティション、ターゲットからソースへの同期に、指定した資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-140">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="fbb1c-141">DMX OPENQUERY ステートメント、ローカル キューブ、およびマイニング モデルの場合、サービス アカウント オプションを選択しても、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-141">For DMX OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used even if you choose the service account option.</span></span> <span data-ttu-id="fbb1c-142">サービス アカウント オプションは、不一致バインドではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-142">The service account option is not supported for out-of-line bindings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbb1c-143">サービス アカウントに Analysis Services インスタンスに対する管理者権限がない場合、キューブからデータ マイニング モデルを処理するときにエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-143">Errors can occur when processing a data mining model from a cube if the service account does not have administrator permissions on the Analysis Services instance.</span></span> <span data-ttu-id="fbb1c-144">詳細については、「 [マイニング構造: DataSource が OLAP キューブの場合の処理に関する問題](https://go.microsoft.com/fwlink/?LinkId=251610)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-144">For more information, see [Mining Structure: Issue while Processing when DataSource is OLAP Cube](https://go.microsoft.com/fwlink/?LinkId=251610).</span></span>  
  
 <span data-ttu-id="fbb1c-145">**[現在のユーザーの資格情報を使用する]**</span><span class="sxs-lookup"><span data-stu-id="fbb1c-145">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="fbb1c-146">このオプションを選択すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトにより、不一致バインド、DMX OPENQUERY、ローカル キューブ、マイニング モデルに現在のユーザーのセキュリティ資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-146">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span>  
  
 <span data-ttu-id="fbb1c-147">このオプションは表形式のデータベースではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-147">This option is not supported for tabular databases.</span></span>  
  
 <span data-ttu-id="fbb1c-148">ローカル キューブおよび不一致バインドを使用した処理を除き、このオプションは多次元データベースではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-148">With the exception of local cubes and processing using out-of-line bindings, this option is not supported for multidimensional databases.</span></span>  
  
 <span data-ttu-id="fbb1c-149">**[既定]** または **[継承]**</span><span class="sxs-lookup"><span data-stu-id="fbb1c-149">**Default** or **Inherit**</span></span>  
 <span data-ttu-id="fbb1c-150">**[既定]** はデータベース レベルで設定されている権限借用オプションで使用され、 **[継承]** はデータ ソース レベルで設定されている権限借用オプションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-150">The dialog box uses **Default** for the impersonation options set at the database level and **Inherit** for impersonation options set at the data source level.</span></span>  
  
 <span data-ttu-id="fbb1c-151">**データソース-Inherit オプション**</span><span class="sxs-lookup"><span data-stu-id="fbb1c-151">**Data Sources - Inherit Option**</span></span>  
  
 <span data-ttu-id="fbb1c-152">データ ソース レベルでは、 **[継承]** によって [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が親オブジェクトの権限借用オプションを使用することが指定されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-152">At the data source level, **Inherit** specifies that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should use the impersonation option of the parent object.</span></span> <span data-ttu-id="fbb1c-153">多次元モデルでは、親オブジェクトは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースです。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-153">In a multidimensional model, the parent object is the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="fbb1c-154">**[継承]** オプションを選択すると、対象のデータ ソースおよび同じデータベースに含まれる他のデータ ソースの権限借用設定を一元的に管理できます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-154">Choosing the **Inherit** option lets you centrally manage the impersonation settings for this and other data sources that are part of the same database.</span></span> <span data-ttu-id="fbb1c-155">このオプションを有効にするには、データベース レベルで特定の Windows ユーザー名とパスワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-155">For this option to be meaningful, choose a specific Windows user name and password at the database level.</span></span> <span data-ttu-id="fbb1c-156">データベース レベルで Windows ユーザー名とパスワードが指定されていない場合、データ ソースの **[継承]** とデータベースの **[既定]** の組み合わせは、サービス アカウント オプションを使用するのと同じです。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-156">Otherwise, the combination of **Inherit** on the data source and **Default** on the database are equivalent to using service account option.</span></span>  
  
 <span data-ttu-id="fbb1c-157">データベース レベルで Windows ユーザー名とパスワードを指定するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-157">To specify a Windows user name and password at the database level, do the following:</span></span>  
  
1.  <span data-ttu-id="fbb1c-158">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でデータベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-158">Right-click the database in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="fbb1c-159">**[データ ソースの権限借用情報]** で、Windows ユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-159">In **Data Source Impersonation Info**, specify a Windows user name and password.</span></span>  
  
3.  <span data-ttu-id="fbb1c-160">各データ ソースを右クリックし、プロパティを表示して、データ ソースが **[継承]** オプションを使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-160">Right-click each data source and view its properties to ensure that each one is using the **Inherit** option.</span></span>  
  
 <span data-ttu-id="fbb1c-161">データベース レベルでの既定の設定に関する詳細については、「[多次元データベースのプロパティ設定 &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-161">For more information about default settings at the database level, see [Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md).</span></span>  
  
 <span data-ttu-id="fbb1c-162">**Databases-既定のオプション**</span><span class="sxs-lookup"><span data-stu-id="fbb1c-162">**Databases - Default option**</span></span>  
  
 <span data-ttu-id="fbb1c-163">表形式データベースの場合、**既定**ではサービスアカウントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-163">For tabular databases, **Default** means use the service account.</span></span>  
  
 <span data-ttu-id="fbb1c-164">多次元データベースの場合、 **[既定]** はサービス アカウントを使用し、データ マイニング操作に現在のユーザーを使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="fbb1c-164">For multidimensional databases, **Default** means use the service account, and current user for data mining operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb1c-165">参照</span><span class="sxs-lookup"><span data-stu-id="fbb1c-165">See Also</span></span>  
 <span data-ttu-id="fbb1c-166">[SSAS 多次元&#41;&#40;データソースを作成する](create-a-data-source-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="fbb1c-166">[Create a Data Source &#40;SSAS Multidimensional&#41;](create-a-data-source-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="fbb1c-167">[SSAS 多次元&#41;&#40;データソースプロパティを設定する](set-data-source-properties-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="fbb1c-167">[Set Data Source Properties &#40;SSAS Multidimensional&#41;](set-data-source-properties-ssas-multidimensional.md) </span></span>  
 [<span data-ttu-id="fbb1c-168">SSAS 表形式&#41;&#40;DirectQuery デプロイシナリオ</span><span class="sxs-lookup"><span data-stu-id="fbb1c-168">DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;</span></span>](../directquery-deployment-scenarios-ssas-tabular.md)  
  
  
