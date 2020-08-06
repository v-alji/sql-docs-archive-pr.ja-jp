---
title: チュートリアル:オフラインでのクイック グラフ レポートの作成 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51a9e648550a0108f47e3d93d75267ab0c1c24f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634279"
---
# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a><span data-ttu-id="dbf04-102">チュートリアル: オフラインでのクイック グラフ レポートの作成 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="dbf04-102">Tutorial: Create a Quick Chart Report Offline (Report Builder)</span></span>
  <span data-ttu-id="dbf04-103">このチュートリアルでは、ウィザードを使用して円グラフを作成し、少し変更して実行可能な操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-103">In this tutorial, you'll create a pie chart by using a wizard, and then you'll modify it a little, just to get an idea of what's possible.</span></span> <span data-ttu-id="dbf04-104">このチュートリアルは 2 つの異なる方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-104">You can do this tutorial two different ways.</span></span> <span data-ttu-id="dbf04-105">どちらの方法でも、次の図に示すような円グラフが同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-105">Both methods have the same outcome-a pie chart like the one in the following illustration:</span></span>

 <span data-ttu-id="dbf04-106">![実行ビューの "My First Pie Chart"](../media/rs-my1stpierunview.gif "実行ビューの最初の円グラフ")</span><span class="sxs-lookup"><span data-stu-id="dbf04-106">!["My First Pie Chart" in Run view](../media/rs-my1stpierunview.gif "My First Pie Chart in Run view")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbf04-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="dbf04-107">Prerequisites</span></span>
 <span data-ttu-id="dbf04-108">XML データを使用するか [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用するかにかかわらず、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] レポート ビルダーにアクセスできることが必要です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-108">Whether you use XML data or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, you need to have access to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder.</span></span> <span data-ttu-id="dbf04-109">スタンドアロン バージョン、またはレポート マネージャーや SharePoint サイトから利用できる ClickOnce バージョンを実行できます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-109">You can run the stand-alone version or the ClickOnce version available from Report Manager or a SharePoint site.</span></span> <span data-ttu-id="dbf04-110">ClickOnce バージョンでは、最初の手順であるレポートビルダーを開く方法のみが異なります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-110">Only the first step, how to open Report Builder, is different for ClickOnce versions.</span></span> <span data-ttu-id="dbf04-111">詳細については、「 [Install、Uninstall、およびレポートビルダー Support](../install-uninstall-and-report-builder-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-111">For more information, see [Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md).</span></span>

##  <a name="two-ways-to-do-this-tutorial"></a><a name="TwoWays"></a><span data-ttu-id="dbf04-112">このチュートリアルを実行する2つの方法</span><span class="sxs-lookup"><span data-stu-id="dbf04-112">Two Ways To Do This Tutorial</span></span>

