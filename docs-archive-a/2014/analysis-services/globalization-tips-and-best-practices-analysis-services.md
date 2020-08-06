---
title: グローバリゼーションのヒントとベストプラクティス (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- translations [Analysis Services], client applications
- date comparisons
- day-of-week comparisons [Analysis Services]
- time [Analysis Services]
- month comparisons [Analysis Services]
ms.assetid: 71a8c438-1370-4c69-961e-d067ee4e47c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: c5bf99878a08e3d2ca57b76e3f902fded2099381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645241"
---
# <a name="globalization-tips-and-best-practices-analysis-services"></a><span data-ttu-id="ee4fe-102">グローバリゼーションのヒントとベスト プラクティス (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="ee4fe-102">Globalization Tips and Best Practices (Analysis Services)</span></span>
  <span data-ttu-id="ee4fe-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 多次元のみ</span><span class="sxs-lookup"><span data-stu-id="ee4fe-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 <span data-ttu-id="ee4fe-104">以下のヒントとガイドラインは、ビジネス インテリジェンス ソリューションの移植性を増すのに役立つと同時に、言語と照合順序の設定に直接関連するエラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-104">These tips and guidelines can help increase the portability of your business intelligence solutions and avoid errors that are directly related to language and collation settings.</span></span>  
  
-   [<span data-ttu-id="ee4fe-105">スタック全体における類似した照合順序の使用</span><span class="sxs-lookup"><span data-stu-id="ee4fe-105">Use similar collations throughout the stack</span></span>](#bkmk_sameColl)  
  
-   [<span data-ttu-id="ee4fe-106">一般的な照合順序に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ee4fe-106">Common collation recommendations</span></span>](#bkmk_recos)  
  
-   [<span data-ttu-id="ee4fe-107">オブジェクト識別子の大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="ee4fe-107">Case sensitivity of object identifiers</span></span>](#bkmk_objid)  
  
-   [<span data-ttu-id="ee4fe-108">Excel と SQL Server Profiler を使用したロケールのテスト</span><span class="sxs-lookup"><span data-stu-id="ee4fe-108">Locale testing using Excel and SQL Server Profiler</span></span>](#bkmk_test)  
  
-   [<span data-ttu-id="ee4fe-109">翻訳を含むソリューションでの MDX クエリの作成</span><span class="sxs-lookup"><span data-stu-id="ee4fe-109">Writing MDX queries in a solution containing Translations</span></span>](#bkmk_mdx)  
  
-   [<span data-ttu-id="ee4fe-110">日付と時刻の値を含む MDX クエリの作成</span><span class="sxs-lookup"><span data-stu-id="ee4fe-110">Writing MDX queries containing Date and Time Values</span></span>](#bkmk_datetime)  
  
##  <a name="use-similar-collations-throughout-the-stack"></a><a name="bkmk_sameColl"></a><span data-ttu-id="ee4fe-111">スタック全体で同様の照合順序を使用する</span><span class="sxs-lookup"><span data-stu-id="ee4fe-111">Use similar collations throughout the stack</span></span>  
 <span data-ttu-id="ee4fe-112">可能な場合には、データベース エンジンに対して使用する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 内の照合順序設定を、文字幅の区別、大文字小文字の区別、アクセントの区別ができるだけ同じ、類似した設定にしてください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-112">If possible, try to use the same collation settings in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you use for the database engine, striving for correspondence in width-sensitivity and case-sensitivity, and access-sensitivity.</span></span>  
  
 <span data-ttu-id="ee4fe-113">各サービスには独自の照合順序設定があり、データベース エンジンは既定で SQL_Latin1_General_CP1_CI_AS に、Analysis Services は Latin1_General_AS にそれぞれ設定されています。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-113">Each service has its own collation settings, with the database engine default set to SQL_Latin1_General_CP1_CI_AS and Analysis Services set to Latin1_General_AS.</span></span> <span data-ttu-id="ee4fe-114">これらの既定値は、大文字小文字、文字幅、アクセントの区別に関しては互換性があります。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-114">The defaults are compatible in term of case, width, and accent sensitivity.</span></span> <span data-ttu-id="ee4fe-115">いずれかの照合順序の設定を変える場合、照合順序プロパティが基本的な仕方で異なると、問題が生じる恐れがあります。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-115">Be forewarned that if you vary the settings of either collation, you can run into problems when the collation properties diverge in fundamental ways.</span></span>  
  
 <span data-ttu-id="ee4fe-116">照合順序設定が機能的に同じである場合でも、文字列内のいずれかの場所にある空白がサービスごとに異なって解釈されるという特殊なケースに陥ることがあります。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-116">Even when collation settings are functionally equivalent, you can run into a special case where an empty space anywhere within a string is interpreted differently by each service.</span></span>  
  
 <span data-ttu-id="ee4fe-117">空白文字は「特殊ケース」です。Unicode では、単一バイト (SBCS) とダブル バイト文字セット (DBCS) のどちらでも表せるからです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-117">The space character is a 'special case' because it can be represented as a single-byte (SBCS) or double-byte character set (DBCS) in Unicode.</span></span> <span data-ttu-id="ee4fe-118">リレーショナル エンジンでは、スペース (1 つは SBCS、もう 1 つは DBCS) で区切られた 2 つの複合文字列は同じであると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-118">In the relational engine, two compound strings separated by a space -- one using SBCS, the other in DBCS -- are considered identical.</span></span> <span data-ttu-id="ee4fe-119">Analysis Services では、処理中、同じ 2 つの複合文字列は同一ではなく、2 つ目のインスタンスは重複としてフラグが立てられます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-119">In Analysis Services, during processing, the same two compound strings are not identical, and the second instance will be flagged as a duplicate.</span></span>  
  
 <span data-ttu-id="ee4fe-120">詳細および提案されている回避策については、「 [Unicode 文字列にブランクがある場合、照合順序に基づいて処理結果が異なる](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-120">For more details and suggested workarounds, see [Blanks in a Unicode string have different processing outcomes based on collation](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx).</span></span>  
  
##  <a name="common-collation-recommendations"></a><a name="bkmk_recos"></a> <span data-ttu-id="ee4fe-121">照合順序に関する一般的な推奨事項</span><span class="sxs-lookup"><span data-stu-id="ee4fe-121">Common collation recommendations</span></span>  
 <span data-ttu-id="ee4fe-122">Analysis Services は、常にすべての使用可能な言語および照合順序の一覧を提示します。ユーザーが選択した言語に基づいて照合順序がフィルター処理されることはありません。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-122">Analysis Services always presents the full list of all available languages and collations; it does not filter the collations based on the language you selected.</span></span> <span data-ttu-id="ee4fe-123">必ず、実行可能な組み合わせを選択してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-123">Be sure to choose a workable combination.</span></span>  
  
 <span data-ttu-id="ee4fe-124">一般的に使用される照合順序には、次の一覧にあるものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-124">Some of the more commonly used collations include those in the following list.</span></span>  
  
 <span data-ttu-id="ee4fe-125">この一覧は、その他の選択肢を除外する明確な推奨事項ではなく、詳しい調査の開始点と見なしてください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-125">You should consider this list to be a starting point for further investigation, rather than a definitive recommendation that excludes other options.</span></span> <span data-ttu-id="ee4fe-126">この一覧で特に推奨されていない照合順序が、対象となるデータに最適なものであることもあります。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-126">You might find that a collation not specifically recommended is the one that works best for your data.</span></span> <span data-ttu-id="ee4fe-127">データ値が適切に並べ替えられ、適切に比較されるかどうか確認する唯一の方法は、徹底的にテストすることです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-127">Thorough testing is the only way to verify whether data values are sorted and compared appropriately.</span></span> <span data-ttu-id="ee4fe-128">照合順序をテストする際には、いつものように、処理とクエリの両方のワークロードを実行してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-128">As always, be sure to run both processing and query workloads when testing collation.</span></span>  
  
-   <span data-ttu-id="ee4fe-129">Latin1_General_100_AS は、 [ISO 基本ラテン アルファベット](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet)の 26 文字を使用するアプリケーションによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-129">Latin1_General_100_AS is often used for applications that use the 26 characters of the [ISO basic Latin alphabet](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet).</span></span>  
  
-   <span data-ttu-id="ee4fe-130">スカンジナビア語の文字 (ø など) 含む北ヨーロッパ言語では、Finnish_Swedish_100 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-130">North European languages that include Scandinavian letters (such as ø) can use Finnish_Swedish_100.</span></span>  
  
-   <span data-ttu-id="ee4fe-131">ロシア語などの東ヨーロッパ言語では、多くの場合、Cyrillic_General_100 を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-131">East European languages, such as Russian, often use Cyrillic_General_100.</span></span>  
  
-   <span data-ttu-id="ee4fe-132">中国語の言語および照合順序は地域によって異なりますが、一般に簡体中国語または繁体中国語のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-132">Chinese language and collations vary by region, but are generally either Chinese Simplified or Chinese Traditional.</span></span>  
  
     <span data-ttu-id="ee4fe-133">中華人民共和国およびシンガポールでは、Microsoft サポートの観察によると、ピンイン付きの簡体字国語の並べ替え順序がよく使用されています。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-133">In PRC and Singapore, Microsoft Support tends to see Simplified Chinese, with Pinyin as the preferred sort order.</span></span> <span data-ttu-id="ee4fe-134">推奨される照合順序は、Chinese_PRC (SQL Server 2000 の場合)、Chinese_PRC_90 (SQL Server 2005 の場合)、または Chinese_Simplified_Pinyin_100 (SQL Server 2008 以降の場合) です。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-134">The recommended collations are Chinese_PRC (for SQL Server 2000), Chinese_PRC_90 (for SQL Server 2005) or Chinese_Simplified_Pinyin_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="ee4fe-135">台湾では、繁体字中国語のほうが一般的で、お勧めする並べ替え順序は画数に基づく次のものです。Chinese_Taiwan_Stroke (SQL Server 2000 の場合)、Chinese_Taiwan_Stroke_90 (SQL Server 2005 の場合)、Chinese_Traditional_Stroke_Count_100 (SQL Server 2008 以降の場合)。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-135">In Taiwan, it is more common to see Traditional Chinese with the recommended sort order is based on Stroke Count: Chinese_Taiwan_Stroke (for SQL Server 2000), Chinese_Taiwan_Stroke_90 (for SQL Server 2005) or Chinese_Traditional_Stroke_Count_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="ee4fe-136">その他の地域 (香港特別行政区やマカオ特別行政区など) も、繁体字中国語を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-136">Other regions (such as Hong Kong SAR and Macao SAR) also use Traditional Chinese.</span></span> <span data-ttu-id="ee4fe-137">香港では、照合順序に Chinese_Hong_Kong_Stroke_90 (SQL Server 2005 上) が使用されることも珍しくありません。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-137">For collations, in Hong Kong, it's not unusual to see Chinese_Hong_Kong_Stroke_90 (on SQL Server 2005).</span></span> <span data-ttu-id="ee4fe-138">マカオでは、Chinese_Traditional_Stroke_Count_100 (SQL Server 2008 以降) が非常に頻繁に使用されています。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-138">In Macao, Chinese_Traditional_Stroke_Count_100 (on SQL Server 2008 and later) is used fairly often.</span></span>  
  
-   <span data-ttu-id="ee4fe-139">日本語では、最もよく使用される照合順序は Japanese_CI_AS です。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-139">For Japanese, the most commonly used collation is Japanese_CI_AS.</span></span> <span data-ttu-id="ee4fe-140">[JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213)をサポートするシステムでは、Japanese_XJIS_100 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-140">Japanese_XJIS_100 is used in installations supporting [JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213).</span></span> <span data-ttu-id="ee4fe-141">Japanese_BIN2 は、通常、Windows 以外のプラットフォームからのデータ、または SQL Server リレーショナル データベース エンジン以外のデータ ソースからのデータを移行するプロジェクトで使用されるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-141">Japanese_BIN2 is typically seen in data migration projects, with data originating from non-Windows platforms, or from data sources other than the SQL Server relational database engine.</span></span>  
  
     <span data-ttu-id="ee4fe-142">Japanese_Bushu_Kakusu_100 が、Analysis Services のワークロードを実行するサーバーで使用されることはまれです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-142">Japanese_Bushu_Kakusu_100 is rarely seen in servers that run Analysis Services workloads.</span></span>  
  
-   <span data-ttu-id="ee4fe-143">韓国では、Korean_100 が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-143">Korean_100 is recommended for Korean.</span></span> <span data-ttu-id="ee4fe-144">Korean_Wansung_Unicode も使用可能なリストにまだ含まれていますが、これは非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-144">Although Korean_Wansung_Unicode is still available in the list, it has been deprecated.</span></span>  
  
##  <a name="case-sensitivity-of-object-identifiers"></a><a name="bkmk_objid"></a> <span data-ttu-id="ee4fe-145">オブジェクト ID の大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="ee4fe-145">Case sensitivity of object identifiers</span></span>  
 <span data-ttu-id="ee4fe-146">SQL Server 2012 SP2 以降、オブジェクト ID の大文字小文字は照合順序に関係なく区別されるようになりましたが、言語ごとに次のように動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-146">Starting in SQL Server 2012 SP2, case sensitivity of object IDs is enforced independently of the collation, but the behavior varies by language:</span></span>  
  
|<span data-ttu-id="ee4fe-147">言語セット</span><span class="sxs-lookup"><span data-stu-id="ee4fe-147">Language script</span></span>|<span data-ttu-id="ee4fe-148">大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="ee4fe-148">Case sensitivity</span></span>|  
|---------------------|----------------------|  
|<span data-ttu-id="ee4fe-149">**基本的なラテン アルファベット**</span><span class="sxs-lookup"><span data-stu-id="ee4fe-149">**Basic Latin alphabet**</span></span>|<span data-ttu-id="ee4fe-150">ラテン文字 (任意の 26 個の英語大文字小文字) で表されるオブジェクト ID は、照合順序に関係なく、大文字小文字の区別なしで処理されます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-150">Object identifiers expressed in Latin script (any of the 26 English upper or lower case letters) are treated as case-insensitive, regardless of collation.</span></span> <span data-ttu-id="ee4fe-151">たとえば、次のオブジェクト ID は同じであると見なされます。54321**abcdef**、54321**ABCDEF**、54321**AbCdEf**。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-151">For example, the following object IDs are considered identical: 54321**abcdef**, 54321**ABCDEF**, 54321**AbCdEf**.</span></span> <span data-ttu-id="ee4fe-152">Analysis Services はこうした文字列内の文字を内部的には大文字として処理し、言語に関係なく単純なバイト比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-152">Internally, Analysis Services treats the characters in the string as if all are uppercase, and then performs a simple byte comparison that is independent of language.</span></span><br /><br /> <span data-ttu-id="ee4fe-153">26 文字だけが影響を受けることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-153">Note that only the 26 characters are affected.</span></span> <span data-ttu-id="ee4fe-154">言語が西ヨーロッパ言語で、スカンジナビア語の文字を使用している場合、追加の文字は大文字に変換されません。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-154">If the language is West European, but uses Scandinavian characters, the additional character will not be upper-cased.</span></span>|  
|<span data-ttu-id="ee4fe-155">**キリル語、ギリシャ語、コプト語、アルメニア語**</span><span class="sxs-lookup"><span data-stu-id="ee4fe-155">**Cyrillic, Greek, Coptic, Armenian**</span></span>|<span data-ttu-id="ee4fe-156">キリル語など、ラテン語以外の大文字小文字の区別がある言語のオブジェクト ID では、常に大文字小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-156">Object identifiers in non-Latin bicameral script, such as Cyrillic, are always case-sensitive.</span></span> <span data-ttu-id="ee4fe-157">たとえば、Измерение と измерение の違いは最初の文字の大文字小文字だけですが、この場合も 2 つの異なる値であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-157">For example, Измерение and измерение are considered two distinct values, even though the only difference is the case of the first letter.</span></span>|  
  
 <span data-ttu-id="ee4fe-158">**オブジェクト ID の大文字小文字の区別の影響**</span><span class="sxs-lookup"><span data-stu-id="ee4fe-158">**Implications of case-sensitivity for object identifiers**</span></span>  
  
 <span data-ttu-id="ee4fe-159">この表で説明されている大文字小文字の動作に関連するのは、オブジェクト名ではなく、オブジェクト ID のみです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-159">Only object identifiers, and not object names, are subject to the casing behaviors described in the table.</span></span> <span data-ttu-id="ee4fe-160">ご使用のソリューションの動作方法に変化がある場合 (比較の前後、つまり SQL Server 2012 SP2 以降のインストール後)、処理上の問題が生じる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-160">If you see a change in how your solution works (a before and after comparison -- after installing SQL Server 2012 SP2 or later), it will most likely be a processing issue.</span></span> <span data-ttu-id="ee4fe-161">クエリは、オブジェクト ID によって影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-161">Queries are not impacted by object identifiers.</span></span> <span data-ttu-id="ee4fe-162">(DAX と MDX の) どちらのクエリ言語の場合であっても、数式エンジンは (ID ではなく) オブジェクト名を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-162">For both query languages (DAX and MDX), the formula engine uses the object name (not the identifier).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee4fe-163">大文字小文字の区別に関連するコードの変更は、一部のアプリケーションの互換性に影響を与える変更です。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-163">Code changes related to case-sensitivity have been a breaking change for some applications.</span></span> <span data-ttu-id="ee4fe-164">詳細については、「 [SQL Server 2014 の Analysis Services 機能における重大な変更」を](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-164">See [Breaking Changes to Analysis Services Features in SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md) for more information.</span></span>  
  
##  <a name="locale-testing-using-excel-sql-server-profiler-and-sql-server-management-studio"></a><a name="bkmk_test"></a> <span data-ttu-id="ee4fe-165">Excel、SQL Server Profiler、SQL Server Management Studio を使用したロケール テスト</span><span class="sxs-lookup"><span data-stu-id="ee4fe-165">Locale testing using Excel, SQL Server Profiler and SQL Server Management Studio</span></span>  
 <span data-ttu-id="ee4fe-166">翻訳をテストする場合、接続で対象の翻訳の LCID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-166">When testing translations, the connection must specify the LCID of the translation.</span></span> <span data-ttu-id="ee4fe-167">「 [SSAS から Excel への各種言語の取得](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx)」に記されているように、Excel を使用して翻訳をテストできます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-167">As documented in [Get Different Language from SSAS into Excel](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx), you can use Excel to test your translations.</span></span>  
  
 <span data-ttu-id="ee4fe-168">このためには、.odc ファイルを手動で編集し、ロケール ID 接続文字列プロパティを含めます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-168">You can do this by hand editing the .odc file to include the locale identifier connection string property.</span></span> <span data-ttu-id="ee4fe-169">これを、Adventure Works サンプル多次元データベースを使用して試してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-169">Try this out with the Adventure Works sample multidimensional database.</span></span>  
  
-   <span data-ttu-id="ee4fe-170">既存の .odc ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-170">Search for existing .odc files.</span></span> <span data-ttu-id="ee4fe-171">Adventure Works 多次元用のファイルが見つかったら、右クリックしてメモ帳で開きます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-171">When you find the one for Adventure Works multidimensional, right-click the file to open it in Notepad.</span></span>  
  
-   <span data-ttu-id="ee4fe-172">接続文字列に `Locale Identifier=1036` を追加します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-172">Add `Locale Identifier=1036` to the connection string.</span></span> <span data-ttu-id="ee4fe-173">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-173">Save and close the file.</span></span>  
  
-   <span data-ttu-id="ee4fe-174">Excel を開く |**データ**  | **既存の接続**。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-174">Open Excel | **Data** | **Existing Connections**.</span></span> <span data-ttu-id="ee4fe-175">リストをフィルター処理し、対象のコンピューター上の接続ファイルのみにします。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-175">Filter the list to just connections files on this computer.</span></span> <span data-ttu-id="ee4fe-176">Adventure Works 用の接続を検索します (名前を注意深く探します。複数ある場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-176">Find the connection for Adventure Works (look at the name carefully; you might have more than one).</span></span> <span data-ttu-id="ee4fe-177">接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-177">Open the connection.</span></span>  
  
     <span data-ttu-id="ee4fe-178">Adventure Works サンプル データベースのフランス語翻訳が表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-178">You should see the French translations from the Adventure Works sample database.</span></span>  
  
     <span data-ttu-id="ee4fe-179">![フランス語翻訳が含まれる Excel ピボットテーブル](media/ssas-localetest-excel.png "フランス語翻訳が含まれる Excel ピボットテーブル")</span><span class="sxs-lookup"><span data-stu-id="ee4fe-179">![Excel PivotTable with French translations](media/ssas-localetest-excel.png "Excel PivotTable with French translations")</span></span>  
  
 <span data-ttu-id="ee4fe-180">その後、SQL Server Profiler を使用してロケールを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-180">As a follow up, you can use SQL Server Profiler to confirm the locale.</span></span> <span data-ttu-id="ee4fe-181">`Session Initialize` イベントをクリックし、下に表示されるテキスト領域のプロパティ リストを探して `<localeidentifier>1036</localeidentifier>`を見つけます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-181">Click a `Session Initialize` event and then look at the property list in the text area below to find `<localeidentifier>1036</localeidentifier>`.</span></span>  
  
 <span data-ttu-id="ee4fe-182">Management Studio で、サーバー接続のロケール ID を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-182">In Management Studio, you can specify Locale Identifier on a server connection.</span></span>  
  
-   <span data-ttu-id="ee4fe-183">オブジェクトエクスプローラー |**接続**  | **Analysis Services**  | **オプション**で、[**追加の接続パラメーター** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-183">In Object Explorer | **Connect** | **Analysis Services** | **Options**, click the **Additional Connection Parameters** tab.</span></span>  
  
-   <span data-ttu-id="ee4fe-184">`Local Identifier=1036` と入力し、[ **接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-184">Enter `Local Identifier=1036` and then click **Connect**.</span></span>  
  
-   <span data-ttu-id="ee4fe-185">Adventure Works データベースに対して、MDX クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-185">Execute an MDX query against the Adventure Works database.</span></span> <span data-ttu-id="ee4fe-186">クエリ結果は、フランス語翻訳になるはずです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-186">The query results should be the French translations.</span></span>  
  
     <span data-ttu-id="ee4fe-187">![SSMS のフランス語翻訳が含まれる MDX クエリ](media/ssas-localetest-ssms.png "SSMS のフランス語翻訳が含まれる MDX クエリ")</span><span class="sxs-lookup"><span data-stu-id="ee4fe-187">![MDX query with French translations in SSMS](media/ssas-localetest-ssms.png "MDX query with French translations in SSMS")</span></span>  
  
##  <a name="writing-mdx-queries-in-a-solution-containing-translations"></a><a name="bkmk_mdx"></a> <span data-ttu-id="ee4fe-188">翻訳が含まれるソリューションにおける MDX クエリの作成</span><span class="sxs-lookup"><span data-stu-id="ee4fe-188">Writing MDX queries in a solution containing Translations</span></span>  
 <span data-ttu-id="ee4fe-189">翻訳では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトの名前の表示情報が提供されますが、同じオブジェクトの識別子は翻訳されません。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-189">Translations provide display information for the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects, but the identifiers for the same objects are not translated.</span></span> <span data-ttu-id="ee4fe-190">可能であれば必ず、翻訳されたキャプションと名前ではなく、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトの識別子とキーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-190">Whenever possible, use the identifiers and keys for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects instead of the translated captions and names.</span></span> <span data-ttu-id="ee4fe-191">たとえば、多次元式 (MDX) ステートメントおよびスクリプトのメンバー名ではなく、メンバー キーを使用して、複数の言語間での移植性を確保します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-191">For example, use member keys instead of member names for Multidimensional Expressions (MDX) statements and scripts to ensure portability across multiple languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee4fe-192">表形式のオブジェクト名は、照合順序に関係なく、いつでも大文字小文字の区別がないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-192">Recall that tabular object names are always case-insensitive, regardless of collation.</span></span> <span data-ttu-id="ee4fe-193">一方、多次元オブジェクト名の場合、照合の大文字小文字の区別の設定に従います。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-193">Multidimensional object names, on the other hand, follow the case sensitivity of the collation.</span></span> <span data-ttu-id="ee4fe-194">多次元オブジェクト名のみが大文字小文字の区別があるため、多次元オブジェクトを参照するすべての MDX クエリの大文字小文字が正しいことを必ずご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-194">Since only multidimensional object names are case-sensitive make sure that all MDX queries referencing multidimensional objects are cased correctly.</span></span>  
  
##  <a name="writing-mdx-queries-containing-date-and-time-values"></a><a name="bkmk_datetime"></a> <span data-ttu-id="ee4fe-195">日付値と時刻値が含まれる MDX クエリの作成</span><span class="sxs-lookup"><span data-stu-id="ee4fe-195">Writing MDX queries containing Date and Time Values</span></span>  
 <span data-ttu-id="ee4fe-196">日付と時刻を MDX に基づくクエリとすることで、異なる言語間での移植性を向上させるための提案を以下に記します。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-196">The following suggestions to make your date and time-based MDX queries more portable across different languages:</span></span>  
  
1.  <span data-ttu-id="ee4fe-197">**比較と操作に対する数値部分の使用**</span><span class="sxs-lookup"><span data-stu-id="ee4fe-197">**Use numeric parts for comparisons and operations**</span></span>  
  
     <span data-ttu-id="ee4fe-198">月と曜日の比較および操作を実行する場合は、文字列相当値ではなく、日付と時刻の数値部分を使用します (たとえば、MonthName ではなく MonthNumberofYear を使用します)。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-198">When you perform month and day-of-week comparisons and operations, use the numeric date and time parts instead of the string equivalents (for example, use MonthNumberofYear instead of MonthName).</span></span> <span data-ttu-id="ee4fe-199">数値は、言語翻訳の違いによってほとんど影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-199">Numeric values are least affected by differences in language translations.</span></span>  
  
2.  <span data-ttu-id="ee4fe-200">**結果セットにおける文字列相当値の使用**</span><span class="sxs-lookup"><span data-stu-id="ee4fe-200">**Use string equivalents in a result set**</span></span>  
  
     <span data-ttu-id="ee4fe-201">エンド ユーザーに表示する結果セットを作成する際、(MonthName などの) 文字列を使用し、提供した翻訳を複数言語の読者が利用できるようにすることを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-201">When building result sets seen by end-users, consider using the string (such as MonthName) so that your multi-lingual audience can benefit from the translations you've provided.</span></span>  
  
3.  <span data-ttu-id="ee4fe-202">**ユニバーサルの日時情報に対する ISO 日付形式の使用**</span><span class="sxs-lookup"><span data-stu-id="ee4fe-202">**Use ISO date formats for universal date and time information**</span></span>  
  
     <span data-ttu-id="ee4fe-203">1 人の [Analysis Services の専門家](http://geekswithblogs.net/darrengosbell/Default.aspx) は次のように勧めています。「SQL または MDX でクエリに渡す日付文字列には ISO 日付形式 yyyy-mm-dd を必ず使います。この形式にはあいまいさがなく、クライアントまたはサーバーの地域設定に関係なく作動するためです。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-203">One [Analysis Services expert](http://geekswithblogs.net/darrengosbell/Default.aspx) has this recommendation: "I always use the ISO date format yyyy-mm-dd for any date strings that I pass in to queries in SQL or MDX because it's unambiguous and will work regardless of the client or server's regional settings.</span></span> <span data-ttu-id="ee4fe-204">サーバーでは、あいまいな日付形式を解析する場合にこの地域設定に従う必要があるとは思いますが、どのような場合であってもそれが最善の選択肢であると考える必要はないとも思います」。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-204">I would agree that the server should defer to its regional settings when parsing an ambiguous date format, but I also think that if you've got an option that is not open to interpretation that you are better choosing that anyway".</span></span>  
  
4.  `Use the Format function to enforce a specific format, regardless of regional language settings`  
  
     <span data-ttu-id="ee4fe-205">フォーラム投稿から借用している以下の MDX クエリは、基礎となる地域設定とは無関係に、特定の形式で日付を返すための Format の使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-205">The following MDX query, borrowed from a forum post, illustrates how to use Format to return dates in a specific format, irrespective of the underlying regional settings.</span></span>  
  
     <span data-ttu-id="ee4fe-206">元々の投稿内容については、「 [SSAS 2012 によって生成される無効な日付 (Network Steve でのフォーラム投稿)](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee4fe-206">See [SSAS 2012 generates invalid dates (forum post on Network Steve](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) for the original post.</span></span>  
  
    ```  
    WITH MEMBER [LinkTimeAdd11Date_Manual] as Format(dateadd("d",15,"2014-12-11"), "mm/dd/yyyy")  
    member [LinkTimeAdd15Date_Manual] as Format(dateadd("d",11,"2014-12-13"), "mm/dd/yyyy")  
    SELECT  
    { [LinkTimeAdd11Date_Manual]  
    ,[LinkTimeAdd15Date_Manual]  
    }  
    ON COLUMNS   
    FROM [Adventure Works]  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ee4fe-207">参照</span><span class="sxs-lookup"><span data-stu-id="ee4fe-207">See Also</span></span>  
 <span data-ttu-id="ee4fe-208">[多次元 Analysis Services のグローバリゼーションのシナリオ](globalization-scenarios-for-analysis-services-multiidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="ee4fe-208">[Globalization scenarios for Analysis Services Multidimensional](globalization-scenarios-for-analysis-services-multiidimensional.md) </span></span>  
 [<span data-ttu-id="ee4fe-209">国際化に対応した Transact-SQL ステートメントの記述</span><span class="sxs-lookup"><span data-stu-id="ee4fe-209">Write International Transact-SQL Statements</span></span>](../relational-databases/collations/write-international-transact-sql-statements.md)  
