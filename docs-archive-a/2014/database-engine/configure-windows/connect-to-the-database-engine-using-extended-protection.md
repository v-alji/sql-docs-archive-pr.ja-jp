---
title: 拡張保護を使用したデータベース エンジンへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- spoofing attacks
- service binding
- luring attacks
- Schannel
- channel binding
- Extended Protection
ms.assetid: ecfd783e-7dbb-4a6c-b5ab-c6c27d5dd57f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 718e5c9897f0883734d460e34ca26bba4f759a54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642286"
---
# <a name="connect-to-the-database-engine-using-extended-protection"></a><span data-ttu-id="e5aec-102">拡張保護を使用したデータベース エンジンへの接続</span><span class="sxs-lookup"><span data-stu-id="e5aec-102">Connect to the Database Engine Using Extended Protection</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e5aec-103">では **で始まる** 拡張保護 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e5aec-103">supports **Extended Protection** beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="e5aec-104">**認証の拡張保護** とは、オペレーティング システムで実装されているネットワーク コンポーネントの機能です。</span><span class="sxs-lookup"><span data-stu-id="e5aec-104">**Extended Protection for Authentication** is a feature of the network components implemented by the operating system.</span></span> <span data-ttu-id="e5aec-105">**拡張保護** は、Windows 7 および Windows Server 2008 R2 でサポートされており、</span><span class="sxs-lookup"><span data-stu-id="e5aec-105">**Extended Protection** is supported in Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="e5aec-106">**以前のオペレーティング システムでは、** 拡張保護 [!INCLUDE[msCoName](../../includes/msconame-md.md)] がサービス パックに含まれています。</span><span class="sxs-lookup"><span data-stu-id="e5aec-106">**Extended Protection** is included in service packs for older [!INCLUDE[msCoName](../../includes/msconame-md.md)] operating systems.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e5aec-107">の接続を **拡張保護**を使用して確立することで、安全性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-107">is more secure when connections are made using **Extended Protection**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e5aec-108">既定では、Windows の **拡張保護** は有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="e5aec-108">Windows does not enable **Extended Protection** by default.</span></span> <span data-ttu-id="e5aec-109">Windows で **拡張保護** を有効にする方法の詳細については、「 [認証に対する保護の強化](https://support.microsoft.com/kb/968389)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5aec-109">For information about how to enable **Extended Protection** in Windows, see [Extended Protection for Authentication](https://support.microsoft.com/kb/968389).</span></span>  
  
