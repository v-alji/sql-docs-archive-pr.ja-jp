---
title: 複数の入力を持つデータ フロー コンポーネントの開発 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb56878c1b1b68dfdc4de19cb2b811de494c761b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736606"
---
# <a name="developing-data-flow-components-with-multiple-inputs"></a><span data-ttu-id="8846f-102">複数の入力を持つデータ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="8846f-102">Developing Data Flow Components with Multiple Inputs</span></span>
  <span data-ttu-id="8846f-103">複数の入力によってデータが不均一なレートで生成される場合に、複数の入力があるデータ フローコンポーネントによって過度にメモリが消費されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8846f-103">A data flow component with multiple inputs may consume excessive memory if its multiple inputs produce data at uneven rates.</span></span> <span data-ttu-id="8846f-104">複数の入力をサポートするカスタム データ フロー コンポーネントを開発するときは、Microsoft.SqlServer.Dts.Pipeline 名前空間の次のメンバーを使用してこのメモリの負荷を管理できます。</span><span class="sxs-lookup"><span data-stu-id="8846f-104">When you develop a custom data flow component that supports two or more inputs, you can manage this memory pressure by using the following members in the Microsoft.SqlServer.Dts.Pipeline namespace:</span></span>  
  
-   <span data-ttu-id="8846f-105"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティ。</span><span class="sxs-lookup"><span data-stu-id="8846f-105">The <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> class.</span></span> <span data-ttu-id="8846f-106">カスタム データ フロー コンポーネントに必要なコードを実装して不均一なレートのデータ フローを管理する場合は、このプロパティの値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8846f-106">Set the value of this property to `true` if you want to implement the code that is necessary for your custom data flow component to manage data flowing at uneven rates.</span></span>  
  
-   <span data-ttu-id="8846f-107"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッド。</span><span class="sxs-lookup"><span data-stu-id="8846f-107">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span> <span data-ttu-id="8846f-108"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> プロパティを `true` に設定する場合は、このメソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8846f-108">You must provide an implementation of this method if you set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true`.</span></span> <span data-ttu-id="8846f-109">実装しない場合、データ フロー エンジンは実行時に例外を発生させます。</span><span class="sxs-lookup"><span data-stu-id="8846f-109">If you do not provide an implementation, the data flow engine raises an exception at run time.</span></span>  
  
-   <span data-ttu-id="8846f-110"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッド。</span><span class="sxs-lookup"><span data-stu-id="8846f-110">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span> <span data-ttu-id="8846f-111"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> プロパティを `true` に設定し、カスタム コンポーネントが複数の入力をサポートしている場合は、このメソッドも実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8846f-111">You must also provide an implementation of this method if you set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` and your custom component supports more than two inputs.</span></span> <span data-ttu-id="8846f-112">実装しない場合、ユーザーが複数の入力をアタッチすると、データ フロー エンジンは実行時に例外を発生させます。</span><span class="sxs-lookup"><span data-stu-id="8846f-112">If you do not provide an implementation, the data flow engine raises an exception at run time if the user attaches more than two inputs.</span></span>  
  
 <span data-ttu-id="8846f-113">また、これらのメンバーを使用すると、マージ変換およびマージ結合変換用にマイクロソフトが開発したような、メモリ負荷のためのソリューションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="8846f-113">Together, these members enable you to develop a solution for memory pressure that is similar to the solution that Microsoft developed for the Merge and Merge Join transformations.</span></span>  
  
## <a name="setting-the-supportsbackpressure-property"></a><span data-ttu-id="8846f-114">SupportsBackPressure プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="8846f-114">Setting the SupportsBackPressure Property</span></span>  
 <span data-ttu-id="8846f-115">複数の入力をサポートするカスタム データ フロー コンポーネントでより効率的なメモリ管理を実装するための最初の手順は、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> で <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> プロパティの値を `true` に設定することです。</span><span class="sxs-lookup"><span data-stu-id="8846f-115">The first step in implementing better memory management for a custom data flow component that supports multiple inputs is to set the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="8846f-116"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> の値が `true` の場合、データ フロー エンジンは <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドを呼び出し、複数の入力があるときは、実行時に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドも呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8846f-116">When the value of <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> is `true`, the data flow engine calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method and, when there are more than two inputs, also calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method at run time.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8846f-117">例</span><span class="sxs-lookup"><span data-stu-id="8846f-117">Example</span></span>  
 <span data-ttu-id="8846f-118">次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> を実装して、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> の値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8846f-118">In the following example, the implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> sets the value of <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> to `true`.</span></span>  
  
