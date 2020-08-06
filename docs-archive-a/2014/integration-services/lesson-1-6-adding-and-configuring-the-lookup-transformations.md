---
title: '手順 6 : 参照変換の追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96b0a848508c19eb24cf1538244a39fcec57361a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641089"
---
# <a name="step-6-adding-and-configuring-the-lookup-transformations"></a><span data-ttu-id="cd0dc-102">手順 6:参照変換の追加と構成</span><span class="sxs-lookup"><span data-stu-id="cd0dc-102">Step 6: Adding and Configuring the Lookup Transformations</span></span>
  <span data-ttu-id="cd0dc-103">ソース ファイルからデータを取り出すフラット ファイルを構成したら、次は、 **CurrencyKey** および **DateKey**の値を取得する際に必要な参照変換を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-103">After you have configured the Flat File source to extract data from the source file, the next task is to define the Lookup transformations needed to obtain the values for the **CurrencyKey** and **DateKey**.</span></span> <span data-ttu-id="cd0dc-104">参照変換は、指定の入力列のデータを参照データセットの列に結合することにより、参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-104">A Lookup transformation performs a lookup by joining data in the specified input column to a column in a reference dataset.</span></span> <span data-ttu-id="cd0dc-105">参照データセットは、既存のテーブル、既存のビュー、新しいテーブル、または SQL ステートメントの結果のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-105">The reference dataset can be an existing table or view, a new table, or the result of an SQL statement.</span></span> <span data-ttu-id="cd0dc-106">このチュートリアルでは、参照変換は、OLE DB 接続マネージャーを使用して、参照データセットのソースとなるデータを含むデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-106">In this tutorial, the Lookup transformation uses an OLE DB connection manager to connect to the database that contains the data that is the source of the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd0dc-107">参照データセットを含むキャッシュに接続するように参照変換を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-107">You can also configure the Lookup transformation to connect to a cache that contains the reference dataset.</span></span> <span data-ttu-id="cd0dc-108">詳細については、「 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-108">For more information, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="cd0dc-109">このチュートリアルでは、次の 2 つの参照変換コンポーネントをパッケージに追加し、構成します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-109">For this tutorial, you will add and configure the following two Lookup transformation components to the package:</span></span>  
  
-   <span data-ttu-id="cd0dc-110">**DimCurrency** ディメンションの **CurrencyKey** 列から取得される値を参照する変換コンポーネント。 **CurrencyID** 列の値と一致する値をフラット ファイルから探します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-110">One transformation to perform a lookup of values from the **CurrencyKey** column of the **DimCurrency** dimension table based on matching **CurrencyID** column values from the flat file.</span></span>  
  
-   <span data-ttu-id="cd0dc-111">**DimDate** ディメンションの **DateKey** 列から取得される値を参照する変換コンポーネント。 **CurrencyDate** 列の値と一致する値をフラット ファイルから探します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-111">One transformation to perform a lookup of values from the **DateKey** column of the **DimDate** dimension table based on matching **CurrencyDate** column values from the flat file.</span></span>  
  
 <span data-ttu-id="cd0dc-112">どちらの場合も、以前に作成した OLE DB 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-112">In both cases, the Lookup transformation will utilize the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a><span data-ttu-id="cd0dc-113">Lookup Currency Key 変換を追加および構成するには</span><span class="sxs-lookup"><span data-stu-id="cd0dc-113">To add and configure the Lookup Currency Key transformation</span></span>  
  
1.  <span data-ttu-id="cd0dc-114">[ **SSIS ツールボックス**] で **[共通**] を展開し、[**参照**] を [**データフロー** ] タブのデザイン画面にドラッグします。 " **Extract Sample Currency" データ**ソースのすぐ下に [参照] を配置します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-114">In the **SSIS Toolbox**, expand **Common**, and then drag **Lookup** onto the design surface of the **Data Flow** tab. Place Lookup directly below the **Extract Sample Currency Data** source.</span></span>  
  
2.  <span data-ttu-id="cd0dc-115">**[Extract Sample Currency Data]** フラット ファイル ソースをクリックします。次に、緑色の矢印を、新しく追加した **[参照]** 変換までドラッグして、これら 2 つのコンポーネントを接続します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-115">Click the **Extract Sample Currency Data** flat file source and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="cd0dc-116">**[データ フロー]** デザイン画面で、 **[参照]** 変換の **[参照]** をクリックし、名前を「 **Lookup Currency Key**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-116">On the **Data Flow** design surface, click **Lookup** in the **Lookup** transformation, and change the name to **Lookup Currency Key**.</span></span>  
  
4.  <span data-ttu-id="cd0dc-117">**Lookup Currency Key** 変換をダブルクリックし、参照変換エディターを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-117">Double-click the **Lookup CurrencyKey** transformation to display the Lookup Transformation Editor.</span></span>  
  
