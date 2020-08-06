---
title: 'Sql: identity 注釈と sql: guid 注釈を使用する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc5c08f158911edb0a1a0638fc4bcee1e05a248c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640867"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a><span data-ttu-id="ede43-102">sql:identity 注釈と sql:guid 注釈の使用</span><span class="sxs-lookup"><span data-stu-id="ede43-102">Using the sql:identity and sql:guid Annotations</span></span>
  <span data-ttu-id="ede43-103">`sql:identity` `sql:guid` のデータベース列にマップされている任意のノードの XSD スキーマで、注釈と注釈を指定でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ede43-103">You can specify the `sql:identity` and `sql:guid` annotations in an XSD schema on any node that maps to a database column in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ede43-104">アップデートグラムの形式では `updg:at-identity` 属性と `updg:guid` 属性がサポートされますが、DiffGram の形式ではこれらの属性はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ede43-104">Whereas the updategram format supports the `updg:at-identity` and `updg:guid` attributes, the DiffGram format does not.</span></span> <span data-ttu-id="ede43-105">`updg:at-identity` 属性では、IDENTITY 型の列を更新するときの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ede43-105">The `updg:at-identity` attribute defines the behavior in updating an IDENTITY-type column.</span></span> <span data-ttu-id="ede43-106">`updg:guid` 属性では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から GUID 値を取得でき、その値をアップデートグラムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ede43-106">The `updg:guid` attribute allows you to obtain a GUID value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and use it in the updategram.</span></span> <span data-ttu-id="ede43-107">詳細および作業サンプルについては、「 [XML アップデートグラムを使用したデータの挿入 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ede43-107">For more information and working samples, see [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="ede43-108">`sql:identity` 注釈と `sql:guid` 注釈を使用すると、この機能が DiffGram にも拡張されます。</span><span class="sxs-lookup"><span data-stu-id="ede43-108">The `sql:identity` and `sql:guid` annotations extend this functionality to DiffGrams.</span></span>  
  
 <span data-ttu-id="ede43-109">DiffGram を実行すると、DiffGram がアップデートグラムに変換された後、アップデートグラムが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ede43-109">When you execute a DiffGram, it is first converted to an updategram, and then the updategram is executed.</span></span> <span data-ttu-id="ede43-110">この場合、XSD スキーマで `sql:identity` 注釈と `sql:guid` 注釈を指定することで、アップデートグラムの動作を定義することになります。</span><span class="sxs-lookup"><span data-stu-id="ede43-110">By specifying the `sql:identity` and `sql:guid` annotations in the XSD schema, you are in fact defining the behavior of an updategram.</span></span> <span data-ttu-id="ede43-111">したがって、すべての注釈はアップデートグラムのコンテキストで記述します。</span><span class="sxs-lookup"><span data-stu-id="ede43-111">Therefore, all the annotations are described in the context of an updategram.</span></span> <span data-ttu-id="ede43-112">これらの注釈は DiffGram とアップデートグラムの両方で使用できますが、アップデートグラムには ID 値と GUID 値をより効率的に処理する機能が既に用意されています。</span><span class="sxs-lookup"><span data-stu-id="ede43-112">The annotations can be used both for DiffGrams and updategrams; however, updategrams already provide a more powerful way of handling identity and GUID values.</span></span>  
  
 <span data-ttu-id="ede43-113">`sql:identity` 注釈と `sql:guid` 注釈は、複合コンテンツを含む要素に定義できます。</span><span class="sxs-lookup"><span data-stu-id="ede43-113">The `sql:identity` and `sql:guid` annotations can be defined on a complex content element.</span></span>  
  
## <a name="sqlidentity-annotation"></a><span data-ttu-id="ede43-114">sql:identity 注釈</span><span class="sxs-lookup"><span data-stu-id="ede43-114">sql:identity Annotation</span></span>  
 <span data-ttu-id="ede43-115">`sql:identity` 注釈は、XSD スキーマで、IDENTITY 型のデータベース列にマップされる任意のノードに指定できます。</span><span class="sxs-lookup"><span data-stu-id="ede43-115">You can specify the `sql:identity` annotation in the XSD schema on any node that maps to an IDENTITY-type database column.</span></span> <span data-ttu-id="ede43-116">この注釈に指定された値は、ID 型列の更新方法を定義します (アップデートグラムで提供されている値を使用して列を変更するか、値を無視することによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] この列に対して生成された値が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="ede43-116">The value specified for this annotation defines how the IDENTITY-type column is updated (either by using the value provided in the updategram to modify the column or by ignoring the value, in which case a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-generated value is used for this column).</span></span>  
  
 <span data-ttu-id="ede43-117">`sql:identity` 注釈には次の 2 つの値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ede43-117">The `sql:identity` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="ede43-118">ignore</span><span class="sxs-lookup"><span data-stu-id="ede43-118">ignore</span></span>  
 <span data-ttu-id="ede43-119">アップデートグラムで列に提供される値を無視し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成される ID 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="ede43-119">Directs the updategram to ignore any value that is provided in the updategram for that column and to rely on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate the identity value.</span></span>  
  
 <span data-ttu-id="ede43-120">useValue</span><span class="sxs-lookup"><span data-stu-id="ede43-120">useValue</span></span>  
 <span data-ttu-id="ede43-121">アップデートグラムで提供される値を使用して、IDENTITY 型列を更新します。</span><span class="sxs-lookup"><span data-stu-id="ede43-121">Directs the updategram to use the value that is provided in the updategram to update the IDENTITY-type column.</span></span> <span data-ttu-id="ede43-122">アップデートグラムでは、列が ID 値かどうかは確認されません。</span><span class="sxs-lookup"><span data-stu-id="ede43-122">An updategram does not check whether the column is an identity value or not.</span></span>  
  
 <span data-ttu-id="ede43-123">アップデートグラムで IDENTITY 型列に値を指定する場合は、スキーマで `sql:identity="useValue"` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ede43-123">If the updategram specifies a value for the IDENTITY-type column, the `sql:identity="useValue"` must be specified in the schema.</span></span>  
  
## <a name="sqlguid-annotation"></a><span data-ttu-id="ede43-124">sql:guid 注釈</span><span class="sxs-lookup"><span data-stu-id="ede43-124">sql:guid Annotation</span></span>  
 <span data-ttu-id="ede43-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で GUID 値を生成し、その値をアップデートグラムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ede43-125">An updategram can have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generate a GUID value and then use this value in the updategram.</span></span> <span data-ttu-id="ede43-126">DiffGram のコンテキストでは `sql:guid` 注釈を使用して、列に対し SQL Server で生成される GUID 値を使用するか、アップデートグラムで提供される値を使用するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ede43-126">In the context of DiffGrams, you can use the `sql:guid` annotation to specify whether to use a GUID value that is generated by SQL Server or use the value that is provided in the updategram for that column.</span></span>  
  
 <span data-ttu-id="ede43-127">`sql:guid` 注釈には次の 2 つの値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ede43-127">The `sql:guid` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="ede43-128">generate</span><span class="sxs-lookup"><span data-stu-id="ede43-128">generate</span></span>  
 <span data-ttu-id="ede43-129">更新操作で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成される GUID を列に使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="ede43-129">Specifies that the GUID generated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] be used for that column in the update operation.</span></span>  
  
 <span data-ttu-id="ede43-130">useValue</span><span class="sxs-lookup"><span data-stu-id="ede43-130">useValue</span></span>  
 <span data-ttu-id="ede43-131">アップデートグラムで提供される値を列に使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="ede43-131">Specifies that the value specified in the updategram be used for the column.</span></span> <span data-ttu-id="ede43-132">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="ede43-132">This is the default value.</span></span>  
  
  
