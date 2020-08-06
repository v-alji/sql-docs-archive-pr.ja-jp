---
title: IOpenRowset を使用した行セットの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: rothja
ms.author: jroth
ms.openlocfilehash: bf74466a698d39f74b9531adaa54c79c75e50ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739811"
---
# <a name="creating-a-rowset-with-iopenrowset"></a><span data-ttu-id="f46db-102">IOpenRowset を使用した行セットの作成</span><span class="sxs-lookup"><span data-stu-id="f46db-102">Creating a Rowset with IOpenRowset</span></span>
  <span data-ttu-id="f46db-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、 **IOpenRowset:: OpenRowset**メソッドがサポートされていますが、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="f46db-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IOpenRowset::OpenRowset** method with the following restrictions:</span></span>  
  
-   <span data-ttu-id="f46db-104">*pTableID* パラメーターが指すデータベース ID (DBID) 構造体に、ベース テーブルまたはビューを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f46db-104">A base table or view must be specified in a database ID (DBID) structure that the *pTableID* parameter points to.</span></span>  
  
-   <span data-ttu-id="f46db-105">DBID の *eKind* メンバーに DBKIND_NAME を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f46db-105">The DBID *eKind* member must indicate DBKIND_NAME.</span></span>  
  
-   <span data-ttu-id="f46db-106">DBID の *uName* メンバーには、既存のベース テーブルまたはビューの名前を Unicode 文字列で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f46db-106">The DBID *uName* member must specify the name of an existing base table or a view as a Unicode character string.</span></span>  
  
-   <span data-ttu-id="f46db-107">**OpenRowset** の *pIndexID* パラメーターには NULL を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f46db-107">The *pIndexID* parameter of **OpenRowset** must be NULL.</span></span>  
  
 <span data-ttu-id="f46db-108">**IOpenRowset::OpenRowset** の結果セットには、1 つの行セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f46db-108">The result set of **IOpenRowset::OpenRowset** contains a single rowset.</span></span> <span data-ttu-id="f46db-109">1つの行セットを含む結果セットは、カーソルでサポートでき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f46db-109">Result sets that contain a single rowset can be supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors.</span></span> <span data-ttu-id="f46db-110">開発者はカーソル サポートによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンカレンシー メカニズムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f46db-110">Cursor support allows the developer to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f46db-111">参照</span><span class="sxs-lookup"><span data-stu-id="f46db-111">See Also</span></span>  
 [<span data-ttu-id="f46db-112">行セット</span><span class="sxs-lookup"><span data-stu-id="f46db-112">Rowsets</span></span>](rowsets.md)  
  
  
