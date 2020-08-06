---
title: コレクション アイテムをコレクション セットに追加する (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection items [SQL Server]
- collection sets [SQL Server], adding items
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0b21508761bdfbaf8918242b074f78203c1bcaed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645648"
---
# <a name="add-a-collection-item-to-a-collection-set-transact-sql"></a><span data-ttu-id="fec71-102">コレクション アイテムをコレクション セットに追加する (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fec71-102">Add a Collection Item to a Collection Set (Transact-SQL)</span></span>
  <span data-ttu-id="fec71-103">データ コレクターに備わっているストアド プロシージャを使用して、コレクション アイテムを既存のコレクション セットに追加できます。</span><span class="sxs-lookup"><span data-stu-id="fec71-103">You can add a collection item to an existing collection set using the stored procedures that are provided with the data collector.</span></span>  
  
 <span data-ttu-id="fec71-104">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のクエリ エディターを使用して、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fec71-104">Carry out the following steps using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="add-a-collection-item-to-a-collection-set"></a><span data-ttu-id="fec71-105">コレクション アイテムのコレクション セットへの追加</span><span class="sxs-lookup"><span data-stu-id="fec71-105">Add a collection item to a collection set</span></span>  
  
1.  <span data-ttu-id="fec71-106">**sp_syscollector_stop_collection_set** ストアド プロシージャを実行して、アイテムを追加するコレクション セットを停止します。</span><span class="sxs-lookup"><span data-stu-id="fec71-106">Stop the collection set that you want to add the item to by running the **sp_syscollector_stop_collection_set** stored procedure.</span></span> <span data-ttu-id="fec71-107">たとえば、"Test Collection Set" という名前のコレクション セットを停止するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="fec71-107">For example, to stop a collection set that is named "Test Collection Set", run the following statements:</span></span>  
  
    ```sql  
    USE msdb  
    DECLARE @csid int  
    SELECT @csid = collection_set_id  
    FROM syscollector_collection_sets  
    WHERE name = 'Test Collection Set'  
    SELECT @csid  
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="fec71-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを使用してコレクション セットを停止することもできます。</span><span class="sxs-lookup"><span data-stu-id="fec71-108">You can also stop the collection set by using Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fec71-109">詳細については、「 [コレクション セットの開始または停止](start-or-stop-a-collection-set.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fec71-109">For more information, see [Start or Stop a Collection Set](start-or-stop-a-collection-set.md).</span></span>  
  
2.  <span data-ttu-id="fec71-110">コレクション アイテムを追加するコレクション セットを宣言します。</span><span class="sxs-lookup"><span data-stu-id="fec71-110">Declare the collection set that you want to add the collection item to.</span></span> <span data-ttu-id="fec71-111">次のコードは、コレクション セット ID を宣言する例です。</span><span class="sxs-lookup"><span data-stu-id="fec71-111">The following code provides an example of how to declare the collection set ID.</span></span>  
  
    ```sql  
    DECLARE @collection_set_id_1 int  
    SELECT @collection_set_id_1 = collection_set_id FROM [msdb].[dbo].[syscollector_collection_sets]  
    WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  <span data-ttu-id="fec71-112">コレクター型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="fec71-112">Declare the collector type.</span></span> <span data-ttu-id="fec71-113">次のコードは、ジェネリック T-SQL Query コレクター型を宣言する例です。</span><span class="sxs-lookup"><span data-stu-id="fec71-113">The following code provides an example of how to declare the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid_1 uniqueidentifier  
    SELECT @collector_type_uid_1 = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     <span data-ttu-id="fec71-114">次のコードを実行して、インストールされているコレクター型の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="fec71-114">You can run the following code to obtain a list of the installed collector types:</span></span>  
  
    ```sql  
    USE msdb  
    SELECT * from syscollector_collector_types  
    GO  
    ```  
  
4.  <span data-ttu-id="fec71-115">**sp_syscollector_create_collection_item** ストアド プロシージャを実行してコレクション アイテムを作成します。</span><span class="sxs-lookup"><span data-stu-id="fec71-115">Run the **sp_syscollector_create_collection_item** stored procedure to create the collection item.</span></span> <span data-ttu-id="fec71-116">コレクション アイテムが目的のコレクター型に必要なスキーマにマップされるように、コレクション アイテムのスキーマを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fec71-116">You must declare the schema for the collection item so that it maps to the required schema for the desired collector type.</span></span> <span data-ttu-id="fec71-117">ジェネリック T-SQL Query の入力スキーマを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fec71-117">The following example uses the Generic T-SQL Query input schema.</span></span>  
  
    ```sql  
    DECLARE @collection_item_id int;  
    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
    @name=N'OS Wait Stats', --name of collection item  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
     <Query>  
      <Value>select * from sys.dm_os_wait_stats</Value>  
      <OutputTable>os_wait_stats</OutputTable>  
    </Query>  
    </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 60,  
    @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
    @collector_type_uid = @collector_type_uid_1 -- Provides the collector type UID  
    SELECT @collection_item_id     
    ```  
  
5.  <span data-ttu-id="fec71-118">更新されたコレクション セットを開始する前に、次のクエリを実行して新しいコレクション アイテムが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fec71-118">Before starting the updated collection set, run the following query to verify that the new collection item has been created:</span></span>  
  
    ```xaml  
    USE msdb  
    SELECT * from syscollector_collection_sets  
    SELECT * from syscollector_collection_items  
    GO  
    ```  
  
     <span data-ttu-id="fec71-119">コレクション セットとそのコレクション アイテムは、 **[結果]** タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fec71-119">The collection sets and their collection items are displayed in the **Results** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec71-120">参照</span><span class="sxs-lookup"><span data-stu-id="fec71-120">See Also</span></span>  
 <span data-ttu-id="fec71-121">[ジェネリック T-SQL Query コレクター型を使用するカスタム コレクション セットの作成 &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span><span class="sxs-lookup"><span data-stu-id="fec71-121">[Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span></span>  
 [<span data-ttu-id="fec71-122">データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fec71-122">Data Collector Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
