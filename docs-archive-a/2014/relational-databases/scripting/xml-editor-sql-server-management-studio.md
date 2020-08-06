---
title: XML エディター
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.editorxml.f1
- sql12.swb.xmleditor.f1
- vs.xmleditor
- sql12.swb.editor.xml.f1
helpviewer_keywords:
- XML Designer [SQL Server Management Studio]
ms.assetid: 0824a5ce-e67b-4b53-98d9-d371faf2d23c
author: rothja
ms.author: jroth
ms.openlocfilehash: b7c3bbbda4f5a31c4d83b559c1aa623ca2aff89f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644413"
---
# <a name="xml-editor-sql-server-management-studio"></a><span data-ttu-id="5199d-102">XML エディター (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5199d-102">XML Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="5199d-103">XML スキーマ、ADO.NET データセット、および XML ドキュメントを操作するためのビジュアルなツールのセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5199d-103">Provides a set of visual tools for working with XML Schemas, ADO.NET datasets, and XML documents.</span></span> <span data-ttu-id="5199d-104">XML デザイナーは、WC3 (World Wide Web Consortium) で定義されている XML スキーマ定義 (XSD) 言語をサポートします。</span><span class="sxs-lookup"><span data-stu-id="5199d-104">The XML Designer supports the XML Schema Definition (XSD) language defined by the World Wide Web Consortium (WC3).</span></span> <span data-ttu-id="5199d-105">デザイナーは、DTD (文書型定義) や XDR (XML-Data Reduced) などのその他の XML スキーマ言語をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="5199d-105">The designer does not support DTDs (document type definitions) or other XML schema languages, such as XDR (XML-Data Reduced).</span></span>  
  
 <span data-ttu-id="5199d-106">デザイナーを表示するには、データセット、XML スキーマ、または XML ファイルをプロジェクトに追加するか、次の表に示す種類のファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="5199d-106">To display the designer, add a dataset, XML Schema, or XML file to your project or open any of the file types listed in the table below.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="5199d-107">スキーマ ビューでは、 **[元に戻す]** コマンドを使用できません。</span><span class="sxs-lookup"><span data-stu-id="5199d-107">There is no **Undo** command when working in Schema view.</span></span> <span data-ttu-id="5199d-108">作業を慎重に計画すると共に、頻繁にファイルを保存してください。</span><span class="sxs-lookup"><span data-stu-id="5199d-108">Plan your work carefully and save your files often.</span></span>  
  
 <span data-ttu-id="5199d-109">デザイナーで XML ファイル、XML スキーマ、およびデータセットを操作する場合は、次の 3 つのビュー (またはモード) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5199d-109">The designer provides the following three views (or modes) to work on XML files, XML Schemas, and datasets:</span></span>  
  
