---
title: ピボット解除変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottrans.f1
helpviewer_keywords:
- Unpivot transformation
- more normalized data set [Integration Services]
- normalized data [Integration Services]
- datasets [Integration Services], normalized data
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e605dc4827a885b5dc65fbb680cce8a434b89fd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644044"
---
# <a name="unpivot-transformation"></a><span data-ttu-id="dbd62-102">ピボット解除変換</span><span class="sxs-lookup"><span data-stu-id="dbd62-102">Unpivot Transformation</span></span>
  <span data-ttu-id="dbd62-103">ピボット解除変換は、単一のレコード内にある複数の列の値を、単一の列内で同じ値を持つ複数のレコードに展開することにより、正規化されていないデータセットを正規化されたバージョンに変換します。</span><span class="sxs-lookup"><span data-stu-id="dbd62-103">The Unpivot transformation makes an unnormalized dataset into a more normalized version by expanding values from multiple columns in a single record into multiple records with the same values in a single column.</span></span> <span data-ttu-id="dbd62-104">たとえば、顧客名を一覧表示するデータセットに、顧客ごとに 1 つの行があり、製品と購入した数量がその行の列に表示されているとします。</span><span class="sxs-lookup"><span data-stu-id="dbd62-104">For example, a dataset that lists customer names has one row for each customer, with the products and the quantity purchased shown in columns in the row.</span></span> <span data-ttu-id="dbd62-105">ピボット解除変換がこのデータセットを正規化すると、データセットには、顧客が購入した各製品に対して異なる行が含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="dbd62-105">After the Unpivot transformation normalizes the data set, the data set contains a different row for each product that the customer purchased.</span></span>  
  
 <span data-ttu-id="dbd62-106">次の図は、データが Product 列でピボット解除される前のデータセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="dbd62-106">The following diagram shows a data set before the data is unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="dbd62-107">![ピボット解除後のデータセット](../../media/mw-dts-18.gif "ピボット解除後のデータセット")</span><span class="sxs-lookup"><span data-stu-id="dbd62-107">![Dataset after it is unpivoted](../../media/mw-dts-18.gif "Dataset after it is unpivoted")</span></span>  
  
 <span data-ttu-id="dbd62-108">次の図は、データが Product 列でピボット解除された後のデータセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="dbd62-108">The following diagram shows a data set after it has been unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="dbd62-109">![ピボット解除前のデータセット](../../media/mw-dts-17.gif "ピボット解除前のデータセット")</span><span class="sxs-lookup"><span data-stu-id="dbd62-109">![Dataset before it is unpivoted](../../media/mw-dts-17.gif "Dataset before it is unpivoted")</span></span>  
  
 <span data-ttu-id="dbd62-110">状況によっては、ピボット解除された結果には予期しない値を持つ行が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dbd62-110">Under some circumstances, the unpivot results may contain rows with unexpected values.</span></span> <span data-ttu-id="dbd62-111">たとえば、図に示したサンプル データのピボット解除では、Fred のすべての Qty 列が NULL 値である場合、出力に含まれる Fred の行は 5 つではなく 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="dbd62-111">For example, if the sample data to unpivot shown in the diagram had null values in all the Qty columns for Fred, then the output would include only one row for Fred, not five.</span></span> <span data-ttu-id="dbd62-112">Qty 列には、列データ型に応じて、NULL または 0 のいずれかが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dbd62-112">The Qty column would contain either null or zero, depending on the column data type.</span></span>  
  
## <a name="configuration-of-the-unpivot-transformation"></a><span data-ttu-id="dbd62-113">ピボット解除変換の構成</span><span class="sxs-lookup"><span data-stu-id="dbd62-113">Configuration of the Unpivot Transformation</span></span>  
 <span data-ttu-id="dbd62-114">ピボット解除変換には、`PivotKeyValue` カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="dbd62-114">The Unpivot transformation includes the `PivotKeyValue` custom property.</span></span> <span data-ttu-id="dbd62-115">このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="dbd62-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="dbd62-116">詳細については、「[Integration Services &#40;SSIS&#41; の式](../../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbd62-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="dbd62-117">この変換は 1 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="dbd62-117">This transformation has one input and one output.</span></span> <span data-ttu-id="dbd62-118">エラー出力はありません。</span><span class="sxs-lookup"><span data-stu-id="dbd62-118">It has no error output.</span></span>  
  
 <span data-ttu-id="dbd62-119">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="dbd62-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="dbd62-120">**[ピボット解除変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbd62-120">For more information about the properties that you can set in the **Unpivot Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="dbd62-121">[[ピボット解除変換エディター]](../../unpivot-transformation-editor.md)</span><span class="sxs-lookup"><span data-stu-id="dbd62-121">[Unpivot Transformation Editor](../../unpivot-transformation-editor.md)</span></span>  
  
 <span data-ttu-id="dbd62-122">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbd62-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="dbd62-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="dbd62-123">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="dbd62-124">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="dbd62-124">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="dbd62-125">データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbd62-125">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
