---
title: Reporting Services データ ソースに資格情報を保存する | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fccf8669d1f39d19a26b443ffcead8e86db66a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643188"
---
# <a name="store-credentials-in-a-reporting-services-data-source"></a><span data-ttu-id="a64cc-102">Store Credentials in a Reporting Services Data Source</span><span class="sxs-lookup"><span data-stu-id="a64cc-102">Store Credentials in a Reporting Services Data Source</span></span>
  <span data-ttu-id="a64cc-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポート サーバーが、レポートに必要な外部データにアクセスするときに使用する、保存された資格情報を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-103">You can configure stored credentials that a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server uses to access external data for a report.</span></span> <span data-ttu-id="a64cc-104">保存された資格情報は、レポートを自動実行する場合に使用されます。たとえば、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サブスクリプションがレポートを電子メールとしてパブリッシュする場合などです。</span><span class="sxs-lookup"><span data-stu-id="a64cc-104">Stored credentials are used if the report runs unattended, for example a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription that publishes a report as an e-mail.</span></span> <span data-ttu-id="a64cc-105">この資格情報は、レポート処理がスケジュールで設定されている場合、または、レポート処理がトリガーされた場合に、レポート サーバーによって取得されて使用されます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-105">The report server retrieves and uses the credentials when report processing is scheduled or triggered.</span></span> <span data-ttu-id="a64cc-106">このトピックでは、ネイティブ モードと SharePoint モードの両方のレポート サーバーに対して、保存された資格情報を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-106">This topic walks you through configuring stored credentials for both Native mode and SharePoint mode report servers.</span></span>

||
|-|
|<span data-ttu-id="a64cc-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="a64cc-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="a64cc-108">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="a64cc-108">**In this topic:**</span></span>

