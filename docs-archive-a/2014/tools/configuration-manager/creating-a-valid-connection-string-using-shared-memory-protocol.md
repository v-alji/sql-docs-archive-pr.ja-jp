---
title: 共有メモリ プロトコルを使用した有効な接続文字列の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca97332a09a33fcfc15a3dbb2599af27dbe0e1db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711377"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a><span data-ttu-id="67a8d-102">共有メモリ プロトコルを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="67a8d-102">Creating a Valid Connection String Using Shared Memory Protocol</span></span>
  <span data-ttu-id="67a8d-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に同じコンピューター上で実行されているクライアントから接続する場合は、共有メモリ プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="67a8d-103">Connections to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client running on the same computer use the shared memory protocol.</span></span> <span data-ttu-id="67a8d-104">共有メモリには、構成可能なプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="67a8d-104">Shared memory has no configurable properties.</span></span> <span data-ttu-id="67a8d-105">共有メモリは常に最初に試行されるプロトコルであり、 **[クライアント プロトコルのプロパティ]** 一覧にある **[有効なプロトコル]** 一覧の最上位から移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="67a8d-105">Shared memory is always tried first, and cannot be moved from the top position of the **Enabled Protocols** list in the **Client Protocols Properties** list.</span></span> <span data-ttu-id="67a8d-106">共有プロトコルを無効にすることは可能です。これは、他のプロトコルのトラブルシューティングを行うときに便利です。</span><span class="sxs-lookup"><span data-stu-id="67a8d-106">The Shared Memory protocol can be disabled, which is useful when troubleshooting one of the other protocols.</span></span>  
  
 <span data-ttu-id="67a8d-107">共有メモリ プロトコルを使用して別名を作成することはできませんが、共有メモリが有効になっている状態で [!INCLUDE[ssDE](../../includes/ssde-md.md)] に名前で接続すると、共有メモリ接続が作成されます。</span><span class="sxs-lookup"><span data-stu-id="67a8d-107">You cannot create an alias using the shared memory protocol, but if shared memory is enabled, then connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by name, creates a shared memory connection.</span></span> <span data-ttu-id="67a8d-108">共有メモリ接続文字列の形式は、 `lpc:<servername>[\instancename]`です。</span><span class="sxs-lookup"><span data-stu-id="67a8d-108">A shared memory connection string uses the format `lpc:<servername>[\instancename]`.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="67a8d-109">ローカル サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="67a8d-109">Connecting to the Local Server</span></span>  
 <span data-ttu-id="67a8d-110">クライアントと同じコンピューター上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合は、サーバー名として " **(local)** " を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="67a8d-110">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use **(local)** as the server name.</span></span> <span data-ttu-id="67a8d-111">このような指定はあいまいさを残すのでお勧めできませんが、対象のコンピューター上でクライアントを実行していることがわかっている場合には便利な機能です。</span><span class="sxs-lookup"><span data-stu-id="67a8d-111">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="67a8d-112">たとえば、営業スタッフは、ノート PC 上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行し、プロジェクト データもそのノート PC に保存しておきます。このように、ネットワークに接続しないモバイル ユーザー用のアプリケーションの場合、 **(local)** に接続するクライアントは、常にそのノート PC で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することになります。</span><span class="sxs-lookup"><span data-stu-id="67a8d-112">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to **(local)** would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="67a8d-113">" **(local)** " の代わりに "**localhost**" またはピリオド ( **.** ) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="67a8d-113">The word **localhost** or a period (**.**) can be used in place of **(local)**.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="67a8d-114">接続プロトコルの確認</span><span class="sxs-lookup"><span data-stu-id="67a8d-114">Verifying your Connection Protocol</span></span>  
 <span data-ttu-id="67a8d-115">以下のクエリは、現在の接続に使用しているプロトコルを返します。</span><span class="sxs-lookup"><span data-stu-id="67a8d-115">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="67a8d-116">例 :</span><span class="sxs-lookup"><span data-stu-id="67a8d-116">Examples:</span></span>  
 <span data-ttu-id="67a8d-117">共有メモリ プロトコルが有効になっている場合に、以下の名前を使用すると、共有メモリを使用してローカル コンピューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="67a8d-117">The following names will connect to the local computer with the shared memory protocol if it is enabled:</span></span>  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 <span data-ttu-id="67a8d-118">共有メモリ接続のための別名を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="67a8d-118">You cannot create an alias for a shared memory connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67a8d-119">**[サーバー]** ボックスで IP アドレスを指定すると、TCP/IP 接続になります。</span><span class="sxs-lookup"><span data-stu-id="67a8d-119">Specifying an IP Address in the **Server** box will result in a TCP/IP connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a8d-120">参照</span><span class="sxs-lookup"><span data-stu-id="67a8d-120">See Also</span></span>  
 <span data-ttu-id="67a8d-121">[TCP/IP を使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="67a8d-121">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 <span data-ttu-id="67a8d-122">[名前付きパイプを使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="67a8d-122">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="67a8d-123">ネットワーク プロトコルの選択</span><span class="sxs-lookup"><span data-stu-id="67a8d-123">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
