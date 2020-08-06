---
title: オブジェクトの名前付け規則 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adfd4b23b6fe9129641271fc3c2381e161119ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643553"
---
# <a name="object-naming-rules-analysis-services"></a><span data-ttu-id="1fccf-102">オブジェクトの名前付け規則 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1fccf-102">Object Naming Rules (Analysis Services)</span></span>
  <span data-ttu-id="1fccf-103">このトピックでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のコードまたはスクリプトにおけるオブジェクトの名前付け規則、および、オブジェクト名で使用できない予約語と文字について説明します。</span><span class="sxs-lookup"><span data-stu-id="1fccf-103">This topic describes object naming conventions, as well as the reserved words and characters that cannot be used in any object name, in code or script in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
##  <a name="naming-conventions"></a><a name="bkmk_Names"></a><span data-ttu-id="1fccf-104">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="1fccf-104">Naming Conventions</span></span>  
 <span data-ttu-id="1fccf-105">あらゆるオブジェクトは `Name` プロパティと `ID` プロパティを持ち、これらは親コレクションのスコープ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fccf-105">Every object has a `Name` and `ID` property that must be unique within the scope of the parent collection.</span></span> <span data-ttu-id="1fccf-106">たとえば、所属するデータベースが異なっていれば、2 つのディメンションが同じ名前であってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-106">For example, two dimensions can have same name as long as each one resides in a different database.</span></span>  
  
 <span data-ttu-id="1fccf-107">手動で指定することもできますが、`ID` は一般にオブジェクトの作成時に自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-107">Although you can specify it manually, the `ID` is typically auto-generated when the object is created.</span></span> <span data-ttu-id="1fccf-108">モデルの構築を開始した後は、`ID` を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="1fccf-108">You should never change the `ID` once you have begun building a model.</span></span> <span data-ttu-id="1fccf-109">モデル内のオブジェクト参照はすべて `ID` に基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-109">All object references throughout a model are based on the `ID`.</span></span> <span data-ttu-id="1fccf-110">したがって、`ID` を変更すると簡単にモデルが壊れます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-110">Thus, changing an `ID` can easily result in model corruption.</span></span>  
  
 <span data-ttu-id="1fccf-111">名前付け規則の例外として、`DataSource` オブジェクトと `DataSourceView` オブジェクトに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1fccf-111">`DataSource` and `DataSourceView` objects have notable exceptions to naming conventions.</span></span> <span data-ttu-id="1fccf-112">`DataSource` の ID は、現在のデータベースの参照として 1 つのドット (.) に設定でき、これは一意ではありません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-112">`DataSource` ID can be set to a single dot (.), which is not unique, as a reference to the current database.</span></span> <span data-ttu-id="1fccf-113">次の例外は、`DataSourceView` で、これは .NET フレームワークの `DataSet` オブジェクト用に定義された名前付け規則に従います。この場合、`Name` が識別子として使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-113">A second exception is `DataSourceView`, which adheres to the naming conventions defined for `DataSet` objects in the .NET Framework, where the `Name` is used as the identifier.</span></span>  
  
 <span data-ttu-id="1fccf-114">`Name` プロパティと `ID` プロパティには、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-114">The following rules apply to `Name` and `ID` properties.</span></span>  
  
-   <span data-ttu-id="1fccf-115">名前では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-115">Names are case insensitive.</span></span> <span data-ttu-id="1fccf-116">同じデータベース内に "sales" という名前のキューブと "Sales" という名前のキューブを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-116">You cannot have a cube named "sales" and another named "Sales" in the same database.</span></span>  
  
-   <span data-ttu-id="1fccf-117">オブジェクト名の先頭または末尾にスペースを付けることは許されません。ただし名前の途中にスペースを入れることはできます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-117">No leading or trailing spaces allowed in an object name, although you can embed spaces within a name.</span></span> <span data-ttu-id="1fccf-118">先頭および末尾にあるスペースは暗黙的に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-118">Leading and trailing spaces are implicitly trimmed.</span></span> <span data-ttu-id="1fccf-119">この規則はオブジェクトの `Name` と `ID` の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-119">This applies to both the `Name` and `ID` of an object.</span></span>  
  
-   <span data-ttu-id="1fccf-120">最大文字数は 100 文字です。</span><span class="sxs-lookup"><span data-stu-id="1fccf-120">The maximum number of characters is 100.</span></span>  
  
-   <span data-ttu-id="1fccf-121">識別子の最初の文字に関する特別な要件はありません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-121">There is no special requirement for the first character of an identifier.</span></span> <span data-ttu-id="1fccf-122">最初の文字には、任意の有効な文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-122">The first character may be any valid character.</span></span>  
  
