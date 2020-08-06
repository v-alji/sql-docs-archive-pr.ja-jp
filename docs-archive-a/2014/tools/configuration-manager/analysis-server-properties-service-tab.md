---
title: 分析サーバーのプロパティ ([サービス] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91200120d87224c8e7733b0ff41ed423d3086c34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741510"
---
# <a name="analysis-server-properties-service-tab"></a><span data-ttu-id="a7e2f-102">[SQL Server Analysis Services のプロパティ] ダイアログ ボックス ([サービス] タブ)</span><span class="sxs-lookup"><span data-stu-id="a7e2f-102">Analysis Server Properties (Service Tab)</span></span>
  <span data-ttu-id="a7e2f-103">このサービスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a7e2f-104">[!INCLUDE[ssAS](../../includes/ssas-md.md)] を正しく機能させるには、このサービスを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-104">This service must be running for [!INCLUDE[ssAS](../../includes/ssas-md.md)] to work properly.</span></span> <span data-ttu-id="a7e2f-105">グレー表示になっているプロパティ値をこのアプリケーションで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-105">The property values in light gray cannot be changed using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7e2f-106">オプション</span><span class="sxs-lookup"><span data-stu-id="a7e2f-106">Options</span></span>  
 <span data-ttu-id="a7e2f-107">**[バイナリ パス]**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-107">**Binary Path**</span></span>  
 <span data-ttu-id="a7e2f-108">このサービスが使用するプログラム ファイルの場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-108">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="a7e2f-109">**[エラー制御]**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-109">**Error Control**</span></span>  
 <span data-ttu-id="a7e2f-110">1 は `SERVICE_ERROR_NORMAL`を示します。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-110">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="a7e2f-111">コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-111">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="a7e2f-112">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-112">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="a7e2f-113">**終了コード**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-113">**Exit Code**</span></span>  
 <span data-ttu-id="a7e2f-114">エラーが発生した場合は、エラー番号がこのボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-114">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="a7e2f-115">その番号を手掛かりにして障害のトラブルシューティングを行ってください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報でその番号を検索することも、技術サポート スタッフにその番号を連絡することも可能です。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-115">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="a7e2f-116">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-116">**Host Name**</span></span>  
 <span data-ttu-id="a7e2f-117">[!INCLUDE[ssAS](../../includes/ssas-md.md)]を実行しているコンピューターまたはクラスターの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-117">Displays the name of the computer or cluster running [!INCLUDE[ssAS](../../includes/ssas-md.md)].</span></span>  
  
 <span data-ttu-id="a7e2f-118">**Name**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-118">**Name**</span></span>  
 <span data-ttu-id="a7e2f-119">サービスの表示名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-119">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="a7e2f-120">**プロセス ID**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-120">**Process ID**</span></span>  
 <span data-ttu-id="a7e2f-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows がこのプログラムのプロセスを追跡するために使用する番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-121">Displays the number used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows to keep track of this program's processes.</span></span>  
  
 <span data-ttu-id="a7e2f-122">**[SQL サービスの種類]**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-122">**SQL Service Type**</span></span>  
 <span data-ttu-id="a7e2f-123">呼び出し側プロセスに提供されるサービスの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-123">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a7e2f-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、いくつかのサービスがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="a7e2f-125">**[開始モード]**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-125">**Start Mode**</span></span>  
 <span data-ttu-id="a7e2f-126">このサービスを以下のいずれかのモードに設定します。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-126">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="a7e2f-127">手動: このサービスは、コンピューターの起動時に自動的に開始しません。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-127">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="a7e2f-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-128">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="a7e2f-129">\[自動]: このサービスは、コンピューターの起動時に開始を試みます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-129">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="a7e2f-130">\[無効]: このサービスは開始できません。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-130">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="a7e2f-131">**State**</span><span class="sxs-lookup"><span data-stu-id="a7e2f-131">**State**</span></span>  
 <span data-ttu-id="a7e2f-132">このサービスが実行中か、停止しているか、無効になっているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e2f-132">Indicates whether this service is running, stopped, or disabled.</span></span>  
  
  
