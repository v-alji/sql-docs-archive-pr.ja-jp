---
title: Sql特殊列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
ms.openlocfilehash: c36ff73606e95ed7ee5e713b81acf7c177a42563
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640921"
---
# <a name="sqlspecialcolumns"></a><span data-ttu-id="baa6e-102">SQLSpecialColumns</span><span class="sxs-lookup"><span data-stu-id="baa6e-102">SQLSpecialColumns</span></span>
  <span data-ttu-id="baa6e-103">行識別子 (*Identifiertype* SQL_BEST_ROWID) を要求すると、 **Sqlている列**は、SQL_SCOPE_CURROW 以外の要求されたスコープに対して空の結果セット (データ行がない) を返します。</span><span class="sxs-lookup"><span data-stu-id="baa6e-103">When requesting row identifiers (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** returns an empty result set (no data rows) for any requested scope other than SQL_SCOPE_CURROW.</span></span> <span data-ttu-id="baa6e-104">生成される結果セットは、列がこのスコープ内でのみ有効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="baa6e-104">The generated result set indicates that the columns are only valid within this scope.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="baa6e-105">では、識別子の擬似列がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="baa6e-105">does not support pseudocolumns for identifiers.</span></span> <span data-ttu-id="baa6e-106">**Sql特殊列**の結果セットでは、すべての列が SQL_PC_NOT_PSEUDO として識別されます。</span><span class="sxs-lookup"><span data-stu-id="baa6e-106">The **SQLSpecialColumns** result set will identify all columns as SQL_PC_NOT_PSEUDO.</span></span>  
  
 <span data-ttu-id="baa6e-107">**Sql特殊な列**は、静的カーソルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="baa6e-107">**SQLSpecialColumns** can be executed on a static cursor.</span></span> <span data-ttu-id="baa6e-108">更新可能な (キーセットドリブンまたは動的) で**sqlsp_helptext 列**を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="baa6e-108">An attempt to execute **SQLSpecialColumns** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type has been changed.</span></span>  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="baa6e-109">SQLSpecialColumns による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="baa6e-109">SQLSpecialColumns Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="baa6e-110">日付型または時刻型の列 DATA_TYPE、TYPE_NAME、COLUMN_SIZE、BUFFER_LENGTH、および DECIMAL_DIGTS に対して返される値の詳細については、「[カタログメタデータ](../native-client-odbc-date-time/metadata-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="baa6e-110">For information about the values returned for the columns DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH, and DECIMAL_DIGTS for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="baa6e-111">一般的な情報については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="baa6e-111">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a><span data-ttu-id="baa6e-112">SQLSpecialColumns による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="baa6e-112">SQLSpecialColumns Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="baa6e-113">**Sqlxl 列**では、大きな CLR ユーザー定義型 (udt) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="baa6e-113">**SQLSpecialColumns** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="baa6e-114">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="baa6e-114">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa6e-115">参照</span><span class="sxs-lookup"><span data-stu-id="baa6e-115">See Also</span></span>  
 <span data-ttu-id="baa6e-116">[Sql特殊列関数](https://go.microsoft.com/fwlink/?LinkId=59371) </span><span class="sxs-lookup"><span data-stu-id="baa6e-116">[SQLSpecialColumns Function](https://go.microsoft.com/fwlink/?LinkId=59371) </span></span>  
 [<span data-ttu-id="baa6e-117">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="baa6e-117">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
