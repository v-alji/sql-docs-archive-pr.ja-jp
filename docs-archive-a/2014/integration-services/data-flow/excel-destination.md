---
title: Excel 変換先 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldest.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e959f14e52fc045cb0cbc2ba0255d20bd0356d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742445"
---
# <a name="excel-destination"></a><span data-ttu-id="3c994-102">Excel 変換先</span><span class="sxs-lookup"><span data-stu-id="3c994-102">Excel Destination</span></span>
  <span data-ttu-id="3c994-103">Excel 変換先は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブックのワークシートまたは範囲にデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3c994-103">The Excel destination loads data into worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
## <a name="access-modes"></a><span data-ttu-id="3c994-104">アクセス モード</span><span class="sxs-lookup"><span data-stu-id="3c994-104">Access Modes</span></span>  
 <span data-ttu-id="3c994-105">Excel 変換先には、データを読み込むために、次の 3 つの異なるデータ アクセス モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3c994-105">The Excel destination provides three different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="3c994-106">テーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="3c994-106">A table or view.</span></span>  
  
-   <span data-ttu-id="3c994-107">変数で指定されたテーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="3c994-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="3c994-108">SQL ステートメントの結果。</span><span class="sxs-lookup"><span data-stu-id="3c994-108">The results of an SQL statement.</span></span> <span data-ttu-id="3c994-109">クエリにはパラメーター化クエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c994-109">The query can be a parameterized query.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c994-110">Excel でのワークシートまたは範囲は、テーブルまたはビューに相当します。</span><span class="sxs-lookup"><span data-stu-id="3c994-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="3c994-111">Excel ソース エディターと Excel 変換先エディターで使用できるテーブルの一覧では、既存のワークシート (Sheet1$ など、ワークシート名に $ 記号を付加して識別) と名前付き範囲 (MyRange など、$ 記号が付かないことで識別) のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c994-111">The lists of available tables in the Excel Source and Destination editors display only existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="3c994-112">使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="3c994-112">Usage Considerations</span></span>  
 <span data-ttu-id="3c994-113">Excel 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 と、それによってサポートされる Excel ISAM (Indexed Sequential Access Method) ドライバーを使用して Excel データ ソースに接続し、データの読み取りおよび書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="3c994-113">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="3c994-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報に含まれる資料の多くは、このプロバイダーおよびドライバーの処理に関するドキュメントです。これらの資料は [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または従来のデータ変換サービスに固有のものではありませんが、予期しない結果が発生する可能性のある特定の動作について知っておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c994-114">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="3c994-115">Excel ドライバーの使用方法や動作に関する一般的な情報については、「 [[HOWTO] Visual Basic または VBA から ADO を Excel データで使用する](https://support.microsoft.com/kb/257819)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c994-115">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="3c994-116">Excel ドライバーに含まれる Jet プロバイダーの次のような動作が原因で、Excel 変換先にデータを保存するときに予期しない結果が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c994-116">The following behaviors of the Jet provider that is included with the Excel driver can lead to unexpected results when saving data to an Excel destination.</span></span>  
  
-   <span data-ttu-id="3c994-117">**テキスト データの保存**。</span><span class="sxs-lookup"><span data-stu-id="3c994-117">**Saving text data**.</span></span> <span data-ttu-id="3c994-118">Excel ドライバーでテキスト データの値を Excel 変換先に保存するときに、保存される値が確実にテキスト値として解釈されるように、ドライバーによって各セルに単一引用符が追加されます。</span><span class="sxs-lookup"><span data-stu-id="3c994-118">When the Excel driver saves text data values to an Excel destination, the driver precedes the text in each cell with the single quote character (') to ensure that the saved values will be interpreted as text values.</span></span> <span data-ttu-id="3c994-119">保存されたデータの読み取りや処理を行う他のアプリケーションがあるか、または開発する場合、各テキスト値の前に付けられた単一引用符に対する特殊な処理を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c994-119">If you have or develop other applications that read or process the saved data, you may need to include special handling for the single quote character that precedes each text value.</span></span>  
  
     <span data-ttu-id="3c994-120">単一引用符が含まれることを回避する方法については、msdn.com のブログ投稿「 [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package (SSIS パッケージで Excel 変換先データ フロー コンポーネントを使用すると、データが Excel に変換されるときに、すべての文字列に単一引用符が追加される)](https://go.microsoft.com/fwlink/?LinkId=400876)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c994-120">For information on how to avoid including the single quote, see this blog post, [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package](https://go.microsoft.com/fwlink/?LinkId=400876), on msdn.com.</span></span>  
  
-   <span data-ttu-id="3c994-121">**メモ (ntext) データの保存**。</span><span class="sxs-lookup"><span data-stu-id="3c994-121">**Saving memo (ntext) da**ta.</span></span> <span data-ttu-id="3c994-122">255 文字を超える文字列を Excel 列に正常に保存するには、変換先の列のデータ型を **文字列型** ではなく **メモ型**としてドライバーが認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c994-122">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span> <span data-ttu-id="3c994-123">変換先のテーブルに既にデータ行が含まれている場合、ドライバーによってサンプリングされた先頭の数行のメモ列に、255 文字を超える値のインスタンスが 1 つ以上含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c994-123">If the destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span> <span data-ttu-id="3c994-124">コピー先のテーブルがパッケージの設計時または実行時に作成される場合、CREATE TABLE ステートメントでは、メモ列のデータ型として LONGTEXT (またはそのいずれかのシノニム) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c994-124">If the destination table is created during package design or at run time, then the CREATE TABLE statement must use LONGTEXT (or one of its synonyms) as the data type of the memo column.</span></span>  
  
-   <span data-ttu-id="3c994-125">**データ型**。</span><span class="sxs-lookup"><span data-stu-id="3c994-125">**Data types**.</span></span> <span data-ttu-id="3c994-126">Excel ドライバーでは、データ型の限定されたセットのみを認識します。</span><span class="sxs-lookup"><span data-stu-id="3c994-126">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="3c994-127">たとえば、すべての数値列は倍精度浮動小数点型 (DT_R8) として解釈され、すべての文字列の列 (メモ列以外) は 255 文字の Unicode 文字列 (DT_WSTR) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="3c994-127">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="3c994-128">では、Excel データ型を次のようにマップします。</span><span class="sxs-lookup"><span data-stu-id="3c994-128">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="3c994-129">Numeric – 倍精度浮動小数点数 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="3c994-129">Numeric    double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="3c994-130">Currency – 通貨 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="3c994-130">Currency     currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="3c994-131">Boolean – ブール (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="3c994-131">Boolean     Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="3c994-132">日付/時刻 `datetime` (DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="3c994-132">Date/time     `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="3c994-133">String – Unicode 文字列、長さ 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="3c994-133">String     Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="3c994-134">Memo – Unicode テキスト ストリーム (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="3c994-134">Memo     Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="3c994-135">**データ型と長さの変換**。</span><span class="sxs-lookup"><span data-stu-id="3c994-135">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="3c994-136">では、データ型の暗黙的な変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="3c994-136">does not implicitly convert data types.</span></span> <span data-ttu-id="3c994-137">したがって、派生列変換またはデータ変換の変換を使用して、Excel データを明示的に変換してから Excel 以外の変換先に読み込むか、Excel データを Excel 以外のデータに変換してから Excel 変換先に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c994-137">As a result, you may need to use the Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="3c994-138">この場合、初期パッケージを作成する際に、必要な変換を構成できるインポート ウィザードおよびエクスポート ウィザードを使用すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c994-138">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="3c994-139">必要な変換の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c994-139">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="3c994-140">特定のコードページを使用した Unicode Excel 文字列の列と Unicode 以外の文字列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="3c994-140">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages.</span></span>  
  
    -   <span data-ttu-id="3c994-141">255 文字の Excel 文字列の列と異なる長さの文字列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="3c994-141">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>  
  
    -   <span data-ttu-id="3c994-142">倍精度の Excel 数値列と他の型の数値列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="3c994-142">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>  
  
## <a name="configuration-of-the-excel-destination"></a><span data-ttu-id="3c994-143">Excel 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="3c994-143">Configuration of the Excel Destination</span></span>  
 <span data-ttu-id="3c994-144">Excel 変換先は、Excel 接続マネージャーを使用してデータ ソースに接続します。Excel 接続マネージャーでは、使用する Excel ブック ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c994-144">The Excel destination uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="3c994-145">詳しくは、「 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3c994-145">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="3c994-146">Excel 変換先は、1 つの標準入力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="3c994-146">The Excel destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="3c994-147">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="3c994-147">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3c994-148">**[Excel 変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c994-148">For more information about the properties that you can set in the **Excel Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="3c994-149">[[Excel 変換先エディター] ([接続マネージャー] ページ)](../excel-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="3c994-149">[Excel Destination Editor &#40;Connection Manager Page&#41;](../excel-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="3c994-150">[[Excel 変換先エディター] ([マッピング] ページ)](../excel-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="3c994-150">[Excel Destination Editor &#40;Mappings Page&#41;](../excel-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="3c994-151">[[Excel 変換先エディター] ([エラー出力] ページ)](../excel-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="3c994-151">[Excel Destination Editor &#40;Error Output Page&#41;](../excel-destination-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="3c994-152">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるすべてのプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="3c994-152">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="3c994-153">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c994-153">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3c994-154">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3c994-154">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="3c994-155">Excel のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="3c994-155">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="3c994-156">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c994-156">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3c994-157">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3c994-157">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3c994-158">SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="3c994-158">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)  
  
-   [<span data-ttu-id="3c994-159">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="3c994-159">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="3c994-160">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="3c994-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c994-161">参照</span><span class="sxs-lookup"><span data-stu-id="3c994-161">See Also</span></span>  
 <span data-ttu-id="3c994-162">[Excel ソース](excel-source.md) </span><span class="sxs-lookup"><span data-stu-id="3c994-162">[Excel Source](excel-source.md) </span></span>  
 <span data-ttu-id="3c994-163">[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3c994-163">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="3c994-164">[データ フロー](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="3c994-164">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="3c994-165">スクリプト タスクを使用した Excel ファイルの操作</span><span class="sxs-lookup"><span data-stu-id="3c994-165">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
