---
title: マルチキャスト変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b5c0a38c966c89f426a213f302b45c390b77cfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743426"
---
# <a name="multicast-transformation"></a><span data-ttu-id="44001-102">マルチキャスト変換</span><span class="sxs-lookup"><span data-stu-id="44001-102">Multicast Transformation</span></span>
  <span data-ttu-id="44001-103">マルチキャスト変換は、入力を 1 つ以上の出力に配信します。</span><span class="sxs-lookup"><span data-stu-id="44001-103">The Multicast transformation distributes its input to one or more outputs.</span></span> <span data-ttu-id="44001-104">この変換は条件分割変換と似ています。</span><span class="sxs-lookup"><span data-stu-id="44001-104">This transformation is similar to the Conditional Split transformation.</span></span> <span data-ttu-id="44001-105">いずれの変換も、1 つの入力を複数の出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="44001-105">Both transformations direct an input to multiple outputs.</span></span> <span data-ttu-id="44001-106">この 2 つの変換の違いは、マルチキャスト変換は各行を各出力に送信するのに対し、条件分割変換は 1 行を単一の出力に送信する点です。</span><span class="sxs-lookup"><span data-stu-id="44001-106">The difference between the two is that the Multicast transformation directs every row to every output, and the Conditional Split directs a row to a single output.</span></span> <span data-ttu-id="44001-107">詳細については、「 [Conditional Split Transformation](conditional-split-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44001-107">For more information, see [Conditional Split Transformation](conditional-split-transformation.md).</span></span>  
  
 <span data-ttu-id="44001-108">マルチキャスト変換を構成するには、出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="44001-108">You configure the Multicast transformation by adding outputs.</span></span>  
  
 <span data-ttu-id="44001-109">マルチキャスト変換を使用すると、パッケージはデータの論理コピーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="44001-109">Using the Multicast transformation, a package can create logical copies of data.</span></span> <span data-ttu-id="44001-110">この機能は、パッケージで複数の変換セットを同一のデータに適用する必要がある場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="44001-110">This capability is useful when the package needs to apply multiple sets of transformations to the same data.</span></span> <span data-ttu-id="44001-111">たとえば、データの 1 つのコピーを集計して要約情報のみを変換先で読み込み、そのデータのもう 1 つのコピーを参照値と派生列で拡張し、その後変換先で読み込みます。</span><span class="sxs-lookup"><span data-stu-id="44001-111">For example, one copy of the data is aggregated and only the summary information is loaded into its destination, while another copy of the data is extended with lookup values and derived columns before it is loaded into its destination.</span></span>  
  
 <span data-ttu-id="44001-112">この変換は 1 つの入力と複数の出力をとります。</span><span class="sxs-lookup"><span data-stu-id="44001-112">This transformation has one input and multiple outputs.</span></span> <span data-ttu-id="44001-113">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="44001-113">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-multicast-transformation"></a><span data-ttu-id="44001-114">マルチキャスト変換の構成</span><span class="sxs-lookup"><span data-stu-id="44001-114">Configuration of the Multicast Transformation</span></span>  
 <span data-ttu-id="44001-115">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="44001-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="44001-116">**[マルチキャスト変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [マルチキャスト変換エディター](../../multicast-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44001-116">For information about the properties that you can set in the **Multicast Transformation Editor** dialog box, see [Multicast Transformation Editor](../../multicast-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="44001-117">プログラムによって設定できるプロパティの詳細については、「 [共通プロパティ](../../common-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44001-117">For information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="44001-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="44001-118">Related Tasks</span></span>  
 <span data-ttu-id="44001-119">このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44001-119">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44001-120">参照</span><span class="sxs-lookup"><span data-stu-id="44001-120">See Also</span></span>  
 <span data-ttu-id="44001-121">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="44001-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="44001-122">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="44001-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
