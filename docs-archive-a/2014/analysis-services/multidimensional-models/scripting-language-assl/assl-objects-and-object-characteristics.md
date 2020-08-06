---
title: ASSL オブジェクトとオブジェクトの特性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d57bb421a7f486983476a6549a5121ce88ee9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642986"
---
# <a name="assl-objects-and-object-characteristics"></a><span data-ttu-id="200a3-102">ASSL オブジェクトとオブジェクトの特性</span><span class="sxs-lookup"><span data-stu-id="200a3-102">ASSL Objects and Object Characteristics</span></span>
  <span data-ttu-id="200a3-103">Analysis Services スクリプト言語 (ASSL) のオブジェクトは、オブジェクト グループ、継承、名前付け、展開、および処理に関して特定のガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="200a3-103">Objects in Analysis Services Scripting Language (ASSL) follow specific guidelines in regards to object groups, inheritance, naming, expansion, and processing.</span></span>  
  
## <a name="object-groups"></a><span data-ttu-id="200a3-104">オブジェクト グループ</span><span class="sxs-lookup"><span data-stu-id="200a3-104">Object Groups</span></span>  
 <span data-ttu-id="200a3-105">すべて [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のオブジェクトには XML 表現があります。</span><span class="sxs-lookup"><span data-stu-id="200a3-105">All [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects have an XML representation.</span></span> <span data-ttu-id="200a3-106">オブジェクトは 2 つのグループに分けられます。</span><span class="sxs-lookup"><span data-stu-id="200a3-106">The objects are divided into two groups:</span></span>  
  
 <span data-ttu-id="200a3-107">**主要なオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="200a3-107">**Major objects**</span></span>  
 <span data-ttu-id="200a3-108">主要なオブジェクトは、個別に作成、変更、削除することができます。</span><span class="sxs-lookup"><span data-stu-id="200a3-108">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="200a3-109">主要なオブジェクトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="200a3-109">Major objects include:</span></span>  
  
-   <span data-ttu-id="200a3-110">サーバー</span><span class="sxs-lookup"><span data-stu-id="200a3-110">Servers</span></span>  
  
-   <span data-ttu-id="200a3-111">データベース</span><span class="sxs-lookup"><span data-stu-id="200a3-111">Databases</span></span>  
  
-   <span data-ttu-id="200a3-112">Dimensions</span><span class="sxs-lookup"><span data-stu-id="200a3-112">Dimensions</span></span>  
  
-   <span data-ttu-id="200a3-113">キューブ</span><span class="sxs-lookup"><span data-stu-id="200a3-113">Cubes</span></span>  
  
-   <span data-ttu-id="200a3-114">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="200a3-114">Measure groups</span></span>  
  
-   <span data-ttu-id="200a3-115">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="200a3-115">Partitions</span></span>  
  
-   <span data-ttu-id="200a3-116">パースペクティブ</span><span class="sxs-lookup"><span data-stu-id="200a3-116">Perspectives</span></span>  
  
-   <span data-ttu-id="200a3-117">[マイニング モデル]</span><span class="sxs-lookup"><span data-stu-id="200a3-117">Mining models</span></span>  
  
-   <span data-ttu-id="200a3-118">ロール</span><span class="sxs-lookup"><span data-stu-id="200a3-118">Roles</span></span>  
  
-   <span data-ttu-id="200a3-119">サーバーまたはデータベースに関連付けられているコマンド</span><span class="sxs-lookup"><span data-stu-id="200a3-119">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="200a3-120">データ ソース</span><span class="sxs-lookup"><span data-stu-id="200a3-120">Data sources</span></span>  
  
 <span data-ttu-id="200a3-121">主要なオブジェクトには、その履歴と状態を追跡するための次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="200a3-121">Major objects have the following properties to track their history and status.</span></span>  
  
-   `CreatedTimestamp`  
  
-   `LastSchemaUpdate`  
  
-   <span data-ttu-id="200a3-122">`LastProcessed` (必要な場合)</span><span class="sxs-lookup"><span data-stu-id="200a3-122">`LastProcessed` (where appropriate)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="200a3-123">オブジェクトを主要なオブジェクトとして分類すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスによるオブジェクトの処理方法と、オブジェクト定義言語でのオブジェクトの処理方法に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="200a3-123">The classification of an object as a major object affects how an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] treats that object and how that object is handled in the object definition language.</span></span> <span data-ttu-id="200a3-124">ただし、この分類によって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理ツールおよび開発ツールでこれらのオブジェクトを単独作成、修正、または削除できることが保証されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="200a3-124">However, this classification does not guarantee that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] management and development tools will allow the independent creation, modification, or deletion of these objects.</span></span>  
  
 <span data-ttu-id="200a3-125">**マイナー オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="200a3-125">**Minor objects**</span></span>  
 <span data-ttu-id="200a3-126">マイナー オブジェクトは、主要な親オブジェクトの作成、変更、または削除の一部としてのみ、作成、変更、または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="200a3-126">Minor objects can only be created, altered, or deleted as part of creating, altering, or deleting the parent major object.</span></span> <span data-ttu-id="200a3-127">マイナー オブジェクトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="200a3-127">Minor objects include:</span></span>  
  