|<span data-ttu-id="5199d-110">表示</span><span class="sxs-lookup"><span data-stu-id="5199d-110">View</span></span>|<span data-ttu-id="5199d-111">説明</span><span class="sxs-lookup"><span data-stu-id="5199d-111">Description</span></span>|<span data-ttu-id="5199d-112">サポートされるファイルの種類</span><span class="sxs-lookup"><span data-stu-id="5199d-112">File types supported</span></span>|  
|----------|-----------------|--------------------------|  
|<span data-ttu-id="5199d-113">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="5199d-113">**Schema**</span></span>|<span data-ttu-id="5199d-114">XML スキーマおよび ADO.NET データセットをビジュアルに作成および変更するために使用します。</span><span class="sxs-lookup"><span data-stu-id="5199d-114">For visually creating and modifying XML Schemas and ADO.NET datasets.</span></span>|<span data-ttu-id="5199d-115">.xsd</span><span class="sxs-lookup"><span data-stu-id="5199d-115">.xsd</span></span>|  
|<span data-ttu-id="5199d-116">**データ**</span><span class="sxs-lookup"><span data-stu-id="5199d-116">**Data**</span></span>|<span data-ttu-id="5199d-117">XML データ ファイルを構造化データ グリッドでビジュアルに変更するために使用します。</span><span class="sxs-lookup"><span data-stu-id="5199d-117">For visually modifying XML data files in a structured data grid.</span></span>|<span data-ttu-id="5199d-118">.xml</span><span class="sxs-lookup"><span data-stu-id="5199d-118">.xml</span></span>|  
|<span data-ttu-id="5199d-119">**XML**</span><span class="sxs-lookup"><span data-stu-id="5199d-119">**XML**</span></span>|<span data-ttu-id="5199d-120">XML を編集するために使用します。ソース エディターには、色分け表示機能や、入力候補およびメンバーの一覧を含む IntelliSense 機能があります。</span><span class="sxs-lookup"><span data-stu-id="5199d-120">For editing XML; the source editor provides color-coding and IntelliSense, including Complete Word and List Members.</span></span>|<span data-ttu-id="5199d-121">.xml、.xsd、.xslt、.wsdl、.web、.resx、.tdl、.wsf、.hta、.disco、.vsdisco、.config</span><span class="sxs-lookup"><span data-stu-id="5199d-121">.xml .xsd .xslt .wsdl.web.resx.tdl.wsf.hta.disco.vsdisco.config</span></span>|  
|<span data-ttu-id="5199d-122">**プラン表示**</span><span class="sxs-lookup"><span data-stu-id="5199d-122">**ShowPlan**</span></span>|<span data-ttu-id="5199d-123">SET SHOWPLAN_XML ON オプションを使用して作成された XML クエリ プランを表示します。</span><span class="sxs-lookup"><span data-stu-id="5199d-123">Displays xml query plans created using the SET SHOWPLAN_XML ON option.</span></span>|<span data-ttu-id="5199d-124">.showplan</span><span class="sxs-lookup"><span data-stu-id="5199d-124">.showplan</span></span>|  
  
## <a name="schema-view"></a><span data-ttu-id="5199d-125">スキーマ ビュー</span><span class="sxs-lookup"><span data-stu-id="5199d-125">Schema View</span></span>  
 <span data-ttu-id="5199d-126">スキーマ ビューでは、XML スキーマおよび ADO.NET データセットを構成する要素、属性、型などをビジュアルに表示します。</span><span class="sxs-lookup"><span data-stu-id="5199d-126">Schema view provides a visual representation of the elements, attributes, types, and so on, that make up XML Schemas and ADO.NET datasets.</span></span>  
  
 <span data-ttu-id="5199d-127">スキーマ ビューでは、ツールボックスの [XML スキーマ] タブまたはサーバー エクスプローラーからデザイン領域に要素をドロップすることによって、スキーマおよびデータセットを構築できます。</span><span class="sxs-lookup"><span data-stu-id="5199d-127">In Schema view you can construct schemas and datasets by dropping elements on the design surface from either the XML Schema tab of the Toolbox or from Server Explorer.</span></span> <span data-ttu-id="5199d-128">また、デザイン領域上で右クリックし、ショートカット メニューの [追加] をクリックして、要素をデザイナーに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="5199d-128">Additionally, you can add elements to the designer by right-clicking the design surface and selecting Add from the shortcut menu.</span></span>  
  
 <span data-ttu-id="5199d-129">スキーマ ビューでは、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5199d-129">In Schema view you can:</span></span>  
  
-   <span data-ttu-id="5199d-130">既存の XML スキーマおよび ADO.NET データセットを構築および変更する。</span><span class="sxs-lookup"><span data-stu-id="5199d-130">Construct and modify existing XML Schemas and ADO.NET datasets</span></span>  
  
-   <span data-ttu-id="5199d-131">テーブル間の関係を作成および編集する。</span><span class="sxs-lookup"><span data-stu-id="5199d-131">Create and edit relationships between tables</span></span>  
  
-   <span data-ttu-id="5199d-132">キーを作成および編集する。</span><span class="sxs-lookup"><span data-stu-id="5199d-132">Create and edit keys</span></span>  
  
-   <span data-ttu-id="5199d-133">XML スキーマから ADO.NET データセットを生成する。</span><span class="sxs-lookup"><span data-stu-id="5199d-133">Generate ADO.NET datasets from XML Schemas</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5199d-134">スキーマ ビューでの要素のレイアウトは、.xsx ファイルに保存されます。このファイルを確認するには、[ソリューション エクスプローラー] のツール バーの **[すべてのファイルを表示]** をクリックし、目的の .xsd ファイルを展開します。</span><span class="sxs-lookup"><span data-stu-id="5199d-134">The layout of elements in Schema view is stored in the .xsx file, which can be seen by clicking **Show All Files** in the Solution Explorer toolbar, and then expanding the .xsd file.</span></span> <span data-ttu-id="5199d-135">.xsd ファイルが存在しない場合は、これまで XML デザイナーでは .xsd ファイルを開いていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="5199d-135">If there is no .xsx file present, it means the .xsd file has never been opened in the XML Designer.</span></span>  
  
