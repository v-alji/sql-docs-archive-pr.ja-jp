---
title: 変更データを取得および理解する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62f60bf4a79c39b4f0cb7d1ba8fb3f52680a1f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720312"
---
# <a name="retrieve-and-understand-the-change-data"></a><span data-ttu-id="a319a-102">変更データを取得および理解する</span><span class="sxs-lookup"><span data-stu-id="a319a-102">Retrieve and Understand the Change Data</span></span>
  <span data-ttu-id="a319a-103">変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フローにおいて、最初のタスクは、変更データを取得するクエリを実行することです。</span><span class="sxs-lookup"><span data-stu-id="a319a-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to run the query that retrieves the change data.</span></span> <span data-ttu-id="a319a-104">このクエリは、データ フロー タスクの変換元コンポーネント内で実行します。</span><span class="sxs-lookup"><span data-stu-id="a319a-104">You execute this query inside a source component in a Data Flow task.</span></span> <span data-ttu-id="a319a-105">その後、下流にある変換や変換先を使用して、変更データを変換先に適用できます。</span><span class="sxs-lookup"><span data-stu-id="a319a-105">You can then use downstream transformations and destinations to apply the change data to your destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a319a-106">テーブル値関数を含むクエリの作成は、変更データの増分読み込みを実行するパッケージを作成するプロセスにおける 3 番目の手順です。</span><span class="sxs-lookup"><span data-stu-id="a319a-106">The creation of a query that contains a table-valued function is the third step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="a319a-107">このクエリの詳細については、「 [変更データを取得する関数を作成する](create-the-function-to-retrieve-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a319a-107">For more information about this query, see, [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span> <span data-ttu-id="a319a-108">変更データの増分読み込みを実行するパッケージを作成するプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](change-data-capture-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a319a-108">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="adding-the-data-flow-task"></a><span data-ttu-id="a319a-109">データ フロー タスクの追加</span><span class="sxs-lookup"><span data-stu-id="a319a-109">Adding the Data Flow Task</span></span>  
 <span data-ttu-id="a319a-110">パッケージのデータ フローでは、変更データを取得し、行われた変更の種類に基づいて行を分割し、変更を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="a319a-110">In the data flow of the package, you retrieve the change data, separate the rows based on the type of change that occurred, and then apply the changes to the destination.</span></span>  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a><span data-ttu-id="a319a-111">データ フロー タスクをパッケージに追加するには</span><span class="sxs-lookup"><span data-stu-id="a319a-111">To add a Data Flow task to the package</span></span>  
  
1.  <span data-ttu-id="a319a-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[制御フロー]** タブで、データ フロー タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="a319a-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Control Flow** tab, add a Data Flow task.</span></span>  
  
2.  <span data-ttu-id="a319a-113">クエリ文字列を準備した先行タスクをデータ フロー タスクに連結します。</span><span class="sxs-lookup"><span data-stu-id="a319a-113">Connect the preceding task that prepared the query string to the Data Flow task.</span></span>  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a><span data-ttu-id="a319a-114">変更をクエリで取得するための変換元コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="a319a-114">Configuring the Source Component to Query for Changes</span></span>  
 <span data-ttu-id="a319a-115">変換元コンポーネントは、変数に格納されている準備済みのクエリ文字列を使用して、変更データを取得するテーブル値関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a319a-115">The source component uses the query string that was prepared and stored in a variable to calls the table-valued function that retrieves the changed data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a319a-116">変数に格納されている準備済みのクエリ文字列の詳細については、「 [変更データのクエリを準備する](prepare-to-query-for-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a319a-116">For more information about the query string that was prepared and stored in a variable, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span> <span data-ttu-id="a319a-117">変更データを取得するテーブル値関数の詳細については、「 [変更データを取得する関数を作成する](create-the-function-to-retrieve-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a319a-117">For more information about the table-valued function that retrieves the change data, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a><span data-ttu-id="a319a-118">変更データを取得するように OLE DB ソースを構成するには</span><span class="sxs-lookup"><span data-stu-id="a319a-118">To configure an OLE DB source to retrieve the change data</span></span>  
  
1.  <span data-ttu-id="a319a-119">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[データ フロー]** タブで、OLE DB ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="a319a-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Data Flow** tab, add an OLE DB source.</span></span>  
  
2.  <span data-ttu-id="a319a-120">**[OLE DB ソース エディター]** の **[接続マネージャー]** ページで、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a319a-120">In the **OLE DB Source Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="a319a-121">ソース データベースへの有効な接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="a319a-121">Configure a valid connection to the source database.</span></span>  
  
    2.  <span data-ttu-id="a319a-122">**[データ アクセス モード]** で **[変数からの SQL コマンド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a319a-122">For **Data access mode**, select **SQL command from variable**.</span></span>  
  
    3.  <span data-ttu-id="a319a-123">**[変数名]** で **[User::SqlDataQuery]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a319a-123">For **Variable name**, select **User::SqlDataQuery**.</span></span>  
  
3.  <span data-ttu-id="a319a-124">**[OLE DB ソース エディター]** の **[列]** ページで、必要なすべての列が出力列にマップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a319a-124">In the **OLE DB Source Editor**, on the **Columns** page, make sure that all the columns that you want are mapped to output columns.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="a319a-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="a319a-125">Next Step</span></span>  
 <span data-ttu-id="a319a-126">変更データを取得するように OLE DB ソースを構成したら、次の手順で、パッケージのデータ フローのデザインを開始します。</span><span class="sxs-lookup"><span data-stu-id="a319a-126">After you have configured an OLE DB source to retrieve the change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="a319a-127">**次のトピック:** [挿入、更新、および削除を処理する](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="a319a-127">**Next topic:** [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>  
  
  
