---
title: ビジネスインテリジェンスの CSDL 注釈 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: bf6f372a-bc67-45ea-a771-b2dc5b0527e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: b3414b0d8b2614e83f62e85c4f750ee0e8c7397d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634701"
---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a><span data-ttu-id="14c4e-102">ビジネス インテリジェンス向けの CSDL 注釈 (CSDLBI)</span><span class="sxs-lookup"><span data-stu-id="14c4e-102">CSDL Annotations for Business Intelligence (CSDLBI)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="14c4e-103">は、ビジネス インテリジェンス注釈付き概念スキーマ定義言語 (CSDLBI) と呼ばれる XML 形式でのテーブル モデルの定義の表示をサポートします。</span><span class="sxs-lookup"><span data-stu-id="14c4e-103">supports the presentation of the definition of a tabular model in an XML format called Conceptual Schema Definition Language with Business Intelligence annotations (CSDLBI).</span></span>  
  
 <span data-ttu-id="14c4e-104">このトピックでは、CSDLBI の概要および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ モデルでの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-104">This topic provides an overview of CSDLBI and how it is used with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data models.</span></span>  
  
## <a name="understanding-the-role-of-csdl"></a><span data-ttu-id="14c4e-105">CSDL の役割について</span><span class="sxs-lookup"><span data-stu-id="14c4e-105">Understanding the Role of CSDL</span></span>  
 <span data-ttu-id="14c4e-106">概念スキーマ定義言語 (CSDL) は、エンティティ、リレーションシップ、および関数を記述する XML ベースの言語です。</span><span class="sxs-lookup"><span data-stu-id="14c4e-106">The Conceptual Schema Data Language (CSDL) is an XML-based language that describes entities, relationships, and functions.</span></span> <span data-ttu-id="14c4e-107">CSDL は Entity Data Framework の一部として定義されます。</span><span class="sxs-lookup"><span data-stu-id="14c4e-107">CSDL is defined as part of the Entity Data Framework.</span></span> <span data-ttu-id="14c4e-108">BI 注釈は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用してデータ モデリングをサポートするための拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="14c4e-108">The BI annotations are an extension designed to support data modeling using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="14c4e-109">CSDL は Entity Data Framework に準拠していますが、エンティティとリレーションシップのモデルについての理解や、テーブル モデルまたはモデルに基づくレポートを構築するための専用ツールは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="14c4e-109">Although CSDL is compliant with the Entity Data Framework, you do not need to understand the entity-relationship model or have any special tools to build a tabular model or a report based on a model.</span></span> <span data-ttu-id="14c4e-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] などのクライアント ツールや AMO などの API を使用してモデルを作成し、それをサーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-110">You build models by using client tools such as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or an API such as AMO, and deploy the model to a server.</span></span> <span data-ttu-id="14c4e-111">クライアントからモデルへの接続にはモデル定義ファイルを使用し、通常、モデル定義ファイルは SharePoint ライブラリにパブリッシュされます。レポート デザイナーとレポート コンシューマーは、このライブラリでモデルの定義ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="14c4e-111">Clients connect to the model by using a model definition file, typically published to a SharePoint library where it can be used by report designers and report consumers.</span></span> <span data-ttu-id="14c4e-112">詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="14c4e-112">For more information, see these links:</span></span>  
  
