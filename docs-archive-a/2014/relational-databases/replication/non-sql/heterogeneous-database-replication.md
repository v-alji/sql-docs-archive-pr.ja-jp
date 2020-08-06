---
title: 異種データベース レプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8988a425bc9519d43b8100e4cd34418114edae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721308"
---
# <a name="heterogeneous-database-replication"></a><span data-ttu-id="a513b-102">異種データベース レプリケーション</span><span class="sxs-lookup"><span data-stu-id="a513b-102">Heterogeneous Database Replication</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a513b-103">は、トランザクション レプリケーションとスナップショット レプリケーションに対する次の異種シナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a513b-103">supports the following heterogeneous scenarios for transactional and snapshot replication:</span></span>  
  
-   <span data-ttu-id="a513b-104">Oracle から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]へのデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="a513b-104">Publishing data from Oracle to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a513b-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーへのデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="a513b-105">Publishing data from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="a513b-106">SQL Server 以外のサブスクライバーへの異種レプリケーションは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a513b-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="a513b-107">Oracle パブリッシングは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a513b-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="a513b-108">データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a513b-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a><span data-ttu-id="a513b-109">Oracle からのデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="a513b-109">Publishing Data from Oracle</span></span>  
 <span data-ttu-id="a513b-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] スナップショット レプリケーションとトランザクション レプリケーションとほぼ同じ機能を使用し、同様の使いやすさで Oracle からのデータをパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="a513b-110">You can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to publish data from Oracle with most of the same features and ease-of-use as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot and transactional replication.</span></span> <span data-ttu-id="a513b-111">Oracle からのデータのパブリッシュは、次のようなシナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="a513b-111">Publishing data from Oracle is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="a513b-112">シナリオ</span><span class="sxs-lookup"><span data-stu-id="a513b-112">Scenario</span></span>|<span data-ttu-id="a513b-113">説明</span><span class="sxs-lookup"><span data-stu-id="a513b-113">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a513b-114">.NET Framework アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="a513b-114">.NET Framework application deployments</span></span>|<span data-ttu-id="a513b-115">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 以外のデータベースからレプリケートされたデータを使用しながら、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio および[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用して開発します。</span><span class="sxs-lookup"><span data-stu-id="a513b-115">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="a513b-116">データ ウェアハウジング ステージング サーバー</span><span class="sxs-lookup"><span data-stu-id="a513b-116">Data warehousing staging servers</span></span>|<span data-ttu-id="a513b-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ステージング データベースと[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースとの同期を保ちます。</span><span class="sxs-lookup"><span data-stu-id="a513b-117">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="a513b-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a513b-118">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="a513b-119">ソース システムの変更のレプリケーション中に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してアプリケーションをリアルタイムでテストします。</span><span class="sxs-lookup"><span data-stu-id="a513b-119">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="a513b-120">移行に問題がなければ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="a513b-120">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
 <span data-ttu-id="a513b-121">詳細については、「[Oracle パブリッシングの概要](oracle-publishing-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a513b-121">For more information, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a><span data-ttu-id="a513b-122">SQL Server 以外のサブスクライバーへのデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="a513b-122">Publishing Data to Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="a513b-123">以下の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースは、スナップショット パブリケーションとトランザクション パブリケーションに対するサブスクライバーとしてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a513b-123">The following non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases are supported as Subscribers to snapshot and transactional publications:</span></span>  
  
-   <span data-ttu-id="a513b-124">Oracle (Oracle がサポートするすべてのプラットフォーム用)</span><span class="sxs-lookup"><span data-stu-id="a513b-124">Oracle for all platforms that Oracle supports.</span></span>  
  
-   <span data-ttu-id="a513b-125">IBM DB2 (AS400、MVS、Unix、Linux、および Windows 用)</span><span class="sxs-lookup"><span data-stu-id="a513b-125">IBM DB2 for AS400, MVS, Unix, Linux, and Windows.</span></span>  
  
 <span data-ttu-id="a513b-126">詳細については、「 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a513b-126">For more information, see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span>  
  
  
