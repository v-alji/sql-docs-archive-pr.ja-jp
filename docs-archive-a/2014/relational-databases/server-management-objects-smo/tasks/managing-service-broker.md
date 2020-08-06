---
title: Service Broker の管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce166825bb7adea241bac13defeca1a78b4f29cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711833"
---
# <a name="managing-service-broker"></a><span data-ttu-id="62d03-102">Service Broker の管理</span><span class="sxs-lookup"><span data-stu-id="62d03-102">Managing Service Broker</span></span>
  <span data-ttu-id="62d03-103">SMO では、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] オブジェクトは `Microsoft.SqlServer.Management.Smo.Broker` 名前空間にあり、この名前空間は Microsoft.SqlServer.Smo.dll への参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="62d03-103">In SMO, the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects are found in the `Microsoft.SqlServer.Management.Smo.Broker` namespace, which requires a reference to the Microsoft.SqlServer.Smo.dll.</span></span> <span data-ttu-id="62d03-104">クラス情報のサポートには、Microsoft.SqlServer.ServiceBrokerEnum.dll への参照も必要です。</span><span class="sxs-lookup"><span data-stu-id="62d03-104">A reference to the Microsoft.SqlServer.ServiceBrokerEnum.dll is also required for supporting class information.</span></span>  
  
 <span data-ttu-id="62d03-105">SMO によって、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 実装のプログラムによる管理 (DDL) を許可する [!INCLUDE[ssSB](../../../includes/sssb-md.md)] オブジェクトのセットが提供されます。</span><span class="sxs-lookup"><span data-stu-id="62d03-105">SMO provides a set of [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects that permit programmatic management (DDL) of the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation.</span></span> <span data-ttu-id="62d03-106">これには、メッセージ型、コントラクト、キュー、およびサービスの定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="62d03-106">This includes defining the message types, contracts, queues, and services.</span></span> <span data-ttu-id="62d03-107">SMO はデータ操作を目的としていない管理ツールであるため、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] メッセージの送受信は SMO ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="62d03-107">Because SMO is a management tool that is not intended for data manipulation, sending and receiving [!INCLUDE[ssSB](../../../includes/sssb-md.md)] messages is not supported by SMO.</span></span>  
  
 <span data-ttu-id="62d03-108">SMO では、<xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> オブジェクトが最上位レベルのクラスであり、この下に [!INCLUDE[ssSB](../../../includes/sssb-md.md)] のすべての機能が配置されます。</span><span class="sxs-lookup"><span data-stu-id="62d03-108">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> object is the top-level class under which all the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] functionality resides.</span></span> <span data-ttu-id="62d03-109">分散メッセージ アプリケーションに参加している各データベースに対して、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 実装が必要です。</span><span class="sxs-lookup"><span data-stu-id="62d03-109">A [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation is required for each database that is participating in the distributed messaging application.</span></span> <span data-ttu-id="62d03-110">したがって、<xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> オブジェクトは、<xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトの子となります。</span><span class="sxs-lookup"><span data-stu-id="62d03-110">Therefore, the <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="62d03-111"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> オブジェクトには、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 実装を定義するために使用される、次のオブジェクトのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="62d03-111">The <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object contains collections of the following objects that are used to define the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation:</span></span>  
  
-   <span data-ttu-id="62d03-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> オブジェクトは、メッセージの内容を定義するメッセージ型を表します。</span><span class="sxs-lookup"><span data-stu-id="62d03-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> objects represent message types that define the content of messages.</span></span>  
  
-   <span data-ttu-id="62d03-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> オブジェクトは、指定されたメッセージ交換でのメッセージの方向と型を指定するコントラクトを表します。</span><span class="sxs-lookup"><span data-stu-id="62d03-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> objects represent contracts that specify the direction and type of messages in a given conversation.</span></span>  
  
-   <span data-ttu-id="62d03-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> オブジェクトは、送信前および受信後にメッセージを格納します。</span><span class="sxs-lookup"><span data-stu-id="62d03-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> objects store messages prior to sending and after they are received.</span></span> <span data-ttu-id="62d03-115">その他の利点に加え、同じメッセージ交換グループ内のメッセージの自動ロックなど、サービス間での非同期通信がこれらのオブジェクトによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="62d03-115">They provide asynchronous communication between services, as well as other benefits, such as automatically locking messages in the same conversation group.</span></span>  
  
-   <span data-ttu-id="62d03-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> オブジェクトは、アドレス指定が可能なメッセージ交換エンドポイントである [!INCLUDE[ssSB](../../../includes/sssb-md.md)] サービスを表します。</span><span class="sxs-lookup"><span data-stu-id="62d03-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> objects represent [!INCLUDE[ssSB](../../../includes/sssb-md.md)] services, which are the addressable endpoints for conversations.</span></span> [!INCLUDE[ssSB](../../../includes/sssb-md.md)] <span data-ttu-id="62d03-117">メッセージは、あるサービスから別のサービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="62d03-117">messages are sent from one service to another service.</span></span> <span data-ttu-id="62d03-118">サービスによってメッセージを保持するキューが指定され、このサービスの対象とするコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="62d03-118">A service specifies a queue to hold messages, and specifies the contracts for which the service can be the target.</span></span>  
  
-   <span data-ttu-id="62d03-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding>オブジェクトは、 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] リモートサービスと通信するときにがセキュリティと認証に使用する設定を表します。</span><span class="sxs-lookup"><span data-stu-id="62d03-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> objects represent the settings that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] uses for security and authentication when communicating with a remote service.</span></span>  
  
-   <span data-ttu-id="62d03-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> オブジェクトは、サービスおよびサービスが定義されているデータベースの位置情報を格納した [!INCLUDE[ssSB](../../../includes/sssb-md.md)] ルートを表します。</span><span class="sxs-lookup"><span data-stu-id="62d03-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> objects represents a [!INCLUDE[ssSB](../../../includes/sssb-md.md)] route, which contains the location information for the service and the database on which it is defined.</span></span> <span data-ttu-id="62d03-121">メッセージの配信にはルートが必要です。</span><span class="sxs-lookup"><span data-stu-id="62d03-121">A route is required for message delivery.</span></span> <span data-ttu-id="62d03-122">既定では、各データベースに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の現在のインスタンスとして場所を示すルートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="62d03-122">By default, each database contains a route that specifies the location as the current instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d03-123">参照</span><span class="sxs-lookup"><span data-stu-id="62d03-123">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [<span data-ttu-id="62d03-124">SQL Server Service Broker (SQL Server Service Broker)</span><span class="sxs-lookup"><span data-stu-id="62d03-124">SQL Server Service Broker</span></span>](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
