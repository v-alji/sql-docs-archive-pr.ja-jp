---
title: SQL Server のプロパティ ([サービス] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e4ae0c6b-6fd8-4325-b54e-1758fc659958
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5822a02d5631e0d0e9318b20a1dcee87b8a4ded1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740632"
---
# <a name="sql-server-properties-service-tab"></a><span data-ttu-id="ec598-102">[SQL Server のプロパティ] ダイアログ ボックス ([サービス] タブ)</span><span class="sxs-lookup"><span data-stu-id="ec598-102">SQL Server Properties (Service Tab)</span></span>
  <span data-ttu-id="ec598-103">**[MSSQLSERVER のプロパティ]** ダイアログ ボックスの **[サービス]** タブでは、以下のオプションの表示や指定を行います。</span><span class="sxs-lookup"><span data-stu-id="ec598-103">Use the **Service**tab on the **MSSQLSERVER Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ec598-104">オプション</span><span class="sxs-lookup"><span data-stu-id="ec598-104">Options</span></span>  
 <span data-ttu-id="ec598-105">**[バイナリ パス]**</span><span class="sxs-lookup"><span data-stu-id="ec598-105">**Binary Path**</span></span>  
 <span data-ttu-id="ec598-106">このサービスで使用するプログラム ファイルの場所を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ec598-106">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="ec598-107">**[エラー制御]**</span><span class="sxs-lookup"><span data-stu-id="ec598-107">**Error Control**</span></span>  
 <span data-ttu-id="ec598-108">1 は `SERVICE_ERROR_NORMAL`を示します。</span><span class="sxs-lookup"><span data-stu-id="ec598-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="ec598-109">コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。</span><span class="sxs-lookup"><span data-stu-id="ec598-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="ec598-110">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="ec598-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="ec598-111">**終了コード**</span><span class="sxs-lookup"><span data-stu-id="ec598-111">**Exit Code**</span></span>  
 <span data-ttu-id="ec598-112">エラーが発生した場合は、エラー番号がこのボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec598-112">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="ec598-113">その番号を手掛かりにして障害のトラブルシューティングを行ってください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報でその番号を検索することも、技術サポート スタッフにその番号を連絡することも可能です。</span><span class="sxs-lookup"><span data-stu-id="ec598-113">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="ec598-114">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="ec598-114">**Host Name**</span></span>  
 <span data-ttu-id="ec598-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを実行しているコンピューターまたはクラスターの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec598-115">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="ec598-116">**Name**</span><span class="sxs-lookup"><span data-stu-id="ec598-116">**Name**</span></span>  
 <span data-ttu-id="ec598-117">サービスの表示名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec598-117">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="ec598-118">**プロセス ID**</span><span class="sxs-lookup"><span data-stu-id="ec598-118">**Process ID**</span></span>  
 <span data-ttu-id="ec598-119">Windows プロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec598-119">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="ec598-120">**[サービスの種類]**</span><span class="sxs-lookup"><span data-stu-id="ec598-120">**Service Type**</span></span>  
 <span data-ttu-id="ec598-121">呼び出し側プロセスに提供されるサービスの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec598-121">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ec598-122">では、いくつかのサービスがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ec598-122">installs several services.</span></span>  
  
 <span data-ttu-id="ec598-123">**[開始モード]**</span><span class="sxs-lookup"><span data-stu-id="ec598-123">**Start Mode**</span></span>  
 <span data-ttu-id="ec598-124">このサービスを以下のいずれかのモードに設定します。</span><span class="sxs-lookup"><span data-stu-id="ec598-124">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="ec598-125">手動: このサービスは、コンピューターの起動時に自動的に開始しません。</span><span class="sxs-lookup"><span data-stu-id="ec598-125">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="ec598-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec598-126">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="ec598-127">\[自動]: このサービスは、コンピューターの起動時に開始を試みます。</span><span class="sxs-lookup"><span data-stu-id="ec598-127">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="ec598-128">\[無効]: このサービスは開始できません。</span><span class="sxs-lookup"><span data-stu-id="ec598-128">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="ec598-129">**State**</span><span class="sxs-lookup"><span data-stu-id="ec598-129">**State**</span></span>  
 <span data-ttu-id="ec598-130">このサービスが実行中か、停止しているか、無効になっているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec598-130">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="ec598-131">" **...** " の場合は、状態の変更が保留になっています。</span><span class="sxs-lookup"><span data-stu-id="ec598-131">"**...**" indicates a state change is pending.</span></span>  
  
  
