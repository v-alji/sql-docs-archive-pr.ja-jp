---
title: 自動実行アカウントの構成 (SSRS 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- no credentials option [Reporting Services]
- security [Reporting Services], unattended report processing
- unattended report processing [Reporting Services]
- credentials [Reporting Services]
- external data sources [Reporting Services]
- accounts [Reporting Services]
- reports [Reporting Services], processing
ms.assetid: 4e50733e-bd8c-4bf6-8379-98b1531bb9ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 437b28b57bc304d079acea3123983bed389341ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716122"
---
# <a name="configure-the-unattended-execution-account-ssrs-configuration-manager"></a><span data-ttu-id="e6238-102">自動実行アカウントの構成 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="e6238-102">Configure the Unattended Execution Account (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e6238-103">には、自動レポート処理とネットワークを介した接続要求の送信に使用される特別なアカウントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e6238-103">provides a special account that is used for unattended report processing and for sending connection requests across the network.</span></span> <span data-ttu-id="e6238-104">アカウントは次の場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="e6238-104">The account is used in the following ways:</span></span>  
  
-   <span data-ttu-id="e6238-105">データベース認証を使用するレポートに対する接続要求のネットワーク経由での送信や、認証を必要としないまたは使用しない外部レポート データ ソースへの接続。</span><span class="sxs-lookup"><span data-stu-id="e6238-105">Send connection requests over the network for reports that use database authentication, or connect to external report data sources that do not require or use authentication.</span></span> <span data-ttu-id="e6238-106">詳細については、SQL Server オンライン ブックの「 [レポート データ ソースに関する資格情報と接続情報を指定する](../../integration-services/connection-manager/data-sources.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6238-106">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in SQL Server Books Online.</span></span>  
  
-   <span data-ttu-id="e6238-107">レポートに使用する外部の画像ファイルの取得。</span><span class="sxs-lookup"><span data-stu-id="e6238-107">Retrieve external image files that are used in report.</span></span> <span data-ttu-id="e6238-108">匿名アクセスでアクセスできない画像ファイルを使用する場合は、自動レポート処理アカウントを構成し、アカウントに対してファイルへのアクセス許可を与えます。</span><span class="sxs-lookup"><span data-stu-id="e6238-108">If you want to use an image file and the file cannot be accessed through Anonymous access, you can configure the unattended report processing account and grant the account permission to access the file.</span></span>  
  
 <span data-ttu-id="e6238-109">自動レポート処理とは、ユーザーの要求ではなく、イベント (スケジュール ドリブンのイベントまたはデータ更新イベント) によって起動されたレポート実行処理を示します。</span><span class="sxs-lookup"><span data-stu-id="e6238-109">Unattended report processing refers to any report execution process that is triggered by an event (either a schedule-driven event or data refresh event) rather than a user request.</span></span> <span data-ttu-id="e6238-110">レポート サーバーは、自動レポート処理アカウントを使用して、外部データ ソースをホストしているコンピューターにログオンします。</span><span class="sxs-lookup"><span data-stu-id="e6238-110">The report server uses the unattended report processing account to log on to the computer that hosts the external data source.</span></span> <span data-ttu-id="e6238-111">レポート サーバー サービス アカウントの資格情報は他のコンピューターへの接続に使用されないため、このアカウントは必要です。</span><span class="sxs-lookup"><span data-stu-id="e6238-111">This account is necessary because the credentials of the Report Server service account are never used to connect to other computers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e6238-112">アカウントの構成は任意ですが、</span><span class="sxs-lookup"><span data-stu-id="e6238-112">Configuring the account is optional.</span></span> <span data-ttu-id="e6238-113">構成しない場合は、一部のデータ ソースに接続するときのオプションを制限することになり、リモート コンピューターから画像ファイルを取得できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-113">However, if you do not configure it, you will limit your options for connecting to some data sources, and you might not be able to retrieve image files from remote computers.</span></span> <span data-ttu-id="e6238-114">アカウントを構成する場合は、アカウントを最新の状態に保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-114">If you do configure the account, you must keep it up to date.</span></span> <span data-ttu-id="e6238-115">特に、パスワードの有効期限が切れたり、Active Directory でアカウント情報が変更されると、次回レポートを処理するときに "ログオンに失敗しました。(rsLogonFailed) ログオン失敗: ユーザー名が不明またはパスワードが正しくありません。" というエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e6238-115">Specifically, if you allow a password to expire or the account information is changed in Active Directory, you will encounter the following error the next time a report is processed: "Logon failed (rsLogonFailed) Logon failure: unknown user name or bad password."</span></span> <span data-ttu-id="e6238-116">外部画像を取得したり外部コンピューターに接続要求を送信する場合でも、自動レポート処理アカウントの適切なメンテナンスは必須です。</span><span class="sxs-lookup"><span data-stu-id="e6238-116">Proper maintenance of the unattended report processing account is essential, even if you never retrieve external images or send connection requests to external computers.</span></span> <span data-ttu-id="e6238-117">構成したアカウントを使用していない場合は、アカウントを削除すると、日常的なアカウント メンテナンス作業を行わずに済みます。</span><span class="sxs-lookup"><span data-stu-id="e6238-117">If you configure the account but then find that you are not using it, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
## <a name="how-to-configure-the-account"></a><span data-ttu-id="e6238-118">アカウントの構成方法</span><span class="sxs-lookup"><span data-stu-id="e6238-118">How to Configure the Account</span></span>  
 <span data-ttu-id="e6238-119">ドメイン ユーザー アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-119">You must use a domain user account.</span></span> <span data-ttu-id="e6238-120">目的上このアカウントは、レポート サーバー サービスの実行に使用されるアカウントとは別のアカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-120">To serve its intended purpose, this account should be different than the one used to run the Report Server service.</span></span> <span data-ttu-id="e6238-121">必ず最小限の権限 (十分なネットワーク接続権限のある読み取り専用アクセス) を持つアカウントを使用し、アクセスする対象を、レポート サーバーにデータ ソースとリソースを提供するコンピューターのみに制限してください。</span><span class="sxs-lookup"><span data-stu-id="e6238-121">Be sure to use an account that has minimum permissions (read-only access with network connection permissions is sufficient) and limited access to just those computers that provide data sources and resources to the report server.</span></span> <span data-ttu-id="e6238-122">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6238-122">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 <span data-ttu-id="e6238-123">アカウントを指定するには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールまたは **rsconfig** ユーティリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e6238-123">To specify the account, you can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool or the **rsconfig** utility.</span></span> <span data-ttu-id="e6238-124">自動実行アカウントを構成する最も簡単な方法は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを実行して、[実行アカウント] ページで資格情報を指定することです。</span><span class="sxs-lookup"><span data-stu-id="e6238-124">The easiest way to configure the unattended execution account is to run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and specify credentials in the Execution Account page.</span></span>  
  
1.  <span data-ttu-id="e6238-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動し、構成するレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6238-125">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span> <span data-ttu-id="e6238-126">手順については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6238-126">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e6238-127">[実行アカウント] ページで、 **[実行アカウントの指定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6238-127">On the Execution Account page, select **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="e6238-128">アカウントとパスワードを入力し、パスワードを再入力して、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6238-128">Type the account and password, retype the password, and then click **Apply**.</span></span>  
  
### <a name="using-rsconfig-utility"></a><span data-ttu-id="e6238-129">RSCONFIG ユーティリティの使用</span><span class="sxs-lookup"><span data-stu-id="e6238-129">Using RSCONFIG Utility</span></span>  
 <span data-ttu-id="e6238-130">アカウントを設定するもう 1 つの方法は、 **rsconfig** ユーティリティを使用することです。</span><span class="sxs-lookup"><span data-stu-id="e6238-130">Another way to set the account is to use the **rsconfig** utility.</span></span> <span data-ttu-id="e6238-131">アカウントを指定するには、 **rsconfig** の **-e**引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e6238-131">To specify the account, use the **-e** argument of **rsconfig**.</span></span> <span data-ttu-id="e6238-132">**rsconfig** に **-e** 引数を指定すると、構成ファイルにアカウント情報を書き込むようユーティリティに指示できます。</span><span class="sxs-lookup"><span data-stu-id="e6238-132">Specifying the **-e** argument for **rsconfig** directs the utility to write the account information to the configuration file.</span></span> <span data-ttu-id="e6238-133">RSreportserver.config へのパスを指定する必要はありません。アカウントを構成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e6238-133">You do not need to specify a path to RSreportserver.config. Follow these steps to configure the account.</span></span>  
  
1.  <span data-ttu-id="e6238-134">レポート サーバーにデータまたはサービスを提供するコンピューターおよびサーバーに対してアクセス権を持つ、ドメイン アカウントを作成または選択します。</span><span class="sxs-lookup"><span data-stu-id="e6238-134">Create or select a domain account that has access to computers and servers that provide data or services to a report server.</span></span> <span data-ttu-id="e6238-135">少ない権限を持つアカウントを使用することをお勧めします (たとえば、読み取り専用権限)。</span><span class="sxs-lookup"><span data-stu-id="e6238-135">You should use an account that has reduced permissions (for example, read-only permissions).</span></span>  
  
2.  <span data-ttu-id="e6238-136">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックし、 **「cmd」** と入力して **[OK]** をクリックして、コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e6238-136">Open a command prompt: On the **Start** menu, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e6238-137">次のコマンドを入力して、ローカル レポート サーバー インスタンス上でアカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="e6238-137">Type the following command to configure the account on a local report server instance:</span></span>  
  
     <span data-ttu-id="e6238-138">**rsconfig-e-u \<domain/username> -p\<password>**</span><span class="sxs-lookup"><span data-stu-id="e6238-138">**rsconfig -e -u\<domain/username> -p\<password>**</span></span>  
  
 <span data-ttu-id="e6238-139">**rsconfig -e** では、他にも引数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e6238-139">**rsconfig -e** supports additional arguments.</span></span> <span data-ttu-id="e6238-140">構文の詳細およびコマンド例については、SQL Server オンライン ブックの「[rsconfig ユーティリティ (SSRS)](../tools/rsconfig-utility-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6238-140">For more information about syntax and to view command examples, see [rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) in SQL Server Books Online.</span></span>  
  
### <a name="how-account-information-is-stored"></a><span data-ttu-id="e6238-141">アカウント情報の保存方法</span><span class="sxs-lookup"><span data-stu-id="e6238-141">How Account Information is Stored</span></span>  
 <span data-ttu-id="e6238-142">アカウントを設定すると、ローカルまたはリモートのレポート サーバー インスタンス上の RSreportserver.config ファイル内で、暗号化された値として次の設定が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e6238-142">When you set the account, the following settings are specified as encrypted values in the RSreportserver.config file on a local or remote report server instance:</span></span>  
  
```  
<UnattendedExecutionAccount>  
     <UserName></UserName>  
     <Password></Password>  
     <Domain></Domain>  
</UnattendedExecutionAccount>  
```  
  
 <span data-ttu-id="e6238-143">いったん値を設定すると、暗号化解除してプレーン テキストで表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="e6238-143">Once you set the values, you cannot decrypt them to view the values in plain text.</span></span> <span data-ttu-id="e6238-144">値を入力し間違えた場合や、指定した値を忘れた場合は、Reporting Services 構成ツールを使用するか、 **rsconfig -e** を実行して最初からやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-144">If you mistype the values or forget the values you specified, you must use the Reporting Services Configuration tool or run **rsconfig -e** to start over.</span></span>  
  
## <a name="how-to-use-the-unattended-report-processing-account"></a><span data-ttu-id="e6238-145">自動レポート処理アカウントの使用方法</span><span class="sxs-lookup"><span data-stu-id="e6238-145">How to Use the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="e6238-146">画像ファイルを取得する際、レポート サーバーでは自動的にこのアカウントが使用され、ユーザー側で特別な操作を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e6238-146">To retrieve image files, the report server uses the account automatically and no specific action is required on your part.</span></span> <span data-ttu-id="e6238-147">このアカウントを使用してレポート用のデータを提供する外部データ ソースに接続するには、レポート データ ソースまたは共有データ ソースの [データ ソースのプロパティ] ページで **[資格情報の種類]** オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-147">To use the account to connect to external data sources that provide data to reports, you must specify a **Credential Type** option in the data source properties page of the report data source or shared data source:</span></span>  
  
-   <span data-ttu-id="e6238-148">レポート マネージャーまたは SharePoint サイトで、 **[資格情報は必要ありません]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6238-148">In Report Manager or on a SharePoint site, select the **Credentials are not required** option.</span></span>  
  
 <span data-ttu-id="e6238-149">自動レポート処理アカウントは主に外部サーバーへの接続に使用されますが、データベース サーバーへのログインには使用されません。</span><span class="sxs-lookup"><span data-stu-id="e6238-149">The unattended report processing account is used primarily to connect to external servers, and not as a login to database servers.</span></span> <span data-ttu-id="e6238-150">アカウント資格情報を使用してデータベースにログインする場合は、資格情報を接続文字列に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-150">If you want to use the account credentials to log in to a database, you must specify credentials in the connection string.</span></span> <span data-ttu-id="e6238-151">データベース サーバーで Windows 統合セキュリティがサポートされ、自動実行レポート処理に使用されるアカウントにデータベースの読み取り権限がある場合は、 **Integrated Security=SSPI** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e6238-151">You can specify **Integrated Security=SSPI** if the database server supports Windows integrated security and the account used for unattended report processing has permission to read the database.</span></span> <span data-ttu-id="e6238-152">それ以外の場合は、接続文字列にユーザー名およびパスワードを入力する必要があり、これはデータ ソース接続プロパティを編集する権限を持つすべてのユーザーにクリア テキストで表示されます。</span><span class="sxs-lookup"><span data-stu-id="e6238-152">Otherwise, you must enter the user name and password in the connection string, where it appears in clear text to any user who has permission to edit data source connection properties.</span></span>  
  
 <span data-ttu-id="e6238-153">接続の確立後に自動実行レポート処理アカウントを使用してデータを取得することもできますが、それは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="e6238-153">Although you are not prevented from using the unattended report processing account to retrieve data after the connection is made, doing so is not recommended.</span></span> <span data-ttu-id="e6238-154">このアカウントは、ごく特定の機能に対してだけ使用されることを意図しています。</span><span class="sxs-lookup"><span data-stu-id="e6238-154">The account is supposed to be used for very specific functions.</span></span> <span data-ttu-id="e6238-155">データの取得に使用した場合、意図された目的に反することになります。</span><span class="sxs-lookup"><span data-stu-id="e6238-155">If you use it to retrieve data, you undermine the purpose for which it is intended.</span></span>  
  
## <a name="how-to-maintain-the-unattended-report-processing-account"></a><span data-ttu-id="e6238-156">自動レポート処理アカウントのメンテナンス方法</span><span class="sxs-lookup"><span data-stu-id="e6238-156">How to Maintain the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="e6238-157">自動レポート処理アカウントを構成したら、アカウントとパスワードを最新の状態に保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6238-157">Once you define the account, you must ensure that the account and password are kept up to date.</span></span> <span data-ttu-id="e6238-158">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用すると、このアカウントに関する情報を保存している構成設定を更新できます。</span><span class="sxs-lookup"><span data-stu-id="e6238-158">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to update the configuration settings that store information about this account.</span></span>  
  
1.  <span data-ttu-id="e6238-159">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動し、構成するレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6238-159">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="e6238-160">[実行アカウント] ページで、 **[実行アカウントの指定]** がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6238-160">On the Execution Account page, verify that **Specify an execution account** is selected.</span></span>  
  
3.  <span data-ttu-id="e6238-161">新しいアカウントまたはパスワードを入力し、確認のためもう一度パスワードを入力して、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6238-161">Type the new account or password, retype the password, and then click **Apply**.</span></span>  
  
## <a name="how-to-delete-the-unattended-report-processing-account"></a><span data-ttu-id="e6238-162">自動レポート処理アカウントの削除方法</span><span class="sxs-lookup"><span data-stu-id="e6238-162">How to Delete the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="e6238-163">アカウントを使用していない場合は、アカウントを削除すると、日常的なアカウント メンテナンス作業を行わずに済みます。</span><span class="sxs-lookup"><span data-stu-id="e6238-163">If you are not using the account, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
1.  <span data-ttu-id="e6238-164">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動し、構成するレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6238-164">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="e6238-165">[実行アカウント] ページで、 **[実行アカウントの指定]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="e6238-165">On the Execution Account page, clear **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="e6238-166">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6238-166">Click **Apply**.</span></span>  
  
 <span data-ttu-id="e6238-167">アカウント情報が RSReportServer.config ファイルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="e6238-167">The account information is removed from the RSReportServer.config file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6238-168">参照</span><span class="sxs-lookup"><span data-stu-id="e6238-168">See Also</span></span>  
 [<span data-ttu-id="e6238-169">Reporting Services Configuration Manager &#40;del&#41;</span><span class="sxs-lookup"><span data-stu-id="e6238-169">Reporting Services Configuration Manager &#40;del&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