## <a name="description-of-extended-protection"></a><span data-ttu-id="e5aec-110">拡張保護の説明</span><span class="sxs-lookup"><span data-stu-id="e5aec-110">Description of Extended Protection</span></span>  
 <span data-ttu-id="e5aec-111">**拡張保護** では、認証リレー攻撃を防止するために、サービス バインドとチャネル バインドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-111">**Extended Protection** uses service binding and channel binding to help prevent an authentication relay attack.</span></span> <span data-ttu-id="e5aec-112">認証リレー攻撃では、NTLM 認証を実行できるクライアント (Windows エクスプローラー、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Outlook、.NET SqlClient アプリケーションなど) が攻撃者のサーバー (悪意のある CIFS ファイル サーバーなど) に接続します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-112">In an authentication relay attack, a client that can perform NTLM authentication (for example, Windows Explorer, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Outlook, a .NET SqlClient application, etc.), connects to an attacker (for example, a malicious CIFS file server).</span></span> <span data-ttu-id="e5aec-113">攻撃者は、そのクライアントの資格情報を使用してクライアントになりすまし、サービス ([!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスのインスタンスなど) への認証を行います。</span><span class="sxs-lookup"><span data-stu-id="e5aec-113">The attacker uses the client's credentials to masquerade as the client and authenticate to a service (for example, an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service).</span></span>  
  
 <span data-ttu-id="e5aec-114">この攻撃には次の 2 つのバリエーションがあります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-114">There are two variations of this attack:</span></span>  
  
-   <span data-ttu-id="e5aec-115">おびき寄せによる攻撃。クライアントが自ら攻撃者のサーバーに接続するようにおびき寄せられます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-115">In a luring attack, the client is lured to voluntarily connect to the attacker.</span></span>  
  
-   <span data-ttu-id="e5aec-116">なりすましによる攻撃。正当なサービスに接続しているつもりのクライアントが、汚染された DNS ルーティングや IP ルーティングによって、知らない間に攻撃者のサーバーにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-116">In a spoofing attack, the client intends to connect to a valid service, but is unaware that one or both of DNS and IP routing are poisoned to redirect the connection to the attacker instead.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e5aec-117">では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対するこれらの攻撃を減らすために、サービス バインドとチャネル バインドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e5aec-117">supports service binding and channel binding to help reduce these attacks on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances.</span></span>  
  
### <a name="service-binding"></a><span data-ttu-id="e5aec-118">サービス バインド</span><span class="sxs-lookup"><span data-stu-id="e5aec-118">Service Binding</span></span>  
 <span data-ttu-id="e5aec-119">サービス バインドでは、接続しようとしている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの署名付きサービス プリンシパル名 (SPN) を送信するようにクライアントに要求することで、おびき寄せによる攻撃に対処します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-119">Service binding addresses luring attacks by requiring a client to send a signed service principal name (SPN) of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service that the client intends to connect to.</span></span> <span data-ttu-id="e5aec-120">サービスでは、認証応答の一部として、パケットで受信した SPN がサービス自身の SPN と一致するかどうかの確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-120">As part of the authentication response, the service validates that the SPN received in the packet matches its own SPN.</span></span> <span data-ttu-id="e5aec-121">クライアントが攻撃者のサーバーに接続するようにおびき寄せられている場合は、パケットに攻撃者の署名付き SPN が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-121">If a client is lured to connect to an attacker, the client will include the signed SPN of the attacker.</span></span> <span data-ttu-id="e5aec-122">そのため、攻撃者がパケットをリレーして本物の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスにクライアントとして認証を受けることはできません。</span><span class="sxs-lookup"><span data-stu-id="e5aec-122">The attacker cannot relay the packet to authenticate to the real [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service as the client, because it would include the SPN of the attacker.</span></span> <span data-ttu-id="e5aec-123">サービス バインドのコストはごく小さく、1 回しか発生しませんが、サービス バインドではなりすましによる攻撃には対処できません。</span><span class="sxs-lookup"><span data-stu-id="e5aec-123">Service binding incurs a one-time, negligible cost, but it does not address spoofing attacks.</span></span> <span data-ttu-id="e5aec-124">サービス バインドが発生するのは、クライアント アプリケーションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続に暗号化を使用しない場合です。</span><span class="sxs-lookup"><span data-stu-id="e5aec-124">Service Binding occurs when a client application does not use encryption to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="channel-binding"></a><span data-ttu-id="e5aec-125">チャネル バインド</span><span class="sxs-lookup"><span data-stu-id="e5aec-125">Channel Binding</span></span>  
 <span data-ttu-id="e5aec-126">チャネル バインドでは、クライアントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス インスタンスとの間に、セキュリティで保護されたチャネル (Schannel) を確立します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-126">Channel binding establishes a secure channel (Schannel) between a client and an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="e5aec-127">サービスでは、クライアントとサービス自身のチャネル固有のチャネル バインド トークン (CBT) を比較することにより、クライアントが本物かどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-127">The service verifies the authenticity of the client by comparing the client's channel binding token (CBT) specific to that channel, with its own CBT.</span></span> <span data-ttu-id="e5aec-128">チャネル バインドでは、おびき寄せによる攻撃となりすましによる攻撃の両方に対処できますが、</span><span class="sxs-lookup"><span data-stu-id="e5aec-128">Channel binding addresses both luring and spoofing attacks.</span></span> <span data-ttu-id="e5aec-129">すべてのセッション トラフィックのトランスポート層セキュリティ (TLS) 暗号化が必要になるため、実行時のコストが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-129">However, it incurs a larger runtime cost, because it requires Transport Layer Security (TLS) encryption of all the session traffic.</span></span> <span data-ttu-id="e5aec-130">チャネル バインドが発生するのは、暗号化がクライアントとサーバーのどちらで強制されているかにかかわらず、クライアント アプリケーションが暗号化を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続する場合です。</span><span class="sxs-lookup"><span data-stu-id="e5aec-130">Channel Binding occurs when a client application uses encryption to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], regardless of whether encryption is enforced by the client or by the server.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e5aec-131">および [!INCLUDE[msCoName](../../includes/msconame-md.md)] 向けの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ プロバイダーでは、SSL 3.0、TLS 1.0 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e5aec-131">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] data providers for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support TLS 1.0 and SSL 3.0.</span></span> <span data-ttu-id="e5aec-132">オペレーティング システムの SChannel 層を変更して別のプロトコル (TLS 1.1、TLS 1.2 など) を適用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-132">If you enforce a different protocol (such as TLS 1.1 or TLS 1.2) by making changes in the operating system SChannel layer, your connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might fail.</span></span>  
  
### <a name="operating-system-support"></a><span data-ttu-id="e5aec-133">オペレーティング システムのサポート</span><span class="sxs-lookup"><span data-stu-id="e5aec-133">Operating System Support</span></span>  
 <span data-ttu-id="e5aec-134">Windows による **拡張保護**のサポートの詳細については、以下のリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5aec-134">The following links provide more information about how Windows supports **Extended Protection**:</span></span>  
  
-   [<span data-ttu-id="e5aec-135">拡張保護付き統合 Windows 認証</span><span class="sxs-lookup"><span data-stu-id="e5aec-135">Integrated Windows Authentication with Extended Protection</span></span>](https://msdn.microsoft.com/library/dd639324.aspx)  
  
-   [<span data-ttu-id="e5aec-136">マイクロソフト セキュリティ アドバイザリ (973811)、認証の拡張保護</span><span class="sxs-lookup"><span data-stu-id="e5aec-136">Microsoft Security Advisory (973811), Extended Protection for Authentication</span></span>](https://support.microsoft.com//help/973811/microsoft-security-advisory-extended-protection-for-authentication)  
  
## <a name="settings"></a><span data-ttu-id="e5aec-137">設定</span><span class="sxs-lookup"><span data-stu-id="e5aec-137">Settings</span></span>  
 <span data-ttu-id="e5aec-138">サービス バインドとチャネル バインドに影響する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の接続設定は 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-138">There are three [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection settings that affect service binding and channel binding.</span></span> <span data-ttu-id="e5aec-139">これらの設定を構成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは WMI を使用します。これらの設定を表示するには、ポリシー ベースの管理の **[サーバー プロトコル設定]** ファセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-139">The settings can be configured by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or by using WMI, and can by viewed by using the **Server Protocol Settings** facet of Policy Based Management.</span></span>  
  
-   <span data-ttu-id="e5aec-140">**[強制的に暗号化]**</span><span class="sxs-lookup"><span data-stu-id="e5aec-140">**Force Encryption**</span></span>  
  
     <span data-ttu-id="e5aec-141">選択できる値は、 **[オン]** と **[オフ]** です。</span><span class="sxs-lookup"><span data-stu-id="e5aec-141">Possible values are **On** and **Off**.</span></span> <span data-ttu-id="e5aec-142">チャネル バインドを使用する場合は、 **[強制的に暗号化]** を **[オン]** に設定して、すべてのクライアントで暗号化が強制されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-142">To use channel binding, **Force Encryption** must be set to **On**, and all clients will be forced to encrypt.</span></span> <span data-ttu-id="e5aec-143">この設定を **[オフ]** にした場合、保証されるのはサービス バインドだけになります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-143">If it is **Off**, only service binding is guaranteed.</span></span> <span data-ttu-id="e5aec-144">**[強制的に暗号化]** は、 **構成マネージャーの** [MSSQLSERVER のプロトコルのプロパティ] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([フラグ] タブ) にあります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-144">**Force Encryption** is on the **Protocols for MSSQLSERVER Properties (Flags Tab)** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="e5aec-145">**拡張保護**</span><span class="sxs-lookup"><span data-stu-id="e5aec-145">**Extended Protection**</span></span>  
  
     <span data-ttu-id="e5aec-146">選択できる値は、 **[オフ]** 、 **[許可]** 、および **[必須]** です。</span><span class="sxs-lookup"><span data-stu-id="e5aec-146">Possible values are **Off**, **Allowed**, and **Required**.</span></span> <span data-ttu-id="e5aec-147">**拡張保護** 変数を使用すると、各 **インスタンスの** 拡張保護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レベルを構成できます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-147">The **Extended Protection** variable lets users configure the **Extended Protection** level for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e5aec-148">**[拡張保護]** は、 **構成マネージャーの** [MSSQLSERVER のプロトコルのプロパティ] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([詳細設定] タブ) にあります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-148">**Extended Protection** is on the **Protocols for MSSQLSERVER Properties (Advanced Tab)** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
    -   <span data-ttu-id="e5aec-149">**[オフ]** に設定すると、 **[拡張保護]** は無効になります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-149">When set to **Off**, **Extended Protection** is disabled.</span></span> <span data-ttu-id="e5aec-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスは、クライアントが保護されているかどうかに関係なく、任意のクライアントからの接続を許可します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-150">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will accept connections from any client regardless of whether the client is protected or not.</span></span> <span data-ttu-id="e5aec-151">**[オフ]** は、古いオペレーティング システムや修正プログラムの適用が解除されたオペレーティング システムと互換性がありますが、安全性は低くなります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-151">**Off** is compatible with older and unpatched operating systems, but is less secure.</span></span> <span data-ttu-id="e5aec-152">この設定は、クライアント オペレーティング システムで拡張保護がサポートされていないことがわかっている場合に使用してください。</span><span class="sxs-lookup"><span data-stu-id="e5aec-152">Use this setting when you know that the client operating systems do not support extended protection.</span></span>  
  
    -   <span data-ttu-id="e5aec-153">**[許可]** に設定すると、 **拡張保護** をサポートするオペレーティング システムからの接続に **拡張保護**が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-153">When set to **Allowed**, **Extended Protection** is required for connections from operating systems that support **Extended Protection**.</span></span> <span data-ttu-id="e5aec-154">**拡張保護** をサポートしないオペレーティング システムからの接続では **拡張保護**が無視されます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-154">**Extended Protection** is ignored for connections from operating systems that do not support **Extended Protection**.</span></span> <span data-ttu-id="e5aec-155">保護されたクライアント オペレーティング システムで実行されている保護されていないクライアント アプリケーションからの接続は拒否されます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-155">Connections from unprotected client applications that are running on protected client operating systems are rejected.</span></span> <span data-ttu-id="e5aec-156">この設定は、 **[オフ]** よりも安全性が高いですが、最も安全な設定ではありません。</span><span class="sxs-lookup"><span data-stu-id="e5aec-156">This setting is more secure than **Off**, but is not the most secure setting.</span></span> <span data-ttu-id="e5aec-157">この設定は、 **拡張保護** をサポートするオペレーティング システムとサポートしないオペレーティング システムが混在する環境で使用します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-157">Use this setting in mixed environments, where some operating systems support **Extended Protection** and some do not.</span></span>  
  
    -   <span data-ttu-id="e5aec-158">**[必須]** に設定すると、保護されたクライアント オペレーティング システム上の保護されているアプリケーションからの接続のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-158">When set to **Required**, only connections from protected applications on protected operating systems are accepted.</span></span> <span data-ttu-id="e5aec-159">この設定は最も安全ですが、 **拡張保護** をサポートしないオペレーティング システムやアプリケーションからの接続では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続することができません。</span><span class="sxs-lookup"><span data-stu-id="e5aec-159">This setting is the most secure but connections from operating systems or applications that do not support **Extended Protection** will not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e5aec-160">**[承認された NTLM SPN]**</span><span class="sxs-lookup"><span data-stu-id="e5aec-160">**Accepted NTLM SPNs**</span></span>  
  
     <span data-ttu-id="e5aec-161">**[承認された NTLM SPN]** の変数は、サーバーに複数の SPN がある場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="e5aec-161">The **Accepted NTLM SPNs** variable is needed when a server is known by more than one SPN.</span></span> <span data-ttu-id="e5aec-162">クライアントがサーバーへの接続に使用した有効な SPN がサーバーで認識されないと、サービス バインドが失敗します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-162">When a client attempts to connect to the server by using a valid SPN that the server does not know, service binding will fail.</span></span> <span data-ttu-id="e5aec-163">この問題を回避するには、 **[承認された NTLM SPN]** を使用して、サーバーを表す複数の SPN を指定します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-163">To avoid this problem, users can specify several SPNs that represent the server by using **Accepted NTLM SPNs**.</span></span> <span data-ttu-id="e5aec-164">**[承認された NTLM SPN]** には、一連の SPN をセミコロンで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-164">**Accepted NTLM SPNs** is a series of SPNs separated my semicolons.</span></span> <span data-ttu-id="e5aec-165">たとえば、 **MSSQLSvc/ HostName1.Contoso.com** および **MSSQLSvc/ HostName2.Contoso.com**という SPN を許可するには、 **[承認された NTLM SPN]** ボックスに「 **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-165">For example, to allow the SPNs **MSSQLSvc/ HostName1.Contoso.com** and **MSSQLSvc/ HostName2.Contoso.com**, type **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com** in the **Accepted NTLM SPNs** box.</span></span> <span data-ttu-id="e5aec-166">変数の最大長は 2048 文字です。</span><span class="sxs-lookup"><span data-stu-id="e5aec-166">The variable has a maximum length of 2,048 characters.</span></span> <span data-ttu-id="e5aec-167">**[承認された NTLM SPN]** は、 **構成マネージャーの** [MSSQLSERVER のプロトコルのプロパティ] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([詳細設定] タブ)) にあります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-167">**Accepted NTLM SPNs** is on the **Protocols for MSSQLSERVER Properties (Advanced Tab)** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="enabling-extended-protection-for-the-database-engine"></a><span data-ttu-id="e5aec-168">データベース エンジンでの拡張保護の有効化</span><span class="sxs-lookup"><span data-stu-id="e5aec-168">Enabling Extended Protection for the Database Engine</span></span>  
 <span data-ttu-id="e5aec-169">**拡張保護**を使用するには、サーバーとクライアントの両方のオペレーティング システムで **拡張保護**がサポートされていて、オペレーティング システムで **拡張保護** が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-169">To use **Extended Protection**, both the server and the client must have an operating system on that supports **Extended Protection**, and **Extended Protection** must be enabled on the operating system.</span></span> <span data-ttu-id="e5aec-170">オペレーティング システムで **拡張保護** を有効にする方法の詳細については、「 [認証に対する保護の強化](https://support.microsoft.com/kb/968389)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5aec-170">For more information about how to enable **Extended Protection** for the operating system, see [Extended Protection for Authentication](https://support.microsoft.com/kb/968389).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e5aec-171">では **で始まる** 拡張保護 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e5aec-171">supports **Extended Protection** beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="e5aec-172">以前のバージョンの**については、今後の更新によって一部で** 拡張保護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e5aec-172">**Extended Protection** for some earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be made available in future updates.</span></span> <span data-ttu-id="e5aec-173">サーバー コンピューターで **拡張保護** を有効にした後、次の手順に従って **拡張保護**を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e5aec-173">After enabling **Extended Protection** on the server computer, use the following steps to enable **Extended Protection**:</span></span>  
  
1.  <span data-ttu-id="e5aec-174">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5aec-174">On the **Start** menu, choose **All Programs**, point to **Microsoft SQL Server** and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="e5aec-175">[ **SQL Server ネットワーク構成**] を展開し、[**のプロトコル**] を右クリックし *\<*InstanceName*>* て、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5aec-175">Expand **SQL Server Network Configuration**, and then right-click **Protocols for** *\<*InstanceName*>*, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e5aec-176">チャネル バインドとサービス バインドの両方について、 **[詳細設定]** タブで **[拡張保護]** を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-176">For both channel binding and service binding, on the **Advanced** tab, set **Extended Protection** to the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="e5aec-177">サーバーに複数の SPN がある場合は、 **[詳細設定]** タブで **[承認された NTLM SPN]** フィールドを構成します。詳細については、「設定」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5aec-177">Optionally, when a server is known by more than one SPN, on the **Advanced** tab configure the **Accepted NTLM SPNs** field as described in the "Settings" section.</span></span>  
  
5.  <span data-ttu-id="e5aec-178">チャネル バインドを使用する場合は、 **[フラグ]** タブで **[強制的に暗号化]** を **[オン]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-178">For channel binding, on the **Flags** tab, set **Force Encryption** to **On**.</span></span>  
  
6.  <span data-ttu-id="e5aec-179">[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="e5aec-179">Restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service.</span></span>  
  
## <a name="configuring-other-sql-server-components"></a><span data-ttu-id="e5aec-180">その他の SQL Server コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="e5aec-180">Configuring Other SQL Server Components</span></span>  
 <span data-ttu-id="e5aec-181">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の 構成方法の詳細については、「 [Reporting Services での認証の拡張保護](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5aec-181">For more information about how to configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Extended Protection for Authentication with Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
 <span data-ttu-id="e5aec-182">IIS を使用して HTTP 接続または HTTPS 接続経由で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データにアクセスする場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で IIS によって提供される拡張保護を利用できます。</span><span class="sxs-lookup"><span data-stu-id="e5aec-182">When using IIS to access [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data using an HTTP or HTTPs connection, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] can take advantage of Extended Protection provided by IIS.</span></span> <span data-ttu-id="e5aec-183">拡張保護を使用するように IIS を構成する方法の詳細については、「 [IIS 7.5 における拡張保護の構成](https://go.microsoft.com/fwlink/?LinkId=181105)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5aec-183">For more information about how to configure IIS to use Extended Protection, see [Configure Extended Protection in IIS 7.5](https://go.microsoft.com/fwlink/?LinkId=181105).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5aec-184">参照</span><span class="sxs-lookup"><span data-stu-id="e5aec-184">See Also</span></span>  
 <span data-ttu-id="e5aec-185">[サーバー ネットワークの構成](server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e5aec-185">[Server Network Configuration](server-network-configuration.md) </span></span>  
 <span data-ttu-id="e5aec-186">[クライアント ネットワーク構成](client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e5aec-186">[Client Network Configuration](client-network-configuration.md) </span></span>  
 <span data-ttu-id="e5aec-187">[認証の拡張保護の概要](https://go.microsoft.com/fwlink/?LinkID=177943) </span><span class="sxs-lookup"><span data-stu-id="e5aec-187">[Extended Protection for Authentication Overview](https://go.microsoft.com/fwlink/?LinkID=177943) </span></span>  
 [<span data-ttu-id="e5aec-188">拡張保護付き統合 Windows 認証</span><span class="sxs-lookup"><span data-stu-id="e5aec-188">Integrated Windows Authentication with Extended Protection</span></span>](https://go.microsoft.com/fwlink/?LinkId=179922)  
  
  