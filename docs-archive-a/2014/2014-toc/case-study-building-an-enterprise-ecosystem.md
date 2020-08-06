---
title: 'ケーススタディ: Microsoft Dynamics ERP を使用したエンタープライズエコシステムの構築と、スケーラビリティとパフォーマンスのための SQL Server 2014 レプリケーション |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 2b0b5ab7-4e08-431a-bd59-360177c4565c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dfde59b5e3e12746aa6dbaf975b079cfe32a3718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631373"
---
# <a name="case-study-building-an-enterprise-ecosystem-with-microsoft-dynamics-erp-and-sql-server-2014-replication-for-scalability-and-performance"></a><span data-ttu-id="d9869-102">ケース スタディ: Microsoft Dynamics ERP と SQL Server 2014 レプリケーションを活用した、スケーラビリティとパフォーマンスの向上のためのエンタープライズ エコシステムの構築</span><span class="sxs-lookup"><span data-stu-id="d9869-102">Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance</span></span>

  <span data-ttu-id="d9869-103">**概要:** このホワイトペーパーでは、次のシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d9869-103">**Summary:** This paper covers the following scenarios:</span></span>  
<span data-ttu-id="d9869-104">SQL Server 2014 でトランザクションレプリケーションを使用して、Dynamics AX クライアントからのトランザクションを複数のノードに分散させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9869-104">How to use transactional replication in SQL Server 2014 to distribute the transactions from Dynamics AX clients across multiple nodes.</span></span> <span data-ttu-id="d9869-105">トランザクション レプリケーションでは、データが複数のノードでリアルタイムに保持されるため、データの冗長性が実現し、データの可用性が向上します。これには、パフォーマンス分析をより効率的に行うために使用できるデータも含まれます。</span><span class="sxs-lookup"><span data-stu-id="d9869-105">Because data is maintained across the nodes in real-time, transactional replication provides data redundancy, which increases the availability of data, includes data available for more efficient performance analysis.</span></span>  
<span data-ttu-id="d9869-106">Microsoft Dynamics ERP で拡張性の高いエンタープライズ エコシステムを構築するためにトランザクション レプリケーションを活用する際に関係する詳細事項を理解する方法。</span><span class="sxs-lookup"><span data-stu-id="d9869-106">How to understand the specifics involved while leveraging transactional replication to build highly scalable Enterprise ecosystems in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="d9869-107">AX の既定の機能をカスタマイズすることなく、高いパフォーマンスとスケーラビリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="d9869-107">Deliver high performance and scalability without customizing the AX out-of-box features.</span></span>  
  
 <span data-ttu-id="d9869-108">トランザクション レプリケーションは、高いスループットが必要とされるサーバー間のワークフローで使われるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="d9869-108">Transactional replication is typically used in server-to-server workflows that require high throughput.</span></span> <span data-ttu-id="d9869-109">たとえば、スケーラビリティと可用性の向上、データ ウェアハウジングとレポート、複数サイトからのデータの統合、異種データの統合、バッチ処理のオフロードなどのシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="d9869-109">These include scenarios, such as improving scalability and availability, data warehousing and reporting, integrating data from multiple sites, integrating heterogeneous data, and offloading batch processing.</span></span> <span data-ttu-id="d9869-110">このホワイト ペーパーでは、Microsoft Dynamics ERP でトランザクション レプリケーションを活用する個々のシナリオと、それに関連するパターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d9869-110">This white paper describes a distinct scenario and associated patterns where transactional replication is leveraged in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="d9869-111">また、Enterprise Resource Planning (ERP) 固有のエンタープライズ ソリューションの構築のためにトランザクション レプリケーションを検討する際の課題とベスト プラクティスや、各段階でのパフォーマンス分析についても解説しています。</span><span class="sxs-lookup"><span data-stu-id="d9869-111">It also covers the challenges and best practices when considering transactional replication to build enterprise solutions specific to Enterprise Resource Planning (ERP), as well as the performance analysis at different stages.</span></span>  
  
 <span data-ttu-id="d9869-112">このコンテンツは、開発者、アーキテクト、データベース管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="d9869-112">This content is suitable for developers, architects, and database administrators.</span></span> <span data-ttu-id="d9869-113">このホワイト ペーパーの読者の皆様には、SQL Server 2008、2012、2014 に関する基礎知識と、SQL Server の管理の経験があることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="d9869-113">It is assumed that readers of this white paper have basic knowledge of SQL Server 2008, 2012, or 2014 as well as SQL Server administration experience.</span></span>  
  
 <span data-ttu-id="d9869-114">**ライター:** Prabhakaran Sethuraman (PRAB)、Microsoft</span><span class="sxs-lookup"><span data-stu-id="d9869-114">**Writer:** Prabhakaran Sethuraman (PRAB), Microsoft</span></span>  
  
 <span data-ttu-id="d9869-115">**技術レビューアー:** Prabhakaran Sethuraman (PRAB)、Microsoft、Santosh Padhy、Microsoft;Pavel Majstrov、Microsoft、Karthik Sankaranarayanan、Microsoft、Jon Acone、Microsoft;David Stahlkopf、Microsoft;Kent Oldenburger、Microsoft、Mandi Ohlinger、Microsoft;Jason Roth、Microsoft</span><span class="sxs-lookup"><span data-stu-id="d9869-115">**Technical Reviewers:** Prabhakaran Sethuraman (PRAB), Microsoft; Santosh Padhy, Microsoft; Pavel Majstrov, Microsoft; Karthik Sankaranarayanan, Microsoft; Jon Acone, Microsoft; David Stahlkopf, Microsoft;Kent Oldenburger, Microsoft; Mandi Ohlinger, Microsoft; Jason Roth, Microsoft</span></span>  
  
 <span data-ttu-id="d9869-116">**発行済み:** 2015年10月</span><span class="sxs-lookup"><span data-stu-id="d9869-116">**Published:** October 2015</span></span>  
  
 <span data-ttu-id="d9869-117">**適用対象:** SQL Server 2008、SQL Server 2012、SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="d9869-117">**Applies to:** SQL Server 2008, SQL Server 2012, and SQL Server 2014</span></span>  
  
 <span data-ttu-id="d9869-118">ドキュメントを確認するには、</span><span class="sxs-lookup"><span data-stu-id="d9869-118">To review the document, please download the</span></span>  
        <span data-ttu-id="d9869-119">[ケーススタディ: Microsoft DYNAMICS ERP を使用したエンタープライズエコシステムの構築と、スケーラビリティとパフォーマンスのための SQL Server 2014 レプリケーション](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx)Word 文書。</span><span class="sxs-lookup"><span data-stu-id="d9869-119">[Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx) Word document.</span></span>  
  
  
