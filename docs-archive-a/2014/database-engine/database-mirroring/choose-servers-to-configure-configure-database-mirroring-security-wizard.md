---
title: 構成するサーバーを選択する (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18e36f5c8ec020b3859dc847d1bbfc019817bcd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634039"
---
# <a name="choose-servers-to-configure-configure-database-mirroring-security-wizard"></a><span data-ttu-id="90fc2-102">[構成するサーバーを選択する] (データベース ミラーリング セキュリティ構成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="90fc2-102">Choose Servers to Configure (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="90fc2-103">このページを使用すると、構成するサーバー インスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="90fc2-103">Use this page to specify which server instances you want to configure now.</span></span> <span data-ttu-id="90fc2-104">ウィザードを進めるには、少なくとも 1 つのサーバー インスタンスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90fc2-104">You must select at least one server instance before continuing the wizard.</span></span>  
  
 <span data-ttu-id="90fc2-105">サーバー インスタンスのチェック ボックスをオフにすると、このウィザードでは、そのサーバーを変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="90fc2-105">If you clear the check box for a server instance, the wizard will not make any changes to it.</span></span> <span data-ttu-id="90fc2-106">ただし、他のサーバー インスタンスの構成の一部としてこのインスタンスの情報を入力し、保存するように求められます。</span><span class="sxs-lookup"><span data-stu-id="90fc2-106">The wizard, however, will ask you to enter information about that instance and save this information as part of the configuration of the other server instances.</span></span> <span data-ttu-id="90fc2-107">たとえば、ミラーリング監視サーバー インスタンスのチェック ボックスをオフにした場合でも、ミラーリング監視サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントを入力するように求められます。これは、プリンシパル サーバー インスタンスおよびミラー サーバー インスタンスに保存するセキュリティ構成の中で、このアカウントのログインを作成する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="90fc2-107">For example, if you clear the check box for the witness server instance, the wizard will ask you to enter the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the witness because a login for that account must be created as part of the security configuration saved at the principal and mirror server instances.</span></span>  
  
 <span data-ttu-id="90fc2-108">**SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**</span><span class="sxs-lookup"><span data-stu-id="90fc2-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="90fc2-109">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="90fc2-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="90fc2-110">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="90fc2-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="90fc2-111">Options</span><span class="sxs-lookup"><span data-stu-id="90fc2-111">Options</span></span>  
 <span data-ttu-id="90fc2-112">**[プリンシパル サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="90fc2-112">**Principal server instance**</span></span>  
 <span data-ttu-id="90fc2-113">プリンシパル サーバーのセキュリティを構成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="90fc2-113">Select to configure security for the principal server.</span></span>  
  
 <span data-ttu-id="90fc2-114">**[ミラー サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="90fc2-114">**Mirror server instance**</span></span>  
 <span data-ttu-id="90fc2-115">ミラー サーバーのセキュリティを構成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="90fc2-115">Select to configure security for the mirror server.</span></span>  
  
 <span data-ttu-id="90fc2-116">**[ミラーリング監視サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="90fc2-116">**Witness server instance**</span></span>  
 <span data-ttu-id="90fc2-117">ミラーリング監視サーバー (存在する場合) のセキュリティを構成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="90fc2-117">Select to configure security for the witness server (if present).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90fc2-118">参照</span><span class="sxs-lookup"><span data-stu-id="90fc2-118">See Also</span></span>  
 <span data-ttu-id="90fc2-119">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="90fc2-119">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 [<span data-ttu-id="90fc2-120">データベース ミラーリング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90fc2-120">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
