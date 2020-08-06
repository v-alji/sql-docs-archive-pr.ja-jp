---
title: ODBC 入力元を使用したデータ抽出 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c05efe2b0479047280fc093ee555e037c77d82e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742433"
---
# <a name="extract-data-by-using-the-odbc-source"></a><span data-ttu-id="536e1-102">ODBC 入力元を使用したデータ抽出</span><span class="sxs-lookup"><span data-stu-id="536e1-102">Extract Data by Using the ODBC Source</span></span>
  <span data-ttu-id="536e1-103">この手順では、ODBC 入力元を使用してデータを抽出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="536e1-103">This procedure describes how to extract data by using an ODBC source.</span></span> <span data-ttu-id="536e1-104">ODBC 入力元を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクがあらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="536e1-104">To add and configure an ODBC source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-odbc-source"></a><span data-ttu-id="536e1-105">ODBC 入力元を使用してデータを抽出するには</span><span class="sxs-lookup"><span data-stu-id="536e1-105">To extract data using an ODBC source</span></span>  
  
1.  <span data-ttu-id="536e1-106">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、使用する [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="536e1-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="536e1-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、ODBC 入力元をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="536e1-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC source to the design surface.</span></span>  
  
3.  <span data-ttu-id="536e1-108">ODBC 入力元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="536e1-108">Double-click the ODBC source.</span></span>  
  
4.  <span data-ttu-id="536e1-109">**[ODBC 入力元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで、既存の ODBC 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="536e1-109">In the **ODBC Source Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="536e1-110">データのアクセス方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="536e1-110">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="536e1-111">**[テーブル名]** : データベースのテーブルまたはビューを選択するか、正規表現を入力して、ODBC 接続マネージャーの接続先のテーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="536e1-111">**Table Name**: Select a table or view in the database or type a regular expression to identify the table to which the ODBC connection manager connects.</span></span>  
  
         <span data-ttu-id="536e1-112">この一覧には、最初の 1,000 個のテーブルのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="536e1-112">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="536e1-113">データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (\*) を使用すると、目的のテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="536e1-113">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
    -   <span data-ttu-id="536e1-114">**[SQLコマンド]** : SQLコマンドを入力するか、 **[参照]** をクリックしてテキスト ファイルから SQL クエリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="536e1-114">**SQL Command**: Type an SQL Command or click **Browse** to load the SQL query from a text file.</span></span>  
  
6.  <span data-ttu-id="536e1-115">**[プレビュー]** をクリックすると、ODBC 入力元によって抽出されるデータを最大 200 行表示できます。</span><span class="sxs-lookup"><span data-stu-id="536e1-115">You can click **Preview** to view up to 200 rows of the data extracted by the ODBC source.</span></span>  
  
7.  <span data-ttu-id="536e1-116">外部列と出力列間のマッピングを更新するには、 **[列]** をクリックし、 **[外部列]** 一覧にある別の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="536e1-116">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="536e1-117">必要に応じて、 **[出力列]** 一覧の値を編集し、出力列の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="536e1-117">If necessary, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="536e1-118">エラー出力を構成するには、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="536e1-118">To configure the error output, click **Error Output**.</span></span>  
  
10. <span data-ttu-id="536e1-119">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="536e1-119">Click **OK**.</span></span>  
  
11. <span data-ttu-id="536e1-120">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="536e1-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536e1-121">参照</span><span class="sxs-lookup"><span data-stu-id="536e1-121">See Also</span></span>  
 <span data-ttu-id="536e1-122">[ODBC ソース エディター ([接続マネージャー] ページ)](../odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="536e1-122">[ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="536e1-123">[[ODBC ソース エディター] &#40;[列] ページ&#41;](../odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="536e1-123">[ODBC Source Editor &#40;Columns Page&#41;](../odbc-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="536e1-124">[[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../odbc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="536e1-124">[ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md)</span></span>  
  
  
