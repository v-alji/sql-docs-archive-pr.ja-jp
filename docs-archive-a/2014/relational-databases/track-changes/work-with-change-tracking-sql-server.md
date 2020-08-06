---
title: 変更の追跡のしくみ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], making changes
- change tracking [SQL Server], troubleshooting
- updating data [SQL Server]
- troubleshooting [SQL Server], change tracking
- data changes [SQL Server]
- tracking data changes [SQL Server]
- data [SQL Server], changing
- change tracking [SQL Server], data restore
- change tracking [SQL Server], ensuring consistent results
- change tracking [SQL Server], handling changes
ms.assetid: 5aec22ce-ae6f-4048-8a45-59ed05f04dc5
author: rothja
ms.author: jroth
ms.openlocfilehash: bdb8205a789894caf8c8e2d3c3f491751757bab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644917"
---
# <a name="work-with-change-tracking-sql-server"></a><span data-ttu-id="cc584-102">変更の追跡のしくみ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc584-102">Work with Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="cc584-103">変更の追跡を使用するアプリケーションは、追跡した変更を取得し、その変更を別のデータ ストアに適用して、ソース データベースを更新できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-103">Applications that use change tracking must be able to obtain tracked changes, apply these changes to another data store, and update the source database.</span></span> <span data-ttu-id="cc584-104">このトピックでは、これらのタスクの実行方法について説明します。また、フェールオーバーが発生してデータベースをバックアップから復元する必要がある場合に、変更の追跡が果たす役割についても説明します。</span><span class="sxs-lookup"><span data-stu-id="cc584-104">This topic describes how to perform these tasks, and also the role change tracking plays when a failover occurs and a database must be restored from a backup.</span></span>  
  
##  <a name="obtain-changes-by-using-change-tracking-functions"></a><a name="Obtain"></a> <span data-ttu-id="cc584-105">変更追跡関数を使用した変更の取得</span><span class="sxs-lookup"><span data-stu-id="cc584-105">Obtain Changes by Using Change Tracking Functions</span></span>  
 <span data-ttu-id="cc584-106">変更追跡関数を使用して、データベースに加えられた変更およびその変更に関する情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc584-106">Describes how to use the change tracking functions to obtain changes and information about the changes that were made to a database.</span></span>  
  
### <a name="about-the-change-tracking-functions"></a><span data-ttu-id="cc584-107">変更追跡関数について</span><span class="sxs-lookup"><span data-stu-id="cc584-107">About the Change Tracking Functions</span></span>  
 <span data-ttu-id="cc584-108">アプリケーションでは、次の関数を使用して、データベースに加えられた変更およびその変更に関する情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="cc584-108">Applications can use the following functions to obtain the changes that are made in a database and information about the changes:</span></span>  
  
 <span data-ttu-id="cc584-109">CHANGETABLE(CHANGES …) 関数</span><span class="sxs-lookup"><span data-stu-id="cc584-109">CHANGETABLE(CHANGES ...) function</span></span>  
 <span data-ttu-id="cc584-110">変更情報のクエリには、この行セット関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="cc584-110">This rowset function is used to query for change information.</span></span> <span data-ttu-id="cc584-111">この関数は、内部変更追跡テーブルに格納されたデータに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc584-111">The function queries the data stored in the internal change tracking tables.</span></span> <span data-ttu-id="cc584-112">この関数は、変更された行の主キーとその他の変更情報 (該当する操作、更新された列、行のバージョンなど) を含む結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="cc584-112">The function returns a results set that contains the primary keys of rows that have changed together with other change information such as the operation, columns updated and version for the row.</span></span>  
  
 <span data-ttu-id="cc584-113">CHANGETABLE(CHANGES ...) は、最終同期バージョンを引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="cc584-113">CHANGETABLE(CHANGES ...) takes a last synchronization version as an argument.</span></span> <span data-ttu-id="cc584-114">最終同期バージョンは、 `@last_synchronization_version` 変数を使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-114">The last sychronization version is obtained using the `@last_synchronization_version` variable.</span></span> <span data-ttu-id="cc584-115">最終同期バージョンのセマンティクスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc584-115">The semantics of the last synchronization version are as follows:</span></span>  
  
-   <span data-ttu-id="cc584-116">呼び出し元のクライアントは、変更を取得し、最終同期バージョン以前のすべての変更を認識しています。</span><span class="sxs-lookup"><span data-stu-id="cc584-116">The calling client has obtained changes and knows about all changes up to and including the last synchronization version.</span></span>  
  
-   <span data-ttu-id="cc584-117">そのため、CHANGETABLE(CHANGES …) からは、最終同期バージョンより後で発生したすべての変更が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-117">CHANGETABLE(CHANGES ...) will therefore return all changes that have occurred after the last synchronization version.</span></span>  
  
     <span data-ttu-id="cc584-118">次の図は、CHANGETABLE(CHANGES …) を使用して変更を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc584-118">The following illustration shows how CHANGETABLE(CHANGES ...) is used to obtain changes.</span></span>  
  
     <span data-ttu-id="cc584-119">![変更の追跡のクエリ出力の例](../../database-engine/media/queryoutput.gif "変更の追跡のクエリ出力の例")</span><span class="sxs-lookup"><span data-stu-id="cc584-119">![Example of change tracking query output](../../database-engine/media/queryoutput.gif "Example of change tracking query output")</span></span>  
  
 <span data-ttu-id="cc584-120">CHANGE_TRACKING_CURRENT_VERSION() 関数</span><span class="sxs-lookup"><span data-stu-id="cc584-120">CHANGE_TRACKING_CURRENT_VERSION() function</span></span>  
 <span data-ttu-id="cc584-121">この関数を使用すると、現在のバージョンを取得して、次回の変更クエリの際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-121">Is used to obtain the current version that will be used the next time when querying changes.</span></span> <span data-ttu-id="cc584-122">このバージョンは、最後にコミットされたトランザクションのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="cc584-122">This version represents the version of the last committed transaction.</span></span>  
  
 <span data-ttu-id="cc584-123">CHANGE_TRACKING_MIN_VALID_VERSION() 関数</span><span class="sxs-lookup"><span data-stu-id="cc584-123">CHANGE_TRACKING_MIN_VALID_VERSION()function</span></span>  
 <span data-ttu-id="cc584-124">この関数を使用すると、クライアントの有効な最小バージョン (CHANGETABLE() から有効な結果を取得するために最低限必要なバージョン) を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-124">Is used to obtain the minimum valid version that a client can have and still obtain valid results from CHANGETABLE().</span></span> <span data-ttu-id="cc584-125">クライアントは、この関数から返される値に対して最終同期バージョンをチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-125">The client should check the last synchronization version against the value thatis returned by this function.</span></span> <span data-ttu-id="cc584-126">最終同期バージョンがこの関数から返されたバージョンより小さいと、クライアントは CHANGETABLE() から有効な結果を取得できないため、再初期化が必要になります。</span><span class="sxs-lookup"><span data-stu-id="cc584-126">If the last synchronization version is less than the version returned by this function, the client will be unable to obtain valid results from CHANGETABLE() and will have to reinitialize.</span></span>  
  
