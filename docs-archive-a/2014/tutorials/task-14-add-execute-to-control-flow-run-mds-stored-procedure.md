---
title: 'タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアドプロシージャを実行する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da8e80b25706c40e749fc364baeb578681e76b42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714841"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a><span data-ttu-id="7e34d-102">タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアド プロシージャを実行する</span><span class="sxs-lookup"><span data-stu-id="7e34d-102">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>
  <span data-ttu-id="7e34d-103">MDS のステージング テーブルにデータを読み込んだ後、ステージングから MDS データベース内の適切なテーブルにデータを読み込むために、そのテーブルに関連付けられているストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-103">After loading data into the staging tables of MDS, you run a stored procedure associated with that table to load the data from staging into the appropriate tables in the MDS database.</span></span> <span data-ttu-id="7e34d-104">このストアド プロシージャには、2 つの必須パラメーター LogFlag および VersionName を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e34d-104">This stored procedure has two required parameters that you need to pass: LogFlag and VersionName.</span></span> <span data-ttu-id="7e34d-105">LogFlag はトランザクションがステージング処理中にログ記録されるかどうかを指定し、VersionName はモデルのバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-105">LogFlag specifies whether transactions are logged during the staging process and VersionName represents the version of the model.</span></span> <span data-ttu-id="7e34d-106">詳細については、「[ステージングストアドプロシージャ](https://msdn.microsoft.com/library/hh231028.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e34d-106">See [Staged Stored Procedure](https://msdn.microsoft.com/library/hh231028.aspx) topic for more details.</span></span>

 <span data-ttu-id="7e34d-107">ここでは、適切な MDS テーブルにステージング データを読み込むためのストアド プロシージャを起動する制御フローに SQL 実行タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-107">In this task, you add the Execute SQL Task to the control flow to invoke the stored procedure to load the staged data into appropriate MDS tables.</span></span>

1.  <span data-ttu-id="7e34d-108">次に、[**制御フロー** ] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="7e34d-108">Now, switch to the **Control Flow** tab.</span></span>

2.  <span data-ttu-id="7e34d-109">**SSIS ツールボックス**から [**制御フロー** ] タブに**SQL 実行タスク**をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="7e34d-109">Drag-drop **Execute SQL Task** from the **SSIS Toolbox** to the **Control Flow** tab.</span></span>

3.  <span data-ttu-id="7e34d-110">[**制御フロー** ] タブで [ **SQL 実行タスク**] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e34d-110">Right-click **Execute SQL Task** in the **Control Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="7e34d-111">「**データを MDS に読み込むためのトリガーストアドプロシージャ**」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-111">Type **Trigger Stored Procedure to Load Data into MDS** and press **ENTER**.</span></span>

4.  <span data-ttu-id="7e34d-112">緑色のコネクタを使用して**データを読み込むストアドプロシージャをトリガー**するために、 **Supplier データの受信、クレンジング、照合、および curate**を接続します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-112">Connect **Receive, Cleanse, Match, and Curate Supplier Data** to **Trigger Stored Procedure to Load Data** using the green connector.</span></span>

     <span data-ttu-id="7e34d-113">![SQL 実行タスクへの接続](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "SQL 実行タスクへの接続")</span><span class="sxs-lookup"><span data-stu-id="7e34d-113">![Connect to Execute SQL Task](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "Connect to Execute SQL Task")</span></span>

5.  <span data-ttu-id="7e34d-114">[**変数**] ウィンドウで、次の設定を使用して2つの新しい変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-114">Using the **Variables** window, add two new variables with the following settings.</span></span> <span data-ttu-id="7e34d-115">[**変数**] ウィンドウが表示されない場合は、メニューバーの [ **SSIS** ] をクリックし、[**変数**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e34d-115">If you do not see the **Variables** window, click **SSIS** on the menu bar and click **Variables**.</span></span>

    |<span data-ttu-id="7e34d-116">名前</span><span class="sxs-lookup"><span data-stu-id="7e34d-116">Name</span></span>|<span data-ttu-id="7e34d-117">データ型</span><span class="sxs-lookup"><span data-stu-id="7e34d-117">Data Type</span></span>|<span data-ttu-id="7e34d-118">値</span><span class="sxs-lookup"><span data-stu-id="7e34d-118">Value</span></span>|
    |----------|---------------|-----------|
    |<span data-ttu-id="7e34d-119">LogFlag</span><span class="sxs-lookup"><span data-stu-id="7e34d-119">LogFlag</span></span>|<span data-ttu-id="7e34d-120">Int32</span><span class="sxs-lookup"><span data-stu-id="7e34d-120">Int32</span></span>|<span data-ttu-id="7e34d-121">1</span><span class="sxs-lookup"><span data-stu-id="7e34d-121">1</span></span>|
    |<span data-ttu-id="7e34d-122">VersionName</span><span class="sxs-lookup"><span data-stu-id="7e34d-122">VersionName</span></span>|<span data-ttu-id="7e34d-123">String</span><span class="sxs-lookup"><span data-stu-id="7e34d-123">String</span></span>|<span data-ttu-id="7e34d-124">VERSION_1</span><span class="sxs-lookup"><span data-stu-id="7e34d-124">VERSION_1</span></span>|

     <span data-ttu-id="7e34d-125">![[SSIS 変数] ウィンドウ](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "[SSIS 変数] ウィンドウ")</span><span class="sxs-lookup"><span data-stu-id="7e34d-125">![SSIS Variables Window](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS Variables Window")</span></span>

6.  <span data-ttu-id="7e34d-126">[トリガーストアドプロシージャ] をダブルクリックして、 **MDS にデータを読み込み**ます。</span><span class="sxs-lookup"><span data-stu-id="7e34d-126">Double-click **Trigger Stored Procedure to Load Data into MDS**.</span></span>

7.  <span data-ttu-id="7e34d-127">[ **SQL 実行タスクエディター** ] ダイアログボックスで、[(ローカル)] を選択し**ます。MDS** (または**localhost。\*\*\*\*接続**用の MDS)。</span><span class="sxs-lookup"><span data-stu-id="7e34d-127">In the **Execute SQL Task Editor** dialog box, select **(local).MDS** (or **localhost.MDS**) for **Connection**.</span></span>

8.  <span data-ttu-id="7e34d-128">「 **EXEC [stg]」と入力します。 [udp_Supplier_Leaf]?,?,?**</span><span class="sxs-lookup"><span data-stu-id="7e34d-128">Type **EXEC [stg].[udp_Supplier_Leaf] ?, ?, ?**</span></span> <span data-ttu-id="7e34d-129">**SQL ステートメント**の場合。</span><span class="sxs-lookup"><span data-stu-id="7e34d-129">for **SQL Statement**.</span></span> <span data-ttu-id="7e34d-130">SQL Server Management Studio を使用して名前を確認できます。</span><span class="sxs-lookup"><span data-stu-id="7e34d-130">You can verify the name by using SQL Server Management Studio.</span></span>

     <span data-ttu-id="7e34d-131">![[SQL 実行エディター] ダイアログ ボックス - [全般設定]](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "[SQL 実行エディター] ダイアログ ボックス - [全般設定]")</span><span class="sxs-lookup"><span data-stu-id="7e34d-131">![Execute SQL Editor Dialog Box - General Settings](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "Execute SQL Editor Dialog Box - General Settings")</span></span>

9. <span data-ttu-id="7e34d-132">左側のメニューの [**パラメーターマッピング**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e34d-132">Click **Parameter Mapping** from the menu on left.</span></span>

10. <span data-ttu-id="7e34d-133">[**パラメーターマッピング**] ページで、[**追加**] をクリックしてマッピングを追加します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-133">In the **Parameter Mapping** page, click **Add** to add a mapping.</span></span> <span data-ttu-id="7e34d-134">ドロップダウン リストに値が正しく表示されるようにウィンドウを最大化し、列のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-134">Maximize the window and resize columns so that you can see values in drop-down lists properly.</span></span>

11. <span data-ttu-id="7e34d-135">**変数名**のドロップダウンリストから [ **User:: versionname** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-135">Select **User::VersionName** from the drop-down list for the **Variable Name**.</span></span>

12. <span data-ttu-id="7e34d-136">[**データ型**] で [ **NVARCHAR** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-136">Select **NVARCHAR** for **Data Type**.</span></span>

13. <span data-ttu-id="7e34d-137">**パラメーター名**として「 **0** 」 (ゼロ) を入力します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-137">Type **0** (zero) for **Parameter Name**.</span></span>

14. <span data-ttu-id="7e34d-138">前の 4 つの手順を繰り返して、さらに 2 つの変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="7e34d-138">Repeat the previous four steps to add two more variables.</span></span>

    |<span data-ttu-id="7e34d-139">変数名</span><span class="sxs-lookup"><span data-stu-id="7e34d-139">Variable Name</span></span>|<span data-ttu-id="7e34d-140">データ型 (重要)</span><span class="sxs-lookup"><span data-stu-id="7e34d-140">Data Type (important)</span></span>|<span data-ttu-id="7e34d-141">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="7e34d-141">Parameter Name</span></span>|
    |-------------------|-----------------------------|--------------------|
    |<span data-ttu-id="7e34d-142">User::LogFlag</span><span class="sxs-lookup"><span data-stu-id="7e34d-142">User::LogFlag</span></span>|<span data-ttu-id="7e34d-143">LONG</span><span class="sxs-lookup"><span data-stu-id="7e34d-143">LONG</span></span>|<span data-ttu-id="7e34d-144">1</span><span class="sxs-lookup"><span data-stu-id="7e34d-144">1</span></span>|
    |<span data-ttu-id="7e34d-145">User::BatchTag</span><span class="sxs-lookup"><span data-stu-id="7e34d-145">User::BatchTag</span></span>|<span data-ttu-id="7e34d-146">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="7e34d-146">NVARCHAR</span></span>|<span data-ttu-id="7e34d-147">2</span><span class="sxs-lookup"><span data-stu-id="7e34d-147">2</span></span>|

     <span data-ttu-id="7e34d-148">![SQL 実行タスク エディター - パラメーター マッピング](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "SQL 実行タスク エディター - パラメーター マッピング")</span><span class="sxs-lookup"><span data-stu-id="7e34d-148">![Execute SQL Task Editor - Parameter Mapping](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "Execute SQL Task Editor - Parameter Mapping")</span></span>

15. <span data-ttu-id="7e34d-149">[ **OK** ] をクリックして [ **SQL 実行エディター** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7e34d-149">Click **OK** to close the **Execute SQL Editor** dialog box.</span></span>

## <a name="next-step"></a><span data-ttu-id="7e34d-150">次の手順</span><span class="sxs-lookup"><span data-stu-id="7e34d-150">Next Step</span></span>
 [<span data-ttu-id="7e34d-151">タスク 15: SSIS プロジェクトをビルドおよび実行する</span><span class="sxs-lookup"><span data-stu-id="7e34d-151">Task 15: Building and Running the SSIS Project</span></span>](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)


