---
title: SQL Server 変換先を使用してデータの一括読み込みを行う | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 92ed530ae849f7a4ce123cded421ac0cd0c411ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640180"
---
# <a name="bulk-load-data-by-using-the-sql-server-destination"></a><span data-ttu-id="d45de-102">SQL Server 変換先を使用してデータの一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="d45de-102">Bulk Load Data by Using the SQL Server Destination</span></span>
  <span data-ttu-id="d45de-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つのデータ ソースがあらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d45de-103">To add and configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, the package must already include at least one Data Flow task and a data source.</span></span>  
  
### <a name="to-load-data-using-a-sql-server-destination"></a><span data-ttu-id="d45de-104">SQL Server 変換先を使用してデータの一括読み込みを行うには</span><span class="sxs-lookup"><span data-stu-id="d45de-104">To load data using a SQL Server destination</span></span>  
  
1.  <span data-ttu-id="d45de-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d45de-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d45de-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="d45de-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d45de-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d45de-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="d45de-108">変換先を、データ フロー内の変換元または直前の変換に連結します。連結するには、コネクタを変換先にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d45de-108">Connect the destination to a source or a previous transformation in the data flow by dragging a connector to the destination.</span></span>  
  
5.  <span data-ttu-id="d45de-109">変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="d45de-109">Double-click the destination.</span></span>  
  
6.  <span data-ttu-id="d45de-110">**[SQL Server 変換先エディター]** の **[接続マネージャー]** ページで、既存の OLE DB 接続マネージャーを選択するか、または **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d45de-110">In the **SQL Server Destination Editor**, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="d45de-111">詳細については、「 [OLE DB 接続マネージャー](../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d45de-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="d45de-112">データの読み込み先となるテーブルまたはビューを指定するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d45de-112">To specify the table or view into which to load the data, do one of the following:</span></span>  
  
    -   <span data-ttu-id="d45de-113">既存のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="d45de-113">Select an existing table or view.</span></span>  
  
    -   <span data-ttu-id="d45de-114">**[新規作成]** をクリックし、 **[テーブルの作成]** ダイアログ ボックスで、テーブルまたはビューを作成する SQL ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="d45de-114">Click **New**, and in the **Create Table** dialog boxwrite an SQL statement that creates a table or view.</span></span>  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="d45de-115">により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d45de-115">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="d45de-116">基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。</span><span class="sxs-lookup"><span data-stu-id="d45de-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="d45de-117">FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。</span><span class="sxs-lookup"><span data-stu-id="d45de-117">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="d45de-118">次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="d45de-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="d45de-119">詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d45de-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="d45de-120">**[マッピング]** をクリックし、 **[使用できる入力列]** 一覧にある列を、 **[使用できる変換先列]** 一覧の列にドラッグして、列をマップします。</span><span class="sxs-lookup"><span data-stu-id="d45de-120">Click **Mappings** and map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d45de-121">この変換先では、同じ名前の列は自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="d45de-121">The destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="d45de-122">**[詳細設定]** をクリックし、一括読み込みオプションの **[ID を保持する]** 、 **[NULL を保持する]** 、 **[テーブル ロック]** 、 **[CHECK 制約]** 、および **[トリガーを起動する]** を設定します。</span><span class="sxs-lookup"><span data-stu-id="d45de-122">Click **Advanced** and set the bulk load options: **Keep identity**, **Keep nulls**, **Table lock**, **Check constraints**, and **Fire triggers**.</span></span>  
  
     <span data-ttu-id="d45de-123">必要に応じて、挿入する最初の入力行と最後の入力行、挿入操作が停止するまでに発生できるエラーの最大数、および挿入を並べ替える列を指定します。</span><span class="sxs-lookup"><span data-stu-id="d45de-123">Optionally, specify the first and last input rows to insert, the maximum number of errors that can occur before the insert operation stops, and the columns on which the insert is sorted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d45de-124">挿入の並べ替え順序は、列の一覧の表示順によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="d45de-124">The sort order is determined by the order in which the columns are listed.</span></span>  
  
10. <span data-ttu-id="d45de-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d45de-125">Click **OK**.</span></span>  
  
11. <span data-ttu-id="d45de-126">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d45de-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45de-127">参照</span><span class="sxs-lookup"><span data-stu-id="d45de-127">See Also</span></span>  
 <span data-ttu-id="d45de-128">[SQL Server Destination](sql-server-destination.md) </span><span class="sxs-lookup"><span data-stu-id="d45de-128">[SQL Server Destination](sql-server-destination.md) </span></span>  
 <span data-ttu-id="d45de-129">[Integration Services の変換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="d45de-129">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="d45de-130">[Integration Services のパス](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="d45de-130">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="d45de-131">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="d45de-131">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
