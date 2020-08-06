---
title: 共有データソースを作成、削除、または変更する (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- removing shared data sources
- data sources [Reporting Services], shared
- deleting shared data sources
- modifying shared data sources
ms.assetid: cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6f4ff658e656b159995087df3121806b462e687
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641514"
---
# <a name="create-delete-or-modify-a-shared-data-source-report-manager"></a><span data-ttu-id="dab02-102">共有データ ソースを作成、削除、または変更する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="dab02-102">Create, Delete, or Modify a Shared Data Source (Report Manager)</span></span>
  <span data-ttu-id="dab02-103">共有データ ソースでは、1 つのデータ ソースに対する接続プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="dab02-103">A shared data source specifies connection properties for a data source.</span></span> <span data-ttu-id="dab02-104">多数のレポート、モデル、またはデータ ドリブン サブスクリプションで 1 つのデータ ソースを使用する場合は、共有データ ソースを作成することにより、同じ接続情報を複数箇所で管理するオーバーヘッドを低減できます。</span><span class="sxs-lookup"><span data-stu-id="dab02-104">If you have a data source that is used by a large number of reports, models, or data-driven subscriptions, consider creating a shared data source to eliminate the overhead of having to maintain the same connection information in multiple places.</span></span>  
  
 <span data-ttu-id="dab02-105">次のアイコンは、レポート マネージャーのフォルダー階層内の共有データ ソースを示します。</span><span class="sxs-lookup"><span data-stu-id="dab02-105">The following icon indicates a shared data source in the Report Manager folder hierarchy:</span></span>  
  
 <span data-ttu-id="dab02-106">![共有データ ソースのアイコン](media/hlp-16datasource.png "共有データ ソースのアイコン")</span><span class="sxs-lookup"><span data-stu-id="dab02-106">![Shared data source icon](media/hlp-16datasource.png "Shared data source icon")</span></span>  
<span data-ttu-id="dab02-107">共有データ ソースのアイコン</span><span class="sxs-lookup"><span data-stu-id="dab02-107">shared data source icon</span></span>  
  
### <a name="to-create-a-shared-data-source"></a><span data-ttu-id="dab02-108">共有データ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="dab02-108">To create a shared data source</span></span>  
  
1.  <span data-ttu-id="dab02-109">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="dab02-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="dab02-110">レポート マネージャーで **[コンテンツ]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="dab02-110">In Report Manager, navigate to the **Contents** page.</span></span>  
  
3.  <span data-ttu-id="dab02-111">**[新しいデータ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-111">Click **New Data Source**.</span></span> <span data-ttu-id="dab02-112">**[新しいデータ ソース]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="dab02-112">The **New Data Source** page opens.</span></span>  
  
4.  <span data-ttu-id="dab02-113">アイテムの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="dab02-113">Type a name for the item.</span></span> <span data-ttu-id="dab02-114">名前は 1 文字以上で、文字で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dab02-114">A name must contain at least one character and it must start with a letter.</span></span> <span data-ttu-id="dab02-115">特定の記号を含めることもできますが、スペースまたは ; ?</span><span class="sxs-lookup"><span data-stu-id="dab02-115">It can also include certain symbols, but not spaces or the characters ; ?</span></span> <span data-ttu-id="dab02-116">: \@ & = +、$/\* \< > |" /.</span><span class="sxs-lookup"><span data-stu-id="dab02-116">: \@ & = + , $ / \* \< > | " /.</span></span>  
  
5.  <span data-ttu-id="dab02-117">必要に応じて説明を入力し、接続に関する情報をユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="dab02-117">Optionally type a description to provide users with information about the connection.</span></span> <span data-ttu-id="dab02-118">この説明は、レポート マネージャーの **[コンテンツ]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="dab02-118">This description will appear on the **Contents** page in Report Manager.</span></span>  
  
6.  <span data-ttu-id="dab02-119">**[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="dab02-119">In the **Data source type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="dab02-120">**[接続文字列]** でレポート サーバーがデータ ソースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="dab02-120">For **Connection string**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="dab02-121">接続文字列には資格情報を指定しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dab02-121">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="dab02-122">次の例は、ローカルデータベースに接続するための接続文字列を示してい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="dab02-122">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="dab02-123">**[接続に使用する認証]** では、レポートが実行される際に資格情報を取得する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="dab02-123">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="dab02-124">ユーザーにログオン名とパスワードを要求する場合は、 **[レポートの実行者により指定された資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-124">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span> <span data-ttu-id="dab02-125">ユーザーが入力する資格情報を Windows 資格情報として使用するには、 **[データ ソースへの接続時に Windows 資格情報として使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-125">To use the credentials that the user enters as Windows credentials, click **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="dab02-126">ユーザー名とパスワードがデータベースの資格情報である場合は、このオプションを選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="dab02-126">If the user name and password are database credentials, do not select this option.</span></span>  
  
    -   <span data-ttu-id="dab02-127">データ ソースの使用目的が、保存された資格情報によって所有者が管理する共有データ ソースとしての使用や、サブスクリプションやその他のスケジュール設定された操作 (自動レポート履歴生成など) をサポートするレポートでの使用である場合は、 **[レポート サーバーに保存され、セキュリティで保護された資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-127">If you intend to use the data source as a shared data source with saved credentials that are managed by the owner of the data source, or for reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span> <span data-ttu-id="dab02-128">データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[データ ソースへの接続が確立した後に、認証されているユーザーの権限を借用する]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="dab02-128">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>  
  
    -   <span data-ttu-id="dab02-129">レポート サーバーが、レポートにアクセスするユーザーの資格情報を、外部データ ソースをホストするサーバーに渡す場合は、 **[Windows 統合セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-129">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="dab02-130">この場合、ユーザーはユーザー名やパスワードを入力することを要求されません。</span><span class="sxs-lookup"><span data-stu-id="dab02-130">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="dab02-131">データ ソースで資格情報を使用しない場合 (ファイル システムからアクセス可能な XML ファイルをデータ ソースとして使用する場合など) は、 **[資格情報は必要ありません]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-131">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="dab02-132">この資格情報オプションは、使用するデータ ソースで妥当と考えられる場合にのみ指定してください。</span><span class="sxs-lookup"><span data-stu-id="dab02-132">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="dab02-133">認証を必要とするデータ ソースに対してこのオプションを選択した場合、接続エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dab02-133">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="dab02-134">このオプションを選択する場合は、ユーザーの資格情報を利用できない場合に、レポート サーバーが他のコンピューターに接続して、データまたはファイルを取得できるように、必ず自動実行アカウントを構成してください。</span><span class="sxs-lookup"><span data-stu-id="dab02-134">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
     <span data-ttu-id="dab02-135">資格情報の構成の詳細については、「 [レポート データ ソースに関する資格情報と接続情報を指定する](report-data/specify-credential-and-connection-information-for-report-data-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dab02-135">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="dab02-136">自動実行アカウントについては、「[自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dab02-136">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
9. <span data-ttu-id="dab02-137">データ ソース構成を検証するには、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-137">Click the **Test Connection** button to validate the data source configuration.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dab02-138">[接続テスト] ボタンは、XML データ ソースの種類ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dab02-138">The Test Connection button is not supported for the XML data source type.</span></span>  
  
10. <span data-ttu-id="dab02-139">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="dab02-139">Click **OK**</span></span>  
  
### <a name="to-modify-a-shared-data-source"></a><span data-ttu-id="dab02-140">共有データ ソースを変更するには</span><span class="sxs-lookup"><span data-stu-id="dab02-140">To modify a shared data source</span></span>  
  
1.  <span data-ttu-id="dab02-141">レポート マネージャーで [コンテンツ] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="dab02-141">In Report Manager, navigate to the Contents page.</span></span>  
  
2.  <span data-ttu-id="dab02-142">共有データ ソース アイテムに移動し、アイテムの上にマウス ポインターを移動して、ドロップダウン リストをクリックし、コンテキスト メニューから **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-142">Navigate to the shared data source item, hover over the item, click the drop-down list, and from the context menu, click **Manage**.</span></span> <span data-ttu-id="dab02-143">**[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="dab02-143">The **Properties** page opens.</span></span>  
  
3.  <span data-ttu-id="dab02-144">データ ソースを変更し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-144">Modify the data source, and then click **Apply**.</span></span>  
  
### <a name="to-delete-a-shared-data-source"></a><span data-ttu-id="dab02-145">共有データ ソースを削除するには</span><span class="sxs-lookup"><span data-stu-id="dab02-145">To delete a shared data source</span></span>  
  
-   <span data-ttu-id="dab02-146">レポート マネージャーで、 **[コンテンツ]** ページに移動し、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="dab02-146">In Report Manager, navigate to the **Contents** page and do one of the following:</span></span>  
  
    -   <span data-ttu-id="dab02-147">共有データ ソース アイテムに移動します。</span><span class="sxs-lookup"><span data-stu-id="dab02-147">Navigate to the shared data source item.</span></span>  
  
         <span data-ttu-id="dab02-148">アイテムをクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="dab02-148">Click the item to open it.</span></span> <span data-ttu-id="dab02-149">[全般プロパティ] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="dab02-149">The General Properties page opens.</span></span>  
  
         <span data-ttu-id="dab02-150">**[削除]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-150">Click **Delete**, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="dab02-151">**[コンテンツ]** ページで、削除するデータ ソースを含むフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="dab02-151">In the **Contents** page, navigate to the folder that contains the data source you want to delete.</span></span>  
  
         <span data-ttu-id="dab02-152">アイテムの上にマウス ポインターを移動して、ドロップダウン リストをクリックし、コンテキスト メニューから **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dab02-152">Hover over the item, click the drop-down list, and from the context menu, click **Delete**.</span></span>  
  
         [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dab02-153">参照</span><span class="sxs-lookup"><span data-stu-id="dab02-153">See Also</span></span>  
 <span data-ttu-id="dab02-154">[Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="dab02-154">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="dab02-155">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="dab02-155">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="dab02-156">[SSRS&#41;&#40;共有データソースを作成、変更、および削除します。](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dab02-156">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="dab02-157">[レポートデータソースの管理](report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="dab02-157">[Manage Report Data Sources](report-data/manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="dab02-158">レポートのデータ ソースのプロパティを構成する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="dab02-158">Configure Data Source Properties for a Report  &#40;Report Manager&#41;</span></span>](report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  
