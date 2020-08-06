---
title: レプリケーションのチュートリアル | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4d70abd6c58b3eb0fa4a53e2806ab1b3fbe9245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631778"
---
# <a name="replication-tutorials"></a><span data-ttu-id="0dfd2-102">レプリケーションのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="0dfd2-102">Replication Tutorials</span></span>
  <span data-ttu-id="0dfd2-103">レプリケーションには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でレプリケーション トポロジをセットアップし、それを実行する方法を学習できるチュートリアルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-103">Replication includes tutorials that you can use to learn how to set up and run replication topologies using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0dfd2-104">レプリケーションのチュートリアルでは、"パブリッシャー" はレプリケート元のデータが配置されているサーバーを指し、"サブスクライバー" はレプリケート先のサーバーを指しています。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-104">In the replication tutorials, "Publisher" refers to the server that contains that source data being replicated and "Subscriber" refers to the destination server.</span></span> <span data-ttu-id="0dfd2-105">パブリッシャーとサブスクライバーが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有することもできますが、これは必須条件ではありません。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-105">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="0dfd2-106">詳細については、 [「レプリケーションのパブリッシング モデルの概要」](publish/replication-publishing-model-overview.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-106">For more information, see [Replication Publishing Model Overview](publish/replication-publishing-model-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0dfd2-107">このチュートリアルで示すタスクのほとんどは、プログラムによって実行できます。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-107">Most of the tasks shown in these tutorials can be performed programmatically.</span></span> <span data-ttu-id="0dfd2-108">詳細については、「[開発者ガイド &#40;レプリケーションの&#41;](concepts/replication-developer-documentation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-108">For more information, see [Developer's Guide &#40;Replication&#41;](concepts/replication-developer-documentation.md).</span></span>  
  
## <a name="replication-tutorials"></a><span data-ttu-id="0dfd2-109">レプリケーションのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="0dfd2-109">Replication Tutorials</span></span>  
 [<span data-ttu-id="0dfd2-110">レプリケーションに備えたサーバーの準備</span><span class="sxs-lookup"><span data-stu-id="0dfd2-110">Preparing the Server for Replication</span></span>](tutorial-preparing-the-server-for-replication.md)  
 <span data-ttu-id="0dfd2-111">最小の権限でレプリケーションを実行できるようサーバーを準備する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-111">Learn how to prepare servers so that replication can be run with least privileges.</span></span> <span data-ttu-id="0dfd2-112">このチュートリアルは、レプリケーション関連のチュートリアルの中で最初に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-112">You must complete this tutorial before the other replication tutorials.</span></span>  
  
 [<span data-ttu-id="0dfd2-113">常時接続サーバー間でのデータのレプリケーション</span><span class="sxs-lookup"><span data-stu-id="0dfd2-113">Replicating Data Between Continuously Connected Servers</span></span>](tutorial-replicating-data-between-continuously-connected-servers.md)  
 <span data-ttu-id="0dfd2-114">トランザクション レプリケーションを使用して、常時接続のサーバー間でデータをレプリケートする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-114">Learn how to use transactional replication to replicate data between fully connected servers.</span></span>  
  
 [<span data-ttu-id="0dfd2-115">モバイル クライアントとの間のデータのレプリケーション</span><span class="sxs-lookup"><span data-stu-id="0dfd2-115">Replicating Data with Mobile Clients</span></span>](tutorial-replicating-data-with-mobile-clients.md)  
 <span data-ttu-id="0dfd2-116">マージ レプリケーションを使用して、サーバーと、常時接続でない 1 つ以上のクライアントの間でデータを交換する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="0dfd2-116">Learn how to use merge replication to exchange data between a server and one or more clients that are only occasionally connected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dfd2-117">参照</span><span class="sxs-lookup"><span data-stu-id="0dfd2-117">See Also</span></span>  
 [<span data-ttu-id="0dfd2-118">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="0dfd2-118">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
