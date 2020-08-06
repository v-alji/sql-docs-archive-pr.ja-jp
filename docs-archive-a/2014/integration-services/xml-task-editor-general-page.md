---
title: XML タスクエディター ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.general.f1
helpviewer_keywords:
- XML Task Editor
ms.assetid: b9622c48-3243-4408-a1de-9ba20e32ff70
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f73681a818d80c4e8b2755086e653e5c7e682f01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736493"
---
# <a name="xml-task-editor-general-page"></a><span data-ttu-id="b81d6-102">XML Task Editor (General Page)</span><span class="sxs-lookup"><span data-stu-id="b81d6-102">XML Task Editor (General Page)</span></span>
  <span data-ttu-id="b81d6-103">**[XML タスク エディター]** ダイアログ ボックスの **[全般]** ノードを使用すると、操作の種類を指定したり構成したりできます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-103">Use the **General Node** of the **XML Task Editor** dialog box to specify the operation type and configure the operation.</span></span>  
  
 <span data-ttu-id="b81d6-104">このタスクの詳細については、「 [XML Task](control-flow/xml-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b81d6-104">To learn about this task, see [XML Task](control-flow/xml-task.md).</span></span> <span data-ttu-id="b81d6-105">XML ドキュメントとデータの操作の詳細については、MSDN ライブラリの「[.NET Framework における XML の使用](https://go.microsoft.com/fwlink/?LinkId=56214)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b81d6-105">For information about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="b81d6-106">静的オプション</span><span class="sxs-lookup"><span data-stu-id="b81d6-106">Static Options</span></span>  
 <span data-ttu-id="b81d6-107">**[OperationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-107">**OperationType**</span></span>  
 <span data-ttu-id="b81d6-108">一覧から操作の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-108">Select the operation type from the list.</span></span> <span data-ttu-id="b81d6-109">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-109">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-110">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-110">Value</span></span>|<span data-ttu-id="b81d6-111">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-112">**検証**</span><span class="sxs-lookup"><span data-stu-id="b81d6-112">**Validate**</span></span>|<span data-ttu-id="b81d6-113">文書型定義 (DTD) または XML スキーマ定義 (XSD) スキーマに対して XML ドキュメントを検証します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-113">Validates the XML document against a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="b81d6-114">このオプションを選択すると、 **[Validate]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-114">Selecting this option displays the dynamic options in section, **Validate**.</span></span>|  
|<span data-ttu-id="b81d6-115">**XSLT (XSLT)**</span><span class="sxs-lookup"><span data-stu-id="b81d6-115">**XSLT**</span></span>|<span data-ttu-id="b81d6-116">XML ドキュメントに対して XSL 変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-116">Performs XSL transformations on XML documents.</span></span> <span data-ttu-id="b81d6-117">このオプションを選択すると、 **[XSLT]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-117">Selecting this option displays the dynamic options in section, **XSLT**.</span></span>|  
|<span data-ttu-id="b81d6-118">**[XPath]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-118">**XPATH**</span></span>|<span data-ttu-id="b81d6-119">XPath クエリと評価を実行します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-119">Performs XPath queries and evaluations.</span></span> <span data-ttu-id="b81d6-120">このオプションを選択すると、 **[Xpath]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-120">Selecting this option displays the dynamic options in section, **XPATH**.</span></span>|  
|<span data-ttu-id="b81d6-121">**[マージ]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-121">**Merge**</span></span>|<span data-ttu-id="b81d6-122">2 つの XML ドキュメントをマージします。</span><span class="sxs-lookup"><span data-stu-id="b81d6-122">Merges two XML documents.</span></span> <span data-ttu-id="b81d6-123">このオプションを選択すると、 **[Merge]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-123">Selecting this option displays the dynamic options in section, **Merge**.</span></span>|  
|<span data-ttu-id="b81d6-124">**[Diff]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-124">**Diff**</span></span>|<span data-ttu-id="b81d6-125">2 つの XML ドキュメントを比較します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-125">Compares two XML documents.</span></span> <span data-ttu-id="b81d6-126">このオプションを選択すると、 **[Diff]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-126">Selecting this option displays the dynamic options in section, **Diff**.</span></span>|  
|<span data-ttu-id="b81d6-127">**[Patch]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-127">**Patch**</span></span>|<span data-ttu-id="b81d6-128">Diff 操作からの出力を適用して、新しいドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-128">Applies the output from the Diff operation to create a new document.</span></span> <span data-ttu-id="b81d6-129">このオプションを選択すると、 **[Patch]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-129">Selecting this option displays the dynamic options in section, **Patch**.</span></span>|  
  
 <span data-ttu-id="b81d6-130">**[SourceType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-130">**SourceType**</span></span>  
 <span data-ttu-id="b81d6-131">XML ドキュメントのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-131">Select the source type of the XML document.</span></span> <span data-ttu-id="b81d6-132">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-133">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-133">Value</span></span>|<span data-ttu-id="b81d6-134">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-135">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-135">**Direct input**</span></span>|<span data-ttu-id="b81d6-136">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-136">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-137">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-137">**File connection**</span></span>|<span data-ttu-id="b81d6-138">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-138">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-139">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-139">**Variable**</span></span>|<span data-ttu-id="b81d6-140">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-140">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-141">**ソース**</span><span class="sxs-lookup"><span data-stu-id="b81d6-141">**Source**</span></span>  
 <span data-ttu-id="b81d6-142">**[ソース]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-142">If **Source** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-143">**[ソース]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-143">If **Source** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-144">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-145">**[ソース]** が **[変数]** に設定されている場合は、既存の変数を選択するか、 **[\<New variable...>]** をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-145">If **Source** is set to **Variable**, select an existing variable, or click **\<New variable...>** to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-146">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-146">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
## <a name="operationtype-dynamic-options"></a><span data-ttu-id="b81d6-147">[OperationType] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="b81d6-147">OperationType Dynamic Options</span></span>  
  
### <a name="operationtype--validate"></a><span data-ttu-id="b81d6-148">[OperationType] = [Validate]</span><span class="sxs-lookup"><span data-stu-id="b81d6-148">OperationType = Validate</span></span>  
 <span data-ttu-id="b81d6-149">Validate 操作用のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-149">Specify options for the Validate operation.</span></span>  
  
 <span data-ttu-id="b81d6-150">**[SaveOperationResult]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-150">**SaveOperationResult**</span></span>  
 <span data-ttu-id="b81d6-151">XML タスクが Validate 操作の出力を保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-151">Specify whether the XML task saves the output of the Validate operation.</span></span>  
  
 <span data-ttu-id="b81d6-152">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-152">**OverwriteDestination**</span></span>  
 <span data-ttu-id="b81d6-153">対象となるファイルまたは変数を上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-153">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="b81d6-154">**宛先**</span><span class="sxs-lookup"><span data-stu-id="b81d6-154">**Destination**</span></span>  
 <span data-ttu-id="b81d6-155">既存のファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-155">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-156">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-156">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-157">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-157">**DestinationType**</span></span>  
 <span data-ttu-id="b81d6-158">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-158">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-159">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-159">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-160">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-160">Value</span></span>|<span data-ttu-id="b81d6-161">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-161">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-162">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-162">**File connection**</span></span>|<span data-ttu-id="b81d6-163">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-163">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-164">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-164">**Variable**</span></span>|<span data-ttu-id="b81d6-165">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-165">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-166">**[ValidationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-166">**ValidationType**</span></span>  
 <span data-ttu-id="b81d6-167">検証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-167">Select the validation type.</span></span> <span data-ttu-id="b81d6-168">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-168">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-169">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-169">Value</span></span>|<span data-ttu-id="b81d6-170">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-171">**[DTD]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-171">**DTD**</span></span>|<span data-ttu-id="b81d6-172">文書型定義 (DTD) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-172">Use a Document Type Definition (DTD).</span></span>|  
|<span data-ttu-id="b81d6-173">**[XSD]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-173">**XSD**</span></span>|<span data-ttu-id="b81d6-174">XML スキーマ定義 (XSD) スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-174">Use an XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="b81d6-175">このオプションを選択すると、 **[ValidationType]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-175">Selecting this option displays the dynamic options in section, **ValidationType**.</span></span>|  
  
 <span data-ttu-id="b81d6-176">**[FailOnValidationFail]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-176">**FailOnValidationFail**</span></span>  
 <span data-ttu-id="b81d6-177">ドキュメントの検証に失敗した場合に、操作が失敗するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-177">Specify whether the operation fails if the document fails to validate.</span></span>  
  
 <span data-ttu-id="b81d6-178">**[ValidationDetails]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-178">**ValidationDetails**</span></span>  
 <span data-ttu-id="b81d6-179">このプロパティの値が true の場合は、詳細なエラー出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-179">Provides rich error output when the value of this property is true.</span></span> <span data-ttu-id="b81d6-180">詳細については、「 [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b81d6-180">For more info, see [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md).</span></span>  
  
### <a name="validationtype-dynamic-options"></a><span data-ttu-id="b81d6-181">[ValidationType] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="b81d6-181">ValidationType Dynamic Options</span></span>  
  
#### <a name="validationtype--xsd"></a><span data-ttu-id="b81d6-182">[ValidationType] = [XSD]</span><span class="sxs-lookup"><span data-stu-id="b81d6-182">ValidationType = XSD</span></span>  
 <span data-ttu-id="b81d6-183">**[SecondOperandType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-183">**SecondOperandType**</span></span>  
 <span data-ttu-id="b81d6-184">2 番目の XML ドキュメントのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-184">Select the source type of the second XML document.</span></span> <span data-ttu-id="b81d6-185">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-185">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-186">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-186">Value</span></span>|<span data-ttu-id="b81d6-187">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-188">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-188">**Direct input**</span></span>|<span data-ttu-id="b81d6-189">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-189">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-190">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-190">**File connection**</span></span>|<span data-ttu-id="b81d6-191">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-191">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-192">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-192">**Variable**</span></span>|<span data-ttu-id="b81d6-193">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-193">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-194">**[SecondOperand]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-194">**SecondOperand**</span></span>  
 <span data-ttu-id="b81d6-195">**[SecondOperandType]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-195">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-196">**[SecondOperandType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-196">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-197">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-197">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-198">**[XPathStringSourceType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-198">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-199">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-199">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xslt"></a><span data-ttu-id="b81d6-200">[OperationType] = [XSLT]</span><span class="sxs-lookup"><span data-stu-id="b81d6-200">OperationType = XSLT</span></span>  
 <span data-ttu-id="b81d6-201">XSLT 操作用のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-201">Specify options for the XSLT operation.</span></span>  
  
 <span data-ttu-id="b81d6-202">**[SaveOperationResult]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-202">**SaveOperationResult**</span></span>  
 <span data-ttu-id="b81d6-203">XML タスクが XSLT 操作の出力を保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-203">Specify whether the XML task saves the output of the XSLT operation.</span></span>  
  
 <span data-ttu-id="b81d6-204">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-204">**OverwriteDestination**</span></span>  
 <span data-ttu-id="b81d6-205">対象となるファイルまたは変数を上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-205">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="b81d6-206">**宛先**</span><span class="sxs-lookup"><span data-stu-id="b81d6-206">**Destination**</span></span>  
 <span data-ttu-id="b81d6-207">**[DestinationType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-207">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-208">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-208">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-209">**[DestinationType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-209">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-210">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-210">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b81d6-211">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-211">**DestinationType**</span></span>  
 <span data-ttu-id="b81d6-212">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-212">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-213">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-213">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-214">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-214">Value</span></span>|<span data-ttu-id="b81d6-215">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-215">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-216">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-216">**File connection**</span></span>|<span data-ttu-id="b81d6-217">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-217">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-218">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-218">**Variable**</span></span>|<span data-ttu-id="b81d6-219">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-219">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-220">**[SecondOperandType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-220">**SecondOperandType**</span></span>  
 <span data-ttu-id="b81d6-221">2 番目の XML ドキュメントのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-221">Select the source type of the second XML document.</span></span> <span data-ttu-id="b81d6-222">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-222">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-223">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-223">Value</span></span>|<span data-ttu-id="b81d6-224">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-225">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-225">**Direct input**</span></span>|<span data-ttu-id="b81d6-226">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-226">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-227">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-227">**File connection**</span></span>|<span data-ttu-id="b81d6-228">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-228">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-229">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-229">**Variable**</span></span>|<span data-ttu-id="b81d6-230">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-230">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-231">**[SecondOperand]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-231">**SecondOperand**</span></span>  
 <span data-ttu-id="b81d6-232">**[SecondOperandType]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-232">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-233">**[SecondOperandType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-233">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-234">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-234">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-235">**[XPathStringSourceType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-235">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-236">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-236">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xpath"></a><span data-ttu-id="b81d6-237">[OperationType] = [XPath]</span><span class="sxs-lookup"><span data-stu-id="b81d6-237">OperationType = XPATH</span></span>  
 <span data-ttu-id="b81d6-238">XPath 操作用のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-238">Specify options for the XPath operation.</span></span>  
  
 <span data-ttu-id="b81d6-239">**[SaveOperationResult]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-239">**SaveOperationResult**</span></span>  
 <span data-ttu-id="b81d6-240">XML タスクが XPath 操作の出力を保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-240">Specify whether the XML task saves the output of the XPath operation.</span></span>  
  
 <span data-ttu-id="b81d6-241">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-241">**OverwriteDestination**</span></span>  
 <span data-ttu-id="b81d6-242">対象となるファイルまたは変数を上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-242">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="b81d6-243">**宛先**</span><span class="sxs-lookup"><span data-stu-id="b81d6-243">**Destination**</span></span>  
 <span data-ttu-id="b81d6-244">**[DestinationType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-244">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-245">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-245">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-246">**[DestinationType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-246">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-247">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-247">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b81d6-248">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-248">**DestinationType**</span></span>  
 <span data-ttu-id="b81d6-249">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-249">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-250">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-250">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-251">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-251">Value</span></span>|<span data-ttu-id="b81d6-252">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-252">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-253">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-253">**File connection**</span></span>|<span data-ttu-id="b81d6-254">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-254">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-255">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-255">**Variable**</span></span>|<span data-ttu-id="b81d6-256">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-256">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-257">**[SecondOperandType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-257">**SecondOperandType**</span></span>  
 <span data-ttu-id="b81d6-258">2 番目の XML ドキュメントのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-258">Select the source type of the second XML document.</span></span> <span data-ttu-id="b81d6-259">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-259">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-260">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-260">Value</span></span>|<span data-ttu-id="b81d6-261">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-261">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-262">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-262">**Direct input**</span></span>|<span data-ttu-id="b81d6-263">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-263">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-264">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-264">**File connection**</span></span>|<span data-ttu-id="b81d6-265">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-265">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-266">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-266">**Variable**</span></span>|<span data-ttu-id="b81d6-267">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-267">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-268">**[SecondOperand]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-268">**SecondOperand**</span></span>  
 <span data-ttu-id="b81d6-269">**[SecondOperandType]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-269">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-270">**[SecondOperandType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-270">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-271">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-271">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-272">**[XPathStringSourceType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-272">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-273">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-273">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b81d6-274">**[PutResultInOneNode]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-274">**PutResultInOneNode**</span></span>  
 <span data-ttu-id="b81d6-275">結果を 1 つのノードに記述するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-275">Specify whether the result is written to a single node.</span></span>  
  
 <span data-ttu-id="b81d6-276">**[XPathOperation]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-276">**XPathOperation**</span></span>  
 <span data-ttu-id="b81d6-277">XPath の結果の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-277">Select the XPath result type.</span></span> <span data-ttu-id="b81d6-278">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-278">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-279">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-279">Value</span></span>|<span data-ttu-id="b81d6-280">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-280">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-281">**評価**</span><span class="sxs-lookup"><span data-stu-id="b81d6-281">**Evaluation**</span></span>|<span data-ttu-id="b81d6-282">XPath 関数の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-282">Returns the results of an XPath function.</span></span>|  
|<span data-ttu-id="b81d6-283">**[ノード リスト]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-283">**Node list**</span></span>|<span data-ttu-id="b81d6-284">選択されたノードを XML フラグメントとして返します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-284">Return the selected nodes as an XML fragment.</span></span>|  
|<span data-ttu-id="b81d6-285">**値**</span><span class="sxs-lookup"><span data-stu-id="b81d6-285">**Values**</span></span>|<span data-ttu-id="b81d6-286">文字列に連結された、選択されたすべてのノードの内部テキスト値を返します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-286">Return the inner text value of all selected nodes, concatenated into a string.</span></span>|  
  
### <a name="operationtype--merge"></a><span data-ttu-id="b81d6-287">[OperationType] = [Merge]</span><span class="sxs-lookup"><span data-stu-id="b81d6-287">OperationType = Merge</span></span>  
 <span data-ttu-id="b81d6-288">Merge 操作用のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-288">Specify options for the Merge operation.</span></span>  
  
 <span data-ttu-id="b81d6-289">**[XPathStringSourceType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-289">**XPathStringSourceType**</span></span>  
 <span data-ttu-id="b81d6-290">XML ドキュメントのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-290">Select the source type of the XML document.</span></span> <span data-ttu-id="b81d6-291">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-291">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-292">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-292">Value</span></span>|<span data-ttu-id="b81d6-293">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-293">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-294">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-294">**Direct input**</span></span>|<span data-ttu-id="b81d6-295">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-295">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-296">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-296">**File connection**</span></span>|<span data-ttu-id="b81d6-297">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-297">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-298">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-298">**Variable**</span></span>|<span data-ttu-id="b81d6-299">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-299">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-300">**[XPathStringSource]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-300">**XPathStringSource**</span></span>  
 <span data-ttu-id="b81d6-301">**[XPathStringSourceType]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-301">If **XPathStringSourceType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-302">**[XPathStringSourceType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-302">If **XPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-303">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-303">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-304">**[XPathStringSourceType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-304">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-305">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-305">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="b81d6-306">XPath ステートメントを使用してソース ドキュメント内でのマージ場所を特定すると、このステートメントによって 1 つのノードが返されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-306">When you use an XPath statement to identify the merge location in the source document, this statement is expected to return a single node.</span></span> <span data-ttu-id="b81d6-307">ステートメントによって複数のノードが返された場合は、最初のノードだけが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-307">If the statement returns multiple nodes, only the first node is used.</span></span> <span data-ttu-id="b81d6-308">2 番目のドキュメントの内容は、XPath クエリによって返される最初のノードでマージされます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-308">The contents of the second document are merged under the first node that the XPath query returns.</span></span>  
  
 <span data-ttu-id="b81d6-309">**[SaveOperationResult]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-309">**SaveOperationResult**</span></span>  
 <span data-ttu-id="b81d6-310">XML タスクが Merge 操作の出力を保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-310">Specify whether the XML task saves the output of the Merge operation.</span></span>  
  
 <span data-ttu-id="b81d6-311">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-311">**OverwriteDestination**</span></span>  
 <span data-ttu-id="b81d6-312">対象となるファイルまたは変数を上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-312">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="b81d6-313">**宛先**</span><span class="sxs-lookup"><span data-stu-id="b81d6-313">**Destination**</span></span>  
 <span data-ttu-id="b81d6-314">**[DestinationType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-314">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-315">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-315">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-316">**[DestinationType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-316">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-317">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-317">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b81d6-318">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-318">**DestinationType**</span></span>  
 <span data-ttu-id="b81d6-319">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-319">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-320">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-320">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-321">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-321">Value</span></span>|<span data-ttu-id="b81d6-322">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-322">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-323">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-323">**File connection**</span></span>|<span data-ttu-id="b81d6-324">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-324">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-325">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-325">**Variable**</span></span>|<span data-ttu-id="b81d6-326">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-326">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-327">**[SecondOperandType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-327">**SecondOperandType**</span></span>  
 <span data-ttu-id="b81d6-328">2 番目の XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-328">Select the destination type of the second XML document.</span></span> <span data-ttu-id="b81d6-329">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-329">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-330">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-330">Value</span></span>|<span data-ttu-id="b81d6-331">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-331">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-332">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-332">**Direct input**</span></span>|<span data-ttu-id="b81d6-333">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-333">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-334">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-334">**File connection**</span></span>|<span data-ttu-id="b81d6-335">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-335">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-336">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-336">**Variable**</span></span>|<span data-ttu-id="b81d6-337">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-337">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-338">**[SecondOperand]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-338">**SecondOperand**</span></span>  
 <span data-ttu-id="b81d6-339">**[SecondOperandType]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-339">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-340">**[SecondOperandType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-340">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-341">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-341">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-342">**[SecondOperandType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-342">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-343">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-343">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--diff"></a><span data-ttu-id="b81d6-344">[OperationType] = [Diff]</span><span class="sxs-lookup"><span data-stu-id="b81d6-344">OperationType = Diff</span></span>  
 <span data-ttu-id="b81d6-345">Diff 操作用のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-345">Specify options for the Diff operation.</span></span>  
  
 <span data-ttu-id="b81d6-346">**[DiffAlgorithm]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-346">**DiffAlgorithm**</span></span>  
 <span data-ttu-id="b81d6-347">Diff アルゴリズムを選択して、文書を比較する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-347">Select the Diff algorithm to use when comparing documents.</span></span> <span data-ttu-id="b81d6-348">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-348">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-349">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-349">Value</span></span>|<span data-ttu-id="b81d6-350">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-350">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-351">**Auto**</span><span class="sxs-lookup"><span data-stu-id="b81d6-351">**Auto**</span></span>|<span data-ttu-id="b81d6-352">XML タスクに、高速アルゴリズムを使用するか、詳細アルゴリズムを使用するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-352">Let the XML task determine whether to use the fast or precise algorithm.</span></span>|  
|<span data-ttu-id="b81d6-353">**[高速]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-353">**Fast**</span></span>|<span data-ttu-id="b81d6-354">高速ではあるが詳細ではない Diff アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-354">Use a fast, but less precise Diff algorithm.</span></span>|  
|<span data-ttu-id="b81d6-355">**[詳細]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-355">**Precise**</span></span>|<span data-ttu-id="b81d6-356">詳細な Diff アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-356">Use a precise Diff algorithm.</span></span>|  
  
 <span data-ttu-id="b81d6-357">**[DiffOptions]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-357">**Diff Options**</span></span>  
 <span data-ttu-id="b81d6-358">Diff 操作に適用するための Diff オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-358">Set the Diff options to apply to the Diff operation.</span></span> <span data-ttu-id="b81d6-359">次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b81d6-359">The options are listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-360">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-360">Value</span></span>|<span data-ttu-id="b81d6-361">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-361">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-362">**[IgnoreXMLDeclaration]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-362">**IgnoreXMLDeclaration**</span></span>|<span data-ttu-id="b81d6-363">XML 宣言を比較するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-363">Specify whether to compare the XML declaration.</span></span>|  
|<span data-ttu-id="b81d6-364">**[IgnoreDTD]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-364">**IgnoreDTD**</span></span>|<span data-ttu-id="b81d6-365">文書型定義 (DTD) を無視するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-365">Specify whether to ignore the document type definition (DTD).</span></span>|  
|<span data-ttu-id="b81d6-366">**[IgnoreWhiteSpaces]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-366">**IgnoreWhite Spaces**</span></span>|<span data-ttu-id="b81d6-367">ドキュメントを比較するときに空白の量の違いを無視するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-367">Specify whether to ignore differences in the amount of white space when comparing documents.</span></span>|  
|<span data-ttu-id="b81d6-368">**[IgnoreNamespaces]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-368">**IgnoreNamespaces**</span></span>|<span data-ttu-id="b81d6-369">要素名および属性名の名前空間の URI (Uniform Resource Identifier) を比較するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-369">Specify whether to compare the namespace uniform resource identifier (URI) of an element and its attribute names.</span></span><br /><br /> <span data-ttu-id="b81d6-370">注: このオプションが `True` に設定されている場合、ローカル名が同じで、名前空間が異なる 2 つの要素は同一と見なされます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-370">Note: If this option is set to `True`, two elements that have the same local name but different namespaces are considered identical.</span></span>|  
|<span data-ttu-id="b81d6-371">**[IgnoreProcessingInstructions]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-371">**IgnoreProcessingInstructions**</span></span>|<span data-ttu-id="b81d6-372">処理命令を比較するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-372">Specify whether to compare processing instructions.</span></span>|  
|<span data-ttu-id="b81d6-373">**[IgnoreOrderOfChildElements]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-373">**IgnoreOrderOf ChildElements**</span></span>|<span data-ttu-id="b81d6-374">子の要素の順序を比較するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-374">Specify whether to compare the order of child elements.</span></span><br /><br /> <span data-ttu-id="b81d6-375">注: このオプションが `True` に設定されている場合、兄弟の一覧で位置のみが異なる子要素は同一と見なされます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-375">Note: If this option is set to `True`, child elements that differ only in their position in a list of siblings are considered identical.</span></span>|  
|<span data-ttu-id="b81d6-376">**[IgnoreComments]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-376">**IgnoreComments**</span></span>|<span data-ttu-id="b81d6-377">コメント ノードを比較するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-377">Specify whether to compare comment nodes.</span></span>|  
|<span data-ttu-id="b81d6-378">**[IgnorePrefixes]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-378">**IgnorePrefixes**</span></span>|<span data-ttu-id="b81d6-379">要素名および属性名のプレフィックスを比較するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-379">Specify whether to compare prefixes of element and attribute names.</span></span><br /><br /> <span data-ttu-id="b81d6-380">注: このオプションが `True` に設定されている場合、ローカル名が同じで、名前空間 URI とプレフィックスが異なる 2 つの要素は同一と見なされます。</span><span class="sxs-lookup"><span data-stu-id="b81d6-380">Note: If you set this option to `True`, two elements that have the same local name, but different namespace URIs and prefixes, are considered identical.</span></span>|  
  
 <span data-ttu-id="b81d6-381">**[FailOnDifference]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-381">**FailOnDifference**</span></span>  
 <span data-ttu-id="b81d6-382">Diff 操作が失敗した場合に、タスクが失敗するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-382">Specify whether the task fails if the Diff operation fails.</span></span>  
  
 <span data-ttu-id="b81d6-383">**[SaveDiffGram]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-383">**SaveDiffGram**</span></span>  
 <span data-ttu-id="b81d6-384">比較結果である DiffGram ドキュメントを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-384">Specify whether to save the comparison result, a DiffGram document.</span></span>  
  
 <span data-ttu-id="b81d6-385">**[SaveOperationResult]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-385">**SaveOperationResult**</span></span>  
 <span data-ttu-id="b81d6-386">XML タスクが Diff 操作の出力を保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-386">Specify whether the XML task saves the output of the Diff operation.</span></span>  
  
 <span data-ttu-id="b81d6-387">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-387">**OverwriteDestination**</span></span>  
 <span data-ttu-id="b81d6-388">対象となるファイルまたは変数を上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-388">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="b81d6-389">**宛先**</span><span class="sxs-lookup"><span data-stu-id="b81d6-389">**Destination**</span></span>  
 <span data-ttu-id="b81d6-390">**[DestinationType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-390">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-391">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-391">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-392">**[DestinationType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-392">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-393">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-393">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b81d6-394">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-394">**DestinationType**</span></span>  
 <span data-ttu-id="b81d6-395">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-395">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-396">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-396">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-397">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-397">Value</span></span>|<span data-ttu-id="b81d6-398">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-398">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-399">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-399">**File connection**</span></span>|<span data-ttu-id="b81d6-400">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-400">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-401">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-401">**Variable**</span></span>|<span data-ttu-id="b81d6-402">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-402">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-403">**[SecondOperandType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-403">**SecondOperandType**</span></span>  
 <span data-ttu-id="b81d6-404">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-404">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-405">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-405">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-406">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-406">Value</span></span>|<span data-ttu-id="b81d6-407">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-407">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-408">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-408">**Direct input**</span></span>|<span data-ttu-id="b81d6-409">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-409">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-410">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-410">**File connection**</span></span>|<span data-ttu-id="b81d6-411">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-411">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-412">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-412">**Variable**</span></span>|<span data-ttu-id="b81d6-413">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-413">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-414">**[SecondOperand]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-414">**SecondOperand**</span></span>  
 <span data-ttu-id="b81d6-415">**[SecondOperandType]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-415">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-416">**[SecondOperandType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-416">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-417">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-417">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-418">**[SecondOperandType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-418">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-419">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-419">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--patch"></a><span data-ttu-id="b81d6-420">[OperationType] = [Patch]</span><span class="sxs-lookup"><span data-stu-id="b81d6-420">OperationType = Patch</span></span>  
 <span data-ttu-id="b81d6-421">Patch 操作用のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-421">Specify options for the Patch operation.</span></span>  
  
 <span data-ttu-id="b81d6-422">**[SaveOperationResult]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-422">**SaveOperationResult**</span></span>  
 <span data-ttu-id="b81d6-423">XML タスクが Patch 操作の出力を保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-423">Specify whether the XML task saves the output of the Patch operation.</span></span>  
  
 <span data-ttu-id="b81d6-424">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-424">**OverwriteDestination**</span></span>  
 <span data-ttu-id="b81d6-425">対象となるファイルまたは変数を上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-425">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="b81d6-426">**宛先**</span><span class="sxs-lookup"><span data-stu-id="b81d6-426">**Destination**</span></span>  
 <span data-ttu-id="b81d6-427">**[DestinationType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-427">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-428">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-428">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-429">**[DestinationType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-429">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-430">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d6-430">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b81d6-431">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-431">**DestinationType**</span></span>  
 <span data-ttu-id="b81d6-432">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-432">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-433">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-433">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-434">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-434">Value</span></span>|<span data-ttu-id="b81d6-435">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-435">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-436">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-436">**File connection**</span></span>|<span data-ttu-id="b81d6-437">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-437">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-438">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-438">**Variable**</span></span>|<span data-ttu-id="b81d6-439">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-439">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-440">**[SecondOperandType]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-440">**SecondOperandType**</span></span>  
 <span data-ttu-id="b81d6-441">XML ドキュメントの対象となる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-441">Select the destination type of the XML document.</span></span> <span data-ttu-id="b81d6-442">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-442">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b81d6-443">値</span><span class="sxs-lookup"><span data-stu-id="b81d6-443">Value</span></span>|<span data-ttu-id="b81d6-444">説明</span><span class="sxs-lookup"><span data-stu-id="b81d6-444">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b81d6-445">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-445">**Direct input**</span></span>|<span data-ttu-id="b81d6-446">ソースを XML ドキュメントに設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-446">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b81d6-447">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-447">**File connection**</span></span>|<span data-ttu-id="b81d6-448">XML ドキュメントが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-448">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b81d6-449">**変数**</span><span class="sxs-lookup"><span data-stu-id="b81d6-449">**Variable**</span></span>|<span data-ttu-id="b81d6-450">ソースを XML ドキュメントが含まれている変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-450">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b81d6-451">**[SecondOperand]**</span><span class="sxs-lookup"><span data-stu-id="b81d6-451">**SecondOperand**</span></span>  
 <span data-ttu-id="b81d6-452">**[SecondOperandType]** が **[直接入力]** に設定されている場合は、XML コードを指定するか、省略記号ボタン **[...]** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-452">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b81d6-453">**[SecondOperandType]** が **[ファイル接続]** に設定されている場合は、ファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-453">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b81d6-454">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-454">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b81d6-455">**[SecondOperandType]** が **[変数]** に設定されている場合は、既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b81d6-455">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b81d6-456">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-456">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81d6-457">参照</span><span class="sxs-lookup"><span data-stu-id="b81d6-457">See Also</span></span>  
 <span data-ttu-id="b81d6-458">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b81d6-458">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b81d6-459">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="b81d6-459">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
