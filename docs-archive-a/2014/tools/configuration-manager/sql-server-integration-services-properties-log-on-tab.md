---
title: '[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([ログオン] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfef02a82872ea1df25e7ccb8526e488aaa5f406
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737308"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a><span data-ttu-id="969fb-102">[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([ログオン] タブ)</span><span class="sxs-lookup"><span data-stu-id="969fb-102">SQL Server Integration Services Properties (Log On Tab)</span></span>
  <span data-ttu-id="969fb-103">[ **の**プロパティ[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]] ダイアログ ボックスの **[ログオン]** タブでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスで使用するアカウントの指定や、そのサービスの開始、停止を行います。</span><span class="sxs-lookup"><span data-stu-id="969fb-103">Use the **Log On** tab of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to specify the account used by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="969fb-104">オプション</span><span class="sxs-lookup"><span data-stu-id="969fb-104">Options</span></span>  
 <span data-ttu-id="969fb-105">**[ローカル システム アカウント]**</span><span class="sxs-lookup"><span data-stu-id="969fb-105">**Local System account**</span></span>  
 <span data-ttu-id="969fb-106">ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="969fb-106">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="969fb-107">ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスと他のサーバーとの対話が制限されることもあります。</span><span class="sxs-lookup"><span data-stu-id="969fb-107">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="969fb-108">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="969fb-108">**This account**</span></span>  
 <span data-ttu-id="969fb-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="969fb-109">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="969fb-110">では、サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="969fb-110">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="969fb-111">アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="969fb-111">For information about selecting an account, search Books Online for the topic, "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="969fb-112">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="969fb-112">**Account Name**</span></span>  
 <span data-ttu-id="969fb-113">ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="969fb-113">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="969fb-114">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="969fb-114">**Password**</span></span>  
 <span data-ttu-id="969fb-115">アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="969fb-115">Type the password of the account.</span></span>  
  
 <span data-ttu-id="969fb-116">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="969fb-116">**Confirm password**</span></span>  
 <span data-ttu-id="969fb-117">アカウントのパスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="969fb-117">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="969fb-118">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="969fb-118">**Start**</span></span>  
 <span data-ttu-id="969fb-119">サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="969fb-119">Start the service.</span></span>  
  
 <span data-ttu-id="969fb-120">**Stop**</span><span class="sxs-lookup"><span data-stu-id="969fb-120">**Stop**</span></span>  
 <span data-ttu-id="969fb-121">サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="969fb-121">Stop the service.</span></span>  
  
 <span data-ttu-id="969fb-122">**[一時停止]**</span><span class="sxs-lookup"><span data-stu-id="969fb-122">**Pause**</span></span>  
 <span data-ttu-id="969fb-123">サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="969fb-123">Pause the service.</span></span>  
  
 <span data-ttu-id="969fb-124">**[再開]**</span><span class="sxs-lookup"><span data-stu-id="969fb-124">**Resume**</span></span>  
 <span data-ttu-id="969fb-125">一時停止したサービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="969fb-125">Resume a paused service.</span></span>  
  
  
