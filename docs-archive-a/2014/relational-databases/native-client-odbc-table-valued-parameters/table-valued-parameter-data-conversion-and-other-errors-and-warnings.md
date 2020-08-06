---
title: テーブル値パラメーターのデータ変換およびその他のエラーと警告 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: rothja
ms.author: jroth
ms.openlocfilehash: 45b9ba7f91b54548e096bbe47da6e01ba562f59d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631853"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a><span data-ttu-id="9c400-102">テーブル値パラメーターのデータ変換およびその他のエラーと警告</span><span class="sxs-lookup"><span data-stu-id="9c400-102">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>
  <span data-ttu-id="9c400-103">テーブル値パラメーターの列の値は、他の列やパラメーターの値と同じ方法で、クライアントのデータ型とサーバーのデータ型間で変換できます。</span><span class="sxs-lookup"><span data-stu-id="9c400-103">Table-valued parameter column values can be converted between client and server data types in the same way as other column and parameter values.</span></span> <span data-ttu-id="9c400-104">ただし、テーブル値パラメーターには複数の列と複数の行を含めることができるため、エラーが発生した箇所の実際の値を識別できることが重要です。</span><span class="sxs-lookup"><span data-stu-id="9c400-104">But because a table-valued parameter can contain multiple columns and multiple rows, it is important to be able to identify the actual value where the error occurred.</span></span>  
  
 <span data-ttu-id="9c400-105">テーブル値パラメーターの列でエラーまたは警告が検出された場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client によって診断レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c400-105">When an error or warning is detected in a table-valued parameter column, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will generate a diagnostic record.</span></span> <span data-ttu-id="9c400-106">エラー メッセージには、テーブル値パラメーターのパラメーター番号に加え、列序数と行番号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c400-106">The error message will contain the parameter number of the table-valued parameter, plus the column ordinal and row number.</span></span> <span data-ttu-id="9c400-107">アプリケーションでは、診断レコード内の SQL_DIAG_SS_TABLE_COLUMN_NUMBER および SQL_DIAG_SS_TABLE_ROW_NUMBER という診断フィールドを使用して、エラーと警告に関連付けられている値を特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c400-107">An application can also use the diagnostic fields SQL_DIAG_SS_TABLE_COLUMN_NUMBER and SQL_DIAG_SS_TABLE_ROW_NUMBER within diagnostic records to determine which values are associated with errors and warnings.</span></span> <span data-ttu-id="9c400-108">これらの診断フィールドは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c400-108">These diagnostic fields are available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span>  
  
 <span data-ttu-id="9c400-109">診断レコードの SQLSTATE コンポーネントとメッセージ コンポーネントは、他のすべての点で既存の ODBC の動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="9c400-109">The SQLSTATE and message components of diagnostic records will conform to existing ODBC behavior in all other respects.</span></span> <span data-ttu-id="9c400-110">つまり、パラメーター、行、および列の識別情報を除き、テーブル値パラメーター以外のパラメーターの場合と同じように、エラーメッセージにはテーブル値パラメーターの値が同じになります。</span><span class="sxs-lookup"><span data-stu-id="9c400-110">That is, except for the parameter, row, and column identification information, error messages have the same values for table-valued parameters as they would for non-table-valued parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c400-111">参照</span><span class="sxs-lookup"><span data-stu-id="9c400-111">See Also</span></span>  
 [<span data-ttu-id="9c400-112">テーブル値パラメーター &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="9c400-112">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
