---
title: 検索値を入力するときの規則 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], searches
- date searches
- dates [SQL Server], searches
- embedding apostrophes [SQL Server]
- logical value searches [SQL Server]
- case-sensitive search matches
- search criteria [SQL Server], rules
- text value searches [SQL Server]
- numeric value searches [SQL Server]
ms.assetid: 3c8134b7-83f4-41b4-99c8-e3949a685ff5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 907bcac93863bc5660993e910b37e25e25a129b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632256"
---
# <a name="rules-for-entering-search-values-visual-database-tools"></a><span data-ttu-id="e97e9-102">検索値を入力するときの規則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e97e9-102">Rules for Entering Search Values (Visual Database Tools)</span></span>
  <span data-ttu-id="e97e9-103">このトピックでは、検索条件に対して次の種類のリテラル値を入力するときに従う規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="e97e9-103">This topic discusses the conventions you must use when entering the following types of literal values for a search condition:</span></span>  
  
-   <span data-ttu-id="e97e9-104">文字列値</span><span class="sxs-lookup"><span data-stu-id="e97e9-104">Text values</span></span>  
  
-   <span data-ttu-id="e97e9-105">数値</span><span class="sxs-lookup"><span data-stu-id="e97e9-105">Numeric values</span></span>  
  
-   <span data-ttu-id="e97e9-106">日付</span><span class="sxs-lookup"><span data-stu-id="e97e9-106">Dates</span></span>  
  
-   <span data-ttu-id="e97e9-107">論理値</span><span class="sxs-lookup"><span data-stu-id="e97e9-107">Logical values</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e97e9-108">このトピックの情報は、標準の SQL-92 に対する規則に基づいていますが、</span><span class="sxs-lookup"><span data-stu-id="e97e9-108">The information in this topic is derived from the rules for standard SQL-92.</span></span> <span data-ttu-id="e97e9-109">各データベースは SQL を独自の方法で実装している場合があります。</span><span class="sxs-lookup"><span data-stu-id="e97e9-109">However, each database can implement SQL in its own way.</span></span> <span data-ttu-id="e97e9-110">したがって、ここに示すガイドラインはすべての場合に当てはまるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e97e9-110">Therefore, the guidelines provided here might not apply in every case.</span></span> <span data-ttu-id="e97e9-111">特定のデータベースでの検索値の入力方法に関して不明な点がある場合は、使用しているデータベースのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e97e9-111">If you have questions about how to enter search values for a particular database, refer to the documentation for the database that you are using.</span></span>  
  
## <a name="searching-on-text-values"></a><span data-ttu-id="e97e9-112">文字列値の検索</span><span class="sxs-lookup"><span data-stu-id="e97e9-112">Searching on Text Values</span></span>  
 <span data-ttu-id="e97e9-113">次の規則は、検索条件に文字列値を入力するときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-113">The following guidelines apply when you enter text values in search conditions:</span></span>  
  
-   <span data-ttu-id="e97e9-114">**引用符** : 次に示す姓の例のように、文字列値は単一引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-114">**Quotation marks** Enclose text values in single quotation marks, as in this example for a last name:</span></span>  
  
    ```  
    'Smith'  
    ```  
  
     <span data-ttu-id="e97e9-115">[抽出条件ペイン](visual-database-tools.md)で検索条件を入力する場合は、単に文字列値を入力するだけです。クエリおよびビュー デザイナーにより、自動的に単一引用符が付加されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-115">If you are entering a search condition in the [Criteria Pane](visual-database-tools.md), you can simply type the text value and the Query and View Designer will automatically put single quotation marks around it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e97e9-116">一部のデータベースでは、単一引用符で囲まれた項目がリテラル値として解釈され、二重引用符で囲まれた項目が列やテーブル参照などのデータベース オブジェクトとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-116">In some databases, terms in single quotation marks are interpreted as literal values, whereas terms in double quotation marks are interpreted as database objects such as column or table references.</span></span> <span data-ttu-id="e97e9-117">このため、クエリおよびビュー デザイナーでは二重引用符で囲まれた項目も受け入れることができますが、その項目が期待どおりに解釈されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="e97e9-117">Therefore, even though the Query and View Designer can accept terms in double quotation marks, it might interpret them differently than you expect.</span></span>  
  
