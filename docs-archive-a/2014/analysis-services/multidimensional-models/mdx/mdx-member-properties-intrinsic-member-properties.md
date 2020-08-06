---
title: 固有メンバープロパティ (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- intrinsic member properties [MDX]
ms.assetid: 84e6fe64-9b37-4e79-bedf-ae02e80bfce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 268203d044734bb4e6a1d2acf6311ee7ef828a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714642"
---
# <a name="intrinsic-member-properties-mdx"></a><span data-ttu-id="e92e1-102">固有メンバー プロパティ (MDX)</span><span class="sxs-lookup"><span data-stu-id="e92e1-102">Intrinsic Member Properties (MDX)</span></span>
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="e92e1-103">は、カスタム アプリケーションで使用する追加のデータまたはメタデータを返したり、モデルの調査や構築を支援したりするために、クエリに含めることができるディメンション メンバーの固有プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-103">exposes intrinsic properties on dimension members that you can include in a query to return additional data or metadata for use in a custom application, or to assist in model investigation or construction.</span></span> <span data-ttu-id="e92e1-104">SQL Server クライアント ツールを使用している場合は、SQL Server Management Studio (SSMS) で固有プロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-104">If you are using the SQL Server client tools, you can view intrinsic properties in SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="e92e1-105">固有プロパティには `ID`、`KEY`、`KEYx`、および `NAME` があります。これらは、各メンバーによって任意のレベルで公開されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-105">Intrinsic properties include `ID`, `KEY`, `KEYx`, and `NAME`, which are properties exposed by every member, at any level.</span></span> <span data-ttu-id="e92e1-106">また、特に `LEVEL_NUMBER` や `PARENT_UNIQUE_NAME` などの位置情報を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-106">You can also return positional information, such as `LEVEL_NUMBER` or `PARENT_UNIQUE_NAME`, among others.</span></span>  
  
 <span data-ttu-id="e92e1-107">クエリの作成方法や、クエリの実行に使用しているクライアント アプリケーションに応じて、メンバー プロパティが結果セットに表示される場合と表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e92e1-107">Depending on how you construct the query, and on the client application you are using to execute queries, member properties may or may not be visible in the result set.</span></span> <span data-ttu-id="e92e1-108">クエリのテストまたは実行に SQL Server Management Studio を使用している場合は、結果セットのメンバーをダブルクリックして [メンバーのプロパティ] ダイアログ ボックスを開くと、各固有メンバー プロパティの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-108">If you are using SQL Server Management Studio to test or run queries, you can double-click a member in the result set to open the Member Properties dialog box, showing the values for each intrinsic member property.</span></span>  
  
 <span data-ttu-id="e92e1-109">ディメンション メンバー プロパティの使用および表示の概要については、「 [SSMS で MDX クエリ ウィンドウ内の SSAS メンバー プロパティを表示する](https://go.microsoft.com/fwlink/?LinkId=317362)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-109">For an introduction to using and viewing dimension member properties, see [Viewing SSAS Member Properties within an MDX Query Window in SSMS](https://go.microsoft.com/fwlink/?LinkId=317362).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e92e1-110">1999年3月 (2.6) の OLE DB 仕様の OLAP セクションに準拠しているプロバイダーは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] このトピックに記載されている固有メンバープロパティをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e92e1-110">As a provider that is compliant with the OLAP section of the OLE DB specification dated March 1999 (2.6), [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supports the intrinsic member properties listed in this topic.</span></span>  
>   
>  <span data-ttu-id="e92e1-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 以外のプロバイダーは、この他にも追加の固有メンバー プロパティをサポートする場合があります。</span><span class="sxs-lookup"><span data-stu-id="e92e1-111">Providers other than [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] may support additional intrinsic member properties.</span></span> <span data-ttu-id="e92e1-112">他のプロバイダーによってサポートされる固有メンバー プロパティについての詳細は、各プロバイダーに付属の資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-112">For more information about the intrinsic member properties supported by other providers, refer to the documentation that comes with those providers.</span></span>  
  
## <a name="types-of-member-properties"></a><span data-ttu-id="e92e1-113">メンバー プロパティの種類</span><span class="sxs-lookup"><span data-stu-id="e92e1-113">Types of Member Properties</span></span>  
 <span data-ttu-id="e92e1-114">でサポートされる固有メンバープロパティに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は、次の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="e92e1-114">The intrinsic member properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] are of two types:</span></span>  
  
 <span data-ttu-id="e92e1-115">状況依存メンバー プロパティ</span><span class="sxs-lookup"><span data-stu-id="e92e1-115">Context sensitive member properties</span></span>  
 <span data-ttu-id="e92e1-116">この種類のメンバー プロパティは、特定の階層またはレベルのコンテキストで使用する必要があり、特定のディメンションまたはレベルの各メンバーに関する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-116">These member properties must be used in the context of a specific hierarchy or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="e92e1-117">次の例で、`KEY` プロパティのパスがどのように含まれているかを確認してください: `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`。</span><span class="sxs-lookup"><span data-stu-id="e92e1-117">Notice how the following example includes the path for the `KEY` property: `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`.</span></span>  
  
 <span data-ttu-id="e92e1-118">非状況依存メンバー プロパティ</span><span class="sxs-lookup"><span data-stu-id="e92e1-118">Non-context sensitive member properties</span></span>  
 <span data-ttu-id="e92e1-119">この種類のメンバー プロパティは、特定のディメンションまたはレベルのコンテキストで使用できず、軸上のすべてのメンバーに関する値を返します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-119">These member properties cannot be used in the context of a specific dimension or level, and return values for all members on an axis.</span></span>  
  
 <span data-ttu-id="e92e1-120">非状況依存のプロパティはスタンドアロンであり、パス情報を含みません。</span><span class="sxs-lookup"><span data-stu-id="e92e1-120">Context-insensitive properties standalone and do not include path information.</span></span> <span data-ttu-id="e92e1-121">次の例で、`PARENT_UNIQUE_NAME` にディメンションまたはレベルが指定されていないことを確認してください: `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span><span class="sxs-lookup"><span data-stu-id="e92e1-121">Notice how there is no dimension or level specified for `PARENT_UNIQUE_NAME` in the following example: `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span></span>  
  
 <span data-ttu-id="e92e1-122">固有メンバー プロパティが状況依存/非状況依存のどちらの場合にも、次のような使用上の規則があります。</span><span class="sxs-lookup"><span data-stu-id="e92e1-122">Regardless of whether the intrinsic member property is context sensitive or not, the following usage rules apply:</span></span>  
  
-   <span data-ttu-id="e92e1-123">軸上に射影されているディメンション メンバーに関連する固有メンバー プロパティだけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-123">You can specify only those intrinsic member properties that relate to dimension members that are projected on the axis.</span></span>  
  
-   <span data-ttu-id="e92e1-124">状況依存メンバー プロパティに対する要求を非状況依存固有メンバー プロパティと同じクエリの中に混合できます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-124">You can mix requests for context sensitive member properties in the same query with non-context sensitive intrinsic member properties.</span></span>  
  
-   <span data-ttu-id="e92e1-125">プロパティを照会するには、キーワード `PROPERTIES` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-125">You use the `PROPERTIES` keyword to query for the properties.</span></span>  
  
 <span data-ttu-id="e92e1-126">以下のセクションでは、で使用できるさまざまな状況依存の固有メンバープロパティと、非状況依存の固有メンバープロパティの両方につい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] て説明し `PROPERTIES` ます。また、キーワードを各種類のプロパティと共に使用する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-126">The following sections describe both the various context sensitive and non-context sensitive intrinsic member properties available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], and how to use the `PROPERTIES` keyword with each type of property.</span></span>  
  
