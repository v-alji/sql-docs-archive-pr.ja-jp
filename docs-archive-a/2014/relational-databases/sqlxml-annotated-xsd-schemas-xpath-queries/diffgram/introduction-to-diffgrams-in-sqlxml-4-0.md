---
title: SQLXML 4.0 | の Diffgram の概要Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
author: rothja
ms.author: jroth
ms.openlocfilehash: e57d87d064ace47247f342ed002b162b920e627f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641553"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a><span data-ttu-id="7e500-102">SQLXML 4.0 の DiffGram の概要</span><span class="sxs-lookup"><span data-stu-id="7e500-102">Introduction to DiffGrams in SQLXML 4.0</span></span>
  <span data-ttu-id="7e500-103">ここでは、DiffGram の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="7e500-103">This topic provides a brief introduction to DiffGrams.</span></span>  
  
## <a name="diffgram-format"></a><span data-ttu-id="7e500-104">DiffGram 形式</span><span class="sxs-lookup"><span data-stu-id="7e500-104">DiffGram Format</span></span>  
 <span data-ttu-id="7e500-105">一般的な DiffGram の書式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e500-105">This is the general DiffGram format:</span></span>  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="7e500-106">DiffGram の書式は次のブロックで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7e500-106">The DiffGram format consists of these blocks:</span></span>  
  
 **\<DataInstance>**  
 <span data-ttu-id="7e500-107">この要素の名前 **DataInstance** は、このドキュメントでの説明用に使用するものです。</span><span class="sxs-lookup"><span data-stu-id="7e500-107">The name of this element, **DataInstance**, is used for explanation purposes in this documentation.</span></span> <span data-ttu-id="7e500-108">たとえば、.NET Framework のデータセットから DiffGram が生成された場合、この要素の名前としてデータセットの**name**プロパティの値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-108">For example, if the DiffGram were generated from a dataset in the .NET Framework, the value of the **Name** property of the dataset would be used as the name of this element.</span></span> <span data-ttu-id="7e500-109">このブロックには、変更後のすべての関連データを指定します。変更されていないデータも指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e500-109">This block contains all relevant data after the change, possibly including data that has not been modified.</span></span> <span data-ttu-id="7e500-110">DiffGram 処理ロジックでは、次のブロック内の要素は無視されます。このブロックは、次の**よう**な属性が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="7e500-110">The DiffGram processing logic ignores the elements in this block for which the **diffgr:hasChanges** attribute is not specified.</span></span>  
  
 **\<diffgr:before>**  
 <span data-ttu-id="7e500-111">省略可能なブロックです。更新または削除する必要がある元のレコード インスタンス (要素) を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e500-111">This optional block contains the original record instances (elements) that must be updated or deleted.</span></span> <span data-ttu-id="7e500-112">DiffGram によって変更 (更新または削除) されるすべてのデータベーステーブルは、ブロック内の最上位レベルの要素として表示される必要があり **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="7e500-112">All the database tables being modified (updated or deleted) by the DiffGram must appear as top-level elements in the **\<before>** block.</span></span>  
  
 **\<diffgr:errors>**  
 <span data-ttu-id="7e500-113">省略可能なブロックです。DiffGram の処理ロジックでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-113">This optional block is ignored by the DiffGram processing logic.</span></span>  
  
## <a name="diffgram-annotations"></a><span data-ttu-id="7e500-114">DiffGram 注釈</span><span class="sxs-lookup"><span data-stu-id="7e500-114">DiffGram Annotations</span></span>  
 <span data-ttu-id="7e500-115">これらの注釈は、DiffGram 名前空間 **"urn: schema-01"** で定義されています。</span><span class="sxs-lookup"><span data-stu-id="7e500-115">These annotations are defined in the DiffGram namespace **"urn:schemas-microsoft-com:xml-diffgram-01"**:</span></span>  
  
 <span data-ttu-id="7e500-116">**ID**</span><span class="sxs-lookup"><span data-stu-id="7e500-116">**id**</span></span>  
 <span data-ttu-id="7e500-117">この属性は、とブロックの要素をペアにするために使用され **\<before>** **\<DataInstance>** ます。</span><span class="sxs-lookup"><span data-stu-id="7e500-117">This attribute is used to pair the elements in the **\<before>** and the **\<DataInstance>** blocks.</span></span>  
  
 <span data-ttu-id="7e500-118">**hasChanges**</span><span class="sxs-lookup"><span data-stu-id="7e500-118">**hasChanges**</span></span>  
 <span data-ttu-id="7e500-119">挿入操作または更新操作の場合、DiffGram では、**挿入**または**変更**された値を使用してこの属性を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e500-119">For an insert or an update operation, the DiffGram must specify this attribute with the value **inserted** or **modified**.</span></span> <span data-ttu-id="7e500-120">この属性が存在しない場合、内の対応する要素 **\<DataInstance>** は処理ロジックによって無視され、更新は実行されません。</span><span class="sxs-lookup"><span data-stu-id="7e500-120">If this attribute is not present, the corresponding element in the **\<DataInstance>** is ignored by the processing logic and no updates are performed.</span></span> <span data-ttu-id="7e500-121">実際のサンプルについては、「 [DiffGram の例 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e500-121">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="7e500-122">**parentID**</span><span class="sxs-lookup"><span data-stu-id="7e500-122">**parentID**</span></span>  
 <span data-ttu-id="7e500-123">この属性は、DiffGram の要素間の親子リレーションシップを指定するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="7e500-123">This attribute is used to specify parent-child relationships among the elements in the DiffGram.</span></span> <span data-ttu-id="7e500-124">この属性はブロックにのみ表示され \<before> ます。</span><span class="sxs-lookup"><span data-stu-id="7e500-124">This attribute appears only in the \<before> block.</span></span> <span data-ttu-id="7e500-125">この属性は更新の適用時に SQLXML で使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-125">It is used by SQLXML when applying updates.</span></span> <span data-ttu-id="7e500-126">親子リレーションシップは、DiffGram の要素の処理順序を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-126">The parent-child relationship is used in determining the order in which the elements in the DiffGram are processed.</span></span>  
  
