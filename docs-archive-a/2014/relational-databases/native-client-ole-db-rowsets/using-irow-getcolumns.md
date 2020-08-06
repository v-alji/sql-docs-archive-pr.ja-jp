---
title: IRow::GetColumns の使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f323dda790946565bc0dbd63c9e1f9d17ac7494b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633825"
---
# <a name="using-irowgetcolumns"></a><span data-ttu-id="3947f-102">IRow::GetColumns の使用</span><span class="sxs-lookup"><span data-stu-id="3947f-102">Using IRow::GetColumns</span></span>
  <span data-ttu-id="3947f-103">**IRow** の実装では、列に対して順方向専用の順次アクセスを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3947f-103">The **IRow** implementation allows forward-only sequential access to the columns.</span></span> <span data-ttu-id="3947f-104">**IRow::GetColumns** を 1 回だけ呼び出して、行内のすべての列にアクセスすることができます。また、行内の複数の列にアクセスするたびに、毎回 **IRow::GetColumns** を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="3947f-104">You can either access all the columns in the row with a single call to **IRow::GetColumns** or call **IRow::GetColumns** multiple times every time that you access several columns in the row.</span></span>  
  
 <span data-ttu-id="3947f-105">**IRow::GetColumns** を複数回呼び出す場合は、呼び出しが重ならないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3947f-105">The multiple calls to **IRow::GetColumns** should not overlap.</span></span> <span data-ttu-id="3947f-106">たとえば、1 回目に **IRow::GetColumns** を呼び出すときに列 1、2、3 を取得する場合、2 回目に **IRow::GetColumns** を呼び出すときには列 4、5、6 を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3947f-106">For example, if the first call to **IRow::GetColumns** retrieves columns 1, 2, and 3, the second call to **IRow::GetColumns** should call for columns 4, 5, and 6.</span></span> <span data-ttu-id="3947f-107">**IRow::GetColumns** の呼び出しが重なると、状態フラグ (DBCOLUMNACCESS の dwstatus フィールド) が DBSTATUS_E_UNAVAILABLE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3947f-107">If later calls to **IRow::GetColumns** overlap, the status flag (dwstatus field in DBCOLUMNACCESS) is set to DBSTATUS_E_UNAVAILABLE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3947f-108">参照</span><span class="sxs-lookup"><span data-stu-id="3947f-108">See Also</span></span>  
 [<span data-ttu-id="3947f-109">IRow による 1 行のフェッチ</span><span class="sxs-lookup"><span data-stu-id="3947f-109">Fetching a Single Row with IRow</span></span>](fetching-a-single-row-with-irow.md)  
  
  
