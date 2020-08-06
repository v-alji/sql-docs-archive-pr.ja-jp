---
title: 登録されているパッケージのイベントを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5e3665a695bd3f40407a8680872c9b0dc79fbc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645773"
---
# <a name="view-the-events-for-registered-packages"></a><span data-ttu-id="14427-102">登録パッケージのイベントの表示</span><span class="sxs-lookup"><span data-stu-id="14427-102">View the Events for Registered Packages</span></span>
  <span data-ttu-id="14427-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 拡張イベント セッションを作成する前に、登録パッケージで提供されているイベントを確認すると役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="14427-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to find out what events are available in the registered packages.</span></span> <span data-ttu-id="14427-104">詳細については、「 [SQL Server 拡張イベント パッケージ](../relational-databases/extended-events/sql-server-extended-events-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14427-104">For more information, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
 <span data-ttu-id="14427-105">この作業には、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用した次の手順の実行も含まれます。</span><span class="sxs-lookup"><span data-stu-id="14427-105">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
 <span data-ttu-id="14427-106">この手順でステートメントの実行が完了すると、クエリ エディターの **[結果]** タブに次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="14427-106">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="14427-107">name:</span><span class="sxs-lookup"><span data-stu-id="14427-107">name.</span></span> <span data-ttu-id="14427-108">パッケージの名前です。</span><span class="sxs-lookup"><span data-stu-id="14427-108">The package name.</span></span>  
  
-   <span data-ttu-id="14427-109">event:</span><span class="sxs-lookup"><span data-stu-id="14427-109">event.</span></span> <span data-ttu-id="14427-110">イベント名。</span><span class="sxs-lookup"><span data-stu-id="14427-110">The event name.</span></span>  
  
-   <span data-ttu-id="14427-111">keyword:</span><span class="sxs-lookup"><span data-stu-id="14427-111">keyword.</span></span> <span data-ttu-id="14427-112">内部数値マッピング テーブルから派生されたキーワードです。</span><span class="sxs-lookup"><span data-stu-id="14427-112">A keyword derived from an internal numeric mapping table.</span></span>  
  
-   <span data-ttu-id="14427-113">channel:</span><span class="sxs-lookup"><span data-stu-id="14427-113">channel.</span></span> <span data-ttu-id="14427-114">イベントの対象ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="14427-114">The audience for an event.</span></span>  
  
-   <span data-ttu-id="14427-115">description:</span><span class="sxs-lookup"><span data-stu-id="14427-115">description.</span></span> <span data-ttu-id="14427-116">イベントの説明。</span><span class="sxs-lookup"><span data-stu-id="14427-116">The event description.</span></span>  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a><span data-ttu-id="14427-117">クエリ エディターを使用して登録パッケージのイベントを表示するには</span><span class="sxs-lookup"><span data-stu-id="14427-117">To view the events for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="14427-118">クエリ エディターで、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="14427-118">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="14427-119">参照</span><span class="sxs-lookup"><span data-stu-id="14427-119">See Also</span></span>  
 <span data-ttu-id="14427-120">[拡張イベントパッケージの SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="14427-120">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="14427-121">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="14427-121">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="14427-122">sys.dm_xe_packages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="14427-122">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
