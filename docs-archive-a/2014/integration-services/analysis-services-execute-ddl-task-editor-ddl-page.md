---
title: Analysis Services DDL 実行タスクエディター ([DDL] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d207afe666e582c44f1014a6c80f4f4984fd5410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633980"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a><span data-ttu-id="64e3e-102">[Analysis Services DDL 実行タスク エディター] ([DDL] ページ)</span><span class="sxs-lookup"><span data-stu-id="64e3e-102">Analysis Services Execute DDL Task Editor (DDL Page)</span></span>
  <span data-ttu-id="64e3e-103">**[Analysis Services DDL 実行タスク エディター]** ダイアログ ボックスの **[DDL]** ページを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースへの接続を指定でき、データ定義言語 (DDL) ステートメントのソースについての情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="64e3e-103">Use the **DDL** page of the **Analysis Services Execute DDL Task Editor** dialog box to specify a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and to provide information about the source of data definition language (DDL) statements.</span></span>  
  
 <span data-ttu-id="64e3e-104">このタスクの詳細については、「 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md)」(Analysis Services DDL 実行タスク) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64e3e-104">To learn about this task, see [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="64e3e-105">静的オプション</span><span class="sxs-lookup"><span data-stu-id="64e3e-105">Static Options</span></span>  
 <span data-ttu-id="64e3e-106">**接続**</span><span class="sxs-lookup"><span data-stu-id="64e3e-106">**Connection**</span></span>  
 <span data-ttu-id="64e3e-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 接続マネージャーを一覧で選択するか、[\<**New connection...**>] をクリックし、 **[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-107">Select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager in the list, or click \<**New connection...**> and use the **Add Analysis Services Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="64e3e-108">**関連トピック:** [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)、[Analysis Services 接続マネージャー](connection-manager/analysis-services-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="64e3e-108">**Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)</span></span>  
  
 <span data-ttu-id="64e3e-109">**[SourceType]**</span><span class="sxs-lookup"><span data-stu-id="64e3e-109">**SourceType**</span></span>  
 <span data-ttu-id="64e3e-110">DDL ステートメントのソースの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-110">Specify the source type of the DDL statements.</span></span> <span data-ttu-id="64e3e-111">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="64e3e-111">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="64e3e-112">値</span><span class="sxs-lookup"><span data-stu-id="64e3e-112">Value</span></span>|<span data-ttu-id="64e3e-113">説明</span><span class="sxs-lookup"><span data-stu-id="64e3e-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64e3e-114">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="64e3e-114">**Direct Input**</span></span>|<span data-ttu-id="64e3e-115">**[SourceDirect]** テキスト ボックスに格納される DDL ステートメントへのソースを設定します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-115">Set the source to the DDL statement stored in the **SourceDirect** text box.</span></span> <span data-ttu-id="64e3e-116">この値を選択すると、次に示す動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64e3e-116">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="64e3e-117">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="64e3e-117">**File Connection**</span></span>|<span data-ttu-id="64e3e-118">DDL ステートメントを含むファイルへのソースを設定します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-118">Set the source to a file that contains the DDL statement.</span></span> <span data-ttu-id="64e3e-119">この値を選択すると、次に示す動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64e3e-119">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="64e3e-120">**変数**</span><span class="sxs-lookup"><span data-stu-id="64e3e-120">**Variable**</span></span>|<span data-ttu-id="64e3e-121">ソースを変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-121">Set the source to a variable.</span></span> <span data-ttu-id="64e3e-122">この値を選択すると、次に示す動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64e3e-122">Selecting this value displays the dynamic options in the following section.</span></span>|  
  
## <a name="dynamic-options"></a><span data-ttu-id="64e3e-123">動的オプション</span><span class="sxs-lookup"><span data-stu-id="64e3e-123">Dynamic Options</span></span>  
  
### <a name="sourcetype--direct-input"></a><span data-ttu-id="64e3e-124">[SourceType] = [直接入力]</span><span class="sxs-lookup"><span data-stu-id="64e3e-124">SourceType = Direct Input</span></span>  
 <span data-ttu-id="64e3e-125">**ソース**</span><span class="sxs-lookup"><span data-stu-id="64e3e-125">**Source**</span></span>  
 <span data-ttu-id="64e3e-126">DDL ステートメントを入力するか、参照ボタン ( **[...]** ) をクリックしてから **[DDL ステートメント]** ダイアログ ボックスでステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-126">Type the DDL statements or click the ellipsis **(...)** and then type the statements in the **DDL Statements** dialog box.</span></span>  
  
### <a name="sourcetype--file-connection"></a><span data-ttu-id="64e3e-127">[SourceType] = [ファイル接続]</span><span class="sxs-lookup"><span data-stu-id="64e3e-127">SourceType = File Connection</span></span>  
 <span data-ttu-id="64e3e-128">**ソース**</span><span class="sxs-lookup"><span data-stu-id="64e3e-128">**Source**</span></span>  
 <span data-ttu-id="64e3e-129">一覧でファイル接続を選択するか、[\<**New connection...**>] をクリックし、 **[ファイル接続マネージャー]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-129">Select a File connection in the list, or click \<**New connection...**> and use the **File Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="64e3e-130">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="64e3e-130">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
### <a name="sourcetype--variable"></a><span data-ttu-id="64e3e-131">[SourceType] = [変数]</span><span class="sxs-lookup"><span data-stu-id="64e3e-131">SourceType = Variable</span></span>  
 <span data-ttu-id="64e3e-132">**ソース**</span><span class="sxs-lookup"><span data-stu-id="64e3e-132">**Source**</span></span>  
 <span data-ttu-id="64e3e-133">一覧で変数を選択するか、[\<**New variable...**>] をクリックし、 **[変数の追加]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="64e3e-133">Select a variable in the list, or click \<**New variable...**> and use the **Add Variable** dialog box to create a new variable.</span></span>  
  
 <span data-ttu-id="64e3e-134">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="64e3e-134">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e3e-135">参照</span><span class="sxs-lookup"><span data-stu-id="64e3e-135">See Also</span></span>  
 <span data-ttu-id="64e3e-136">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="64e3e-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="64e3e-137">[Analysis Services DDL 実行タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="64e3e-137">[Analysis Services Execute DDL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="64e3e-138">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="64e3e-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="64e3e-139">[制御フロー](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="64e3e-139">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="64e3e-140">[Analysis Services スクリプト言語 &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span><span class="sxs-lookup"><span data-stu-id="64e3e-140">[Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span></span>  
 [<span data-ttu-id="64e3e-141">XML for Analysis (XML for Analysis) リファレンス</span><span class="sxs-lookup"><span data-stu-id="64e3e-141">XML for Analysis  &#40;XMLA&#41; Reference</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
