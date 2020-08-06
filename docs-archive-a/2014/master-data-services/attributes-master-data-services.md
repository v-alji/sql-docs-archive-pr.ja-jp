---
title: 属性 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5a6fb01b47658f39e14c599ae88aa7ad3d29c69a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644012"
---
# <a name="attributes-master-data-services"></a><span data-ttu-id="b7fa9-102">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-102">Attributes (Master Data Services)</span></span>
  <span data-ttu-id="b7fa9-103">属性とは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] エンティティに含まれるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-103">Attributes are objects that are contained in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] entities.</span></span> <span data-ttu-id="b7fa9-104">属性値はエンティティのメンバーを表します。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-104">Attribute values describe the members of the entity.</span></span> <span data-ttu-id="b7fa9-105">属性を使用してリーフ メンバー、統合メンバー、またはコレクションを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-105">An attribute can be used to describe a leaf member, a consolidated member, or a collection.</span></span>  
  
## <a name="how-attributes-relate-to-other-model-objects"></a><span data-ttu-id="b7fa9-106">属性と他のモデル オブジェクトとの関連付け</span><span class="sxs-lookup"><span data-stu-id="b7fa9-106">How Attributes Relate to Other Model Objects</span></span>  
 <span data-ttu-id="b7fa9-107">属性は、エンティティ テーブルの列と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-107">You can think of an attribute as a column in an entity table.</span></span> <span data-ttu-id="b7fa9-108">属性値は、特定のメンバーを表すために使用される値です。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-108">An attribute value is the value used to describe a specific member.</span></span>  
  
 <span data-ttu-id="b7fa9-109">![テーブルとして表されたマスター データ サービス エンティティ](../../2014/master-data-services/media/mds-conc-entity-table.gif "テーブルとして表されたマスター データ サービス エンティティ")</span><span class="sxs-lookup"><span data-stu-id="b7fa9-109">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>  
  
 <span data-ttu-id="b7fa9-110">多数の属性を含むエンティティを作成するときは、属性を属性グループに整理できます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-110">When you create an entity that contains many attributes, you can organize the attributes into attribute groups.</span></span> <span data-ttu-id="b7fa9-111">詳細については、「 [属性グループ (マスター データ サービス)](attribute-groups-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-111">For more information, see [Attribute Groups &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).</span></span>  
  
## <a name="required-attributes"></a><span data-ttu-id="b7fa9-112">必須の属性</span><span class="sxs-lookup"><span data-stu-id="b7fa9-112">Required Attributes</span></span>  
 <span data-ttu-id="b7fa9-113">エンティティを作成すると、Name 属性と Code 属性が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-113">When you create an entity, the Name and Code attributes are automatically created.</span></span> <span data-ttu-id="b7fa9-114">Code 属性には値が必要であり、Code 属性はエンティティ内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-114">Code requires a value and must be unique within the entity.</span></span> <span data-ttu-id="b7fa9-115">Name 属性と Code 属性を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-115">You cannot remove the Name and Code attributes.</span></span>  
  
## <a name="attribute-types"></a><span data-ttu-id="b7fa9-116">属性の種類</span><span class="sxs-lookup"><span data-stu-id="b7fa9-116">Attribute Types</span></span>  
 <span data-ttu-id="b7fa9-117">次の 3 種類の属性があります。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-117">There are three types of attributes:</span></span>  
  
-   <span data-ttu-id="b7fa9-118">自由形式属性。テキスト、数値、日付、またはリンクを自由形式で入力できます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-118">Free-form attributes, which allow free-form input for text, numbers, dates, or links.</span></span>  
  
-   <span data-ttu-id="b7fa9-119">ドメイン ベースの属性。エンティティによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-119">Domain-based attributes, which are populated by entities.</span></span> <span data-ttu-id="b7fa9-120">詳細については、「 [ドメインベースの属性 (マスター データ サービス)](../../2014/master-data-services/domain-based-attributes-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-120">For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="b7fa9-121">ファイル属性。ファイル、ドキュメント、または画像を格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-121">File attributes, which are used to store files, documents, or images.</span></span> <span data-ttu-id="b7fa9-122">ファイル属性は、ファイルに特定の拡張子を付けることによって、データの一貫性を確保するためのものです。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-122">File attributes are intended to help with the consistency of your data by requiring files to have a specific extension.</span></span> <span data-ttu-id="b7fa9-123">悪意のあるユーザーによる異なる種類のファイルのアップロードを防ぐことを保証するものではありません。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-123">File attributes cannot be guaranteed to prevent a malicious user from uploading a file of a different type.</span></span>  
  
