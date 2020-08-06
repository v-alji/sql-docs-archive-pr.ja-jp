---
title: IPv6 を使用した接続 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f2ecd605f67446fade262cfe795f344dfb165c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720667"
---
# <a name="connecting-using-ipv6"></a><span data-ttu-id="4c331-102">IPv6 を使用した接続</span><span class="sxs-lookup"><span data-stu-id="4c331-102">Connecting Using IPv6</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c331-103">および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、インターネット プロトコル バージョン 4 (IPv4) とインターネット プロトコル バージョン 6 (IPv6) の両方が完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4c331-103">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> <span data-ttu-id="4c331-104">Windows で IPv6 が構成されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のコンポーネントは IPv6 の存在を自動的に認識します。</span><span class="sxs-lookup"><span data-stu-id="4c331-104">When Windows is configured with IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], components automatically recognize the existence of IPv6.</span></span> <span data-ttu-id="4c331-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で特別な構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4c331-105">No special [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration is necessary.</span></span>  
  
 <span data-ttu-id="4c331-106">サポートには次のものが含まれていますが、これらだけではありません。</span><span class="sxs-lookup"><span data-stu-id="4c331-106">Support includes but is not limited to the following:</span></span>  
  
-   <span data-ttu-id="4c331-107">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] と他のサーバー コンポーネントは、同時に IPv4 および IPv6 の両方のアドレスでリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="4c331-107">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and the other server components can listen on both IPv4 and IPv6 addresses at the same time.</span></span> <span data-ttu-id="4c331-108">IPv4 と IPv6 の両方が存在する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、IPv4 アドレスまたは IPv6 アドレスのどちらかだけでリッスンするように [!INCLUDE[ssDE](../../includes/ssde-md.md)] を構成できます。</span><span class="sxs-lookup"><span data-stu-id="4c331-108">When both IPv4 and IPv6 are present, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen only on IPv4 addresses or only on IPv6 addresses.</span></span>  
  
-   <span data-ttu-id="4c331-109">IPv4 および IPv6 の両方をサポートするコンピューターで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスに対して、IPv4 アドレスにクエリが実行された場合、IPv4 アドレスとそのリストにある最初の IPv4 TCP ポートを使用して応答が行われます。</span><span class="sxs-lookup"><span data-stu-id="4c331-109">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service running on a machine that supports both IPv4 and IPv6 is queried on an IPv4 address, it responds with an IPv4 address and the first IPv4 TCP port in its list.</span></span> <span data-ttu-id="4c331-110">IPv6 アドレスにクエリが実行された場合は、IPv6 アドレスとそのリストにある最初の IPv6 TCP ポートを使用して応答が行われます。</span><span class="sxs-lookup"><span data-stu-id="4c331-110">When queried on an IPv6 address, it responds with an IPv6 address and the first IPv6 TCP port in its list.</span></span> <span data-ttu-id="4c331-111">一貫性を保つために、IPv4 リスナーと IPv6 リスナーが同じポートでリッスンするように構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4c331-111">To avoid inconsistency, we recommend that the IPv4 and IPv6 listeners be configured to listen to the same port.</span></span>  
  
-   <span data-ttu-id="4c331-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーなどのツールでは、IP アドレスに IPv4 と IPv6 の両方の形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c331-112">Tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager accept both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="4c331-113">ほとんどの場合、 \<*computer_name*> \\ < *instance_name*> がサーバーのホスト名または完全修飾ドメイン名 (FQDN) を使用して指定されている場合、接続文字列を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c331-113">In most cases, the connection string does not need to be modified if the \<*computer_name*>\\<*instance_name*> is specified using server hostname or fully qualified domain name (FQDN).</span></span> <span data-ttu-id="4c331-114">サーバー コンピューターで IPv4 と IPv6 の両方が構成されている場合、そのホスト名または FQDN は複数の IP アドレス (少なくとも、1 つの IPv4 アドレスと複数の IPv6 アドレス) に解決されます。</span><span class="sxs-lookup"><span data-stu-id="4c331-114">If the server computer has both IPv4 and IPv6, its hostname or FQDN will be resolved into multiple IP addresses, including at least one IPv4 address and multiple IPv6 addresses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c331-115">Native Client は、これらの IP アドレスを TCP/IP から受信した順序で使用して接続の確立を試み、最初に成功した接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c331-115">Native Client attempts to establish connections using these IP addresses in the order received from TCP/IP and uses the first connection that succeeds.</span></span> <span data-ttu-id="4c331-116">順序は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client が予測できないため、ランダムな順序になります。</span><span class="sxs-lookup"><span data-stu-id="4c331-116">Because the order cannot be predicted by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, this should be regarded as random order.</span></span> <span data-ttu-id="4c331-117">IPv4 アドレスと IPv6 アドレスの両方が存在する場合、最初に IPv4 アドレスで試行されます。</span><span class="sxs-lookup"><span data-stu-id="4c331-117">IPv4 addresses are attempted first if both IPv4 and IPv6 addresses are present.</span></span> <span data-ttu-id="4c331-118">このロジックは、ODBC、OLE DB、または ADO.NET のユーザーに対して透過的です。</span><span class="sxs-lookup"><span data-stu-id="4c331-118">This logic is transparent to the users of ODBC, OLE DB, or ADO.NET.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c331-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] が IPv4 でリッスンしていない場合、IPv6 アドレスで試行するには、試行された IPv4 接続がタイムアウトするまでの間、待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c331-119">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not listening on IPv4, the attempted IPv4 connection must wait for the time-out period before the IPv6 address is attempted.</span></span> <span data-ttu-id="4c331-120">これを回避するには、直接 IPv6 の IP アドレスで接続するか、IPv6 アドレスを使用してクライアントの別名を構成してください。</span><span class="sxs-lookup"><span data-stu-id="4c331-120">To avoid this, connect directly to the IPv6 IP address or configure an alias on the client with the IPv6 address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c331-121">参照</span><span class="sxs-lookup"><span data-stu-id="4c331-121">See Also</span></span>  
 [<span data-ttu-id="4c331-122">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="4c331-122">SQL Server Configuration Manager</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
  
