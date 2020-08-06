---
title: インターネット経由のレプリケーションのセキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Internet
- Internet [SQL Server replication], security
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 47408b2b9559d33da4563c6fc9560d20338ee01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740806"
---
# <a name="securing-replication-over-the-internet"></a><span data-ttu-id="1416d-102">インターネット経由のレプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="1416d-102">Securing Replication Over the Internet</span></span>
  <span data-ttu-id="1416d-103">インターネット経由のレプリケーションを利用すると、特にモバイルのサブスクライバーで必要とされるような柔軟性を実現できます。ただし、適切に構成して十分なセキュリティを確保する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1416d-103">Replication over the Internet can provide flexibility, particularly for mobile Subscribers, but you must configure Internet replication appropriately to ensure adequate security.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="1416d-104">では、インターネット経由で情報を安全に共有するために、次のいずれかの技術を使用することを推奨しています。</span><span class="sxs-lookup"><span data-stu-id="1416d-104">recommends using one of two techniques for securely sharing information over the Internet:</span></span>  
  
-   <span data-ttu-id="1416d-105">仮想プライベート ネットワーク (VPN)</span><span class="sxs-lookup"><span data-stu-id="1416d-105">Virtual private network (VPN)</span></span>  
  
-   <span data-ttu-id="1416d-106">マージ レプリケーション用の Web 同期オプション</span><span class="sxs-lookup"><span data-stu-id="1416d-106">The Web synchronization option for merge replication</span></span>  
  
## <a name="virtual-private-network"></a><span data-ttu-id="1416d-107">仮想プライベート ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1416d-107">Virtual Private Network</span></span>  
 <span data-ttu-id="1416d-108">仮想プライベート ネットワークを使用すると、複数の層を使ったシンプルかつ安全な方法で、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータをインターネット経由でレプリケートできます。</span><span class="sxs-lookup"><span data-stu-id="1416d-108">Virtual private networks provide a simple and secure layered approach to replicating [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data over the Internet.</span></span> <span data-ttu-id="1416d-109">インターネットを介しての VPN 接続は、論理的にはサイト間のワイド エリア ネットワーク (WAN) リンクとして動作します。</span><span class="sxs-lookup"><span data-stu-id="1416d-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="1416d-110">これは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows&#xA0;NT Version&#xA0;4.0 または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows&#xA0;2000 オペレーティング システムで使用できる [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point トンネリング プロトコル (PPTP)、または Windows&#xA0;2000 オペレーティング システムで使用できるレイヤー 2 トンネリング プロトコル (L2TP) などのプロトコルを使用して、ユーザーがインターネットや他のパブリック ネットワークをトンネリングできるようにすることで実現します。</span><span class="sxs-lookup"><span data-stu-id="1416d-110">This is achieved by allowing the user to tunnel through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) available with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT version 4.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 operating system, or Layer Two Tunneling Protocol (L2TP) available with the Windows 2000 operating system.</span></span> <span data-ttu-id="1416d-111">これにより、プライベート ネットワークとほぼ同等のセキュリティと機能が実現されます。</span><span class="sxs-lookup"><span data-stu-id="1416d-111">This process provides security and features similar to those available in a private network.</span></span>  
  
 <span data-ttu-id="1416d-112">VPN の設定の詳細については、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1416d-112">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="web-synchronization-through-iis"></a><span data-ttu-id="1416d-113">IIS による Web 同期</span><span class="sxs-lookup"><span data-stu-id="1416d-113">Web Synchronization Through IIS</span></span>  
 <span data-ttu-id="1416d-114">マージ レプリケーション用の Web 同期オプションを使用すると、HTTPS プロトコルを使用してデータをレプリケートできます。この方法は、ファイアウォール越しにデータをレプリケートする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="1416d-114">The web synchronization option for merge replication provides the ability to replicate data using the HTTPS protocol, which can be a convenient approach to replicating data through a firewall.</span></span> <span data-ttu-id="1416d-115">詳細については、「[Web 同期の構成](../configure-web-synchronization.md)」および「[Web 同期のセキュリティ アーキテクチャ](security-architecture-for-web-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1416d-115">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md) and [Security Architecture for Web Synchronization](security-architecture-for-web-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1416d-116">参照</span><span class="sxs-lookup"><span data-stu-id="1416d-116">See Also</span></span>  
 <span data-ttu-id="1416d-117">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="1416d-117">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="1416d-118">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="1416d-118">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