```csharp  
[DtsPipelineComponent(ComponentType = ComponentType.Transform,  
        DisplayName = "Shuffler",  
        Description = "Shuffle the rows from input.",  
        SupportsBackPressure = true,  
        LocalizationType = typeof(Localized),  
        IconResource = "Microsoft.Samples.SqlServer.Dts.MIBPComponent.ico")  
]  
public class Shuffler : Microsoft.SqlServer.Dts.Pipeline.PipelineComponent  
        {  
          ...  
        }  
```  
  
## <a name="implementing-the-isinputready-method"></a><span data-ttu-id="8846f-119">IsInputReady メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="8846f-119">Implementing the IsInputReady Method</span></span>  
 <span data-ttu-id="8846f-120"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> オブジェクトの <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティの値を `true` に設定する場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドも実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8846f-120">When you set the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> object, you must also provide an implementation for the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8846f-121"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドの実装では、基本クラスで実装を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8846f-121">Your implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method should not call the implementations in the base class.</span></span> <span data-ttu-id="8846f-122">基本クラスでのこのメソッドの既定の実装では、`NotImplementedException` を発生させるだけです。</span><span class="sxs-lookup"><span data-stu-id="8846f-122">The default implementation of this method in the base class simply raises a `NotImplementedException`.</span></span>  
  
 <span data-ttu-id="8846f-123">このメソッドを実装し、コンポーネントの各入力に対して Boolean 型の *canProcess* 配列で要素の状態を設定します</span><span class="sxs-lookup"><span data-stu-id="8846f-123">When you implement this method, you set the status of an element in the Boolean *canProcess* array for each of the component's inputs.</span></span> <span data-ttu-id="8846f-124">(入力は、 *inputIDs*配列内の ID 値によって識別されます)。*Canprocess*配列の要素の値を入力用にに設定すると、 `true` データフローエンジンは、コンポーネントのメソッドを呼び出し、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 指定された入力に対してより多くのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="8846f-124">(The inputs are identified by their ID values in the *inputIDs* array.) When you set the value of an element in the *canProcess* array to `true` for an input, the data flow engine calls the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method and provides more data for the specified input.</span></span>  
  
 <span data-ttu-id="8846f-125">より多くのアップストリームデータを使用できますが、少なくとも1つの入力の*Canprocess*配列要素の値は、常にであるか、処理が停止する必要があり `true` ます。</span><span class="sxs-lookup"><span data-stu-id="8846f-125">While more upstream data is available, the value of the *canProcess* array element for at least one input must always be `true`, or processing stops.</span></span>  
  
 <span data-ttu-id="8846f-126">データ フロー エンジンは、データの各バッファーを送信する前に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドを呼び出して、追加データの受信を待機している入力を判断します。</span><span class="sxs-lookup"><span data-stu-id="8846f-126">The data flow engine calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method before sending each buffer of data to determine which inputs are waiting to receive more data.</span></span> <span data-ttu-id="8846f-127">入力がブロックされていることが戻り値によって示された場合、データ フロー エンジンは、バッファーをコンポーネントに送信する代わりに、入力データの追加バッファーを一時的にキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="8846f-127">When the return value indicates that an input is blocked, the data flow engine temporarily caches additional buffers of data for that input instead of sending them to the component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8846f-128">独自に記述するコード内で、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="8846f-128">You do not call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> methods in your own code.</span></span> <span data-ttu-id="8846f-129">データ フロー エンジンはコンポーネントを実行するとき、これらのメソッドやオーバーライドする `PipelineComponent` クラスのその他のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8846f-129">The data flow engine calls these methods, and the other methods of the `PipelineComponent` class that you override, when the data flow engine runs your component.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8846f-130">例</span><span class="sxs-lookup"><span data-stu-id="8846f-130">Example</span></span>  
 <span data-ttu-id="8846f-131">次の例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> の実装により、以下の条件に該当する場合に入力が追加のデータを待っていることを示します。</span><span class="sxs-lookup"><span data-stu-id="8846f-131">In the following example, the implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that an input is waiting to receive more data when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="8846f-132">入力に対する追加の上流データがある (`!inputEOR`)。</span><span class="sxs-lookup"><span data-stu-id="8846f-132">More upstream data is available for the input (`!inputEOR`).</span></span>  
  
