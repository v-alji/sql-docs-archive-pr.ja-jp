---
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beb854c866256728574e06f8c9efb50fb354e15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643910"
---
# <a name="mssqlserver_15404"></a><span data-ttu-id="7e900-102">MSSQLSERVER_15404</span><span class="sxs-lookup"><span data-stu-id="7e900-102">MSSQLSERVER_15404</span></span>
    
## <a name="details"></a><span data-ttu-id="7e900-103">詳細</span><span class="sxs-lookup"><span data-stu-id="7e900-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e900-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7e900-104">Product Name</span></span>|<span data-ttu-id="7e900-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7e900-105">SQL Server</span></span>|  
|<span data-ttu-id="7e900-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7e900-106">Event ID</span></span>|<span data-ttu-id="7e900-107">15404</span><span class="sxs-lookup"><span data-stu-id="7e900-107">15404</span></span>|  
|<span data-ttu-id="7e900-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7e900-108">Event Source</span></span>|<span data-ttu-id="7e900-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7e900-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7e900-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7e900-110">Component</span></span>|<span data-ttu-id="7e900-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7e900-111">SQLEngine</span></span>|  
|<span data-ttu-id="7e900-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7e900-112">Symbolic Name</span></span>|<span data-ttu-id="7e900-113">SEC_NTGRP_ERROR</span><span class="sxs-lookup"><span data-stu-id="7e900-113">SEC_NTGRP_ERROR</span></span>|  
|<span data-ttu-id="7e900-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7e900-114">Message Text</span></span>|<span data-ttu-id="7e900-115">Windows NT グループまたはユーザー '*user*' に関する情報を取得できませんでした。エラー コード *code*。</span><span class="sxs-lookup"><span data-stu-id="7e900-115">Could not obtain information about Windows NT group/user '*user*', error code *code*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7e900-116">説明</span><span class="sxs-lookup"><span data-stu-id="7e900-116">Explanation</span></span>  
 <span data-ttu-id="7e900-117">無効なプリンシパルが指定された場合は、15404 が認証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e900-117">15404 is used in authentication when an invalid principal is specified.</span></span> <span data-ttu-id="7e900-118">そうしないと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントと Windows アカウントのドメインとの完全信頼リレーションシップがないために、アカウントの権限借用が失敗します。</span><span class="sxs-lookup"><span data-stu-id="7e900-118">Or, impersonation of a Windows account fails because there is no full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7e900-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7e900-119">User Action</span></span>  
 <span data-ttu-id="7e900-120">Windows プリンシパルが存在し、スペルが誤っていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7e900-120">Check that the Windows principal exists and is not misspelled.</span></span>  
  
 <span data-ttu-id="7e900-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントと Windows アカウントのドメインとの完全信頼リレーションシップがないことが、このエラーの原因である場合、次のいずれかの操作でエラーを解決できます。</span><span class="sxs-lookup"><span data-stu-id="7e900-121">If this error is the result of a lack of a full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account, one of the following actions can resolve the error:</span></span>  
  
-   <span data-ttu-id="7e900-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの Windows ユーザーと同じドメインからのアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e900-122">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="7e900-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が Network Service や Local System などのコンピューター アカウントを使用している場合は、Windows ユーザーを含むコンピューターはドメインから信頼されます。</span><span class="sxs-lookup"><span data-stu-id="7e900-123">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows User.</span></span>  
  
-   <span data-ttu-id="7e900-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e900-124">Use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
  
