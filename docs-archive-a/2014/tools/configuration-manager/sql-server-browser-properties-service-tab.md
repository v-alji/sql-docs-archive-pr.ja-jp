---
title: SQL Server Browser のプロパティ ([サービス] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 98ace9b0-72d5-4b72-9b7b-11fbc490981a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 200e45648b94e26c5e808e9a817cfe01866e6a65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632253"
---
# <a name="sql-server-browser-properties-service-tab"></a><span data-ttu-id="50f7b-102">[SQL Server Browser のプロパティ] ダイアログ ボックス ([サービス] タブ)</span><span class="sxs-lookup"><span data-stu-id="50f7b-102">SQL Server Browser Properties (Service Tab)</span></span>
  <span data-ttu-id="50f7b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser プログラムはサーバー上のサービスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="50f7b-104">Browser では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種リソースに関する着信要求を受信し、このコンピューター上にインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="50f7b-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 <span data-ttu-id="50f7b-105">**[SQL Server Browser のプロパティ]** ダイアログ ボックスの **[サービス]** タブでは、以下のオプションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-105">Use the **Service** tab on the **SQL Server Browser Properties** dialog box to view the following options.</span></span> <span data-ttu-id="50f7b-106">**[開始モード]** 以外のプロパティはすべて読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="50f7b-106">All properties except **Start Mode** are read-only.</span></span>  
  
## <a name="options"></a><span data-ttu-id="50f7b-107">オプション</span><span class="sxs-lookup"><span data-stu-id="50f7b-107">Options</span></span>  
 <span data-ttu-id="50f7b-108">**[バイナリ パス]**</span><span class="sxs-lookup"><span data-stu-id="50f7b-108">**Binary Path**</span></span>  
 <span data-ttu-id="50f7b-109">このサービスが使用するプログラム ファイルの場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-109">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="50f7b-110">**[エラー制御]**</span><span class="sxs-lookup"><span data-stu-id="50f7b-110">**Error Control**</span></span>  
 <span data-ttu-id="50f7b-111">1 は `SERVICE_ERROR_NORMAL`を示します。</span><span class="sxs-lookup"><span data-stu-id="50f7b-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="50f7b-112">コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。</span><span class="sxs-lookup"><span data-stu-id="50f7b-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="50f7b-113">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="50f7b-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="50f7b-114">**終了コード**</span><span class="sxs-lookup"><span data-stu-id="50f7b-114">**Exit Code**</span></span>  
 <span data-ttu-id="50f7b-115">エラーが発生した場合は、エラー番号がこのボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="50f7b-116">その番号を手掛かりにして障害のトラブルシューティングを行ってください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報でその番号を検索することも、技術サポート スタッフにその番号を連絡することも可能です。</span><span class="sxs-lookup"><span data-stu-id="50f7b-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="50f7b-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="50f7b-117">**Host Name**</span></span>  
 <span data-ttu-id="50f7b-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行しているコンピューターまたはクラスターの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-118">Displays the name of the computer or cluster running the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="50f7b-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="50f7b-119">**Name**</span></span>  
 <span data-ttu-id="50f7b-120">サービスの表示名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="50f7b-121">**プロセス ID**</span><span class="sxs-lookup"><span data-stu-id="50f7b-121">**Process ID**</span></span>  
 <span data-ttu-id="50f7b-122">Windows プロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="50f7b-123">**[サービスの種類]**</span><span class="sxs-lookup"><span data-stu-id="50f7b-123">**Service Type**</span></span>  
 <span data-ttu-id="50f7b-124">呼び出し側プロセスに提供されるサービスの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="50f7b-125">では、いくつかのサービスがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-125">installs several services.</span></span>  
  
 <span data-ttu-id="50f7b-126">**[開始モード]**</span><span class="sxs-lookup"><span data-stu-id="50f7b-126">**Start Mode**</span></span>  
 <span data-ttu-id="50f7b-127">このサービスを以下のいずれかのモードに設定します。</span><span class="sxs-lookup"><span data-stu-id="50f7b-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="50f7b-128">手動: このサービスは、コンピューターの起動時に自動的に開始しません。</span><span class="sxs-lookup"><span data-stu-id="50f7b-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="50f7b-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50f7b-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="50f7b-130">\[自動]: このサービスは、コンピューターの起動時に開始を試みます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="50f7b-131">\[無効]: このサービスは開始できません。</span><span class="sxs-lookup"><span data-stu-id="50f7b-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="50f7b-132">**State**</span><span class="sxs-lookup"><span data-stu-id="50f7b-132">**State**</span></span>  
 <span data-ttu-id="50f7b-133">このサービスが実行中か、停止しているか、無効になっているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7b-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="50f7b-134">" **...** " の場合は、状態の変更が保留になっています。</span><span class="sxs-lookup"><span data-stu-id="50f7b-134">"**...**" indicates a state change is pending.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f7b-135">参照</span><span class="sxs-lookup"><span data-stu-id="50f7b-135">See Also</span></span>  
 [<span data-ttu-id="50f7b-136">SQL Server Browser サービス</span><span class="sxs-lookup"><span data-stu-id="50f7b-136">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
