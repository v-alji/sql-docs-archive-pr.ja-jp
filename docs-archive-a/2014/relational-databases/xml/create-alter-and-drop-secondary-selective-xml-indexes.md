---
title: 選択的セカンダリ XML インデックスの作成、変更、および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: rothja
ms.author: jroth
ms.openlocfilehash: e6f7296896b6421db5329565403cdcbaf10b26a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713930"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a><span data-ttu-id="dd330-102">選択的セカンダリ XML インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="dd330-102">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>
  <span data-ttu-id="dd330-103">新しい選択的セカンダリ XML インデックスの作成や、既存の選択的セカンダリ XML インデックスの変更または削除を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd330-103">Describes how to create a new secondary selective XML index, or alter or drop an existing secondary selective XML index.</span></span>  
  
##  <a name="creating-a-secondary-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="dd330-104">選択的セカンダリ XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="dd330-104">Creating a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a><span data-ttu-id="dd330-105">方法: 選択的セカンダリ XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="dd330-105">How to: Create a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="dd330-106">**Transact-SQL を使用して選択的セカンダリ XML インデックスを作成する**</span><span class="sxs-lookup"><span data-stu-id="dd330-106">**Create a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="dd330-107">CREATE SELECTIVE XML INDEX ステートメントを呼び出して選択的セカンダリ XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd330-107">Create a secondary selective XML index by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="dd330-108">詳細については、[XML インデックス &#40;選択的 XML インデックスの作成&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes.</span><span class="sxs-lookup"><span data-stu-id="dd330-108">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="dd330-109">**例**</span><span class="sxs-lookup"><span data-stu-id="dd330-109">**Example**</span></span>  
  
 <span data-ttu-id="dd330-110">次の例では、パス `'pathabc'`に選択的セカンダリ XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd330-110">The following example creates a secondary selective XML index on the path `'pathabc'`.</span></span> <span data-ttu-id="dd330-111">インデックスを作成するパスは、作成時に CREATE SELECTIVE XML INDEX ステートメントで指定された名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="dd330-111">The path to index is identified by the name that was given to it when it was created with the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="dd330-112">詳細については、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd330-112">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="altering-a-secondary-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="dd330-113">選択的セカンダリ XML インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="dd330-113">Altering a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="dd330-114">ALTER ステートメントは、選択的セカンダリ XML インデックスではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dd330-114">The ALTER statement is not supported for secondary selective XML indexes.</span></span> <span data-ttu-id="dd330-115">選択的セカンダリ XML インデックスを変更するには、既存のインデックスを削除し、再作成します。</span><span class="sxs-lookup"><span data-stu-id="dd330-115">To change a secondary selective XML index, drop the existing index and recreate it.</span></span>  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a><span data-ttu-id="dd330-116">方法:選択的セカンダリ XML インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="dd330-116">How to: Alter a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="dd330-117">**Transact-SQL を使用して選択的セカンダリ XML インデックスを変更する**</span><span class="sxs-lookup"><span data-stu-id="dd330-117">**Alter a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 1.  <span data-ttu-id="dd330-118">DROP INDEX ステートメントを呼び出して既存の選択的セカンダリ XML インデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="dd330-118">Drop the existing secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="dd330-119">詳細については、「[DROP INDEX &#40;選択的 XML インデックス&#41;](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd330-119">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
2.  <span data-ttu-id="dd330-120">CREATE XML INDEX ステートメントを呼び出すことによって必要なオプションのインデックスを再作成します。</span><span class="sxs-lookup"><span data-stu-id="dd330-120">Recreate the index with the desired options by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="dd330-121">詳細については、[XML インデックス &#40;選択的 XML インデックスの作成&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes.</span><span class="sxs-lookup"><span data-stu-id="dd330-121">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="dd330-122">**例**</span><span class="sxs-lookup"><span data-stu-id="dd330-122">**Example**</span></span>  
  
 <span data-ttu-id="dd330-123">次の例では、インデックスを削除して再作成することにより、選択的セカンダリ XML インデックスを変更します。</span><span class="sxs-lookup"><span data-stu-id="dd330-123">The following example changes a secondary selective XML index by dropping it and recreating it.</span></span>  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="dropping-a-secondary-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="dd330-124">選択的セカンダリ XML インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="dd330-124">Dropping a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a><span data-ttu-id="dd330-125">方法: 選択的セカンダリ XML インデックスのドロップ</span><span class="sxs-lookup"><span data-stu-id="dd330-125">How to: Drop a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="dd330-126">**Transact-SQL を使用して選択的セカンダリ XML インデックスを削除する**</span><span class="sxs-lookup"><span data-stu-id="dd330-126">**Drop a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="dd330-127">DROP INDEX ステートメントを呼び出して選択的セカンダリ XML インデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="dd330-127">Drop a secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="dd330-128">詳細については、「[DROP INDEX &#40;選択的 XML インデックス&#41;](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd330-128">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="dd330-129">**例**</span><span class="sxs-lookup"><span data-stu-id="dd330-129">**Example**</span></span>  
  
 <span data-ttu-id="dd330-130">DROP INDEX ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dd330-130">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a><span data-ttu-id="dd330-131">参照</span><span class="sxs-lookup"><span data-stu-id="dd330-131">See Also</span></span>  
 [<span data-ttu-id="dd330-132">選択的 XML インデックス &#40;SXI&#41;</span><span class="sxs-lookup"><span data-stu-id="dd330-132">Selective XML Indexes &#40;SXI&#41;</span></span>](selective-xml-indexes-sxi.md)  
  
  
