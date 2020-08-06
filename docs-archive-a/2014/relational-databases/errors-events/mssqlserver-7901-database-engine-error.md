---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fae6e55cbe7170f795aff85400da2c5cdaef780a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640974"
---
# <a name="mssqlserver_7901"></a><span data-ttu-id="c3291-102">MSSQLSERVER_7901</span><span class="sxs-lookup"><span data-stu-id="c3291-102">MSSQLSERVER_7901</span></span>
    
## <a name="details"></a><span data-ttu-id="c3291-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c3291-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3291-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c3291-104">Product Name</span></span>|<span data-ttu-id="c3291-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c3291-105">SQL Server</span></span>|  
|<span data-ttu-id="c3291-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c3291-106">Event ID</span></span>|<span data-ttu-id="c3291-107">7901</span><span class="sxs-lookup"><span data-stu-id="c3291-107">7901</span></span>|  
|<span data-ttu-id="c3291-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c3291-108">Event Source</span></span>|<span data-ttu-id="c3291-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c3291-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c3291-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c3291-110">Component</span></span>|<span data-ttu-id="c3291-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c3291-111">SQLEngine</span></span>|  
|<span data-ttu-id="c3291-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c3291-112">Symbolic Name</span></span>|<span data-ttu-id="c3291-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span><span class="sxs-lookup"><span data-stu-id="c3291-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span></span>|  
|<span data-ttu-id="c3291-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c3291-114">Message Text</span></span>|<span data-ttu-id="c3291-115">修復ステートメントは処理されませんでした。</span><span class="sxs-lookup"><span data-stu-id="c3291-115">The repair statement was not processed.</span></span> <span data-ttu-id="c3291-116">データベースが緊急モードのときは、このレベルの修復はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c3291-116">This level of repair is not supported when the database is in emergency mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c3291-117">説明</span><span class="sxs-lookup"><span data-stu-id="c3291-117">Explanation</span></span>  
 <span data-ttu-id="c3291-118">データベースが緊急モードであり、REPAIR_ALLOW_DATA_LOSS 以外の修復レベルが指定されました。</span><span class="sxs-lookup"><span data-stu-id="c3291-118">The database is in emergency mode and a repair level other than REPAIR_ALLOW_DATA_LOSS has been specified.</span></span> <span data-ttu-id="c3291-119">REPAIR_ALLOW_DATA_LOSS が指定されていない場合に、緊急モードで修復を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="c3291-119">Repairs cannot be made in emergency mode unless REPAIR_ALLOW_DATA_LOSS is specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c3291-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c3291-120">User Action</span></span>  
 <span data-ttu-id="c3291-121">REPAIR_ALLOW_DATA_LOSS オプションを指定して、コマンドを再実行します。</span><span class="sxs-lookup"><span data-stu-id="c3291-121">Rerun the command and specify the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
  
