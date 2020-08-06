---
title: CSV ファイルへのエクスポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 68ec746e-8c82-47f5-8c3d-dbe403a441e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 635d5904acf6e616378f5423bfbaf4cf5390fa9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631619"
---
# <a name="exporting-to-a-csv-file-report-builder-and-ssrs"></a><span data-ttu-id="c55b7-102">CSV ファイルへのエクスポート (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c55b7-102">Exporting to a CSV File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c55b7-103">CSV (コンマ区切り) 表示拡張機能では、レポートのデータを平面的に表して、標準化されたプレーンテキスト形式でレポートを表示します。プレーンテキスト形式のレポートは、多くのアプリケーションで簡単に読み取ったり変換したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-103">The Comma-Separated Value (CSV) rendering extension renders reports as a flattened representation of data from a report in a standardized, plain-text format that is easily readable and exchangeable with many applications.</span></span>  
  
 <span data-ttu-id="c55b7-104">CSV 表示拡張機能は、文字による区切り記号を使用してフィールドと行を分けます。この区切り記号には、コンマ以外の文字を使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-104">The CSV rendering extension uses a string character delimiter to separate fields and rows, with the string character delimiter configurable to be a character other than a comma.</span></span> <span data-ttu-id="c55b7-105">エクスポートされたファイルは、 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] などのスプレッドシート プログラムで開いたり、他のプログラムのインポート形式として使用できます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-105">The resulting file can be opened in a spreadsheet program like [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or used as an import format for other programs.</span></span> <span data-ttu-id="c55b7-106">エクスポートされたレポートは .csv ファイルとなり、MIME の種類として `text/csv` を返します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-106">The exported report becomes a .csv file, and returns a MIME type of `text/csv`.</span></span>  
  
 <span data-ttu-id="c55b7-107">グラフ、データ バー、スパークライン、ゲージ、インジケーターに関連するデータを [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]で操作する場合は、レポートを CSV ファイルにエクスポートし、そのファイルを [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel で開きます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-107">If you want to work with data related to charts, data bars, sparklines, gauges, and indicators in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)], export the report to a CSV file, and then open the file in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="csv-rendering"></a><a name="CSVRendering"></a> <span data-ttu-id="c55b7-108">CSV の表示</span><span class="sxs-lookup"><span data-stu-id="c55b7-108">CSV Rendering</span></span>  
 <span data-ttu-id="c55b7-109">既定の設定を使用して表示された場合、CSV 形式のレポートは次のような特徴のレポートになります。</span><span class="sxs-lookup"><span data-stu-id="c55b7-109">When rendered using the default settings, a CSV report has the following characteristics:</span></span>  
  
-   <span data-ttu-id="c55b7-110">既定のフィールド区切り記号は、コンマ (,) です。</span><span class="sxs-lookup"><span data-stu-id="c55b7-110">The default field delimiter string is a comma (,).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c55b7-111">フィールド区切り記号を任意の文字 (タブなど) に変更するには、デバイス情報設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-111">You can change the field delimiter to any character that you want, including TAB, by changing the device information settings.</span></span> <span data-ttu-id="c55b7-112">詳細については、「 [CSV Device Information Settings](../csv-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c55b7-112">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
-   <span data-ttu-id="c55b7-113">レコードの区切り記号は、キャリッジリターンとラインフィード ( \<cr> \<lf> ) です。</span><span class="sxs-lookup"><span data-stu-id="c55b7-113">The record delimiter string is the carriage return and line feed (\<cr>\<lf>).</span></span>  
  
-   <span data-ttu-id="c55b7-114">テキスト修飾子は、二重引用符 (") です。</span><span class="sxs-lookup"><span data-stu-id="c55b7-114">The text qualifier string is a quotation mark (").</span></span>  
  
     <span data-ttu-id="c55b7-115">CSV レンダラーは、すべてのテキスト文字列の周りに修飾子を追加するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-115">The CSV renderer does not add qualifiers around all text strings.</span></span> <span data-ttu-id="c55b7-116">テキスト修飾子が追加されるのは、値に区切り文字が含まれている場合、または値に改行が含まれている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="c55b7-116">Text qualifiers are added only when the value contains the delimiter character or when the value has a line break.</span></span>  
  
-   <span data-ttu-id="c55b7-117">テキストに区切り記号や修飾子が埋め込まれている場合は、テキスト修飾子でテキストが囲まれ、テキスト中に埋め込まれた修飾子は 2 つ重ねて使用されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-117">If the text contains an embedded delimiter string or qualifier string, the text qualifier is placed around the text, and the embedded qualifier strings are doubled.</span></span>  
  
-   <span data-ttu-id="c55b7-118">書式およびレイアウトは無視されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-118">Formatting and layout are ignored.</span></span>  
  
 <span data-ttu-id="c55b7-119">表示中は次のアイテムが無視されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-119">The following items are ignored during rendering:</span></span>  
  
-   <span data-ttu-id="c55b7-120">ページ ヘッダー</span><span class="sxs-lookup"><span data-stu-id="c55b7-120">Page header</span></span>  
  
-   <span data-ttu-id="c55b7-121">ページ フッター</span><span class="sxs-lookup"><span data-stu-id="c55b7-121">Page footer</span></span>  
  
-   <span data-ttu-id="c55b7-122">カスタム レポート アイテム</span><span class="sxs-lookup"><span data-stu-id="c55b7-122">Custom report items</span></span>  
  
-   <span data-ttu-id="c55b7-123">行</span><span class="sxs-lookup"><span data-stu-id="c55b7-123">Line</span></span>  
  
-   <span data-ttu-id="c55b7-124">Image</span><span class="sxs-lookup"><span data-stu-id="c55b7-124">Image</span></span>  
  
-   <span data-ttu-id="c55b7-125">Rectangle</span><span class="sxs-lookup"><span data-stu-id="c55b7-125">Rectangle</span></span>  
  
-   <span data-ttu-id="c55b7-126">自動集計</span><span class="sxs-lookup"><span data-stu-id="c55b7-126">Automatic subtotals</span></span>  
  
 <span data-ttu-id="c55b7-127">その他のレポート アイテムは、まず先頭から末尾に並べ替えられてから左から右に向かって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-127">The remaining report items are sorted, from top to bottom, then left to right.</span></span> <span data-ttu-id="c55b7-128">その後、各アイテムが列に生成されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-128">Each item is then rendered to a column.</span></span> <span data-ttu-id="c55b7-129">レポートに一覧やテーブルなどの入れ子になったアイテムがある場合は、親アイテムが各レコードに繰り返し使用されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-129">If the report has nested data items like lists or tables, the parent items are repeated in each record.</span></span>  
  
 <span data-ttu-id="c55b7-130">次の表では、表示した際のレポート アイテムの外観について説明します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-130">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="c55b7-131">Item</span><span class="sxs-lookup"><span data-stu-id="c55b7-131">Item</span></span>|<span data-ttu-id="c55b7-132">表示動作</span><span class="sxs-lookup"><span data-stu-id="c55b7-132">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="c55b7-133">テキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="c55b7-133">Text box</span></span>|<span data-ttu-id="c55b7-134">テキスト ボックスの内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-134">Renders the contents of the text box.</span></span> <span data-ttu-id="c55b7-135">既定のモードでは、アイテムは、そのアイテムの書式設定プロパティに基づいて書式が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-135">In default mode, items are formatted based on the item's formatting properties.</span></span> <span data-ttu-id="c55b7-136">準拠モードでは、デバイス情報設定によって書式を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-136">In compliant mode, formatting can be changed by device information settings.</span></span> <span data-ttu-id="c55b7-137">CSV 表示モードの詳細については、以下の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c55b7-137">For more information about CSV rendering modes, see below.</span></span>|  
|<span data-ttu-id="c55b7-138">テーブル</span><span class="sxs-lookup"><span data-stu-id="c55b7-138">Table</span></span>|<span data-ttu-id="c55b7-139">テーブルを展開して表示します。最も詳細なレベルでの各行と列に対応した、行と列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-139">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="c55b7-140">集計の行と列には、列見出しまたは行見出しは付けられません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-140">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="c55b7-141">詳細レポートはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-141">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="c55b7-142">Matrix</span><span class="sxs-lookup"><span data-stu-id="c55b7-142">Matrix</span></span>|<span data-ttu-id="c55b7-143">マトリックスを展開して表示します。最も詳細なレベルでの各行と列に対応した、行と列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-143">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="c55b7-144">集計の行と列には、列見出しまたは行見出しは付けられません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-144">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="c55b7-145">List</span><span class="sxs-lookup"><span data-stu-id="c55b7-145">List</span></span>|<span data-ttu-id="c55b7-146">一覧の詳細行またはインスタンスそれぞれに対応するレコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-146">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="c55b7-147">サブレポート</span><span class="sxs-lookup"><span data-stu-id="c55b7-147">Subreport</span></span>|<span data-ttu-id="c55b7-148">親アイテムは、コンテンツのインスタンスごとに繰り返し表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-148">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="c55b7-149">グラフ</span><span class="sxs-lookup"><span data-stu-id="c55b7-149">Chart</span></span>|<span data-ttu-id="c55b7-150">それぞれのグラフ値の行およびメンバー ラベルを作成することにより表示します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-150">Renders by creating a row for each chart value and member labels.</span></span> <span data-ttu-id="c55b7-151">階層内の系列およびカテゴリのラベルは、フラット化され、グラフ値の行内に含まれています。</span><span class="sxs-lookup"><span data-stu-id="c55b7-151">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="c55b7-152">データ バー</span><span class="sxs-lookup"><span data-stu-id="c55b7-152">Data bar</span></span>|<span data-ttu-id="c55b7-153">グラフのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-153">Renders like a chart.</span></span> <span data-ttu-id="c55b7-154">通常、データ バーには階層またはラベルは含まれません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-154">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="c55b7-155">スパークライン</span><span class="sxs-lookup"><span data-stu-id="c55b7-155">Sparkline</span></span>|<span data-ttu-id="c55b7-156">グラフのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-156">Renders like a chart.</span></span> <span data-ttu-id="c55b7-157">通常、スパークラインには階層またはラベルは含まれません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-157">Typically, a sparkline does not  do not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="c55b7-158">ゲージ</span><span class="sxs-lookup"><span data-stu-id="c55b7-158">Gauge</span></span>|<span data-ttu-id="c55b7-159">線形スケールの最小値/最大値、範囲の開始値/終了値、およびポインターの値を含む単一のレコードとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-159">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="c55b7-160">インジケーター</span><span class="sxs-lookup"><span data-stu-id="c55b7-160">Indicator</span></span>|<span data-ttu-id="c55b7-161">アクティブな状態名、使用可能な状態、およびデータ値を持つ単一のレコードとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-161">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="c55b7-162">マップ</span><span class="sxs-lookup"><span data-stu-id="c55b7-162">Map</span></span>|<span data-ttu-id="c55b7-163">マップ レイヤーのマップ メンバーごとにラベルと値のある行を表示します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-163">Renders a row with the labels and values for each map member of a map layer.</span></span><br /><br /> <span data-ttu-id="c55b7-164">マップに複数のレイヤーがある場合、同じマップ データ領域を使用しているか、異なるマップ データ領域を使用しているかによって行の値が変化します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-164">If the map has multiple layers the values in the rows varies depending on whether the map layers use the same or different map data regions.</span></span> <span data-ttu-id="c55b7-165">複数のマップ レイヤーが同じデータ領域を使用している場合、行にはすべてのレイヤーからのデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-165">If multiple map layers use the same data region, the rows contain data from all layers.</span></span>|  
  
### <a name="hierarchical-and-grouped-data"></a><span data-ttu-id="c55b7-166">階層データとグループ化データ</span><span class="sxs-lookup"><span data-stu-id="c55b7-166">Hierarchical and Grouped Data</span></span>  
 <span data-ttu-id="c55b7-167">階層データとグループ化データは、CSV 形式で表示するためにフラット化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c55b7-167">Hierarchical and grouped data must be flattened in order to be represented in the CSV format.</span></span>  
  
 <span data-ttu-id="c55b7-168">表示拡張機能では、レポートをフラット化して、データ領域内で入れ子になっているグループを表すツリー構造にします。</span><span class="sxs-lookup"><span data-stu-id="c55b7-168">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="c55b7-169">レポートをフラット化する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c55b7-169">To flatten the report:</span></span>  
  
-   <span data-ttu-id="c55b7-170">行階層がフラット化されてから列階層がフラット化されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-170">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="c55b7-171">列が並べ替えられます。本文中のテキスト ボックスが左から右、上から下に並べ替えられた後、データ領域が左から右、上から下に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-171">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="c55b7-172">データ領域内の列が、コーナーのメンバー、行階層メンバー、列階層メンバー、セルの順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-172">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="c55b7-173">ピア データ領域は、一般的なデータ領域または動的な先祖を共有する、データ領域または動的グループです。</span><span class="sxs-lookup"><span data-stu-id="c55b7-173">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="c55b7-174">ピア データがフラットなツリーの分岐で識別されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-174">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="c55b7-175">詳細については、「 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c55b7-175">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="renderer-modes"></a><a name="RenderingModes"></a> <span data-ttu-id="c55b7-176">表示モード</span><span class="sxs-lookup"><span data-stu-id="c55b7-176">Renderer Modes</span></span>  
 <span data-ttu-id="c55b7-177">CSV 表示拡張機能は 2 つのモードで操作できます。1 つは Excel に最適なモード、もう 1 つは、RFC 4180 の CSV 仕様に厳密に準拠することが要求されるサードパーティのアプリケーションに最適なモードです。</span><span class="sxs-lookup"><span data-stu-id="c55b7-177">The CSV rendering extension can operate in two modes: one is optimized for Excel and the other is optimized for third-party applications that require strict CSV compliance to the CSV specification in RFC 4180.</span></span> <span data-ttu-id="c55b7-178">使用するモードによって、ピア データ領域の処理は異なります。</span><span class="sxs-lookup"><span data-stu-id="c55b7-178">Depending on which mode you use, peer data regions are handled differently.</span></span>  
  
### <a name="default-mode"></a><span data-ttu-id="c55b7-179">既定モード</span><span class="sxs-lookup"><span data-stu-id="c55b7-179">Default Mode</span></span>  
 <span data-ttu-id="c55b7-180">既定のモードは Excel 向けに最適化されたモードです。</span><span class="sxs-lookup"><span data-stu-id="c55b7-180">The default mode is optimized for Excel.</span></span> <span data-ttu-id="c55b7-181">既定のモードで表示された場合、CSV 表示データの複数のセクションが含まれた CSV ファイルとしてレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-181">When rendered in default mode, the report is rendered as a CSV file with multiple sections of CSV-rendered data.</span></span> <span data-ttu-id="c55b7-182">各ピア データ領域は空の行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-182">Each peer data region is delimited by an empty line.</span></span> <span data-ttu-id="c55b7-183">レポート本文内のピア データ領域は、CSV ファイル内で個別のデータ ブロックとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-183">Peer data regions within the report body are rendered as separate blocks of data within the CSV file.</span></span> <span data-ttu-id="c55b7-184">その結果、CSV ファイル内は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c55b7-184">The result is a CSV file in which:</span></span>  
  
-   <span data-ttu-id="c55b7-185">レポート本文内の個々のテキスト ボックスは、CSV ファイル内の最初のデータ ブロックとして 1 回表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-185">Individual text boxes within the report body are rendered once as the first block of data within the CSV file.</span></span>  
  
-   <span data-ttu-id="c55b7-186">レポート本文内の最上位レベルのピア データ領域はそれぞれ、独自のデータ ブロック内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-186">Each top-level peer data region in the report body is rendered in its own data block.</span></span>  
  
-   <span data-ttu-id="c55b7-187">入れ子になったデータ領域は、同じデータ ブロックで対角線上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-187">Nested data regions are rendered diagonally into the same data block.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="c55b7-188">書式設定</span><span class="sxs-lookup"><span data-stu-id="c55b7-188">Formatting</span></span>  
 <span data-ttu-id="c55b7-189">数値は、書式設定された状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-189">Numeric values are rendered in their formatted state.</span></span> <span data-ttu-id="c55b7-190">Excel は、通貨、パーセンテージ、日付などの書式設定された数値を認識できます。また、CSV ファイルをインポートする場合、セルの書式を適切に設定します。</span><span class="sxs-lookup"><span data-stu-id="c55b7-190">Excel can recognize formatted numeric values, such as currency, percentage and date, and format the cells appropriately when importing the CSV file.</span></span>  
  
### <a name="compliant-mode"></a><span data-ttu-id="c55b7-191">準拠モード</span><span class="sxs-lookup"><span data-stu-id="c55b7-191">Compliant Mode</span></span>  
 <span data-ttu-id="c55b7-192">準拠モードでは、サードパーティのアプリケーション向けにデータの形式が最適化されます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-192">Compliant mode is optimized for third-party applications.</span></span>  
  
#### <a name="data-regions"></a><span data-ttu-id="c55b7-193">データ領域</span><span class="sxs-lookup"><span data-stu-id="c55b7-193">Data Regions</span></span>  
 <span data-ttu-id="c55b7-194">ファイルの最初の行のみに列ヘッダーが含まれます。また、各行の列数は同じになります。</span><span class="sxs-lookup"><span data-stu-id="c55b7-194">Only the first row of the file contains the column headers and each row has the same number of columns.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="c55b7-195">書式設定</span><span class="sxs-lookup"><span data-stu-id="c55b7-195">Formatting</span></span>  
 <span data-ttu-id="c55b7-196">値の書式は設定されていません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-196">Values are unformatted.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="c55b7-197">双</span><span class="sxs-lookup"><span data-stu-id="c55b7-197">Interactivity</span></span>  
 <span data-ttu-id="c55b7-198">このレンダラーによって生成されたどちらの CSV 形式でも、対話性はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-198">Interactivity is not supported by either CSV formats generated by this renderer.</span></span> <span data-ttu-id="c55b7-199">次の対話型要素は表示されません。</span><span class="sxs-lookup"><span data-stu-id="c55b7-199">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="c55b7-200">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="c55b7-200">Hyperlinks</span></span>  
  
-   <span data-ttu-id="c55b7-201">表示/非表示</span><span class="sxs-lookup"><span data-stu-id="c55b7-201">Show or Hide</span></span>  
  
-   <span data-ttu-id="c55b7-202">ドキュメント マップ</span><span class="sxs-lookup"><span data-stu-id="c55b7-202">Document Map</span></span>  
  
-   <span data-ttu-id="c55b7-203">ドリルスルー リンクまたはクリックスルー リンク</span><span class="sxs-lookup"><span data-stu-id="c55b7-203">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="c55b7-204">エンド ユーザー並べ替え</span><span class="sxs-lookup"><span data-stu-id="c55b7-204">End user sort</span></span>  
  
-   <span data-ttu-id="c55b7-205">固定ヘッダー</span><span class="sxs-lookup"><span data-stu-id="c55b7-205">Fixes headers</span></span>  
  
-   <span data-ttu-id="c55b7-206">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="c55b7-206">Bookmarks</span></span>  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="c55b7-207">デバイス情報の設定</span><span class="sxs-lookup"><span data-stu-id="c55b7-207">Device Information Settings</span></span>  
 <span data-ttu-id="c55b7-208">このレンダラーでは、デバイス情報設定を変更することで既定の設定の一部を変更できます。たとえば、表示モード、区切り記号として使用する文字、テキスト修飾子の既定の文字として使用する文字などを変更できます。</span><span class="sxs-lookup"><span data-stu-id="c55b7-208">You can change some default settings for this renderer, including which mode to render in, which characters to use as delimiters and which characters to use as the text qualifier default string, by changing the device information settings.</span></span> <span data-ttu-id="c55b7-209">詳細については、「 [CSV Device Information Settings](../csv-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c55b7-209">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="c55b7-210">参照</span><span class="sxs-lookup"><span data-stu-id="c55b7-210">See Also</span></span>  
 <span data-ttu-id="c55b7-211">[Reporting Services &#40;レポートビルダーおよび SSRS&#41;での改ページ](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c55b7-211">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c55b7-212">[レポートビルダーおよび SSRS&#41;&#40;レンダリング動作](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c55b7-212">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c55b7-213">[さまざまなレポート表示拡張機能の対話機能 &#40;レポートビルダーと SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="c55b7-213">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="c55b7-214">[レポートビルダーおよび SSRS&#41;&#40;レポートアイテムのレンダリング](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c55b7-214">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c55b7-215">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c55b7-215">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