-   [<span data-ttu-id="a64cc-109">レポート固有のデータソース用の保存された資格情報を構成する (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-109">Configure stored credentials for a report-specific data source (Native mode)</span></span>](#bkmk_stored_credentials_data_source_native)

-   [<span data-ttu-id="a64cc-110">レポート固有のデータソース用の保存された資格情報の構成 (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-110">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_data_source_sharepoint)

-   [<span data-ttu-id="a64cc-111">共有データソース用の保存された資格情報を構成する (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-111">Configure stored credentials for a shared data source (Native mode)</span></span>](#bkmk_stored_credentials_shared_data_source_native)

-   [<span data-ttu-id="a64cc-112">共有データ ソース用の保存された資格情報を構成する (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-112">Configure stored credentials for a shared data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_shared_data_source_sharepoint)

##  <a name="security-policy-requirements-for-stored-credentials"></a><a name="bkmk_top"></a> <span data-ttu-id="a64cc-113">保存された資格情報のセキュリティ ポリシー要件</span><span class="sxs-lookup"><span data-stu-id="a64cc-113">Security policy requirements for stored credentials</span></span>
 <span data-ttu-id="a64cc-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") 保存された資格情報に使用するアカウントを、レポート サーバー上で、次のいずれかのセキュリティ ポリシー用に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a64cc-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") It is required that the account you use for stored credentials, is configured for one of the following security policies on the report server.</span></span> <span data-ttu-id="a64cc-115">環境に必要な最小レベルの権限を持つポリシーを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-115">It is recommended you select the policy with the minimum level of permissions you require for your environment.</span></span>

1.  <span data-ttu-id="a64cc-116">**ローカルログオンを許可**します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-116">**Allow log on locally**.</span></span> <span data-ttu-id="a64cc-117">詳細については、「 [ローカル ログオンを許可する](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a64cc-117">For more information, see [Allow log on locally](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).</span></span>

2.  <span data-ttu-id="a64cc-118">**バッチ ジョブとしてログオン**。</span><span class="sxs-lookup"><span data-stu-id="a64cc-118">**Log on as a batch job**.</span></span> <span data-ttu-id="a64cc-119">詳細については、「 [バッチ ジョブとしてログオン](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a64cc-119">For more information, see [Log on as a batch job](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).</span></span>

3.  <span data-ttu-id="a64cc-120">ポリシーに関する一般的な情報については、「 [グループ ポリシー オブジェクトのセキュリティの設定を編集する](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a64cc-120">For general information on policies, see [Edit security settings on a Group Policy object](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-native-mode"></a><a name="bkmk_stored_credentials_data_source_native"></a> <span data-ttu-id="a64cc-121">レポート固有のデータ ソース用の保存された資格情報を構成する (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-121">Configure stored credentials for a report-specific data source (Native mode)</span></span>

1.  <span data-ttu-id="a64cc-122">ネイティブ モードのレポート マネージャーで、レポートが含まれているフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-122">In Native mode Report Manager, browse to the folder that contains the report.</span></span> <span data-ttu-id="a64cc-123">![Ssrs 項目については、レポートマネージャーで項目の](../media/ssrs-report-manager-item-context-menu.png "レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー")コンテキストメニューのコンテキストメニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-123">Click the item context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items").</span></span>

2.  <span data-ttu-id="a64cc-124">**[管理]** をクリックして、 **[データ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-124">Click **Manage** and then click **Data Sources**.</span></span>

3.  <span data-ttu-id="a64cc-125">**[カスタム データ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-125">Select **A custom data source**.</span></span>

4.  <span data-ttu-id="a64cc-126">**[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-126">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="a64cc-127">[**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-127">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="a64cc-128">次の例は、データベースへの接続に使用される接続文字列を示してい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-128">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="a64cc-129">**[接続に使用する認証]** で、 **[レポート サーバーに保存され、セキュリティで保護された資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-129">For **Connect Using**, select **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="a64cc-130">ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-130">Type a user name and password.</span></span>

    -   <span data-ttu-id="a64cc-131">アカウントが Windows ドメインユーザーアカウントの場合は、<アカウントの形式で指定し、 \<domain> \\ \> [**データソースへの接続時に windows 資格情報として使用**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-131">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="a64cc-132">ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]** を選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="a64cc-132">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="a64cc-133">データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[データ ソースへの接続が確立した後に、認証されているユーザーの権限を借用する]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-133">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

8.  <span data-ttu-id="a64cc-134">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-134">Click **Apply**.</span></span>

     <span data-ttu-id="a64cc-135">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシーの要件](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="a64cc-135">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_data_source_sharepoint"></a> <span data-ttu-id="a64cc-136">レポート固有のデータ ソース用の保存された資格情報を構成する (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-136">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="a64cc-137">レポートを含むドキュメント ライブラリを参照し、開くメニューをクリックします![ssrs 項目のドキュメント ライブラリのコンテキスト メニュー](../media/ssrs-sharepoint-item-context-menu.png "ssrs 項目のドキュメント ライブラリのコンテキスト メニュー")。</span><span class="sxs-lookup"><span data-stu-id="a64cc-137">Browse to the document library that contains the report and then click the open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

2.  <span data-ttu-id="a64cc-138">2 番目の開くメニューをクリックし![ssrs 項目のドキュメント ライブラリのコンテキスト メニュー](../media/ssrs-sharepoint-item-context-menu.png "ssrs 項目のドキュメント ライブラリのコンテキスト メニュー")、**[データ ソースの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-138">Click second open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click **Manage Data Sources**.</span></span>

3.  <span data-ttu-id="a64cc-139">資格情報を使用して構成する **[カスタム]** データ ソースの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-139">Click the name of the **Custom** data source you want to configure with stored credentials.</span></span>

4.  <span data-ttu-id="a64cc-140">**[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-140">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="a64cc-141">[**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-141">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="a64cc-142">次の例は、データベースへの接続に使用される接続文字列を示してい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-142">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="a64cc-143">**[資格情報]** で、 **[格納された資格情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-143">For **Credentials**, select **Stored Credentials**.</span></span>

7.  <span data-ttu-id="a64cc-144">**ユーザー名**と**パスワード**を入力します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-144">Type a **user name** and **password**.</span></span>

    -   <span data-ttu-id="a64cc-145">アカウントが Windows ドメインユーザーアカウントの場合は、<アカウントの形式で指定し、 \<domain> \\ \> [**データソースへの接続時に windows 資格情報として使用**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-145">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="a64cc-146">ユーザー名とパスワードがデータベースの資格情報である場合は、 **[Windows 資格情報として使用する]** を選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="a64cc-146">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="a64cc-147">データベースサーバーで権限借用または委任がサポートされている場合は、[**実行コンテキストをこのアカウントに設定**する] を選択できます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-147">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>

8.  <span data-ttu-id="a64cc-148">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-148">Click **ok**.</span></span>

     <span data-ttu-id="a64cc-149">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシーの要件](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="a64cc-149">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-native-mode"></a><a name="bkmk_stored_credentials_shared_data_source_native"></a> <span data-ttu-id="a64cc-150">共有データ ソース用の保存された資格情報を構成する (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-150">Configure stored credentials for a shared data source (Native mode)</span></span>

1.  <span data-ttu-id="a64cc-151">ネイティブ モードのレポート マネージャーで、共有データ ソース アイテムに移動します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-151">In Native mode Report Manager, browse to the shared data source item.</span></span> <span data-ttu-id="a64cc-152">![共有データ ソースのアイコン](../media/hlp-16datasource.png "共有データ ソースのアイコン")</span><span class="sxs-lookup"><span data-stu-id="a64cc-152">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="a64cc-153">![レポートマネージャーの ssrs 項目について](../media/ssrs-report-manager-item-context-menu.png "レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー")、コンテキストメニューのコンテキストメニューをクリックし、[**管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-153">Click the context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items") and then click **Manage**.</span></span>

3.  <span data-ttu-id="a64cc-154">[**データソースの種類**] ボックスの一覧で、データソースからのデータを処理するために使用するデータ処理拡張機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-154">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

4.  <span data-ttu-id="a64cc-155">[**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-155">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a64cc-156">では、接続文字列に資格情報を指定しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-156">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="a64cc-157">次の例は、ローカルデータベースへの接続に使用される接続文字列を示してい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-157">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

5.  <span data-ttu-id="a64cc-158">ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-158">Type a user name and password.</span></span>

    -   <span data-ttu-id="a64cc-159">アカウントが Windows ドメインユーザーアカウントの場合は、<アカウントの形式で指定し、 \<domain> \\ \> [**データソースへの接続時に windows 資格情報として使用**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-159">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="a64cc-160">ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]** を選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="a64cc-160">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="a64cc-161">データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[データ ソースへの接続が確立した後に、認証されているユーザーの権限を借用する]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-161">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

6.  <span data-ttu-id="a64cc-162">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-162">Click **Apply**.</span></span>

     <span data-ttu-id="a64cc-163">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシーの要件](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="a64cc-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a><span data-ttu-id="a64cc-164">共有データソース用の保存された資格情報の構成 (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="a64cc-164">Configure stored credentials for a shared data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="a64cc-165">ドキュメント ライブラリで、共有データ ソース項目を参照します。![共有データ ソースのアイコン](../media/hlp-16datasource.png "共有データ ソースのアイコン")</span><span class="sxs-lookup"><span data-stu-id="a64cc-165">In the document library, browse to the shared data source item.![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="a64cc-166">コンテキスト メニューをクリックし![ssrs 項目のドキュメント ライブラリのコンテキスト メニュー](../media/ssrs-sharepoint-item-context-menu.png "ssrs 項目のドキュメント ライブラリのコンテキスト メニュー")、2 番目のコンテキスト メニューをクリックします![ssrs 項目のドキュメント ライブラリのコンテキスト メニュー](../media/ssrs-sharepoint-item-context-menu.png "ssrs 項目のドキュメント ライブラリのコンテキスト メニュー")。</span><span class="sxs-lookup"><span data-stu-id="a64cc-166">Click the context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click the second context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

3.  <span data-ttu-id="a64cc-167">**[データ ソース定義の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-167">Click **Edit Data Source Definition**.</span></span>

4.  <span data-ttu-id="a64cc-168">[**データソースの種類**] ボックスの一覧で、データソースからのデータを処理するために使用するデータ処理拡張機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-168">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="a64cc-169">[**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-169">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a64cc-170">では、接続文字列に資格情報を指定しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-170">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="a64cc-171">次の例は、ローカルデータベースへの接続に使用される接続文字列を示してい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-171">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="a64cc-172">ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-172">Type a user name and password.</span></span>

    -   <span data-ttu-id="a64cc-173">アカウントが Windows ドメインユーザーアカウントの場合は、<アカウントの形式で指定し、 \<domain> \\ \> [ **Windows 資格情報として使用する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a64cc-173">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials.**</span></span>

    -   <span data-ttu-id="a64cc-174">ユーザー名とパスワードがデータベースの資格情報である場合は、 **[Windows 資格情報として使用する]** を選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="a64cc-174">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="a64cc-175">データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[実行コンテキストをこのアカウントに設定する]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="a64cc-175">If the database server supports impersonation or delegation, you can select **Set Execution context to this account**.</span></span>

7.  <span data-ttu-id="a64cc-176">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a64cc-176">Click **Ok**.</span></span>

     <span data-ttu-id="a64cc-177">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシーの要件](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="a64cc-177">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

## <a name="see-also"></a><span data-ttu-id="a64cc-178">参照</span><span class="sxs-lookup"><span data-stu-id="a64cc-178">See Also</span></span>
 <span data-ttu-id="a64cc-179">[レポートデータソースの資格情報と接続情報を指定する](../../integration-services/connection-manager/data-sources.md)[レポートのデータソースのプロパティを構成する &#40;レポートマネージャー&#41;](configure-data-source-properties-for-a-report-report-manager.md) [共有データソースを作成、削除、または変更する &#40;レポートマネージャー](../create-delete-or-modify-a-shared-data-source-report-manager.md)&#41;データソース][プロパティページ](../data-sources-properties-page-report-manager.md)&#40;レポートマネージャー [[新しいデータソース] ページ](../new-data-source-page-report-manager.md)&#41;&#40;レポートマネージャー</span><span class="sxs-lookup"><span data-stu-id="a64cc-179">[Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) [Configure Data Source Properties for a Report  &#40;Report Manager&#41;](configure-data-source-properties-for-a-report-report-manager.md) [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) [Data Sources Properties Page &#40;Report Manager&#41;](../data-sources-properties-page-report-manager.md) [New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md)</span></span>


