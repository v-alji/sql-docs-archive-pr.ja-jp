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
# <a name="bcp_done"></a>bcp_done
  Bcp_sendrow で実行されるプログラム変数からの一括コピーを終了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。 [bcp_sendrow](bcp-sendrow.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 [Bcp_batch](bcp-batch.md)を最後に呼び出した後に完全に保存された行の数。エラーが発生した場合は-1。  
  
## <a name="remarks"></a>解説  
 [Bcp_sendrow](bcp-sendrow.md)または[bcp_moretext](bcp-moretext.md)を最後に呼び出した後に**bcp_done**を呼び出します。 すべてのデータをコピーした後に**bcp_done**を呼び出さないと、エラーになります。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
