---
title: Windows アプリケーション ログの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22f900a0b203e652bbc9cc6e9638711d138756c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640291"
---
# <a name="viewing-the-windows-application-log"></a><span data-ttu-id="5a4c2-102">Windows アプリケーション ログの表示</span><span class="sxs-lookup"><span data-stu-id="5a4c2-102">Viewing the Windows Application Log</span></span>
  <span data-ttu-id="5a4c2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が Microsoft Windows アプリケーション ログを使用するように構成されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各セッションでは新しいイベントが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Microsoft Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="5a4c2-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログとは異なり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを開始するたびに新しいアプリケーション ログが作成されることはありません。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5a4c2-105">Windows イベント ビューアーまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のログ ビューアーを使用して、Windows アプリケーション ログを表示および管理します。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-105">View and manage the Windows application log by using Windows Event Viewer or the Log Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5a4c2-106">イベント ビューアーでは、次の 3 つのログを表示できます。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-106">There are three logs that can be viewed with Event Viewer.</span></span>  
  
|<span data-ttu-id="5a4c2-107">Windows ログの種類</span><span class="sxs-lookup"><span data-stu-id="5a4c2-107">Windows log type</span></span>|<span data-ttu-id="5a4c2-108">説明</span><span class="sxs-lookup"><span data-stu-id="5a4c2-108">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="5a4c2-109">システム ログ</span><span class="sxs-lookup"><span data-stu-id="5a4c2-109">System log</span></span>|<span data-ttu-id="5a4c2-110">Windows オペレーティング システムのコンポーネントによってログに記録されるイベントを記録します。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-110">Records events logged by the Windows operating system components.</span></span> <span data-ttu-id="5a4c2-111">たとえば、起動時にドライバーや他のシステム コンポーネントの読み込みが失敗した場合には、システム ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-111">For example, the failure of a driver or other system component to load during startup is recorded in the system log.</span></span>|  
|<span data-ttu-id="5a4c2-112">Security log</span><span class="sxs-lookup"><span data-stu-id="5a4c2-112">Security log</span></span>|<span data-ttu-id="5a4c2-113">失敗したログイン試行などのセキュリティ イベントを記録します。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-113">Records security events, such as failed login attempts.</span></span> <span data-ttu-id="5a4c2-114">これは、セキュリティ システムへの変更を監視し、セキュリティ侵害のおそれのある箇所を特定するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-114">This helps track changes to the security system and identify possible breaches to security.</span></span> <span data-ttu-id="5a4c2-115">たとえば、システムへのログオン試行は、User Manager の監査設定によってセキュリティ ログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-115">For example, attempts to log on to the system may be recorded in the security log, depending on the audit settings in the User Manager.</span></span><br /><br /> <span data-ttu-id="5a4c2-116">**sysadmin** 固定サーバー ロールのメンバーだけが、セキュリティ ログを表示できます。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-116">Only members of the **sysadmin** fixed server role can view the security log.</span></span>|  
|<span data-ttu-id="5a4c2-117">アプリケーション ログ</span><span class="sxs-lookup"><span data-stu-id="5a4c2-117">Application log</span></span>|<span data-ttu-id="5a4c2-118">アプリケーションによってログに記録されるイベントを記録します。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-118">Records events that are logged by applications.</span></span> <span data-ttu-id="5a4c2-119">たとえば、データベース アプリケーションは、アプリケーション ログにファイル エラーを記録することがあります。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-119">For example, a database application might record a file error in the application log.</span></span>|  
  
 <span data-ttu-id="5a4c2-120">イベント ビューアーの使用方法、アプリケーション ログの管理方法、および表示される情報の解釈方法の詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a4c2-120">For more information about using Event Viewer, managing the application log, and understanding the information it presents, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="5a4c2-121">**Windows アプリケーション ログを表示するには**</span><span class="sxs-lookup"><span data-stu-id="5a4c2-121">**To view the Windows application log**</span></span>  
  
 [<span data-ttu-id="5a4c2-122">Windows アプリケーション ログの表示 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="5a4c2-122">View the Windows Application Log &#40;Windows&#41;</span></span>](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
