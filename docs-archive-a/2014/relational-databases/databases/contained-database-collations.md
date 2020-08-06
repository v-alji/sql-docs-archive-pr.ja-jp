---
title: 包含データベースの照合順序 | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- contained database, collations
ms.assetid: 4b44f6b9-2359-452f-8bb1-5520f2528483
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2648dbedea7708c4f39c922c56bba96cf38b0c0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718243"
---
# <a name="contained-database-collations"></a><span data-ttu-id="738d2-102">包含データベースの照合順序</span><span class="sxs-lookup"><span data-stu-id="738d2-102">Contained Database Collations</span></span>
  <span data-ttu-id="738d2-103">大文字と小文字の区別、アクセント記号の区別、使用されるベース言語など、さまざまなプロパティがテキスト データの並べ替え順序と等値セマンティクスに影響します。</span><span class="sxs-lookup"><span data-stu-id="738d2-103">Various properties affect the sort order and equality semantics of textual data, including case sensitivity, accent sensitivity, and the base language being used.</span></span> <span data-ttu-id="738d2-104">これらの性質の指定は、データの照合順序の選択を通じて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に示されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-104">These qualities are expressed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the choice of collation for the data.</span></span> <span data-ttu-id="738d2-105">照合順序の詳細については、「 [照合順序と Unicode のサポート](../collations/collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="738d2-105">For a more in-depth discussion of collations themselves, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="738d2-106">照合順序は、ユーザー テーブルに格納されているデータだけでなく、メタデータ、一時オブジェクト、変数名など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって処理されるすべてのテキストに適用されます。これらの処理は、包含データベースと非包含データベースとでは異なります。</span><span class="sxs-lookup"><span data-stu-id="738d2-106">Collations apply not only to data stored in user tables, but to all text handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including metadata, temporary objects, variable names, etc. The handling of these differs in contained and non-contained databases.</span></span> <span data-ttu-id="738d2-107">この変更は、多くのユーザーには影響しませんが、インスタンスに対する独立性と統一性を提供する助けになります。</span><span class="sxs-lookup"><span data-stu-id="738d2-107">This change will not affect many users, but helps provide instance independence and uniformity.</span></span> <span data-ttu-id="738d2-108">これも、包含データベースと非包含データベースの両方にアクセスするセッションの問題と同様に、いくつかの混乱を生じさせる場合があります。</span><span class="sxs-lookup"><span data-stu-id="738d2-108">But this may also cause some confusion, as well as problems for sessions that access both contained and non-contained databases.</span></span>  
  
 <span data-ttu-id="738d2-109">このトピックでは、変更の内容を明確にし、変更が問題を引き起こす状況について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="738d2-109">This topic clarifies the content of the change, and examines areas where the change may cause problems.</span></span>  
  