### <a name="customizing-schema-view"></a><span data-ttu-id="5199d-136">スキーマ ビューのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5199d-136">Customizing Schema View</span></span>  
 <span data-ttu-id="5199d-137">次の機能を使用すると、スキーマ ビューでの要素のビジュアルなレイアウトを変更できます。</span><span class="sxs-lookup"><span data-stu-id="5199d-137">The following features modify the visual layout of elements in Schema view:</span></span>  
  
-   <span data-ttu-id="5199d-138">ズーム</span><span class="sxs-lookup"><span data-stu-id="5199d-138">Zooming</span></span>  
  
-   <span data-ttu-id="5199d-139">入れ子になった要素の展開と折りたたみ</span><span class="sxs-lookup"><span data-stu-id="5199d-139">Expanding or collapsing of nested elements</span></span>  
  
-   <span data-ttu-id="5199d-140">要素の自動レイアウト</span><span class="sxs-lookup"><span data-stu-id="5199d-140">Automatically arranging layout of elements</span></span>  
  
-   <span data-ttu-id="5199d-141">展開された要素の既定の状態のリセット</span><span class="sxs-lookup"><span data-stu-id="5199d-141">Resetting default state of collapsed elements</span></span>  
  
##### <a name="to-expand-hidden-nested-elements"></a><span data-ttu-id="5199d-142">入れ子になった非表示の要素を展開するには</span><span class="sxs-lookup"><span data-stu-id="5199d-142">To expand hidden nested elements</span></span>  
  
-   <span data-ttu-id="5199d-143">要素の下部の正符号アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5199d-143">Click the plus icon on the bottom of the element.</span></span>  
  
##### <a name="to-collapse-nested-elements"></a><span data-ttu-id="5199d-144">入れ子になった要素を折りたたむには</span><span class="sxs-lookup"><span data-stu-id="5199d-144">To collapse nested elements</span></span>  
  
-   <span data-ttu-id="5199d-145">デザイナーに表示する最下位レベルにある要素の負符号アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5199d-145">Click the minus icon on the bottom-most element that you want to appear on the designer.</span></span>  
  
## <a name="data-view"></a><span data-ttu-id="5199d-146">データ ビュー</span><span class="sxs-lookup"><span data-stu-id="5199d-146">Data View</span></span>  
 <span data-ttu-id="5199d-147">データ ビューでは、.xml ファイルを編集するためにデータ グリッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5199d-147">Data view provides a data grid that can be used to modify .xml files.</span></span> <span data-ttu-id="5199d-148">データ ビューでは、XML ファイルの内容 (タグおよび構造体を除く) だけを編集できます。</span><span class="sxs-lookup"><span data-stu-id="5199d-148">Only the content (but not the tags and structure) in an XML file can be edited in Data view.</span></span>  
  
 <span data-ttu-id="5199d-149">データ ビューは、 **[データ テーブル]** 領域と **[データ]** 領域から構成されます。</span><span class="sxs-lookup"><span data-stu-id="5199d-149">There are two separate areas in Data view: **Data Tables** and **Data**.</span></span> <span data-ttu-id="5199d-150">**[データ テーブル]** 領域には、XML ファイルに定義されている関係の一覧がその入れ子の順 (最も外側から最も内側の順) に示されます。</span><span class="sxs-lookup"><span data-stu-id="5199d-150">The **Data Tables** area is a list of relations defined in the XML file, in the order of its nesting (from the outermost to the innermost).</span></span> <span data-ttu-id="5199d-151">**[データ]** 領域は、[データ テーブル] 領域の選択内容に基づいてデータを表示するデータ グリッドです。</span><span class="sxs-lookup"><span data-stu-id="5199d-151">The **Data** area is a data grid that displays data based on the selection in the Data Tables area.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5199d-152">新しく作成された XML ファイルにはデータは含まれていないので、データ ビューに表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="5199d-152">Newly created XML files contain no data and therefore cannot be displayed in Data view.</span></span> <span data-ttu-id="5199d-153">また、データ ビューをまったく呼び出すことができない XML ドキュメントのインスタンスもあります。</span><span class="sxs-lookup"><span data-stu-id="5199d-153">There are also some instances of XML documents where data view cannot be invoked at all.</span></span> <span data-ttu-id="5199d-154">XML は適切な形式と見なされますが、構造化データではなく、データ ビューへの切り替えが試行されている場合は、"この XML ドキュメントは正しい形式ですが、データ ビューで表示できない構造体を含んでいます。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5199d-154">Although the XML would be considered well formed, if it is not structured data trying to switch to Data view will generate the following message: "Although this document is well formed, it contains structure that Data View cannot display."</span></span>  
  
 <span data-ttu-id="5199d-155">データ ビューでは、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5199d-155">In Data view you can:</span></span>  
  
