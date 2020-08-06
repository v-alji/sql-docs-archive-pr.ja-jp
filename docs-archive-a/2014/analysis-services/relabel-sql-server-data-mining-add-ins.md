---
title: ラベルの再付け (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
ms.openlocfilehash: a625676f60e2da32e19b85a94002b51eeb9ac816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641253"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a><span data-ttu-id="a082d-102">ラベルの変更 (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="a082d-102">Relabel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="a082d-103">![ラベルの変更ツールの Office 13 アイコン](media/dm13-relabel.gif "ラベルの変更ツールの Office 13 アイコン")</span><span class="sxs-lookup"><span data-stu-id="a082d-103">![Office 13 icon for Relabel tool](media/dm13-relabel.gif "Office 13 icon for Relabel tool")</span></span>

 <span data-ttu-id="a082d-104">Excel 用のデータ マイニング クライアントでは、データの新しいラベルを作成して、分析結果を理解しやすくできます。</span><span class="sxs-lookup"><span data-stu-id="a082d-104">The Data Mining Client for Excel helps you create new labels for data to make it easier to understand the results of analysis.</span></span>

 <span data-ttu-id="a082d-105">ラベルを変更する理由は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a082d-105">Reasons for relabeling include:</span></span>

-   <span data-ttu-id="a082d-106">データがコード化された結果を含んでいる場合 (たとえば 1 は男性、2 は女性など)。</span><span class="sxs-lookup"><span data-stu-id="a082d-106">The data includes results that were coded, such as 1 for Male and 2 for Female.</span></span>

-   <span data-ttu-id="a082d-107">バケット化した数値の範囲に、わかりやすい名前を付ける場合。</span><span class="sxs-lookup"><span data-stu-id="a082d-107">You are bucketing numeric values and want to give the ranges a descriptive name.</span></span>

-   <span data-ttu-id="a082d-108">長い名前を簡単にする場合。</span><span class="sxs-lookup"><span data-stu-id="a082d-108">You want to simplify long names.</span></span>

## <a name="using-the-relabel-wizard"></a><span data-ttu-id="a082d-109">ラベルの変更ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="a082d-109">Using the Relabel Wizard</span></span>

1.  <span data-ttu-id="a082d-110">[**データマイニング**] リボンで、[**クリーン**] をクリックし、[**再ラベル**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a082d-110">In the **Data Mining** ribbon, click **Clean** and then select **Re-Label**.</span></span>

2.  <span data-ttu-id="a082d-111">Select the table or data range that has the data you want to fix.修正するデータが含まれているテーブルまたはデータ範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="a082d-111">Select the table or data range that has the data you want to fix.</span></span>

3.  <span data-ttu-id="a082d-112">ウィザードの [**ラベル**の変更] ページで、ドロップダウンリストから列を選択するか、[**データサンプル**] ペインの列をクリックして、1つの列を選択します。</span><span class="sxs-lookup"><span data-stu-id="a082d-112">In the **Re-label** page of the wizard, select a single column, either by choosing the column from the dropdown list, or by clicking the column in the **Data samples** pane.</span></span>

     <span data-ttu-id="a082d-113">[**データサンプル**] ペインには、約50行のデータのみが表示されますが、値が適切に分散されていることを確認するためにサンプリングされます。</span><span class="sxs-lookup"><span data-stu-id="a082d-113">The **Data samples** pane only shows about 50 rows of data, but they are sampled to ensure that you see a good spread of values.</span></span>

     <span data-ttu-id="a082d-114">[**カウント**] の列ヘッダーをクリックすると、各値のカウント順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="a082d-114">Click the column header for **Count** to sort by the count of each value.</span></span>

     <span data-ttu-id="a082d-115">また、**元のラベル**で並べ替えることもできます。これは、最大値または最小値を最初に再ラベルする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a082d-115">You can also sort by **Original Labels**, which is handy if you want to re-label all the highest or lowest values first.</span></span>

4.  <span data-ttu-id="a082d-116">ウィザードの [**ラベル**の変更] ページで、[**元のラベル**] 列の値を確認し、それらをグループ化または編集する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="a082d-116">In the **Re-label** data page of the wizard, review the values in the **Original Labels** column, and decide how you want to group or edit them.</span></span>

5.  <span data-ttu-id="a082d-117">新しい**ラベル**の下の行に新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a082d-117">Type a new value into the row under **New Labels**.</span></span> <span data-ttu-id="a082d-118">値は、既存の値の一覧から選択できます。</span><span class="sxs-lookup"><span data-stu-id="a082d-118">You can also choose a value from the list of existing values.</span></span> <span data-ttu-id="a082d-119">新しい値は、入力した直後から再利用に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a082d-119">As you type new values, they become available for re-use right away.</span></span>

6.  <span data-ttu-id="a082d-120">十分な行を入力したら、[**次へ**] をクリックし、[**変換先の選択**] ページで、再ラベル付けされたデータを保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="a082d-120">When you have entered enough rows, click **Next**, and on the **Select Destination** page, choose where you'll save the relabeled data.</span></span>

    -   <span data-ttu-id="a082d-121">**[現在のワークシートに新しい列として追加する]**</span><span class="sxs-lookup"><span data-stu-id="a082d-121">**Add as a new column to the current worksheet**</span></span>

         <span data-ttu-id="a082d-122">新しい値が格納されている列をテーブルに追加する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="a082d-122">Click to add a new column to the table that contains the new values.</span></span>

    -   <span data-ttu-id="a082d-123">**[変更されたシートのデータを新しいワークシートにコピーする]**</span><span class="sxs-lookup"><span data-stu-id="a082d-123">**Copy sheet data with changes to a new worksheet**</span></span>

         <span data-ttu-id="a082d-124">更新されたデータが格納された新しいワークシートを作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="a082d-124">Click to create a new worksheet that contains the updated data.</span></span>

    -   <span data-ttu-id="a082d-125">**[配置データを変更する]**</span><span class="sxs-lookup"><span data-stu-id="a082d-125">**Change data in place**</span></span>

         <span data-ttu-id="a082d-126">元データを新しい値に置き換える場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="a082d-126">Click to replace the original data with the new values.</span></span>

## <a name="see-also"></a><span data-ttu-id="a082d-127">参照</span><span class="sxs-lookup"><span data-stu-id="a082d-127">See Also</span></span>
 [<span data-ttu-id="a082d-128">データの探索とクリーニング</span><span class="sxs-lookup"><span data-stu-id="a082d-128">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)


