---
title: ブックマーク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: rothja
ms.author: jroth
ms.openlocfilehash: be8e5486e5a442ddafa133a9cbd3f408d30a50d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738256"
---
# <a name="bookmarks"></a><span data-ttu-id="64223-102">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="64223-102">Bookmarks</span></span>
  <span data-ttu-id="64223-103">ブックマークを使用すると、コンシューマーは行をすばやく返すことができます。</span><span class="sxs-lookup"><span data-stu-id="64223-103">Bookmarks let consumers quickly return to a row.</span></span> <span data-ttu-id="64223-104">コンシューマーはブックマークの値を基に、行にランダムにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="64223-104">With bookmarks, consumers can access rows randomly based on the bookmark value.</span></span> <span data-ttu-id="64223-105">ブックマーク列は、行セットの列 0 です。</span><span class="sxs-lookup"><span data-stu-id="64223-105">The bookmark column is column 0 in the rowset.</span></span> <span data-ttu-id="64223-106">コンシューマーは、バインド構造体の dwFlag フィールド値に DBCOLUMNSINFO_ISBOOKMARK を設定して、その列がブックマークに使用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="64223-106">The consumer sets the dwFlag field value of the binding structure to DBCOLUMNSINFO_ISBOOKMARK to indicate that the column is used as a bookmark.</span></span> <span data-ttu-id="64223-107">また、コンシューマーは行セット プロパティ DBPROP_BOOKMARKS に VARIANT_TRUE を設定します。</span><span class="sxs-lookup"><span data-stu-id="64223-107">The consumer also sets the rowset property DBPROP_BOOKMARKS to VARIANT_TRUE.</span></span> <span data-ttu-id="64223-108">その結果、行セットに列 0 が存在できるようになります。</span><span class="sxs-lookup"><span data-stu-id="64223-108">This lets column 0 be present in the rowset.</span></span> <span data-ttu-id="64223-109">**IRowsetLocate::GetRowsAt** メソッドを使用すると、ブックマークからのオフセットで指定された行で始まる行が取り出されます。</span><span class="sxs-lookup"><span data-stu-id="64223-109">The **IRowsetLocate::GetRowsAt** method is then used to fetch rows, starting with the row specified as an offset from a bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64223-110">参照</span><span class="sxs-lookup"><span data-stu-id="64223-110">See Also</span></span>  
 [<span data-ttu-id="64223-111">行セット</span><span class="sxs-lookup"><span data-stu-id="64223-111">Rowsets</span></span>](rowsets.md)  
  
  
