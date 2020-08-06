---
title: MSSQLSERVER_41332 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72a87838673f07f7a40596517ab54533d944e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642838"
---
# <a name="mssqlserver_41332"></a>MSSQLSERVER_41332
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41332|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQL_SNAPSHOT_NOT_SUPPORTED|  
|メッセージ テキスト|セッション TRANSACTION ISOLATION LEVEL が SNAPSHOT に設定されている場合、メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャはアクセスまたは作成できません。|  
  
## <a name="explanation"></a>説明  
 トランザクションはスナップショット分離レベルで開始され、互換性のない機能を使用しようとしました。  
  
## <a name="user-action"></a>ユーザーの操作  
 他の分離レベルでトランザクションを開始します。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
