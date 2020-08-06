---
title: 比率サンプリング変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e5fe41ecf4a2ca0f9d20eec2c8e10af8ed4cd47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743422"
---
# <a name="percentage-sampling-transformation"></a><span data-ttu-id="389db-102">比率サンプリング変換</span><span class="sxs-lookup"><span data-stu-id="389db-102">Percentage Sampling Transformation</span></span>
  <span data-ttu-id="389db-103">比率サンプリング変換は、変換入力行の比率を選択することにより、サンプル データセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="389db-103">The Percentage Sampling transformation creates a sample data set by selecting a percentage of the transformation input rows.</span></span> <span data-ttu-id="389db-104">サンプル データセットとは、変換入力からランダムに行を選択し、その結果、入力のサンプルとなるデータセットのことです。</span><span class="sxs-lookup"><span data-stu-id="389db-104">The sample data set is a random selection of rows from the transformation input, to make the resultant sample representative of the input.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="389db-105">比率サンプリング変換は、指定した比率に加え、サンプル出力に行を含めるかどうかを決定するアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="389db-105">In addition to the specified percentage, the Percentage Sampling transformation uses an algorithm to determine whether a row should be included in the sample output.</span></span> <span data-ttu-id="389db-106">したがって、サンプル出力の行数は、指定した比率を正確に反映しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="389db-106">This means that the number of rows in the sample output may not exactly reflect the specified percentage.</span></span> <span data-ttu-id="389db-107">たとえば、25,000 行の入力データセットに対して 10% を指定した場合、2,500 行のサンプルが生成されず、サンプルの行がこの数を多少前後することがあります。</span><span class="sxs-lookup"><span data-stu-id="389db-107">For example, specifying 10 percent for an input data set that has 25,000 rows may not generate a sample with 2,500 rows; the sample may have a few more or a few less rows.</span></span>  
  
 <span data-ttu-id="389db-108">比率サンプリング変換は、特にデータ マイニングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="389db-108">The Percentage Sampling transformation is especially useful for data mining.</span></span> <span data-ttu-id="389db-109">この変換を使用すると、データセットをランダムに 2 つのデータセットに分割できます。たとえば、1 つをデータ マイニング モデルの学習用に、もう 1 つはそのモデルのテスト用に分割します。</span><span class="sxs-lookup"><span data-stu-id="389db-109">By using this transformation, you can randomly divide a data set into two data sets: one for training the data mining model, and one for testing the model.</span></span>  
  
 <span data-ttu-id="389db-110">また、比率サンプリング変換は、パッケージ開発用のサンプル データセットを作成するうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="389db-110">The Percentage Sampling transformation is also useful for creating sample data sets for package development.</span></span> <span data-ttu-id="389db-111">比率サンプリング変換をデータ フローに適用すると、データの特性を保持したまま、データセットのサイズを一様に縮小できます。</span><span class="sxs-lookup"><span data-stu-id="389db-111">By applying the Percentage Sampling transformation to a data flow, you can uniformly reduce the size of the data set while preserving its data characteristics.</span></span> <span data-ttu-id="389db-112">したがって、テスト パッケージは、サイズは小さいが代表的なデータセットを使用するため、実行速度は速くなります。</span><span class="sxs-lookup"><span data-stu-id="389db-112">The test package can then run more quickly because it uses a small, but representative, data set.</span></span>  
  
## <a name="configuration-the-percentage-sampling-transformation"></a><span data-ttu-id="389db-113">比率サンプリング変換の構成</span><span class="sxs-lookup"><span data-stu-id="389db-113">Configuration the Percentage Sampling Transformation</span></span>  
 <span data-ttu-id="389db-114">サンプリング シードを指定して、変換が行の選択に使用する乱数ジェネレーターの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="389db-114">You can specify a sampling seed to modify the behavior of the random number generator that the transformation uses to select rows.</span></span> <span data-ttu-id="389db-115">同じサンプリング シードが使用される場合、この変換は、常に同じサンプル出力を作成します。</span><span class="sxs-lookup"><span data-stu-id="389db-115">If the same sampling seed is used, the transformation always creates the same sample output.</span></span> <span data-ttu-id="389db-116">シードを指定しない場合、この変換はオペレーティング システムのティック数を使用して乱数を作成します。</span><span class="sxs-lookup"><span data-stu-id="389db-116">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="389db-117">したがって、パッケージの開発やテスト中に変換結果を確認する際は標準シードを使用するように選択し、パッケージの稼働時にはランダム シードを使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="389db-117">Therefore, you might choose to use a standard seed when you want to verify the transformation results during the development and testing of a package, and then change to use a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="389db-118">この変換は、行サンプリング変換と同様です。ただし、行サンプリング変換は、指定する入力行数を選択してサンプル データセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="389db-118">This transformation is similar to the Row Sampling transformation, which creates a sample data set by selecting a specified number of the input rows.</span></span> <span data-ttu-id="389db-119">詳細については、「 [Row Sampling Transformation](row-sampling-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="389db-119">For more information, see [Row Sampling Transformation](row-sampling-transformation.md).</span></span>  
  
 <span data-ttu-id="389db-120">比率サンプリング変換には、`SamplingValue` カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="389db-120">The Percentage Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="389db-121">このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="389db-121">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="389db-122">詳細については、「[Integration Services &#40;SSIS&#41; の式](../../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="389db-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="389db-123">この変換は、1 つの入力と 2 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="389db-123">The transformation has one input and two outputs.</span></span> <span data-ttu-id="389db-124">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="389db-124">It does not support an error output.</span></span>  
  
 <span data-ttu-id="389db-125">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="389db-125">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="389db-126">**[比率サンプリング変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [比率サンプリング変換エディター](../../percentage-sampling-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="389db-126">For more information about the properties that you can set in the **Percentage Sampling Transformation Editor** dialog box, see [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="389db-127">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="389db-127">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="389db-128">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="389db-128">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="389db-129">Common Properties</span><span class="sxs-lookup"><span data-stu-id="389db-129">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="389db-130">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="389db-130">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="389db-131">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="389db-131">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
