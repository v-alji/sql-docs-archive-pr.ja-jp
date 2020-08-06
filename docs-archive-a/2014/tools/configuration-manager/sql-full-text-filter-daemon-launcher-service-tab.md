---
title: SQL フルテキスト フィルター デーモン ランチャー ([サービス] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 6aad7ebe-c4be-4d37-8536-61502f51faa2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f0d9c76d7d92947dd17fe2ed6e912e3d6baa6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644724"
---
# <a name="sql-full-text-filter-daemon-launcher-service-tab"></a><span data-ttu-id="4b7df-102">SQL フルテキスト フィルター デーモン ランチャー ([サービス] タブ)</span><span class="sxs-lookup"><span data-stu-id="4b7df-102">SQL Full-text Filter Daemon Launcher (Service Tab)</span></span>
  <span data-ttu-id="4b7df-103">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フルテキスト検索で SQL フルテキスト フィルター デーモン ランチャー (FDHOST ランチャー) サービスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text.</span></span> <span data-ttu-id="4b7df-104">フルテキスト検索を使用する場合はこのサービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b7df-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="4b7df-105">フィルター デーモン ホスト プロセスの詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「フルテキスト検索のアーキテクチャ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b7df-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="4b7df-106">**[SQL フルテキスト フィルター デーモン ランチャーのプロパティ]** ダイアログ ボックスの **[サービス]** タブでは、以下のオプションの表示や指定を行います。</span><span class="sxs-lookup"><span data-stu-id="4b7df-106">Use the **Service**tab on the **SQL Full-text Filter Daemon LauncherProperties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4b7df-107">オプション</span><span class="sxs-lookup"><span data-stu-id="4b7df-107">Options</span></span>  
 <span data-ttu-id="4b7df-108">**[バイナリ パス]**</span><span class="sxs-lookup"><span data-stu-id="4b7df-108">**Binary Path**</span></span>  
 <span data-ttu-id="4b7df-109">このサービスで使用するプログラム ファイルの場所を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="4b7df-109">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="4b7df-110">**[エラー制御]**</span><span class="sxs-lookup"><span data-stu-id="4b7df-110">**Error Control**</span></span>  
 <span data-ttu-id="4b7df-111">1 は `SERVICE_ERROR_NORMAL`を示します。</span><span class="sxs-lookup"><span data-stu-id="4b7df-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="4b7df-112">コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。</span><span class="sxs-lookup"><span data-stu-id="4b7df-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="4b7df-113">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="4b7df-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="4b7df-114">**終了コード**</span><span class="sxs-lookup"><span data-stu-id="4b7df-114">**Exit Code**</span></span>  
 <span data-ttu-id="4b7df-115">エラーが発生した場合は、エラー番号がこのボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="4b7df-116">その番号を手掛かりにして障害のトラブルシューティングを行ってください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報でその番号を検索することも、技術サポート スタッフにその番号を連絡することも可能です。</span><span class="sxs-lookup"><span data-stu-id="4b7df-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="4b7df-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="4b7df-117">**Host Name**</span></span>  
 <span data-ttu-id="4b7df-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを実行しているコンピューターまたはクラスターの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-118">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="4b7df-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="4b7df-119">**Name**</span></span>  
 <span data-ttu-id="4b7df-120">サービスの表示名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="4b7df-121">**プロセス ID**</span><span class="sxs-lookup"><span data-stu-id="4b7df-121">**Process ID**</span></span>  
 <span data-ttu-id="4b7df-122">Windows プロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="4b7df-123">**[SQL サービスの種類]**</span><span class="sxs-lookup"><span data-stu-id="4b7df-123">**SQL Service Type**</span></span>  
 <span data-ttu-id="4b7df-124">呼び出し側プロセスに提供されるサービスの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4b7df-125">では、いくつかのサービスがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-125">installs several services.</span></span>  
  
 <span data-ttu-id="4b7df-126">**[開始モード]**</span><span class="sxs-lookup"><span data-stu-id="4b7df-126">**Start Mode**</span></span>  
 <span data-ttu-id="4b7df-127">このサービスを以下のいずれかのモードに設定します。</span><span class="sxs-lookup"><span data-stu-id="4b7df-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="4b7df-128">手動: このサービスは、コンピューターの起動時に自動的に開始しません。</span><span class="sxs-lookup"><span data-stu-id="4b7df-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="4b7df-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b7df-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="4b7df-130">\[自動]: このサービスは、コンピューターの起動時に開始を試みます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="4b7df-131">\[無効]: このサービスは開始できません。</span><span class="sxs-lookup"><span data-stu-id="4b7df-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="4b7df-132">**State**</span><span class="sxs-lookup"><span data-stu-id="4b7df-132">**State**</span></span>  
 <span data-ttu-id="4b7df-133">このサービスが実行中か、停止しているか、無効になっているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b7df-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="4b7df-134">" **...** " の場合は、状態の変更が保留になっています。</span><span class="sxs-lookup"><span data-stu-id="4b7df-134">"**...**" indicates a state change is pending.</span></span>  
  
  
