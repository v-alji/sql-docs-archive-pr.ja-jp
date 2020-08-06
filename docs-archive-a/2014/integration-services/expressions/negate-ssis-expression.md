---
title: '- (負数化) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a2d8ba292f2d24633598ab080ddf75ded5e8bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720270"
---
# <a name="--negate-ssis-expression"></a>- (負数化) (SSIS 式)
  数値式を負数化します。  
  
## <a name="syntax"></a>構文  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 任意の数値データ型の有効な式です。 サポートされるデータ型は、符号付き数値データ型のみです。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="result-types"></a>戻り値の型  
 データ型を返す *numeric_expression*です。  
  
## <a name="expression-examples"></a>式の例  
 この例では、変数 **Counter** の値を負数化して、数値リテラル 50 を加算します。  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](operators-ssis-expression.md)  
  
  
