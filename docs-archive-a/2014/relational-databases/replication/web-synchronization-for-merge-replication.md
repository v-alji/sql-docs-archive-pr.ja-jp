---
title: マージ レプリケーションの Web 同期 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication synchronization [SQL Server replication]
- Internet [SQL Server replication], synchronization
- synchronization [SQL Server replication], Web Synchronization
- Web publishing [SQL Server replication], synchronization
- Web synchronization, about
- Web synchronization
ms.assetid: 84785aba-b2c1-4821-9e9d-a363c73dcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7bf5a6f77d593a90508a0b69d02f8c0db04407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644434"
---
# <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="4e293-102">マージ レプリケーションの Web 同期</span><span class="sxs-lookup"><span data-stu-id="4e293-102">Web Synchronization for Merge Replication</span></span>
  <span data-ttu-id="4e293-103">マージ レプリケーションの Web 同期を利用すると、HTTPS プロトコルを使用したデータのレプリケートが可能になり、以下のようなシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4e293-103">Web synchronization for merge replication lets you replicate data by using the HTTPS protocol, and is useful for the following scenarios:</span></span>

-   <span data-ttu-id="4e293-104">モバイル ユーザーからのデータをインターネット上で同期します。</span><span class="sxs-lookup"><span data-stu-id="4e293-104">Synchronizing data from mobile users over the Internet.</span></span>

