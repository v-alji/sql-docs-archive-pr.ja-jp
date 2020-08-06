---
title: SQL Server 以外のサブスクライバーの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e36d048b11fcc71b27ab0ab2ee815b0284187c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641628"
---
# <a name="add-non-sql-server-subscriber"></a><span data-ttu-id="f2c77-102">[SQL Server 以外のサブスクライバーの追加]</span><span class="sxs-lookup"><span data-stu-id="f2c77-102">Add Non-SQL Server Subscriber</span></span>
  <span data-ttu-id="f2c77-103">レプリケーションでは、Oracle サブスクライバーと IBM DB2 のサブスクライバーのスナップショット パブリケーションおよびトランザクション パブリケーションに対するプッシュ サブスクリプションの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f2c77-103">Replication supports creating push subscriptions to snapshot and transactional publications for Oracle and IBM DB2 Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2c77-104">オプション</span><span class="sxs-lookup"><span data-stu-id="f2c77-104">Options</span></span>  
 <span data-ttu-id="f2c77-105">**[追加するサブスクライバーの種類]**</span><span class="sxs-lookup"><span data-stu-id="f2c77-105">**Type of Subscriber to add**</span></span>  
 <span data-ttu-id="f2c77-106">Oracle サブスクライバーまたは IBM DB2 サブスクライバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2c77-106">Select an Oracle Subscriber or IBM DB2 Subscriber.</span></span> <span data-ttu-id="f2c77-107">これらのサブスクライバーのサポートの詳細については、「[SQL Server 以外のサブスクライバー](non-sql/non-sql-server-subscribers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2c77-107">For more information about support for these Subscribers, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
 <span data-ttu-id="f2c77-108">**[データ ソース名]**</span><span class="sxs-lookup"><span data-stu-id="f2c77-108">**Data source name**</span></span>  
 <span data-ttu-id="f2c77-109">ネットワーク上のデータベースを探すために使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="f2c77-109">The name used to locate the database on a network.</span></span> <span data-ttu-id="f2c77-110">レプリケーションでは、このウィザードの **[ディストリビューション エージェント セキュリティ]** ページに指定されたログイン、パスワード、および任意の接続オプションをデータ ソース名と組み合わせて、データベースの接続文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="f2c77-110">Replication produces a connection string for the database using the data source name, combined with the login, password, and any connection options you specify in the **Distribution Agent Security** page in this wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2c77-111">データ ソース名と接続文字列は、ディストリビューション エージェントがサブスクリプションの初期化を試みるまでは [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって検証されません。</span><span class="sxs-lookup"><span data-stu-id="f2c77-111">The data source name and connection string are not validated by [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until the Distribution Agent attempts to initialize the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c77-112">参照</span><span class="sxs-lookup"><span data-stu-id="f2c77-112">See Also</span></span>  
 <span data-ttu-id="f2c77-113">[SQL Server 以外のサブスクライバーのサブスクリプションの作成](create-a-subscription-for-a-non-sql-server-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="f2c77-113">[Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md) </span></span>  
 <span data-ttu-id="f2c77-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="f2c77-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="f2c77-115">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="f2c77-115">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
