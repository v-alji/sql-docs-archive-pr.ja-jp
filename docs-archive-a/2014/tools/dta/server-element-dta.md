---
title: Server 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab67e0303c2b629c3774886441474f5ef5b10a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643056"
---
# <a name="server-element-dta"></a><span data-ttu-id="1d993-102">Server 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="1d993-102">Server Element (DTA)</span></span>
  <span data-ttu-id="1d993-103">チューニングするデータベースが置かれているサーバーの識別情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d993-103">Contains the identifying information for the server on which the databases reside that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d993-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d993-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="1d993-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="1d993-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="1d993-106">特徴</span><span class="sxs-lookup"><span data-stu-id="1d993-106">Characteristic</span></span>|<span data-ttu-id="1d993-107">説明</span><span class="sxs-lookup"><span data-stu-id="1d993-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1d993-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="1d993-108">**Data type and length**</span></span>|<span data-ttu-id="1d993-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="1d993-109">None.</span></span>|  
|<span data-ttu-id="1d993-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="1d993-110">**Default value**</span></span>|<span data-ttu-id="1d993-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="1d993-111">None.</span></span>|  
|<span data-ttu-id="1d993-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="1d993-112">**Occurrence**</span></span>|<span data-ttu-id="1d993-113">必須。`DTAInput` 要素につき 1 個。</span><span class="sxs-lookup"><span data-stu-id="1d993-113">Required once per `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="1d993-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="1d993-114">Element Relationships</span></span>  
  
|<span data-ttu-id="1d993-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="1d993-115">Relationship</span></span>|<span data-ttu-id="1d993-116">要素</span><span class="sxs-lookup"><span data-stu-id="1d993-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="1d993-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="1d993-117">**Parent element**</span></span>|[<span data-ttu-id="1d993-118">DTAInput 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1d993-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="1d993-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="1d993-119">**Child elements**</span></span>|[<span data-ttu-id="1d993-120">Server の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1d993-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="1d993-121">Server の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1d993-121">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="1d993-122">解説</span><span class="sxs-lookup"><span data-stu-id="1d993-122">Remarks</span></span>  
 <span data-ttu-id="1d993-123">要素に指定できる要素は1つだけ `Server` `DTAInput` です。</span><span class="sxs-lookup"><span data-stu-id="1d993-123">You can specify only one `Server` element for the `DTAInput` element.</span></span> <span data-ttu-id="1d993-124">この要素は、DTA XML スキーマの **ServerDetailsTypecomplexType** の名前です。</span><span class="sxs-lookup"><span data-stu-id="1d993-124">This element is of the **ServerDetailsTypecomplexType** name in the DTA XML schema.</span></span> <span data-ttu-id="1d993-125">この `Server` 要素を `Configuration` 要素の子要素と混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="1d993-125">Do not confuse this `Server` element with the one that is the child of the `Configuration` element.</span></span> <span data-ttu-id="1d993-126">詳細については、「[Configuration のサーバー要素 &#40;DTA&#41;](server-element-for-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d993-126">For more information, see [Server Element for Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d993-127">例</span><span class="sxs-lookup"><span data-stu-id="1d993-127">Example</span></span>  
 <span data-ttu-id="1d993-128">次の例は、SERVER001 上の **AdventureWorks** データベースの **Sales.SalesPerson** テーブルを指定する方法を示しています:</span><span class="sxs-lookup"><span data-stu-id="1d993-128">The following example shows how to specify the **Sales.SalesPerson** table in the **AdventureWorks** database on SERVER001:</span></span>  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d993-129">参照</span><span class="sxs-lookup"><span data-stu-id="1d993-129">See Also</span></span>  
 [<span data-ttu-id="1d993-130">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="1d993-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
