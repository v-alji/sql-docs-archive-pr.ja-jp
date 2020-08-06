---
title: MSSQLSERVER_7308 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9978f35ebe41eeda1470220772f87e83ab1ad942
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640979"
---
# <a name="mssqlserver_7308"></a><span data-ttu-id="f293f-102">MSSQLSERVER_7308</span><span class="sxs-lookup"><span data-stu-id="f293f-102">MSSQLSERVER_7308</span></span>
    
## <a name="details"></a><span data-ttu-id="f293f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f293f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f293f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f293f-104">Product Name</span></span>|<span data-ttu-id="f293f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f293f-105">SQL Server</span></span>|  
|<span data-ttu-id="f293f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f293f-106">Event ID</span></span>|<span data-ttu-id="f293f-107">7308</span><span class="sxs-lookup"><span data-stu-id="f293f-107">7308</span></span>|  
|<span data-ttu-id="f293f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f293f-108">Event Source</span></span>|<span data-ttu-id="f293f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f293f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f293f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f293f-110">Component</span></span>|<span data-ttu-id="f293f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f293f-111">SQLEngine</span></span>|  
|<span data-ttu-id="f293f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f293f-112">Symbolic Name</span></span>|<span data-ttu-id="f293f-113">RMT_STA_DISABLED</span><span class="sxs-lookup"><span data-stu-id="f293f-113">RMT_STA_DISABLED</span></span>|  
|<span data-ttu-id="f293f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f293f-114">Message Text</span></span>|<span data-ttu-id="f293f-115">OLE DB プロバイダー '%ls' を分散クエリに使用することはできません。このプロバイダーは、シングル スレッド アパートメント モードで実行するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="f293f-115">OLE DB provider '%ls' cannot be used for distributed queries because the provider is configured to run in single-threaded apartment mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f293f-116">説明</span><span class="sxs-lookup"><span data-stu-id="f293f-116">Explanation</span></span>  
 <span data-ttu-id="f293f-117">シングル スレッド アパートメント (STA) モードで実行するように構成されている OLE DB プロバイダーを使用しました。</span><span class="sxs-lookup"><span data-stu-id="f293f-117">You have used an OLE DB provider that is configured to run in single-threaded apartment (STA) mode.</span></span> <span data-ttu-id="f293f-118">シングル スレッド アパートメント (STA) モードで実行する OLE DB プロバイダーを分散クエリに使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f293f-118">OLE DB providers that run in single-threaded apartment (STA) mode cannot be used for distributed queries.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f293f-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f293f-119">User Action</span></span>  
 <span data-ttu-id="f293f-120">このエラーを解決するには、プロバイダーをマルチスレッド アパートメント (MTA) モードで実行するように構成します。</span><span class="sxs-lookup"><span data-stu-id="f293f-120">To resolve this error, configure the provider to run in multithreaded apartment (MTA) mode.</span></span> <span data-ttu-id="f293f-121">プロバイダーが MTA をサポートしておらず、MTA をサポートするバージョンにアップグレードできない場合は、プロバイダーをプロセス外で実行するように構成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f293f-121">If the provider does not support MTA, and the provider cannot be upgraded to a version that supports MTA, consider configuring the provider to run out-of-process.</span></span> <span data-ttu-id="f293f-122">プロバイダーが MTA またはプロセス外での実行をサポートしているかどうかは、プロバイダーの製造元に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="f293f-122">The provider vendor should be able to tell you if the provider supports MTA or running out-of-process.</span></span>  
  
  
