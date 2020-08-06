---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c152a542550d7b81af880545f526037baeb4644e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718182"
---
# <a name="mssqlserver_21889"></a><span data-ttu-id="a0031-102">MSSQLSERVER_21889</span><span class="sxs-lookup"><span data-stu-id="a0031-102">MSSQLSERVER_21889</span></span>
    
## <a name="details"></a><span data-ttu-id="a0031-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a0031-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0031-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a0031-104">Product Name</span></span>|<span data-ttu-id="a0031-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a0031-105">SQL Server</span></span>|  
|<span data-ttu-id="a0031-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a0031-106">Event ID</span></span>|<span data-ttu-id="a0031-107">21889</span><span class="sxs-lookup"><span data-stu-id="a0031-107">21889</span></span>|  
|<span data-ttu-id="a0031-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a0031-108">Event Source</span></span>|<span data-ttu-id="a0031-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a0031-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a0031-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a0031-110">Component</span></span>|<span data-ttu-id="a0031-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a0031-111">SQLEngine</span></span>|  
|<span data-ttu-id="a0031-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a0031-112">Symbolic Name</span></span>|<span data-ttu-id="a0031-113">SQLErrorNum21889</span><span class="sxs-lookup"><span data-stu-id="a0031-113">SQLErrorNum21889</span></span>|  
|<span data-ttu-id="a0031-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a0031-114">Message Text</span></span>|<span data-ttu-id="a0031-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス '%s' はレプリケーション パブリッシャーではありません。</span><span class="sxs-lookup"><span data-stu-id="a0031-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' is not a replication publisher.</span></span> <span data-ttu-id="a0031-116">このインスタンスがパブリッシング データベース '%s' をホストできるようにするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス '%s' で、ディストリビューター '%s' を指定して `sp_adddistributor` を実行します。</span><span class="sxs-lookup"><span data-stu-id="a0031-116">Run `sp_adddistributor` on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' with distributor '%s' in order to enable the instance to host the publishing database '%s'.</span></span> <span data-ttu-id="a0031-117">元のパブリッシャーで使用されているものと同じログインおよびパスワードを指定していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a0031-117">Make certain to specify the same login and password as that used for the original publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a0031-118">説明</span><span class="sxs-lookup"><span data-stu-id="a0031-118">Explanation</span></span>  
 <span data-ttu-id="a0031-119">パブリッシャー データベースをホストするためには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがレプリケーション パブリッシャーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0031-119">In order to host the publisher database, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be a replication publisher.</span></span> <span data-ttu-id="a0031-120">`sp_validate_redirected_publisher` は、リモート サーバーで `sp_helpdistributor` を呼び出し、サーバーがレプリケーション パブリッシャーであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="a0031-120">`sp_validate_redirected_publisher` calls `sp_helpdistributor` at the remote server to determine whether the server is a replication publisher.</span></span> <span data-ttu-id="a0031-121">このエラーは、ストアド プロシージャ `sp_helpdistributor` を実行して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の対象のインスタンがレプリケーション パブリッシャーでないことが示された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a0031-121">This error is returned when execution of the stored procedure `sp_helpdistributor` indicates that the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not a replication publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a0031-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a0031-122">User Action</span></span>  
 <span data-ttu-id="a0031-123">パブリッシャー データベースをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで `sp_adddistributor` を実行します。</span><span class="sxs-lookup"><span data-stu-id="a0031-123">Execute `sp_adddistributor` at the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the publisher database.</span></span> <span data-ttu-id="a0031-124">`sp_adddistributor` を実行するときに、正しいディストリビューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0031-124">When running `sp_adddistributor`, specify the correct distributor.</span></span> <span data-ttu-id="a0031-125">*@password*がディストリビューターで最初に実行されたときに使用したのと同じ値をパラメーターとして使用し `sp_adddistributor` ます。</span><span class="sxs-lookup"><span data-stu-id="a0031-125">Use the same value for the *@password* parameter as that used when `sp_adddistributor` was initially run at the distributor.</span></span>  
  
  
