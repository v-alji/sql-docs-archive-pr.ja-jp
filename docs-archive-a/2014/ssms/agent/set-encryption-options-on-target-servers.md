---
title: ターゲット サーバーでの暗号化オプションの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd10d2e05e59015542f41cc123de993e6128f9f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644282"
---
# <a name="set-encryption-options-on-target-servers"></a><span data-ttu-id="82407-102">ターゲット サーバーでの暗号化オプションの設定</span><span class="sxs-lookup"><span data-stu-id="82407-102">Set Encryption Options on Target Servers</span></span>
  <span data-ttu-id="82407-103">マスター サーバーと一部またはすべてのターゲット サーバーの間で SSL (Secure Sockets Layer) 暗号通信の証明書を使用できない場合、これらの間のチャネルを暗号化するには、必要なセキュリティ レベルを使用するようにターゲット サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="82407-103">If you cannot use a certificate for Secure Sockets Layer (SSL) encrypted communications between master servers and some or all of your target servers, but you want to encrypt the channel between them, configure the target server to use the level of security required.</span></span>  
  
 <span data-ttu-id="82407-104">特定のマスターサーバー/対象サーバーの通信チャネルに必要なセキュリティレベルを構成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 対象サーバーでエージェントのレジストリサブキー \*\*\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ \*\* \<*instance_name*> **\SQLServerAgent\MsxEncryptChannelOptions (REG_DWORD)** を次のいずれかの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="82407-104">To configure the appropriate level of security required for a specific master server/target server communication channel, set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** on the target server to one of the following values.</span></span> <span data-ttu-id="82407-105">の値 \<*instance_name*> は**MSSQL です。**_n_。</span><span class="sxs-lookup"><span data-stu-id="82407-105">The value of \<*instance_name*> is **MSSQL.**_n_.</span></span> <span data-ttu-id="82407-106">たとえば、 **MSSQL.1** や **MSSQL.3**となります。</span><span class="sxs-lookup"><span data-stu-id="82407-106">For example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
|<span data-ttu-id="82407-107">値</span><span class="sxs-lookup"><span data-stu-id="82407-107">Value</span></span>|<span data-ttu-id="82407-108">説明</span><span class="sxs-lookup"><span data-stu-id="82407-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="82407-109">**0**</span><span class="sxs-lookup"><span data-stu-id="82407-109">**0**</span></span>|<span data-ttu-id="82407-110">このターゲット サーバーとマスター サーバーの間の暗号化を無効にします。</span><span class="sxs-lookup"><span data-stu-id="82407-110">Disables encryption between this target server and the master server.</span></span> <span data-ttu-id="82407-111">ターゲット サーバーとマスター サーバー間のチャネルのセキュリティを別の手段で保護する場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="82407-111">Choose this option only when the channel between the target server and master server is secured by another means.</span></span>|  
|<span data-ttu-id="82407-112">**1**</span><span class="sxs-lookup"><span data-stu-id="82407-112">**1**</span></span>|<span data-ttu-id="82407-113">このターゲット サーバーとマスター サーバーの間のみ暗号化を有効にしますが、証明書の検証は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="82407-113">Enables encryption only between this target server and the master server, but no certificate validation is required.</span></span>|  
|<span data-ttu-id="82407-114">**2**</span><span class="sxs-lookup"><span data-stu-id="82407-114">**2**</span></span>|<span data-ttu-id="82407-115">このターゲット サーバーとマスター サーバーの間で、完全な SSL 暗号化と証明書の検証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="82407-115">Enables full SSL encryption and certificate validation between this target server and the master server.</span></span> <span data-ttu-id="82407-116">これは、既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="82407-116">This setting is the default.</span></span> <span data-ttu-id="82407-117">別の値を選択する具体的な理由がある場合を除いて、この値を変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="82407-117">Unless you have specific reason to choose a different value, we recommend not changing it.</span></span>|  
  
 <span data-ttu-id="82407-118">**1** または **2** を指定する場合、マスター サーバーとターゲット サーバーの両方で SSL を有効にしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="82407-118">If **1** or **2** is specified, you must have SSL enabled on both the master and target servers.</span></span> <span data-ttu-id="82407-119">**2** を指定する場合、マスター サーバーには適切に署名された証明書も必要になります。</span><span class="sxs-lookup"><span data-stu-id="82407-119">If **2** is specified, you must also have a properly signed certificate present on the master server.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82407-120">参照</span><span class="sxs-lookup"><span data-stu-id="82407-120">See Also</span></span>  
 [<span data-ttu-id="82407-121">データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="82407-121">Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;</span></span>](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
