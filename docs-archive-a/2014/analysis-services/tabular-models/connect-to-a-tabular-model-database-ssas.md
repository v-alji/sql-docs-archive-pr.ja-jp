---
title: テーブルモデルデータベースへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 983d0c8a-77da-4c6e-8638-283bcb14f143
author: minewiskan
ms.author: owend
ms.openlocfilehash: be41cc3ab493d126d12ba0cab572d484ee3348d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634681"
---
# <a name="connect-to-a-tabular-model-database-ssas"></a><span data-ttu-id="238c6-102">テーブル モデル データベースへの接続 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="238c6-102">Connect to a Tabular Model Database (SSAS)</span></span>
  <span data-ttu-id="238c6-103">テーブル モデルを構築し、Analysis Services テーブル モード サーバーに配置したら、クライアント アプリケーションからの使用を可能にするための権限を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="238c6-103">After you build a tabular model and deploy it to an Analysis Services tabular mode server, you need to set permissions that make it available to client applications.</span></span> <span data-ttu-id="238c6-104">このトピックでは、クライアント アプリケーションからデータベースに接続するための権限と方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="238c6-104">This topic explains how to permissions and how to connect to a database from client applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="238c6-105">既定では、ファイアウォールを構成するまで、Analysis Services へのリモート接続は利用できません。</span><span class="sxs-lookup"><span data-stu-id="238c6-105">By default, remote connections to Analysis Services are not available until you configure the firewall.</span></span> <span data-ttu-id="238c6-106">クライアント接続の名前付きインスタンスまたは既定のインスタンスを構成する場合は、適切なポートを開いていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="238c6-106">Be sure that you have opened the appropriate port if you are configuring a named or default instance for client connections.</span></span> <span data-ttu-id="238c6-107">詳細については、「 [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="238c6-107">For more information, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
 <span data-ttu-id="238c6-108">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="238c6-108">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="238c6-109">データベースに対するユーザー権限</span><span class="sxs-lookup"><span data-stu-id="238c6-109">User permissions on the database</span></span>](#bkmk_userpermissions)  
  
 [<span data-ttu-id="238c6-110">サーバーの管理権限</span><span class="sxs-lookup"><span data-stu-id="238c6-110">Administrative permissions on the server</span></span>](#bkmk_admin)  
  
 [<span data-ttu-id="238c6-111">Excel または SharePoint からの接続</span><span class="sxs-lookup"><span data-stu-id="238c6-111">Connecting from Excel or SharePoint</span></span>](#bkmk_excelconn)  
  
 [<span data-ttu-id="238c6-112">接続の問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="238c6-112">Troubleshooting Connection Problems</span></span>](#bkmk_Tshoot)  
  
##  <a name="user-permissions-on-the-database"></a><a name="bkmk_userpermissions"></a><span data-ttu-id="238c6-113">データベースに対するユーザー権限</span><span class="sxs-lookup"><span data-stu-id="238c6-113">User permissions on the database</span></span>  
 <span data-ttu-id="238c6-114">テーブル データベースに接続するユーザーには、読み取りアクセスを指定するデータベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-114">Users who connect to tabular databases must have membership in a database role that specifies Read access.</span></span>  
  
 <span data-ttu-id="238c6-115">ロール (および場合によってはロール メンバーシップ) が定義されるのは、モデルが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で作成されるときです。または、配置済みモデルの場合は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]によって使用されるときです。</span><span class="sxs-lookup"><span data-stu-id="238c6-115">Roles, and sometimes role membership, are defined when a model is authored in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], or for deployed models, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="238c6-116">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でロール マネージャーを使用したロールの作成の詳細については、「[ロールの作成および管理 &#40;SSAS テーブル&#41;](roles-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-116">For more information about creating roles by using Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], see [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span> <span data-ttu-id="238c6-117">配置済みモデルのロールの作成と管理の詳細については、「[テーブル モデル ロール &#40;SSAS テーブル&#41;](tabular-model-roles-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-117">For more information about creating and managing roles for a deployed model, see [Tabular Model Roles &#40;SSAS Tabular&#41;](tabular-model-roles-ssas-tabular.md).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="238c6-118">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のロール マネージャーを使用して定義済みロールを含むテーブル モデル プロジェクトを再配置すると、配置済みテーブル モデルに定義されたロールが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="238c6-118">Re-deploying a tabular model project with roles defined by using Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] will overwrite roles defined in a deployed tabular model.</span></span>  
  
##  <a name="administrative-permissions-on-the-server"></a><a name="bkmk_admin"></a> <span data-ttu-id="238c6-119">サーバーに対する管理権限</span><span class="sxs-lookup"><span data-stu-id="238c6-119">Administrative permissions on the server</span></span>  
 <span data-ttu-id="238c6-120">Excel ブックまたは Reporting Services レポートをホストするために SharePoint を使用している組織では、SharePoint ユーザーがテーブル モデル データを利用できるようにする追加の構成が必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-120">For organizations that use SharePoint for hosting Excel workbooks or Reporting Services reports, additional configuration is required to make tabular model data available to SharePoint users.</span></span> <span data-ttu-id="238c6-121">SharePoint を使用していない場合は、このセクションを省略してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-121">If you are not using SharePoint, skip this section.</span></span>  
  
 <span data-ttu-id="238c6-122">テーブル データを含む Excel ブックまたは [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートを表示するには、Excel Services または Reporting Services を実行するアカウントに、Analysis Services インスタンスに対する管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-122">Viewing Excel workbooks or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports that contain tabular data requires that the account used to run Excel Services or Reporting Services has administrator permissions on the Analysis Services instance.</span></span> <span data-ttu-id="238c6-123">これらのサービスが Analysis Services インスタンスによって信頼されるようにするには、管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-123">Administrative permissions are required so that these services are trusted by the Analysis Services instance.</span></span>  
  
#### <a name="grant-administrative-access-on-the-server"></a><span data-ttu-id="238c6-124">サーバーに対する管理アクセス権の付与</span><span class="sxs-lookup"><span data-stu-id="238c6-124">Grant administrative access on the server</span></span>  
  
1.  <span data-ttu-id="238c6-125">サーバーの全体管理で、[サービス アカウントの構成] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="238c6-125">In Central Administration, open the Configure service accounts page.</span></span>  
  
2.  <span data-ttu-id="238c6-126">Excel Services によって使用されるサービス アプリケーション プールを選択します。</span><span class="sxs-lookup"><span data-stu-id="238c6-126">Select the service application pool used by Excel Services.</span></span> <span data-ttu-id="238c6-127">これは、**サービスアプリケーションプール-SharePoint Web サービスシステム**またはカスタムアプリケーションプールである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="238c6-127">It might **Service Application Pool - SharePoint Web Services System** or a custom application pool.</span></span> <span data-ttu-id="238c6-128">Excel Services によって使用される管理アカウントがページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="238c6-128">The managed account used by Excel Services will appear on the page.</span></span>  
  
     <span data-ttu-id="238c6-129">SharePoint モードの Reporting Services を含む SharePoint ファームでは、Reporting Services サービス アプリケーションのアカウント情報も取得します。</span><span class="sxs-lookup"><span data-stu-id="238c6-129">For SharePoint farms that include Reporting Services in SharePoint mode, get the account information for the Reporting Services service application as well.</span></span>  
  
     <span data-ttu-id="238c6-130">次の手順では、これらのアカウントを Analysis Services インスタンスのサーバー ロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="238c6-130">In the following steps, you will add these accounts to the Server role on the Analysis Services instance.</span></span>  
  
3.  <span data-ttu-id="238c6-131">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、サーバー インスタンスを右クリックして **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="238c6-131">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], right-click the server instance, and select **Properties**.</span></span> <span data-ttu-id="238c6-132">オブジェクト エクスプローラーで **[ロール]** を右クリックして、 **[新しいロール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="238c6-132">In Object Explorer, right-click **Roles** and select **New Role**.</span></span>  
  
4.  <span data-ttu-id="238c6-133">[Analysis Services のプロパティ] ページで、 **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="238c6-133">In the Analysis Services Properties page, click **Security**.</span></span>  
  
5.  <span data-ttu-id="238c6-134">**[追加]** をクリックし、Excel Services によって使用されるアカウントを入力します。Reporting Services によって使用されるアカウントも続けて入力します。</span><span class="sxs-lookup"><span data-stu-id="238c6-134">Click **Add**, and then enter the account used by Excel Services, followed by the account used by Reporting Services.</span></span>  
  
##  <a name="connecting-from-excel-or-sharepoint"></a><a name="bkmk_excelconn"></a><span data-ttu-id="238c6-135">Excel または SharePoint からの接続</span><span class="sxs-lookup"><span data-stu-id="238c6-135">Connecting from Excel or SharePoint</span></span>  
 <span data-ttu-id="238c6-136">Analysis Services データベースへのアクセスを提供するクライアント ライブラリを使用して、テーブル モード サーバー上で実行される model データベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="238c6-136">Client libraries that provide access to Analysis Services databases can be used to connect to model databases that run on a tabular mode server.</span></span> <span data-ttu-id="238c6-137">ライブラリには、Analysis Services OLE DB プロバイダー、ADOMD.NET、および AMO が含まれています。</span><span class="sxs-lookup"><span data-stu-id="238c6-137">Libraries include the Analysis Services OLE DB provider, ADOMD.NET, and AMO.</span></span>  
  
 <span data-ttu-id="238c6-138">Excel では、OLE DB プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="238c6-138">Excel uses the OLE DB provider.</span></span> <span data-ttu-id="238c6-139">SQL Server 2008 R2 の MSOLAP.4 (ファイル名 msolap100.dll、バージョン 10.50.1600.1)、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] バージョンの PowerPivot for Excel と共にインストールされる MSOLAP.5 (ファイル名 msolap110.dll) がある場合、テーブル データベースに接続されるバージョンを持っています。</span><span class="sxs-lookup"><span data-stu-id="238c6-139">If you have either MSOLAP.4 from SQL Server 2008 R2 (file name msolap100.dll, version 10.50.1600.1), or MSOLAP.5 (filename msolap110.dll) that is installed with the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] version of PowerPivot for Excel, you have a version that will connect to tabular databases.</span></span>  
  
 <span data-ttu-id="238c6-140">Excel から model データベースに接続するには、次のいずれかのアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="238c6-140">Choose from the following approaches to connect to model databases from Excel:</span></span>  
  
-   <span data-ttu-id="238c6-141">次のセクションで説明する手順を使用して、Excel 内からデータ接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="238c6-141">Create a data connection from within Excel, using the instructions provided in the next section.</span></span>  
  
-   <span data-ttu-id="238c6-142">Analysis Services テーブル モード サーバー上で実行されているデータベースへのリダイレクトを提供する BI セマンティック モデル接続 (.bism) ファイルを SharePoint で作成します。</span><span class="sxs-lookup"><span data-stu-id="238c6-142">Create a BI semantic model connection (.bism) file in SharePoint that provides redirection to a database running on an Analysis Services tabular mode server.</span></span> <span data-ttu-id="238c6-143">BI セマンティック モデル接続ファイルにより、その接続で指定した model データベースを使用する Excel を起動する右クリック コマンドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="238c6-143">A BI semantic model connection file provides a right-click command that launches Excel using the model database that you specified in the connection.</span></span> <span data-ttu-id="238c6-144">Reporting Services がインストールされている場合には、これによって [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] も起動されます。</span><span class="sxs-lookup"><span data-stu-id="238c6-144">It will also launch [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] if Reporting Services is installed.</span></span> <span data-ttu-id="238c6-145">BI セマンティック モデル接続ファイルの作成および使用の詳細については、「 [テーブル モデル データベースへの BI セマンティック モデル接続の作成](../power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-145">For more information about creating and using BI semantic model connection files, see [Create a BI Semantic Model Connection to a Tabular Model Database](../power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).</span></span>  
  
-   <span data-ttu-id="238c6-146">データ ソースとしてテーブル データベースを参照する Reporting Services 共有データ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="238c6-146">Create a Reporting Services shared data source that references a tabular database as the data source.</span></span> <span data-ttu-id="238c6-147">SharePoint で共有データ ソースを作成し、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]を起動するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="238c6-147">You can create the shared data source in SharePoint and use it to launch [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
#### <a name="connect-from-excel"></a><span data-ttu-id="238c6-148">Excel からの接続</span><span class="sxs-lookup"><span data-stu-id="238c6-148">Connect from Excel</span></span>  
  
1.  <span data-ttu-id="238c6-149">Excel の **[データ]** タブの **[外部データの取り込み]** で、 **[その他のデータ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="238c6-149">In Excel, on the **Data** tab, in **Get External Data**, click **From Other Sources**.</span></span>  
  
2.  <span data-ttu-id="238c6-150">**[Analysis Services から]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="238c6-150">Select **From Analysis Services**.</span></span>  
  
3.  <span data-ttu-id="238c6-151">**[サーバー名]** に、データベースをホストする Analysis Services インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="238c6-151">In **Server Name**, specify the Analysis Services instance that hosts the database.</span></span> <span data-ttu-id="238c6-152">通常、サーバー名は、サーバー ソフトウェアを実行するコンピューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="238c6-152">The server name is often the name of the computer that runs the server software.</span></span> <span data-ttu-id="238c6-153">サーバーが名前付きインスタンスとしてインストールされている場合は、<instancename の形式で名前を指定する必要があります \<servername> \\ \> 。</span><span class="sxs-lookup"><span data-stu-id="238c6-153">If the server was installed as a named instance, you must specify the name in this format: \<servername>\\<instancename\>.</span></span>  
  
     <span data-ttu-id="238c6-154">スタンドアロン テーブル配置用にサーバー インスタンスを構成する必要があります。そのサーバー インスタンスには、アクセスを許可する受信の規則が必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-154">The server instance must be configured for standalone tabular deployment and the server instance must have an inbound rule that allows access to it.</span></span> <span data-ttu-id="238c6-155">詳細については、「 [Analysis Services インスタンスのサーバー モードの決定](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) 」および「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-155">For more information, see [Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) and [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
4.  <span data-ttu-id="238c6-156">データベースに対する読み取り権限がある場合は、ログオン資格情報について **[Windows 認証を使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="238c6-156">For log on credentials, choose **Use Windows Authentication** if you have read permissions to the database.</span></span> <span data-ttu-id="238c6-157">それ以外の場合は、 **[以下のユーザー名とパスワードを使用する]** を選択し、データベース権限を持つ Windows アカウントのユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="238c6-157">Otherwise, choose **Use the Following User Name and Password**, and enter the username and password of a Windows account that has database permissions.</span></span> <span data-ttu-id="238c6-158">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="238c6-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="238c6-159">データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="238c6-159">Select the database.</span></span> <span data-ttu-id="238c6-160">有効なデータベースを選択すると、データベースの単一の **モデル** キューブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="238c6-160">A valid selection will show a single **Model** cube for the database.</span></span> <span data-ttu-id="238c6-161">**[次へ]** をクリックしてから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="238c6-161">Click **Next** and then click **Finish**.</span></span>  
  
 <span data-ttu-id="238c6-162">接続を確立した後は、データを使用して、ピボットテーブルやピボットグラフを作成できます。</span><span class="sxs-lookup"><span data-stu-id="238c6-162">After the connection is established, you can use the data to create a PivotTable or PivotChart.</span></span> <span data-ttu-id="238c6-163">詳しくは、後の「 [Excel で分析 &#40;SSAS テーブル&#41;](analyze-in-excel-ssas-tabular.md)で [ロール マネージャー] ダイアログ ボックスを使用してロールを定義するテーブル モデル作成者向けです。</span><span class="sxs-lookup"><span data-stu-id="238c6-163">For more information, see [Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md).</span></span>  
  
##  <a name="connect-from-sharepoint"></a><a name="bkmk_sharepoint"></a><span data-ttu-id="238c6-164">SharePoint からの接続</span><span class="sxs-lookup"><span data-stu-id="238c6-164">Connect from SharePoint</span></span>  
 <span data-ttu-id="238c6-165">PowerPivot for SharePoint を使用している場合は、Analysis Services テーブル モード サーバー上で実行されているデータベースへのリダイレクトを提供する BI セマンティック モデル接続ファイルを SharePoint で作成できます。</span><span class="sxs-lookup"><span data-stu-id="238c6-165">If you are using PowerPivot for SharePoint, you can create a BI semantic model connection file in SharePoint that provides redirection to a database running on an Analysis Services tabular mode server.</span></span> <span data-ttu-id="238c6-166">BI セマンティック モデル接続により、データベースへの HTTP エンドポイントが提供されます。</span><span class="sxs-lookup"><span data-stu-id="238c6-166">A BI semantic model connection provides an HTTP endpoint to a database.</span></span> <span data-ttu-id="238c6-167">また、SharePoint サイト上のドキュメントを定期的に使用するナレッジ ワーカーが簡単にテーブル モデルにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="238c6-167">It also simplifies tabular model access for knowledge workers who routinely use documents on a SharePoint site.</span></span> <span data-ttu-id="238c6-168">ナレッジ ワーカーがテーブル モデル データベースにアクセスするために知っておく必要があるのは、BI セマンティック モデル接続ファイルの場所またはその URL だけです。</span><span class="sxs-lookup"><span data-stu-id="238c6-168">Knowledge workers only need to know the location of the BI semantic model connection file or its URL to access tabular model databases.</span></span> <span data-ttu-id="238c6-169">サーバーの場所やデータベース名に関する詳細は、BI セマンティック モデル接続にカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="238c6-169">Details about server location or database name are encapsulated in the BI semantic model connection.</span></span> <span data-ttu-id="238c6-170">BI セマンティックモデル接続ファイルの作成と使用の詳細については、「 [POWERPIVOT Bi セマンティックモデル接続 &#40;](../power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md) 」を参照してください&#41;。また、[テーブルモデルデータベースへの Bi セマンティックモデル接続を作成](../power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-170">For more information about creating and using BI semantic model connection files, see [PowerPivot BI Semantic Model Connection &#40;.bism&#41;](../power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md) and   [Create a BI Semantic Model Connection to a Tabular Model Database](../power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).</span></span>  
  
##  <a name="troubleshooting-connection-problems"></a><a name="bkmk_Tshoot"></a><span data-ttu-id="238c6-171">接続の問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="238c6-171">Troubleshooting Connection Problems</span></span>  
 <span data-ttu-id="238c6-172">このセクションでは、テーブル モデル データベースに接続する際に発生する問題の原因と解決手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="238c6-172">This section provides cause and resolution steps for problems that occur while connecting to a tabular model database.</span></span>  
  
 <span data-ttu-id="238c6-173">**データ接続ウィザードで、指定したデータ ソースからデータベースのリストを取得できません。**</span><span class="sxs-lookup"><span data-stu-id="238c6-173">**The Data Connection Wizard cannot obtain a list of databases from the specified data source.**</span></span>  
  
 <span data-ttu-id="238c6-174">データをインポートする場合に、十分な権限がないのに、ウィザードを使用してリモートの Analysis Services サーバー上のテーブル モデル データベースに接続しようとすると、この Microsoft Excel エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="238c6-174">When importing data, this Microsoft Excel error occurs when you try to use the Wizard to connect to a tabular model database on a remote Analysis Services server, and you do not have sufficient permissions.</span></span> <span data-ttu-id="238c6-175">このエラーを解決するには、データベースに対するユーザー アクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-175">To resolve this error, you must have user access rights on the database.</span></span> <span data-ttu-id="238c6-176">データへのユーザー アクセスの許可については、このトピックの前半で説明している手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-176">Refer to the instructions provided earlier in this topic for granting user access to data.</span></span>  
  
 <span data-ttu-id="238c6-177">**外部データソースへの接続を確立しようとしているときにエラーが発生しました。次の接続を更新できませんでした: \<model name> サンドボックス**</span><span class="sxs-lookup"><span data-stu-id="238c6-177">**An error occurred during an attempt to establish a connection to the external data source. The following connections failed to refresh: \<model name> Sandbox**</span></span>  
  
 <span data-ttu-id="238c6-178">SharePoint では、モデル データを使用するピボットテーブルでデータのフィルター処理などのデータ操作を実行しようとすると、この Microsoft Excel エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="238c6-178">On SharePoint, this Microsoft Excel error occurs when you attempt data interaction, such as filtering data, in a PivotTable that uses model data.</span></span> <span data-ttu-id="238c6-179">このエラーは、リモートの Analysis Services サーバーに対する十分な権限がないために発生します。</span><span class="sxs-lookup"><span data-stu-id="238c6-179">The error occurs because you do not have sufficient permissions on the remote Analysis Services server.</span></span> <span data-ttu-id="238c6-180">このエラーを解決するには、データベースに対するユーザー アクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-180">To resolve this error, you must have user access rights on the database.</span></span> <span data-ttu-id="238c6-181">データへのユーザー アクセスの許可については、このトピックの前半で説明している手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-181">Refer to the instructions provided earlier in this topic for granting user access to data.</span></span>  
  
 <span data-ttu-id="238c6-182">**この操作を実行しようとして、エラーが発生しました。ブックを再読み込みしてから、この操作をもう一度実行してください。**</span><span class="sxs-lookup"><span data-stu-id="238c6-182">**An error occurred while attempting to perform this operation. Reload the workbook, and then try to perform this operation again.**</span></span>  
  
 <span data-ttu-id="238c6-183">SharePoint では、モデル データを使用するピボットテーブルでデータのフィルター処理などのデータ操作を実行しようとすると、この Microsoft Excel エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="238c6-183">On SharePoint, this Microsoft Excel error occurs when you attempt data interaction, such as filtering data, in a PivotTable that uses model data.</span></span> <span data-ttu-id="238c6-184">このエラーは、Excel Services が、モデル データが配置されている Analysis Services インスタンスによって信頼されていないために発生します。</span><span class="sxs-lookup"><span data-stu-id="238c6-184">The error occurs because Excel Services is not trusted by the Analysis Services instance on which the model data is deployed.</span></span> <span data-ttu-id="238c6-185">このエラーを解決するには、Analysis Services インスタンスに対する Excel Services の管理権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="238c6-185">To resolve this error, grant Excel Services administrative permission on the Analysis Services instance.</span></span> <span data-ttu-id="238c6-186">管理権限の付与については、このトピックの前半で説明している手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="238c6-186">Refer to the instructions provided earlier in this topic for granting administrator permissions.</span></span> <span data-ttu-id="238c6-187">エラーが引き続き発生する場合は、Excel Services アプリケーション プールを再利用します。</span><span class="sxs-lookup"><span data-stu-id="238c6-187">If the error persists, recycle the Excel Services application pool.</span></span>  
  
 <span data-ttu-id="238c6-188">**ブックで使用されている外部データ ソースへの接続を確立しようとするとエラーが発生しました。**</span><span class="sxs-lookup"><span data-stu-id="238c6-188">**An error occurred during an attempt to establish a connection to the external data source used in the workbook**</span></span>  
  
 <span data-ttu-id="238c6-189">SharePoint では、モデル データを使用するピボットテーブルでデータのフィルター処理などのデータ操作を実行しようとすると、この Microsoft Excel エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="238c6-189">On SharePoint, this Microsoft Excel error occurs when you attempt data interaction, such as filtering data, in a PivotTable that uses model data.</span></span> <span data-ttu-id="238c6-190">このエラーは、ユーザーがブックに対する十分な SharePoint 権限を持っていないために発生します。</span><span class="sxs-lookup"><span data-stu-id="238c6-190">The error occurs because the user does not have sufficient SharePoint permissions on the workbook.</span></span> <span data-ttu-id="238c6-191">ユーザーには、 **読み取り** 権限以上の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="238c6-191">The user must have **Read** permissions or above.</span></span> <span data-ttu-id="238c6-192">データにアクセスするには、**表示のみ** 権限では不十分です。</span><span class="sxs-lookup"><span data-stu-id="238c6-192">**View-Only** permissions are not sufficient for data access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238c6-193">参照</span><span class="sxs-lookup"><span data-stu-id="238c6-193">See Also</span></span>  
 [<span data-ttu-id="238c6-194">テーブル モデル ソリューションの配置 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="238c6-194">Tabular Model Solution Deployment &#40;SSAS Tabular&#41;</span></span>](tabular-model-solution-deployment-ssas-tabular.md)  
  
  