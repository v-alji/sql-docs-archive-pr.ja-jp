---
title: ジェネリック T-sql Query コレクター型を使用するカスタムコレクションセットの作成 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- T-SQL Query collector type
- collection sets [SQL Server], creating custom
ms.assetid: 6b06db5b-cfdc-4ce0-addd-ec643460605b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab21ad5fd65556dec639fd5ca6999d23e2de673b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642837"
---
# <a name="create-a-custom-collection-set-that-uses-the-generic-t-sql-query-collector-type-transact-sql"></a><span data-ttu-id="6a1e2-102">ジェネリック T-SQL Query コレクター型を使用するカスタム コレクション セットの作成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6a1e2-102">Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type (Transact-SQL)</span></span>
  <span data-ttu-id="6a1e2-103">データ コレクターで用意されているストアド プロシージャを使用して、ジェネリック T-SQL Query コレクター型を使用するコレクション アイテムを含むカスタム コレクション セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-103">You can create a custom collection set with collection items that use the Generic T-SQL Query collector type by using the stored procedures that are provided with the data collector.</span></span> <span data-ttu-id="6a1e2-104">この作業には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用した次の手順の実行も含まれます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-104">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedures:</span></span>  
  
-   <span data-ttu-id="6a1e2-105">アップロードのスケジュールを構成する。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-105">Configure upload schedules.</span></span>  
  
-   <span data-ttu-id="6a1e2-106">コレクション セットを定義して作成する。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-106">Define and create the collection set.</span></span>  
  
-   <span data-ttu-id="6a1e2-107">コレクション アイテムを定義して作成する。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-107">Define and create a collection item.</span></span>  
  
-   <span data-ttu-id="6a1e2-108">コレクション セットとコレクション アイテムが存在することを確認する。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-108">Verify that the collection set and collection items exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a1e2-109">カスタム コレクション セットを作成する前に、データ コレクションのパラメーターを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-109">Before you create a custom collection set, you must configure data collection parameters.</span></span> <span data-ttu-id="6a1e2-110">詳細については、「[データ コレクションのパラメーターの構成 &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-110">For more information, see [Configure Data Collection Parameters &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md).</span></span>  
  
### <a name="define-and-create-the-collection-set"></a><span data-ttu-id="6a1e2-111">コレクション セットを定義して作成する</span><span class="sxs-lookup"><span data-stu-id="6a1e2-111">Define and create the collection set</span></span>  
  
1.  <span data-ttu-id="6a1e2-112">sp_syscollector_create_collection_set ストアド プロシージャを使用して、新しいコレクション セットを定義します。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-112">Define a new collection set using the sp_syscollector_create_collection_set stored procedure.</span></span>  
  
    ```  
    USE msdb;  
    DECLARE @collection_set_id int;  
    DECLARE @collection_set_uid uniqueidentifier;  
    EXEC sp_syscollector_create_collection_set   
        @name=N'DMV Test 1',   
        @collection_mode=0,   
        @description=N'This is a test collection set',   
        @logging_level=1,   
        @days_until_expiration=14,   
        @schedule_name=N'CollectorSchedule_Every_15min',   
        @collection_set_id=@collection_set_id OUTPUT,   
        @collection_set_uid=@collection_set_uid OUTPUT;  
    SELECT @collection_set_id, @collection_set_uid;  
    ```  
  
     <span data-ttu-id="6a1e2-113">コレクション モードは、0 (キャッシュ) または 1 (非キャッシュ) に設定できます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-113">The collection mode can be set to either 0 (cached) or to 1 (non-cached).</span></span>  
  
     <span data-ttu-id="6a1e2-114">ログ記録レベルは、0、1、または 2 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-114">The logging level can be set to 0, 1 or 2.</span></span>  
  
     <span data-ttu-id="6a1e2-115">データ コレクターには、以下の事前に構成されたスケジュールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-115">The following preconfigured schedules are provided with the data collector:</span></span>  
  
    -   <span data-ttu-id="6a1e2-116">CollectorSchedule_Every_5min</span><span class="sxs-lookup"><span data-stu-id="6a1e2-116">CollectorSchedule_Every_5min</span></span>  
  
    -   <span data-ttu-id="6a1e2-117">CollectorSchedule_Every_10min</span><span class="sxs-lookup"><span data-stu-id="6a1e2-117">CollectorSchedule_Every_10min</span></span>  
  
    -   <span data-ttu-id="6a1e2-118">CollectorSchedule_Every_15min</span><span class="sxs-lookup"><span data-stu-id="6a1e2-118">CollectorSchedule_Every_15min</span></span>  
  
    -   <span data-ttu-id="6a1e2-119">CollectorSchedule_Every_30min</span><span class="sxs-lookup"><span data-stu-id="6a1e2-119">CollectorSchedule_Every_30min</span></span>  
  
    -   <span data-ttu-id="6a1e2-120">CollectorSchedule_Every_60min</span><span class="sxs-lookup"><span data-stu-id="6a1e2-120">CollectorSchedule_Every_60min</span></span>  
  
    -   <span data-ttu-id="6a1e2-121">CollectorSchedule_Every_6h</span><span class="sxs-lookup"><span data-stu-id="6a1e2-121">CollectorSchedule_Every_6h</span></span>  
  
     <span data-ttu-id="6a1e2-122">用意されているスケジュールのいずれも使用しない場合は、コレクション セットに新しいスケジュールを作成して使用できます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-122">If you do not want to use one of the schedules that are provided, you can create a new schedule and use it for the collection set.</span></span> <span data-ttu-id="6a1e2-123">詳細については、「 [スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-123">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
