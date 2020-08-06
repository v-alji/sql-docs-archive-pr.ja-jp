---
title: NULL 処理 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 430643e8a6c9bd3dd00b2763990645c6a162ee40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642708"
---
# <a name="null-handling-sqlxml-40"></a><span data-ttu-id="1b83b-102">NULL の取り扱い (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="1b83b-102">NULL Handling (SQLXML 4.0)</span></span>
  <span data-ttu-id="1b83b-103">XML 構文では、NULL は "存在しない" ことを表します。</span><span class="sxs-lookup"><span data-stu-id="1b83b-103">XML syntax denotes NULL as an absence.</span></span> <span data-ttu-id="1b83b-104">(たとえば、属性または要素の値が NULL の場合、その属性または要素は XML ドキュメントに存在しません)。SQLXML では、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] `updg:nullvalue` 属性を使用して、要素または属性値に NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b83b-104">(For example, if an attribute or element value is NULL, that attribute or element is absent from the XML document.) In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, the `updg:nullvalue` attribute enables specifying NULL for an element or attribute value.</span></span>  
  
 <span data-ttu-id="1b83b-105">たとえば、次のアップデートグラムでは、 **ContactID**が64である連絡先の**TITLE**値が NULL であることを確認し、 **title**値を "Mr" に更新します。</span><span class="sxs-lookup"><span data-stu-id="1b83b-105">For example, the following updategram ensures that the **Title** value for a contact with **ContactID** of 64 is NULL, and then updates the **Title** value to "Mr."</span></span> <span data-ttu-id="1b83b-106">をお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="1b83b-106">for this contact.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="1b83b-107">パラメーターをアップデートグラムに渡すときには、パラメーター値として NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b83b-107">When parameters are passed to an updategram, NULL can be passed as the parameter value.</span></span> <span data-ttu-id="1b83b-108">これを行うには、`nullvalue` ブロックに `<updg:header>` 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b83b-108">This is done by specifying the `nullvalue` attribute in the `<updg:header>` block.</span></span> <span data-ttu-id="1b83b-109">例については、「[アップデートグラムへのパラメーターの引き渡し &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b83b-109">For an example, see [Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b83b-110">参照</span><span class="sxs-lookup"><span data-stu-id="1b83b-110">See Also</span></span>  
 [<span data-ttu-id="1b83b-111">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="1b83b-111">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
