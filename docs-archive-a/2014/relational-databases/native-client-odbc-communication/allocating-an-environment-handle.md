---
title: 環境ハンドルを割り当てる |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c655b5e9a406c3e1881c9dd199a92666377918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642065"
---
# <a name="allocating-an-environment-handle"></a><span data-ttu-id="66a82-102">環境ハンドルの割り当て</span><span class="sxs-lookup"><span data-stu-id="66a82-102">Allocating an Environment Handle</span></span>
  <span data-ttu-id="66a82-103">どの ODBC 関数をアプリケーションから呼び出す場合でも、呼び出す前に ODBC 環境を初期化して環境ハンドルを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="66a82-103">Before an application can call any ODBC function, it must initialize the ODBC environment and allocate an environment handle.</span></span> <span data-ttu-id="66a82-104">環境ハンドルはグローバルなコンテキスト ハンドルで、ODBC の他のハンドルのプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="66a82-104">This is the global context handle and placeholder for the other handles in ODBC.</span></span> <span data-ttu-id="66a82-105">これを行うには、 *Handletype*パラメーターを SQL_HANDLE_ENV に設定し、 *InputHandle*を SQL_NULL_HANDLE に設定して、 **SQLAllocHandle**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="66a82-105">You do this by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_ENV and *InputHandle* set to SQL_NULL_HANDLE.</span></span>  
  
 <span data-ttu-id="66a82-106">環境ハンドルを割り当てたら、使用する ODBC 関数呼び出しのバージョンを指定する環境属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66a82-106">After allocating the environment handle, the application must set environment attributes to indicate which version of ODBC function calls it will be using.</span></span> <span data-ttu-id="66a82-107">ODBC 3 を使用する場合はです。*x*関数は、*属性*パラメーターを SQL_ATTR_ODBC_VERSION に設定し、 *valueptr*を SQL_OV_ODBC3 に設定して、 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="66a82-107">To use the ODBC 3.*x* functions, call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) with the *Attribute* parameter set to SQL_ATTR_ODBC_VERSION and *ValuePtr* set to SQL_OV_ODBC3.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a82-108">参照</span><span class="sxs-lookup"><span data-stu-id="66a82-108">See Also</span></span>  
 [<span data-ttu-id="66a82-109">ODBC&#41;&#40;SQL Server との通信</span><span class="sxs-lookup"><span data-stu-id="66a82-109">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
