---
title: ODBC 入力先を使用したデータ読み込み | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 339ec0a8-922e-48c0-97b3-fc5ee34f95e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8bf0b30619c2886df6ddb28858cf98bad858421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715618"
---
# <a name="load-data-by-using-the-odbc-destination"></a><span data-ttu-id="e4e0a-102">ODBC 入力先を使用したデータ読み込み</span><span class="sxs-lookup"><span data-stu-id="e4e0a-102">Load Data by Using the ODBC Destination</span></span>
  <span data-ttu-id="e4e0a-103">次の手順では、ODBC 入力先を使用してデータを読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-103">This procedure shows how to load data by using the ODBC destination.</span></span> <span data-ttu-id="e4e0a-104">ODBC 入力先を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの入力元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-104">To add and configure an ODBC destination, the package must already include at least one Data Flow task and source.</span></span>  
  
### <a name="to-load-data-using-an-odbc-destination"></a><span data-ttu-id="e4e0a-105">ODBC 入力先を使用してデータを読み込むには</span><span class="sxs-lookup"><span data-stu-id="e4e0a-105">To load data using an ODBC destination</span></span>  
  
1.  <span data-ttu-id="e4e0a-106">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、使用する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="e4e0a-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、ODBC 入力先をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC destination to the design surface.</span></span>  
  
3.  <span data-ttu-id="e4e0a-108">利用可能なデータ フロー コンポーネントの出力を ODBC 入力先の入力にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-108">Drag an available output of a data flow component to the input of the ODBC destination.</span></span>  
  
4.  <span data-ttu-id="e4e0a-109">ODBC 入力先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-109">Double-click the ODBC destination.</span></span>  
  
5.  <span data-ttu-id="e4e0a-110">**[ODBC 入力先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで、既存の ODBC 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-110">In the **ODBC Destination Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
6.  <span data-ttu-id="e4e0a-111">データのアクセス方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-111">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="e4e0a-112">**[テーブル名 - バッチ]** バッチモードで動作する ODBC 入力先を構成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-112">**Table Name - Batch**: Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="e4e0a-113">このオプションを選択すると、 **[バッチ サイズ]** を設定できます。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-113">When you select this option, you can set the **Batch size**.</span></span>  
  
    -   <span data-ttu-id="e4e0a-114">**[テーブル名 - 行ごと]** : 一度に 1 行ずつ、入力先に各行を挿入する ODBC 入力先を構成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-114">**Table Name - Row by Row**: Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="e4e0a-115">このオプションを選択すると、データは一度に 1 行ずつ、テーブルに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-115">When you select this option, the data is loaded into the table one row at a time.</span></span>  
  
7.  <span data-ttu-id="e4e0a-116">**[テーブル名またはビュー名]** フィールドで、使用できるテーブルまたはビューを一覧のデータベースから選択するか、正規表現を入力してテーブルを指定します。この一覧には、最初の 1,000 テーブルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-116">In the **Name of the table or the view** field, select an available table or view from the database from the list or type in a regular expression to identify the table.This list contains the first 1000 tables only.</span></span> <span data-ttu-id="e4e0a-117">データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (\*) を使用すると、目的のテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-117">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
8.  <span data-ttu-id="e4e0a-118">**[プレビュー]** をクリックすると、ODBC 入力先で選択されるテーブルのデータを最大 200 行表示することができます。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-118">You can click **Preview** to view up to 200 rows of the data from the table selected in the ODBC destination.</span></span>  
  
9. <span data-ttu-id="e4e0a-119">**[マッピング]** をクリックし、 **[使用できる入力列]** 一覧にある列を、 **[使用できる変換先列]** 一覧の列にドラッグして、列をマップします。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-119">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
10. <span data-ttu-id="e4e0a-120">エラー出力を構成するには、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-120">To configure the error output, click **Error Output**.</span></span>  
  
11. <span data-ttu-id="e4e0a-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="e4e0a-122">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4e0a-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e0a-123">参照</span><span class="sxs-lookup"><span data-stu-id="e4e0a-123">See Also</span></span>  
 <span data-ttu-id="e4e0a-124">[ODBC 変換先エディター &#40;[接続マネージャー] ページ&#41;](../odbc-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="e4e0a-124">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="e4e0a-125">[[ODBC 変換先エディター] &#40;[マッピング] ページ&#41;](../odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="e4e0a-125">[ODBC Destination Editor &#40;Mappings Page&#41;](../odbc-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="e4e0a-126">[[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../odbc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="e4e0a-126">[ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md)</span></span>  
  
  