-   <span data-ttu-id="e97e9-118">**アポストロフィの埋め込み** : 検索するデータに単一引用符 (アポストロフィ) が含まれる場合は、その単一引用符が区切り記号でなくリテラル値であることを示すために、2 つの単一引用符を入力します。</span><span class="sxs-lookup"><span data-stu-id="e97e9-118">**Embedding apostrophes** If the data you are searching for contains a single quotation mark (an apostrophe), you can enter two single quotation marks to indicate that you mean the single quotation mark as a literal value and not a delimiter.</span></span> <span data-ttu-id="e97e9-119">たとえば、次の条件は "Swann's Way" という値を検索します。</span><span class="sxs-lookup"><span data-stu-id="e97e9-119">For example, the following condition searches for the value "Swann's Way:"</span></span>  
  
    ```  
    ='Swann''s Way'  
    ```  
  
-   <span data-ttu-id="e97e9-120">**長さの制限** : 長い文字列を入力するときには、データベースにおける SQL ステートメントの最大長を超えないようにします。</span><span class="sxs-lookup"><span data-stu-id="e97e9-120">**Length limits** Do not exceed the maximum length of the SQL statement for your database when entering long strings.</span></span>  
  
-   <span data-ttu-id="e97e9-121">**大文字小文字の区別** : 使用しているデータベースの大文字小文字の区別の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="e97e9-121">**Case sensitivity** Follow the case sensitivity rules for the database you are using.</span></span> <span data-ttu-id="e97e9-122">使用しているデータベースによって、文字列の検索で大文字小文字が区別されるかどうかが異なります。</span><span class="sxs-lookup"><span data-stu-id="e97e9-122">The database you are using determines whether text searches are case sensitive.</span></span> <span data-ttu-id="e97e9-123">たとえば、あるデータベースでは演算子 "=" は厳密に大文字小文字を区別した一致を意味しますが、別のデータベースでは大文字と小文字の任意の組み合わせの一致が許されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-123">For example, some databases interpret the operator "=" to mean an exact case-sensitive match, but others will allow matches on any combination of uppercase and lowercase characters.</span></span>  
  
     <span data-ttu-id="e97e9-124">データベースで大文字小文字が区別して検索されるかどうかがわからない場合は、次の例に示すように、検索条件で UPPER 関数または LOWER 関数を使用して検索データを大文字または小文字に変換してください。</span><span class="sxs-lookup"><span data-stu-id="e97e9-124">If you are unsure about whether the database uses a case-sensitive search, you can use the UPPER or LOWER functions in the search condition to convert the case of the search data, as illustrated in the following example:</span></span>  
  
    ```  
    WHERE UPPER(lname) = 'SMITH'  
    ```  
  
## <a name="searching-on-numeric-values"></a><span data-ttu-id="e97e9-125">数値の検索</span><span class="sxs-lookup"><span data-stu-id="e97e9-125">Searching on Numeric Values</span></span>  
 <span data-ttu-id="e97e9-126">次の規則は、検索条件に数値を入力するときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-126">The following guidelines apply when you enter numeric values in search conditions:</span></span>  
  
-   <span data-ttu-id="e97e9-127">**引用符** : 数値は引用符で囲まないでください。</span><span class="sxs-lookup"><span data-stu-id="e97e9-127">**Quotation marks** Do not enclose numbers in quotation marks.</span></span>  
  
-   <span data-ttu-id="e97e9-128">**数値以外の文字** : 小数点記号 (Windows コントロール パネルの **[地域のオプション]** ダイアログ ボックスで定義) と負の符号 (-) を除き、非数値文字を入力することはできません。</span><span class="sxs-lookup"><span data-stu-id="e97e9-128">**Non-numeric characters** Do not include non-numeric characters except the decimal separator (as defined in the **Regional Settings** dialog box of Windows Control Panel) and negative sign (-).</span></span> <span data-ttu-id="e97e9-129">桁区切り記号 (3 桁ごとに挿入されるコンマなど) や通貨記号を入力することはできません。</span><span class="sxs-lookup"><span data-stu-id="e97e9-129">Do not include digit grouping symbols (such as a comma between thousands) or currency symbols.</span></span>  
  