-   <span data-ttu-id="5199d-156">データ テーブルに手動でデータを入力する。</span><span class="sxs-lookup"><span data-stu-id="5199d-156">Manually populate data tables</span></span>  
  
-   <span data-ttu-id="5199d-157">既存のデータ テーブルを編集する。</span><span class="sxs-lookup"><span data-stu-id="5199d-157">Edit existing data tables</span></span>  
  
-   <span data-ttu-id="5199d-158">XML ドキュメントから XML スキーマを生成する。</span><span class="sxs-lookup"><span data-stu-id="5199d-158">Generate an XML Schema from an XML document</span></span>  
  
## <a name="xml-view"></a><span data-ttu-id="5199d-159">XML ビュー</span><span class="sxs-lookup"><span data-stu-id="5199d-159">XML View</span></span>  
 <span data-ttu-id="5199d-160">XML ビューは、生の XML を編集するためのエディターを提供すると共に、IntelliSense および色分け表示機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="5199d-160">XML view provides an editor for editing raw XML and provides IntelliSense and color coding.</span></span> <span data-ttu-id="5199d-161">入力候補機能は、関連スキーマを持つ .xsd ファイルおよび .xml ファイルを操作している場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5199d-161">Statement completion is available when working on .xsd files and .xml files that have an associated schema.</span></span> <span data-ttu-id="5199d-162">「」と入力して \< タグを開始すると、その場所で有効な要素の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5199d-162">Type \< to initiate a tag and you will be presented with a list of elements that are valid at that location.</span></span> <span data-ttu-id="5199d-163">要素名を入力し、Space キーを押すと、その要素でサポートされる属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5199d-163">After you type the element name and press the SPACEBAR, you will be presented with a list of attributes that the element supports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="5199d-164">IntelliSense オプションは、ツール バーからは利用できません。</span><span class="sxs-lookup"><span data-stu-id="5199d-164">IntelliSense options are not available on the toolbar.</span></span> <span data-ttu-id="5199d-165">XML エディターを使用しているときにこれらのオプションにアクセスするには、 **[編集]** メニューの **[IntelliSense]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5199d-165">When in the XML Editor, to access the options, on the **Edit** menu, click **IntelliSense**.</span></span>  
  
## <a name="showplan-view"></a><span data-ttu-id="5199d-166">プラン表示ビュー</span><span class="sxs-lookup"><span data-stu-id="5199d-166">SHOWPLAN view</span></span>  
 <span data-ttu-id="5199d-167">クエリ プランは、作成時に SET SHOWPLAN_XML ON オプションを使用して XML 形式で保存できます。</span><span class="sxs-lookup"><span data-stu-id="5199d-167">Query plans can be saved in XML format when created using SET SHOWPLAN_XML ON option.</span></span> <span data-ttu-id="5199d-168">拡張子が .showplan のファイルをダブルクリックすると、クエリ プランが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5199d-168">Double-click a file with the .showplan extension to open the query plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5199d-169">参照</span><span class="sxs-lookup"><span data-stu-id="5199d-169">See Also</span></span>  
 [<span data-ttu-id="5199d-170">XML 形式での実行プランの保存</span><span class="sxs-lookup"><span data-stu-id="5199d-170">Save an Execution Plan in XML Format</span></span>](../performance/save-an-execution-plan-in-xml-format.md)  
  
  
