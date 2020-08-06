---
title: SQL Native Client 11.0 Configuration |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client configuration [SQL Server], SQL Server Native Client
ms.assetid: e73143e9-5e7b-4d0a-8827-ab900efdcb35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 183dd2d161b1bf0b13140a607167b81dab086fdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632873"
---
# <a name="sql-native-client-110-configuration"></a><span data-ttu-id="44f87-102">SQL Native Client 11.0 の構成</span><span class="sxs-lookup"><span data-stu-id="44f87-102">SQL Native Client 11.0 Configuration</span></span>
  <span data-ttu-id="44f87-103">ここでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの **[SQL Server Native Client の構成]** ダイアログ ボックスの F1 ヘルプ トピックについて紹介します。</span><span class="sxs-lookup"><span data-stu-id="44f87-103">This section contains the F1 Help topics for the **SQL Server Native Client Configuration** dialogs in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="44f87-104">Native Client は、クライアント コンピューターが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するために使用するネットワーク ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="44f87-104">Native Client is the network library that client computers use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], starting with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="44f87-105">[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の構成] ダイアログ ボックスの設定は、クライアント プログラムを実行するコンピューターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="44f87-105">The settings configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Configuration, are used on the computer running the client program.</span></span> <span data-ttu-id="44f87-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行するコンピューター上で構成された設定は、サーバー上で実行するクライアント プログラムだけに影響します。</span><span class="sxs-lookup"><span data-stu-id="44f87-106">When configured on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they affect only those client programs running on the server.</span></span>  
  
 <span data-ttu-id="44f87-107">この設定は、旧バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続するクライアントには影響しません。ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以降のクライアント ツール ( [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]など) を使用する場合は例外です。</span><span class="sxs-lookup"><span data-stu-id="44f87-107">These settings do not affect clients connecting to previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], unless they are using the client tools starting with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44f87-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="44f87-108">In this Section</span></span>  
  
-   <span data-ttu-id="44f87-109">[[SQL Server Native Client の構成のプロパティ] ダイアログ ボックス &#40;[フラグ] タブ&#41;](../../../2014/tools/configuration-manager/sql-server-native-client-configuration-properties-flags-tab.md)</span><span class="sxs-lookup"><span data-stu-id="44f87-109">[SQL Server Native Client Configuration Properties &#40;Flags Tab&#41;](../../../2014/tools/configuration-manager/sql-server-native-client-configuration-properties-flags-tab.md)</span></span>  
  
-   [<span data-ttu-id="44f87-110">クライアント プロトコル &#40;SQL Server 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="44f87-110">Client Protocols &#40;SQL Server Configuration Manager&#41;</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
    -   <span data-ttu-id="44f87-111">[[クライアント プロトコルのプロパティ] ダイアログ ボックス &#40;[順序] タブ&#41;](../../../2014/tools/configuration-manager/client-protocols-properties-order-tab.md)</span><span class="sxs-lookup"><span data-stu-id="44f87-111">[Client Protocols Properties &#40;Order Tab&#41;](../../../2014/tools/configuration-manager/client-protocols-properties-order-tab.md)</span></span>  
  
    -   <span data-ttu-id="44f87-112">[クライアント プロトコル - [共有メモリのプロパティ] ダイアログ ボックス &#40;[プロトコル] タブ&#41;](../../../2014/tools/configuration-manager/client-protocols-shared-memory-properties-protocol-tab.md)</span><span class="sxs-lookup"><span data-stu-id="44f87-112">[Client Protocols - Shared Memory Properties &#40;Protocol Tab&#41;](../../../2014/tools/configuration-manager/client-protocols-shared-memory-properties-protocol-tab.md)</span></span>  
  
    -   <span data-ttu-id="44f87-113">[クライアントプロトコル-TCP および IP のプロパティ &#40;プロトコル] タブ&#41;](../../../2014/tools/configuration-manager/client-protocols-tcp-and-ip-properties-protocol-tab.md)</span><span class="sxs-lookup"><span data-stu-id="44f87-113">[Client Protocols - TCP and IP Properties &#40;Protocol Tab&#41;](../../../2014/tools/configuration-manager/client-protocols-tcp-and-ip-properties-protocol-tab.md)</span></span>  
  
    -   <span data-ttu-id="44f87-114">[クライアント プロトコル - [名前付きパイプのプロパティ] ダイアログ ボックス &#40;[プロトコル] タブ&#41;](../../../2014/tools/configuration-manager/client-protocols-named-pipes-properties-protocol-tab.md)</span><span class="sxs-lookup"><span data-stu-id="44f87-114">[Client Protocols - Named Pipes Properties &#40;Protocol Tab&#41;](../../../2014/tools/configuration-manager/client-protocols-named-pipes-properties-protocol-tab.md)</span></span>  
  
-   [<span data-ttu-id="44f87-115">別名 &#40;SQL Server 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="44f87-115">Aliases &#40;SQL Server Configuration Manager&#41;</span></span>](../../../2014/tools/configuration-manager/aliases-sql-server-configuration-manager.md)  
  
    -   <span data-ttu-id="44f87-116">[[別名 - 新規] ダイアログ ボックス &#40;[別名] タブ&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)</span><span class="sxs-lookup"><span data-stu-id="44f87-116">[New Alias &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)</span></span>  
  
    -   <span data-ttu-id="44f87-117">[[&#60;Alias&#62; のプロパティ] ダイアログ ボックス &#40;[別名] タブ&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)</span><span class="sxs-lookup"><span data-stu-id="44f87-117">[&#60;Alias&#62; Properties &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)</span></span>  
  
    -   [<span data-ttu-id="44f87-118">共有メモリ プロトコルを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="44f87-118">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
    -   [<span data-ttu-id="44f87-119">TCP/IP を使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="44f87-119">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
    -   [<span data-ttu-id="44f87-120">名前付きパイプを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="44f87-120">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
