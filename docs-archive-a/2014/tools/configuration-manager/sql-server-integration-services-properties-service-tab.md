---
title: '[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([サービス] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: stevestein
ms.author: sstein
ms.openlocfilehash: a752bdeab3c99ac97445e3281d3165a2d8f79866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644719"
---
# <a name="sql-server-integration-services-properties-service-tab"></a><span data-ttu-id="7f91c-102">[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([サービス] タブ)</span><span class="sxs-lookup"><span data-stu-id="7f91c-102">SQL Server Integration Services Properties (Service Tab)</span></span>
  <span data-ttu-id="7f91c-103">[[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  **のプロパティ]** ダイアログ ボックスの **[サービス]** タブでは、以下のオプションの表示や指定を行います。</span><span class="sxs-lookup"><span data-stu-id="7f91c-103">Use the **Service**tab on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f91c-104">Options</span><span class="sxs-lookup"><span data-stu-id="7f91c-104">Options</span></span>  
 <span data-ttu-id="7f91c-105">**[バイナリ パス]**</span><span class="sxs-lookup"><span data-stu-id="7f91c-105">**Binary Path**</span></span>  
 <span data-ttu-id="7f91c-106">このサービスが使用するプログラム ファイルの場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-106">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="7f91c-107">**[エラー制御]**</span><span class="sxs-lookup"><span data-stu-id="7f91c-107">**Error Control**</span></span>  
 <span data-ttu-id="7f91c-108">1 は `SERVICE_ERROR_NORMAL`を示します。</span><span class="sxs-lookup"><span data-stu-id="7f91c-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="7f91c-109">コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。</span><span class="sxs-lookup"><span data-stu-id="7f91c-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="7f91c-110">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="7f91c-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="7f91c-111">**終了コード**</span><span class="sxs-lookup"><span data-stu-id="7f91c-111">**Exit Code**</span></span>  
 <span data-ttu-id="7f91c-112">このサービスの開始時または停止時に検出された問題を定義する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows エラー コードです。</span><span class="sxs-lookup"><span data-stu-id="7f91c-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows error code defining any problems encountered in starting or stopping the service.</span></span> <span data-ttu-id="7f91c-113">このクラスで表されるサービスに固有のエラーが検出されると、このプロパティは **ERROR_SERVICE_SPECIFIC_ERROR** (1066) に設定され、そのエラーに関する情報は、 **ServiceSpecificExitCode** プロパティで利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7f91c-113">This property is set to **ERROR_SERVICE_SPECIFIC_ERROR** (1066) when the error is unique to the service represented by this class, and information about the error is available in the **ServiceSpecificExitCode** property.</span></span> <span data-ttu-id="7f91c-114">この値は、実行中と正常終了時には NO_ERROR (0) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-114">The service sets this value to NO_ERROR (0) when running, and again upon normal termination.</span></span>  
  
 <span data-ttu-id="7f91c-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="7f91c-115">**Host Name**</span></span>  
 <span data-ttu-id="7f91c-116">[!INCLUDE[ssIS](../../includes/ssis-md.md)] サービスを実行しているコンピューターまたはクラスターの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-116">Displays the name of the computer or cluster running the [!INCLUDE[ssIS](../../includes/ssis-md.md)] service.</span></span>  
  
 <span data-ttu-id="7f91c-117">**名前**</span><span class="sxs-lookup"><span data-stu-id="7f91c-117">**Name**</span></span>  
 <span data-ttu-id="7f91c-118">サービスの表示名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="7f91c-119">**プロセス ID**</span><span class="sxs-lookup"><span data-stu-id="7f91c-119">**Process ID**</span></span>  
 <span data-ttu-id="7f91c-120">Windows プロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-120">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="7f91c-121">**[SQL サービスの種類]**</span><span class="sxs-lookup"><span data-stu-id="7f91c-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="7f91c-122">呼び出し側プロセスに提供されるサービスの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-122">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="7f91c-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、いくつかのサービスがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="7f91c-124">**[開始モード]**</span><span class="sxs-lookup"><span data-stu-id="7f91c-124">**Start Mode**</span></span>  
 <span data-ttu-id="7f91c-125">このサービスを以下のいずれかのモードに設定します。</span><span class="sxs-lookup"><span data-stu-id="7f91c-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="7f91c-126">手動: このサービスは、コンピューターの起動時に自動的に開始されません。</span><span class="sxs-lookup"><span data-stu-id="7f91c-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="7f91c-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f91c-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="7f91c-128">自動:コンピューターの起動時に、このサービスの開始が試みられます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="7f91c-129">無効:このサービスを開始できません。</span><span class="sxs-lookup"><span data-stu-id="7f91c-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="7f91c-130">**State**</span><span class="sxs-lookup"><span data-stu-id="7f91c-130">**State**</span></span>  
 <span data-ttu-id="7f91c-131">このサービスが実行中か、停止しているか、無効になっているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f91c-131">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="7f91c-132">" **...** " の場合は、状態の変更が保留になっています。</span><span class="sxs-lookup"><span data-stu-id="7f91c-132">"**...**" indicates a state change is pending.</span></span>  
  
  
