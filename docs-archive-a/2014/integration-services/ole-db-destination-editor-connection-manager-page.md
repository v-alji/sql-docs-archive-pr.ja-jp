---
title: OLE DB 変換先エディター ([接続マネージャー] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdestadapter.connection.f1
helpviewer_keywords:
- OLE DB Destination Editor
ms.assetid: ae2200c6-8ba0-49b7-b01a-53425b84d2ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7217380d664ac5d20cf1ba7b437924ee3460841b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633217"
---
# <a name="ole-db-destination-editor-connection-manager-page"></a><span data-ttu-id="ba72c-102">[OLE DB 変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="ba72c-102">OLE DB Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="ba72c-103">**[OLE DB 変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、変換先の OLE DB 接続を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-103">Use the **Connection Manager** page of the **OLE DB Destination Editor** dialog box to select the OLE DB connection for the destination.</span></span> <span data-ttu-id="ba72c-104">さらにこのページを使用して、データベースのテーブルやビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-105">`CommandTimeout`OLE DB 変換先のプロパティは、 **OLE DB 変換先エディター**では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-105">The `CommandTimeout` property of the OLE DB destination is not available in the **OLE DB Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="ba72c-106">また、一部の高速読み込みオプションは **[詳細エディター]** でしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="ba72c-106">In addition, certain fast load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="ba72c-107">これらのプロパティの詳細については、「 [OLE DB カスタム プロパティ](data-flow/ole-db-custom-properties.md)」の OLE DB 変換先に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-107">For more information on these properties, see the OLE DB Destination section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="ba72c-108">OLE DB 変換先の詳細については、「 [OLE DB Destination](data-flow/ole-db-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-108">To learn more about the OLE DB destination, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="ba72c-109">静的オプション</span><span class="sxs-lookup"><span data-stu-id="ba72c-109">Static Options</span></span>  
 <span data-ttu-id="ba72c-110">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="ba72c-111">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-111">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="ba72c-112">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-112">**New**</span></span>  
 <span data-ttu-id="ba72c-113">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-113">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="ba72c-114">**[データ アクセス モード]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-114">**Data access mode**</span></span>  
 <span data-ttu-id="ba72c-115">データを変換先に読み込む方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-115">Specify the method for loading data into the destination.</span></span> <span data-ttu-id="ba72c-116">2 バイト文字セット (DBCS) データを読み込むには、高速読み込みオプションのいずれかを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba72c-116">Loading double-byte character set (DBCS) data requires use of one of the fast load options.</span></span> <span data-ttu-id="ba72c-117">一括挿入用に最適化された高速読み込みデータ アクセス モードの詳細については、「 [OLE DB 変換先](data-flow/ole-db-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-117">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
|<span data-ttu-id="ba72c-118">オプション</span><span class="sxs-lookup"><span data-stu-id="ba72c-118">Option</span></span>|<span data-ttu-id="ba72c-119">説明</span><span class="sxs-lookup"><span data-stu-id="ba72c-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ba72c-120">[テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="ba72c-120">Table or view</span></span>|<span data-ttu-id="ba72c-121">データを OLE DB 変換先のテーブルまたはビューに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-121">Load data into a table or view in the OLE DB destination.</span></span>|  
|<span data-ttu-id="ba72c-122">[テーブルまたはビュー - 高速読み込み]</span><span class="sxs-lookup"><span data-stu-id="ba72c-122">Table or view - fast load</span></span>|<span data-ttu-id="ba72c-123">高速読み込みオプションを使用し、データを OLE DB 変換先のテーブルまたはビューに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-123">Load data into a table or view in the OLE DB destination and use the fast load option.</span></span> <span data-ttu-id="ba72c-124">一括挿入用に最適化された高速読み込みデータ アクセス モードの詳細については、「 [OLE DB 変換先](data-flow/ole-db-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-124">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="ba72c-125">[テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="ba72c-125">Table name or view name variable</span></span>|<span data-ttu-id="ba72c-126">テーブル名またはビュー名を変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-126">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="ba72c-127">**関連情報**: [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="ba72c-127">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="ba72c-128">[テーブル名またはビュー名の変数 - 高速読み込み]</span><span class="sxs-lookup"><span data-stu-id="ba72c-128">Table name or view name variable - fast load</span></span>|<span data-ttu-id="ba72c-129">高速読み込みオプションを使用し、テーブル名またはビュー名を変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-129">Specify the table or view name in a variable, and use the fast load option to load the data.</span></span> <span data-ttu-id="ba72c-130">一括挿入用に最適化された高速読み込みデータ アクセス モードの詳細については、「 [OLE DB 変換先](data-flow/ole-db-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-130">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="ba72c-131">[SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="ba72c-131">SQL command</span></span>|<span data-ttu-id="ba72c-132">SQL クエリを使用し、データを OLE DB 変換先に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-132">Load data into the OLE DB destination by using a SQL query.</span></span>|  
  
 <span data-ttu-id="ba72c-133">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="ba72c-133">**Preview**</span></span>  
 <span data-ttu-id="ba72c-134">**[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="ba72c-134">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="ba72c-135">プレビューでは、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-135">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="ba72c-136">データ アクセス モードの動的オプション</span><span class="sxs-lookup"><span data-stu-id="ba72c-136">Data Access Mode Dynamic Options</span></span>  
 <span data-ttu-id="ba72c-137">**[データ アクセス モード]** の各設定には、その設定に固有のオプションの動的なセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-137">Each of the settings for **Data access mode** displays a dynamic set of options specific to that setting.</span></span> <span data-ttu-id="ba72c-138">次のセクションでは、各 **[データ アクセス モード]** 設定で使用可能な各動的オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-138">The following sections describe each of the dynamic options available for each **Data access mode** setting.</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="ba72c-139">[データ アクセス モード] = [テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="ba72c-139">Data access mode = Table or view</span></span>  
 <span data-ttu-id="ba72c-140">**[テーブル名またはビュー名]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-140">**Name of the table or the view**</span></span>  
 <span data-ttu-id="ba72c-141">データ ソースで使用できるテーブルまたはビューの一覧から、テーブルまたはビューの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-141">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
 <span data-ttu-id="ba72c-142">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-142">**New**</span></span>  
 <span data-ttu-id="ba72c-143">**[テーブルの作成]** ダイアログ ボックスを使用して新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-143">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-144">**[新規作成]** をクリックすると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-144">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="ba72c-145">基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。</span><span class="sxs-lookup"><span data-stu-id="ba72c-145">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="ba72c-146">FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-146">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="ba72c-147">次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-147">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="ba72c-148">詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-148">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
### <a name="data-access-mode--table-or-view---fast-load"></a><span data-ttu-id="ba72c-149">[データ アクセス モード] = [テーブルまたはビュー - 高速読み込み]</span><span class="sxs-lookup"><span data-stu-id="ba72c-149">Data access mode = Table or view - fast load</span></span>  
 <span data-ttu-id="ba72c-150">**[テーブル名またはビュー名]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-150">**Name of the table or view**</span></span>  
 <span data-ttu-id="ba72c-151">この一覧を使用してデータベースからテーブルまたはビューを選択するか、 **[新規作成]** をクリックして新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-151">Select a table or view from the database by using this list, or create a new table by clicking **New**.</span></span>  
  
 <span data-ttu-id="ba72c-152">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-152">**New**</span></span>  
 <span data-ttu-id="ba72c-153">**[テーブルの作成]** ダイアログ ボックスを使用して新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-153">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-154">**[新規作成]** をクリックすると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-154">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="ba72c-155">基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。</span><span class="sxs-lookup"><span data-stu-id="ba72c-155">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="ba72c-156">FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-156">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="ba72c-157">次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-157">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="ba72c-158">詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-158">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="ba72c-159">**[ID を保持する]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-159">**Keep identity**</span></span>  
 <span data-ttu-id="ba72c-160">データが読み込まれるときに ID 値をコピーするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-160">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="ba72c-161">このプロパティは、高速読み取りオプションを指定した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-161">This property is available only with the fast load option.</span></span> <span data-ttu-id="ba72c-162">このプロパティの既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-162">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="ba72c-163">**[NULL を保持する]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-163">**Keep nulls**</span></span>  
 <span data-ttu-id="ba72c-164">データが読み込まれるときに NULL 値をコピーするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-164">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="ba72c-165">このプロパティは、高速読み取りオプションを指定した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-165">This property is available only with the fast load option.</span></span> <span data-ttu-id="ba72c-166">このプロパティの既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-166">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="ba72c-167">**[テーブル ロック]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-167">**Table lock**</span></span>  
 <span data-ttu-id="ba72c-168">読み込み中にテーブルをロックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-168">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="ba72c-169">このプロパティの既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-169">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="ba72c-170">**CHECK 制約**</span><span class="sxs-lookup"><span data-stu-id="ba72c-170">**Check constraints**</span></span>  
 <span data-ttu-id="ba72c-171">データの読み込み中に変換先で制約をチェックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-171">Specify whether the destination checks constraints when it loads data.</span></span> <span data-ttu-id="ba72c-172">このプロパティの既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-172">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="ba72c-173">**[バッチごとの行数]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-173">**Rows per batch**</span></span>  
 <span data-ttu-id="ba72c-174">バッチ内の行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-174">Specify the number of rows in a batch.</span></span> <span data-ttu-id="ba72c-175">このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-175">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-176">このプロパティにカスタム値を割り当てない場合、 **[OLE DB 変換先エディター]** のテキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="ba72c-176">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="ba72c-177">**[挿入コミット サイズの最大値]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-177">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="ba72c-178">高速読み込み操作の実行中に OLE DB 変換先でコミットを試行するバッチ サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-178">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="ba72c-179">値 **0** は、すべての行が処理された後、すべてのデータを 1 つのバッチでコミットすることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-179">The value of **0** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-180">値を **0** にすると、OLE DB 変換先と別のデータ フロー コンポーネントが同じソース テーブルを更新している場合に、実行中のパッケージが応答を停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba72c-180">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="ba72c-181">パッケージが停止しないようにするには、 **[挿入コミット サイズの最大値]** オプションを **2147483647**に設定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-181">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
 <span data-ttu-id="ba72c-182">このプロパティに値を指定すると、変換先で **[挿入コミット サイズの最大値]** 未満の行数のバッチがコミットされます。値を指定しない場合は、現在処理されているバッファー内の残りの行数がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-182">If you provide a value for this property, the destination commits rows in batches that are the smaller of (a) the **Maximum insert commit size**, or (b) the remaining rows in the buffer that is currently being processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-183">変換先で制約が失敗すると、 **[挿入コミット サイズの最大値]** で定義された行数のバッチ全体が失敗します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-183">Any constraint failure at the destination causes the entire batch of rows defined by **Maximum insert commit size** to fail.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="ba72c-184">[データ アクセス モード] = [テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="ba72c-184">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="ba72c-185">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-185">**Variable name**</span></span>  
 <span data-ttu-id="ba72c-186">テーブル名またはビュー名を含む変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-186">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable---fast-load"></a><span data-ttu-id="ba72c-187">[データ アクセス モード] = [テーブル名またはビュー名の変数 - 高速読み込み]</span><span class="sxs-lookup"><span data-stu-id="ba72c-187">Data Access Mode = Table name or view name variable - fast load)</span></span>  
 <span data-ttu-id="ba72c-188">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-188">**Variable name**</span></span>  
 <span data-ttu-id="ba72c-189">テーブル名またはビュー名を含む変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-189">Select the variable that contains the name of the table or view.</span></span>  
  
 <span data-ttu-id="ba72c-190">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-190">**New**</span></span>  
 <span data-ttu-id="ba72c-191">**[テーブルの作成]** ダイアログ ボックスを使用して新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-191">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-192">**[新規作成]** をクリックすると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-192">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="ba72c-193">基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。</span><span class="sxs-lookup"><span data-stu-id="ba72c-193">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="ba72c-194">FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-194">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="ba72c-195">次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-195">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="ba72c-196">詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-196">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="ba72c-197">**[ID を保持する]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-197">**Keep identity**</span></span>  
 <span data-ttu-id="ba72c-198">データが読み込まれるときに ID 値をコピーするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-198">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="ba72c-199">このプロパティは、高速読み取りオプションを指定した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-199">This property is available only with the fast load option.</span></span> <span data-ttu-id="ba72c-200">このプロパティの既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-200">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="ba72c-201">**[NULL を保持する]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-201">**Keep nulls**</span></span>  
 <span data-ttu-id="ba72c-202">データが読み込まれるときに NULL 値をコピーするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-202">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="ba72c-203">このプロパティは、高速読み取りオプションを指定した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba72c-203">This property is available only with the fast load option.</span></span> <span data-ttu-id="ba72c-204">このプロパティの既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-204">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="ba72c-205">**[テーブル ロック]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-205">**Table lock**</span></span>  
 <span data-ttu-id="ba72c-206">読み込み中にテーブルをロックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-206">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="ba72c-207">このプロパティの既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-207">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="ba72c-208">**CHECK 制約**</span><span class="sxs-lookup"><span data-stu-id="ba72c-208">**Check constraints**</span></span>  
 <span data-ttu-id="ba72c-209">タスクで制約をチェックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-209">Specify whether the task checks constraints.</span></span> <span data-ttu-id="ba72c-210">このプロパティの既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="ba72c-210">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="ba72c-211">**[バッチごとの行数]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-211">**Rows per batch**</span></span>  
 <span data-ttu-id="ba72c-212">バッチ内の行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-212">Specify the number of rows in a batch.</span></span> <span data-ttu-id="ba72c-213">このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-213">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-214">このプロパティにカスタム値を割り当てない場合、 **[OLE DB 変換先エディター]** のテキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="ba72c-214">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="ba72c-215">**[挿入コミット サイズの最大値]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-215">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="ba72c-216">高速読み込み操作の実行中に OLE DB 変換先でコミットを試行するバッチ サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-216">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="ba72c-217">既定値の **2147483647** は、すべての行が処理された後、すべてのデータを 1 つのバッチでコミットすることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-217">The default value of **2147483647** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-218">値を **0** にすると、OLE DB 変換先と別のデータ フロー コンポーネントが同じソース テーブルを更新している場合に、実行中のパッケージが応答を停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba72c-218">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="ba72c-219">パッケージが停止しないようにするには、 **[挿入コミット サイズの最大値]** オプションを **2147483647**に設定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-219">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="ba72c-220">[データ アクセス モード] = [SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="ba72c-220">Data access mode = SQL command</span></span>  
 <span data-ttu-id="ba72c-221">**[SQL コマンド テキスト]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-221">**SQL command text**</span></span>  
 <span data-ttu-id="ba72c-222">SQL クエリのテキストを入力し、 **[クエリの作成]** をクリックしてクエリを作成するか、 **[参照]** をクリックしてクエリ テキストを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-222">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba72c-223">OLE DB 変換先ではパラメーターがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ba72c-223">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="ba72c-224">パラメーター化された INSERT ステートメントを実行する必要がある場合は、OLE DB コマンド変換を検討してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-224">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="ba72c-225">詳細については、「 [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba72c-225">For more information, see [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="ba72c-226">**[クエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-226">**Build query**</span></span>  
 <span data-ttu-id="ba72c-227">SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-227">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="ba72c-228">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-228">**Browse**</span></span>  
 <span data-ttu-id="ba72c-229">**[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-229">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="ba72c-230">**[クエリの解析]**</span><span class="sxs-lookup"><span data-stu-id="ba72c-230">**Parse query**</span></span>  
 <span data-ttu-id="ba72c-231">クエリ テキストの構文を検査します。</span><span class="sxs-lookup"><span data-stu-id="ba72c-231">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba72c-232">参照</span><span class="sxs-lookup"><span data-stu-id="ba72c-232">See Also</span></span>  
 <span data-ttu-id="ba72c-233">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ba72c-233">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ba72c-234">[OLE DB 変換先エディター &#40;マッピング] ページ&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="ba72c-234">[OLE DB Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="ba72c-235">[OLE DB 変換先エディター &#40;[エラー出力] ページ&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="ba72c-235">[OLE DB Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="ba72c-236">OLE DB 変換先を使用してデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="ba72c-236">Load Data by Using the OLE DB Destination</span></span>](data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  
