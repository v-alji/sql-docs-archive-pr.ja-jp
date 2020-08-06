---
title: MSSQLSERVER_-2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d39b4a11387a60056bba3f87adffcb2653b60f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716369"
---
# <a name="mssqlserver_-2"></a><span data-ttu-id="ee9bb-102">MSSQLSERVER_-2</span><span class="sxs-lookup"><span data-stu-id="ee9bb-102">MSSQLSERVER_-2</span></span>
    
## <a name="details"></a><span data-ttu-id="ee9bb-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ee9bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee9bb-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ee9bb-104">Product Name</span></span>|<span data-ttu-id="ee9bb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ee9bb-105">SQL Server</span></span>|  
|<span data-ttu-id="ee9bb-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ee9bb-106">Event ID</span></span>|<span data-ttu-id="ee9bb-107">-2</span><span class="sxs-lookup"><span data-stu-id="ee9bb-107">-2</span></span>|  
|<span data-ttu-id="ee9bb-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ee9bb-108">Event Source</span></span>|<span data-ttu-id="ee9bb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ee9bb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ee9bb-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ee9bb-110">Component</span></span>|<span data-ttu-id="ee9bb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ee9bb-111">SQLEngine</span></span>|  
|<span data-ttu-id="ee9bb-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ee9bb-112">Symbolic Name</span></span>||  
|<span data-ttu-id="ee9bb-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ee9bb-113">Message Text</span></span>|<span data-ttu-id="ee9bb-114">タイムアウトに達しました。</span><span class="sxs-lookup"><span data-stu-id="ee9bb-114">Timeout expired.</span></span>  <span data-ttu-id="ee9bb-115">処理が完了する前にタイムアウト期間が経過したか、サーバーが応答していません。</span><span class="sxs-lookup"><span data-stu-id="ee9bb-115">The timeout period elapsed prior to completion of the operation or the server is not responding.</span></span> <span data-ttu-id="ee9bb-116">(Microsoft SQL Server、エラー: -2)。</span><span class="sxs-lookup"><span data-stu-id="ee9bb-116">(Microsoft SQL Server, Error: -2)</span></span>|   
  
## <a name="explanation"></a><span data-ttu-id="ee9bb-117">説明</span><span class="sxs-lookup"><span data-stu-id="ee9bb-117">Explanation</span></span>  
 <span data-ttu-id="ee9bb-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="ee9bb-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="ee9bb-119">このエラーは、サーバー上のファイアウォールで接続が拒否されたために発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee9bb-119">This error could occur because the firewall on the server has refused the connection.</span></span> 
  
## <a name="user-action"></a><span data-ttu-id="ee9bb-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ee9bb-120">User Action</span></span>  
 <span data-ttu-id="ee9bb-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサーバー インスタンスで、接続を許可するようにファイアウォールを構成していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee9bb-121">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee9bb-122">参照</span><span class="sxs-lookup"><span data-stu-id="ee9bb-122">See Also</span></span>  
 <span data-ttu-id="ee9bb-123">[SQL Server アクセスを許可するように Windows ファイアウォールを構成する](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="ee9bb-123">[Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span></span>  
 <span data-ttu-id="ee9bb-124">[データベースエンジンアクセスできるように Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="ee9bb-124">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="ee9bb-125">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="ee9bb-125">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="ee9bb-126">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="ee9bb-126">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="ee9bb-127">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="ee9bb-127">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="ee9bb-128">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="ee9bb-128">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="ee9bb-129">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="ee9bb-129">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
