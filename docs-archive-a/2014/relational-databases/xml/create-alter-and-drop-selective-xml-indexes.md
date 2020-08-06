---
title: 選択的 XML インデックスの作成、変更、および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4123a46cc13359c936e6f9cfc0db3dcfdaa175
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713929"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a><span data-ttu-id="1721e-102">選択的 XML インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="1721e-102">Create, Alter, and Drop Selective XML Indexes</span></span>
  <span data-ttu-id="1721e-103">新しい選択的 XML インデックスの作成や、既存の選択的 XML インデックスの変更または削除を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1721e-103">Describes how to create a new selective XML index, or alter or drop an existing selective XML index.</span></span>  
  
 <span data-ttu-id="1721e-104">選択的 XML インデックスの詳細については、「 [選択的 XML インデックス &#40;SXI&#41;](selective-xml-indexes-sxi.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1721e-104">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="creating-a-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="1721e-105">選択的 XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="1721e-105">Creating a Selective XML Index</span></span>  
  
### <a name="how-to-create-a-selective-xml-index"></a><span data-ttu-id="1721e-106">方法: 選択的 XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="1721e-106">How to: Create a Selective XML Index</span></span>  
 <span data-ttu-id="1721e-107">**Transact-SQL を使用して選択的 XML インデックスを作成する**</span><span class="sxs-lookup"><span data-stu-id="1721e-107">**Create a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="1721e-108">CREATE SELECTIVE XML INDEX ステートメントを呼び出して選択的 XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1721e-108">Create a selective XML index by calling the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="1721e-109">詳細については、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1721e-109">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
 <span data-ttu-id="1721e-110">**例**</span><span class="sxs-lookup"><span data-stu-id="1721e-110">**Example**</span></span>  
  
 <span data-ttu-id="1721e-111">次の例では、選択的 XML インデックスを作成するための構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="1721e-111">The following example shows the syntax for creating a selective XML index.</span></span> <span data-ttu-id="1721e-112">また、インデックスを作成するパスと省略可能な最適化ヒントを指定する構文のいくつかのバリエーションを示します。</span><span class="sxs-lookup"><span data-stu-id="1721e-112">It also shows several variations of the syntax for describing the paths to be indexed, with optional optimization hints.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="altering-a-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="1721e-113">選択的 XML インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="1721e-113">Altering a Selective XML Index</span></span>  
  
### <a name="how-to-alter-a-selective-xml-index"></a><span data-ttu-id="1721e-114">方法: 選択的 XML インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="1721e-114">How to: Alter a Selective XML Index</span></span>  
 <span data-ttu-id="1721e-115">**Transact-SQL を使用して選択的 XML インデックスを変更する**</span><span class="sxs-lookup"><span data-stu-id="1721e-115">**Alter a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="1721e-116">ALTER INDEX ステートメントを呼び出して既存の選択的 XML インデックスを変更します。</span><span class="sxs-lookup"><span data-stu-id="1721e-116">Alter an existing selective XML index by calling the ALTER INDEX statement.</span></span> <span data-ttu-id="1721e-117">詳細については、「[ALTER INDEX &#40;選択的 XML インデックス&#41;](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1721e-117">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="1721e-118">**例**</span><span class="sxs-lookup"><span data-stu-id="1721e-118">**Example**</span></span>  
  
 <span data-ttu-id="1721e-119">ALTER INDEX ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1721e-119">The following example shows an ALTER INDEX statement.</span></span> <span data-ttu-id="1721e-120">このステートメントは、インデックスの XQuery の部分にパス `'/a/b/m'` を追加し、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)」のトピックの例で作成したインデックスの SQL の部分からパス `'/a/b/e'` を削除します。</span><span class="sxs-lookup"><span data-stu-id="1721e-120">This statement adds the path `'/a/b/m'` to the XQuery part of the index and deletes the path `'/a/b/e'` from the SQL part of the index created in the example in the topic [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span> <span data-ttu-id="1721e-121">削除するパスは、作成時に指定された名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="1721e-121">The path to delete is identified by the name that was given to it when it was created.</span></span>  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="dropping-a-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="1721e-122">選択的 XML インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="1721e-122">Dropping a Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-selective-xml-index"></a><span data-ttu-id="1721e-123">方法: 選択的 XML インデックスのドロップ</span><span class="sxs-lookup"><span data-stu-id="1721e-123">How to: Drop a Selective XML Index</span></span>  
 <span data-ttu-id="1721e-124">**Transact-SQL を使用して選択的 XML インデックスを削除する**</span><span class="sxs-lookup"><span data-stu-id="1721e-124">**Drop a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="1721e-125">DROP INDEX ステートメントを呼び出して選択的 XML インデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="1721e-125">Drop a selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="1721e-126">詳細については、「[DROP INDEX &#40;選択的 XML インデックス&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1721e-126">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes).</span></span>  
  
 <span data-ttu-id="1721e-127">**例**</span><span class="sxs-lookup"><span data-stu-id="1721e-127">**Example**</span></span>  
  
 <span data-ttu-id="1721e-128">DROP INDEX ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1721e-128">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
