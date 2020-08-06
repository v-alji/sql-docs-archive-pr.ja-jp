---
title: 複数フラット ファイル接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Multiple Flat Files connection manager
- connections [Integration Services], flat files
- flat files
- flat file connections [Integration Services]
- connection managers [Integration Services], Multiple Flat Files
- multiple flat file connections
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a17125fedb495daabc4838161b3260c0d5590319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644095"
---
# <a name="multiple-flat-files-connection-manager"></a><span data-ttu-id="cb407-102">複数フラット ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="cb407-102">Multiple Flat Files Connection Manager</span></span>
  <span data-ttu-id="cb407-103">複数フラット ファイル接続マネージャーを使用すると、パッケージで複数のフラット ファイルのデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cb407-103">A Multiple Flat Files connection manager enables a package to access data in multiple flat files.</span></span> <span data-ttu-id="cb407-104">たとえば、データ フロー タスクが For ループ コンテナーなどのループ コンテナーの内部にある場合は、フラット ファイル ソースで複数フラット ファイル接続マネージャーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb407-104">For example, a Flat File source can use a Multiple Flat Files connection manager when the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="cb407-105">コンテナーの各ループで、フラット ファイル ソースは、複数フラット ファイル接続マネージャーが提供する次のファイル名からデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="cb407-105">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span>  
  
 <span data-ttu-id="cb407-106">複数フラットファイル接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時に複数のフラットファイル接続を解決する接続マネージャーを作成し、複数フラットファイル接続マネージャーのプロパティを設定して、複数フラットファイル接続マネージャーを `Connections` パッケージのコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="cb407-106">When you add a Multiple Flat Files connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Flat Files connection at run time, sets the properties on the Multiple Flat Files connection manager, and adds the Multiple Flat Files connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="cb407-107">接続マネージャーの `ConnectionManagerType` プロパティは、`MULTIFLATFILE` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cb407-107">The `ConnectionManagerType` property of the connection manager is set to `MULTIFLATFILE`.</span></span>  
  
 <span data-ttu-id="cb407-108">複数フラット ファイル接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="cb407-108">You can configure the Multiple Flat Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="cb407-109">使用するファイル、ロケール、およびコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb407-109">Specify the files, locale, and code page to use.</span></span> <span data-ttu-id="cb407-110">ロケールは、日付など、ロケール依存型のデータの解釈に使用されます。コード ページは、文字列データを Unicode に変換するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cb407-110">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="cb407-111">ファイル形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb407-111">Specify the file format.</span></span> <span data-ttu-id="cb407-112">区切られた形式、固定幅形式、または幅合わせしない形式が使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb407-112">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="cb407-113">ヘッダー行、データ行、および列の区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb407-113">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="cb407-114">列の区切り記号は、ファイル レベルで設定し、列レベルで上書きできます。</span><span class="sxs-lookup"><span data-stu-id="cb407-114">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="cb407-115">ファイルの最初の行に列の名前が含まれるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cb407-115">Indicate whether the first row in the files contains column names.</span></span>  
  
-   <span data-ttu-id="cb407-116">テキスト修飾子文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb407-116">Specify a text qualifier character.</span></span> <span data-ttu-id="cb407-117">各列は、テキスト修飾子を認識するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="cb407-117">Each column can be configured to recognize a text qualifier.</span></span>  
  
