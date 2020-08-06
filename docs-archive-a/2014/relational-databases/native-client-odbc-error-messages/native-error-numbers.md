---
title: ネイティブエラー番号 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7232a921027246c3ceb7d0ae1ffd5efbd3672895
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714341"
---
# <a name="native-error-numbers"></a><span data-ttu-id="de7e6-102">ネイティブ エラー番号</span><span class="sxs-lookup"><span data-stu-id="de7e6-102">Native Error Numbers</span></span>
  <span data-ttu-id="de7e6-103">データソースで発生したエラー (によって返される) の場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーは、によって返されたネイティブエラー番号を返し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="de7e6-103">For errors that occur in the data source (returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns the native error number returned to it by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de7e6-104">ドライバーによって検出されたエラーの場合、native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLIENT ODBC ドライバーは、ネイティブエラー番号0を返します。</span><span class="sxs-lookup"><span data-stu-id="de7e6-104">For errors detected by the driver, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns a native error number of 0.</span></span> <span data-ttu-id="de7e6-105">ネイティブエラー番号の一覧の詳細については、の**master**データベースにある**sysmessages**システムテーブルの error 列を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="de7e6-105">For more information about a list of native error numbers, see the error column of the **sysmessages** system table in the **master** database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="de7e6-106">状態エラーコードの詳細については、「 [SQLSTATE &#40;ODBC エラーコード&#41;](sqlstate-odbc-error-codes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7e6-106">For information about the state error codes, see [SQLSTATE &#40;ODBC Error Codes&#41;](sqlstate-odbc-error-codes.md).</span></span> <span data-ttu-id="de7e6-107">Net-Library から返されたエラーについては、ネイティブ エラー番号は基になるネットワーク ソフトウェアから返されます。</span><span class="sxs-lookup"><span data-stu-id="de7e6-107">For errors returned by the Net-Library, the native error number is from the underlying network software.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7e6-108">参照</span><span class="sxs-lookup"><span data-stu-id="de7e6-108">See Also</span></span>  
 [<span data-ttu-id="de7e6-109">エラーとメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="de7e6-109">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
