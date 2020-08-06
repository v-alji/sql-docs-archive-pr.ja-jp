---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5786d5de4748f6bbf59d2bd4acecd7ca77977f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642109"
---
# <a name="mssqlserver_18452"></a><span data-ttu-id="188bc-102">MSSQLSERVER_18452</span><span class="sxs-lookup"><span data-stu-id="188bc-102">MSSQLSERVER_18452</span></span>
    
## <a name="details"></a><span data-ttu-id="188bc-103">詳細</span><span class="sxs-lookup"><span data-stu-id="188bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="188bc-104">製品名</span><span class="sxs-lookup"><span data-stu-id="188bc-104">Product Name</span></span>|<span data-ttu-id="188bc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="188bc-105">SQL Server</span></span>|  
|<span data-ttu-id="188bc-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="188bc-106">Event ID</span></span>|<span data-ttu-id="188bc-107">18452</span><span class="sxs-lookup"><span data-stu-id="188bc-107">18452</span></span>|  
|<span data-ttu-id="188bc-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="188bc-108">Event Source</span></span>|<span data-ttu-id="188bc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="188bc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="188bc-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="188bc-110">Component</span></span>|<span data-ttu-id="188bc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="188bc-111">SQLEngine</span></span>|  
|<span data-ttu-id="188bc-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="188bc-112">Symbolic Name</span></span>|<span data-ttu-id="188bc-113">LOGON_INVALID_CONNECT</span><span class="sxs-lookup"><span data-stu-id="188bc-113">LOGON_INVALID_CONNECT</span></span>|  
|<span data-ttu-id="188bc-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="188bc-114">Message Text</span></span>|<span data-ttu-id="188bc-115">ユーザー '%.\*ls' はログインできませんでした。</span><span class="sxs-lookup"><span data-stu-id="188bc-115">Login failed for user '%.\*ls'.</span></span> <span data-ttu-id="188bc-116">このログインは SQL Server ログインなので、Windows 認証では使用できません。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="188bc-116">The login is a SQL Server login and cannot be used with Windows Authentication.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="188bc-117">説明</span><span class="sxs-lookup"><span data-stu-id="188bc-117">Explanation</span></span>  
 <span data-ttu-id="188bc-118">検証できない資格情報でユーザーがログインしようとしました。</span><span class="sxs-lookup"><span data-stu-id="188bc-118">The user attempted to login with credentials that cannot be validated.</span></span> <span data-ttu-id="188bc-119">次の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="188bc-119">Possible causes are:</span></span>  
  
-   <span data-ttu-id="188bc-120">ログインは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインですが、サーバーは Windows 認証のみを受け付けます。</span><span class="sxs-lookup"><span data-stu-id="188bc-120">The login may be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login but the server only accepts Windows Authentication.</span></span>  
  
-   <span data-ttu-id="188bc-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしていますが、使用しているログインが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に存在しません。</span><span class="sxs-lookup"><span data-stu-id="188bc-121">You are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but the login used does not exist on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="188bc-122">ログインで Windows 認証を使用していますが、そのログインは認識できない Windows プリンシパルです。</span><span class="sxs-lookup"><span data-stu-id="188bc-122">The login may use Windows Authentication but the login is an unrecognized Windows principal.</span></span> <span data-ttu-id="188bc-123">認識できない Windows プリンシパルは、ログインを Windows で確認できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="188bc-123">An unrecognized Windows principal means that the login cannot be verified by Windows.</span></span> <span data-ttu-id="188bc-124">これは、信頼されていないドメインからの Windows ログインである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="188bc-124">This could be because the Windows login is from an untrusted domain.</span></span>  
  
 <span data-ttu-id="188bc-125">同様の問題によって、より広い意味のエラー 18456 が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="188bc-125">Similar problems can cause the less-specific error 18456.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="188bc-126">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="188bc-126">User Action</span></span>  
 <span data-ttu-id="188bc-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が混合モード認証で構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="188bc-127">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="188bc-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="188bc-128">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists.</span></span>  
  
 <span data-ttu-id="188bc-129">Windows 認証を使用して接続しようとしている場合は、正しいドメインに適切にログインしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="188bc-129">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
  