### <a name="obtaining-initial-data"></a><span data-ttu-id="cc584-127">初期データの取得</span><span class="sxs-lookup"><span data-stu-id="cc584-127">Obtaining Initial Data</span></span>  
 <span data-ttu-id="cc584-128">アプリケーションで初めて変更を取得する前に、クエリを送信して初期データおよび同期バージョンを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-128">Before an application can obtain changes for the first time, the application must send a query to obtain the initial data and the synchronization version.</span></span> <span data-ttu-id="cc584-129">アプリケーションで適切なデータをテーブルから直接取得してから、CHANGE_TRACKING_CURRENT_VERSION() を使用して初期バージョンを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-129">The application must obtain the appropriate data directly from the table, and then use CHANGE_TRACKING_CURRENT_VERSION() to obtain the initial version.</span></span> <span data-ttu-id="cc584-130">このバージョンは、初めて変更を取得するときに CHANGETABLE(CHANGES …) に渡されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-130">This version will be passed to CHANGETABLE(CHANGES ...) the first time that changes are obtained.</span></span>  
  
 <span data-ttu-id="cc584-131">次の例は、初期同期バージョンと初期データセットを取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc584-131">The following example shows how to obtain the initial synchronization version and the initial data set.</span></span>  
  
```sql  
    -- Obtain the current synchronization version. This will be used next time that changes are obtained.  
    SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
    -- Obtain initial data set.  
    SELECT  
        P.ProductID, P.Name, P.ListPrice  
    FROM  
        SalesLT.Product AS P  
```  
  
### <a name="using-the-change-tracking-functions-to-obtain-changes"></a><span data-ttu-id="cc584-132">変更追跡関数を使用した変更の取得</span><span class="sxs-lookup"><span data-stu-id="cc584-132">Using the Change Tracking Functions to Obtain Changes</span></span>  
 <span data-ttu-id="cc584-133">テーブルの変更された行およびその変更に関する情報を取得するには、CHANGETABLE(CHANGES…) を使用します。たとえば、次のクエリは、 `SalesLT.Product` テーブルの変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-133">To obtain the changed rows for a table and information about the changes, use CHANGETABLE(CHANGES...). For example, the following query obtains changes for the `SalesLT.Product` table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, CT.SYS_CHANGE_OPERATION,  
    CT.SYS_CHANGE_COLUMNS, CT.SYS_CHANGE_CONTEXT  
FROM  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
  
```  
  
 <span data-ttu-id="cc584-134">通常、クライアントでは、行の主キーだけでなく、行の最新のデータを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-134">Usually, a client will want to obtain the latest data for a row instead of only the primary keys for the row.</span></span> <span data-ttu-id="cc584-135">そのため、アプリケーションで CHANGETABLE(CHANGES …) の結果をユーザー テーブルのデータと結合します。</span><span class="sxs-lookup"><span data-stu-id="cc584-135">Therefore, an application would join the results from CHANGETABLE(CHANGES ...) with the data in the user table.</span></span> <span data-ttu-id="cc584-136">たとえば、次のクエリでは、 `SalesLT.Product` テーブルと結合して、 `Name` 列と `ListPrice` 列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-136">For example, the following query joins with the `SalesLT.Product` table to obtain the values for the `Name` and `ListPrice` columns.</span></span> <span data-ttu-id="cc584-137">`OUTER JOIN`が使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc584-137">Note the use of `OUTER JOIN`.</span></span> <span data-ttu-id="cc584-138">これは、ユーザー テーブルから削除された行の変更情報が返されるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="cc584-138">This is required to make sure that the change information is returned for those rows that have been deleted from the user table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
 <span data-ttu-id="cc584-139">次回の変更の列挙で使用するバージョンを取得するには、次の例に示すように、CHANGE_TRACKING_CURRENT_VERSION() を使用します。</span><span class="sxs-lookup"><span data-stu-id="cc584-139">To obtain the version for use in the next change enumeration, use CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION()  
```  
  
 <span data-ttu-id="cc584-140">アプリケーションで変更を取得する際は、次の例に示すように、CHANGETABLE(CHANGES…) と CHANGE_TRACKING_CURRENT_VERSION() の両方を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-140">When an application obtains changes, it must use both CHANGETABLE(CHANGES...) and CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
-- Obtain the current synchronization version. This will be used the next time CHANGETABLE(CHANGES...) is called.  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
-- Obtain incremental changes by using the synchronization version obtained the last time the data was synchronized.  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
### <a name="version-numbers"></a><span data-ttu-id="cc584-141">バージョン番号</span><span class="sxs-lookup"><span data-stu-id="cc584-141">Version Numbers</span></span>  
 <span data-ttu-id="cc584-142">変更の追跡が有効になっているデータベースにはバージョン カウンターがあり、変更追跡対象テーブルに変更が加えられるたびに値が増加します。</span><span class="sxs-lookup"><span data-stu-id="cc584-142">A database that has change tracking enabled has a version counter that increases as changes are made to change tracked tables.</span></span> <span data-ttu-id="cc584-143">変更された各行には、バージョン番号が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="cc584-143">Each changed row has a version number that is associated with it.</span></span> <span data-ttu-id="cc584-144">変更のクエリを実行する要求がアプリケーションに送信されると、バージョン番号を提供する関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-144">When a request is sent to an application to query for changes, a function is called that supplies a version number.</span></span> <span data-ttu-id="cc584-145">この関数により、そのバージョン以降に行われたすべての変更に関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-145">The function returns information about all the changes that have been made since that version.</span></span> <span data-ttu-id="cc584-146">変更追跡バージョンは、`rowversion` データ型の概念といくつかの点で似ている部分があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-146">In some ways, change tracking version is similar in concept to the `rowversion` data type.</span></span>  
  
