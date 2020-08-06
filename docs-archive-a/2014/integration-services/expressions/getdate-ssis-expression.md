---
title: GETDATE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0acb384a8c3c3dfdae55c7172f341f9e32765e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639565"
---
# <a name="getdate-ssis-expression"></a>GETDATE (SSIS 式)
  システムの現在の日付を、DT_DBTIMESTAMP 形式で返します。 GETDATE 関数に引数はありません。  
  
> [!NOTE]  
>  GETDATE 関数から返される結果の長さは 29 文字です。  
  
## <a name="syntax"></a>構文  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="result-types"></a>戻り値の型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>式の例  
 この例では、現在の日付の年が返されます。  
  
```  
DATEPART("year",GETDATE())  
```  
  
 この例では、 **ModifiedDate** 列にある日付と現在の日付の間の日数が返されます。  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 この例では、現在の日付に 3 か月追加した値が返されます。  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>参照  
 [GETUTCDATE (SSIS 式)](getutcdate-ssis-expression.md)   
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
