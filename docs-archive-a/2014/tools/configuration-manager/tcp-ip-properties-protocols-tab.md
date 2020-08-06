---
title: '[TCP-IP のプロパティ] ([プロトコル] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d5bc28faddae9a86a6636b56b907b57a2d8711a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632252"
---
# <a name="tcp---ip-properties-protocols-tab"></a><span data-ttu-id="0adb0-102">[TCP-IP のプロパティ] ([プロトコル] タブ)</span><span class="sxs-lookup"><span data-stu-id="0adb0-102">TCP - IP Properties (Protocols Tab)</span></span>
  <span data-ttu-id="0adb0-103">**[TCP/IP のプロパティ]** ダイアログ ボックスは、TCP/IP プロトコルのオプションを構成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-103">Use the **TCP/IP Properties** dialog box to configure the options for the TCP/IP protocol.</span></span> <span data-ttu-id="0adb0-104">左ペインで **[TCP/IP]** をクリックすると、詳細ペインに個々の IP アドレス構成が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-104">Click **TCP/IP** in the left pane, to show individual IP address configurations in the details pane.</span></span>  
  
 <span data-ttu-id="0adb0-105">変更を有効にするには、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0adb0-105">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted before the changes take effect.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0adb0-106">オプション</span><span class="sxs-lookup"><span data-stu-id="0adb0-106">Options</span></span>  
 <span data-ttu-id="0adb0-107">**有効**</span><span class="sxs-lookup"><span data-stu-id="0adb0-107">**Enabled**</span></span>  
 <span data-ttu-id="0adb0-108">可能な値は、 **[はい]** と **[いいえ]** です。</span><span class="sxs-lookup"><span data-stu-id="0adb0-108">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="0adb0-109">**[Keep Alive]**</span><span class="sxs-lookup"><span data-stu-id="0adb0-109">**Keep Alive**</span></span>  
 <span data-ttu-id="0adb0-110">接続のリモート側のコンピューターが使用可能かどうかを確認するために、Keep Alive パケットを送信する間隔 (ミリ秒) を指定します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-110">Specify the interval (milliseconds) in which keep-alive packets are transmitted to verify that the computer at the remote end of a connection is still available.</span></span>  
  
 <span data-ttu-id="0adb0-111">**[すべて受信待ち]**</span><span class="sxs-lookup"><span data-stu-id="0adb0-111">**Listen All**</span></span>  
 <span data-ttu-id="0adb0-112">コンピューター上のネットワーク カードに割り当てられているすべての IP アドレスで SQL Server がリッスンするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-112">Specify whether SQL Server will listen on all the IP addresses that are bound to network cards on the computer.</span></span> <span data-ttu-id="0adb0-113">**[いいえ]** に設定した場合は、各 IP アドレスのプロパティ ダイアログ ボックスを使用して、IP アドレスごとに個別の構成を行ってください。</span><span class="sxs-lookup"><span data-stu-id="0adb0-113">If set to **No**, configure each IP address separately using the properties dialog box for each IP address.</span></span> <span data-ttu-id="0adb0-114">**[はい]** に設定した場合は、 **[IPAll]** プロパティ ボックスの設定がすべての IP アドレスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-114">If set to **Yes**, the settings of the **IPAll** properties box will apply to all IP addresses.</span></span> <span data-ttu-id="0adb0-115">既定値は **[はい]** です。</span><span class="sxs-lookup"><span data-stu-id="0adb0-115">Default value is **Yes**.</span></span>  
  
 <span data-ttu-id="0adb0-116">**[遅延なし]**</span><span class="sxs-lookup"><span data-stu-id="0adb0-116">**No Delay**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0adb0-117">では、このプロパティに対する変更は実装されません。</span><span class="sxs-lookup"><span data-stu-id="0adb0-117">does not implement changes to this property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adb0-118">参照</span><span class="sxs-lookup"><span data-stu-id="0adb0-118">See Also</span></span>  
 <span data-ttu-id="0adb0-119">[ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="0adb0-119">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="0adb0-120">TCP/IP を使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="0adb0-120">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