### <a name="validating-the-last-synchronized-version"></a><span data-ttu-id="cc584-147">最終同期バージョンの検証</span><span class="sxs-lookup"><span data-stu-id="cc584-147">Validating the Last Synchronized Version</span></span>  
 <span data-ttu-id="cc584-148">変更に関する情報を保持する期間には制限があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-148">Information about changes is maintained for a limited time.</span></span> <span data-ttu-id="cc584-149">期間の長さは、ALTER DATABASE の一部として指定できる CHANGE_RETENTION パラメーターで制御されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-149">The length of time is controlled by the CHANGE_RETENTION parameter that can be specified as part of the ALTER DATABASE.</span></span>  
  
 <span data-ttu-id="cc584-150">CHANGE_RETENTION に指定された期間によって、すべてのアプリケーションで、データベースから変更を要求する必要がある頻度が決まることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc584-150">Be aware that the time specified for CHANGE_RETENTION determines how frequently all applications must request changes from the database.</span></span> <span data-ttu-id="cc584-151">*last_synchronization_version* の値がテーブルの有効な最小同期バージョンより古い場合、そのアプリケーションでは有効な変更の列挙を実行できません。</span><span class="sxs-lookup"><span data-stu-id="cc584-151">If an application has a value for *last_synchronization_version* that is older than the minimum valid synchronization version for a table, that application cannot perform valid change enumeration.</span></span> <span data-ttu-id="cc584-152">これは、変更情報の一部がクリーンアップされている場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="cc584-152">This is because some change information might have been cleaned up.</span></span> <span data-ttu-id="cc584-153">アプリケーションで CHANGETABLE(CHANGES …) を使用して変更を取得する前に、CHANGETABLE(CHANGES …) に渡す予定の *last_synchronization_version* の値を検証する必要があります。*last_synchronization_version* の値が有効ではない場合は、そのアプリケーションのすべてのデータを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-153">Before an application obtains changes by using CHANGETABLE(CHANGES ...), the application must validate the value for *last_synchronization_version* that it plans to pass to CHANGETABLE(CHANGES ...). If the value of *last_synchronization_version* is not valid, that application must reinitialize all the data.</span></span>  
  
 <span data-ttu-id="cc584-154">次の例では、 `last_synchronization_version` の値の有効性をテーブルごとに検証する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cc584-154">The following example shows how to verify the validity of the value of `last_synchronization_version` for each table.</span></span>  
  
```sql  
-- Check individual table.  
IF (@last_synchronization_version < CHANGE_TRACKING_MIN_VALID_VERSION(  
                                   OBJECT_ID('SalesLT.Product')))  
BEGIN  
  -- Handle invalid version and do not enumerate changes.  
  -- Client must be reinitialized.  
END  
```  
  
 <span data-ttu-id="cc584-155">次の例に示すように、 `last_synchronization_version` の値の有効性は、データベースのすべてのテーブルに対してチェックできます。</span><span class="sxs-lookup"><span data-stu-id="cc584-155">As the following example shows, the validity of the value of `last_synchronization_version` can be checked against all tables in the database.</span></span>  
  
```sql  
-- Check all tables with change tracking enabled  
IF EXISTS (  
  SELECT COUNT(*) FROM sys.change_tracking_tables  
  WHERE min_valid_version > @last_synchronization_version )  
BEGIN  
  -- Handle invalid version & do not enumerate changes  
  -- Client must be reinitialized  
END  
```  
  
### <a name="using-column-tracking"></a><span data-ttu-id="cc584-156">列追跡の使用</span><span class="sxs-lookup"><span data-stu-id="cc584-156">Using Column Tracking</span></span>  
 <span data-ttu-id="cc584-157">列追跡を使用すると、行全体ではなく、変更された列のみのデータをアプリケーションで取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-157">Column tracking enables applications to obtain the data for only the columns that have changed instead of the whole row.</span></span> <span data-ttu-id="cc584-158">たとえば、サイズは大きいが変更頻度は低い 1 つ以上の列と、頻繁に変更される他の列で構成されるテーブルのシナリオについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="cc584-158">For example, consider the scenario in which a table has one or more columns that are large, but rarely change; and also has other columns that frequently change.</span></span> <span data-ttu-id="cc584-159">列追跡を使用しない場合、アプリケーションでは行が変更されたことしか判断できないため、大きな列データを含むすべてのデータを同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-159">Without column tracking, an application can only determine that a row has changed and would have to synchronize all the data that includes the large column data.</span></span> <span data-ttu-id="cc584-160">一方、列追跡を使用すると、アプリケーションでは大きな列データが変更されたかどうかを判断し、変更された場合にのみそのデータを同期できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-160">However, by using column tracking, an application can determine whether the large column data changed and only synchronize the data if it has changed.</span></span>  
  
 <span data-ttu-id="cc584-161">列追跡情報は、CHANGETABLE(CHANGES …) 関数によって返される SYS_CHANGE_COLUMNS 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-161">Column tracking information appears in the SYS_CHANGE_COLUMNS column that is returned by the CHANGETABLE(CHANGES ...) function.</span></span>  
  
 <span data-ttu-id="cc584-162">列追跡を使用すると、変更されていない列に対して NULL が返されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="cc584-162">Column tracking can be used so that NULL is returned for a column that has not changed.</span></span> <span data-ttu-id="cc584-163">NULL に変更できる列の場合は、別々に列を返してその列が変更されたかどうかを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-163">If the column can be changed to NULL, a separate column must be returned to indicate whether the column changed.</span></span>  
  
 <span data-ttu-id="cc584-164">次の例では、 `CT_ThumbnailPhoto` 列は、変更されていない場合は `NULL` になります。</span><span class="sxs-lookup"><span data-stu-id="cc584-164">In the following example, the `CT_ThumbnailPhoto` column will be `NULL` if that column did not change.</span></span> <span data-ttu-id="cc584-165">この列は `NULL` に変更された場合にも `NULL` になりますが、アプリケーションでは `CT_ThumbNailPhoto_Changed` 列を使用して、列が変更されたかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-165">This column could also be `NULL` because it was changed to `NULL` - the application can use the `CT_ThumbNailPhoto_Changed` column to determine whether the column changed.</span></span>  
  
```sql  
DECLARE @PhotoColumnId int = COLUMNPROPERTY(  
    OBJECT_ID('SalesLT.Product'),'ThumbNailPhoto', 'ColumnId')  
  
SELECT  
    CT.ProductID, P.Name, P.ListPrice, -- Always obtain values.  
    CASE  
           WHEN CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) = 1  
            THEN ThumbNailPhoto  
            ELSE NULL  
      END AS CT_ThumbNailPhoto,  
      CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) AS  
                                   CT_ThumbNailPhoto_Changed  
     CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
     CT.SYS_CHANGE_CONTEXT  
FROM  
     SalesLT.Product AS P  
INNER JOIN  
     CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
     P.ProductID = CT.ProductID AND  
     CT.SYS_CHANGE_OPERATION = 'U'  
```  
  
### <a name="obtaining-consistent-and-correct-results"></a><span data-ttu-id="cc584-166">一貫性のある正しい結果の取得</span><span class="sxs-lookup"><span data-stu-id="cc584-166">Obtaining Consistent and Correct Results</span></span>  
 <span data-ttu-id="cc584-167">テーブルの変更されたデータを取得するには、複数の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-167">Obtaining the changed data for a table requires multiple steps.</span></span> <span data-ttu-id="cc584-168">特定の問題について考慮して対処しないと、一貫性のない結果や正しくない結果が返される可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc584-168">Be aware that inconsistent or incorrect results could be returned if certain issues are not considered and handled.</span></span>  
  
 <span data-ttu-id="cc584-169">たとえば、Sales テーブルと SalesOrders テーブルに対して行われた変更を取得するには、アプリケーションで次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc584-169">For example, to obtain the changes that were made to a Sales table and SalesOrders table, an application would perform the following steps:</span></span>  
  
