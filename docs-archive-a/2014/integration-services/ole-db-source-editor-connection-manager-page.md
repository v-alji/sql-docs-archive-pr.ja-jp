---
title: '[OLE DB ソースエディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.connection.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6b9d841ff902107847a9d85779af41f476315db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644555"
---
# <a name="ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="df8f4-102">[OLE DB ソース エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="df8f4-102">OLE DB Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="df8f4-103">**[OLE DB ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、ソースの OLE DB 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="df8f4-103">Use the **Connection Manager** page of the **OLE DB Source Editor** dialog box to select the OLE DB connection manager for the source.</span></span> <span data-ttu-id="df8f4-104">さらにこのページを使用して、データベースのテーブルやビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="df8f4-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df8f4-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007 を使用するデータ ソースからデータを読み込むには、OLE DB ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-105">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007, use an OLE DB source.</span></span> <span data-ttu-id="df8f4-106">Excel ソースを使用して Excel 2007 データ ソースからデータを読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="df8f4-106">You cannot use an Excel source to load data from an Excel 2007 data source.</span></span> <span data-ttu-id="df8f4-107">詳細については、「 [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md)」 (OLE DB 接続マネージャーの構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df8f4-107">For more information, see [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md).</span></span>  
>   
>  <span data-ttu-id="df8f4-108">[!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 以前のバージョンを使用するデータ ソースからデータを読み込むには、Excel ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-108">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 or earlier, use an Excel source.</span></span> <span data-ttu-id="df8f4-109">詳細については、「[[Excel ソース エディター] ([接続マネージャー] ページ)](../../2014/integration-services/excel-source-editor-connection-manager-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df8f4-109">For more information, see [Excel Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df8f4-110">`CommandTimeout`OLE DB ソースのプロパティは、 **OLE DB ソースエディター**では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="df8f4-110">The `CommandTimeout` property of the OLE DB source is not available in the **OLE DB Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="df8f4-111">このプロパティの詳細については、「 [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)」(OLE DB のカスタム プロパティ) の Excel ソースのセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="df8f4-111">For more information on this property, see the Excel Source section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="df8f4-112">OLE DB ソースの詳細については、「 [OLE DB Source](data-flow/ole-db-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df8f4-112">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="open-the-ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="df8f4-113">OLE DB ソース エディターを開く ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="df8f4-113">Open the OLE DB Source Editor (Connection Manager Page</span></span>  
  
1.  <span data-ttu-id="df8f4-114">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で、OLE DB ソースを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]パッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-114">Add the OLE DB source to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="df8f4-115">ソース コンポーネントを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df8f4-115">Right-click the source component and when click **Edit**.</span></span>  
  
3.  <span data-ttu-id="df8f4-116">**[接続マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df8f4-116">Click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="df8f4-117">静的オプション</span><span class="sxs-lookup"><span data-stu-id="df8f4-117">Static Options</span></span>  
 <span data-ttu-id="df8f4-118">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-118">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="df8f4-119">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-119">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="df8f4-120">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-120">**New**</span></span>  
 <span data-ttu-id="df8f4-121">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-121">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="df8f4-122">**[データ アクセス モード]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-122">**Data access mode**</span></span>  
 <span data-ttu-id="df8f4-123">ソースからデータを選択する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-123">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="df8f4-124">オプション</span><span class="sxs-lookup"><span data-stu-id="df8f4-124">Option</span></span>|<span data-ttu-id="df8f4-125">説明</span><span class="sxs-lookup"><span data-stu-id="df8f4-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="df8f4-126">[テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="df8f4-126">Table or view</span></span>|<span data-ttu-id="df8f4-127">OLE DB データベースのテーブルまたはビューからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-127">Retrieve data from a table or view in the OLE DB data source.</span></span>|  
|<span data-ttu-id="df8f4-128">[テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="df8f4-128">Table name or view name variable</span></span>|<span data-ttu-id="df8f4-129">テーブル名またはビュー名を変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-129">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="df8f4-130">**関連情報:** [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="df8f4-130">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="df8f4-131">[SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="df8f4-131">SQL command</span></span>|<span data-ttu-id="df8f4-132">SQL クエリを使用して、OLE DB データ ソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-132">Retrieve data from the OLE DB data source by using a SQL query.</span></span>|  
|<span data-ttu-id="df8f4-133">[変数からの SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="df8f4-133">SQL command from variable</span></span>|<span data-ttu-id="df8f4-134">SQL クエリ テキストを変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-134">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="df8f4-135">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="df8f4-135">**Preview**</span></span>  
 <span data-ttu-id="df8f4-136">**[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="df8f4-136">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="df8f4-137">**プレビュー** では、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="df8f4-137">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df8f4-138">データをプレビューするときに、CLR ユーザー定義型を含む列にはデータが表示されません。</span><span class="sxs-lookup"><span data-stu-id="df8f4-138">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="df8f4-139">その代わりに、\<value too big to display> または System.Byte[] が値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="df8f4-139">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="df8f4-140">前者は、SQL OLE DB プロバイダーを使用してデータ ソースにアクセスする場合に表示されます。後者は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client プロバイダーを使用している場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="df8f4-140">The former displays when the data source is accessed using the SQL OLE DB provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="df8f4-141">データ アクセス モードの動的オプション</span><span class="sxs-lookup"><span data-stu-id="df8f4-141">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="df8f4-142">[データ アクセス モード] = [テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="df8f4-142">Data access mode = Table or view</span></span>  
 <span data-ttu-id="df8f4-143">**[テーブル名またはビュー名]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-143">**Name of the table or the view**</span></span>  
 <span data-ttu-id="df8f4-144">データ ソースで使用できるテーブルまたはビューの一覧から、テーブルまたはビューの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-144">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="df8f4-145">[データ アクセス モード] = [テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="df8f4-145">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="df8f4-146">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-146">**Variable name**</span></span>  
 <span data-ttu-id="df8f4-147">テーブル名またはビュー名を含む変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-147">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="df8f4-148">[データ アクセス モード] = [SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="df8f4-148">Data access mode = SQL command</span></span>  
 <span data-ttu-id="df8f4-149">**[SQL コマンド テキスト]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-149">**SQL command text**</span></span>  
 <span data-ttu-id="df8f4-150">SQL クエリのテキストを入力し、 **[クエリの作成]** をクリックしてクエリを作成するか、 **[参照]** をクリックしてクエリ テキストを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-150">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="df8f4-151">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="df8f4-151">**Parameters**</span></span>  
 <span data-ttu-id="df8f4-152">クエリ テキスト内でパラメーターのプレースホルダーとして "?" を使用することにより、</span><span class="sxs-lookup"><span data-stu-id="df8f4-152">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="df8f4-153">パラメーター化クエリを入力した場合は、 **[クエリ パラメーターの設定]** ダイアログ ボックスを使用して、クエリ入力パラメーターをパッケージ変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="df8f4-153">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="df8f4-154">**[クエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-154">**Build query**</span></span>  
 <span data-ttu-id="df8f4-155">SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-155">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="df8f4-156">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-156">**Browse**</span></span>  
 <span data-ttu-id="df8f4-157">**[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-157">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="df8f4-158">**[クエリの解析]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-158">**Parse query**</span></span>  
 <span data-ttu-id="df8f4-159">クエリ テキストの構文を検査します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-159">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="df8f4-160">データ アクセス モードが [変数からの SQL コマンド] の場合</span><span class="sxs-lookup"><span data-stu-id="df8f4-160">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="df8f4-161">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="df8f4-161">**Variable name**</span></span>  
 <span data-ttu-id="df8f4-162">SQL クエリのテキストを含む変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="df8f4-162">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df8f4-163">参照</span><span class="sxs-lookup"><span data-stu-id="df8f4-163">See Also</span></span>  
 <span data-ttu-id="df8f4-164">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="df8f4-164">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="df8f4-165">[OLE DB ソースエディター &#40;列] ページ&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="df8f4-165">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="df8f4-166">[OLE DB ソースエディター &#40;[エラー出力] ページ&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="df8f4-166">[OLE DB Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="df8f4-167">[OLE DB ソースを使用してデータを抽出する](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="df8f4-167">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="df8f4-168">OLE DB 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="df8f4-168">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
