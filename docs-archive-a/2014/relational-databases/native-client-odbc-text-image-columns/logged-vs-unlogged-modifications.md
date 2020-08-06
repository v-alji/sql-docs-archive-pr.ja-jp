---
title: ログ記録と Unlogged の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8768acc75d18ea2236f0e9280e5d0c805e688107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741941"
---
# <a name="logged-vs-unlogged-modifications"></a><span data-ttu-id="fe28c-102">ログに記録される変更と記録されない変更</span><span class="sxs-lookup"><span data-stu-id="fe28c-102">Logged vs. Unlogged Modifications</span></span>
  <span data-ttu-id="fe28c-103">アプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーが**text**、 **ntext**、および**image**の変更をログに記録しないように要求できます。</span><span class="sxs-lookup"><span data-stu-id="fe28c-103">An application can request that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver not log **text**, **ntext**, and **image** modifications.</span></span> <span data-ttu-id="fe28c-104">ただし、このオプションの使用には注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="fe28c-104">Care should be used with this option, however.</span></span> <span data-ttu-id="fe28c-105">**Text**型、 **ntext**型、または**image**型のデータが重要ではなく、データ所有者がデータを回復してパフォーマンスを向上させることができない場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="fe28c-105">It should be used only for those situations where the **text**, **ntext**, or **image** data is not critical and data owners are willing to trade off the ability to recover data for higher performance.</span></span>  
  
 <span data-ttu-id="fe28c-106">**Text**、 **ntext**、および**image**の変更のログ記録は、*属性*パラメーターを SQL_SOPT_SS_ TEXTPTR_LOGGING に設定し、 *valueptr*を SQL_TL_ON または SQL_TL_OFF に設定して、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="fe28c-106">The logging of **text**, **ntext**, and **image** modifications is controlled by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with the *Attribute* parameter set to SQL_SOPT_SS_ TEXTPTR_LOGGING and *ValuePtr* set to either SQL_TL_ON or SQL_TL_OFF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe28c-107">参照</span><span class="sxs-lookup"><span data-stu-id="fe28c-107">See Also</span></span>  
 [<span data-ttu-id="fe28c-108">text 列と image 列の管理</span><span class="sxs-lookup"><span data-stu-id="fe28c-108">Managing Text and Image Columns</span></span>](managing-text-and-image-columns.md)  
  
  
