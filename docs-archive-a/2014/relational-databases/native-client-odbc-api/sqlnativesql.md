---
title: SQLNativeSql |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: rothja
ms.author: jroth
ms.openlocfilehash: 433b086dc36a79cb82868edebac9f0a4814c21fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645027"
---
# <a name="sqlnativesql"></a><span data-ttu-id="b306a-102">SQLNativeSql</span><span class="sxs-lookup"><span data-stu-id="b306a-102">SQLNativeSql</span></span>
  <span data-ttu-id="b306a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、サーバーにアクセスせずに **SQLNativeSql** 要求に応じます。</span><span class="sxs-lookup"><span data-stu-id="b306a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver satisfies **SQLNativeSql** requests without visiting the server.</span></span> <span data-ttu-id="b306a-104">この関数を使用すると、SQL ステートメントの構文を効率的にテストできます。</span><span class="sxs-lookup"><span data-stu-id="b306a-104">The function efficiently tests the syntax of SQL statements.</span></span> <span data-ttu-id="b306a-105">構文チェックでは、識別子または SQL ステートメント内の式の結果が有効かどうかは判断されないので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLNativeSql **によって返された** ネイティブ SQL を実行すると失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="b306a-105">Syntax checking does not determine if identifiers or the results of expressions in the SQL statements are valid, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native SQL returned by **SQLNativeSql** can fail to run.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b306a-106">参照</span><span class="sxs-lookup"><span data-stu-id="b306a-106">See Also</span></span>  
 <span data-ttu-id="b306a-107">[SQLNativeSql 関数](https://go.microsoft.com/fwlink/?LinkID=59358) </span><span class="sxs-lookup"><span data-stu-id="b306a-107">[SQLNativeSql Function](https://go.microsoft.com/fwlink/?LinkID=59358) </span></span>  
 [<span data-ttu-id="b306a-108">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="b306a-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
