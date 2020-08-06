---
title: 実行時データと Text、ntext、または Image 型の列 |Microsoft Docs
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
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 404fade34862fe4705ec440eef7f466a9073250b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741961"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a><span data-ttu-id="3c21d-102">実行時データと text 型、ntext 型、または image 型の列</span><span class="sxs-lookup"><span data-stu-id="3c21d-102">Data-at-Execution and Text, ntext, or Image Columns</span></span>
  <span data-ttu-id="3c21d-103">ODBC 実行時データは、バインドされた列やパラメーターに対して、アプリケーションが大量のデータを操作できるようにする機能です。</span><span class="sxs-lookup"><span data-stu-id="3c21d-103">ODBC data-at-execution is a feature that enables applications to work with extremely large amounts of data on bound columns or parameters.</span></span> <span data-ttu-id="3c21d-104">非常に大きな**text**型、 **ntext**型、または**image**型の列を取得する場合、アプリケーションは単純に大きなバッファーを割り当てて、その列をバッファーにバインドし、行をフェッチすることができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c21d-104">When retrieving very large **text**, **ntext**, or **image** columns, an application may not be able to simply allocate a huge buffer, bind the column into the buffer, and fetch the row.</span></span> <span data-ttu-id="3c21d-105">非常に大きな**text**型、 **ntext**型、または**image**型の列を更新する場合、アプリケーションは単純に大きなバッファーを割り当てて、それを SQL ステートメントのパラメーターマーカーにバインドした後、ステートメントを実行できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c21d-105">When updating very large **text**, **ntext**, or **image** columns, the application might not be able to simply allocate a huge buffer, bind it to a parameter marker in an SQL statement, and then execute the statement.</span></span> <span data-ttu-id="3c21d-106">このような場合、アプリケーションでは、実行時データオプションを使用して[SQLGetData](../native-client-odbc-api/sqlgetdata.md)または[sqlputdata](../native-client-odbc-api/sqlputdata.md)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c21d-106">In these cases, the application must use [SQLGetData](../native-client-odbc-api/sqlgetdata.md) or [SQLPutData](../native-client-odbc-api/sqlputdata.md) with its data-at-execution options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c21d-107">参照</span><span class="sxs-lookup"><span data-stu-id="3c21d-107">See Also</span></span>  
 [<span data-ttu-id="3c21d-108">text 列と image 列の管理</span><span class="sxs-lookup"><span data-stu-id="3c21d-108">Managing Text and Image Columns</span></span>](managing-text-and-image-columns.md)  
  
  
