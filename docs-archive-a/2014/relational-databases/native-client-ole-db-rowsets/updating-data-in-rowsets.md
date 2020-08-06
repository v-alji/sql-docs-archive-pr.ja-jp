---
title: 行セット内のデータの更新 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: rothja
ms.author: jroth
ms.openlocfilehash: 993cfb67d4e6b72eec7cc0537e9b47371e94af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718087"
---
# <a name="updating-data-in-rowsets"></a><span data-ttu-id="46b1d-102">行セット内のデータの更新</span><span class="sxs-lookup"><span data-stu-id="46b1d-102">Updating Data in Rowsets</span></span>
  <span data-ttu-id="46b1d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンシューマーがそのデータを含む変更可能な行セットを更新するときにデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="46b1d-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider updates [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data when a consumer updates a modifiable rowset that contains that data.</span></span> <span data-ttu-id="46b1d-104">コンシューマーが **IRowsetChange** インターフェイスまたは **IRowsetUpdate** インターフェイスのいずれかのサポートを要求すると、変更可能な行セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="46b1d-104">A modifiable rowset is created when the consumer requests support for either the **IRowsetChange** or **IRowsetUpdate** interface.</span></span>  
  
 <span data-ttu-id="46b1d-105">すべて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Native Client OLE DB プロバイダー変更可能な行セット [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、カーソルを使用して行セットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="46b1d-105">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider-modifiable rowsets use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support the rowset.</span></span> <span data-ttu-id="46b1d-106">行セット プロパティ DBPROP_LOCKMODE は、カーソルでの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンカレンシー制御動作を変更し、更新可能な行セット内の行をフェッチする動作や、その行セット内のデータの整合性に関するエラーを生成する動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="46b1d-106">The rowset property DBPROP_LOCKMODE alters [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency control behavior in cursors and determines the behavior of rowset row fetching and data integrity error generation in updatable rowsets.</span></span>  
  
 <span data-ttu-id="46b1d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、更新前または更新後の行の同期がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="46b1d-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports row synchronization before or after an update.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46b1d-108">IRowChange::SetColumns を使用して、行オブジェクトの 1 つ以上の名前付き列の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="46b1d-108">IRowChange::SetColumns is available to set the values of one or more named columns of a row object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46b1d-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="46b1d-109">In This Section</span></span>  
  
-   [<span data-ttu-id="46b1d-110">SQL Server カーソルでのデータ更新</span><span class="sxs-lookup"><span data-stu-id="46b1d-110">Updating Data in SQL Server Cursors</span></span>](updating-data-in-sql-server-cursors.md)  
  
-   [<span data-ttu-id="46b1d-111">行の再同期</span><span class="sxs-lookup"><span data-stu-id="46b1d-111">Resynchronizing Rows</span></span>](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a><span data-ttu-id="46b1d-112">参照</span><span class="sxs-lookup"><span data-stu-id="46b1d-112">See Also</span></span>  
 [<span data-ttu-id="46b1d-113">行セット</span><span class="sxs-lookup"><span data-stu-id="46b1d-113">Rowsets</span></span>](rowsets.md)  
  
  
