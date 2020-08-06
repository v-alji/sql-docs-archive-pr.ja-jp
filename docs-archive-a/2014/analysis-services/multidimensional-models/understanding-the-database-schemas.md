---
title: データベーススキーマについてMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Schema Generation Wizard, database schema
- database schema [Analysis Services]
- relational schema [Analysis Services], database schema
- subject area schema options [Analysis Services]
- staging area schema options [Analysis Services]
- denormalized schemas
ms.assetid: 51e411f9-ee3f-4b92-9833-c2bce8c6b752
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f44db1b7abca1b8cad45cf5f46fcc0006bd92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715773"
---
# <a name="understanding-the-database-schemas"></a><span data-ttu-id="be8db-102">データベース スキーマの理解</span><span class="sxs-lookup"><span data-stu-id="be8db-102">Understanding the Database Schemas</span></span>
  <span data-ttu-id="be8db-103">スキーマ生成ウィザードでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のディメンションおよびメジャー グループに基づいて、サブジェクト領域のデータベース用の非正規化されたリレーショナル スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="be8db-103">The Schema Generation Wizard generates a denormalized relational schema for the subject area database based on the dimensions and measure groups in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="be8db-104">このウィザードでは、ディメンション データを格納するための各ディメンション用のリレーショナル テーブル (ディメンション テーブル)、およびファクト データを格納するための各メジャー グループ用のリレーショナル テーブル (ファクト テーブル) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-104">The wizard generates a relational table for each dimension to store dimension data, which is called a dimension table, and a relational table for each measure group to store fact data, which is called a fact table.</span></span> <span data-ttu-id="be8db-105">このウィザードを使用してこれらのリレーショナル テーブルを生成する場合、リンク ディメンション、リンク メジャー グループ、およびサーバー時間ディメンションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-105">The wizard ignores linked dimensions, linked measure groups, and server time dimensions when it generates these relational tables.</span></span>  
  
## <a name="validation"></a><span data-ttu-id="be8db-106">検証</span><span class="sxs-lookup"><span data-stu-id="be8db-106">Validation</span></span>  
 <span data-ttu-id="be8db-107">基になるリレーショナル スキーマの生成を開始する前に、スキーマ生成ウィザードによって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] キューブおよびディメンションが検証されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-107">Before it begins to generate the underlying relational schema, the Schema Generation Wizard validates the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cubes and dimensions.</span></span> <span data-ttu-id="be8db-108">ウィザードによってエラーが検出された場合には、ウィザードは停止し、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [タスク一覧] ウィンドウにエラー レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-108">If the wizard detects errors, it stops and reports the errors to the Task List window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="be8db-109">スキーマの生成を妨げるエラーには次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="be8db-109">Examples of errors that prevent generation include the following:</span></span>  
  
-   <span data-ttu-id="be8db-110">ディメンションに複数のキー属性がある。</span><span class="sxs-lookup"><span data-stu-id="be8db-110">Dimensions that have more than one key attribute.</span></span>  
  
-   <span data-ttu-id="be8db-111">親属性がキー属性と異なるデータ型を持っている。</span><span class="sxs-lookup"><span data-stu-id="be8db-111">Parent attributes that have different data types than the key attributes.</span></span>  
  
-   <span data-ttu-id="be8db-112">メジャー グループにメジャーがない。</span><span class="sxs-lookup"><span data-stu-id="be8db-112">Measure groups that do not have measures.</span></span>  
  
-   <span data-ttu-id="be8db-113">逆ディメンションまたはメジャーが不適切に構成されている。</span><span class="sxs-lookup"><span data-stu-id="be8db-113">Degenerate dimensions or measures that are improperly configured.</span></span>  
  
-   <span data-ttu-id="be8db-114">代理キーが不適切に構成されている (`ScdOriginalID` 属性型を使用した複数の属性や、整数データ型を使用した列にバインドされていない `ScdOriginalID` を使用した属性など)。</span><span class="sxs-lookup"><span data-stu-id="be8db-114">Surrogate keys that are improperly configured, such as multiple attributes using the `ScdOriginalID` attribute type or an attribute using the `ScdOriginalID` that is not bound to a column using the integer data type.</span></span>  
  
