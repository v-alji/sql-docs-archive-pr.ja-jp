---
title: '[SQL Server Native Client の構成のプロパティ] ダイアログ ボックス ([フラグ] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3ca7b87963fc3848bbb933a5c21f9d608d37d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644715"
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a><span data-ttu-id="6c4a1-102">[SQL Server Native Client の構成のプロパティ] ダイアログ ボックス ([フラグ] タブ)</span><span class="sxs-lookup"><span data-stu-id="6c4a1-102">SQL Server Native Client Configuration Properties (Flags Tab)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6c4a1-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ライブラリ ファイルで提供されているプロトコルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーと通信します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this machine, communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers using the protocols provided in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client library file.</span></span> <span data-ttu-id="6c4a1-104">このページでは、クライアント コンピューターで SSL (Secure Sockets Layer) を使用した暗号化接続を要求するための構成を行います。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-104">This page provides configures the client computer to request an encrypted connection using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="6c4a1-105">暗号化接続を確立できない場合は、接続が失敗します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-105">If an encrypted connection cannot be established, the connection will fail.</span></span>  
  
 <span data-ttu-id="6c4a1-106">ログイン プロセスは常に暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-106">The login process is always encrypted.</span></span> <span data-ttu-id="6c4a1-107">以下のオプションは暗号化されているデータにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-107">The options below apply only to encrypting data.</span></span> <span data-ttu-id="6c4a1-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が通信を暗号化する方法の詳細、およびサーバー証明書のルート機関を信頼するようにクライアントを構成する方法については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「 [!INCLUDE[ssDE](../../includes/ssde-md.md)] への接続の暗号化」と「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への暗号化接続を有効にする方法 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-108">For more information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypts communication and for instructions on how to configure the client to trust the root authority of the server certificate, see "Encrypting Connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" and "How to: Enable Encrypted Connections to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6c4a1-109">Options</span><span class="sxs-lookup"><span data-stu-id="6c4a1-109">Options</span></span>  
 <span data-ttu-id="6c4a1-110">**[Force protocol encryption]**</span><span class="sxs-lookup"><span data-stu-id="6c4a1-110">**Force protocol encryption**</span></span>  
 <span data-ttu-id="6c4a1-111">常に、SSL を使用して接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-111">Request a connection using SSL.</span></span>  
  
 <span data-ttu-id="6c4a1-112">**[Trust Server Certificate]**</span><span class="sxs-lookup"><span data-stu-id="6c4a1-112">**Trust Server Certificate**</span></span>  
 <span data-ttu-id="6c4a1-113">**[いいえ]** に設定されている場合、クライアント プロセスはサーバー証明書の検証を試みます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-113">When set to **No**, the client process attempts to validate the server certificate.</span></span> <span data-ttu-id="6c4a1-114">クライアントとサーバーはそれぞれ、公的な証明機関から発行された証明書を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-114">The client and server must have each have a certificate issues from a public certification authority.</span></span> <span data-ttu-id="6c4a1-115">クライアント コンピューターに証明書がない場合や、証明書の検証が失敗した場合は、接続が終了します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-115">If the certificate is not present on the client computer, or if the validation of the certificate fails, the connection is terminated.</span></span>  
  
 <span data-ttu-id="6c4a1-116">**[はい]** に設定されている場合、クライアントは、サーバー証明書を検証せずに、自己署名証明書の使用を許可します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-116">When set to **Yes**, the client does not validate the server certificate, thereby enabling the use of a self-signed certificate.</span></span>  
  
 <span data-ttu-id="6c4a1-117">**[Trust Server Certificate]** は、 **[Force protocol encryption]** が **[はい]** に設定されている場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-117">**Trust Server Certificate** is only available if **Force protocol encryption** is set to **Yes**.</span></span>  
  
  
