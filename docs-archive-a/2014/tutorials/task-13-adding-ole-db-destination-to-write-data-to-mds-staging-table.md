---
title: 'タスク 13: MDS ステージングテーブルにデータを書き込むための OLE DB 変換先の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77799782518a3be2441b4c461467e3132781298d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714870"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a><span data-ttu-id="7a625-102">タスク 13: データを書き込む OLE DB 変換先を MDS ステージング テーブルに追加する</span><span class="sxs-lookup"><span data-stu-id="7a625-102">Task 13: Adding OLE DB Destination to Write Data to MDS Staging Table</span></span>
  <span data-ttu-id="7a625-103">すべてのレコードに**Importtype**と**batchtag**の値を追加したので、ステージング用に MDS に送信する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="7a625-103">Now that you have added **ImportType** and **BatchTag** values to all records, you are ready to send them over to MDS for staging.</span></span> <span data-ttu-id="7a625-104">このタスクでは、OLE DB 変換先を使用して、データを**stg. supplier_Leaf**ステージングテーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7a625-104">In this task, you use the OLE DB Destination to write the data into **stg.supplier_Leaf** staging table.</span></span>  
  
1.  <span data-ttu-id="7a625-105">**SSIS ツールボックス**の [**その他の変換**先] セクションから [**データフロー** ] タブに [**変換先**] を OLE DB ドラッグし、[ **MDS で必要な列を追加**] の下にドロップします。</span><span class="sxs-lookup"><span data-stu-id="7a625-105">Drag **OLE DB Destination** from **Other Destinations** section in the **SSIS Toolbox** to the **Data Flow** tab and drop it under **Add Columns Required by MDS**.</span></span>  
  
2.  <span data-ttu-id="7a625-106">[**データフロー** ] タブの [ **OLE DB Destination** ] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a625-106">Right-click **OLE DB Destination** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="7a625-107">「 **MDS ステージングテーブルにサプライヤーデータを書き込む**」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7a625-107">Type **Write Supplier Data to MDS Staging Table** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="7a625-108">Blue コネクタを使用して**Mds ステージングテーブルにサプライヤーデータを書き込む**には、Mds が必要とする**Add 列**を接続します。</span><span class="sxs-lookup"><span data-stu-id="7a625-108">Connect the **Add Columns Required by MDS** to **Write Supplier Data to MDS Staging Table** using the blue connector.</span></span>  
  
4.  <span data-ttu-id="7a625-109">[**データフロー** ] タブの [ **MDS ステージングテーブルにサプライヤーデータを書き込む] を**ダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a625-109">Double-click **Write Supplier Data to MDS Staging Table** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="7a625-110">[ **OLE DB 変換先エディター** ] ダイアログボックスで、[(ローカル)] が選択されていることを確認し**ます。MDS** (または**localhost。**[ **OLE DB 接続マネージャー** ] フィールドに対して [MDS] が選択されています。</span><span class="sxs-lookup"><span data-stu-id="7a625-110">In the **OLE DB Destination Editor** Dialog box, make sure that **(local).MDS** (or **localhost.MDS**) is selected for the **OLE DB Connection Manager** field.</span></span>  
  
6.  <span data-ttu-id="7a625-111">[Stg] を選択し**ます。** テーブル**またはビューの名前**の一覧からテーブルを Supplier_Leaf します。</span><span class="sxs-lookup"><span data-stu-id="7a625-111">Select **stg.Supplier_Leaf** table from the list of **Name of the table or the view**.</span></span>  
  
     <span data-ttu-id="7a625-112">![OLEDB 変換先エディター](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB 変換先エディター")</span><span class="sxs-lookup"><span data-stu-id="7a625-112">![OLEDB Destination Editor](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB Destination Editor")</span></span>  
  
7.  <span data-ttu-id="7a625-113">左側のメニューの [**マッピング**] をクリックして、[**マッピング**] ページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="7a625-113">Switch to the **Mappings** page by clicking **Mapping** on the menu on left.</span></span>  
  
8.  <span data-ttu-id="7a625-114">次の表に示すように、**入力**列と**変換先**列をマップします。</span><span class="sxs-lookup"><span data-stu-id="7a625-114">Map **input** and **destination** columns as shown in the following table.</span></span>  
  
     <span data-ttu-id="7a625-115">![OLEDB 変換先エディター - マッピング](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB 変換先エディター - マッピング")</span><span class="sxs-lookup"><span data-stu-id="7a625-115">![OLEDB Destination Editor - Mappings](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB Destination Editor - Mappings")</span></span>  
  
9. <span data-ttu-id="7a625-116">**_Status**または **_Source**列ではなく、入力列に **_Output**列を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a625-116">Confirm that you are using **_Output** columns for Input Columns, not the **_Status** or **_Source** columns.</span></span> <span data-ttu-id="7a625-117">**_Output**列には、DQS クレンジングの出力値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7a625-117">**_Output** columns contain the output values from DQS Cleansing.</span></span>  
  
10. <span data-ttu-id="7a625-118">[ **OK** ] をクリックして [ **OLE DB 変換先エディター** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7a625-118">Click **OK** to close the **OLE DB Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="7a625-119">データ フローは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="7a625-119">The data flow should like the following image.</span></span>  
  
     <span data-ttu-id="7a625-120">![完了したデータ フロー](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "完了したデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="7a625-120">![Completed Data Flow](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "Completed Data Flow")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="7a625-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="7a625-121">Next Step</span></span>  
 [<span data-ttu-id="7a625-122">タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアド プロシージャを実行する</span><span class="sxs-lookup"><span data-stu-id="7a625-122">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
