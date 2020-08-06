---
title: FILESTREAM のサポート (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: rothja
ms.author: jroth
ms.openlocfilehash: cde3c2cd1b72773cfcf17eacedeb3276dd2f63da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642754"
---
# <a name="filestream-support-ole-db"></a><span data-ttu-id="48ee6-102">FILESTREAM のサポート (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="48ee6-102">FILESTREAM Support (OLE DB)</span></span>
  <span data-ttu-id="48ee6-103">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 以降では、OLE DB では、拡張された FILESTREAM 機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="48ee6-103">Beginning with [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, OLE DB supports the enhanced FILESTREAM feature.</span></span> <span data-ttu-id="48ee6-104">この機能の詳細については、「 [FILESTREAM のサポート](../features/filestream-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48ee6-104">For more information about this feature, see [FILESTREAM Support](../features/filestream-support.md).</span></span> <span data-ttu-id="48ee6-105">サンプルについては、「[FILESTREAM と OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48ee6-105">For samples, see [Filestream and OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).</span></span>  
  
 <span data-ttu-id="48ee6-106">アプリケーションで 2 GB より大きい `varbinary(max)` 値を送受信するには、パラメーターと結果のバインドで `DBTYPE_IUNKNOWN` を使用します。</span><span class="sxs-lookup"><span data-stu-id="48ee6-106">To send and receive `varbinary(max)` values greater than 2 GB, an application uses `DBTYPE_IUNKNOWN` in parameter and result bindings.</span></span> <span data-ttu-id="48ee6-107">パラメーターの場合、プロバイダーは ISequentialStream および ISequentialStream を返す結果に対して IUnknown::QueryInterface を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="48ee6-107">For parameters the provider must call IUnknown::QueryInterface for ISequentialStream and for results that return ISequentialStream.</span></span>  
  
 <span data-ttu-id="48ee6-108">OLE DB の場合は、ISequentialStream 値に関連するチェックが緩和されます。</span><span class="sxs-lookup"><span data-stu-id="48ee6-108">For OLE DB, checking related to ISequentialStream values will be relaxed.</span></span> <span data-ttu-id="48ee6-109">*Wtype*が `DBTYPE_IUNKNOWN` 構造体に含まれている場合 `DBBINDING` は、dwpart からを省略するか、データ `DBPART_LENGTH` の長さ (データバッファー内のオフセット*oblength* ) を ~ 0 に設定することによって、長さのチェックを無効にすることができます。 *dwPart*</span><span class="sxs-lookup"><span data-stu-id="48ee6-109">When *wType* is `DBTYPE_IUNKNOWN` in the `DBBINDING` struct, length checking can be disabled either by omitting `DBPART_LENGTH` from *dwPart* or by setting the length of the data (at offset *obLength* in the data buffer) to ~0.</span></span> <span data-ttu-id="48ee6-110">この場合、プロバイダーは値の長さをチェックせず、ストリームで利用可能なすべてのデータを要求し、返します。</span><span class="sxs-lookup"><span data-stu-id="48ee6-110">In this case, the provider will not check the length of the value and will request and return all of the data available through the stream.</span></span> <span data-ttu-id="48ee6-111">この変更は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (以降の) サーバーに接続する場合に限り、すべてのラージ オブジェクト (LOB) 型と XML に適用されます。</span><span class="sxs-lookup"><span data-stu-id="48ee6-111">This change will be applied to all large object (LOB) types and XML, but only when connected to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (or later) servers.</span></span> <span data-ttu-id="48ee6-112">これにより、既存のアプリケーションや下位レベルのサーバーとの一貫性や下位互換性を維持しつつ、より柔軟な開発が可能になります。</span><span class="sxs-lookup"><span data-stu-id="48ee6-112">This will provide greater flexibility for developers, while maintaining consistency and backwards compatibility for existing applications and downlevel servers.</span></span>  
  
 <span data-ttu-id="48ee6-113">この変更は、データを転送するすべてのインターフェイス (主に IRowset:: GetData、ICommand:: Execute、および IRowsetFastLoad::InsertRow) に影響します。</span><span class="sxs-lookup"><span data-stu-id="48ee6-113">This change affects all interfaces that transfer data, principally IRowset::GetData, ICommand::Execute, and IRowsetFastLoad::InsertRow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ee6-114">参照</span><span class="sxs-lookup"><span data-stu-id="48ee6-114">See Also</span></span>  
 [<span data-ttu-id="48ee6-115">SQL Server Native Client プログラミング</span><span class="sxs-lookup"><span data-stu-id="48ee6-115">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  
