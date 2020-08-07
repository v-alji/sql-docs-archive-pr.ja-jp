---
title: MSSQLSERVER_9001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e61894d0d071fbdb36dcfb77895c46c61d0bbd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719952"
---
# <a name="mssqlserver_9001"></a><span data-ttu-id="81d7a-102">MSSQLSERVER_9001</span><span class="sxs-lookup"><span data-stu-id="81d7a-102">MSSQLSERVER_9001</span></span>
    
## <a name="details"></a><span data-ttu-id="81d7a-103">詳細</span><span class="sxs-lookup"><span data-stu-id="81d7a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81d7a-104">製品名</span><span class="sxs-lookup"><span data-stu-id="81d7a-104">Product Name</span></span>|<span data-ttu-id="81d7a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="81d7a-105">SQL Server</span></span>|  
|<span data-ttu-id="81d7a-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="81d7a-106">Event ID</span></span>|<span data-ttu-id="81d7a-107">9001</span><span class="sxs-lookup"><span data-stu-id="81d7a-107">9001</span></span>|  
|<span data-ttu-id="81d7a-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="81d7a-108">Event Source</span></span>|<span data-ttu-id="81d7a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="81d7a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="81d7a-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="81d7a-110">Component</span></span>|<span data-ttu-id="81d7a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="81d7a-111">SQLEngine</span></span>|  
|<span data-ttu-id="81d7a-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="81d7a-112">Symbolic Name</span></span>|<span data-ttu-id="81d7a-113">LOG_NOT_AVAIL</span><span class="sxs-lookup"><span data-stu-id="81d7a-113">LOG_NOT_AVAIL</span></span>|  
|<span data-ttu-id="81d7a-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="81d7a-114">Message Text</span></span>|<span data-ttu-id="81d7a-115">データベース '%.\*ls' のログは使用できません。</span><span class="sxs-lookup"><span data-stu-id="81d7a-115">The log for database '%.\*ls' is not available.</span></span> <span data-ttu-id="81d7a-116">イベント ログで、関連するエラー メッセージを確認してください。</span><span class="sxs-lookup"><span data-stu-id="81d7a-116">Check the event log for related error messages.</span></span> <span data-ttu-id="81d7a-117">エラーがある場合は解決し、データベースを再起動してください。</span><span class="sxs-lookup"><span data-stu-id="81d7a-117">Resolve any errors and restart the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="81d7a-118">説明</span><span class="sxs-lookup"><span data-stu-id="81d7a-118">Explanation</span></span>  
 <span data-ttu-id="81d7a-119">データベース ログがオフラインになりました。</span><span class="sxs-lookup"><span data-stu-id="81d7a-119">The database log was taken offline.</span></span> <span data-ttu-id="81d7a-120">通常、これは、データベースの再起動を必要とする重大なエラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="81d7a-120">Usually this signifies a catastrophic failure that requires the database to restart.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="81d7a-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="81d7a-121">User Action</span></span>  
 <span data-ttu-id="81d7a-122">他のエラーを診断し、まだ自動的に再起動されていない場合は SQL Server インスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="81d7a-122">Diagnose other errors and restart the instance of SQL Server if it has not already restarted itself.</span></span>  
  
  
