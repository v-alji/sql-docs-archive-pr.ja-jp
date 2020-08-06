---
title: テーブル値パラメーターの ODBC SQL 型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: rothja
ms.author: jroth
ms.openlocfilehash: c8ed46bf117c9158ae5b60c10ebd89e3d348f77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643819"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a><span data-ttu-id="f9eb3-102">テーブル値パラメーター用の ODBC SQL 型</span><span class="sxs-lookup"><span data-stu-id="f9eb3-102">ODBC SQL Type for Table-Valued Parameters</span></span>
  <span data-ttu-id="f9eb3-103">テーブル値パラメーターは、新しい ODBC SQL 型である SQL_SS_TABLE でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-103">Support for table-valued parameters is provided by a new ODBC SQL type, SQL_SS_TABLE.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9eb3-104">解説</span><span class="sxs-lookup"><span data-stu-id="f9eb3-104">Remarks</span></span>  
 <span data-ttu-id="f9eb3-105">SQL_SS_TABLE は、他の ODBC データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できません。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-105">SQL_SS_TABLE cannot be converted to any other ODBC or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="f9eb3-106">SQL_SS_TABLE が SQLBindParameter の*ValueType*パラメーターで C データ型として使用されている場合、またはアプリケーションパラメーター記述子 (APD) レコードの SQL_DESC_TYPE を SQL_SS_TABLE に設定しようとした場合、SQL_ERROR が返され、"アプリケーションバッファーの種類が無効です" という内容の診断レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-106">If SQL_SS_TABLE is used as a C data type in the *ValueType* parameter of SQLBindParameter, or an attempt is made to set SQL_DESC_TYPE in an application parameter descriptor (APD) record to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="f9eb3-107">IPD レコードで SQL_DESC_TYPE を SQL_SS_TABLE に設定し、対応するアプリケーション パラメーター記述子レコードが SQL_C_DEFAULT ではない場合、SQL_ERROR が返され、"アプリケーションのバッファー型が無効です" というメッセージで SQLSTATE=HY003 の診断レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-107">If SQL_DESC_TYPE is set to SQL_SS_TABLE in an IPD record and the corresponding application parameter descriptor record is not SQL_C_DEFAULT, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span> <span data-ttu-id="f9eb3-108">これは、SQLSetDescField、SQLSetDescRec、または SQLBindParameter の*ParameterType*で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-108">This can occur with the *ParameterType* of a SQLSetDescField, SQLSetDescRec or SQLBindParameter.</span></span>  
  
 <span data-ttu-id="f9eb3-109">SQLGetData を呼び出すときに*TargetType*パラメーターが SQL_SS_TABLE 場合、SQL_ERROR が返され、"アプリケーションバッファーの種類が無効です" という SQLSTATE = HY003 の診断レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-109">If the *TargetType* parameter is SQL_SS_TABLE when calling SQLGetData, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="f9eb3-110">テーブル値パラメーターの列は、SQL_SS_TABLE 型としてバインドできません。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-110">A table-valued parameter column cannot be bound as type SQL_SS_TABLE.</span></span> <span data-ttu-id="f9eb3-111">`SQLBindParameter` *ParameterType*を SQL_SS_TABLE に設定してを呼び出した場合、SQL_ERROR が返され、"SQL データ型が無効です" という SQLSTATE = HY004 の診断レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-111">If `SQLBindParameter` is called with *ParameterType* set to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY004, "Invalid SQL data type".</span></span> <span data-ttu-id="f9eb3-112">これは、SQLSetDescField および SQLSetDescRec でも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-112">This can also occur with SQLSetDescField and SQLSetDescRec.</span></span>  
  
 <span data-ttu-id="f9eb3-113">テーブル値パラメーターの列の値には、パラメーターおよび結果列と同じデータ変換オプションが設定されています。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-113">Table-valued parameter column values have the same data conversion options as parameters and result columns.</span></span>  
  
 <span data-ttu-id="f9eb3-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、テーブル値パラメーターは入力パラメーターのみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-114">A table-valued parameter can only be an input parameter in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="f9eb3-115">SQLBindParameter または SQLSetDescField を介して SQL_PARAM_INPUT 以外の値に SQL_DESC_PARAMETER_TYPE を設定しようとすると、SQL_ERROR が返され、SQLSTATE = HY105 のステートメントに診断レコードが追加され、"パラメーターの型が無効です" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-115">If an attempt is made to set SQL_DESC_PARAMETER_TYPE to a value other than SQL_PARAM_INPUT via SQLBindParameter or SQLSetDescField, SQL_ERROR is returned and a diagnostic record is added to the statement with SQLSTATE=HY105 and the message "Invalid parameter type".</span></span>  
  
 <span data-ttu-id="f9eb3-116">テーブル値パラメーターでは、行ごとの既定値はサポートされていないので、テーブル値パラメーターの列は*StrLen_or_IndPtr*で SQL_DEFAULT_PARAM を使用できません。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-116">Table-valued parameter columns cannot use SQL_DEFAULT_PARAM in *StrLen_or_IndPtr*, because per-row default values are not supported with table-valued parameters.</span></span> <span data-ttu-id="f9eb3-117">代わりに、アプリケーションで列の属性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE を 1 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-117">Instead, an application can set the column attribute SQL_CA_SS_COL_HAS_DEFAULT_VALUE to 1.</span></span> <span data-ttu-id="f9eb3-118">つまり、この列にすべての行の既定値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-118">This means that the column will have default values for all rows.</span></span> <span data-ttu-id="f9eb3-119">*StrLen_or_IndPtr*が SQL_DEFAULT_PARAM に設定されている場合、sqlexecute または SQLExecDirect は SQL_ERROR を返し、メッセージ "文字列またはバッファーの長さが無効です" というメッセージで SQLSTATE = HY090 のステートメントに診断レコードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="f9eb3-119">If *StrLen_or_IndPtr* is set to SQL_DEFAULT_PARAM, SQLExecute or SQLExecDirect will return SQL_ERROR, and a diagnostic record will be added to the statement with SQLSTATE=HY090 and the message "Invalid string or buffer length".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9eb3-120">参照</span><span class="sxs-lookup"><span data-stu-id="f9eb3-120">See Also</span></span>  
 [<span data-ttu-id="f9eb3-121">テーブル値パラメーター &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="f9eb3-121">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
