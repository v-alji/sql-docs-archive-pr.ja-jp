---
title: OLE DB 変換先を使用してデータを読み込む | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43e8d1123ae91d9e68c00fbe3e05c490383afe0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715614"
---
# <a name="load-data-by-using-the-ole-db-destination"></a><span data-ttu-id="603cd-102">OLE DB 変換先を使用してデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="603cd-102">Load Data by Using the OLE DB Destination</span></span>
  <span data-ttu-id="603cd-103">OLE DB 変換先を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="603cd-103">To add and configure an OLE DB destination, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-load-data-using-an-ole-db-destination"></a><span data-ttu-id="603cd-104">OLE DB 変換先を使用してデータを読み込むには</span><span class="sxs-lookup"><span data-stu-id="603cd-104">To load data using an OLE DB destination</span></span>  
  
1.  <span data-ttu-id="603cd-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="603cd-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="603cd-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="603cd-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="603cd-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、OLE DB 変換先をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="603cd-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="603cd-108">OLE DB 変換先をデータ フローに連結します。連結するには、データ ソースまたは前の変換から変換先にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="603cd-108">Connect the OLE DB destination to the data flow by dragging a connector from a data source or a previous transformation to the destination.</span></span>  
  
5.  <span data-ttu-id="603cd-109">OLE DB 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="603cd-109">Double-click the OLE DB destination.</span></span>  
  
6.  <span data-ttu-id="603cd-110">**[OLE DB 変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで、既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="603cd-110">In the **OLE DB Destination Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="603cd-111">詳細については、「 [OLE DB 接続マネージャー](../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="603cd-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="603cd-112">データのアクセス方法を、次の中から選択します。</span><span class="sxs-lookup"><span data-stu-id="603cd-112">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="603cd-113">**[テーブルまたはビュー]** データが含まれるデータベース内のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="603cd-113">**Table or view** Select a table or view in the database that contains the data.</span></span>  
  
    -   <span data-ttu-id="603cd-114">**[テーブルまたはビュー - 高速読み込み]** データが含まれるデータベース内のテーブルまたはビューを選択し、高速読み込みのオプションを設定します。高速読み込みのオプションには、 **[ID を保持する]** 、 **[NULL を保持する]** 、 **[テーブル ロック]** 、 **[CHECK 制約]** 、 **[バッチごとの行数]** 、または **[挿入コミット サイズの最大値]** があります。</span><span class="sxs-lookup"><span data-stu-id="603cd-114">**Table or view - fast load** Select a table or view in the database that contains the data, and then set the fast-load options: **Keep identity**, **Keep null**, **Table lock**, **Check constraint**, **Rows per batch**, or **Maximum insert commit size**.</span></span>  
  
    -   <span data-ttu-id="603cd-115">**[テーブル名またはビュー名の変数]** データベースのテーブルまたはビューの名前が含まれている、ユーザー定義変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="603cd-115">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database.</span></span>  
  
    -   <span data-ttu-id="603cd-116">**[テーブル名またはビュー名の変数 - 高速読み込み]** データが含まれるデータベースのテーブルまたはビューの名前が含まれているユーザー定義変数を選択し、次に高速読み込みのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="603cd-116">**Table name or view name variable fast load** Select the user-defined variable that contains the name of a table or view in the database that contains the data, and then set the fast-load options.</span></span>  
  
    -   <span data-ttu-id="603cd-117">**[SQL コマンド]** SQL コマンドを入力するか、 **[クエリ ビルダー]** で **[クエリの作成]** をクリックして、SQL コマンドを記述します。</span><span class="sxs-lookup"><span data-stu-id="603cd-117">**SQL command** Type an SQL command or click **Build Query** to write an SQL command by using the **Query Builder**.</span></span>  
  
8.  <span data-ttu-id="603cd-118">**[マッピング]** をクリックし、 **[使用できる入力列]** 一覧にある列を、 **[使用できる変換先列]** 一覧の列にドラッグして、列をマップします。</span><span class="sxs-lookup"><span data-stu-id="603cd-118">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="603cd-119">OLE DB 変換先では、同じ名前の列は自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="603cd-119">The OLE DB destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="603cd-120">エラー出力を構成するには、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="603cd-120">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="603cd-121">詳細については、「 [データ フロー コンポーネントでエラー出力を構成する](../configure-an-error-output-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="603cd-121">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="603cd-122">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="603cd-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="603cd-123">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="603cd-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603cd-124">参照</span><span class="sxs-lookup"><span data-stu-id="603cd-124">See Also</span></span>  
 <span data-ttu-id="603cd-125">[OLE DB 変換先](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="603cd-125">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="603cd-126">[Integration Services の変換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="603cd-126">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="603cd-127">[Integration Services のパス](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="603cd-127">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="603cd-128">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="603cd-128">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