##  <a name="reserved-words-and-characters"></a><a name="bkmk_reserved"></a><span data-ttu-id="1fccf-123">予約語と文字</span><span class="sxs-lookup"><span data-stu-id="1fccf-123">Reserved Words and Characters</span></span>  
 <span data-ttu-id="1fccf-124">予約語は英語で、オブジェクト名に適用されます。キャプションには適用されません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-124">Reserved words are in English, and apply to object names, not Captions.</span></span> <span data-ttu-id="1fccf-125">不注意で予約語をオブジェクト名に使用すると、検証エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1fccf-125">If you inadvertently use a reserved word in an object name, a validation error will occur.</span></span> <span data-ttu-id="1fccf-126">多次元モデルとデータ マイニング モデルでは、どのような場合でも、以下で説明する予約語をオブジェクト名で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-126">For multidimensional and data mining models, the reserved words described below cannot be used in any object name, at any time.</span></span>  
  
 <span data-ttu-id="1fccf-127">テーブル モデルでは、データベース互換性が 1103 に設定されている場合、一部のオブジェクトで検証ルールが緩められており、一部のクライアント アプリケーションの拡張文字要件と名前付け規則のためにルールに準拠していません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-127">For tabular models, where the database compatibility is set to 1103, validation rules have been relaxed for certain objects, out of compliance for the extended character requirements and naming conventions of certain client applications.</span></span> <span data-ttu-id="1fccf-128">これらの条件を満たすデータベースは、厳格でない検証ルールに従います。</span><span class="sxs-lookup"><span data-stu-id="1fccf-128">Databases that meet these criteria are subject to less stringent validation rules.</span></span> <span data-ttu-id="1fccf-129">この場合、制限された文字がオブジェクト名に使用されていても、検証に合格することがあります。</span><span class="sxs-lookup"><span data-stu-id="1fccf-129">In this case, it's possible for an object name to include a restricted character and still pass validation.</span></span>  
  
 <span data-ttu-id="1fccf-130">**予約語**</span><span class="sxs-lookup"><span data-stu-id="1fccf-130">**Reserved Words**</span></span>  
  
-   <span data-ttu-id="1fccf-131">AUX</span><span class="sxs-lookup"><span data-stu-id="1fccf-131">AUX</span></span>  
  
-   <span data-ttu-id="1fccf-132">CLOCK$</span><span class="sxs-lookup"><span data-stu-id="1fccf-132">CLOCK$</span></span>  
  
-   <span data-ttu-id="1fccf-133">COM1 ～ COM9 (COM1、COM2、COM3 など)</span><span class="sxs-lookup"><span data-stu-id="1fccf-133">COM1 through COM9 (COM1, COM2, COM3, and so on)</span></span>  
  
-   <span data-ttu-id="1fccf-134">CON</span><span class="sxs-lookup"><span data-stu-id="1fccf-134">CON</span></span>  
  
-   <span data-ttu-id="1fccf-135">LPT1 ～ LPT9 (LPT1、LPT2、LPT3 など)</span><span class="sxs-lookup"><span data-stu-id="1fccf-135">LPT1 through LPT9 (LPT1, LPT2, LPT3, and so on)</span></span>  
  
-   <span data-ttu-id="1fccf-136">NUL</span><span class="sxs-lookup"><span data-stu-id="1fccf-136">NUL</span></span>  
  
-   <span data-ttu-id="1fccf-137">PRN</span><span class="sxs-lookup"><span data-stu-id="1fccf-137">PRN</span></span>  
  
-   <span data-ttu-id="1fccf-138">NULL は XML 内の文字列の文字として許容されません。 </span><span class="sxs-lookup"><span data-stu-id="1fccf-138">NULL is not allowed as a character in any string within the XML</span></span>  
  
 <span data-ttu-id="1fccf-139">**予約文字**</span><span class="sxs-lookup"><span data-stu-id="1fccf-139">**Reserved Characters**</span></span>  
  
 <span data-ttu-id="1fccf-140">次の表では、特定のオブジェクトで無効な文字を示します。</span><span class="sxs-lookup"><span data-stu-id="1fccf-140">The following table lists invalid characters for specific objects.</span></span>  
  
