---
title: データ マイニング クエリ変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 278fdc3b1abd38b63f01e967e28d11983a09e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632028"
---
# <a name="data-mining-query-transformation"></a><span data-ttu-id="595be-102">データ マイニング クエリ変換</span><span class="sxs-lookup"><span data-stu-id="595be-102">Data Mining Query Transformation</span></span>
  <span data-ttu-id="595be-103">データ マイニング クエリ変換は、データ マイニング モデルに対して予測クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="595be-103">The Data Mining Query transformation performs prediction queries against data mining models.</span></span> <span data-ttu-id="595be-104">この変換には、データ マイニング拡張機能 (DMX) クエリを作成するためのクエリ ビルダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="595be-104">This transformation contains a query builder for creating Data Mining Extensions (DMX) queries.</span></span> <span data-ttu-id="595be-105">このクエリ ビルダーを使用すると、DMX 言語を使用して、既存のマイニング モデルに対して変換入力データを評価する、カスタム ステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="595be-105">The query builder lets you create custom statements for evaluating the transformation input data against an existing mining model using the DMX language.</span></span> <span data-ttu-id="595be-106">詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](/sql/dmx/data-mining-extensions-dmx-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="595be-106">For more information, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
 <span data-ttu-id="595be-107">同じデータ マイニング構造で複数のモデルが構築されている場合、1 回の変換で複数の予測クエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="595be-107">One transformation can execute multiple prediction queries if the models are built on the same data mining structure.</span></span> <span data-ttu-id="595be-108">詳細については、「[データマイニングクエリインターフェイス](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="595be-108">For more information, see [Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span></span>  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a><span data-ttu-id="595be-109">データ マイニング クエリ変換の構成</span><span class="sxs-lookup"><span data-stu-id="595be-109">Configuration of the Data Mining Query Transformation</span></span>  
 <span data-ttu-id="595be-110">データ マイニング クエリ変換は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 接続マネージャーを使用して [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] プロジェクト、またはマイニング構造とマイニング モデルを含む [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="595be-110">The Data Mining Query transformation uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models.</span></span> <span data-ttu-id="595be-111">詳しくは、「 [Analysis Services 接続マネージャー](../../connection-manager/analysis-services-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="595be-111">For more information, see [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="595be-112">この変換は 1 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="595be-112">This transformation has one input and one output.</span></span> <span data-ttu-id="595be-113">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="595be-113">It does not support an error output.</span></span>  
  
 <span data-ttu-id="595be-114">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="595be-114">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="595be-115">**[データ マイニング クエリ変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="595be-115">For more information about the properties that you can set in the **Data Mining Query Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="595be-116">[[データ マイニング クエリ変換エディター] &#40;[マイニング モデル] タブ&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)</span><span class="sxs-lookup"><span data-stu-id="595be-116">[Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)</span></span>  
  
-   <span data-ttu-id="595be-117">[[データ マイニング クエリ変換エディター] &#40;[マイニング モデル] タブ&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)</span><span class="sxs-lookup"><span data-stu-id="595be-117">[Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)</span></span>  
  
 <span data-ttu-id="595be-118">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="595be-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="595be-119">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="595be-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="595be-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="595be-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="595be-121">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="595be-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="595be-122">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="595be-122">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
