---
title: SQLTables |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: rothja
ms.author: jroth
ms.openlocfilehash: bad60aa102a7771935e37ac963e6fa0d3cb2fd57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640912"
---
# <a name="sqltables"></a><span data-ttu-id="bb821-102">SQLTables</span><span class="sxs-lookup"><span data-stu-id="bb821-102">SQLTables</span></span>
  <span data-ttu-id="bb821-103">SQLTables は、静的サーバーカーソルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb821-103">SQLTables can be executed on a static server cursor.</span></span> <span data-ttu-id="bb821-104">更新可能なカーソル (動的カーソルまたはキーセットカーソル) で SQLTables を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="bb821-104">An attempt to execute SQLTables on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="bb821-105">*CatalogName*パラメーターが SQL_ALL_CATALOGS、他のすべてのパラメーターに既定値 (NULL ポインター) が含まれている場合、sqltables はすべてのデータベースのテーブルを報告します。</span><span class="sxs-lookup"><span data-stu-id="bb821-105">SQLTables reports tables from all databases when the *CatalogName* parameter is SQL_ALL_CATALOGS and all other parameters contain default values (NULL pointers).</span></span>  
  
 <span data-ttu-id="bb821-106">使用可能なカタログ、スキーマ、およびテーブルの種類をレポートするために、SQLTables は空の文字列 (長さゼロのバイトポインター) を特別に使用します。</span><span class="sxs-lookup"><span data-stu-id="bb821-106">To report available catalogs, schemas, and table types, SQLTables makes special use of empty strings (zero-length byte pointers).</span></span> <span data-ttu-id="bb821-107">空文字列は、既定値 (NULL ポインター) ではありません。</span><span class="sxs-lookup"><span data-stu-id="bb821-107">Empty strings are not default values (NULL pointers).</span></span>  
  
 <span data-ttu-id="bb821-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *CatalogName*パラメーターに2つの部分で構成される名前を使用して、リンクサーバー上のテーブルに関する情報のレポートをサポートしています。 *Linked_Server_Name Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="bb821-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
 <span data-ttu-id="bb821-109">SQLTables は、名前が*TableName*に一致し、現在のユーザーが所有しているテーブルに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="bb821-109">SQLTables returns information about any tables whose names match *TableName* and are owned by the current user.</span></span>  
  
## <a name="sqltables-and-table-valued-parameters"></a><span data-ttu-id="bb821-110">SQLTables とテーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb821-110">SQLTables and Table-Valued Parameters</span></span>  
 <span data-ttu-id="bb821-111">ステートメント属性 SQL_SOPT_SS_NAME_SCOPE の値が既定値の SQL_SS_NAME_SCOPE_TABLE ではなく SQL_SS_NAME_SCOPE_TABLE_TYPE の場合、SQLTables はテーブル型に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="bb821-111">When the statement attribute SQL_SOPT_SS_NAME_SCOPE has the value SQL_SS_NAME_SCOPE_TABLE_TYPE, rather than its default value of SQL_SS_NAME_SCOPE_TABLE, SQLTables returns information about table types.</span></span> <span data-ttu-id="bb821-112">SQLTables によって返される結果セットの列4のテーブル型に対して返される TABLE_TYPE 値はテーブル型です。</span><span class="sxs-lookup"><span data-stu-id="bb821-112">The TABLE_TYPE value returned for a table type in column 4 of the result set returned by SQLTables is TABLE TYPE.</span></span> <span data-ttu-id="bb821-113">SQL_SOPT_SS_NAME_SCOPE の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb821-113">For more information on SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="bb821-114">テーブル、ビュー、およびシノニムは、テーブル型によって使用される名前空間とは異なる、共通の名前空間を共有します。</span><span class="sxs-lookup"><span data-stu-id="bb821-114">Tables, views, and synonyms share a common namespace that is distinct from the namespace used by table types.</span></span> <span data-ttu-id="bb821-115">テーブルとビューを同じ名前にすることはできませんが、同じ名前のテーブルとテーブル型を同じカタログおよびスキーマ内に配置することはできます。</span><span class="sxs-lookup"><span data-stu-id="bb821-115">Although it is not possible to have a table and a view with the same name, it is possible to have a table and a table type with the same in the same catalog and schema.</span></span>  
  
 <span data-ttu-id="bb821-116">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb821-116">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb821-117">例</span><span class="sxs-lookup"><span data-stu-id="bb821-117">Example</span></span>  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb821-118">参照</span><span class="sxs-lookup"><span data-stu-id="bb821-118">See Also</span></span>  
 <span data-ttu-id="bb821-119">[SQLTables 関数](https://go.microsoft.com/fwlink/?LinkId=59374) </span><span class="sxs-lookup"><span data-stu-id="bb821-119">[SQLTables Function](https://go.microsoft.com/fwlink/?LinkId=59374) </span></span>  
 [<span data-ttu-id="bb821-120">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="bb821-120">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
