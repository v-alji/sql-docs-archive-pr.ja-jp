---
title: レポート サーバーのプロパティ ([サービス] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2a2e1dbf-02b9-4893-aaf0-c0e4a2c9b4f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d223234e5f53eb087650d0634eb09b520cd21e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642429"
---
# <a name="report-server-properties-service-tab"></a><span data-ttu-id="cdbf7-102">[SQL Server Reporting Services のプロパティ] ダイアログ ボックス ([サービス] タブ)</span><span class="sxs-lookup"><span data-stu-id="cdbf7-102">Report Server Properties (Service Tab)</span></span>
  <span data-ttu-id="cdbf7-103">このサービスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のレポート サーバー サービスです。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server service.</span></span> <span data-ttu-id="cdbf7-104">グレー表示になっているプロパティ値をこのアプリケーションで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-104">The property values in light gray cannot be changed by using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cdbf7-105">オプション</span><span class="sxs-lookup"><span data-stu-id="cdbf7-105">Options</span></span>  
 <span data-ttu-id="cdbf7-106">**[バイナリ パス]**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-106">**Binary Path**</span></span>  
 <span data-ttu-id="cdbf7-107">このサービスが使用するプログラム ファイルの場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-107">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="cdbf7-108">**[エラー制御]**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-108">**Error Control**</span></span>  
 <span data-ttu-id="cdbf7-109">1 は、"SERVICE_ERROR_NORMAL" を示します。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-109">1 indicates "SERVICE_ERROR_NORMAL".</span></span> <span data-ttu-id="cdbf7-110">コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-110">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="cdbf7-111">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-111">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="cdbf7-112">**終了コード**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-112">**Exit Code**</span></span>  
 <span data-ttu-id="cdbf7-113">エラーが発生した場合は、エラー番号がこのボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-113">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="cdbf7-114">その番号を手掛かりにして障害のトラブルシューティングを行ってください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報でその番号を検索することも、技術サポート スタッフにその番号を連絡することも可能です。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-114">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="cdbf7-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-115">**Host Name**</span></span>  
 <span data-ttu-id="cdbf7-116">フルテキスト検索を実行しているコンピューターまたはクラスターの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-116">Displays the name of the computer or cluster running the full text search.</span></span>  
  
 <span data-ttu-id="cdbf7-117">**Name**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-117">**Name**</span></span>  
 <span data-ttu-id="cdbf7-118">サービスの表示名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="cdbf7-119">**プロセス ID**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-119">**Process ID**</span></span>  
 <span data-ttu-id="cdbf7-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows プロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-120">Displays the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows process ID.</span></span>  
  
 <span data-ttu-id="cdbf7-121">**[SQL サービスの種類]**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="cdbf7-122">呼び出し側プロセスに提供されるサービスの種類です。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-122">Type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cdbf7-123">では、いくつかのサービスがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-123">installs several services.</span></span>  
  
 <span data-ttu-id="cdbf7-124">**[開始モード]**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-124">**Start Mode**</span></span>  
 <span data-ttu-id="cdbf7-125">このサービスを以下のいずれかのモードに設定します。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="cdbf7-126">手動: このサービスは、コンピューターの起動時に自動的に開始しません。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="cdbf7-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="cdbf7-128">\[自動]: このサービスは、コンピューターの起動時に開始を試みます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="cdbf7-129">\[無効]: このサービスは開始できません。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="cdbf7-130">**State**</span><span class="sxs-lookup"><span data-stu-id="cdbf7-130">**State**</span></span>  
 <span data-ttu-id="cdbf7-131">このサービスが実行中か、停止しているか、無効になっているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-131">Indicates whether this service is running, stopped, or disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbf7-132">参照</span><span class="sxs-lookup"><span data-stu-id="cdbf7-132">See Also</span></span>  
 [<span data-ttu-id="cdbf7-133">SQL Server のサービス</span><span class="sxs-lookup"><span data-stu-id="cdbf7-133">SQL Server Services</span></span>](../../../2014/tools/configuration-manager/sql-server-services.md)  
  
  
