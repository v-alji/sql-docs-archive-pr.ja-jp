---
title: SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: rothja
ms.author: jroth
ms.openlocfilehash: dc3d86229501f80b25fb077788d1835a5f4f5c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639957"
---
# <a name="sqlcancel"></a>SQLCancel
  [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)のトピックでは、ODBC 2.x で、 `SQLCancel` ステートメントで処理が実行されていないときにアプリケーションがを呼び出すと、オプションと同じ効果があることが示されて `SQLCancel` います `SQLFreeStmt` `SQL_CLOSE` 。この動作は、完全を期すためだけに定義されており、アプリケーションは `SQLFreeStmt` `SQLCloseCursor` カーソルを閉じる必要があります。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ クライアント アプリケーションで ODBC API バージョンを 3.5.x 以降に設定した場合も、`SQLCancel` 関数では、ODBC 2.x の動作が使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
