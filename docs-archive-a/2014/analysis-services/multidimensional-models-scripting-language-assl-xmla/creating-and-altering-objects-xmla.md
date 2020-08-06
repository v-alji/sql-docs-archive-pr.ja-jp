---
title: オブジェクトの作成と変更 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2390c0b921368e7e06f0e5563a7eb59769d99c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644199"
---
# <a name="creating-and-altering-objects-xmla"></a><span data-ttu-id="7473e-102">オブジェクトの作成と変更 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="7473e-102">Creating and Altering Objects (XMLA)</span></span>
  <span data-ttu-id="7473e-103">主要なオブジェクトは、個別に作成、変更、削除することができます。</span><span class="sxs-lookup"><span data-stu-id="7473e-103">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="7473e-104">主要なオブジェクトには以下のオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7473e-104">Major objects include the following objects:</span></span>  
  
-   <span data-ttu-id="7473e-105">サーバー</span><span class="sxs-lookup"><span data-stu-id="7473e-105">Servers</span></span>  
  
-   <span data-ttu-id="7473e-106">データベース</span><span class="sxs-lookup"><span data-stu-id="7473e-106">Databases</span></span>  
  
-   <span data-ttu-id="7473e-107">Dimensions</span><span class="sxs-lookup"><span data-stu-id="7473e-107">Dimensions</span></span>  
  
-   <span data-ttu-id="7473e-108">キューブ</span><span class="sxs-lookup"><span data-stu-id="7473e-108">Cubes</span></span>  
  
-   <span data-ttu-id="7473e-109">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="7473e-109">Measure groups</span></span>  
  
-   <span data-ttu-id="7473e-110">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="7473e-110">Partitions</span></span>  
  
-   <span data-ttu-id="7473e-111">パースペクティブ</span><span class="sxs-lookup"><span data-stu-id="7473e-111">Perspectives</span></span>  
  
-   <span data-ttu-id="7473e-112">[マイニング モデル]</span><span class="sxs-lookup"><span data-stu-id="7473e-112">Mining models</span></span>  
  
-   <span data-ttu-id="7473e-113">ロール</span><span class="sxs-lookup"><span data-stu-id="7473e-113">Roles</span></span>  
  
