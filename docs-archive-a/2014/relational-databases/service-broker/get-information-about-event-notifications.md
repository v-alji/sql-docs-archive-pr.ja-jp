---
title: イベント通知に関する情報の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8d8271b6279910321058d01c7b2f96b1df62bd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716162"
---
# <a name="get-information-about-event-notifications"></a><span data-ttu-id="fe100-102">イベント通知に関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="fe100-102">Get Information About Event Notifications</span></span>
  <span data-ttu-id="fe100-103">次のカタログ ビューは、イベント通知に関するメタデータのクエリに使用できます。</span><span class="sxs-lookup"><span data-stu-id="fe100-103">The following catalog views are available to query metadata about event notifications.</span></span>  
  
 <span data-ttu-id="fe100-104">**サーバー以外のレベルのイベント通知に関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="fe100-104">**To get information about nonserver-level event notifications**</span></span>  
  
-   [<span data-ttu-id="fe100-105">sys.event_notifications &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fe100-105">sys.event_notifications &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="fe100-106">データベース レベルで作成した **sys.event_notifications** の任意のイベント通知に関するメタデータを表示するには、少なくとも、データベースに対して CONTROL 権限、ALTER 権限、TAKE OWNERSHIP 権限、または VIEW DEFINITION 権限を持っているか、イベント通知の所有者であるか、ALTER ANY DATABASE EVENT NOTIFICATION 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe100-106">To view metadata about any event notification in **sys.event_notifications** created at the database level, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the database, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.</span></span> <span data-ttu-id="fe100-107">特定のキューで作成したイベント通知の場合は、少なくとも、オブジェクトに対して CONTROL 権限、ALTER 権限、TAKE OWNERSHIP 権限、または VIEW DEFINITION 権限を持っているか、イベント通知の所有者であるか、ALTER ANY DATABASE EVENT NOTIFICATION 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe100-107">For event notifications created on a specific queue, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the object, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.</span></span>  
  
 <span data-ttu-id="fe100-108">**サーバーレベルのイベント通知に関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="fe100-108">**To get information about server-level event notifications**</span></span>  
  
-   [<span data-ttu-id="fe100-109">sys.server_event_notifications &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fe100-109">sys.server_event_notifications &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="fe100-110">**sys.server_event_notifications**の任意のイベント通知に関するメタデータを表示するには、少なくとも、サーバーに対して CONTROL 権限または VIEW ANY DEFINITION 権限を持っているか、イベント通知のログオンまたは所有者であるか、ALTER ANY EVENT NOTIFICATION 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe100-110">At the minimum, you must have the following: CONTROL or VIEW ANY DEFINITION permission on the server, be the logon or owner of the event notification, or have ALTER ANY EVENT NOTIFICATION permission to view metadata about any event notification in **sys.server_event_notifications**.</span></span>  
  
 <span data-ttu-id="fe100-111">**イベント通知を発生させることができるすべてのイベントに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="fe100-111">**To get information about all events that can fire event notifications**</span></span>  
  
-   [<span data-ttu-id="fe100-112">sys.event_notification_event_types &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fe100-112">sys.event_notification_event_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="fe100-113">このカタログ ビューからイベント グループが返されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fe100-113">This catalog view does not return event groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe100-114">参照</span><span class="sxs-lookup"><span data-stu-id="fe100-114">See Also</span></span>  
 [<span data-ttu-id="fe100-115">イベント通知</span><span class="sxs-lookup"><span data-stu-id="fe100-115">Event Notifications</span></span>](event-notifications.md)  
  
  
