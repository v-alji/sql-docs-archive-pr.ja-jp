---
title: '[キュー リーダー エージェントのセキュリティ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 22a5e5751184b626ab1af86f01782a42028b5ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644436"
---
# <a name="queue-reader-agent-security"></a><span data-ttu-id="7cc31-102">[キュー リーダー エージェントのセキュリティ]</span><span class="sxs-lookup"><span data-stu-id="7cc31-102">Queue Reader Agent Security</span></span>
  <span data-ttu-id="7cc31-103">**[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスを使用すると、キュー リーダー エージェントを実行したり、ディストリビューターへのローカル接続を行ったりするための [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7cc31-103">The **Queue Reader Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Queue Reader Agent runs and makes local connections to the Distributor.</span></span> <span data-ttu-id="7cc31-104">エージェントは、( **[ディストリビューターのプロパティ]** ダイアログ ボックスから呼び出される) **[パブリッシャーのプロパティ]** ダイアログ ボックスで指定されたアカウントを使用してパブリッシャーに接続します。エージェントは、同じコンテキストを使用して、サブスクリプションのディストリビューション エージェントとしてサブスクライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="7cc31-104">The agent connects to the Publisher using the account specified in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box); the agent connects to the Subscriber using the same context as the Distribution Agent for the subscription.</span></span> <span data-ttu-id="7cc31-105">詳細については、「 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cc31-105">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="7cc31-106">アカウントは、適切なパスワードが指定された有効なアカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cc31-106">The account must be valid with the correct password specified.</span></span> <span data-ttu-id="7cc31-107">アカウントとパスワードは、エージェントが実行されるまで検証されません。</span><span class="sxs-lookup"><span data-stu-id="7cc31-107">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7cc31-108">オプション</span><span class="sxs-lookup"><span data-stu-id="7cc31-108">Options</span></span>  
 <span data-ttu-id="7cc31-109">**[プロセス アカウント]**</span><span class="sxs-lookup"><span data-stu-id="7cc31-109">**Process account**</span></span>  
 <span data-ttu-id="7cc31-110">ディストリビューターでキュー リーダー エージェントを実行するための Windows アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="7cc31-110">Enter a Windows account under which the Queue Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="7cc31-111">指定した Windows アカウントは少なくともディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cc31-111">The Windows account you specify must at minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
 <span data-ttu-id="7cc31-112">**[パスワード]** と **[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="7cc31-112">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="7cc31-113">Windows アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7cc31-113">Enter the password for the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc31-114">参照</span><span class="sxs-lookup"><span data-stu-id="7cc31-114">See Also</span></span>  
 <span data-ttu-id="7cc31-115">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="7cc31-115">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="7cc31-116">[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="7cc31-116">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="7cc31-117">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="7cc31-117">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="7cc31-118">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="7cc31-118">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
