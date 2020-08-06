---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b63be325273e4df33d837ec1548ed46701323977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715357"
---
# <a name="mssqlserver_17130"></a><span data-ttu-id="6b258-102">MSSQLSERVER_17130</span><span class="sxs-lookup"><span data-stu-id="6b258-102">MSSQLSERVER_17130</span></span>
    
## <a name="details"></a><span data-ttu-id="6b258-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6b258-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b258-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6b258-104">Product Name</span></span>|<span data-ttu-id="6b258-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6b258-105">SQL Server</span></span>|  
|<span data-ttu-id="6b258-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6b258-106">Event ID</span></span>|<span data-ttu-id="6b258-107">17130</span><span class="sxs-lookup"><span data-stu-id="6b258-107">17130</span></span>|  
|<span data-ttu-id="6b258-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6b258-108">Event Source</span></span>|<span data-ttu-id="6b258-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6b258-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6b258-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6b258-110">Component</span></span>|<span data-ttu-id="6b258-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6b258-111">SQLEngine</span></span>|  
|<span data-ttu-id="6b258-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6b258-112">Symbolic Name</span></span>|<span data-ttu-id="6b258-113">INIT_NOLOCKSPACE</span><span class="sxs-lookup"><span data-stu-id="6b258-113">INIT_NOLOCKSPACE</span></span>|  
|<span data-ttu-id="6b258-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6b258-114">Message Text</span></span>|<span data-ttu-id="6b258-115">構成されたロック数に対するメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="6b258-115">Not enough memory for the configured number of locks.</span></span> <span data-ttu-id="6b258-116">より小さいロックのハッシュ テーブルで開始しますが、パフォーマンスに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6b258-116">Attempting to start with a smaller lock hash table, which may impact performance.</span></span> <span data-ttu-id="6b258-117">データベース管理者に連絡して、データベース エンジンのこのインスタンスに割り当てるメモリを増やすように構成してください。</span><span class="sxs-lookup"><span data-stu-id="6b258-117">Contact the database administrator to configure more memory for this instance of the Database Engine.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6b258-118">説明</span><span class="sxs-lookup"><span data-stu-id="6b258-118">Explanation</span></span>  
 <span data-ttu-id="6b258-119">ロック マネージャーのハッシュ テーブルの必要なサイズに対してメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="6b258-119">Not enough memory for the desired lock manager hash table size.</span></span>  <span data-ttu-id="6b258-120">より小さいハッシュ テーブルの割り当てが試行されます。</span><span class="sxs-lookup"><span data-stu-id="6b258-120">An attempt will be made to allocate a smaller hash table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6b258-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6b258-121">User Action</span></span>  
 <span data-ttu-id="6b258-122">サーバーのメモリ構成パラメーター (min/max server memory) を確認し、メモリ負荷を確認します。</span><span class="sxs-lookup"><span data-stu-id="6b258-122">Check server memory configuration parameters (min/max server memory), check for memory pressures.</span></span> <span data-ttu-id="6b258-123">SQL Server へのメモリの割り当てを増やします。</span><span class="sxs-lookup"><span data-stu-id="6b258-123">Provide SQL Server more memory.</span></span>  
  
  
