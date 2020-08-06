---
title: メモリ最適化テーブル サブスクライバーへのレプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df61b83d2f6d07cbbd21773b8940dd4e5341f76b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631780"
---
# <a name="replication-to-memory-optimized-table-subscribers"></a><span data-ttu-id="dc542-102">メモリ最適化テーブル サブスクライバーへのレプリケーション</span><span class="sxs-lookup"><span data-stu-id="dc542-102">Replication to Memory-Optimized Table Subscribers</span></span>
  <span data-ttu-id="dc542-103">トランザクション レプリケーションのサブスクライバーとして機能するテーブルは、ピア ツー ピア トランザクション レプリケーションを除き、メモリ最適化テーブルとして構成できます。</span><span class="sxs-lookup"><span data-stu-id="dc542-103">Tables acting as transactional replication subscribers, excluding Peer-to-peer transactional replication, can be configured as memory-optimized tables.</span></span> <span data-ttu-id="dc542-104">その他のレプリケーション構成はメモリ最適化テーブルとは互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="dc542-104">Other replication configurations are not compatible with memory-optimized tables.</span></span>  
  
## <a name="configuring-a-memory-optimized-table-as-a-subscriber"></a><span data-ttu-id="dc542-105">サブスクライバーとしてのメモリ最適化テーブルの構成</span><span class="sxs-lookup"><span data-stu-id="dc542-105">Configuring a memory-optimized table as a subscriber</span></span>  
 <span data-ttu-id="dc542-106">サブスクライバーとしてメモリ最適化テーブルを構成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="dc542-106">To configure a memory-optimized table as a subscriber, perform the following steps.</span></span>  
  
 <span data-ttu-id="dc542-107">**パブリケーションを作成して有効にする**</span><span class="sxs-lookup"><span data-stu-id="dc542-107">**Create and Enable Publication**</span></span>  
  
1.  <span data-ttu-id="dc542-108">パブリケーションの作成。</span><span class="sxs-lookup"><span data-stu-id="dc542-108">Create a publication.</span></span>  
  
2.  <span data-ttu-id="dc542-109">パブリケーションにアーティクルを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc542-109">Add articles to the publication.</span></span> <span data-ttu-id="dc542-110">`@upd_cmd` パラメーターには、SCALL または SQL 規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc542-110">For the `@upd_cmd` parameter, use the SCALL or SQL convention.</span></span>  
  
    ```  
    EXEC sp_addarticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @source_owner = N'dbo',  
        @source_object = N'Mem_Table',  
        @type = N'logbased',  
        @description = null,  
        @creation_script = null,  
        @pre_creation_cmd = N'none',  
        @schema_option = 0x00000000080050DF,  
        @identityrangemanagementoption = N'manual',  
        @destination_table = N'Mem_Table',  
        @destination_owner = N'dbo',  
        @vertical_partition = N'false',  
        @ins_cmd = N'CALL sp_MSins_Mem_Table',  
        @del_cmd = N'CALL sp_MSdel_Mem_Table',  
        @upd_cmd = N'SCALL sp_MSupd_Mem_Table';  
    GO  
    ```  
  
 <span data-ttu-id="dc542-111">**スナップショットを生成してスキーマを調整する**</span><span class="sxs-lookup"><span data-stu-id="dc542-111">**Generate a Snapshot and Adjust the Schema**</span></span>  
  
1.  <span data-ttu-id="dc542-112">スナップショット ジョブを作成し、スナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="dc542-112">Create a snapshot job and generate a snapshot.</span></span>  
  
    ```  
    EXEC sp_addpublication_snapshot @publication = N'Publication1', @frequency_type = 1;  
    EXEC sp_startpublication_snapshot @publication = N'Publication1';  
    ```  
  
