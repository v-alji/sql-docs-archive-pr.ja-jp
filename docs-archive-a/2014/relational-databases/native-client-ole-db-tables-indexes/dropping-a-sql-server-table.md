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
# <a name="dropping-a-sql-server-table"></a><span data-ttu-id="7e386-102">SQL Server テーブルの削除</span><span class="sxs-lookup"><span data-stu-id="7e386-102">Dropping a SQL Server Table</span></span>
  <span data-ttu-id="7e386-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **Itabledefinition::D roptable**関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="7e386-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropTable** function.</span></span> <span data-ttu-id="7e386-104">これにより、コンシューマーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからテーブルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="7e386-104">This allows consumers to remove a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from a database.</span></span>  
  
 <span data-ttu-id="7e386-105">コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e386-105">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="7e386-106">*pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e386-106">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e386-107">参照</span><span class="sxs-lookup"><span data-stu-id="7e386-107">See Also</span></span>  
 [<span data-ttu-id="7e386-108">テーブルとインデックス</span><span class="sxs-lookup"><span data-stu-id="7e386-108">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  
