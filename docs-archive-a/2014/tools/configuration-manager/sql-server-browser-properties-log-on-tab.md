---
title: SQL Server Browser のプロパティ ([ログオン] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c1f7d0cfd9e9b05a2a04f3c3e9efba687522298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711378"
---
# <a name="sql-server-browser-properties-log-on-tab"></a><span data-ttu-id="7e2b4-102">[SQL Server Browser のプロパティ] ダイアログ ボックス ([ログオン] タブ)</span><span class="sxs-lookup"><span data-stu-id="7e2b4-102">SQL Server Browser Properties (Log On Tab)</span></span>
  <span data-ttu-id="7e2b4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser プログラムはサーバー上のサービスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7e2b4-104">Browser では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種リソースに関する着信要求を受信し、このコンピューター上にインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7e2b4-105">Browser は、UDP ポートでリッスンし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP) を使用して未認証の要求を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-105">Browser listens on a UDP port and accepts unauthenticated requests using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP).</span></span>  
  
 <span data-ttu-id="7e2b4-106">アカウントのパスワードを変更した場合、サービスを再起動しなくても、すぐにその変更が有効になります。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-106">Changing the password of an account takes effect immediately without restarting the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7e2b4-107">オプション</span><span class="sxs-lookup"><span data-stu-id="7e2b4-107">Options</span></span>  
 <span data-ttu-id="7e2b4-108">**[ローカル システム アカウント]**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-108">**Local System account**</span></span>  
 <span data-ttu-id="7e2b4-109">ローカル システム アカウントのセキュリティ コンテキストで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-109">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service in the security context of the Local System account.</span></span> <span data-ttu-id="7e2b4-110">可能な場合は、この代わりに低い権限を設定したアカウントを使用してください。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-110">When possible, use a low-permission account instead.</span></span>  
  
 <span data-ttu-id="7e2b4-111">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-111">**This account**</span></span>  
 <span data-ttu-id="7e2b4-112">Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-112">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="7e2b4-113">サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-113">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="7e2b4-114">アカウントの選択の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「Windows サービス アカウントの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-114">For information about selecting an account, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="7e2b4-115">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-115">**Browse**</span></span>  
 <span data-ttu-id="7e2b4-116">ユーザーまたは組み込みのセキュリティ プリンシパルを表示します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-116">Browse for a user or built-in security principal.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7e2b4-117">低い権限を設定したアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-117">Use a low-permission account.</span></span> <span data-ttu-id="7e2b4-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスに必要な権限の詳細については、「 [SQL Server Browser サービス](../../../2014/tools/configuration-manager/sql-server-browser-service.md)」の「セキュリティ」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-118">For information about the permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service, see the Security section of [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="7e2b4-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-119">**Password**</span></span>  
 <span data-ttu-id="7e2b4-120">セキュリティ プリンシパルのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-120">Enter the password of the security principal.</span></span>  
  
 <span data-ttu-id="7e2b4-121">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-121">**Confirm password**</span></span>  
 <span data-ttu-id="7e2b4-122">セキュリティ プリンシパルのパスワードを確認入力します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-122">Confirm the password of the security principal.</span></span>  
  
 <span data-ttu-id="7e2b4-123">**サービスの状態**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-123">**Service status**</span></span>  
 <span data-ttu-id="7e2b4-124">このサービスが実行中か、停止しているか、無効になっているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-124">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="7e2b4-125">" **...** " の場合は、状態の変更が保留になっています。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-125">"**...**" indicates a state change is pending.</span></span>  
  
 <span data-ttu-id="7e2b4-126">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-126">**Start**</span></span>  
 <span data-ttu-id="7e2b4-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-127">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="7e2b4-128">**Stop**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-128">**Stop**</span></span>  
 <span data-ttu-id="7e2b4-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-129">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="7e2b4-130">**[一時停止]**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-130">**Pause**</span></span>  
 <span data-ttu-id="7e2b4-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-131">Pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="7e2b4-132">**[再開]**</span><span class="sxs-lookup"><span data-stu-id="7e2b4-132">**Resume**</span></span>  
 <span data-ttu-id="7e2b4-133">一時停止した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="7e2b4-133">Resume a paused [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2b4-134">参照</span><span class="sxs-lookup"><span data-stu-id="7e2b4-134">See Also</span></span>  
 [<span data-ttu-id="7e2b4-135">SQL Server Browser サービス</span><span class="sxs-lookup"><span data-stu-id="7e2b4-135">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