-   <span data-ttu-id="200a3-128">階層とレベル</span><span class="sxs-lookup"><span data-stu-id="200a3-128">Hierarchies and levels</span></span>  
  
-   <span data-ttu-id="200a3-129">属性</span><span class="sxs-lookup"><span data-stu-id="200a3-129">Attributes</span></span>  
  
-   <span data-ttu-id="200a3-130">メジャー</span><span class="sxs-lookup"><span data-stu-id="200a3-130">Measures</span></span>  
  
-   <span data-ttu-id="200a3-131">マイニングモデル列</span><span class="sxs-lookup"><span data-stu-id="200a3-131">Mining model columns</span></span>  
  
-   <span data-ttu-id="200a3-132">キューブに関連付けられているコマンド</span><span class="sxs-lookup"><span data-stu-id="200a3-132">Commands associated with a cube</span></span>  
  
-   <span data-ttu-id="200a3-133">集計</span><span class="sxs-lookup"><span data-stu-id="200a3-133">Aggregations</span></span>  
  
## <a name="object-expansion"></a><span data-ttu-id="200a3-134">オブジェクトの展開</span><span class="sxs-lookup"><span data-stu-id="200a3-134">Object Expansion</span></span>  
 <span data-ttu-id="200a3-135">`ObjectExpansion` 制限は、サーバーから返される ASSL XML をどの程度展開するかを制御するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="200a3-135">The `ObjectExpansion` restriction can be used to control the degree of expansion of ASSL XML returned by the server.</span></span> <span data-ttu-id="200a3-136">次の表には、この制限のオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="200a3-136">This restriction has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="200a3-137">列挙値</span><span class="sxs-lookup"><span data-stu-id="200a3-137">Enumeration value</span></span>|<span data-ttu-id="200a3-138">許可される対象\<Alter></span><span class="sxs-lookup"><span data-stu-id="200a3-138">Allowed for \<Alter></span></span>|<span data-ttu-id="200a3-139">説明</span><span class="sxs-lookup"><span data-stu-id="200a3-139">Description</span></span>|  
