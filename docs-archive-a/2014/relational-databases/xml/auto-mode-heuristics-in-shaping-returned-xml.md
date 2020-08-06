---
title: 返される XML を構造化する際の AUTO モード ヒューリスティック | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a64cda8989e1e45d4ad869f8883e1c9d65f4b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631706"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a><span data-ttu-id="57870-102">返される XML を構造化する際の AUTO モード ヒューリスティック</span><span class="sxs-lookup"><span data-stu-id="57870-102">AUTO Mode Heuristics in Shaping Returned XML</span></span>
  <span data-ttu-id="57870-103">AUTO モードでは、返される XML の構造はクエリに基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="57870-103">AUTO mode determines the shape of returned XML based on the query.</span></span> <span data-ttu-id="57870-104">要素を入れ子にする方法を決定するとき、AUTO モード ヒューリスティックによって、隣接する行の列値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="57870-104">In determining how elements are to be nested, AUTO mode heuristics compare column values in adjacent rows.</span></span> <span data-ttu-id="57870-105">**ntext**型、 **text**型、 **image**型、および **xml**型を除くすべての型の列が比較されます。</span><span class="sxs-lookup"><span data-stu-id="57870-105">Columns of all types, except **ntext**, **text**, **image**, and **xml**, are compared.</span></span> <span data-ttu-id="57870-106">**(n)varchar(max)** 型と **varbinary(max)** 型の列は比較されます。</span><span class="sxs-lookup"><span data-stu-id="57870-106">Columns of type **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="57870-107">次の例では、生成される XML の構造を決定する AUTO モード ヒューリスティックを示します。</span><span class="sxs-lookup"><span data-stu-id="57870-107">The following example illustrates the AUTO mode heuristics that determine the shape of the resulting XML:</span></span>  
  
```  
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
FOR XML AUTO  
ORDER BY T1.Id  
```  
  
 <span data-ttu-id="57870-108">テーブル T1 のキーが指定されていない場合は、新しい <`T1`> 要素の開始位置を決定するために、**ntext** 型、**text** 型、**image** 型、および **xml** 型を除く T1 の列のすべての値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="57870-108">To determine where a new <`T1`> element starts, all column values of T1, except **ntext**, **text**, **image** and **xml**, are compared if the key on the table T1 is not specified.</span></span> <span data-ttu-id="57870-109">次に、 **Name** 列が **nvarchar(40)** 型で、SELECT ステートメントから次の行セットが返されるとします。</span><span class="sxs-lookup"><span data-stu-id="57870-109">Next, assume that the **Name** column is **nvarchar(40)** and the SELECT statement returns this rowset:</span></span>  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 <span data-ttu-id="57870-110">AUTO モード ヒューリスティックにより、テーブル T1 のすべての値 (Id 列と Name 列) が比較されます。</span><span class="sxs-lookup"><span data-stu-id="57870-110">The AUTO mode heuristics compare all the values of table T1, the Id and Name columns.</span></span> <span data-ttu-id="57870-111">最初の 2 行の Id 列と Name 列の値は同じなので、2 つの \<T2> 子要素を持っている 1 つの \<T1> 要素が結果に追加されます。</span><span class="sxs-lookup"><span data-stu-id="57870-111">Because the first two rows have the same values for the Id and Name columns, one \<T1> element having two \<T2> child elements is added in the result.</span></span>  
  
 <span data-ttu-id="57870-112">次に、返される XML を示します。</span><span class="sxs-lookup"><span data-stu-id="57870-112">Following is the XML that is returned:</span></span>  
  
```  
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 <span data-ttu-id="57870-113">ここで、Name 列は **text** 型であるとします。</span><span class="sxs-lookup"><span data-stu-id="57870-113">Now assume that the Name column is of **text** type.</span></span> <span data-ttu-id="57870-114">この型の値は、AUTO モード ヒューリスティックによって比較されません。</span><span class="sxs-lookup"><span data-stu-id="57870-114">The AUTO mode heuristics do not compare the values for this type.</span></span> <span data-ttu-id="57870-115">この場合、値が異なると想定されます。</span><span class="sxs-lookup"><span data-stu-id="57870-115">Instead, it assumes that the values are not the same.</span></span> <span data-ttu-id="57870-116">この結果、次に示すように XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="57870-116">This results in XML generation as shown in the following:</span></span>  
  
```  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57870-117">参照</span><span class="sxs-lookup"><span data-stu-id="57870-117">See Also</span></span>  
 [<span data-ttu-id="57870-118">FOR XML での AUTO モードの使用</span><span class="sxs-lookup"><span data-stu-id="57870-118">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
