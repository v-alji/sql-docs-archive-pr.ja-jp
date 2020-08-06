---
title: フラット ファイル接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], Flat File
- connections [Integration Services], flat files
- files [Integration Services], connections
- Flat File connection manager
- flat files
- flat file connections [Integration Services]
ms.assetid: 7830f80d-af32-4e8f-a6fc-f03af6bc1946
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 961fa5ebd0c254c152cb4a84a855f719b6dfaa43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738574"
---
# <a name="flat-file-connection-manager"></a><span data-ttu-id="2aeb3-102">フラット ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="2aeb3-102">Flat File Connection Manager</span></span>
  <span data-ttu-id="2aeb3-103">フラット ファイル接続マネージャーを使用すると、パッケージはフラット ファイルのデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-103">A Flat File connection manager enables a package to access data in a flat file.</span></span> <span data-ttu-id="2aeb3-104">たとえば、フラット ファイルの変換元と変換先は、フラット ファイル接続マネージャーを使用して、データの抽出および読み込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-104">For example, the Flat File source and destination can use Flat File connection managers to extract and load data.</span></span>  
  
 <span data-ttu-id="2aeb3-105">フラット ファイル接続マネージャーがアクセスできるファイルは、1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-105">The Flat File connection manager can access only one file.</span></span> <span data-ttu-id="2aeb3-106">複数のファイルを参照するには、フラット ファイル接続マネージャーではなく、複数フラット ファイル接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-106">To reference multiple files, use a Multiple Flat Files connection manager instead of a Flat File connection manager.</span></span> <span data-ttu-id="2aeb3-107">詳細については、「 [複数フラット ファイル接続マネージャー](multiple-flat-files-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-107">For more information, see [Multiple Flat Files Connection Manager](multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="column-length"></a><span data-ttu-id="2aeb3-108">列の長さ</span><span class="sxs-lookup"><span data-stu-id="2aeb3-108">Column Length</span></span>  
 <span data-ttu-id="2aeb3-109">フラット ファイル接続マネージャーでは、文字列型の列の長さが既定で 50 文字に設定されています。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-109">By default, the Flat File connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="2aeb3-110">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスでは、サンプル データを評価し、これらの列の長さを自動的に変更して、データが切り捨てられたり、列の幅が広すぎたりしないようにできます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-110">In the **Flat File Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="2aeb3-111">また、その後にフラット ファイル ソースまたは変換で列の長さを変更しない限り、データ フロー全体をとおして文字列型の列の長さは一定です。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-111">Also, unless you subsequently resize the column length in a Flat File source or a transformation, the column length of string column remains the same throughout the data flow.</span></span> <span data-ttu-id="2aeb3-112">これらの文字列型の列が、変換先として幅の狭い列にマップされた場合、ユーザー インターフェイスに警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-112">If these string columns map to destination columns that are narrower, warnings appear in the user interface.</span></span> <span data-ttu-id="2aeb3-113">さらに、実行時にデータの切り捨てによるエラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-113">Moreover, at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="2aeb3-114">エラーや切り捨てが発生しないように、フラット ファイル接続マネージャー、フラット ファイル ソース、または変換で、変換先列に合うように列のサイズを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-114">To avoid errors or truncation, you can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="2aeb3-115">出力列の長さを変更するには、[ `Length` **詳細エディター** ] ダイアログボックスの [**入力プロパティと出力プロパティ**] タブで、出力列のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-115">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="2aeb3-116">接続マネージャーを使用するフラット ファイル ソースを追加および構成した後に、フラット ファイル接続マネージャーで列の長さを変更した場合は、フラット ファイル ソースの出力列のサイズを手動で変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-116">If you update column lengths in the Flat File connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="2aeb3-117">**[フラット ファイル ソース]** ダイアログ ボックスを開くと、列のメタデータを同期するためのオプションがフラット ファイル ソースによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-117">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-flat-file-connection-manager"></a><span data-ttu-id="2aeb3-118">フラット ファイル接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="2aeb3-118">Configuration of the Flat File Connection Manager</span></span>  
 <span data-ttu-id="2aeb3-119">フラットファイル接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時にフラットファイル接続を解決する接続マネージャーを作成し、フラットファイル接続プロパティを設定して、フラットファイル接続マネージャーを `Connections` パッケージのコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-119">When you add a Flat File connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Flat File connection at run time, sets the Flat File connection properties, and adds the Flat File connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="2aeb3-120">接続マネージャーの `ConnectionManagerType` プロパティは、`FLATFILE` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-120">The `ConnectionManagerType` property of the connection manager is set to `FLATFILE`.</span></span>  
  
 <span data-ttu-id="2aeb3-121">既定では、フラット ファイル接続マネージャーは、引用符で囲まれていないデータの行区切り記号を常に確認し、行区切り記号が見つかると新しい行を開始します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-121">By default, the Flat File connection manager always checks for a row delimiter in unquoted data, and starts a new row when a row delimiter is found.</span></span> <span data-ttu-id="2aeb3-122">これにより、接続マネージャーは列フィールドがない行を含むファイルを正しく解析できます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-122">This enables the connection manager to correctly parse files with rows that are missing column fields.</span></span>  
  
 <span data-ttu-id="2aeb3-123">場合によっては、この機能を無効にすると、パッケージのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-123">In some cases, disabling this feature may improve package performance.</span></span> <span data-ttu-id="2aeb3-124">この機能を無効にするには、フラットファイル接続マネージャーのプロパティである**Always Checkforrowデリミター**をに設定し `False` ます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-124">You can disable this feature by setting the Flat File connection manager property, **AlwaysCheckForRowDelimiters**, to `False`.</span></span>  
  
 <span data-ttu-id="2aeb3-125">フラット ファイル接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-125">You can configure the Flat File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="2aeb3-126">使用するファイル、ロケール、およびコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-126">Specify the file, locale, and code page to use.</span></span> <span data-ttu-id="2aeb3-127">ロケールは、日付など、ロケール依存型のデータの解釈に使用されます。コード ページは、文字列データを Unicode に変換するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-127">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="2aeb3-128">ファイル形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-128">Specify the file format.</span></span> <span data-ttu-id="2aeb3-129">区切られた形式、固定幅形式、または幅合わせしない形式が使用できます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-129">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="2aeb3-130">ヘッダー行、データ行、および列の区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-130">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="2aeb3-131">列の区切り記号は、ファイル レベルで設定し、列レベルで上書きできます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-131">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="2aeb3-132">ファイルの最初の行に列の名前が含まれるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-132">Indicate whether the first row in the file contains column names.</span></span>  
  
-   <span data-ttu-id="2aeb3-133">テキスト修飾子文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-133">Specify a text qualifier character.</span></span> <span data-ttu-id="2aeb3-134">各列は、テキスト修飾子を認識するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-134">Each column can be configured to recognize a text qualifier.</span></span>  
  
     <span data-ttu-id="2aeb3-135">修飾子文字を使用して、修飾される文字列に修飾子文字を埋め込むことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-135">The use of a qualifier character to embed a qualifier character into a qualified string is now supported.</span></span> <span data-ttu-id="2aeb3-136">テキスト修飾子の二重インスタンスは、1 つのリテラル、つまりその文字列の 1 つのインスタンスとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-136">The double instance of a text qualifier is interpreted as a literal, single instance of that string.</span></span> <span data-ttu-id="2aeb3-137">たとえば、テキスト修飾子が単一引用符で、入力データが 'abc'、'def'、'g'hi' の場合、出力データは abc、def、g'hi になります。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-137">For example, if the text qualifier is a single quote and the input data is 'abc', 'def', 'g'hi', the output data is abc, def, g'hi.</span></span>  
  
-   <span data-ttu-id="2aeb3-138">各列の名前、データ型、最大幅などのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-138">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="2aeb3-139">フラット ファイル接続マネージャーの ConnectionString プロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [プロパティ] ウィンドウで式を指定することで設定できます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-139">You can set the ConnectionString property for the Flat File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="2aeb3-140">検証エラーを回避するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-140">To avoid a validation error, do the following.</span></span>  
  
-   <span data-ttu-id="2aeb3-141">式を使用してファイルを指定する場合は、 **[フラット ファイル接続マネージャー エディター]** の **[ファイル名]** ボックスにファイル パスを追加します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-141">When you use an expression to specify the file, add a file path in the **File name** box in the **Flat File Connection Manager Editor**.</span></span>  
  
-   <span data-ttu-id="2aeb3-142">フラット ファイル接続マネージャーの **DelayValidation** プロパティを **True**に設定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-142">Set the **DelayValidation** property on the Flat File connection manager to **True**.</span></span>  
  
 <span data-ttu-id="2aeb3-143">フラット ファイルの変換先に対してフラット ファイル接続マネージャーを使用することにより、実行時に式を使用してファイル名を作成できます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-143">You can use an expression to create a file name at runtime by using the Flat File connection manager with the Flat File destination.</span></span>  
  
 <span data-ttu-id="2aeb3-144">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-144">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2aeb3-145">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-145">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="2aeb3-146">[[フラット ファイル接続マネージャー エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="2aeb3-146">[Flat File Connection Manager Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="2aeb3-147">[[フラット ファイル接続マネージャー エディター] &#40;[列] ページ&#41;](../flat-file-connection-manager-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="2aeb3-147">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../flat-file-connection-manager-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="2aeb3-148">[[フラット ファイル接続マネージャー エディター] &#40;[詳細設定] ページ&#41;](../flat-file-connection-manager-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="2aeb3-148">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../flat-file-connection-manager-editor-advanced-page.md)</span></span>  
  
-   <span data-ttu-id="2aeb3-149">[[フラット ファイル接続マネージャー エディター] ([プレビュー] ページ)](../flat-file-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="2aeb3-149">[Flat File Connection Manager Editor &#40;Preview Page&#41;](../flat-file-connection-manager-editor-preview-page.md)</span></span>  
  
 <span data-ttu-id="2aeb3-150">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="2aeb3-150">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
