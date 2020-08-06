---
title: DirectQuery モードでの DAX 数式の互換性 (SSAS 2014) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: acaac82d6930787a45281c0e942def8df764f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639781"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a><span data-ttu-id="d509f-102">DirectQuery モードでの DAX 数式の互換性 (SSAS 2014)</span><span class="sxs-lookup"><span data-stu-id="d509f-102">DAX Formula Compatibility in DirectQuery Mode (SSAS 2014)</span></span>
<span data-ttu-id="d509f-103">Data Analysis Expression 言語 (DAX) を使用すると、Analysis Services テーブルモデル、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Excel ブックのデータモデル、および Power BI Desktop データモデルで使用するメジャーやその他のカスタム式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d509f-103">The Data Analysis Expression language (DAX) can be used to create measures and other custom formulas for use in Analysis Services Tabular models, [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] data models in Excel workbooks, and Power BI Desktop data models.</span></span> <span data-ttu-id="d509f-104">ほとんどの場合、これらの環境で作成するモデルは同じであり、同じメジャー、リレーションシップ、および Kpi などを使用できます。ただし、Analysis Services テーブルモデルを作成して DirectQuery モードで配置した場合は、使用できる数式にいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-104">In most respects, the models you create in these environments are identical, and you can use the same measures, relationships, and KPIs, etc. However, if you author an Analysis Services Tabular model and deploy it in DirectQuery mode, there are some restrictions on the formulas that you can use.</span></span> <span data-ttu-id="d509f-105">このトピックでは、これらの違いの概要について説明します。 SQL Server 2014 Analysis Services tabulars モデルでサポートされていない機能を互換性レベル1100または1103と DirectQuery モードで一覧表示し、サポートされているが、異なる結果を返す可能性のある関数を示します。</span><span class="sxs-lookup"><span data-stu-id="d509f-105">This topic provides an overview of those differences, lists the functions that are not supported in SQL Server 2014 Analysis Services tabulars model at compatibility level 1100 or 1103 and in DirectQuery mode, and lists the functions that are supported but might return different results.</span></span>  
  
<span data-ttu-id="d509f-106">このトピックでは、*インメモリモデル*という用語を使用して、テーブルモデルを参照します。テーブルモデルは、表形式モードで実行されている Analysis Services サーバー上のメモリ内キャッシュされたデータを完全にホストします。</span><span class="sxs-lookup"><span data-stu-id="d509f-106">Within this topic, we use the term *in-memory model* to refer to  Tabular models, which are fully hosted in-memory cached data on an Analysis Services server running in Tabular mode.</span></span> <span data-ttu-id="d509f-107">Directquery*モデル*は、directquery モードで作成または配置されたテーブルモデルを参照するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d509f-107">We use *DirectQuery models* to refer to Tabular models that have been authored and/or deployed in DirectQuery mode.</span></span> <span data-ttu-id="d509f-108">DirectQuery モードの詳細については、「 [Directquery モード (SSAS テーブル)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d509f-108">For information about DirectQuery mode, see [DirectQuery Mode (SSAS Tabular)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5).</span></span>  
  
  
## <a name="differences-between-in-memory-and-directquery-mode"></a><a name="bkmk_SemanticDifferences"></a><span data-ttu-id="d509f-109">インメモリ モードと DirectQuery モードの違い</span><span class="sxs-lookup"><span data-stu-id="d509f-109">Differences between in-memory and DirectQuery mode</span></span>  
<span data-ttu-id="d509f-110">DirectQuery モードで配置されたモデルでのクエリは、同じモデルがインメモリで配置されたときとは異なる結果を返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-110">Queries on a model deployed in DirectQuery mode can return different results than the same model deployed in in-memory mode.</span></span> <span data-ttu-id="d509f-111">これは、DirectQuery では、データがリレーショナルデータストアから直接クエリされ、数式に必要な集計が、ストレージと計算に xVelocity メモリ内分析エンジン (VertiPaq) を使用するのではなく、関連するリレーショナルエンジンを使用して実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="d509f-111">This is because with DirectQuery, data is queried directly from a relational data store and aggregations required by formulas are performed using the relevant relational engine, rather than using the xVelocity in-memory analytics engine (VertiPaq) for storage and calculation.</span></span>  
  
<span data-ttu-id="d509f-112">たとえば、特定のリレーショナル データ ストアが数値、日付、null などを処理する方法に違いがあります。</span><span class="sxs-lookup"><span data-stu-id="d509f-112">For example, there are differences in the way that certain relational data stores handle numeric values, dates, nulls, and so forth.</span></span>  
  
<span data-ttu-id="d509f-113">一方、DAX 言語は、Microsoft Excel での関数の動作をできる限り忠実にエミュレートするようになっています。</span><span class="sxs-lookup"><span data-stu-id="d509f-113">In contrast, the DAX language is intended to emulate as closely as possible the behavior of functions in Microsoft Excel.</span></span> <span data-ttu-id="d509f-114">たとえば、null、空の文字列、ゼロ値を処理するときに、Excel では正確なデータ型に関係なく最善の結果を提供するようになっているため、xVelocity エンジンも同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="d509f-114">For example, when handling nulls, empty strings and zero values, Excel attempts to provide the best answer regardless of the precise data type, and therefore the xVelocity engine does the same.</span></span> <span data-ttu-id="d509f-115">ただし、テーブルモデルが DirectQuery モードで配置され、評価のためにリレーショナルデータソースに数式を渡す場合、データはリレーショナルデータソースのセマンティクスに従って処理される必要があります。この場合、通常は空の文字列と null を個別に処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-115">However, when a tabular model is deployed in DirectQuery mode and passes formulas to a relational data source for evaluation, the data must be handled according to the semantics of the relational data source, which typically require distinct handling of empty strings vs. nulls.</span></span> <span data-ttu-id="d509f-116">このため、同じ数式でも、キャッシュされたデータに対して評価されるときと、リレーショナル ストアから戻されたデータのみに対して評価されるときでは、異なる結果が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-116">For this reason, the same formula might return a different result when evaluated against cached data and against data returned solely from the relational store.</span></span>  
  
<span data-ttu-id="d509f-117">また、一部の関数は、現在のコンテキストのデータをパラメーターとしてリレーショナルデータソースに送信する必要があるため、DirectQuery モードではまったく使用できません。</span><span class="sxs-lookup"><span data-stu-id="d509f-117">Additionally, some functions cannot be used at all in DirectQuery mode because the calculation would require the data in the current context be sent to the relational data source as a parameter.</span></span> <span data-ttu-id="d509f-118">たとえば、ブック内のメジャーは、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブック内で使用できる日付範囲を参照するタイムインテリジェンス関数を使用することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="d509f-118">For example, measures in a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] workbook often use time-intelligence functions that reference date ranges available within the workbook.</span></span> <span data-ttu-id="d509f-119">このような数式は、一般に、DirectQuery モードでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d509f-119">Such formulas generally cannot be used in DirectQuery mode.</span></span>  
  
## <a name="semantic-differences"></a><span data-ttu-id="d509f-120">セマンティックの相違</span><span class="sxs-lookup"><span data-stu-id="d509f-120">Semantic differences</span></span>  
<span data-ttu-id="d509f-121">このセクションでは、予想されるセマンティックの相違の種類の一覧を示し、関数の使用方法またはクエリの結果に適用される可能性のある制限について説明します。</span><span class="sxs-lookup"><span data-stu-id="d509f-121">This section lists the types of semantic differences that you can expect, and describes any limitations that might apply to the usage of functions or to query results.</span></span>  
  
### <a name="comparisons"></a><a name="bkmk_Comparisons"></a><span data-ttu-id="d509f-122">比較</span><span class="sxs-lookup"><span data-stu-id="d509f-122">Comparisons</span></span>  
<span data-ttu-id="d509f-123">インメモリ モデルでの DAX は、異なるデータ型のスカラー値に解決される 2 つの式の比較をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d509f-123">DAX in in-memory models support comparisons of two expressions that resolve to scalar values of different data types.</span></span> <span data-ttu-id="d509f-124">一方、DirectQuery モードで配置されるモデルはリレーショナル エンジンのデータ型と比較演算子を使用するので、異なる結果が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-124">However, models that are deployed in DirectQuery mode use the data types and comparison operators of the relational engine, and therefore might return different results.</span></span>  
  
<span data-ttu-id="d509f-125">次の比較は、DirectQuery データ ソースでの計算で使用すると、常にエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-125">The following comparisons will always return an error when used in a calculation on a DirectQuery data source:</span></span>  
  
-   <span data-ttu-id="d509f-126">数値データ型と任意の文字列データ型の比較</span><span class="sxs-lookup"><span data-stu-id="d509f-126">Numeric data type compared to any string data type</span></span>  
  
-   <span data-ttu-id="d509f-127">数値データ型とブール値の比較</span><span class="sxs-lookup"><span data-stu-id="d509f-127">Numeric data type compared to a Boolean value</span></span>  
  
-   <span data-ttu-id="d509f-128">任意の文字列データ型とブール値の比較</span><span class="sxs-lookup"><span data-stu-id="d509f-128">Any string data type compared to a Boolean value</span></span>  
  
