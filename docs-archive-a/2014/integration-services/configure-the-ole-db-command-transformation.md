---
title: OLE DB コマンド変換を構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [Integration Services]
- OLE DB Command transformation
ms.assetid: c800f167-3d2e-4c10-8ba3-a02f1872ccea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d1714a6b798c6d8256052fd3c16bd86182480bcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738634"
---
# <a name="configure-the-ole-db-command-transformation"></a><span data-ttu-id="4c281-102">OLE DB コマンド変換を構成する</span><span class="sxs-lookup"><span data-stu-id="4c281-102">Configure the OLE DB Command Transformation</span></span>
  <span data-ttu-id="4c281-103">OLE DB コマンド変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと、フラット ファイル ソースや OLE DB ソースなどの変換元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c281-103">To add and configure an OLE DB Command transformation, the package must already include at least one Data Flow task and a source such as a Flat File source or an OLE DB source.</span></span> <span data-ttu-id="4c281-104">この変換は、通常、パラメーター化クエリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c281-104">This transformation is typically used for running parameterized queries.</span></span>  
  
### <a name="to-configure-the-ole-db-command-transformation"></a><span data-ttu-id="4c281-105">OLE DB コマンド変換を構成するには</span><span class="sxs-lookup"><span data-stu-id="4c281-105">To configure the OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="4c281-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4c281-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="4c281-107">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="4c281-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4c281-108">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、OLE DB コマンド変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4c281-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB Command transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="4c281-109">OLE DB コマンド変換をデータ フローに連結します。連結するには、緑または赤の矢印のコネクタを、データ ソースまたは前の変換から OLE DB コマンド変換にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4c281-109">Connect the OLE DB Command transformation to the data flow by dragging a connector-the green or red arrow-from a data source or a previous transformation to the OLE DB Command transformation.</span></span>  
  
5.  <span data-ttu-id="4c281-110">コンポーネントを右クリックし、[編集] または **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-110">Right-click the component and select Edit or Show **Advanced Editor**.</span></span>  
  
