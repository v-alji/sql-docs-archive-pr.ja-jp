---
title: Excel ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsource.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1324ca9e9b9535b8598e3e2de22f6c06c350b7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742449"
---
# <a name="excel-source"></a><span data-ttu-id="d9eb9-102">Excel ソース</span><span class="sxs-lookup"><span data-stu-id="d9eb9-102">Excel Source</span></span>
  <span data-ttu-id="d9eb9-103">Excel ソースは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブック内のワークシートまたは範囲からデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-103">The Excel source extracts data from worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
 <span data-ttu-id="d9eb9-104">Excel ソースでは、データを抽出するために、次の 4 つの異なるデータ アクセス モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-104">The Excel source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="d9eb9-105">テーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-105">A table or view.</span></span>  
  
-   <span data-ttu-id="d9eb9-106">変数で指定されたテーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-106">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="d9eb9-107">SQL ステートメントの結果。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-107">The results of an SQL statement.</span></span> <span data-ttu-id="d9eb9-108">クエリにはパラメーター化クエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-108">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="d9eb9-109">変数に格納された SQL ステートメントの結果。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-109">The results of an SQL statement stored in a variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9eb9-110">Excel でのワークシートまたは範囲は、テーブルまたはビューに相当します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="d9eb9-111">Excel ソース エディターと Excel 変換先エディターで使用できるテーブルの一覧では、既存のワークシート (Sheet1$ など、ワークシート名に $ 記号を付加して識別) と名前付き範囲 (MyRange など、$ 記号が付かないことで識別) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-111">The list of available tables in the Excel Source and Destination editors displays existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span> <span data-ttu-id="d9eb9-112">詳細については、「使用に関する注意点」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-112">For more information, see the Usage Considerations section.</span></span>  
  
 <span data-ttu-id="d9eb9-113">Excel ソースは、Excel 接続マネージャーを使用してデータ ソースに接続します。Excel 接続マネージャーでは、使用する Excel ブック ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-113">The Excel source uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="d9eb9-114">詳しくは、「 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-114">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d9eb9-115">Excel ソースは、1 つの標準出力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-115">The Excel source has one regular output and one error output.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="d9eb9-116">使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="d9eb9-116">Usage Considerations</span></span>  
 <span data-ttu-id="d9eb9-117">Excel 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 と、それによってサポートされる Excel ISAM (Indexed Sequential Access Method) ドライバーを使用して Excel データ ソースに接続し、データの読み取りおよび書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-117">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="d9eb9-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報に含まれる資料の多くは、このプロバイダーおよびドライバーの処理に関するドキュメントです。これらの資料は [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または従来のデータ変換サービスに固有のものではありませんが、予期しない結果が発生する可能性のある特定の動作について知っておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-118">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="d9eb9-119">Excel ドライバーの使用方法や動作に関する一般的な情報については、「 [[HOWTO] Visual Basic または VBA から ADO を Excel データで使用する](https://support.microsoft.com/kb/257819)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-119">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="d9eb9-120">Jet プロバイダーを Excel ドライバーと共に使用した場合、次のような動作が原因で、Excel データ ソースのデータを読み取るときに予期しない結果が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-120">The following behaviors of the Jet provider with the Excel driver can lead to unexpected results when reading data from an Excel data source.</span></span>  
  
-   <span data-ttu-id="d9eb9-121">**データ ソース**。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-121">**Data sources**.</span></span> <span data-ttu-id="d9eb9-122">Excel ブックの変換元データには、ワークシートまたは名前付き範囲 (MyRange など) を使用できます。ワークシート名には $ 記号を付加する必要があります (Sheet1$ など)。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-122">The source of data in an Excel workbook can be a worksheet, to which the $ sign must be appended (for example, Sheet1$), or a named range (for example, MyRange).</span></span> <span data-ttu-id="d9eb9-123">SQL ステートメントでは、$ 記号による構文エラーを回避するため、ワークシートの名前を [Sheet1$] などのように区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-123">In a SQL statement, the name of a worksheet must be delimited (for example, [Sheet1$]) to avoid a syntax error caused by the $ sign.</span></span> <span data-ttu-id="d9eb9-124">クエリ ビルダーは、これらの区切り記号を自動的に付加します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-124">The Query Builder automatically adds these delimiters.</span></span> <span data-ttu-id="d9eb9-125">ワークシートまたは範囲を指定した場合、ドライバーは、ワークシートまたは範囲の左上の空でない最初のセルから、連続したセルのブロックを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-125">When you specify a worksheet or range, the driver reads the contiguous block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="d9eb9-126">したがって、ソース データには、タイトル行またはヘッダー行とデータ行との間に空の行を入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-126">Therefore you cannot have empty rows in the source data, or an empty row between title or header rows and the data rows.</span></span>  
  
-   <span data-ttu-id="d9eb9-127">**値が不足**しています。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-127">**Missing values**.</span></span> <span data-ttu-id="d9eb9-128">Excel ドライバーは、指定した変換元の特定の行数 (既定では 8 行) を読み取り、各列のデータ型を推測します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-128">The Excel driver reads a certain number of rows (by default, 8 rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="d9eb9-129">1 つの列に複数のデータ型が混在している可能性がある場合、特に数値データとテキスト データが混合している場合に、Excel ドライバーは数が多い方のデータ型を優先して判定し、それ以外のデータ型のデータが含まれるセルについては NULL 値を返します</span><span class="sxs-lookup"><span data-stu-id="d9eb9-129">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="d9eb9-130">(同数の場合は、数値型が優先されます)。Excel ワークシートでのセル書式のほとんどのオプションは、このデータ型の判定に影響しません。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-130">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span> <span data-ttu-id="d9eb9-131">Excel ドライバーのこの動作を変更するには、インポート モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-131">You can modify this behavior of the Excel driver by specifying Import Mode.</span></span> <span data-ttu-id="d9eb9-132">インポートモードを指定するには、[ `IMEX=1` **プロパティ**] ウィンドウで、Excel 接続マネージャーの接続文字列の [拡張プロパティ] の値にを追加します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-132">To specify Import Mode, add `IMEX=1` to the value of Extended Properties in the connection string of the Excel connection manager in the **Properties** window.</span></span> <span data-ttu-id="d9eb9-133">詳細については、「 [[PRB] DAO の OpenRecordset を使用すると Excel の値として NULL が返される](https://support.microsoft.com/kb/194124)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-133">For more information, see [PRB: Excel Values Returned as NULL Using DAO OpenRecordset](https://support.microsoft.com/kb/194124).</span></span>  
  
-   <span data-ttu-id="d9eb9-134">**切り捨てら**れたテキスト。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-134">**Truncated text**.</span></span> <span data-ttu-id="d9eb9-135">Excel の列にテキスト データが含まているとドライバーが判定した場合、ドライバーはサンプリングした最も長い値に基づいて、データ型 (文字列またはメモ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-135">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="d9eb9-136">ドライバーがサンプリングした行で 255 文字より長い値が検出されなかった場合、その列はメモ列ではなく、255 文字の文字列の列として扱われます。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-136">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="d9eb9-137">このため、255 文字より長い値があると、切り捨てられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-137">Therefore, values longer than 255 characters may be truncated.</span></span> <span data-ttu-id="d9eb9-138">切り捨てを発生させずにメモ列からデータをインポートするには、サンプリングされた行のうち 1 行以上のメモ列に、255 文字より長い値が含まれている状態にする必要があります。または、そのような行が含まれるように、ドライバーがサンプリングする行数を増やす必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-138">To import data from a memo column without truncation, you must make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters, or you must increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="d9eb9-139">サンプリングする行数を増やすには、 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** レジストリ キーの **TypeGuessRows** の値を増やします。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-139">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** registry key.</span></span> <span data-ttu-id="d9eb9-140">詳細については、「 [[PRB] DTS: Jet 4.0 OLEDB からの転送がバッファーのオーバーフロー エラーで失敗](https://support.microsoft.com/kb/281517)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-140">For more information, see [PRB: Transfer of Data from Jet 4.0 OLEDB Source Fails w/ Error](https://support.microsoft.com/kb/281517).</span></span>  
  
-   <span data-ttu-id="d9eb9-141">**データ型**。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-141">**Data types**.</span></span> <span data-ttu-id="d9eb9-142">Excel ドライバーでは、データ型の限定されたセットのみを認識します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-142">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="d9eb9-143">たとえば、すべての数値列は倍精度浮動小数点型 (DT_R8) として解釈され、すべての文字列の列 (メモ列以外) は 255 文字の Unicode 文字列 (DT_WSTR) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-143">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="d9eb9-144">では、Excel データ型を次のようにマップします。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-144">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="d9eb9-145">Numeric - 倍精度浮動小数点数 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-145">Numeric - double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="d9eb9-146">Currency - 通貨 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-146">Currency - currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="d9eb9-147">Boolean - ブール (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-147">Boolean - Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="d9eb9-148">日付/時刻- `datetime` (DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-148">Date/time - `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="d9eb9-149">String - Unicode 文字列、長さ 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-149">String - Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="d9eb9-150">Memo - Unicode テキスト ストリーム (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-150">Memo - Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="d9eb9-151">**データ型と長さの変換**。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-151">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="d9eb9-152">では、データ型の暗黙的な変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-152">does not implicitly convert data types.</span></span> <span data-ttu-id="d9eb9-153">したがって、派生列変換またはデータ変換の変換を使用して、Excel データを明示的に変換してから Excel 以外の変換先に読み込むか、Excel データを Excel 以外のデータに変換してから Excel 変換先に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-153">As a result, you may need to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="d9eb9-154">この場合、初期パッケージを作成する際に、必要な変換を構成できるインポート ウィザードおよびエクスポート ウィザードを使用すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-154">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="d9eb9-155">必要な変換の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-155">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="d9eb9-156">特定のコードページを使用した Unicode Excel 文字列の列と Unicode 以外の文字列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="d9eb9-156">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages</span></span>  
  
    -   <span data-ttu-id="d9eb9-157">255 文字の Excel 文字列の列と異なる長さの文字列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="d9eb9-157">Conversion between 255-character Excel string columns and string columns of different lengths</span></span>  
  
    -   <span data-ttu-id="d9eb9-158">倍精度の Excel 数値列と他の型の数値列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="d9eb9-158">Conversion between double-precision Excel numeric columns and numeric columns of other types</span></span>  
  
## <a name="excel-source-configuration"></a><span data-ttu-id="d9eb9-159">Excel ソースの構成</span><span class="sxs-lookup"><span data-stu-id="d9eb9-159">Excel Source Configuration</span></span>  
 <span data-ttu-id="d9eb9-160">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d9eb9-161">**[Excel ソース エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-161">For more information about the properties that you can set in the **Excel Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="d9eb9-162">[[Excel ソース エディター] &#40;[接続マネージャー] ページ&#41;](../excel-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-162">[Excel Source Editor &#40;Connection Manager Page&#41;](../excel-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="d9eb9-163">[[Excel ソース エディター] &#40;[列] ページ&#41;](../excel-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-163">[Excel Source Editor &#40;Columns Page&#41;](../excel-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="d9eb9-164">[[Excel ソース エディター] ([エラー出力] ページ)](../excel-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-164">[Excel Source Editor &#40;Error Output Page&#41;](../excel-source-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="d9eb9-165">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるすべてのプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-165">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="d9eb9-166">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-166">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d9eb9-167">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d9eb9-167">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="d9eb9-168">Excel のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="d9eb9-168">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="d9eb9-169">Excel ファイルのグループによるループ処理については、「 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../control-flow/foreach-loop-container.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-169">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d9eb9-170">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d9eb9-170">Related Tasks</span></span>  

-   [<span data-ttu-id="d9eb9-171">SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="d9eb9-171">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)

-   [<span data-ttu-id="d9eb9-172">クエリ パラメーターをデータ フロー コンポーネントの変数にマップする</span><span class="sxs-lookup"><span data-stu-id="d9eb9-172">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="d9eb9-173">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="d9eb9-173">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="d9eb9-174">マージ変換およびマージ結合変換用にデータを並べ替える</span><span class="sxs-lookup"><span data-stu-id="d9eb9-174">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [<span data-ttu-id="d9eb9-175">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="d9eb9-175">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="d9eb9-176">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="d9eb9-176">Related Content</span></span>  
  
-   <span data-ttu-id="d9eb9-177">hrvoje.piasevoli.com のブログ「 [Importing data from 64-bit Excel in SSIS](https://go.microsoft.com/fwlink/?LinkId=217673)」(SSIS での 64 ビット バージョンの Excel からのデータ インポート)</span><span class="sxs-lookup"><span data-stu-id="d9eb9-177">Blog entry, [Importing data from 64-bit Excel in SSIS](https://go.microsoft.com/fwlink/?LinkId=217673), on hrvoje.piasevoli.com</span></span>  
  
-   <span data-ttu-id="d9eb9-178">[SSIS の Excel (.xlsx) に接続する](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html)ブログエントリ。</span><span class="sxs-lookup"><span data-stu-id="d9eb9-178">Blog entry, [Connecting to Excel (XLSX) in SSIS](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html).</span></span>  
  
  
