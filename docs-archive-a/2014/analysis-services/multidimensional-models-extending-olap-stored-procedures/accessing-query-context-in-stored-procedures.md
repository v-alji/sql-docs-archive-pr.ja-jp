---
title: ストアドプロシージャのクエリコンテキストへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9da8ddb223ed03c0208fe524ea5cd7195a039c97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711117"
---
# <a name="accessing-query-context-in-stored-procedures"></a><span data-ttu-id="bcd37-102">ストアド プロシージャのクエリ コンテキストへのアクセス</span><span class="sxs-lookup"><span data-stu-id="bcd37-102">Accessing Query Context in Stored Procedures</span></span>
  <span data-ttu-id="bcd37-103">ストアド プロシージャの実行コンテキストは、ADOMD.NET サーバー オブジェクト モデルの `Context` オブジェクトとして、ストアド プロシージャのコードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="bcd37-103">The execution context of a stored procedure is available within the code of the stored procedure as the `Context` object of the ADOMD.NET server object model.</span></span> <span data-ttu-id="bcd37-104">これは、読み取り専用のコンテキストであり、ストアド プロシージャによって変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="bcd37-104">This is a read-only context and cannot be modified by the stored procedure.</span></span> <span data-ttu-id="bcd37-105">このオブジェクトでは次のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bcd37-105">The following properties are available on this object.</span></span>  
  
|<span data-ttu-id="bcd37-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bcd37-106">Property</span></span>|<span data-ttu-id="bcd37-107">Type</span><span class="sxs-lookup"><span data-stu-id="bcd37-107">Type</span></span>|<span data-ttu-id="bcd37-108">説明</span><span class="sxs-lookup"><span data-stu-id="bcd37-108">Description</span></span>|  
|--------------|----------|-----------------|  
|<span data-ttu-id="bcd37-109">**CurrentCube**</span><span class="sxs-lookup"><span data-stu-id="bcd37-109">**CurrentCube**</span></span>|<span data-ttu-id="bcd37-110">キューブ</span><span class="sxs-lookup"><span data-stu-id="bcd37-110">Cube</span></span>|<span data-ttu-id="bcd37-111">現在のクエリ コンテキストのキューブです。</span><span class="sxs-lookup"><span data-stu-id="bcd37-111">The cube for the current query context.</span></span>|  
|<span data-ttu-id="bcd37-112">**CurrentDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="bcd37-112">**CurrentDatabaseName**</span></span>|<span data-ttu-id="bcd37-113">String</span><span class="sxs-lookup"><span data-stu-id="bcd37-113">String</span></span>|<span data-ttu-id="bcd37-114">現在のデータベースの識別子です。</span><span class="sxs-lookup"><span data-stu-id="bcd37-114">The identifier of the current database.</span></span>|  
|<span data-ttu-id="bcd37-115">**CurrentConnection**</span><span class="sxs-lookup"><span data-stu-id="bcd37-115">**CurrentConnection**</span></span>|<span data-ttu-id="bcd37-116">Connection</span><span class="sxs-lookup"><span data-stu-id="bcd37-116">Connection</span></span>|<span data-ttu-id="bcd37-117">現在のコンテキストの接続オブジェクトへの参照です。</span><span class="sxs-lookup"><span data-stu-id="bcd37-117">A reference to the connection object in the current context.</span></span>|  
|<span data-ttu-id="bcd37-118">**合格**</span><span class="sxs-lookup"><span data-stu-id="bcd37-118">**Pass**</span></span>|<span data-ttu-id="bcd37-119">Integer</span><span class="sxs-lookup"><span data-stu-id="bcd37-119">Integer</span></span>|<span data-ttu-id="bcd37-120">現在のコンテキストのパス番号です。</span><span class="sxs-lookup"><span data-stu-id="bcd37-120">The pass number for the current context.</span></span>|  
  
 <span data-ttu-id="bcd37-121">`Context` オブジェクトは、多次元式 (MDX) オブジェクト モデルがストアド プロシージャで使用されている場合に存在し、</span><span class="sxs-lookup"><span data-stu-id="bcd37-121">The `Context` object exists when the Multidimensional Expressions (MDX) object model is used in a stored procedure.</span></span> <span data-ttu-id="bcd37-122">MDX オブジェクト モデルがクライアントで使用されている場合には利用できません。</span><span class="sxs-lookup"><span data-stu-id="bcd37-122">It is not available when the MDX object model is used on a client.</span></span> <span data-ttu-id="bcd37-123">`Context` オブジェクトは、ストアド プロシージャに明示的に渡されたり、ストアド プロシージャから明示的に返されることはなく、</span><span class="sxs-lookup"><span data-stu-id="bcd37-123">The `Context` object is not explicitly passed to or returned by the stored procedure.</span></span> <span data-ttu-id="bcd37-124">ストアド プロシージャの実行中に利用できます。</span><span class="sxs-lookup"><span data-stu-id="bcd37-124">It is available during the execution of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd37-125">参照</span><span class="sxs-lookup"><span data-stu-id="bcd37-125">See Also</span></span>  
 <span data-ttu-id="bcd37-126">[多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="bcd37-126">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="bcd37-127">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="bcd37-127">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