### <a name="numeric-free-form-attributes"></a><span data-ttu-id="b7fa9-124">数値自由形式属性</span><span class="sxs-lookup"><span data-stu-id="b7fa9-124">Numeric Free-Form Attributes</span></span>  
 <span data-ttu-id="b7fa9-125">数値自由形式属性値は **SqlDouble** 値型に限定されるため、この属性には特別な処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-125">Numeric free-form attributes require special handling, because numeric free-form attribute values are limited to the **SqlDouble** value type.</span></span>  
  
 <span data-ttu-id="b7fa9-126">既定では、 **SqlDouble** 値には有効桁数 15 桁の 10 進数が含まれますが、内部的には最大 17 桁が保持されています。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-126">By default, a **SqlDouble** value contains 15 decimal digits of precision, although a maximum of 17 digits is maintained internally.</span></span> <span data-ttu-id="b7fa9-127">浮動小数点数の有効桁数により、複数の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-127">The precision of a floating-point number has several consequences:</span></span>  
  
-   <span data-ttu-id="b7fa9-128">特定の有効桁数で等しく見える 2 つの浮動小数点数が、最小有効数字が異なっているために等しくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-128">Two floating-point numbers that appear equal for a particular precision might not compare equal because their least significant digits are different.</span></span>  
  
-   <span data-ttu-id="b7fa9-129">浮動小数点数を使用する数学的演算または比較演算で小数が使用された場合は、浮動小数点数がその小数に正確に近似していない場合があるため、同じ結果が生成されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-129">A mathematical or comparison operation that uses a floating-point number might not yield the same result if a decimal number is used because the floating-point number might not exactly approximate the decimal number.</span></span>  
  
-   <span data-ttu-id="b7fa9-130">浮動小数点数が含まれていると、値が " *ラウンド トリップ* " されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-130">A value might not *roundtrip* if a floating-point number is involved.</span></span> <span data-ttu-id="b7fa9-131">値のラウンド トリップとは、演算で元の浮動小数点数が別の形式に変換され、逆の演算で変換後の形式から浮動小数点数に戻されて、最終の浮動小数点数が元の浮動小数点数に等しくなる場合をいいます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-131">A value is said to roundtrip if an operation converts an original floating-point number to another form, an inverse operation transforms the converted form back to a floating-point number, and the final floating-point number is equal to the original floating-point number.</span></span> <span data-ttu-id="b7fa9-132">変換で最小有効数字が 1 桁以上失われるか、または変更された場合は、ラウンド トリップが失敗します。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-132">The roundtrip might fail because one or more least significant digits are lost or changed in a conversion.</span></span>  
  
