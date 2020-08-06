---
title: MERGE 機能の実装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c2e2d3f0796396c0f3f451215f1fd685979a842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639522"
---
# <a name="implementing-merge-functionality"></a>MERGE 機能の実装
  データベースは、特定の行がデータベースに既に存在するかどうかによって、挿入か更新のどちらかの実行が必要になる場合があります。  
  
 `MERGE` ステートメントを使用せずに [!INCLUDE[tsql](../../includes/tsql-md.md)] で使用できる方法の 1 つは次のとおりです。  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 マージを実装する [!INCLUDE[tsql](../../includes/tsql-md.md)] の別の方法は次のとおりです。  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 ネイティブ コンパイル ストアド プロシージャ向け  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)   
 [インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