<span data-ttu-id="d509f-129">一般に、DAX はインメモリ モデルでの方がデータ型の不一致に対して寛容であり、このセクションで説明するように、最大で 2 回は値の暗黙のキャストを試みます。</span><span class="sxs-lookup"><span data-stu-id="d509f-129">In general, DAX is more forgiving of data type mismatches in in-memory models and will attempt an implicit cast of values up to two times, as described in this section.</span></span> <span data-ttu-id="d509f-130">一方、DirectQuery モードのリレーショナル データ ストアに送信される数式の方が、リレーショナル エンジンの規則に従ってより厳密に評価され、失敗する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="d509f-130">However, formulas sent to a relational data store in DirectQuery mode are evaluated more strictly, following the rules of the relational engine, and are more likely to fail.</span></span>  
  
<span data-ttu-id="d509f-131">**文字列と数値の比較**</span><span class="sxs-lookup"><span data-stu-id="d509f-131">**Comparisons of strings and numbers**</span></span>  
<span data-ttu-id="d509f-132">例: `"2" < 3`</span><span class="sxs-lookup"><span data-stu-id="d509f-132">EXAMPLE: `"2" < 3`</span></span>  
  
<span data-ttu-id="d509f-133">数式は文字列と数値を比較します。</span><span class="sxs-lookup"><span data-stu-id="d509f-133">The formula compares a text string to a number.</span></span> <span data-ttu-id="d509f-134">式は、DirectQuery モードでもインメモリ モデルでも **true** になります。</span><span class="sxs-lookup"><span data-stu-id="d509f-134">The expression is **true** in both DirectQuery mode and in-memory models.</span></span>  
  
<span data-ttu-id="d509f-135">インメモリ モデルでは、文字列としての数値が数値データ型に暗黙でキャストされて他の数値と比較されるため、結果は **true** です。</span><span class="sxs-lookup"><span data-stu-id="d509f-135">In an in-memory model, the result is **true** because numbers as strings are implicitly cast to a numerical data type for comparisons with other numbers.</span></span> <span data-ttu-id="d509f-136">SQL も、数値データ型との比較のために、テキストの数値を数値として暗黙的にキャストします。</span><span class="sxs-lookup"><span data-stu-id="d509f-136">SQL also implicitly casts text numbers as numbers for comparison to numerical data types.</span></span>  
  
<span data-ttu-id="d509f-137">これは、最初のバージョンのからの動作の変更を表します。これは、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] テキスト "2" は常に任意の数値より大きいと見なされるため、 **false**を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-137">Note that this represents a change in behavior from the first version of [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], which would return **false**, because the text "2" would always be considered larger than any number.</span></span>  
  
<span data-ttu-id="d509f-138">**テキストとブール値の比較**</span><span class="sxs-lookup"><span data-stu-id="d509f-138">**Comparison of text with Boolean**</span></span>  
<span data-ttu-id="d509f-139">例: `"VERDADERO" = TRUE`</span><span class="sxs-lookup"><span data-stu-id="d509f-139">EXAMPLE: `"VERDADERO" = TRUE`</span></span>  
  
<span data-ttu-id="d509f-140">この式は、テキスト文字列とブール値を比較します。</span><span class="sxs-lookup"><span data-stu-id="d509f-140">This expression compares a text string with a Boolean value.</span></span> <span data-ttu-id="d509f-141">一般に、DirectQuery またはインメモリ モデルの場合、文字列値とブール値の比較の結果はエラーになります。</span><span class="sxs-lookup"><span data-stu-id="d509f-141">In general, for DirectQuery or In-Memory models, comparing a string value to a Boolean value results in an error.</span></span> <span data-ttu-id="d509f-142">この規則に対する唯一の例外は、文字列に単語 **true** または **false**が含まれる場合です。この場合は、ブール型への変換が行われ、比較が実行されて論理的な結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-142">The only exceptions to the rule are when the string contains the word **true** or the word **false**; if the string contains any of true or false values, a conversion to Boolean is made and the comparison takes place giving the logical result.</span></span>  
  
<span data-ttu-id="d509f-143">**Null 値の比較**</span><span class="sxs-lookup"><span data-stu-id="d509f-143">**Comparison of nulls**</span></span>  
<span data-ttu-id="d509f-144">例: `EVALUATE ROW("X", BLANK() = BLANK())`</span><span class="sxs-lookup"><span data-stu-id="d509f-144">EXAMPLE: `EVALUATE ROW("X", BLANK() = BLANK())`</span></span>  
  
<span data-ttu-id="d509f-145">この数式は、SQL で NULL に相当する値と NULL を比較します。</span><span class="sxs-lookup"><span data-stu-id="d509f-145">This formula compares the SQL equivalent of a null to a null.</span></span> <span data-ttu-id="d509f-146">インメモリ モデルおよび DirectQuery モデルでは **true** が返されます。DirectQuery モデルでは、インメモリ モデルと同じ動作が保証されるように準備が行われます。</span><span class="sxs-lookup"><span data-stu-id="d509f-146">It returns **true** in in-memory and DirectQuery models; a provision is made in DirectQuery model to guarantee similar behavior to in-memory model.</span></span>  
  
<span data-ttu-id="d509f-147">Transact-SQL では NULL と NULL は等しくならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d509f-147">Note that in Transact-SQL, a null is never equal to a null.</span></span> <span data-ttu-id="d509f-148">ただし、DAX では空白は別の空白と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="d509f-148">However, in DAX, a blank is equal to another blank.</span></span> <span data-ttu-id="d509f-149">この動作はすべてのインメモリ モデルについて同じです。</span><span class="sxs-lookup"><span data-stu-id="d509f-149">This behavior is the same for all in-memory models.</span></span> <span data-ttu-id="d509f-150">ほとんどの場合、DirectQuery モードは SQL Server のセマンティックを使用します。しかし、この場合はそうではなく、新しい NULL 比較動作が行われます。</span><span class="sxs-lookup"><span data-stu-id="d509f-150">It is important to note that DirectQuery mode uses, most of, the semantics of SQL Server; but, in this case it separates from it giving a new behavior to NULL comparisons.</span></span>  
  
### <a name="casts"></a><a name="bkmk_Casts"></a><span data-ttu-id="d509f-151">キャスト</span><span class="sxs-lookup"><span data-stu-id="d509f-151">Casts</span></span>  
  
<span data-ttu-id="d509f-152">DAX のようなキャスト関数はありませんが、多くの比較演算および算術演算では暗黙のキャストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-152">There is no cast function as such in DAX, but implicit casts are performed in many comparison and arithmetic operations.</span></span> <span data-ttu-id="d509f-153">比較演算または数理演算により、結果のデータ型が決まります。</span><span class="sxs-lookup"><span data-stu-id="d509f-153">It is the comparison or arithmetic operation that determines the data type of the result.</span></span> <span data-ttu-id="d509f-154">たとえば、</span><span class="sxs-lookup"><span data-stu-id="d509f-154">For example,</span></span>  
  
-   <span data-ttu-id="d509f-155">ブール値は、算術演算では数値として扱われるか (TRUE + 1 など)、ブール値の列に関数 MIN が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-155">Boolean values are treated as numeric in arithmetic operations, such as TRUE + 1, or the function MIN applied to a column of Boolean values.</span></span> <span data-ttu-id="d509f-156">NOT 演算も数値を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-156">A NOT operation also returns a numeric value.</span></span>  
  
-   <span data-ttu-id="d509f-157">ブール値は、比較において、および EXACT、AND、OR、 &amp;&amp;、または || で使用されるときは、常に論理値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="d509f-157">Boolean values are always treated as logical values in comparisons and when used with EXACT, AND, OR, &amp;&amp;, or ||.</span></span>  
  
<span data-ttu-id="d509f-158">**文字列からブールへのキャスト**</span><span class="sxs-lookup"><span data-stu-id="d509f-158">**Cast from string to Boolean**</span></span>  
<span data-ttu-id="d509f-159">インメモリモデルと DirectQuery モデルでは、キャストは、 **""** (空の文字列)、 **"true"**、 **"false"** の各文字列からのブール値にのみ許可されます。空の文字列が false 値にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="d509f-159">In in-memory and DirectQuery models, casts are permitted to Boolean values from these strings only: **""** (empty string), **"true"**, **"false"**; where an empty string casts to false value.</span></span>  
  
<span data-ttu-id="d509f-160">他のすべての文字列からブール データ型へのキャストはエラーになります。</span><span class="sxs-lookup"><span data-stu-id="d509f-160">Casts to the Boolean data type of any other string results in an error.</span></span>  
  
<span data-ttu-id="d509f-161">**文字列から日付/時刻へのキャスト**</span><span class="sxs-lookup"><span data-stu-id="d509f-161">**Cast from string to date/time**</span></span>  
<span data-ttu-id="d509f-162">DirectQuery モードでは、文字列表現の日時から実際の **datetime** 値へのキャストは、SQL Server と同じように行われます。</span><span class="sxs-lookup"><span data-stu-id="d509f-162">In DirectQuery mode, casts from string representations of dates and times to actual **datetime** values behave the same way as they do in SQL Server.</span></span>  
  