## <a name="context-sensitive-member-properties"></a><span data-ttu-id="e92e1-127">状況依存メンバー プロパティ</span><span class="sxs-lookup"><span data-stu-id="e92e1-127">Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="e92e1-128">すべてのディメンション メンバーとレベル メンバーでは、状況に依存する固有メンバー プロパティがいくつかサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-128">All dimension members and level members support a list of intrinsic member properties that are context sensitive.</span></span> <span data-ttu-id="e92e1-129">次の表は、それらの状況依存プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="e92e1-129">The following table lists these context-sensitive properties.</span></span>  
  
|<span data-ttu-id="e92e1-130">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e92e1-130">Property</span></span>|<span data-ttu-id="e92e1-131">説明</span><span class="sxs-lookup"><span data-stu-id="e92e1-131">Description</span></span>|  
|--------------|-----------------|  
|`ID`|<span data-ttu-id="e92e1-132">内部的に管理されるメンバー ID。</span><span class="sxs-lookup"><span data-stu-id="e92e1-132">The internally maintained ID for the member.</span></span>|  
|`Key`|<span data-ttu-id="e92e1-133">元のデータ型でのメンバー キーの値。</span><span class="sxs-lookup"><span data-stu-id="e92e1-133">The value of the member key in the original data type.</span></span> <span data-ttu-id="e92e1-134">MEMBER_KEY は、旧バージョンとの互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="e92e1-134">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="e92e1-135">MEMBER_KEY プロパティの値は、非複合キーについては KEY0 と等しく、複合キーについては NULL です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-135">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`KEYx`|<span data-ttu-id="e92e1-136">メンバーのキー (x はキーの序数で、0 から始まります)。</span><span class="sxs-lookup"><span data-stu-id="e92e1-136">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="e92e1-137">KEY0 は複合キーおよび非複合キーで使用できますが、主に複合キーで使用されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-137">KEY0 is available for composite and non-composite keys, but primarily used for composite keys.</span></span><br /><br /> <span data-ttu-id="e92e1-138">複合キーの場合、KEY0、KEY1、KEY2 などは、全体として複合キーを形成します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-138">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="e92e1-139">クエリでそれぞれを個別に使用すると、複合キーのその部分を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-139">You can use each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="e92e1-140">たとえば、KEY0 を指定すると複合キーの最初の部分が返され、KEY1 を指定すると複合キーの次の部分が返されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-140">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="e92e1-141">キーが非複合キーの場合、KEY0 は `Key` と同じです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-141">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="e92e1-142">`KEYx` は、コンテキストの有無にかかわらず使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-142">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="e92e1-143">このため、両方の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-143">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="e92e1-144">このメンバー プロパティの使用方法の例については、「 [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364)」(単純な MDX の情報: Key0、Key1、Key2) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-144">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|`Name`|<span data-ttu-id="e92e1-145">メンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-145">The name of the member.</span></span>|  
  
