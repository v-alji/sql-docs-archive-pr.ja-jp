---
title: その他のスクリプト コンポーネントの例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: 849dd38a-abb5-4702-a413-882aae3980a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 897ca075674f5c3dbaf355390fe8346580bf638a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642185"
---
# <a name="additional-script-component-examples"></a><span data-ttu-id="3b291-102">その他のスクリプト コンポーネントの例</span><span class="sxs-lookup"><span data-stu-id="3b291-102">Additional Script Component Examples</span></span>
  <span data-ttu-id="3b291-103">スクリプト コンポーネントは構成可能なツールです。パッケージのデータ フローで使用すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に備わっている変換元、変換、および変換先では満たせないほとんどすべての要件に対応できます。</span><span class="sxs-lookup"><span data-stu-id="3b291-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="3b291-104">ここでは、使用できるさまざまな種類の機能を説明する、スクリプト コンポーネントのコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="3b291-104">This section contains Script component code samples that demonstrate the various types of functionality that are available.</span></span>  
  
 <span data-ttu-id="3b291-105">スクリプト コンポーネントを基本の変換元、変換、または変換先として構成する方法の例については、「[特定の種類のスクリプト コンポーネントの開発](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b291-105">For samples that demonstrate how to configure the Script component as a basic source, transformation, or destination, see [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b291-106">複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、これらのスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="3b291-106">If you want to create components that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in these Script component samples as the starting point for custom data flow components.</span></span> <span data-ttu-id="3b291-107">詳細については、「 [カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b291-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b291-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3b291-108">In This Section</span></span>  
 [<span data-ttu-id="3b291-109">スクリプト コンポーネントに対するエラー出力のシミュレート</span><span class="sxs-lookup"><span data-stu-id="3b291-109">Simulating an Error Output for the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 <span data-ttu-id="3b291-110">スクリプト コンポーネントは標準エラー出力をサポートしませんが、若干の追加構成とコーディングを行うだけで標準エラー出力をシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="3b291-110">The Script component does not support a standard error output, but you can simulate a standard error output with very little additional configuration and coding.</span></span>  
  
 [<span data-ttu-id="3b291-111">スクリプト コンポーネントによるエラー出力の強化</span><span class="sxs-lookup"><span data-stu-id="3b291-111">Enhancing an Error Output with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)  
 <span data-ttu-id="3b291-112">スクリプト コンポーネントを使用して標準エラー出力に追加情報を追加する方法を、説明および例示します。</span><span class="sxs-lookup"><span data-stu-id="3b291-112">Explains and demonstrates how to add additional information to a standard error output by using the Script component.</span></span>  
  
 [<span data-ttu-id="3b291-113">スクリプト コンポーネントによる ODBC 変換先の作成</span><span class="sxs-lookup"><span data-stu-id="3b291-113">Creating an ODBC Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/creating-an-odbc-destination-with-the-script-component.md)  
 <span data-ttu-id="3b291-114">スクリプト コンポーネントを使用して ODBC データ フローの変換先を作成する方法を、説明および例示します。</span><span class="sxs-lookup"><span data-stu-id="3b291-114">Explains and demonstrates how to create an ODBC data flow destination by using the Script component.</span></span>  
  
 [<span data-ttu-id="3b291-115">スクリプト コンポーネントを使用した標準以外のテキスト ファイル形式の解析</span><span class="sxs-lookup"><span data-stu-id="3b291-115">Parsing Non-Standard Text File Formats with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/parsing-non-standard-text-file-formats-with-the-script-component.md)  
 <span data-ttu-id="3b291-116">2 つの標準以外のテキスト ファイル形式を変換先のテーブルに解析する方法を、説明および例示します。</span><span class="sxs-lookup"><span data-stu-id="3b291-116">Explains and demonstrates how to parse two different non-standard text file formats into destination tables.</span></span>  
  
<span data-ttu-id="3b291-117">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="3b291-117">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3b291-118">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b291-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3b291-119">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="3b291-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3b291-120">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="3b291-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