## <a name="attribute-examples"></a><span data-ttu-id="b7fa9-133">属性の例</span><span class="sxs-lookup"><span data-stu-id="b7fa9-133">Attribute Examples</span></span>  
 <span data-ttu-id="b7fa9-134">次の例では、エンティティに Name、Code、Subcategory、StandardCost、ListPrice、および FilePhoto という属性があります。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-134">In the following example, the entity has the attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto.</span></span> <span data-ttu-id="b7fa9-135">これらの属性はメンバーを表します。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-135">These attributes describe the members.</span></span> <span data-ttu-id="b7fa9-136">各メンバーは、属性値の 1 行で表されます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-136">Each member is represented by a single row of attribute values.</span></span>  
  
 <span data-ttu-id="b7fa9-137">![自転車製品エンティティ テーブル](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自転車製品エンティティ テーブル")</span><span class="sxs-lookup"><span data-stu-id="b7fa9-137">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>  
  
 <span data-ttu-id="b7fa9-138">次の例では、Product エンティティに次の属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-138">In the following example, the Product entity contains:</span></span>  
  
-   <span data-ttu-id="b7fa9-139">自由形式属性 Name、Code、StandardCost、および ListPrice</span><span class="sxs-lookup"><span data-stu-id="b7fa9-139">The free-form attributes of Name, Code, StandardCost and ListPrice.</span></span>  
  
-   <span data-ttu-id="b7fa9-140">ドメイン ベースの属性 Subcategory</span><span class="sxs-lookup"><span data-stu-id="b7fa9-140">The domain-based attribute of Subcategory.</span></span>  
  
-   <span data-ttu-id="b7fa9-141">ファイル属性 FilePhoto</span><span class="sxs-lookup"><span data-stu-id="b7fa9-141">The file attribute of FilePhoto.</span></span>  
  
 <span data-ttu-id="b7fa9-142">Subcategory は、Product のドメイン ベースの属性として使用されるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-142">Subcategory is an entity that is used as a domain-based attribute of Product.</span></span> <span data-ttu-id="b7fa9-143">Category は、Subcategory のドメイン ベースの属性として使用されるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-143">Category is an entity that is used as a domain-based attribute of Subcategory.</span></span> <span data-ttu-id="b7fa9-144">Product エンティティと同様に、Category エンティティと Subcategory エンティティにはそれぞれ、既定の Name 属性と Code 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-144">Like the Product entity, the Category and Subcategory entities each contain the default Name and Code attributes.</span></span>  
  
 <span data-ttu-id="b7fa9-145">![製品エンティティ ツリー構造](../../2014/master-data-services/media/mds-conc-entity-ui.gif "製品エンティティ ツリー構造")</span><span class="sxs-lookup"><span data-stu-id="b7fa9-145">![Product Entity Tree Structure](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Product Entity Tree Structure")</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b7fa9-146">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b7fa9-146">Related Tasks</span></span>  
  
|<span data-ttu-id="b7fa9-147">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="b7fa9-147">Task Description</span></span>|<span data-ttu-id="b7fa9-148">トピック</span><span class="sxs-lookup"><span data-stu-id="b7fa9-148">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="b7fa9-149">新しい自由形式のテキスト属性を作成する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-149">Create a new free-form text attribute.</span></span>|[<span data-ttu-id="b7fa9-150">テキスト属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-150">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)|  
|<span data-ttu-id="b7fa9-151">新しい自由形式の数値属性を作成する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-151">Create a new free-form numeric attribute.</span></span>|[<span data-ttu-id="b7fa9-152">数値属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-152">Create a Numeric Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|<span data-ttu-id="b7fa9-153">新しい自由形式のリンク属性を作成する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-153">Create a new free-form link attribute.</span></span>|[<span data-ttu-id="b7fa9-154">リンク属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-154">Create a Link Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)|  
|<span data-ttu-id="b7fa9-155">新しいファイル属性を作成する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-155">Create a new file attribute.</span></span>|[<span data-ttu-id="b7fa9-156">ファイル属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-156">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|<span data-ttu-id="b7fa9-157">新しいドメインベース属性を作成する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-157">Create a new domain-based attribute.</span></span>|[<span data-ttu-id="b7fa9-158">ドメイン ベースの属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-158">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|<span data-ttu-id="b7fa9-159">既存の属性の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-159">Change the name of an existing attribute.</span></span>|[<span data-ttu-id="b7fa9-160">属性名を変更する &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="b7fa9-160">Change an Attribute Name &#40;Master Data Services&#41;</span></span>](change-an-attribute-name-and-data-type-master-data-services.md)|  
|<span data-ttu-id="b7fa9-161">変更の追跡グループに既存の属性を追加する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-161">Add existing attributes to a change tracking group.</span></span>|[<span data-ttu-id="b7fa9-162">変更の追跡グループに属性を追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-162">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="b7fa9-163">既存の属性を削除する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-163">Delete an existing attribute.</span></span>|[<span data-ttu-id="b7fa9-164">属性を削除する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="b7fa9-164">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)|  
|<span data-ttu-id="b7fa9-165">属性の順序を変更する。</span><span class="sxs-lookup"><span data-stu-id="b7fa9-165">Change the order of attributes.</span></span>|[<span data-ttu-id="b7fa9-166">属性の順序の変更</span><span class="sxs-lookup"><span data-stu-id="b7fa9-166">Change the Order of Attributes</span></span>](../../2014/master-data-services/change-the-order-of-attributes.md)|  
  
## <a name="related-content"></a><span data-ttu-id="b7fa9-167">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b7fa9-167">Related Content</span></span>  
  
-   [<span data-ttu-id="b7fa9-168">ドメインベースの属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-168">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [<span data-ttu-id="b7fa9-169">属性グループ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-169">Attribute Groups &#40;Master Data Services&#41;</span></span>](attribute-groups-master-data-services.md)  
  
-   [<span data-ttu-id="b7fa9-170">メンバー (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-170">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
-   [<span data-ttu-id="b7fa9-171">リーフ権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b7fa9-171">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [<span data-ttu-id="b7fa9-172">統合アクセス許可 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="b7fa9-172">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
