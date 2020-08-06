---
title: '[既存のセカンダリレプリカに接続] ページ (レプリカの追加ウィザードとデータベースの追加ウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.connecttoreplicas.f1
- sql12.swb.adddatabasewizard.connecttoreplicas.f1
ms.assetid: 850f1bc8-d7d0-425c-bd7b-03f0e9d3348e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 80af8dfebd6e23a923ddf67438edabf9ab0e2f65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713509"
---
# <a name="connect-to-existing-secondary-replicas-page-add-replica-wizard-and-add-databases-wizard"></a><span data-ttu-id="1d43e-102">既存のセカンダリ レプリカ ページへの接続 (レプリカの追加ウィザードとデータベース追加ウィザード)</span><span class="sxs-lookup"><span data-stu-id="1d43e-102">Connect to Existing Secondary Replicas Page (Add Replica Wizard and Add Databases Wizard)</span></span>
  <span data-ttu-id="1d43e-103"> このヘルプ トピックでは、**[既存のセカンダリ レプリカへの接続]** ページのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1d43e-103">This help topic describes the options of the **Connect to Existing Secondary Replicas** page.</span></span> <span data-ttu-id="1d43e-104">このトピックでは、 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] の [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] および [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d43e-104">This topic is used by the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="1d43e-105">**グリッド列:**</span><span class="sxs-lookup"><span data-stu-id="1d43e-105">**Grid columns:**</span></span>  
 <span data-ttu-id="1d43e-106">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="1d43e-106">**Server Instance**</span></span>  
 <span data-ttu-id="1d43e-107">可用性レプリカをホストするサーバー インスタンスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="1d43e-107">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="1d43e-108">**接続ユーザー**</span><span class="sxs-lookup"><span data-stu-id="1d43e-108">**Connected As**</span></span>  
 <span data-ttu-id="1d43e-109">接続が確立されると、サーバー インスタンスに接続されるアカウントを表示します。</span><span class="sxs-lookup"><span data-stu-id="1d43e-109">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="1d43e-110">この列で、特定のサーバー インスタンスについて **"未接続"** と表示される場合、 **[接続]** または **[すべての接続]** ボタンのいずれかをクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d43e-110">If this column displays "**Not Connected**" for a given server instance, you will need to click either the **Connect** or **Connect All** button.</span></span>  
  
 <span data-ttu-id="1d43e-111">**接続する**</span><span class="sxs-lookup"><span data-stu-id="1d43e-111">**Connect**</span></span>  
 <span data-ttu-id="1d43e-112">このサーバー インスタンスが、接続する他のサーバー インスタンスとは異なるアカウントで実行されている場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d43e-112">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="1d43e-113">**[すべての接続]**</span><span class="sxs-lookup"><span data-stu-id="1d43e-113">**Connect All**</span></span>  
 <span data-ttu-id="1d43e-114">接続する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべてのインスタンスが、同じユーザー アカウントでサービスとして実行されている場合にのみクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d43e-114">Click only if every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which you need to connect is running as a service in the same user account.</span></span>  
  
 <span data-ttu-id="1d43e-115">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="1d43e-115">**Cancel**</span></span>  
 <span data-ttu-id="1d43e-116">ウィザードをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="1d43e-116">Click to cancel the wizard.</span></span> <span data-ttu-id="1d43e-117">**[既存のセカンダリ レプリカへの接続]** ページでウィザードをキャンセルすると、何もアクションを実行せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="1d43e-117">On the **Connect to Existing Secondary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1d43e-118">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1d43e-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1d43e-119">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1d43e-119">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="1d43e-120">可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1d43e-120">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="1d43e-121">参照</span><span class="sxs-lookup"><span data-stu-id="1d43e-121">See Also</span></span>  
 [<span data-ttu-id="1d43e-122">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="1d43e-122">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
