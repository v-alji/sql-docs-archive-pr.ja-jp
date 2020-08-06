---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d6d065d4a0e841da3b5ecb84f902df17dcfd60c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639996"
---
# <a name="mssqlserver_9790"></a><span data-ttu-id="c6a7f-102">MSSQLSERVER_9790</span><span class="sxs-lookup"><span data-stu-id="c6a7f-102">MSSQLSERVER_9790</span></span>
    
## <a name="details"></a><span data-ttu-id="c6a7f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c6a7f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6a7f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c6a7f-104">Product Name</span></span>|<span data-ttu-id="c6a7f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c6a7f-105">SQL Server</span></span>|  
|<span data-ttu-id="c6a7f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c6a7f-106">Event ID</span></span>|<span data-ttu-id="c6a7f-107">9790</span><span class="sxs-lookup"><span data-stu-id="c6a7f-107">9790</span></span>|  
|<span data-ttu-id="c6a7f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c6a7f-108">Event Source</span></span>|<span data-ttu-id="c6a7f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c6a7f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c6a7f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c6a7f-110">Component</span></span>|<span data-ttu-id="c6a7f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c6a7f-111">SQLEngine</span></span>|  
|<span data-ttu-id="c6a7f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c6a7f-112">Symbolic Name</span></span>|<span data-ttu-id="c6a7f-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span><span class="sxs-lookup"><span data-stu-id="c6a7f-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span></span>|  
|<span data-ttu-id="c6a7f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c6a7f-114">Message Text</span></span>|<span data-ttu-id="c6a7f-115">着信メッセージをルーティングできません。</span><span class="sxs-lookup"><span data-stu-id="c6a7f-115">Unable to route the incoming message.</span></span> <span data-ttu-id="c6a7f-116">ルーティング情報を保持するシステム データベース MSDB がシングル ユーザー モードです。</span><span class="sxs-lookup"><span data-stu-id="c6a7f-116">The system database MSDB containing routing information is in SINGLE USER mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6a7f-117">説明</span><span class="sxs-lookup"><span data-stu-id="c6a7f-117">Explanation</span></span>  
 <span data-ttu-id="c6a7f-118">MSDB データベースがシングル ユーザー モードであったため、外部から受信したメッセージを分類しようとしたときにエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c6a7f-118">An error occurred while trying to classify a message received off the wire because the MSDB database was in Single User mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6a7f-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c6a7f-119">User Action</span></span>  
 <span data-ttu-id="c6a7f-120">ALTER DATABASE コマンドを使用して、MSDB をマルチ ユーザー モードに変更します。</span><span class="sxs-lookup"><span data-stu-id="c6a7f-120">Change MSDB to be in MULTI USER mode with the ALTER DATABASE command.</span></span>  
  
  
