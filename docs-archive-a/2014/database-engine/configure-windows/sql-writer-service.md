---
title: SQL ライター サービス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- VDI [SQL Server]
- restoring [SQL Server], SQL Writer Service
- backups [SQL Server], while SQL Server running
- Volume Shadow Copy Service
- volume backups while running [SQL Server]
- Virtual Backup Device Interface [SQL Server]
- SQL Writer Service
- services [SQL Server], SQL Writer
- MSDE Writer
- VSS
ms.assetid: 0f299867-f499-4c2a-ad6f-b2ef1869381d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 310722c6617c7a2c9e0f384ec23ae371ab230536
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632092"
---
# <a name="sql-writer-service"></a><span data-ttu-id="e0b2c-102">SQL ライター サービス</span><span class="sxs-lookup"><span data-stu-id="e0b2c-102">SQL Writer Service</span></span>
  <span data-ttu-id="e0b2c-103">SQL ライター サービスは、ボリューム シャドウ コピー サービス フレームワークを通じて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップと復元に関する追加機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-103">The SQL Writer Service provides added functionality for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the Volume Shadow Copy Service framework.</span></span>  
  
 <span data-ttu-id="e0b2c-104">SQL ライター サービスは、自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-104">The SQL Writer Service is installed automatically.</span></span> <span data-ttu-id="e0b2c-105">SQL ライター サービスは、ボリューム シャドウ コピー サービス (VSS) アプリケーションがバックアップまたは復元を要求したときに動作している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-105">It must be running when the Volume Shadow Copy Service (VSS) application requests a backup or restore.</span></span> <span data-ttu-id="e0b2c-106">SQL ライター サービスを構成するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービス アプレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-106">To configure the service, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services applet.</span></span> <span data-ttu-id="e0b2c-107">SQL ライター サービスは、すべてのオペレーティング システムにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-107">The SQL Writer Service installs on all operating systems.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="e0b2c-108">目的</span><span class="sxs-lookup"><span data-stu-id="e0b2c-108">Purpose</span></span>  
 <span data-ttu-id="e0b2c-109">SQL ライター サービスが実行されている場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はデータ ファイルをロックして排他アクセス権を取得します。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-109">When running, [!INCLUDE[ssDE](../../includes/ssde-md.md)] locks and has exclusive access to the data files.</span></span> <span data-ttu-id="e0b2c-110">SQL ライター サービスが実行されていない場合、Windows で実行中のバックアップ プログラムはデータ ファイルにアクセスできないため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップ機能を使用してバックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-110">When the SQL Writer Service is not running, backup programs running in Windows do not have access to the data files, and backups must be performed using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup.</span></span>  
  
 <span data-ttu-id="e0b2c-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の実行中に Windows のバックアップ プログラムが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ファイルをコピーできるようにするには、SQL ライター サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-111">Use the SQL Writer Service to permit Windows backup programs to copy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
## <a name="volume-shadow-copy-service"></a><span data-ttu-id="e0b2c-112">ボリューム シャドウ コピー サービス</span><span class="sxs-lookup"><span data-stu-id="e0b2c-112">Volume Shadow Copy Service</span></span>  
 <span data-ttu-id="e0b2c-113">VSS は、システム上のアプリケーションがボリュームへの書き込みを続行している間に、ボリューム バックアップを実行できるようにするためのフレームワークとなる COM API セットです。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-113">The VSS is a set of COM APIs that implements a framework to allow volume backups to be performed while applications on a system continue to write to the volumes.</span></span> <span data-ttu-id="e0b2c-114">VSS には、一貫性のあるインターフェイスが用意されており、ディスク上のデータを更新するユーザー アプリケーション (ライター) とアプリケーションをバックアップするユーザー アプリケーション (リクエスター) 間の連携が可能になります。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-114">The VSS provides a consistent interface that allows coordination between user applications that update data on disk (writers) and those that back up applications (requestors).</span></span>  
  
 <span data-ttu-id="e0b2c-115">VSS は、実行中のシステム (特にサーバー) で提供されているサービスのパフォーマンスや安定性を必要以上に低下させることなく、これらのシステム上で安定したバックアップ イメージをキャプチャしてコピーします。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-115">The VSS captures and copies stable images for backup on running systems, particularly servers, without unduly degrading the performance and stability of the services they provide.</span></span> <span data-ttu-id="e0b2c-116">VSS の詳細については、Windows ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-116">For more information on the VSS, see your Windows documentation.</span></span>  
  
