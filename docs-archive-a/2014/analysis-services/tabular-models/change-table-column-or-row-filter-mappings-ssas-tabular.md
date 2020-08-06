---
title: テーブル、列、または行のフィルターのマッピングの変更 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: d8a597fb51804ea12caace63f3308b07bffc5899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639668"
---
# <a name="change-table-column-or-row-filter-mappings-ssas-tabular"></a><span data-ttu-id="92e9f-102">テーブル、列、または行のフィルターのマッピングの変更 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="92e9f-102">Change table, column, or row filter mappings (SSAS Tabular)</span></span>
  <span data-ttu-id="92e9f-103">このトピックでは、 **の** [テーブルのプロパティの編集] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]ダイアログ ボックスを使用して、テーブル、列、または行のフィルターのマッピングを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="92e9f-103">This topic describes how to change table, column, or row filter mappings by using the **Edit Table Properties** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="92e9f-104">**[テーブルのプロパティの編集]** ダイアログ ボックスのオプションは、最初にデータをインポートしたときに一覧からテーブルを選択したか SQL クエリを使用したかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="92e9f-104">Options in the **Edit Table Properties** dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span> <span data-ttu-id="92e9f-105">最初にデータをインポートするときに一覧から選択した場合は、 **[テーブルのプロパティの編集]** ダイアログ ボックスにテーブルのプレビュー モードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92e9f-105">If you originally imported the data by selecting from a list, the **Edit Table Properties** dialog box displays the Table Preview mode.</span></span> <span data-ttu-id="92e9f-106">このモードでは、ソース テーブルの最初の 50 行に制限されたサブセットのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92e9f-106">This mode displays only a subset limited to the first fifty rows of the source table.</span></span> <span data-ttu-id="92e9f-107">最初にデータをインポートするときに SQL ステートメントを使用した場合は、 **[テーブルのプロパティの編集]** ダイアログ ボックスには SQL ステートメントのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92e9f-107">If you originally imported the data by using a SQL statement, the **Edit Table Properties** dialog box only displays a SQL statement.</span></span> <span data-ttu-id="92e9f-108">SQL クエリ ステートメントを使用すると、フィルターをデザインするか、SQL ステートメントを手動で編集することによって、行のサブセットを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="92e9f-108">Using a SQL query statement, you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="92e9f-109">現在のテーブルと異なる列を持つテーブルにソースを変更すると、列が異なることを示す警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92e9f-109">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="92e9f-110">現在のテーブルに含める列を選択し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e9f-110">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="92e9f-111">テーブルの左側にあるチェック ボックスをオンにすると、テーブル全体を置換できます。</span><span class="sxs-lookup"><span data-stu-id="92e9f-111">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92e9f-112">テーブルに複数のパーティションがある場合、[テーブルのプロパティの編集] ダイアログ ボックスを使用して、行のフィルターのマッピングを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="92e9f-112">If your table has more than one partition, you cannot use the Edit Table Properties dialog box to change row filter mappings.</span></span> <span data-ttu-id="92e9f-113">複数のパーティションを持つテーブルについて行のフィルターのマッピングを変更するには、パーティション マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="92e9f-113">To change row filter mappings for tables with multiple partitions, use Partition Manager.</span></span> <span data-ttu-id="92e9f-114">詳細については、「 [パーティション (SSAS テーブル)](partitions-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92e9f-114">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a><span data-ttu-id="92e9f-115">テーブル、列、または行のフィルターのマッピングを変更するには</span><span class="sxs-lookup"><span data-stu-id="92e9f-115">To change table, column, or row filter mappings</span></span>  
  
1.  <span data-ttu-id="92e9f-116">モデル デザイナーでテーブルをクリックし、 **[テーブル]** メニュー、 **[テーブルのプロパティ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e9f-116">In the model designer, click the table, then click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="92e9f-117">**[テーブルのプロパティの編集]** ダイアログ ボックスで、フィルターの基準とする条件を含む列を見つけ、列見出しの右側にある下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e9f-117">In the **Edit Table Properties** dialog box, locate the column that contains the criteria you want to filter on, and then click the down arrow at the right of the column heading.</span></span>  
  
3.  <span data-ttu-id="92e9f-118">[**オートフィルター** ] メニューで、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="92e9f-118">In the **AutoFilter** menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="92e9f-119">列の値の一覧で、フィルター処理の基準にする 1 つ以上の値を選択するか、選択を解除し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e9f-119">In the list of column values, select or clear one or more values to filter by, and then click OK.</span></span>  
  
         <span data-ttu-id="92e9f-120">値の数が極端に多い場合、個々のアイテムが一覧に表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="92e9f-120">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="92e9f-121">その場合は、"アイテムが多すぎるため、表示できません" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92e9f-121">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="92e9f-122">列の種類に応じて **[数値フィルター]** または **[テキスト フィルター]** をクリックし、比較演算子コマンド ([等しい] など) のいずれかをクリックするか、[カスタム フィルター] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e9f-122">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as Equals), or click Custom Filter.</span></span> <span data-ttu-id="92e9f-123">**[カスタム フィルター]** ダイアログ ボックスで、フィルターを作成し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e9f-123">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
         <span data-ttu-id="92e9f-124">設定を間違ったため最初からやり直す場合は、 **[行フィルターのクリア]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e9f-124">If you make a mistake and need to start over, click **Clear Row Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e9f-125">参照</span><span class="sxs-lookup"><span data-stu-id="92e9f-125">See Also</span></span>  
 <span data-ttu-id="92e9f-126">[[テーブルのプロパティの編集] ダイアログ ボックス (SSAS)](../edit-table-properties-dialog-box-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="92e9f-126">[Edit Table Properties Dialog Box &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md)</span></span>  
  
  
