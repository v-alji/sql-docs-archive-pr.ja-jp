---
title: すべてのイベントのフィールドを取得します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 01d98e827121a0c47111dd601c6e1772f796849d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716606"
---
# <a name="get-the-fields-for-all-events"></a><span data-ttu-id="77f02-102">すべてのイベントのフィールドを取得する</span><span class="sxs-lookup"><span data-stu-id="77f02-102">Get the Fields for All Events</span></span>
  <span data-ttu-id="77f02-103">この作業には、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のクエリ エディターを使用した次の手順の実行も含まれます。</span><span class="sxs-lookup"><span data-stu-id="77f02-103">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="77f02-104">この手順でステートメントの実行が完了すると、クエリ エディターの **[結果]** タブに次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77f02-104">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="77f02-105">package_name</span><span class="sxs-lookup"><span data-stu-id="77f02-105">package_name</span></span>  
  
-   <span data-ttu-id="77f02-106">event_name</span><span class="sxs-lookup"><span data-stu-id="77f02-106">event_name</span></span>  
  
-   <span data-ttu-id="77f02-107">event_field</span><span class="sxs-lookup"><span data-stu-id="77f02-107">event_field</span></span>  
  
-   <span data-ttu-id="77f02-108">field_type</span><span class="sxs-lookup"><span data-stu-id="77f02-108">field_type</span></span>  
  
-   <span data-ttu-id="77f02-109">column_type</span><span class="sxs-lookup"><span data-stu-id="77f02-109">column_type</span></span>  
  
 <span data-ttu-id="77f02-110">バケット ターゲットを使用するイベント セッションを設定する場合は、上記の情報を使用できます。</span><span class="sxs-lookup"><span data-stu-id="77f02-110">You can use the preceding information when configuring event sessions that use the bucketing target.</span></span> <span data-ttu-id="77f02-111">詳細については、「 [SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77f02-111">For more information, see [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="77f02-112">開始する前に</span><span class="sxs-lookup"><span data-stu-id="77f02-112">Before you Begin</span></span>  
 <span data-ttu-id="77f02-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 拡張イベント セッションを作成する前に、イベントに関連したフィールドについての情報を取得すると役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="77f02-113">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to get information about the fields associated with events.</span></span>  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a><span data-ttu-id="77f02-114">クエリ エディターを使用してすべてのイベントのフィールドを取得するには</span><span class="sxs-lookup"><span data-stu-id="77f02-114">To get the fields for all events using Query Editor</span></span>  
  
-   <span data-ttu-id="77f02-115">クエリ エディターで、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="77f02-115">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77f02-116">参照</span><span class="sxs-lookup"><span data-stu-id="77f02-116">See Also</span></span>  
 <span data-ttu-id="77f02-117">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77f02-117">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="77f02-118">sys.dm_xe_packages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="77f02-118">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