6.  <span data-ttu-id="4c281-111">**[接続マネージャー]** タブで、 **[接続マネージャー]** 一覧から OLE DB 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="4c281-111">On the **Connection Managers** tab, select an OLE DB connection manager in the **Connection Manager** list.</span></span> <span data-ttu-id="4c281-112">詳細については、「 [OLE DB 接続マネージャー](connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c281-112">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="4c281-113">**[コンポーネントのプロパティ]** タブをクリックし、**[SQL コマンド]** ボックスの参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-113">Click the **Component Properties** tab and click the ellipsis button **(...)** in the **SqlCommand** box.</span></span>  
  
8.  <span data-ttu-id="4c281-114">**[文字列値エディター]** で、各パラメーターのパラメーター マーカーとして疑問符 (?) を使用して、パラメーター化 SQL ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="4c281-114">In the **String Value Editor**, type the parameterized SQL statement using a question mark (?) as the parameter marker for each parameter.</span></span>  
  
9. <span data-ttu-id="4c281-115">**[最新の情報に更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-115">Click **Refresh**.</span></span> <span data-ttu-id="4c281-116">**[更新]** をクリックすると、この変換は各パラメーターに対する列を External Columns コレクションに作成し、DBParamInfoFlags プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4c281-116">When you click **Refresh**, the transformation creates a column for each parameter in the External Columns collection and sets the DBParamInfoFlags property.</span></span>  
  
10. <span data-ttu-id="4c281-117">**[入力プロパティと出力プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-117">Click the **Input and Output Properties** tab.</span></span>  
  
11. <span data-ttu-id="4c281-118">**[OLE DB コマンドの入力]** を展開し、次に **[外部列]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="4c281-118">Expand **OLE DB Command Input**, and then expand **External Columns**.</span></span>  
  
12. <span data-ttu-id="4c281-119">**[外部列]** 一覧に、SQL ステートメント内の各パラメーターに対する列が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4c281-119">Verify that **External Columns** lists a column for each parameter in the SQL statement.</span></span> <span data-ttu-id="4c281-120">列名は、 **Param_0**、 **Param_1**のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c281-120">The column names are **Param_0**, **Param_1**, and so on.</span></span>  
  
     <span data-ttu-id="4c281-121">この列名は変更できません。</span><span class="sxs-lookup"><span data-stu-id="4c281-121">You should not change the column names.</span></span> <span data-ttu-id="4c281-122">列名を変更すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] によって OLE DB コマンド変換の検証エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4c281-122">If you change the column names, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a validation error for the OLE DB Command transformation.</span></span>  
  
     <span data-ttu-id="4c281-123">また、このデータ型も変更できません。</span><span class="sxs-lookup"><span data-stu-id="4c281-123">Also, you should not change the data type.</span></span> <span data-ttu-id="4c281-124">各列の DataType プロパティは、正しいデータ型に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4c281-124">The DataType property of each column is set to the correct data type.</span></span>  
  
13. <span data-ttu-id="4c281-125">**[外部列]** 一覧に列が表示されていない場合は、手動で列を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c281-125">If **External Columns** lists no columns you must add them manually.</span></span>  
  
    -   <span data-ttu-id="4c281-126">SQL ステートメントのパラメーターごとに、 **[列の追加]** を 1 回ずつクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-126">Click **Add Column** one time for each parameter in the SQL statement.</span></span>  
  
    -   <span data-ttu-id="4c281-127">列名を、 **Param_0**、 **Param_1**のように更新します。</span><span class="sxs-lookup"><span data-stu-id="4c281-127">Update the column names to **Param_0**, **Param_1**, and so on.</span></span>  
  
    -   <span data-ttu-id="4c281-128">DBParamInfoFlags プロパティの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c281-128">Specify a value in the DBParamInfoFlags property.</span></span> <span data-ttu-id="4c281-129">この値は、OLE DB DBPARAMFLAGSENUM 列挙値と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c281-129">The value must match a value in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="4c281-130">詳細については、OLE DB のリファレンス マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c281-130">For more information, see the OLE DB reference documentation.</span></span>  
  
    -   <span data-ttu-id="4c281-131">データ型に応じて列のデータ型を指定し、列のコード ページ、長さ、有効桁数、および小数点以下桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c281-131">Specify the data type of the column and, depending on the data type, specify the code page, length, precision, and scale of the column.</span></span>  
  
    -   <span data-ttu-id="4c281-132">未使用のパラメーターを削除するには、 **[外部列]** でパラメーターを選択し、 **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-132">To delete an unused parameter, select the parameter in **External Columns**, and then click **Remove Column**.</span></span>  
  
    -   <span data-ttu-id="4c281-133">**[列マッピング]** をクリックし、 **[使用できる入力列]** 一覧の列を **[使用できる変換先列]** 一覧のパラメーターにマップします。</span><span class="sxs-lookup"><span data-stu-id="4c281-133">Click **Column Mappings** and map columns in the **Available Input Columns** list to parameters in the **Available Destination Columns** list.</span></span>  
  
14. <span data-ttu-id="4c281-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-134">Click **OK**.</span></span>  
  
15. <span data-ttu-id="4c281-135">更新したパッケージを保存するには、 **[ファイル]** メニューの **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c281-135">To save the updated package, click **Save** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c281-136">参照</span><span class="sxs-lookup"><span data-stu-id="4c281-136">See Also</span></span>  
 <span data-ttu-id="4c281-137">[OLE DB コマンド変換](data-flow/transformations/ole-db-command-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="4c281-137">[OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md) </span></span>  
 <span data-ttu-id="4c281-138">[Integration Services の変換](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="4c281-138">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="4c281-139">[Integration Services のパス](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="4c281-139">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="4c281-140">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="4c281-140">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
