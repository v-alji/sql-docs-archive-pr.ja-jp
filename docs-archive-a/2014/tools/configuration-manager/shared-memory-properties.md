---
title: 共有メモリのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6275215afdb6de3aa134dbffe74aa22b9e7b6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644728"
---
# <a name="shared-memory-properties"></a><span data-ttu-id="b1288-102">[共有メモリのプロパティ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="b1288-102">Shared Memory Properties</span></span>
  <span data-ttu-id="b1288-103">**[共有メモリのプロパティ]** ダイアログ ボックスの **[プロトコル]** ページは、共有メモリ プロトコルを有効または無効にするために使用します。</span><span class="sxs-lookup"><span data-stu-id="b1288-103">Use the **Protocol**page on the **Shared Memory Properties** dialog box to enable or disable the shared memory protocol.</span></span> <span data-ttu-id="b1288-104">共有メモリは、使用できる最も単純なプロトコルであり、構成可能な設定はありません。</span><span class="sxs-lookup"><span data-stu-id="b1288-104">Shared memory is the simplest protocol to use and has no configurable settings.</span></span> <span data-ttu-id="b1288-105">共有メモリ プロトコルを使用するクライアントは、同じコンピューター上で実行されている [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにしか接続できないため、ほとんどのデータベース操作にとって実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="b1288-105">Because clients using the shared memory protocol can only connect to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance running on the same computer, it is not useful for most database activity.</span></span> <span data-ttu-id="b1288-106">共有メモリ プロトコルは、他のプロトコルが正しく構成されていない可能性がある場合に、トラブルシューティングを行うために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1288-106">Use the shared memory protocol for troubleshooting when you suspect the other protocols are configured incorrectly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b1288-107">を再起動しないと、このプロトコルを有効または無効にできません。</span><span class="sxs-lookup"><span data-stu-id="b1288-107">must be restarted to enable or disable the protocol.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b1288-108">オプション</span><span class="sxs-lookup"><span data-stu-id="b1288-108">Options</span></span>  
 <span data-ttu-id="b1288-109">**有効**</span><span class="sxs-lookup"><span data-stu-id="b1288-109">**Enabled**</span></span>  
 <span data-ttu-id="b1288-110">可能な値は、 **[はい]** と **[いいえ]** です。</span><span class="sxs-lookup"><span data-stu-id="b1288-110">Possible values are **Yes** and **No**.</span></span> <span data-ttu-id="b1288-111">既定では、共有メモリ プロトコルは有効になっています。</span><span class="sxs-lookup"><span data-stu-id="b1288-111">The shared memory protocol is enabled by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1288-112">参照</span><span class="sxs-lookup"><span data-stu-id="b1288-112">See Also</span></span>  
 <span data-ttu-id="b1288-113">[ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="b1288-113">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="b1288-114">共有メモリ プロトコルを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="b1288-114">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