## <a name="virtual-backup-device-interface-vdi"></a><span data-ttu-id="e0b2c-117">Virtual Backup Device Interface (VDI)</span><span class="sxs-lookup"><span data-stu-id="e0b2c-117">Virtual Backup Device Interface (VDI)</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e0b2c-118">には、Virtual Backup Device Interface (VDI) と呼ばれる API が用意されています。これにより、独立系ソフトウェア ベンダーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を独自の製品に統合して、バックアップおよび復元操作のサポートを提供できます。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-118">provides an API called Virtual Backup Device Interface (VDI) that enables independent software vendors to integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into their products for providing support for backup and restore operations.</span></span> <span data-ttu-id="e0b2c-119">これらの API は、最高の信頼性とパフォーマンスを提供するほか、ホット バックアップ機能やスナップショット バックアップ機能など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のあらゆるバックアップおよび復元機能をサポートするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-119">These APIs are engineered to provide maximum reliability and performance, and support the full range of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore functionality, including the full range of hot and snapshot backup capabilities.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="e0b2c-120">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="e0b2c-120">Permissions</span></span>  
 <span data-ttu-id="e0b2c-121">SQL ライター サービスは、 **ローカル システム** アカウントで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-121">The SQL Writer service must run under the **Local System** account.</span></span> <span data-ttu-id="e0b2c-122">SQL ライター サービスは、 **に接続するために** NT Service\SQLWriter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインを使用します。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-122">The SQL Writer service uses the **NT Service\SQLWriter** login to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0b2c-123">**NT Service\SQLWriter** ログインを使用すると、SQL ライター プロセスは **ログインなし**と指定されたアカウントを通じた低い特権レベルで実行され、その結果、脆弱性を制限することになります。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-123">Using the **NT Service\SQLWriter** login allows the SQL Writer process to run at a lower privilege level in an account designated as **no login**, which limits vulnerability.</span></span> <span data-ttu-id="e0b2c-124">SQL ライター サービスが無効になっている場合は、System Center Data Protection Manager や他のいくつかのサード パーティ製品のように VSS スナップショットに依存する任意のユーティリティは動作に失敗するか、より悪い場合は、一貫性のないデータベースのバックアップを取得するリスクが生じます。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-124">If the SQL Writer service is disabled, then any utility which in relies on VSS snapshots, such as System Center Data Protection Manager, as well as some other 3rd-party products, would be broken, or worse, at risk of taking backups of databases which were not consistent.</span></span> <span data-ttu-id="e0b2c-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行するシステムと、ホスト システム (仮想マシンの場合) のどちらも、 [!INCLUDE[tsql](../../includes/tsql-md.md)] によるバックアップのみを必要とし、それ以外のバックアップを何も必要としない場合は、SQL ライター サービスを無効にしてログインを削除しても安全です。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-125">If neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the system it runs on, nor the host system (in the event of a virtual machine), need to use anything besides [!INCLUDE[tsql](../../includes/tsql-md.md)] backup, then the SQL Writer service can be safely disabled and the login removed.</span></span>  <span data-ttu-id="e0b2c-126">バックアップが直接的なスナップショット ベースであるかどうかにかかわりなく、SQL ライター サービスはシステム レベルとボリューム レベルどちらのバックアップからも開始できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-126">Note that the SQL Writer service may be invoked by a system or volume level backup, whether the backup is directly snapshot-based or not.</span></span> <span data-ttu-id="e0b2c-127">いくつかのシステム バックアップ製品は、開いているファイルやロックされているファイルがブロックされることを防止するために VSS を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-127">Some system backup products use VSS to avoid being blocked by open or locked files.</span></span> <span data-ttu-id="e0b2c-128">SQL ライター サービスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのすべての I/O を短時間にわたって停止するため、自らが動作する目的で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内で昇格された権限を必要とします。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-128">The SQL Writer service needs elevated permissions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because in the course of its activities it briefly freezes all I/O for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="features"></a><span data-ttu-id="e0b2c-129">特徴</span><span class="sxs-lookup"><span data-stu-id="e0b2c-129">Features</span></span>  
 <span data-ttu-id="e0b2c-130">SQL ライターは次の機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-130">SQL Writer supports:</span></span>  
  
-   <span data-ttu-id="e0b2c-131">フルテキスト カタログなど、データベースの完全バックアップおよび復元</span><span class="sxs-lookup"><span data-stu-id="e0b2c-131">Full database backup and restore including full-text catalogs</span></span>  
  
-   <span data-ttu-id="e0b2c-132">差分バックアップおよび復元</span><span class="sxs-lookup"><span data-stu-id="e0b2c-132">Differential backup and restore</span></span>  
  
-   <span data-ttu-id="e0b2c-133">移動を伴う復元</span><span class="sxs-lookup"><span data-stu-id="e0b2c-133">Restore with move</span></span>  
  
-   <span data-ttu-id="e0b2c-134">データベースの名前変更</span><span class="sxs-lookup"><span data-stu-id="e0b2c-134">Database rename</span></span>  
  
-   <span data-ttu-id="e0b2c-135">コピーのみのバックアップ</span><span class="sxs-lookup"><span data-stu-id="e0b2c-135">Copy-only backup</span></span>  
  
-   <span data-ttu-id="e0b2c-136">データベース スナップショットの自動復旧</span><span class="sxs-lookup"><span data-stu-id="e0b2c-136">Auto-recovery of database snapshot</span></span>  
  
 <span data-ttu-id="e0b2c-137">SQL ライターは次の機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e0b2c-137">SQL Writer does not support:</span></span>  
  
-   <span data-ttu-id="e0b2c-138">ログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="e0b2c-138">Log backups</span></span>  
  
-   <span data-ttu-id="e0b2c-139">ファイルとファイル グループのバックアップ</span><span class="sxs-lookup"><span data-stu-id="e0b2c-139">File and filegroup backup</span></span>  
  
-   <span data-ttu-id="e0b2c-140">ページ復元</span><span class="sxs-lookup"><span data-stu-id="e0b2c-140">Page restore</span></span>  
  
  
