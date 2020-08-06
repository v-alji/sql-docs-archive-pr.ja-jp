---
title: Oracle パブリッシャーの管理上の注意点 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], administrative considerations
- administering replication, Oracle publishing
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3104b507987a4a236d39dd0ae1f8e3c29358c730
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643242"
---
# <a name="administrative-considerations-for-oracle-publishers"></a><span data-ttu-id="440fe-102">Oracle パブリッシャーの管理上の注意点</span><span class="sxs-lookup"><span data-stu-id="440fe-102">Administrative Considerations for Oracle Publishers</span></span>
  <span data-ttu-id="440fe-103">Oracle データベース システムの管理者は、Oracle パブリッシャーを構成して、レプリケーションの変更追跡のメカニズムを設定した後でも、標準の Oracle データベース ユーティリティを使用したり、通常のシステム管理作業を実行したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="440fe-103">After an Oracle Publisher is configured and the replication change tracking mechanisms are in place, administrators of the Oracle database system can still use standard Oracle database utilities and perform typical system administration tasks.</span></span> <span data-ttu-id="440fe-104">しかし、特定の管理作業を実行してパブリッシュされたデータへの影響については注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="440fe-104">However, you should be aware of the effects on the published data of performing certain administrative tasks.</span></span>  
  
 <span data-ttu-id="440fe-105">レプリケーション用にパブリッシュされた列の削除や変更、またはレプリケーション オブジェクトの削除や変更の場合を除いて、これらの注意点はスナップショット パブリケーションには当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="440fe-105">With the exception of dropping or modifying a column that is published for replication, or dropping or modifying any replication objects, these considerations do not apply to snapshot publications.</span></span>  
  
## <a name="importing-and-loading-data"></a><span data-ttu-id="440fe-106">データのインポートと読み込み</span><span class="sxs-lookup"><span data-stu-id="440fe-106">Importing and loading data</span></span>  
 <span data-ttu-id="440fe-107">Oracle 上のトランザクション パブリケーションでは、トリガーを使用して変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="440fe-107">Triggers are used in change tracking for transactional publications on Oracle.</span></span> <span data-ttu-id="440fe-108">パブリッシュされたテーブルに対する変更がサブスクライバーにレプリケートされるのは、更新、挿入、削除の際にレプリケーション トリガーが起動されたときだけです。</span><span class="sxs-lookup"><span data-stu-id="440fe-108">Changes to published tables can be replicated to Subscribers only if the replication triggers fire when an update, insert, or delete occurs.</span></span> <span data-ttu-id="440fe-109">Oracle ユーティリティの Oracle インポートおよび SQL\*Loader には、レプリケートされたテーブルにこれらのユーティリティから行を挿入したときにトリガーを起動するかどうかを指定するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="440fe-109">The Oracle utilities Oracle Import and SQL\*Loader both have options that affect whether triggers will fire when rows are inserted into replicated tables with these utilities.</span></span>  
  
### <a name="oracle-import"></a><span data-ttu-id="440fe-110">Oracle インポート</span><span class="sxs-lookup"><span data-stu-id="440fe-110">Oracle Import</span></span>  
 <span data-ttu-id="440fe-111">Oracle インポートでは、 **ignore** オプションを「y」または「n」に設定できます (既定値は「n」です)。</span><span class="sxs-lookup"><span data-stu-id="440fe-111">With Oracle Import, you can set the option **ignore** to 'y' or 'n' (the default is 'n').</span></span> <span data-ttu-id="440fe-112">**ignore** を「n」に設定すると、インポート時にテーブルが削除されて再作成されます。</span><span class="sxs-lookup"><span data-stu-id="440fe-112">If **ignore** is set to 'n', the table is dropped and re-created during import.</span></span> <span data-ttu-id="440fe-113">このときレプリケーション トリガーが削除され、レプリケーションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="440fe-113">This removes replication triggers and disables replication.</span></span> <span data-ttu-id="440fe-114">**ignore** を「y」に設定すると、既存のテーブルに行が読み込まれ、レプリケーション トリガーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="440fe-114">If **ignore** is set to 'y', import will attempt to load the rows into the existing table, which fires the replication triggers.</span></span> <span data-ttu-id="440fe-115">したがって、レプリケートされるテーブルに Import ツールでインポートする際には、 **ignore** を「y」に設定してください。</span><span class="sxs-lookup"><span data-stu-id="440fe-115">Therefore, ensure **ignore** is set to 'y' when importing into a replicated table with the Import tool.</span></span>  
  
