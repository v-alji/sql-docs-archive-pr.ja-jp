---
title: 既存のデータソース接続の編集 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.selexistconn.f1
ms.assetid: 97e63f18-a01d-4c91-a411-e7e6d40a0647
author: minewiskan
ms.author: owend
ms.openlocfilehash: 675a0d1119e25a92231d3e74a79739cb2e96b6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644205"
---
# <a name="edit-an-existing-data-source-connection-ssas-tabular"></a><span data-ttu-id="4ceff-102">既存のデータ ソース接続の編集 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="4ceff-102">Edit an Existing Data Source Connection (SSAS Tabular)</span></span>
  <span data-ttu-id="4ceff-103">このトピックでは、テーブル モデルの既存のデータ ソース接続のプロパティを編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-103">This topic describes how to edit the properties of an existing data source connection in a tabular model.</span></span>  
  
 <span data-ttu-id="4ceff-104">外部データ ソースへの接続を作成した後、次のようにして接続を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-104">After you have created a connection to an external data source, you can later modify that connection in these ways:</span></span>  
  
-   <span data-ttu-id="4ceff-105">ソースとして使用するファイル、フィード、またはデータベース、そのプロパティ、その他のプロバイダー固有の接続オプションなどの接続情報を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-105">You can change the connection information, including the file, feed, or database used as a source, its properties, or other provider-specific connection options.</span></span>  
  
-   <span data-ttu-id="4ceff-106">テーブルと列のマッピングを変更したり、使用されなくなった列への参照を削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-106">You can change table and column mappings, and remove references to columns that are no longer used.</span></span>  
  
-   <span data-ttu-id="4ceff-107">外部データ ソースから取得するテーブル、ビュー、または列を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-107">You can change the tables, views, or columns that you get from the external data source.</span></span>  
  
## <a name="modify-a-connection"></a><span data-ttu-id="4ceff-108">接続の変更</span><span class="sxs-lookup"><span data-stu-id="4ceff-108">Modify a Connection</span></span>  
 <span data-ttu-id="4ceff-109">この手順では、データベースのデータ ソース接続を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-109">This procedure describes how to modify a database data source connection.</span></span> <span data-ttu-id="4ceff-110">データ ソース操作用のオプションはデータ ソースの種類によって異なる場合がありますが、その違いは簡単に識別できます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-110">Some options for working with data sources differ depending on the data source type; however, you should be able to easily identify those differences.</span></span>  
  
#### <a name="to-change-the-external-data-source-used-by-a-current-connection"></a><span data-ttu-id="4ceff-111">現在の接続で使用する外部データ ソースを変更するには</span><span class="sxs-lookup"><span data-stu-id="4ceff-111">To change the external data source used by a current connection</span></span>  
  
1.  <span data-ttu-id="4ceff-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックしてから **[既存の接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ceff-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="4ceff-113">変更するデータ ソース接続を選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ceff-113">Select the data source connection you want to modify, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="4ceff-114">**[接続の編集]** ダイアログ ボックスの **[参照]** をクリックして、同じ種類で名前または場所が異なる別のデータベースを探します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-114">In the **Edit Connection** dialog box, click **Browse** to locate another database of the same type but with a different name or location.</span></span>  
  
     <span data-ttu-id="4ceff-115">データベース ファイルを変更すると、新しいデータを表示するにはテーブルを保存および更新する必要があることを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-115">As soon as you change the database file, a message appears indicating that you need to save and refresh the tables in order to see the new data.</span></span>  
  
4.  <span data-ttu-id="4ceff-116">**[保存]** をクリックしてから、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ceff-116">Click **Save**, and then click **Close**.</span></span>  
  
