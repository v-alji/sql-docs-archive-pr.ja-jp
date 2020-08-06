---
title: 行サンプリング変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowsamplingtrans.f1
helpviewer_keywords:
- sampling seeds [Integration Services]
- random seeds
- random sampling
- sample data sets [Integration Services]
- Row Sampling transformation
- packages [Integration Services], samples
- datasets [Integration Services], sample
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c56f07d9fafa03752ef8c6572a13c6ad7c02a8c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743417"
---
# <a name="row-sampling-transformation"></a><span data-ttu-id="3781c-102">行サンプリング変換</span><span class="sxs-lookup"><span data-stu-id="3781c-102">Row Sampling Transformation</span></span>
  <span data-ttu-id="3781c-103">行サンプリング変換を使用すると、入力データセットからランダムに選択されたサブセットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="3781c-103">The Row Sampling transformation is used to obtain a randomly selected subset of an input dataset.</span></span> <span data-ttu-id="3781c-104">出力サンプルの正確なサイズを指定したり、乱数ジェネレーターのシード値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3781c-104">You can specify the exact size of the output sample, and specify a seed for the random number generator.</span></span>  
  
 <span data-ttu-id="3781c-105">ランダム サンプリング用のアプリケーションには、多くの種類があります。</span><span class="sxs-lookup"><span data-stu-id="3781c-105">There are many applications for random sampling.</span></span> <span data-ttu-id="3781c-106">たとえば、ある会社がくじ引きを行って、ランダムに選択された 50 人の社員を当選者とする場合、社員データベースに対して行サンプリング変換を行い、正確な数の当選者を生成できます。</span><span class="sxs-lookup"><span data-stu-id="3781c-106">For example, a company that wanted to randomly select 50 employees to receive prizes in a lottery could use the Row Sampling transformation on the employee database to generate the exact number of winners.</span></span>  
  
 <span data-ttu-id="3781c-107">また、行サンプリング変換は、パッケージの開発中にサイズは小さいが標本化されたデータセットを作成する際に便利です。</span><span class="sxs-lookup"><span data-stu-id="3781c-107">The Row Sampling transformation is also useful during package development for creating a small but representative dataset.</span></span> <span data-ttu-id="3781c-108">十分に標本化されたデータがあれば、パッケージの実行とデータ変換のテストを行うことができます。この場合、完全なデータセットではなくランダム サンプルを使用するため、より迅速にテストできます。</span><span class="sxs-lookup"><span data-stu-id="3781c-108">You can test package execution and data transformation with richly representative data, but more quickly because a random sample is used instead of the full dataset.</span></span> <span data-ttu-id="3781c-109">テスト パッケージで使用されるサンプル データセットは常に同じサイズであるため、サンプル サブセットを使用することで、パッケージのパフォーマンスの問題をより簡単に判別することもできます。</span><span class="sxs-lookup"><span data-stu-id="3781c-109">Because the sample dataset used by the test package is always the same size, using the sample subset also makes it easier to identify performance problems in the package.</span></span>  
  
 <span data-ttu-id="3781c-110">この変換は、比率サンプリング変換と同様です。ただし、比率サンプリング変換は、入力行数の比率を選択してサンプル データセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="3781c-110">This transformation is similar to the Percentage Sampling transformation, which creates a sample dataset by selecting a percentage of the input rows.</span></span> <span data-ttu-id="3781c-111">「 [比率サンプリング変換](percentage-sampling-transformation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3781c-111">See [Percentage Sampling Transformation](percentage-sampling-transformation.md).</span></span>  
  
## <a name="configuring-the-row-sampling-transformation"></a><span data-ttu-id="3781c-112">行サンプリング変換の構成</span><span class="sxs-lookup"><span data-stu-id="3781c-112">Configuring the Row Sampling Transformation</span></span>  
 <span data-ttu-id="3781c-113">行サンプリング変換は、指定された数の変換入力行を選択してサンプル データセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="3781c-113">The Row Sampling transformation creates a sample dataset by selecting a specified number of the transformation input rows.</span></span> <span data-ttu-id="3781c-114">変換入力からの行の選択はランダムに行われるため、結果サンプルは入力の標本となります。</span><span class="sxs-lookup"><span data-stu-id="3781c-114">Because the selection of rows from the transformation input is random, the resultant sample is representative of the input.</span></span> <span data-ttu-id="3781c-115">乱数ジェネレーターで使用するシード値を指定すると、変換による行の選択方法を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="3781c-115">You can also specify the seed that is used by the random number generator, to affect how the transformation selects rows.</span></span>  
  
 <span data-ttu-id="3781c-116">同じ変換入力で同じランダム シードを使用すると、常に同じサンプル出力が作成されます。</span><span class="sxs-lookup"><span data-stu-id="3781c-116">Using the same random seed on the same transformation input always creates the same sample output.</span></span> <span data-ttu-id="3781c-117">シードを指定しない場合、この変換はオペレーティング システムのティック数を使用して乱数を作成します。</span><span class="sxs-lookup"><span data-stu-id="3781c-117">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="3781c-118">したがって、パッケージの開発およびテスト中に変換結果を確認するためにテスト中は同じシード値を使用し、パッケージの実稼働時にランダム シードへ変更することができます。</span><span class="sxs-lookup"><span data-stu-id="3781c-118">Therefore, you could use the same seed during testing, to verify the transformation results during the development and testing of the package, and then change to a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="3781c-119">行サンプリング変換には、`SamplingValue` カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3781c-119">The Row Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="3781c-120">このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="3781c-120">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="3781c-121">詳細については、「[Integration Services &#40;SSIS&#41; の式](../../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3781c-121">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="3781c-122">この変換は、1 つの入力と 2 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="3781c-122">This transformation has one input and two outputs.</span></span> <span data-ttu-id="3781c-123">エラー出力はありません。</span><span class="sxs-lookup"><span data-stu-id="3781c-123">It has no error output.</span></span>  
  
 <span data-ttu-id="3781c-124">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="3781c-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3781c-125">**[行サンプリング変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「[行サンプリング変換エディター &#40;[サンプリング] ページ&#41;](../../row-sampling-transformation-editor-sampling-page.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3781c-125">For more information about the properties that you can set in the **Row Sampling Transformation Editor** dialog box, see [Row Sampling Transformation Editor &#40;Sampling Page&#41;](../../row-sampling-transformation-editor-sampling-page.md).</span></span>  
  
 <span data-ttu-id="3781c-126">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="3781c-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="3781c-127">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3781c-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3781c-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3781c-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="3781c-129">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="3781c-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="3781c-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3781c-130">Related Tasks</span></span>  
 [<span data-ttu-id="3781c-131">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="3781c-131">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
  
