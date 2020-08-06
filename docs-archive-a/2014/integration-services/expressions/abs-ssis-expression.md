---
title: ABS (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f429dda94282646ef769a1c393f9fa54b56e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642941"
---
# <a name="abs-ssis-expression"></a>ABS (SSIS 式)
  数値式の正の絶対値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 符号付きまたは符号なしの数値式です。  
  
## <a name="result-types"></a>戻り値の型  
 関数に送信された数値式のデータ型です。  
  
## <a name="remarks"></a>解説  
 引数が NULL の場合、ABS は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 次の例では、正の数および負の数に ABS 関数を適用します。 どちらも 1.23 を返します。  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 この例では、変数 **HighTemperature** および **LowTempature**の値を減算する式に対して ABS 関数を適用します。  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>参照  
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
