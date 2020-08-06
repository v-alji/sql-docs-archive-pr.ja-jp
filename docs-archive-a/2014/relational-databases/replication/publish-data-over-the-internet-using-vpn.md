---
title: VPN を使用したインターネット経由のデータのパブリッシュ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- VPNs [SQL Server replication]
- Web publishing [SQL Server replication], VPNs
- Internet [SQL Server replication], VPNs
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a477e70031053a9563c2f3ed3740091d632febe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645531"
---
# <a name="publish-data-over-the-internet-using-vpn"></a><span data-ttu-id="ca9ad-102">VPN を使用したインターネット経由のデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="ca9ad-102">Publish Data over the Internet Using VPN</span></span>
  <span data-ttu-id="ca9ad-103">仮想プライベート ネットワーク (VPN) 技術を使用すると、自宅、支店、リモート クライアント、および他社で作業しているユーザーが安全な通信を維持しながらインターネット経由で企業ネットワークに接続できます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-103">Virtual Private Networking (VPN) technology allows users working at home, branch offices, remote clients, and other companies to connect to a corporate network over the Internet, while maintaining secure communications.</span></span> <span data-ttu-id="ca9ad-104">ユーザーは、ローカル エリア ネットワーク (LAN) 上にいる場合と同じように Windows 認証を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-104">Users can use Windows Authentication as though they were on a Local Area Network (LAN).</span></span> <span data-ttu-id="ca9ad-105">すべての種類の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションは VPN 経由でデータをレプリケートできますが、Web 同期では VPN の必要がなくなるため、マージ レプリケーションを使用している場合は、Web 同期を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-105">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but consider using Web synchronization if you are using merge replication, because Web synchronization eliminates the need for a VPN.</span></span> <span data-ttu-id="ca9ad-106">詳細については、「 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-106">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="ca9ad-107">VPN にはクライアント ソフトウェアが含まれているので、コンピューターはインターネットを介して (場合によってはイントラネットも介して)、専用のコンピューターまたはサーバー内のソフトウェアに接続できます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-107">A VPN includes client software so that computers connect over the Internet (or in special cases, even an intranet) to software in a dedicated computer or a server.</span></span> <span data-ttu-id="ca9ad-108">ユーザー認証方式に加えて、オプションで接続の両端に暗号化が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-108">Optionally, encryption at both ends, as well as user authentication methods, are used.</span></span> <span data-ttu-id="ca9ad-109">インターネットを介しての VPN 接続は、論理的にはサイト間のワイド エリア ネットワーク (WAN) リンクとして動作します。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="ca9ad-110">VPN は、別のネットワークを使用して、ネットワークのコンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-110">A VPN connects the components of a network using another network.</span></span> <span data-ttu-id="ca9ad-111">接続するには、ユーザーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point トンネリング プロトコル (PPTP) またはレイヤー 2 トンネリング プロトコル (L2TP) などのプロトコルを使用して、インターネットまたは別のパブリック ネットワークを経由したトンネリングを行います。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-111">To connect, the user tunnels through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) or Layer Two Tunneling Protocol (L2TP).</span></span> <span data-ttu-id="ca9ad-112">以前はプライベート ネットワークでのみ実現されていたセキュリティと機能が、この環境でも同じように実現されます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-112">This process provides the same security and features previously available only in a private network.</span></span> <span data-ttu-id="ca9ad-113">PPTP は、Microsoft Windows NT Version 4.0 および [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 以上のオペレーティング システムで使用できます。L2TP は、Windows 2000 以上で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-113">PPTP is available with the Microsoft Windows NT version 4.0 and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (and later) operating systems; L2TP is available with Windows 2000 and later.</span></span>  
  
 <span data-ttu-id="ca9ad-114">ユーザーには、インターネットの中間のルーティング インフラストラクチャは見えず、データが専用のプライベート リンクを経由して送信されているように感じられます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-114">For the user, the intermediate routing infrastructure of the Internet is not visible and it appears as though the data is being sent over a dedicated private link.</span></span> <span data-ttu-id="ca9ad-115">ユーザーにとっては、VPN によってユーザーのコンピューターと企業のサーバー間がポイント ツー ポイントで接続されているのと同様になります。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-115">As far as users are concerned, the VPN is a point-to-point connection between the user computer and a corporate server.</span></span>  
  
 <span data-ttu-id="ca9ad-116">リモート クライアントが VPN を使用して接続するように構成され、インターネットにアクセスし、企業 LAN にログインした後は、そのリモート クライアントが LAN に直接接続しているのと同じようにレプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-116">After you have your remote client configured to connect using a VPN, and the client has Internet access and is logged in to the corporate LAN, you can configure replication as though the remote client is connected directly on the LAN.</span></span> <span data-ttu-id="ca9ad-117">セキュリティを確保するため、VPN 経由で接続しているユーザーと LAN で直接接続しているユーザーには別々のネットワーク リソースを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-117">For security reasons, it is possible to have different network resources available to users connected over VPN and to those connected directly on the LAN.</span></span>  
  
 <span data-ttu-id="ca9ad-118">VPN の設定の詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca9ad-118">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9ad-119">参照</span><span class="sxs-lookup"><span data-stu-id="ca9ad-119">See Also</span></span>  
 [<span data-ttu-id="ca9ad-120">インターネット経由のレプリケーション</span><span class="sxs-lookup"><span data-stu-id="ca9ad-120">Replication over the Internet</span></span>](replication-over-the-internet.md)  
  
  
