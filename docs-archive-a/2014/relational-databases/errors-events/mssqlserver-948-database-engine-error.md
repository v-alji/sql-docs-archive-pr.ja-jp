---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8461069a3fceb7bdca318b82a522f7f51af83d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639999"
---
# <a name="mssqlserver_948"></a><span data-ttu-id="d4542-102">MSSQLSERVER_948</span><span class="sxs-lookup"><span data-stu-id="d4542-102">MSSQLSERVER_948</span></span>
    
## <a name="details"></a><span data-ttu-id="d4542-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d4542-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d4542-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d4542-104">Product Name</span></span>|<span data-ttu-id="d4542-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d4542-105">SQL Server</span></span>|  
|<span data-ttu-id="d4542-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d4542-106">Event ID</span></span>|<span data-ttu-id="d4542-107">948</span><span class="sxs-lookup"><span data-stu-id="d4542-107">948</span></span>|  
|<span data-ttu-id="d4542-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d4542-108">Event Source</span></span>|<span data-ttu-id="d4542-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d4542-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d4542-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d4542-110">Component</span></span>|<span data-ttu-id="d4542-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d4542-111">SQLEngine</span></span>|  
|<span data-ttu-id="d4542-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d4542-112">Symbolic Name</span></span>|<span data-ttu-id="d4542-113">NA</span><span class="sxs-lookup"><span data-stu-id="d4542-113">NA</span></span>|  
|<span data-ttu-id="d4542-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d4542-114">Message Text</span></span>|<span data-ttu-id="d4542-115">データベース '%.\*ls' のバージョンは %d なので、開けません。</span><span class="sxs-lookup"><span data-stu-id="d4542-115">The database '%.\*ls' cannot be opened because it is version %d.</span></span> <span data-ttu-id="d4542-116">このサーバーではバージョン %d 以前がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d4542-116">This server supports version %d and earlier.</span></span> <span data-ttu-id="d4542-117">このダウングレード パスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d4542-117">A downgrade path is not supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d4542-118">説明</span><span class="sxs-lookup"><span data-stu-id="d4542-118">Explanation</span></span>  
 <span data-ttu-id="d4542-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部の機能は、データベース ファイルの構造に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="d4542-119">Certain features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affect the structure of the database files.</span></span> <span data-ttu-id="d4542-120">データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスにアタッチする場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のバージョンが違っていると、ファイル形式の互換性がない場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4542-120">When you attach a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the file format might not be compatible with a different version of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="d4542-121">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack 2 以降のバージョンで vardecimal ストレージ形式を使用して、それよりも前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] でデータベース ファイルをアタッチしようとすると、このエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d4542-121">For example, this error can be caused by using the vardecimal storage format in a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then trying to attach the database files in a version earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d4542-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d4542-122">User Action</span></span>  
 <span data-ttu-id="d4542-123">元のサーバーで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを判断します。</span><span class="sxs-lookup"><span data-stu-id="d4542-123">Determine the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on the originating server.</span></span> <span data-ttu-id="d4542-124">で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーを右クリックし、[**プロパティ**] をクリックするか、クエリウィンドウを入力し `SELECT @@VERSION` ます。</span><span class="sxs-lookup"><span data-stu-id="d4542-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], either right-click the server and then click **Properties** or type `SELECT @@VERSION` in a query window.</span></span> <span data-ttu-id="d4542-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の元のバージョンを使用してデータベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="d4542-125">Open the database by using the original version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d4542-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで、元のデータベースで有効になっている機能を調べます。</span><span class="sxs-lookup"><span data-stu-id="d4542-126">Investigate the features that are enabled on the original database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d4542-127">データベースをアタッチする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンで使用できるように、これらの設定を修正します。</span><span class="sxs-lookup"><span data-stu-id="d4542-127">Modify these settings to work with the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in which the database will be attached.</span></span>  
  
  
