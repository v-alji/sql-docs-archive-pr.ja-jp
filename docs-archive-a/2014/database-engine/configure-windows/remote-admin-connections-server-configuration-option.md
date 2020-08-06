---
title: remote admin connections サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c17cf278d18444c5b93d4f4b7e0a3da8dbfb671e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644137"
---
# <a name="remote-admin-connections-server-configuration-option"></a><span data-ttu-id="96727-102">remote admin connections サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="96727-102">remote admin connections Server Configuration Option</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="96727-103">には専用管理者接続 (DAC) があります。</span><span class="sxs-lookup"><span data-stu-id="96727-103">provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="96727-104">管理者は、DAC により、実行中のサーバーにアクセスして、診断関数や [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行したり、サーバー上の問題のトラブルシューティングを行ったりすることができます。このことは、サーバーがロックされていたり、異常状態で実行されたりしていて、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 接続に応答していない場合も同じです。</span><span class="sxs-lookup"><span data-stu-id="96727-104">The DAC lets an administrator access a running server to execute diagnostic functions or [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or to troubleshoot problems on the server, even when the server is locked or running in an abnormal state and not responding to a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] connection.</span></span> <span data-ttu-id="96727-105">既定では、DAC はそのサーバー上のクライアントからしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="96727-105">By default, the DAC is only available from a client on the server.</span></span> <span data-ttu-id="96727-106">リモート コンピューター上のクライアント アプリケーションから DAC を使用できるようにするには、sp_configure の remote admin connections オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="96727-106">To enable client applications on remote computers to use the DAC, use the remote admin connections option of sp_configure.</span></span>  
  
 <span data-ttu-id="96727-107">既定では、DAC はループバック IP アドレス (127.0.0.1)、ポート 1434 だけをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="96727-107">By default, the DAC only listens on the loop-back IP address (127.0.0.1), port 1434.</span></span> <span data-ttu-id="96727-108">TCP ポート 1434 を使用できない場合は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の起動時に TCP ポートが動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="96727-108">If TCP port 1434 is not available, a TCP port is dynamically assigned when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] starts up.</span></span> <span data-ttu-id="96727-109">複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがコンピューターにインストールされている場合、TCP ポート番号についてはエラー ログを確認してください。</span><span class="sxs-lookup"><span data-stu-id="96727-109">When more than one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, check the error log for the TCP port number.</span></span>  
  
 <span data-ttu-id="96727-110">次の表は、remote admin connections オプションの使用可能な値の一覧です。</span><span class="sxs-lookup"><span data-stu-id="96727-110">The following table lists the possible values for the remote admin connections option.</span></span>  
  
|<span data-ttu-id="96727-111">値</span><span class="sxs-lookup"><span data-stu-id="96727-111">Value</span></span>|<span data-ttu-id="96727-112">説明</span><span class="sxs-lookup"><span data-stu-id="96727-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="96727-113">0</span><span class="sxs-lookup"><span data-stu-id="96727-113">0</span></span>|<span data-ttu-id="96727-114">ローカル接続のみで DAC を使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="96727-114">Indicates only local connections are allowed by using the DAC.</span></span>|  
|<span data-ttu-id="96727-115">1</span><span class="sxs-lookup"><span data-stu-id="96727-115">1</span></span>|<span data-ttu-id="96727-116">リモート接続で DAC を使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="96727-116">Indicates remote connections are allowed by using the DAC.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96727-117">例</span><span class="sxs-lookup"><span data-stu-id="96727-117">Example</span></span>  
 <span data-ttu-id="96727-118">次の例では、リモート コンピューターから DAC を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="96727-118">The following example enables the DAC from a remote computer.</span></span>  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="96727-119">参照</span><span class="sxs-lookup"><span data-stu-id="96727-119">See Also</span></span>  
 [<span data-ttu-id="96727-120">データベース管理者用の診断接続</span><span class="sxs-lookup"><span data-stu-id="96727-120">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  
