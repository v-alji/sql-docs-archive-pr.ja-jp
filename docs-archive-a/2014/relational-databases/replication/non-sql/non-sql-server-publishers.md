---
title: SQL Server 以外のパブリッシャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f15f07dbf294d697afd385318f3dbf1447c8e2d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631810"
---
# <a name="non-sql-server-publishers"></a><span data-ttu-id="219ac-102">SQL Server 以外のパブリッシャー</span><span class="sxs-lookup"><span data-stu-id="219ac-102">Non-SQL Server Publishers</span></span>
  <span data-ttu-id="219ac-103">以外のソースからデータ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をパブリッシュすると、でデータを統合でき [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="219ac-103">Publishing data from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sources allows you to consolidate data in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="219ac-104">は、Oracle データベースからパブリッシュされたスナップショット データまたはトランザクション データをサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="219ac-104">can subscribe to snapshot or transactional data published from an Oracle database.</span></span> <span data-ttu-id="219ac-105">Oracle からのパブリッシュの詳細については、「[Oracle Publishing Overview](oracle-publishing-overview.md)」 (Oracle パブリッシングの概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="219ac-105">For more information about publishing from Oracle, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="219ac-106">SQL Server 以外のサブスクライバーへの異種レプリケーションは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="219ac-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="219ac-107">Oracle パブリッシングは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="219ac-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="219ac-108">データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="219ac-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="219ac-109">以下のような場合には、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースからのパブリッシュが理想的です。</span><span class="sxs-lookup"><span data-stu-id="219ac-109">Publishing from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="219ac-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="219ac-110">Scenario</span></span>|<span data-ttu-id="219ac-111">説明</span><span class="sxs-lookup"><span data-stu-id="219ac-111">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="219ac-112">.NET Framework アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="219ac-112">.NET Framework application deployments</span></span>|<span data-ttu-id="219ac-113">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 以外のデータベースからレプリケートされたデータを使用しながら、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio および[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用して開発します。</span><span class="sxs-lookup"><span data-stu-id="219ac-113">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="219ac-114">データ ウェアハウジング ステージング サーバー</span><span class="sxs-lookup"><span data-stu-id="219ac-114">Data warehousing staging servers</span></span>|<span data-ttu-id="219ac-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ステージング データベースと[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースとの同期を保ちます。</span><span class="sxs-lookup"><span data-stu-id="219ac-115">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="219ac-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="219ac-116">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="219ac-117">ソース システムの変更のレプリケーション中に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してアプリケーションをリアルタイムでテストします。</span><span class="sxs-lookup"><span data-stu-id="219ac-117">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="219ac-118">移行に問題がなければ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="219ac-118">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="219ac-119">参照</span><span class="sxs-lookup"><span data-stu-id="219ac-119">See Also</span></span>  
 [<span data-ttu-id="219ac-120">異種データベース レプリケーション</span><span class="sxs-lookup"><span data-stu-id="219ac-120">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
