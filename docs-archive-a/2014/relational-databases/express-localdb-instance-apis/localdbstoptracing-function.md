---
title: LocalDBStopTracing 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2bf6051fe8c86728c2ebf0a0b2bc34fabb98edb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632483"
---
# <a name="localdbstoptracing-function"></a><span data-ttu-id="01546-102">LocalDBStopTracing 関数</span><span class="sxs-lookup"><span data-stu-id="01546-102">LocalDBStopTracing Function</span></span>
  <span data-ttu-id="01546-103">現在の Windows ユーザーが所有しているすべての SQL Server Express LocalDB インスタンスの API 呼び出しの追跡を無効にします。</span><span class="sxs-lookup"><span data-stu-id="01546-103">Disables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="01546-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="01546-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01546-105">構文</span><span class="sxs-lookup"><span data-stu-id="01546-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="01546-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="01546-106">Returns</span></span>  
 <span data-ttu-id="01546-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="01546-107">S_OK</span></span>  
 <span data-ttu-id="01546-108">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="01546-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="01546-109">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="01546-109">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="01546-110">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="01546-110">An unexpected error occurred.</span></span> <span data-ttu-id="01546-111">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="01546-111">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01546-112">解説</span><span class="sxs-lookup"><span data-stu-id="01546-112">Remarks</span></span>  
 <span data-ttu-id="01546-113">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01546-113">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01546-114">参照</span><span class="sxs-lookup"><span data-stu-id="01546-114">See Also</span></span>  
 [<span data-ttu-id="01546-115">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="01546-115">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