1.  <span data-ttu-id="cc584-170">CHANGE_TRACKING_MIN_VALID_VERSION() を使用して最終同期バージョンを検証します。</span><span class="sxs-lookup"><span data-stu-id="cc584-170">Validate the last synchronized version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
2.  <span data-ttu-id="cc584-171">CHANGE_TRACKING_CURRENT_VERSION() を使用して、次回の変更の取得の際に使用できるバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-171">Obtain the version that can be used to obtain change the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
3.  <span data-ttu-id="cc584-172">CHANGETABLE(CHANGES ...) を使用して Sales テーブルの変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-172">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...).</span></span>  
  
4.  <span data-ttu-id="cc584-173">CHANGETABLE(CHANGES ...) を使用して SalesOrders テーブルの変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-173">Obtain the changes for the SalesOrders table by using CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="cc584-174">データベースで実行される次の 2 つのプロセスが、上記の手順で返される結果に影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-174">Two processes are occurring in the database that can affect the results that are returned by the previous steps:</span></span>  
  
-   <span data-ttu-id="cc584-175">バックグラウンドでクリーンアップ プロセスが実行され、指定した保有期間より古い変更追跡情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-175">The cleanup process runs in the background and removes change tracking information that is older than the specified retention period.</span></span>  
  
     <span data-ttu-id="cc584-176">クリーンアップ プロセスは、データベースの変更の追跡を構成したときに指定した保有期間を使用する個別のバックグラウンド プロセスです。</span><span class="sxs-lookup"><span data-stu-id="cc584-176">The cleanup process is a separate background process that uses the retention period that is specified when you configure change tracking for the database.</span></span> <span data-ttu-id="cc584-177">問題になるのは、最終同期バージョンが検証されてから CHANGETABLE(CHANGES…) の呼び出しが行われるまでの間にクリーンアップ プロセスが実行された場合です。</span><span class="sxs-lookup"><span data-stu-id="cc584-177">The issue is that the cleanup process can occur in the time between when the last synchronization version was validated and when the call to CHANGETABLE(CHANGES...) is made.</span></span> <span data-ttu-id="cc584-178">検証の時点で有効だった最終同期バージョンが、変更の取得時には有効ではなくなっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-178">A last synchronization version that was just valid might no longer be valid by the time the changes are obtained.</span></span> <span data-ttu-id="cc584-179">そのため、正しくない結果が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-179">Therefore, incorrect results might be returned.</span></span>  
  
-   <span data-ttu-id="cc584-180">継続的な DML 操作として、Sales テーブルと SalesOrders テーブルで次のような操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-180">Ongoing DML operations are occurring in the Sales and SalesOrders tables, such as the following operations:</span></span>  
  
    -   <span data-ttu-id="cc584-181">CHANGE_TRACKING_CURRENT_VERSION() を使用して次回のバージョンが取得された後に、テーブルに対して変更が行われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-181">Changes can be made to the tables after the version for next time has been obtained by using CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="cc584-182">そのため、予想よりも多くの変更が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-182">Therefore, more changes can be returned than expected.</span></span>  
  
    -   <span data-ttu-id="cc584-183">Sales テーブルから変更を取得する呼び出しと、SalesOrders テーブルから変更を取得する呼び出しの間に、トランザクションがコミットされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-183">A transaction could commit in the time between the call to obtain changes from the Sales table and the call to obtain changes from the SalesOrders table.</span></span> <span data-ttu-id="cc584-184">そのため、SalesOrder テーブルの結果に、Sales テーブルには存在しない外部キー値が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-184">Therefore, the results for the SalesOrder table could have foreign key value that does not exist in the Sales table.</span></span>  
  
 <span data-ttu-id="cc584-185">上記の課題を解決するには、スナップショット分離を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cc584-185">To overcome the previously listed challenges, we recommend that you use snapshot isolation.</span></span> <span data-ttu-id="cc584-186">これにより、変更情報の一貫性を確保し、バックグラウンドのクリーンアップ タスクに関連する競合状態を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="cc584-186">This will help to ensure consistency of change information and avoid race conditions that are related to the background cleanup task.</span></span> <span data-ttu-id="cc584-187">スナップショット トランザクションを使用しないと、変更の追跡を使用するアプリケーションの開発にかかる手間が大幅に増えることがあります。</span><span class="sxs-lookup"><span data-stu-id="cc584-187">If you do not use snapshot transactions, developing an application that uses change tracking could require significantly more effort.</span></span>  
  
#### <a name="using-snapshot-isolation"></a><span data-ttu-id="cc584-188">スナップショット分離の使用</span><span class="sxs-lookup"><span data-stu-id="cc584-188">Using Snapshot Isolation</span></span>  
 <span data-ttu-id="cc584-189">変更の追跡は、スナップショット分離でも適切に機能するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="cc584-189">Change tracking has been designed to work well with snapshot isolation.</span></span> <span data-ttu-id="cc584-190">データベースに対してスナップショット分離を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-190">Snapshot isolation must be enabled for the database.</span></span> <span data-ttu-id="cc584-191">また、変更の取得に必要なすべての手順がスナップショット トランザクション内に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-191">All the steps that are required to obtain changes must be included inside a snapshot transaction.</span></span> <span data-ttu-id="cc584-192">これにより、変更の取得中にデータに対して行われたすべての変更が、スナップショット トランザクション内のクエリからは認識されなくなります。</span><span class="sxs-lookup"><span data-stu-id="cc584-192">This will ensure that all changes that are made to data while obtaining changes will not be visible to the queries inside the snapshot transaction.</span></span>  
  
 <span data-ttu-id="cc584-193">スナップショット トランザクション内でデータを取得するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc584-193">To obtain data inside a snapshot transaction, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="cc584-194">トランザクション分離レベルをスナップショットに設定し、トランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="cc584-194">Set the transaction isolation level to snapshot and start a transaction.</span></span>  
  
2.  <span data-ttu-id="cc584-195">CHANGE_TRACKING_MIN_VALID_VERSION() を使用して最終同期バージョンを検証します。</span><span class="sxs-lookup"><span data-stu-id="cc584-195">Validate the last synchronization version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
3.  <span data-ttu-id="cc584-196">CHANGE_TRACKING_CURRENT_VERSION() を使用して、次回使用するバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-196">Obtain the version to be used the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
4.  <span data-ttu-id="cc584-197">CHANGETABLE(CHANGES …) を使用して Sales テーブルの変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-197">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...)</span></span>  
  
5.  <span data-ttu-id="cc584-198">CHANGETABLE(CHANGES ...) を使用して SalesOrders テーブルの変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-198">Obtain the changes for the Salesorders table by using CHANGETABLE(CHANGES ...)</span></span>  
  
6.  <span data-ttu-id="cc584-199">トランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="cc584-199">Commit the transaction.</span></span>  
  
 <span data-ttu-id="cc584-200">変更を取得するすべての手順がスナップショット トランザクション内で行われるため、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc584-200">Some points to remember as all steps to obtain changes are inside a snapshot transaction:</span></span>  
  
