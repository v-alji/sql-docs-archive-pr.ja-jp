---
title: OLE DB ソースを使用してデータを抽出する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 352d62cc66e3f17fb10839086e7ee9c5307f1a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742430"
---
# <a name="extract-data-by-using-the-ole-db-source"></a><span data-ttu-id="f1b10-102">OLE DB ソースを使用してデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="f1b10-102">Extract Data by Using the OLE DB Source</span></span>
  <span data-ttu-id="f1b10-103">OLE DB ソースを追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクがあらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1b10-103">To add and configure an OLE DB source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-ole-db-source"></a><span data-ttu-id="f1b10-104">OLE DB ソースを使用してデータを抽出するには</span><span class="sxs-lookup"><span data-stu-id="f1b10-104">To extract data using an OLE DB Source</span></span>  
  
1.  <span data-ttu-id="f1b10-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1b10-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f1b10-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="f1b10-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f1b10-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、OLE DB ソースをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f1b10-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="f1b10-108">OLE DB ソースをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1b10-108">Double-click the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="f1b10-109">**[OLE DB ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで、既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-109">In the **OLE DB Source Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="f1b10-110">詳細については、「 [OLE DB 接続マネージャー](../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1b10-110">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
6.  <span data-ttu-id="f1b10-111">データのアクセス方法を、次の中から選択します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-111">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="f1b10-112">**[テーブルまたはビュー]** OLE DB 接続マネージャーの接続先となる、データベースのテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-112">**Table or view** Select a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="f1b10-113">**[テーブル名またはビュー名の変数]** OLE DB 接続マネージャーの接続先となるデータベースのテーブルまたはビューの名前が含まれる、ユーザー定義変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-113">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="f1b10-114">**[SQL コマンド]** SQL コマンドを入力するか、 **[クエリ ビルダー]** で **[クエリの作成]** をクリックして、SQL コマンドを記述します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-114">**SQL command** Type an SQL command or click **Build Query** to write an SQL command using the **Query Builder**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f1b10-115">コマンドにはパラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f1b10-115">The command can include parameters.</span></span> <span data-ttu-id="f1b10-116">詳細については、「 [クエリ パラメーターをデータ フロー コンポーネントの変数にマップする](map-query-parameters-to-variables-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1b10-116">For more information, see [Map Query Parameters to Variables in a Data Flow Component](map-query-parameters-to-variables-in-a-data-flow-component.md).</span></span>  
  
    -   <span data-ttu-id="f1b10-117">**[変数からの SQL コマンド]** SQL コマンドが含まれるユーザー定義変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-117">**SQL command from variable** Select the user-defined variable that contains the SQL command.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f1b10-118">変数は、OLE DB ソースを含む同じデータ フロー タスクのスコープ内、または同じパッケージのスコープ内で定義する必要があります。また、変数は文字列データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1b10-118">The variables must be defined in the scope of the same Data Flow task that contains the OLE DB source, or in the scope of the same package; additionally, the variable must have a string data type.</span></span>  
  
7.  <span data-ttu-id="f1b10-119">外部列と出力列間のマッピングを更新するには、 **[列]** をクリックし、 **[外部列]** 一覧にある別の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-119">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="f1b10-120">必要に応じて、 **[出力列]** 一覧の値を編集し、出力列の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="f1b10-120">Optionally, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="f1b10-121">エラー出力を構成するには、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1b10-121">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="f1b10-122">詳細については、「 [データ フロー コンポーネントでエラー出力を構成する](../configure-an-error-output-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1b10-122">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="f1b10-123">**[プレビュー]** をクリックすると、OLE DB ソースによって抽出されたデータを最大 200 行表示できます。</span><span class="sxs-lookup"><span data-stu-id="f1b10-123">You can click **Preview** to view up to 200 rows of the data extracted by the OLE DB source.</span></span>  
  
11. <span data-ttu-id="f1b10-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1b10-124">Click **OK**.</span></span>  
  
12. <span data-ttu-id="f1b10-125">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1b10-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b10-126">参照</span><span class="sxs-lookup"><span data-stu-id="f1b10-126">See Also</span></span>  
 <span data-ttu-id="f1b10-127">[OLE DB ソース](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="f1b10-127">[OLE DB Source](ole-db-source.md) </span></span>  
 <span data-ttu-id="f1b10-128">[Integration Services の変換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="f1b10-128">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="f1b10-129">[Integration Services のパス](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="f1b10-129">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="f1b10-130">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="f1b10-130">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
