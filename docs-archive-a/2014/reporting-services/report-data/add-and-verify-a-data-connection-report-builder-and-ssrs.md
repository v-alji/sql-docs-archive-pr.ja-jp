---
title: データ接続またはデータソースの追加と検証 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d3b2573-e29d-480d-9dde-d26379c86618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d86b3e6598c12545f0e24ef1d162eeb1131bd15d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631603"
---
# <a name="add-and-verify-a-data-connection-or-data-source-report-builder-and-ssrs"></a><span data-ttu-id="8da9d-102">データ接続またはデータ ソースの追加および確認 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8da9d-102">Add and Verify a Data Connection or Data Source (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8da9d-103">レポート ビルダーでは、レポート サーバーから共有データ ソースを追加することも、レポートで使用される埋め込みデータ ソースを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-103">In Report Builder, you can add a shared data source from the report server or create an embedded data source for your report.</span></span> <span data-ttu-id="8da9d-104">レポート デザイナーでは、共有データ ソースまたは埋め込みデータ ソースを作成して、レポート サーバーに配置することができます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-104">In Report Designer, you can create a shared data source or an embedded data source and deploy it to a report server.</span></span>  
  
 <span data-ttu-id="8da9d-105">レポートに共有データ ソースを追加するには、レポート サーバーを参照して共有データ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-105">To add a shared data source to your report, browse to a report server and select a shared data source.</span></span> <span data-ttu-id="8da9d-106">レポート内の共有データ ソースは、レポート サーバー上の共有データ ソース定義を参照しています。</span><span class="sxs-lookup"><span data-stu-id="8da9d-106">The shared data source in your report points to the shared data source definition on the report server.</span></span>  
  
 <span data-ttu-id="8da9d-107">埋め込みデータ ソースを作成するには、データの外部ソースへの接続情報が必要で、データへのアクセスに必要な権限を把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8da9d-107">To create an embedded data source, you must have connection information to the external source of data and you must know which permissions you need to access the data.</span></span> <span data-ttu-id="8da9d-108">通常、この情報は、データ ソースの所有者から得られます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-108">This information usually comes from the owner of the data source.</span></span> <span data-ttu-id="8da9d-109">接続をテストすることによって、指定されている資格情報が十分かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-109">You can test the connection to verify that the credentials that are specified are sufficient.</span></span>  
  
 <span data-ttu-id="8da9d-110">詳細については、「[レポートビルダーのデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」および「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da9d-110">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) and [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-reference-to-a-shared-data-source"></a><span data-ttu-id="8da9d-111">共有データ ソースの参照を作成するには</span><span class="sxs-lookup"><span data-stu-id="8da9d-111">To create a reference to a shared data source</span></span>  
  
1.  <span data-ttu-id="8da9d-112">ツール バーのレポート データ ペインで、 **[新規作成]** 、 **[データ ソース]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da9d-112">On the toolbar in the Report Data pane, click **New,** and then click **Data Source**.</span></span> <span data-ttu-id="8da9d-113">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-113">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8da9d-114">**[名前]** ボックスに、データ ソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-114">In the **Name** text box, type a name for the data source.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8da9d-115">この名前は、ローカル レポート定義に保存されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-115">This name is saved in the local report definition.</span></span> <span data-ttu-id="8da9d-116">この名前は、レポート サーバー上の共有データ ソースの名前ではありません。</span><span class="sxs-lookup"><span data-stu-id="8da9d-116">This name is not the name of the shared data source on the report server.</span></span>  
  
3.  <span data-ttu-id="8da9d-117">**[共有接続またはレポート モデルを使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-117">Select **Use a shared connection or report model**.</span></span> <span data-ttu-id="8da9d-118">最近使用した共有データ ソースおよびレポート モデルの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-118">The list of recently used shared data sources and report models appears.</span></span> <span data-ttu-id="8da9d-119">レポート サーバーから共有データ ソースを 1 つ選択するには、 **[参照]** をクリックし、共有データ ソースを使用できるレポート サーバー上のフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-119">To select one from a report server, click **Browse** and browse to the folder on the report server where shared data sources are available.</span></span>  
  
4.  <span data-ttu-id="8da9d-120">共有データ ソースを選択し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da9d-120">Select the shared data source and then click **Open**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="8da9d-121">データ ソースがレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-121">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="8da9d-122">埋め込みデータ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="8da9d-122">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="8da9d-123">ツール バーのレポート データ ペインで、 **[新規作成]**、 **[データ ソース]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da9d-123">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span> <span data-ttu-id="8da9d-124">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-124">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8da9d-125">**[名前]** ボックスにデータ ソースの名前を入力するか、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-125">In the **Name** text box, type a name for the data source or accept the default.</span></span>  
  
3.  <span data-ttu-id="8da9d-126">**[個人用レポートに埋め込まれている接続を使用]** がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-126">Verify that **Use a connection embedded in my report** is selected.</span></span>  
  
    1.  <span data-ttu-id="8da9d-127">**[接続の種類の選択]** ボックスの一覧から、データ ソースの種類 ( **[Microsoft SQL Server]** や **[OLE DB]** など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-127">From the **Select connection type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="8da9d-128">次の選択肢の 1 つを使用して、接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-128">Specify a connection string by using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="8da9d-129">**[接続文字列]** ボックスに接続文字列を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-129">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="8da9d-130">接続文字列の例の一覧については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da9d-130">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
    -   <span data-ttu-id="8da9d-131">式 (**[fx]** ) ボタンをクリックして、接続文字列を評価する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-131">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="8da9d-132">**[式]** ダイアログ ボックスで、式ペインに式を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-132">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="8da9d-133">**[構築]** をクリックして、手順 2 で選択したデータ ソースの種類の **[接続のプロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-133">Click **Build** to open the **Connection Properties** dialog box for the data source type that you chose in step 2.</span></span>  
  
         <span data-ttu-id="8da9d-134">データ ソースの種類に合わせて **[接続のプロパティ]** ダイアログ ボックスのフィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-134">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="8da9d-135">接続のプロパティには、データ ソースの種類、データ ソースの名前、および使用する資格情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-135">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="8da9d-136">このダイアログ ボックスで値を指定した後、 **[接続テスト]** をクリックして、データ ソースが使用可能であること、および指定した資格情報が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-136">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span>  
  
4.  <span data-ttu-id="8da9d-137">**[資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da9d-137">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="8da9d-138">このデータ ソースに使用する資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-138">Specify the credentials to use for this data source.</span></span> <span data-ttu-id="8da9d-139">サポートされる資格情報の種類は、データ ソースの所有者によって選択されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-139">The owner of the data source chooses the type of credentials that are supported.</span></span> <span data-ttu-id="8da9d-140">場合によっては、データ ソースの所有者がレポート サーバーで共有データ ソースを管理し、そのデータ ソースで使用可能な資格情報を構成していることがあります。</span><span class="sxs-lookup"><span data-stu-id="8da9d-140">In some cases, the owner of the data source maintains a shared data source on a report server and configures the data source with credentials that you can use.</span></span> <span data-ttu-id="8da9d-141">この情報については、データ ソースの所有者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="8da9d-141">Contact the data source owner for this information.</span></span> <span data-ttu-id="8da9d-142">詳細については、「 [レポート ビルダーでの資格情報の指定](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da9d-142">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="8da9d-143">データ ソースがレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-143">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-verify-a-data-connection"></a><span data-ttu-id="8da9d-144">データ接続を確認するには</span><span class="sxs-lookup"><span data-stu-id="8da9d-144">To verify a data connection</span></span>  
  
1.  <span data-ttu-id="8da9d-145">レポート データ ペインのツール バーで、データ ソースをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da9d-145">On the toolbar in the Report Data pane, double-click the data source.</span></span> <span data-ttu-id="8da9d-146">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-146">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8da9d-147">**[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da9d-147">Click **Test Connection**.</span></span>  
  
3.  <span data-ttu-id="8da9d-148">接続に成功すると、"接続が正常に作成されました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-148">If the connection is successful, the following message appears: "Connection created successfully".</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="8da9d-149">接続に成功しなかった場合は、"データ ソースに接続できません。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da9d-149">If the connection is not successful, the following message appears: "Unable to connect to the data source."</span></span>  
  
5.  <span data-ttu-id="8da9d-150">**[詳細]** をクリックし、情報に基づいて問題を修正します。</span><span class="sxs-lookup"><span data-stu-id="8da9d-150">Click **Details**, and use the information to correct the issue.</span></span>  
  
     <span data-ttu-id="8da9d-151">詳細については、「 [レポート ビルダーでの資格情報の指定](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da9d-151">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8da9d-152">参照</span><span class="sxs-lookup"><span data-stu-id="8da9d-152">See Also</span></span>  
 <span data-ttu-id="8da9d-153">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8da9d-153">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="8da9d-154">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8da9d-154">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8da9d-155">[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8da9d-155">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8da9d-156">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="8da9d-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
