---
title: スパース列のサポート (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 076709f3f37e92492f7c3f8c20ee692416d9e867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718074"
---
# <a name="sparse-columns-support-odbc"></a><span data-ttu-id="b5876-102">スパース列のサポート (ODBC)</span><span class="sxs-lookup"><span data-stu-id="b5876-102">Sparse Columns Support (ODBC)</span></span>
  <span data-ttu-id="b5876-103">このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC でのスパース列のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b5876-103">This topic describes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC support for sparse columns.</span></span> <span data-ttu-id="b5876-104">スパース列の ODBC サポートを示すサンプルについては、「[スパース列を含むテーブルでの SQLColumns の呼び出し](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5876-104">For a sample demonstrating ODBC support for sparse columns, see [Call SQLColumns on a Table with Sparse Columns](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md).</span></span> <span data-ttu-id="b5876-105">スパース列の詳細については、「 [SQL Server Native Client でのスパース列のサポート](../features/sparse-columns-support-in-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5876-105">For more information about sparse columns, see [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).</span></span>  
  
## <a name="statement-metadata"></a><span data-ttu-id="b5876-106">ステートメント メタデータ</span><span class="sxs-lookup"><span data-stu-id="b5876-106">Statement Metadata</span></span>  
 <span data-ttu-id="b5876-107">アプリケーション パラメーター記述子 (APD) の記述子フィールドと SQL_SOPT_SS_NAME_SCOPE ステートメント属性は、追加の値 SQL_SS_NAME_SCOPE_EXTENDED および SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="b5876-107">The application parameter descriptor (APD) descriptor field and SQL_SOPT_SS_NAME_SCOPE statement attribute accepts the additional values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span> <span data-ttu-id="b5876-108">これらの値は、 [sqlcolumns](../../native-client-odbc-api/sqlcolumns.md)によって返される結果セットに含める列を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5876-108">These values specify which columns are included in the result set returned by [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span> <span data-ttu-id="b5876-109">SQL_SOPT_SS_NAME_SCOPE の詳細については、「 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5876-109">For more information about SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="b5876-110">新しい実装行記述子 (IRD) の、SQL_CA_SS_IS_COLUMN_SET という名前の読み取り専用 SQLSMALLINT フィールドを使用して、列が XML `column_set` 値かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b5876-110">A new implementation row descriptor (IRD), a read-only SQLSMALLINT field called SQL_CA_SS_IS_COLUMN_SET, can be used to determine if a column is an XML `column_set` value.</span></span> <span data-ttu-id="b5876-111">SQL_CA_SS_IS_COLUMN_SET は、値 SQL_TRUE および SQL_FALSE を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b5876-111">SQL_CA_SS_IS_COLUMN_SET takes the values SQL_TRUE and SQL_FALSE.</span></span>  
  
## <a name="catalog-metadata"></a><span data-ttu-id="b5876-112">カタログ メタデータ</span><span class="sxs-lookup"><span data-stu-id="b5876-112">Catalog Metadata</span></span>  
 <span data-ttu-id="b5876-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Sqlcolumns](../../native-client-odbc-api/sqlcolumns.md)の結果セットには、2つの特定の列 (SS_IS_SPARSE と SS_IS_COLUMN_SET) が追加されています。</span><span class="sxs-lookup"><span data-stu-id="b5876-113">Two [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific columns (SS_IS_SPARSE and SS_IS_COLUMN_SET) have been added to the result set for [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="odbc-function-support-for-sparse-columns"></a><span data-ttu-id="b5876-114">ODBC 関数によるスパース列のサポート</span><span class="sxs-lookup"><span data-stu-id="b5876-114">ODBC Function Support for Sparse Columns</span></span>  
 <span data-ttu-id="b5876-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client でスパース列をサポートするために、次の ODBC 関数が更新されました。</span><span class="sxs-lookup"><span data-stu-id="b5876-115">The following ODBC functions have been updated to support sparse columns in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   [<span data-ttu-id="b5876-116">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="b5876-116">SQLColAttribute</span></span>](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="b5876-117">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="b5876-117">SQLColumns</span></span>](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="b5876-118">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="b5876-118">SQLGetDescField</span></span>](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [<span data-ttu-id="b5876-119">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="b5876-119">SQLSetDescField</span></span>](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [<span data-ttu-id="b5876-120">SQLSetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="b5876-120">SQLSetStmtAttr</span></span>](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5876-121">参照</span><span class="sxs-lookup"><span data-stu-id="b5876-121">See Also</span></span>  
 [<span data-ttu-id="b5876-122">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="b5876-122">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