-   <span data-ttu-id="cc584-201">最終同期バージョンの検証後にクリーンアップが実行された場合でも、クリーンアップで実行された削除操作がトランザクション内からは認識されないため、CHANGETABLE(CHANGES ...) から有効な結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-201">If cleanup occurs after the last synchronization version is validated, the results from CHANGETABLE(CHANGES ...) will still be valid as the delete operations performed by cleanup will not be visible inside the transaction.</span></span>  
  
-   <span data-ttu-id="cc584-202">次回の同期バージョンの取得後に Sales テーブルまたは SalesOrders テーブルに対して行われた変更は認識されません。そのため、CHANGETABLE(CHANGES ...) の呼び出しで、CHANGE_TRACKING_CURRENT_VERSION() によって返されたバージョンより後の変更は返されません。</span><span class="sxs-lookup"><span data-stu-id="cc584-202">Any changes that are made to the Sales table or the SalesOrders table after the next synchronization version is obtained will not be visible, and the calls to CHANGETABLE(CHANGES ...) will never return changes with a version later than that returned by CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="cc584-203">また、Sales テーブルと SalesOrders テーブルの間の一貫性も保持されます。それぞれの CHANGETABLE(CHANGES …) の呼び出しの間にコミットされたトランザクションが認識されないためです。</span><span class="sxs-lookup"><span data-stu-id="cc584-203">Consistency between the Sales table and the SalesOrders table will also be maintained, because the transactions that were committed in the time between calls to CHANGETABLE(CHANGES ...) will not be visible.</span></span>  
  
 <span data-ttu-id="cc584-204">次の例では、データベースに対してスナップショット分離を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cc584-204">The following example shows how snapshot isolation is enabled for a database.</span></span>  
  
```sql  
-- The database must be configured to enable snapshot isolation.  
ALTER DATABASE AdventureWorksLT  
    SET ALLOW_SNAPSHOT_ISOLATION ON;  
```  
  
 <span data-ttu-id="cc584-205">スナップショット トランザクションは次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="cc584-205">A snapshot transaction is used as follows:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
  -- Verify that version of the previous synchronization is valid.  
  -- Obtain the version to use next time.  
  -- Obtain changes.  
