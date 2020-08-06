---
title: SQLGetTypeInfo |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b2bca833eeed5e51237347a5ea118d839dd36de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645041"
---
# <a name="sqlgettypeinfo"></a><span data-ttu-id="c6458-102">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="c6458-102">SQLGetTypeInfo</span></span>
  <span data-ttu-id="c6458-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、の結果セットに列 USERTYPE を追加して報告し `SQLGetTypeInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="c6458-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver reports the additional column USERTYPE in the result set of `SQLGetTypeInfo`.</span></span> <span data-ttu-id="c6458-104">USERTYPE には DB-Library データ型の定義が示されるので、既存の DB-Library アプリケーションを ODBC に移植する開発者にとって便利です。</span><span class="sxs-lookup"><span data-stu-id="c6458-104">USERTYPE reports the DB-Library data type definition and is useful to developers porting existing DB-Library applications to ODBC.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c6458-105">では ID が属性として処理されますが、ODBC ではデータ型として処理されます。</span><span class="sxs-lookup"><span data-stu-id="c6458-105">treats identity as an attribute, whereas ODBC treats it as a data type.</span></span> <span data-ttu-id="c6458-106">この不一致を解決するために、は `SQLGetTypeInfo` データ型**intidentity**、 **smallintidentity**、 **tinyintidentity**、 **decimalidentity**、および**numericidentity**を返します。</span><span class="sxs-lookup"><span data-stu-id="c6458-106">To resolve this mismatch, `SQLGetTypeInfo` returns the data types: **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity**, and **numericidentity**.</span></span> <span data-ttu-id="c6458-107">`SQLGetTypeInfo`結果セット列 AUTO_UNIQUE_VALUE は、これらのデータ型の値 TRUE を報告します。</span><span class="sxs-lookup"><span data-stu-id="c6458-107">The `SQLGetTypeInfo` result set column AUTO_UNIQUE_VALUE reports the value TRUE for these data types.</span></span>  
  
 <span data-ttu-id="c6458-108">**Varchar**、 **nvarchar** 、および**Varbinary**の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、実際には無制限であるにもかかわらず、COLUMN_SIZE の値に対してそれぞれ8000、4000、および8000を報告し続けます。</span><span class="sxs-lookup"><span data-stu-id="c6458-108">For **varchar**, **nvarchar** and **varbinary**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver continues to report 8000, 4000 and 8000 respectively for the COLUMN_SIZE value, even though it is actually unlimited.</span></span> <span data-ttu-id="c6458-109">これにより、旧バージョンとの互換性が確保されます。</span><span class="sxs-lookup"><span data-stu-id="c6458-109">This is to ensure backward compatibility.</span></span>  
  
 <span data-ttu-id="c6458-110">**Xml**データ型の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、サイズを無制限に示す COLUMN_SIZE の SQL_SS_LENGTH_UNLIMITED を報告します。</span><span class="sxs-lookup"><span data-stu-id="c6458-110">For the **xml** data type, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver reports SQL_SS_LENGTH_UNLIMITED for COLUMN_SIZE to denote unlimited size.</span></span>  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a><span data-ttu-id="c6458-111">SQLGetTypeInfo とテーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6458-111">SQLGetTypeInfo and Table-Valued Parameters</span></span>  
 <span data-ttu-id="c6458-112">テーブル値パラメーターのテーブル型は、実質的には、他の型を定義するために使用される型であるメタ型です。</span><span class="sxs-lookup"><span data-stu-id="c6458-112">The table type for table-valued parameters is effectively a meta-type-that is, a type used to define other types.</span></span> <span data-ttu-id="c6458-113">そのため、SQLGetTypeInfo を介して公開する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c6458-113">Therefore, it does not have to be exposed through SQLGetTypeInfo.</span></span> <span data-ttu-id="c6458-114">アプリケーションでは、テーブル値パラメーターで使用されるテーブル型のメタデータを取得するために、SQLGetTypeInfo ではなく SQLTables を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6458-114">Applications must use SQLTables, rather than SQLGetTypeInfo, to retrieve metadata for table types used with table-valued parameters.</span></span>  
  
 <span data-ttu-id="c6458-115">テーブル値パラメーターのメタデータの取得の詳細については、「[テーブル値パラメーターに影響を与えるステートメント属性](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6458-115">For more information, about retrieving metdata for table-valued parameters, see [Statement Attributes that Affect Table-Valued Parameters](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).</span></span>  
  
 <span data-ttu-id="c6458-116">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6458-116">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="c6458-117">SQLGetTypeInfo による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="c6458-117">SQLGetTypeInfo Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="c6458-118">日付型または時刻型に対して返される値については、「[カタログメタデータ](../native-client-odbc-date-time/metadata-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6458-118">For the values returned for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="c6458-119">一般的な情報については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6458-119">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a><span data-ttu-id="c6458-120">SQLGetTypeInfo による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="c6458-120">SQLGetTypeInfo Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="c6458-121">`SQLGetTypeInfo` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c6458-121">`SQLGetTypeInfo` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="c6458-122">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6458-122">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6458-123">参照</span><span class="sxs-lookup"><span data-stu-id="c6458-123">See Also</span></span>  
 <span data-ttu-id="c6458-124">[SQLGetTypeInfo 関数](https://go.microsoft.com/fwlink/?LinkId=59356) </span><span class="sxs-lookup"><span data-stu-id="c6458-124">[SQLGetTypeInfo Function](https://go.microsoft.com/fwlink/?LinkId=59356) </span></span>  
 [<span data-ttu-id="c6458-125">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="c6458-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