-   <span data-ttu-id="8846f-133">コンポーネントが、受信済みのバッファーで入力に対して処理できるデータを現在持っていない (`inputBuffers[inputIndex].CurrentRow() == null`)。</span><span class="sxs-lookup"><span data-stu-id="8846f-133">The component does not currently have data available to process for the input in the buffers that the component has already received (`inputBuffers[inputIndex].CurrentRow() == null`).</span></span>  
  
 <span data-ttu-id="8846f-134">入力がさらに多くのデータの受信を待機している場合、データフローコンポーネントは、 `true` その入力に対応する*canprocess*配列の要素の値をに設定することによってこれを示します。</span><span class="sxs-lookup"><span data-stu-id="8846f-134">If an input is waiting to receive more data, the data flow component indicates this by setting to `true` the value of the element in the *canProcess* array that corresponds to that input.</span></span>  
  
 <span data-ttu-id="8846f-135">逆に、コンポーネントが入力に対して処理できるデータを持っている場合、この例では入力の処理を中断します。</span><span class="sxs-lookup"><span data-stu-id="8846f-135">Conversely, when the component still has data available to process for the input, the example suspends the processing of the input.</span></span> <span data-ttu-id="8846f-136">この例では、この `false` 入力に対応する*canprocess*配列の要素の値をに設定します。</span><span class="sxs-lookup"><span data-stu-id="8846f-136">The example does this by setting to `false` the value of the element in the *canProcess* array that corresponds to that input.</span></span>  
  
```csharp  
public override void IsInputReady(int[] inputIDs, ref bool[] canProcess)  
{  
    for (int i = 0; i < inputIDs.Length; i++)  
    {  
        int inputIndex = ComponentMetaData.InputCollection.GetObjectIndexByID(inputIDs[i]);  
  
        canProcess[i] = (inputBuffers[inputIndex].CurrentRow() == null)  
            && !inputEOR[inputIndex];  
    }  
}  
```  
  
 <span data-ttu-id="8846f-137">前の例は、Boolean 型の `inputEOR` 配列を使用して、各入力で追加のアップストリーム データを使用できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8846f-137">The preceding example uses the Boolean `inputEOR` array to indicate whether more upstream data is available for each input.</span></span> <span data-ttu-id="8846f-138">配列名の `EOR` は "行セットの末尾 (end of rowset)" を示し、データ フロー バッファーの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティを参照します。</span><span class="sxs-lookup"><span data-stu-id="8846f-138">`EOR` in the name of the array represents "end of rowset" and refers to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property of data flow buffers.</span></span> <span data-ttu-id="8846f-139">ここに含まれていない例の部分では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドを使用して、受信するデータの各バッファーに対して <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="8846f-139">In a portion of the example that is not included here, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method checks the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property for each buffer of data that it receives.</span></span> <span data-ttu-id="8846f-140">値 `true` によって、入力でこれ以上のアップストリーム データを利用できないことが示された場合、その入力の `inputEOR` 配列要素の値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8846f-140">When a value of `true` indicates that there is no more upstream data available for an input, the example sets the value of the `inputEOR` array element for that input to `true`.</span></span> <span data-ttu-id="8846f-141">このメソッドの例では、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 配列要素の値によって、 *canProcess* `false` `inputEOR` 入力に使用できるアップストリームデータがないことが示された場合に、canprocess 配列内の対応する要素の値をに設定します。</span><span class="sxs-lookup"><span data-stu-id="8846f-141">This example of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method sets the value of the corresponding element in the *canProcess* array to `false` for an input when the value of the `inputEOR` array element indicates that there is no more upstream data available for the input.</span></span>  
  