COMMIT TRAN  
```  
  
 <span data-ttu-id="cc584-206">スナップショット トランザクションの詳細については、「[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc584-206">For more information about snapshot transactions, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
#### <a name="alternatives-to-using-snapshot-isolation"></a><span data-ttu-id="cc584-207">スナップショット分離の使用に代わる方法</span><span class="sxs-lookup"><span data-stu-id="cc584-207">Alternatives to Using Snapshot Isolation</span></span>  
 <span data-ttu-id="cc584-208">スナップショット分離の使用に代わる方法がありますが、すべてのアプリケーション要件を満たしていることを確認するための作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="cc584-208">There are alternatives to using snapshot isolation, but they require more work to make sure all application requirements are met.</span></span> <span data-ttu-id="cc584-209">*last_synchronization_version* が有効であり、クリーンアップ プロセスでデータが削除されていないことを変更の取得前に確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc584-209">To make sure the *last_synchronization_version* is valid and data is not removed by the cleanup process before changes are obtained, do the following:</span></span>  
  
1.  <span data-ttu-id="cc584-210">CHANGETABLE() の呼び出し後に *last_synchronization_version* を確認します。</span><span class="sxs-lookup"><span data-stu-id="cc584-210">Check *last_synchronization_version* after the calls to CHANGETABLE().</span></span>  
  
2.  <span data-ttu-id="cc584-211">CHANGETABLE() を使用して変更を取得する各クエリで、その一部として *last_synchronization_version* を確認します。</span><span class="sxs-lookup"><span data-stu-id="cc584-211">Check *last_synchronization_version* as part of each query to obtain changes by using CHANGETABLE().</span></span>  
  
 <span data-ttu-id="cc584-212">次回の列挙の同期バージョンが取得された後に変更が行われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-212">Changes can occur after the synchronization version for the next enumeration has been obtained.</span></span> <span data-ttu-id="cc584-213">この状況に対処するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-213">There are two ways to handle this situation.</span></span> <span data-ttu-id="cc584-214">使用するオプションは、アプリケーションおよび各方法の副作用への対処方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cc584-214">The option that is used depends on the application and how it can handle the side-effects of each approach:</span></span>  
  
-   <span data-ttu-id="cc584-215">新しい同期バージョンよりバージョンが大きい変更を無視します。</span><span class="sxs-lookup"><span data-stu-id="cc584-215">Ignore changes that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="cc584-216">この方法の副作用として、新しい同期バージョンより前に行が作成または更新された場合、新しい行や更新された行がスキップされ、後で更新されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-216">This approach has the side effect that a new or updated row would be skipped if it was created or updated before the new synchronization version, but then updated afterward.</span></span> <span data-ttu-id="cc584-217">新しい行がある場合、作成された別のテーブルにスキップされた行を参照する行があると、参照整合性の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-217">If there is a new row, a referential integrity problem might occur if there was a row in another table that was created that referenced the skipped row.</span></span> <span data-ttu-id="cc584-218">更新された既存の行がある場合、その行はスキップされ、次回まで同期されません。</span><span class="sxs-lookup"><span data-stu-id="cc584-218">If there is an updated existing row, the row will be skipped and not synchronized until the next time.</span></span>  
  
-   <span data-ttu-id="cc584-219">新しい同期バージョンよりバージョンが大きい変更も含め、すべての変更を含めます。</span><span class="sxs-lookup"><span data-stu-id="cc584-219">Include all changes, even those that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="cc584-220">新しい同期バージョンよりバージョンが大きい行は、次回の同期で再度取得されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-220">The rows that have a version larger than the new synchronization version will be obtained again on the next synchronization.</span></span> <span data-ttu-id="cc584-221">アプリケーションでは、このことを想定して対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-221">This must be expected and handled by the application.</span></span>  
  
 <span data-ttu-id="cc584-222">上記の 2 つのオプションに加え、操作に応じて両方を組み合わせた方法を検討することもできます。</span><span class="sxs-lookup"><span data-stu-id="cc584-222">In addition to the previous two options, you can devise approach that combines both options, depending on the operation.</span></span> <span data-ttu-id="cc584-223">たとえば、アプリケーションによっては、次回の同期バージョンより新しい変更 (行の作成または削除) は無視し、更新は無視しないようにすることが最適な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cc584-223">For example, you might want an application for which it is best to ignore changes newer than the next synchronization version in which the row was created or deleted, but updates are not ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc584-224">変更の追跡 (または任意のカスタムの追跡メカニズム) を使用する場合にアプリケーションで使用する方法を選択する際には、十分な分析が必要です。</span><span class="sxs-lookup"><span data-stu-id="cc584-224">Choosing the approach that will work for the application when you are using change tracking (or any custom tracking mechanism), requires significant analysis.</span></span> <span data-ttu-id="cc584-225">したがって、スナップショット分離を使用した方がはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="cc584-225">Therefore, it is much simpler to use snapshot isolation.</span></span>  
  
##  <a name="how-change-tracking-handles-changes-to-a-database"></a><a name="Handles"></a><span data-ttu-id="cc584-226">Change Tracking がデータベースへの変更を処理する方法</span><span class="sxs-lookup"><span data-stu-id="cc584-226">How Change Tracking Handles Changes to a Database</span></span>  
 <span data-ttu-id="cc584-227">変更の追跡を使用するアプリケーションの中には、別のデータ ストアとの双方向の同期を行うものもあります。</span><span class="sxs-lookup"><span data-stu-id="cc584-227">Some applications that use change tracking perform two-way synchronization with another data store.</span></span> <span data-ttu-id="cc584-228">この場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースで行われた変更が他のデータ ストアで更新され、他のデータ ストアで行われた変更が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースで更新されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-228">That is, changes that are made in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database are updated in the other data store, and changes that are made in the other store are updated in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="cc584-229">別のデータ ストアからの変更でローカル データベースを更新する際には、アプリケーションで次の操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-229">When an application updates the local database with changes from another data store, the application must perform the following operations:</span></span>  
  
-   <span data-ttu-id="cc584-230">競合がないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="cc584-230">Check for conflicts.</span></span>  
  
     <span data-ttu-id="cc584-231">両方のデータ ストアで同じデータが同時に変更されると、競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="cc584-231">A conflict occurs when the same data is changed at the same time in both data stores.</span></span> <span data-ttu-id="cc584-232">アプリケーションで、競合がないかどうかを確認したり、競合を解決するための十分な情報を取得したりできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-232">The application must be able to check for a conflict and obtain enough information to enable the conflict to be resolved.</span></span>  
  
-   <span data-ttu-id="cc584-233">アプリケーション コンテキスト情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="cc584-233">Store application context information.</span></span>  
  
     <span data-ttu-id="cc584-234">変更追跡情報を持つデータをアプリケーションで格納します。</span><span class="sxs-lookup"><span data-stu-id="cc584-234">The application stores data that has the change tracking information.</span></span> <span data-ttu-id="cc584-235">この情報は、変更がローカル データベースから取得されるときに他の変更追跡情報と共に取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-235">This information would be available together with other change tracking information when changes were obtained from the local database.</span></span> <span data-ttu-id="cc584-236">たとえば変更のソースとなったデータ ストアの ID は、このコンテキスト情報の一例です。</span><span class="sxs-lookup"><span data-stu-id="cc584-236">A common example of this contextual information is an identifier for the data store that was the source of the change.</span></span>  
  
 <span data-ttu-id="cc584-237">同期アプリケーションでこれらの操作を実行するには、次の関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-237">To perform the previous operations, a synchronization application can use the following functions:</span></span>  
  
-   <span data-ttu-id="cc584-238">CHANGETABLE(VERSION...)</span><span class="sxs-lookup"><span data-stu-id="cc584-238">CHANGETABLE(VERSION...)</span></span>  
  
     <span data-ttu-id="cc584-239">アプリケーションで変更を加える際にこの関数を使用すると、競合がないかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-239">When an application is making changes, it can use this function to check for conflicts.</span></span> <span data-ttu-id="cc584-240">この関数は、変更追跡対象テーブルの指定された行に関する最新の変更追跡情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-240">The function obtains the latest change tracking information for a specified row in a change tracked table.</span></span> <span data-ttu-id="cc584-241">この変更追跡情報には、最後に変更された行のバージョンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc584-241">The change tracking information includes the version of the row that was last changed.</span></span> <span data-ttu-id="cc584-242">この情報をアプリケーションで使用することによって、アプリケーションの前回の同期後に行が変更されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-242">This information enables an application to determine whether the row was changed after the last time that the application was synchronized.</span></span>  
  
-   <span data-ttu-id="cc584-243">WITH CHANGE_TRACKING_CONTEXT</span><span class="sxs-lookup"><span data-stu-id="cc584-243">WITH CHANGE_TRACKING_CONTEXT</span></span>  
  
     <span data-ttu-id="cc584-244">アプリケーションでこの句を使用すると、コンテキスト データを格納できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-244">An application can use this clause to store context data.</span></span>  
  
### <a name="checking-for-conflicts"></a><span data-ttu-id="cc584-245">競合の確認</span><span class="sxs-lookup"><span data-stu-id="cc584-245">Checking for Conflicts</span></span>  
 <span data-ttu-id="cc584-246">双方向同期のシナリオでは、前回変更を取得してから行が更新されていないかどうかをクライアント アプリケーションで確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-246">In a two-way synchronization scenario, the client application must determine whether a row has not been updated since the application last obtained the changes.</span></span>  
  
 <span data-ttu-id="cc584-247">次の例は、CHANGETABLE(VERSION ...) 関数を使用して最も効率的に (別のクエリを使用せずに) 競合を確認する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc584-247">The following example shows how to use the CHANGETABLE(VERSION ...) function to check for conflicts in the most efficient way, without a separate query.</span></span> <span data-ttu-id="cc584-248">この例では、 `CHANGETABLE(VERSION ...)` が、 `SYS_CHANGE_VERSION` で指定される行の `@product id`を判別します。</span><span class="sxs-lookup"><span data-stu-id="cc584-248">In the example, `CHANGETABLE(VERSION ...)` determines the `SYS_CHANGE_VERSION` for the row specified by `@product id`.</span></span> <span data-ttu-id="cc584-249">`CHANGETABLE(CHANGES ...)` でも同じ情報を取得できますが、効率が下がります。</span><span class="sxs-lookup"><span data-stu-id="cc584-249">`CHANGETABLE(CHANGES ...)` can obtain the same information, but that would be less efficient.</span></span> <span data-ttu-id="cc584-250">行の `SYS_CHANGE_VERSION` の値が `@last_sync_version`の値より大きい場合は競合があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-250">If the value of `SYS_CHANGE_VERSION` for the row is larger than the value of `@last_sync_version`, there is a conflict.</span></span> <span data-ttu-id="cc584-251">競合がある場合、行は更新されません。</span><span class="sxs-lookup"><span data-stu-id="cc584-251">If there is a conflict, the row will not be updated.</span></span> <span data-ttu-id="cc584-252">`ISNULL()` の確認が必要なのは、行の変更情報がない場合もあるためです。</span><span class="sxs-lookup"><span data-stu-id="cc584-252">The `ISNULL()` check is required because there might be no change information available for the row.</span></span> <span data-ttu-id="cc584-253">変更の追跡を有効にしてからまだ行が更新されていない場合や、変更情報がクリーンアップされてからまだ行が更新されていない場合は、変更情報は存在しません。</span><span class="sxs-lookup"><span data-stu-id="cc584-253">No change information would exist if the row had not been updated since change tracking was enabled or since the change information was cleaned up.</span></span>  
  
```sql  
-- Assumption: @last_sync_version has been validated.  
  
