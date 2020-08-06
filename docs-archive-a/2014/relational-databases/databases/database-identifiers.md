---
title: データベース識別子 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- regular identifiers [SQL Server]
- identifiers [SQL Server]
- names [SQL Server], identifiers
- identifiers [SQL Server], about identifiers
- SQL Server identifiers
- Transact-SQL identifiers
- database objects [SQL Server], names
ms.assetid: 171291bb-f57f-4ad1-8cea-0b092d5d150c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 347b20c12a0ac5edd82172741377617aa0fe12c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640076"
---
# <a name="database-identifiers"></a><span data-ttu-id="81542-102">データベース識別子</span><span class="sxs-lookup"><span data-stu-id="81542-102">Database Identifiers</span></span>
  <span data-ttu-id="81542-103">データベース オブジェクトの名前は識別子と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="81542-103">The database object name is referred to as its identifier.</span></span> <span data-ttu-id="81542-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、すべてのオブジェクトに識別子を設定できます。</span><span class="sxs-lookup"><span data-stu-id="81542-104">Everything in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can have an identifier.</span></span> <span data-ttu-id="81542-105">サーバーやデータベース、またはテーブル、ビュー、列、インデックス、トリガー、プロシージャ、制約、規則などのデータベース オブジェクトに対して識別子を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="81542-105">Servers, databases, and database objects, such as tables, views, columns, indexes, triggers, procedures, constraints, and rules, can have identifiers.</span></span> <span data-ttu-id="81542-106">ほとんどのオブジェクトには識別子が必要です。ただし、制約などの一部のオブジェクトについては、識別子は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="81542-106">Identifiers are required for most objects, but are optional for some objects such as constraints.</span></span>  
  
 <span data-ttu-id="81542-107">オブジェクトの識別子は、オブジェクトを定義するときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="81542-107">An object identifier is created when the object is defined.</span></span> <span data-ttu-id="81542-108">作成された識別子を使用して、そのオブジェクトを参照できます。</span><span class="sxs-lookup"><span data-stu-id="81542-108">The identifier is then used to reference the object.</span></span> <span data-ttu-id="81542-109">たとえば、次のステートメントは識別子が `TableX`であるテーブル 1 つと、識別子がそれぞれ `KeyCol` 、 `Description`である 2 つの列を作成します。</span><span class="sxs-lookup"><span data-stu-id="81542-109">For example, the following statement creates a table with the identifier `TableX`, and two columns with the identifiers `KeyCol` and `Description`:</span></span>  
  
```  
CREATE TABLE TableX  
(KeyCol INT PRIMARY KEY, Description nvarchar(80))  
```  
  
 <span data-ttu-id="81542-110">このテーブルには名前のない制約も含まれます。</span><span class="sxs-lookup"><span data-stu-id="81542-110">This table also has an unnamed constraint.</span></span> <span data-ttu-id="81542-111">`PRIMARY KEY` 制約には識別子がありません。</span><span class="sxs-lookup"><span data-stu-id="81542-111">The `PRIMARY KEY` constraint has no identifier.</span></span>  
  
 <span data-ttu-id="81542-112">識別子の照合順序は、識別子が定義されているレベルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="81542-112">The collation of an identifier depends on the level at which it is defined.</span></span> <span data-ttu-id="81542-113">ログイン名やデータベース名など、インスタンスレベルのオブジェクトの識別子には、インスタンスの既定の照合順序が指定されます。</span><span class="sxs-lookup"><span data-stu-id="81542-113">Identifiers of instance-level objects, such as logins and database names, are assigned the default collation of the instance.</span></span> <span data-ttu-id="81542-114">テーブル名、ビュー名、列名など、データベース内のオブジェクトの識別子には、データベースの既定の照合順序が指定されます。</span><span class="sxs-lookup"><span data-stu-id="81542-114">Identifiers of objects in a database, such as tables, views, and column names, are assigned the default collation of the database.</span></span> <span data-ttu-id="81542-115">たとえば、大文字と小文字を区別する照合順序が指定されたデータベースでは、同じ名前で大文字と小文字のみが異なる 2 つのテーブルを作成できますが、大文字と小文字を区別しない照合順序が指定されたデータベースでは作成できません。</span><span class="sxs-lookup"><span data-stu-id="81542-115">For example, two tables with names that differ only in case can be created in a database that has case-sensitive collation, but cannot be created in a database that has case-insensitive collation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81542-116">変数名、関数およびストアド プロシージャのパラメーター名は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子の規則に従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="81542-116">The names of variables, or the parameters of functions and stored procedures must comply with the rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
