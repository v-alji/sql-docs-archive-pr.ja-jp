---
title: IRowsetFastLoad (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ecf72f0015d9ed197b3b7a33d4f9bb3246134b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644445"
---
# <a name="irowsetfastload-ole-db"></a><span data-ttu-id="c1bcb-102">IRowsetFastLoad (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c1bcb-102">IRowsetFastLoad (OLE DB)</span></span>
  <span data-ttu-id="c1bcb-103">インターフェイスは、 `IRowsetFastLoad` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリベースの一括コピー操作のサポートを公開します。</span><span class="sxs-lookup"><span data-stu-id="c1bcb-103">The `IRowsetFastLoad` interface exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory-based bulk-copy operations.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="c1bcb-104">Native Client OLE DB プロバイダーコンシューマーは、インターフェイスを使用して、既存のテーブルにデータを迅速に追加し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c1bcb-104">Native Client OLE DB provider consumers use the interface to rapidly add data to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="c1bcb-105">セッションで SSPROP_ENABLEFASTLOAD を VARIANT_TRUE に設定した場合、その後にそのセッションから返される行セットのデータを読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="c1bcb-105">If you set SSPROP_ENABLEFASTLOAD to VARIANT_TRUE for a session, you cannot read data from rowsets subsequently returned from that session.</span></span> <span data-ttu-id="c1bcb-106">SSPROP_ENABLEFASTLOAD が VARIANT_TRUE に設定されている場合、そのセッションで作成される行セットはすべて IRowsetFastLoad 型になります。</span><span class="sxs-lookup"><span data-stu-id="c1bcb-106">When SSPROP_ENABLEFASTLOAD is set to VARIANT_TRUE, all rowsets created on the session will be of type IRowsetFastLoad.</span></span> <span data-ttu-id="c1bcb-107">IRowsetFastLoad の行セットは行セットのフェッチをサポートしていないため、これらの行セットのデータを読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="c1bcb-107">IRowsetFastLoad rowsets do not support rowset fetch functionality; therefore, data from these rowsets cannot be read.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1bcb-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c1bcb-108">In This Section</span></span>  
  
|<span data-ttu-id="c1bcb-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="c1bcb-109">Method</span></span>|<span data-ttu-id="c1bcb-110">説明</span><span class="sxs-lookup"><span data-stu-id="c1bcb-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1bcb-111">IRowsetFastLoad::Commit &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="c1bcb-111">IRowsetFastLoad::Commit &#40;OLE DB&#41;</span></span>](irowsetfastload-commit-ole-db.md)|<span data-ttu-id="c1bcb-112">挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c1bcb-112">Marks the end of a batch of inserted rows and writes the rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|[<span data-ttu-id="c1bcb-113">IRowsetFastLoad::InsertRow &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="c1bcb-113">IRowsetFastLoad::InsertRow &#40;OLE DB&#41;</span></span>](irowsetfastload-insertrow-ole-db.md)|<span data-ttu-id="c1bcb-114">一括コピー行セットに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="c1bcb-114">Adds a row to the bulk copy rowset.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1bcb-115">参照</span><span class="sxs-lookup"><span data-stu-id="c1bcb-115">See Also</span></span>  
 <span data-ttu-id="c1bcb-116">[インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="c1bcb-116">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 <span data-ttu-id="c1bcb-117">[IRowsetFastLoad &#40;OLE DB を使用した一括データコピー&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="c1bcb-117">[Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) </span></span>  
 [<span data-ttu-id="c1bcb-118">IROWSETFASTLOAD と ISEQUENTIALSTREAM を使用した SQL SERVER への BLOB データの送信 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="c1bcb-118">Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
