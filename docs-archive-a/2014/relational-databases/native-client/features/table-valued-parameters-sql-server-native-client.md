---
title: テーブル値パラメーター (SQL Server Native Client) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, table-valued parameters
- table-valued parameters (SQL Server Native Client)
ms.assetid: 5ee6bdcd-0309-4a20-b5c2-0e6b6839f34f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6af4979b9a77c94f52be5197b01179007a971283
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633117"
---
# <a name="table-valued-parameters-sql-server-native-client"></a><span data-ttu-id="f5e7c-102">テーブル値パラメーター (SQL Server Native Client)</span><span class="sxs-lookup"><span data-stu-id="f5e7c-102">Table-Valued Parameters (SQL Server Native Client)</span></span>
  <span data-ttu-id="f5e7c-103">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] で導入されたテーブル値パラメーターを使用すると、複数行のデータを効率的にサーバーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f5e7c-103">Table-valued parameters were introduced in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="f5e7c-104">テーブル値パラメーターの機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../../includes/tsql-md.md)] との統合も緊密です。また、多くの場合、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f5e7c-104">Table-valued parameters provide functionality similar to parameter arrays, but they offer more flexibility and closer integration with [!INCLUDE[tsql](../../../includes/tsql-md.md)], and can frequently improve performance.</span></span> <span data-ttu-id="f5e7c-105">テーブル値パラメーターはセットベースの操作にも使用できますが、パラメーター配列は使用できません。</span><span class="sxs-lookup"><span data-stu-id="f5e7c-105">Table-valued parameters can also participate in set-based operations, whereas parameter arrays cannot.</span></span>  
  
 <span data-ttu-id="f5e7c-106">テーブル値パラメーターと ODBC の詳細については、「[テーブル値パラメーター &#40;odbc&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5e7c-106">For information about table-valued parameters and ODBC, see [Table-Valued Parameters &#40;ODBC&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
 <span data-ttu-id="f5e7c-107">テーブル値パラメーターおよび OLE DB の詳細については、「[テーブル値パラメーター &#40;OLE DB&#41;](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5e7c-107">For information about table-valued parameters and OLE DB, see [Table-Valued Parameters &#40;OLE DB&#41;](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e7c-108">参照</span><span class="sxs-lookup"><span data-stu-id="f5e7c-108">See Also</span></span>  
 [<span data-ttu-id="f5e7c-109">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="f5e7c-109">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
