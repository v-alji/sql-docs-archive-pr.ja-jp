---
title: '[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 743a8d558e97e9ad83cfc66e9ef1adf2e1bc0c2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644267"
---
# <a name="sql-server-agent-properties-job-system-page"></a><span data-ttu-id="7635e-102">[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ)</span><span class="sxs-lookup"><span data-stu-id="7635e-102">SQL Server Agent Properties (Job System Page)</span></span>
  <span data-ttu-id="7635e-103">このページを使用すると、エージェントサービスがジョブを管理する方法を表示したり、変更したり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="7635e-103">Use this page to view and modify how the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service manages jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7635e-104">Options</span><span class="sxs-lookup"><span data-stu-id="7635e-104">Options</span></span>  
 <span data-ttu-id="7635e-105">**[シャットダウン タイムアウト間隔 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="7635e-105">**Shutdown time-out interval (in seconds)**</span></span>  
 <span data-ttu-id="7635e-106">シャットダウンの前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがジョブの完了を待つ時間を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="7635e-106">Specifies the number of seconds that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for jobs to complete before shutting down.</span></span> <span data-ttu-id="7635e-107">指定した時間が過ぎてもジョブが実行されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって強制的にジョブが停止されます。</span><span class="sxs-lookup"><span data-stu-id="7635e-107">If the job is still running after the interval specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent forcefully stops the job.</span></span>  
  
 <span data-ttu-id="7635e-108">**[管理者以外のプロキシ アカウントを使用する]**</span><span class="sxs-lookup"><span data-stu-id="7635e-108">**Use a non-administrator proxy account**</span></span>  
 <span data-ttu-id="7635e-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに管理者以外のプロキシ アカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="7635e-109">Sets a non-administrator proxy account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="7635e-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降のバージョンでは複数のプロキシがサポートされるため、このオプションは管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] する場合にのみ適用できます。より前のバージョンのエージェント [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7635e-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="7635e-111">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="7635e-111">**User name**</span></span>  
 <span data-ttu-id="7635e-112">管理者以外のプロキシ アカウントのユーザーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="7635e-112">Type the name of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7635e-113">では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]エージェントを管理する場合にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="7635e-113">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="7635e-114">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="7635e-114">**Password**</span></span>  
 <span data-ttu-id="7635e-115">管理者以外のプロキシ アカウントのユーザーのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7635e-115">Type the password of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="7635e-116">以降のバージョンでは複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]エージェントを管理する場合にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="7635e-116">and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="7635e-117">**[ドメイン]**</span><span class="sxs-lookup"><span data-stu-id="7635e-117">**Domain**</span></span>  
 <span data-ttu-id="7635e-118">管理者以外のプロキシ アカウントのユーザーのドメインを入力します。</span><span class="sxs-lookup"><span data-stu-id="7635e-118">Type the domain of the user for the non-administrative proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7635e-119">では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]エージェントを管理する場合にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="7635e-119">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7635e-120">参照</span><span class="sxs-lookup"><span data-stu-id="7635e-120">See Also</span></span>  
 [<span data-ttu-id="7635e-121">ジョブの実装</span><span class="sxs-lookup"><span data-stu-id="7635e-121">Implement Jobs</span></span>](implement-jobs.md)  
  
  
