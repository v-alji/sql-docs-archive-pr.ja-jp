---
title: '[Foreach ループエディター] ([コレクション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.collection.f1
ms.assetid: 95a19dde-61ca-4d9b-aa3d-131fa4264296
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a90ce0c8971c57ef90b502cfde298605a73c253d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743373"
---
# <a name="foreach-loop-editor-collection-page"></a><span data-ttu-id="128ce-102">[Foreach ループ エディター] ([コレクション] ページ)</span><span class="sxs-lookup"><span data-stu-id="128ce-102">Foreach Loop Editor (Collection Page)</span></span>
  <span data-ttu-id="128ce-103">**[Foreach ループ エディター]** ダイアログ ボックスの **[コレクション]** ページを使用すると、列挙子の型を指定して列挙子を構成できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-103">Use the **Collection** pageof the **Foreach Loop Editor** dialog box to specify the enumerator type and configure the enumerator.</span></span>  
  
 <span data-ttu-id="128ce-104">Foreach ループ コンテナーとその構成方法については、「 [Foreach ループ コンテナー](control-flow/foreach-loop-container.md) 」と「 [Foreach ループ コンテナーを構成する](../../2014/integration-services/configure-a-foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="128ce-104">To learn about the Foreach Loop container and how to configure it, see [Foreach Loop Container](control-flow/foreach-loop-container.md) and [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="128ce-105">静的オプション</span><span class="sxs-lookup"><span data-stu-id="128ce-105">Static Options</span></span>  
 <span data-ttu-id="128ce-106">**列挙子**</span><span class="sxs-lookup"><span data-stu-id="128ce-106">**Enumerator**</span></span>  
 <span data-ttu-id="128ce-107">列挙子の型を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-107">Select the enumerator type from the list.</span></span> <span data-ttu-id="128ce-108">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="128ce-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="128ce-109">値</span><span class="sxs-lookup"><span data-stu-id="128ce-109">Value</span></span>|<span data-ttu-id="128ce-110">説明</span><span class="sxs-lookup"><span data-stu-id="128ce-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="128ce-111">**[Foreach File 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-111">**Foreach File Enumerator**</span></span>|<span data-ttu-id="128ce-112">ファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-112">Enumerate files.</span></span> <span data-ttu-id="128ce-113">この値を選択すると、セクション **[Foreach File 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-113">Selecting this value displays the dynamic options in the section, **Foreach File Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-114">**[Foreach Item 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-114">**Foreach Item Enumerator**</span></span>|<span data-ttu-id="128ce-115">アイテム内の値を列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-115">Enumerate values in an item.</span></span> <span data-ttu-id="128ce-116">この値を選択すると、セクション **[Foreach Item 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-116">Selecting this value displays the dynamic options in the section, **Foreach Item Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-117">**[Foreach ADO 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-117">**Foreach ADO Enumerator**</span></span>|<span data-ttu-id="128ce-118">テーブルまたはテーブル内の行を列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-118">Enumerate tables or rows in tables.</span></span> <span data-ttu-id="128ce-119">この値を選択すると、セクション **[Foreach ADO 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-119">Selecting this value displays the dynamic options in the section, **Foreach ADO Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-120">**[Foreach ADO.NET Schema Rowset 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-120">**Foreach ADO.NET Schema Rowset Enumerator**</span></span>|<span data-ttu-id="128ce-121">スキーマを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-121">Enumerate a schema.</span></span> <span data-ttu-id="128ce-122">この値を選択すると、セクション **[Foreach ADO.NET Schema Rowset 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-122">Selecting this value displays the dynamic options in the section, **Foreach ADO.NET Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-123">**[Foreach From Variable 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-123">**Foreach From Variable Enumerator**</span></span>|<span data-ttu-id="128ce-124">変数内の値を列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-124">Enumerate the value in a variable.</span></span> <span data-ttu-id="128ce-125">この値を選択すると、セクション **[Foreach From Variable 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-125">Selecting this value displays the dynamic options in the section, **Foreach From Variable Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-126">**[Foreach Nodelist 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-126">**Foreach Nodelist Enumerator**</span></span>|<span data-ttu-id="128ce-127">XML ドキュメント内のノードを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-127">Enumerate nodes in an XML document.</span></span> <span data-ttu-id="128ce-128">この値を選択すると、セクション **[Foreach NodeList 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-128">Selecting this value displays the dynamic options in the section, **Foreach Nodelist Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-129">**[ForEach SMO 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-129">**Foreach SMO Enumerator**</span></span>|<span data-ttu-id="128ce-130">SMO オブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-130">Enumerate a SMO object.</span></span> <span data-ttu-id="128ce-131">この値を選択すると、セクション **[Foreach SMO 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-131">Selecting this value displays the dynamic options in the section, **Foreach SMO Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-132">**[Foreach Azure Blob 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-132">**Foreach Azure Blob Enumerator**</span></span>|<span data-ttu-id="128ce-133">指定された BLOB の場所に BLOB ファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-133">Enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="128ce-134">この値を選択すると、セクション **[Foreach Azure Blob 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-134">Selecting this value displays the dynamic options in the section, **Foreach Azure Blob Enumerator**.</span></span>|  
|<span data-ttu-id="128ce-135">**[Foreach ADLS File 列挙子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-135">**Foreach ADLS File Enumerator**</span></span>|<span data-ttu-id="128ce-136">フィルターを使用して ADLS 上のファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-136">Enumerate files on ADLS with filters.</span></span> <span data-ttu-id="128ce-137">この値を選択すると、セクション **[Foreach ADLS File 列挙子]** に動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-137">Selecting this value displays the dynamic options in the section, **Foreach ADLS File Enumerator**.</span></span>|
  
 <span data-ttu-id="128ce-138">**式**</span><span class="sxs-lookup"><span data-stu-id="128ce-138">**Expressions**</span></span>  
 <span data-ttu-id="128ce-139">**[式]** をクリックして展開すると、既存のプロパティ式のリストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-139">Click or expand **Expressions** to view the list of existing property expressions.</span></span> <span data-ttu-id="128ce-140">参照ボタン ( **[...]** ) ボタンをクリックして、列挙子プロパティのプロパティ式を追加するか、既存のプロパティ式を編集して評価します。</span><span class="sxs-lookup"><span data-stu-id="128ce-140">Click the ellipsis button **(...)** to add a property expression for an enumerator property, or edit and evaluate an existing property expression.</span></span>  
  
 <span data-ttu-id="128ce-141">**関連トピック:** [Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)、[プロパティ式エディター](expressions/property-expressions-editor.md)、[式ビルダー](expressions/expression-builder.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-141">**Related Topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Property Expressions Editor](expressions/property-expressions-editor.md), [Expression Builder](expressions/expression-builder.md)</span></span>  
  
## <a name="enumerator-dynamic-options"></a><span data-ttu-id="128ce-142">列挙子の動的オプション</span><span class="sxs-lookup"><span data-stu-id="128ce-142">Enumerator Dynamic Options</span></span>  
  
### <a name="enumerator--foreach-file-enumerator"></a><span data-ttu-id="128ce-143">[Enumerator] = [Foreach File 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-143">Enumerator = Foreach File Enumerator</span></span>  
 <span data-ttu-id="128ce-144">Foreach File 列挙子を使用して、フォルダー内のファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-144">You use the Foreach File enumerator to enumerate files in a folder.</span></span> <span data-ttu-id="128ce-145">たとえば、Foreach ループに SQL 実行タスクが含まれている場合、Foreach File 列挙子を使用して、SQL 実行タスクが実行する SQL ステートメントが含まれているファイルを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-145">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach File enumerator to enumerate files that contain SQL statements that the Execute SQL task runs.</span></span> <span data-ttu-id="128ce-146">この列挙子は、サブフォルダーが含められるように構成することができます。</span><span class="sxs-lookup"><span data-stu-id="128ce-146">The enumerator can be configured to include subfolders.</span></span>  
  
 <span data-ttu-id="128ce-147">Foreach File 列挙子が列挙するフォルダーとサブフォルダーの内容は、ループの実行中に変化する場合があります。これは、外部プロセスまたはループ内のタスクによって、ループの実行時にファイルの追加、名前変更、または削除が発生するためです。</span><span class="sxs-lookup"><span data-stu-id="128ce-147">The content of the folders and subfolders that the Foreach File enumerator enumerates might change while the loop is executing because external processes or tasks in the loop add, rename, or delete files while the loop is executing.</span></span> <span data-ttu-id="128ce-148">これは、次のような予期しない状況が発生する可能性を意味しています。</span><span class="sxs-lookup"><span data-stu-id="128ce-148">This means that a number of unexpected situations may occur:</span></span>  
  
-   <span data-ttu-id="128ce-149">ファイルが削除された場合、Foreach ループ内の 1 つのタスクで使用されたものとは異なるファイルのセットが、それ以降のタスクで使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="128ce-149">If files are deleted, one task in the Foreach Loop may perform work on a different set of files than the files used by subsequent tasks.</span></span>  
  
-   <span data-ttu-id="128ce-150">ファイルの名前が変更され、それらのファイルを置き換えるためのファイルが外部プロセスによって自動的に追加されると、Foreach ループは同じファイル コンテンツに対して 2 回作業を実行することになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="128ce-150">If files are renamed and an external process automatically adds files to replace the renamed files, the Foreach Loop might perform work twice on the same file content.</span></span>  
  
-   <span data-ttu-id="128ce-151">ファイルが追加されると、Foreach ループがどのファイルに対して作業を実行したか判断することが困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="128ce-151">If files are added, it may be difficult to determine for which files the Foreach Loop performed work.</span></span>  
  
 <span data-ttu-id="128ce-152">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="128ce-152">**Folder**</span></span>  
 <span data-ttu-id="128ce-153">列挙するルート フォルダーのパスを示します。</span><span class="sxs-lookup"><span data-stu-id="128ce-153">Provide the path of the root folder to enumerate.</span></span>  
  
 <span data-ttu-id="128ce-154">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="128ce-154">**Browse**</span></span>  
 <span data-ttu-id="128ce-155">ルート フォルダーの場所を参照して指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-155">Browse to locate the root folder.</span></span>  
  
 <span data-ttu-id="128ce-156">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="128ce-156">**Files**</span></span>  
 <span data-ttu-id="128ce-157">列挙するファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-157">Specify the files to enumerate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="128ce-158">ワイルドカード文字 (\*) を使用して、コレクションに含めるファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-158">Use wildcard characters (\*) to specify the files to include in the collection.</span></span> <span data-ttu-id="128ce-159">たとえば、名前に "abc" が含まれているファイルを追加するには、\*abc\* というフィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="128ce-159">For example, to include files with names that contain "abc", use the following filter: \*abc\*.</span></span>  
>   
>  <span data-ttu-id="128ce-160">ファイル名の拡張子を指定すると、列挙子は、文字が追加された同じ拡張子のファイルも返します</span><span class="sxs-lookup"><span data-stu-id="128ce-160">When you specify a file name extension, the enumerator also returns files that have the same extension with additional characters appended.</span></span> <span data-ttu-id="128ce-161">(これは、旧バージョンとの互換性のために 8.3 ファイル名も比較する、オペレーティング システムの **dir** コマンドと同じ動作です)。この列挙子の動作は、予期しない結果になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="128ce-161">(This is the same behavior as that of the **dir** command in the operating system, which also compares 8.3 file names for backward compatibility.) This behavior of the enumerator could cause unexpected results.</span></span> <span data-ttu-id="128ce-162">たとえば、Excel 2003 ファイルのみを列挙する場合は「\*.xls」と指定しますが、</span><span class="sxs-lookup"><span data-stu-id="128ce-162">For example, you want to enumerate only Excel 2003 files, and you specify "\*.xls".</span></span> <span data-ttu-id="128ce-163">列挙子は Excel 2007 のファイルも返します。これらのファイルの拡張子が ".xlsx" であるためです。</span><span class="sxs-lookup"><span data-stu-id="128ce-163">However, the enumerator will also return Excel 2007 files because those files have the extension, ".xlsx".</span></span>  
>   
>  <span data-ttu-id="128ce-164">コレクションに追加するファイルを式で指定するには、 **[コレクション]** ページの **[式]** を展開し、 **[FileSpec]** プロパティを選択して参照ボタン ( […] ) をクリックし、プロパティ式を追加します。</span><span class="sxs-lookup"><span data-stu-id="128ce-164">You can use an expression to specify the files to include in a collection, by expanding **Expressions** on the **Collection** page, selecting the **FileSpec** property, and then clicking the ellipsis button (...) to add the property expression.</span></span> <span data-ttu-id="128ce-165">指定したファイルを動的に選択する方法の詳細については、「 [SSIS-動的に設定されるファイルマスク: FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="128ce-165">For more information about dynamically selecting specified files, see [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)</span></span>  
  
 <span data-ttu-id="128ce-166">**[完全修飾名]**</span><span class="sxs-lookup"><span data-stu-id="128ce-166">**Fully qualified**</span></span>  
 <span data-ttu-id="128ce-167">ファイル名の完全修飾パスを取得する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-167">Select to retrieve the fully qualified path of file names.</span></span> <span data-ttu-id="128ce-168">[ファイル] オプションにワイルドカード文字が指定されている場合、返された完全修飾パスはフィルターに一致します。</span><span class="sxs-lookup"><span data-stu-id="128ce-168">If wildcard characters are specified in the Files option, then the fully-qualified paths that are returned match the filter.</span></span>  
  
 <span data-ttu-id="128ce-169">**[テーブル名のみ]**</span><span class="sxs-lookup"><span data-stu-id="128ce-169">**Name only**</span></span>  
 <span data-ttu-id="128ce-170">ファイル名のみを取得する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-170">Select to retrieve only the file names.</span></span> <span data-ttu-id="128ce-171">[ファイル] オプションにワイルドカード文字が指定されている場合、返されたファイル名はフィルターに一致します。</span><span class="sxs-lookup"><span data-stu-id="128ce-171">If wildcard characters are specified in the Files option, then the file names returned match the filter.</span></span>  
  
 <span data-ttu-id="128ce-172">**[ファイル名と拡張子]**</span><span class="sxs-lookup"><span data-stu-id="128ce-172">**Name and extension**</span></span>  
 <span data-ttu-id="128ce-173">ファイル名とファイル名拡張子を取得する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-173">Select to retrieve the file names and their file name extensions.</span></span> <span data-ttu-id="128ce-174">[ファイル] オプションにワイルドカード文字が指定されている場合、返されたファイル名および拡張子はフィルターに一致します。</span><span class="sxs-lookup"><span data-stu-id="128ce-174">If wildcard characters are specified in the Files option, then the name and extension of files returned match the filter.</span></span>  
  
 <span data-ttu-id="128ce-175">**[サブフォルダーをスキャンする]**</span><span class="sxs-lookup"><span data-stu-id="128ce-175">**Traverse Subfolders**</span></span>  
 <span data-ttu-id="128ce-176">列挙にサブフォルダーを含める場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-176">Select to include the subfolders in the enumeration.</span></span>  
  
### <a name="enumerator--foreach-item-enumerator"></a><span data-ttu-id="128ce-177">[Enumerator] = [Foreach Item 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-177">Enumerator = Foreach Item Enumerator</span></span>  
 <span data-ttu-id="128ce-178">Foreach Item 列挙子は、コレクション内のアイテムを列挙するために使用します。</span><span class="sxs-lookup"><span data-stu-id="128ce-178">You use the Foreach Item enumerator to enumerate items in a collection.</span></span> <span data-ttu-id="128ce-179">コレクション内のアイテムは、列と列の値を指定して定義します。</span><span class="sxs-lookup"><span data-stu-id="128ce-179">You define the items in the collection by specifying columns and column values.</span></span> <span data-ttu-id="128ce-180">行内の各列は個々のアイテムを定義します。</span><span class="sxs-lookup"><span data-stu-id="128ce-180">The columns in a row define an item.</span></span> <span data-ttu-id="128ce-181">たとえば、プロセス実行タスクで実行される実行可能ファイルとそのタスクで使用される作業ディレクトリを指定するアイテムに 2 つの列を割り当て、1 列は実行可能ファイルの名前、もう 1 列は作業ディレクトリの表示に使用できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-181">For example, an item that specifies the executables that an Execute Process task runs and the working directory that the task uses has two columns, one that lists the names of executables and one that lists the working directory.</span></span> <span data-ttu-id="128ce-182">行数により、ループが繰り返される回数が決まります。</span><span class="sxs-lookup"><span data-stu-id="128ce-182">The number of rows determines the number of times that the loop is repeated.</span></span> <span data-ttu-id="128ce-183">テーブルに 10 行ある場合は、ループが 10 回繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-183">If the table has 10 rows, the loop repeats 10 times.</span></span>  
  
 <span data-ttu-id="128ce-184">プロセス実行タスクのプロパティを更新するには、列のインデックスを使用してアイテムの列に変数をマップします。</span><span class="sxs-lookup"><span data-stu-id="128ce-184">To update the properties of the Execute Process task, you map variables to item columns by using the index of the column.</span></span> <span data-ttu-id="128ce-185">列挙子のアイテムで定義される最初の列のインデックス値は 0、2 番目の列のインデックス値は 1 になり、それ以降も順番にインデックス値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="128ce-185">The first column defined in the enumerator item has the index value 0, the second column 1, and so on.</span></span> <span data-ttu-id="128ce-186">変数の値は、ループが繰り返されるたびに更新されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-186">The variable values are updated with each repeat of the loop.</span></span> <span data-ttu-id="128ce-187">プロセス実行タスクの `Executable` プロパティと `WorkingDirectory` プロパティは、これらの変数を使用するプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-187">The `Executable` and `WorkingDirectory` properties of the Execute Process task can then be updated by property expressions that use these variables.</span></span>  
  
 <span data-ttu-id="128ce-188">**[For Each Item コレクションのアイテムの定義]**</span><span class="sxs-lookup"><span data-stu-id="128ce-188">**Define the items in the For Each Item collection**</span></span>  
 <span data-ttu-id="128ce-189">テーブル内の各列に値を提供します。</span><span class="sxs-lookup"><span data-stu-id="128ce-189">Provide a value for each column in the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="128ce-190">値を行列に入力した後で、新しい行がテーブルに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-190">A new row is automatically added to the table after you enter values in row columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="128ce-191">提供された値が列データ型と互換性がない場合、テキストは赤になります。</span><span class="sxs-lookup"><span data-stu-id="128ce-191">If the values provided are not compatible with the column data type, the text is colored red.</span></span>  
  
 <span data-ttu-id="128ce-192">**[列データ型]**</span><span class="sxs-lookup"><span data-stu-id="128ce-192">**Column data type**</span></span>  
 <span data-ttu-id="128ce-193">アクティブな列のデータ型を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="128ce-193">Lists the data type of the active column.</span></span>  
  
 <span data-ttu-id="128ce-194">**Remove**</span><span class="sxs-lookup"><span data-stu-id="128ce-194">**Remove**</span></span>  
 <span data-ttu-id="128ce-195">アイテムを一覧から削除するには、そのアイテムを選択してから **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="128ce-195">Select an item, and then click **Remove** to remove it from the list.</span></span>  
  
 <span data-ttu-id="128ce-196">**[列]**</span><span class="sxs-lookup"><span data-stu-id="128ce-196">**Columns**</span></span>  
 <span data-ttu-id="128ce-197">アイテム内の列のデータ型を構成する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="128ce-197">Click to configure the data type of the columns in the item.</span></span>  
  
 <span data-ttu-id="128ce-198">**関連トピック:** [[For Each Item 列] ダイアログ ボックスの UI リファレンス](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-198">**Related Topics:** [For Each Item Columns Dialog Box UI Reference](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span></span>  
  
### <a name="enumerator--foreach-ado-enumerator"></a><span data-ttu-id="128ce-199">[Enumerator] = [Foreach ADO 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-199">Enumerator = Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="128ce-200">Foreach ADO 列挙子は、変数に格納されている ADO オブジェクトまたは ADO.NET オブジェクト内の行またはテーブルを列挙するために使用します。</span><span class="sxs-lookup"><span data-stu-id="128ce-200">You use the Foreach ADO enumerator to enumerate rows or tables in an ADO or ADO.NET object that is stored in a variable.</span></span> <span data-ttu-id="128ce-201">たとえば、変数にデータセットを書き込むスクリプト タスクが Foreach ループに含まれている場合、Foreach ADO 列挙子を使用して、データセット内の行を列挙できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-201">For example, if the Foreach Loop includes a Script task that writes a dataset to a variable, you can use the Foreach ADO enumerator to enumerate the rows in the dataset.</span></span> <span data-ttu-id="128ce-202">変数に ADO.NET データセットが格納されている場合は、複数のテーブル内の行を列挙するか、テーブルを列挙するようにこの列挙子を構成できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-202">If the variable contains an ADO.NET dataset, the enumerator can be configured to enumerate rows in multiple tables or to enumerate tables.</span></span>  
  
 <span data-ttu-id="128ce-203">**[ADO オブジェクト ソース変数]**</span><span class="sxs-lookup"><span data-stu-id="128ce-203">**ADO object source variable**</span></span>  
 <span data-ttu-id="128ce-204">ユーザー定義変数を一覧から選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-204">Select a user-defined variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="128ce-205">変数は、Object データ型にする必要があります。それ以外の場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="128ce-205">The variable must have the Object data type, otherwise an error occurs.</span></span>  
  
 <span data-ttu-id="128ce-206">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-206">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="128ce-207">**[最初のテーブル内の行]**</span><span class="sxs-lookup"><span data-stu-id="128ce-207">**Rows in first table**</span></span>  
 <span data-ttu-id="128ce-208">最初のテーブルの行のみを列挙する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-208">Select to enumerate only rows in the first table.</span></span>  
  
 <span data-ttu-id="128ce-209">**[すべてのテーブルの行 (ADO.NET のデータセットのみ)]**</span><span class="sxs-lookup"><span data-stu-id="128ce-209">**Rows in all tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="128ce-210">すべてのテーブルの行を列挙する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-210">Select to enumerate rows in all tables.</span></span> <span data-ttu-id="128ce-211">このオプションは、列挙するオブジェクトがすべて同じ ADO.NET データセットのメンバーである場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-211">This option is available only if the objects to enumerate are all members of the same ADO.NET dataset.</span></span>  
  
 <span data-ttu-id="128ce-212">**[すべてのテーブル (ADO.NET のデータセットのみ)]**</span><span class="sxs-lookup"><span data-stu-id="128ce-212">**All tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="128ce-213">テーブルのみを列挙する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-213">Select to enumerate tables only.</span></span>  
  
### <a name="enumerator--foreach-adonet-schema-rowset-enumerator"></a><span data-ttu-id="128ce-214">[Enumerator] = [Foreach ADO.NET Schema Rowset 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-214">Enumerator = Foreach ADO.NET Schema Rowset Enumerator</span></span>  
 <span data-ttu-id="128ce-215">Foreach ADO.NET Schema Rowset 列挙子は、指定したデータ ソースのスキーマを列挙するために使用します。</span><span class="sxs-lookup"><span data-stu-id="128ce-215">You use the Foreach ADO.NET Schema Rowset enumerator to enumerate a schema for a specified data source.</span></span> <span data-ttu-id="128ce-216">たとえば、Foreach ループに SQL 実行タスクが含まれている場合、Foreach ADO.NET Schema Rowset 列挙子を使用して、 **AdventureWorks** データベース内の列や、スキーマ権限を取得するための SQL 実行タスクなど、スキーマを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-216">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach ADO.NET Schema Rowset enumerator to enumerate schemas such as the columns in the **AdventureWorks** database, and the Execute SQL task to get the schema permissions.</span></span>  
  
 <span data-ttu-id="128ce-217">**接続**</span><span class="sxs-lookup"><span data-stu-id="128ce-217">**Connection**</span></span>  
 <span data-ttu-id="128ce-218">ADO.NET 接続マネージャーを一覧から選択するか、[\<**New connection...**>] をクリックして ADO.NET 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-218">Select an ADO.NET connection manager in the list, or click \<**New connection...**> to create a new ADO.NET connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="128ce-219">ADO.NET 接続マネージャーでは、OLE DB の .NET プロバイダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="128ce-219">The ADO.NET connection manager must use a .NET provider for OLE DB.</span></span> <span data-ttu-id="128ce-220">SQL Server に接続する場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client の使用をお勧めします。このプロバイダーは、 **[接続マネージャー]** ダイアログ ボックスの **[OleDb の .Net プロバイダー]** セクションに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-220">If connecting to SQL Server, the recommended provider to use is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client, listed in the **.Net Providers for OleDb** section of the **Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="128ce-221">**関連トピック:** [ADO 接続マネージャー](connection-manager/ado-connection-manager.md)、[ADO.NET の接続マネージャーの構成](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-221">**Related Topics:** [ADO Connection Manager](connection-manager/ado-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="128ce-222">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="128ce-222">**Schema**</span></span>  
 <span data-ttu-id="128ce-223">列挙するスキーマを選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-223">Select the schema to enumerate.</span></span>  
  
 <span data-ttu-id="128ce-224">**[制限の設定]**</span><span class="sxs-lookup"><span data-stu-id="128ce-224">**Set Restrictions**</span></span>  
 <span data-ttu-id="128ce-225">指定したスキーマに適用する制約を設定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-225">Set the restrictions to apply to the specified schema.</span></span>  
  
 <span data-ttu-id="128ce-226">**関連トピック:** [[スキーマの制限] ダイアログ ボックス](../../2014/integration-services/schema-restrictions-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-226">**Related Topics:** [Schema Restrictions Dialog Box](../../2014/integration-services/schema-restrictions-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-from-variable-enumerator"></a><span data-ttu-id="128ce-227">[Enumerator] = [Foreach From Variable 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-227">Enumerator = Foreach From Variable Enumerator</span></span>  
 <span data-ttu-id="128ce-228">Foreach From Variable 列挙子は、指定した変数に含まれる列挙可能なオブジェクトを列挙するために使用します。</span><span class="sxs-lookup"><span data-stu-id="128ce-228">You use the Foreach From Variable enumerator to enumerate the enumerable objects in the specified variable.</span></span> <span data-ttu-id="128ce-229">たとえば、クエリを実行し、その結果を変数に格納する SQL 実行タスクが Foreach ループに含まれている場合、Foreach From Variable 列挙子を使用してクエリの結果を列挙できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-229">For example, if the Foreach Loop includes an Execute SQL task that runs a query and stores the result in a variable, you can use the Foreach From Variable enumerator to enumerate the query results.</span></span>  
  
 <span data-ttu-id="128ce-230">**変数**</span><span class="sxs-lookup"><span data-stu-id="128ce-230">**Variable**</span></span>  
 <span data-ttu-id="128ce-231">一覧で変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-231">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="128ce-232">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-232">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="enumerator--foreach-nodelist-enumerator"></a><span data-ttu-id="128ce-233">[Enumerator] = [Foreach NodeList 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-233">Enumerator = Foreach NodeList Enumerator</span></span>  
 <span data-ttu-id="128ce-234">Foreach Nodelist 列挙子は、XPath 式を XML ファイルに適用した結果として生成された XML ノードのセットを列挙するために使用します。</span><span class="sxs-lookup"><span data-stu-id="128ce-234">You use the Foreach Nodelist enumerator to enumerate the set of XML nodes that results from applying an XPath expression to an XML file.</span></span> <span data-ttu-id="128ce-235">たとえば、Foreach ループにスクリプト タスクが含まれている場合、Foreach NodeList 列挙子を使用して、XPath 式の条件を満たす値を XML ファイルからスクリプト タスクに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="128ce-235">For example, if the Foreach Loop includes a Script task, you can use the Foreach NodeList enumerator to pass a value that meets the XPath expression criteria from the XML file to the Script task.</span></span>  
  
 <span data-ttu-id="128ce-236">XML ファイルに適用される XPath 式は、OuterXPathString プロパティに格納された外部 XPath 操作です。</span><span class="sxs-lookup"><span data-stu-id="128ce-236">The XPath expression that applies to the XML file is the outer XPath operation, stored in the OuterXPathString property.</span></span> <span data-ttu-id="128ce-237">XPath 列挙型がに設定されている場合 `ElementCollection` 、Foreach ノード列挙子は、Innerxpath 文字列プロパティに格納されている内部 XPath 式を要素のコレクションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-237">If the XPath enumeration type is set to `ElementCollection`, the Foreach NodeList enumerator can apply an inner XPath expression, stored in the InnerXPathString property, to a collection of element.</span></span>  
  
 <span data-ttu-id="128ce-238">XML ドキュメントとデータの操作の詳細については、MSDN ライブラリの「[.NET Framework における XML の使用](https://go.microsoft.com/fwlink/?LinkId=56214)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="128ce-238">To learn more about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
 <span data-ttu-id="128ce-239">**[DocumentSourceType]**</span><span class="sxs-lookup"><span data-stu-id="128ce-239">**DocumentSourceType**</span></span>  
 <span data-ttu-id="128ce-240">XML ドキュメントのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-240">Select the source type of the XML document.</span></span> <span data-ttu-id="128ce-241">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="128ce-241">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="128ce-242">値</span><span class="sxs-lookup"><span data-stu-id="128ce-242">Value</span></span>|<span data-ttu-id="128ce-243">説明</span><span class="sxs-lookup"><span data-stu-id="128ce-243">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="128ce-244">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="128ce-244">**Direct input**</span></span>|<span data-ttu-id="128ce-245">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-245">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="128ce-246">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="128ce-246">**File connection**</span></span>|<span data-ttu-id="128ce-247">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-247">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="128ce-248">**変数**</span><span class="sxs-lookup"><span data-stu-id="128ce-248">**Variable**</span></span>|<span data-ttu-id="128ce-249">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-249">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="128ce-250">**[DocumentSource]**</span><span class="sxs-lookup"><span data-stu-id="128ce-250">**DocumentSource**</span></span>  
 <span data-ttu-id="128ce-251">**[DocumentSourceType]** が **[直接入力]** に設定されている場合は、XML コードを入力するか、 **[ドキュメント ソース エディター]** ダイアログ ボックスで参照ボタン ([...]) をクリックして XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-251">If **DocumentSourceType** is set to **Direct input**, provide the XML code, or click the ellipsis (...) button to provide XML by using the **Document Source Edito**r dialog box.</span></span>  
  
 <span data-ttu-id="128ce-252">**[DocumentSourceType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-252">If **DocumentSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="128ce-253">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-253">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="128ce-254">**[DocumentSourceType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-254">If **DocumentSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="128ce-255">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="128ce-255">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="128ce-256">**[EnumerationType]**</span><span class="sxs-lookup"><span data-stu-id="128ce-256">**EnumerationType**</span></span>  
 <span data-ttu-id="128ce-257">一覧から列挙型を選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-257">Select an enumeration type from the list.</span></span> <span data-ttu-id="128ce-258">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="128ce-258">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="128ce-259">値</span><span class="sxs-lookup"><span data-stu-id="128ce-259">Value</span></span>|<span data-ttu-id="128ce-260">説明</span><span class="sxs-lookup"><span data-stu-id="128ce-260">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="128ce-261">**[Navigator]**</span><span class="sxs-lookup"><span data-stu-id="128ce-261">**Navigator**</span></span>|<span data-ttu-id="128ce-262">XPathNavigator を使用して列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-262">Enumerate using an XPathNavigator.</span></span>|  
|<span data-ttu-id="128ce-263">**Node**</span><span class="sxs-lookup"><span data-stu-id="128ce-263">**Node**</span></span>|<span data-ttu-id="128ce-264">XPath 操作によって返されたノードを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-264">Enumerate nodes returned by an XPath operation.</span></span>|  
|<span data-ttu-id="128ce-265">**[NodeText]**</span><span class="sxs-lookup"><span data-stu-id="128ce-265">**NodeText**</span></span>|<span data-ttu-id="128ce-266">XPath 操作によって返されたテキスト ノードを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-266">Enumerate text nodes returned by an XPath operation.</span></span>|  
|`ElementCollection`|<span data-ttu-id="128ce-267">XPath 操作によって返された要素ノードを列挙します。</span><span class="sxs-lookup"><span data-stu-id="128ce-267">Enumerates element nodes returned by an XPath operation.</span></span>|  
  
 <span data-ttu-id="128ce-268">**[OuterXPathStringSourceType]**</span><span class="sxs-lookup"><span data-stu-id="128ce-268">**OuterXPathStringSourceType**</span></span>  
 <span data-ttu-id="128ce-269">XPath 文字列のソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-269">Select the source type of the XPath string.</span></span> <span data-ttu-id="128ce-270">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="128ce-270">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="128ce-271">値</span><span class="sxs-lookup"><span data-stu-id="128ce-271">Value</span></span>|<span data-ttu-id="128ce-272">説明</span><span class="sxs-lookup"><span data-stu-id="128ce-272">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="128ce-273">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="128ce-273">**Direct input**</span></span>|<span data-ttu-id="128ce-274">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-274">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="128ce-275">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="128ce-275">**File connection**</span></span>|<span data-ttu-id="128ce-276">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-276">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="128ce-277">**変数**</span><span class="sxs-lookup"><span data-stu-id="128ce-277">**Variable**</span></span>|<span data-ttu-id="128ce-278">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-278">Set the source to a variable that contains the XML document.</span></span>|  
  
 `OuterXPathString`  
 <span data-ttu-id="128ce-279">**[OuterXPathStringSourceType]** が **[直接入力]** に設定されている場合は、XPath 文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-279">If **OuterXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="128ce-280">**[OuterXPathStringSourceType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-280">If **OuterXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="128ce-281">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-281">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="128ce-282">**[OuterXPathStringSourceType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-282">If **OuterXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="128ce-283">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="128ce-283">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="128ce-284">**[InnerElementType]**</span><span class="sxs-lookup"><span data-stu-id="128ce-284">**InnerElementType**</span></span>  
 <span data-ttu-id="128ce-285">**EnumerationType**がに設定されている場合は `ElementCollection` 、リスト内の内部要素の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-285">If **EnumerationType** is set to `ElementCollection`, select the type of inner element in the list.</span></span>  
  
 <span data-ttu-id="128ce-286">**[InnerXPathStringSourceType]**</span><span class="sxs-lookup"><span data-stu-id="128ce-286">**InnerXPathStringSourceType**</span></span>  
 <span data-ttu-id="128ce-287">内部 XPath 文字列のソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-287">Select the source type of the inner XPath string.</span></span> <span data-ttu-id="128ce-288">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="128ce-288">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="128ce-289">値</span><span class="sxs-lookup"><span data-stu-id="128ce-289">Value</span></span>|<span data-ttu-id="128ce-290">説明</span><span class="sxs-lookup"><span data-stu-id="128ce-290">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="128ce-291">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="128ce-291">**Direct input**</span></span>|<span data-ttu-id="128ce-292">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-292">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="128ce-293">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="128ce-293">**File connection**</span></span>|<span data-ttu-id="128ce-294">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-294">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="128ce-295">**変数**</span><span class="sxs-lookup"><span data-stu-id="128ce-295">**Variable**</span></span>|<span data-ttu-id="128ce-296">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-296">Set the source to a variable that contains the XML document.</span></span>|  
  
 `InnerXPathString`  
 <span data-ttu-id="128ce-297">**[InnerXPathStringSourceType]** が **[直接入力]** に設定されている場合は、XPath 文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-297">If **InnerXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="128ce-298">**[InnerXPathStringSourceType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-298">If **InnerXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="128ce-299">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-299">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="128ce-300">**[InnerXPathStringSourceType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-300">If **InnerXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="128ce-301">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="128ce-301">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="enumerator--foreach-smo-enumerator"></a><span data-ttu-id="128ce-302">[Enumerator] = [Foreach SMO 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-302">Enumerator = Foreach SMO Enumerator</span></span>  
 <span data-ttu-id="128ce-303">Foreach SMO 列挙子は、SQL Server 管理オブジェクト (SMO) のオブジェクトを列挙するために使用します。</span><span class="sxs-lookup"><span data-stu-id="128ce-303">You use the Foreach SMO enumerator to enumerate SQL Server Management Object (SMO) objects.</span></span> <span data-ttu-id="128ce-304">たとえば、Foreach ループに SQL 実行タスクが含まれている場合、Foreach SMO 列挙子を使用して、 **AdventureWorks** データベース内のテーブルを列挙し、各テーブル内の行数をカウントするクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-304">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach SMO enumerator to enumerate the tables in the **AdventureWorks** database and run queries that counts the number of rows in each table.</span></span>  
  
 <span data-ttu-id="128ce-305">**接続**</span><span class="sxs-lookup"><span data-stu-id="128ce-305">**Connection**</span></span>  
 <span data-ttu-id="128ce-306">既存の ADO.NET 接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-306">Select an existing ADO.NET connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="128ce-307">関連トピック:[ADO.NET 接続マネージャー](connection-manager/ado-net-connection-manager.md)、[ADO.NET の接続マネージャーの構成](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-307">Related Topics: [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="128ce-308">**[列挙]**</span><span class="sxs-lookup"><span data-stu-id="128ce-308">**Enumerate**</span></span>  
 <span data-ttu-id="128ce-309">列挙する SMO オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-309">Specify the SMO object to enumerate.</span></span>  
  
 <span data-ttu-id="128ce-310">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="128ce-310">**Browse**</span></span>  
 <span data-ttu-id="128ce-311">SMO 列挙を選択します。</span><span class="sxs-lookup"><span data-stu-id="128ce-311">Select the SMO enumeration.</span></span>  
  
 <span data-ttu-id="128ce-312">**関連トピック:** [[SMO 列挙の選択] ダイアログ ボックス](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-312">**Related Topics:** [Select SMO Enumeration Dialog Box](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-azure-blob-enumerator"></a><span data-ttu-id="128ce-313">列挙子 = Foreach Azure BLOB 列挙子</span><span class="sxs-lookup"><span data-stu-id="128ce-313">Enumerator = Foreach Azure Blob Enumerator</span></span>  
 <span data-ttu-id="128ce-314">**Azure BLOB 列挙子**を使用すると、SSIS パッケージは指定された BLOB の場所に BLOB ファイルを列挙できるようになります。</span><span class="sxs-lookup"><span data-stu-id="128ce-314">The  **Azure Blob Enumerator**r enables an SSIS package to enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="128ce-315">列挙された BLOB ファイルの名前は変数に格納され、Foreach ループ コンテナー内のタスクで使用されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-315">The name of enumerated blob file can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>  
  
 <span data-ttu-id="128ce-316">**[Azure Storage 接続マネージャー]**</span><span class="sxs-lookup"><span data-stu-id="128ce-316">**Azure storage connection manager**</span></span>  
 <span data-ttu-id="128ce-317">既存の Azure ストレージ接続マネージャーを選択するか、Azure ストレージ アカウントを参照する接続マネージャーを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-317">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
 <span data-ttu-id="128ce-318">関連トピック:[Azure Storage 接続マネージャー](connection-manager/azure-storage-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="128ce-318">Related Topics: [Azure Storage Connection Manager](connection-manager/azure-storage-connection-manager.md).</span></span>  
  
 <span data-ttu-id="128ce-319">**BLOB コンテナーの名前**</span><span class="sxs-lookup"><span data-stu-id="128ce-319">**Blob container name**</span></span>  
 <span data-ttu-id="128ce-320">列挙する BLOB ファイルを含む BLOB コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-320">Specify the name of the blob container that contains the blob files to be enumerated..</span></span>  
  
 <span data-ttu-id="128ce-321">**[BLOB ディレクトリ]**</span><span class="sxs-lookup"><span data-stu-id="128ce-321">**Blob directory**</span></span>  
 <span data-ttu-id="128ce-322">列挙する BLOB ファイルを含む BLOB ディレクトリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-322">Specify the specify the blob directory that contains the blob files to be enumerated.</span></span> <span data-ttu-id="128ce-323">BLOB ディレクトリは仮想階層構造です。</span><span class="sxs-lookup"><span data-stu-id="128ce-323">The blob directory is a virtual hierarchical structure.</span></span>  
  
 <span data-ttu-id="128ce-324">**[BLOB 名のフィルター]**</span><span class="sxs-lookup"><span data-stu-id="128ce-324">**Blob name filter**</span></span>  
 <span data-ttu-id="128ce-325">特定の名前のパターンを持つファイルを列挙する名前フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-325">Specify a name filter to enumerate files with a certain name pattern.</span></span> <span data-ttu-id="128ce-326">例:</span><span class="sxs-lookup"><span data-stu-id="128ce-326">E.g.</span></span> <span data-ttu-id="128ce-327">MySheet\*.xls\* の場合、MySheet001.xls や MySheetABC.xlsx などのファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="128ce-327">MySheet\*.xls\* will include files such as MySheet001.xls and MySheetABC.xlsx.</span></span>  
  
 <span data-ttu-id="128ce-328">**[BLOB 時間範囲フィルター]**</span><span class="sxs-lookup"><span data-stu-id="128ce-328">**Blob time range from/to filter**</span></span>  
 <span data-ttu-id="128ce-329">時間範囲フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-329">Specify a time range filter.</span></span> <span data-ttu-id="128ce-330">**TimeRangeFrom** の後から **TimeRangeTo** の前までに変更されたファイルが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-330">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be enumerated.</span></span>  
### <a name="enumerator--foreach-adls-file-enumerator"></a><span data-ttu-id="128ce-331"> [列挙子] = [Foreach ADLS File 列挙子]</span><span class="sxs-lookup"><span data-stu-id="128ce-331">Enumerator = Foreach ADLS File Enumerator</span></span>  
<span data-ttu-id="128ce-332">**Adls ファイル列挙子**を使用すると、SSIS パッケージはフィルターを使用して adls 上のファイルを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-332">The **ADLS File Enumerator** enables an SSIS package to enumerate files on ADLS with filters.</span></span> <span data-ttu-id="128ce-333">列挙された `/` ファイルのスラッシュ () で始まる完全なパスは、変数に格納し、Foreach ループコンテナー内のタスクで使用できます。</span><span class="sxs-lookup"><span data-stu-id="128ce-333">The slash (`/`)-prefixed full path of enumerated files can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>
  
<span data-ttu-id="128ce-334">**[AzureDataLakeConnection]**</span><span class="sxs-lookup"><span data-stu-id="128ce-334">**AzureDataLakeConnection**</span></span>  
<span data-ttu-id="128ce-335">Azure Data Lake 接続マネージャーを指定するか、ADLS アカウントを参照する新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="128ce-335">Specifies an Azure Data Lake connection manager, or creates a new one that refers to an ADLS account.</span></span>   
  
<span data-ttu-id="128ce-336">**[AzureDataLakeDirectory]**</span><span class="sxs-lookup"><span data-stu-id="128ce-336">**AzureDataLakeDirectory**</span></span>  
<span data-ttu-id="128ce-337">検索する ADLS ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-337">Specifies the ADLS directory to search.</span></span>
  
<span data-ttu-id="128ce-338">**[FileNamePattern]**</span><span class="sxs-lookup"><span data-stu-id="128ce-338">**FileNamePattern**</span></span>  
<span data-ttu-id="128ce-339">ファイル名フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-339">Specifies a file name filter.</span></span> <span data-ttu-id="128ce-340">名前が指定したパターンに一致するファイルのみが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="128ce-340">Only files whose name matches the specified pattern will be enumerated.</span></span> <span data-ttu-id="128ce-341">ワイルドカードの `*` と `?` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="128ce-341">Wildcards `*` and `?` are supported.</span></span> 
  
<span data-ttu-id="128ce-342">**[SearchRecursively]**</span><span class="sxs-lookup"><span data-stu-id="128ce-342">**SearchRecursively**</span></span>  
<span data-ttu-id="128ce-343">指定されたディレクトリ内で再帰的に検索するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="128ce-343">Specifies whether to search recursively within the specified directory.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="128ce-344">外部リソース</span><span class="sxs-lookup"><span data-stu-id="128ce-344">External Resources</span></span>  
  
-   <span data-ttu-id="128ce-345">bidn.com のブログ「 [SSIS の For Each ノード一覧の列挙子](https://go.microsoft.com/fwlink/?LinkId=220671)」</span><span class="sxs-lookup"><span data-stu-id="128ce-345">Blog entry, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), on bidn.com.</span></span>  
  
-   <span data-ttu-id="128ce-346">ブログエントリ、 [SSIS-動的に設定するファイルマスク: FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)。</span><span class="sxs-lookup"><span data-stu-id="128ce-346">Blog entry, [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128ce-347">参照</span><span class="sxs-lookup"><span data-stu-id="128ce-347">See Also</span></span>  
 <span data-ttu-id="128ce-348">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="128ce-348">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="128ce-349">[Foreach ループエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="128ce-349">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="128ce-350">[[Foreach ループエディター &#40;変数のマッピング] ページ&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="128ce-350">[Foreach Loop Editor &#40;Variable Mappings Page&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span></span>  
 <span data-ttu-id="128ce-351">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="128ce-351">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="128ce-352">For ループ コンテナー</span><span class="sxs-lookup"><span data-stu-id="128ce-352">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
