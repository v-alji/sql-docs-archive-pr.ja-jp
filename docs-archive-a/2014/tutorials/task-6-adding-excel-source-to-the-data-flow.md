---
title: 'タスク 6: Excel ソースをデータフローに追加する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ae183dee04619a407655026a49b189f7bb3ac6fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643653"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a><span data-ttu-id="7f571-102">タスク 6: Excel ソースをデータ フローに追加する</span><span class="sxs-lookup"><span data-stu-id="7f571-102">Task 6: Adding Excel Source to the Data Flow</span></span>
  <span data-ttu-id="7f571-103">ここでは、Excel ソースをデータ フローに追加してソース Excel ファイルから仕入先データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="7f571-103">In this task, you add an Excel Source to the data flow to read supplier data from the source Excel file.</span></span> <span data-ttu-id="7f571-104">Excel ソースは、Microsoft Excel ブック内のワークシートまたは範囲からデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="7f571-104">The Excel Source extracts data from worksheets or ranges in Microsoft Excel workbooks.</span></span> <span data-ttu-id="7f571-105">詳細については、「 [Excel ソース](../integration-services/data-flow/excel-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f571-105">See [Excel Source](../integration-services/data-flow/excel-source.md) topic for more details.</span></span>

1.  <span data-ttu-id="7f571-106">[ **SSIS ツールボックス**] の [**その他のソース**] から [ **Excel ソース**] を [**データフロー** ] タブにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="7f571-106">Drag-drop **Excel Source** from **Other Sources** in **SSIS Toolbox** to the **Data Flow** tab.</span></span>

2.  <span data-ttu-id="7f571-107">[**データフロー** ] タブで [ **Excel ソース**] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7f571-107">Right-click on **Excel Source** in the **Data Flow** tab, and click **Rename**.</span></span>

3.  <span data-ttu-id="7f571-108">「 **Excel ファイルから Supplier データを読み取る**」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7f571-108">Type **Read Supplier Data from Excel File** and press **ENTER**.</span></span>

4.  <span data-ttu-id="7f571-109">[Excel**ファイルから Supplier データを読み取る**] をダブルクリックして、[ **excel ソースエディター** ] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="7f571-109">Double-click **Read Supplier Data from Excel File** to launch the **Excel Source Editor** dialog box.</span></span>

5.  <span data-ttu-id="7f571-110">[ **Excel ソースエディター** ] ダイアログボックスで、[**新規**] をクリックして excel 接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7f571-110">In the **Excel Source Editor** dialog box, click **New** to create an Excel connection.</span></span>

6.  <span data-ttu-id="7f571-111">[ **Excel 接続マネージャー** ] ダイアログボックスで、 **[参照**] をクリックし、 **EIM チュートリアル**フォルダー内の**Suppliers.xls**ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7f571-111">In the **Excel Connection Manager** dialog box, click **Browse**, and then select the **Suppliers.xls** file in the **EIM Tutorial** folder.</span></span> <span data-ttu-id="7f571-112">[ **Excel バージョン**] ボックスで [ **Microsoft excel 97-2003** ] が選択されていることを確認し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7f571-112">Confirm that **Microsoft Excel 97-2003** is selected in the **Excel Version** box and then click **OK**.</span></span>

     <span data-ttu-id="7f571-113">![[Excel 接続マネージャー] ダイアログ ボックス](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "[Excel 接続マネージャー] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="7f571-113">![Excel Connection Manager Dialog Box](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel Connection Manager Dialog Box")</span></span>

7.  <span data-ttu-id="7f571-114">[ **Excel ソースエディター** ] ダイアログボックスで、[ **Excel シートの名前**] ボックスの一覧の [ **IncomingSuppliers $** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f571-114">In the **Excel Source Editor** dialog box, select **IncomingSuppliers$** in the **Name of the Excel sheet** list box.</span></span>

     <span data-ttu-id="7f571-115">![Excel シートの名前 - 今後の仕入先$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Excel シートの名前 - 今後の仕入先$")</span><span class="sxs-lookup"><span data-stu-id="7f571-115">![Name of Excel Sheet - Incoming Suppliers$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Name of Excel Sheet - Incoming Suppliers$")</span></span>

8.  <span data-ttu-id="7f571-116">Excel ファイルでデータをプレビューするには、[**プレビュー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7f571-116">Click **Preview** to preview the data in Excel file.</span></span>

9. <span data-ttu-id="7f571-117">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7f571-117">Click **OK** to close the dialog box.</span></span>

10. <span data-ttu-id="7f571-118">[ **SSIS ツールボックス**] の**他の変換**で**DQS クレンジング**変換を [**データフロー** ] タブにドラッグアンドドロップします。 [ **Excel ファイルから Supplier データを読み取る**] の下にあります。</span><span class="sxs-lookup"><span data-stu-id="7f571-118">Drag-drop **DQS Cleansing** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Read Supplier Data from Excel File**.</span></span> <span data-ttu-id="7f571-119">DQS クレンジング変換では、Data Quality Services (DQS) を使用し、ナレッジ ベースの承認済みのルールを適用することで、データを修正します。</span><span class="sxs-lookup"><span data-stu-id="7f571-119">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data by applying approved rules in the knowledge base.</span></span> <span data-ttu-id="7f571-120">この変換は、実行時に、DQS サーバー上に DQS クレンジング プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f571-120">This transform, at runtime, creates a DQS cleansing project on the DQS server.</span></span> <span data-ttu-id="7f571-121">詳細については、「 [DQS クレンジング変換](https://msdn.microsoft.com/library/ee677619.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f571-121">See [DQS Cleansing Transformation](https://msdn.microsoft.com/library/ee677619.aspx) topic for more details.</span></span>

## <a name="next-step"></a><span data-ttu-id="7f571-122">次の手順</span><span class="sxs-lookup"><span data-stu-id="7f571-122">Next Step</span></span>

[<span data-ttu-id="7f571-123">タスク 7: DQS クレンジング変換をデータ フローに追加する</span><span class="sxs-lookup"><span data-stu-id="7f571-123">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>](task-7-adding-dqs-cleansing-transform-to-the-data-flow.md)

### <a name="see-also"></a><span data-ttu-id="7f571-124">参照</span><span class="sxs-lookup"><span data-stu-id="7f571-124">See Also</span></span>

[<span data-ttu-id="7f571-125">データ フロー</span><span class="sxs-lookup"><span data-stu-id="7f571-125">Data Flow</span></span>](../integration-services/data-flow/data-flow.md)
