---
title: SQL Server テーブルの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- SQL Server Native Client OLE DB provider, tables
- removing tables
- dropping tables
ms.assetid: b6d6c4de-43c6-473e-92aa-34ffddd58cbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d7bea98a3afcd0022f66117b6bde2d968a866b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642046"
---
# <a name="dropping-a-sql-server-table"></a>SQL Server テーブルの削除
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **Itabledefinition::D roptable**関数を公開します。 これにより、コンシューマーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからテーブルを削除できます。  
  
 コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。 *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](tables-and-indexes.md)  
  
  
