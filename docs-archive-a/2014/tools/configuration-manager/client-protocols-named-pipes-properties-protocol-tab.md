---
title: クライアント プロトコル - [名前付きパイプのプロパティ] ダイアログ ボックス ([プロトコル] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: stevestein
ms.author: sstein
ms.openlocfilehash: 169b6d98212c724b8d6c43615ae2fa7eba9cfc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712678"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a><span data-ttu-id="60014-102">クライアント プロトコル - [名前付きパイプのプロパティ] ダイアログ ボックス ([プロトコル] タブ)</span><span class="sxs-lookup"><span data-stu-id="60014-102">Client Protocols - Named Pipes Properties (Protocol Tab)</span></span>
  <span data-ttu-id="60014-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、 **[名前付きパイプのプロパティ]** ダイアログ ボックスの **[プロトコル]** タブを使用して、既定のパイプに関する説明の表示や変更を行います。</span><span class="sxs-lookup"><span data-stu-id="60014-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager use the **Protocol** tab on the **Named Pipes Properties** dialog box to view or modify the description of default pipe.</span></span> <span data-ttu-id="60014-104">別のパイプに接続するには、そのパイプを **[既定のパイプ]** ボックスに入力してください。</span><span class="sxs-lookup"><span data-stu-id="60014-104">To connect to a different pipe, type the pipe in the **Default Pipe** box.</span></span> <span data-ttu-id="60014-105">接続文字列の詳細については、「 [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60014-105">For more information about connection strings, see [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="60014-106">オプション</span><span class="sxs-lookup"><span data-stu-id="60014-106">Options</span></span>  
 <span data-ttu-id="60014-107">**[既定のパイプ]**</span><span class="sxs-lookup"><span data-stu-id="60014-107">**Default Pipe**</span></span>  
 <span data-ttu-id="60014-108">名前付きパイプ Net-Library が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスに接続するために使用する既定のパイプを指定します。</span><span class="sxs-lookup"><span data-stu-id="60014-108">Specifies the default pipe the Named Pipes Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="60014-109">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は `\\.\pipe\sql\query`</span><span class="sxs-lookup"><span data-stu-id="60014-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query`</span></span>  
  
 <span data-ttu-id="60014-110">既定のパイプに接続するには、 `sql\query`</span><span class="sxs-lookup"><span data-stu-id="60014-110">To connect to the default pipe, enter `sql\query`</span></span>  
  
 <span data-ttu-id="60014-111">**有効**</span><span class="sxs-lookup"><span data-stu-id="60014-111">**Enabled**</span></span>  
 <span data-ttu-id="60014-112">可能な値は、 **[はい]** と **[いいえ]** です。</span><span class="sxs-lookup"><span data-stu-id="60014-112">Possible values are **Yes** and **No**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60014-113">参照</span><span class="sxs-lookup"><span data-stu-id="60014-113">See Also</span></span>  
 [<span data-ttu-id="60014-114">ネットワーク プロトコルの選択</span><span class="sxs-lookup"><span data-stu-id="60014-114">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
