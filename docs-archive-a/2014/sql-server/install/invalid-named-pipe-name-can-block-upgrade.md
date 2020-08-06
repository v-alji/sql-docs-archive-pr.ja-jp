---
title: 無効な名前付きパイプ名を使用してアップグレードをブロックすることができます |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bacfd3d097d7cccb0a5780328c4db95dc5afc733
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740710"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a><span data-ttu-id="55b80-102">無効な名前付きパイプ名によってアップグレードがブロックされる</span><span class="sxs-lookup"><span data-stu-id="55b80-102">Invalid named pipe name can block upgrade</span></span>
  <span data-ttu-id="55b80-103">アップグレードは、名前付きパイプのプロトコルの構成が正しくない場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="55b80-103">Upgrade fails if the named pipes protocol is incorrectly configured.</span></span>  
  
## <a name="component"></a><span data-ttu-id="55b80-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="55b80-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="55b80-105">説明</span><span class="sxs-lookup"><span data-stu-id="55b80-105">Description</span></span>  
 <span data-ttu-id="55b80-106">アップグレード中、セットアッププログラムは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 共有メモリサポート (ローカル接続のみを受け入れる名前付きパイプ) を使用してインスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="55b80-106">During upgrade, the Setup program starts the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] instance with shared memory support, a named pipe that only accepts local connections.</span></span> <span data-ttu-id="55b80-107">サーバーで指定されているパイプ名が空白でない場合は、文字列 "て .\pipe" で始まる必要があり \\ \\ \\ ます。</span><span class="sxs-lookup"><span data-stu-id="55b80-107">If the pipe name specified on the server is not blank, it must begin with the string "\\\\.\pipe\\" to be valid.</span></span> <span data-ttu-id="55b80-108">パイプ名が有効でない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が起動せず、セットアップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="55b80-108">If the pipe name is not valid, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will not start, and setup will fail.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="55b80-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="55b80-109">Corrective Action</span></span>  
 <span data-ttu-id="55b80-110">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワークユーティリティ\*\*を使用して有効なパイプ名を指定してから、セットアップを実行してください。</span><span class="sxs-lookup"><span data-stu-id="55b80-110">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility** to supply a valid pipe name, and then run Setup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b80-111">参照</span><span class="sxs-lookup"><span data-stu-id="55b80-111">See Also</span></span>  
 <span data-ttu-id="55b80-112">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="55b80-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="55b80-113">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="55b80-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
