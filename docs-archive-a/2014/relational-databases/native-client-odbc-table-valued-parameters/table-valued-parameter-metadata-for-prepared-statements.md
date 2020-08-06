---
title: 準備されたステートメントのテーブル値パラメーターのメタデータ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: rothja
ms.author: jroth
ms.openlocfilehash: ad1394bd5e5bedc69a98308ba67a98434559c146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741945"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a><span data-ttu-id="23184-102">準備されたステートメント用のテーブル値パラメーターのメタデータ</span><span class="sxs-lookup"><span data-stu-id="23184-102">Table-Valued Parameter Metadata for Prepared Statements</span></span>
  <span data-ttu-id="23184-103">アプリケーションでは、SQLNumParams と SQLDescribeParam を使用して、準備されたプロシージャ呼び出しのメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="23184-103">An application can obtain metadata for a prepared procedure call through SQLNumParams and SQLDescribeParam.</span></span> <span data-ttu-id="23184-104">テーブル値パラメーターの場合、 *DataTypePtr*は SQL_SS_TABLE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="23184-104">For table-valued parameters, *DataTypePtr* is set to SQL_SS_TABLE.</span></span> <span data-ttu-id="23184-105">追加のメタデータは、SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME の SQLGetDescField を通じて入手できます。</span><span class="sxs-lookup"><span data-stu-id="23184-105">Additional metadata is available through SQLGetDescField for SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME.</span></span>  
  
 <span data-ttu-id="23184-106">SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME を SQLColumns と共に使用すると、テーブル値パラメーターに関連付けられているテーブル型の列のメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="23184-106">SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can be used with SQLColumns to obtain column metadata for table types associated with table-valued parameters.</span></span> <span data-ttu-id="23184-107">この場合、SQLColumns が呼び出される前に、SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_TABLE_TYPE に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23184-107">In this case, SQL_SOPT_SS_NAME_SCOPE must be set to SQL_SS_NAME_SCOPE_TABLE_TYPE before SQLColumns is called.</span></span> <span data-ttu-id="23184-108">その後、アプリケーションでテーブル値パラメーターの列のメタデータの取得が完了したら、SQL_SOPT_SS_NAME_SCOPE を既定値の SQL_SS_NAME_SCOPE_TABLE に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="23184-108">SQL_SOPT_SS_NAME_SCOPE should then be set back to the default value, SQL_SS_NAME_SCOPE_TABLE, when the application has finished retrieving table-valued parameter column metadata.</span></span>  
  
 <span data-ttu-id="23184-109">SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME は、CLR ユーザー定義型パラメーターでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="23184-109">SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can also be used with CLR user-defined type parameters.</span></span>  
  
 <span data-ttu-id="23184-110">ストアド プロシージャ呼び出しではない準備されたステートメント用にテーブル値パラメーターのメタデータを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="23184-110">You cannot obtain table-valued parameter metadata for prepared statements that are not stored procedure calls.</span></span> <span data-ttu-id="23184-111">取得しようとすると、アプリケーションから SQLSTATE 42000 で "構文エラーまたはアクセス違反です" というメッセージの SQL_ERROR が返されます。</span><span class="sxs-lookup"><span data-stu-id="23184-111">If you try to do this, the application returns SQL_ERROR with SQLSTATE 42000 and the message "Syntax error or access violation".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23184-112">参照</span><span class="sxs-lookup"><span data-stu-id="23184-112">See Also</span></span>  
 [<span data-ttu-id="23184-113">テーブル値パラメーター &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="23184-113">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
