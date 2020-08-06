---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eeec3a3adf318cadc96501938f8a5565f1c07670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632000"
---
# <a name="mssqlserver_10502"></a>MSSQLSERVER_10502
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10502|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_DUP_FOUND|  
|メッセージ テキスト|プラン ガイド '%.*ls' を作成できません。@stmt と @module_or_batch または @plan_handle と @statement_start_offset で指定したステートメントがデータベース内の既存のプラン ガイド '%.\*ls' と一致しています。 新しいプラン ガイドを作成する前に、既存のプラン ガイドを削除します。|  
  
## <a name="explanation"></a>説明  
 指定したステートメントのプラン ガイドが存在します。  
  
## <a name="user-action"></a>ユーザーの操作  
 新しいプラン ガイドを作成する前に、既存のプラン ガイドを削除します。  
  
## <a name="see-also"></a>参照  
 [プランガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
