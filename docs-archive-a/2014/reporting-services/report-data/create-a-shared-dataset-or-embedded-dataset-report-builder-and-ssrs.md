---
title: 共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d1d7bc71-f0e9-4ce5-b3ad-6fee54388a31
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fca74e1ba7965eeef6ce562e79e378af5bb9e145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712793"
---
# <a name="create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs"></a><span data-ttu-id="55cc0-102">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="55cc0-102">Create a Shared Dataset or Embedded Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="55cc0-103">データセットを作成する際は、1 つのレポートに使用する埋め込みデータセットか、レポート サーバーに保存して複数のレポートに使用する共有データセットを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-103">You can create an embedded dataset for use in a single report or a shared dataset to save to a report server, for use by multiple reports.</span></span> <span data-ttu-id="55cc0-104">データセットを作成するには、埋め込みデータ ソースまたは共有データ ソースが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55cc0-104">To create a dataset, you must have an embedded or shared data source.</span></span>

 <span data-ttu-id="55cc0-105">レポート ビルダーを使用して、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="55cc0-105">Use Report Builder to do the following tasks:</span></span>

-   <span data-ttu-id="55cc0-106">データセットのデザイン ビューで共有データセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-106">Create a shared dataset in Dataset Design View.</span></span> <span data-ttu-id="55cc0-107">共有データセットには、パブリッシュされた共有データ ソースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55cc0-107">Shared datasets must use published shared data sources.</span></span>

-   <span data-ttu-id="55cc0-108">レポートのデザイン ビューで、埋め込みのデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-108">Create an embedded dataset in Report Design View.</span></span>

-   <span data-ttu-id="55cc0-109">レポート サーバーまたは SharePoint サイトにデータセットを直接保存します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-109">Save the dataset directly to the report server or SharePoint site.</span></span>

 <span data-ttu-id="55cc0-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、レポート デザイナーを使用して、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="55cc0-110">Use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to do the following tasks:</span></span>

1.  <span data-ttu-id="55cc0-111">ソリューション エクスプローラーで共有データセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-111">Create a shared dataset in Solution Explorer.</span></span> <span data-ttu-id="55cc0-112">共有データセットには、ソリューション エクスプローラーの [共有データ ソース] フォルダーのデータ ソースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55cc0-112">Shared datasets must use data sources from the Shared Data Sources folder in Solution Explorer.</span></span>

2.  <span data-ttu-id="55cc0-113">レポート データ ペインで、埋め込みデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-113">Create an embedded dataset in the Report Data pane.</span></span>

3.  <span data-ttu-id="55cc0-114">必要に応じて、共有データセットと共有データ ソースをレポートと一緒に配置します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-114">Optionally deploy the shared datasets and shared data source with the report.</span></span> <span data-ttu-id="55cc0-115">アイテムの種類ごとに、プロジェクトのプロパティを使用して、レポート サーバーまたは SharePoint サイト上のフォルダーへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-115">For each type of item, use Project Properties to specify paths to folders on the report server or SharePoint site.</span></span>

 <span data-ttu-id="55cc0-116">詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-116">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-open-report-builder-and-create-a-shared-dataset"></a><span data-ttu-id="55cc0-117">レポート ビルダーを開き、共有データセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="55cc0-117">To open Report Builder and create a shared dataset</span></span>

1.  <span data-ttu-id="55cc0-118">レポート ビルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-118">Open Report Builder.</span></span> <span data-ttu-id="55cc0-119">次の図のように、 **[新しいレポートまたはデータセット]** ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-119">The **New report or dataset pane** opens, as shown in the following figure:</span></span>

     <span data-ttu-id="55cc0-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span><span class="sxs-lookup"><span data-stu-id="55cc0-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="55cc0-121">**[新しいレポートまたはデータセット]** ペインが表示されない場合は、レポート ビルダーのボタンの **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-121">If the **New report or dataset pane** does not appear, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="55cc0-122">左側のペインの **[データセットを作成する]** にある **[共有データセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-122">In the left pane, under **Create a dataset**, click **Shared Dataset**.</span></span>

3.  <span data-ttu-id="55cc0-123">右側のペインで、 **[参照]** をクリックしてレポート サーバーから共有データ ソースを選択し、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-123">In the right pane, click **Browse** to select a shared data source from the report server, and then click **Create**.</span></span> <span data-ttu-id="55cc0-124">共有データ ソースに関連付けられたクエリ デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-124">The query designer associated with the shared data source opens.</span></span>