5.  <span data-ttu-id="4ceff-117">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]**、 **[処理]** の順にクリックしてから、 **[すべて処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ceff-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model**, click **Process**, and then click **Process All**.</span></span>  
  
     <span data-ttu-id="4ceff-118">新しいデータ ソースと元のデータ選択を使用して、テーブルが再処理されます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-118">The tables are re-processed using the new data source, but with the original data selections.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4ceff-119">元のデータ ソースに存在しなかったテーブルが新しいデータ ソースに含まれている場合は、変更した接続を再度開いてテーブルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ceff-119">If the new data source contains any additional tables that were not present in the original data source, you must re-open the changed connection and add the tables.</span></span>  
  
## <a name="edit-table-and-column-mappings-bindings"></a><span data-ttu-id="4ceff-120">テーブルと列のマッピング (バインド) の編集</span><span class="sxs-lookup"><span data-stu-id="4ceff-120">Edit Table and Column Mappings (Bindings)</span></span>  
 <span data-ttu-id="4ceff-121">この手順では、データ ソースの変更後にマッピングを編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-121">This procedure describes how to edit the mappings after you change a data source.</span></span>  
  
#### <a name="to-edit-column-mappings-when-a-data-source-changes"></a><span data-ttu-id="4ceff-122">データ ソースの変更時に列マッピングを編集するには</span><span class="sxs-lookup"><span data-stu-id="4ceff-122">To edit column mappings when a data source changes</span></span>  
  
1.  <span data-ttu-id="4ceff-123">モデル デザイナーでテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-123">In the model designer, select a table.</span></span>  
  
2.  <span data-ttu-id="4ceff-124">**[テーブル]** メニューをクリックし、 **[テーブルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ceff-124">Click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
     <span data-ttu-id="4ceff-125">選択したテーブルの名前が **[テーブル名]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-125">The name of the selected table is displayed in the **Table Name** box.</span></span> <span data-ttu-id="4ceff-126">**[ソース名]** ボックスには、外部データ ソース内のテーブルの名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4ceff-126">The **Source Name** box contains the name of the table in the external data source.</span></span> <span data-ttu-id="4ceff-127">ソースとモデルで列に異なる名前が付いている場合、 **[ソース]** または **[モデル]** を選択すると、2 つの列名セットの間を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-127">If columns are named differently in the source and in the model, you can toggle between the two sets of column names by selecting the options **Source** or **Model**.</span></span>  
  
3.  <span data-ttu-id="4ceff-128">データ ソースとして使用するテーブルを変更するには、 **[ソース名]** で、現在のテーブルと異なるテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-128">To change the table that is used as a data source, for **Source Name**, select a different table than the current one.</span></span>  
  
4.  <span data-ttu-id="4ceff-129">必要に応じて列マッピングを変更します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-129">Change column mappings if needed:</span></span>  
  
    1.  <span data-ttu-id="4ceff-130">ソースにあってモデルにない列を追加するには、列名の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4ceff-130">To add columns that are present in the source but not in the model, select the checkbox beside the column name.</span></span>  
  
         <span data-ttu-id="4ceff-131">実際のデータは、次回更新時にモデルに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-131">The actual data will be loaded into the model the next time you refresh.</span></span>  
  
    2.  <span data-ttu-id="4ceff-132">現在のデータ ソースで使用できなくなった列がモデルにある場合は、無効な列を示すメッセージが通知領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-132">If some columns in the model are no longer available in the current data source, a message appears in the notification area that lists the invalid columns.</span></span> <span data-ttu-id="4ceff-133">他の操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4ceff-133">You do not need to do anything else.</span></span>  
  
5.  <span data-ttu-id="4ceff-134">**[保存]** をクリックして、モデルに変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="4ceff-134">Click **Save** to apply the changes to your model.</span></span>  
  
     <span data-ttu-id="4ceff-135">現在のテーブルのプロパティ セットを保存すると、テーブルを処理する必要があることを示すメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="4ceff-135">When you save the current set of table properties, a message may appear indicating that you need to process the tables.</span></span> <span data-ttu-id="4ceff-136">**[処理]** をクリックして、更新されたデータをモデルに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4ceff-136">Click **Process** to load updated data into your model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ceff-137">参照</span><span class="sxs-lookup"><span data-stu-id="4ceff-137">See Also</span></span>  
 <span data-ttu-id="4ceff-138">[SSAS 表形式&#41;&#40;データを処理する](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="4ceff-138">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="4ceff-139">サポートされているデータ ソース &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="4ceff-139">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
