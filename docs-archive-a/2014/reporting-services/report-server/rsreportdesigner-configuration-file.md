---
title: RSReportDesigner 構成ファイル | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], configuration file
- RSReportDesigner configuration file
ms.assetid: fdcc9c58-3bad-45b3-ba8e-c7816d64f14c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 563c5ea602eef3af2400057f3da41a5850a31cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641448"
---
# <a name="rsreportdesigner-configuration-file"></a><span data-ttu-id="440b9-102">RSReportDesigner 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="440b9-102">RSReportDesigner Configuration File</span></span>
  <span data-ttu-id="440b9-103">RSReportDesigner.config ファイルには、レポート デザイナーに利用できる表示拡張機能およびデータ処理拡張機能に関する設定が保存されています。</span><span class="sxs-lookup"><span data-stu-id="440b9-103">The RSReportDesigner.config file stores settings about the rendering and data processing extensions available to Report Designer.</span></span> <span data-ttu-id="440b9-104">データ処理拡張機能の情報は、`Data` 要素に保存されます。</span><span class="sxs-lookup"><span data-stu-id="440b9-104">Data processing extension information is stored in the `Data` element.</span></span> <span data-ttu-id="440b9-105">表示拡張機能の情報は、`Render` 要素に保存されます。</span><span class="sxs-lookup"><span data-stu-id="440b9-105">Rendering extension information is stored in the `Render` element.</span></span> <span data-ttu-id="440b9-106">`Designer` 要素には、レポート デザイナーで使用されるクエリ ビルダーが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="440b9-106">The `Designer` element enumerates the query builders that are used in Report Designer.</span></span>  
  
 <span data-ttu-id="440b9-107">レポート デザイナーでは、レポートをプレビューするために埋め込みのレポート サーバー機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="440b9-107">Report Designer uses embedded report server functionality to preview reports.</span></span> <span data-ttu-id="440b9-108">サーバー関連の設定を指定すると、サーバー側のプレビュー処理をローカルでサポートできます。</span><span class="sxs-lookup"><span data-stu-id="440b9-108">Server-related settings can be specified to support local server-side processing for preview operations.</span></span> <span data-ttu-id="440b9-109">レポートサーバーの構成設定の詳細については、「 [Rsreportserver Configuration File](rsreportserver-config-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440b9-109">For more information about report server configuration settings, see [RSReportServer Configuration File](rsreportserver-config-configuration-file.md).</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="440b9-110">ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="440b9-110">File Location</span></span>  
 <span data-ttu-id="440b9-111">このファイルは、\Program Files\Microsoft Visual Studio 8\Common7\IDE\PrivateAssemblies にあります。</span><span class="sxs-lookup"><span data-stu-id="440b9-111">This file is located in the \Program Files\Microsoft Visual Studio 8\Common7\IDE\PrivateAssemblies.</span></span>  
  
## <a name="editing-guidelines"></a><span data-ttu-id="440b9-112">編集のガイドライン</span><span class="sxs-lookup"><span data-stu-id="440b9-112">Editing Guidelines</span></span>  
 <span data-ttu-id="440b9-113">カスタム拡張機能を配置または削除する場合、プレビュー時のキャッシュを無効にする場合、およびサービス パック アップグレードの後に新しいデータ処理拡張機能を登録する場合を除いて、このファイルの設定を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="440b9-113">Do not modify the settings in this file unless you are deploying or removing a custom extension, disabling caching during preview, or registering a new data processing extension after a Service Pack upgrade.</span></span>  
  
 <span data-ttu-id="440b9-114">表示拡張機能の設定をカスタマイズしている場合は、構成ファイルの編集方法を説明したトピックが用意されています。</span><span class="sxs-lookup"><span data-stu-id="440b9-114">Specific instructions for editing configuration files are available if you are customizing rendering extension settings.</span></span> <span data-ttu-id="440b9-115">詳細については、「 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../customize-rendering-extension-parameters-in-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440b9-115">For more information, see [Customize Rendering Extension Parameters in RSReportServer.Config](../customize-rendering-extension-parameters-in-rsreportserver-config.md).</span></span>  
  
 <span data-ttu-id="440b9-116">一般的な構成ファイルを編集する方法については、「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440b9-116">For general instructions on how to edit configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span>  
  
## <a name="example-configuration-file"></a><span data-ttu-id="440b9-117">構成ファイルの例</span><span class="sxs-lookup"><span data-stu-id="440b9-117">Example Configuration File</span></span>  
 <span data-ttu-id="440b9-118">以下の例は、RSReportDesigner.config ファイルの形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="440b9-118">The following example illustrates the format of the RSReportDesigner.config file.</span></span>  
  
```  
<Configuration>  
  <Add Key="SecureConnectionLevel" Value="0" />  
  <Add Key="InstanceName" Value="Microsoft.ReportingServices.PreviewServer" />  
  <Add Key="SessionCookies" Value="true" />  
  <Add Key="SessionTimeoutMinutes" Value="3" />  
  <Add Key="PolicyLevel" Value="rspreviewpolicy.config" />  
  <Add Key="CacheDataForPreview" Value="true" />  
  <Extensions>  
    <Render> . . . </Render>  
    <Data> . . . </Data>  
    <Designer> . . . </Designer>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="440b9-119">構成設定</span><span class="sxs-lookup"><span data-stu-id="440b9-119">Configuration Settings</span></span>  
  
|<span data-ttu-id="440b9-120">設定</span><span class="sxs-lookup"><span data-stu-id="440b9-120">Setting</span></span>|<span data-ttu-id="440b9-121">説明</span><span class="sxs-lookup"><span data-stu-id="440b9-121">Description</span></span>|  
|-------------|-----------------|  
|`SecureConnectionLevel`|<span data-ttu-id="440b9-122">Web サービス接続のセキュリティ レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-122">Specifies the degree of security of the Web service connection.</span></span> <span data-ttu-id="440b9-123">有効な値は、0 ～ 3 で、0 はセキュリティ レベルが最も低くなります。</span><span class="sxs-lookup"><span data-stu-id="440b9-123">Valid values range from 0 through 3, where 0 is least secure.</span></span> <span data-ttu-id="440b9-124">詳細については、「 [セキュリティで保護された Web サービス メソッドの使用](../report-server-web-service/net-framework/using-secure-web-service-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440b9-124">For more information, see [Using Secure Web Service Methods](../report-server-web-service/net-framework/using-secure-web-service-methods.md).</span></span>|  
|`InstanceName`|<span data-ttu-id="440b9-125">プレビュー サーバーの識別子です。</span><span class="sxs-lookup"><span data-stu-id="440b9-125">An identifier for the preview server.</span></span> <span data-ttu-id="440b9-126">この値は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="440b9-126">Do not modify this value.</span></span>|  
|`SessionCookies`|<span data-ttu-id="440b9-127">レポート サーバーがブラウザーのクッキーを使用してセッション情報を保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-127">Specifies whether the report server uses browser cookies to maintain session information.</span></span> <span data-ttu-id="440b9-128">有効な値として、`true` および `false` があります。</span><span class="sxs-lookup"><span data-stu-id="440b9-128">Valid values include `true` and `false`.</span></span> <span data-ttu-id="440b9-129">既定では、 `true`です。</span><span class="sxs-lookup"><span data-stu-id="440b9-129">The default is `true`.</span></span> <span data-ttu-id="440b9-130">この値を false に設定すると、セッション データが **reportservertempdb** データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="440b9-130">If you set this value to false, session data is stored in the **reportservertempdb** database.</span></span>|  
|`SessionTimeoutMinutes`|<span data-ttu-id="440b9-131">セッションのクッキーの有効期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-131">Specifies the period for which a session cookie is valid.</span></span> <span data-ttu-id="440b9-132">既定値は 3 分です。</span><span class="sxs-lookup"><span data-stu-id="440b9-132">The default is 3 minutes.</span></span>|  
|`PolicyLevel`|<span data-ttu-id="440b9-133">セキュリティ ポリシーの構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-133">Specifies the security policy configuration file.</span></span> <span data-ttu-id="440b9-134">有効な値は Rspreviewpolicy.config です。詳細については、「 [Reporting Services セキュリティポリシーファイルの使用](../extensions/secure-development/using-reporting-services-security-policy-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440b9-134">The valid value is Rspreviewpolicy.config. For more information, see [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).</span></span>|  
|`CacheDataForPreview`|<span data-ttu-id="440b9-135">`True` に設定すると、レポート デザイナーがローカル コンピューター上のキャッシュ ファイルにデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="440b9-135">When set to `True`, the Report Designer stores data in a cache file on the local computer.</span></span> <span data-ttu-id="440b9-136">有効な値は、`True` (既定値) および `False` です。</span><span class="sxs-lookup"><span data-stu-id="440b9-136">Valid values are `True` (default) and `False`.</span></span> <span data-ttu-id="440b9-137">詳細については、「 [レポートのプレビュー](../reports/previewing-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440b9-137">For more information, see [Previewing Reports](../reports/previewing-reports.md).</span></span>|  
|`Render`|<span data-ttu-id="440b9-138">プレビューのためにレポート デザイナーで利用できる表示拡張機能を列挙します。</span><span class="sxs-lookup"><span data-stu-id="440b9-138">Enumerates the rendering extensions that are available to Report Designer for preview purposes.</span></span> <span data-ttu-id="440b9-139">プレビューに使用する表示拡張機能のセットは、レポート サーバーと一緒にインストールされた表示拡張機能と同一である必要があります。</span><span class="sxs-lookup"><span data-stu-id="440b9-139">The set of rendering extensions that are used for preview should be identical to those installed with the report server.</span></span><br /><br /> <span data-ttu-id="440b9-140">`Name` は、表示拡張機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-140">`Name` specifies the rendering extension.</span></span> <span data-ttu-id="440b9-141">コードで表示拡張機能を起動している場合は、この値を使用して、特定の拡張機能を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="440b9-141">If you are invoking a rendering extension through code, use this value to call a specific extension.</span></span><br /><br /> <span data-ttu-id="440b9-142">`Type` は、拡張クラスの完全修飾クラス名、およびライブラリ名をコンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-142">`Type` specifies the fully qualified class name of the extension class, plus the library name, comma separated.</span></span><br /><br /> <span data-ttu-id="440b9-143">`Visible` は、任意のユーザー インターフェイスに名前を表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-143">`Visible` specifies whether the name appears in any user interface.</span></span> <span data-ttu-id="440b9-144">この値には、`True` (既定値) または `False` があります。</span><span class="sxs-lookup"><span data-stu-id="440b9-144">This value can be `True` (default) or `False`.</span></span> <span data-ttu-id="440b9-145">`True` を指定すると、名前がユーザー インターフェイスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="440b9-145">If `True`, it appears in user interfaces.</span></span>|  
|`Data`|<span data-ttu-id="440b9-146">レポートにデータを提供するデータ ソースに接続するためにレポート デザイナーで利用できるデータ処理拡張機能を列挙します。</span><span class="sxs-lookup"><span data-stu-id="440b9-146">Enumerates the data processing extensions that are available to Report Designer for the purpose of connecting to data sources that provide data to reports.</span></span> <span data-ttu-id="440b9-147">レポート デザイナーで使用するデータ処理拡張機能のセットは、レポート サーバーと一緒にインストールされたデータ処理拡張機能と同一のものである場合があります。</span><span class="sxs-lookup"><span data-stu-id="440b9-147">The set of data processing extensions used in Report Designer may be identical to those installed with the report server.</span></span> <span data-ttu-id="440b9-148">カスタム拡張機能を追加または削除する場合は、「 [データ処理拡張機能の配置](../extensions/data-processing/deploying-a-data-processing-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440b9-148">If you are adding or removing custom extensions, see [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md).</span></span><br /><br /> <span data-ttu-id="440b9-149">`Name` は、データ処理拡張機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-149">`Name` specifies the data processing extension.</span></span><br /><br /> <span data-ttu-id="440b9-150">`Type` は、拡張クラスの完全修飾クラス名、およびライブラリ名をコンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-150">`Type` specifies the fully qualified class name of the extension class, plus the library name, comma separated.</span></span>|  
|`Designer`|<span data-ttu-id="440b9-151">レポート デザイナーで使用できるクエリ ビルダーが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="440b9-151">Enumerates the query builders that are available to Report Designer.</span></span> <span data-ttu-id="440b9-152">クエリ ビルダーは、レポートで使用されるデータを取得するクエリを構築するためのユーザー インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="440b9-152">Query builders provide a user interface for constructing queries that retrieve data used in reports.</span></span> <span data-ttu-id="440b9-153">クエリ ビルダーは、データ処理拡張機能によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="440b9-153">Query builders may vary for different data processing extensions.</span></span> <span data-ttu-id="440b9-154">既定では、Reporting Services は、製品に含まれるすべてのデータ処理拡張機能に 1 つのビジュアル データ ツール ユーザー インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="440b9-154">By default, Reporting Services provides one visual data tool user interface for all data processing extensions that are included in the product.</span></span> <span data-ttu-id="440b9-155">ただし、サード パーティのデータ処理拡張機能を構築または使用している場合は、他のクエリ ビルダー インターフェイスが適用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="440b9-155">However, if you are building or using third-party data processing extensions, other query builder interfaces may apply.</span></span>|  
|`PreviewProcessingServiceStartupTimeoutSeconds`|<span data-ttu-id="440b9-156">エラー メッセージを表示する前にプレビュー処理サービスの起動を待機する時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="440b9-156">Specifies the period to wait for the preview processing service to start up before showing an error message.</span></span> <span data-ttu-id="440b9-157">既定値は 15 秒です。</span><span class="sxs-lookup"><span data-stu-id="440b9-157">The default is 15 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="440b9-158">参照</span><span class="sxs-lookup"><span data-stu-id="440b9-158">See Also</span></span>  
 <span data-ttu-id="440b9-159">[Reporting Services 構成ファイル](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="440b9-159">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="440b9-160">レポートデザイナー SQL Server Data Tools のクエリデザインツール &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="440b9-160">Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;</span></span>](../report-data/query-design-tools-ssrs.md)  
  
  