### <a name="define-and-create-a-collection-item"></a><span data-ttu-id="6a1e2-124">コレクション アイテムを定義して作成する</span><span class="sxs-lookup"><span data-stu-id="6a1e2-124">Define and create a collection item</span></span>  
  
1.  <span data-ttu-id="6a1e2-125">新しいコレクション アイテムはインストール済みのジェネリックコレクター型に基づいているため、次のコードを実行して、ジェネリック T-SQL Query コレクター型に対応するように GUID を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-125">Because the new collection item is based on a generic collector type that is already installed, you can run the following code to set the GUID to correspond to the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid uniqueidentifier;  
    SELECT @collector_type_uid = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
    WHERE name = N'Generic T-SQL Query Collector Type';  
    DECLARE @collection_item_id int;  
    ```  
  
2.  <span data-ttu-id="6a1e2-126">sp_syscollector_create_collection_item ストアド プロシージャを使用してコレクション アイテムを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-126">Use the sp_syscollector_create_collection_item stored procedure to create the collection item.</span></span> <span data-ttu-id="6a1e2-127">コレクション アイテムがジェネリック T-SQL Query コレクター型に必要なスキーマにマップされるように、コレクション アイテムのスキーマを宣言します。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-127">Declare the schema for the collection item so it maps to the schema that is required for the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    EXEC sp_syscollector_create_collection_item   
        @name=N'Query Stats - Test 1',   
        @parameters=N'  
            <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
            <Value>SELECT * FROM sys.dm_exec_query_stats</Value>  
            <OutputTable>dm_exec_query_stats</OutputTable>  
            </Query>  
            </ns:TSQLQueryCollector>',   
        @collection_item_id=@collection_item_id OUTPUT,   
        @frequency=5,   
        @collection_set_id=@collection_set_id,   
        @collector_type_uid=@collector_type_uid;  
    SELECT @collection_item_id;  
    ```  
  
### <a name="verify-that-the-new-collection-set-and-collection-item-exist"></a><span data-ttu-id="6a1e2-128">新しいコレクション セットとコレクション アイテムが存在することを確認する</span><span class="sxs-lookup"><span data-stu-id="6a1e2-128">Verify that the new collection set and collection item exist</span></span>  
  
1.  <span data-ttu-id="6a1e2-129">新しいコレクション セットを開始する前に、次のクエリを実行して新しいコレクション セットとそのコレクション アイテムが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-129">Before starting the new collection set, run the following query to verify that the new collection set and its collection item have been created.</span></span>  
  
    ```sql  
    USE msdb;  
    SELECT * FROM syscollector_collection_sets;  
    SELECT * FROM syscollector_collection_items;  
    GO  
    ```  
  
     <span data-ttu-id="6a1e2-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で目視で確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-130">You can also do a visual check in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6a1e2-131">オブジェクト エクスプローラーで、 **[管理]** ノードを展開し、 **[データ コレクション]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-131">In Object Explorer, expand the **Management** node, and then expand **Data Collection**.</span></span> <span data-ttu-id="6a1e2-132">新しいコレクション セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-132">The new collection set will be displayed.</span></span> <span data-ttu-id="6a1e2-133">コレクション セットに赤い円のアイコンが付いている場合、コレクション セットが停止されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-133">The red circle icon for the collection set indicates that the collection set is stopped.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a1e2-134">例</span><span class="sxs-lookup"><span data-stu-id="6a1e2-134">Example</span></span>  
 <span data-ttu-id="6a1e2-135">次のコード サンプルは、上記の手順で説明されている例を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-135">The following code sample combines the examples that are documented in the previous steps.</span></span> <span data-ttu-id="6a1e2-136">コレクション セットのコレクション モードはキャッシュ モード (0) に設定されているため、コレクション アイテムに設定された収集頻度 (5 秒) は無視されます。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-136">Note that the collection frequency that is set for the collection item (5 seconds) is ignored because the collection set collection mode is set to 0, which is cached mode.</span></span> <span data-ttu-id="6a1e2-137">詳細については、「 [Data Collection](data-collection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a1e2-137">For more information, see [Data Collection](data-collection.md).</span></span>  
  
```sql  
USE msdb;  
  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier  
  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'DMV Stats Test 1',  
    @collection_mode = 0,  
    @description = N'This is a test collection set',  
    @logging_level=1,  
    @days_until_expiration = 14,  
    @schedule_name=N'CollectorSchedule_Every_15min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
SELECT @collection_set_id,@collection_set_uid;  
  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = collector_type_uid FROM syscollector_collector_types   
WHERE name = N'Generic T-SQL Query Collector Type';  
  
DECLARE @collection_item_id int;  
EXEC sp_syscollector_create_collection_item  
@name= N'Query Stats - Test 1',  
@parameters=N'  
<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
<Query>  
  <Value>select * from sys.dm_exec_query_stats</Value>  
  <OutputTable>dm_exec_query_stats</OutputTable>  
</Query>  
 </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 5, -- This parameter is ignored in cached mode  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid;  
SELECT @collection_item_id;  
  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a1e2-138">参照</span><span class="sxs-lookup"><span data-stu-id="6a1e2-138">See Also</span></span>  
 <span data-ttu-id="6a1e2-139">[データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6a1e2-139">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="6a1e2-140">[[スケジュールの管理]](../../ssms/agent/manage-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="6a1e2-140">[Manage Schedules](../../ssms/agent/manage-schedules.md) </span></span>  
 [<span data-ttu-id="6a1e2-141">コレクション セットの開始または停止</span><span class="sxs-lookup"><span data-stu-id="6a1e2-141">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
  
