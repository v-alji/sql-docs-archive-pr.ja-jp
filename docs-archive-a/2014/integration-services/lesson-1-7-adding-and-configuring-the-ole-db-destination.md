---
title: '手順 7 : OLE DB 変換先の追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da917ccc4ca756c2442e70477976b5a71f7eb56e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641088"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a><span data-ttu-id="628f2-102">手順 7:OLE DB 変換先の追加と構成</span><span class="sxs-lookup"><span data-stu-id="628f2-102">Step 7: Adding and Configuring the OLE DB Destination</span></span>
  <span data-ttu-id="628f2-103">前回までの実習で、フラット ファイル ソースからデータを抽出し、変換先との互換性のある形式にデータを変換できるパッケージを作成しました。</span><span class="sxs-lookup"><span data-stu-id="628f2-103">Your package now can extract data from the flat file source and transform that data into a format that is compatible with the destination.</span></span> <span data-ttu-id="628f2-104">次は、変換したデータを実際に変換先に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="628f2-104">The next task is to actually load the transformed data into the destination.</span></span> <span data-ttu-id="628f2-105">データを読み込むには、データ フローに OLE DB 変換先を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="628f2-105">To load the data, you must add an OLE DB destination to the data flow.</span></span> <span data-ttu-id="628f2-106">OLE DB 変換先では、データベース テーブル、ビュー、または SQL コマンドを使用して、OLE DB に準拠するさまざまなデータベースにデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="628f2-106">The OLE DB destination can use a database table, view, or an SQL command to load data into a variety of OLE DB-compliant databases.</span></span>  
  
 <span data-ttu-id="628f2-107">この操作では、以前に作成した OLE DB の接続マネージャーを使用できるように、OLE DB 変換先を追加、構成します。</span><span class="sxs-lookup"><span data-stu-id="628f2-107">In this procedure, you add and configure an OLE DB destination to use the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a><span data-ttu-id="628f2-108">サンプルの OLE DB 変換先を追加および構成するには</span><span class="sxs-lookup"><span data-stu-id="628f2-108">To add and configure the sample OLE DB destination</span></span>  
  
1.  <span data-ttu-id="628f2-109">[ **SSIS ツールボックス**] で **[その他の**変換先] を展開し、[ **OLE DB Destination** ] を [**データフロー** ] タブのデザイン画面にドラッグします。 OLE DB の変換先を [ **Lookup Date Key** ] 変換のすぐ下に配置します。</span><span class="sxs-lookup"><span data-stu-id="628f2-109">In the **SSIS Toolbox**, expand **Other Destinations**, and drag **OLE DB Destination** onto the design surface of the **Data Flow** tab. Place the OLE DB destination directly below the **Lookup Date Key** transformation.</span></span>  
  
2.  <span data-ttu-id="628f2-110">**[Lookup Date Key]** 変換をクリックし、緑色の矢印を、新しく追加した **[OLE DB 変換先]** にドラッグします。2 つのコンポーネントが接続されます。</span><span class="sxs-lookup"><span data-stu-id="628f2-110">Click the **Lookup Date Key** transformation and drag the green arrow over to the newly added **OLE DB Destination** to connect the two components together.</span></span>  
  
3.  <span data-ttu-id="628f2-111">**[入出力の選択]** ダイアログ ボックスの **[出力]** ボックスの一覧で **[参照の一致出力]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628f2-111">In the **Input Output Selection** dialog box, in the **Output** list box, click **Lookup Match Output**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="628f2-112">**[データ フロー]** デザイン画面で、新しく追加した **[OLE DB 変換先]** コンポーネントの **[OLE DB 変換先]** をクリックし、名前を「 **Sample OLE DB Destination**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="628f2-112">On the **Data Flow** design surface, click **OLE DB Destination** in the newly added **OLE DB Destination** component, and change the name to **Sample OLE DB Destination**.</span></span>  
  
5.  <span data-ttu-id="628f2-113">**[Sample OLE DB Destination]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="628f2-113">Double-click **Sample OLE DB Destination**.</span></span>  
  
6.  <span data-ttu-id="628f2-114">**[OLE DB 変換先エディター]** ダイアログ ボックスの **[OLE DB 接続マネージャー]** ボックスで **localhost.AdventureWorksDW2012** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="628f2-114">In the **OLE DB Destination Editor** dialog box, ensure that **localhost.AdventureWorksDW2012** is selected in the **OLE DB Connection manager** box.</span></span>  
  
7.  <span data-ttu-id="628f2-115">**[テーブル名またはビュー名]** ボックスで **[dbo].[FactCurrencyRate]** を選択するか、または直接入力します。</span><span class="sxs-lookup"><span data-stu-id="628f2-115">In the **Name of the table or the view** box, type or select **[dbo].[FactCurrencyRate]**.</span></span>  
  
8.  <span data-ttu-id="628f2-116">**[新規作成]** ボタンをクリックして新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="628f2-116">Click the **New** button to create a new table.</span></span>  <span data-ttu-id="628f2-117">スクリプト内のテーブル名を「 **NewFactCurrencyRate**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="628f2-117">Change the name of the table in the script to read **NewFactCurrencyRate**.</span></span>  <span data-ttu-id="628f2-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628f2-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="628f2-119">**[OK]** をクリックすると、ダイアログが閉じ、 **[テーブル名またはビュー名]** は自動的に「 **NewFactCurrencyRate**」に変更されます。</span><span class="sxs-lookup"><span data-stu-id="628f2-119">Upon clicking **OK**, the dialog will close and the **Name of the table or the view** will automatically change to **NewFactCurrencyRate**.</span></span>  
  
10. <span data-ttu-id="628f2-120">**[マッピング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628f2-120">Click **Mappings**.</span></span>  
  
11. <span data-ttu-id="628f2-121">**AverageRate**、 **CurrencyKey**、 **EndOfDayRate**、および **DateKey** の各入力列が変換先列に正しくマップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="628f2-121">Verify that the **AverageRate**, **CurrencyKey**, **EndOfDayRate**, and **DateKey** input columns are mapped correctly to the destination columns.</span></span> <span data-ttu-id="628f2-122">同じ名前の列がマップされていれば、マッピングは適切です。</span><span class="sxs-lookup"><span data-stu-id="628f2-122">If same-named columns are mapped, the mapping is correct.</span></span>  
  
12. <span data-ttu-id="628f2-123">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628f2-123">Click **OK**.</span></span>  
  
13. <span data-ttu-id="628f2-124">**[Sample OLE DB Destination]** 変換先を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628f2-124">Right-click the **Sample OLE DB Destination** destination and click **Properties**.</span></span>  
  
14. <span data-ttu-id="628f2-125">プロパティウィンドウで、 `LocaleID` プロパティが**英語 (米国)** に設定され、 `DefaultCodePage` プロパティが**1252**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="628f2-125">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the`DefaultCodePage` property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="628f2-126">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="628f2-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="628f2-127">手順 8:レッスン 1 のパッケージをわかりやすくする作業</span><span class="sxs-lookup"><span data-stu-id="628f2-127">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a><span data-ttu-id="628f2-128">参照</span><span class="sxs-lookup"><span data-stu-id="628f2-128">See Also</span></span>  
 [<span data-ttu-id="628f2-129">OLE DB 変換先</span><span class="sxs-lookup"><span data-stu-id="628f2-129">OLE DB Destination</span></span>](data-flow/ole-db-destination.md)  
  
  