UPDATE  
    SalesLT.Product  
SET  
    ListPrice = @new_listprice  
FROM  
    SalesLT.Product AS P  
WHERE  
    ProductID = @product_id AND  
    @last_sync_version >= ISNULL (  
        SELECT CT.SYS_CHANGE_VERSION  
        FROM CHANGETABLE(VERSION SalesLT.Product,  
                        (ProductID), (P.ProductID)) AS CT),  
        0)  
```  
  
 <span data-ttu-id="cc584-254">次のコードでは、更新された行の数を確認して、競合に関する詳細情報を特定できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-254">The following code can check the updated row count and can identify more information about the conflict.</span></span>  
  
```sql  
-- If the change cannot be made, find out more information.  
IF (@@ROWCOUNT = 0)  
BEGIN  
    -- Obtain the complete change information for the row.  
    SELECT  
        CT.SYS_CHANGE_VERSION, CT.SYS_CHANGE_CREATION_VERSION,  
        CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS  
    FROM  
        CHANGETABLE(CHANGES SalesLT.Product, @last_sync_version) AS CT  
    WHERE  
        CT.ProductID = @product_id;  
  
    -- Check CT.SYS_CHANGE_VERSION to verify that it really was a conflict.  
    -- Check CT.SYS_CHANGE_OPERATION to determine the type of conflict:  
    -- update-update or update-delete.  
    -- The row that is specified by @product_id might no longer exist   
    -- if it has been deleted.  
END  
```  
  
### <a name="setting-context-information"></a><span data-ttu-id="cc584-255">コンテキスト情報の設定</span><span class="sxs-lookup"><span data-stu-id="cc584-255">Setting Context Information</span></span>  
 <span data-ttu-id="cc584-256">WITH CHANGE_TRACKING_CONTEXT 句を使用すると、アプリケーションで変更情報と一緒にコンテキスト情報を格納できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-256">By using the WITH CHANGE_TRACKING_CONTEXT clause, an application can store context information together with the change information.</span></span> <span data-ttu-id="cc584-257">格納した情報は、CHANGETABLE(CHANGES ...) によって返される SYS_CHANGE_CONTEXT 列から取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc584-257">This information can then be obtained from the SYS_CHANGE_CONTEXT column that is returned by CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="cc584-258">コンテキスト情報は通常、変更のソースを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-258">Context information is typically used to identify the source of the changes.</span></span> <span data-ttu-id="cc584-259">変更のソースを識別できれば、その情報をデータ ストアで使用して、再び同期される際に変更が取得されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="cc584-259">If the source of the change can be identified, that information can be used by a data store to avoid obtaining changes when it synchronizes again.</span></span>  
  
```sql  
  -- Try to update the row and check for a conflict.  
  WITH CHANGE_TRACKING_CONTEXT (@source_id)  
  UPDATE  
     SalesLT.Product  
  SET  
      ListPrice = @new_listprice  
  FROM  
      SalesLT.Product AS P  
  WHERE  
     ProductID = @product_id AND  
     @last_sync_version >= ISNULL (  
         (SELECT CT.SYS_CHANGE_VERSION FROM CHANGETABLE(VERSION SalesLT.Product,  
         (ProductID), (P.ProductID)) AS CT),  
         0)  
```  
  
### <a name="ensuring-consistent-and-correct-results"></a><span data-ttu-id="cc584-260">一貫性のある正しい結果の確保</span><span class="sxs-lookup"><span data-stu-id="cc584-260">Ensuring Consistent and Correct Results</span></span>  
 <span data-ttu-id="cc584-261">アプリケーションで @last_sync_version の値を検証するときには、クリーンアップ プロセスを考慮に入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-261">An application must consider the cleanup process when it validates the value of @last_sync_version.</span></span> <span data-ttu-id="cc584-262">これは、CHANGE_TRACKING_MIN_VALID_VERSION() が呼び出された後、更新が行われる前に、データが削除される可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="cc584-262">This is because data could have been removed after CHANGE_TRACKING_MIN_VALID_VERSION() was called, but before the update was made.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cc584-263">スナップショット分離を使用してスナップショット トランザクション内で変更を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cc584-263">We recommend that you use snapshot isolation and make the changes within a snapshot transaction.</span></span>  
  
```sql  
-- Prerequisite is to ensure ALLOW_SNAPSHOT_ISOLATION is ON for the database.  
  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
    -- Verify that last_sync_version is valid.  
    IF (@last_sync_version <  
CHANGE_TRACKING_MIN_VALID_VERSION(OBJECT_ID('SalesLT.Product')))  
    BEGIN  
       RAISERROR (N'Last_sync_version too old', 16, -1);  
    END  
    ELSE  
    BEGIN  
        -- Try to update the row.  
        -- Check @@ROWCOUNT and check for a conflict.  
    END  
