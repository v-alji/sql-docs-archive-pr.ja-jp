---
title: MSSQL_ENG018456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b05ca549781215e0c4f247110fee87f6def56f04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717967"
---
# <a name="mssql_eng018456"></a><span data-ttu-id="ea1a5-102">MSSQL_ENG018456</span><span class="sxs-lookup"><span data-stu-id="ea1a5-102">MSSQL_ENG018456</span></span>
    
## <a name="message-details"></a><span data-ttu-id="ea1a5-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="ea1a5-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea1a5-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ea1a5-104">Product Name</span></span>|<span data-ttu-id="ea1a5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ea1a5-105">SQL Server</span></span>|  
|<span data-ttu-id="ea1a5-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ea1a5-106">Event ID</span></span>|<span data-ttu-id="ea1a5-107">18456</span><span class="sxs-lookup"><span data-stu-id="ea1a5-107">18456</span></span>|  
|<span data-ttu-id="ea1a5-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ea1a5-108">Event Source</span></span>|<span data-ttu-id="ea1a5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ea1a5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ea1a5-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ea1a5-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="ea1a5-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ea1a5-111">Symbolic Name</span></span>||  
|<span data-ttu-id="ea1a5-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ea1a5-112">Message Text</span></span>|<span data-ttu-id="ea1a5-113">ユーザー '%.\*ls'.%.\*ls はログインできませんでした</span><span class="sxs-lookup"><span data-stu-id="ea1a5-113">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ea1a5-114">説明</span><span class="sxs-lookup"><span data-stu-id="ea1a5-114">Explanation</span></span>  
 <span data-ttu-id="ea1a5-115">ログインの試行が失敗するたびに、エラー MSSQL_ENG018456 が発生します。</span><span class="sxs-lookup"><span data-stu-id="ea1a5-115">Error MSSQL_ENG018456 is raised whenever a login attempt fails.</span></span> <span data-ttu-id="ea1a5-116">エラー メッセージにアカウント **distributor_admin** が含まれている場合 ("ユーザー 'distributor_admin' はログインできませんでした。" となっている場合)、問題はレプリケーションによって使用されているアカウントに関するものです。</span><span class="sxs-lookup"><span data-stu-id="ea1a5-116">If the error message includes the account **distributor_admin** (Login failed for user 'distributor_admin'.), the issue is with an account used by replication.</span></span> <span data-ttu-id="ea1a5-117">レプリケーションによってリモート サーバー **repl_distributor**が作成され、これによってディストリビューターとパブリッシャーの間の通信が可能になります。</span><span class="sxs-lookup"><span data-stu-id="ea1a5-117">Replication creates a remote server, **repl_distributor**, which allows communication between the Distributor and Publisher.</span></span> <span data-ttu-id="ea1a5-118">ログイン **distributor_admin** は、このリモート サーバーに関連付けられており、有効なパスワードを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea1a5-118">The login **distributor_admin** is associated with this remote server and must have a valid password.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ea1a5-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ea1a5-119">User Action</span></span>  
 <span data-ttu-id="ea1a5-120">このアカウントに対するパスワードを指定したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ea1a5-120">Ensure that you have specified a password for this account.</span></span> <span data-ttu-id="ea1a5-121">詳細については、「[ディストリビューターのセキュリティ保護](security/secure-the-distributor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea1a5-121">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1a5-122">参照</span><span class="sxs-lookup"><span data-stu-id="ea1a5-122">See Also</span></span>  
 [<span data-ttu-id="ea1a5-123">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="ea1a5-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
