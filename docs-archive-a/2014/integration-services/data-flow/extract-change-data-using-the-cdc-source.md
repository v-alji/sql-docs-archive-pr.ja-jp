---
title: CDC ソースを使用した変更データ抽出 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 604fbafb-15fa-4d11-8487-77d7b626eed8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ef981a22e286f519c9b93b3181b47df43321548b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742442"
---
# <a name="extract-change-data-using-the-cdc-source"></a><span data-ttu-id="e7f09-102">CDC ソースを使用した変更データ抽出</span><span class="sxs-lookup"><span data-stu-id="e7f09-102">Extract Change Data Using the CDC Source</span></span>
  <span data-ttu-id="e7f09-103">CDC ソースを追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの CDC 制御タスクがあらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7f09-103">To add and configure a CDC source, the package must already include at least one Data Flow task and a CDC Control task.</span></span>  
  
 <span data-ttu-id="e7f09-104">CDC 制御タスクの操作の詳細については、「 [CDC 制御タスク](../control-flow/cdc-control-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7f09-104">For more information about the CDC Control task, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="e7f09-105">CDC ソースの詳細については、「 [CDC ソース](cdc-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7f09-105">For more information about the CDC source, see [CDC Source](cdc-source.md).</span></span>  
  
### <a name="to-extract-change-data-using-a-cdc-source"></a><span data-ttu-id="e7f09-106">CDC ソースを使用して変更データを抽出するには</span><span class="sxs-lookup"><span data-stu-id="e7f09-106">To extract change data using a CDC source</span></span>  
  
1.  <span data-ttu-id="e7f09-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e7f09-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e7f09-108">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="e7f09-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e7f09-109">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、CDC ソースをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e7f09-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC source to the design surface.</span></span>  
  
4.  <span data-ttu-id="e7f09-110">CDC ソースをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7f09-110">Double-click the CDC source.</span></span>  
  
5.  <span data-ttu-id="e7f09-111">**[CDC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで、一覧から既存の ADO.NET 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-111">In the **CDC Source Editor** dialog box, on the **Connection Manager** page, select an existing ADO.NET connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="e7f09-112">読み取る変更テーブルが含まれる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの接続であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="e7f09-112">The connection should be to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the change tables to read.</span></span>  
  
6.  <span data-ttu-id="e7f09-113">変更を処理する **[CDC テーブル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-113">Select the **CDC table** where you want to process changes.</span></span>  
  
7.  <span data-ttu-id="e7f09-114">読み取る CDC テーブルの **CDC キャプチャ インスタンス** の名前を選択または入力します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-114">Select or type in the name of the **CDC capture instance** with the CDC table to be read.</span></span>  
  
     <span data-ttu-id="e7f09-115">キャプチャされたソース テーブルには、スキーマの変更によりテーブル定義のシームレスな遷移を処理するためのキャプチャされたインスタンスが 1 ～ 2 個含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="e7f09-115">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="e7f09-116">キャプチャ対象のソース テーブルに複数のキャプチャ インスタンスが定義されている場合は、ここで使用するキャプチャ インスタンスを選択してください。</span><span class="sxs-lookup"><span data-stu-id="e7f09-116">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="e7f09-117">[schema].[table] という形式のテーブルの既定のキャプチャ インスタンス名は \<schema>_\<table> ですが、使用される実際のキャプチャ インスタンス名は異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7f09-117">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="e7f09-118">読み取り元の実際のテーブルは、**cdc .\<capture-instance>_CT** という形式の CDC テーブルです。</span><span class="sxs-lookup"><span data-stu-id="e7f09-118">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
8.  <span data-ttu-id="e7f09-119">処理上のニーズに最も適した処理モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-119">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="e7f09-120">オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e7f09-120">The possible options are:</span></span>  
  
    -   <span data-ttu-id="e7f09-121">**[すべて]** : **[更新前]** の値なしで、現在の CDC 範囲内の変更を返します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-121">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
    -   <span data-ttu-id="e7f09-122">**[古い値を含むすべて]** : 古い値 ( **[更新前]** ) を含め、現在の CDC 処理範囲内の変更を返します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-122">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="e7f09-123">更新操作ごとに、2 つの行 (更新前の値の行と更新後の値の行) が存在することになります。</span><span class="sxs-lookup"><span data-stu-id="e7f09-123">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
    -   <span data-ttu-id="e7f09-124">**[差分]** : 現在の CDC 処理範囲内で変更された、ソース行あたり 1 つの変更行のみを返します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-124">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="e7f09-125">ソース行が複数回更新された場合は、変更が結合されたうえで生成されます (たとえば、挿入と更新が 1 回の更新として、または更新と削除が 1 回の削除として、結合されたうえで生成されることがあります)。</span><span class="sxs-lookup"><span data-stu-id="e7f09-125">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="e7f09-126">[差分] 変更処理モードで作業する場合は、1 つのソース行が複数の出力に出現するため、変更を削除、挿入、および更新の各出力に分割し、並行処理することができます。</span><span class="sxs-lookup"><span data-stu-id="e7f09-126">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
    -   <span data-ttu-id="e7f09-127">**[更新マスクを含む差分]** : このモードは通常の [差分] モードと似ていますが、 **__$\<column-name>\__Changed** という名前のパターンを持つブール型の列も追加されます。これは、現在の変更行の変更された列を示します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-127">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
    -   <span data-ttu-id="e7f09-128">**[結合を含む差分]** : このモードは通常の [結合] モードと似ていますが、挿入操作と更新操作が 1 つの結合操作 (UPSERT) に結合されます。</span><span class="sxs-lookup"><span data-stu-id="e7f09-128">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
9. <span data-ttu-id="e7f09-129">現在の CDC コンテキストの CDC 状態を保持する SSIS 文字列パッケージ変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-129">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="e7f09-130">CDC 状態変数の詳細については、「 [状態変数の定義](define-a-state-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7f09-130">For more information about the CDC state variable, see [Define a State Variable](define-a-state-variable.md).</span></span>  
  
10. <span data-ttu-id="e7f09-131">**__$reprocessing** という特別な出力列を作成する場合は、 **[再処理インジケーター列を含める]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e7f09-131">Select the **Include reprocessing indicator column** check box to create a special output column called **__$reprocessing**.</span></span> <span data-ttu-id="e7f09-132">CDC 処理範囲が初期処理範囲 (初期読み込みの期間に対応する LSN の範囲) と重なる場合か、CDC 処理範囲が前の実行でのエラーの後に再処理される場合、この列の値は **true** になります。</span><span class="sxs-lookup"><span data-stu-id="e7f09-132">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="e7f09-133">このインジケーター列を使用すると、SSIS 開発者は変更を再処理するときに、エラーを別々に処理できます (たとえば、非既存行の削除やキーの重複により失敗した挿入などの操作を無視できます)。</span><span class="sxs-lookup"><span data-stu-id="e7f09-133">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
     <span data-ttu-id="e7f09-134">詳細については、「 [CDC ソースのカスタム プロパティ](cdc-source-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7f09-134">For more information, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
11. <span data-ttu-id="e7f09-135">外部列と出力列間のマッピングを更新するには、 **[列]** をクリックし、 **[外部列]** 一覧にある別の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-135">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
12. <span data-ttu-id="e7f09-136">必要に応じて、 **[出力列]** 一覧の値を削除し、出力列の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="e7f09-136">Optionally update the values of the output columns by deleting values in the **Output Column** list.</span></span>  
  
13. <span data-ttu-id="e7f09-137">エラー出力を構成するには、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7f09-137">To configure the error output, click **Error Output**.</span></span>  
  
14. <span data-ttu-id="e7f09-138">**[プレビュー]** をクリックすると、CDC ソースによって抽出されるデータを最大 200 行表示できます。</span><span class="sxs-lookup"><span data-stu-id="e7f09-138">You can click **Preview** to view up to 200 rows of data extracted by the CDC source.</span></span>  
  
15. <span data-ttu-id="e7f09-139">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7f09-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f09-140">参照</span><span class="sxs-lookup"><span data-stu-id="e7f09-140">See Also</span></span>  
 <span data-ttu-id="e7f09-141">[CDC ソース エディター &#40;[接続マネージャー] ページ&#41;](../cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="e7f09-141">[CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="e7f09-142">[[CDC ソース エディター] ([列] ページ)](../cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e7f09-142">[CDC Source Editor &#40;Columns Page&#41;](../cdc-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e7f09-143">[CDC ソース エディター &#40;[エラー出力] ページ&#41;](../cdc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="e7f09-143">[CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md)</span></span>  
  
  
