---
title: 用語抽出変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextractiontrans.f1
helpviewer_keywords:
- word boundaries [Integration Services]
- extracting data [Integration Services]
- sentence boundaries
- word extractions [Integration Services]
- Term Extraction transformation
- tagging words
- normalized data [Integration Services]
- tokenizing text [Integration Services]
- parts of speech [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- stemming words [Integration Services]
ms.assetid: d0821526-1603-4ea6-8322-2d901568fbeb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8215b53de7da43bbdbcbe29a9bb7f5ad8edc0d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738544"
---
# <a name="term-extraction-transformation"></a><span data-ttu-id="cca4f-102">用語抽出変換</span><span class="sxs-lookup"><span data-stu-id="cca4f-102">Term Extraction Transformation</span></span>
  <span data-ttu-id="cca4f-103">用語抽出変換は、変換入力列内のテキストから用語を抽出し、変換出力列に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-103">The Term Extraction transformation extracts terms from text in a transformation input column, and then writes the terms to a transformation output column.</span></span> <span data-ttu-id="cca4f-104">この変換で処理されるテキストは英語テキストのみで、独自の英語辞書および英語に関する言語情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-104">The transformation works only with English text and it uses its own English dictionary and linguistic information about English.</span></span>  
  
 <span data-ttu-id="cca4f-105">用語抽出変換を使用すると、データセットの内容を検出できます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-105">You can use the Term Extraction transformation to discover the content of a data set.</span></span> <span data-ttu-id="cca4f-106">たとえば、電子メール メッセージが含まれるテキストに、製品に関する有用なフィードバックがある場合、用語抽出変換を使用してメッセージに記述されているトピックを抽出し、フィードバックの分析に使用できます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-106">For example, text that contains e-mail messages may provide useful feedback about products, so that you could use the Term Extraction transformation to extract the topics of discussion in the messages, as a way of analyzing the feedback.</span></span>  
  
## <a name="extracted-terms-and-data-types"></a><span data-ttu-id="cca4f-107">抽出された用語とデータ型</span><span class="sxs-lookup"><span data-stu-id="cca4f-107">Extracted Terms and Data Types</span></span>  
 <span data-ttu-id="cca4f-108">用語抽出変換は、名詞のみ、名詞句のみ、または名詞と名詞句の両方を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-108">The Term Extraction transformation can extract nouns only, noun phrases only, or both nouns and noun phases.</span></span> <span data-ttu-id="cca4f-109">名詞とは 1 つの名詞のことです。名詞句とは 2 つ以上の単語で、1 語は名詞、他の語は名詞または形容詞です。</span><span class="sxs-lookup"><span data-stu-id="cca4f-109">A noun is a single noun; a noun phrases is at least two words, of which one is a noun and the other is a noun or an adjective.</span></span> <span data-ttu-id="cca4f-110">たとえば、この変換が名詞のみのオプションを使用している場合は、 *bicycle* や *landscape*などの用語が抽出されます。名詞句のオプションを使用している場合は、 *new blue bicycle*、 *bicycle helmet*、 *boxed bicycles*などの用語が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-110">For example, if the transformation uses the nouns-only option, it extracts terms like *bicycle* and *landscape*; if the transformation uses the noun phrase option, it extracts terms like *new blue bicycle*, *bicycle helmet*, and *boxed bicycles*.</span></span>  
  
 <span data-ttu-id="cca4f-111">冠詞と代名詞は抽出されません。</span><span class="sxs-lookup"><span data-stu-id="cca4f-111">Articles and pronouns are not extracted.</span></span> <span data-ttu-id="cca4f-112">たとえば、 *the bicycle* 、 *my bicycle*、および *that bicycle*のテキストからは、用語 *bicycle*が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-112">For example, the Term Extraction transformation extracts the term *bicycle* from the text *the bicycle*, *my bicycle*, and *that bicycle*.</span></span>  
  
 <span data-ttu-id="cca4f-113">用語抽出変換は、抽出する各用語のスコアを生成します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-113">The Term Extraction transformation generates a score for each term that it extracts.</span></span> <span data-ttu-id="cca4f-114">スコアには、TFIDF 値または生の頻度のどちらかを設定できます。生の頻度とは、正規化された用語が入力内に出現する回数のことです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-114">The score can be either a TFIDF value or the raw frequency, meaning the number of times the normalized term appears in the input.</span></span> <span data-ttu-id="cca4f-115">どちらの場合も、スコアは 0 より大きい実数で表されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-115">In either case, the score is represented by a real number that is greater than 0.</span></span> <span data-ttu-id="cca4f-116">たとえば、TFIDF スコアの値は 0.5、頻度は 1.0 または 2.0 などのように表されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-116">For example, the TFIDF score might have the value 0.5, and the frequency would be a value like 1.0 or 2.0.</span></span>  
  
 <span data-ttu-id="cca4f-117">用語抽出変換の出力には、2 つの列のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-117">The output of the Term Extraction transformation includes only two columns.</span></span> <span data-ttu-id="cca4f-118">1 つの列には抽出した用語が含まれ、もう 1 つの列にはスコアが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-118">One column contains the extracted terms and the other column contains the score.</span></span> <span data-ttu-id="cca4f-119">列の既定の名前は**Term**と `Score` です。</span><span class="sxs-lookup"><span data-stu-id="cca4f-119">The default names of the columns are **Term** and `Score`.</span></span> <span data-ttu-id="cca4f-120">入力のテキスト列には複数の用語が含まれる場合があるため、通常、用語抽出変換の出力には、入力よりも多くの行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-120">Because the text column in the input may contain multiple terms, the output of the Term Extraction transformation typically has more rows than the input.</span></span>  
  
 <span data-ttu-id="cca4f-121">抽出した用語がテーブルに書き込まれると、用語参照変換、あいまい参照変換、参照変換など、他の参照変換で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-121">If the extracted terms are written to a table, they can be used by other lookup transformation such as the Term Lookup, Fuzzy Lookup, and Lookup transformations.</span></span>  
  
 <span data-ttu-id="cca4f-122">用語抽出変換で処理できるテキストは、DT_WSTR または DT_NTEXT データ型のどちらかの列にあるテキストのみです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-122">The Term Extraction transformation can work only with text in a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="cca4f-123">列にテキストが含まれていても、これらのデータ型ではない場合、データ変換の変換を使用して、DT_WSTR または DT_NTEXT データ型の列をデータ フローに追加し、列の値を新しい列にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-123">If a column contains text but does not have one of these data types, the Data Conversion transformation can be used to add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="cca4f-124">その後、データ変換の変換からの出力を、用語抽出変換への入力として使用できます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-124">The output from the Data Conversion transformation can then be used as the input to the Term Extraction transformation.</span></span> <span data-ttu-id="cca4f-125">詳細については、「 [Data Conversion Transformation](data-conversion-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cca4f-125">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="exclusion-terms"></a><span data-ttu-id="cca4f-126">除外用語</span><span class="sxs-lookup"><span data-stu-id="cca4f-126">Exclusion Terms</span></span>  
 <span data-ttu-id="cca4f-127">必要に応じて、用語抽出変換は、除外用語を含むテーブルの列を参照できます。除外用語とは、変換によりデータセットから抽出されたときに、スキップされる用語のことです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-127">Optionally, the Term Extraction transformation can reference a column in a table that contains exclusion terms, meaning terms that the transformation should skip when it extracts terms from a data set.</span></span> <span data-ttu-id="cca4f-128">これは、ある用語の組み合わせが、非常に高い頻度で発生するためにノイズ ワードになる場合など、特定の業務や事業では既に重要でないと判断されている場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cca4f-128">This is useful when a set of terms has already been identified as inconsequential in a particular business and industry, typically because the term occurs with such high frequency that it becomes a noise word.</span></span> <span data-ttu-id="cca4f-129">たとえば、特定ブランドの自動車に関する顧客サポート情報が含まれるデータセットから用語を抽出するときに、ブランド名自体は除外します。ブランド名は非常に頻繁に挙げられるので、重要性を持たないためです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-129">For example, when extracting terms from a data set that contains customer support information about a particular brand of cars, the brand name itself might be excluded because it is mentioned too frequently to have significance.</span></span> <span data-ttu-id="cca4f-130">このため、除外一覧の値は処理するデータセットに応じてカスタマイズする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-130">Therefore, the values in the exclusion list must be customized to the data set you are working with.</span></span>  
  
 <span data-ttu-id="cca4f-131">ある用語を除外一覧に追加すると、その用語を含むすべての用語 (単語または名詞句) も除外されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-131">When you add a term to the exclusion list, all the terms-words or noun phrases-that contain the term are also excluded.</span></span> <span data-ttu-id="cca4f-132">たとえば、除外一覧に 1 つの単語 *data*が含まれる場合、 *data*、 *data mining*、 *data integrity*、および *data validation* など、この単語を含むすべての用語も除外されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-132">For example, if the exclusion list includes the single word *data*, then all the terms that contain this word, such as *data*, *data mining*, *data integrity*, and *data validation* will also be excluded.</span></span> <span data-ttu-id="cca4f-133">単語 *data*を含む複合語のみを除外する場合、その複合語を除外一覧に明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-133">If you want to exclude only compounds that contain the word *data*, you must explicitly add those compound terms to the exclusion list.</span></span> <span data-ttu-id="cca4f-134">たとえば、 *data*の出現を抽出して、 *data validation*を除外する場合は、 *data validation* を除外一覧に追加し、除外一覧から *data* が削除されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-134">For example, if you want to extract incidences of *data*, but exclude *data validation*, you would add *data validation* to the exclusion list, and make sure that *data* is removed from the exclusion list.</span></span>  
  
 <span data-ttu-id="cca4f-135">参照テーブルは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または Access データベースのテーブルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-135">The reference table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="cca4f-136">用語抽出変換は、個別の OLE DB 接続を使用して、参照テーブルに接続します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-136">The Term Extraction transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="cca4f-137">詳細については、「 [OLE DB 接続マネージャー](../../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cca4f-137">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="cca4f-138">用語抽出変換は、完全な事前キャッシュ モードで動作します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-138">The Term Extraction transformation works in a fully precached mode.</span></span> <span data-ttu-id="cca4f-139">用語抽出変換は、実行時に参照テーブルの除外用語を読み取って独自のメモリに格納してから、変換入力行を処理します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-139">At run time, the Term Extraction transformation reads the exclusion terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
## <a name="extraction-of-terms-from-text"></a><span data-ttu-id="cca4f-140">テキストからの用語の抽出</span><span class="sxs-lookup"><span data-stu-id="cca4f-140">Extraction of Terms from Text</span></span>  
 <span data-ttu-id="cca4f-141">用語抽出変換は、テキストから用語を抽出するために次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-141">To extract terms from text, the Term Extraction transformation performs the following tasks.</span></span>  
  
### <a name="identification-of-words"></a><span data-ttu-id="cca4f-142">単語の識別</span><span class="sxs-lookup"><span data-stu-id="cca4f-142">Identification of Words</span></span>  
 <span data-ttu-id="cca4f-143">最初に、用語抽出変換は次のタスクを実行することによって単語を識別します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-143">First, the Term Extraction transformation identifies words by performing the following tasks:</span></span>  
  
-   <span data-ttu-id="cca4f-144">スペース、改行、および英語のその他のターミネータを使用して、テキストを単語に分割します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-144">Separating text into words by using spaces, line breaks, and other word terminators in the English language.</span></span> <span data-ttu-id="cca4f-145">たとえば、 *?* や</span><span class="sxs-lookup"><span data-stu-id="cca4f-145">For example, punctuation marks such as *?*</span></span> <span data-ttu-id="cca4f-146">*:* などの句読点は、単語を区切るための文字です。</span><span class="sxs-lookup"><span data-stu-id="cca4f-146">and *:* are word-breaking characters.</span></span>  
  
-   <span data-ttu-id="cca4f-147">ハイフンまたはアンダースコアでつながれている単語を保持します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-147">Preserving words that are connected by hyphens or underscores.</span></span> <span data-ttu-id="cca4f-148">たとえば、 *copy-protected* および *read-only* は、1 単語のまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-148">For example, the words *copy-protected* and *read-only* remain one word.</span></span>  
  
-   <span data-ttu-id="cca4f-149">ピリオドを含む頭字語をそのまま残します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-149">Keeping intact acronyms that include periods.</span></span> <span data-ttu-id="cca4f-150">たとえば、 *A.B.C* Company は、 **ABC** および **Company**としてトークン化されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-150">For example, the *A.B.C* Company would be tokenized as **ABC** and **Company**.</span></span>  
  
-   <span data-ttu-id="cca4f-151">特殊文字の箇所で単語を分割します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-151">Splitting words on special characters.</span></span> <span data-ttu-id="cca4f-152">たとえば、単語 *date/time* は *date* および *time*として、 *(bicycle)* は *bicycle*としてそれぞれ抽出され、さらに、C# は C として扱われます。特殊文字は破棄され、語彙化できません。</span><span class="sxs-lookup"><span data-stu-id="cca4f-152">For example, the word *date/time* is extracted as *date* and *time*, *(bicycle)* as *bicycle*, and C# is treated as C. Special characters are discarded and cannot be lexicalized.</span></span>  
  
-   <span data-ttu-id="cca4f-153">アポストロフィなどの特殊文字が単語を分割しない場合を認識します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-153">Recognizing when special characters such as the apostrophe should not split words.</span></span> <span data-ttu-id="cca4f-154">たとえば、単語 *bicycle's* は、2 つの単語に分割されず、1 つの用語 *bicycle* (名詞) になります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-154">For example, the word *bicycle's* is not split into two words, and yields the single term *bicycle* (noun).</span></span>  
  
-   <span data-ttu-id="cca4f-155">時刻式、金額式、電子メール アドレス、および住所を分割します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-155">Splitting time expressions, monetary expressions, e-mail addresses, and postal addresses.</span></span> <span data-ttu-id="cca4f-156">たとえば、日付 *January 31, 2004* は、 *January*、 *31*、および *2004*の 3 つのトークンに分割されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-156">For example, the date *January 31, 2004* is separated into the three tokens *January*, *31*, and *2004*.</span></span>  
  
### <a name="tagged-words"></a><span data-ttu-id="cca4f-157">タグ付きの単語</span><span class="sxs-lookup"><span data-stu-id="cca4f-157">Tagged Words</span></span>  
 <span data-ttu-id="cca4f-158">次に、用語抽出変換は、次のいずれかの品詞として単語をタグ付けします。</span><span class="sxs-lookup"><span data-stu-id="cca4f-158">Second, the Term Extraction transformation tags words as one of the following parts of speech:</span></span>  
  
-   <span data-ttu-id="cca4f-159">単数形の名詞。</span><span class="sxs-lookup"><span data-stu-id="cca4f-159">A noun in the singular form.</span></span> <span data-ttu-id="cca4f-160">たとえば、 *bicycle* や *potato*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-160">For example, *bicycle* and *potato*.</span></span>  
  
-   <span data-ttu-id="cca4f-161">複数形の名詞。</span><span class="sxs-lookup"><span data-stu-id="cca4f-161">A noun in the plural form.</span></span> <span data-ttu-id="cca4f-162">たとえば、 *bicycles* や *potatoes*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-162">For example, *bicycles* and *potatoes*.</span></span> <span data-ttu-id="cca4f-163">見出し語化されていないすべての複数形の名詞は、語幹を抽出されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-163">All plural nouns that are not lemmatized are subject to stemming.</span></span>  
  
-   <span data-ttu-id="cca4f-164">単数形の固有名詞。</span><span class="sxs-lookup"><span data-stu-id="cca4f-164">A proper noun in the singular form.</span></span> <span data-ttu-id="cca4f-165">たとえば、 *April* や *Peter*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-165">For example, *April* and *Peter*.</span></span>  
  
-   <span data-ttu-id="cca4f-166">複数形の固有名詞。</span><span class="sxs-lookup"><span data-stu-id="cca4f-166">A proper noun in the plural form.</span></span> <span data-ttu-id="cca4f-167">たとえば、 *Aprils* や *Peters*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-167">For example *Aprils* and *Peters*.</span></span> <span data-ttu-id="cca4f-168">固有名詞の語幹を抽出するには、標準的な英単語に限定されている内部辞書に固有名詞が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-168">For a proper noun to be subject to stemming, it must be a part of the internal lexicon, which is limited to standard English words.</span></span>  
  
-   <span data-ttu-id="cca4f-169">形容詞。</span><span class="sxs-lookup"><span data-stu-id="cca4f-169">An adjective.</span></span> <span data-ttu-id="cca4f-170">たとえば、 *blue*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-170">For example, *blue*.</span></span>  
  
-   <span data-ttu-id="cca4f-171">2 つのものを比較する、比較級の形容詞。</span><span class="sxs-lookup"><span data-stu-id="cca4f-171">A comparative adjective that compares two things.</span></span> <span data-ttu-id="cca4f-172">たとえば、 *higher* や *taller*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-172">For example, *higher* and *taller*.</span></span>  
  
-   <span data-ttu-id="cca4f-173">少なくとも 3 つ以上のものを比較し、そのうちで最も上位または最も下位のものを識別する、最上級の形容詞。</span><span class="sxs-lookup"><span data-stu-id="cca4f-173">A superlative adjective that identifies a thing that has a quality above or below the level of at least two others.</span></span> <span data-ttu-id="cca4f-174">たとえば、 *highest* や *tallest*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-174">For example, *highest* and *tallest*.</span></span>  
  
-   <span data-ttu-id="cca4f-175">数字。</span><span class="sxs-lookup"><span data-stu-id="cca4f-175">A number.</span></span> <span data-ttu-id="cca4f-176">たとえば、 *62* や *2004*などです。</span><span class="sxs-lookup"><span data-stu-id="cca4f-176">For example, *62* and *2004*.</span></span>  
  
 <span data-ttu-id="cca4f-177">これらの品詞に含まれない単語は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-177">Words that are not one of these parts of speech are discarded.</span></span> <span data-ttu-id="cca4f-178">たとえば、動詞や代名詞は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-178">For example, verbs and pronouns are discarded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cca4f-179">品詞のタグ付けは統計モデルに基づいており、タグ付けが完全に正確でない場合があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-179">The tagging of parts of speech is based on a statistical model and the tagging may not be completely accurate.</span></span>  
  
 <span data-ttu-id="cca4f-180">用語抽出変換が名詞のみを抽出するように構成されている場合、名詞および固有名詞の単数形または複数形としてタグ付けされている単語のみが抽出されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-180">If the Term Extraction transformation is configured to extract only nouns, only the words that are tagged as singular or plural forms of nouns and proper nouns are extracted.</span></span>  
  
 <span data-ttu-id="cca4f-181">用語抽出変換が名詞句のみを抽出するように構成されている場合、名詞、固有名詞、形容詞、および数字としてタグ付けされている単語が組み合わされて名詞句となります。ただし名詞句には、名詞または固有名詞の単数形または複数形としてタグ付けされた単語が、少なくとも 1 つは含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-181">If the Term Extraction transformation is configured to extract only noun phrases, words that are tagged as nouns, proper nouns, adjectives, and numbers may be combined to make a noun phrase, but the phrase must include at least one word that is tagged as a singular or plural form of a noun or a proper noun.</span></span> <span data-ttu-id="cca4f-182">たとえば、名詞句 *highest mountain* は、最上級の形容詞としてタグ付けされた単語 (*highest*) と、名詞としてタグ付けされた単語 (*mountain*) が組み合わされています。</span><span class="sxs-lookup"><span data-stu-id="cca4f-182">For example, the noun phrase *highest mountain* combines a word tagged as a superlative adjective (*highest*) and a word tagged as noun (*mountain*).</span></span>  
  
 <span data-ttu-id="cca4f-183">用語抽出が名詞と名詞句の両方を抽出するように構成されている場合、名詞の規則と名詞句の規則の両方が適用されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-183">If the Term Extraction is configured to extract both nouns and noun phrases, both the rules for nouns and the rules for noun phrases apply.</span></span> <span data-ttu-id="cca4f-184">たとえば、変換はテキスト *many beautiful blue bicycles* から、 *bicycle* と *beautiful blue bicycle*を抽出します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-184">For example, the transformation extracts *bicycle* and *beautiful blue bicycle* from the text *many beautiful blue bicycles*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cca4f-185">抽出された用語には、変換が使用する用語の最大長と頻度のしきい値がそのまま適用されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-185">The extracted terms remain subject to the maximum term length and frequency threshold that the transformation uses.</span></span>  
  
### <a name="stemmed-words"></a><span data-ttu-id="cca4f-186">語幹選択された単語</span><span class="sxs-lookup"><span data-stu-id="cca4f-186">Stemmed Words</span></span>  
 <span data-ttu-id="cca4f-187">また、用語抽出変換は名詞の語幹のみを使用し、名詞の単数形のみを抽出します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-187">The Term Extraction transformation also stems nouns to extract only the singular form of a noun.</span></span> <span data-ttu-id="cca4f-188">たとえば、 *men* から *man*、 *mice* から *mouse*、および *bicycles* から *bicycle*が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-188">For example, the transformation extracts *man* from *men*, *mouse* from *mice*, and *bicycle* from *bicycles*.</span></span> <span data-ttu-id="cca4f-189">この変換は、名詞の語幹を抽出する際に独自の辞書を使用します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-189">The transformation uses its dictionary to stem nouns.</span></span> <span data-ttu-id="cca4f-190">動名詞は、辞書にある場合は名詞として扱われます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-190">Gerunds are treated as nouns if they are in the dictionary.</span></span>  
  
 <span data-ttu-id="cca4f-191">さらに、用語抽出変換では、用語抽出変換の内部辞書を使用して、次の例で示すように辞書形式の単語の語幹を選択します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-191">The Term Extraction transformation stems words to their dictionary form as shown in these examples by using the dictionary internal to the Term Extraction transformation.</span></span>  
  
-   <span data-ttu-id="cca4f-192">名詞から *s* を削除します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-192">Removing *s* from nouns.</span></span> <span data-ttu-id="cca4f-193">たとえば、 *bicycles* は *bicycle*になります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-193">For example, *bicycles* becomes *bicycle*.</span></span>  
  
-   <span data-ttu-id="cca4f-194">名詞から *es* を削除します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-194">Removing *es* from nouns.</span></span> <span data-ttu-id="cca4f-195">たとえば、 *stories* は *story*になります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-195">For example, *stories* becomes *story*.</span></span>  
  
-   <span data-ttu-id="cca4f-196">不規則名詞の単数形を、辞書から取得します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-196">Retrieving the singular form for irregular nouns from the dictionary.</span></span> <span data-ttu-id="cca4f-197">たとえば、 *geese* は *goose*になります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-197">For example, *geese* becomes *goose*.</span></span>  
  
### <a name="normalized-words"></a><span data-ttu-id="cca4f-198">正規化された単語</span><span class="sxs-lookup"><span data-stu-id="cca4f-198">Normalized Words</span></span>  
 <span data-ttu-id="cca4f-199">用語抽出変換は、文における位置だけが理由で大文字になっている用語を正規化し、代わりに小文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-199">The Term Extraction transformation normalizes terms that are capitalized only because of their position in a sentence, and uses their non-capitalized form instead.</span></span> <span data-ttu-id="cca4f-200">たとえば、句 *Dogs chase cats* および *Mountain paths are steep*において、 *Dogs* および *Mountain* は、 *dog* および *mountain*に正規化されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-200">For example, in the phrases *Dogs chase cats* and *Mountain paths are steep*, *Dogs* and *Mountain* would be normalized to *dog* and *mountain*.</span></span>  
  
 <span data-ttu-id="cca4f-201">用語抽出変換は単語を正規化するため、大文字または小文字で表記された単語は、異なる用語としては扱われません。</span><span class="sxs-lookup"><span data-stu-id="cca4f-201">The Term Extraction transformation normalizes words so that the capitalized and noncapitalized versions of words are not treated as different terms.</span></span> <span data-ttu-id="cca4f-202">たとえば、 *You see many bicycles in Seattle* および *Bicycles are blue*のテキストにおいて、 *bicycles* と *Bicycles* は同じ用語として認識され、変換は *bicycle*のみを保持します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-202">For example, in the text *You see many bicycles in Seattle* and *Bicycles are blue*, *bicycles* and *Bicycles* are recognized as the same term and the transformation keeps only *bicycle*.</span></span> <span data-ttu-id="cca4f-203">内部辞書の一覧にない固有名詞と単語は、正規化されません。</span><span class="sxs-lookup"><span data-stu-id="cca4f-203">Proper nouns and words that are not listed in the internal dictionary are not normalized.</span></span>  
  
### <a name="case-sensitive-normalization"></a><span data-ttu-id="cca4f-204">大文字と小文字を区別する正規化</span><span class="sxs-lookup"><span data-stu-id="cca4f-204">Case-Sensitive Normalization</span></span>  
 <span data-ttu-id="cca4f-205">用語抽出変換は、大文字と小文字の単語を別個の用語と見なすか、または同一用語の変形として見なすように構成できます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-205">The Term Extraction transformation can be configured to consider lowercase and uppercase words as either distinct terms, or as different variants of the same term.</span></span>  
  
-   <span data-ttu-id="cca4f-206">大文字と小文字を区別するように変換を構成した場合、 *Method* および *method* などのような用語は、2 つの異なる用語として抽出されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-206">If the transformation is configured to recognize differences in case, terms like *Method* and *method* are extracted as two different terms.</span></span> <span data-ttu-id="cca4f-207">文の最初にない大文字の単語は正規化されず、固有名詞としてタグ付けされます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-207">Capitalized words that are not the first word in a sentence are never normalized, and are tagged as proper nouns.</span></span>  
  
-   <span data-ttu-id="cca4f-208">大文字と小文字を区別しないように変換を構成した場合、 *Method* および *method* などのような用語は、1 つの単語の変形として認識されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-208">If the transformation is configured to be case-insensitive, terms like *Method* and *method* are recognized as variants of a single term.</span></span> <span data-ttu-id="cca4f-209">入力データセットで最初に出現した単語に応じて、 *Method* または *method*のどちらかが、抽出された用語の一覧に含まれます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-209">The list of extracted terms might include either *Method* or *method*, depending on which word occurs first in the input data set.</span></span> <span data-ttu-id="cca4f-210">*Method* が、文の最初の単語であることのみの理由で大文字になっている場合は、正規化された形式で抽出されます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-210">If *Method* is capitalized only because it is the first word in a sentence, it is extracted in normalized form.</span></span>  
  
## <a name="sentence-and-word-boundaries"></a><span data-ttu-id="cca4f-211">文および単語の境界</span><span class="sxs-lookup"><span data-stu-id="cca4f-211">Sentence and Word Boundaries</span></span>  
 <span data-ttu-id="cca4f-212">用語抽出変換は、次の文字を文の境界として使用することにより、テキストを文に分割します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-212">The Term Extraction transformation separates text into sentences using the following characters as sentence boundaries:</span></span>  
  
-   <span data-ttu-id="cca4f-213">ASCII 改行文字の 0x0d (キャリッジ リターン) および 0x0a (ライン フィード)。</span><span class="sxs-lookup"><span data-stu-id="cca4f-213">ASCII line-break characters 0x0d (carriage return) and 0x0a (line feed).</span></span> <span data-ttu-id="cca4f-214">この文字を文の境界として使用するには、1 行に 2 文字以上の改行文字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-214">To use this character as a sentence boundary, there must be two or more line-break characters in a row.</span></span>  
  
-   <span data-ttu-id="cca4f-215">ハイフン (–)。</span><span class="sxs-lookup"><span data-stu-id="cca4f-215">Hyphens (-).</span></span> <span data-ttu-id="cca4f-216">この文字を文の境界として使用するには、アンダースコアが左右の文字の間に挟まれていないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="cca4f-216">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="cca4f-217">アンダースコア (_)。</span><span class="sxs-lookup"><span data-stu-id="cca4f-217">Underscore (_).</span></span> <span data-ttu-id="cca4f-218">この文字を文の境界として使用するには、アンダースコアが左右の文字の間に挟まれていないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="cca4f-218">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="cca4f-219">0x19 以下または 0x7b 以上のすべての Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="cca4f-219">All Unicode characters that are less than or equal to 0x19, or greater than or equal to 0x7b.</span></span>  
  
-   <span data-ttu-id="cca4f-220">数字、句読点、および英文字の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="cca4f-220">Combinations of numbers, punctuation marks, and alphabetical characters.</span></span> <span data-ttu-id="cca4f-221">たとえば、 *A23B#99* は、用語 *A23B*を返します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-221">For example, *A23B#99* returns the term *A23B*.</span></span>  
  
-   <span data-ttu-id="cca4f-222">%、@、&、$、#、\*、:、;、.、 **、** 、!、?、\<, >、+、=、^、~、|、\\、/、(、)、[、]、{、}、"、' 文字。</span><span class="sxs-lookup"><span data-stu-id="cca4f-222">The characters, %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cca4f-223">1 つ以上のピリオド (.) が含まれる頭字語は、複数の文に分割されません。</span><span class="sxs-lookup"><span data-stu-id="cca4f-223">Acronyms that include one or more periods (.) are not separated into multiple sentences.</span></span>  
  
 <span data-ttu-id="cca4f-224">次に、用語抽出変換は、次の単語の境界を使用して、文を単語に分割します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-224">The Term Extraction transformation then separates the sentence into words using the following word boundaries:</span></span>  
  
-   <span data-ttu-id="cca4f-225">Space</span><span class="sxs-lookup"><span data-stu-id="cca4f-225">Space</span></span>  
  
-   <span data-ttu-id="cca4f-226">タブ</span><span class="sxs-lookup"><span data-stu-id="cca4f-226">Tab</span></span>  
  
-   <span data-ttu-id="cca4f-227">ASCII 0x0d (キャリッジ リターン)</span><span class="sxs-lookup"><span data-stu-id="cca4f-227">ASCII 0x0d (carriage return)</span></span>  
  
-   <span data-ttu-id="cca4f-228">ASCII 0x0a (ライン フィード)</span><span class="sxs-lookup"><span data-stu-id="cca4f-228">ASCII 0x0a (line feed)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cca4f-229">アポストロフィが、 *we're* や *it's*などの短縮形の単語に含まれている場合、単語はアポストロフィの位置で分けられます。それ以外の場合、アポストロフィに続く文字は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="cca4f-229">If an apostrophe is in a word that is a contraction, such as *we're* or *it's*, the word is broken at the apostrophe; otherwise, the letters following the apostrophe are trimmed.</span></span> <span data-ttu-id="cca4f-230">たとえば、 *we're* は *we* と *'re*に分割され、 *bicycle's* は切り捨てられて *bicycle*になります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-230">For example, *we're* is split into *we* and *'re*, and *bicycle's* is trimmed to *bicycle*.</span></span>  
  
## <a name="configuration-of-the-term-extraction-transformation"></a><span data-ttu-id="cca4f-231">用語抽出変換の構成</span><span class="sxs-lookup"><span data-stu-id="cca4f-231">Configuration of the Term Extraction Transformation</span></span>  
 <span data-ttu-id="cca4f-232">用語抽出変換は、内部アルゴリズムと統計モデルを使用して変換結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-232">The Text Extraction transformation uses internal algorithms and statistical models to generate its results.</span></span> <span data-ttu-id="cca4f-233">用語抽出変換を複数回実行して結果を検証し、テキスト マイニング ソリューションに役立つ種類の結果を生成するように変換を構成する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-233">You may have to run the Term Extraction transformation several times and examine the results to configure the transformation to generate the type of results that works for your text mining solution.</span></span>  
  
 <span data-ttu-id="cca4f-234">用語抽出変換は、1 つの標準入力、1 つの出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="cca4f-234">The Term Extraction transformation has one regular input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="cca4f-235">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="cca4f-235">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cca4f-236">**[用語抽出変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cca4f-236">For more information about the properties that you can set in the **Term Extraction Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="cca4f-237">[[用語抽出変換エディター] &#40;[用語抽出] タブ&#41;](../../term-extraction-transformation-editor-term-extraction-tab.md)</span><span class="sxs-lookup"><span data-stu-id="cca4f-237">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../term-extraction-transformation-editor-term-extraction-tab.md)</span></span>  
  
-   <span data-ttu-id="cca4f-238">[[用語抽出変換エディター] &#40;[除外] タブ&#41;](../../term-extraction-transformation-editor-exclusion-tab.md)</span><span class="sxs-lookup"><span data-stu-id="cca4f-238">[Term Extraction Transformation Editor &#40;Exclusion Tab&#41;](../../term-extraction-transformation-editor-exclusion-tab.md)</span></span>  
  
-   <span data-ttu-id="cca4f-239">[[用語抽出変換エディター] &#40;[詳細設定] タブ&#41;](../../term-extraction-transformation-editor-advanced-tab.md)</span><span class="sxs-lookup"><span data-stu-id="cca4f-239">[Term Extraction Transformation Editor &#40;Advanced Tab&#41;](../../term-extraction-transformation-editor-advanced-tab.md)</span></span>  
  
 <span data-ttu-id="cca4f-240">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cca4f-240">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cca4f-241">Common Properties</span><span class="sxs-lookup"><span data-stu-id="cca4f-241">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="cca4f-242">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="cca4f-242">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="cca4f-243">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cca4f-243">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
