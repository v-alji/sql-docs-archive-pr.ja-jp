---
title: 国際化に対応した Transact-SQL ステートメントの記述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1888d1045e43e0a9839fd76a21c51500af63539a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645650"
---
# <a name="write-international-transact-sql-statements"></a><span data-ttu-id="05942-102">国際化に対応した Transact-SQL ステートメントの記述</span><span class="sxs-lookup"><span data-stu-id="05942-102">Write International Transact-SQL Statements</span></span>
  <span data-ttu-id="05942-103">以下のガイドラインに従うと、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するデータベースやデータベース アプリケーションをある言語から別の言語に移行することが容易になり、複数の言語をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="05942-103">Databases and database applications that use [!INCLUDE[tsql](../../includes/tsql-md.md)] statements will become more portable from one language to another, or will support multiple languages, if the following guidelines are followed:</span></span>  
  
-   <span data-ttu-id="05942-104">`char`、`varchar`、および `text` の各データ型を使用しているすべての個所をそれぞれ `nchar`、`nvarchar`、および `nvarchar(max)` データ型に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="05942-104">Replace all uses of the `char`, `varchar`, and `text` data types with `nchar`, `nvarchar`, and `nvarchar(max)`.</span></span> <span data-ttu-id="05942-105">これを行うことにより、コード ページの変換の問題について考慮する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="05942-105">By doing this, you do not have to consider code page conversion issues.</span></span> <span data-ttu-id="05942-106">詳細については、「 [Collation and Unicode Support](collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05942-106">For more information, see [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="05942-107">月単位または曜日単位で比較や操作を行う場合、名前の文字列ではない数字の日付要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="05942-107">When you perform month and day-of-week comparisons and operations, use the numeric date parts instead of the name strings.</span></span> <span data-ttu-id="05942-108">言語設定が異なると、月や曜日の名前が異なります。</span><span class="sxs-lookup"><span data-stu-id="05942-108">Different language settings return different names for the months and weekdays.</span></span> <span data-ttu-id="05942-109">たとえば、DATENAME(MONTH,GETDATE()) は、言語の設定が英語 (U.S.) になっていれば "May" を返します。設定がドイツ語になっていれば "Mai"、フランス語になっていれば "mai" を返します。</span><span class="sxs-lookup"><span data-stu-id="05942-109">For example, DATENAME(MONTH,GETDATE()) returns May when the language is set to U.S. English, returns Mai when the language is set to German, and returns mai when the language is set to French.</span></span> <span data-ttu-id="05942-110">代わりに、DATEPART のような関数を使用すると、月の名前の代わりに数字が返されます。</span><span class="sxs-lookup"><span data-stu-id="05942-110">Instead, use a function such as DATEPART that uses the number of the month instead of the name.</span></span> <span data-ttu-id="05942-111">多くの場合、日付を数字で表記するよりも名前で表記する方がよりわかりやすくなるので、ユーザーに表示する結果セットを構築するときは、DATEPART 名を使用してください。</span><span class="sxs-lookup"><span data-stu-id="05942-111">Use the DATEPART names when you build result sets to be displayed to a user, because the date names are frequently more meaningful than a numeric representation.</span></span> <span data-ttu-id="05942-112">ただし、特定の言語の表示名に依存するロジックはコーディングしないでください。</span><span class="sxs-lookup"><span data-stu-id="05942-112">However, do not code any logic that depends on the displayed names being from a specific language.</span></span>  
  
-   <span data-ttu-id="05942-113">日付を比較する場合、または INSERT ステートメントまたは UPDATE ステートメントで日付を指定する場合は、どの言語設定でも同じ解釈が行われる制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="05942-113">When you specify dates in comparisons or for input to INSERT or UPDATE statements, use constants that are interpreted the same way for all language settings:</span></span>  
  
    -   <span data-ttu-id="05942-114">ADO、OLE DB、および ODBC アプリケーションでは、以下に示す ODBC タイムスタンプ、日付、時刻のエスケープ句を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05942-114">ADO, OLE DB, and ODBC applications should use the ODBC timestamp, date, and time escape clauses of:</span></span>  
  
         <span data-ttu-id="05942-115">**{ts '** yyyy **-** _mm_ **-** _ddhh_**:**_mm_**:**_ss_[**.**_fff_**'}** 例: **{ts '** 1998 **-** 09 **-** 24 10 **:** 02 **:** 20 **'}**</span><span class="sxs-lookup"><span data-stu-id="05942-115">**{ ts'** yyyy**-**_mm_**-**_ddhh_**:**_mm_**:**_ss_[**.**_fff_] **'}** such as: **{ ts'** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **' }**</span></span>  
  
         <span data-ttu-id="05942-116">**{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** such as: **{ d'** 1998**-** 09**-** 24 **'}**</span><span class="sxs-lookup"><span data-stu-id="05942-116">**{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** such as: **{ d'** 1998**-** 09**-** 24 **'}**</span></span>  
  
         <span data-ttu-id="05942-117">**{t '** _hh_ **:** _mm_ **:** _ss_ **'}** (例: **{t '** 10:02:20 **'}** )</span><span class="sxs-lookup"><span data-stu-id="05942-117">**{ t'** _hh_ **:** _mm_ **:** _ss_ **'}** such as: **{ t'** 10:02:20 **'}**</span></span>  
  
    -   <span data-ttu-id="05942-118">他の API、または [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、ストアド プロシージャ、およびトリガーを使用するアプリケーションでは、区切られていない数字列を使用してください。</span><span class="sxs-lookup"><span data-stu-id="05942-118">Applications that use other APIs, or [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, stored procedures, and triggers, should use the unseparated numeric strings.</span></span> <span data-ttu-id="05942-119">たとえば、 *yyyymmdd* には 19980924 を使用します。</span><span class="sxs-lookup"><span data-stu-id="05942-119">For example, *yyyymmdd* as 19980924.</span></span>  
  
    -   <span data-ttu-id="05942-120">他の api、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、ストアドプロシージャ、およびトリガーを使用するアプリケーションでは、、、 `time` `date` `smalldate` 、 `datetime` 、 **datetime2**、および `datetimeoffset` データ型と文字列データ型の間のすべての変換に対して、明示的なスタイルパラメーターを指定して CONVERT ステートメントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05942-120">Applications that use other APIs, or [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, stored procedures, and triggers should use the CONVERT statement with an explicit style parameter for all conversions between the `time`, `date`, `smalldate`, `datetime`, **datetime2**, and `datetimeoffset` data types and character string data types.</span></span> <span data-ttu-id="05942-121">たとえば、次のステートメントは、すべての言語または日付形式の接続設定で同じように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="05942-121">For example, the following statement is interpreted in the same way for all language or date format connection settings:</span></span>  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         <span data-ttu-id="05942-122">詳細については、「[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05942-122">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
  
