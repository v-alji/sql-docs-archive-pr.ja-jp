---
title: Oracle CDC インスタンス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ed71e8c4-e013-4bf2-8b6c-1e833ff2a41d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2228872b5a190fd416dccaa8062dd79dbc1f7a79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641194"
---
# <a name="the-oracle-cdc-instance"></a><span data-ttu-id="5602b-102">Oracle CDC インスタンス</span><span class="sxs-lookup"><span data-stu-id="5602b-102">The Oracle CDC Instance</span></span>
  <span data-ttu-id="5602b-103">Oracle CDC インスタンスは、単一の Oracle ソース データベースからキャプチャされた変更を処理するために、Oracle CDC Service によって作成されたプロセスです。</span><span class="sxs-lookup"><span data-stu-id="5602b-103">The Oracle CDC Instance is a process created by the Oracle CDC Service to process changes captured from a single Oracle source database.</span></span> <span data-ttu-id="5602b-104">Oracle CDC インスタンスは、その構成を **cdc.xdbcdc_config** テーブルから取得し、その状態を **cdc.xdbcdc_state** テーブルで維持します。</span><span class="sxs-lookup"><span data-stu-id="5602b-104">The Oracle CDC Instance retrieves its configuration from the **cdc.xdbcdc_config** table and maintains its state in the **cdc.xdbcdc_state** table.</span></span> <span data-ttu-id="5602b-105">これらのテーブルは、Oracle CDC インスタンスを定義する CDC データベースの一部です。</span><span class="sxs-lookup"><span data-stu-id="5602b-105">These tables are part of the CDC database, which defines the Oracle CDC Instance.</span></span> <span data-ttu-id="5602b-106">xdbcdc データベースおよびテーブルの詳細については、「 [The CDC Databases](the-oracle-cdc-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5602b-106">For more information about the xdbcdc database and tables see [The CDC Databases](the-oracle-cdc-service.md).</span></span>  
  
 <span data-ttu-id="5602b-107">Oracle CDC インスタンスによって実行されるタスクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5602b-107">The following describes the tasks carried out by the Oracle CDC instance:</span></span>  
  
-   <span data-ttu-id="5602b-108">**サービス開始時の検証の処理**: 起動した CDC インスタンスは、 **xdbcdc_config** テーブルから構成を読み込み、一連の状態検証を実行します。この検証で、CDC インスタンスの永続化された状態に一貫性があり、変更の処理を開始できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5602b-108">**Handling service startup verification**: When started, the CDC instance loads its configuration from the **xdbcdc_config** table and performs a series of status verifications that ensure that the CDC instance persisted state is consistent and that it can start processing changes.</span></span>  
  
-   <span data-ttu-id="5602b-109">**変更のキャプチャの準備**: 検証が正常に終了した場合、Oracle CDC インスタンスは現在定義されているすべてのキャプチャ インスタンスをスキャンし、変更のキャプチャに必要な Oracle LogMiner クエリおよびその他のサポート構造を準備します。</span><span class="sxs-lookup"><span data-stu-id="5602b-109">**Preparing for change capture**: When the verification passes successfully, the Oracle CDC Instance scans all of the capture instances currently defined and prepares the Oracle LogMiner queries and other support structures required for change capture.</span></span> <span data-ttu-id="5602b-110">また、Oracle インスタンスは Oracle CDC インスタンスが最後に実行されたときに保存された内部キャプチャ状態を再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5602b-110">In addition, the Oracle instance re-loads the internal capture state that was saved the last time the Oracle CDC Instance run.</span></span>  
  
-   <span data-ttu-id="5602b-111">**Oracle の変更のキャプチャ**: Oracle CDC インスタンスは、Oracle LogMiner 機能を利用して Oracle の変更をプールし、トランザクションのコミットに従ってそれらを並べ替え、トランザクションの時刻を変更して CDC データベースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変更テーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5602b-111">**Capturing changes from Oracle**: The Oracle CDC Instance pools changes from Oracle by means of the Oracle LogMiner facility, orders them in according to transaction commit, and then changes the time in a transaction and writes them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables in the CDC database.</span></span>  
  
-   <span data-ttu-id="5602b-112">**サービスのシャットダウンの処理**: Oracle CDC インスタンスのライフ サイクルは、Oracle CDC Service によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="5602b-112">**Handling service shutdown**: The life cycle of the Oracle CDC Instance is managed by the Oracle CDC Service.</span></span> <span data-ttu-id="5602b-113">シャットダウンを要求された場合、Oracle CDC インスタンスは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="5602b-113">When the Oracle CDC Instance is requested to shut down, it performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="5602b-114">Oracle トランザクション ログからの読み取りを停止します。</span><span class="sxs-lookup"><span data-stu-id="5602b-114">Stops reading from the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="5602b-115">完了した Oracle トランザクションの CDC データベースへの書き込みを停止します。</span><span class="sxs-lookup"><span data-stu-id="5602b-115">Stops writing completed Oracle transactions to the CDC database.</span></span>  
  
    -   <span data-ttu-id="5602b-116">必要に応じて、現在のトランザクションの CDC データベースへの書き込みが終了するまで、最大で 30 秒待機します。</span><span class="sxs-lookup"><span data-stu-id="5602b-116">Waits for up to 30 seconds (if necessary) until the current transaction finishes writing to the CDC database.</span></span> <span data-ttu-id="5602b-117">30 秒以上が経過した場合、書き込みはキャンセルされ、トランザクションはロールバックされます (CDC インスタンスが再起動したときに再試行されます)。</span><span class="sxs-lookup"><span data-stu-id="5602b-117">If more than 30 seconds pass, the writing is cancelled and transaction is rolled back (to be retried when the CDC instance is restarted).</span></span>  
  
    -   <span data-ttu-id="5602b-118">個別のスレッドで、ステージングされたトランザクション テーブルに最大で 30 秒間、メモリにキャッシュされたレコードをできるだけ多く書き込み (最も古いトランザクションから最新のトランザクションの順)、 **xdbcdc_state** テーブルを更新してすべての変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="5602b-118">In a separate thread, writes as many memory-cached records as possible to the staged transactions table for up to 30 seconds (from the oldest transaction to the newest), then updates the **xdbcdc_state** table and commits all the changes.</span></span>  
  
-   <span data-ttu-id="5602b-119">**構成の変更の処理**: Oracle CDC インスタンスは、CDC Service から、または **cdc.xdbcdc_config** テーブルで新しいバージョンを検出することにより、構成の変更に関する通知を受けます。</span><span class="sxs-lookup"><span data-stu-id="5602b-119">**Handling configuration changes**: The Oracle CDC Instance is notified about configuration changes either from the CDC Service or by detecting a new version in the **cdc.xdbcdc_config** table.</span></span> <span data-ttu-id="5602b-120">ほとんどの変更では、Oracle CDC インスタンスを再起動する必要はありません (キャプチャ インスタンスの追加または削除など)。</span><span class="sxs-lookup"><span data-stu-id="5602b-120">Most changes do not require the restart of the Oracle CDC Instance (for example, adding or removing capture instances).</span></span> <span data-ttu-id="5602b-121">しかし、Oracle 接続文字列やアクセス資格情報の変更など、一部の変更では、Oracle CDC インスタンスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5602b-121">However, some changes, such as changing the Oracle connection string or access credentials do require the restart of the CDC Instance.</span></span>  
  
-   <span data-ttu-id="5602b-122">**復旧の処理**: Oracle CDC インスタンスが起動すると、その内部状態が **xdbcdc_state** テーブルおよび **xdbcdc_staged_transactions** テーブルから復元されます。</span><span class="sxs-lookup"><span data-stu-id="5602b-122">**Handling recovery**: When an Oracle CDC Instance starts its internal state is restored from the **xdbcdc_state** and the **xdbcdc_staged_transactions** tables.</span></span> <span data-ttu-id="5602b-123">状態が復元されると、CDC インスタンスは通常どおり実行されます。</span><span class="sxs-lookup"><span data-stu-id="5602b-123">Once the state is restored, the CDC instance proceeds as usual.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5602b-124">参照</span><span class="sxs-lookup"><span data-stu-id="5602b-124">See Also</span></span>  
 [<span data-ttu-id="5602b-125">エラー処理</span><span class="sxs-lookup"><span data-stu-id="5602b-125">Error Handling</span></span>](error-handling.md)  
  
  
