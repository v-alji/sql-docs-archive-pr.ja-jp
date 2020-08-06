---
title: IRow による 1 行のフェッチ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: rothja
ms.author: jroth
ms.openlocfilehash: b5573fe1fef39f29329e373323f5f8aaf15f2c58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643792"
---
# <a name="fetching-a-single-row-with-irow"></a><span data-ttu-id="63d5d-102">IRow による 1 行のフェッチ</span><span class="sxs-lookup"><span data-stu-id="63d5d-102">Fetching a Single Row with IRow</span></span>
  <span data-ttu-id="63d5d-103">Native Client OLE DB プロバイダーでの**IRow**インターフェイスの実装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、パフォーマンスを向上させるために簡略化されています。</span><span class="sxs-lookup"><span data-stu-id="63d5d-103">The **IRow** interface implementation in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is simplified to increase performance.</span></span> <span data-ttu-id="63d5d-104">**IRow** では、1 つの行オブジェクトの列に直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="63d5d-104">**IRow** allows direct access to columns of a single row object.</span></span> <span data-ttu-id="63d5d-105">コマンドの実行結果が正確に 1 行になることが事前にわかっている場合、**IRow** でその行の列を取得できます。</span><span class="sxs-lookup"><span data-stu-id="63d5d-105">If you know beforehand that the result of a command execution will produce exactly one row, **IRow** will retrieve the columns of that row.</span></span> <span data-ttu-id="63d5d-106">結果セットが複数の行で構成される場合は、**IRow** では先頭の行だけが公開されます。</span><span class="sxs-lookup"><span data-stu-id="63d5d-106">If the result set includes multiple rows, **IRow** will expose only the first row.</span></span>  
  
 <span data-ttu-id="63d5d-107">**IRow** 実装では、行を移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="63d5d-107">The **IRow** implementation does not allow any navigation of the row.</span></span> <span data-ttu-id="63d5d-108">行内の各列には 1 回だけアクセスされます。ただし、例外が 1 つあります。最初に列サイズを確認し、次にデータをフェッチする場合は、列に 2 回アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="63d5d-108">Each column in the row is accessed only one time with one exception: A column can be accessed one time to find the column size and again to fetch the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63d5d-109">**IRow::Open** は、DBGUID_STREAM 型と DBGUID_NULL 型のオブジェクトを開くことだけをサポートします。</span><span class="sxs-lookup"><span data-stu-id="63d5d-109">**IRow::Open** supports only DBGUID_STREAM and DBGUID_NULL type of objects to be opened.</span></span>  
  
 <span data-ttu-id="63d5d-110">**ICommand::Execute** メソッドを使用して行オブジェクトを取得するには、IID_IRow を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="63d5d-110">To obtain a row object using **ICommand::Execute** method, IID_IRow must be passed.</span></span> <span data-ttu-id="63d5d-111">複数の結果セットを処理するには、**IMultipleResults** インターフェイスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63d5d-111">The **IMultipleResults** interface must be used to handle multiple result sets.</span></span> <span data-ttu-id="63d5d-112">**IMultipleResults** では、**IRow** と **IRowset** がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="63d5d-112">**IMultipleResults** supports **IRow** and **IRowset**.</span></span> <span data-ttu-id="63d5d-113">**IRowset** は、一括操作に使用されます。</span><span class="sxs-lookup"><span data-stu-id="63d5d-113">**IRowset** is used for bulk operations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63d5d-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="63d5d-114">In This Section</span></span>  
  
-   [<span data-ttu-id="63d5d-115">IRow::GetColumns の使用</span><span class="sxs-lookup"><span data-stu-id="63d5d-115">Using IRow::GetColumns</span></span>](using-irow-getcolumns.md)  
  
-   [<span data-ttu-id="63d5d-116">IRow を使用した BLOB データのフェッチ</span><span class="sxs-lookup"><span data-stu-id="63d5d-116">Fetching BLOB Data Using IRow</span></span>](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a><span data-ttu-id="63d5d-117">参照</span><span class="sxs-lookup"><span data-stu-id="63d5d-117">See Also</span></span>  
 [<span data-ttu-id="63d5d-118">行セット</span><span class="sxs-lookup"><span data-stu-id="63d5d-118">Rowsets</span></span>](rowsets.md)  
  
  
