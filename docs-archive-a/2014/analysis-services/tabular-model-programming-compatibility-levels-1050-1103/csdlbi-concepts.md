---
title: CSDLBI の概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 2fbdf621-a94d-4a55-a088-3d56d65016ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 16c6597171eef10da67ad497e4303b3716298e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634693"
---
# <a name="csdlbi-concepts"></a><span data-ttu-id="21011-102">CSDLBI の概念</span><span class="sxs-lookup"><span data-stu-id="21011-102">CSDLBI Concepts</span></span>
  <span data-ttu-id="21011-103">BI 注釈付き概念スキーマ定義言語 (CSDLBI) は、さまざまなデータセットにプログラムでアクセスしてクエリやエクスポートを実行できるように各種のデータを抽象的に表す、Entity Data Framework に基づく言語です。</span><span class="sxs-lookup"><span data-stu-id="21011-103">Conceptual Schema Definition Language with BI annotations (CSDLBI) is based on the Entity Data Framework, which is an abstraction for representing data in a way that enables disparate data sets to be programmatically accessed, queried, or exported.</span></span> <span data-ttu-id="21011-104">CSDLBI はリッチ形式でデータ ドリブンのレポートとアプリケーションをサポートしているため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して作成されたデータ モデルを表すために CSDLBI が使用されます。</span><span class="sxs-lookup"><span data-stu-id="21011-104">CSDLBI is used to represent data models created using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] because it supports rich, data-driven reporting and applications.</span></span>  
  
 <span data-ttu-id="21011-105">このセクションでは、CSDLBI 表現と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ モデルをマップする方法 (テーブルと多次元の両方) を、各モデルの種類の例と共に説明します。</span><span class="sxs-lookup"><span data-stu-id="21011-105">This section explains how the CSDLBI representation maps to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data models (both tabular and multidimensional), along with examples of each model type.</span></span>  
  
 <span data-ttu-id="21011-106">これらの概念を示すために、Codeplex から入手できる AdventureWorks サンプル データベースの例を使用しています。</span><span class="sxs-lookup"><span data-stu-id="21011-106">Examples used to illustrate these concepts are taken from the AdventureWorks sample database, available on Codeplex.</span></span> <span data-ttu-id="21011-107">サンプルの詳細については、「 [SQL Server のための Adventure Works サンプル](https://go.microsoft.com/fwlink/?linkID=220093)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21011-107">For more information about the samples, see [Adventure Works Samples for SQL Server](https://go.microsoft.com/fwlink/?linkID=220093).</span></span>  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a><span data-ttu-id="21011-108">CSDLBI のテーブル モデルの構造</span><span class="sxs-lookup"><span data-stu-id="21011-108">Structure of a Tabular Model in CSDLBI</span></span>  
 <span data-ttu-id="21011-109">レポート モデルとそのデータを記述する CSDLBI ドキュメントでは、最初に xsd ステートメントを記述し、その後にモデルの定義を記述します。</span><span class="sxs-lookup"><span data-stu-id="21011-109">A CSDLBI document that describes a report model and its data begins with the xsd statement, followed by the definition of a model.</span></span>  
  
 <span data-ttu-id="21011-110">モデルは名前空間として定義されます。主なエンティティ、アソシエーション、およびプロパティを次に示します。</span><span class="sxs-lookup"><span data-stu-id="21011-110">The model is a namespace, which contains the following major entities, associations, and properties:</span></span>  
  
-   <span data-ttu-id="21011-111">`EntityContainer` は、モデルのテーブルの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="21011-111">The `EntityContainer` lists the tables in the model.</span></span>  
  
-   <span data-ttu-id="21011-112">各テーブルは、`EntityContainer` で  `EntitySet` として示されます。</span><span class="sxs-lookup"><span data-stu-id="21011-112">Each table is listed with the `EntityContainer` as an `EntitySet`.</span></span>  
  
-   <span data-ttu-id="21011-113">2 つのテーブル間の各リレーションシップは、リレーションシップのエンド ポイントとロールを定義する `AssociationSet` として記述されます。</span><span class="sxs-lookup"><span data-stu-id="21011-113">Each relationship between two tables is described as an `AssociationSet` that defines the relationship end points and the relationship roles.</span></span>  
  
-   <span data-ttu-id="21011-114">`EntityType` 要素は、BISM 向けに拡張されており、テーブルやその列に関する追加情報を提供できるようになっています。これには、並べ替えや表示の目的で使用されるプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="21011-114">The `EntityType` element is extended for BISM to provide additional detail about the tables and the columns in them, including properties for sorting and display purposes.</span></span>  
  
-   <span data-ttu-id="21011-115">`Measure` 要素は、モデルで使用できる計算を定義します。</span><span class="sxs-lookup"><span data-stu-id="21011-115">The `Measure` element defines calculations that can be used in the model.</span></span> <span data-ttu-id="21011-116">新しい `KPI` 要素を使用すると、一連の特殊な表示属性を追加することでメジャーを KPI に変換できます。</span><span class="sxs-lookup"><span data-stu-id="21011-116">A measure can be turned into a KPI by adding a set of special display attributes, using the new `KPI` Element.</span></span>  
  
-   <span data-ttu-id="21011-117">パースペクティブの表現はありません。</span><span class="sxs-lookup"><span data-stu-id="21011-117">There is no separate representation of perspectives.</span></span> <span data-ttu-id="21011-118">パースペクティブに含まれていない列やテーブルが CSDL にある場合、`Hidden` 属性のフラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="21011-118">Columns and tables that are not included in a perspective are present in the CSDL but flagged with the `Hidden` attribute.</span></span>  
  
### <a name="entities-entitysets-and-entitytypes"></a><span data-ttu-id="21011-119">Entity、EntitySet、および Entitytype</span><span class="sxs-lookup"><span data-stu-id="21011-119">Entities, EntitySets, and EntityTypes</span></span>  
 <span data-ttu-id="21011-120">Entity Data Framework のエンティティの表記が拡張され、データ モデルの列やテーブルを表現できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="21011-120">The notion of an entity in the Entity Data Framework is extended to represent columns and tables from the data model.</span></span> <span data-ttu-id="21011-121">次の例は、テーブルを 3 つだけ含む単純なモデルの `EntitySet` 要素の記述部分を抜粋したものです。</span><span class="sxs-lookup"><span data-stu-id="21011-121">The following excerpt shows the list of `EntitySet` elements in a simple model containing only three tables.</span></span>  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 <span data-ttu-id="21011-122">`EntitySet` には、テーブルの列やデータに関する情報はありません。</span><span class="sxs-lookup"><span data-stu-id="21011-122">The `EntitySet` does not contain information about columns or data in the table.</span></span> <span data-ttu-id="21011-123">列とそのプロパティの詳細な記述は、EntityType 要素で提供されます。</span><span class="sxs-lookup"><span data-stu-id="21011-123">The detailed description of the columns and their properties is provided in the EntityType element.</span></span>  
  
 <span data-ttu-id="21011-124">各エンティティ (テーブル) の `EntitySet` 要素には、キー列、列のデータ型と長さ、NULL 値を許容するかどうか、並べ替えの動作など、詳細を定義する一連のプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="21011-124">The `EntitySet` element for each entity (table) includes a collection of properties that define the key column, the data type and length of the column, nullability, sorting behavior, and so forth.</span></span> <span data-ttu-id="21011-125">たとえば、次の CSDL は、Customer テーブルの 3 つの列の記述部分を抜粋したものです。</span><span class="sxs-lookup"><span data-stu-id="21011-125">For example, the following CSDL excerpt describes three columns in the Customer table.</span></span> <span data-ttu-id="21011-126">最初の列は、モデルの内部で使用される特殊な非表示の列です。</span><span class="sxs-lookup"><span data-stu-id="21011-126">The first column is a special hidden column used internally by the model.</span></span>  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 <span data-ttu-id="21011-127">生成される CSDLBI ドキュメントのサイズを制限するために、エンティティで複数回使用されるプロパティは、既存のプロパティへの参照で指定されます。これにより、`EntityType` には、各プロパティを 1 回だけ指定すれば済みます。</span><span class="sxs-lookup"><span data-stu-id="21011-127">To limit the size of the CSDLBI document that is generated, properties that appear more than once in an entity are specified by a reference to an existing property, so that the property need be listed only once for the `EntityType`.</span></span> <span data-ttu-id="21011-128">クライアント アプリケーションでは、`EntityType` に一致する `OriginEntityType` を検出することでプロパティの値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="21011-128">The client application can get the value of the property by finding the `EntityType` that matches the `OriginEntityType`.</span></span>  
  
### <a name="relationships"></a><span data-ttu-id="21011-129">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="21011-129">Relationships</span></span>  
 <span data-ttu-id="21011-130">Entity Data Framework では、リレーションシップはエンティティ間の*アソシエーション*として定義されます。</span><span class="sxs-lookup"><span data-stu-id="21011-130">In the Entity Data Framework, relationships are defined as *associations* between entities.</span></span>  
  
 <span data-ttu-id="21011-131">アソシエーションには必ず 2 つのエンド ポイントがあり、それぞれがテーブルのフィールドまたは列を参照します。</span><span class="sxs-lookup"><span data-stu-id="21011-131">Associations always have exactly two ends, each pointing to a field or column in a table.</span></span> <span data-ttu-id="21011-132">したがって、リレーションシップのエンド ポイントが異なれば、2 つのテーブル間に複数のリレーションシップを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="21011-132">Therefore, multiple relationships are possible between two tables, if the relationships have different end points.</span></span> <span data-ttu-id="21011-133">アソシエーションのエンド ポイントにはロール名が割り当てられます。このロール名は、データ モデルのコンテキストにおけるアソシエーションの用途を示します。</span><span class="sxs-lookup"><span data-stu-id="21011-133">A role name is assigned to the end points of the association, and indicates how the association is used in the context of the data model.</span></span> <span data-ttu-id="21011-134">たとえば、Orders テーブルの顧客 ID に関連付けられている顧客 ID に適用されている場合、ロール名の例として**ShipTo**が使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="21011-134">An example of a role name might be **ShipTo**, when applied to a customer ID that is related to the customer ID in an Orders table.</span></span>  
  
 <span data-ttu-id="21011-135">モデルの CSDLBI 表現にはアソシエーションの属性も含まれており、アソシエーションの*複数要素*の接続性の観点からエンティティが相互にマップされる方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="21011-135">The CSDLBI representation of the model also contains attributes on the association that determine how the entities are mapped to each other in terms of the *multiplicity* of the association.</span></span> <span data-ttu-id="21011-136">複数要素の接続性は、テーブル間のリレーションシップのエンド ポイントの属性または列がリレーションシップの "一" 側か "多" 側かを示します。</span><span class="sxs-lookup"><span data-stu-id="21011-136">Multiplicity indicates whether the attribute or column at the end point of a relationship between tables is on the one side of a relationship, or on the many side.</span></span> <span data-ttu-id="21011-137">一対一のリレーションシップを表す値はありません。</span><span class="sxs-lookup"><span data-stu-id="21011-137">There is no separate value for one-to-one relationships.</span></span> <span data-ttu-id="21011-138">CSDLBI 注釈でサポートされる複数要素の接続性の値は、エンティティが他のエンティティと関連付けられていないことを示す 0 と、一対一のリレーションシップまたは一対多のリレーションシップであることを示す 0..1 です。</span><span class="sxs-lookup"><span data-stu-id="21011-138">CSDLBI annotations support multiplicity of 0 (meaning the entity is not associated with anything) or 0..1, which means either a one-one relationship or a one-to-many relationship.</span></span>  
  
 <span data-ttu-id="21011-139">次のサンプルは、列 DateAlternateKey で結合された Date および ProductInventory という 2 つのテーブルのリレーションシップの CSDLBI 出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="21011-139">The following sample represents the CSDLBI output for a relationship between the tables, Date and ProductInventory, where the two tables are joined on the column DateAlternateKey.</span></span> <span data-ttu-id="21011-140">既定では、`AssociationSet` の名前は、リレーションシップに関係する列の完全修飾名になります。</span><span class="sxs-lookup"><span data-stu-id="21011-140">Notice that, by default, the name of the `AssociationSet` is the fully qualified name of the columns that are involved in the relationship.</span></span> <span data-ttu-id="21011-141">ただし、モデルのデザイン時にこの動作を変更すれば、別の名前付け形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="21011-141">However, you can change this behavior when you design the model, to use a different naming format.</span></span>  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a><span data-ttu-id="21011-142">視覚化とナビゲーションプロパティ</span><span class="sxs-lookup"><span data-stu-id="21011-142">Visualization and Navigation Properties</span></span>  
 <span data-ttu-id="21011-143">CSDLBI 注釈で重要なものに、レポート層での表示を定義するためのプロパティと、エンティティ間のリレーションシップをナビゲートするためのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="21011-143">An important part of the CSDLBI annotations are the properties for defining presentation in the reporting layer, and for navigating the relationships among entities.</span></span> <span data-ttu-id="21011-144">通常、データ モデルを作成する際に、データの順序やグループ化の方法を制御したり既定値を決めたりすることはそれほど重要視されません。これは、順序などの表示に関する詳細はクライアント アプリケーションで指定されると想定されるためです。</span><span class="sxs-lookup"><span data-stu-id="21011-144">Typically, when you are creating a data model, you do not consider it important to control how the data is ordered or grouped, or what the default value might be, on the assumption that the client application will specify ordering and other details of presentation.</span></span> <span data-ttu-id="21011-145">ただし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のテーブル モデルは [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポート クライアントと統合できる設計になっており、レポート デザイン画面でのデータ モデルのエンティティの表示をサポートするプロパティと属性が用意されています。</span><span class="sxs-lookup"><span data-stu-id="21011-145">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular models are designed for integration with the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reporting client, and includes properties and attributes that support presentation of entities from the data model in the report design surface.</span></span>  
  
 <span data-ttu-id="21011-146">視覚化についての拡張機能には、数値データで使用する既定の集計を指定するための属性、テキスト フィールドが画像の URL を指すことを示すための属性、現在のフィールドの並べ替えに使用するフィールドを指定するための属性などがあります。</span><span class="sxs-lookup"><span data-stu-id="21011-146">Extensions for visualization include attributes for specifying the default aggregation to use with numerical data, for indicating that a text field points to a URL of an image, or specifying the field used to sort the current field.</span></span>  
  
### <a name="name-properties-and-naming-conventions"></a><span data-ttu-id="21011-147">名前のプロパティと名前付け規則</span><span class="sxs-lookup"><span data-stu-id="21011-147">Name Properties and Naming Conventions</span></span>  
 <span data-ttu-id="21011-148">CSDLBI スキーマでは、キーとして使用できる一意の名前と識別子を各エンティティに割り当てるように規定されています。</span><span class="sxs-lookup"><span data-stu-id="21011-148">The CSDLBI schema provides that each entity has a unique name and an identifier that can be used as a key.</span></span> <span data-ttu-id="21011-149">また、一部のエンティティには、表示目的で使用されるキャプションや、エンティティの使用場所によって変化するコンテキスト名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="21011-149">In addition, some entities can have captions used for display purposes, and contextual names that change depending on where the entity is used.</span></span>  
  
 <span data-ttu-id="21011-150">`Documentation` 要素を使用すると、レポートの設計者は、ビジネス ユーザーがデータの意味を理解できるようにエンティティの説明を記述することができます。</span><span class="sxs-lookup"><span data-stu-id="21011-150">The `Documentation` element provides the opportunity for report designers to furnish a description of the entity, to help business users understand the meaning of the data.</span></span> <span data-ttu-id="21011-151">また、一部のエンティティでは、1 つ以上の `Annotation` 属性を使用して、アプリケーションやクライアントで使用できる追加のメタデータを提供できます。</span><span class="sxs-lookup"><span data-stu-id="21011-151">Some entities also allow one or more `Annotation` attributes, which provide extra metadata for consumption by the application or by clients.</span></span>  
  
 <span data-ttu-id="21011-152">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ツールでモデルを生成すると、オブジェクトの名前付けと名前の一意性に関する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の規則に従ってオブジェクトの名前が作成されます。</span><span class="sxs-lookup"><span data-stu-id="21011-152">When you generate a model the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tools, the names that are created for objects follow the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conventions for object naming and name uniqueness.</span></span> <span data-ttu-id="21011-153">ただし、CSDLBI は Entity Data Framework (EDF) に基づくため、C# の識別子に関する規則に従って名前を付ける必要があります。そのため、モデルの CSDLBI 出力をサーバーで作成するときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のスキーマ内で使用されている名前が取得され、EDF の要件を満たす新しいオブジェクト名が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="21011-153">However, because CSDLBI is based on the Entity Data Framework (EDF), which requires that names adhere to conventions for C# identifiers, when the server creates the CSDLBI output for a model, the server takes the names used within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] schema and automatically creates new object names that comply with EDF requirements.</span></span> <span data-ttu-id="21011-154">次の表に、新しい名前が生成されるときの処理を示します。</span><span class="sxs-lookup"><span data-stu-id="21011-154">The following table describes the operations by which the new names are generated.</span></span>  
  
|<span data-ttu-id="21011-155">ルール</span><span class="sxs-lookup"><span data-stu-id="21011-155">Rule</span></span>|<span data-ttu-id="21011-156">アクション</span><span class="sxs-lookup"><span data-stu-id="21011-156">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="21011-157">禁止されている文字を使用しない</span><span class="sxs-lookup"><span data-stu-id="21011-157">No forbidden characters</span></span>|<span data-ttu-id="21011-158">禁止されている文字は、アンダースコアに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="21011-158">Forbidden characters are replaced by underscore.</span></span>|  
|<span data-ttu-id="21011-159">名前は一意でなければならない</span><span class="sxs-lookup"><span data-stu-id="21011-159">Names must be unique</span></span>|<span data-ttu-id="21011-160">同じ文字列が 2 つある場合は、一意にするために、どちらかにアンダースコアと数値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="21011-160">If two strings are the same, one is made unique by appending underscore plus a number</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="21011-161">キャプションと修飾子の両方に翻訳があります。特定の言語では、どちらか一方だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="21011-161">Captions and qualifiers both have translations, and for a given language, one or the other might be present.</span></span> <span data-ttu-id="21011-162">つまり、修飾子と名前または修飾子とキャプションを連結した場合、文字列が 2 種類の言語で示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="21011-162">This means that in cases where a qualifier and name or qualifier and caption are concatenated, the strings could be in two different languages.</span></span>  
  
## <a name="additions-to-support-multidimensional-models"></a><span data-ttu-id="21011-163">多次元モデルをサポートするための追加事項</span><span class="sxs-lookup"><span data-stu-id="21011-163">Additions to Support Multidimensional Models</span></span>  
 <span data-ttu-id="21011-164">CSDLBI 注釈の Version 1.0 ではテーブル モデルのみがサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="21011-164">Version 1.0 of the CSDLBI annotations supported only tabular models.</span></span> <span data-ttu-id="21011-165">Version 1.1 では、従来の BI 開発ツールを使用して作成された多次元モデル (OLAP キューブ) もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="21011-165">In version 1.1, support was added for multidimensional models (OLAP cubes) created using traditional BI development tools.</span></span> <span data-ttu-id="21011-166">その結果、多次元モデルに XML 要求を実行して、レポートで使用するためのモデルの CSDLBI 定義を受信できます。</span><span class="sxs-lookup"><span data-stu-id="21011-166">Therefore, you can now issue an XML request to a multidimensional model and receive a CSDLBI definition of the model, for use in reporting.</span></span>  
  
 <span data-ttu-id="21011-167">**キューブ:** SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表形式データベースには、1つのモードのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="21011-167">**Cubes:** A SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular database can contain only one mode.</span></span> <span data-ttu-id="21011-168">一方、多次元データベースには複数のキューブを含めることができ、各データベースは既定のキューブに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="21011-168">In contrast, each multidimensional database can contain multiple cubes, each database being associated with a default cube.</span></span> <span data-ttu-id="21011-169">したがって、XML 要求を多次元サーバーに対して実行する場合は、キューブを指定する必要があり、キューブを指定しないと、既定のキューブに対する XML が返されます。</span><span class="sxs-lookup"><span data-stu-id="21011-169">Therefore, when issuing an XML request against a multidimensional server, it is necessary to specify the cube; otherwise, the XML for the default cube will be returned.</span></span>  
  
 <span data-ttu-id="21011-170">その場合、キューブの表現はテーブル モデル データベースによく似ています。</span><span class="sxs-lookup"><span data-stu-id="21011-170">The representation of a cube is otherwise very much like that of a tabular model database.</span></span> <span data-ttu-id="21011-171">キューブ名とキューブが、表形式のデータベース名とデータベース識別子に対応します。</span><span class="sxs-lookup"><span data-stu-id="21011-171">The cube name and cube correspond to the tabular database name and database identifier.</span></span>  
  
 <span data-ttu-id="21011-172">**ディメンション:** ディメンションは、列とプロパティを持つエンティティ (テーブル) として CSDLBI で表されます。</span><span class="sxs-lookup"><span data-stu-id="21011-172">**Dimensions:** A dimension is represented in CSDLBI as an entity (table) with columns and properties.</span></span> <span data-ttu-id="21011-173">パースペクティブに含まれていない場合でも、モデルに含まれるディメンションは、`Hidden` とマークされて CSDL 出力で表現されます。</span><span class="sxs-lookup"><span data-stu-id="21011-173">Note that even if not included in a perspective, a dimension that is included in the model will be represented in the CSDL output, marked as `Hidden`.</span></span>  
  
 <span data-ttu-id="21011-174">**パースペクティブ:** クライアントは、個々のパースペクティブに対して CSDL を要求できます。</span><span class="sxs-lookup"><span data-stu-id="21011-174">**Perspectives:** A client can request CSDL for individual perspectives.</span></span> <span data-ttu-id="21011-175">詳細については、「 [DISCOVER_CSDL_METADATA 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21011-175">For more information, see [DISCOVER_CSDL_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).</span></span>  
  
 <span data-ttu-id="21011-176">**階層:** 階層はサポートされており、CSDLBI では一連のレベルとして表されます。</span><span class="sxs-lookup"><span data-stu-id="21011-176">**Hierarchies:** Hierarchies are supported and represented in CSDLBI as a set of levels.</span></span>  
  
 <span data-ttu-id="21011-177">**メンバー:** 既定のメンバーのサポートが追加され、既定値が CSDLBI 出力に自動的に追加されました。</span><span class="sxs-lookup"><span data-stu-id="21011-177">**Members:** Support for the default member has been added and default values are automatically added to the CSDLBI output.</span></span>  
  
 <span data-ttu-id="21011-178">**計算されるメンバー:** 多次元モデルでは、1つの real メンバーを持つ**すべて**の子の計算されるメンバーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="21011-178">**Calculated Members:** Multidimensional models support calculated members for child of **All** with a single real member.</span></span>  
  
 <span data-ttu-id="21011-179">**ディメンションの属性:** CSDLBI 出力では、ディメンション属性がサポートされており、自動的に集計不可としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="21011-179">**Dimension attributes:** In CSDLBI output, dimension attributes are supported and automatically marked as non-aggregatable.</span></span>  
  
 <span data-ttu-id="21011-180">**Kpi:** Kpi は CSDLBI バージョン1.1 でサポートされていましたが、表現が変更されました。</span><span class="sxs-lookup"><span data-stu-id="21011-180">**KPIs:** KPIs were supported in CSDLBI version 1.1, but the representation has changed.</span></span> <span data-ttu-id="21011-181">以前の KPI はメジャーのプロパティでした。</span><span class="sxs-lookup"><span data-stu-id="21011-181">Before, a KPI was a property of a measure.</span></span> <span data-ttu-id="21011-182">バージョン1.1 では、KPI 要素をメジャーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="21011-182">In version 1.1, the KPI element can be added to a measure</span></span>  
  
 <span data-ttu-id="21011-183">**新しいプロパティ:** DirectQuery モデルをサポートするために追加の属性が追加されました。</span><span class="sxs-lookup"><span data-stu-id="21011-183">**New properties:** Additional attributes were added to support DirectQuery models.</span></span>  
  
 <span data-ttu-id="21011-184">**制限事項:** セルのセキュリティはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="21011-184">**Limitations:** Cell security is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21011-185">参照</span><span class="sxs-lookup"><span data-stu-id="21011-185">See Also</span></span>  
 [<span data-ttu-id="21011-186">ビジネス インテリジェンス向けの CSDL 注釈 (CSDLBI)</span><span class="sxs-lookup"><span data-stu-id="21011-186">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
  