### <a name="properties-syntax-for-context-sensitive-properties"></a><span data-ttu-id="e92e1-146">状況依存プロパティの PROPERTIES の構文</span><span class="sxs-lookup"><span data-stu-id="e92e1-146">PROPERTIES Syntax for Context Sensitive Properties</span></span>  
 <span data-ttu-id="e92e1-147">この種類のメンバー プロパティは、特定のディメンションまたはレベルのコンテキストで使用し、特定のディメンションまたはレベルの各メンバーに関する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-147">You use these member properties in the context of a specific dimension or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="e92e1-148">ディメンション メンバー プロパティの場合、プロパティ名の前に、そのプロパティが適用されるディメンションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-148">For dimension member properties, you precede the name of the property with the name of the dimension to which the property applies.</span></span> <span data-ttu-id="e92e1-149">次の例は、適切な構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="e92e1-149">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES Dimension.Property_name`  
  
 <span data-ttu-id="e92e1-150">レベル メンバー プロパティの場合、プロパティ名の前にレベル名だけを指定するか、プロパティ名の前にディメンション名とレベル名を両方とも指定することができます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-150">For a level member property, you can precede the name of the property with just the level name or, for additional specification, both the dimension and level name.</span></span> <span data-ttu-id="e92e1-151">次の例は、適切な構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="e92e1-151">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.Property_name`  
  
 <span data-ttu-id="e92e1-152">たとえば、 `[Sales]` ディメンション内で参照される各メンバーのすべての名前を取得する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="e92e1-152">To illustrate, you would like to return all the names of each referenced member in the `[Sales]` dimension.</span></span> <span data-ttu-id="e92e1-153">それらの名前を返すには、多次元 (MDX) クエリで次のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-153">To return these names, you would use the following statement in a Multidimensional Expressions (MDX) query:</span></span>  
  
 `DIMENSION PROPERTIES [Sales].Name`  
  
