---
title: SqlTriggerContext オブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
author: rothja
ms.author: jroth
ms.openlocfilehash: f7eae3d290a70bedee0ed9badf9e6d0503caa2bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742310"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext オブジェクト
  `SqlTriggerContext` クラスでは、トリガーに関するコンテキスト情報が提供されます。 このコンテキスト情報には、トリガーを起動した動作の種類、UPDATE 操作で変更された列が含まれます。DDL (データ定義言語) トリガーの場合は、トリガー操作が記述されている XML `EventData` 構造体も含まれます。 クラスの使用方法の詳細と例につい `SqlTriggerContext` ては、「 [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md)」を参照してください。  
  
 詳細については、 `Microsoft.SqlServer.Server.SqlTriggerContext` .NET FRAMEWORK SDK のドキュメントのクラスリファレンスドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR トリガー](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
