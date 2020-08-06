---
title: RDL ファイルのアセンブリの参照 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14593717d2319d7d702fd0c414e0c24428006f51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712822"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a><span data-ttu-id="6bc2a-102">RDL ファイルのアセンブリの参照</span><span class="sxs-lookup"><span data-stu-id="6bc2a-102">Referencing Assemblies in an RDL File</span></span>
  <span data-ttu-id="6bc2a-103">レポート定義ファイルでのカスタム コード アセンブリの使用をサポートするため、2 つのレポート定義言語 (RDL) 要素 **CodeModules** と **Classes** が RDL 仕様に含まれています。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-103">To support the use of custom code assemblies in report definition files, two Report Definition Language (RDL) elements are included in the RDL specification: the **CodeModules** element and the **Classes** element.</span></span>  
  
 <span data-ttu-id="6bc2a-104">**CodeModules** 要素を使用すると、レポート式でマネージド コード アセンブリを参照できます。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-104">The **CodeModules** element enables you to refer to managed code assemblies in report expressions.</span></span> <span data-ttu-id="6bc2a-105">**CodeModules** は、レポート定義ファイルで特殊な関数の呼び出しに使用するアセンブリへの参照を含むトップレベルの要素です。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-105">**CodeModules** is a top-level element that contains the reference to the assembly that you use in your report definition files to call specialized functions.</span></span> <span data-ttu-id="6bc2a-106">カスタム アセンブリの使用をサポートするレポート定義のエントリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-106">An entry in a report definition that supports the use of a custom assembly might look like the following:</span></span>  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 <span data-ttu-id="6bc2a-107">カスタム コードから <xref:System.Reflection.Assembly.Load%2A> を呼び出すのではなく、**CodeModule** 要素を RDL ファイルに手動で追加するか、**[レポートのプロパティ]** ダイアログの **[参照]** タブを使用してカスタム アセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-107">Instead of calling <xref:System.Reflection.Assembly.Load%2A> from your custom code, register your custom assemblies by either manually adding **CodeModule** elements to your RDL file or by using the **References** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="6bc2a-108">詳細については、「 [レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)を表しています。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-108">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="6bc2a-109">**Classes** 要素では、レポート定義でのインスタンス メンバーの使用がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-109">The **Classes** element supports the use of instance members in a report definition.</span></span> <span data-ttu-id="6bc2a-110">**Classes** は、クラス名とインスタンス名への参照を含むトップレベルの要素です。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-110">**Classes** is a top-level element that contains a reference to the class name and an instance name.</span></span> <span data-ttu-id="6bc2a-111">インスタンス メンバーの使用をサポートするレポート定義のエントリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-111">An entry in a report definition that supports the use of instance members might look like the following:</span></span>  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 <span data-ttu-id="6bc2a-112">詳細については、「[式を使用したカスタム アセンブリへのアクセス](accessing-custom-assemblies-through-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bc2a-112">For more information, see [Accessing Custom Assemblies Through Expressions](accessing-custom-assemblies-through-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc2a-113">参照</span><span class="sxs-lookup"><span data-stu-id="6bc2a-113">See Also</span></span>  
 [<span data-ttu-id="6bc2a-114">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="6bc2a-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