-   <span data-ttu-id="7473e-114">サーバーまたはデータベースに関連付けられているコマンド</span><span class="sxs-lookup"><span data-stu-id="7473e-114">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="7473e-115">データ ソース</span><span class="sxs-lookup"><span data-stu-id="7473e-115">Data sources</span></span>  
  
 <span data-ttu-id="7473e-116">のインスタンスに主要なオブジェクトを作成するには[create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)コマンドを使用し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの既存の主要なオブジェクトを変更するには[alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7473e-116">You use the [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) command to create a major object on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and the [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command to alter an existing major object on an instance.</span></span> <span data-ttu-id="7473e-117">どちらのコマンドも、 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="7473e-117">Both commands are run using the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="7473e-118">オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="7473e-118">Creating Objects</span></span>  
 <span data-ttu-id="7473e-119">`Create` メソッドを使用してオブジェクトを作成する場合は、まず、作成する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを含む親オブジェクトを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7473e-119">When you create objects by using the `Create` method, you must first identify the parent object that contains the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object to be created.</span></span> <span data-ttu-id="7473e-120">親オブジェクトを特定するには、コマンドの[ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティにオブジェクト参照を指定し `Create` ます。</span><span class="sxs-lookup"><span data-stu-id="7473e-120">You identify the parent object by providing an object reference in the [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Create` command.</span></span> <span data-ttu-id="7473e-121">それぞれのオブジェクト参照には、`Create` コマンドの対象の親オブジェクトを一意に識別するのに必要なオブジェクト識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7473e-121">Each object reference contains the object identifiers needed to uniquely identify the parent object for the `Create` command.</span></span> <span data-ttu-id="7473e-122">オブジェクト参照の詳細については、「 [XMLA&#41;&#40;オブジェクトの定義と識別](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7473e-122">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="7473e-123">たとえば、キューブに新しいメジャー グループを作成するには、キューブへのオブジェクト参照を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7473e-123">For example, you must provide an object reference to a cube to create a new measure group for the cube.</span></span> <span data-ttu-id="7473e-124">`ParentObject` プロパティでのキューブへのオブジェクト参照には、データベース識別子とキューブ識別子の両方が含まれます。別のデータベースでも同じキューブ識別子が使用されている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="7473e-124">The object reference for the cube in the `ParentObject` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="7473e-125">[Objectdefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)要素には、作成する主要なオブジェクトを定義する Analysis Services スクリプト言語 (assl) 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7473e-125">The [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) element contains Analysis Services Scripting Language (ASSL) elements that define the major object to be created.</span></span> <span data-ttu-id="7473e-126">ASSL の詳細については、「 [Analysis Services スクリプト言語 &#40;assl&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7473e-126">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="7473e-127">`AllowOverwrite` コマンドの `Create` 属性を true に設定すると、指定された識別子を持つ既存の主要なオブジェクトを上書きできます。</span><span class="sxs-lookup"><span data-stu-id="7473e-127">If you set the `AllowOverwrite` attribute of the `Create` command to true, you can overwrite an existing major object that has the specified identifier.</span></span> <span data-ttu-id="7473e-128">そうしない場合、親オブジェクト内に指定された識別子を持つ主要なオブジェクトが既に存在するときに、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7473e-128">Otherwise, an error occurs if a major object that has the specified identifier already exists in the parent object.</span></span>  
  
 <span data-ttu-id="7473e-129">コマンドの詳細につい `Create` ては、「 [Create ELEMENT &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7473e-129">For more information about the `Create` command, see [Create Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).</span></span>  
  
### <a name="creating-session-objects"></a><span data-ttu-id="7473e-130">セッション オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="7473e-130">Creating Session Objects</span></span>  
 <span data-ttu-id="7473e-131">セッション オブジェクトは一時オブジェクトであり、クライアント アプリケーションで使用される明示的または暗黙的なセッションでのみ使用でき、セッションの終了時には削除されます。</span><span class="sxs-lookup"><span data-stu-id="7473e-131">Session objects are temporary objects that are available only to the explicit or implicit session used by a client application and are deleted when the session is ended.</span></span> <span data-ttu-id="7473e-132">セッションオブジェクトを作成するには、 `Scope` コマンドの属性 `Create` を*session*に設定します。</span><span class="sxs-lookup"><span data-stu-id="7473e-132">You can create session objects by setting the `Scope` attribute of the `Create` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7473e-133">*セッション*設定を使用する場合、 `ObjectDefinition` 要素には[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)、または[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) assl の要素のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7473e-133">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="altering-objects"></a><span data-ttu-id="7473e-134">オブジェクトの変更</span><span class="sxs-lookup"><span data-stu-id="7473e-134">Altering Objects</span></span>  
 <span data-ttu-id="7473e-135">メソッドを使用してオブジェクトを変更する場合は、 `Alter` まず、コマンドの[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティにオブジェクト参照を指定することによって、変更するオブジェクトを特定する必要があり `Alter` ます。</span><span class="sxs-lookup"><span data-stu-id="7473e-135">When modifying objects by using the `Alter` method, you must first identify the object to be modified by providing an object reference in the [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Alter` command.</span></span> <span data-ttu-id="7473e-136">それぞれのオブジェクト参照には、`Alter` コマンドの対象のオブジェクトを一意に識別するのに必要なオブジェクト識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7473e-136">Each object reference contains the object identifiers needed to uniquely identify the object for the `Alter` command.</span></span> <span data-ttu-id="7473e-137">オブジェクト参照の詳細については、「 [XMLA&#41;&#40;オブジェクトの定義と識別](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7473e-137">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="7473e-138">たとえば、キューブの構造を変更するためには、キューブへのオブジェクト参照を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7473e-138">For example, you must provide an object reference to a cube in order to modify the structure of a cube.</span></span> <span data-ttu-id="7473e-139">`Object` プロパティでのキューブへのオブジェクト参照には、データベース識別子とキューブ識別子の両方が含まれます。別のデータベースでも同じキューブ識別子が使用されている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="7473e-139">The object reference for the cube in the `Object` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="7473e-140">`ObjectDefinition` 要素には、変更する主要なオブジェクトを定義する ASSL 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7473e-140">The `ObjectDefinition` element contains ASSL elements that define the major object to be modified.</span></span> <span data-ttu-id="7473e-141">ASSL の詳細については、「 [Analysis Services スクリプト言語 &#40;assl&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7473e-141">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="7473e-142">`AllowCreate` コマンドの `Alter` 属性を true に設定すると、指定された主要なオブジェクトが存在しない場合に、それを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7473e-142">If you set the `AllowCreate` attribute of the `Alter` command to true, you can create the specified major object if the object does not exist.</span></span> <span data-ttu-id="7473e-143">そうしない場合、指定された主要なオブジェクトが存在していないときに、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7473e-143">Otherwise, an error occurs if a specified major object does not already exist.</span></span>  
  
### <a name="using-the-objectexpansion-attribute"></a><span data-ttu-id="7473e-144">ObjectExpansion 属性の使用</span><span class="sxs-lookup"><span data-stu-id="7473e-144">Using the ObjectExpansion Attribute</span></span>  
 <span data-ttu-id="7473e-145">主要なオブジェクトのプロパティのみを変更し、主要なオブジェクトに含まれているマイナーオブジェクトを再定義しない場合は、 `ObjectExpansion` コマンドの属性 `Alter` を*objectproperties*に設定できます。</span><span class="sxs-lookup"><span data-stu-id="7473e-145">If you are changing only the properties of the major object and are not redefining minor objects that are contained by the major object, you can set the `ObjectExpansion` attribute of the `Alter` command to *ObjectProperties*.</span></span> <span data-ttu-id="7473e-146">`ObjectDefinition` プロパティには、主要なオブジェクトのプロパティに対応する要素だけを含めればよく、その場合 `Alter` コマンドは主要なオブジェクトに関連付けられている副次オブジェクトに変更を加えません。</span><span class="sxs-lookup"><span data-stu-id="7473e-146">The `ObjectDefinition` property then only has to contain the elements for the properties of the major object, and the `Alter` command leaves minor objects associated with the major object untouched.</span></span>  
  
 <span data-ttu-id="7473e-147">主要なオブジェクトの副オブジェクトを再定義するには、 `ObjectExpansion` 属性を*expandfull*に設定し、オブジェクト定義に、主要なオブジェクトに含まれるすべてのマイナーオブジェクトを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="7473e-147">To redefine minor objects for a major object, you must set the `ObjectExpansion` attribute to *ExpandFull* and the object definition must include all minor objects that are contained by the major object.</span></span> <span data-ttu-id="7473e-148">`ObjectDefinition` コマンドの `Alter` プロパティに、主要なオブジェクトに格納される副次オブジェクトが明示的に含められていない場合、含まれない副次オブジェクトは削除されます。</span><span class="sxs-lookup"><span data-stu-id="7473e-148">If the `ObjectDefinition` property of the `Alter` command does not explicitly include a minor object that is contained by the major object, the minor object that was not included is deleted.</span></span>  
  
### <a name="altering-session-objects"></a><span data-ttu-id="7473e-149">セッション オブジェクトの変更</span><span class="sxs-lookup"><span data-stu-id="7473e-149">Altering Session Objects</span></span>  
 <span data-ttu-id="7473e-150">コマンドによって作成されたセッションオブジェクトを変更するには、 `Create` `Scope` コマンドの属性 `Alter` を*session*に設定します。</span><span class="sxs-lookup"><span data-stu-id="7473e-150">To modify session objects created by the `Create` command, set the `Scope` attribute of the `Alter` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7473e-151">*セッション*設定を使用する場合、 `ObjectDefinition` 要素には[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)、または[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) assl の要素のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7473e-151">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="creating-or-altering-subordinate-objects"></a><span data-ttu-id="7473e-152">下位オブジェクトの作成または変更</span><span class="sxs-lookup"><span data-stu-id="7473e-152">Creating or Altering Subordinate Objects</span></span>  
 <span data-ttu-id="7473e-153">`Create` または `Alter` コマンドで作成または変更できるのは最上位の主要なオブジェクトだけですが、作成中または変更中の主要なオブジェクトには、囲んでいる `ObjectDefinition` プロパティの中に、従属する他の主要なオブジェクトや副次オブジェクトの定義を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7473e-153">Although a `Create` or `Alter` command creates or alters only one topmost major object, the major object being created or modified can contain definitions within the enclosing `ObjectDefinition` property for other major and minor objects that are subordinate to it.</span></span> <span data-ttu-id="7473e-154">たとえば、キューブを定義する場合、`ParentObject` で親データベースを指定します。`ObjectDefinition` でのキューブ定義にはキューブのメジャー グループを定義でき、さらにメジャー グループ内ではそれぞれのメジャー グループのパーティションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="7473e-154">For example, if you define a cube, you specify the parent database in `ParentObject`, and within the cube definition in `ObjectDefinition` you can define measure groups for the cube, and within the measure groups you can define partitions for each measure group.</span></span> <span data-ttu-id="7473e-155">副次オブジェクトは、それを格納する主要なオブジェクトの中でのみ定義できます。</span><span class="sxs-lookup"><span data-stu-id="7473e-155">A minor object can be defined only under the major object that contains it.</span></span> <span data-ttu-id="7473e-156">メジャーおよびマイナーオブジェクトの詳細については、「[データベースオブジェクト &#40;Analysis Services-多次元データ&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7473e-156">For more information about major and minor objects, see [Database Objects &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7473e-157">例</span><span class="sxs-lookup"><span data-stu-id="7473e-157">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="7473e-158">説明</span><span class="sxs-lookup"><span data-stu-id="7473e-158">Description</span></span>  
 <span data-ttu-id="7473e-159">次の例では、サンプルデータベースを参照するリレーショナルデータソースを作成し [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7473e-159">The following example creates a relational data source that references the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7473e-160">コード</span><span class="sxs-lookup"><span data-stu-id="7473e-160">Code</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a><span data-ttu-id="7473e-161">説明</span><span class="sxs-lookup"><span data-stu-id="7473e-161">Description</span></span>  
 <span data-ttu-id="7473e-162">次の例では、前の例で作成されたリレーショナル データ ソースを変更して、データ ソースのクエリ タイムアウトを 30 秒に設定します。</span><span class="sxs-lookup"><span data-stu-id="7473e-162">The following example alters the relational data source created in the previous example to set the query time-out for the data source to 30 seconds.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7473e-163">コード</span><span class="sxs-lookup"><span data-stu-id="7473e-163">Code</span></span>  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a><span data-ttu-id="7473e-164">説明</span><span class="sxs-lookup"><span data-stu-id="7473e-164">Comments</span></span>  
 <span data-ttu-id="7473e-165">`ObjectExpansion`コマンドの属性 `Alter` が*objectproperties*に設定されました。</span><span class="sxs-lookup"><span data-stu-id="7473e-165">The `ObjectExpansion` attribute of the `Alter` command was set to *ObjectProperties*.</span></span> <span data-ttu-id="7473e-166">この設定により、 [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)要素 (マイナーオブジェクト) を、で定義されているデータソースから除外でき `ObjectDefinition` ます。</span><span class="sxs-lookup"><span data-stu-id="7473e-166">This setting allows the [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) element, a minor object, to be excluded from the data source defined in `ObjectDefinition`.</span></span> <span data-ttu-id="7473e-167">そのため、そのデータ ソースに関する権限借用情報は、最初の例で指定したとおりにサービス アカウントに対して設定されたままになります。</span><span class="sxs-lookup"><span data-stu-id="7473e-167">Therefore, the impersonation information for that data source remains set to the service account, as specified in the first example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7473e-168">参照</span><span class="sxs-lookup"><span data-stu-id="7473e-168">See Also</span></span>  
 <span data-ttu-id="7473e-169">[XMLA&#41;&#40;メソッドの実行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span><span class="sxs-lookup"><span data-stu-id="7473e-169">[Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span></span>  
 <span data-ttu-id="7473e-170">[Analysis Services スクリプト言語 &#40;ASSL&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="7473e-170">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="7473e-171">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="7473e-171">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
