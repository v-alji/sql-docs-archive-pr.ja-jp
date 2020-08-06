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
# <a name="sqltriggercontext-object"></a><span data-ttu-id="aa5d2-102">SqlTriggerContext オブジェクト</span><span class="sxs-lookup"><span data-stu-id="aa5d2-102">SqlTriggerContext Object</span></span>
  <span data-ttu-id="aa5d2-103">`SqlTriggerContext` クラスでは、トリガーに関するコンテキスト情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="aa5d2-103">The `SqlTriggerContext` class provides context information about the trigger.</span></span> <span data-ttu-id="aa5d2-104">このコンテキスト情報には、トリガーを起動した動作の種類、UPDATE 操作で変更された列が含まれます。DDL (データ定義言語) トリガーの場合は、トリガー操作が記述されている XML `EventData` 構造体も含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa5d2-104">This contextual information includes the type of action that caused the trigger to fire, which columns were modified in an UPDATE operation, and, in the case of a data definition language (DDL) trigger, an XML `EventData` structure that describes the triggering operation.</span></span> <span data-ttu-id="aa5d2-105">クラスの使用方法の詳細と例につい `SqlTriggerContext` ては、「 [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa5d2-105">For more information and examples of how to use the `SqlTriggerContext` class, see [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span>  
  
 <span data-ttu-id="aa5d2-106">詳細については、 `Microsoft.SqlServer.Server.SqlTriggerContext` .NET FRAMEWORK SDK のドキュメントのクラスリファレンスドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa5d2-106">For more information, see the `Microsoft.SqlServer.Server.SqlTriggerContext` class reference documentation in the .NET Framework SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5d2-107">参照</span><span class="sxs-lookup"><span data-stu-id="aa5d2-107">See Also</span></span>  
 <span data-ttu-id="aa5d2-108">[CLR トリガー](../../database-engine/dev-guide/clr-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="aa5d2-108">[CLR Triggers](../../database-engine/dev-guide/clr-triggers.md) </span></span>  
 [<span data-ttu-id="aa5d2-109">EVENTDATA &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aa5d2-109">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