-   <span data-ttu-id="e97e9-130">**小数点** : 数を入力するときは、検索する値が整数か実数かに関係なく、小数点を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-130">**Decimal marks** If you are entering whole numbers, you can include a decimal mark, whether the value you are searching for is an integer or a real number.</span></span>  
  
-   <span data-ttu-id="e97e9-131">**指数表記** : 非常に大きな数や非常に小さな数は、次の例のように指数表記で入力できます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-131">**Scientific notation** You can enter very large or very small numbers using scientific notation, as in this example:</span></span>  
  
    ```  
    > 1.23456e-9  
    ```  
  
## <a name="searching-on-dates"></a><span data-ttu-id="e97e9-132">日付の検索</span><span class="sxs-lookup"><span data-stu-id="e97e9-132">Searching on Dates</span></span>  
 <span data-ttu-id="e97e9-133">日付を入力するときに使用する形式は、使用しているデータベースによって異なります。また、クエリおよびビュー デザイナーのどのペインに日付を入力するかによっても異なります。</span><span class="sxs-lookup"><span data-stu-id="e97e9-133">The format you use to enter dates depends on the database you are using and in what pane of the Query and View Designer you are entering the date.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e97e9-134">データ ソースが使用している形式が不明な場合は、抽出条件ペインのフィルター列に任意の形式で日付を入力してください。</span><span class="sxs-lookup"><span data-stu-id="e97e9-134">If you don't know which format your data source uses, type a date into the filter column of the Criteria pane in any format familiar to you.</span></span> <span data-ttu-id="e97e9-135">クエリおよびビュー デザイナーは、このような入力のほとんどを適切な形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="e97e9-135">The designer will convert most of such entries into the appropriate format.</span></span>  
  
 <span data-ttu-id="e97e9-136">クエリおよびビュー デザイナーは、次の日付形式を処理できます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-136">The Query and View Designer can work with the following date formats:</span></span>  
  
-   <span data-ttu-id="e97e9-137">**ロケール固有** : Windows の **[地域のオプション]** ダイアログ ボックスで指定された日付の形式。</span><span class="sxs-lookup"><span data-stu-id="e97e9-137">**Locale-specific** The format specified for dates in the **Windows Regional Settings Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="e97e9-138">**データベース固有** : データベースによって認識される任意の形式。</span><span class="sxs-lookup"><span data-stu-id="e97e9-138">**Database-specific** Any format understood by the database.</span></span>  
  
-   <span data-ttu-id="e97e9-139">**ANSI 標準日付** : 次の例のように、中かっこ ({})、日付を指定するマーカー 'd'、および日付の文字列を使用する形式。</span><span class="sxs-lookup"><span data-stu-id="e97e9-139">**ANSI standard date** A format that uses braces, the marker 'd' to designate the date, and a date string, as in the following example:</span></span>  
  
    ```  
    { d '1990-12-31' }  
    ```  
  
-   <span data-ttu-id="e97e9-140">**ANSI 標準日付/時刻** : ANSI 標準日付に似ていますが、'd' の代わりに 'ts' を使用し、日付に時、分、秒 (24 時間表記) を付加します。1990 年 12 月 31 日の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e97e9-140">**ANSI standard datetime** Similar to ANSI-standard date, but uses 'ts' instead of 'd' and adds hours, minutes, and seconds to the date (using a 24-hour clock), as in this example for December 31, 1990:</span></span>  
  
    ```  
    { ts '1990-12-31 00:00:00' }  
    ```  
  
     <span data-ttu-id="e97e9-141">一般に、通常の日付型を使用して日付を表現するデータベースでは、ANSI 標準の日付形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-141">In general, the ANSI standard date format is used with databases that represent dates using a true date data type.</span></span> <span data-ttu-id="e97e9-142">一方、datetime データ型をサポートするデータベースでは、datetime 形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-142">In contrast, the datetime format is used with databases that support a datetime data type.</span></span>  
  
 <span data-ttu-id="e97e9-143">次の表は、クエリおよびビュー デザイナーの各ペインで使用できる日付形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="e97e9-143">The following table summarizes the date format that you can use in different panes of the Query and View Designer.</span></span>  
  