<span data-ttu-id="d509f-163">モデル内の文字列から**datetime**データ型へのキャストを管理する規則の詳細については、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 「 [DAX 構文リファレンス](/dax/dax-syntax-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d509f-163">For information about the rules governing casts from string to **datetime** data types in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, see the [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="d509f-164">インメモリ データ ストアを使用するモデルで日付に対してサポートされるテキスト形式の範囲は、SQL Server でサポートされる日付の文字列形式より制限されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-164">Models that use the in-memory data store support a more limited range of text formats for dates than the string formats for dates that are supported by SQL Server.</span></span> <span data-ttu-id="d509f-165">ただし、DAX では日付と時刻のカスタム形式がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d509f-165">However, DAX supports custom date and time formats.</span></span>  
  
<span data-ttu-id="d509f-166">**文字列から他の非ブール値へのキャスト**</span><span class="sxs-lookup"><span data-stu-id="d509f-166">**Cast from string to other non Boolean values**</span></span>  
<span data-ttu-id="d509f-167">文字列から非ブール値へのキャストの場合、DirectQuery モードは SQL Server と同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="d509f-167">When casting from strings to non-Boolean values, DirectQuery mode behaves the same as SQL Server.</span></span> <span data-ttu-id="d509f-168">詳細については、「 [CAST および CONVERT &#40;Transact-SQL&#41;](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d509f-168">For more information, see [CAST and CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8).</span></span>  
  
<span data-ttu-id="d509f-169">**認められない数値から文字列へのキャスト**</span><span class="sxs-lookup"><span data-stu-id="d509f-169">**Cast from numbers to string not allowed**</span></span>  
<span data-ttu-id="d509f-170">例: `CONCATENATE(102,",345")`</span><span class="sxs-lookup"><span data-stu-id="d509f-170">EXAMPLE: `CONCATENATE(102,",345")`</span></span>  
  
<span data-ttu-id="d509f-171">数値から文字列へのキャストは SQL Server では認められません。</span><span class="sxs-lookup"><span data-stu-id="d509f-171">Casting from numbers to strings is not allowed in SQL Server.</span></span>  
  
<span data-ttu-id="d509f-172">この数式は表形式モデルおよび DirectQuery モードではエラーになりますが、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]では結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-172">This formula returns an error in tabular models and in DirectQuery mode; however, the formula produces a result in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)].</span></span>  
  
<span data-ttu-id="d509f-173">**DirectQuery での 2 試行キャストの非サポート**</span><span class="sxs-lookup"><span data-stu-id="d509f-173">**No support for two-try casts in DirectQuery**</span></span>  
<span data-ttu-id="d509f-174">インメモリ モデルでは、通常、第 1 のキャストが失敗すると、第 2 のキャストが試みられます。</span><span class="sxs-lookup"><span data-stu-id="d509f-174">In-memory models often attempt a second cast when the first one fails.</span></span> <span data-ttu-id="d509f-175">DirectQuery モードではこのようなことは行われません。</span><span class="sxs-lookup"><span data-stu-id="d509f-175">This never happens in DirectQuery mode.</span></span>  
  
<span data-ttu-id="d509f-176">例: `TODAY() + "13:14:15"`</span><span class="sxs-lookup"><span data-stu-id="d509f-176">EXAMPLE: `TODAY() + "13:14:15"`</span></span>  
  
<span data-ttu-id="d509f-177">この式では、第 1 のパラメーターは **datetime** 型で、第 2 のパラメーターは **string**型です。</span><span class="sxs-lookup"><span data-stu-id="d509f-177">In this expression, the first parameter has type **datetime** and second parameter has type **string**.</span></span> <span data-ttu-id="d509f-178">ただし、オペランドを結合するときのキャストの処理は異なります。</span><span class="sxs-lookup"><span data-stu-id="d509f-178">However, the casts when combining the operands are handled differently.</span></span> <span data-ttu-id="d509f-179">DAX は、 **string** から **double**への暗黙のキャストを実行します。</span><span class="sxs-lookup"><span data-stu-id="d509f-179">DAX will perform an implicit cast from **string** to **double**.</span></span> <span data-ttu-id="d509f-180">インメモリ モデルでは、数式エンジンは **double**への直接キャストを試み、それが失敗した場合は、文字列から **datetime**へのキャストを試みます。</span><span class="sxs-lookup"><span data-stu-id="d509f-180">In in-memory models, the formula engine attempts to cast directly to **double**, and if that fails, it will try to cast the string to **datetime**.</span></span>  
  
<span data-ttu-id="d509f-181">DirectQuery モードでは、 **string** から **double** への直接キャストだけが試みられます。</span><span class="sxs-lookup"><span data-stu-id="d509f-181">In DirectQuery mode, only the direct cast from **string** to **double** will be applied.</span></span> <span data-ttu-id="d509f-182">このキャストが失敗した場合、数式はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-182">If this cast fails, the formula will return an error.</span></span>  
  
### <a name="math-functions-and-arithmetic-operations"></a><a name="bkmk_Math"></a><span data-ttu-id="d509f-183">数学関数と算術演算</span><span class="sxs-lookup"><span data-stu-id="d509f-183">Math functions and arithmetic operations</span></span>  
<span data-ttu-id="d509f-184">基になっているデータ型または演算で適用できるキャストの違いにより、一部の数学関数は、DirectQuery モードでは異なる結果を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-184">Some mathematical functions will return different results in DirectQuery mode because of differences in the underlying data type or the casts that can be applied in operations.</span></span> <span data-ttu-id="d509f-185">また、前に説明した許可される値の範囲についての制限が、算術演算の結果に影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-185">Also, the restrictions described above on the allowed range of values might affect the outcome of arithmetic operations.</span></span>  
  
<span data-ttu-id="d509f-186">**加算の順序**</span><span class="sxs-lookup"><span data-stu-id="d509f-186">**Order of addition**</span></span>  
<span data-ttu-id="d509f-187">一連の数値を加算する数式を作成する場合、インメモリ モデルでは数値の処理順序が DirectQuery モデルと異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-187">When you create a formula that adds a series of numbers, an in-memory model might process the numbers in a different order than a DirectQuery model.</span></span>  <span data-ttu-id="d509f-188">したがって、非常に大きい正の値および非常に大きい負の値がある場合、演算によってはエラーになる場合と結果が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-188">Therefore, when you have many very large positive numbers and very large negative numbers, you may get an error in one operation and results in another operation.</span></span>  
  
<span data-ttu-id="d509f-189">**POWER 関数の使用**</span><span class="sxs-lookup"><span data-stu-id="d509f-189">**Use of the POWER function**</span></span>  
<span data-ttu-id="d509f-190">例: `POWER(-64, 1/3)`</span><span class="sxs-lookup"><span data-stu-id="d509f-190">EXAMPLE: `POWER(-64, 1/3)`</span></span>  
  
<span data-ttu-id="d509f-191">DirectQuery モードの POWER 関数では、分数の指数に対する基数として負の値を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d509f-191">In DirectQuery mode, the POWER function cannot use negative values as the base when raised to a fractional exponent.</span></span> <span data-ttu-id="d509f-192">これは SQL Server の想定される動作です。</span><span class="sxs-lookup"><span data-stu-id="d509f-192">This is the expected behavior in SQL Server.</span></span>  
  
<span data-ttu-id="d509f-193">インメモリ モデルでは、この数式からは -4 が返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-193">In an in-memory model, the formula returns -4.</span></span>  
  
<span data-ttu-id="d509f-194">**数値のオーバーフロー動作**</span><span class="sxs-lookup"><span data-stu-id="d509f-194">**Numerical overflow operations**</span></span>  
<span data-ttu-id="d509f-195">Transact-SQL では、数値オーバーフローになる演算ではオーバーフロー エラーが返されます。一方、DirectQuery モードでは、オーバーフローになる数式でもエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d509f-195">In Transact-SQL, operations that result in a numerical overflow return an overflow error; therefore, formulas that result in an overflow also raise an error in DirectQuery mode.</span></span>  
  
<span data-ttu-id="d509f-196">ただし、同じ数式をインメモリ モデルで使用すると、8 バイトの整数が返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-196">However, the same formula when used in an in-memory model returns an eight-byte integer.</span></span> <span data-ttu-id="d509f-197">これは、数式エンジンが数値オーバーフローのチェックを実行しないためです。</span><span class="sxs-lookup"><span data-stu-id="d509f-197">That is because the formula engine does not perform checks for numerical overflows.</span></span>  
  
<span data-ttu-id="d509f-198">**異なる結果を返すブランクの LOG 関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-198">**LOG functions with blanks return different results**</span></span>  
<span data-ttu-id="d509f-199">SQL Server では、NULL と空白の処理が xVelocity エンジンとは異なります。</span><span class="sxs-lookup"><span data-stu-id="d509f-199">SQL Server handles nulls and blanks differently than the xVelocity engine.</span></span> <span data-ttu-id="d509f-200">その結果、次の式は、DirectQuery モードではエラーを返しますが、インメモリモードでは無限大 (-inf) を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-200">As a result, the following formula returns an error in DirectQuery mode, but return infinity (-inf) in in-memory mode.</span></span>  
  
`EXAMPLE: LOG(blank())`  
  
<span data-ttu-id="d509f-201">同じ制限が、他の対数関数 LOG10 および LN にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-201">The same limitations apply to the other logarithmic functions: LOG10 and LN.</span></span>  
  
<span data-ttu-id="d509f-202">DAX での **blank** データ型の詳細については、「 [DAX 構文のリファレンス](/dax/dax-syntax-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d509f-202">For more information about the **blank** data type in DAX, see [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="d509f-203">**0 での除算とブランクでの除算**</span><span class="sxs-lookup"><span data-stu-id="d509f-203">**Division by 0 and division by Blank**</span></span>  
<span data-ttu-id="d509f-204">DirectQuery モードでは、ゼロ (0) による除算または BLANK による除算は常にエラーになります。</span><span class="sxs-lookup"><span data-stu-id="d509f-204">In DirectQuery mode, division by zero (0) or division by BLANK will always result in an error.</span></span> <span data-ttu-id="d509f-205">SQL Server は無限大の表記をサポートしていず、0 による除算の自然な結果は無限大なので、結果はエラーになります。</span><span class="sxs-lookup"><span data-stu-id="d509f-205">SQL Server does not support the notion of infinity, and because the natural result of any division by 0 is infinity, the result is an error.</span></span> <span data-ttu-id="d509f-206">ただし、SQL Server は NULL による除算はサポートしており、結果は常に NULL になります。</span><span class="sxs-lookup"><span data-stu-id="d509f-206">However, SQL Server supports division by nulls, and the result must always equal null.</span></span>  
  
<span data-ttu-id="d509f-207">DirectQuery モードでは、どちらの種類の演算 (ゼロによる除算と NULL による除算) でもエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-207">Rather than return different results for these operations, in DirectQuery mode, both types of operations (division by zero and division by null) return an error.</span></span>  
  
<span data-ttu-id="d509f-208">Excel モデルおよび [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] モデルでも、ゼロによる除算ではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-208">Note that, in Excel and in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, division by zero also returns an error.</span></span> <span data-ttu-id="d509f-209">ブランクによる除算ではブランクが返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-209">Division by a blank returns a blank.</span></span>  
  
<span data-ttu-id="d509f-210">次の式はすべて、インメモリ モデルでは有効ですが、DirectQuery モードでは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d509f-210">The following expressions are all valid in in-memory models, but will fail in DirectQuery mode:</span></span>  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
<span data-ttu-id="d509f-211">式 `BLANK/BLANK` は特殊なケースであり、インメモリ モデルでも DirectQuery モードでも `BLANK` が返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-211">The expression `BLANK/BLANK` is a special case that returns `BLANK` in both for in-memory models, and in DirectQuery mode.</span></span>  
  
### <a name="supported-numeric-and-date-time-ranges"></a><a name="bkmk_Ranges"></a><span data-ttu-id="d509f-212">サポートされる数値および日付と時刻の範囲</span><span class="sxs-lookup"><span data-stu-id="d509f-212">Supported numeric and date-time ranges</span></span>  
<span data-ttu-id="d509f-213">[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]メモリ内のおよびテーブルモデルの数式には、実数と日付に許容される最大値に関して、Excel と同じ制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-213">Formulas in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and tabular models in-memory are subject to the same limitations as Excel with regard to maximum allowed values for real numbers and dates.</span></span> <span data-ttu-id="d509f-214">ただし、最大値が計算またはクエリから返される場合、または値の変換、キャスト、丸め、または切り捨てが行われる場合は、相違が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d509f-214">However, differences can arise when the maximum value is returned from a calculation or query, or when values are converted, cast, rounded, or truncated.</span></span>  
  
-   <span data-ttu-id="d509f-215">**Currency** 型と **Real** 型の値の乗算を行い、結果が最大許容値より大きい場合、DirectQuery モードではエラーは発生せず、NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-215">If values of types **Currency** and **Real** are multiplied, and the result is larger than the maximum possible value, in DirectQuery mode, no error is raised, and a null is returned.</span></span>  
  
-   <span data-ttu-id="d509f-216">インメモリ モデルでは、エラーは発生しませんが、最大値が返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-216">In in-memory models, no error is raised, but the maximum value is returned.</span></span>  
  
<span data-ttu-id="d509f-217">一般に、Excel と SQL Server では許容される日付の範囲が異なるため、結果が一致することが保証されるのは、共通の日付範囲内の日付の場合だけです。これには、次の日付が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d509f-217">In general, because the accepted date ranges are different for Excel and SQL Server, results can be guaranteed to match only when dates are within the common date range, which is inclusive of the following dates:</span></span>  
  
-   <span data-ttu-id="d509f-218">最も早い日付: 1990 年 3 月 1 日</span><span class="sxs-lookup"><span data-stu-id="d509f-218">Earliest date: March 1, 1990</span></span>  
  
-   <span data-ttu-id="d509f-219">最も遅い日付: 9999 年 12 月 31 日</span><span class="sxs-lookup"><span data-stu-id="d509f-219">Latest date: December 31, 9999</span></span>  
  
<span data-ttu-id="d509f-220">数式で使用されるいずれかの日付がこの範囲内にない場合は、数式がエラーになるか、または結果が一致しません。</span><span class="sxs-lookup"><span data-stu-id="d509f-220">If any dates used in formulas fall outside this range, either the formula will result in an error, or the results will not match.</span></span>  
  
<span data-ttu-id="d509f-221">**CEILING でサポートされる浮動小数点値**</span><span class="sxs-lookup"><span data-stu-id="d509f-221">**Floating point values supported by CEILING**</span></span>  
<span data-ttu-id="d509f-222">例: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span><span class="sxs-lookup"><span data-stu-id="d509f-222">EXAMPLE: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span></span>  
  
<span data-ttu-id="d509f-223">DAX の CEILING 関数に相当する Transact-SQL の関数は、大きさが 10^19 以下の値のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d509f-223">The Transact-SQL equivalent of the DAX CEILING function only supports values with magnitude of 10^19 or less.</span></span> <span data-ttu-id="d509f-224">原則として、浮動小数点値は **bigint**に格納できます。</span><span class="sxs-lookup"><span data-stu-id="d509f-224">A rule of thumb is that floating point values should be able to fit into **bigint**.</span></span>  
  
<span data-ttu-id="d509f-225">**範囲外の日付での Datepart 関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-225">**Datepart functions with dates that are out of range**</span></span>  
<span data-ttu-id="d509f-226">DirectQuery モードでの結果とインメモリ モデルでの結果が一致することが保証されるのは、引数として使用される日付が有効な日付範囲内である場合だけです。</span><span class="sxs-lookup"><span data-stu-id="d509f-226">Results in DirectQuery mode are guaranteed to match those in in-memory models only when the date used as the argument is in the valid date range.</span></span> <span data-ttu-id="d509f-227">この条件が満たされない場合は、エラーが発生するか、または DirectQuery とインメモリ モードで数式から返される結果が異なります。</span><span class="sxs-lookup"><span data-stu-id="d509f-227">If these conditions are not satisfied, either an error will be raised, or the formula will return different results in DirectQuery than in in-memory mode.</span></span>  
  
<span data-ttu-id="d509f-228">例: `MONTH(0)` または `YEAR(0)`</span><span class="sxs-lookup"><span data-stu-id="d509f-228">EXAMPLE: `MONTH(0)` or `YEAR(0)`</span></span>  
  
<span data-ttu-id="d509f-229">DirectQuery モードでは、式から返される値はそれぞれ 12 および 1899 です。</span><span class="sxs-lookup"><span data-stu-id="d509f-229">In DirectQuery mode, the expressions return 12 and 1899, respectively.</span></span>  
  
<span data-ttu-id="d509f-230">インメモリ モデルでは、それぞれ 1 および 1900 が返されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-230">In in-memory models, the expressions return 1 and 1900, respectively.</span></span>  
  
<span data-ttu-id="d509f-231">例:  `EOMONTH(0.0001, 1)`</span><span class="sxs-lookup"><span data-stu-id="d509f-231">EXAMPLE:  `EOMONTH(0.0001, 1)`</span></span>  
  
<span data-ttu-id="d509f-232">この式の結果は、パラメーターとして渡されるデータが有効な日付範囲内の場合にのみ一致します。</span><span class="sxs-lookup"><span data-stu-id="d509f-232">The results of this expression will match only when the data supplied as a parameter is within the valid date range.</span></span>  
  
<span data-ttu-id="d509f-233">例: `EOMONTH(blank(), blank())` または `EDATE(blank(), blank())`</span><span class="sxs-lookup"><span data-stu-id="d509f-233">EXAMPLE: `EOMONTH(blank(), blank())` or `EDATE(blank(), blank())`</span></span>  
  
<span data-ttu-id="d509f-234">この式の結果は、DirectQuery モードでもインメモリ モードでも同じになります。</span><span class="sxs-lookup"><span data-stu-id="d509f-234">The results of this expression should be the same in DirectQuery mode and in-memory mode.</span></span>  
  
<span data-ttu-id="d509f-235">**時刻値の切り捨て**</span><span class="sxs-lookup"><span data-stu-id="d509f-235">**Truncation of time values**</span></span>  
<span data-ttu-id="d509f-236">例: `SECOND(1231.04097222222)`</span><span class="sxs-lookup"><span data-stu-id="d509f-236">EXAMPLE: `SECOND(1231.04097222222)`</span></span>  
  
<span data-ttu-id="d509f-237">DirectQuery モードでは、結果は SQL Server の規則に従って切り捨てられ、式は 59 と評価されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-237">In DirectQuery mode, the result is truncated, following the rules of SQL Server, and the expression evaluates to 59.</span></span>  
  
<span data-ttu-id="d509f-238">インメモリ モデルでは、途中の各演算で結果が丸められるため、式は 0 と評価されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-238">In in-memory models, the results of each interim operation are rounded; therefore, the expression evaluates to 0.</span></span>  
  
<span data-ttu-id="d509f-239">この値の計算方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d509f-239">The following example demonstrates how this value is calculated:</span></span>  
  
1.  <span data-ttu-id="d509f-240">入力の小数部 (0.04097222222) に 24 が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-240">The fraction of the input (0.04097222222) is multiplied by 24.</span></span>  
  
2.  <span data-ttu-id="d509f-241">結果の時間の値 (0.98333333328) に 60 が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-241">The resulting hour value (0.98333333328) is multiplied by 60.</span></span>  
  
3.  <span data-ttu-id="d509f-242">結果の分の値は 58.9999999968 です。</span><span class="sxs-lookup"><span data-stu-id="d509f-242">The resulting minute value is 58.9999999968.</span></span>  
  
4.  <span data-ttu-id="d509f-243">分の値の小数部 (0.9999999968) に 60 が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-243">The fraction of the minute value (0.9999999968) is multiplied by 60.</span></span>  
  
5.  <span data-ttu-id="d509f-244">結果の 2 番目の値 (59.999999808) が 60 に丸められます。</span><span class="sxs-lookup"><span data-stu-id="d509f-244">The resulting second value (59.999999808) rounds up to 60.</span></span>  
  
6.  <span data-ttu-id="d509f-245">60 は 0 と等価です。</span><span class="sxs-lookup"><span data-stu-id="d509f-245">60 is equivalent to 0.</span></span>  
  
<span data-ttu-id="d509f-246">**SQL の時間データ型はサポートされない**</span><span class="sxs-lookup"><span data-stu-id="d509f-246">**SQL Time data type not supported**</span></span>  
<span data-ttu-id="d509f-247">インメモリ モデルでは、SQL の新しい **Time** データ型の使用はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d509f-247">In-memory models do not support use of the new SQL **Time** data type.</span></span> <span data-ttu-id="d509f-248">DirectQuery モードでは、このデータ型の列を参照する数式はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-248">In DirectQuery mode, formulas that reference columns with this data type will return an error.</span></span> <span data-ttu-id="d509f-249">時刻データ列をインメモリ モデルにインポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d509f-249">Time data columns cannot be imported into an in-memory model.</span></span>  
  
<span data-ttu-id="d509f-250">ただし、およびでは、キャッシュされた [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] モデルでは、エンジンが時刻値を許容されるデータ型にキャストし、数式から結果が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d509f-250">However, in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and in cached models, sometimes the engine casts the time value to an acceptable data type, and the formula returns a result.</span></span>  
  
<span data-ttu-id="d509f-251">この動作は、日付列をパラメーターとして使用するすべての関数に影響します。</span><span class="sxs-lookup"><span data-stu-id="d509f-251">This behavior affects all functions that use a date column as a parameter.</span></span>  
  
### <a name="currency"></a><a name="bkmk_Currency"></a><span data-ttu-id="d509f-252">貨</span><span class="sxs-lookup"><span data-stu-id="d509f-252">Currency</span></span>  
<span data-ttu-id="d509f-253">DirectQuery モードでは、算術演算の結果が **Currency**型の場合、値は次の範囲内である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-253">In DirectQuery mode, if the result of an arithmetic operation has the type **Currency**, the value must be within the following range:</span></span>  
  
-   <span data-ttu-id="d509f-254">最小: -922337203685477.5808</span><span class="sxs-lookup"><span data-stu-id="d509f-254">Minimum: -922337203685477.5808</span></span>  
  
-   <span data-ttu-id="d509f-255">最大: 922337203685477.5807</span><span class="sxs-lookup"><span data-stu-id="d509f-255">Maximum: 922337203685477.5807</span></span>  
  
<span data-ttu-id="d509f-256">**通貨データ型と REAL データ型の組み合わせ**</span><span class="sxs-lookup"><span data-stu-id="d509f-256">**Combining currency and REAL data types**</span></span>  
<span data-ttu-id="d509f-257">例: `Currency sample 1`</span><span class="sxs-lookup"><span data-stu-id="d509f-257">EXAMPLE: `Currency sample 1`</span></span>  
  
<span data-ttu-id="d509f-258">**Currency** 型と **Real** 型を乗算して結果が 9223372036854774784 (0x7ffffffffffffc00) より大きい場合、DirectQuery モードではエラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="d509f-258">If **Currency** and **Real** types are multiplied, and the result is larger than 9223372036854774784 (0x7ffffffffffffc00), DirectQuery mode will not raise an error.</span></span>  
  
<span data-ttu-id="d509f-259">インメモリ モデルでは、結果の絶対値が 922337203685477.4784 より大きい場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d509f-259">In an in-memory model, an error is raised if the absolute value of the result is larger than 922337203685477.4784.</span></span>  
  
<span data-ttu-id="d509f-260">**演算の結果が範囲外の値**</span><span class="sxs-lookup"><span data-stu-id="d509f-260">**Operation results in an out-of-range value**</span></span>  
<span data-ttu-id="d509f-261">例: `Currency sample 2`</span><span class="sxs-lookup"><span data-stu-id="d509f-261">EXAMPLE: `Currency sample 2`</span></span>  
  
<span data-ttu-id="d509f-262">2 つの通貨値の演算の結果が指定されている範囲外の値になる場合、インメモリ モデルではエラーが発生しますが、DirectQuery モデルでは発生しません。</span><span class="sxs-lookup"><span data-stu-id="d509f-262">If operations on any two currency values result in a value that is outside the specified range, an error is raised in in-memory models, but not in DirectQuery models.</span></span>  
  
<span data-ttu-id="d509f-263">**通貨データ型と他のデータ型の組み合わせ**</span><span class="sxs-lookup"><span data-stu-id="d509f-263">**Combining currency with other data types**</span></span>  
<span data-ttu-id="d509f-264">通貨値を他の数値型の値で除算した場合、結果が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-264">Division of currency values by values of other numeric types can result in different results.</span></span>  
  
### <a name="aggregation-functions"></a><a name="bkmk_Aggregations"></a><span data-ttu-id="d509f-265">集計関数</span><span class="sxs-lookup"><span data-stu-id="d509f-265">Aggregation functions</span></span>  
<span data-ttu-id="d509f-266">1 行のテーブルに対する統計関数は異なる結果を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-266">Statistical functions on a table with one row return different results.</span></span> <span data-ttu-id="d509f-267">空のテーブルに対する集計関数も、インメモリ モデルと DirectQuery モードでは動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="d509f-267">Aggregation functions over empty tables also behave differently in in-memory models than they do in DirectQuery mode.</span></span>  
  
<span data-ttu-id="d509f-268">**1 行のテーブルに対する統計関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-268">**Statistical functions over a table with a single row**</span></span>  
<span data-ttu-id="d509f-269">引数として使用されるテーブルに 1 行しか含まれない場合、DirectQuery モードでは STDEV や VAR などの統計関数は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-269">If the table that is used as argument contains a single row, in DirectQuery mode, statistical functions such as STDEV and VAR return null.</span></span>  
  
<span data-ttu-id="d509f-270">インメモリ モデルでは、1 行だけのテーブルに対して STDEV または VAR を使用する数式はゼロ除算エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-270">In an in-memory model, a formula that uses STDEV or VAR over a table with a single row returns a division by zero error.</span></span>  
  
### <a name="text-functions"></a><a name="bkmk_Text"></a><span data-ttu-id="d509f-271">文字列関数</span><span class="sxs-lookup"><span data-stu-id="d509f-271">Text functions</span></span>  
<span data-ttu-id="d509f-272">リレーショナル データ ストアでは Excel とは異なるテキスト データ型が提供されるので、文字列の検索やサブストリングの処理での結果が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-272">Because relational data stores provide different text data types than does Excel, you may see different results when searching strings or working with substrings.</span></span> <span data-ttu-id="d509f-273">文字列の長さも異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-273">The length of strings also can be different.</span></span>  
  
<span data-ttu-id="d509f-274">一般に、固定サイズの列を引数として使用する文字列操作関数は結果が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-274">In general, any string manipulation functions that use fixed-size columns as arguments can have different results.</span></span>  
  
<span data-ttu-id="d509f-275">また、SQL Server の一部のテキスト関数は、Excel では提供されていない追加引数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d509f-275">Additionally, in SQL Server, some text functions support additional arguments that are not provided in Excel.</span></span> <span data-ttu-id="d509f-276">足りない引数が数式で必要な場合、インメモリ モデルでは異なる結果またはエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-276">If the formula requires the missing argument you can get different results or errors in the in-memory model.</span></span>  
  
<span data-ttu-id="d509f-277">**LEFT や RIGHT などを使用する文字を返す演算では正しい文字が返されますが、大文字と小文字の使用が異なったり、または結果を返さない場合があります。**</span><span class="sxs-lookup"><span data-stu-id="d509f-277">**Operations that return a character using LEFT, RIGHT, etc. may return the correct character but in a different case, or no results**</span></span>  
<span data-ttu-id="d509f-278">例: `LEFT(["text"], 2)`</span><span class="sxs-lookup"><span data-stu-id="d509f-278">EXAMPLE: `LEFT(["text"], 2)`</span></span>  
  
<span data-ttu-id="d509f-279">DirectQuery モードでは、返される文字の大文字と小文字の使い分けは、データベースに格納されている文字と常にまったく同じです。</span><span class="sxs-lookup"><span data-stu-id="d509f-279">In DirectQuery mode, the case of the character that is returned is always exactly the same as the letter that is stored in the database.</span></span> <span data-ttu-id="d509f-280">ただし、xVelocity エンジンでは、パフォーマンスの向上のため、値の圧縮およびインデックス作成に使用されるアルゴリズムが異なります。</span><span class="sxs-lookup"><span data-stu-id="d509f-280">However, the xVelocity engine uses a different algorithm for compression and indexing of values, to improve performance.</span></span>  
  
<span data-ttu-id="d509f-281">既定で使用される Latin1_General 照合順序では、大文字と小文字は区別されませんが、アクセントは区別されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-281">By default, the Latin1_General collation is used, which is case-insensitive but accent-sensitive.</span></span> <span data-ttu-id="d509f-282">したがって、小文字だけ、大文字だけ、または小文字と大文字の混合を使用する、同じテキスト文字列の複数のインスタンスが存在する場合、すべてのインスタンスが同じ文字列と見なされて、文字列の最初のインスタンスだけがインデックスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-282">Therefore, if there are multiple instances of a text string in lower case, upper case, or mixed case, all instances are considered the same string, and only the first instance of the string is stored in the index.</span></span> <span data-ttu-id="d509f-283">格納された文字列を使用するすべてのテキスト関数は、インデックス形式の指定された部分を取得します。</span><span class="sxs-lookup"><span data-stu-id="d509f-283">All text functions that operate on stored strings will retrieve the specified portion of the indexed form.</span></span> <span data-ttu-id="d509f-284">したがって、例の数式では、最初のインスタンスを入力として使用し、列全体に対して同じ値を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-284">Therefore, the example formula would return the same value for the entire column, using the first instance as the input.</span></span>  
  
[<span data-ttu-id="d509f-285">テーブル モデルの文字列ストレージと照合順序</span><span class="sxs-lookup"><span data-stu-id="d509f-285">String Storage and Collation in Tabular Models</span></span>](https://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
<span data-ttu-id="d509f-286">この動作は、RIGHT、MID などの他のテキスト関数にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-286">This behavior also applies to other text functions, including RIGHT, MID, and so forth.</span></span>  
  
<span data-ttu-id="d509f-287">**結果に影響を与える文字列の長さ**</span><span class="sxs-lookup"><span data-stu-id="d509f-287">**String length affects results**</span></span>  
<span data-ttu-id="d509f-288">例: `SEARCH("within string", "sample target  text", 1, 1)`</span><span class="sxs-lookup"><span data-stu-id="d509f-288">EXAMPLE: `SEARCH("within string", "sample target  text", 1, 1)`</span></span>  
  
<span data-ttu-id="d509f-289">SEARCH 関数を使用して文字列を検索し、ターゲットの文字列が内部の文字列より長い場合、DirectQuery モードではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d509f-289">If you search for a string using the SEARCH function, and the target string is longer than the within string, DirectQuery mode raises an error.</span></span>  
  
<span data-ttu-id="d509f-290">インメモリ モデルでは、検索された文字列が返されますが、長さは &lt;内部のテキスト&gt;の長さに切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="d509f-290">In an in-memory model, the searched string is returned, but with its length truncated to the length of &lt;within text&gt;.</span></span>  
  
<span data-ttu-id="d509f-291">例: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span><span class="sxs-lookup"><span data-stu-id="d509f-291">EXAMPLE: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span></span>  
  
<span data-ttu-id="d509f-292">置換文字列の長さが元の文字列の長さより長い場合、DirectQuery モードでは数式は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-292">If the length of the replacement string is greater than the length of the original string, in DirectQuery mode, the formula returns null.</span></span>  
  
<span data-ttu-id="d509f-293">インメモリ モデルでは数式は Excel の動作に従い、元の文字列と置換文字列を結合して、CACalifornia を返します。</span><span class="sxs-lookup"><span data-stu-id="d509f-293">In in-memory models, the formula follows the behavior of Excel, which concatenates the source string and the replacement string, which returns CACalifornia.</span></span>  
  
<span data-ttu-id="d509f-294">**文字列の途中での暗黙の TRIM**</span><span class="sxs-lookup"><span data-stu-id="d509f-294">**Implicit TRIM in the middle of strings**</span></span>  
<span data-ttu-id="d509f-295">例: `TRIM(" A sample sentence with leading white space")`</span><span class="sxs-lookup"><span data-stu-id="d509f-295">EXAMPLE: `TRIM(" A sample sentence with leading white space")`</span></span>  
  
<span data-ttu-id="d509f-296">DirectQuery モードでは、DAX の TRIM 関数は SQL ステートメント `LTRIM(RTRIM(<column>))`に変換されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-296">DirectQuery mode translates the DAX TRIM function to the SQL statement `LTRIM(RTRIM(<column>))`.</span></span> <span data-ttu-id="d509f-297">この結果、先頭と末尾の空白文字だけが削除されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-297">As a result, only leading and trailing white space is removed.</span></span>  
  
<span data-ttu-id="d509f-298">一方、インメモリ モデルでは、Excel の動作に従って、同じ数式により文字列内の空白文字が削除されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-298">In contrast, the same formula in an in-memory model removes spaces within the string, following the behavior of Excel.</span></span>  
  
<span data-ttu-id="d509f-299">**LEN 関数を使用するときの暗黙的な RTRIM**</span><span class="sxs-lookup"><span data-stu-id="d509f-299">**Implicit RTRIM with use of LEN function**</span></span>  
<span data-ttu-id="d509f-300">例: `LEN('string_column')`</span><span class="sxs-lookup"><span data-stu-id="d509f-300">EXAMPLE: `LEN('string_column')`</span></span>  
  
<span data-ttu-id="d509f-301">SQL Server と同様に、DirectQuery モードでは、文字列の列の最後から空白文字が自動的に削除されます。つまり、暗黙的に RTRIM が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-301">Like SQL Server, DirectQuery mode automatically removes white space from the end of string columns: that is, it performs an implicit RTRIM.</span></span> <span data-ttu-id="d509f-302">したがって、LEN 関数を使用する数式は、文字列の末尾に空白文字がある場合に異なる値を返すことがあります。</span><span class="sxs-lookup"><span data-stu-id="d509f-302">Therefore, formulas that use the LEN function can return different values if the string has trailing spaces.</span></span>  
  
<span data-ttu-id="d509f-303">**インメモリでサポートされる SUBSTITUTE の追加パラメーター**</span><span class="sxs-lookup"><span data-stu-id="d509f-303">**In-memory supports additional parameters for SUBSTITUTE**</span></span>  
<span data-ttu-id="d509f-304">例: `SUBSTITUTE([Title],"Doctor","Dr.")`</span><span class="sxs-lookup"><span data-stu-id="d509f-304">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.")`</span></span>  
  
<span data-ttu-id="d509f-305">例: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span><span class="sxs-lookup"><span data-stu-id="d509f-305">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span></span>  
  
<span data-ttu-id="d509f-306">DirectQuery モードでは、この関数のパラメーターが 3 つ (列の参照、古いテキスト、新しいテキスト) あるバージョンだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d509f-306">In DirectQuery mode, you can use only the version of this function that has three (3) parameters: a reference to a column, the old text, and the new text.</span></span> <span data-ttu-id="d509f-307">2 番目の数式を使用するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d509f-307">If you use the second formula, an error is raised.</span></span>  
  
<span data-ttu-id="d509f-308">インメモリ モデルでは、省略可能な 4 番目のパラメーターを使用して、置換する文字列のインスタンス番号を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d509f-308">In in-memory models, you can use an optional fourth parameter to specify the instance number of the string to replace.</span></span> <span data-ttu-id="d509f-309">たとえば、2 番目のインスタンスだけを置換できます。</span><span class="sxs-lookup"><span data-stu-id="d509f-309">For example, you can replace only the second instance, etc.</span></span>  
  
<span data-ttu-id="d509f-310">**REPT 操作の文字列長の制限**</span><span class="sxs-lookup"><span data-stu-id="d509f-310">**Restrictions on string lengths for REPT operations**</span></span>  
<span data-ttu-id="d509f-311">インメモリ モデルでは、REPT を使用する操作の結果として生成される文字列の長さは、32,767 文字未満でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="d509f-311">In in-memory models, the length of a string resulting from an operation using REPT must be less than 32,767 characters.</span></span>  
  
<span data-ttu-id="d509f-312">この制限は、DirectQuery モードでは適用されません。</span><span class="sxs-lookup"><span data-stu-id="d509f-312">This limitation does not apply in DirectQuery mode.</span></span>  
  
<span data-ttu-id="d509f-313">**文字の型によって異なる結果を返すサブストリング操作**</span><span class="sxs-lookup"><span data-stu-id="d509f-313">**Substring operations return different results depending on character type**</span></span>  
<span data-ttu-id="d509f-314">例: `MID([col], 2, 5)`</span><span class="sxs-lookup"><span data-stu-id="d509f-314">EXAMPLE: `MID([col], 2, 5)`</span></span>  
  
<span data-ttu-id="d509f-315">入力テキストが **varchar** または **nvarchar**の場合、数式の結果は常に同じになります。</span><span class="sxs-lookup"><span data-stu-id="d509f-315">If the input text is **varchar** or **nvarchar**, the result of the formula is always the same.</span></span>  
  
<span data-ttu-id="d509f-316">ただし、テキストが固定長文字で、 \* &lt; num_chars &gt; \*の値がターゲット文字列の長さよりも大きい場合、DirectQuery モードでは、結果の文字列の末尾に空白が追加されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-316">However, if the text is a fixed-length character and the value for *&lt;num_chars&gt;* is greater than the length of the target string, in DirectQuery mode, a blank is added at the end of the result string.</span></span>  
  
<span data-ttu-id="d509f-317">インメモリ モデルでは、結果は文字列の最後の文字で終了し、ブランクの埋め込みは行われません。</span><span class="sxs-lookup"><span data-stu-id="d509f-317">In an in-memory model, the result terminates at the last string character, with no padding.</span></span>  
  
## <a name="functions-supported-in-directquery-mode"></a><a name="bkmk_SupportedFunc"></a><span data-ttu-id="d509f-318">DirectQuery モードでサポートされている関数</span><span class="sxs-lookup"><span data-stu-id="d509f-318">Functions supported in DirectQuery mode</span></span>  
<span data-ttu-id="d509f-319">DirectQuery モードでは次の DAX 関数を使用できますが、前のセクションで説明した制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d509f-319">The following DAX functions can be used in DirectQuery mode, but with the qualifications as described in the preceding section.</span></span>  
  
<span data-ttu-id="d509f-320">**テキスト関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-320">**Text functions**</span></span>  
  
<span data-ttu-id="d509f-321">CONCATENATE</span><span class="sxs-lookup"><span data-stu-id="d509f-321">CONCATENATE</span></span>  
  
<span data-ttu-id="d509f-322">[FIND]</span><span class="sxs-lookup"><span data-stu-id="d509f-322">FIND</span></span>  
  
<span data-ttu-id="d509f-323">LEFT</span><span class="sxs-lookup"><span data-stu-id="d509f-323">LEFT</span></span>  
  
<span data-ttu-id="d509f-324">LEN</span><span class="sxs-lookup"><span data-stu-id="d509f-324">LEN</span></span>  
  
<span data-ttu-id="d509f-325">MID</span><span class="sxs-lookup"><span data-stu-id="d509f-325">MID</span></span>  
  
<span data-ttu-id="d509f-326">REPLACE</span><span class="sxs-lookup"><span data-stu-id="d509f-326">REPLACE</span></span>  
  
<span data-ttu-id="d509f-327">REPT</span><span class="sxs-lookup"><span data-stu-id="d509f-327">REPT</span></span>  
  
<span data-ttu-id="d509f-328">RIGHT</span><span class="sxs-lookup"><span data-stu-id="d509f-328">RIGHT</span></span>  
  
<span data-ttu-id="d509f-329">SUBSTITUTE</span><span class="sxs-lookup"><span data-stu-id="d509f-329">SUBSTITUTE</span></span>  
  
<span data-ttu-id="d509f-330">TRIM</span><span class="sxs-lookup"><span data-stu-id="d509f-330">TRIM</span></span>  
  
<span data-ttu-id="d509f-331">**統計関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-331">**Statistical functions**</span></span>  
  
<span data-ttu-id="d509f-332">COUNT</span><span class="sxs-lookup"><span data-stu-id="d509f-332">COUNT</span></span>  
  
<span data-ttu-id="d509f-333">STDEV.P</span><span class="sxs-lookup"><span data-stu-id="d509f-333">STDEV.P</span></span>  
  
<span data-ttu-id="d509f-334">STDEV.S</span><span class="sxs-lookup"><span data-stu-id="d509f-334">STDEV.S</span></span>  
  
<span data-ttu-id="d509f-335">STDEVX.P</span><span class="sxs-lookup"><span data-stu-id="d509f-335">STDEVX.P</span></span>  
  
<span data-ttu-id="d509f-336">STDEVX.S</span><span class="sxs-lookup"><span data-stu-id="d509f-336">STDEVX.S</span></span>  
  
<span data-ttu-id="d509f-337">VAR.P</span><span class="sxs-lookup"><span data-stu-id="d509f-337">VAR.P</span></span>  
  
<span data-ttu-id="d509f-338">VAR.S</span><span class="sxs-lookup"><span data-stu-id="d509f-338">VAR.S</span></span>  
  
<span data-ttu-id="d509f-339">VARX.P</span><span class="sxs-lookup"><span data-stu-id="d509f-339">VARX.P</span></span>  
  
<span data-ttu-id="d509f-340">VARX.S</span><span class="sxs-lookup"><span data-stu-id="d509f-340">VARX.S</span></span>  
  
<span data-ttu-id="d509f-341">**日付/時刻関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-341">**Date/time functions**</span></span>  
  
<span data-ttu-id="d509f-342">DATE</span><span class="sxs-lookup"><span data-stu-id="d509f-342">DATE</span></span>  
  
<span data-ttu-id="d509f-343">EDATE</span><span class="sxs-lookup"><span data-stu-id="d509f-343">EDATE</span></span>  
  
<span data-ttu-id="d509f-344">EOMONTH</span><span class="sxs-lookup"><span data-stu-id="d509f-344">EOMONTH</span></span>  
  
<span data-ttu-id="d509f-345">DATE</span><span class="sxs-lookup"><span data-stu-id="d509f-345">DATE</span></span>  
  
<span data-ttu-id="d509f-346">TIME</span><span class="sxs-lookup"><span data-stu-id="d509f-346">TIME</span></span>  
  
<span data-ttu-id="d509f-347">SECOND</span><span class="sxs-lookup"><span data-stu-id="d509f-347">SECOND</span></span>  
  
<span data-ttu-id="d509f-348">**数学関数と算術関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-348">**Math and number functions**</span></span>  
  
<span data-ttu-id="d509f-349">CEILING</span><span class="sxs-lookup"><span data-stu-id="d509f-349">CEILING</span></span>  
  
<span data-ttu-id="d509f-350">LN</span><span class="sxs-lookup"><span data-stu-id="d509f-350">LN</span></span>  
  
<span data-ttu-id="d509f-351">LOG</span><span class="sxs-lookup"><span data-stu-id="d509f-351">LOG</span></span>  
  
<span data-ttu-id="d509f-352">LOG10</span><span class="sxs-lookup"><span data-stu-id="d509f-352">LOG10</span></span>  
  
<span data-ttu-id="d509f-353">POWER</span><span class="sxs-lookup"><span data-stu-id="d509f-353">POWER</span></span>  
  
<span data-ttu-id="d509f-354">**DAX テーブルクエリ**</span><span class="sxs-lookup"><span data-stu-id="d509f-354">**DAX Table queries**</span></span>  
  
<span data-ttu-id="d509f-355">DAX テーブル クエリを使用して DirectQuery モデルに対する数式を評価するときは、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="d509f-355">There are some limitations when you evaluate formulas against a DirectQuery model by using DAX Table queries.</span></span> <span data-ttu-id="d509f-356">DirectQuery では、ORDER BY 句で同じ列を 2 回参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="d509f-356">DirectQuery does not support referring to the same column twice in an ORDER BY clause.</span></span> <span data-ttu-id="d509f-357">同等の Transact-SQL ステートメントを作成できず、クエリは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d509f-357">The equivalent Transact-SQL statement cannot be created and the query fails.</span></span>  
  
<span data-ttu-id="d509f-358">インメモリ モデルでは、ORDER BY 句を繰り返しても結果に影響はありません。</span><span class="sxs-lookup"><span data-stu-id="d509f-358">In an in-memory model, repeating the ORDER by clause has no effect on the results.</span></span>  
  
## <a name="functions-not-supported-in-directquery-mode"></a><a name="bkmk_NotSupportedFunc"></a><span data-ttu-id="d509f-359">DirectQuery モードでサポートされていない関数</span><span class="sxs-lookup"><span data-stu-id="d509f-359">Functions not supported in DirectQuery Mode</span></span>  
<span data-ttu-id="d509f-360">一部の DAX 関数は、DirectQuery モードで配置されたモデルではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d509f-360">Some DAX functions are not supported in models that are deployed in DirectQuery mode.</span></span> <span data-ttu-id="d509f-361">特定の関数がサポートされない理由は、次のいずれか、または組み合わせによります。</span><span class="sxs-lookup"><span data-stu-id="d509f-361">The reasons that a particular function is not supported can include any or a combination of these reasons:</span></span>  
  
-   <span data-ttu-id="d509f-362">基になるリレーショナル エンジンが、xVelocity エンジンによって実行されるものと同等の計算を実行できない。</span><span class="sxs-lookup"><span data-stu-id="d509f-362">The underlying relational engine cannot perform calculations equivalent to those performed by the xVelocity engine.</span></span>  
  
-   <span data-ttu-id="d509f-363">数式を同等の SQL 式に変換できない。</span><span class="sxs-lookup"><span data-stu-id="d509f-363">The formula cannot be converted to en equivalent SQL expression.</span></span>  
  
-   <span data-ttu-id="d509f-364">変換された式およびその結果の計算のパフォーマンスが受け入れられない。</span><span class="sxs-lookup"><span data-stu-id="d509f-364">The performance of the converted expression and the resulting calculations would be unacceptable.</span></span>  
  
<span data-ttu-id="d509f-365">次の DAX 関数は、DirectQuery モデルでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d509f-365">The following DAX functions cannot be used in DirectQuery models.</span></span>  
  
<span data-ttu-id="d509f-366">**パス関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-366">**Path functions**</span></span>  
  
<span data-ttu-id="d509f-367">PATH</span><span class="sxs-lookup"><span data-stu-id="d509f-367">PATH</span></span>  
  
<span data-ttu-id="d509f-368">PATHCONTAINS</span><span class="sxs-lookup"><span data-stu-id="d509f-368">PATHCONTAINS</span></span>  
  
<span data-ttu-id="d509f-369">PATHITEM</span><span class="sxs-lookup"><span data-stu-id="d509f-369">PATHITEM</span></span>  
  
<span data-ttu-id="d509f-370">PATHITEMREVERSE</span><span class="sxs-lookup"><span data-stu-id="d509f-370">PATHITEMREVERSE</span></span>  
  
<span data-ttu-id="d509f-371">PATHLENGTH</span><span class="sxs-lookup"><span data-stu-id="d509f-371">PATHLENGTH</span></span>  
  
<span data-ttu-id="d509f-372">**その他の関数**</span><span class="sxs-lookup"><span data-stu-id="d509f-372">**Misc functions**</span></span>  
  
<span data-ttu-id="d509f-373">COUNTBLANK</span><span class="sxs-lookup"><span data-stu-id="d509f-373">COUNTBLANK</span></span>  
  
<span data-ttu-id="d509f-374">FIXED</span><span class="sxs-lookup"><span data-stu-id="d509f-374">FIXED</span></span>  
  
<span data-ttu-id="d509f-375">FORMAT</span><span class="sxs-lookup"><span data-stu-id="d509f-375">FORMAT</span></span>  
  
<span data-ttu-id="d509f-376">RAND</span><span class="sxs-lookup"><span data-stu-id="d509f-376">RAND</span></span>  
  
<span data-ttu-id="d509f-377">RANDBETWEEN</span><span class="sxs-lookup"><span data-stu-id="d509f-377">RANDBETWEEN</span></span>  
  
<span data-ttu-id="d509f-378">**タイム インテリジェンス関数: 開始日と終了日**</span><span class="sxs-lookup"><span data-stu-id="d509f-378">**Time intelligence functions: Start and end dates**</span></span>  
  
<span data-ttu-id="d509f-379">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="d509f-379">DATESQTD</span></span>  
  
<span data-ttu-id="d509f-380">DATESYTD</span><span class="sxs-lookup"><span data-stu-id="d509f-380">DATESYTD</span></span>  
  
<span data-ttu-id="d509f-381">DATESMTD</span><span class="sxs-lookup"><span data-stu-id="d509f-381">DATESMTD</span></span>  
  
<span data-ttu-id="d509f-382">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="d509f-382">DATESQTD</span></span>  
  
<span data-ttu-id="d509f-383">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="d509f-383">DATESINPERIOD</span></span>  
  
<span data-ttu-id="d509f-384">TOTALMTD</span><span class="sxs-lookup"><span data-stu-id="d509f-384">TOTALMTD</span></span>  
  
<span data-ttu-id="d509f-385">TOTALQTD</span><span class="sxs-lookup"><span data-stu-id="d509f-385">TOTALQTD</span></span>  
  
<span data-ttu-id="d509f-386">TOTALYTD</span><span class="sxs-lookup"><span data-stu-id="d509f-386">TOTALYTD</span></span>  
  
<span data-ttu-id="d509f-387">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="d509f-387">DATESINPERIOD</span></span>  
  
<span data-ttu-id="d509f-388">SAMEPERIODLASTYEAR</span><span class="sxs-lookup"><span data-stu-id="d509f-388">SAMEPERIODLASTYEAR</span></span>  
  
<span data-ttu-id="d509f-389">PARALLELPERIOD</span><span class="sxs-lookup"><span data-stu-id="d509f-389">PARALLELPERIOD</span></span>  
  
<span data-ttu-id="d509f-390">**タイムインテリジェンス関数: 残高**</span><span class="sxs-lookup"><span data-stu-id="d509f-390">**Time-intelligence functions: Balances**</span></span>  
  
<span data-ttu-id="d509f-391">OPENINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="d509f-391">OPENINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="d509f-392">OPENINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="d509f-392">OPENINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="d509f-393">OPENINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="d509f-393">OPENINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="d509f-394">CLOSINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="d509f-394">CLOSINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="d509f-395">CLOSINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="d509f-395">CLOSINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="d509f-396">CLOSINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="d509f-396">CLOSINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="d509f-397">**タイム インテリジェンス関数: 前の期間および次の期間**</span><span class="sxs-lookup"><span data-stu-id="d509f-397">**Time intelligence functions: Previous and next periods**</span></span>  
  
<span data-ttu-id="d509f-398">PREVIOUSDAY</span><span class="sxs-lookup"><span data-stu-id="d509f-398">PREVIOUSDAY</span></span>  
  
<span data-ttu-id="d509f-399">PREVIOUSMONTH</span><span class="sxs-lookup"><span data-stu-id="d509f-399">PREVIOUSMONTH</span></span>  
  
<span data-ttu-id="d509f-400">PREVIOUSQUARTER</span><span class="sxs-lookup"><span data-stu-id="d509f-400">PREVIOUSQUARTER</span></span>  
  
<span data-ttu-id="d509f-401">PREVIOUSYEAR</span><span class="sxs-lookup"><span data-stu-id="d509f-401">PREVIOUSYEAR</span></span>  
  
<span data-ttu-id="d509f-402">NEXTDAY</span><span class="sxs-lookup"><span data-stu-id="d509f-402">NEXTDAY</span></span>  
  
<span data-ttu-id="d509f-403">NEXTMONTH</span><span class="sxs-lookup"><span data-stu-id="d509f-403">NEXTMONTH</span></span>  
  
<span data-ttu-id="d509f-404">NEXTQUARTER</span><span class="sxs-lookup"><span data-stu-id="d509f-404">NEXTQUARTER</span></span>  
  
<span data-ttu-id="d509f-405">NEXTYEAR</span><span class="sxs-lookup"><span data-stu-id="d509f-405">NEXTYEAR</span></span>  
  
<span data-ttu-id="d509f-406">**タイム インテリジェンス関数: 期間および期間に対する計算**</span><span class="sxs-lookup"><span data-stu-id="d509f-406">**Time intelligence functions: Periods and calculations over periods**</span></span>  
  
<span data-ttu-id="d509f-407">STARTOFMONTH</span><span class="sxs-lookup"><span data-stu-id="d509f-407">STARTOFMONTH</span></span>  
  
<span data-ttu-id="d509f-408">STARTOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="d509f-408">STARTOFQUARTER</span></span>  
  
<span data-ttu-id="d509f-409">STARTOFYEAR</span><span class="sxs-lookup"><span data-stu-id="d509f-409">STARTOFYEAR</span></span>  
  
<span data-ttu-id="d509f-410">ENDOFMONTH</span><span class="sxs-lookup"><span data-stu-id="d509f-410">ENDOFMONTH</span></span>  
  
<span data-ttu-id="d509f-411">ENDOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="d509f-411">ENDOFQUARTER</span></span>  
  
<span data-ttu-id="d509f-412">ENDOFYEAR</span><span class="sxs-lookup"><span data-stu-id="d509f-412">ENDOFYEAR</span></span>  
  
<span data-ttu-id="d509f-413">FIRSTDATE</span><span class="sxs-lookup"><span data-stu-id="d509f-413">FIRSTDATE</span></span>  
  
<span data-ttu-id="d509f-414">LASTDATE</span><span class="sxs-lookup"><span data-stu-id="d509f-414">LASTDATE</span></span>  
  
<span data-ttu-id="d509f-415">[DATEADD]</span><span class="sxs-lookup"><span data-stu-id="d509f-415">DATEADD</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d509f-416">参照</span><span class="sxs-lookup"><span data-stu-id="d509f-416">See also</span></span>  
[<span data-ttu-id="d509f-417">DirectQuery モード (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="d509f-417">DirectQuery Mode (SSAS Tabular)</span></span>](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  

