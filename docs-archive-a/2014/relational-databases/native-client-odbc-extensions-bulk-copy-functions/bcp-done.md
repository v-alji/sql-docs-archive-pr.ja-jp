---
title: bcp_done |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9b0cbcc927fcd10c2d81b3c5c3d39bb80a8e9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630990"
---
# <a name="bcp_done"></a><span data-ttu-id="0bdb0-102">bcp_done</span><span class="sxs-lookup"><span data-stu-id="0bdb0-102">bcp_done</span></span>
  <span data-ttu-id="0bdb0-103">Bcp_sendrow で実行されるプログラム変数からの一括コピーを終了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="0bdb0-103">Ends a bulk copy from program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performed with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bdb0-104">構文</span><span class="sxs-lookup"><span data-stu-id="0bdb0-104">Syntax</span></span>  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0bdb0-105">引数</span><span class="sxs-lookup"><span data-stu-id="0bdb0-105">Arguments</span></span>  
 <span data-ttu-id="0bdb0-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="0bdb0-106">*hdbc*</span></span>  
 <span data-ttu-id="0bdb0-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="0bdb0-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="0bdb0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0bdb0-108">Returns</span></span>  
 <span data-ttu-id="0bdb0-109">[Bcp_batch](bcp-batch.md)を最後に呼び出した後に完全に保存された行の数。エラーが発生した場合は-1。</span><span class="sxs-lookup"><span data-stu-id="0bdb0-109">The number of rows permanently saved after the last call to [bcp_batch](bcp-batch.md) or -1 in case of error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bdb0-110">解説</span><span class="sxs-lookup"><span data-stu-id="0bdb0-110">Remarks</span></span>  
 <span data-ttu-id="0bdb0-111">[Bcp_sendrow](bcp-sendrow.md)または[bcp_moretext](bcp-moretext.md)を最後に呼び出した後に**bcp_done**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0bdb0-111">Call **bcp_done** after the last call to [bcp_sendrow](bcp-sendrow.md) or [bcp_moretext](bcp-moretext.md).</span></span> <span data-ttu-id="0bdb0-112">すべてのデータをコピーした後に**bcp_done**を呼び出さないと、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="0bdb0-112">Failure to call **bcp_done** after copying all data results in errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bdb0-113">参照</span><span class="sxs-lookup"><span data-stu-id="0bdb0-113">See Also</span></span>  
 [<span data-ttu-id="0bdb0-114">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="0bdb0-114">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
