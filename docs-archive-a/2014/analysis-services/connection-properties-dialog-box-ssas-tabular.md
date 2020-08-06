---
title: '[接続プロパティ] ダイアログボックス (SSAS-テーブル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.ConnectionProperties.F1
ms.assetid: 17bae8ae-2ba0-4978-be70-61c687f59d54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e4b0360d59f43bc932f68a846f239c4873a5aa9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633454"
---
# <a name="connection-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="c1e95-102">[接続プロパティ] ダイアログ ボックス (SSAS - テーブル)</span><span class="sxs-lookup"><span data-stu-id="c1e95-102">Connection Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="c1e95-103">このページを使用すると、SQL Server Management Studio で、テーブル モデル データベースによって使用されるデータ ソースの接続プロパティを表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="c1e95-103">Use this page to view or modify in SQL Server Management Studio the connection properties of a data source used by a tabular model database.</span></span>  
  
 <span data-ttu-id="c1e95-104">このダイアログ ボックスは、タイムスタンプとその他の情報に加え、接続の特性を決定するカスタマイズ可能なプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-104">This dialog box provides timestamps and other descriptive information, plus customizable properties that determine characteristics of the connection.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c1e95-105">Options</span><span class="sxs-lookup"><span data-stu-id="c1e95-105">Options</span></span>  
  
|<span data-ttu-id="c1e95-106">期間</span><span class="sxs-lookup"><span data-stu-id="c1e95-106">Term</span></span>|<span data-ttu-id="c1e95-107">定義</span><span class="sxs-lookup"><span data-stu-id="c1e95-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="c1e95-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="c1e95-108">**Name**</span></span>|<span data-ttu-id="c1e95-109">データ ソース名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-109">Specifies the name of the data source.</span></span>|  
|<span data-ttu-id="c1e95-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="c1e95-110">**ID**</span></span>|<span data-ttu-id="c1e95-111">データ ソース オブジェクトの識別子を表示します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-111">Displays the identifier of the data source object.</span></span>|  
|<span data-ttu-id="c1e95-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="c1e95-112">**Description**</span></span>|<span data-ttu-id="c1e95-113">データ ソース オブジェクトの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-113">Displays the description of the data source object.</span></span>|  
|<span data-ttu-id="c1e95-114">**[タイムスタンプの作成]**</span><span class="sxs-lookup"><span data-stu-id="c1e95-114">**Create Timestamp**</span></span>|<span data-ttu-id="c1e95-115">データベースが作成された日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1e95-115">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="c1e95-116">**[スキーマの最終更新]**</span><span class="sxs-lookup"><span data-stu-id="c1e95-116">**Last Schema Update**</span></span>|<span data-ttu-id="c1e95-117">データベースのメタデータが最後に更新されたときの日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1e95-117">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="c1e95-118">**接続文字列**</span><span class="sxs-lookup"><span data-stu-id="c1e95-118">**Connection String**</span></span>|<span data-ttu-id="c1e95-119">データをモデルに提供するデータ ソースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-119">Displays the connection string used to connect to the data source that provides data to the model.</span></span>|  
|<span data-ttu-id="c1e95-120">**最大接続数**</span><span class="sxs-lookup"><span data-stu-id="c1e95-120">**Maximum Number of Connections**</span></span>|<span data-ttu-id="c1e95-121">このデータベースへのクライアント接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-121">Specifies the maximum number of client connections to this database.</span></span>|  
|<span data-ttu-id="c1e95-122">**分離**</span><span class="sxs-lookup"><span data-stu-id="c1e95-122">**Isolation**</span></span>|<span data-ttu-id="c1e95-123">有効な値は、ReadCommitted または Snapshot です。</span><span class="sxs-lookup"><span data-stu-id="c1e95-123">Valid values are ReadCommitted or Snapshot.</span></span> <span data-ttu-id="c1e95-124">詳細については、「[Isolation 要素 (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1e95-124">For more information, see [Isolation Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl).</span></span>|  
|<span data-ttu-id="c1e95-125">**クエリのタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="c1e95-125">**Query Timeout**</span></span>|<span data-ttu-id="c1e95-126">データの取得を試みたときにタイムアウトまでの時間を指定します (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="c1e95-126">Specifies the time, in seconds, after which an attempt to retrieve data is timed out.</span></span>|  
|<span data-ttu-id="c1e95-127">**マネージド プロバイダー**</span><span class="sxs-lookup"><span data-stu-id="c1e95-127">**Managed Provider**</span></span>|<span data-ttu-id="c1e95-128">マネージド プロバイダーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-128">Specifies the name of the managed provider.</span></span> <span data-ttu-id="c1e95-129">データ ソース接続にネイティブ OLE DB プロバイダーを使用する場合、この値は空です。</span><span class="sxs-lookup"><span data-stu-id="c1e95-129">If the data source connection uses a native OLE DB provider, this value is empty.</span></span>|  
|<span data-ttu-id="c1e95-130">**[権限借用情報]**</span><span class="sxs-lookup"><span data-stu-id="c1e95-130">**Impersonation Info**</span></span>|<span data-ttu-id="c1e95-131">リレーショナル データ ストア (DirectQuery による) に対して実行されるクエリ、不一致バインド、リモート パーティション、およびターゲットからソースへのデータベース同期で、データを処理または更新するときにデータベース接続で使用される権限借用アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e95-131">Specifies the impersonation account used for database connections when processing or refreshing data, queries that run against a relational data store (via DirectQuery), out-of-line bindings, remote partitions, and database synchronization from target to source.</span></span><br /><br /> <span data-ttu-id="c1e95-132">有効な値には、Analysis Services サービス アカウントまたは Windows 資格情報の特定のセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c1e95-132">Valid values include the Analysis Services service account or a specific set of Windows credentials.</span></span> <span data-ttu-id="c1e95-133">**[現在のユーザーの資格情報を使用する]** または **[継承する]** を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="c1e95-133">Do not specify **Use the credentials of the current user** or **Inherit**.</span></span> <span data-ttu-id="c1e95-134">これらの資格情報オプションは、テーブル モデル データベースではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c1e95-134">Those credential options are not supported for a tabular model database.</span></span>|  
  
  
