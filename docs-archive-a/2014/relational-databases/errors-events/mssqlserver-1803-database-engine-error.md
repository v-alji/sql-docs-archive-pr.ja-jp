---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11302f882846c49c6e9998608967e7042ac9860c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642116"
---
# <a name="mssqlserver_1803"></a><span data-ttu-id="b5677-102">MSSQLSERVER_1803</span><span class="sxs-lookup"><span data-stu-id="b5677-102">MSSQLSERVER_1803</span></span>
    
## <a name="details"></a><span data-ttu-id="b5677-103">詳細</span><span class="sxs-lookup"><span data-stu-id="b5677-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5677-104">製品名</span><span class="sxs-lookup"><span data-stu-id="b5677-104">Product Name</span></span>|<span data-ttu-id="b5677-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b5677-105">SQL Server</span></span>|  
|<span data-ttu-id="b5677-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="b5677-106">Event ID</span></span>|<span data-ttu-id="b5677-107">1803</span><span class="sxs-lookup"><span data-stu-id="b5677-107">1803</span></span>|  
|<span data-ttu-id="b5677-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="b5677-108">Event Source</span></span>|<span data-ttu-id="b5677-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b5677-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b5677-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b5677-110">Component</span></span>|<span data-ttu-id="b5677-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b5677-111">SQLEngine</span></span>|  
|<span data-ttu-id="b5677-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="b5677-112">Symbolic Name</span></span>|<span data-ttu-id="b5677-113">NO_SPACE</span><span class="sxs-lookup"><span data-stu-id="b5677-113">NO_SPACE</span></span>|  
|<span data-ttu-id="b5677-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="b5677-114">Message Text</span></span>|<span data-ttu-id="b5677-115">CREATE DATABASE が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="b5677-115">CREATE DATABASE failed.</span></span> <span data-ttu-id="b5677-116">プライマリ ファイルは、model データベースのコピーを格納するために少なくとも %d MB にしてください。</span><span class="sxs-lookup"><span data-stu-id="b5677-116">Primary file must be at least %d MB to accommodate a copy of the model database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b5677-117">説明</span><span class="sxs-lookup"><span data-stu-id="b5677-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b5677-118">では、model データベースのコピーを作成することによって、データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5677-118">creates a database by making a copy of the model database.</span></span> <span data-ttu-id="b5677-119">その後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってコピーの名前が変更され、新しいデータベースが要求されたサイズに拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b5677-119">Then [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renames the copy, and enlarges the new database to the requested size.</span></span> <span data-ttu-id="b5677-120">この場合は、ユーザーが model データベースよりも小さいデータベースの作成を試みました。</span><span class="sxs-lookup"><span data-stu-id="b5677-120">In this case, the user tried to create a database smaller than the model database.</span></span> <span data-ttu-id="b5677-121">この操作は、model データベースのコピーがプライマリ データ ファイルに収まらなかったため失敗しました。これは、プライマリ データ ファイルが model データベースより小さいことが原因です。</span><span class="sxs-lookup"><span data-stu-id="b5677-121">The operation failed because the copy of the model database could not fit on the primary data file, because the file was smaller than the model database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b5677-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="b5677-122">User Action</span></span>  
 <span data-ttu-id="b5677-123">データベース ファイルのサイズを大きくして、データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5677-123">Create the database by using a larger database file size.</span></span> <span data-ttu-id="b5677-124">その後で、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または DBCC SHRINKDATABASE ステートメントを使用して、必要に応じてデータベースを圧縮します。</span><span class="sxs-lookup"><span data-stu-id="b5677-124">Then shrink the database if you want by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or the DBCC SHRINKDATABASE statement.</span></span>  
  
  
