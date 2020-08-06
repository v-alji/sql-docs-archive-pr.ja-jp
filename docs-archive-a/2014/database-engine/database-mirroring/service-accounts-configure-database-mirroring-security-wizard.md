---
title: サービス アカウント (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58e49467a28e816c6592b1ded212b5aea0e6bc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716734"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a><span data-ttu-id="c7039-102">[サービス アカウント] (データベース ミラーリング セキュリティ構成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="c7039-102">Service Accounts (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="c7039-103">Windows 認証でサーバー インスタンスが別のアカウントを使用している場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7039-103">When using Windows Authentication, if the server instances use different accounts, specify the service accounts for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7039-104">これらのサービス アカウントは、すべて (同じドメインまたは信頼関係のあるドメインの) ドメイン アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7039-104">These service accounts must all be domain accounts (in the same or trusted domains).</span></span>  
  
 <span data-ttu-id="c7039-105">すべてのサーバー インスタンスが同じアカウントを使用している場合、または証明書ベースの認証を使用している場合、フィールドは空のままにします。</span><span class="sxs-lookup"><span data-stu-id="c7039-105">If all the server instances use the same domain account or use certificate-based authentication, leave the fields blank.</span></span> <span data-ttu-id="c7039-106">**[完了]** をクリックするだけで、現在のウィザードのアカウントに基づいてアカウントが自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="c7039-106">Simply click **Finish**, and the wizard automatically configures the accounts based on the account of the current wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7039-107">サーバー インスタンスのデータベース ミラーリング エンドポイントで証明書を使用するように構成されている場合は、サービス アカウント フィールドをすべて空にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7039-107">If the database mirroring endpoints of the server instances are configured to use certificates, you must leave the service account fields empty.</span></span>  
  
 <span data-ttu-id="c7039-108">**SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**</span><span class="sxs-lookup"><span data-stu-id="c7039-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="c7039-109">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c7039-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="c7039-110">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c7039-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="c7039-111">Options</span><span class="sxs-lookup"><span data-stu-id="c7039-111">Options</span></span>  
 <span data-ttu-id="c7039-112">**プリンシパル**</span><span class="sxs-lookup"><span data-stu-id="c7039-112">**Principal**</span></span>  
 <span data-ttu-id="c7039-113">プリンシパル サーバー インスタンスのサービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7039-113">Specify the service account of the principal server instance.</span></span> <span data-ttu-id="c7039-114">ドメイン名を大文字で入力します。</span><span class="sxs-lookup"><span data-stu-id="c7039-114">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="c7039-115">*DOMAINNAME* \\*ユーザー名*</span><span class="sxs-lookup"><span data-stu-id="c7039-115">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="c7039-116">**ミラー**</span><span class="sxs-lookup"><span data-stu-id="c7039-116">**Mirror**</span></span>  
 <span data-ttu-id="c7039-117">ミラー サーバー インスタンスのサービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7039-117">Specify the service account of the mirror server instance.</span></span> <span data-ttu-id="c7039-118">ドメイン名を大文字で入力します。</span><span class="sxs-lookup"><span data-stu-id="c7039-118">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="c7039-119">*DOMAINNAME* \\*ユーザー名*</span><span class="sxs-lookup"><span data-stu-id="c7039-119">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="c7039-120">**監視**</span><span class="sxs-lookup"><span data-stu-id="c7039-120">**Witness**</span></span>  
 <span data-ttu-id="c7039-121">ミラーリング監視サーバー インスタンスのサービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7039-121">Specify the service account of the witness server instance.</span></span> <span data-ttu-id="c7039-122">ドメイン名を大文字で入力します。</span><span class="sxs-lookup"><span data-stu-id="c7039-122">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="c7039-123">*DOMAINNAME* \\*ユーザー名*</span><span class="sxs-lookup"><span data-stu-id="c7039-123">*DOMAINNAME*\\*username*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7039-124">参照</span><span class="sxs-lookup"><span data-stu-id="c7039-124">See Also</span></span>  
 <span data-ttu-id="c7039-125">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="c7039-125">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="c7039-126">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c7039-126">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="c7039-127">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c7039-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="c7039-128">データベースミラーリングまたは AlwaysOn 可用性グループ &#40;SQL Server のログインアカウントを設定&#41;</span><span class="sxs-lookup"><span data-stu-id="c7039-128">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
