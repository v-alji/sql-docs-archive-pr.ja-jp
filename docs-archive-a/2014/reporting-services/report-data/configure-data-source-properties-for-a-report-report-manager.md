---
title: レポートのデータ ソースのプロパティを構成する (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42969b4667dd71e4c6413f38e4deadb96491169c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632916"
---
# <a name="configure-data-source-properties-for-a-report--report-manager"></a><span data-ttu-id="707bc-102">レポートのデータ ソースのプロパティを構成する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="707bc-102">Configure Data Source Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="707bc-103">レポートを実行すると、レポート サーバーは、データ ソースへの接続方法を調べるためにプロパティ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="707bc-103">When you run a report, the report server retrieves property information to determine how to connect to a data source.</span></span> <span data-ttu-id="707bc-104">パブリッシュされたレポートの [データ ソース] プロパティ ページには、データ ソースの種類、接続文字列、および資格情報が指定されています。</span><span class="sxs-lookup"><span data-stu-id="707bc-104">The data source type, connection string, and credential information are specified in the Data Source property pages of the published report.</span></span> <span data-ttu-id="707bc-105">これらのプロパティを設定することで、データ ソースの接続情報を、レポートの作成時に指定された元の値から変更することができます。</span><span class="sxs-lookup"><span data-stu-id="707bc-105">You can set the properties to vary the data source connection information from the original values that were specified when the report was created.</span></span>  
  
 <span data-ttu-id="707bc-106">また、定義済みの共有データ ソースが存在し、そこで使用する接続情報が既に指定されている場合は、代わりにその共有データ ソースを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="707bc-106">Alternatively, if you have a predefined shared data source that already specifies the connection information you want to use, you can specify a shared data source instead.</span></span> <span data-ttu-id="707bc-107">共有データ ソースを使用するには、レポートの [データ ソース] プロパティ ページの **[共有データ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="707bc-107">To use a shared data source, click **A shared data source** on the Data Source properties page of the report.</span></span>  
  
### <a name="to-configure-an-embedded-data-source"></a><span data-ttu-id="707bc-108">埋め込みデータ ソースを構成するには</span><span class="sxs-lookup"><span data-stu-id="707bc-108">To configure an embedded data source</span></span>  
  
1.  <span data-ttu-id="707bc-109">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="707bc-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="707bc-110">レポート マネージャーで **[コンテンツ]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="707bc-110">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="707bc-111">レポート固有のデータ ソースを構成するレポートに移動し、そのレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="707bc-111">Navigate to the report that you want to configure a report-specific data source for, and open the report.</span></span>  
  
3.  <span data-ttu-id="707bc-112">[**プロパティ**] タブをクリックします。**[全般**プロパティ] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="707bc-112">Click the **Properties** tab. The **General** properties page opens.</span></span>  
  
4.  <span data-ttu-id="707bc-113">[**データソース**] タブをクリックします。これにより、レポートの [データソース] プロパティページが開きます。</span><span class="sxs-lookup"><span data-stu-id="707bc-113">Click the **Data Sources** tab. This opens the Data Source properties page of the report.</span></span>  
  
5.  <span data-ttu-id="707bc-114">**[カスタム データ ソース]** をクリックして、レポート内のデータ ソース接続情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="707bc-114">Click **A custom data source** to specify data source connection information within the report.</span></span>  
  
6.  <span data-ttu-id="707bc-115">**[接続の種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="707bc-115">In the **Connection Type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="707bc-116">[**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="707bc-116">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="707bc-117">接続文字列には資格情報を指定しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="707bc-117">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="707bc-118">次の例は、ローカルデータベースに接続するための接続文字列を示してい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="707bc-118">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="707bc-119">**[接続に使用する認証]** では、レポートが実行される際に資格情報を取得する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="707bc-119">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="707bc-120">ユーザーにログオン名とパスワードを要求する場合は、 **[レポートの実行者により指定された資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="707bc-120">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span>  
  
    -   <span data-ttu-id="707bc-121">サブスクリプションやその他のスケジュールに設定された操作 (自動レポート履歴生成など) をサポートするレポートでデータ ソースを使用する場合は、 **[レポート サーバーに保存され、セキュリティで保護された資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="707bc-121">If you intend to use the data source with reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span>  
  
    -   <span data-ttu-id="707bc-122">レポート サーバーが、レポートにアクセスするユーザーの資格情報を、外部データ ソースをホストするサーバーに渡す場合は、 **[Windows 統合セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="707bc-122">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="707bc-123">この場合、ユーザーはユーザー名やパスワードを入力することを要求されません。</span><span class="sxs-lookup"><span data-stu-id="707bc-123">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="707bc-124">データ ソースで資格情報を使用しない場合 (ファイル システムからアクセス可能な XML ファイルをデータ ソースとして使用する場合など) は、 **[資格情報は必要ありません]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="707bc-124">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="707bc-125">この資格情報オプションは、使用するデータ ソースで妥当と考えられる場合にのみ指定してください。</span><span class="sxs-lookup"><span data-stu-id="707bc-125">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="707bc-126">認証を必要とするデータ ソースに対してこのオプションを選択した場合、接続エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="707bc-126">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="707bc-127">このオプションを選択する場合は、ユーザーの資格情報を利用できない場合に、レポート サーバーが他のコンピューターに接続して、データまたはファイルを取得できるように、必ず自動実行アカウントを構成してください。</span><span class="sxs-lookup"><span data-stu-id="707bc-127">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
 <span data-ttu-id="707bc-128">資格情報の構成の詳細については、「 [レポート データ ソースに関する資格情報と接続情報を指定する](specify-credential-and-connection-information-for-report-data-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="707bc-128">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="707bc-129">自動実行アカウントについては、「[自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="707bc-129">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707bc-130">参照</span><span class="sxs-lookup"><span data-stu-id="707bc-130">See Also</span></span>  
 <span data-ttu-id="707bc-131">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="707bc-131">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="707bc-132">[[新しいデータソース] ページ &#40;レポートマネージャー&#41;](../new-data-source-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="707bc-132">[New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md) </span></span>  
 <span data-ttu-id="707bc-133">[SSRS&#41;&#40;共有データソースを作成、変更、および削除します。](create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="707bc-133">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="707bc-134">[レポートデータソースの管理](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="707bc-134">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="707bc-135">[共有データソース &#40;レポートマネージャーの作成、削除、または変更&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="707bc-135">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="707bc-136">[[データ ソース] プロパティ ページ &#40;レポート マネージャー&#41;](../data-sources-properties-page-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="707bc-136">[Data Sources Properties Page &#40;Report Manager&#41;](../data-sources-properties-page-report-manager.md)</span></span>  
  
  