## <a name="classes-of-identifiers"></a><span data-ttu-id="81542-117">識別子のクラス</span><span class="sxs-lookup"><span data-stu-id="81542-117">Classes of Identifiers</span></span>  
 <span data-ttu-id="81542-118">識別子のクラスには、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="81542-118">There are two classes of identifiers:</span></span>  
  
 <span data-ttu-id="81542-119">標準識別子</span><span class="sxs-lookup"><span data-stu-id="81542-119">Regular identifiers</span></span>  
 <span data-ttu-id="81542-120">識別子の形式に関する規則に従います。</span><span class="sxs-lookup"><span data-stu-id="81542-120">Comply with the rules for the format of identifiers.</span></span> <span data-ttu-id="81542-121">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用するときは、標準識別子を区切る必要はありません。</span><span class="sxs-lookup"><span data-stu-id="81542-121">Regular identifiers are not delimited when they are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
SELECT *  
FROM TableX  
WHERE KeyCol = 124  
```  
  
 <span data-ttu-id="81542-122">区切られた識別子</span><span class="sxs-lookup"><span data-stu-id="81542-122">Delimited identifiers</span></span>  
 <span data-ttu-id="81542-123">二重引用符 (") または角かっこ ([ ]) で囲まれています。</span><span class="sxs-lookup"><span data-stu-id="81542-123">Are enclosed in double quotation marks (") or brackets ([ ]).</span></span> <span data-ttu-id="81542-124">識別子の形式に関する規則に従っている識別子は、区切らなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="81542-124">Identifiers that comply with the rules for the format of identifiers might not be delimited.</span></span> <span data-ttu-id="81542-125">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="81542-125">For example:</span></span>  
  
```  
SELECT *  
FROM [TableX]         --Delimiter is optional.  
WHERE [KeyCol] = 124  --Delimiter is optional.  
```  
  
 <span data-ttu-id="81542-126">識別子の規則に従わない識別子を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用する場合は、必ず区切らなければなりません。</span><span class="sxs-lookup"><span data-stu-id="81542-126">Identifiers that do not comply with all the rules for identifiers must be delimited in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="81542-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="81542-127">For example:</span></span>  
  
```  
SELECT *  
FROM [My Table]      --Identifier contains a space and uses a reserved keyword.  
WHERE [order] = 10   --Identifier is a reserved keyword.  
```  
  
 <span data-ttu-id="81542-128">標準識別子および区切られた識別子は、文字、記号 (_ @ #)、および数字を含む 1 ～ 128 個の文字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="81542-128">Both regular and delimited identifiers must contain from 1 through 128 characters.</span></span> <span data-ttu-id="81542-129">ローカル一時テーブルの場合、識別子は 116 文字以下でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="81542-129">For local temporary tables, the identifier can have a maximum of 116 characters.</span></span>  
  
## <a name="rules-for-regular-identifiers"></a><span data-ttu-id="81542-130">標準識別子に関する規則</span><span class="sxs-lookup"><span data-stu-id="81542-130">Rules for Regular Identifiers</span></span>  
 <span data-ttu-id="81542-131">変数、関数、およびストアド プロシージャの名前は、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子の規則に従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="81542-131">The names of variables, functions, and stored procedures must comply with the following rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
1.  <span data-ttu-id="81542-132">最初の文字が次のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="81542-132">The first character must be one of the following:</span></span>  
  
    -   <span data-ttu-id="81542-133">Unicode 規格 3.2 で定義されている文字。</span><span class="sxs-lookup"><span data-stu-id="81542-133">A letter as defined by the Unicode Standard 3.2.</span></span> <span data-ttu-id="81542-134">Unicode の文字定義には、各国言語の文字の他に、ラテン文字 a ～ z と A ～ Z も含まれます。</span><span class="sxs-lookup"><span data-stu-id="81542-134">The Unicode definition of letters includes Latin characters from a through z, from A through Z, and also letter characters from other languages.</span></span>  
  
    -   <span data-ttu-id="81542-135">アンダースコア (_)、アット マーク (@)、または番号記号 (#)。</span><span class="sxs-lookup"><span data-stu-id="81542-135">The underscore (_), at sign (@), or number sign (#).</span></span>  
  
         <span data-ttu-id="81542-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、識別子の先頭にある一定の記号には特別な意味があります。</span><span class="sxs-lookup"><span data-stu-id="81542-136">Certain symbols at the beginning of an identifier have special meaning in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="81542-137">アット マークで始まる標準識別子は、常にローカル変数またはローカル パラメーターを表し、他の種類のオブジェクトの名前としては使用できません。</span><span class="sxs-lookup"><span data-stu-id="81542-137">A regular identifier that starts with the at sign always denotes a local variable or parameter and cannot be used as the name of any other type of object.</span></span> <span data-ttu-id="81542-138">番号記号で始まる識別子は一時テーブルまたは一時プロシージャを表します。</span><span class="sxs-lookup"><span data-stu-id="81542-138">An identifier that starts with a number sign denotes a temporary table or procedure.</span></span> <span data-ttu-id="81542-139">2 つの番号記号 (##) で始まる識別子は、グローバルな一時オブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="81542-139">An identifier that starts with double number signs (##) denotes a global temporary object.</span></span> <span data-ttu-id="81542-140">1 つまたは 2 つの番号記号で始まる名前を、他の種類のオブジェクトの名前として使用することもできますが、このような番号記号の使用はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="81542-140">Although the number sign or double number sign characters can be used to begin the names of other types of objects, we do not recommend this practice.</span></span>  
  
         <span data-ttu-id="81542-141">一部の [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数の名前は、2 つのアット マーク (@@) から始まります。</span><span class="sxs-lookup"><span data-stu-id="81542-141">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] functions have names that start with double at signs (@@).</span></span> <span data-ttu-id="81542-142">これらの関数との混同を避けるために、@@ から始まる名前は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="81542-142">To avoid confusion with these functions, you should not use names that start with @@.</span></span>  
  
2.  <span data-ttu-id="81542-143">名前の先頭以外では、次の文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="81542-143">Subsequent characters can include the following:</span></span>  
  
    -   <span data-ttu-id="81542-144">Unicode 規格 3.2 で定義されている文字</span><span class="sxs-lookup"><span data-stu-id="81542-144">Letters as defined in the Unicode Standard 3.2.</span></span>  
  
    -   <span data-ttu-id="81542-145">Basic Latin スクリプトまたはその他の各国スクリプトの 10 進数</span><span class="sxs-lookup"><span data-stu-id="81542-145">Decimal numbers from either Basic Latin or other national scripts.</span></span>  
  
    -   <span data-ttu-id="81542-146">アット マーク、ドル記号 ($)、番号記号、またはアンダースコア</span><span class="sxs-lookup"><span data-stu-id="81542-146">The at sign, dollar sign ($), number sign, or underscore.</span></span>  
  
3.  <span data-ttu-id="81542-147">[!INCLUDE[tsql](../../includes/tsql-md.md)] 予約語を識別子として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="81542-147">The identifier must not be a [!INCLUDE[tsql](../../includes/tsql-md.md)] reserved word.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="81542-148">の予約語は、大文字、小文字ともに予約されています。</span><span class="sxs-lookup"><span data-stu-id="81542-148">reserves both the uppercase and lowercase versions of reserved words.</span></span> <span data-ttu-id="81542-149">これらの規則に従っていない識別子を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用する場合は、二重引用符または角かっこで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="81542-149">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span> <span data-ttu-id="81542-150">予約語は、データベースの互換性レベルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="81542-150">The words that are reserved depend on the database compatibility level.</span></span> <span data-ttu-id="81542-151">このレベルは、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) ステートメントを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="81542-151">This level can be set by using the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) statement.</span></span>  
  
4.  <span data-ttu-id="81542-152">埋め込み型スペースおよび特殊文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="81542-152">Embedded spaces or special characters are not allowed.</span></span>  
  
5.  <span data-ttu-id="81542-153">補助文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="81542-153">Supplementary characters are not allowed.</span></span>  
  
 <span data-ttu-id="81542-154">これらの規則に従っていない識別子を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用する場合は、二重引用符または角かっこで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="81542-154">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81542-155">標準識別子の形式に関する規則は、データベースの互換性レベルに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="81542-155">Some rules for the format of regular identifiers depend on the database compatibility level.</span></span> <span data-ttu-id="81542-156">互換性レベルは、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="81542-156">This level can be set by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81542-157">参照</span><span class="sxs-lookup"><span data-stu-id="81542-157">See Also</span></span>  
 <span data-ttu-id="81542-158">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-158">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="81542-159">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-159">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="81542-160">[CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-160">[CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) </span></span>  
 <span data-ttu-id="81542-161">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-161">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="81542-162">[CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-162">[CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql) </span></span>  
 <span data-ttu-id="81542-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="81542-164">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-164">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="81542-165">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-165">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 <span data-ttu-id="81542-166">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-166">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="81542-167">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-167">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="81542-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="81542-169">[予約済みキーワード &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-169">[Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span></span>  
 <span data-ttu-id="81542-170">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="81542-170">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="81542-171">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="81542-171">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
