---
title: MSSQLSERVER_41302 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 751dac91378c002a7e6c6c619ddaf12be8173400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639537"
---
# <a name="mssqlserver_41302"></a>MSSQLSERVER_41302
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41302|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|WRITE_WRITE_CONFLICT|  
|メッセージ テキスト|現在のトランザクションが、このトランザクションが開始してから更新されたレコードを更新しようとしました。 トランザクションは中止されました。|  
  
## <a name="explanation"></a>説明  
 トランザクションで書き込み/書き込みの競合が発生したため、ステートメントが終了しました。  
  
## <a name="user-action"></a>ユーザーの操作  
 別のトランザクションで、後で操作を再試行してください。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
