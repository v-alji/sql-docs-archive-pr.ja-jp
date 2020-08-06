---
title: 式のリファレンス (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: bb16e4ab-b13f-48f2-8cfe-1851656875ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7854aa2cc256d63fe93ddb049486e782bfaa0e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634863"
---
# <a name="expression-reference-report-builder-and-ssrs"></a><span data-ttu-id="d6d69-102">式のリファレンス (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d6d69-102">Expression Reference (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d6d69-103">レポートの式には、各種の組み込み関数や組み込みコレクションの参照を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6d69-103">Report expressions support a variety of references to built-in functions and built-in collections.</span></span> <span data-ttu-id="d6d69-104">レポートをパブリッシュまたは処理するには、式に有効な [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 構文が使用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6d69-104">Expressions must have valid [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] syntax before a report can be published or processed.</span></span>  
  
 <span data-ttu-id="d6d69-105">複合式、またはカスタム コードやカスタム アセンブリを使った式を作成するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でレポート デザイナーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d6d69-105">To develop complex expressions or expressions that use custom code or custom assemblies, we recommend that you use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d6d69-106">詳細については、「 [レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)を表しています。</span><span class="sxs-lookup"><span data-stu-id="d6d69-106">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="d6d69-107">レポートで簡単な式を作成する方法については、このセクションで紹介している各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6d69-107">Use the topics in this section to help write simple expressions in a report.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6d69-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d6d69-108">In This Section</span></span>  
 [<span data-ttu-id="d6d69-109">式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-109">Data Types in Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="d6d69-110">式で使用される定数 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-110">Constants in Expressions &#40;Report Builder and SSRS&#41;</span></span>](constants-in-expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="d6d69-111">式で使用される演算子 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-111">Operators in Expressions &#40;Report Builder and SSRS&#41;</span></span>](operators-in-expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="d6d69-112">式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-112">Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-in-expressions-report-builder.md)  
  
 [<span data-ttu-id="d6d69-113">組み込み Globals および Users 参照 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d6d69-113">Built-in Globals and Users References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-built-in-globals-and-users-references-report-builder.md)  
  
 [<span data-ttu-id="d6d69-114">Parameters コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-114">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
 [<span data-ttu-id="d6d69-115">データセット フィールド コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-115">Dataset Fields Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-dataset-fields-collection-references-report-builder.md)  
  
 [<span data-ttu-id="d6d69-116">DataSources コレクションと DataSets コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-116">DataSources and DataSets Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-datasources-and-datasets-references-report-builder.md)  
  
 [<span data-ttu-id="d6d69-117">レポート変数コレクションとグループ変数コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-117">Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-report-and-group-variables-references-report-builder.md)  
  
 [<span data-ttu-id="d6d69-118">ReportItems コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-118">ReportItems Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-reportitems-collection-references-report-builder.md)  
  
## <a name="see-also"></a><span data-ttu-id="d6d69-119">参照</span><span class="sxs-lookup"><span data-stu-id="d6d69-119">See Also</span></span>  
 [<span data-ttu-id="d6d69-120">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6d69-120">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