4.  <span data-ttu-id="55cc0-125">クエリ デザイナーで、データセットに含めるフィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-125">In the query designer, specify the fields to include in the dataset.</span></span>

5.  <span data-ttu-id="55cc0-126">[**実行**] (**!**) をクリックしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-126">Click **Run** (**!**) to run the query.</span></span>

6.  <span data-ttu-id="55cc0-127">**レポート ビルダー** のボタンの **[保存]** または **[名前を付けて保存]** をクリックして、共有データセットをレポート サーバーに保存します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-127">On the **Report Builder** button, click **Save** or **Save As** to save the shared dataset to the report server.</span></span>

7.  <span data-ttu-id="55cc0-128">レポート ビルダーを終了するには、 **[レポート ビルダー]** をクリックして、 **[レポート ビルダーの終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-128">To exit Report Builder, click **Report Builder**, and then click **Exit Report Builder**.</span></span> <span data-ttu-id="55cc0-129">レポートを使用するには、 **[レポート ビルダー]** をクリックして、 **[新規作成]** または **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-129">To work with reports, click **Report Builder**, and then click **New** or **Open**.</span></span>

### <a name="to-set-query-parameter-options"></a><span data-ttu-id="55cc0-130">クエリ パラメーター オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="55cc0-130">To set query parameter options</span></span>

1.  <span data-ttu-id="55cc0-131">レポート ビルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-131">Open Report Builder.</span></span>

2.  <span data-ttu-id="55cc0-132">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-132">Click **Open**.</span></span>

3.  <span data-ttu-id="55cc0-133">レポート サーバーを参照して共有データ ソースのフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-133">Browse to the report server, and select the folder for the shared data source.</span></span>

4.  <span data-ttu-id="55cc0-134">**[アイテムの種類]** で、ドロップダウン リストの [データセット (\*.rsd)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-134">In **Items of type**, click Datasets (\*.rsd) in the drop-down list.</span></span>

5.  <span data-ttu-id="55cc0-135">共有データセットを選択し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-135">Select the shared dataset, and then click **Open**.</span></span> <span data-ttu-id="55cc0-136">関連付けられているクエリ デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-136">The associated query designer opens.</span></span>

6.  <span data-ttu-id="55cc0-137">リボンの **[データセットのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-137">On the Ribbon, click **Dataset Properties**.</span></span>

7.  <span data-ttu-id="55cc0-138">**[パラメーター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-138">Click **Parameters**.</span></span> <span data-ttu-id="55cc0-139">このページで、定数または式に既定値を設定し、パラメーターを読み取り専用、Null 値許容、または **[クエリから省略]** としてマークします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-139">On this page, set a default value to a constant or an expression, mark the parameter as read-only, nullable, or **Omit From Query**.</span></span> <span data-ttu-id="55cc0-140">詳細については、「[[パラメーター] ([データセットのプロパティ] ダイアログ ボックス) &#40;レポート ビルダー&#41;](../dataset-properties-dialog-box-parameters-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55cc0-140">For more information, see [Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../dataset-properties-dialog-box-parameters-report-builder.md).</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]


### <a name="to-create-a-dataset-from-a-sql-server-relational-database"></a><span data-ttu-id="55cc0-141">SQL Server リレーショナル データベースからデータセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="55cc0-141">To create a dataset from a SQL Server relational database</span></span>

1.  <span data-ttu-id="55cc0-142">レポート データ ペインでデータ ソース名を右クリックし、 **[データセットの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-142">In the Report Data pane, right-click the name of the data source, and then click **Add Dataset**.</span></span> <span data-ttu-id="55cc0-143">**[データセットのプロパティ]** ダイアログ ボックスの **[クエリ]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-143">The **Query** page of the **Dataset Properties** dialog box opens.</span></span>

2.  <span data-ttu-id="55cc0-144">**[名前]** にデータセットの名前を入力するか、既定の名前をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-144">In **Name**, type a name for the dataset or accept the default name.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="55cc0-145">データセット名は、レポート内部で使用されます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-145">The dataset name is used internally within the report.</span></span> <span data-ttu-id="55cc0-146">判断しやすいように、データセットには、クエリが返すデータがわかるような名前を付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-146">For clarity, we recommend that the name of the dataset describe the data that the query returns.</span></span>

3.  <span data-ttu-id="55cc0-147">**[データ ソース]** で既存の共有データ ソースの名前を参照して選択するか、 **[新規作成]** をクリックして新しい埋め込みデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-147">In **Data source**, browse to and select the name of an existing shared data source, or click **New** to create a new embedded data source.</span></span>

4.  <span data-ttu-id="55cc0-148">**[クエリの種類]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-148">Select a **Query type** option.</span></span> <span data-ttu-id="55cc0-149">オプションは、データ ソースの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="55cc0-149">Options depend on the data source type.</span></span>

    -   <span data-ttu-id="55cc0-150">データ ソースのクエリ言語を使用したクエリを作成するには、 **[Text]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-150">Select **Text** to write a query using the query language of the data source.</span></span>

    -   <span data-ttu-id="55cc0-151">リレーショナル データベース テーブルのすべてのフィールドを取得するには、 **[Table]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-151">Select **Table** to return all the fields in a relational database table.</span></span>

    -   <span data-ttu-id="55cc0-152">名前を指定してストアド プロシージャを実行するには、 **[ストアド プロシージャ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-152">Select **StoredProcedure** to run a stored procedure by name.</span></span>

5.  <span data-ttu-id="55cc0-153">**[クエリ]** には、クエリ、ストアド プロシージャ、またはテーブル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-153">In **Query**, type the query, stored procedure, or table name.</span></span> <span data-ttu-id="55cc0-154">あるいは、 **[クエリ デザイナー]** をクリックしてグラフィカルまたはテキストベースのクエリ デザイナー ツールを開くか、 **[インポート]** をクリックして既存のレポートからクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="55cc0-154">Alternatively, click **Query Designer** to open the graphical or text-based query designer tool, or **Import** to import the query from an existing report.</span></span>

     <span data-ttu-id="55cc0-155">ただし、データ ソースでクエリを実行することによってしか、クエリによって指定されたフィールド コレクションを決定できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="55cc0-155">In a few cases, the field collection specified by the query can only be determined by running the query on the data source.</span></span> <span data-ttu-id="55cc0-156">たとえば、ストアド プロシージャは結果セットのフィールドの変数セットを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="55cc0-156">For example, a stored procedure may return a variable set of fields in the result set.</span></span> <span data-ttu-id="55cc0-157">**[フィールドの更新]** をクリックしてデータ ソースでクエリを実行し、レポート データ ペインのデータセット フィールド コレクションを設定するのに必要なフィールド名を取得します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-157">Click **Refresh Fields** to run the query on the data source and retrieve the field names that are needed to populate the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="55cc0-158">**[データセットのプロパティ]** ダイアログ ボックスを閉じると、フィールド コレクションがデータセット ノードの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-158">The field collection appears under the dataset node after you close the **Dataset Properties** dialog box.</span></span>

6.  <span data-ttu-id="55cc0-159">**[タイムアウト]** には、レポート サーバーがデータベースからの応答を待機する秒数を入力します。</span><span class="sxs-lookup"><span data-stu-id="55cc0-159">In **Timeout**, type the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="55cc0-160">既定値は 0 秒です。</span><span class="sxs-lookup"><span data-stu-id="55cc0-160">The default value is 0 seconds.</span></span> <span data-ttu-id="55cc0-161">クエリ タイムアウト値が 0 秒の場合は、クエリはタイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="55cc0-161">When the time out value is 0 seconds, the query does not time out.</span></span>

7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="55cc0-162">データセットとそのフィールド コレクションがレポート データ ペインのデータ ソース ノードの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="55cc0-162">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>

## <a name="see-also"></a><span data-ttu-id="55cc0-163">参照</span><span class="sxs-lookup"><span data-stu-id="55cc0-163">See Also</span></span>
 <span data-ttu-id="55cc0-164">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと ssrs&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [データセットフィールドコレクション &#40;レポートビルダーと Ssrs&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [クエリデザイナー &#40;](../query-designers-report-builder.md)レポートビルダー&#41;レポートビルダーと Ssrs &#40;[の](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)[データ接続、データソース、および接続文字列レポートビルダー&#41;と ssrs レポートビルダーのデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md) [をレポートに追加](report-datasets-ssrs.md)&#40;</span><span class="sxs-lookup"><span data-stu-id="55cc0-164">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) [Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)</span></span>