5.  <span data-ttu-id="cd0dc-118">**[全般]** ページで、以下の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-118">On the **General** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="cd0dc-119">**[フル キャッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-119">Select **Full cache**.</span></span>  
  
    2.  <span data-ttu-id="cd0dc-120">**[接続の種類]** 領域で、 **[OLE DB 接続マネージャー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-120">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
6.  <span data-ttu-id="cd0dc-121">**[接続]** ページで、以下の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-121">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="cd0dc-122">**[OLE DB 接続マネージャー]** ダイアログ ボックスに、 **localhost.AdventureWorksDW2012** が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-122">In the **OLE DB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="cd0dc-123">**[SQL クエリの結果を使用する]** をクリックし、次の SQL ステートメントを入力するかコピーします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-123">Select **Use results of an SQL query**, and then type or copy the following SQL statement:</span></span>  
  
        ```  
        select * from (select * from [dbo].[DimCurrency]) as refTable  
        where [refTable].[CurrencyAlternateKey] = 'ARS'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'AUD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'BRL'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CAD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CNY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'DEM'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'EUR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'FRF'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'GBP'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'JPY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'MXN'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'SAR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'USD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'VEB'  
        ```  
  
7.  <span data-ttu-id="cd0dc-124">**[列]** ページで、以下の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-124">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="cd0dc-125">**[使用できる入力列]** パネルの **[CurrencyID]** を **[使用できる参照列]** パネルにドラッグし、 **[CurrencyAlternateKey]** の上にドロップします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-125">In the **Available Input Columns** panel, drag **CurrencyID** to the **Available Lookup Columns** panel and drop it on **CurrencyAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="cd0dc-126">**[使用できる参照列]** ボックスの一覧で、 **[CurrencyKey]** の左側のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-126">In the **Available Lookup Columns** list, select the check box to the left of **CurrencyKey**.</span></span>  
  
8.  <span data-ttu-id="cd0dc-127">**[OK]** をクリックして、 **[データ フロー]** デザイン画面に戻ります。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-127">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
9. <span data-ttu-id="cd0dc-128">[Lookup Currency Key] 変換を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-128">Right-click the Lookup Currency Key transformation, click **Properties**.</span></span>  
  
10. <span data-ttu-id="cd0dc-129">プロパティウィンドウで、 `LocaleID` プロパティが**英語 (米国)** に設定され、 **defaultcodepage**プロパティが**1252**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-129">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a><span data-ttu-id="cd0dc-130">Lookup Date Key 変換を追加および構成するには</span><span class="sxs-lookup"><span data-stu-id="cd0dc-130">To add and configure the  Lookup DateKey transformation</span></span>  
  
1.  <span data-ttu-id="cd0dc-131">**[SSIS ツールボックス]** で **[参照]** をクリックし、 **[データ フロー]** デザイン画面上にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-131">In the **SSIS Toolbox**, drag **Lookup** onto the **Data Flow** design surface.</span></span> <span data-ttu-id="cd0dc-132">[参照] を **[Lookup Currency Key]** のすぐ下に配置します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-132">Place Lookup directly below the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="cd0dc-133">**[Lookup Currency Key]** 変換をクリックします。緑色の矢印を、新しく追加した **[参照]** 変換までドラッグして、これら 2 つのコンポーネントを接続します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-133">Click the **Lookup Currency Key** transformation and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="cd0dc-134">**[入出力の選択]** ダイアログ ボックスの **[出力]** ボックスの一覧で **[参照の一致出力]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-134">In the **Input Output Selection** dialog box, click **Lookup Match Output** in the **Output** list box, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="cd0dc-135">**[データ フロー]** デザイン画面で、新しく追加した **[参照]** 変換の **[参照]** をクリックし、名前を「 **Lookup Date Key**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-135">On the **Data Flow** design surface, click **Lookup** in the newly added **Lookup** transformation, and change the name to **Lookup Date Key**.</span></span>  
  
5.  <span data-ttu-id="cd0dc-136">**[Lookup Date Key]** 変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-136">Double-click the **Lookup Date Key** transformation.</span></span>  
  
6.  <span data-ttu-id="cd0dc-137">**[全般]** ページで、 **[部分キャッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-137">On the **General** page, select **Partial cache**.</span></span>  
  
7.  <span data-ttu-id="cd0dc-138">**[接続]** ページで、以下の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-138">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="cd0dc-139">**[OLEDB 接続マネージャー]** ダイアログ ボックスに、 **localhost.AdventureWorksDW2012** が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-139">In the **OLEDB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="cd0dc-140">**[テーブルまたはビューを使用]** ボックスで、 **[dbo].[DimDate]** を選択するか、または入力します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-140">In the **Use a table or view** box, type or select **[dbo].[DimDate]**.</span></span>  
  
8.  <span data-ttu-id="cd0dc-141">**[列]** ページで、以下の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-141">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="cd0dc-142">**[使用できる入力列]** パネルの **[CurrencyDate]** を **[使用できる参照列]** パネルにドラッグし、 **[FullDateAlternateKey]** の上にドロップします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-142">In the **Available Input Columns** panel, drag **CurrencyDate** to the **Available Lookup Columns** panel and drop it on **FullDateAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="cd0dc-143">**[使用できる参照列]** ボックスの一覧で、 **[DateKey]** の左側のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-143">In the **Available Lookup Columns** list, select the check box to the left of **DateKey**.</span></span>  
  
9. <span data-ttu-id="cd0dc-144">**[詳細設定]** ページで、キャッシュ オプションを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-144">On the **Advanced** page, review the caching options.</span></span>  
  
10. <span data-ttu-id="cd0dc-145">**[OK]** をクリックして、 **[データ フロー]** デザイン画面に戻ります。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-145">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
11. <span data-ttu-id="cd0dc-146">[Lookup Date Key] 変換を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-146">Right-click the Lookup Date Key transformation and click **Properties.**</span></span>  
  
12. <span data-ttu-id="cd0dc-147">プロパティウィンドウで、 `LocaleID` プロパティが**英語 (米国)** に設定され、 **defaultcodepage**プロパティが**1252**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd0dc-147">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="cd0dc-148">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="cd0dc-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="cd0dc-149">手順 7:OLE DB 変換先の追加と構成</span><span class="sxs-lookup"><span data-stu-id="cd0dc-149">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd0dc-150">参照</span><span class="sxs-lookup"><span data-stu-id="cd0dc-150">See Also</span></span>  
 [<span data-ttu-id="cd0dc-151">参照変換</span><span class="sxs-lookup"><span data-stu-id="cd0dc-151">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
