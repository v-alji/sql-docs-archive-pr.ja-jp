---
title: SQL Server 構成マネージャーのヘルプ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10a6d6052fe109892f975774a1ed65b818ef0581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737302"
---
# <a name="sql-server-configuration-manager-help"></a><span data-ttu-id="5f437-102">SQL Server 構成マネージャーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="5f437-102">SQL Server Configuration Manager Help</span></span>
  <span data-ttu-id="5f437-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種サービスやネットワーク接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="5f437-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and configure network connectivity.</span></span> <span data-ttu-id="5f437-104">データベース オブジェクトの作成または管理、セキュリティの構成、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリの作成には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f437-104">To create or manage database objects, configure security, and write [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5f437-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f437-105">For more information about [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="5f437-106">ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの各ダイアログ ボックスの F1 ヘルプ トピックについて紹介します。</span><span class="sxs-lookup"><span data-stu-id="5f437-106">This section contains the F1 Help topics for the dialogs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f437-107">構成マネージャーで [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] よりも前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="5f437-107">Configuration Manager cannot configure versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="services"></a><span data-ttu-id="5f437-108">サービス</span><span class="sxs-lookup"><span data-stu-id="5f437-108">Services</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f437-109">構成マネージャーでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に関連する各種サービスを管理します。</span><span class="sxs-lookup"><span data-stu-id="5f437-109">Configuration Manager manages services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5f437-110">これらのタスクの多くは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の [サービス] ダイアログ ボックスからも実行できますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、管理対象のサービスに関して追加の操作を実行できます。たとえば、サービス アカウントの変更時に正しい権限を適用することなどが可能です。</span><span class="sxs-lookup"><span data-stu-id="5f437-110">Although many of these tasks can be accomplished using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services dialog, is important to note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager performs additional operations on the services it manages, such as applying the correct permissions when the service account is changed.</span></span> <span data-ttu-id="5f437-111">また、Windows の通常の [サービス] ダイアログ ボックスから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種サービスを構成すると、そのサービスが正しく機能しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="5f437-111">Using the normal Windows Services dialog to configure any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services might cause the service to malfunction.</span></span>  
  
 <span data-ttu-id="5f437-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、各種サービスに関する以下のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5f437-112">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks for services:</span></span>  
  
-   <span data-ttu-id="5f437-113">サービスの開始、停止、一時停止</span><span class="sxs-lookup"><span data-stu-id="5f437-113">Start, stop, and pause services</span></span>  
  
-   <span data-ttu-id="5f437-114">サービスの開始を自動にするか手動にするかの構成、サービスの無効化、サービスの他の設定の変更</span><span class="sxs-lookup"><span data-stu-id="5f437-114">Configure services to start automatically or manually, disable the services, or change other service settings</span></span>  
  
-   <span data-ttu-id="5f437-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種サービスが使用するアカウントのパスワードの変更</span><span class="sxs-lookup"><span data-stu-id="5f437-115">Change the passwords for the accounts used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services</span></span>  
  
-   <span data-ttu-id="5f437-116">トレース フラグ (コマンド ライン パラメーター) を使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の開始</span><span class="sxs-lookup"><span data-stu-id="5f437-116">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using trace flags (command line parameters)</span></span>  
  
-   <span data-ttu-id="5f437-117">サービスのプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="5f437-117">View the properties of services</span></span>  
  
## <a name="sql-server-network-configuration"></a><span data-ttu-id="5f437-118">SQL Server のネットワーク構成</span><span class="sxs-lookup"><span data-stu-id="5f437-118">SQL Server Network Configuration</span></span>  
 <span data-ttu-id="5f437-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、このコンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種サービスに関する以下のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5f437-119">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on this computer:</span></span>  
  
-   <span data-ttu-id="5f437-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="5f437-120">Enable or disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
-   <span data-ttu-id="5f437-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワーク プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="5f437-121">Configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f437-122">プロトコルを構成して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に接続する方法に関する簡単なチュートリアルについては、「 [チュートリアル:データベース エンジンの概要](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f437-122">For a short tutorial about how to configure protocols and connect to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see [Tutorial: Getting Started with the Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).</span></span>  
  
## <a name="sql-server-native-client-configuration"></a><span data-ttu-id="5f437-123">SQL Server Native Client の構成</span><span class="sxs-lookup"><span data-stu-id="5f437-123">SQL Server Native Client Configuration</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f437-124">クライアントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ネットワーク ライブラリを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="5f437-124">clients connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client network library.</span></span> <span data-ttu-id="5f437-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、このコンピューター上のクライアント アプリケーションに関する以下のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5f437-125">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to client applications on this computer:</span></span>  
  
-   <span data-ttu-id="5f437-126">このコンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント アプリケーションに関して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続するときのプロトコルの順序を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f437-126">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications on this computer, specify the protocol order, when connecting to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5f437-127">クライアント接続プロトコルを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5f437-127">Configure client connection protocols.</span></span>  
  
-   <span data-ttu-id="5f437-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント アプリケーションに関して、クライアントからカスタム接続文字列を使用して接続するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの別名を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5f437-128">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications, create aliases for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so that clients can connect using a custom connection string.</span></span>  
  
 <span data-ttu-id="5f437-129">各タスクの詳細については、各タスクに関する F1 ヘルプを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f437-129">For more information about each of these tasks, see F1 help for each task.</span></span>  
  
#### <a name="to-open-sql-server-configuration-manager"></a><span data-ttu-id="5f437-130">構成マネージャーを開くには、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5f437-130">To open SQL Server Configuration Manager</span></span>  
  
-   <span data-ttu-id="5f437-131">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]** (バージョン)、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f437-131">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server** (version), point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f437-132">参照</span><span class="sxs-lookup"><span data-stu-id="5f437-132">See Also</span></span>  
 <span data-ttu-id="5f437-133">[SQL Server サービス](../../../2014/tools/configuration-manager/sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="5f437-133">[SQL Server Services](../../../2014/tools/configuration-manager/sql-server-services.md) </span></span>  
 <span data-ttu-id="5f437-134">[ネットワーク構成の SQL Server](sql-server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5f437-134">[SQL Server Network Configuration](sql-server-network-configuration.md) </span></span>  
 <span data-ttu-id="5f437-135">[SQL Native Client 11.0 構成](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5f437-135">[SQL Native Client 11.0 Configuration](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span></span>  
 [<span data-ttu-id="5f437-136">ネットワーク プロトコルの選択</span><span class="sxs-lookup"><span data-stu-id="5f437-136">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
