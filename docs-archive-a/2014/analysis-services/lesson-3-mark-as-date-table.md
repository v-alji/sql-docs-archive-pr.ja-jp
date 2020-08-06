---
title: 'レッスン 4: 日付テーブルとしてマークする |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
ms.openlocfilehash: c3ccc57d770d954e9523196d2393fa9dc2ada5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642392"
---
# <a name="lesson-4-mark-as-date-table"></a><span data-ttu-id="484dd-102">レッスン 4:日付テーブルとしてマーク</span><span class="sxs-lookup"><span data-stu-id="484dd-102">Lesson 4: Mark as Date Table</span></span>
  <span data-ttu-id="484dd-103">「レッスン 2: データの追加」では、DimDate という名前のディメンション テーブルをインポートしました。</span><span class="sxs-lookup"><span data-stu-id="484dd-103">In Lesson 2: Add Data, you imported a dimension table named DimDate.</span></span> <span data-ttu-id="484dd-104">次に、「レッスン 3: 列名の変更」では DimDate テーブルの名前を単純な Date に変更しました。</span><span class="sxs-lookup"><span data-stu-id="484dd-104">You then renamed the DimDate table, in Lesson 3: Rename Columns, to simply, Date.</span></span> <span data-ttu-id="484dd-105">このモデルでは、このテーブルは Date という名前になりましたが、実際は日付と時刻のデータが含まれた*日付テーブル*になります。</span><span class="sxs-lookup"><span data-stu-id="484dd-105">While in your model this table is now named Date, it can also be known as a *Date table*, in that it contains date and time data.</span></span>  
  
 <span data-ttu-id="484dd-106">計算でタイム インテリジェンス関数を使用する場合は必ず、少し後でメジャーを作成することになるので、 *Date table* と、そのテーブル内で一意の識別子である *Date column* を含む日付テーブル プロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="484dd-106">Whenever you use Time Intelligence functions in calculations, as you will do when you create measures a little later, you must specify date table properties, which include a *Date table* and a unique identifier *Date column* in that table.</span></span> <span data-ttu-id="484dd-107">他のテーブルと日付テーブルの間で有効なリレーションシップを作成できます。これは、DAX のタイム インテリジェンス機能を使用して計算するために必要です。</span><span class="sxs-lookup"><span data-stu-id="484dd-107">You can then create valid relationships between other tables and the Date table; necessary for calculations using DAX time intelligence functions.</span></span>  
  
 <span data-ttu-id="484dd-108">このレッスンでは、インポートされ名前を変更された Date テーブルを *日付テーブル* 、Date テーブルの Date 列を *日付列* (一意識別子) として設定します。</span><span class="sxs-lookup"><span data-stu-id="484dd-108">In this lesson, you will mark the imported and renamed Date table as the *Date table* and the Date column (in the Date table) as the *Date column* (unique identifier).</span></span> <span data-ttu-id="484dd-109">名前の日付を使用すると、混乱を招く可能性がありますが、すぐに考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="484dd-109">All the use of the name Date can get kind of confusing, but you'll soon get the idea.</span></span>  
  
 <span data-ttu-id="484dd-110">このレッスンの推定所要時間: **3 分**</span><span class="sxs-lookup"><span data-stu-id="484dd-110">Estimated time to complete this lesson: **3 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="484dd-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="484dd-111">Prerequisites</span></span>  
 <span data-ttu-id="484dd-112">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="484dd-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="484dd-113">このレッスンの実習を行う前に、前のレッスン [「レッスン 3: 列名の変更」](rename-columns.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="484dd-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
### <a name="to-set-mark-as-date-table"></a><span data-ttu-id="484dd-114">Mark as Date Table を設定する</span><span class="sxs-lookup"><span data-stu-id="484dd-114">To set Mark as Date Table</span></span>  
  
1.  <span data-ttu-id="484dd-115">モデル デザイナーで、 **Date** テーブル (タブ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="484dd-115">In the model designer, click the **Date** table (tab).</span></span>  
  
2.  <span data-ttu-id="484dd-116">[**テーブル**] メニューをクリックし、[**日付**] をクリックして、[**日付テーブルとしてマーク**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="484dd-116">Click the **Table** menu, then click **Date**, and then click **Mark as Date Table**.</span></span>  
  
3.  <span data-ttu-id="484dd-117">**[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意の識別子として **[Date]** 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="484dd-117">In the **Mark as Date Table** dialog box, in the **Date** listbox, select the **Date** column as the unique identifier.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="484dd-118">次の手順</span><span class="sxs-lookup"><span data-stu-id="484dd-118">Next Steps</span></span>  
 <span data-ttu-id="484dd-119">このチュートリアルを続行するには、次のレッスン「 [レッスン 5: リレーションシップの作成](lesson-4-create-relationships.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="484dd-119">To continue this tutorial, go to the next lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
  