-   [<span data-ttu-id="14c4e-113">テーブル モデル ソリューション &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="14c4e-113">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
-   [<span data-ttu-id="14c4e-114">テーブル モデル ソリューションの配置 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="14c4e-114">Tabular Model Solution Deployment &#40;SSAS Tabular&#41;</span></span>](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
-   [<span data-ttu-id="14c4e-115">PowerPivot BI セマンティックモデル接続 &#40;。 bism&#41;</span><span class="sxs-lookup"><span data-stu-id="14c4e-115">PowerPivot BI Semantic Model Connection &#40;.bism&#41;</span></span>](../power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)  
  
 <span data-ttu-id="14c4e-116">CSDLBI スキーマは、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントからのモデル定義の要求に対して、Analysis Services サーバーで生成されます。</span><span class="sxs-lookup"><span data-stu-id="14c4e-116">The CSDLBI schema is generated by the Analysis Services server in response to a request for a model definition from a client such as [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="14c4e-117">クライアント アプリケーションは、モデル データをホストする Analysis Services サーバーに XML クエリを送信します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-117">The client application sends an XML query to the Analysis Services server that hosts the model data.</span></span> <span data-ttu-id="14c4e-118">その応答として、サーバーはモデル内のエンティティの定義を含む XML メッセージを CSDLBI 注釈を使用して送信します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-118">In response, the server sends an XML message containing a definition of the entities in the model, using the CSDLBI annotations.</span></span> <span data-ttu-id="14c4e-119">レポートクライアントは、この情報を使用して、モデルで使用できるフィールド、集計、およびメジャーを表示します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-119">The reporting client then uses the information to present the fields, aggregations, and measures that are available in the model.</span></span> <span data-ttu-id="14c4e-120">CSDLBI 注釈は、データのグループ化、並べ替え、および書式設定の方法に関する情報も提供します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-120">The CSDLBI annotations also provide information about how to group, sort, and format the data.</span></span>  
  
 <span data-ttu-id="14c4e-121">CSDLBI の一般的な情報については、「 [CSDLBI の概念](/analysis-services/csdlbi/csdlbi-concepts)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14c4e-121">For general information about CSDLBI, see [CSDLBI Concepts](/analysis-services/csdlbi/csdlbi-concepts).</span></span>  
  
### <a name="working-with-csdl"></a><span data-ttu-id="14c4e-122">CSDL の操作</span><span class="sxs-lookup"><span data-stu-id="14c4e-122">Working with CSDL</span></span>  
 <span data-ttu-id="14c4e-123">特定のテーブル モデルを表す CSDLBI 注釈のセットは、単純型と複合型の両方のエンティティのコレクションを含む XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="14c4e-123">The set of CSDLBI annotations that represents any particular tabular model is an XML document containing a collection of entities, both simple and complex.</span></span> <span data-ttu-id="14c4e-124">エンティティは、計算列、メジャーまたは KPI に含まれるテーブル (またはディメンション)、列 (属性)、関連付け (リレーションシップ) および式を定義します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-124">The entities define tables (or dimensions), columns (attributes), associations (relationships), and formulas included in calculated columns, measure, or KPIs.</span></span>  
  
 <span data-ttu-id="14c4e-125">これらのオブジェクトを直接変更することはできません。テーブル モデルを操作するには、クライアント ツールおよびアプリケーション プログラミング インターフェイス (API) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="14c4e-125">You cannot modify these objects directly, but must use the client tools and application programming interfaces (APIs) provided for working with tabular models.</span></span>  
  
 <span data-ttu-id="14c4e-126">モデルの CSDL を取得するには、モデルをホストするサーバーに DISCOVER 要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-126">You can obtain the CSDL for a model by sending a DISCOVER request to the server that hosts the model.</span></span> <span data-ttu-id="14c4e-127">この要求は、サーバーとモデルのほか、必要に応じてビューまたはパースペクティブを指定して修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14c4e-127">The request must be qualified by specifying the server and the model, and, optionally, a view or perspective.</span></span> <span data-ttu-id="14c4e-128">返されるメッセージは、XML 文字列です。</span><span class="sxs-lookup"><span data-stu-id="14c4e-128">The returned message is an XML string.</span></span> <span data-ttu-id="14c4e-129">一部の要素は言語に依存しているため、現在の接続の言語に応じて異なる値が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="14c4e-129">Certain elements are language-dependent and may return different values depending on the language of the current connection.</span></span> <span data-ttu-id="14c4e-130">詳細については、「 [DISCOVER_CSDL_METADATA 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14c4e-130">For more information, see [DISCOVER_CSDL_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).</span></span>  
  
### <a name="csdlbi-versions"></a><span data-ttu-id="14c4e-131">CSDLBI のバージョン</span><span class="sxs-lookup"><span data-stu-id="14c4e-131">CSDLBI Versions</span></span>  
 <span data-ttu-id="14c4e-132">元の CSDL 仕様 (Entity Data Framework に基づく) では、モデリングのサポートに必要なエンティティとプロパティの大半が規定されています。</span><span class="sxs-lookup"><span data-stu-id="14c4e-132">The original CSDL specification (from the Entity Data Framework) provides for most of the entities and properties that are needed to support modeling.</span></span> <span data-ttu-id="14c4e-133">BI 注釈は、テーブル モデルの特殊な要件、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントに必要なレポート プロパティ、および多次元モデルに必要な追加のメタデータをサポートします。</span><span class="sxs-lookup"><span data-stu-id="14c4e-133">The BI annotations support special requirements of tabular models, reporting properties required for clients such as [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], and additional metadata required for multidimensional models.</span></span> <span data-ttu-id="14c4e-134">このセクションでは、各バージョンでの更新内容を説明します。</span><span class="sxs-lookup"><span data-stu-id="14c4e-134">This section describes the updates in each version.</span></span>  
  
 <span data-ttu-id="14c4e-135">**CSDLBI 1.0**</span><span class="sxs-lookup"><span data-stu-id="14c4e-135">**CSDLBI 1.0**</span></span>  
  
 <span data-ttu-id="14c4e-136">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] テーブル モデルをサポートするために CSDL スキーマに追加された最初のセットです。データ モデリング、カスタム計算、および拡張表現をサポートする注釈を含みました。</span><span class="sxs-lookup"><span data-stu-id="14c4e-136">The initial set of additions to the CSDL schema to support [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular models contained annotations in support of data modeling, custom calculations, and enhanced presentation:</span></span>  
  
-   <span data-ttu-id="14c4e-137">テーブル モデルをサポートする新しい要素とプロパティ。</span><span class="sxs-lookup"><span data-stu-id="14c4e-137">New elements and properties to support tabular models.</span></span> <span data-ttu-id="14c4e-138">たとえば、モデルの作成に使用されるデータベース クエリの種類を指定するためのプロパティが追加されました。</span><span class="sxs-lookup"><span data-stu-id="14c4e-138">For example, a property was added to specify the type of database query used to populate the model.</span></span>  
  
-   <span data-ttu-id="14c4e-139">既存のエンティティの新しいプロパティと拡張。</span><span class="sxs-lookup"><span data-stu-id="14c4e-139">New properties and extensions to existing entities.</span></span>  <span data-ttu-id="14c4e-140">たとえば、リレーションシップをサポートするように Association 要素が拡張されました。</span><span class="sxs-lookup"><span data-stu-id="14c4e-140">For example, the Association element was extended to support relationships.</span></span>  
  
-   <span data-ttu-id="14c4e-141">視覚化プロパティとナビゲーション プロパティ。</span><span class="sxs-lookup"><span data-stu-id="14c4e-141">Visualization and navigation properties.</span></span> <span data-ttu-id="14c4e-142">たとえば、カスタムの並べ替えフィールド、既定の画像をサポートするためのプロパティが追加されました。</span><span class="sxs-lookup"><span data-stu-id="14c4e-142">For example, properties were added to support custom sorting fields, default images, and</span></span>  
  
 <span data-ttu-id="14c4e-143">**CSDLBI 1.1**</span><span class="sxs-lookup"><span data-stu-id="14c4e-143">**CSDLBI 1.1**</span></span>  
  
 <span data-ttu-id="14c4e-144">このバージョンの CSDLBI スキーマは、多次元データベース (OLAP キューブなど) をサポートします。</span><span class="sxs-lookup"><span data-stu-id="14c4e-144">This version of the CSDLBI schema includes additions in support of multidimensional databases (such as OLAP cubes).</span></span> <span data-ttu-id="14c4e-145">新しい要素とプロパティは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="14c4e-145">The new elements and properties are as follows:</span></span>  
  
-   <span data-ttu-id="14c4e-146">エンティティとしてディメンションのサポート。</span><span class="sxs-lookup"><span data-stu-id="14c4e-146">Support for dimensions as entities.</span></span>  
  
-   <span data-ttu-id="14c4e-147">階層のサポート。</span><span class="sxs-lookup"><span data-stu-id="14c4e-147">Support for hierarchies.</span></span>  
  
-   <span data-ttu-id="14c4e-148">ROLAP パーティションの公開。</span><span class="sxs-lookup"><span data-stu-id="14c4e-148">Exposes ROLAP partitions.</span></span>  
  
-   <span data-ttu-id="14c4e-149">翻訳のサポート</span><span class="sxs-lookup"><span data-stu-id="14c4e-149">Support for translations.</span></span>  
  
-   <span data-ttu-id="14c4e-150">パースペクティブのサポート。</span><span class="sxs-lookup"><span data-stu-id="14c4e-150">Support for perspectives.</span></span>  
  
 <span data-ttu-id="14c4e-151">CSDLBI 注釈の個々の要素の詳細については、「 [CSDL への BI 注釈のテクニカルリファレンス](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14c4e-151">For detailed information about individual elements in the CSDLBI annotations, see [Technical Reference for BI Annotations to CSDL](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl).</span></span> <span data-ttu-id="14c4e-152">CSDL のコア仕様の詳細については、 [csdl v3 の仕様](https://docs.microsoft.com/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14c4e-152">For information about the core CSDL specification, see the [CSDL v3 Specification](https://docs.microsoft.com/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="14c4e-153">参照</span><span class="sxs-lookup"><span data-stu-id="14c4e-153">See Also</span></span>  
 <span data-ttu-id="14c4e-154">[表形式オブジェクトモデルについて](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md) </span><span class="sxs-lookup"><span data-stu-id="14c4e-154">[Understanding the Tabular Object Model](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md) </span></span>  
 <span data-ttu-id="14c4e-155">[CSDLBI の概念](/analysis-services/csdlbi/csdlbi-concepts) </span><span class="sxs-lookup"><span data-stu-id="14c4e-155">[CSDLBI Concepts](/analysis-services/csdlbi/csdlbi-concepts) </span></span>  
 [<span data-ttu-id="14c4e-156">テーブル オブジェクト モデルについて</span><span class="sxs-lookup"><span data-stu-id="14c4e-156">Understanding the Tabular Object Model</span></span>](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
