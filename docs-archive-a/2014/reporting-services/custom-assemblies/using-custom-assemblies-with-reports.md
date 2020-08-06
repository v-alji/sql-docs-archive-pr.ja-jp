---
title: レポートでのカスタム アセンブリの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f77b9da44ebb57617bd45e43d1e1e847e9074662
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713901"
---
# <a name="using-custom-assemblies-with-reports"></a><span data-ttu-id="26423-102">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="26423-102">Using Custom Assemblies with Reports</span></span>
  <span data-ttu-id="26423-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート アイテムの値、スタイル、および書式設定に関するカスタム コードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="26423-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can write custom code for report item values, styles, and formatting.</span></span> <span data-ttu-id="26423-104">たとえば、カスタム コードを使用して、ロケールに基づいて通貨を書式設定したり、特殊な書式設定の特定の値にフラグを設定したり、または企業で実際に使用している他のビジネス ルールを適用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="26423-104">For example, you can use custom code to format currencies based on locale, flag certain values with special formatting, or apply other business rules that are in practice for your company.</span></span> <span data-ttu-id="26423-105">このコードをレポートに含める方法の1つは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] レポート定義ファイル内から参照できるを使用して、カスタムコードアセンブリを作成することです。</span><span class="sxs-lookup"><span data-stu-id="26423-105">One way to include this code in your reports is to create a custom code assembly using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that you can reference from within your report definition files.</span></span> <span data-ttu-id="26423-106">サーバーは、レポートを実行するときにカスタム アセンブリの関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="26423-106">The server calls the functions in your custom assemblies when a report is run.</span></span> <span data-ttu-id="26423-107">カスタム アセンブリは、レポートで使用する特別な関数を取得するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="26423-107">Custom assemblies can be used to retrieve specialized functions that you plan to use in your reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26423-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="26423-108">In This Section</span></span>  
 [<span data-ttu-id="26423-109">RDL ファイルのアセンブリの参照</span><span class="sxs-lookup"><span data-stu-id="26423-109">Referencing Assemblies in an RDL File</span></span>](referencing-assemblies-in-an-rdl-file.md)  
 <span data-ttu-id="26423-110">レポート定義言語ファイルのカスタム アセンブリを参照する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26423-110">Describes how to reference your custom assemblies in a report definition language file.</span></span>  
  
 [<span data-ttu-id="26423-111">カスタム アセンブリの配置</span><span class="sxs-lookup"><span data-stu-id="26423-111">Deploying a Custom Assembly</span></span>](deploying-a-custom-assembly.md)  
 <span data-ttu-id="26423-112">カスタム アセンブリをレポート デザイナーとレポート サーバーに配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26423-112">Describes how to deploy a custom assembly to Report Designer and the report server.</span></span>  
  
 [<span data-ttu-id="26423-113">複雑な名前を持つカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="26423-113">Using Strong-Named Custom Assemblies</span></span>](using-strong-named-custom-assemblies.md)  
 <span data-ttu-id="26423-114">複雑な名前を持つカスタム アセンブリの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26423-114">Describes how to use custom assemblies with strong names.</span></span>  
  
 [<span data-ttu-id="26423-115">カスタム アセンブリでの権限のアサート</span><span class="sxs-lookup"><span data-stu-id="26423-115">Asserting Permissions in Custom Assemblies</span></span>](asserting-permissions-in-custom-assemblies.md)  
 <span data-ttu-id="26423-116">カスタム アセンブリの権限を限定して配置する方法と権限をコード内でアサートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26423-116">Describes how to deploy custom assemblies with limited and specific permissions and how to assert those permissions in code.</span></span>  
  
 [<span data-ttu-id="26423-117">式を使用したカスタム アセンブリへのアクセス</span><span class="sxs-lookup"><span data-stu-id="26423-117">Accessing Custom Assemblies Through Expressions</span></span>](accessing-custom-assemblies-through-expressions.md)  
 <span data-ttu-id="26423-118">カスタム アセンブリ メソッドをレポート定義のレポート式として呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26423-118">Describes how to call custom assembly methods as report expressions in your report definitions.</span></span>  
  
 [<span data-ttu-id="26423-119">カスタム アセンブリ オブジェクトの初期化</span><span class="sxs-lookup"><span data-stu-id="26423-119">Initializing Custom Assembly Objects</span></span>](initializing-custom-assembly-objects.md)  
 <span data-ttu-id="26423-120">レポートから呼び出されたカスタム アセンブリ オブジェクトの値を初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26423-120">Describes how to initialize values for custom assembly objects called from a report.</span></span>  
  
 [<span data-ttu-id="26423-121">方法:カスタム アセンブリをデバッグする</span><span class="sxs-lookup"><span data-stu-id="26423-121">How to: Debug Custom Assemblies</span></span>](how-to-debug-custom-assemblies.md)  
 <span data-ttu-id="26423-122">カスタム アセンブリ コードのデバッグ方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26423-122">Describes how to debug your custom assembly code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26423-123">参照</span><span class="sxs-lookup"><span data-stu-id="26423-123">See Also</span></span>  
 [<span data-ttu-id="26423-124">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="26423-124">Report Definition Language &#40;SSRS&#41;</span></span>](../reports/report-definition-language-ssrs.md)  
  
  