## <a name="implementing-the-getdependentinputs-method"></a><span data-ttu-id="8846f-142">GetDependentInputs メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="8846f-142">Implementing the GetDependentInputs Method</span></span>  
 <span data-ttu-id="8846f-143">カスタム データ フロー コンポーネントが複数の入力をサポートしている場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドも実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8846f-143">When your custom data flow component supports more than two inputs, you must also provide an implementation for the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8846f-144"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドの実装では、基本クラスで実装を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8846f-144">Your implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method should not call the implementations in the base class.</span></span> <span data-ttu-id="8846f-145">基本クラスでのこのメソッドの既定の実装では、`NotImplementedException` を発生させるだけです。</span><span class="sxs-lookup"><span data-stu-id="8846f-145">The default implementation of this method in the base class simply raises a `NotImplementedException`.</span></span>  
  
 <span data-ttu-id="8846f-146">データ フロー エンジンは、ユーザーが 3 つ以上の入力をコンポーネントにアタッチする場合に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドを呼び出すだけです。</span><span class="sxs-lookup"><span data-stu-id="8846f-146">The data flow engine only calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method when the user attaches more than two inputs to the component.</span></span> <span data-ttu-id="8846f-147">コンポーネントに入力が2つしかないときに、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドが1つの入力がブロックされていることを示している場合 (*canprocess*  =  `false` )、データフローエンジンは、他の入力がさらに多くのデータの受信を待機していることを認識します。</span><span class="sxs-lookup"><span data-stu-id="8846f-147">When a component has only two inputs, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that one input is blocked (*canProcess* = `false`), the data flow engine knows that the other input is waiting to receive more data.</span></span> <span data-ttu-id="8846f-148">ただし、入力が 2 つより多い場合に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドによって 1 つの入力がブロックされていることが示されたときは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> の追加のコードはどの入力が追加データの受信を待機しているかを示します。</span><span class="sxs-lookup"><span data-stu-id="8846f-148">However, when there are more than two inputs, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that one input is blocked, the additional code in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> identifies which inputs are waiting to receive more data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8846f-149">独自に記述するコード内で、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="8846f-149">You do not call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> methods in your own code.</span></span> <span data-ttu-id="8846f-150">データ フロー エンジンはコンポーネントを実行するとき、これらのメソッドやオーバーライドする `PipelineComponent` クラスのその他のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8846f-150">The data flow engine calls these methods, and the other methods of the `PipelineComponent` class that you override, when the data flow engine runs your component.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8846f-151">例</span><span class="sxs-lookup"><span data-stu-id="8846f-151">Example</span></span>  
 <span data-ttu-id="8846f-152">ある 1 つの入力がブロックされている場合、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドの次の実装は、追加データの受信を待機している入力のコレクションを返し、はじめの 1 つの入力はブロッキング状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="8846f-152">For a specific input that is blocked, the following implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method returns a collection of the inputs that are waiting to receive more data, and are therefore blocking the specified input.</span></span> <span data-ttu-id="8846f-153">コンポーネントは、既に受信したバッファー内に、ブロックされている入力以外の入力が処理できるデータが現在ないことをチェックして、ブロックしている入力を特定します (`inputBuffers[i].CurrentRow() == null`)。</span><span class="sxs-lookup"><span data-stu-id="8846f-153">The component identifies the blocking inputs by checking for inputs other than the blocked input that do not currently have data available to process in the buffers that the component has already received (`inputBuffers[i].CurrentRow() == null`).</span></span> <span data-ttu-id="8846f-154">次に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは、ブロックしている入力のコレクションを入力 ID のコレクションとして返します。</span><span class="sxs-lookup"><span data-stu-id="8846f-154">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method then returns the collection of blocking inputs as a collection of input IDs.</span></span>  
  
```csharp  
public override Collection<int> GetDependentInputs(int blockedInputID)  
{  
    Collection<int> currentDependencies = new Collection<int>();  
    for (int i = 0; i < ComponentMetaData.InputCollection.Count; i++)  
    {  
        if (ComponentMetaData.InputCollection[i].ID != blockedInputID  
            && inputBuffers[i].CurrentRow() == null)  
        {  
            currentDependencies.Add(ComponentMetaData.InputCollection[i].ID);  
        }  
    }  
  
    return currentDependencies;  
}  
```  
  
  
