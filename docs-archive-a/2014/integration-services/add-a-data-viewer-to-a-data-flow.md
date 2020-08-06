---
title: データフローにデータビューアーを追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data viewers [Integration Services]
- data flow [Integration Services], data viewers
- adding data viewers
ms.assetid: 5e573274-a170-4132-bfc8-a8ff3a8411e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7abd76417552ec50da736afe024a5ae36ee6a2ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632050"
---
# <a name="add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="7568f-102">データ フローにデータ ビューアーを追加する</span><span class="sxs-lookup"><span data-stu-id="7568f-102">Add a Data Viewer to a Data Flow</span></span>
  <span data-ttu-id="7568f-103">このトピックでは、データ フローにデータ ビューアーを追加して構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7568f-103">This topic describes how to add and configure a data viewer in a data flow.</span></span> <span data-ttu-id="7568f-104">データ ビューアーには、2 つのデータ フロー コンポーネント間を移動するデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7568f-104">A data viewer displays data that is moving between two data flow components.</span></span> <span data-ttu-id="7568f-105">たとえば、データ ビューアーでは、データ ソースから抽出されたデータを、データ フローの変換で変更される前の状態で表示できます。</span><span class="sxs-lookup"><span data-stu-id="7568f-105">For example, a data viewer can display the data that is extracted from a data source before a transformation in the data flow modifies the data.</span></span>  
  
 <span data-ttu-id="7568f-106">パスは、データ フロー コンポーネントの出力を別のコンポーネントの入力に連結することにより、データ フロー内のコンポーネントを連結します。</span><span class="sxs-lookup"><span data-stu-id="7568f-106">A path connects components in a data flow by connecting the output of one data flow component to the input of another component.</span></span>  
  
 <span data-ttu-id="7568f-107">データ ビューアーをパッケージに追加するには、パッケージにデータ フロー タスクが含まれていて、少なくとも 2 つのデータ フロー コンポーネントが接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7568f-107">Before you can add data viewers to a package, the package must include a Data Flow task and at least two data flow components that are connected.</span></span>  
  
### <a name="to-add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="7568f-108">データ フローにデータ ビューアーを追加するには</span><span class="sxs-lookup"><span data-stu-id="7568f-108">To add a data viewer to a data flow</span></span>  
  
1.  <span data-ttu-id="7568f-109">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="7568f-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="7568f-110">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="7568f-110">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="7568f-111">アクティブになっていない場合は、 **[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7568f-111">Click the **Control Flow** tab, if it is not already active.</span></span>  
  
4.  <span data-ttu-id="7568f-112">データ ビューアーをアタッチするデータ フローに対応するデータ フロー タスクをクリックし、 **[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7568f-112">Click the Data Flow task to whose data flow you want to attach a data viewer and then click the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="7568f-113">2 つのデータ フロー コンポーネント間のパスを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7568f-113">Right-click a path between two data flow components, and click **Edit**.</span></span>  
  
6.  <span data-ttu-id="7568f-114">**[全般]** ページで、パスのプロパティを表示および編集できます。</span><span class="sxs-lookup"><span data-stu-id="7568f-114">On the **General** page, you can view and edit path properties.</span></span> <span data-ttu-id="7568f-115">たとえば、 **[PathAnnotation]** ボックスの一覧で、パスの横に表示される注釈を選択できます。</span><span class="sxs-lookup"><span data-stu-id="7568f-115">For example, from the **PathAnnotation** drop-down list you can select the annotation that appears next to the path.</span></span>  
  
7.  <span data-ttu-id="7568f-116">**[メタデータ]** ページで、列のメタデータを表示し、メタデータをクリップボードにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="7568f-116">On the **Metadata** page, you can view the column metadata and copy the metadata to the Clipboard.</span></span>  
  
8.  <span data-ttu-id="7568f-117">**[データ ビューアー]** ページで、 **[データ ビューアーを有効にする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7568f-117">On the **Data Viewer** page, click **Enable data viewer**.</span></span>  
  
9. <span data-ttu-id="7568f-118">[表示する列] 領域で、データ ビューアーに表示する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="7568f-118">In the Columns to display area, select the columns you want to display in the data viewer.</span></span> <span data-ttu-id="7568f-119">既定では、表示可能なすべての列が選択され、 **[表示する列]** の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7568f-119">By default, all the available columns are selected and listed in the **Displayed Columns** list.</span></span> <span data-ttu-id="7568f-120">表示しない列は、選択してから左矢印をクリックして、 **[未使用の列]** の一覧に移動させます。</span><span class="sxs-lookup"><span data-stu-id="7568f-120">Move columns that you do not want to use to the **Unused Column** list by selecting them and then clicking the left arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7568f-121">グリッドでは、DT_DATE、DT_DBTIME2、DT_FILETIME、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、および DT_DBTIMESTAMPOFFSET の各データ型を表す値は、ISO 8601 に従って書式設定された文字列として表示され、`T` 区切りが空白区切りに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="7568f-121">In the grid, values that represent the DT_DATE, DT_DBTIME2, DT_FILETIME, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types appear as ISO 8601 formatted strings and a space separator replaces the `T` separator.</span></span> <span data-ttu-id="7568f-122">DT_DATE データ型および DT_FILETIME データ型を表す値には、秒の小数部を表す 7 桁が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7568f-122">Values that represent the DT_DATE and DT_FILETIME data types include seven digits for fractional seconds.</span></span> <span data-ttu-id="7568f-123">DT_FILETIME データ型では秒の小数部が 3 桁のみ格納されるため、残りの 4 桁についてはグリッドに 0 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7568f-123">Because the DT_FILETIME data type stores only three digits of fractional seconds, the grid displays zeros for the remaining four digits.</span></span> <span data-ttu-id="7568f-124">DT_DBTIMESTAMP データ型を表す値には、秒の小数部を表す 3 桁が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7568f-124">Values that represent the DT_DBTIMESTAMP data type include three digits for fractional seconds.</span></span> <span data-ttu-id="7568f-125">DT_DBTIME2、DT_DBTIMESTAMP2、および DT_DBTIMESTAMPOFFSET の各データ型を表す値については、秒を表す小数点以下桁数が、列のデータ型で指定された小数点以下桁数と一致します。</span><span class="sxs-lookup"><span data-stu-id="7568f-125">For values that represent the DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types, the number of digits for fractional seconds corresponds to the scale specified for the column's data type.</span></span> <span data-ttu-id="7568f-126">ISO 8601 形式の詳細については、「 [日付および時刻の形式](../../2014/integration-services/date-and-time-formats.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7568f-126">For more information about ISO 8601 formats, see [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span> <span data-ttu-id="7568f-127">データ型について詳しくは、「 [Integration Services のデータ型](data-flow/integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7568f-127">For more information about data types, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
10. <span data-ttu-id="7568f-128">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7568f-128">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7568f-129">参照</span><span class="sxs-lookup"><span data-stu-id="7568f-129">See Also</span></span>  
 <span data-ttu-id="7568f-130">[Integration Services の変換](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="7568f-130">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="7568f-131">[Integration Services のパス](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="7568f-131">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="7568f-132">[データ フロー](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="7568f-132">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="7568f-133">データ フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="7568f-133">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
  