COMMIT TRAN  
```  
  
> [!NOTE]  
>  <span data-ttu-id="cc584-264">スナップショット トランザクション内で更新の対象になっている行は、スナップショット トランザクションの開始後に別のトランザクションで更新されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-264">There is a possibility that the row being updated within the snapshot transaction could have been updated in another transaction after the snapshot transaction was started.</span></span> <span data-ttu-id="cc584-265">この場合はスナップショット分離の更新の競合が発生し、トランザクションは終了します。</span><span class="sxs-lookup"><span data-stu-id="cc584-265">In this case, a snapshot isolation update conflict will occur and lead to the transaction being terminated.</span></span> <span data-ttu-id="cc584-266">この状況が発生した場合は、更新を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="cc584-266">If this happens, retry the update.</span></span> <span data-ttu-id="cc584-267">その結果、変更の追跡の競合が検出されることになり、行は変更されません。</span><span class="sxs-lookup"><span data-stu-id="cc584-267">This will then lead to a change tracking conflict being detected and no rows being changed.</span></span>  
  
##  <a name="change-tracking-and-data-restore"></a><a name="DataRestore"></a><span data-ttu-id="cc584-268">Change Tracking とデータの復元</span><span class="sxs-lookup"><span data-stu-id="cc584-268">Change Tracking and Data Restore</span></span>  
 <span data-ttu-id="cc584-269">同期が必要なアプリケーションでは、変更の追跡が有効になっているデータベースが以前のバージョンのデータに戻るケースを考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-269">Applications that require synchronization must consider the case in which a database that has change tracking enabled reverts to an earlier version of the data.</span></span> <span data-ttu-id="cc584-270">この状況は、非同期データベース ミラーへのフェールオーバーや、ログ配布の使用時のエラーに伴い、データベースがバックアップから復元された後に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc584-270">This can occur after a database is restored from a backup, when there is a failover to an asynchronous database mirror, or when there is a failure when using log shipping.</span></span> <span data-ttu-id="cc584-271">この問題を説明するシナリオを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc584-271">The following scenario illustrates the issue:</span></span>  
  
1.  <span data-ttu-id="cc584-272">テーブル T1 は変更の追跡の対象になっており、このテーブルの有効な最小バージョンは 50 になっています。</span><span class="sxs-lookup"><span data-stu-id="cc584-272">Table T1 is change tracked, and the minimum valid version for table is 50.</span></span>  
  
2.  <span data-ttu-id="cc584-273">クライアント アプリケーションはバージョン 100 でデータを同期し、バージョン 50 とバージョン 100 の間で発生したすべての変更に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-273">A client application synchronizes data at version 100 and obtains information about all changes between versions 50 and 100.</span></span>  
  
3.  <span data-ttu-id="cc584-274">テーブル T1 には、バージョン 100 以降もさらに変更が加えられます。</span><span class="sxs-lookup"><span data-stu-id="cc584-274">Additional changes are made to table T1 after version 100.</span></span>  
  
4.  <span data-ttu-id="cc584-275">バージョン 120 でエラーが発生し、データベース管理者がデータベースを復元しますが、これに伴ってデータ損失が発生します。</span><span class="sxs-lookup"><span data-stu-id="cc584-275">At version 120, there is a failure and the database administrator restores the database with data loss.</span></span> <span data-ttu-id="cc584-276">復元操作の後、テーブルにはバージョン 70 までのデータが格納され、最小同期バージョンは 50 のままになります。</span><span class="sxs-lookup"><span data-stu-id="cc584-276">After the restore operation, the table contains data up through version 70, and the minimum synchronized version is still 50.</span></span>  
  
     <span data-ttu-id="cc584-277">これは、プライマリ データ ストアには存在しないデータが同期データ ストアに含まれることを意味します。</span><span class="sxs-lookup"><span data-stu-id="cc584-277">This means that the synchronized data store has data that no longer exists in the primary data store.</span></span>  
  
5.  <span data-ttu-id="cc584-278">T1 は何度も更新されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-278">T1 is updated many times.</span></span> <span data-ttu-id="cc584-279">その結果、現在のバージョンは 130 になります。</span><span class="sxs-lookup"><span data-stu-id="cc584-279">This brings the current version to 130.</span></span>  
  
6.  <span data-ttu-id="cc584-280">クライアント アプリケーションが再び同期を実行します。このとき、クライアント アプリケーションの最終同期バージョンは 100 になっています。</span><span class="sxs-lookup"><span data-stu-id="cc584-280">The client application synchronizes again and supplies a last-synchronized version of 100.</span></span> <span data-ttu-id="cc584-281">100 は 50 より大きいため、この番号はクライアントの検証を通過します。</span><span class="sxs-lookup"><span data-stu-id="cc584-281">The client validates this number successfully because 100 is greater than 50.</span></span>  
  
     <span data-ttu-id="cc584-282">クライアントはバージョン 100 と 130 の間の変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc584-282">The client obtains changes between version 100 and 130.</span></span> <span data-ttu-id="cc584-283">この時点で、クライアントは 70 と 100 の間の変更が以前と同じではないことを認識していません。</span><span class="sxs-lookup"><span data-stu-id="cc584-283">At this point, the client is not aware that the changes between 70 and 100 are not the same as before.</span></span> <span data-ttu-id="cc584-284">クライアントとサーバーのデータは同期されません。</span><span class="sxs-lookup"><span data-stu-id="cc584-284">The data on the client and server are not synchronized.</span></span>  
  
 <span data-ttu-id="cc584-285">データベースがバージョン 100 より後の時点の状態に復旧された場合は、同期の問題は発生しません。</span><span class="sxs-lookup"><span data-stu-id="cc584-285">Note that if the database was recovered to a point after version 100, there would be no problems with synchronization.</span></span> <span data-ttu-id="cc584-286">クライアントとサーバーのデータは、次の同期間隔の間に正しく同期されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-286">The client and server would synchronize data correctly during the next synchronization interval.</span></span>  
  
 <span data-ttu-id="cc584-287">変更の追跡では、データ損失からの復旧はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cc584-287">Change tracking does not provide support for recovering from the loss of data.</span></span> <span data-ttu-id="cc584-288">ただし、この種の同期の問題を検出する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="cc584-288">However, there are two options for detecting these types of synchronization issues:</span></span>  
  
-   <span data-ttu-id="cc584-289">データベース バージョン ID をサーバーに保存し、データベースの復旧などでデータが失われるたびに、この値を更新する方法。</span><span class="sxs-lookup"><span data-stu-id="cc584-289">Store a database version ID on the server, and update this value whenever a database is recovered or otherwise loses data.</span></span> <span data-ttu-id="cc584-290">この ID を各クライアント アプリケーションに保存し、各クライアントがデータを同期する際に必ず検証されるようにします。</span><span class="sxs-lookup"><span data-stu-id="cc584-290">Each client application would store the ID, and each client would have to validate this ID when it synchronizes data.</span></span> <span data-ttu-id="cc584-291">データ損失が発生した場合は ID が一致しなくなり、クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="cc584-291">If data loss occurs, the IDs will not match and the clients would reinitialize.</span></span> <span data-ttu-id="cc584-292">1 つの欠点は、データ損失が最後に同期された範囲に及んでいない場合に、不要な再初期化が行われる可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="cc584-292">One drawback is if the data loss had not crossed the last synchronized boundary, the client might do unnecessary reinitialization.</span></span>  
  
-   <span data-ttu-id="cc584-293">クライアントが変更クエリを実行した時点で、最終同期バージョンの番号をクライアントごとにサーバー上に記録する方法。</span><span class="sxs-lookup"><span data-stu-id="cc584-293">When a client queries for changes, record the last synchronization version number for each client on the server.</span></span> <span data-ttu-id="cc584-294">データに問題がある場合は、最終同期バージョンの番号が一致しません。</span><span class="sxs-lookup"><span data-stu-id="cc584-294">If there is a problem with the data, the last synchronized version numbers would not match.</span></span> <span data-ttu-id="cc584-295">これによって、再初期化が必要であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="cc584-295">This indicates that a reinitialization is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc584-296">参照</span><span class="sxs-lookup"><span data-stu-id="cc584-296">See Also</span></span>  
 <span data-ttu-id="cc584-297">[データ変更の追跡 &#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc584-297">[Track Data Changes &#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="cc584-298">[変更の追跡について &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc584-298">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="cc584-299">[Change Tracking &#40;SQL Server の管理&#41;](../track-changes/manage-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc584-299">[Manage Change Tracking &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="cc584-300">[Change Tracking &#40;SQL Server を有効または無効にする&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc584-300">[Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="cc584-301">[CHANGETABLE &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc584-301">[CHANGETABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span></span>  
 <span data-ttu-id="cc584-302">[CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc584-302">[CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span></span>  
 <span data-ttu-id="cc584-303">[CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc584-303">[CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span></span>  
 [<span data-ttu-id="cc584-304">WITH CHANGE_TRACKING_CONTEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc584-304">WITH CHANGE_TRACKING_CONTEXT &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/with-change-tracking-context-transact-sql)  
  
  
