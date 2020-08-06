---
title: マージ サブスクライバーのパーティション情報の検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication data validation [SQL Server replication], partitions
- parameterized filters [SQL Server replication], validating partition information
- validating partition information
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3032ff13af69a0690e1f81f08f7b3fb17aae0ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631763"
---
# <a name="validate-partition-information-for-a-merge-subscriber"></a><span data-ttu-id="07b01-102">マージ サブスクライバーのパーティション情報の検証</span><span class="sxs-lookup"><span data-stu-id="07b01-102">Validate Partition Information for a Merge Subscriber</span></span>
  <span data-ttu-id="07b01-103">マージ パプリケーションに対してパラメーター化された行フィルターを定義している場合は、サブスクライバー情報 (サブスクライバーのログイン名など) を参照する関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="07b01-103">When you define a parameterized row filter for a merge publication, you use a function that references Subscriber information, such as the Subscriber's login name.</span></span> <span data-ttu-id="07b01-104">既定では、レプリケーションはその関数に基づいて、各同期の前およびサブスクライバーにスナップショットが適用されるたびに、サブスクライバー情報を検証します。</span><span class="sxs-lookup"><span data-stu-id="07b01-104">By default, replication validates Subscriber information based on that function before each synchronization and whenever a snapshot is applied at the Subscriber.</span></span> <span data-ttu-id="07b01-105">検証プロセスによって、各サブスクライバーのデータが正しくパーティション分割されます。</span><span class="sxs-lookup"><span data-stu-id="07b01-105">The validation process ensures that data is partitioned correctly for each Subscriber.</span></span> <span data-ttu-id="07b01-106">検証の動作は、**validate_subscriber_info** パブリケーション プロパティで制御されます。このプロパティは、[sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) または **[パブリケーションのプロパティ]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで変更できます。</span><span class="sxs-lookup"><span data-stu-id="07b01-106">Validation behavior is controlled by the **validate_subscriber_info** publication property, which can be changed using [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) or on the **Subscription Options** page of the **Publication Properties** dialog box.</span></span> <span data-ttu-id="07b01-107">パブリケーションのプロパティの変更の詳細については、「 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07b01-107">For more information about changing publication properties, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
## <a name="how-partition-validation-works"></a><span data-ttu-id="07b01-108">パーティション検証の動作</span><span class="sxs-lookup"><span data-stu-id="07b01-108">How Partition Validation Works</span></span>  
 <span data-ttu-id="07b01-109">たとえば、 **SUSER_SNAME()** 関数によってパブリケーションをフィルター選択するとき、マージ エージェントは **SUSER_SNAME()** 式で有効なデータに基づいて初期スナップショットを各サブスクライバーに適用します。</span><span class="sxs-lookup"><span data-stu-id="07b01-109">When a publication is filtered, for example, using the function **SUSER_SNAME()**, the Merge Agent applies the initial snapshot to each Subscriber based on data that is valid for the **SUSER_SNAME()** expression.</span></span>  
  
 <span data-ttu-id="07b01-110">検証が有効な場合、次の同期のためにサブスクライバーがパブリッシャーに再接続すると、マージ エージェントはサブスクライバーの情報を検証し、各サブスクライバーのパーティションが、初期スナップショットで受信したパーティションと同じであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="07b01-110">If validation is enabled, when the Subscriber reconnects to the Publisher for the next synchronization, the Merge Agent validates the information at the Subscriber and ensures that each Subscriber's partition is the same as the one received in the initial snapshot.</span></span> <span data-ttu-id="07b01-111">その後の各マージ アプリケーションまたはスナップショット アプリケーションでは、マージ エージェントは各サブスクライバーのパーティションを検証します。</span><span class="sxs-lookup"><span data-stu-id="07b01-111">For each subsequent merge or snapshot application, the Merge Agent validates each Subscriber's partition.</span></span>  
  
 <span data-ttu-id="07b01-112">フィルター式で使用されている関数が初期スナップショットで返された値と異なる値を返すことをマージ エージェントが検出すると、マージ アプリケーションまたはスナップショット アプリケーションは失敗し、場合によってはそのサブスクライバーのサブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07b01-112">If the Merge Agent detects that the function used in the filtering expression returns a different value than it did at the initial snapshot, the merge or snapshot application fails, and that Subscriber's subscription might require reinitialization.</span></span> <span data-ttu-id="07b01-113">サブスクライバーのマージ設定が変更された場合に発生する問題を回避するために再初期化が必要な場合がありますが、ログイン名などのサブスクライバーの情報を変更して、元のスナップショット時に使用していた値に戻すだけで十分な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="07b01-113">Reinitialization might be necessary to prevent problems that can arise if the merge settings of a Subscriber are changed, but it might be sufficient to change information at the Subscriber, such as the login name, back to the value used at the time of the original snapshot.</span></span>  
  
 <span data-ttu-id="07b01-114">マージ エージェントがパーティションを検証するときには、フィルター式で使用するすべての関数から返される値に対してパーティションを検証するだけなく、メタデータのクリーンアップ操作やスキーマ変更などの変更が行われる前に、その変更で無効になったスナップショットが生成されていたかどうかもチェックします。</span><span class="sxs-lookup"><span data-stu-id="07b01-114">When the Merge Agent validates a partition, in addition to validating the partition against the values returned by any functions used in filtering expressions, the agent also checks whether the snapshot was generated prior to changes that invalidate it, such as metadata cleanup operations or schema changes.</span></span> <span data-ttu-id="07b01-115">パーティション化されたスナップショットが古すぎる場合、マージ エージェントはエラーを返します。この場合は、現在の標準スナップショットに基づいてそのサブスクライバーのパーティション化されたスナップショットを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07b01-115">If a partitioned snapshot is too old, the Merge Agent will return an error and you must regenerate a partitioned snapshot for that Subscriber based on a current regular snapshot.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b01-116">参照</span><span class="sxs-lookup"><span data-stu-id="07b01-116">See Also</span></span>  
 <span data-ttu-id="07b01-117">[レプリケーション管理に関する FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="07b01-117">[Replication Administration FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="07b01-118">[レプリケーション管理のベストプラクティス](administration/best-practices-for-replication-administration.md) </span><span class="sxs-lookup"><span data-stu-id="07b01-118">[Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md) </span></span>  
 <span data-ttu-id="07b01-119">[サブスクリプションの再初期化](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="07b01-119">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 [<span data-ttu-id="07b01-120">レプリケートされたデータの検証</span><span class="sxs-lookup"><span data-stu-id="07b01-120">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
