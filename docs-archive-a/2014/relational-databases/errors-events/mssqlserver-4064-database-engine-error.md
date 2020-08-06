---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 201098aadeb6bd091f0312532138f692ae8079b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644475"
---
# <a name="mssqlserver_4064"></a><span data-ttu-id="4f7c1-102">MSSQLSERVER_4064</span><span class="sxs-lookup"><span data-stu-id="4f7c1-102">MSSQLSERVER_4064</span></span>
    
## <a name="details"></a><span data-ttu-id="4f7c1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4f7c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f7c1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4f7c1-104">Product Name</span></span>|<span data-ttu-id="4f7c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4f7c1-105">SQL Server</span></span>|  
|<span data-ttu-id="4f7c1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4f7c1-106">Event ID</span></span>|<span data-ttu-id="4f7c1-107">4064</span><span class="sxs-lookup"><span data-stu-id="4f7c1-107">4064</span></span>|  
|<span data-ttu-id="4f7c1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4f7c1-108">Event Source</span></span>|<span data-ttu-id="4f7c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4f7c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4f7c1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4f7c1-110">Component</span></span>|<span data-ttu-id="4f7c1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4f7c1-111">SQLEngine</span></span>|  
|<span data-ttu-id="4f7c1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4f7c1-112">Symbolic Name</span></span>|<span data-ttu-id="4f7c1-113">DB_UFAIL_FATAL</span><span class="sxs-lookup"><span data-stu-id="4f7c1-113">DB_UFAIL_FATAL</span></span>|  
|<span data-ttu-id="4f7c1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4f7c1-114">Message Text</span></span>|<span data-ttu-id="4f7c1-115">ユーザーの既定データベースを開けません。</span><span class="sxs-lookup"><span data-stu-id="4f7c1-115">Cannot open user default database.</span></span> <span data-ttu-id="4f7c1-116">ログインできませんでした。</span><span class="sxs-lookup"><span data-stu-id="4f7c1-116">Login failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4f7c1-117">説明</span><span class="sxs-lookup"><span data-stu-id="4f7c1-117">Explanation</span></span>  
 <span data-ttu-id="4f7c1-118">SQL Server ログインの既定のデータベースに問題があるため接続できませんでした。</span><span class="sxs-lookup"><span data-stu-id="4f7c1-118">The SQL Server login was unable to connect because of a problem with its default database.</span></span> <span data-ttu-id="4f7c1-119">データベース自体が無効であるか、ログインにデータベースでの CONNECT 権限がありません。</span><span class="sxs-lookup"><span data-stu-id="4f7c1-119">Either the database itself is invalid or the login lacks CONNECT permission on the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4f7c1-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4f7c1-120">User Action</span></span>  
 <span data-ttu-id="4f7c1-121">ALTER LOGIN を使用して、ログインの既定のデータベースを変更します。</span><span class="sxs-lookup"><span data-stu-id="4f7c1-121">Use ALTER LOGIN to change the login's default database.</span></span> <span data-ttu-id="4f7c1-122">CONNECT 権限をログインに許可します。</span><span class="sxs-lookup"><span data-stu-id="4f7c1-122">Grant CONNECT permission to the login.</span></span>  
  
  
