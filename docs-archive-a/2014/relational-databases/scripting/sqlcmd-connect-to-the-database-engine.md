---
title: sqlcmd によるデータベース エンジンへの接続
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sqlcmd utility, Database Engine connections
- Named Pipes [SQL Server], sqlcmd utility
- TCP/IP [SQL Server], client protocols
- network protocols [SQL Server], sqlcmd utility
- protocols [SQL Server], sqlcmd utility
- VIA
- client protocols [SQL Server]
ms.assetid: 74b0fb71-7f8e-4171-9431-d07528532524
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b409683b651e3e6508baced5eb3bc9fcc631e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633048"
---
# <a name="connect-to-the-database-engine-with-sqlcmd"></a><span data-ttu-id="f2805-102">sqlcmd によるデータベース エンジンへの接続</span><span class="sxs-lookup"><span data-stu-id="f2805-102">Connect to the Database Engine With sqlcmd</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f2805-103">TCP/IP ネットワーク プロトコル (既定) および名前付きパイプ プロトコルを使用したクライアント通信をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f2805-103">supports client communication with the TCP/IP network protocol (the default), and the named pipes protocol.</span></span> <span data-ttu-id="f2805-104">クライアントが、同じコンピューター上で[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続している場合は、共有メモリ プロトコルも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2805-104">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="f2805-105">プロトコルの選択には、3 つの一般的な方法があります。</span><span class="sxs-lookup"><span data-stu-id="f2805-105">There are three common methods of selecting the protocol.</span></span> <span data-ttu-id="f2805-106">**sqlcmd** ユーティリティで使用されるプロトコルは、次の順序で決定されます。</span><span class="sxs-lookup"><span data-stu-id="f2805-106">The protocol used by the **sqlcmd** utility is determined in the following order:</span></span>  
  
-   <span data-ttu-id="f2805-107">**sqlcmd** では、下に示す接続文字列の一部として指定されているプロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2805-107">**sqlcmd** uses the protocol specified as part of the connection string as described below.</span></span>  
  
-   <span data-ttu-id="f2805-108">接続文字列でプロトコルが指定されていない場合、 **sqlcmd** では、接続先の別名の一部として定義されているプロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2805-108">If no protocol is specified as part the connection string, **sqlcmd** will use the protocol defined as part of the alias that it is connecting to.</span></span> <span data-ttu-id="f2805-109">別名を作成して特定のネットワーク プロトコルを使用するように **sqlcmd** を構成するには、「[クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2805-109">To configure **sqlcmd** to use a specific network protocol by creating an alias, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="f2805-110">他の方法でプロトコルが指定されていない場合、 **sqlcmd** では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで指定されているプロトコル順序によって使用するネットワーク プロトコルが決定されます。</span><span class="sxs-lookup"><span data-stu-id="f2805-110">If the protocol is not specified in some other way, **sqlcmd** will use the network protocol determined by the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="f2805-111">次の例では、ポート 1433 の [!INCLUDE[ssDE](../../includes/ssde-md.md)] の既定のインスタンスと、ポート 1691 でリッスンしていると想定される [!INCLUDE[ssDE](../../includes/ssde-md.md)] の名前付きインスタンスに接続するさまざまな方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f2805-111">The following examples show various ways of connecting to the default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on port 1433, and named instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] presumed to be listening on port 1691.</span></span> <span data-ttu-id="f2805-112">一部の例では、ループバック アダプターの IP アドレス (127.0.0.1) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="f2805-112">Some of these examples use the IP address of the loopback adapter (127.0.0.1).</span></span> <span data-ttu-id="f2805-113">使用しているコンピューターのネットワーク インターフェイス カードの IP アドレスを使用してテストしてください。</span><span class="sxs-lookup"><span data-stu-id="f2805-113">Test using the IP address of your computer network interface card.</span></span>  
  
 <span data-ttu-id="f2805-114">インスタンス名を指定して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-114">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the instance name:</span></span>  
  
```  
sqlcmd -S ComputerA  
sqlcmd -S ComputerA\instanceB  
```  
  
 <span data-ttu-id="f2805-115">IP アドレスを指定して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-115">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the IP address:</span></span>  
  
```  
sqlcmd -S 127.0.0.1  
sqlcmd -S 127.0.0.1\instanceB  
```  
  
 <span data-ttu-id="f2805-116">TCP/IP ポート番号を指定して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the TCP\IP port number:</span></span>  
  
```  
sqlcmd -S ComputerA,1433  
sqlcmd -S ComputerA,1691  
sqlcmd -S 127.0.0.1,1433  
sqlcmd -S 127.0.0.1,1691  
```  
  
### <a name="to-connect-using-tcpip"></a><span data-ttu-id="f2805-117">TCP/IP を使用して接続するには</span><span class="sxs-lookup"><span data-stu-id="f2805-117">To connect using TCP/IP</span></span>  
  
-   <span data-ttu-id="f2805-118">次に示す一般構文を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-118">Connect using the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S tcp:<computer name>,<port number>  
    ```  
  
-   <span data-ttu-id="f2805-119">既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-119">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1433  
    sqlcmd -S tcp:127.0.0.1,1433  
    ```  
  
-   <span data-ttu-id="f2805-120">名前付きインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-120">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1691  
    sqlcmd -S tcp:127.0.0.1,1691  
    ```  
  
### <a name="to-connect-using-named-pipes"></a><span data-ttu-id="f2805-121">名前付きパイプを使用して接続するには</span><span class="sxs-lookup"><span data-stu-id="f2805-121">To connect using named pipes</span></span>  
  
-   <span data-ttu-id="f2805-122">次に示す一般構文のいずれかを使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-122">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S np:\\<computer name>\<pipe name>  
    ```  
  
-   <span data-ttu-id="f2805-123">既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-123">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\sql\query  
    ```  
  
-   <span data-ttu-id="f2805-124">名前付きインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-124">Connect to a named instance instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\MSSQL$<instancename>\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\MSSQL$<instancename>\sql\query  
    ```  
  
### <a name="to-connect-using-shared-memory-a-local-procedure-call-from-a-client-on-the-server"></a><span data-ttu-id="f2805-125">サーバー上のクライアントから共有メモリ (ローカル プロシージャ コール) を使用して接続するには</span><span class="sxs-lookup"><span data-stu-id="f2805-125">To connect using shared memory (a local procedure call) from a client on the server</span></span>  
  
-   <span data-ttu-id="f2805-126">次に示す一般構文のいずれかを使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-126">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S lpc:<computer name>  
    ```  
  
-   <span data-ttu-id="f2805-127">既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-127">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA  
    ```  
  
-   <span data-ttu-id="f2805-128">名前付きインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f2805-128">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA\<instancename>  
    ```  
  
  
