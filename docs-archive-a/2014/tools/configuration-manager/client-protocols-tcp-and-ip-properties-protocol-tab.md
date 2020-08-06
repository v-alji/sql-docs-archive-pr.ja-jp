---
title: クライアントプロトコル-TCP および IP のプロパティ ([プロトコル] タブ) |Microsoft Docs
description: Microsoft SQL Server Configuration Manager で TCP/IP オプションを指定する方法 (キープアライブパラメーターや既定のポート番号など) について説明します。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: rothja
ms.author: jroth
ms.openlocfilehash: dfcf0348dc863970384a40cc9e773481adeedb35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737357"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a><span data-ttu-id="4a5d0-103">クライアント プロトコル - TCP および IP のプロパティ ([プロトコル] タブ)</span><span class="sxs-lookup"><span data-stu-id="4a5d0-103">Client Protocols - TCP and IP Properties (Protocol Tab)</span></span>
  <span data-ttu-id="4a5d0-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、**[TCP/IP のプロパティ]** ダイアログ ボックスの **[プロトコル]** タブを使用して、以下のオプションの表示や指定を行います。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-104">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, use the **Protocol** tab on the **TCP/IP Properties** dialog box to view or specify the following options.</span></span> <span data-ttu-id="4a5d0-105">別のポートに接続するには、 **[既定のポート]** ボックスにポート番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-105">To connect to a different port, type the port number in the **Default Port** box.</span></span> <span data-ttu-id="4a5d0-106">接続文字列の詳細については、「 [TCP/IP を使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-106">For more information about connection strings, see [Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4a5d0-107">Options</span><span class="sxs-lookup"><span data-stu-id="4a5d0-107">Options</span></span>  
 <span data-ttu-id="4a5d0-108">**[既定のポート]**</span><span class="sxs-lookup"><span data-stu-id="4a5d0-108">**Default Port**</span></span>  
 <span data-ttu-id="4a5d0-109">TCP/IP Net-Library が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスに接続するために使用するポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-109">Specifies the port that the TCP/IP Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4a5d0-110">既定値のポートは 1433 です。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-110">The default value port is 1433.</span></span>  
  
 <span data-ttu-id="4a5d0-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスに接続する場合、クライアントはこの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-111">When connecting to a default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client uses this value.</span></span> <span data-ttu-id="4a5d0-112">既定のインスタンスが別のポートでリッスンするように構成されている場合は、この値をそのポート番号に変更してください。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-112">If a default instance has been configured to listen on a different port, change this value to that port number.</span></span>  
  
 <span data-ttu-id="4a5d0-113">[!INCLUDE[ssDE](../../includes/ssde-md.md)]の名前付きインスタンスに接続する場合、クライアントはサーバー コンピューターで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスからポート番号の取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-113">When connecting to a named instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client will attempt to obtain the port number from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service running on the server computer.</span></span> <span data-ttu-id="4a5d0-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていない場合、ポート番号がこの設定か、接続文字列の一部として指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-114">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service is not running, the port number must be provided through this setting, or as part of the connection string.</span></span>  
  
 <span data-ttu-id="4a5d0-115">**有効**</span><span class="sxs-lookup"><span data-stu-id="4a5d0-115">**Enabled**</span></span>  
 <span data-ttu-id="4a5d0-116">使用可能な値は**Yes**と**No**です。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-116">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="4a5d0-117">**キープアライブ**</span><span class="sxs-lookup"><span data-stu-id="4a5d0-117">**Keep Alive**</span></span>  
 <span data-ttu-id="4a5d0-118">このパラメーターは、 **KEEPALIVE** パケットを送信することによって、アイドル状態の接続が壊れていないかどうかを TCP が確認する頻度をミリ秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-118">This parameter (in milliseconds) controls how often TCP attempts to verify that an idle connection is still intact by sending a **KEEPALIVE** packet.</span></span> <span data-ttu-id="4a5d0-119">既定値は 30,000 ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-119">The default is 30000 milliseconds.</span></span>  
  
 <span data-ttu-id="4a5d0-120">**[Keep Alive 間隔]**</span><span class="sxs-lookup"><span data-stu-id="4a5d0-120">**Keep Alive Interval**</span></span>  
 <span data-ttu-id="4a5d0-121">このパラメーターは、応答を受信するまで **KEEPALIVE** パケットを再送信する間隔をミリ秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-121">This parameter (in milliseconds) determines the interval separating **KEEPALIVE** retransmissions until a response is received.</span></span> <span data-ttu-id="4a5d0-122">既定値は 1,000 ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="4a5d0-122">The default is 1000 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5d0-123">参照</span><span class="sxs-lookup"><span data-stu-id="4a5d0-123">See Also</span></span>  
 <span data-ttu-id="4a5d0-124">[ネットワークプロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="4a5d0-124">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 <span data-ttu-id="4a5d0-125">[新しいエイリアス &#40;エイリアス] タブ&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span><span class="sxs-lookup"><span data-stu-id="4a5d0-125">[New Alias &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span></span>  
 <span data-ttu-id="4a5d0-126">[[&#60;Alias&#62; のプロパティ] ダイアログ ボックス &#40;[別名] タブ&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)</span><span class="sxs-lookup"><span data-stu-id="4a5d0-126">[&#60;Alias&#62; Properties &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)</span></span>  
  
  
