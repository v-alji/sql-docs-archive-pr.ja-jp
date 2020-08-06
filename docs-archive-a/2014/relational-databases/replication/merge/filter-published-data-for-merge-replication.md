---
title: マージ レプリケーション用にパブリッシュされたデータのフィルター選択 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], filtering published data
- replication [SQL Server], filtering published data
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ad9ad45a64f57a6bef8255373180ea943af9893f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630958"
---
# <a name="filter-published-data-for-merge-replication"></a><span data-ttu-id="4fbca-102">マージ レプリケーション用にパブリッシュされたデータのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="4fbca-102">Filter Published Data for Merge Replication</span></span>
  <span data-ttu-id="4fbca-103">他の種類のレプリケーションで定義できる静的行フィルターと列フィルター以外に、マージ レプリケーションでは、パラメーター化された行フィルターと結合フィルターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4fbca-103">In addition to the static row filters and column filters you can define with other types of replication, merge replication offers parameterized row filters and join filters.</span></span> <span data-ttu-id="4fbca-104">静的行フィルターと列フィルターの詳細については、「[パブリッシュされたデータのフィルター選択](../publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fbca-104">For more information about static row filters and column filters, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
 <span data-ttu-id="4fbca-105">マージ レプリケーションは、モバイル ユーザーをサポートする多くのアプリケーションで使用されています。これらのアプリケーションには通常、多数のサブスクリプションが含まれ、各サブスクリプションが一意のデータセットを受信します。</span><span class="sxs-lookup"><span data-stu-id="4fbca-105">Merge replication is used in many applications that support mobile users; these applications usually have a large number of subscriptions with each subscription receiving a unique data set.</span></span> <span data-ttu-id="4fbca-106">パラメーター化されたフィルターと結合フィルターを組み合わせることにより、管理者は 1 つのパブリケーション (多くても数個のパブリケーション) を設定するだけでさまざまなデータセットをユーザーに提供でき、複数のパブリケーションを作成することにより発生する管理オーバーヘッドを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="4fbca-106">Parameterized filters combined with join filters allow an administrator to set up one publication (or at most a small number of publications) and yet provide different data sets to users, reducing the management overhead introduced by creating multiple publications.</span></span>  
  
-   <span data-ttu-id="4fbca-107">パラメーター化されたフィルターを使用すると、複数のパブリケーションを作成しなくても、パーティションの異なるデータをそれぞれ対応するサブスクライバーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="4fbca-107">Parameterized filters allow different partitions of data to be sent to different Subscribers without requiring multiple publications to be created.</span></span> <span data-ttu-id="4fbca-108">たとえば、テーブルをフィルターして、指定された営業担当者のデータをその担当者に対してのみレプリケートすることができます。</span><span class="sxs-lookup"><span data-stu-id="4fbca-108">For example, a table can be filtered so that data for a given sales representative is replicated only to that representative.</span></span> <span data-ttu-id="4fbca-109">パラメーター化されたフィルターには、パフォーマンスを最適化し、データとアプリケーションの要件に最も適した結果が得られるようにフィルターを調整するための、さまざまなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="4fbca-109">Parameterized filters have a variety of options that allow you to tailor filtering to optimize performance and best match your data and application requirements.</span></span> <span data-ttu-id="4fbca-110">詳しくは、「 [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4fbca-110">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="4fbca-111">結合フィルターは、通常、関連するテーブルに対するフィルターを拡張するために、パラメーター化されたフィルターと組み合わせて使用します (静的フィルターと組み合わせて使用することもできます)。</span><span class="sxs-lookup"><span data-stu-id="4fbca-111">Join filters are typically used in conjunction with parameterized filters to extend filtering to related tables (they can also be used in conjunction with static filters).</span></span> <span data-ttu-id="4fbca-112">たとえば、営業担当者は、通常、顧客テーブルや注文テーブルなどの他のテーブルにデータを持っています。</span><span class="sxs-lookup"><span data-stu-id="4fbca-112">For example, the sales representative typically has data in other tables such as customer and order tables.</span></span> <span data-ttu-id="4fbca-113">このデータをフィルター選択することにより、営業担当者は、担当の顧客とその顧客の注文についてのデータのみを受信することができます。</span><span class="sxs-lookup"><span data-stu-id="4fbca-113">This data can be filtered so the sales representative receives only the data on her customers and her customers' orders.</span></span> <span data-ttu-id="4fbca-114">詳しくは、「 [Join Filters](join-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4fbca-114">For more information, see [Join Filters](join-filters.md).</span></span>  
  
 <span data-ttu-id="4fbca-115">フィルターには、レプリケーションで行の識別に使用される `rowguidcol` を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="4fbca-115">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="4fbca-116">既定では、これはマージ レプリケーションのセットアップ時に追加される列であり、 **rowguid**という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="4fbca-116">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fbca-117">参照</span><span class="sxs-lookup"><span data-stu-id="4fbca-117">See Also</span></span>  
 [<span data-ttu-id="4fbca-118">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="4fbca-118">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
