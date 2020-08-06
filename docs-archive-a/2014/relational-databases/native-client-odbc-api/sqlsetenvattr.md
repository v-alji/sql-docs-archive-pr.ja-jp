---
title: SQLSetEnvAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: rothja
ms.author: jroth
ms.openlocfilehash: f0dbd4d01de9ca769c46a93f810f0149f5b86981
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645005"
---
# <a name="sqlsetenvattr"></a><span data-ttu-id="b49ae-102">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="b49ae-102">SQLSetEnvAttr</span></span>
  <span data-ttu-id="b49ae-103">Odbc[プログラマーズリファレンス](https://go.microsoft.com/fwlink/?LinkId=45250)では、odbc ドライバーが odbc 2 に書き込まれたアプリケーションから**SQLSetEnvAttr**属性の仕様を解釈する方法を定義します。*x*または ODBC 3。*x* API。</span><span class="sxs-lookup"><span data-stu-id="b49ae-103">The [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250) defines how ODBC drivers should interpret the **SQLSetEnvAttr** attribute specifications from applications written to either the ODBC 2.*x* or ODBC 3.*x* API.</span></span> <span data-ttu-id="b49ae-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、これらの規則に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="b49ae-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with those rules.</span></span>  
  
 <span data-ttu-id="b49ae-105">**SQLSetEnvAttr**によって制御される属性の1つは、接続プールを使用するかどうかです。</span><span class="sxs-lookup"><span data-stu-id="b49ae-105">One of the attributes controlled by **SQLSetEnvAttr** is whether connection pooling is to be used.</span></span> <span data-ttu-id="b49ae-106">Native Client ODBC ドライバーで接続プールを使用する場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [SQLDriverConnect](sqldriverconnect.md)または**SQLConnect**を使用して接続するときに、 *drivercompletion*パラメーターを SQL_DRIVER_NOPROMPT に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b49ae-106">If connection pooling is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, the *DriverCompletion* parameter must be set to SQL_DRIVER_NOPROMPT when connecting with either [SQLDriverConnect](sqldriverconnect.md) or **SQLConnect**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b49ae-107">参照</span><span class="sxs-lookup"><span data-stu-id="b49ae-107">See Also</span></span>  
 <span data-ttu-id="b49ae-108">[SQLSetEnvAttr 関数](https://go.microsoft.com/fwlink/?LinkId=59369) </span><span class="sxs-lookup"><span data-stu-id="b49ae-108">[SQLSetEnvAttr Function](https://go.microsoft.com/fwlink/?LinkId=59369) </span></span>  
 [<span data-ttu-id="b49ae-109">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="b49ae-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