-   <span data-ttu-id="cb407-118">各列の名前、データ型、最大幅などのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cb407-118">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="cb407-119">複数フラット ファイル接続マネージャーが複数のファイルを参照する場合、ファイルのパスをパイプ (|) 文字で区切ります。</span><span class="sxs-lookup"><span data-stu-id="cb407-119">When the Multiple Flat Files connection manager references multiple files, the paths of the files are separated by the pipe (|) character.</span></span> <span data-ttu-id="cb407-120">この接続マネージャーの `ConnectionString` プロパティの形式は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cb407-120">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="cb407-121">複数のファイルを指定する場合、ワイルドカード文字を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb407-121">You can also specify multiple files by using wildcard characters.</span></span> <span data-ttu-id="cb407-122">たとえば、C ドライブ上のすべてのテキストファイルを参照するには、プロパティの値を `ConnectionString` c: \* .txt に設定します \\ 。</span><span class="sxs-lookup"><span data-stu-id="cb407-122">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="cb407-123">複数フラット ファイル接続マネージャーが複数のファイルを参照する場合、ファイルの形式はすべて同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb407-123">If a Multiple Flat Files connection manager references multiple files, all the files must have the same format.</span></span>  
  
 <span data-ttu-id="cb407-124">複数フラット ファイル接続マネージャーでは、文字列型の列の長さが既定で 50 文字に設定されています。</span><span class="sxs-lookup"><span data-stu-id="cb407-124">By default, the Multiple Flat Files connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="cb407-125">**[複数フラット ファイル接続マネージャー エディター]** ダイアログ ボックスでは、データが切り捨てられたり、列の幅が広くなりすぎないように、サンプル データを評価して、これらの列の長さを自動的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="cb407-125">In the **Multiple Flat Files Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="cb407-126">フラット ファイル ソースまたは変換で列の長さを変更しない限り、データ フローでの列の長さは一定です。</span><span class="sxs-lookup"><span data-stu-id="cb407-126">Unless you resize the column length in a Flat File source or a transformation, the column length remains the same throughout the data flow.</span></span> <span data-ttu-id="cb407-127">これらの列が幅の狭い変換先列にマップされると、ユーザー インターフェイスに警告が表示されます。また、実行時にデータの切り捨てによるエラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb407-127">If these columns map to destination columns that are narrower, warnings appear in the user interface, and at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="cb407-128">フラット ファイル接続マネージャー、フラット ファイル ソース、または変換では、変換先列に合うように列のサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="cb407-128">You can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="cb407-129">出力列の長さを変更するには、[ `Length` **詳細エディター** ] ダイアログボックスの [**入力プロパティと出力プロパティ**] タブで、出力列のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cb407-129">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="cb407-130">接続マネージャーを使用するフラット ファイル ソースを追加および構成した後に、複数フラット ファイル接続マネージャーで列の長さを変更しても、フラット ファイル ソースの出力列のサイズを手動で変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cb407-130">If you update column lengths in the Multiple Flat Files connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="cb407-131">**[フラット ファイル ソース]** ダイアログ ボックスを開くと、列のメタデータを同期するためのオプションがフラット ファイル ソースによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="cb407-131">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-multiple-flat-files-connection-manager"></a><span data-ttu-id="cb407-132">複数フラット ファイル接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="cb407-132">Configuration of the Multiple Flat Files Connection Manager</span></span>  
 <span data-ttu-id="cb407-133">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="cb407-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cb407-134">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb407-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="cb407-135">[[複数フラット ファイル接続マネージャー エディター] ([全般] ページ)](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="cb407-135">[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="cb407-136">[[複数フラット ファイル接続マネージャー エディター] ([列] ページ)](../multiple-flat-files-connection-manager-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="cb407-136">[Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../multiple-flat-files-connection-manager-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="cb407-137">[[複数フラット ファイル接続マネージャー エディター] ([詳細設定] ページ)](../multiple-flat-files-connection-manager-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="cb407-137">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../multiple-flat-files-connection-manager-editor-advanced-page.md)</span></span>  
  
-   <span data-ttu-id="cb407-138">[[複数フラット ファイル接続マネージャー エディター] &#40;[プレビュー] ページ&#41;](../multiple-flat-files-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="cb407-138">[Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;](../multiple-flat-files-connection-manager-editor-preview-page.md)</span></span>  
  
 <span data-ttu-id="cb407-139">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cb407-139">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb407-140">参照</span><span class="sxs-lookup"><span data-stu-id="cb407-140">See Also</span></span>  
 <span data-ttu-id="cb407-141">[フラット ファイル ソース](../data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="cb407-141">[Flat File Source](../data-flow/flat-file-source.md) </span></span>  
 <span data-ttu-id="cb407-142">[フラット ファイル変換先](../data-flow/flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="cb407-142">[Flat File Destination](../data-flow/flat-file-destination.md) </span></span>  
 [<span data-ttu-id="cb407-143">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="cb407-143">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