## <a name="non-context-sensitive-member-properties"></a><span data-ttu-id="e92e1-154">非状況依存メンバー プロパティ</span><span class="sxs-lookup"><span data-stu-id="e92e1-154">Non-Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="e92e1-155">すべてのメンバーでは、コンテキストに関係なく同じである固有メンバー プロパティがいくつかサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-155">All members support a list of intrinsic member properties that are the same regardless of context.</span></span> <span data-ttu-id="e92e1-156">これらのプロパティが提供する追加情報をアプリケーションで使用すれば、ユーザー エクスペリエンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-156">These properties provide additional information that can be used by applications to enhance the user's experience.</span></span>  
  
 <span data-ttu-id="e92e1-157">次の表に、でサポートされる非状況依存の固有プロパティを示し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-157">The following table lists the non-context sensitive intrinsic properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e92e1-158">MEMBERS スキーマ行セット内の列は、以下の表に示されている固有メンバー プロパティをサポートします。</span><span class="sxs-lookup"><span data-stu-id="e92e1-158">Columns in the MEMBERS schema rowset support the intrinsic member properties listed in the following table.</span></span> <span data-ttu-id="e92e1-159">スキーマ行セットの詳細については `MEMBERS` 、「 [MDSCHEMA_MEMBERS 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-159">For more information about the `MEMBERS` schema rowset, see [MDSCHEMA_MEMBERS Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset).</span></span>  
  
|<span data-ttu-id="e92e1-160">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e92e1-160">Property</span></span>|<span data-ttu-id="e92e1-161">説明</span><span class="sxs-lookup"><span data-stu-id="e92e1-161">Description</span></span>|  
|--------------|-----------------|  
|`CATALOG_NAME`|<span data-ttu-id="e92e1-162">このメンバーが所属するキューブの名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-162">The name of the cube to which this member belongs.</span></span>|  
|`CHILDREN_CARDINALITY`|<span data-ttu-id="e92e1-163">メンバーが持つ子の数。</span><span class="sxs-lookup"><span data-stu-id="e92e1-163">The number of children that the member has.</span></span> <span data-ttu-id="e92e1-164">これは推定値の場合があります。したがって、この数値を正確な数として使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-164">This can be an estimate, so you should not rely on this to be the exact count.</span></span> <span data-ttu-id="e92e1-165">プロバイダーは、正確な数に最も近い推定値を返します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-165">Providers should return the best estimate possible.</span></span>|  
|`CUSTOM_ROLLUP`|<span data-ttu-id="e92e1-166">カスタム メンバー式。</span><span class="sxs-lookup"><span data-stu-id="e92e1-166">The custom member expression.</span></span>|  
|`CUSTOM_ROLLUP_PROPERTIES`|<span data-ttu-id="e92e1-167">カスタム メンバー プロパティ。</span><span class="sxs-lookup"><span data-stu-id="e92e1-167">The custom member properties.</span></span>|  
|`DESCRIPTION`|<span data-ttu-id="e92e1-168">メンバーに関する、人間が読める形式の説明。</span><span class="sxs-lookup"><span data-stu-id="e92e1-168">A human-readable description of the member.</span></span>|  
|`DIMENSION_UNIQUE_NAME`|<span data-ttu-id="e92e1-169">このメンバーが所属するディメンションの一意な名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-169">The unique name of the dimension to which this member belongs.</span></span> <span data-ttu-id="e92e1-170">修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-170">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`HIERARCHY_UNIQUE_NAME`|<span data-ttu-id="e92e1-171">階層の一意な名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-171">The unique name of the hierarchy.</span></span> <span data-ttu-id="e92e1-172">メンバーが複数の階層に所属している場合は、そのメンバーが所属する階層ごとに対応する行があります。</span><span class="sxs-lookup"><span data-stu-id="e92e1-172">If the member belongs to more than one hierarchy, there is one row for each hierarchy to which the member belongs.</span></span> <span data-ttu-id="e92e1-173">修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-173">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`IS_DATAMEMBER`|<span data-ttu-id="e92e1-174">メンバーがデータ メンバーであるかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="e92e1-174">A Boolean that indicates whether the member is a data member.</span></span>|  
|`IS_PLACEHOLDERMEMBER`|<span data-ttu-id="e92e1-175">メンバーがプレースホルダーであるかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="e92e1-175">A Boolean that indicates whether the member is a placeholder.</span></span>|  
|`KEYx`|<span data-ttu-id="e92e1-176">メンバーのキー (x はキーの序数で、0 から始まります)。</span><span class="sxs-lookup"><span data-stu-id="e92e1-176">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="e92e1-177">KEY0 は複合キーおよび非複合キーに使用できます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-177">KEY0 is available for composite and non-composite keys.</span></span><br /><br /> <span data-ttu-id="e92e1-178">キーが非複合キーの場合、KEY0 は `Key` と同じです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-178">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="e92e1-179">複合キーの場合、KEY0、KEY1、KEY2 などは、全体として複合キーを形成します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-179">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="e92e1-180">クエリでそれぞれを個別に参照すると、複合キーのその部分を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-180">You can reference each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="e92e1-181">たとえば、KEY0 を指定すると複合キーの最初の部分が返され、KEY1 を指定すると複合キーの次の部分が返されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-181">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="e92e1-182">`KEYx` は、コンテキストの有無にかかわらず使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-182">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="e92e1-183">このため、両方の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-183">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="e92e1-184">このメンバー プロパティの使用方法の例については、「 [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364)」(単純な MDX の情報: Key0、Key1、Key2) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-184">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|<span data-ttu-id="e92e1-185">`LCID` *x*</span><span class="sxs-lookup"><span data-stu-id="e92e1-185">`LCID` *x*</span></span>|<span data-ttu-id="e92e1-186">ロケール ID の 16 進値で表現されたメンバー キャプションを変換したもの。 *x* はロケール ID の 10 進値です (たとえば、カナダ英語の場合は LCID1009)。</span><span class="sxs-lookup"><span data-stu-id="e92e1-186">The translation of the member caption in the locale ID hexadecimal value, where *x* is the locale ID decimal value (for example, LCID1009 as English-Canada).</span></span> <span data-ttu-id="e92e1-187">これは、データ ソースにバインドされたキャプション列が変換にある場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-187">This is only available if the translation has the caption column bound to the data source.</span></span>|  
|`LEVEL_NUMBER`|<span data-ttu-id="e92e1-188">階層のルートからメンバーまでの距離。</span><span class="sxs-lookup"><span data-stu-id="e92e1-188">The distance of the member from the root of the hierarchy.</span></span> <span data-ttu-id="e92e1-189">ルートのレベルは 0 です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-189">The root level is zero.</span></span>|  
|`LEVEL_UNIQUE_NAME`|<span data-ttu-id="e92e1-190">メンバーが所属するレベルの一意な名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-190">The unique name of the level to which the member belongs.</span></span> <span data-ttu-id="e92e1-191">修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-191">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_CAPTION`|<span data-ttu-id="e92e1-192">メンバーに関連付けられたラベルまたはキャプション。</span><span class="sxs-lookup"><span data-stu-id="e92e1-192">A label or caption associated with the member.</span></span> <span data-ttu-id="e92e1-193">キャプションの主な用途は、表示用です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-193">The caption is primarily for display purposes.</span></span> <span data-ttu-id="e92e1-194">キャプションが存在しない場合、クエリの結果として `MEMBER_NAME` が返されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-194">If a caption does not exist, the query returns `MEMBER_NAME`.</span></span>|  
|`MEMBER_KEY`|<span data-ttu-id="e92e1-195">元のデータ型でのメンバー キーの値。</span><span class="sxs-lookup"><span data-stu-id="e92e1-195">The value of the member key in the original data type.</span></span> <span data-ttu-id="e92e1-196">MEMBER_KEY は、旧バージョンとの互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="e92e1-196">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="e92e1-197">MEMBER_KEY プロパティの値は、非複合キーについては KEY0 と等しく、複合キーについては NULL です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-197">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`MEMBER_NAME`|<span data-ttu-id="e92e1-198">メンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-198">The name of the member.</span></span>|  
|`MEMBER_TYPE`|<span data-ttu-id="e92e1-199">メンバーの種類。</span><span class="sxs-lookup"><span data-stu-id="e92e1-199">The type of the member.</span></span> <span data-ttu-id="e92e1-200">このプロパティの値は、次のいずれか 1 つです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-200">This property can have one of the following values:</span></span> <br /><span data-ttu-id="e92e1-201">**MDMEMBER_TYPE_REGULAR**</span><span class="sxs-lookup"><span data-stu-id="e92e1-201">**MDMEMBER_TYPE_REGULAR**</span></span><br /><span data-ttu-id="e92e1-202">**MDMEMBER_TYPE_ALL**</span><span class="sxs-lookup"><span data-stu-id="e92e1-202">**MDMEMBER_TYPE_ALL**</span></span><br /><span data-ttu-id="e92e1-203">**MDMEMBER_TYPE_FORMULA**</span><span class="sxs-lookup"><span data-stu-id="e92e1-203">**MDMEMBER_TYPE_FORMULA**</span></span><br /><span data-ttu-id="e92e1-204">**MDMEMBER_TYPE_MEASURE**</span><span class="sxs-lookup"><span data-stu-id="e92e1-204">**MDMEMBER_TYPE_MEASURE**</span></span><br /><span data-ttu-id="e92e1-205">**MDMEMBER_TYPE_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="e92e1-205">**MDMEMBER_TYPE_UNKNOWN**</span></span><br /><br /> <br /><br /> <span data-ttu-id="e92e1-206">MDMEMBER_TYPE_FORMULA は MDMEMBER_TYPE_MEASURE より優先順位が上です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-206">MDMEMBER_TYPE_FORMULA takes precedence over MDMEMBER_TYPE_MEASURE.</span></span> <span data-ttu-id="e92e1-207">したがって、数式メンバー (計算されるメンバー) がメジャー ディメンションに存在する場合、計算されるメンバーの `MEMBER_TYPE` プロパティは MDMEMBER_TYPE_FORMULA です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-207">Therefore, if there is a formula (calculated) member on the Measures dimension, the `MEMBER_TYPE` property for the calculated member is MDMEMBER_TYPE_FORMULA.</span></span>|  
|`MEMBER_UNIQUE_NAME`|<span data-ttu-id="e92e1-208">メンバーの一意な名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-208">The unique name of the member.</span></span> <span data-ttu-id="e92e1-209">修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-209">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_VALUE`|<span data-ttu-id="e92e1-210">元の型でのメンバーの値。</span><span class="sxs-lookup"><span data-stu-id="e92e1-210">The value of the member in the original type.</span></span>|  
|`PARENT_COUNT`|<span data-ttu-id="e92e1-211">このメンバーが持つ親の数。</span><span class="sxs-lookup"><span data-stu-id="e92e1-211">The number of parents that this member has.</span></span>|  
|`PARENT_LEVEL`|<span data-ttu-id="e92e1-212">階層のルート レベルからメンバーの親までの距離。</span><span class="sxs-lookup"><span data-stu-id="e92e1-212">The distance of the member's parent from the root level of the hierarchy.</span></span> <span data-ttu-id="e92e1-213">ルートのレベルは 0 です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-213">The root level is zero.</span></span>|  
|`PARENT_UNIQUE_NAME`|<span data-ttu-id="e92e1-214">メンバーの親の一意の名前。</span><span class="sxs-lookup"><span data-stu-id="e92e1-214">The unique name of the member's parent.</span></span> <span data-ttu-id="e92e1-215">`NULL` ルート レベルのノードに対しては NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-215">`NULL` is returned for any members at the root level.</span></span> <span data-ttu-id="e92e1-216">修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-216">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`SKIPPED_LEVELS`|<span data-ttu-id="e92e1-217">メンバーに関するスキップされたレベルの数。</span><span class="sxs-lookup"><span data-stu-id="e92e1-217">The number of skipped levels for the member.</span></span>|  
|`UNARY_OPERATOR`|<span data-ttu-id="e92e1-218">メンバーの単項演算子。</span><span class="sxs-lookup"><span data-stu-id="e92e1-218">The unary operator for the member.</span></span>|  
|`UNIQUE_NAME`|<span data-ttu-id="e92e1-219">[dimension].[level].[key6] 形式で表す、メンバーの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="e92e1-219">The fully-qualified name of the member, in this format: [dimension].[level].[key6.]</span></span>|  
  
### <a name="properties-syntax-for-non-context-sensitive-properties"></a><span data-ttu-id="e92e1-220">非状況依存プロパティの PROPERTIES の構文</span><span class="sxs-lookup"><span data-stu-id="e92e1-220">PROPERTIES Syntax for Non-Context Sensitive Properties</span></span>  
 <span data-ttu-id="e92e1-221">`PROPERTIES` キーワードを使用して固有の非状況依存メンバー プロパティを指定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-221">Use the following syntax to specify an intrinsic, non-context sensitive member property using the `PROPERTIES` keyword:</span></span>  
  
 `DIMENSION PROPERTIES Property`  
  
 <span data-ttu-id="e92e1-222">この構文では、プロパティをディメンションまたはレベルで修飾できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-222">Notice that this syntax does not allow the property to be qualified by a dimension or level.</span></span> <span data-ttu-id="e92e1-223">プロパティを修飾できない理由は、非状況依存の固有メンバー プロパティが軸上のすべてのメンバーに適用されるためです。</span><span class="sxs-lookup"><span data-stu-id="e92e1-223">The property cannot be qualified because an intrinsic member property that is not context sensitive applies to all members of an axis.</span></span>  
  
 <span data-ttu-id="e92e1-224">たとえば、`DESCRIPTION` 固有メンバー プロパティを指定する MDX ステートメントは次のような構文になります。</span><span class="sxs-lookup"><span data-stu-id="e92e1-224">For example, an MDX statement that specifies the `DESCRIPTION` intrinsic member property would have the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES DESCRIPTION`  
  
 <span data-ttu-id="e92e1-225">このステートメントは、軸ディメンション内の各メンバーに関する説明を返します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-225">This statement returns the description of each member in the axis dimension.</span></span> <span data-ttu-id="e92e1-226">ディメンション*または*レベルのように、プロパティをディメンションまたはレベルで修飾しようとすると、 `.DESCRIPTION` *Level* `.DESCRIPTION` ステートメントは検証されません。</span><span class="sxs-lookup"><span data-stu-id="e92e1-226">If you tried to qualify the property with a dimension or level, as in *Dimension*`.DESCRIPTION` or *Level*`.DESCRIPTION`, the statement would not validate.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e92e1-227">例</span><span class="sxs-lookup"><span data-stu-id="e92e1-227">Example</span></span>  
 <span data-ttu-id="e92e1-228">固有プロパティを返す MDX クエリの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-228">The following examples show MDX queries that return intrinsic properties.</span></span>  
  
 <span data-ttu-id="e92e1-229">**例 1: クエリで状況依存の固有プロパティを使用する**</span><span class="sxs-lookup"><span data-stu-id="e92e1-229">**Example 1: Use context-sensitive intrinsic properties in query**</span></span>  
  
 <span data-ttu-id="e92e1-230">次の例では、各製品カテゴリの親 ID、キー、および名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-230">The following example returns parent ID, key, and name for each product category.</span></span> <span data-ttu-id="e92e1-231">プロパティがメジャーとしてどのように公開されているかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e92e1-231">Notice how the properties are exposed as measures.</span></span> <span data-ttu-id="e92e1-232">これにより、SSMS の [メンバーのプロパティ] ダイアログではなく、クエリの実行時にセル セットのプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-232">This lets you view the properties in a cellset when you run the query, rather than the Member Properties dialog in SSMS.</span></span> <span data-ttu-id="e92e1-233">既に配置されているキューブからメンバー メタデータを取得する場合に、このようなクエリを実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="e92e1-233">You might run a query like this to retrieve member metadata from a cube that is already deployed.</span></span>  
  
```  
WITH  
MEMBER [Measures].[Parent Member ID] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("ID")  
MEMBER [Measures].[Parent Member Key] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")  
MEMBER [Measures].[Parent Member Name] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("Name")  
SELECT  
 {[Measures].[Parent Member ID], [Measures].[Parent Member Key], [Measures].[Parent Member Name] } on COLUMNS,   
 [Product].[Product Categories].AllMembers on ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="e92e1-234">**例 2: 非状況依存の固有プロパティを使用する**</span><span class="sxs-lookup"><span data-stu-id="e92e1-234">**Example 2: Non-context-sensitive intrinsic properties**</span></span>  
  
 <span data-ttu-id="e92e1-235">次の例は、非状況依存の固有プロパティの完全な一覧です。</span><span class="sxs-lookup"><span data-stu-id="e92e1-235">The following example is the full list of non-context-sensitive intrinsic properties.</span></span> <span data-ttu-id="e92e1-236">SSMS でクエリを実行した後、個々のメンバーをクリックすると、[メンバーのプロパティ] ダイアログ ボックスにプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e92e1-236">After running the query in SSMS, click individual members to view properties in the Member Properties dialog box.</span></span>  
  
```  
SELECT [Measures].[Sales Amount Quota] on COLUMNS,  
[Employee].[Employees].members  
DIMENSION PROPERTIES  
 CATALOG_NAME ,   
 CHILDREN_CARDINALITY ,  
 CUSTOM_ROLLUP ,   
 CUSTOM_ROLLUP_PROPERTIES ,   
 DESCRIPTION ,   
 DIMENSION_UNIQUE_NAME ,   
 HIERARCHY_UNIQUE_NAME ,  
 IS_DATAMEMBER ,   
 IS_PLACEHOLDERMEMBER ,   
 KEY0 ,  
 LCID ,  
 LEVEL_NUMBER ,  
 LEVEL_UNIQUE_NAME ,  
 MEMBER_CAPTION ,   
 MEMBER_KEY ,   
 MEMBER_NAME ,   
 MEMBER_TYPE ,  
 MEMBER_UNIQUE_NAME ,   
 MEMBER_VALUE ,   
 PARENT_COUNT ,   
 PARENT_LEVEL ,   
 PARENT_UNIQUE_NAME ,  
 SKIPPED_LEVELS ,   
 UNARY_OPERATOR ,   
 UNIQUE_NAME    
 ON ROWS  
FROM [Adventure Works]  
WHERE [Employee].[Employee Department].[Department].&[Sales]  
```  
  
 <span data-ttu-id="e92e1-237">**例 3: 結果セット内のデータとしてメンバー プロパティを返す**</span><span class="sxs-lookup"><span data-stu-id="e92e1-237">**Example 3: Return member properties as data in a result set**</span></span>  
  
 <span data-ttu-id="e92e1-238">次の例では、Adventure Works キューブの Product ディメンションに含まれる製品カテゴリ メンバーのキャプションを、指定されたロケールの言語で翻訳して返します。</span><span class="sxs-lookup"><span data-stu-id="e92e1-238">The following example returns the translated caption for the product category member in the Product dimension in the Adventure Works cube for specified locales.</span></span>  
  
```  
WITH   
MEMBER Measures.CategoryCaption AS Product.Category.CurrentMember.MEMBER_CAPTION  
MEMBER Measures.SpanishCategoryCaption AS Product.Category.CurrentMember.Properties("LCID3082")  
MEMBER Measures.FrenchCategoryCaption AS Product.Category.CurrentMember.Properties("LCID1036")  
SELECT   
{ Measures.CategoryCaption, Measures.SpanishCategoryCaption, Measures.FrenchCategoryCaption } ON 0  
,[Product].[Category].MEMBERS ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="e92e1-239">参照</span><span class="sxs-lookup"><span data-stu-id="e92e1-239">See Also</span></span>  
 <span data-ttu-id="e92e1-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span></span>  
 <span data-ttu-id="e92e1-241">[子 &#40;MDX&#41;](/sql/mdx/children-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-241">[Children &#40;MDX&#41;](/sql/mdx/children-mdx) </span></span>  
 <span data-ttu-id="e92e1-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 <span data-ttu-id="e92e1-243">[MDX&#41;&#41; &#40;設定 &#40;数](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-243">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="e92e1-244">[MDX&#41;のフィルター処理 &#40;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-244">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="e92e1-245">[MDX&#41;&#40;の Add演算メンバー](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-245">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="e92e1-246">[MDX&#41;&#40;ドリルダウンレベル](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-246">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="e92e1-247">[MDX&#41;&#40;プロパティ](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-247">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="e92e1-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span><span class="sxs-lookup"><span data-stu-id="e92e1-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span></span>  
 <span data-ttu-id="e92e1-249">[MDX&#41;&#40;メンバープロパティを使用する](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e92e1-249">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="e92e1-250">MDX 関数リファレンス &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="e92e1-250">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
