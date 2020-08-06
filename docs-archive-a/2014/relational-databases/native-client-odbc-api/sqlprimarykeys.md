---
title: SQLPrimaryKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: rothja
ms.author: jroth
ms.openlocfilehash: 67a932996ccbf52f5ab21fd6aa62381184ebc510
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645023"
---
# <a name="sqlprimarykeys"></a><span data-ttu-id="a8f40-102">SQLPrimaryKeys</span><span class="sxs-lookup"><span data-stu-id="a8f40-102">SQLPrimaryKeys</span></span>
  <span data-ttu-id="a8f40-103">テーブルには、一意の行識別子として使用できる1つ以上の列が含まれる場合があります。また、PRIMARY KEY 制約なしで作成されたテーブルは、SQLPrimaryKeys に空の結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="a8f40-103">A table might have a column or columns that can serve as unique row identifiers, and tables created without a PRIMARY KEY constraint return an empty result set to SQLPrimaryKeys.</span></span> <span data-ttu-id="a8f40-104">ODBC 関数[sqlの列](sqlspecialcolumns.md)は、主キーのないテーブルの行識別子の候補を報告します。</span><span class="sxs-lookup"><span data-stu-id="a8f40-104">The ODBC function [SQLSpecialColumns](sqlspecialcolumns.md) reports row identifier candidates for tables without primary keys.</span></span>  
  
 <span data-ttu-id="a8f40-105">SQLPrimaryKeys は、 *CatalogName*、 *SchemaName*、または*TableName*パラメーターの値が存在するかどうかを SQL_SUCCESS 返します。</span><span class="sxs-lookup"><span data-stu-id="a8f40-105">SQLPrimaryKeys returns SQL_SUCCESS whether or not values exist for *CatalogName*, *SchemaName*, or *TableName* parameters.</span></span> <span data-ttu-id="a8f40-106">SQLFetch では、これらのパラメーターに無効な値が使用されると SQL_NO_DATA が返されます。</span><span class="sxs-lookup"><span data-stu-id="a8f40-106">SQLFetch returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="a8f40-107">SQLPrimaryKeys は、静的サーバーカーソルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="a8f40-107">SQLPrimaryKeys can be executed on a static server cursor.</span></span> <span data-ttu-id="a8f40-108">更新可能なカーソル (動的カーソルまたはキーセットカーソル) で SQLPrimaryKeys を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="a8f40-108">An attempt to execute SQLPrimaryKeys on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="a8f40-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *CatalogName*パラメーターに2つの部分で構成される名前を使用して、リンクサーバー上のテーブルに関する情報のレポートをサポートしています。 *Linked_Server_Name Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="a8f40-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a><span data-ttu-id="a8f40-110">SQLPrimaryKeys とテーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8f40-110">SQLPrimaryKeys and Table-Valued Parameters</span></span>  
 <span data-ttu-id="a8f40-111">ステートメント属性 SQL_SOPT_SS_NAME_SCOPE の値が既定値の SQL_SS_NAME_SCOPE_TABLE ではなく SQL_SS_NAME_SCOPE_TABLE_TYPE の場合、SQLPrimaryKeys はテーブル型の主キー列に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="a8f40-111">If the statement attribute SQL_SOPT_SS_NAME_SCOPE has the value SQL_SS_NAME_SCOPE_TABLE_TYPE, rather than its default value of SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys will return information about primary key columns of table types.</span></span> <span data-ttu-id="a8f40-112">SQL_SOPT_SS_NAME_SCOPE の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8f40-112">For more information on SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="a8f40-113">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8f40-113">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f40-114">参照</span><span class="sxs-lookup"><span data-stu-id="a8f40-114">See Also</span></span>  
 <span data-ttu-id="a8f40-115">[SQLPrimaryKeys 関数](https://go.microsoft.com/fwlink/?LinkId=59361) </span><span class="sxs-lookup"><span data-stu-id="a8f40-115">[SQLPrimaryKeys Function](https://go.microsoft.com/fwlink/?LinkId=59361) </span></span>  
 [<span data-ttu-id="a8f40-116">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="a8f40-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
