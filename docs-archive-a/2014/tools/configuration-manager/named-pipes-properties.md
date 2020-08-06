---
title: 名前付きパイプのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80790c1cb8830a0fd132721f375a70d2574421b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640299"
---
# <a name="named-pipes-properties"></a><span data-ttu-id="226cb-102">[名前付きパイプのプロパティ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="226cb-102">Named Pipes Properties</span></span>
  <span data-ttu-id="226cb-103">**[名前付きパイプのプロパティ]** ダイアログ ボックスの **[プロトコル]** ページでは、名前付きパイプ プロトコルを使用している場合に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプの表示や変更を行います。</span><span class="sxs-lookup"><span data-stu-id="226cb-103">Use the **Protocol**page on the **Named Pipes Properties** dialog box to view or change the named pipe that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens to, when using the Named Pipes protocol.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="226cb-104">を再起動する必要があるのは、プロトコルを有効または無効にする場合、または名前付きパイプを変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="226cb-104">must be restarted to enable or disable the protocol, or change the named pipe.</span></span>  
  
## <a name="options"></a><span data-ttu-id="226cb-105">オプション</span><span class="sxs-lookup"><span data-stu-id="226cb-105">Options</span></span>  
 <span data-ttu-id="226cb-106">**有効**</span><span class="sxs-lookup"><span data-stu-id="226cb-106">**Enabled**</span></span>  
 <span data-ttu-id="226cb-107">可能な値は、 **[はい]** と **[いいえ]** です。</span><span class="sxs-lookup"><span data-stu-id="226cb-107">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="226cb-108">**[パイプ名]**</span><span class="sxs-lookup"><span data-stu-id="226cb-108">**Pipe Name**</span></span>  
 <span data-ttu-id="226cb-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプを指定します。</span><span class="sxs-lookup"><span data-stu-id="226cb-109">Specifies the named pipe on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens.</span></span> <span data-ttu-id="226cb-110">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定のインスタンスの場合は `\\.\pipe\sql\query` と、名前付きインスタンスの場合は `\\.\pipe\MSSQL$<instancename>\sql\query` でリッスンします。</span><span class="sxs-lookup"><span data-stu-id="226cb-110">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query` for the default instance and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="226cb-111">このフィールドには最大 2,047 文字まで入力できます。</span><span class="sxs-lookup"><span data-stu-id="226cb-111">This field is limited to 2047 characters.</span></span>  
  
## <a name="creating-an-alternate-named-pipe"></a><span data-ttu-id="226cb-112">代替名前付きパイプの作成</span><span class="sxs-lookup"><span data-stu-id="226cb-112">Creating an Alternate Named Pipe</span></span>  
 <span data-ttu-id="226cb-113">名前付きパイプを変更するには、新しいパイプ名を **[パイプ名]** ボックスに入力し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="226cb-113">To change the named pipe, type the new pipe name in the **Pipe Name** box and then stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="226cb-114">**sql\query** は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が使用する名前付きパイプとしてよく知られているため、パイプを変更することによって、悪意のあるプログラムによる攻撃の危険性を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="226cb-114">Since **sql\query** is well known as the named pipe used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], changing the pipe can help reduce the risk of attack by malicious programs.</span></span>  
  
### <a name="example"></a><span data-ttu-id="226cb-115">例</span><span class="sxs-lookup"><span data-stu-id="226cb-115">Example</span></span>  
 <span data-ttu-id="226cb-116">**\\\\unit\app** パイプでリッスンするには、 **.\pipe\unit\app** と入力します。</span><span class="sxs-lookup"><span data-stu-id="226cb-116">Type **\\\\.\pipe\unit\app** to listen on the **unit\app** pipe.</span></span>  
  
 <span data-ttu-id="226cb-117">**\\\\acct** パイプでリッスンするには、 **.\pipe\acct** と入力します。</span><span class="sxs-lookup"><span data-stu-id="226cb-117">Type **\\\\.\pipe\acct** to listen on the **acct** pipe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226cb-118">参照</span><span class="sxs-lookup"><span data-stu-id="226cb-118">See Also</span></span>  
 <span data-ttu-id="226cb-119">[サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="226cb-119">[Enable or Disable a Server Network Protocol](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 <span data-ttu-id="226cb-120">[ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="226cb-120">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="226cb-121">名前付きパイプを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="226cb-121">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
