---
title: MSSQLSERVER_3169 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b13d9c1c17eddb34648bc4a536e2fccf371b99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640985"
---
# <a name="mssqlserver_3169"></a><span data-ttu-id="29173-102">MSSQLSERVER_3169</span><span class="sxs-lookup"><span data-stu-id="29173-102">MSSQLSERVER_3169</span></span>
    
## <a name="details"></a><span data-ttu-id="29173-103">詳細</span><span class="sxs-lookup"><span data-stu-id="29173-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29173-104">製品名</span><span class="sxs-lookup"><span data-stu-id="29173-104">Product Name</span></span>|<span data-ttu-id="29173-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="29173-105">SQL Server</span></span>|  
|<span data-ttu-id="29173-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="29173-106">Event ID</span></span>|<span data-ttu-id="29173-107">3169</span><span class="sxs-lookup"><span data-stu-id="29173-107">3169</span></span>|  
|<span data-ttu-id="29173-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="29173-108">Event Source</span></span>|<span data-ttu-id="29173-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29173-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29173-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="29173-110">Component</span></span>|<span data-ttu-id="29173-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="29173-111">SQLEngine</span></span>|  
|<span data-ttu-id="29173-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="29173-112">Symbolic Name</span></span>|<span data-ttu-id="29173-113">NA</span><span class="sxs-lookup"><span data-stu-id="29173-113">NA</span></span>|  
|<span data-ttu-id="29173-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="29173-114">Message Text</span></span>|<span data-ttu-id="29173-115">データベースはバージョン %ls を実行中のサーバーにバックアップされました。</span><span class="sxs-lookup"><span data-stu-id="29173-115">The database was backed up on a server running version %ls.</span></span> <span data-ttu-id="29173-116">このバージョンは、このサーバー (バージョン %ls を実行) とは互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="29173-116">That version is incompatible with this server, which is running version %ls.</span></span> <span data-ttu-id="29173-117">バックアップをサポートしているサーバーでデータベースを復元するか、またはこのサーバーと互換性のあるバックアップを使用してください。</span><span class="sxs-lookup"><span data-stu-id="29173-117">Either restore the database on a server that supports the backup, or use a backup that is compatible with this server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29173-118">説明</span><span class="sxs-lookup"><span data-stu-id="29173-118">Explanation</span></span>  
 <span data-ttu-id="29173-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部の機能は、データベース ファイルの構造に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="29173-119">Certain features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affect the structure of the database files.</span></span> <span data-ttu-id="29173-120">データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスに復元する場合、ファイル形式が [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の別のバージョンと互換性がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="29173-120">When you restore a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the file format might not be compatible with a different version of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="29173-121">たとえば、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 以降のバージョンで vardecimal ストレージ形式を使用して、それよりも前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でデータベース ファイルを復元しようとすると、このエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="29173-121">For example, this error can be caused by using the vardecimalstorage format in a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then trying to restore the database files in a version earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29173-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="29173-122">User Action</span></span>  
 <span data-ttu-id="29173-123">元のサーバーで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを判断します。</span><span class="sxs-lookup"><span data-stu-id="29173-123">Determine the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on the originating server.</span></span> <span data-ttu-id="29173-124">で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーを右クリックし、[**プロパティ**] をクリックするか、クエリウィンドウを入力し `SELECT @@VERSION` ます。</span><span class="sxs-lookup"><span data-stu-id="29173-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], either right-click the server and then click **Properties** or type `SELECT @@VERSION` in a query window.</span></span> <span data-ttu-id="29173-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の元のバージョンを使用してデータベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="29173-125">Open the database by using the original version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29173-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで、元のデータベースで有効になっている機能を調べます。</span><span class="sxs-lookup"><span data-stu-id="29173-126">Investigate the features that are enabled on the original database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29173-127">データベースの復元先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンで使用できるように、これらの設定を修正します。</span><span class="sxs-lookup"><span data-stu-id="29173-127">Modify these settings to work with the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in which the database will be restored.</span></span>  
  
  
