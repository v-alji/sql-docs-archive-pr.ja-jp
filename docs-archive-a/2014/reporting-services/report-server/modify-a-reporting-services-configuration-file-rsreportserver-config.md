---
title: Reporting Services の構成ファイル (RSreportserver.config) の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 958ef51f-2699-4cb2-a92e-3b4322e36a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75ff276a0ba43cb89393466bf40a71b7acd21368
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640605"
---
# <a name="modify-a-reporting-services-configuration-file-rsreportserverconfig"></a><span data-ttu-id="ead55-102">Modify a Reporting Services Configuration File (RSreportserver.config)</span><span class="sxs-lookup"><span data-stu-id="ead55-102">Modify a Reporting Services Configuration File (RSreportserver.config)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ead55-103">では、一連の構成ファイルにアプリケーション設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="ead55-103">stores application settings in a set of configuration files.</span></span> <span data-ttu-id="ead55-104">構成ファイルはセットアップ時に作成され、インストールしたレポート サーバー インスタンスごとに存在します。</span><span class="sxs-lookup"><span data-stu-id="ead55-104">Setup creates the configuration files for each report server instance you install.</span></span> <span data-ttu-id="ead55-105">各ファイル内の値は、インストール中に設定されるか、ツールやアプリケーションを使用してサーバーの動作を構成したときに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-105">Within each file, values are either set during installation or when you use tools and applications to configure a server for operation.</span></span> <span data-ttu-id="ead55-106">場合によっては、高度な設定を追加したり構成したりするために、ファイルを直接変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ead55-106">In some cases, you must modify a file directly to add or configure advanced settings.</span></span> <span data-ttu-id="ead55-107">構成設定は、XML 要素または XML 属性のいずれかとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-107">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="ead55-108">XML ファイルおよび構成ファイルを理解している場合は、テキスト エディターまたはコード エディターを使用して、ユーザーが定義可能な設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ead55-108">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span>  
  
 <span data-ttu-id="ead55-109">一部の構成設定は、ツールを使ってのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="ead55-109">Some configuration settings can be set only through a tool.</span></span> <span data-ttu-id="ead55-110">暗号化された値を含んだ設定は、Reporting Services 構成ツール、セットアップ プログラム、または **rsconfig** コマンド ライン ユーティリティで変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ead55-110">Settings that contain encrypted values must be modified through the Reporting Services Configuration tool, the Setup program, or the **rsconfig** command line utility.</span></span> <span data-ttu-id="ead55-111">これらのツールを実行するには、ローカルの Administrators グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ead55-111">You must be a member of the local Administrators group to run these tools.'</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ead55-112">構成ファイルを変更する場合は注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="ead55-112">Use caution when modifying configuration files.</span></span> <span data-ttu-id="ead55-113">内部で使用するために予約されている設定を変更すると、インストールが無効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="ead55-113">If you modify a setting that is reserved for internal use, you may disable your installation.</span></span> <span data-ttu-id="ead55-114">一般的に、特定の問題を解決しようとしている場合を除いて、構成設定を変更することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="ead55-114">Generally, modifying configuration settings is not recommended unless you are trying to solve a specific problem.</span></span> <span data-ttu-id="ead55-115">変更できる設定の詳細については、「 [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) 」または「 [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ead55-115">For more information about which settings are safe to change, see [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) or [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md).</span></span> <span data-ttu-id="ead55-116">構成ファイルの詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の製品ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ead55-116">For more information about configuration files, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span>  
  
 <span data-ttu-id="ead55-117">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="ead55-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="ead55-118">構成値の読み取りと使用</span><span class="sxs-lookup"><span data-stu-id="ead55-118">Reading and Using Configuration Values</span></span>](#bkmk_read_values)  
  
