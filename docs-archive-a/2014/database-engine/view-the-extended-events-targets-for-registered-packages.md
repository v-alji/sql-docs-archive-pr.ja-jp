---
title: 登録されているパッケージの拡張イベントターゲットを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- viewing event targets
- extended events [SQL Server], viewing targets
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e796d141ef943399fc2469c232b34b1956cef3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645772"
---
# <a name="view-the-extended-events-targets-for-registered-packages"></a><span data-ttu-id="6b5f1-102">登録パッケージの拡張イベント ターゲットの表示</span><span class="sxs-lookup"><span data-stu-id="6b5f1-102">View the Extended Events Targets for Registered Packages</span></span>
  <span data-ttu-id="6b5f1-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 拡張イベント セッションを作成する前に、提供されている拡張イベント ターゲットを確認すると役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="6b5f1-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to determine what Extended Events targets are available.</span></span> <span data-ttu-id="6b5f1-104">この作業では、以降に示した手順を実行するために [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b5f1-104">This task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to perform the following procedure.</span></span>  
  
 <span data-ttu-id="6b5f1-105">この手順でステートメントの実行を完了すると、クエリ エディターの **[結果]** タブに次の 2 つの列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b5f1-105">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following two columns:</span></span>  
  
-   <span data-ttu-id="6b5f1-106">package_name</span><span class="sxs-lookup"><span data-stu-id="6b5f1-106">package_name</span></span>  
  
-   <span data-ttu-id="6b5f1-107">target_name</span><span class="sxs-lookup"><span data-stu-id="6b5f1-107">target_name</span></span>  
  
## <a name="to-view-the-extended-events-targets-for-registered-packages-using-query-editor"></a><span data-ttu-id="6b5f1-108">クエリ エディターを使用して登録パッケージの拡張イベント ターゲットを表示するには</span><span class="sxs-lookup"><span data-stu-id="6b5f1-108">To view the Extended Events targets for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="6b5f1-109">クエリ エディターで、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6b5f1-109">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name package_name, o.name target_name  
    FROM sys.dm_xe_objects o  
    JOIN sys.dm_xe_packages p  
         ON o.package_guid = p.guid  
    WHERE o.object_type = 'target'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6b5f1-110">参照</span><span class="sxs-lookup"><span data-stu-id="6b5f1-110">See Also</span></span>  
 <span data-ttu-id="6b5f1-111">[SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="6b5f1-111">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="6b5f1-112">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6b5f1-112">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="6b5f1-113">sys.dm_xe_packages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6b5f1-113">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
