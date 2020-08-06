---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: rothja
ms.author: jroth
ms.openlocfilehash: 24cdf6e2934c2b80a55d8fa1fcc572a976b636ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640900"
---
# <a name="bcp_batch"></a><span data-ttu-id="5008e-102">bcp_batch</span><span class="sxs-lookup"><span data-stu-id="5008e-102">bcp_batch</span></span>
  <span data-ttu-id="5008e-103">プログラム変数から一括コピーされ、bcp_sendrow によってに送信されたすべての行をコミットし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="5008e-103">Commits all rows previously bulk copied from program variables and sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5008e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5008e-104">Syntax</span></span>  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="5008e-105">引数</span><span class="sxs-lookup"><span data-stu-id="5008e-105">Arguments</span></span>  
 <span data-ttu-id="5008e-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="5008e-106">*hdbc*</span></span>  
 <span data-ttu-id="5008e-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="5008e-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5008e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5008e-108">Returns</span></span>  
 <span data-ttu-id="5008e-109">**Bcp_batch**を最後に呼び出した後に保存された行の数。エラーが発生した場合は-1。</span><span class="sxs-lookup"><span data-stu-id="5008e-109">The number of rows saved after the last call to **bcp_batch**, or -1 in case of error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5008e-110">解説</span><span class="sxs-lookup"><span data-stu-id="5008e-110">Remarks</span></span>  
 <span data-ttu-id="5008e-111">一括コピーのバッチではトランザクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="5008e-111">Bulk copy batches define transactions.</span></span> <span data-ttu-id="5008e-112">アプリケーションで[bcp_bind](bcp-bind.md)を使用し、プログラム変数から SQL Server テーブルに行を一括コピーする**bcp_sendrow** 、プログラムが**bcp_batch**または[bcp_done](bcp-done.md)を呼び出した場合にのみ、行がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="5008e-112">When an application uses [bcp_bind](bcp-bind.md) and **bcp_sendrow** to bulk copy rows from program variables to SQL Server tables, the rows are committed only when the program calls **bcp_batch** or [bcp_done](bcp-done.md).</span></span>  
  
 <span data-ttu-id="5008e-113">**Bcp_batch**は、 *n*行ごとに、または (テレメトリアプリケーションと同様に) 受信データになどがあるときに1回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5008e-113">You can call **bcp_batch** once every *n* rows or when there is a lull in incoming data (as in a telemetry application).</span></span> <span data-ttu-id="5008e-114">アプリケーションがを呼び出さない場合**bcp_batch** **bcp_done**が呼び出されたときにのみ、一括コピーされた行がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="5008e-114">If an application does not call **bcp_batch** the bulk copied rows are committed only when **bcp_done** is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5008e-115">参照</span><span class="sxs-lookup"><span data-stu-id="5008e-115">See Also</span></span>  
 [<span data-ttu-id="5008e-116">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="5008e-116">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