## <a name="understanding-the-diffgram-processing-logic"></a><span data-ttu-id="7e500-127">DiffGram の処理ロジックについて</span><span class="sxs-lookup"><span data-stu-id="7e500-127">Understanding the DiffGram Processing Logic</span></span>  
 <span data-ttu-id="7e500-128">DiffGram の処理ロジックでは、一定の規則に従い、挿入、更新、削除のうちどの操作であるかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-128">The DiffGram processing logic uses certain rules to determine whether an operation is an insert, update, or delete operation.</span></span> <span data-ttu-id="7e500-129">次の表は、この規則についてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="7e500-129">These rules are described in the following table.</span></span>  
  
|<span data-ttu-id="7e500-130">操作</span><span class="sxs-lookup"><span data-stu-id="7e500-130">Operation</span></span>|<span data-ttu-id="7e500-131">説明</span><span class="sxs-lookup"><span data-stu-id="7e500-131">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e500-132">挿入</span><span class="sxs-lookup"><span data-stu-id="7e500-132">Insert</span></span>|<span data-ttu-id="7e500-133">DiffGram は、要素がブロック内に存在 **\<DataInstance>** しても対応するブロックに含まれておらず、 **\<before>** 要素に対して "、" と**いう**属性が指定されている (**diffgram gr: haschanges = inserted**) 場合に挿入操作を示します。</span><span class="sxs-lookup"><span data-stu-id="7e500-133">A DiffGram indicates an insert operation when an element appears in the **\<DataInstance>** block but not in the corresponding **\<before>** block, and the **diffgr:hasChanges** attribute is specified (**diffgr:hasChanges=inserted**) on the element.</span></span> <span data-ttu-id="7e500-134">この場合、DiffGram はブロックで指定されたレコードインスタンスを **\<DataInstance>** データベースに挿入します。</span><span class="sxs-lookup"><span data-stu-id="7e500-134">In this case, the DiffGram inserts the record instance that is specified in the **\<DataInstance>** block into the database.</span></span><br /><br /> <span data-ttu-id="7e500-135">次の**よう**に、属性が指定されていない場合、要素は処理ロジックによって無視され、挿入は実行されません。</span><span class="sxs-lookup"><span data-stu-id="7e500-135">If the **diffgr:hasChanges** attribute is not specified, the element is ignored by the processing logic and no insert is performed.</span></span> <span data-ttu-id="7e500-136">実際のサンプルについては、「 [DiffGram の例 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e500-136">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>|  
|<span data-ttu-id="7e500-137">更新</span><span class="sxs-lookup"><span data-stu-id="7e500-137">Update</span></span>|<span data-ttu-id="7e500-138">DiffGram は、ブロック内に対応する要素が存在する (つまり、両方の要素の値が同じである) 要素がブロック内に存在 \<before> **\<DataInstance>** し**diffgr:id** 、ブロック内の要素で**変更**された値を使用し**て、すべて**の要素の属性が指定されている場合に、更新操作を示し **\<DataInstance>** ます。</span><span class="sxs-lookup"><span data-stu-id="7e500-138">The DiffGram indicates an update operation when there is an element in the \<before> block for which there is a corresponding element in the **\<DataInstance>** block (that is, both elements have a **diffgr:id** attribute with same value) and the **diffgr:hasChanges** attribute is specified with the value **modified** on the element in the **\<DataInstance>** block.</span></span><br /><br /> <span data-ttu-id="7e500-139">ブロック内の要素で、"次の値に**変更**する" 属性が指定されていない場合 **\<DataInstance>** 、処理ロジックによってエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-139">If the **diffgr:hasChanges** attribute is not specified on the element in the **\<DataInstance>** block, an error is returned by the processing logic.</span></span> <span data-ttu-id="7e500-140">実際のサンプルについては、「 [DiffGram の例 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e500-140">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="7e500-141">場合 **、** このブロックで指定されている **\<before>** 要素の親子リレーションシップ**は、** レコードを更新する順序を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-141">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are updated.</span></span>|  
|<span data-ttu-id="7e500-142">削除</span><span class="sxs-lookup"><span data-stu-id="7e500-142">Delete</span></span>|<span data-ttu-id="7e500-143">DiffGram は、要素が **\<before>** ブロックにあり、対応するブロックには存在しない場合に、削除操作を示し **\<DataInstance>** ます。</span><span class="sxs-lookup"><span data-stu-id="7e500-143">A DiffGram indicates a delete operation when an element appears in the **\<before>** block but not in the corresponding **\<DataInstance>** block.</span></span> <span data-ttu-id="7e500-144">この場合、DiffGram は、ブロックで指定されたレコードインスタンスを **\<before>** データベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="7e500-144">In this case, the DiffGram deletes the record instance that is specified in the **\<before>** block from the database.</span></span> <span data-ttu-id="7e500-145">実際のサンプルについては、「 [DiffGram の例 &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e500-145">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="7e500-146">場合 **、** このブロックで指定されている **\<before>** 要素の親子リレーションシップ**は、** レコードを削除する順序を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e500-146">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are deleted.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7e500-147">DiffGram にパラメーターを渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7e500-147">Parameters cannot be passed to DiffGrams.</span></span>  
  
  