|<span data-ttu-id="e97e9-144">**ペイン**</span><span class="sxs-lookup"><span data-stu-id="e97e9-144">**Pane**</span></span>|<span data-ttu-id="e97e9-145">**日付形式**</span><span class="sxs-lookup"><span data-stu-id="e97e9-145">**Date format**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="e97e9-146">条件</span><span class="sxs-lookup"><span data-stu-id="e97e9-146">Criteria</span></span>|<span data-ttu-id="e97e9-147">ロケール固有&#x2028;データベース固有&#x2028;ANSI 標準</span><span class="sxs-lookup"><span data-stu-id="e97e9-147">Locale-specific Database-specific ANSI standard</span></span><br /><br /> <span data-ttu-id="e97e9-148">[抽出条件ペイン](visual-database-tools.md) で入力された日付は、SQL ペインではデータベース互換の形式に変換されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-148">Dates entered in the [Criteria Pane](visual-database-tools.md) are converted to a database-compatible format in the SQL pane.</span></span>|  
|<span data-ttu-id="e97e9-149">SQL</span><span class="sxs-lookup"><span data-stu-id="e97e9-149">SQL</span></span>|<span data-ttu-id="e97e9-150">データベース固有&#x2028;ANSI 標準</span><span class="sxs-lookup"><span data-stu-id="e97e9-150">Database-specific ANSI standard</span></span>|  
|<span data-ttu-id="e97e9-151">[結果]</span><span class="sxs-lookup"><span data-stu-id="e97e9-151">Results</span></span>|<span data-ttu-id="e97e9-152">ロケール固有</span><span class="sxs-lookup"><span data-stu-id="e97e9-152">Locale-specific</span></span>|  
  
## <a name="searching-on-logical-values"></a><span data-ttu-id="e97e9-153">論理値の検索</span><span class="sxs-lookup"><span data-stu-id="e97e9-153">Searching on Logical Values</span></span>  
 <span data-ttu-id="e97e9-154">論理データの形式はデータベースごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="e97e9-154">The format of logical data varies from database to database.</span></span> <span data-ttu-id="e97e9-155">多くのデータベースで、False の値はゼロ (0) として格納されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-155">Very frequently, a value of False is stored as zero (0).</span></span> <span data-ttu-id="e97e9-156">多くのデータベースでは、True の値は 1 として格納されます。ただし、True の値を -1 として格納するデータベースもあります。</span><span class="sxs-lookup"><span data-stu-id="e97e9-156">A value of True is most frequently stored as 1 and occasionally as -1.</span></span> <span data-ttu-id="e97e9-157">検索条件に論理値を入力するときには、次のガイドラインが適用されます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-157">The following guidelines apply when you enter logical values in search conditions:</span></span>  
  
-   <span data-ttu-id="e97e9-158">False の値を検索する場合は、次の例のようにゼロを使用します。</span><span class="sxs-lookup"><span data-stu-id="e97e9-158">To search for a value of False, use a zero, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 0  
    ```  
  
-   <span data-ttu-id="e97e9-159">True の値を検索するときにどの形式を使用するかわからない場合は、次の例のように 1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="e97e9-159">If you are not sure what format to use when searching for a True value, try using 1, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 1  
    ```  
  
-   <span data-ttu-id="e97e9-160">または、次の例のように、ゼロでない任意の値を検索することで、検索のスコープを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="e97e9-160">Alternatively, you can broaden the scope of the search by searching for any non-zero value, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract <> 0  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e97e9-161">参照</span><span class="sxs-lookup"><span data-stu-id="e97e9-161">See Also</span></span>  
 [<span data-ttu-id="e97e9-162">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e97e9-162">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
