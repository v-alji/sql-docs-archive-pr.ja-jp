---
title: WMI Provider for Server Events のクラスとプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 471e77cb7afa4e6aed441dcbbc8b3b70064f6737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739613"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a><span data-ttu-id="4c584-102">WMI Provider for Server Events のクラスとプロパティ</span><span class="sxs-lookup"><span data-stu-id="4c584-102">WMI Provider for Server Events Classes and Properties</span></span>
  <span data-ttu-id="4c584-103">次に示すサーバー イベントは、WMI Provider for Server Events のプログラミング モデルを構成しています。</span><span class="sxs-lookup"><span data-stu-id="4c584-103">The following server events make up the programming model for the WMI Provider for Server Events.</span></span> <span data-ttu-id="4c584-104">プロバイダーに対する WQL クエリの実行によってクエリを実行できるイベントには、2 つの主なカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="4c584-104">There are two main categories of events that can be queried by issuing WQL queries against the provider.</span></span> <span data-ttu-id="4c584-105">その 2 つとは、データ定義言語 (DDL) イベントおよびトレース イベントです。</span><span class="sxs-lookup"><span data-stu-id="4c584-105">These are data definition language (DDL) events and trace events.</span></span> <span data-ttu-id="4c584-106">また、QUEUE_ACTIVATION および BROKER_QUEUE_DISABLED の Service Broker イベントも照会することができます。</span><span class="sxs-lookup"><span data-stu-id="4c584-106">The QUEUE_ACTIVATION and BROKER_QUEUE_DISABLED service broker events can also be queried.</span></span> <span data-ttu-id="4c584-107">次のツリー ダイアグラムの包含的な性質に注意してください。</span><span class="sxs-lookup"><span data-stu-id="4c584-107">Note the inclusive nature of the following tree diagrams.</span></span> <span data-ttu-id="4c584-108">たとえば、DDL_ASSEMBLY_EVENTS イベントには、ALTER_ASSEMBLY、CREATE_ASSEMBLY、および DROP_ASSEMBLY イベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c584-108">The DDL_ASSEMBLY_EVENTS event, for example, includes any ALTER_ASSEMBLY, CREATE_ASSEMBLY, and DROP_ASSEMBLY event.</span></span> <span data-ttu-id="4c584-109">同様に、TRC_FULL_TEXT イベントには、FT_CRAWL_ABORTED、FT_CRAWL_STARTED、および FT_CRAWL_STOPPED イベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c584-109">Similarly, the TRC_FULL_TEXT event includes any FT_CRAWL_ABORTED, FT_CRAWL_STARTED, and FT_CRAWL_STOPPED event.</span></span> <span data-ttu-id="4c584-110">ALL_EVENTS は、すべての DDL イベント、トレース イベント、QUEUE_ACTIVATION、および BROKER_QUEUE_DISABLED をカバーします。</span><span class="sxs-lookup"><span data-stu-id="4c584-110">ALL_EVENTS covers all DDL events, trace events, QUEUE_ACTIVATION, and BROKER_QUEUE_DISABLED.</span></span>  
  
 <span data-ttu-id="4c584-111">イベントまたはイベント グループから照会できるプロパティについては、イベント スキーマを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c584-111">To learn which properties can be queried from an event or event group, refer to the event schema.</span></span> <span data-ttu-id="4c584-112">既定では、イベント スキーマは、[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd ディレクトリにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4c584-112">By default, the event schema is installed in the following directory: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.</span></span>  
  
 <span data-ttu-id="4c584-113">または、で公開されているイベントスキーマを参照することもでき [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100) ます。</span><span class="sxs-lookup"><span data-stu-id="4c584-113">Alternatively, you can refer to the event schema published at [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="4c584-114">たとえば、ALTER_DATABASE イベントを参照すると、その親イベントが DDL_SERVER_LEVEL_EVENTS で、そのプロパティが `TSQLCommand` と `DatabaseName` であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4c584-114">For example, by referring to the ALTER_DATABASE event, you will learn that its parent event is DDL_SERVER_LEVEL_EVENTS and its properties are `TSQLCommand` and `DatabaseName`.</span></span> <span data-ttu-id="4c584-115">また、プロパティ `SQLInstance`、`PostTime`、`ComputerName`、`SPID`、および `LoginName` が継承されています。</span><span class="sxs-lookup"><span data-stu-id="4c584-115">The event also inherits the properties `SQLInstance`, `PostTime`, `ComputerName`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="4c584-116">イベントには、子イベントはありません。</span><span class="sxs-lookup"><span data-stu-id="4c584-116">The event has no children events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c584-117">DDL と同様の操作を実行するシステム ストアド プロシージャもイベント通知を起動できます。</span><span class="sxs-lookup"><span data-stu-id="4c584-117">System stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="4c584-118">イベント通知はテストして、実行されているシステム ストアド プロシージャに応答するかどうか、確認してください。</span><span class="sxs-lookup"><span data-stu-id="4c584-118">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="4c584-119">たとえば、CREATE TYPE ステートメントと**sp_addtype**ストアドプロシージャはどちらも、CREATE_TYPE イベントで作成されたイベント通知を起動します。</span><span class="sxs-lookup"><span data-stu-id="4c584-119">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="4c584-120">詳細については、「[DDL イベント](../../relational-databases/triggers/ddl-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c584-120">For more information, see[DDL Events](../../relational-databases/triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="4c584-121">**データ定義言語イベントおよびイベント グループ**</span><span class="sxs-lookup"><span data-stu-id="4c584-121">**Data Definition Language Events and Event Groups**</span></span>  
  
 <span data-ttu-id="4c584-122">![サーバー イベントのイベント ツリーの WMI プロバイダー](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "サーバー イベントのイベント ツリーの WMI プロバイダー")</span><span class="sxs-lookup"><span data-stu-id="4c584-122">![WMI Provider for Server Events Event Tree](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server Events Event Tree")</span></span>  
  
 <span data-ttu-id="4c584-123">**トレース イベントおよびイベント グループ**</span><span class="sxs-lookup"><span data-stu-id="4c584-123">**Trace Events and Event Groups**</span></span>  
  
 <span data-ttu-id="4c584-124">![トレースイベントとイベントグループ](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "トレース イベントとイベント グループ")</span><span class="sxs-lookup"><span data-stu-id="4c584-124">![Trace events and event groups](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "Trace events and event groups")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c584-125">参照</span><span class="sxs-lookup"><span data-stu-id="4c584-125">See Also</span></span>  
 <span data-ttu-id="4c584-126">[WMI Provider for Server Events の概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4c584-126">[WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span></span>  
 [<span data-ttu-id="4c584-127">WMI Provider for Server Events と WQL の使用</span><span class="sxs-lookup"><span data-stu-id="4c584-127">Using WQL with the WMI Provider for Server Events</span></span>](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
