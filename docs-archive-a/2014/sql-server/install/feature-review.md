---
title: 機能の確認 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1e2b22b8-5811-4f50-875b-685f3ddbd1ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e258ac763d8c5e057f8dcdb6f740aacb4fef1c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643143"
---
# <a name="feature-review"></a><span data-ttu-id="7b3e1-102">[機能の確認]</span><span class="sxs-lookup"><span data-stu-id="7b3e1-102">Feature Review</span></span>
  <span data-ttu-id="7b3e1-103">[機能の確認] ページは、準備された機能の読み取り専用の一覧です。これらの機能は、イメージの完了ステップの最後に構成されて完了となります。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-103">The Feature Review page is a read-only list of features that have been prepared and will be configured and completed at the end of the complete image step.</span></span> <span data-ttu-id="7b3e1-104">機能一覧はイメージの準備ステップ時に選択されます。イメージの完了ステップで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-104">The feature list is selected during the prepare image step and cannot be modified during complete image step.</span></span> <span data-ttu-id="7b3e1-105">表示されている機能に加え、準備済みインスタンスには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client も含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-105">In addition to the features displayed, a prepared instance also includes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="7b3e1-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の準備済みインスタンスの構成が完了した後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの準備済みインスタンスに含まれていない他の機能を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-106">You can add other features not included in the prepared instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance after you have completed the configuration of the prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7b3e1-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="7b3e1-107">UI element list</span></span>  
  
|<span data-ttu-id="7b3e1-108">コンポーネント グループ</span><span class="sxs-lookup"><span data-stu-id="7b3e1-108">Component Group</span></span>|<span data-ttu-id="7b3e1-109">コンポーネントおよび機能</span><span class="sxs-lookup"><span data-stu-id="7b3e1-109">Components and features</span></span>|  
|---------------------|-----------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="7b3e1-110">サービス</span><span class="sxs-lookup"><span data-stu-id="7b3e1-110">Services</span></span>|<span data-ttu-id="7b3e1-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、データの格納、処理、セキュリティ確保のための中心的なサービスです。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="7b3e1-112">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]には、次のコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-112">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] includes the following components:</span></span><br /><br /> <span data-ttu-id="7b3e1-113">レプリケーション: (オプション) レプリケーションは、あるデータベースから別のデータベースへデータ オブジェクトやデータベース オブジェクトのコピーと配布を行い、一貫性を維持するためにデータベース間の同期を行う一連のテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-113">Replication: (Optional) Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span><br /><br /> <span data-ttu-id="7b3e1-114">フルテキスト検索: (オプション) フルテキスト検索は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルのプレーン文字ベースのデータに対してフルテキスト クエリを実行するための機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-114">Full-Text Search: (Optional) Full-Text Search provides functionality to issue full-text queries against plain character-based data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span><br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] <span data-ttu-id="7b3e1-115">(オプション): [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) は、データ ソース内で一貫性のない不適切なデータを発見できるデータ クレンジング ソリューションであり、データのクレンジングを自動的かつインタラクティブに行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-115">(Optional): [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) is a data-cleansing solution that enables you to discover inconsistent and incorrect data in your data source, and provides automated and interactive ways to cleanse the data.</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7b3e1-116">には、表形式、マトリックス形式、グラフィカル形式、および自由形式のレポートを作成、管理、配置するためのサーバー コンポーネントとクライアント コンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-116">includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free-form reports.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7b3e1-117">は、レポート アプリケーション開発用の拡張可能プラットフォームとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b3e1-117">is also an extensible platform that you can use to develop report applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b3e1-118">参照</span><span class="sxs-lookup"><span data-stu-id="7b3e1-118">See Also</span></span>  
 [<span data-ttu-id="7b3e1-119">SysPrep を使用した SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="7b3e1-119">Install SQL Server 2014 Using SysPrep</span></span>](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
  
  