-   [<span data-ttu-id="ead55-119">既定値について</span><span class="sxs-lookup"><span data-stu-id="ead55-119">About Default Values</span></span>](#bkmk_default_values)  
  
-   [<span data-ttu-id="ead55-120">構成設定の削除</span><span class="sxs-lookup"><span data-stu-id="ead55-120">Deleting Configuration Settings</span></span>](#bkmk_delete_config_settings)  
  
-   [<span data-ttu-id="ead55-121">Reporting Services の構成ファイルを編集するには</span><span class="sxs-lookup"><span data-stu-id="ead55-121">To Edit a Reporting Services Configuration File</span></span>](#bkmk_edit_configuation_file)  
  
##  <a name="reading-and-using-configuration-values"></a><a name="bkmk_read_values"></a> <span data-ttu-id="ead55-122">構成値の読み取りと使用</span><span class="sxs-lookup"><span data-stu-id="ead55-122">Reading and Using Configuration Values</span></span>  
 <span data-ttu-id="ead55-123">レポート サーバーが構成ファイルを読み取るタイミングは、サービスが開始されたときと、構成ファイルが保存されたときです。</span><span class="sxs-lookup"><span data-stu-id="ead55-123">A report server reads the configuration files when the service starts and whenever the configuration file is saved.</span></span> <span data-ttu-id="ead55-124">新しい値や変更された値は、現在のアプリケーション ドメインの有効期間が切れた後、新しいアプリケーション ドメインで有効になります。</span><span class="sxs-lookup"><span data-stu-id="ead55-124">New and revised values take effect in a new application domain after the current application domain expires.</span></span> <span data-ttu-id="ead55-125">現在のアプリケーション ドメインで処理中の要求は、できる限り最後まで完了するように配慮されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-125">Whenever possible, requests that are still processing in the current application domain are allowed to complete.</span></span> <span data-ttu-id="ead55-126">ただし、いくつかの設定については、アプリケーション ドメインのリサイクルが直ちに必要となります。</span><span class="sxs-lookup"><span data-stu-id="ead55-126">However, a few settings require an immediate application domain recycle operation.</span></span> <span data-ttu-id="ead55-127">この場合、処理中の要求はすべて、新しいアプリケーション ドメインで再開されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-127">In this case, all requests that are in process are restarted in a new application domain.</span></span>  
  
 <span data-ttu-id="ead55-128">無効な値が検出された場合、レポート サーバーによって Windows アプリケーション ログにエラーが記録され、エラーの内容に応じてレポート サーバーの起動が失敗するか、または既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-128">If the report server detects an invalid value, the report server logs an error to the Windows application log and either fails to start or uses a default value, depending on the error:</span></span>  
  
-   <span data-ttu-id="ead55-129">エラーの内容が不適切な形式の XML である場合は、レポート サーバーが起動されません。</span><span class="sxs-lookup"><span data-stu-id="ead55-129">If the error is malformed XML, the report server will not start.</span></span> <span data-ttu-id="ead55-130">レポート サーバーの実行中にエラーが発生した場合、レポート サーバーが再起動されるまで、またはアプリケーション ドメインのリサイクルが発生するまで、レポート サーバーは無効な構成ファイルを無視します。</span><span class="sxs-lookup"><span data-stu-id="ead55-130">If the report server is running when you introduce the error, the report server ignores the invalid configuration file until the report server restarts or the application domain is recycled.</span></span> <span data-ttu-id="ead55-131">エラーが検出されると、レポート サーバーは起動されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ead55-131">Once the error is detected, the report server will no longer start.</span></span>  
  
-   <span data-ttu-id="ead55-132">エラーの内容が無効な構成値である場合、内部の既定値が使用され、エラーがトレース ログ ファイルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-132">If the error is an invalid configuration value, the server will use internal default values and log an error to the trace log files.</span></span> <span data-ttu-id="ead55-133">サーバーの動作にきわめて重要な意味を持つ構成設定が無効であった場合で、かつ、内部の既定値が使用できないごく限られた状況では、サーバーから rsServerConfigurationError エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-133">In the few cases where internal default values are not available, the server will return the rsServerConfigurationError error if the invalid configuration setting is critical to server operations.</span></span> <span data-ttu-id="ead55-134">設定が欠落している場合や、きわめて重要な設定が無効であった場合、クライアント アプリケーションには、それに関するエラーが HTML 形式のエラー ページとして返され、イベント ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-134">Errors about missing or invalid critical settings are returned to the client application in an HTML error page and logged to the event log.</span></span>  
  
 <span data-ttu-id="ead55-135">正常な変更も含め、構成ファイルに対するすべての変更は、レポート サーバーのトレース ログ ファイルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-135">All configuration file changes, including successful changes, are recorded in the report server trace log file.</span></span> <span data-ttu-id="ead55-136">アプリケーション イベント ログには、エラーだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-136">Only errors are logged to the application event log.</span></span>  
  
##  <a name="about-default-values"></a><a name="bkmk_default_values"></a> <span data-ttu-id="ead55-137">既定値について</span><span class="sxs-lookup"><span data-stu-id="ead55-137">About Default Values</span></span>  
 <span data-ttu-id="ead55-138">ほとんどの構成設定には、レポート サーバー内部で指定される既定値があります。</span><span class="sxs-lookup"><span data-stu-id="ead55-138">Most configuration settings have default values that are specified internally in the report server.</span></span> <span data-ttu-id="ead55-139">ユーザー定義の値が無効であったり、指定されていなかった場合は、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-139">The report server will use these values if a user-defined value is invalid or not specified.</span></span> <span data-ttu-id="ead55-140">構成設定が無効であるため既定値を使用した場合は、トレース ログ ファイルにエラーが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ead55-140">If a default value must be used due to an invalid configuration setting, an error is written to the trace log file.</span></span>  
  
##  <a name="deleting-configuration-settings"></a><a name="bkmk_delete_config_settings"></a> <span data-ttu-id="ead55-141">構成設定の削除</span><span class="sxs-lookup"><span data-stu-id="ead55-141">Deleting Configuration Settings</span></span>  
 <span data-ttu-id="ead55-142">既定値がある構成設定の場合は、構成ファイルから設定を削除しても影響はありません。</span><span class="sxs-lookup"><span data-stu-id="ead55-142">For configuration settings that have default values, removing the setting from the configuration file has no effect.</span></span> <span data-ttu-id="ead55-143">ほとんどの構成設定は、実際には内部的に定義および構成されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-143">Most configuration settings are actually defined and configured internally.</span></span> <span data-ttu-id="ead55-144">構成ファイルから項目を削除しても、内部コピーは引き続き使用でき、その項目に対して定義されている既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-144">If you delete an item from the configuration file, the internal copy is still available and uses the default value that is defined for it.</span></span>  
  
##  <a name="to-edit-a-reporting-services-configuration-file"></a><a name="bkmk_edit_configuation_file"></a> <span data-ttu-id="ead55-145">Reporting Services の構成ファイルを編集するには</span><span class="sxs-lookup"><span data-stu-id="ead55-145">To Edit a Reporting Services Configuration File</span></span>  
  
1.  <span data-ttu-id="ead55-146">編集する構成ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="ead55-146">Find the configuration file you want to edit:</span></span>  
  
    -   <span data-ttu-id="ead55-147">**RSReportServer.config** は次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="ead55-147">**RSReportServer.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
        ```  
  
    -   <span data-ttu-id="ead55-148">**RSReportServerServices.exe.config** は次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="ead55-148">**RSReportServerServices.exe.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer\bin  
        ```  
  
    -   <span data-ttu-id="ead55-149">**RSReportDesigner.config** は次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="ead55-149">**RSReportDesigner.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies  
        ```  
  
2.  <span data-ttu-id="ead55-150">変更をロールバックする必要がある場合は、ファイルのコピーを保存します。</span><span class="sxs-lookup"><span data-stu-id="ead55-150">Save a copy of the file in case you need to roll back your changes.</span></span>  
  
3.  <span data-ttu-id="ead55-151">元のファイルをメモ帳またはコード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="ead55-151">Open the original file in Notepad or a code editor.</span></span> <span data-ttu-id="ead55-152">Textpad は使用しないでください。ファイルの保存前にファイルの長さが設定されるため、無効な文字を示すエラーがトレース ログ ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ead55-152">Do not use Textpad; it sets the file length before the file is saved, causing an invalid character error to be written to the trace log file.</span></span>  
  
4.  <span data-ttu-id="ead55-153">追加または使用する要素 (または値) を入力します。</span><span class="sxs-lookup"><span data-stu-id="ead55-153">Type the element or value that you want to add or use.</span></span> <span data-ttu-id="ead55-154">要素では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="ead55-154">Elements are case-sensitive.</span></span> <span data-ttu-id="ead55-155">要素を追加する場合は、大文字と小文字を正しく区別して入力してください。</span><span class="sxs-lookup"><span data-stu-id="ead55-155">If you are adding an element, be sure to use the correct upper and lower case letters.</span></span> <span data-ttu-id="ead55-156">表示拡張機能、認証拡張機能、またはデータ処理拡張機能をカスタマイズしている場合は、対応する構成ファイルの編集方法を説明したトピックが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ead55-156">Specific instructions for editing configuration files are available if you are customizing rendering extension, authentication extensions, or data processing extensions:</span></span>  
  
    -   [<span data-ttu-id="ead55-157">レポート サーバーでの認証</span><span class="sxs-lookup"><span data-stu-id="ead55-157">Authentication with the Report Server</span></span>](../security/authentication-with-the-report-server.md)  
  
    -   [<span data-ttu-id="ead55-158">カスタム認証クッキーを送信するようにレポート マネージャーを構成する</span><span class="sxs-lookup"><span data-stu-id="ead55-158">Configure Report Manager to Pass Custom Authentication Cookies</span></span>](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)  
  
    -   [<span data-ttu-id="ead55-159">RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ead55-159">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](../customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
5.  <span data-ttu-id="ead55-160">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ead55-160">Save the file.</span></span>  
  
6.  <span data-ttu-id="ead55-161">トレース ログ ファイルを見て、エラーが発生していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ead55-161">Check the trace log files to verify that errors did not occur.</span></span> <span data-ttu-id="ead55-162">エラー状態が記録されていた場合は、設定またはその値が正しく指定されていません。</span><span class="sxs-lookup"><span data-stu-id="ead55-162">If you see error conditions, a setting or its value is specified incorrectly.</span></span> <span data-ttu-id="ead55-163">「 [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) 」を参照し、エラーの原因となっている設定について有効な値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ead55-163">Review the [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) for valid values for any setting that is causing an error.</span></span> <span data-ttu-id="ead55-164">トレース ログの表示方法の詳細については、「 [レポート サーバー サービスのトレース ログ](report-server-service-trace-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ead55-164">For more information about how to view the trace log, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead55-165">参照</span><span class="sxs-lookup"><span data-stu-id="ead55-165">See Also</span></span>  
 <span data-ttu-id="ead55-166">[RSReportServer 構成ファイル](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="ead55-166">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="ead55-167">[Reportingservices サービス構成ファイル](reportingservicesservice-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="ead55-167">[ReportingServicesService Configuration File](reportingservicesservice-configuration-file.md) </span></span>  
 <span data-ttu-id="ead55-168">[RSReportDesigner 構成ファイル](rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="ead55-168">[RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="ead55-169">[データ処理拡張機能の配置](../extensions/data-processing/deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="ead55-169">[Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="ead55-170">[配信拡張機能の配置](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="ead55-170">[Deploying a Delivery Extension](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="ead55-171">[表示拡張機能の配置](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="ead55-171">[Deploying a Rendering Extension](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="ead55-172">[カスタムレポートアイテムを配置する方法](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="ead55-172">[How to: Deploy a Custom Report Item](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="ead55-173">Reporting Services 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="ead55-173">Reporting Services Configuration Files</span></span>](reporting-services-configuration-files.md)  
  
  
