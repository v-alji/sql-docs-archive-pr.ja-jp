---
title: LocalDBStartTracing 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1b10482e9839d43e29da72dbe2c194a01d8248eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743266"
---
# <a name="localdbstarttracing-function"></a><span data-ttu-id="35396-102">LocalDBStartTracing 関数</span><span class="sxs-lookup"><span data-stu-id="35396-102">LocalDBStartTracing Function</span></span>
  <span data-ttu-id="35396-103">現在の Windows ユーザーが所有しているすべての SQL Server Express LocalDB インスタンスの API 呼び出しの追跡を有効にします。</span><span class="sxs-lookup"><span data-stu-id="35396-103">Enables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="35396-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="35396-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35396-105">構文</span><span class="sxs-lookup"><span data-stu-id="35396-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="35396-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="35396-106">Returns</span></span>  
 <span data-ttu-id="35396-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="35396-107">S_OK</span></span>  
 <span data-ttu-id="35396-108">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="35396-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="35396-109">LOCALDB_ERROR_XEVENT_FAILED</span><span class="sxs-lookup"><span data-stu-id="35396-109">LOCALDB_ERROR_XEVENT_FAILED</span></span>](../express-localdb-error-messages/localdb-error-xevent-failed.md)  
 <span data-ttu-id="35396-110">LocalDB インスタンスの API 内で XEvent エンジンを開始できませんでした。</span><span class="sxs-lookup"><span data-stu-id="35396-110">Failed to start XEvent engine within the LocalDB Instance API.</span></span>  
  
 [<span data-ttu-id="35396-111">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="35396-111">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="35396-112">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="35396-112">An unexpected error occurred.</span></span> <span data-ttu-id="35396-113">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="35396-113">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35396-114">解説</span><span class="sxs-lookup"><span data-stu-id="35396-114">Remarks</span></span>  
 <span data-ttu-id="35396-115">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35396-115">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35396-116">参照</span><span class="sxs-lookup"><span data-stu-id="35396-116">See Also</span></span>  
 [<span data-ttu-id="35396-117">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="35396-117">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