2.  <span data-ttu-id="dc542-113">スナップショット フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="dc542-113">Navigate to the snapshot folder.</span></span> <span data-ttu-id="dc542-114">既定の場所は "C:\Program Server\MSSQL12. \<INSTANCE> SQL\MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS \\ "。</span><span class="sxs-lookup"><span data-stu-id="dc542-114">The default location is "C:\Program Files\Microsoft SQL Server\MSSQL12.\<INSTANCE>\MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS\\".</span></span>  
  
3.  <span data-ttu-id="dc542-115">を見つけ**ます。** テーブルの sch-m ファイルを開き、Management Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="dc542-115">Locate the **.SCH** file for your table and open it in Management Studio.</span></span> <span data-ttu-id="dc542-116">次に説明するように、テーブル スキーマを変更し、ストアド プロシージャを更新します。</span><span class="sxs-lookup"><span data-stu-id="dc542-116">Change the table schema and update the stored procedure as described below.</span></span>  
  
     <span data-ttu-id="dc542-117">IDX ファイルで定義されているインデックスを評価します。</span><span class="sxs-lookup"><span data-stu-id="dc542-117">Evaluate the indexes defined in the IDX file.</span></span> <span data-ttu-id="dc542-118">必要なインデックス、制約、主キー、メモリ最適化構文を指定するように `CREATE TABLE` を変更します。</span><span class="sxs-lookup"><span data-stu-id="dc542-118">Modify `CREATE TABLE` to specify the required indexes, constraints, primary key, and memory-optimized syntax.</span></span> <span data-ttu-id="dc542-119">メモリ最適化テーブルでは、インデックス列を null にしないでください。文字型のインデックス列は Unicode にし、BIN2 照合順序を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc542-119">For memory-optimized tables, index columns should be NOT NULL and index columns of character types must be Unicode and use BIN2 collation.</span></span> <span data-ttu-id="dc542-120">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc542-120">See example below:</span></span>  
  
    ```  
    SET ANSI_PADDING ON;  
    GO  
  
    SET ANSI_NULLS ON;  
    GO  
  
    SET QUOTED_IDENTIFIER ON;  
    GO  
  
    CREATE TABLE [dbo].[Mem_Table]([c1] [int] NOT NULL,  
        [c2] [float] NOT NULL,  
        [c3] [decimal](10, 2) NOT NULL,  
        [c4] [nvarchar](5) COLLATE SQL_Latin1_General_CP850_BIN2 NOT NULL,  
        INDEX [hash_index_sample_memoryoptimizedtable_c2] HASH (c2) WITH (BUCKET_COUNT = 1024),  
        INDEX [index_sample_memoryoptimizedtable_c3] NONCLUSTERED ([c3]),  
        INDEX [nvarchar_index_sample_memoryoptimizedtable_c4] ([c4]),  
        CONSTRAINT [PK_sample_memoryoptimizedtable] PRIMARY KEY NONCLUSTERED ([c1])) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA);  
    GO  
    ```  
  
