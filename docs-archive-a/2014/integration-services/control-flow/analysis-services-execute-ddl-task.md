---
title: Analysis Services DDL 実行タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.f1
helpviewer_keywords:
- Analysis Services Execute DDL task
- DDL
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a75bae174c816cdabd07ce688e068cbadb016b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641175"
---
# <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="2aa6f-102">Analysis Services DDL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="2aa6f-102">Analysis Services Execute DDL Task</span></span>
  <span data-ttu-id="2aa6f-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 実行タスクは、データ定義言語 (DDL) ステートメントを実行します。DDL ステートメントを使用すると、マイニング モデルや多次元オブジェクト (キューブおよびディメンションなど) を作成、削除、または変更できます。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task runs data definition language (DDL) statements that can create, drop, or alter mining models and multidimensional objects such as cubes and dimensions.</span></span> <span data-ttu-id="2aa6f-104">たとえば DDL ステートメントは、 **Adventure Works** キューブ内にパーティションを作成したり、 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]に含まれるサンプルの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のディメンションを削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-104">For example, a DDL statement can create a partition in the **Adventure Works** cube, or delete a dimension in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2aa6f-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 実行タスクは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトに接続します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-105">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="2aa6f-106">詳しくは、「 [Analysis Services 接続マネージャー](../connection-manager/analysis-services-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-106">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="2aa6f-107">には、分析オブジェクトの処理やデータ マイニング予測クエリの実行など、ビジネス インテリジェンス操作を実行する多数のタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-107">includes a number of tasks that perform business intelligence operations, such as processing analytic objects and running data mining prediction queries.</span></span>  
  
 <span data-ttu-id="2aa6f-108">関連するビジネス インテリジェンス タスクの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-108">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2aa6f-109">Analysis Services 処理タスク</span><span class="sxs-lookup"><span data-stu-id="2aa6f-109">Analysis Services Processing Task</span></span>](analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="2aa6f-110">データ マイニング クエリ タスク</span><span class="sxs-lookup"><span data-stu-id="2aa6f-110">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="ddl-statements"></a><span data-ttu-id="2aa6f-111">DDL ステートメント</span><span class="sxs-lookup"><span data-stu-id="2aa6f-111">DDL Statements</span></span>  
 <span data-ttu-id="2aa6f-112">DDL ステートメントは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) のステートメントとして表され、XML for Analysis (XMLA) コマンドで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-112">The DDL statements are represented as statements in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL), and framed in an XML for Analysis (XMLA) command.</span></span>  
  
-   <span data-ttu-id="2aa6f-113">ASSL は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス、それに含まれるデータベースやデータベース オブジェクトの定義、および記述に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-113">ASSL is used to define and describe an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and the databases and database objects it contains.</span></span> <span data-ttu-id="2aa6f-114">詳細については、「 [Analysis Services Scripting Language &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-114">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
-   <span data-ttu-id="2aa6f-115">XMLA は、Create、Alter、Process などのアクション コマンドを、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに送信する場合に使用されるコマンド言語です。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-115">XMLA is a command language that is used to send action commands, such as Create, Alter, or Process, to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="2aa6f-116">詳細については、「[XML for Analysis (XMLA) リファレンス](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-116">For more information, see [XML for Analysis  &#40;XMLA&#41; Reference](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).</span></span>  
  
 <span data-ttu-id="2aa6f-117">DDL コードが別のファイルに格納されている場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 実行タスクはファイル接続マネージャーを使用して、そのファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-117">If the DDL code is stored in a separate file, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses a File connection manager to specify the path of the file.</span></span> <span data-ttu-id="2aa6f-118">詳しくは「 [File Connection Manager](../connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-118">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="2aa6f-119">DDL ステートメントには、パスワードおよびその他の機微な情報が含まれる場合があるため、1 つ以上の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 実行タスクが含まれるパッケージでは、パッケージの保護レベル `EncryptAllWithUserKey` または `EncryptAllWithPassword` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-119">Because DDL statements can contain passwords and other sensitive information, a package that contains one or more [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL tasks should use the package protection level `EncryptAllWithUserKey` or `EncryptAllWithPassword`.</span></span> <span data-ttu-id="2aa6f-120">詳細については、「[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-120">For more information, see [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md).</span></span>  
  
### <a name="ddl-examples"></a><span data-ttu-id="2aa6f-121">DDL の例</span><span class="sxs-lookup"><span data-stu-id="2aa6f-121">DDL Examples</span></span>  
 <span data-ttu-id="2aa6f-122">次の 3 つの DDL ステートメントは、 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]に含まれる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースである、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスクリプト オブジェクトによって生成されたものです。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-122">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2aa6f-123">次の DDL ステートメントは、 **Promotion** ディメンションを削除します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-123">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="2aa6f-124">次の DDL ステートメントは、 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] キューブを処理します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-124">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="2aa6f-125">次の DDL ステートメントは、 **Forecasting** マイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-125">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 <span data-ttu-id="2aa6f-126">次の 3 つの DDL ステートメントは、 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]に含まれる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースである、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスクリプト オブジェクトによって生成されたものです。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-126">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2aa6f-127">次の DDL ステートメントは、 **Promotion** ディメンションを削除します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-127">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="2aa6f-128">次の DDL ステートメントは、 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] キューブを処理します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-128">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="2aa6f-129">次の DDL ステートメントは、 **Forecasting** マイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-129">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## <a name="configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="2aa6f-130">Analysis Services DDL 実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="2aa6f-130">Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="2aa6f-131">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2aa6f-132">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="2aa6f-133">[[Analysis Services DDL 実行タスク エディター] ([全般] ページ)](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="2aa6f-133">[Analysis Services Execute DDL Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="2aa6f-134">[[Analysis Services DDL 実行タスク エディター] ([DDL] ページ)](../analysis-services-execute-ddl-task-editor-ddl-page.md)</span><span class="sxs-lookup"><span data-stu-id="2aa6f-134">[Analysis Services Execute DDL Task Editor &#40;DDL Page&#41;](../analysis-services-execute-ddl-task-editor-ddl-page.md)</span></span>  
  
-   <span data-ttu-id="2aa6f-135">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="2aa6f-135">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="2aa6f-136">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-136">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="2aa6f-137">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="2aa6f-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="2aa6f-138">プログラムによる Analysis Services DDL 実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="2aa6f-138">Programmatic Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="2aa6f-139">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-139">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  