|<span data-ttu-id="1fccf-141">Object</span><span class="sxs-lookup"><span data-stu-id="1fccf-141">Object</span></span>|<span data-ttu-id="1fccf-142">無効な文字</span><span class="sxs-lookup"><span data-stu-id="1fccf-142">Invalid characters</span></span>|  
|------------|------------------------|  
|`Server`|<span data-ttu-id="1fccf-143">サーバー オブジェクトに名前を付けるときは、Windows サーバーの名前付け規則に従います。</span><span class="sxs-lookup"><span data-stu-id="1fccf-143">Follow Windows server naming conventions when naming a server object.</span></span> <span data-ttu-id="1fccf-144">詳細については、「[名前付け規則 (Windows)](/windows/desktop/DNS/naming-conventions) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fccf-144">See [Naming Conventions (Windows)](/windows/desktop/DNS/naming-conventions) for details.</span></span>|  
|`DataSource`| `: / \ * \| ? " () [] {} <>` |  
|<span data-ttu-id="1fccf-145">`Level` または `Attribute`</span><span class="sxs-lookup"><span data-stu-id="1fccf-145">`Level` or `Attribute`</span></span>|````. , ; ' ` : / \ * & \| ? " & % $ ! + = [] {} < >````|  
|<span data-ttu-id="1fccf-146">`Dimension` または `Hierarchy`</span><span class="sxs-lookup"><span data-stu-id="1fccf-146">`Dimension` or `Hierarchy`</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} <,>````|  
|<span data-ttu-id="1fccf-147">他のすべてのオブジェクト</span><span class="sxs-lookup"><span data-stu-id="1fccf-147">All other objects</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} < >````|  
  
 <span data-ttu-id="1fccf-148">**例外: 予約文字を使用できる場合**</span><span class="sxs-lookup"><span data-stu-id="1fccf-148">**Exceptions: When Reserved Characters are Allowed**</span></span>  
  
 <span data-ttu-id="1fccf-149">先に述べたように、特定のモダリティと互換性レベルを持つデータベースでは、予約文字を含むオブジェクト名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-149">As noted, databases of a specific modality and compatibility level can have object names that include reserved characters.</span></span> <span data-ttu-id="1fccf-150">拡張文字を使用できる表形式データベース (1103 以上) の場合、ディメンション属性、階層、レベル、メジャー、および KPI オブジェクト名で予約文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-150">Dimension attribute, hierarchy, level, measure and KPI object names can include reserved characters, for tabular databases (1103 or higher) that allow the use of extended characters:</span></span>  
  
|<span data-ttu-id="1fccf-151">サーバー モードとデータベース互換性レベル</span><span class="sxs-lookup"><span data-stu-id="1fccf-151">Server mode and database compatibility level</span></span>|<span data-ttu-id="1fccf-152">予約文字を使用できるか</span><span class="sxs-lookup"><span data-stu-id="1fccf-152">Reserved characters allowed?</span></span>|  
|--------------------------------------------------|----------------------------------|  
|<span data-ttu-id="1fccf-153">MOLAP (すべてのバージョン)</span><span class="sxs-lookup"><span data-stu-id="1fccf-153">MOLAP (all versions)</span></span>|<span data-ttu-id="1fccf-154">いいえ</span><span class="sxs-lookup"><span data-stu-id="1fccf-154">No</span></span>|  
|<span data-ttu-id="1fccf-155">表形式-1050</span><span class="sxs-lookup"><span data-stu-id="1fccf-155">Tabular - 1050</span></span>|<span data-ttu-id="1fccf-156">いいえ</span><span class="sxs-lookup"><span data-stu-id="1fccf-156">No</span></span>|  
|<span data-ttu-id="1fccf-157">表形式 - 1100</span><span class="sxs-lookup"><span data-stu-id="1fccf-157">Tabular - 1100</span></span>|<span data-ttu-id="1fccf-158">いいえ</span><span class="sxs-lookup"><span data-stu-id="1fccf-158">No</span></span>|  
|<span data-ttu-id="1fccf-159">表形式-1130 以降</span><span class="sxs-lookup"><span data-stu-id="1fccf-159">Tabular - 1130 and higher</span></span>|<span data-ttu-id="1fccf-160">はい</span><span class="sxs-lookup"><span data-stu-id="1fccf-160">Yes</span></span>|  
  
 <span data-ttu-id="1fccf-161">データベースは既定の ModelType を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="1fccf-161">Databases can have a ModelType of default.</span></span> <span data-ttu-id="1fccf-162">既定値は多次元モデルと同等です。そのため、列名での予約文字の使用はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1fccf-162">Default is equivalent to multidimensional, and thus does not support the use of reserved characters in column names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fccf-163">参照</span><span class="sxs-lookup"><span data-stu-id="1fccf-163">See Also</span></span>  
 <span data-ttu-id="1fccf-164">[MDX の予約語](/sql/mdx/mdx-reserved-words) </span><span class="sxs-lookup"><span data-stu-id="1fccf-164">[MDX Reserved Words](/sql/mdx/mdx-reserved-words) </span></span>  
 <span data-ttu-id="1fccf-165">[翻訳 &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span><span class="sxs-lookup"><span data-stu-id="1fccf-165">[Translations &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span></span>  
 [<span data-ttu-id="1fccf-166">XMLA&#41;&#40;XML for Analysis コンプライアンス</span><span class="sxs-lookup"><span data-stu-id="1fccf-166">XML for Analysis Compliance &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
