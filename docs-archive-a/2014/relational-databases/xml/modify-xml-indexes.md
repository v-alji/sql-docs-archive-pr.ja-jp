---
title: XML インデックスの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML indexes [SQL Server], modifying
- modifying indexes
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
author: rothja
ms.author: jroth
ms.openlocfilehash: c5c67470fc9aaaeefe49e5ccb1a8602e082c4054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712834"
---
# <a name="modify-xml-indexes"></a><span data-ttu-id="d90f6-102">XML インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="d90f6-102">Modify XML Indexes</span></span>
  <span data-ttu-id="d90f6-103">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL ステートメントを使用すると、既存の XML インデックスや XML 以外のインデックスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d90f6-103">The [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement can be used to modify existing XML and non-XML indexes.</span></span> <span data-ttu-id="d90f6-104">ただし、一部の ALTER INDEX オプションは XML インデックスに使用できません。</span><span class="sxs-lookup"><span data-stu-id="d90f6-104">However, not all the ALTER INDEX options are available to XML indexes.</span></span> <span data-ttu-id="d90f6-105">次のオプションは、XML インデックスの変更時には無効です。</span><span class="sxs-lookup"><span data-stu-id="d90f6-105">The following options are not valid when modifying XML indexes:</span></span>  
  
-   <span data-ttu-id="d90f6-106">再構築と設定オプションの IGNORE_DUP_KEY は XML インデックスでは無効です。</span><span class="sxs-lookup"><span data-stu-id="d90f6-106">The rebuild and set option IGNORE_DUP_KEY is not valid for XML indexes.</span></span> <span data-ttu-id="d90f6-107">再構築オプション ONLINE は、セカンダリ XML インデックスでは OFF に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d90f6-107">The rebuild option ONLINE must be set to OFF for secondary XML indexes.</span></span> <span data-ttu-id="d90f6-108">オプション DROP_EXISTING は、ALTER INDEX ステートメントでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d90f6-108">The option DROP_EXISTING is not permitted in the ALTER INDEX statement.</span></span>  
  
-   <span data-ttu-id="d90f6-109">ユーザー テーブルの主キー制約に変更があった場合、自動的には XML インデックスに反映されません。</span><span class="sxs-lookup"><span data-stu-id="d90f6-109">The modifications of the primary key constraint in the user table are not automatically propagated to XML indexes.</span></span> <span data-ttu-id="d90f6-110">ユーザーが、まず XML インデックスを削除し、次に XML インデックスを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d90f6-110">The user must drop the XML indexes first and then re-create them.</span></span>  
  
-   <span data-ttu-id="d90f6-111">ALTER INDEX ALL を指定すると、このオプションは XML 以外のインデックスと XML インデックスの両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d90f6-111">If ALTER INDEX ALL is specified, it applies to both non-XML and XML indexes.</span></span> <span data-ttu-id="d90f6-112">一方の種類のインデックスでは無効なインデックス オプションが指定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d90f6-112">Indexing options may be specified that are not valid for both types of indexes.</span></span> <span data-ttu-id="d90f6-113">その場合、ステートメント全体が失敗します。</span><span class="sxs-lookup"><span data-stu-id="d90f6-113">In this case, the whole statement fails.</span></span>  
  
## <a name="example-modifying-an-xml-index"></a><span data-ttu-id="d90f6-114">例: XML インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="d90f6-114">Example: Modifying an XML Index</span></span>  
 <span data-ttu-id="d90f6-115">次の例では、XML インデックスを作成後、 `ALLOW_ROW_LOCKS` オプションを `OFF`に設定してインデックスを変更します。</span><span class="sxs-lookup"><span data-stu-id="d90f6-115">In the following example, an XML index is created and then modified by setting the option `ALLOW_ROW_LOCKS` to `OFF`.</span></span> <span data-ttu-id="d90f6-116">`ALLOW_ROW_LOCKS` が `OFF`の場合、行はロックされないので、ページレベルおよびテーブルレベルのロックを使用して、指定したインデックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d90f6-116">When `ALLOW_ROW_LOCKS` is `OFF`, rows are not locked and access to the specified indexes is obtained by using page-and table-level locks.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## <a name="example-disabling-and-enabling-an-xml-index"></a><span data-ttu-id="d90f6-117">例: XML インデックスの無効化と有効化</span><span class="sxs-lookup"><span data-stu-id="d90f6-117">Example: Disabling and Enabling an XML Index</span></span>  
 <span data-ttu-id="d90f6-118">既定では、XML インデックスは有効です。</span><span class="sxs-lookup"><span data-stu-id="d90f6-118">By default, an XML index is enabled.</span></span> <span data-ttu-id="d90f6-119">XML インデックスが無効になっている場合、その XML 列に実行されるクエリでは XML インデックスが使用されません。</span><span class="sxs-lookup"><span data-stu-id="d90f6-119">If an XML index is disabled, the queries running against the XML column do not use the XML index.</span></span> <span data-ttu-id="d90f6-120">XML インデックスを有効にするには、 `ALTER INDEX` オプションを指定した `REBUILD` を使用します。</span><span class="sxs-lookup"><span data-stu-id="d90f6-120">To enable an XML index, use `ALTER INDEX` with the `REBUILD` option.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="d90f6-121">参照</span><span class="sxs-lookup"><span data-stu-id="d90f6-121">See Also</span></span>  
 [<span data-ttu-id="d90f6-122">XML インデックス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d90f6-122">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
