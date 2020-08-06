---
title: IRowsetFind での比較 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ad359ca4957b434c3798d1a441eb0fd57644a59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633131"
---
# <a name="comparability-for-irowsetfind"></a><span data-ttu-id="01736-102">IRowsetFind での比較</span><span class="sxs-lookup"><span data-stu-id="01736-102">Comparability for IRowsetFind</span></span>
  <span data-ttu-id="01736-103">日付型または時刻型の場合のみ、IRowsetFind では、次の比較がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="01736-103">For date/time types only, IRowsetFind supports the following comparisons:</span></span>  
  
-   <span data-ttu-id="01736-104">LT</span><span class="sxs-lookup"><span data-stu-id="01736-104">LT</span></span>  
  
-   <span data-ttu-id="01736-105">LE</span><span class="sxs-lookup"><span data-stu-id="01736-105">LE</span></span>  
  
-   <span data-ttu-id="01736-106">EQ</span><span class="sxs-lookup"><span data-stu-id="01736-106">EQ</span></span>  
  
-   <span data-ttu-id="01736-107">GE</span><span class="sxs-lookup"><span data-stu-id="01736-107">GE</span></span>  
  
-   <span data-ttu-id="01736-108">GT</span><span class="sxs-lookup"><span data-stu-id="01736-108">GT</span></span>  
  
-   <span data-ttu-id="01736-109">NE</span><span class="sxs-lookup"><span data-stu-id="01736-109">NE</span></span>  
  
-   <span data-ttu-id="01736-110">IGNORE</span><span class="sxs-lookup"><span data-stu-id="01736-110">IGNORE</span></span>  
  
 <span data-ttu-id="01736-111">その他の比較を試みると、DB_E_BADCOMPAREOP が返されます。</span><span class="sxs-lookup"><span data-stu-id="01736-111">If any other comparison is attempted, DB_E_BADCOMPAREOP is returned.</span></span> <span data-ttu-id="01736-112">これは OLE DB 仕様に従っています。</span><span class="sxs-lookup"><span data-stu-id="01736-112">This is consistent with the OLE DB specification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01736-113">参照</span><span class="sxs-lookup"><span data-stu-id="01736-113">See Also</span></span>  
 [<span data-ttu-id="01736-114">日付と時刻の強化機能 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="01736-114">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
