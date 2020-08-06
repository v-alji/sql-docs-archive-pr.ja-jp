---
title: 行の再同期 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 47c628ae583f3e635f422d5146f64508372a1114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633830"
---
# <a name="resynchronizing-rows"></a><span data-ttu-id="90ba3-102">行の再同期</span><span class="sxs-lookup"><span data-stu-id="90ba3-102">Resynchronizing Rows</span></span>
  <span data-ttu-id="90ba3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **IRowsetResynch** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソルがサポートされている行セットに対してのみ IRowsetResynch をサポートします。</span><span class="sxs-lookup"><span data-stu-id="90ba3-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IRowsetResynch** on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor-supported rowsets only.</span></span> <span data-ttu-id="90ba3-104">**IRowsetResynch** を、要求時に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="90ba3-104">**IRowsetResynch** is not available on demand.</span></span> <span data-ttu-id="90ba3-105">コンシューマーは、行セットを開く前にインターフェイスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90ba3-105">The consumer must request the interface before opening the rowset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ba3-106">参照</span><span class="sxs-lookup"><span data-stu-id="90ba3-106">See Also</span></span>  
 [<span data-ttu-id="90ba3-107">行セット内のデータの更新</span><span class="sxs-lookup"><span data-stu-id="90ba3-107">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  
