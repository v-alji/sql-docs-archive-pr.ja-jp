---
title: '[CDC ソースエディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.connection.f1
ms.assetid: 304e6717-e160-4a7b-a06f-32182449fef8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b0ed4792f13006bb9013771c69053b04539bc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644592"
---
# <a name="cdc-source-editor-connection-manager-page"></a><span data-ttu-id="388fe-102">[CDC ソース エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="388fe-102">CDC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="388fe-103">**[CDC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、CDC ソースが変更行を読み取る [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] データベース (CDC データベース) の ADO.NET 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="388fe-103">Use the **Connection Manager** page of the **CDC Source Editor** dialog box to select the ADO.NET connection manager for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database that the CDC source reads change rows from (the CDC database).</span></span> <span data-ttu-id="388fe-104">CDC データベースを選択した後で、キャプチャされたテーブルをデータベースで選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="388fe-104">Once the CDC database is selected you need to select a captured table in the database.</span></span>  
  
 <span data-ttu-id="388fe-105">CDC ソースの詳細については、「 [CDC ソース](data-flow/cdc-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="388fe-105">For more information about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="388fe-106">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="388fe-106">Task List</span></span>  
 <span data-ttu-id="388fe-107">**[CDC ソース エディター] の [接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="388fe-107">**To open the CDC Source Editor Connection Manager Page**</span></span>  
  
1.  <span data-ttu-id="388fe-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、CDC ソースを含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="388fe-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="388fe-109">**[データ フロー]** タブで、CDC ソースをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="388fe-109">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="388fe-110">**[CDC ソース エディター]** で、 **[接続マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="388fe-110">In the **CDC Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="388fe-111">オプション</span><span class="sxs-lookup"><span data-stu-id="388fe-111">Options</span></span>  
 <span data-ttu-id="388fe-112">**ADO.NET 接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="388fe-112">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="388fe-113">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="388fe-113">Select an existing connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="388fe-114">選択した変更テーブルが存在する、CDC に対応した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースへの接続である必要があります。</span><span class="sxs-lookup"><span data-stu-id="388fe-114">The connection must be to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that is enabled for CDC and where the selected change table is located.</span></span>  
  
 <span data-ttu-id="388fe-115">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="388fe-115">**New**</span></span>  
 <span data-ttu-id="388fe-116">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="388fe-116">Click **New**.</span></span> <span data-ttu-id="388fe-117">新しい接続マネージャーを作成できる **[ADO.NET 接続マネージャーの構成エディター]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="388fe-117">The **Configure ADO.NET Connection Manager Editor** dialog box opens where you can create a new connection manager</span></span>  
  
 <span data-ttu-id="388fe-118">**[CDC テーブル]**</span><span class="sxs-lookup"><span data-stu-id="388fe-118">**CDC Table**</span></span>  
 <span data-ttu-id="388fe-119">読み取って、処理のために下流の SSIS コンポーネントに渡す、キャプチャされた変更の含まれる CDC ソース テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="388fe-119">Select the CDC source table that contains the captured changes that you want read and feed to downstream SSIS components for processing.</span></span>  
  
 <span data-ttu-id="388fe-120">**[キャプチャ インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="388fe-120">**Capture instance**</span></span>  
 <span data-ttu-id="388fe-121">読み取る CDC テーブルの CDC キャプチャ インスタンスの名前を選択または入力します。</span><span class="sxs-lookup"><span data-stu-id="388fe-121">Select or type in the name of the CDC capture instance with the CDC table to be read.</span></span>  
  
 <span data-ttu-id="388fe-122">キャプチャされたソース テーブルには、スキーマの変更によりテーブル定義のシームレスな遷移を処理するためのキャプチャされたインスタンスが 1 ～ 2 個含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="388fe-122">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="388fe-123">キャプチャ対象のソース テーブルに複数のキャプチャ インスタンスが定義されている場合は、ここで使用するキャプチャ インスタンスを選択してください。</span><span class="sxs-lookup"><span data-stu-id="388fe-123">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="388fe-124">[schema].[table] という形式のテーブルの既定のキャプチャ インスタンス名は \<schema>_\<table> ですが、使用される実際のキャプチャ インスタンス名は異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="388fe-124">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="388fe-125">読み取り元の実際のテーブルは、**cdc .\<capture-instance>_CT** という形式の CDC テーブルです。</span><span class="sxs-lookup"><span data-stu-id="388fe-125">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
 <span data-ttu-id="388fe-126">**[CDC 処理モード]**</span><span class="sxs-lookup"><span data-stu-id="388fe-126">**CDC Processing Mode**</span></span>  
 <span data-ttu-id="388fe-127">処理上のニーズに最も適した処理モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="388fe-127">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="388fe-128">オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="388fe-128">The possible options are:</span></span>  
  
-   <span data-ttu-id="388fe-129">**[すべて]** : **[更新前]** の値なしで、現在の CDC 範囲内の変更を返します。</span><span class="sxs-lookup"><span data-stu-id="388fe-129">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
-   <span data-ttu-id="388fe-130">**[古い値を含むすべて]** : 古い値 ( **[更新前]** ) を含め、現在の CDC 処理範囲内の変更を返します。</span><span class="sxs-lookup"><span data-stu-id="388fe-130">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="388fe-131">更新操作ごとに、2 つの行 (更新前の値の行と更新後の値の行) が存在することになります。</span><span class="sxs-lookup"><span data-stu-id="388fe-131">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
-   <span data-ttu-id="388fe-132">**[差分]** : 現在の CDC 処理範囲内で変更された、ソース行あたり 1 つの変更行のみを返します。</span><span class="sxs-lookup"><span data-stu-id="388fe-132">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="388fe-133">ソース行が複数回更新された場合は、変更が結合されたうえで生成されます (たとえば、挿入と更新が 1 回の更新として、または更新と削除が 1 回の削除として、結合されたうえで生成されることがあります)。</span><span class="sxs-lookup"><span data-stu-id="388fe-133">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="388fe-134">[差分] 変更処理モードで作業する場合は、1 つのソース行が複数の出力に出現するため、変更を削除、挿入、および更新の各出力に分割し、並行処理することができます。</span><span class="sxs-lookup"><span data-stu-id="388fe-134">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
-   <span data-ttu-id="388fe-135">**[更新マスクを含む差分]** : このモードは通常の [差分] モードと似ていますが、 **__$\<column-name>\__Changed** という名前のパターンを持つブール型の列も追加されます。これは、現在の変更行の変更された列を示します。</span><span class="sxs-lookup"><span data-stu-id="388fe-135">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
-   <span data-ttu-id="388fe-136">**[結合を含む差分]** : このモードは通常の [結合] モードと似ていますが、挿入操作と更新操作が 1 つの結合操作 (UPSERT) に結合されます。</span><span class="sxs-lookup"><span data-stu-id="388fe-136">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="388fe-137">どの差分変更オプションを使用する場合も、ソース テーブルに主キーまたは一意のインデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="388fe-137">For all Net change options, the source table must have a primary key or unique index.</span></span> <span data-ttu-id="388fe-138">主キーまたは一意のインデックスがないテーブルに対しては、 **[すべて]** オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="388fe-138">For tables without a primary key or unique indes, you must yse the **All** option.</span></span>  
  
 <span data-ttu-id="388fe-139">**[CDC 状態を含む変数]**</span><span class="sxs-lookup"><span data-stu-id="388fe-139">**Variable containing the CDC state**</span></span>  
 <span data-ttu-id="388fe-140">現在の CDC コンテキストの CDC 状態を保持する SSIS 文字列パッケージ変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="388fe-140">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="388fe-141">CDC 状態変数の詳細については、「 [状態変数の定義](data-flow/define-a-state-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="388fe-141">For more information about the CDC state variable, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
 <span data-ttu-id="388fe-142">**[再処理インジケーター列を含める]**</span><span class="sxs-lookup"><span data-stu-id="388fe-142">**Include reprocessing indicator column**</span></span>  
 <span data-ttu-id="388fe-143">**__$reprocessing**という特別な出力列を作成する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="388fe-143">Select this check box to create a special output column called **__$reprocessing**.</span></span>  
  
 <span data-ttu-id="388fe-144">CDC 処理範囲が初期処理範囲 (初期読み込みの期間に対応する LSN の範囲) と重なる場合か、CDC 処理範囲が前の実行でのエラーの後に再処理される場合、この列の値は **true** になります。</span><span class="sxs-lookup"><span data-stu-id="388fe-144">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="388fe-145">このインジケーター列を使用すると、SSIS 開発者は変更を再処理するときに、エラーを別々に処理できます (たとえば、非既存行の削除やキーの重複により失敗した挿入などの操作を無視できます)。</span><span class="sxs-lookup"><span data-stu-id="388fe-145">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
 <span data-ttu-id="388fe-146">詳細については、「 [CDC ソースのカスタム プロパティ](data-flow/cdc-source-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="388fe-146">For more information, see [CDC Source Custom Properties](data-flow/cdc-source-custom-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388fe-147">参照</span><span class="sxs-lookup"><span data-stu-id="388fe-147">See Also</span></span>  
 <span data-ttu-id="388fe-148">[[CDC ソース エディター] ([列] ページ)](../../2014/integration-services/cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="388fe-148">[CDC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="388fe-149">[CDC ソース エディター &#40;[エラー出力] ページ&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="388fe-149">[CDC Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)</span></span>  
  
  
