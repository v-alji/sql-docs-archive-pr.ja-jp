---
title: レポート データ ソース内の資格情報を SharePoint サイトから更新する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e0c50b6e-89e7-4b4d-8fe5-c90682c5d1b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 923fee5656ed6032201fb4276fcca75be799e42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631567"
---
# <a name="update-credentials-in-report-data-sources-from-a-sharepoint-site"></a><span data-ttu-id="4876f-102">レポート データ ソース内の資格情報を SharePoint サイトから更新する</span><span class="sxs-lookup"><span data-stu-id="4876f-102">Update Credentials in Report Data Sources from a SharePoint Site</span></span>
  <span data-ttu-id="4876f-103">このトピックでは、レポートに埋め込まれたデータ ソースや、SharePoint ドキュメント ライブラリ内に保存された共有データ ソースを更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4876f-103">This topic describes how to update data sources embedded in reports and shared data sources that are saved in a SharePoint document library.</span></span>  
  
 <span data-ttu-id="4876f-104">多くのレポートには、データ ソースが含まれていたり、Windows 認証を使用するように構成された共有データ ソースが使用されていることがあります。</span><span class="sxs-lookup"><span data-stu-id="4876f-104">Many of your reports might include data sources or use shared data sources that are configured to use Windows Authentication.</span></span> <span data-ttu-id="4876f-105">SharePoint ドキュメント ライブラリ内に保存されたレポートに関するデータ警告を作成する場合など、状況によっては、データ ソース資格情報を更新して、保存済み資格情報を使用するようにしたり、資格情報を要求しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4876f-105">Under some circumstances, such as creating data alerts on reports saved to a SharePoint document library, you need to update the data source credentials to stored credentials or require no credentials.</span></span>  
  
 <span data-ttu-id="4876f-106">保存された資格情報をレポートで使用するために、新しい SQL Server ログインを作成および使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="4876f-106">To use stored credentials in reports, you might decide to create and use a new SQL Server login.</span></span> <span data-ttu-id="4876f-107">詳細については、「 [ログインの作成](../../relational-databases/security/authentication-access/create-a-login.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4876f-107">For more information, see [Create a Login](../../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
### <a name="to-update-an-embedded-data-source-to-use-stored-credentials"></a><span data-ttu-id="4876f-108">保存された資格情報を使用するように埋め込みデータソースを更新するには</span><span class="sxs-lookup"><span data-stu-id="4876f-108">To update an embedded data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="4876f-109">レポートを保存した SharePoint ドキュメント ライブラリに移動します。</span><span class="sxs-lookup"><span data-stu-id="4876f-109">Go to the SharePoint document library where you saved the report.</span></span>  
  
2.  <span data-ttu-id="4876f-110">レポートの展開ドロップダウン メニューのアイコンをクリックし、 **[データ ソースの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4876f-110">Click the icon for the expand drop-down menu on the report and then click **Manage Data Sources**.</span></span>  
  
     <span data-ttu-id="4876f-111">[データ ソースの管理] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="4876f-111">The Manage Data Sources page opens.</span></span>  
  
3.  <span data-ttu-id="4876f-112">**[名前]** 列で、データ ソースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4876f-112">In the **Name** column, click the data source.</span></span>  
  
4.  <span data-ttu-id="4876f-113">**[接続の種類]** で、 **[カスタム データ ソース]** オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4876f-113">For **Connection Type** verify that the **Custom data source** option is selected.</span></span>  
  
     <span data-ttu-id="4876f-114">このオプションは、データ ソースがレポートに埋め込まれることを示します。</span><span class="sxs-lookup"><span data-stu-id="4876f-114">This option indicates that the data source is embedded in the report.</span></span>  
  
5.  <span data-ttu-id="4876f-115">レポートを別の種類のデータ ソース、別のサーバー、または別のデータ ストアに接続したい場合を除き、 **[データ ソースの種類]** オプションと **[接続文字列]** オプションはそのままにします。</span><span class="sxs-lookup"><span data-stu-id="4876f-115">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the report to connect to different type of data source, a different server, or data store.</span></span>  
  
6.  <span data-ttu-id="4876f-116">**[資格情報]** で、 **[格納された資格情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4876f-116">For **Credentials**, select **Stored credentials**.</span></span> <span data-ttu-id="4876f-117">このオプションは、データ ソースで資格情報が不要な場合、または他の方法で資格情報を渡している場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="4876f-117">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="4876f-118">状況によっては、 **[資格情報は必要ありません]** オプションを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4876f-118">The **Credentials are not required** option can also be used under some circumstances.</span></span>  
  
     <span data-ttu-id="4876f-119">一部の種類のデータ ソースについては、レポート サーバーで自動実行アカウントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4876f-119">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="4876f-120">詳細については、「[外部データ ソースのデータを追加する (SSRS)](add-data-from-external-data-sources-ssrs.md)」および「[自動実行アカウントの構成 (SSRS 構成マネージャー)](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」で、対応するデータ ソースの種類に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4876f-120">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
7.  <span data-ttu-id="4876f-121">ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="4876f-121">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="4876f-122">アカウントが Windows ドメインユーザーアカウントの場合は、<アカウントの形式で指定し、 \<domain> \\ \> [**データソースへの接続時に windows 資格情報として使用**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4876f-122">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source**.</span></span>  
  
    -   <span data-ttu-id="4876f-123">ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]** を選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="4876f-123">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="4876f-124">データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[実行コンテキストをこのアカウントに設定する]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="4876f-124">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
8.  <span data-ttu-id="4876f-125">データ ソースが更新後の資格情報を使用して接続できるかどうかを確認するには、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4876f-125">To verify the data source can connect by using the updated credentials, click **Test connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-update-a-shared-data-source-to-use-stored-credentials"></a><span data-ttu-id="4876f-126">保存された資格情報を使用するように共有データソースを更新するには</span><span class="sxs-lookup"><span data-stu-id="4876f-126">To update a shared data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="4876f-127">共有データ ソースを保存した SharePoint ドキュメント ライブラリに移動します。</span><span class="sxs-lookup"><span data-stu-id="4876f-127">Go to the SharePoint document library where you saved the shared data source.</span></span>  
  
2.  <span data-ttu-id="4876f-128">共有データ ソースの展開ドロップダウン メニューのアイコンをクリックし、 **[データ ソース定義の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4876f-128">Click the icon for the expand drop-down menu on shared data source, and then click **Edit Data Source Definition**.</span></span>  
  
     <span data-ttu-id="4876f-129">[データ ソース] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="4876f-129">The Data Source page opens.</span></span>  
  
3.  <span data-ttu-id="4876f-130">共有データ ソースを別の種類のデータ ソース、別のサーバー、または別のデータ ストアに接続したい場合を除き、 **[データ ソースの種類]** オプションと **[接続文字列]** オプションはそのままにします。</span><span class="sxs-lookup"><span data-stu-id="4876f-130">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the shared data source to connect to different type of data source, a different server, or data store.</span></span>  
  
4.  <span data-ttu-id="4876f-131">**[資格情報]** で、 **[格納された資格情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4876f-131">For **Credentials**, select **Stored credentials**.</span></span>  
  
     <span data-ttu-id="4876f-132">状況によっては、 **[資格情報は必要ありません]** オプションを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4876f-132">The **Credentials are not required** option can also be used under some circumstances.</span></span> <span data-ttu-id="4876f-133">このオプションは、データ ソースで資格情報が不要な場合、または他の方法で資格情報を渡している場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="4876f-133">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="4876f-134">一部の種類のデータ ソースについては、レポート サーバーで自動実行アカウントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4876f-134">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="4876f-135">詳細については、「[外部データ ソースのデータを追加する (SSRS)](add-data-from-external-data-sources-ssrs.md)」および「[自動実行アカウントの構成 (SSRS 構成マネージャー)](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」で、対応するデータ ソースの種類に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4876f-135">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="4876f-136">ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="4876f-136">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="4876f-137">アカウントが Windows ドメインユーザーアカウントの場合は、<アカウントの形式で指定し、 \<domain> \\ \> [**データソースへの接続時に windows 資格情報として使用**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4876f-137">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>  
  
    -   <span data-ttu-id="4876f-138">ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]** を選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="4876f-138">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="4876f-139">データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[実行コンテキストをこのアカウントに設定する]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="4876f-139">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
6.  <span data-ttu-id="4876f-140">データ ソースが更新後の資格情報を使用して接続できるかどうかを確認するには、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4876f-140">To verify the data source can connect using the updated credentials, **Test connection**.</span></span>  
  
7.  <span data-ttu-id="4876f-141">[このデータ ソースを有効にする] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4876f-141">Verify that Enable this data source is selected.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4876f-142">参照</span><span class="sxs-lookup"><span data-stu-id="4876f-142">See Also</span></span>  
 [<span data-ttu-id="4876f-143">SharePoint ライブラリへのドキュメントのアップロード &#40;Reporting Services の SharePoint モード&#41;</span><span class="sxs-lookup"><span data-stu-id="4876f-143">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
  
