---
title: 挿入、更新、および削除を処理する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],processing data
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67f016aaf4f7f83c0fa506966c4e78f5b8fadef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632039"
---
# <a name="process-inserts-updates-and-deletes"></a><span data-ttu-id="73d19-102">挿入、更新、および削除を処理する</span><span class="sxs-lookup"><span data-stu-id="73d19-102">Process Inserts, Updates, and Deletes</span></span>
  <span data-ttu-id="73d19-103">変更データの増分読み込みを実行する Integration Services パッケージのデータ フローにおいて、2 番目のタスクは、挿入、更新、および削除を分割することです。</span><span class="sxs-lookup"><span data-stu-id="73d19-103">In the data flow of an Integration Services package that performs an incremental load of change data, the second task is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="73d19-104">その後、適切なコマンドを使用してそれらの変更を変換先に適用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="73d19-104">Then, you can use appropriate commands to apply them to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73d19-105">変更データの増分読み込みを実行するパッケージのデータ フローをデザインするための最初のタスクは、変更データを取得するクエリを実行する変換元コンポーネントを構成することです。</span><span class="sxs-lookup"><span data-stu-id="73d19-105">The first task in designing the data flow of a package that performs an incremental load of change data is to configure the source component that runs the query that retrieves the change data.</span></span> <span data-ttu-id="73d19-106">このコンポーネントに関する詳細については、「 [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73d19-106">For more information about this component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span> <span data-ttu-id="73d19-107">変更データの増分読み込みを実行するパッケージを作成するプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](change-data-capture-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73d19-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="associating-friendly-values-to-separate-inserts-updates-and-deletes"></a><span data-ttu-id="73d19-108">挿入、更新、および削除を分割するための表示値の関連付け</span><span class="sxs-lookup"><span data-stu-id="73d19-108">Associating Friendly Values to Separate Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="73d19-109">変更データを取得するクエリ例では、**cdc.fn_cdc_get_net_changes_<capture_instance>** 関数が **__$operation** という名前のメタデータ列のみを返します。</span><span class="sxs-lookup"><span data-stu-id="73d19-109">In the example query that retrieves change data, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns only the column of metadata named **__$operation**.</span></span> <span data-ttu-id="73d19-110">このメタデータ列には、変更を行った操作を示す序数値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="73d19-110">This metadata column contains an ordinal value that indicates which operation caused the change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73d19-111">**cdc.fn_cdc_get_net_changes_<capture_instance>** 関数を呼び出すクエリの詳細については、「[変更データを取得する関数を作成する](create-the-function-to-retrieve-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73d19-111">For more information about the query that uses calls the **cdc.fn_cdc_get_net_changes_<capture_instance>** function, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
 <span data-ttu-id="73d19-112">序数値と対応する操作を照合するよりも、操作のニーモニックを使用する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="73d19-112">Matching an ordinal value to its corresponding operation is not as easy as using a mnemonic of the operation.</span></span> <span data-ttu-id="73d19-113">たとえば、'D' は削除操作、'I' は挿入操作というように簡単に表すことができます。</span><span class="sxs-lookup"><span data-stu-id="73d19-113">For example, 'D' can easily represent a delete operation and 'I' represent an insert operation.</span></span> <span data-ttu-id="73d19-114">「 [変更データを取得する関数の作成](create-the-function-to-retrieve-the-change-data.md)」で作成したクエリ例では、序数値が新しい列に返される表示文字列値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="73d19-114">The example query that was created in the topic, [Creating the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md), makes this conversion from an ordinal value to a friendly string value that is returned in a new column.</span></span> <span data-ttu-id="73d19-115">次のコードのセグメントは、この変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="73d19-115">The following segment of code shows this conversion:</span></span>  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## <a name="configuring-a-conditional-split-transformation-to-direct-inserts-updates-and-deletes"></a><span data-ttu-id="73d19-116">挿入、更新、および削除を直接行うための条件分割変換の構成</span><span class="sxs-lookup"><span data-stu-id="73d19-116">Configuring a Conditional Split Transformation to Direct Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="73d19-117">変更データの行を 3 つの出力のいずれかに送信するには、条件分割変換が理想的です。</span><span class="sxs-lookup"><span data-stu-id="73d19-117">To direct rows of change data to one of three outputs, the Conditional Split transformation is ideal.</span></span> <span data-ttu-id="73d19-118">この変換では、単に各行の **CDC_OPERATION** 列の値がチェックされ、その変更が挿入、更新、または削除かどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="73d19-118">The transformation just checks the value of the **CDC_OPERATION** column in each row and determines whether that change was an insert, update, or delete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73d19-119">CDC_OPERATION 列には、 **__$operation** 列の数値から取得された表示文字列値が格納されています。</span><span class="sxs-lookup"><span data-stu-id="73d19-119">The CDC_OPERATION column contains a friendly string value derived from the numeric value in the **__$operation** column.</span></span>  
  
#### <a name="to-split-inserts-updates-and-deletes-for-processing-by-using-a-conditional-split-transformation"></a><span data-ttu-id="73d19-120">条件分割変換を使用して処理用に挿入、更新、および削除を分割するには</span><span class="sxs-lookup"><span data-stu-id="73d19-120">To split inserts, updates, and deletes for processing by using a Conditional Split transformation</span></span>  
  
1.  <span data-ttu-id="73d19-121">**[データ フロー]** タブで、条件分割変換を追加します。</span><span class="sxs-lookup"><span data-stu-id="73d19-121">On the **Data Flow** tab, add a Conditional Split transformation.</span></span>  
  
2.  <span data-ttu-id="73d19-122">OLE DB ソースの出力を条件分割変換に接続します。</span><span class="sxs-lookup"><span data-stu-id="73d19-122">Connect the output of the OLE DB source to the Conditional Split transformation.</span></span>  
  
3.  <span data-ttu-id="73d19-123">**[条件分割変換エディター]** の下側のペインで、次の 3 行を入力して 3 つの出力を指定します。</span><span class="sxs-lookup"><span data-stu-id="73d19-123">In the **Conditional Split Transformation Editor**, in the lower pane of the editor, enter the following three lines to designate the three outputs</span></span>  
  
    1.  <span data-ttu-id="73d19-124">条件 `CDC_OPERATION == "I"` を指定する行を入力し、挿入した行を挿入用の出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="73d19-124">Enter a line with the condition `CDC_OPERATION == "I"` to direct inserted rows to the output for inserts.</span></span>  
  
    2.  <span data-ttu-id="73d19-125">条件 `CDC_OPERATION == "U"` を指定する行を入力し、更新した行を更新用の出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="73d19-125">Enter a line with the condition `CDC_OPERATION == "U"` to direct updated rows to the output for updates.</span></span>  
  
    3.  <span data-ttu-id="73d19-126">条件 `CDC_OPERATION == "D"` を指定する行を入力し、削除した行を削除用の出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="73d19-126">Enter a line with the condition `CDC_OPERATION == "D"` to direct deleted rows to the output for deletes.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="73d19-127">次の手順</span><span class="sxs-lookup"><span data-stu-id="73d19-127">Next Step</span></span>  
 <span data-ttu-id="73d19-128">処理用に行を分割したら、次に変更を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="73d19-128">After you split the rows for processing, the next step is to apply the changes to the destination.</span></span>  
  
 <span data-ttu-id="73d19-129">**次のトピック:** [変換先に変更を適用する](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="73d19-129">**Next topic:** [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d19-130">参照</span><span class="sxs-lookup"><span data-stu-id="73d19-130">See Also</span></span>  
 <span data-ttu-id="73d19-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="73d19-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span></span>  
 [<span data-ttu-id="73d19-132">条件分割変換を使用してデータセットを分割する</span><span class="sxs-lookup"><span data-stu-id="73d19-132">Split a Dataset by Using the Conditional Split Transformation</span></span>](../data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
