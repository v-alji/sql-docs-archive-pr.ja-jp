---
title: 特定の種類のスクリプト コンポーネントの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 114c9ddca90ea02a8e1847444b28b9d5876650a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641738"
---
# <a name="developing-specific-types-of-script-components"></a><span data-ttu-id="005ac-102">特定の種類のスクリプト コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="005ac-102">Developing Specific Types of Script Components</span></span>
  <span data-ttu-id="005ac-103">スクリプト コンポーネントは構成可能なツールです。パッケージのデータ フローで使用すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に備わっている変換元、変換、および変換先では満たせないほとんどすべての要件に対応できます。</span><span class="sxs-lookup"><span data-stu-id="005ac-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="005ac-104">ここで紹介するスクリプト コンポーネントのコード例では、スクリプト コンポーネントの 4 つの構成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="005ac-104">This section contains Script component code samples that demonstrate the four options for configuring the Script component:</span></span>  
  
-   <span data-ttu-id="005ac-105">変換元として構成する</span><span class="sxs-lookup"><span data-stu-id="005ac-105">As a source.</span></span>  
  
-   <span data-ttu-id="005ac-106">同期出力型の変換として構成する</span><span class="sxs-lookup"><span data-stu-id="005ac-106">As a transformation with synchronous outputs.</span></span>  
  
-   <span data-ttu-id="005ac-107">非同期出力型の変換として出力する</span><span class="sxs-lookup"><span data-stu-id="005ac-107">As a transformation with asynchronous outputs.</span></span>  
  
-   <span data-ttu-id="005ac-108">変換先として出力する</span><span class="sxs-lookup"><span data-stu-id="005ac-108">As a destination.</span></span>  
  
 <span data-ttu-id="005ac-109">スクリプト コンポーネントのその他の例については、「[その他のスクリプト コンポーネントの例](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="005ac-109">For additional examples of the Script component, see [Additional Script Component Examples](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="005ac-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="005ac-110">In This Section</span></span>  
 [<span data-ttu-id="005ac-111">スクリプト コンポーネントによる変換元の作成</span><span class="sxs-lookup"><span data-stu-id="005ac-111">Creating a Source with the Script Component</span></span>](creating-a-source-with-the-script-component.md)  
 <span data-ttu-id="005ac-112">スクリプト コンポーネントを使用してデータ フローの変換元を作成する方法を、説明および例示します。</span><span class="sxs-lookup"><span data-stu-id="005ac-112">Explains and demonstrates how to create a data flow source by using the Script component.</span></span>  
  
 [<span data-ttu-id="005ac-113">スクリプト コンポーネントによる同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="005ac-113">Creating a Synchronous Transformation with the Script Component</span></span>](creating-a-synchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="005ac-114">スクリプト コンポーネントを使用して同期出力型のデータ フロー変換を作成する方法を、説明および例示します。</span><span class="sxs-lookup"><span data-stu-id="005ac-114">Explains and demonstrates how to create a data flow transformation with synchronous outputs by using the Script component.</span></span> <span data-ttu-id="005ac-115">この種類の変換は、スクリプト コンポーネントを通過する時点でデータ行を変更します。</span><span class="sxs-lookup"><span data-stu-id="005ac-115">This kind of transformation modifies rows of data in place as they pass through the component.</span></span>  
  
 [<span data-ttu-id="005ac-116">スクリプト コンポーネントによる非同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="005ac-116">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="005ac-117">スクリプト コンポーネントを使用して非同期出力型のデータ フロー変換を作成する方法を、説明および例示します。</span><span class="sxs-lookup"><span data-stu-id="005ac-117">Explains and demonstrates how to create a data flow transformation with asynchronous outputs by using the Script component.</span></span> <span data-ttu-id="005ac-118">この種類の変換では、計算された集計結果などの追加情報をコンポーネントを通過するデータに追加する前に、すべてのデータ行を読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="005ac-118">This kind of transformation has to read all rows of data before it can add more information, such as calculated aggregates, to the data that passes through the component.</span></span>  
  
 [<span data-ttu-id="005ac-119">スクリプト コンポーネントによる変換先の作成</span><span class="sxs-lookup"><span data-stu-id="005ac-119">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 <span data-ttu-id="005ac-120">スクリプト コンポーネントを使用してデータ フローの変換先を作成する方法を、説明および例示します。</span><span class="sxs-lookup"><span data-stu-id="005ac-120">Explains and demonstrates how to create a data flow destination by using the Script component.</span></span>  
  
<span data-ttu-id="005ac-121">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="005ac-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="005ac-122">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="005ac-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="005ac-123">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="005ac-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="005ac-124">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="005ac-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005ac-125">参照</span><span class="sxs-lookup"><span data-stu-id="005ac-125">See Also</span></span>  
 <span data-ttu-id="005ac-126">[スクリプトソリューションとカスタムオブジェクトの比較](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="005ac-126">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="005ac-127">特定の種類のデータ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="005ac-127">Developing Specific Types of Data Flow Components</span></span>](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