### <a name="sqlloader"></a><span data-ttu-id="440fe-116">SQL\*Loader</span><span class="sxs-lookup"><span data-stu-id="440fe-116">SQL\*Loader</span></span>  
 <span data-ttu-id="440fe-117">SQL\*Loader では、**direct** オプションを「true」または「false」に設定できます (既定値は「false」です)。</span><span class="sxs-lookup"><span data-stu-id="440fe-117">With SQL\*Loader, you can set the option **direct** to 'true' or 'false' (the default is 'false').</span></span> <span data-ttu-id="440fe-118">**direct** を「false」に設定すると、通常の INSERT ステートメントを使用して行が挿入され、レプリケーション トリガーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="440fe-118">If **direct** is set to 'false', rows are inserted using conventional INSERT statements, which fire replication triggers.</span></span> <span data-ttu-id="440fe-119">**direct** を「true」に設定すると、読み込みが最適化され、トリガーは起動されません。</span><span class="sxs-lookup"><span data-stu-id="440fe-119">If **direct** is set to 'true', the load is optimized, and triggers are not fired.</span></span> <span data-ttu-id="440fe-120">したがって、SQL\*Loader ツールでレプリケートされるテーブルへの読み込みを行う際には、 **direct** を「false」に設定してください。</span><span class="sxs-lookup"><span data-stu-id="440fe-120">Therefore, ensure **direct** is set to 'false' when loading into a replicated table with the SQL\*Loader tool.</span></span>  
  
## <a name="making-changes-to-published-objects"></a><span data-ttu-id="440fe-121">パブリッシュされたオブジェクトに対する変更</span><span class="sxs-lookup"><span data-stu-id="440fe-121">Making changes to published objects</span></span>  
 <span data-ttu-id="440fe-122">以下の操作には、特別な注意は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="440fe-122">The following actions require no special considerations:</span></span>  
  
-   <span data-ttu-id="440fe-123">パブリッシュされたテーブルでのインデックスの再構築</span><span class="sxs-lookup"><span data-stu-id="440fe-123">Rebuilding indexes on published tables.</span></span>  
  
-   <span data-ttu-id="440fe-124">パブリッシュされたテーブルへのユーザー トリガーの追加</span><span class="sxs-lookup"><span data-stu-id="440fe-124">Adding user triggers to a published table.</span></span>  
  
 <span data-ttu-id="440fe-125">以下の操作では、パブリッシュされたテーブルに対するすべての操作を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="440fe-125">The following action requires you to stop all activity on the published tables:</span></span>  
  
-   <span data-ttu-id="440fe-126">パブリッシュされたテーブルの移動</span><span class="sxs-lookup"><span data-stu-id="440fe-126">Moving a published table.</span></span>  
  
 <span data-ttu-id="440fe-127">以下の操作では、パブリケーションを削除し、各操作を実行した後でパブリケーションを作成し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="440fe-127">The following actions require you to drop the publication, perform the operation, and then recreate the publication:</span></span>  
  
-   <span data-ttu-id="440fe-128">パブリッシュされたテーブルの切り捨て</span><span class="sxs-lookup"><span data-stu-id="440fe-128">Truncating a published table.</span></span>  
  
-   <span data-ttu-id="440fe-129">パブリッシュされたテーブル名の変更</span><span class="sxs-lookup"><span data-stu-id="440fe-129">Renaming a published table.</span></span>  
  
-   <span data-ttu-id="440fe-130">パブリッシュされたテーブルへの列の追加</span><span class="sxs-lookup"><span data-stu-id="440fe-130">Adding a column to a published table.</span></span>  
  
-   <span data-ttu-id="440fe-131">レプリケーション用にパブリッシュされた列の削除または変更</span><span class="sxs-lookup"><span data-stu-id="440fe-131">Dropping or modifying a column that is published for replication.</span></span>  
  
-   <span data-ttu-id="440fe-132">ログに記録されない操作の実行</span><span class="sxs-lookup"><span data-stu-id="440fe-132">Performing non-logged operations.</span></span>  
  
## <a name="dropping-or-modifying-replication-objects"></a><span data-ttu-id="440fe-133">レプリケーション オブジェクトの削除と変更</span><span class="sxs-lookup"><span data-stu-id="440fe-133">Dropping or modifying replication objects</span></span>  
 <span data-ttu-id="440fe-134">パブリッシャー レベルの追跡テーブル、トリガー、シーケンス、ストアド プロシージャを削除または変更するには、パブリッシャーを削除して再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="440fe-134">You must drop and reconfigure the Publisher if you drop or modify any Publisher level tracking tables, triggers, sequences, or stored procedures.</span></span> <span data-ttu-id="440fe-135">これらのオブジェクトの一部の一覧については、「[Oracle パブリッシャー上で作成されたオブジェクト](objects-created-on-the-oracle-publisher.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440fe-135">For a partial list of these objects, see [Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="440fe-136">パブリッシャーの削除と再構成の詳細については、「[Oracle パブリッシャーのトラブルシューティング](troubleshooting-oracle-publishers.md)」の「パブリッシャーの再構成が必要になる変更」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="440fe-136">For information about dropping and reconfiguring the Publisher, see the section "Changes are made that require reconfiguration of the Publisher" in the topic [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="440fe-137">参照</span><span class="sxs-lookup"><span data-stu-id="440fe-137">See Also</span></span>  
 <span data-ttu-id="440fe-138">[Oracle パブリッシャーの構成](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="440fe-138">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="440fe-139">[Oracle パブリッシャーの設計上の注意点および制限](design-considerations-and-limitations-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="440fe-139">[Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="440fe-140">Oracle パブリッシングの概要</span><span class="sxs-lookup"><span data-stu-id="440fe-140">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