-   [<span data-ttu-id="dbf04-113">XML データを使用して円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="dbf04-113">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

-   [<span data-ttu-id="dbf04-114">データを含む SQL クエリを使用して円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="dbf04-114">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

### <a name="using-xml-data-for-this-tutorial"></a><span data-ttu-id="dbf04-115">このチュートリアルでの XML データの使用</span><span class="sxs-lookup"><span data-stu-id="dbf04-115">Using XML data for this tutorial</span></span>
 <span data-ttu-id="dbf04-116">このトピックからコピーしてウィザードに貼り付けた XML データを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-116">You can use XML data that you copy from this topic and paste into the wizard.</span></span> <span data-ttu-id="dbf04-117">レポート サーバーまたは SharePoint 統合モードのレポート サーバーに接続している必要はありません。[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスへのアクセスも不要です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-117">You don't need to be connected to a report server or a report server in SharePoint integrated mode, and you don't need access to an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>

 [<span data-ttu-id="dbf04-118">XML データを使用して円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="dbf04-118">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

### <a name="using-a-transact-sql-query-that-contains-data-for-this-tutorial"></a><span data-ttu-id="dbf04-119">このチュートリアル用のデータを含む Transact-SQL クエリの使用</span><span class="sxs-lookup"><span data-stu-id="dbf04-119">Using a Transact-SQL query that contains data for this tutorial</span></span>
 <span data-ttu-id="dbf04-120">データを含むクエリをこのトピックからコピーし、ウィザードに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-120">You can copy a query with data included in it from this topic and paste it into the wizard.</span></span> <span data-ttu-id="dbf04-121">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスの名前と、任意のデータベースに読み取り専用でアクセスするのに十分な資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-121">You will need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="dbf04-122">チュートリアルのデータセット クエリでは、リテラル データを使用します。ただし、クエリは、レポート データセットに必要なメタデータを返すように、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスで処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-122">The dataset query in the tutorial uses literal data, but the query must be processed by an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to return the metadata that is required for a report dataset.</span></span>

 <span data-ttu-id="dbf04-123">[!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用する利点は、レポート ビルダーの他のすべてのチュートリアルで同じ方法が使用されているため、他のチュートリアルを実行するときに既に手順がわかっていることです。</span><span class="sxs-lookup"><span data-stu-id="dbf04-123">The advantage of using the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query is that all the other Report Builder tutorials use the same method, so when you do the other tutorials, you will already know what to do.</span></span>

 <span data-ttu-id="dbf04-124">[!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリの場合、他にもいくつか必要な前提条件があります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-124">The [!INCLUDE[tsql](../../../includes/tsql-md.md)] query does require a few other prerequisites.</span></span> <span data-ttu-id="dbf04-125">詳細については、「[チュートリアルの前提条件 &#40;レポート ビルダー&#41;](../report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-125">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

 [<span data-ttu-id="dbf04-126">データを含む SQL クエリを使用して円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="dbf04-126">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

## <a name="also-in-this-article"></a><span data-ttu-id="dbf04-127">この記事の他の内容</span><span class="sxs-lookup"><span data-stu-id="dbf04-127">Also in This Article</span></span>
 [<span data-ttu-id="dbf04-128">ウィザードを実行した後</span><span class="sxs-lookup"><span data-stu-id="dbf04-128">After You Run the Wizard</span></span>](#AfterWizard)

 [<span data-ttu-id="dbf04-129">次の内容</span><span class="sxs-lookup"><span data-stu-id="dbf04-129">What's Next</span></span>](#WhatsNext)

##  <a name="creating-the-pie-chart-with-xml-data"></a><a name="CreatePieChartXML"></a><span data-ttu-id="dbf04-130">XML データを使用して円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="dbf04-130">Creating the pie chart with XML data</span></span>

#### <a name="to-create-the-pie-chart-with-xml-data"></a><span data-ttu-id="dbf04-131">XML データを使用して円グラフを作成するには</span><span class="sxs-lookup"><span data-stu-id="dbf04-131">To create the pie chart with XML data</span></span>

1.  <span data-ttu-id="dbf04-132">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

     <span data-ttu-id="dbf04-133">[**はじめに**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-133">The **Getting Started** dialog box appears.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="dbf04-134">[**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-134">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>

2.  <span data-ttu-id="dbf04-135">左側のウィンドウで、[**レポート**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-135">In the left pane, verify that **Report** is selected.</span></span>

3.  <span data-ttu-id="dbf04-136">右ペインで、 **[グラフ ウィザード]** をクリックし、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-136">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="dbf04-137">**[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-137">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="dbf04-138">**[データ ソースへの接続の選択]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-138">In the **Choose a connection to a data source** page, click **New**.</span></span>

     <span data-ttu-id="dbf04-139">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-139">The **Data Source Properties** dialog box opens.</span></span>

6.  <span data-ttu-id="dbf04-140">データ ソースに任意の名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-140">You can name a data source anything you want.</span></span> <span data-ttu-id="dbf04-141">**[名前]** ボックスに、「 **MyPieChart**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-141">In the **Name** box, type **MyPieChart**.</span></span>

7.  <span data-ttu-id="dbf04-142">[**接続の種類の選択**] ボックスで、[XML] をクリックし**ます。**</span><span class="sxs-lookup"><span data-stu-id="dbf04-142">In the **Select connection type** box, click **XML.**</span></span>

8.  <span data-ttu-id="dbf04-143">[**資格情報**] タブで、[現在の Windows ユーザーを使用する] を選択し**ます。Kerberos 委任が必要な場合**は、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-143">Click the **Credentials** tab, select **Use current Windows user. Kerberos delegation may be required**, and then click **OK**.</span></span>

9. <span data-ttu-id="dbf04-144">**[データ ソースへの接続の選択]** ページで **[MyPieChart]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-144">In the **Choose a connection to a data source** page, click **MyPieChart**, and then click **Next**.</span></span>

10. <span data-ttu-id="dbf04-145">次のテキストをコピーし、[**クエリのデザイン**] ページの中央にある大きいボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-145">Copy the following text and paste it in the large box in the center of the **Design a query** page.</span></span>

    ```
    <Query>
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>
    <XmlData>
    <Root>
    <S Sales="150">
      <C FullName="Jae Pak" />
    </S>
    <S Sales="350">
      <C FullName="Jillian  Carson" />
    </S>
    <S Sales="250">
      <C FullName="Linda C Mitchell" />
    </S>
    <S Sales="500">
      <C FullName="Michael Blythe" />
    </S>
    <S Sales="450">
      <C FullName="Ranjit Varkey" />
    </S>
    </Root>
    </XmlData>
    </Query>
    ```

11. <span data-ttu-id="dbf04-146">(省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

12. <span data-ttu-id="dbf04-147">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-147">Click **Next**.</span></span>

13. <span data-ttu-id="dbf04-148">**[グラフの種類の選択]** ページで **[円]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-148">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

14. <span data-ttu-id="dbf04-149">**[グラフのフィールドの配置]** ページの **[使用できるフィールド]** ボックスで、**[Sales]** フィールドをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-149">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="dbf04-150">このフィールドは数値なので、 **[値]** ボックスに自動的に移動します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-150">Note that it automatically moves to the **Values** box, because it is a numerical value.</span></span>

15. <span data-ttu-id="dbf04-151">**[FullName]** フィールドを **[使用できるフィールド]** ボックスから **[カテゴリ]** ボックスにドラッグし (または、ダブルクリックすると **[カテゴリ]** ボックスに移動します)、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-151">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

16. <span data-ttu-id="dbf04-152">[**スタイルの選択**] ページでは、既定で [**海上**] が選択されています。</span><span class="sxs-lookup"><span data-stu-id="dbf04-152">In the **Choose a style** page, **Ocean** is selected by default.</span></span> <span data-ttu-id="dbf04-153">他のスタイルをクリックして、その違いを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-153">Click the other styles to see what they look like.</span></span>

17. <span data-ttu-id="dbf04-154">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-154">Click **Finish**.</span></span>

     <span data-ttu-id="dbf04-155">デザイン画面に、新しい円グラフ レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-155">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="dbf04-156">表示内容は見本です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-156">What you see is representational.</span></span> <span data-ttu-id="dbf04-157">凡例には販売員の名前ではなく Full Name 1、Full Name 2 などが示されており、円のスライスのサイズは正確ではありません。</span><span class="sxs-lookup"><span data-stu-id="dbf04-157">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="dbf04-158">これは、レポートがどのように表示されるか概要を見るためだけのものです。</span><span class="sxs-lookup"><span data-stu-id="dbf04-158">This is just to give you an idea of what your report will look like.</span></span>

18. <span data-ttu-id="dbf04-159">実際の円グラフを表示するには、リボンの **[ホーム]** タブで **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-159">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="dbf04-160">トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")</span><span class="sxs-lookup"><span data-stu-id="dbf04-160">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="creating-the-pie-chart-with-a-tsql-query"></a><a name="CreatePieQueryData"></a><span data-ttu-id="dbf04-161">[!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用して円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="dbf04-161">Creating the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query</span></span>

#### <a name="to-create-the-pie-chart-with-a-tsql-query-that-contains-data"></a><span data-ttu-id="dbf04-162">データを含む [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用して円グラフを作成するには</span><span class="sxs-lookup"><span data-stu-id="dbf04-162">To create the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query that contains data</span></span>

1.  <span data-ttu-id="dbf04-163">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-163">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

2.  <span data-ttu-id="dbf04-164">[**新しいレポートまたはデータセット**] ダイアログボックスで、左側のペインで [**レポート**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-164">In the **New report or dataset** dialog box, verify that **Report** is selected in the left pane.</span></span>

3.  <span data-ttu-id="dbf04-165">右ペインで、 **[グラフ ウィザード]** をクリックし、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-165">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="dbf04-166">**[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-166">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="dbf04-167">**[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-167">In the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="dbf04-168">ユーザー名とパスワードの入力が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-168">You may need to enter a user name and password.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="dbf04-169">適切な権限を持っている限り、選択するデータ ソースは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="dbf04-169">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="dbf04-170">データ ソースからはデータを取得しません。</span><span class="sxs-lookup"><span data-stu-id="dbf04-170">You will not be getting data from the data source.</span></span> <span data-ttu-id="dbf04-171">詳細については、「[チュートリアルの前提条件 &#40;レポート ビルダー&#41;](../report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-171">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

6.  <span data-ttu-id="dbf04-172">[**クエリのデザイン**] ページで、[**テキストとして編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-172">On the **Design a Query** page, click **Edit as Text**.</span></span>

7.  <span data-ttu-id="dbf04-173">次のクエリをクエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-173">Paste the following query into the query pane:</span></span>

    ```
    SELECT 150 AS Sales, 'Jae Pak' AS FullName 
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName 
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName 
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName 
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName 
    ```

8.  <span data-ttu-id="dbf04-174">(省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-174">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

9. <span data-ttu-id="dbf04-175">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-175">Click **Next**.</span></span>

10. <span data-ttu-id="dbf04-176">**[グラフの種類の選択]** ページで **[円]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-176">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

11. <span data-ttu-id="dbf04-177">**[グラフのフィールドの配置]** ページの **[使用できるフィールド]** ボックスで、**[Sales]** フィールドをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-177">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="dbf04-178">このフィールドは数値なので、 **[値]** ボックスに自動的に移動します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-178">Note that it automatically moves to the **Values** box, because it's a numerical value.</span></span>

12. <span data-ttu-id="dbf04-179">**[FullName]** フィールドを **[使用できるフィールド]** ボックスから **[カテゴリ]** ボックスにドラッグし (または、ダブルクリックすると **[カテゴリ]** ボックスに移動します)、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-179">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

13. <span data-ttu-id="dbf04-180">**[スタイルの選択]** ページでは、既定で [オーシャン] が選択されています。</span><span class="sxs-lookup"><span data-stu-id="dbf04-180">In the **Choose a style** page, Ocean is selected by default.</span></span> <span data-ttu-id="dbf04-181">他のスタイルをクリックして、その違いを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-181">Click the other styles to see what they look like.</span></span>

14. <span data-ttu-id="dbf04-182">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-182">Click **Finish**.</span></span>

     <span data-ttu-id="dbf04-183">デザイン画面に、新しい円グラフ レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-183">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="dbf04-184">表示内容は見本です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-184">What you see is representational.</span></span> <span data-ttu-id="dbf04-185">凡例には販売員の名前ではなく Full Name 1、Full Name 2 などが示されており、円のスライスのサイズは正確ではありません。</span><span class="sxs-lookup"><span data-stu-id="dbf04-185">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="dbf04-186">これは、レポートがどのように表示されるか概要を見るためだけのものです。</span><span class="sxs-lookup"><span data-stu-id="dbf04-186">This is just to give you an idea of what your report will look like.</span></span>

15. <span data-ttu-id="dbf04-187">実際の円グラフを表示するには、リボンの **[ホーム]** タブで **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-187">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="dbf04-188">トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")</span><span class="sxs-lookup"><span data-stu-id="dbf04-188">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="after-you-run-the-wizard"></a><a name="AfterWizard"></a><span data-ttu-id="dbf04-189">ウィザードを実行した後</span><span class="sxs-lookup"><span data-stu-id="dbf04-189">After You Run the Wizard</span></span>
 <span data-ttu-id="dbf04-190">円グラフ レポートが完成したので、操作してみます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-190">Now that you have your pie chart report, you can play with it.</span></span> <span data-ttu-id="dbf04-191">変更を続行するには、リボンの **[実行]** タブで **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbf04-191">On the **Run** tab of the Ribbon, click **Design**, so you can continue modifying it.</span></span>

### <a name="make-the-chart-bigger"></a><span data-ttu-id="dbf04-192">グラフの拡大</span><span class="sxs-lookup"><span data-stu-id="dbf04-192">Make the chart bigger</span></span>
 <span data-ttu-id="dbf04-193">円グラフを拡大するには、</span><span class="sxs-lookup"><span data-stu-id="dbf04-193">You may want the pie chart to be bigger.</span></span> <span data-ttu-id="dbf04-194">グラフ内の要素ではなくグラフをクリックして選択し、右下隅をドラッグしてサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-194">Click the chart, but not on any element in the chart, to select it and drag the lower-right corner to resize it.</span></span>

### <a name="add-a-report-title"></a><span data-ttu-id="dbf04-195">レポート タイトルの追加</span><span class="sxs-lookup"><span data-stu-id="dbf04-195">Add a report title</span></span>
 <span data-ttu-id="dbf04-196">グラフ上部の **[グラフのタイトル]** というテキストを選択し、「 **Sales Pie Chart**」などのタイトルを入力します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-196">Select the words **Chart title** at the top of the chart, and then type a title, such as **Sales Pie Chart**.</span></span>

### <a name="add-percentages"></a><span data-ttu-id="dbf04-197">パーセンテージの追加</span><span class="sxs-lookup"><span data-stu-id="dbf04-197">Add percentages</span></span>

##### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="dbf04-198">円グラフにパーセンテージをラベルとして表示するには</span><span class="sxs-lookup"><span data-stu-id="dbf04-198">To display percentage values as labels on a pie chart</span></span>

1.  <span data-ttu-id="dbf04-199">円グラフを右クリックし、[**データラベルの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-199">Right-click on the pie chart and select **Show Data Labels**.</span></span> <span data-ttu-id="dbf04-200">円グラフの各スライス内にデータ ラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-200">The data labels should appear within each slice on the pie chart.</span></span>

2.  <span data-ttu-id="dbf04-201">ラベルを右クリックし、[**系列ラベルのプロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-201">Right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="dbf04-202">**[系列ラベルのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-202">The **Series Label Properties** dialog box appears.</span></span>

3.  <span data-ttu-id="dbf04-203">`#PERCENT{P0}`[**ラベルデータ**] オプションに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dbf04-203">Type `#PERCENT{P0}` for the **Label data** option.</span></span>

     <span data-ttu-id="dbf04-204">`{P0}` を指定すると、小数点以下を含まないパーセンテージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-204">The `{P0}` gives you the percentage without decimal places.</span></span> <span data-ttu-id="dbf04-205">「`#PERCENT`」とだけ入力すると、小数点以下 2 桁を含む数値になります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-205">If you type just `#PERCENT`, your numbers will have two decimal places.</span></span> <span data-ttu-id="dbf04-206">`#PERCENT` は計算または関数を実行するキーワードで、他にも多数あります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-206">`#PERCENT` is a keyword that performs a calculation or function for you; there are many others.</span></span>

 <span data-ttu-id="dbf04-207">グラフのラベルと凡例をカスタマイズする方法の詳細については、「[円グラフへのパーセンテージの表示 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)」および「[凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-207">For more information about customizing chart labels and legends, see [Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) and [Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md).</span></span>

 <span data-ttu-id="dbf04-208">トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")</span><span class="sxs-lookup"><span data-stu-id="dbf04-208">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="whats-next"></a><a name="WhatsNext"></a><span data-ttu-id="dbf04-209">次は何ですか?</span><span class="sxs-lookup"><span data-stu-id="dbf04-209">What's Next?</span></span>
 <span data-ttu-id="dbf04-210">レポート ビルダーでレポートを初めて自分で作成したので、他のチュートリアルに取り組んで独自のデータからレポートを作成する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="dbf04-210">Now that you have created your first report in Report Builder, you are ready to try the other tutorials and to start creating reports from your own data.</span></span> <span data-ttu-id="dbf04-211">レポートビルダーを実行するには、実際にデータソースに接続する*接続文字列*を使用して、データベースなどのデータソースにアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-211">To run Report Builder, you need permission to access your data sources, such as databases, with a *connection string*, which actually connects you to the data source.</span></span> <span data-ttu-id="dbf04-212">システム管理者がこの情報を保持し、ユーザーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-212">Your system administrator will have this information and can set you up.</span></span>

 <span data-ttu-id="dbf04-213">他のチュートリアルを実行するには、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスの名前と、任意のデータベースに読み取り専用でアクセスするのに十分な資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-213">To work through the other tutorials, you need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="dbf04-214">これもシステム管理者が設定できます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-214">Your system administrator can also set that up for you.</span></span>

 <span data-ttu-id="dbf04-215">最後に、レポートをレポート サーバーまたはレポート サーバーと統合されている SharePoint サイトに保存するには、URL と権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-215">Finally, to save your reports to a report server or a SharePoint site that is integrated with a report server, you need the URL and permissions.</span></span> <span data-ttu-id="dbf04-216">作成したレポートは自分のコンピューターから直接実行できますが、レポート サーバーまたは SharePoint サイトから実行するとレポートの機能が増えます。</span><span class="sxs-lookup"><span data-stu-id="dbf04-216">You can run any report you create directly from your computer, but reports have more functionality when run from the report server or SharePoint site.</span></span> <span data-ttu-id="dbf04-217">自分のレポートまたはその他のレポートをパブリッシュ元のレポート サーバーまたは SharePoint サイトから実行する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="dbf04-217">You need permissions to run your reports or others from the report server or SharePoint site where they are published.</span></span> <span data-ttu-id="dbf04-218">アクセス権を取得するには、システム管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-218">Talk to your system administrator to obtain access.</span></span>

 <span data-ttu-id="dbf04-219">開始する前に、いくつかの概念や用語について確認しておくと役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-219">It may help to read about some of the concepts and terms before you get started.</span></span> <span data-ttu-id="dbf04-220">詳細については、「[レポート作成の概念 &#40;レポートビルダーと SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-220">For more information, see [Report Authoring Concepts &#40;Report Builder and SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="dbf04-221">また、レポートを初めて自分で作成する前に、計画の時間を取ってください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-221">Also, spend some time planning, before you create your first report.</span></span> <span data-ttu-id="dbf04-222">時間を費やす価値があります。</span><span class="sxs-lookup"><span data-stu-id="dbf04-222">It will be time well spent.</span></span> <span data-ttu-id="dbf04-223">詳細については、「 [Planning a Report &#40;レポートビルダー&#41;](../report-design/planning-a-report-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf04-223">For more information, see [Planning a Report &#40;Report Builder&#41;](../report-design/planning-a-report-report-builder.md).</span></span>

 <span data-ttu-id="dbf04-224">トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")</span><span class="sxs-lookup"><span data-stu-id="dbf04-224">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

## <a name="see-also"></a><span data-ttu-id="dbf04-225">参照</span><span class="sxs-lookup"><span data-stu-id="dbf04-225">See Also</span></span>
 <span data-ttu-id="dbf04-226">[チュートリアル &#40;](../report-builder-tutorials.md) [SQL Server 2014 でのレポートビルダー](report-builder-in-sql-server-2016.md)&#41;レポートビルダー</span><span class="sxs-lookup"><span data-stu-id="dbf04-226">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder-in-sql-server-2016.md)</span></span>


