---
title: lightweight pooling サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 549ff7451a31b48459b5a290b94ad406c3768a91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641863"
---
# <a name="lightweight-pooling-server-configuration-option"></a><span data-ttu-id="84794-102">lightweight pooling サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="84794-102">lightweight pooling Server Configuration Option</span></span>
  <span data-ttu-id="84794-103">**lightweight pooling** オプションは、SMP (symmetric multiprocessing) 環境で発生するコンテキストの過度の切り替えによるシステムのオーバーヘッドを削減する手段を提供する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="84794-103">Use the **lightweight pooling** option to provide a means of reducing the system overhead associated with the excessive context switching sometimes seen in symmetric multiprocessing (SMP) environments.</span></span> <span data-ttu-id="84794-104">コンテキストの過度の切り替えが発生した場合、簡易プーリングを使用してコンテキストの切り替えをインラインで行い、ユーザーまたはカーネルのリング遷移を削減することによって、スループットを向上できます。</span><span class="sxs-lookup"><span data-stu-id="84794-104">When excessive context switching is present, lightweight pooling can provide better throughput by performing the context switching inline, thus helping to reduce user/kernel ring transitions.</span></span>  
  
 <span data-ttu-id="84794-105">ファイバー モードは、UMS ワーカーのコンテキスト切り替えがパフォーマンスの重大なボトルネックになる状況を対象としています。</span><span class="sxs-lookup"><span data-stu-id="84794-105">Fiber mode is intended for certain situations in which the context switching of the UMS workers are the critical bottleneck in performance.</span></span> <span data-ttu-id="84794-106">この状況はまれであるため、一般的なシステムのパフォーマンスやスケーラビリティがファイバー モードで向上することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="84794-106">Because this is rare, fiber mode rarely enhances performance or scalability on the typical system.</span></span> <span data-ttu-id="84794-107">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] ではコンテキストの切り替えが改良されているため、ファイバー モードの必要性も少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="84794-107">Improved context switching in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] has also reduced the need for fiber mode.</span></span> <span data-ttu-id="84794-108">ルーチン処理にファイバー モード スケジューリングを使用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="84794-108">We do not recommend that you use fiber mode scheduling for routine operation.</span></span> <span data-ttu-id="84794-109">これは、コンテキストの切り替えがもたらす本来の利点が損なわれることでパフォーマンスが低下する場合があるためと、スレッド ローカル ストレージ (TLS) やスレッド所有オブジェクト (ミューテックス (Win32 カーネル オブジェクトの一種) など) を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部のコンポーネントがファイバー モードでは正常に機能しない場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="84794-109">This is because it can decrease performance by inhibiting the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a type of Win32 kernel object), cannot function correctly in fiber mode.</span></span>  
  
 <span data-ttu-id="84794-110">**lightweight pooling** を 1 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はファイバー モード スケジューリングに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="84794-110">Setting **lightweight pooling** to 1 causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to switch to fiber mode scheduling.</span></span> <span data-ttu-id="84794-111">このオプションの既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="84794-111">The default value for this option is 0.</span></span>  
  
 <span data-ttu-id="84794-112">**lightweight pooling** オプションは拡張オプションです。</span><span class="sxs-lookup"><span data-stu-id="84794-112">The **lightweight pooling** option is an advanced option.</span></span> <span data-ttu-id="84794-113">**sp_configure** システム ストアド プロシージャを使用して **lightweight pooling** の設定を変更するには、 **show advanced options** を 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84794-113">If you are using the **sp_configure** system stored procedure to change the setting, you can change **lightweight pooling** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="84794-114">この設定は、サーバーを再起動した後に有効になります。</span><span class="sxs-lookup"><span data-stu-id="84794-114">The setting takes effect after the server is restarted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84794-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 および [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP では、簡易プーリングはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="84794-115">Lightweight pooling is not supported for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP.</span></span> [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] <span data-ttu-id="84794-116">では、簡易プーリングが完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="84794-116">provides full support for lightweight pooling.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84794-117">簡易プーリングでは、共通言語ランタイム (CLR) の実行はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="84794-117">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="84794-118">"clr enabled" オプションまたは "lightweight pooling" オプションのいずれかを無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="84794-118">Disable one of two options: "clr enabled" or "lightweight pooling".</span></span> <span data-ttu-id="84794-119">CLR に依存していてファイバー モードで正しく動作しない機能には、Hierarchy データ型、レプリケーション、およびポリシー ベースの管理があります。</span><span class="sxs-lookup"><span data-stu-id="84794-119">Features that rely upon CLR and that do not work properly in fiber mode include the hierarchy data type, replication, and Policy-Based Management.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84794-120">参照</span><span class="sxs-lookup"><span data-stu-id="84794-120">See Also</span></span>  
 <span data-ttu-id="84794-121">[clr enabled サーバー構成オプション](clr-enabled-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="84794-121">[clr enabled Server Configuration Option](clr-enabled-server-configuration-option.md) </span></span>  
 <span data-ttu-id="84794-122">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="84794-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="84794-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84794-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="84794-124">clr enabled サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="84794-124">clr enabled Server Configuration Option</span></span>](clr-enabled-server-configuration-option.md)  
  
  