## <a name="non-contained-databases"></a><span data-ttu-id="738d2-110">非包含データベース</span><span class="sxs-lookup"><span data-stu-id="738d2-110">Non-Contained Databases</span></span>  
 <span data-ttu-id="738d2-111">すべてのデータベースには既定の照合順序があり、データベースの作成時または変更時に設定できます。</span><span class="sxs-lookup"><span data-stu-id="738d2-111">All databases have a default collation (which can be set when creating or altering a database.</span></span> <span data-ttu-id="738d2-112">この照合順序は、データベース内のすべての文字列型の列に対する既定値と同様に、データベース内のすべてのメタデータで使用されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-112">This collation is used for all metadata in the database, as well as the default for all string columns within the database.</span></span> <span data-ttu-id="738d2-113">ユーザーは、`COLLATE` 句を使用して、特定の列に対して別の照合順序を選択できます。</span><span class="sxs-lookup"><span data-stu-id="738d2-113">Users can choose a different collation for any particular column by using the `COLLATE` clause.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="738d2-114">例 1</span><span class="sxs-lookup"><span data-stu-id="738d2-114">Example 1</span></span>  
 <span data-ttu-id="738d2-115">たとえば、北京で作業する場合は、中国語の照合順序を使用するでしょう。</span><span class="sxs-lookup"><span data-stu-id="738d2-115">For example, if we were working in Beijing, we might use a Chinese collation:</span></span>  
  
```sql  
ALTER DATABASE MyDB COLLATE Chinese_Simplified_Pinyin_100_CI_AS;  
```  
  
 <span data-ttu-id="738d2-116">その場合、列を作成すると、既定の照合順序は中国語の照合順序になりますが、必要であれば別の照合順序を選択できます。</span><span class="sxs-lookup"><span data-stu-id="738d2-116">Now if we create a column, its default collation will be this Chinese collation, but we can choose another one if we want:</span></span>  
  
```sql  
CREATE TABLE MyTable  
      (mycolumn1 nvarchar,  
      mycolumn2 nvarchar COLLATE Frisian_100_CS_AS);  
GO  
SELECT name, collation_name  
FROM sys.columns  
WHERE name LIKE 'mycolumn%' ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```sql  
name            collation_name  
--------------- ----------------------------------  
mycolumn1       Chinese_Simplified_Pinyin_100_CI_AS  
mycolumn2       Frisian_100_CS_AS  
```  
  
 <span data-ttu-id="738d2-117">これは比較的簡単に見えますが、いくつかの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="738d2-117">This appears relatively simple, but several problems arise.</span></span> <span data-ttu-id="738d2-118">列の照合順序は、テーブルが作成されるデータベースに依存しているため、に格納されている一時テーブルを使用すると問題が発生し `tempdb` ます。</span><span class="sxs-lookup"><span data-stu-id="738d2-118">Because the collation for a column is dependent on the database in which the table is created, problems arise with the use of temporary tables which are stored in `tempdb`.</span></span> <span data-ttu-id="738d2-119">の照合順序は、 `tempdb` 通常、インスタンスの照合順序と一致しますが、データベースの照合順序と一致する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="738d2-119">The collation of `tempdb` usually matches the collation for the instance, which does not have to match the database collation.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="738d2-120">例 2</span><span class="sxs-lookup"><span data-stu-id="738d2-120">Example 2</span></span>  
 <span data-ttu-id="738d2-121">たとえば、上の中国語のデータベースが、 **Latin1_General** 照合順序のインスタンス上で使用されるとします。</span><span class="sxs-lookup"><span data-stu-id="738d2-121">For example, consider the (Chinese) database above when used on an instance with a **Latin1_General** collation:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max)) ;  
GO  
```  
  
 <span data-ttu-id="738d2-122">一見したところでは、これらの 2 つのテーブルは同じスキーマを持っているように見えます。しかし、データベースの照合順序が異なるため、値は実際には互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="738d2-122">At first glance, these two tables look like they have the same schema, but since the collations of the databases differ, the values are actually incompatible:</span></span>  
  
```  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="738d2-123">メッセージ 468、レベル 16、状態 9、行 2</span><span class="sxs-lookup"><span data-stu-id="738d2-123">Msg 468, Level 16, State 9, Line 2</span></span>  
  
 <span data-ttu-id="738d2-124">等しい操作の "Latin1_General_100_CI_AS_KS_WS_SC" と "Chinese_Simplified_Pinyin_100_CI_AS" 間での照合順序の競合を解決できません。</span><span class="sxs-lookup"><span data-stu-id="738d2-124">Cannot resolve the collation conflict between "Latin1_General_100_CI_AS_KS_WS_SC" and Chinese_Simplified_Pinyin_100_CI_AS" in the equal to operation.</span></span>  
  
 <span data-ttu-id="738d2-125">この問題は、一時テーブルの照合順序を明示的に指定することで解決できます。</span><span class="sxs-lookup"><span data-stu-id="738d2-125">We can fix this by explicitly collating the temporary table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="738d2-126">では、`DATABASE_DEFAULT` 句に `COLLATE` キーワードを用意することで、この操作を簡単に実行できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="738d2-126">makes this somewhat easier by providing the `DATABASE_DEFAULT` keyword for the `COLLATE` clause.</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max) COLLATE DATABASE_DEFAULT);  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="738d2-127">これで、エラーなしで実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="738d2-127">This now runs without error.</span></span>  
  
 <span data-ttu-id="738d2-128">変数に関しても、照合順序に依存する動作があります。</span><span class="sxs-lookup"><span data-stu-id="738d2-128">We can also see collation-dependent behavior with variables.</span></span> <span data-ttu-id="738d2-129">次のような関数があるとします。</span><span class="sxs-lookup"><span data-stu-id="738d2-129">Consider the following function:</span></span>  
  
```  
CREATE FUNCTION f(@x INT) RETURNS INT  
AS BEGIN   
      DECLARE @I INT = 1  
      DECLARE @?? INT = 2  
      RETURN @x * @i  
END;  
```  
  
 <span data-ttu-id="738d2-130">これは少し変わった関数です。</span><span class="sxs-lookup"><span data-stu-id="738d2-130">This is a rather peculiar function.</span></span> <span data-ttu-id="738d2-131">大文字と小文字を区別する照合順序で @i は、return 句のを @I または @??. にバインドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="738d2-131">In a case-sensitive collation, the @i in the return clause cannot bind to either @I or @??.</span></span> <span data-ttu-id="738d2-132">大文字と小文字を区別しない Latin1_General 照合順序では、@i が @I にバインドされ、関数は 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="738d2-132">In a case-insensitive Latin1_General collation, @i binds to @I, and the function returns 1.</span></span> <span data-ttu-id="738d2-133">ただし、大文字小文字を区別しないトルコ語の照合順序では、は @i @??, にバインドし、関数は2を返します。</span><span class="sxs-lookup"><span data-stu-id="738d2-133">But in a case-insensitive Turkish collation, @i binds to @??, and the function returns 2.</span></span> <span data-ttu-id="738d2-134">このことは、照合順序が異なるインスタンス間で移動されるデータベースでは、大きな問題になります。</span><span class="sxs-lookup"><span data-stu-id="738d2-134">This can wreak havoc on a database that moves between instances with different collations.</span></span>  
  
## <a name="contained-databases"></a><span data-ttu-id="738d2-135">包含データベース</span><span class="sxs-lookup"><span data-stu-id="738d2-135">Contained Databases</span></span>  
 <span data-ttu-id="738d2-136">包含データベースの設計目標は、データベースを自己完結させることなので、インスタンスと `tempdb` の照合順序への依存は解消する必要があります。</span><span class="sxs-lookup"><span data-stu-id="738d2-136">Since a design objective of contained databases is to make them self-contained, the dependence on the instance and `tempdb` collations must be severed.</span></span> <span data-ttu-id="738d2-137">そのために、包含データベースにはカタログ照合順序の概念が導入されました。</span><span class="sxs-lookup"><span data-stu-id="738d2-137">To do this, contained databases introduce the concept of the catalog collation.</span></span> <span data-ttu-id="738d2-138">カタログ照合順序は、システム メタデータと一時的なオブジェクトに使用されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-138">The catalog collation is used for system metadata and transient objects.</span></span> <span data-ttu-id="738d2-139">詳細については、以下で説明します。</span><span class="sxs-lookup"><span data-stu-id="738d2-139">Details are provided below.</span></span>  
  
 <span data-ttu-id="738d2-140">包含データベースでは、カタログ照合順序は **Latin1_General_100_CI_AS_WS_KS_SC**です。</span><span class="sxs-lookup"><span data-stu-id="738d2-140">In a contained database, the catalog collation **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="738d2-141">この照合順序は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインスタンスのすべての包含データベースで共通であり、変更できません。</span><span class="sxs-lookup"><span data-stu-id="738d2-141">This collation is the same for all contained databases on all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and cannot be changed.</span></span>  
  
 <span data-ttu-id="738d2-142">データベースの照合順序は保持されますが、ユーザー データの既定の照合順序としてのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-142">The database collation is retained, but is only used as the default collation for user data.</span></span> <span data-ttu-id="738d2-143">既定では、データベースの照合順序は model データベースの照合順序と同じですが、ユーザーがまたはコマンドを使用して、 `CREATE` `ALTER DATABASE` 非包含データベースと同様に変更できます。</span><span class="sxs-lookup"><span data-stu-id="738d2-143">By default, the database collation is equal to the model database collation, but can be changed by the user through a `CREATE` or `ALTER DATABASE` command as with non-contained databases.</span></span>  
  
 <span data-ttu-id="738d2-144">新しいキーワード `CATALOG_DEFAULT` を `COLLATE` 句で使用できます。</span><span class="sxs-lookup"><span data-stu-id="738d2-144">A new keyword, `CATALOG_DEFAULT`, is available in the `COLLATE` clause.</span></span> <span data-ttu-id="738d2-145">これは、包含データベースと非包含データベースの両方のメタデータにおける現在の照合順序へのショートカットとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-145">This is used as a shortcut to the current collation of metadata in both contained and non-contained databases.</span></span> <span data-ttu-id="738d2-146">つまり、非包含データベースでは、メタデータがデータベースの照合順序で照合されるので、`CATALOG_DEFAULT` は現在のデータベースの照合順序を返します。</span><span class="sxs-lookup"><span data-stu-id="738d2-146">That is, in a non-contained database, `CATALOG_DEFAULT` will return the current database collation, since metadata is collated in the database collation.</span></span> <span data-ttu-id="738d2-147">包含データベースでは、ユーザーがデータベースの照合順序をカタログ照合順序と一致しないように変更できるため、これらの 2 つの値は異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="738d2-147">In a contained database, these two values may be different, since the user can change the database collation so that it does not match the catalog collation.</span></span>  
  
 <span data-ttu-id="738d2-148">以下の表は、非包含データベースと包含データベースのさまざまなオブジェクトの動作をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="738d2-148">The behavior of various objects in both non-contained and contained databases is summarized in this table:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="738d2-149">**Item**</span><span class="sxs-lookup"><span data-stu-id="738d2-149">**Item**</span></span>|<span data-ttu-id="738d2-150">**非包含データベース**</span><span class="sxs-lookup"><span data-stu-id="738d2-150">**Non-Contained Database**</span></span>|<span data-ttu-id="738d2-151">**包含データベース**</span><span class="sxs-lookup"><span data-stu-id="738d2-151">**Contained Database**</span></span>|  
|<span data-ttu-id="738d2-152">ユーザー データ (既定値)</span><span class="sxs-lookup"><span data-stu-id="738d2-152">User Data (default)</span></span>|<span data-ttu-id="738d2-153">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-153">DATABASE_DEFAULT</span></span>|<span data-ttu-id="738d2-154">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-154">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="738d2-155">一時データ (既定値)</span><span class="sxs-lookup"><span data-stu-id="738d2-155">Temp Data (default)</span></span>|<span data-ttu-id="738d2-156">TempDB の照合順序</span><span class="sxs-lookup"><span data-stu-id="738d2-156">TempDB Collation</span></span>|<span data-ttu-id="738d2-157">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-157">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="738d2-158">Metadata</span><span class="sxs-lookup"><span data-stu-id="738d2-158">Metadata</span></span>|<span data-ttu-id="738d2-159">DATABASE_DEFAULT / CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="738d2-159">DATABASE_DEFAULT / CATALOG_DEFAULT</span></span>|<span data-ttu-id="738d2-160">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-160">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="738d2-161">一時的なメタデータ</span><span class="sxs-lookup"><span data-stu-id="738d2-161">Temporary Metadata</span></span>|<span data-ttu-id="738d2-162">TempDB の照合順序</span><span class="sxs-lookup"><span data-stu-id="738d2-162">tempdb Collation</span></span>|<span data-ttu-id="738d2-163">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-163">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="738d2-164">変数</span><span class="sxs-lookup"><span data-stu-id="738d2-164">Variables</span></span>|<span data-ttu-id="738d2-165">インスタンスの照合順序</span><span class="sxs-lookup"><span data-stu-id="738d2-165">Instance Collation</span></span>|<span data-ttu-id="738d2-166">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-166">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="738d2-167">Goto ラベル</span><span class="sxs-lookup"><span data-stu-id="738d2-167">Goto Labels</span></span>|<span data-ttu-id="738d2-168">インスタンスの照合順序</span><span class="sxs-lookup"><span data-stu-id="738d2-168">Instance Collation</span></span>|<span data-ttu-id="738d2-169">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-169">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="738d2-170">カーソル名</span><span class="sxs-lookup"><span data-stu-id="738d2-170">Cursor Names</span></span>|<span data-ttu-id="738d2-171">インスタンスの照合順序</span><span class="sxs-lookup"><span data-stu-id="738d2-171">Instance Collation</span></span>|<span data-ttu-id="738d2-172">COLLATE</span><span class="sxs-lookup"><span data-stu-id="738d2-172">CATALOG_DEFAULT</span></span>|  
  
 <span data-ttu-id="738d2-173">前に説明した一時テーブルの例でわかるように、この照合順序の動作によって、多くの一時テーブルでは明示的に `COLLATE` 句を使用する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="738d2-173">If we temp table example previously described, we can see that this collation behavior eliminates the need for an explicit `COLLATE` clause in most temp table uses.</span></span> <span data-ttu-id="738d2-174">包含データベースでは、データベースとインスタンスの照合順序が異なる場合でも、このコードはエラーにならずに実行されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-174">In a contained database, this code now runs without error, even if the database and instance collations differ:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max));  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="738d2-175">このコードがうまく機能するのは、 `T1_txt` と `T2_txt` の両方が、包含データベースのデータベース照合順序で照合されるためです。</span><span class="sxs-lookup"><span data-stu-id="738d2-175">This works because both `T1_txt` and `T2_txt` are collated in the database collation of the contained database.</span></span>  
  
## <a name="crossing-between-contained-and-uncontained-contexts"></a><span data-ttu-id="738d2-176">包含コンテキストと非包含コンテキスト間の移動</span><span class="sxs-lookup"><span data-stu-id="738d2-176">Crossing Between Contained and Uncontained Contexts</span></span>  
 <span data-ttu-id="738d2-177">包含データベース内のセッションが包含されたままである限り、そのセッションは接続されているデータベース内で維持されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-177">As long as a session in a contained database remains contained, it must remain within the database to which it connected.</span></span> <span data-ttu-id="738d2-178">この場合の動作は非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="738d2-178">In this case the behavior is very straightforward.</span></span> <span data-ttu-id="738d2-179">しかし、セッションが包含コンテキストと非包含コンテキスト間にまたがると、2 つの規則のセットに対応する必要があるので、動作はより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="738d2-179">But if a session crosses between contained and non-contained contexts, the behavior becomes more complex, since the two sets of rules must be bridged.</span></span> <span data-ttu-id="738d2-180">この問題は、部分的包含データベースで発生する場合があります。ユーザーが `USE` で別のデータベースを使用できるためです。</span><span class="sxs-lookup"><span data-stu-id="738d2-180">This can happen in a partially-contained database, since a user may `USE` to another database.</span></span> <span data-ttu-id="738d2-181">この場合、照合順序の規則の違いは、以下の原則に従って処理されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-181">In this case, the difference in collation rules is handled by the following principle.</span></span>  
  
-   <span data-ttu-id="738d2-182">バッチの照合順序の動作は、バッチを開始したデータベースによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-182">The collation behavior for a batch is determined by the database in which the batch begins.</span></span>  
  
 <span data-ttu-id="738d2-183">この決定は、最初の `USE` も含めて、どのコマンドの実行よりも前に行われることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="738d2-183">Note that this decision is made before any commands are issued, including an initial `USE`.</span></span> <span data-ttu-id="738d2-184">つまり、バッチが包含データベース内で開始されると、最初のコマンドが非包含データベースに対する `USE` であっても、バッチで使用されるのは包含の照合順序の動作のままです。</span><span class="sxs-lookup"><span data-stu-id="738d2-184">That is, if a batch begins in a contained database, but the first command is a `USE` to a non-contained database, the contained collation behavior will still be used for the batch.</span></span> <span data-ttu-id="738d2-185">このため、たとえば変数への参照が、次のような複数の結果を持つ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="738d2-185">Given this, a reference to a variable, for example, may have multiple possible outcomes:</span></span>  
  
-   <span data-ttu-id="738d2-186">参照がただ 1 つの一致を見つけられる。</span><span class="sxs-lookup"><span data-stu-id="738d2-186">The reference may find exactly one match.</span></span> <span data-ttu-id="738d2-187">この場合、参照はエラーにならずに動作します。</span><span class="sxs-lookup"><span data-stu-id="738d2-187">In this case, the reference will work without error.</span></span>  
  
-   <span data-ttu-id="738d2-188">参照が現在の照合順序では一致を見つけられないが、前の照合順序では 1 つ見つかった。</span><span class="sxs-lookup"><span data-stu-id="738d2-188">The reference may not find a match in the current collation where there was one before.</span></span> <span data-ttu-id="738d2-189">この場合は、変数が作成されたことが明らかであっても、変数が存在しないというエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-189">This will raise an error indicating that the variable does not exist, even though it was apparently created.</span></span>  
  
-   <span data-ttu-id="738d2-190">参照が、本来は区別可能であった複数の一致を見つけられる。</span><span class="sxs-lookup"><span data-stu-id="738d2-190">The reference may find multiple matches that were originally distinct.</span></span> <span data-ttu-id="738d2-191">この場合も、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="738d2-191">This will also raise an error.</span></span>  
  
 <span data-ttu-id="738d2-192">この問題を、いくつかの例で説明します。</span><span class="sxs-lookup"><span data-stu-id="738d2-192">We'll illustrate this with a few examples.</span></span> <span data-ttu-id="738d2-193">これらの例では、 `MyCDB` という名前の部分的包含データベースがあり、そのデータベースの照合順序が既定の照合順序の **Latin1_General_100_CI_AS_WS_KS_SC**に設定されているものとします。</span><span class="sxs-lookup"><span data-stu-id="738d2-193">For these we assume there is a partially-contained database named `MyCDB` with its database collation set to the default collation, **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="738d2-194">また、インスタンスの照合順序は `Latin1_General_100_CS_AS_WS_KS_SC` であるとします。</span><span class="sxs-lookup"><span data-stu-id="738d2-194">We assume that the instance collation is `Latin1_General_100_CS_AS_WS_KS_SC`.</span></span> <span data-ttu-id="738d2-195">2 つの照合順序の違いは、大文字と小文字を区別するかどうかだけです。</span><span class="sxs-lookup"><span data-stu-id="738d2-195">The two collations differ only in case sensitivity.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="738d2-196">例 1</span><span class="sxs-lookup"><span data-stu-id="738d2-196">Example 1</span></span>  
 <span data-ttu-id="738d2-197">次の例は、参照がただ 1 つの一致を見つける場合を示しています。</span><span class="sxs-lookup"><span data-stu-id="738d2-197">The following example illustrates the case where the reference finds exactly one match.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #a VALUES(1);  
GO  
  
USE master;  
GO  
  
SELECT * FROM #a;  
GO  
  
Results:  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
x  
-----------  
1  
```  
  
 <span data-ttu-id="738d2-198">この例では、識別された #a が、大文字と小文字を区別しないカタログ照合順序と、大文字と小文字を区別するインスタンス照合順序の両方でバインドされ、コードは正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="738d2-198">In this case, the identified #a binds in both the case-insensitive catalog collation and the case-sensitive instance collation, and the code works.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="738d2-199">例 2</span><span class="sxs-lookup"><span data-stu-id="738d2-199">Example 2</span></span>  
 <span data-ttu-id="738d2-200">次の例は、参照が現在の照合順序では一致を見つけられず、前の照合順序では 1 つ見つけた場合を示しています。</span><span class="sxs-lookup"><span data-stu-id="738d2-200">The following example illustrates the case where the reference does not find a match in the current collation where there was one before.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #A VALUES(1);  
GO  
```  
  
 <span data-ttu-id="738d2-201">ここでは、大文字と小文字を区別しない既定の照合順序で #A が #a にバインドされ、挿入を正常に実行できます。</span><span class="sxs-lookup"><span data-stu-id="738d2-201">Here, the #A binds to #a in the case-insensitive default collation, and the insert works,</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="738d2-202">しかし、スクリプトを続行すると ...</span><span class="sxs-lookup"><span data-stu-id="738d2-202">But if we continue the script...</span></span>  
  
```  
USE master;  
GO  
  
SELECT * FROM #A;  
GO  
```  
  
 <span data-ttu-id="738d2-203">大文字と小文字を区別するインスタンスの照合順序で #A にバインドしようとして、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="738d2-203">We get an error trying to bind to #A in the case-sensitive instance collation;</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="738d2-204">メッセージ 208、レベル 16、状態 0、行 2</span><span class="sxs-lookup"><span data-stu-id="738d2-204">Msg 208, Level 16, State 0, Line 2</span></span>  
  
 <span data-ttu-id="738d2-205">オブジェクト名 '#A' が無効です。</span><span class="sxs-lookup"><span data-stu-id="738d2-205">Invalid object name '#A'.</span></span>  
  
### <a name="example-3"></a><span data-ttu-id="738d2-206">例 3</span><span class="sxs-lookup"><span data-stu-id="738d2-206">Example 3</span></span>  
 <span data-ttu-id="738d2-207">次の例は、参照が本来は区別可能であった複数の一致を見つける場合を示しています。</span><span class="sxs-lookup"><span data-stu-id="738d2-207">The following example illustrates the case where the reference finds multiple matches that were originally distinct.</span></span> <span data-ttu-id="738d2-208">まず、 `tempdb` (インスタンスと同じ照合順序を持つ) から開始し、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="738d2-208">First, we start in `tempdb` (which has the same case-sensitive collation as our instance) and execute the following statements.</span></span>  
  
```  
USE tempdb;  
GO  
  
CREATE TABLE #a(x int);  
GO  
CREATE TABLE #A(x int);  
GO  
INSERT INTO #a VALUES(1);  
GO  
INSERT INTO #A VALUES(2);  
GO  
```  
  
 <span data-ttu-id="738d2-209">この照合順序では、テーブルが区別可能であるため、問題なく動作します。</span><span class="sxs-lookup"><span data-stu-id="738d2-209">This succeeds, since the tables are distinct in this collation:</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="738d2-210">しかし、包含データベース内に移動すると、これらのテーブルへのバインドができなくなります。</span><span class="sxs-lookup"><span data-stu-id="738d2-210">If we move into our contained database, however, we find that we can no longer bind to these tables.</span></span>  
  
```  
USE MyCDB;  
GO  
SELECT * FROM #a;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="738d2-211">メッセージ 12800、レベル 16、状態 1、行 2</span><span class="sxs-lookup"><span data-stu-id="738d2-211">Msg 12800, Level 16, State 1, Line 2</span></span>  
  
 <span data-ttu-id="738d2-212">一時テーブル名 '#a' への参照があいまいで、解決できません。</span><span class="sxs-lookup"><span data-stu-id="738d2-212">The reference to temp table name '#a' is ambiguous and cannot be resolved.</span></span> <span data-ttu-id="738d2-213">候補となるのは '#a' と '#A' です。</span><span class="sxs-lookup"><span data-stu-id="738d2-213">Possible candidates are '#a' and '#A'.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="738d2-214">まとめ</span><span class="sxs-lookup"><span data-stu-id="738d2-214">Conclusion</span></span>  
 <span data-ttu-id="738d2-215">包含データベースの照合順序の動作は、非包含データベースの場合と微妙に異なります。</span><span class="sxs-lookup"><span data-stu-id="738d2-215">The collation behavior of contained databases differs subtly from that in non-contained databases.</span></span> <span data-ttu-id="738d2-216">この動作は、インスタンスに対する独立性と簡易性を提供し、一般的には有益です。</span><span class="sxs-lookup"><span data-stu-id="738d2-216">This behavior is generally beneficial, providing instance-independence and simplicity.</span></span> <span data-ttu-id="738d2-217">ただし、場合によっては、特にセッションが包含データベースと非包含データベースの両方にアクセスする場合には、問題が発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="738d2-217">Some users may have issues, particularly when a session accesses both contained and non-contained databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738d2-218">参照</span><span class="sxs-lookup"><span data-stu-id="738d2-218">See Also</span></span>  
 [<span data-ttu-id="738d2-219">包含データベース</span><span class="sxs-lookup"><span data-stu-id="738d2-219">Contained Databases</span></span>](contained-databases.md)  
  
  