## <a name="dimension-tables"></a><span data-ttu-id="be8db-115">ディメンション テーブル</span><span class="sxs-lookup"><span data-stu-id="be8db-115">Dimension Tables</span></span>  
 <span data-ttu-id="be8db-116">各ディメンションに対して、スキーマ生成ウィザードによって、サブジェクト領域データベースに含まれるディメンション テーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-116">For each dimension, the Schema Generation Wizard generates a dimension table to be included in the subject area database.</span></span> <span data-ttu-id="be8db-117">ディメンション テーブルの構造は、基になるディメンションをデザイン中に行った選択によって異なります。</span><span class="sxs-lookup"><span data-stu-id="be8db-117">The structure of the dimension table depends on the choices made while designing the dimension on which it is based.</span></span>  
  
 <span data-ttu-id="be8db-118">[列]</span><span class="sxs-lookup"><span data-stu-id="be8db-118">Columns</span></span>  
 <span data-ttu-id="be8db-119">このウィザードでは、各属性の `KeyColumns`、`NameColumn`、`ValueColumn`、`CustomRollupColumn`、`CustomRollupPropertiesColumn`、および `UnaryOperatorColumn` プロパティのバインドなど、ディメンション テーブルの基になるディメンション内の各属性に関連付けられたバインド用に 1 つの列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-119">The wizard generates one column for the bindings associated to each attribute in the dimension on which the dimension table is based, such as the bindings for the `KeyColumns`, `NameColumn`, `ValueColumn`, `CustomRollupColumn`, `CustomRollupPropertiesColumn`, and `UnaryOperatorColumn` properties of each attribute.</span></span>  
  
 <span data-ttu-id="be8db-120">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="be8db-120">Relationships</span></span>  
 <span data-ttu-id="be8db-121">このウィザードでは、各親属性の列とディメンション テーブルの主キーの間のリレーションシップが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-121">The wizard generates a relationship between the column for each parent attribute and the primary key of the dimension table.</span></span>  
  
 <span data-ttu-id="be8db-122">また、必要に応じて、キューブ内で参照ディメンションとして定義されている、それぞれの追加ディメンション テーブルの主キーへのリレーションシップも生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-122">The wizard also generates a relationship to the primary key in each additional dimension table defined as a referenced dimension in the cube, if applicable.</span></span>  
  
 <span data-ttu-id="be8db-123">制約</span><span class="sxs-lookup"><span data-stu-id="be8db-123">Constraints</span></span>  
 <span data-ttu-id="be8db-124">このウィザードでは、既定で、ディメンションのキー属性に基づいて各ディメンション テーブル用の主キー制約が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-124">The wizard generates a primary key constraint, by default, for each dimension table based on the key attribute of the dimension.</span></span> <span data-ttu-id="be8db-125">主キー制約が生成された場合には、既定で、個別の名前列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-125">If the primary key constraint is generated, a separate name column is generated by default.</span></span> <span data-ttu-id="be8db-126">データベースに主キーを作成しない場合でも、データ ソース ビューに論理主キーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-126">A logical primary key is created in the data source view even if you decide not to create the primary key in the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be8db-127">ディメンション テーブルの基になるディメンションに複数のキー属性が指定されている場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="be8db-127">An error occurs if more than one key attribute is specified in the dimension on which the dimension table is based.</span></span>  
  
 <span data-ttu-id="be8db-128">翻訳</span><span class="sxs-lookup"><span data-stu-id="be8db-128">Translations</span></span>  
 <span data-ttu-id="be8db-129">このウィザードでは、翻訳列が必要なすべての属性に対して、翻訳済みの値を格納する個別のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-129">The wizard generates a separate table to hold the translated values for any attribute that requires a translation column.</span></span> <span data-ttu-id="be8db-130">また、必要な言語ごとに個別の列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-130">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="fact-tables"></a><span data-ttu-id="be8db-131">ファクト テーブル</span><span class="sxs-lookup"><span data-stu-id="be8db-131">Fact Tables</span></span>  
 <span data-ttu-id="be8db-132">キューブ内の各メジャー グループに対して、スキーマ生成ウィザードによって、サブジェクト領域データベースに含まれるファクト テーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-132">For each measure group in a cube, the Schema Generation Wizard generates a fact table to be included in the subject area database.</span></span> <span data-ttu-id="be8db-133">ファクト テーブルの構造は、基になるメジャー グループのデザイン中に行われた選択と、メジャー グループと含まれるディメンションの間のリレーションシップによって異なります。</span><span class="sxs-lookup"><span data-stu-id="be8db-133">The structure of the fact table depends on the choices made while designing the measure group on which it is based, and the relationships established between the measure group and any included dimensions.</span></span>  
  
 <span data-ttu-id="be8db-134">[列]</span><span class="sxs-lookup"><span data-stu-id="be8db-134">Columns</span></span>  
 <span data-ttu-id="be8db-135">このウィザードでは、`Count` 集計関数を使用するメジャー以外の各メジャーに 1 つずつ列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-135">The wizard generates one column for each measure, except for measures that use the `Count` aggregation function.</span></span> <span data-ttu-id="be8db-136">これらのメジャーは、ファクト テーブルに対応する列を必要としません。</span><span class="sxs-lookup"><span data-stu-id="be8db-136">Such measures do not require a corresponding column in the fact table.</span></span>  
  
 <span data-ttu-id="be8db-137">さらに、必要に応じて、メジャー グループ上の標準のディメンション リレーションシップごとの各粒度属性列に 1 つの列が生成され、このテーブルの基になるメジャー グループへのファクト ディメンション リレーションシップがあるディメンションの各属性に関連付けられたバインドに 1 つまたは複数の列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-137">The wizard also generates one column for each granularity attribute column of each regular dimension relationship on the measure group, and one or more columns for the bindings associated to each attribute of a dimension that has a fact dimension relationship to the measure group on which this table is based, if applicable.</span></span>  
  
 <span data-ttu-id="be8db-138">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="be8db-138">Relationships</span></span>  
 <span data-ttu-id="be8db-139">このウィザードでは、ファクト テーブルからディメンション テーブルの粒度属性への標準のディメンション リレーションシップごとに 1 つのリレーションシップが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-139">The wizard generates one relationship for each regular dimension relationship from the fact table to the dimension table's granularity attribute.</span></span> <span data-ttu-id="be8db-140">粒度がディメンション テーブルのキー属性に基づいている場合には、リレーションシップはデータベース内およびデータ ソース ビュー内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-140">If the granularity is based on the key attribute of the dimension table, the relationship is created in the database and in the data source view.</span></span> <span data-ttu-id="be8db-141">粒度がその他の属性に基づいている場合には、リレーションシップはデータ ソース ビュー内のみに作成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-141">If the granularity is based on another attribute, the relationship is created only in the data source view.</span></span>  
  
 <span data-ttu-id="be8db-142">ウィザードでインデックスを生成することを選択した場合は、これらのリレーションシップ列ごとに非クラスター化インデックスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-142">If you chose to generate indexes in the wizard, a nonclustered index is generated for each of these relationship columns.</span></span>  
  
 <span data-ttu-id="be8db-143">制約</span><span class="sxs-lookup"><span data-stu-id="be8db-143">Constraints</span></span>  
 <span data-ttu-id="be8db-144">主キーはファクト テーブル上では生成されません。</span><span class="sxs-lookup"><span data-stu-id="be8db-144">Primary keys are not generated on fact tables.</span></span>  
  
 <span data-ttu-id="be8db-145">参照整合性の適用を選択すると、参照整合性制約がディメンション テーブルとファクト テーブルの間の適切な場所に生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-145">If you chose to enforce referential integrity, referential integrity constraints are generated between dimension tables and fact tables where applicable.</span></span>  
  
 <span data-ttu-id="be8db-146">翻訳</span><span class="sxs-lookup"><span data-stu-id="be8db-146">Translations</span></span>  
 <span data-ttu-id="be8db-147">このウィザードでは、翻訳列を必要とするメジャー グループのすべてのプロパティの翻訳済みの値を格納する個別のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-147">The wizard generates a separate table to hold the translated values for any property in the measure group that requires a translation column.</span></span> <span data-ttu-id="be8db-148">また、必要な言語ごとに個別の列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-148">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="data-type-conversion-and-default-lengths"></a><span data-ttu-id="be8db-149">データ型変換と既定の長さ</span><span class="sxs-lookup"><span data-stu-id="be8db-149">Data Type Conversion and Default Lengths</span></span>  
 <span data-ttu-id="be8db-150">スキーマ生成ウィザードでは、データ型を使用する列を除き、すべての場合にデータ型が無視さ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` れます。</span><span class="sxs-lookup"><span data-stu-id="be8db-150">Schema Generation Wizard ignores data types in all cases except for columns that use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` data type.</span></span> <span data-ttu-id="be8db-151">`wchar` データ サイズは、`nvarchar` データ型に直接変換されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-151">The `wchar` data size translates directly to the `nvarchar` data type.</span></span> <span data-ttu-id="be8db-152">ただし、`wchar` サイズを使用している列の指定された長さが 4,000 バイトより長い場合には、スキーマ生成ウィザードではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="be8db-152">However, if the specified length of a column using the `wchar` size is larger than 4000 bytes, the Schema Generation Wizard generates an error.</span></span>  
  
 <span data-ttu-id="be8db-153">属性のバインドなどのデータ アイテムに長さが指定されていない場合、次の表に示す既定の長さが列に使用されます。</span><span class="sxs-lookup"><span data-stu-id="be8db-153">If a data item, such as the binding for an attribute, has no specified length, the default length listed in the following table is used for the column.</span></span>  
  
