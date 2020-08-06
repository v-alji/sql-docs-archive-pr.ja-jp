---
title: 'レッスン 1: サンプル サブスクライバー データベースの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ee49f0858b28c0c4b00fd391b0db7b4d2c54b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742910"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a><span data-ttu-id="36e57-102">レッスン 1 : サンプル サブスクライバー データベースの作成</span><span class="sxs-lookup"><span data-stu-id="36e57-102">Lesson 1: Creating a Sample Subscriber Database</span></span>
  <span data-ttu-id="36e57-103">データ ドリブン サブスクリプションを定義するには、その前に、サブスクリプション データを提供するデータ ソースを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36e57-103">Before you can define a data-driven subscription, you must have a data source that provides subscription data.</span></span> <span data-ttu-id="36e57-104">ここでは、このチュートリアル用のサブスクリプション データを格納する簡単なデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="36e57-104">In this step, you will create a small database to store the subscription data used in this tutorial.</span></span> <span data-ttu-id="36e57-105">後でサブスクリプションを処理する際、このデータがレポート サーバーにより取得され、レポート出力、配信オプション、およびレポート表示形式のカスタマイズに使用されます。</span><span class="sxs-lookup"><span data-stu-id="36e57-105">Later, when the subscription is processed, the report server retrieves this data and uses it to customize report output, delivery options, and report presentation format.</span></span>  
  
 <span data-ttu-id="36e57-106">このレッスンでは、を使用してデータベースを作成することを前提としてい [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="36e57-106">This lesson assumes you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to create a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span>  
  
### <a name="to-create-a-sample-subscriber-database"></a><span data-ttu-id="36e57-107">サンプル サブスクライバー データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="36e57-107">To create a sample Subscriber database</span></span>  
  
1.  <span data-ttu-id="36e57-108">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] を起動し、[!INCLUDE[ssDE](../includes/ssde-md.md)]への接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="36e57-108">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and open a connection to a [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="36e57-109">[データベース] を右クリックして **[新しいデータベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36e57-109">Right-click on Databases, select **New Database...**.</span></span>  
  
3.  <span data-ttu-id="36e57-110">[新しいデータベース] ダイアログボックスの [データベース名] に「*サブスクライバー*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="36e57-110">In the New Database dialog box, in Database Name, type *Subscribers*.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="36e57-111">ツール バーの **[新しいクエリ]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36e57-111">Click the **New Query** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="36e57-112">次の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="36e57-112">Copy the following [!INCLUDE[tsql](../includes/tsql-md.md)] statements into the empty query:</span></span>  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
6.  <span data-ttu-id="36e57-113">ツールバーの **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36e57-113">Click **! Execute** on the toolbar.</span></span>  
  
7.  <span data-ttu-id="36e57-114">SELECT ステートメントを使用して、3 行のデータがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="36e57-114">Use a SELECT statement to verify that you have three rows of data.</span></span> <span data-ttu-id="36e57-115">例: `select * from OrderInfo`</span><span class="sxs-lookup"><span data-stu-id="36e57-115">For example: `select * from OrderInfo`</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="36e57-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="36e57-116">Next Steps</span></span>  
 <span data-ttu-id="36e57-117">以上の操作で、レポートを配信し、各サブスクライバーごとにレポート出力を変えるサブスクリプション データを作成できました。</span><span class="sxs-lookup"><span data-stu-id="36e57-117">You have successfully created the subscription data that will drive report distribution and vary the report output for each subscriber.</span></span> <span data-ttu-id="36e57-118">次に、サブスクライバーに配信するレポートのデータ ソース プロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="36e57-118">Next, you will modify the data source properties of the report you will distribute to subscribers.</span></span> <span data-ttu-id="36e57-119">データ ソース プロパティを更新する目的は、データ ドリブン サブスクリプション配信用のレポートを準備することです。</span><span class="sxs-lookup"><span data-stu-id="36e57-119">Modifying the data source properties is done to prepare the report for data-driven subscription delivery.</span></span> <span data-ttu-id="36e57-120">また、レポートのデザインを変更して、サブスクリプションがサブスクライバーのデータと共に使用するパラメーターを含めます。</span><span class="sxs-lookup"><span data-stu-id="36e57-120">You will also modify the report design to include a parameter that the subscription will use with the subscriber data.</span></span> <span data-ttu-id="36e57-121">[レッスン 2: レポートデータソースのプロパティの変更](lesson-2-modifying-the-report-data-source-properties.md)</span><span class="sxs-lookup"><span data-stu-id="36e57-121">[Lesson 2: Modifying the Report Data Source Properties](lesson-2-modifying-the-report-data-source-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e57-122">参照</span><span class="sxs-lookup"><span data-stu-id="36e57-122">See Also</span></span>  
 <span data-ttu-id="36e57-123">[データ ドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;](create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="36e57-123">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="36e57-124">[データベースを作成する](../relational-databases/databases/create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="36e57-124">[Create a Database](../relational-databases/databases/create-a-database.md) </span></span>  
 [<span data-ttu-id="36e57-125">基本的なテーブル レポートの作成 (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="36e57-125">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