4.  <span data-ttu-id="dc542-121">`@upd_cmd` パラメーターに SCALL 規約を使用するときは、スキーマ (.SCH) ファイルに移動し、`create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` でテーブル更新ステートメントを変更して、主キー列を削除します。</span><span class="sxs-lookup"><span data-stu-id="dc542-121">When using SCALL convention for the `@upd_cmd` parameter, go to the schema (.SCH) file and change the table update statement in `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` to remove primary key columns.</span></span>  
  
     <span data-ttu-id="dc542-122">主キーの更新をサポートするには、次のように、カスタムの更新ストアド プロシージャを使用して主キーの更新ステートメントを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dc542-122">To support primary key updates, use a custom update stored procedure to replace the primary key update statement, as follows:</span></span>  
  
    1.  <span data-ttu-id="dc542-123">値のない列を選択します (SCALL では更新操作にかかわる列にのみ値を渡す)。</span><span class="sxs-lookup"><span data-stu-id="dc542-123">Select missing column values (SCALL only provides the column involved into the update operation).</span></span>  
  
    2.  <span data-ttu-id="dc542-124">既存のレコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="dc542-124">Delete the existing record.</span></span>  
  
    3.  <span data-ttu-id="dc542-125">新しいレコードを挿入し、新しい主キーを含む新しい値を渡します。</span><span class="sxs-lookup"><span data-stu-id="dc542-125">Insert a new record with new values provided including the new primary key.</span></span>  
  
     <span data-ttu-id="dc542-126">元の更新プロシージャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dc542-126">The original update procedure looks like this:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
                   [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="dc542-127">主キーがパブリッシャーで更新されない場合。</span><span class="sxs-lookup"><span data-stu-id="dc542-127">If the primary key should never be updated on a publisher.</span></span> <span data-ttu-id="dc542-128">更新プロシージャのこのような列に対する更新を次のようにコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="dc542-128">Comment out the update to such columns in the update procedure as follows:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
    --             [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="dc542-129">主キーの更新のサポートを許可するには、読み取る更新プロシージャを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="dc542-129">To allow the support of updates to the primary key, modify the update procedure to read as follows</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                    @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    select  
                   @c1 = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   @c2 = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   @c3 = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   @c4 = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    from [dbo].[Mem_Table] where [c1] = @pkc1  
    if @@rowcount <> 0 begin  
            delete [dbo].[Mem_Table] where [c1] = @pkc1  
            if @@rowcount <> 0  
                   insert into [dbo].[Mem_Table]([c1],  
                           [c2],  
                           [c3],  
                           [c4]) values (  
                           @c1,  
                           @c2,  
                           @c3,  
                           @c4  
                   )   
    end  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
5.  <span data-ttu-id="dc542-130">[**スナップショット分離に昇格**] オプションを使用してサブスクライバーデータベースを作成し、Unicode 以外の文字データ型を使用する場合は、既定の照合順序を Latin1_General_CS_AS_KS_WS に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc542-130">Create subscriber database using the **elevate to snapshot isolation** option and set the default collation to Latin1_General_CS_AS_KS_WS in case of using non Unicode character data types.</span></span>  
  
    ```  
    CREATE DATABASE [Sub]   
    CONTAINMENT = NONE   
    ON PRIMARY ( NAME = [Sub], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.mdf]),   
    FILEGROUP [mem] CONTAINS MEMORY_OPTIMIZED_DATA ( NAME = [mem],   
    FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub])  
    LOG ON ( NAME = [Sub_log], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.ldf])  
    COLLATE Latin1_General_CS_AS_KS_WS;  
  
    ALTER DATABASE [Sub] SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
    GO  
    ```  
  
6.  <span data-ttu-id="dc542-131">スキーマをサブスクライバーのデータベースに適用し、将来使用するためにスキーマを保存します。</span><span class="sxs-lookup"><span data-stu-id="dc542-131">Apply the schema to a subscriber's database and save the schema for future use.</span></span>  
  
7.  <span data-ttu-id="dc542-132">パブリッシャー (ソース) のデータをサブスクライバーに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="dc542-132">Load the publisher (source) data to the subscriber.</span></span> <span data-ttu-id="dc542-133">サブスクリプションを追加するまで、パブリッシャーでデータを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="dc542-133">Data should not change at the publisher until you add a subscription.</span></span>  <span data-ttu-id="dc542-134">次に示すように BCP を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dc542-134">You can use BCP as shown below:</span></span>  
  
    ```  
    bcp Pub.dbo.Mem_Table out Mem_Table.bcp -S. -T -C1252 -n  
    bcp Sub.dbo.Mem_Table in Mem_Table.bcp -S. -T -C1252 -n  
    ```  
  
8.  <span data-ttu-id="dc542-135">サブスクライバーでのスキーマの変更を無効にするようにアーティクルを再構成します。</span><span class="sxs-lookup"><span data-stu-id="dc542-135">Reconfigure the article to disable schema changes on the subscriber:</span></span>  
  
    ```  
    EXEC sp_changearticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @property = N'schema_option',  
        @value = 0,  
        @force_invalidate_snapshot = 1,  
        @force_reinit_subscription = 1;  
    GO  
    ```  
  
 <span data-ttu-id="dc542-136">**非同期サブスクリプションを追加する**</span><span class="sxs-lookup"><span data-stu-id="dc542-136">**Add no sync Subscription**</span></span>  
  
 <span data-ttu-id="dc542-137">非同期サブスクリプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc542-137">Add a nosync subscription.</span></span>  
  
```  
EXEC sp_addsubscription  
    @publication = N' Publication1',  
    @subscriber = @@ServerName,  
    @destination_db = N'Sub',  
    @subscription_type = N'Push',  
    @sync_type = N'replication support only',  
    @article = N'all',  
    @update_mode = N'read only',  
    @subscriber_type = 0;  
GO  
```  
  
 <span data-ttu-id="dc542-138">これでメモリ最適化テーブルはパブリッシャーから更新を受け取り始めます。</span><span class="sxs-lookup"><span data-stu-id="dc542-138">Memory-optimized tables should now start receiving updates from the publisher.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="dc542-139">制限</span><span class="sxs-lookup"><span data-stu-id="dc542-139">Restrictions</span></span>  
 <span data-ttu-id="dc542-140">一方向トランザクション レプリケーションのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="dc542-140">Only one-way transactional replication is supported.</span></span> <span data-ttu-id="dc542-141">ピア ツー ピア トランザクション レプリケーションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="dc542-141">Peer-to-peer transactional replication is not supported.</span></span>  
  
 <span data-ttu-id="dc542-142">メモリ最適化テーブルをパブリッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="dc542-142">Memory-optimized tables cannot be published.</span></span>  
  
 <span data-ttu-id="dc542-143">ディストリビューターのレプリケーション テーブルをメモリ最適化テーブルとして構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="dc542-143">Replication tables on the distributor cannot be configured as memory-optimized tables.</span></span>  
  
 <span data-ttu-id="dc542-144">マージ レプリケーションにメモリ最適化テーブルを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="dc542-144">Merge replication cannot include memory-optimized tables.</span></span>  
  
 <span data-ttu-id="dc542-145">サブスクライバーで、トランザクション レプリケーションにかかわるテーブルをメモリ最適化テーブルとして構成できますが、サブスクライバーのテーブルはメモリ最適化テーブルの要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc542-145">At the subscriber, tables involved in transactional replication can be configured as memory optimized tables, but the subscriber tables must meet the requirements of memory-optimized tables.</span></span> <span data-ttu-id="dc542-146">この場合の制限事項は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc542-146">This requires the following restrictions.</span></span>  
  
-   <span data-ttu-id="dc542-147">トランザクション レプリケーションのサブスクライバーでメモリ最適化テーブルを作成するには、メモリ最適化テーブルの作成に使用されるスナップショット スキーマ ファイルを手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc542-147">To create a memory-optimized table on a transactional replication subscriber, the snapshot schema files used to create the memory-optimized tables must be manually modified.</span></span> <span data-ttu-id="dc542-148">詳細については、「[スキーマファイルの変更](#Schema)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc542-148">For more information, see [Modifying a schema file](#Schema).</span></span>  
  
-   <span data-ttu-id="dc542-149">サブスクライバーのメモリ最適化テーブルにレプリケートされるテーブルは、メモリ最適化テーブルの行の制限に従って 8,060 バイトに制限されます。</span><span class="sxs-lookup"><span data-stu-id="dc542-149">Tables replicated to memory-optimized tables on a subscriber are limited to the 8060 bytes per row limit of memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="dc542-150">サブスクライバーのメモリ最適化テーブルにレプリケートされるテーブルは、メモリ最適化テーブルに使用できるデータ型に制限されます。</span><span class="sxs-lookup"><span data-stu-id="dc542-150">Tables replicated to memory-optimized tables on a subscriber are limited to the data types permitted in memory-optimized tables.</span></span> <span data-ttu-id="dc542-151">詳細については、「[サポートされるデータ型](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc542-151">For more information, see [Supported Data Types](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md).</span></span>  
  
-   <span data-ttu-id="dc542-152">サブスクライバーのメモリ最適化テーブルにレプリケートされるテーブルの主キーを更新するには、制限があります。</span><span class="sxs-lookup"><span data-stu-id="dc542-152">There are restrictions on updating the primary key of tables being replicated to a memory-optimized table on a subscriber.</span></span> <span data-ttu-id="dc542-153">詳細については、「[主キーへの変更のレプリケート](#PrimaryKey)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc542-153">For more information, see [Replicating changes to a primary key](#PrimaryKey).</span></span>  
  
-   <span data-ttu-id="dc542-154">外部キー、UNIQUE 制約、トリガー、スキーマの変更、ROWGUIDCOL、計算列、データ圧縮、別名データ型、バージョン管理、ロックは、メモリ最適化テーブルではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="dc542-154">Foreign key, unique constraint, triggers, schema modifications, ROWGUIDCOL, computed columns, data compression, alias data types, versioning, and locks are not supported in memory-optimized tables.</span></span> <span data-ttu-id="dc542-155">詳細については、「 [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc542-155">See [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) for information.</span></span>  
  
##  <a name="modifying-a-schema-file"></a><a name="Schema"></a><span data-ttu-id="dc542-156">スキーマファイルの変更</span><span class="sxs-lookup"><span data-stu-id="dc542-156">Modifying a schema file</span></span>  
  
-   <span data-ttu-id="dc542-157">クラスター化インデックスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="dc542-157">Clustered indexes are not supported.</span></span> <span data-ttu-id="dc542-158">クラスター化インデックスを非クラスター化インデックスに変更します。</span><span class="sxs-lookup"><span data-stu-id="dc542-158">Change any clustered indexes to nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="dc542-159">インデックスのキーのすべての列を `NOT NULL` として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc542-159">All columns in the key of an index must be specified as `NOT NULL`.</span></span>  
  
-   <span data-ttu-id="dc542-160">メモリ最適化テーブルのオプション `DURABILITY = SCHEMA_AND_DATA` を使用する場合、テーブルには非クラスター化主キー インデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="dc542-160">If using the memory-optimized table option `DURABILITY = SCHEMA_AND_DATA` the table must have a nonclustered primary key index.</span></span>  
  
-   <span data-ttu-id="dc542-161">ANSI_PADDING は ON にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc542-161">ANSI_PADDING must be ON.</span></span>  
  
##  <a name="replicating-changes-to-a-primary-key"></a><a name="PrimaryKey"></a><span data-ttu-id="dc542-162">主キーへの変更のレプリケート</span><span class="sxs-lookup"><span data-stu-id="dc542-162">Replicating changes to a primary key</span></span>  
 <span data-ttu-id="dc542-163">メモリ最適化テーブルの主キーを更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="dc542-163">The primary key of a memory-optimized table cannot be updated.</span></span> <span data-ttu-id="dc542-164">サブスクライバーの主キーの更新をレプリケートするには、DELETE/INSERT ペアとして更新を渡すように更新ストアド プロシージャを変更します。</span><span class="sxs-lookup"><span data-stu-id="dc542-164">To replicate a primary key update on a subscriber, modify the update stored procedure to deliver the update as a delete and insert pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc542-165">参照</span><span class="sxs-lookup"><span data-stu-id="dc542-165">See Also</span></span>  
 [<span data-ttu-id="dc542-166">SQL Server レプリケーション</span><span class="sxs-lookup"><span data-stu-id="dc542-166">SQL Server Replication</span></span>](sql-server-replication.md)  
  
  
