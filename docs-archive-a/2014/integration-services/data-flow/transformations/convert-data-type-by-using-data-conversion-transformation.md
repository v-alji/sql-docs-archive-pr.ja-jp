---
title: データ変換の変換を使用してデータを別のデータ型に変換する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 878741717c36c18e9a069c62e86be0148272239f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642203"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a><span data-ttu-id="ef66f-102">データ変換の変換を使用してデータを別のデータ型に変換する</span><span class="sxs-lookup"><span data-stu-id="ef66f-102">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>
  <span data-ttu-id="ef66f-103">データ変換の変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef66f-103">To add and configure a Data Conversion transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-convert-data-to-a-different-data-type"></a><span data-ttu-id="ef66f-104">データを別のデータ型に変換するには</span><span class="sxs-lookup"><span data-stu-id="ef66f-104">To convert data to a different data type</span></span>  
  
1.  <span data-ttu-id="ef66f-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="ef66f-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="ef66f-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="ef66f-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="ef66f-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、データ変換の変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ef66f-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Data Conversion transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="ef66f-108">データ変換の変換をデータ フローに連結します。連結するには、変換元または前の変換からデータ変換の変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ef66f-108">Connect the Data Conversion transformation to the data flow by dragging a connector from the source or the previous transformation to the Data Conversion transformation.</span></span>  
  
5.  <span data-ttu-id="ef66f-109">データ変換の変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef66f-109">Double-click the Data Conversion transformation.</span></span>  
  
6.  <span data-ttu-id="ef66f-110">**[データ変換変換エディター]** ダイアログ ボックスの **[使用できる入力列]** テーブルで、データ型を変換する列の隣にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ef66f-110">In the **Data ConversionTransformation Editor** dialog box, in the **Available Input Columns** table, select the check box next to the columns whose data type you want to convert.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef66f-111">1 つの入力列に複数のデータ変換を適用できます。</span><span class="sxs-lookup"><span data-stu-id="ef66f-111">You can apply multiple data conversions to an input column.</span></span>  
  
7.  <span data-ttu-id="ef66f-112">必要に応じ、 **[出力の別名]** 列の既定値を変更します。</span><span class="sxs-lookup"><span data-stu-id="ef66f-112">Optionally, modify the default values in the **Output Alias** column.</span></span>  
  
8.  <span data-ttu-id="ef66f-113">**[データ型]** 一覧で、列の新しいデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef66f-113">In the **Data Type** list, select the new data type for the column.</span></span> <span data-ttu-id="ef66f-114">既定のデータ型は、入力列のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="ef66f-114">The default data type is the data type of the input column.</span></span>  
  
9. <span data-ttu-id="ef66f-115">選択したデータ型によっては、必要に応じて **[長さ]** 、 **[有効桁数]** 、 **[小数点以下桁数]** 、および **[コード ページ]** 列の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="ef66f-115">Optionally, depending on the selected data type, update the values in the **Length**, the **Precision**, the **Scale**, and the **Code Page** columns.</span></span>  
  
10. <span data-ttu-id="ef66f-116">エラー出力を構成するには、 **[エラー出力の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef66f-116">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="ef66f-117">詳細については、「 [データ フロー コンポーネントでエラー出力を構成する](../../configure-an-error-output-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef66f-117">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="ef66f-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef66f-118">Click **OK**.</span></span>  
  
12. <span data-ttu-id="ef66f-119">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef66f-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef66f-120">参照</span><span class="sxs-lookup"><span data-stu-id="ef66f-120">See Also</span></span>  
 <span data-ttu-id="ef66f-121">[Data Conversion Transformation](data-conversion-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="ef66f-121">[Data Conversion Transformation](data-conversion-transformation.md) </span></span>  
 <span data-ttu-id="ef66f-122">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="ef66f-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="ef66f-123">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="ef66f-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="ef66f-124">[Integration Services のデータ型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ef66f-124">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 [<span data-ttu-id="ef66f-125">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="ef66f-125">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