-   <span data-ttu-id="4e293-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース間で、企業のファイアウォールを介してデータを同期します。</span><span class="sxs-lookup"><span data-stu-id="4e293-105">Synchronizing data between [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases across a corporate firewall.</span></span>

 <span data-ttu-id="4e293-106">たとえば、移動中の営業担当者は Web 同期を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4e293-106">For example, a traveling sales representative can use Web synchronization.</span></span> <span data-ttu-id="4e293-107">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]の営業担当者は、担当地域内の多数の店舗や納入業者を回ります。</span><span class="sxs-lookup"><span data-stu-id="4e293-107">The company, [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], has sales representatives that travel to various stores and suppliers throughout their regions.</span></span> <span data-ttu-id="4e293-108">長い移動の際にはホテルに滞在するため、一日の終わりに販売データをアップロードしたり、製品の更新をダウンロードするための便利な方法が必要になります。</span><span class="sxs-lookup"><span data-stu-id="4e293-108">On longer trips the representatives stay in hotels and need a convenient way to upload sales data and download any product updates at the end of each day.</span></span>

 <span data-ttu-id="4e293-109">[!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] の IT 部門は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で各ポータブル コンピューターを構成し、マージ レプリケーションで Web 同期を使用できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="4e293-109">The [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] IT department has configured each portable computer with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and has enabled merge replication to use Web synchronization.</span></span> <span data-ttu-id="4e293-110">各ポータブル コンピューターのマージ エージェントでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) を実行しているコンピューターにインストールされたレプリケーション コンポーネントを指すインターネットの URL を保持しています。</span><span class="sxs-lookup"><span data-stu-id="4e293-110">The Merge Agent on each portable computer has an Internet URL that points to the replication components that are installed on a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS).</span></span> <span data-ttu-id="4e293-111">これらのコンポーネントにより、パブリッシャーとサブスクライバーが同期されます。</span><span class="sxs-lookup"><span data-stu-id="4e293-111">These components synchronize the Subscriber with the Publisher.</span></span> <span data-ttu-id="4e293-112">これで各担当者は、リモート ダイアルアップ接続を行わなくても、任意のインターネット接続経由で必要なデータのアップロードやダウンロードが行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="4e293-112">Each representative can now connect through any available Internet connection without using a remote dial-up connection, and can upload and download the appropriate data.</span></span> <span data-ttu-id="4e293-113">インターネット接続では SSL (Secure Sockets Layer) を使用するため、仮想プライベート ネットワーク (VPN) は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4e293-113">The Internet connection uses Secure Sockets Layer (SSL); therefore, a virtual private network (VPN) is not required.</span></span>

 <span data-ttu-id="4e293-114">Web 同期に必要なコンポーネントを構成する方法については、「[Configure Web Synchronization (Web 同期の構成)](configure-web-synchronization.md)」、「[Configure IIS for Web Synchronization (Web 同期用の IIS の構成)](configure-iis-for-web-synchronization.md)」、「[Configure IIS 7 for Web Synchronization (Web 同期用の IIS 7 の構成)](configure-iis-7-for-web-synchronization.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4e293-114">For information about how to configure the components that are required for Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md), [Configure IIS for Web Synchronization](configure-iis-for-web-synchronization.md), and [Configure IIS 7 for Web Synchronization](configure-iis-7-for-web-synchronization.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="4e293-115">Web 同期は、ポータブル コンピューター、ハンドヘルド デバイスなどのクライアントでデータを同期することを目的に設計されています。</span><span class="sxs-lookup"><span data-stu-id="4e293-115">Web synchronization is designed for synchronizing data with portable computers, handheld devices, and other clients.</span></span> <span data-ttu-id="4e293-116">Web 同期は、サーバー間のアプリケーションでの大量のデータ同期には適していません。</span><span class="sxs-lookup"><span data-stu-id="4e293-116">Web synchronization is not intended for high-volume server-to-server applications.</span></span>

## <a name="overview-of-how-web-synchronization-works"></a><span data-ttu-id="4e293-117">Web 同期の動作の概要</span><span class="sxs-lookup"><span data-stu-id="4e293-117">Overview of How Web Synchronization Works</span></span>
 <span data-ttu-id="4e293-118">Web 同期を使用すると、サブスクライバーでの更新はパッケージ化され、HTTPS プロトコルを使用して XML メッセージとして IIS を実行しているコンピューターに送信されます。</span><span class="sxs-lookup"><span data-stu-id="4e293-118">When Web synchronization is used, updates at the Subscriber are packaged and sent as an XML message to the computer that is running IIS by using the HTTPS protocol.</span></span> <span data-ttu-id="4e293-119">次に IIS を実行しているコンピューターは、バイナリ形式でパブリッシャーにコマンドを送信します (通常は TCP/IP を使用します)。</span><span class="sxs-lookup"><span data-stu-id="4e293-119">The computer that is running IIS then sends the commands to the Publisher in a binary format, typically by using TCP/IP.</span></span> <span data-ttu-id="4e293-120">パブリッシャーでの更新は、IIS を実行しているコンピューターに送信され、XML メッセージとしてパッケージ化されてサブスクライバーに配信されます。</span><span class="sxs-lookup"><span data-stu-id="4e293-120">Updates at the Publisher are sent to the computer that is running IIS and then packaged as an XML message for delivery to the Subscriber.</span></span>

 <span data-ttu-id="4e293-121">次の図は、マージ レプリケーションの Web 同期に関係するコンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="4e293-121">The following illustration shows some of the components that are involved in Web synchronization for merge replication.</span></span>

 <span data-ttu-id="4e293-122">![Web 同期コンポーネントとデータ フロー](media/web-sync01.gif "Web 同期コンポーネントとデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="4e293-122">![Web synchronization components and data flow](media/web-sync01.gif "Web synchronization components and data flow")</span></span>

 <span data-ttu-id="4e293-123">Web 同期は、プル サブスクリプションだけのオプションなので、サブスクライバー上では必ずマージ エージェントが動作します。</span><span class="sxs-lookup"><span data-stu-id="4e293-123">Web synchronization is an option only for pull subscriptions; therefore, a Merge Agent will always run on the Subscriber.</span></span> <span data-ttu-id="4e293-124">標準のマージ エージェント、マージ エージェントの ActiveX コントロール、またはレプリケーション管理オブジェクト (RMO) によって同期機能を提供するアプリケーションのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e293-124">This Merge Agent can be the standard Merge Agent, the Merge Agent ActiveX control, or an application that provides synchronization through Replication Management Objects (RMO).</span></span> <span data-ttu-id="4e293-125">IIS を実行しているコンピューターの場所を指定するには、マージエージェントに **-interneturl**パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="4e293-125">To specify the location of the computer that is running IIS, use the **-InternetUrl** parameter for the Merge Agent.</span></span>

 <span data-ttu-id="4e293-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナー (Replisapi.dll) は、IIS を実行しているコンピューター上で構成され、パブリッシャーとサブスクライバーからサーバーに送信されたメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="4e293-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (Replisapi.dll) is configured on the computer that is running IIS and is responsible for handling messages that are sent to the server from the Publisher and Subscribers.</span></span> <span data-ttu-id="4e293-127">トポロジの各ノードは、マージ レプリケーション競合回避モジュール (Replrec.dll) を使用して XML データ ストリームを処理します。</span><span class="sxs-lookup"><span data-stu-id="4e293-127">Each node in the topology handles the XML data stream by using the Merge Replication Reconciler (Replrec.dll).</span></span>

 <span data-ttu-id="4e293-128">Web 同期に参加するすべてのコンピューターに、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="4e293-128">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version is required for all computers that participate in Web synchronization.</span></span>

### <a name="synchronization-process"></a><span data-ttu-id="4e293-129">同期プロセス</span><span class="sxs-lookup"><span data-stu-id="4e293-129">Synchronization Process</span></span>
 <span data-ttu-id="4e293-130">同期中の手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4e293-130">The following steps occur during synchronization:</span></span>

1.  <span data-ttu-id="4e293-131">マージ エージェントがサブスクライバーで開始されます。</span><span class="sxs-lookup"><span data-stu-id="4e293-131">The Merge Agent is started at the Subscriber.</span></span> <span data-ttu-id="4e293-132">このエージェントでは、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="4e293-132">The agent does the following:</span></span>

    1.  <span data-ttu-id="4e293-133">サブスクリプション データベースに SQL 接続を行います。</span><span class="sxs-lookup"><span data-stu-id="4e293-133">Makes an SQL connection to the subscription database.</span></span>

    2.  <span data-ttu-id="4e293-134">データベースからすべての変更を抽出します。</span><span class="sxs-lookup"><span data-stu-id="4e293-134">Extracts any changes from the database.</span></span>

    3.  <span data-ttu-id="4e293-135">IIS を実行しているコンピューターに HTTPS 要求を行います。</span><span class="sxs-lookup"><span data-stu-id="4e293-135">Makes an HTTPS request to the computer that is running IIS.</span></span>

    4.  <span data-ttu-id="4e293-136">データの変更を XML メッセージとしてアップロードします。</span><span class="sxs-lookup"><span data-stu-id="4e293-136">Uploads data changes as an XML message.</span></span>

2.  <span data-ttu-id="4e293-137">IIS を実行しているコンピューター上でホストされる、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーおよびマージ レプリケーション競合回避モジュールでは、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="4e293-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener and Merge Replication Reconciler that are hosted on the computer that is running IIS do the following:</span></span>

    1.  <span data-ttu-id="4e293-138">HTTPS 要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="4e293-138">Respond to the HTTPS request.</span></span>

    2.  <span data-ttu-id="4e293-139">パブリケーション データベースに SQL 接続を行います。</span><span class="sxs-lookup"><span data-stu-id="4e293-139">Make an SQL connection to the publication database.</span></span>

    3.  <span data-ttu-id="4e293-140">アップロードされた変更をパブリケーション データベースに適用します。</span><span class="sxs-lookup"><span data-stu-id="4e293-140">Apply the upload changes to the publication database.</span></span>

    4.  <span data-ttu-id="4e293-141">サブスクライバー用にダウンロードされた変更を抽出します。</span><span class="sxs-lookup"><span data-stu-id="4e293-141">Extract the download changes for the Subscriber.</span></span>

    5.  <span data-ttu-id="4e293-142">HTTPS 応答をマージ エージェントに返送します。</span><span class="sxs-lookup"><span data-stu-id="4e293-142">Send an HTTPS response back to the Merge Agent.</span></span>

3.  <span data-ttu-id="4e293-143">その後、サブスクライバーのマージ エージェントは HTTPS 応答を受け取り、サブスクリプション データベースに変更のダウンロードを適用します。</span><span class="sxs-lookup"><span data-stu-id="4e293-143">The Merge Agent at the Subscriber then accepts the HTTPS response and applies the download changes to the subscription database.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e293-144">参照</span><span class="sxs-lookup"><span data-stu-id="4e293-144">See Also</span></span>
 <span data-ttu-id="4e293-145">Web 同期の[Web 同期](configure-web-synchronization.md)[トポロジを](topologies-for-web-synchronization.md)構成する</span><span class="sxs-lookup"><span data-stu-id="4e293-145">[Configure Web Synchronization](configure-web-synchronization.md) [Topologies for Web Synchronization](topologies-for-web-synchronization.md)</span></span>


