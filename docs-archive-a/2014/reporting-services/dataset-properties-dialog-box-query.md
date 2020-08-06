---
title: '[クエリ] ([データセットのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bffb14155d37e67333eb626747e1fcc54e618bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645403"
---
# <a name="dataset-properties-dialog-box-query"></a><span data-ttu-id="ac6b2-102">[クエリ] ([データセットのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="ac6b2-102">Dataset Properties Dialog Box, Query</span></span>
  <span data-ttu-id="ac6b2-103">[データセットの**プロパティ**] ダイアログボックスの [**クエリ**] を選択すると、データソースを選択してクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-103">Select **Query** on the **Dataset Properties** dialog box to choose a data source and create a query.</span></span>  
  
 <span data-ttu-id="ac6b2-104">**[データセットのプロパティ]** ダイアログ ボックスには、次のカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-104">The **Dataset Properties** dialog box includes the following:</span></span>  
  
-   <span data-ttu-id="ac6b2-105">[[パラメーター] ([データセットのプロパティ] ダイアログ ボックス)](report-data/dataset-properties-dialog-box-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="ac6b2-105">[Dataset Properties Dialog Box, Parameters](report-data/dataset-properties-dialog-box-parameters.md)</span></span>  
  
-   <span data-ttu-id="ac6b2-106">[[フィールド] ([データセットのプロパティ] ダイアログ ボックス)](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)</span><span class="sxs-lookup"><span data-stu-id="ac6b2-106">[Dataset Properties Dialog Box, Fields](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)</span></span>  
  
-   <span data-ttu-id="ac6b2-107">[[オプション] ([データセットのプロパティ] ダイアログ ボックス)](../../2014/reporting-services/dataset-properties-dialog-box-options.md)</span><span class="sxs-lookup"><span data-stu-id="ac6b2-107">[Dataset Properties Dialog Box, Options](../../2014/reporting-services/dataset-properties-dialog-box-options.md)</span></span>  
  
-   <span data-ttu-id="ac6b2-108">[[フィルター] ([データセットのプロパティ] ダイアログ ボックス)](report-data/dataset-properties-dialog-box-filters.md)</span><span class="sxs-lookup"><span data-stu-id="ac6b2-108">[Dataset Properties Dialog Box, Filters](report-data/dataset-properties-dialog-box-filters.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="ac6b2-109">Options</span><span class="sxs-lookup"><span data-stu-id="ac6b2-109">Options</span></span>  
 <span data-ttu-id="ac6b2-110">**名前**</span><span class="sxs-lookup"><span data-stu-id="ac6b2-110">**Name**</span></span>  
 <span data-ttu-id="ac6b2-111">データセットの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-111">Type a name for the dataset.</span></span> <span data-ttu-id="ac6b2-112">名前は、レポートのすべてのデータ領域名またはグループ名と異なっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-112">The name cannot be the same as a name for any data region or group in the report.</span></span>  
  
 <span data-ttu-id="ac6b2-113">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="ac6b2-113">**Data Source**</span></span>  
 <span data-ttu-id="ac6b2-114">データセットが基づくデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-114">Select the data source on which to base the dataset.</span></span> <span data-ttu-id="ac6b2-115">新しいデータ ソースを作成するには、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-115">To create a new data source, click **New**.</span></span>  
  
 <span data-ttu-id="ac6b2-116">**クエリの種類**</span><span class="sxs-lookup"><span data-stu-id="ac6b2-116">**Query type**</span></span>  
 <span data-ttu-id="ac6b2-117">データセットに使用するコマンドまたはクエリの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-117">Select the type of command or query to use for the dataset.</span></span> <span data-ttu-id="ac6b2-118">データベースからデータを取得するクエリを実行するには、 **[テキスト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-118">Select **Text** to run a query to retrieve data from the database.</span></span> <span data-ttu-id="ac6b2-119">**の** TableDirect **機能を使用してテーブル内のすべてのフィールドを選択するには、** [テーブル] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-119">Select **Table** to use the **TableDirect** feature of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to select all the fields within a table.</span></span> <span data-ttu-id="ac6b2-120">名前を指定してストアド プロシージャを実行するには、 **[ストアド プロシージャ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-120">Select **Stored Procedure** to run a stored procedure by name.</span></span> <span data-ttu-id="ac6b2-121">既定では、ほとんどのクエリに使用される **[テキスト]** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-121">**Text** is selected by default and is used for most queries.</span></span> <span data-ttu-id="ac6b2-122">選択したデータ ソース クエリを編集するには、 **[クエリ デザイナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-122">To edit the selected data source query, click **Query Designer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac6b2-123">すべての種類のクエリがすべてのデータ ソースでサポートされるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-123">Not all query types are supported by all data sources.</span></span> <span data-ttu-id="ac6b2-124">たとえば、 **テーブル** をサポートしているデータ ソースの種類は **OLE DB** および **ODBC**のみです。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-124">For example, **Table** is supported only by data source types **OLE DB** and **ODBC**.</span></span>  
  
 <span data-ttu-id="ac6b2-125">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="ac6b2-125">**Query**</span></span>  
 <span data-ttu-id="ac6b2-126">このオプションは、コマンドの種類のオプションとして **[テキスト]** を選択したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-126">This option appears when you choose the **Text** command type option.</span></span> <span data-ttu-id="ac6b2-127">クエリを入力するか、 **[インポート]** をクリックして既存のクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-127">Type a query or import a pre-existing query by clicking **Import**.</span></span> <span data-ttu-id="ac6b2-128">式を編集するには、**式**([*fx*]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-128">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac6b2-129">クエリ デザイナーを使用してクエリを作成した場合は、クエリのテキストがこのボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-129">If you used a query designer to build a query, the text of the query appears in this box.</span></span>  
  
 <span data-ttu-id="ac6b2-130">**[テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="ac6b2-130">**Table name**</span></span>  
 <span data-ttu-id="ac6b2-131">データセットとして使用するテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-131">Enter the name of the table that you want to use as a dataset.</span></span> <span data-ttu-id="ac6b2-132">このオプションは **[テーブル]** を選択したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-132">This option appears when you select **Table**.</span></span>  
  
 <span data-ttu-id="ac6b2-133">**[ストアド プロシージャ名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="ac6b2-133">**Select or enter stored procedure name**</span></span>  
 <span data-ttu-id="ac6b2-134">使用するストアド プロシージャの名前を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-134">Type or choose the name of the stored procedure that you want to use.</span></span> <span data-ttu-id="ac6b2-135">式を編集するには、**式**([*fx*]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-135">Click the **Expression** (*fx*) button to edit the expression.</span></span> <span data-ttu-id="ac6b2-136">このオプションは、コマンドの種類のオプションとして [ストアド プロシージャ] を選択したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-136">This option appears when you choose the Stored Procedure command type option.</span></span>  
  
 <span data-ttu-id="ac6b2-137">**[タイムアウト (秒)]**</span><span class="sxs-lookup"><span data-stu-id="ac6b2-137">**Time out (in seconds)**</span></span>  
 <span data-ttu-id="ac6b2-138">クエリがタイムアウトするまでの秒数を入力します。既定値は30秒です。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-138">Type the number of seconds until the query times out. The default is 30 seconds.</span></span> <span data-ttu-id="ac6b2-139">**[タイムアウト]** には、値を指定しないか、0 より大きい値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-139">The value for **Time out** must be empty or greater than zero.</span></span> <span data-ttu-id="ac6b2-140">空の場合は、クエリはタイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="ac6b2-140">If it is empty, the query does not time out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac6b2-141">参照</span><span class="sxs-lookup"><span data-stu-id="ac6b2-141">See Also</span></span>  
 <span data-ttu-id="ac6b2-142">[Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="ac6b2-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="ac6b2-143">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ac6b2-143">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="ac6b2-144">[クエリデザイナー &#40;レポートビルダー&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ac6b2-144">[Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span></span>  
 [<span data-ttu-id="ac6b2-145">Reporting Services クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="ac6b2-145">Reporting Services Query Designers</span></span>](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
