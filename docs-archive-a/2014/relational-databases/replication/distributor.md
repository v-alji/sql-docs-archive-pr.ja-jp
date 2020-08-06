---
title: ディストリビューター | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.selectdistributor.f1
ms.assetid: 787f0e9c-09dd-438a-bc04-5b8f99c127b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c601a540088b5cd9d7a2033510a5cf9b83c3170e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632368"
---
# <a name="distributor"></a><span data-ttu-id="408e0-102">ディストリビューター</span><span class="sxs-lookup"><span data-stu-id="408e0-102">Distributor</span></span>
  <span data-ttu-id="408e0-103">**[ディストリビューター]** ページは、ディストリビューションの構成ウィザードとパブリケーションの新規作成ウィザードで表示されます。</span><span class="sxs-lookup"><span data-stu-id="408e0-103">The **Distributor** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="408e0-104">ディストリビューターは、ディストリビューション データベースを備え、あらゆる種類のレプリケーションのメタデータおよび履歴データを格納するサーバーです。</span><span class="sxs-lookup"><span data-stu-id="408e0-104">The Distributor is a server that contains the distribution database and stores metadata and history data for all types of replication.</span></span> <span data-ttu-id="408e0-105">ディストリビューターは、トランザクション レプリケーションのトランザクションも格納します。</span><span class="sxs-lookup"><span data-stu-id="408e0-105">The Distributor also stores transactions for transactional replication.</span></span> <span data-ttu-id="408e0-106">ディストリビューターは、パブリッシャーと同じサーバーであっても、別のサーバーであってもかまいません。前者の場合はローカル ディストリビューターで、後者の場合はリモート ディストリビューターになります。</span><span class="sxs-lookup"><span data-stu-id="408e0-106">The Distributor can be the same server as the Publisher (a local Distributor) or it can be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="408e0-107">ディストリビューターの役割は、実装するレプリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="408e0-107">The role of the Distributor varies, depending on which type of replication you implement.</span></span> <span data-ttu-id="408e0-108">一般に、マージ レプリケーションやスナップショット レプリケーションに比べて、トランザクション レプリケーションに対するディストリビューターの役割は大きくなります。</span><span class="sxs-lookup"><span data-stu-id="408e0-108">In general, its role is much greater for transactional replication than it is for merge replication and snapshot replication.</span></span> <span data-ttu-id="408e0-109">マージ レプリケーションおよびスナップショット レプリケーションではローカル ディストリビューターを使用するのが一般的です。ただし、非常に稼働率が高いシステムでのトランザクション レプリケーションの場合は、リモート ディストリビューターを利用すると効果的です。</span><span class="sxs-lookup"><span data-stu-id="408e0-109">Merge and snapshot replication typically use a local Distributor, but transactional replication on a very busy system can benefit from using a remote Distributor.</span></span>  
  
 <span data-ttu-id="408e0-110">サーバーがディストリビューターとして指定されると、次のようなリソースが新たに消費されることになります。</span><span class="sxs-lookup"><span data-stu-id="408e0-110">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="408e0-111">一般的な方法でパブリケーションのスナップショット ファイルがサーバーに格納される場合は、そのためのディスク領域</span><span class="sxs-lookup"><span data-stu-id="408e0-111">Additional disk space if the snapshot files for the publication are stored on it (which they typically are).</span></span>  
  
-   <span data-ttu-id="408e0-112">ディストリビューション データベースを格納するためのディスク領域</span><span class="sxs-lookup"><span data-stu-id="408e0-112">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="408e0-113">ディストリビューター上で実行されるプッシュ サブスクリプションのために、レプリケーション エージェントによって使用されるプロセッサ時間</span><span class="sxs-lookup"><span data-stu-id="408e0-113">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="408e0-114">ディストリビューターとして指定するサーバーには、サーバー上でさまざまな機能を果たしながら、レプリケーションの処理を実行できるだけの十分なディスク容量とプロセッサ パワーが必要です。</span><span class="sxs-lookup"><span data-stu-id="408e0-114">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span>  
  
## <a name="options"></a><span data-ttu-id="408e0-115">Options</span><span class="sxs-lookup"><span data-stu-id="408e0-115">Options</span></span>  
 <span data-ttu-id="408e0-116">**'\<ServerName>' を独自のディストリビューターとする (SQL Server はディストリビューション データベースとログを作成します)**</span><span class="sxs-lookup"><span data-stu-id="408e0-116">**'\<ServerName>' will act as its own Distributor; SQL Server will create a distribution database and log**</span></span>  
 <span data-ttu-id="408e0-117">このオプションを選択すると、ディストリビューターとして接続するサーバーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="408e0-117">Select this option to configure the server you are connected to as a Distributor.</span></span>  
  
 <span data-ttu-id="408e0-118">**[以下のサーバーをディストリビューターとして使用する (選択するサーバーはディストリビューターとして構成されている必要があります)]**</span><span class="sxs-lookup"><span data-stu-id="408e0-118">**Use the following server as the Distributor (Note: the server you select must already be configured as a Distributor)**</span></span>  
 <span data-ttu-id="408e0-119">別のサーバーをディストリビューターとして構成するには、このオプションを選択し、以下のサーバーの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="408e0-119">Select this option and then click on the name of a server below to configure another server as the Distributor.</span></span>  
  
 <span data-ttu-id="408e0-120">**追加**</span><span class="sxs-lookup"><span data-stu-id="408e0-120">**Add**</span></span>  
 <span data-ttu-id="408e0-121">ディストリビューターとして構成するサーバーが表示されていない場合は、 **[追加]** をクリックし、目的のサーバーを識別して一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="408e0-121">If the server you want to use as a Distributor is not listed, click **Add** to identify the server and add it to the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="408e0-122">リモート サーバーをディストリビューターとして使用するには、リモート サーバーがディストリビューターとして構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="408e0-122">To use a remote server as the Distributor, the remote server must already be configured as a Distributor.</span></span> <span data-ttu-id="408e0-123">このウィザードの実行の対象となるサーバーは、そのディストリビューター上でパブリッシャーとして有効に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="408e0-123">The server against which this wizard is running must be enabled as a Publisher on that Distributor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408e0-124">参照</span><span class="sxs-lookup"><span data-stu-id="408e0-124">See Also</span></span>  
 <span data-ttu-id="408e0-125">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="408e0-125">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="408e0-126">パブリッシングおよびディストリビューションの構成</span><span class="sxs-lookup"><span data-stu-id="408e0-126">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
  
