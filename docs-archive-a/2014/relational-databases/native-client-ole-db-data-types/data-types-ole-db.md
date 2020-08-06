---
title: データ型 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- data types [OLE DB]
- OLE DB, data types
ms.assetid: 15953706-f0d1-45f5-a2eb-a8bd36e1a5fc
author: rothja
ms.author: jroth
ms.openlocfilehash: 860d188f7a934e707766b157d4c089a88207ce02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740870"
---
# <a name="data-types-ole-db"></a><span data-ttu-id="62b92-102">データ型 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="62b92-102">Data Types (OLE DB)</span></span>
  <span data-ttu-id="62b92-103">[!INCLUDE[tsql](../../includes/tsql-md.md)]Native client OLE DB プロバイダーを使用してステートメントを実行し、結果を処理するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 行セット内のパラメーターまたは列をバインドするとき、および**itabledefinition**インターフェイスを使用してでテーブルを作成するときに、native client OLE DB プロバイダーがデータ型を OLE DB データ型にマップする方法を把握しておく必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="62b92-103">In order to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and process the results using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you must know how the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider maps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to OLE DB data types when binding parameters or columns in a rowset, and when it uses the **ITableDefinition** interface to create a table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62b92-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="62b92-104">In This Section</span></span>  
  
-   [<span data-ttu-id="62b92-105">行セットとパラメーターでのデータ型マッピング</span><span class="sxs-lookup"><span data-stu-id="62b92-105">Data Type Mapping in Rowsets and Parameters</span></span>](data-type-mapping-in-rowsets-and-parameters.md)  
  
-   [<span data-ttu-id="62b92-106">ITableDefinition でのデータ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="62b92-106">Data Type Mapping in ITableDefinition</span></span>](data-type-mapping-in-itabledefinition.md)  
  
-   [<span data-ttu-id="62b92-107">SSVARIANT 構造体</span><span class="sxs-lookup"><span data-stu-id="62b92-107">SSVARIANT Structure</span></span>](ssvariant-structure.md)  
  
## <a name="see-also"></a><span data-ttu-id="62b92-108">参照</span><span class="sxs-lookup"><span data-stu-id="62b92-108">See Also</span></span>  
 [<span data-ttu-id="62b92-109">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="62b92-109">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