|-----------------------|---------------------------|-----------------|  
|<span data-ttu-id="200a3-140">*ReferenceOnly*</span><span class="sxs-lookup"><span data-stu-id="200a3-140">*ReferenceOnly*</span></span>|<span data-ttu-id="200a3-141">no</span><span class="sxs-lookup"><span data-stu-id="200a3-141">no</span></span>|<span data-ttu-id="200a3-142">要求されたオブジェクトおよび含まれているすべての主要なオブジェクトの名前、ID、およびタイムスタンプだけを再帰的に返します。</span><span class="sxs-lookup"><span data-stu-id="200a3-142">Returns only the name, ID, and timestamp for the requested object and for all contained major objects recursively.</span></span>|  
|<span data-ttu-id="200a3-143">*ObjectProperties*</span><span class="sxs-lookup"><span data-stu-id="200a3-143">*ObjectProperties*</span></span>|<span data-ttu-id="200a3-144">可</span><span class="sxs-lookup"><span data-stu-id="200a3-144">yes</span></span>|<span data-ttu-id="200a3-145">要求されたオブジェクトと含まれいているマイナー オブジェクトを展開し、含まれている主要なオブジェクトは返しません。</span><span class="sxs-lookup"><span data-stu-id="200a3-145">Expands the requested object and minor contained objects, but does not return major contained objects.</span></span>|  
|<span data-ttu-id="200a3-146">*全場合*</span><span class="sxs-lookup"><span data-stu-id="200a3-146">*ExpandObject*</span></span>|<span data-ttu-id="200a3-147">Ｘ</span><span class="sxs-lookup"><span data-stu-id="200a3-147">no</span></span>|<span data-ttu-id="200a3-148">*Objectproperties*と同じですが、含まれている主要なオブジェクトの名前、ID、タイムスタンプも返されます。</span><span class="sxs-lookup"><span data-stu-id="200a3-148">Same as *ObjectProperties*, but also returns the name, ID, and timestamp for contained major objects.</span></span>|  
|<span data-ttu-id="200a3-149">*ExpandFull*</span><span class="sxs-lookup"><span data-stu-id="200a3-149">*ExpandFull*</span></span>|<span data-ttu-id="200a3-150">可</span><span class="sxs-lookup"><span data-stu-id="200a3-150">yes</span></span>|<span data-ttu-id="200a3-151">要求されたオブジェクトと含まれているすべてのオブジェクトを再帰的に完全に展開します。</span><span class="sxs-lookup"><span data-stu-id="200a3-151">Fully expands the requested object and all contained objects recursively.</span></span>|  
  
 <span data-ttu-id="200a3-152">この ASSL リファレンスセクションでは、 *Expandfull*表現について説明します。</span><span class="sxs-lookup"><span data-stu-id="200a3-152">This ASSL reference section describes the *ExpandFull* representation.</span></span> <span data-ttu-id="200a3-153">他のすべての `ObjectExpansion` レベルがこのレベルから派生します。</span><span class="sxs-lookup"><span data-stu-id="200a3-153">All other `ObjectExpansion` levels are derived from this level.</span></span>  
  
## <a name="object-processing"></a><span data-ttu-id="200a3-154">オブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="200a3-154">Object Processing</span></span>  
 <span data-ttu-id="200a3-155">ASSL には、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスから読み取ることはできても、そのインスタンスにコマンド スクリプトが送信されるときに省略される読み取り専用の要素またはプロパティ (`LastProcessed` など) があります。</span><span class="sxs-lookup"><span data-stu-id="200a3-155">ASSL includes read-only elements or properties (for example, `LastProcessed`) that can be read from the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, but which are omitted when command scripts are submitted to the instance.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]  <span data-ttu-id="200a3-156">では、読み取り専用の要素の変更された値を無視し、警告やエラーを返しません。</span><span class="sxs-lookup"><span data-stu-id="200a3-156">ignores modified values for read-only elements without warning or error.</span></span>  
  
 <span data-ttu-id="200a3-157">また、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、不適切なプロパティや無関係なプロパティは無視し、検証エラーを返しません。</span><span class="sxs-lookup"><span data-stu-id="200a3-157">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] also ignores inappropriate or irrelevant properties without raising validation errors.</span></span> <span data-ttu-id="200a3-158">たとえば、Y 要素に特定の値がある場合、X 要素は存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="200a3-158">For example, the X element should only be present when the Y element has a particular value.</span></span> <span data-ttu-id="200a3-159">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスでは、X 要素を無視し、Y 要素の値に対して X 要素を検証しません。</span><span class="sxs-lookup"><span data-stu-id="200a3-159">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance ignores the X element instead of validating that element against the value of the Y element.</span></span>  
  
  
