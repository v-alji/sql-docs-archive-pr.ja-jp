---
title: データのコピーと貼り付け (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30df733377f3cb6f7583d380fbb8e92a0ea69e88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633453"
---
# <a name="copy-and-paste-data-ssas-tabular"></a><span data-ttu-id="34b0e-102">データのコピーと貼り付け (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="34b0e-102">Copy and Paste Data (SSAS Tabular)</span></span>
  <span data-ttu-id="34b0e-103">テーブルのデータを外部アプリケーションからコピーし、モデル デザイナーの新規または既存のテーブルに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-103">You can copy table data from external applications and paste it into a new or existing table in the model designer.</span></span> <span data-ttu-id="34b0e-104">Excel や Word からコピーされたデータなど、クリップボードから貼り付けるデータは HTML 形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="34b0e-104">The data that you paste from the Clipboard must be in HTML format, for example, data that is copied from Excel or Word.</span></span> <span data-ttu-id="34b0e-105">モデル デザイナーは自動的にデータ型を検出し、貼り付けられたデータにその型を適用します。</span><span class="sxs-lookup"><span data-stu-id="34b0e-105">The model designer will automatically detect and apply data types to the pasted data.</span></span> <span data-ttu-id="34b0e-106">手動でデータ型を変更することも、列の書式を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-106">You can also manually modify the data type or display formatting of a column.</span></span>  
  
 <span data-ttu-id="34b0e-107">データ ソースが接続されたテーブルとは異なり、貼り付けたテーブルには、接続名またはソース データ プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="34b0e-107">Unlike tables with a data source connection, pasted tables do not have a Connection Name or Source Data property.</span></span> <span data-ttu-id="34b0e-108">貼り付けられたデータは、Model.bim ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-108">Pasted data is persisted in the Model.bim file.</span></span> <span data-ttu-id="34b0e-109">プロジェクトまたは Model.bim ファイルを保存すると、貼り付けられたデータも保存されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-109">When the project or Model.bim file is saved, the pasted data is also saved.</span></span>  
  
 <span data-ttu-id="34b0e-110">モデルを配置すると、配置によってモデルが処理されるかどうかに関係なく、貼り付けられたデータも一緒に配置されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-110">When a model is deployed, pasted data will also be deployed with it regardless if the model is processed with the deployment.</span></span>  
  
 <span data-ttu-id="34b0e-111">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="34b0e-111">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="34b0e-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="34b0e-112">Prerequisites</span></span>](#bkmk_prerequisites)  
  
-   [<span data-ttu-id="34b0e-113">データの貼り付け</span><span class="sxs-lookup"><span data-stu-id="34b0e-113">Paste Data</span></span>](#bkmk_paste_data)  
  
-   <span data-ttu-id="34b0e-114">[[貼り付けプレビュー] ダイアログ ボックス](#bkmk_paste_preview)</span><span class="sxs-lookup"><span data-stu-id="34b0e-114">[Paste Preview Dialog Box](#bkmk_paste_preview)</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> <span data-ttu-id="34b0e-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="34b0e-115">Prerequisites</span></span>  
 <span data-ttu-id="34b0e-116">データを貼り付けるときには、次のような制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="34b0e-116">There are some restrictions when pasting data:</span></span>  
  
-   <span data-ttu-id="34b0e-117">貼り付けたテーブルは 10, 000 より多い行を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="34b0e-117">Pasted tables cannot have more than 10,000 rows.</span></span>  
  
-   <span data-ttu-id="34b0e-118">貼り付けたテーブルをパーティション分割することはできません。</span><span class="sxs-lookup"><span data-stu-id="34b0e-118">Pasted tables cannot be partitioned.</span></span>  
  
-   <span data-ttu-id="34b0e-119">貼り付けられたテーブルは、DirectQuery モードではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="34b0e-119">Pasted tables are not supported in DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="34b0e-120">**[貼り付け追加]** と **[貼り付け置換]** は、クリップボードからのデータの貼り付けによって作成されたテーブルで作業する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-120">The **Paste Append** and **Paste Replace** options are only available when working with a table that was initially created by pasting data from the Clipboard.</span></span> <span data-ttu-id="34b0e-121">**[貼り付け追加]** または **[貼り付け置換]** を使用して、別の種類のデータ ソースからインポートされたデータのテーブルにデータを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="34b0e-121">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data from another type of data source.</span></span>  
  
-   <span data-ttu-id="34b0e-122">**[貼り付け追加]** または **[貼り付け置換]** を使用する場合、新しいデータには元のデータと同じ数の列が必要です。</span><span class="sxs-lookup"><span data-stu-id="34b0e-122">When you use **Paste Append** or **Paste Replace**, the new data must contain exactly the same number of columns as the original data.</span></span> <span data-ttu-id="34b0e-123">さらに、貼り付けまたは追加するデータの列は、貼り付け先または追加先のテーブルの列のデータ型と同じか互換性のあるデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="34b0e-123">Preferably, the columns of data that you paste or append should also be of the same or compatible data type as those in the destination table.</span></span> <span data-ttu-id="34b0e-124">異なるデータ型を使用できる場合もありますが、 **型の不一致** エラーが表示されることもあります。</span><span class="sxs-lookup"><span data-stu-id="34b0e-124">In some cases you can use a different data type, but a **Type mismatch** error may be displayed.</span></span>  
  
##  <a name="paste-data"></a><a name="bkmk_paste_data"></a><span data-ttu-id="34b0e-125">データの貼り付け</span><span class="sxs-lookup"><span data-stu-id="34b0e-125">Paste Data</span></span>  
  
#### <a name="to-paste-data-into-the-designer"></a><span data-ttu-id="34b0e-126">デザイナーにデータを貼り付けるには</span><span class="sxs-lookup"><span data-stu-id="34b0e-126">To paste data into the designer</span></span>  
  
-   <span data-ttu-id="34b0e-127">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の **[編集]** メニューをクリックし、次のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="34b0e-127">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Edit** menu, and then clicke of the following:</span></span>  
  
    -   <span data-ttu-id="34b0e-128">クリップボードの内容を新しいテーブルに貼り付けるには、 **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34b0e-128">Click **Paste** to paste the contents of the Clipboard into a new table.</span></span>  
  
    -   <span data-ttu-id="34b0e-129">クリップボードの内容を選択したテーブルに追加の行として貼り付けるには、 **[貼り付け追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34b0e-129">Click **Paste Append** to paste the contents of the Clipboard as additional rows into the selected table.</span></span> <span data-ttu-id="34b0e-130">新しい行がテーブルの末尾に追加されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-130">The new rows will be added to the end of the table.</span></span>  
  
    -   <span data-ttu-id="34b0e-131">選択したテーブルをクリップボードの内容に置き換えるには、 **[貼り付け置換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34b0e-131">Click **Paste Replace** to replace the selected table with the contents of the Clipboard.</span></span> <span data-ttu-id="34b0e-132">既存のすべての列ヘッダー名はテーブルに残り、リレーションシップは保持されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-132">All existing column header names will remain in the table, and relationships are preserved.</span></span>  
  
##  <a name="paste-preview-dialog-box"></a><a name="bkmk_paste_preview"></a><span data-ttu-id="34b0e-133">[貼り付けプレビュー] ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="34b0e-133">Paste Preview Dialog Box</span></span>  
 <span data-ttu-id="34b0e-134">**[貼り付けプレビュー]** ダイアログ ボックスを使用すると、デザイナー ウィンドウにコピーされたデータのプレビューを表示して、データが正しくコピーされたことを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-134">The **Paste Preview** dialog box enables you to see a preview of data that is copied into the designer window and to ensure that the data is copied correctly.</span></span> <span data-ttu-id="34b0e-135">このダイアログ ボックスにアクセスするには、テーブル ベースのデータを HTML 形式でクリップボードにコピーし、デザイナーで **[編集]** メニューをクリックして、 **[貼り付け]**、 **[貼り付け追加]**、または **[貼り付け置換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34b0e-135">To access this dialog box, copy table-based data in the HTML format to the clipboard, and then in the designer, click on the **Edit** menu, and then click **Paste**, **Paste Append**, or **Paste Replace**.</span></span> <span data-ttu-id="34b0e-136">**[貼り付け追加]** オプションと **[貼り付け置換]** オプションは、クリップボードからコピーして貼り付けることで作成されたテーブル内のデータを追加または置換する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-136">The **Paste Append** and **Paste Replace** options are only available when you add or replace data in a table that was created by copying and pasting from the Clipboard.</span></span> <span data-ttu-id="34b0e-137">**[貼り付け追加]** または **[貼り付け置換]** を使用して、インポートされたデータのテーブルにデータを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="34b0e-137">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data.</span></span>  
  
 <span data-ttu-id="34b0e-138">このダイアログ ボックスのオプションは、まったく新しいテーブルにデータを貼り付けるか、既存のテーブルにデータを貼り付けて既存のデータを新しいデータで置き換えるか、既存のテーブルにデータを追加するかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="34b0e-138">The options for this dialog box are different depending on whether you paste data into a completely new table, paste data into an existing table and then replace the existing data with the new data, or whether you append data to an existing table.</span></span>  
  
### <a name="paste-to-new-table"></a><span data-ttu-id="34b0e-139">[新規テーブル]</span><span class="sxs-lookup"><span data-stu-id="34b0e-139">Paste to New Table</span></span>  
 <span data-ttu-id="34b0e-140">**[テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="34b0e-140">**Table name**</span></span>  
 <span data-ttu-id="34b0e-141">デザイナーで作成するテーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="34b0e-141">Specify the name of the table that will be created in the designer.</span></span>  
  
 <span data-ttu-id="34b0e-142">**[貼り付けるデータ]**</span><span class="sxs-lookup"><span data-stu-id="34b0e-142">**Data to be pasted**</span></span>  
 <span data-ttu-id="34b0e-143">貼り付け先テーブルに追加されるクリップボードの内容のサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-143">Shows a sample of the Clipboard contents that will be added to the destination table.</span></span>  
  
### <a name="paste-append"></a><span data-ttu-id="34b0e-144">[貼り付け追加]</span><span class="sxs-lookup"><span data-stu-id="34b0e-144">Paste Append</span></span>  
 <span data-ttu-id="34b0e-145">**[テーブル内の既存のデータ]**</span><span class="sxs-lookup"><span data-stu-id="34b0e-145">**Existing data in the table**</span></span>  
 <span data-ttu-id="34b0e-146">列やデータ型を確認できるように、テーブル内の既存のデータのサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-146">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="34b0e-147">**[貼り付けるデータ]**</span><span class="sxs-lookup"><span data-stu-id="34b0e-147">**Data to be pasted**</span></span>  
 <span data-ttu-id="34b0e-148">クリップボードの内容のサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-148">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="34b0e-149">既存のデータに、このデータが追加されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-149">The existing data will be appended by this data.</span></span>  
  
### <a name="paste-replace"></a><span data-ttu-id="34b0e-150">[貼り付け置換]</span><span class="sxs-lookup"><span data-stu-id="34b0e-150">Paste Replace</span></span>  
 <span data-ttu-id="34b0e-151">**[テーブル内の既存のデータ]**</span><span class="sxs-lookup"><span data-stu-id="34b0e-151">**Existing data in the table**</span></span>  
 <span data-ttu-id="34b0e-152">列やデータ型を確認できるように、テーブル内の既存のデータのサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-152">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="34b0e-153">**[貼り付けるデータ]**</span><span class="sxs-lookup"><span data-stu-id="34b0e-153">**Data to be pasted**</span></span>  
 <span data-ttu-id="34b0e-154">クリップボードの内容のサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-154">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="34b0e-155">貼り付け先のテーブル内の既存のデータは削除され、テーブルに新しい行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="34b0e-155">The existing data in the destination table will be deleted and the new rows will be inserted into the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b0e-156">参照</span><span class="sxs-lookup"><span data-stu-id="34b0e-156">See Also</span></span>  
 <span data-ttu-id="34b0e-157">[SSAS 表形式&#41;&#40;データをインポートする](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="34b0e-157">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="34b0e-158">[SSAS 表形式&#41;&#40;サポートされるデータソース](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="34b0e-158">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="34b0e-159">列のデータ型の設定 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="34b0e-159">Set the Data Type of a Column &#40;SSAS Tabular&#41;</span></span>](tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  
