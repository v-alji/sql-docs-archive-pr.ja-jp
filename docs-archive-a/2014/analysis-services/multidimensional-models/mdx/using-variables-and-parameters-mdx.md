---
title: 変数とパラメーターの使用 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd01cf78ea5e3284aa51cad7dc848176a5dc9298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736990"
---
# <a name="using-variables-and-parameters-mdx"></a><span data-ttu-id="61a59-102">変数とパラメーターの使用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="61a59-102">Using Variables and Parameters (MDX)</span></span>
  <span data-ttu-id="61a59-103">では [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、多次元式 (MDX) ステートメントをパラメーター化できます。</span><span class="sxs-lookup"><span data-stu-id="61a59-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can parameterize a Multidimensional Expressions (MDX) statement.</span></span> <span data-ttu-id="61a59-104">ステートメントをパラメーター化すれば、実行時にカスタマイズ可能な汎用ステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="61a59-104">A parameterized statement lets you create generic statements that can be customized at runtime.</span></span>  
  
 <span data-ttu-id="61a59-105">パラメーター化されたステートメントを作成するときには、パラメーター名の前に @ 記号を付けることによってパラメーター名を識別します。</span><span class="sxs-lookup"><span data-stu-id="61a59-105">In creating a parameterized statement, you identify the parameter name by prefixing the name with the at sign (@).</span></span> <span data-ttu-id="61a59-106">たとえば、は @Year 有効なパラメーター名です。</span><span class="sxs-lookup"><span data-stu-id="61a59-106">For example, @Year would be a valid parameter name</span></span>  
  
 <span data-ttu-id="61a59-107">MDX は、リテラルまたはスカラー値用のパラメーターだけをサポートします。</span><span class="sxs-lookup"><span data-stu-id="61a59-107">MDX supports only parameters for literal or scalar values.</span></span> <span data-ttu-id="61a59-108">メンバー、セット、または組を参照するパラメーターを作成するには、 [StrToMember](/sql/mdx/strtomember-mdx) や [StrToSet](/sql/mdx/strtoset-mdx)などの関数を使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="61a59-108">To create a parameter that references a member, set, or tuple, you would have to use a function such as [StrToMember](/sql/mdx/strtomember-mdx) or [StrToSet](/sql/mdx/strtoset-mdx).</span></span>  
  
 <span data-ttu-id="61a59-109">次の XML for Analysis (XMLA) の例では、 @CountryName 顧客データを取得する国がパラメーターに含まれています。</span><span class="sxs-lookup"><span data-stu-id="61a59-109">In the following XML for Analysis (XMLA) example, the @CountryName parameter will contain the country for which customer data is retrieved:</span></span>  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 <span data-ttu-id="61a59-110">OLE DB でこの機能を使用するには、`ICommandWithParameters` インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="61a59-110">To use this functionality with OLE DB, you would use the `ICommandWithParameters` interface.</span></span> <span data-ttu-id="61a59-111">ADOMD.Net でこの機能を使用するには、 **AdomdCommand.Parameters** コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="61a59-111">To use this functionality with ADOMD.Net, you would use the **AdomdCommand.Parameters** collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a59-112">参照</span><span class="sxs-lookup"><span data-stu-id="61a59-112">See Also</span></span>  
 [<span data-ttu-id="61a59-113">MDX スクリプティングの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="61a59-113">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