|<span data-ttu-id="be8db-154">データ アイテム</span><span class="sxs-lookup"><span data-stu-id="be8db-154">Data item</span></span>|<span data-ttu-id="be8db-155">既定の長さ (バイト)</span><span class="sxs-lookup"><span data-stu-id="be8db-155">Default length (bytes)</span></span>|  
|---------------|------------------------------|  
|<span data-ttu-id="be8db-156">KeyColumn</span><span class="sxs-lookup"><span data-stu-id="be8db-156">KeyColumn</span></span>|<span data-ttu-id="be8db-157">50</span><span class="sxs-lookup"><span data-stu-id="be8db-157">50</span></span>|  
|<span data-ttu-id="be8db-158">NameColumn</span><span class="sxs-lookup"><span data-stu-id="be8db-158">NameColumn</span></span>|<span data-ttu-id="be8db-159">50</span><span class="sxs-lookup"><span data-stu-id="be8db-159">50</span></span>|  
|<span data-ttu-id="be8db-160">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="be8db-160">CustomRollupColumn</span></span>|<span data-ttu-id="be8db-161">3000</span><span class="sxs-lookup"><span data-stu-id="be8db-161">3000</span></span>|  
|<span data-ttu-id="be8db-162">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="be8db-162">CustomRollupPropertiesColumn</span></span>|<span data-ttu-id="be8db-163">500</span><span class="sxs-lookup"><span data-stu-id="be8db-163">500</span></span>|  
|<span data-ttu-id="be8db-164">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="be8db-164">UnaryOperatorColumn</span></span>|<span data-ttu-id="be8db-165">1</span><span class="sxs-lookup"><span data-stu-id="be8db-165">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be8db-166">参照</span><span class="sxs-lookup"><span data-stu-id="be8db-166">See Also</span></span>  
 <span data-ttu-id="be8db-167">[増分生成の理解](understanding-incremental-generation.md) </span><span class="sxs-lookup"><span data-stu-id="be8db-167">[Understanding Incremental Generation](understanding-incremental-generation.md) </span></span>  
 [<span data-ttu-id="be8db-168">データ ソース ビューおよびデータ ソースへの変更の管理</span><span class="sxs-lookup"><span data-stu-id="be8db-168">Manage Changes to Data Source Views and Data Sources</span></span>](manage-changes-to-data-source-views-and-data-sources.md)  
  
  
