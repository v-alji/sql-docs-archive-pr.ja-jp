---
title: Integration Services のトランザクション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], transactions
- transactions [Integration Services], about transactions in packages
- tasks [Integration Services], transactions
- transactions [Integration Services]
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0ee195bbcb7b9779111add4c1f2349816d5441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641116"
---
# <a name="integration-services-transactions"></a><span data-ttu-id="e55f2-102">Integration Services のトランザクション</span><span class="sxs-lookup"><span data-stu-id="e55f2-102">Integration Services Transactions</span></span>
  <span data-ttu-id="e55f2-103">パッケージではトランザクションを使用して、タスクがアトミック単位で実行するデータベース処理をバインドし、この処理によってデータの整合性を保ちます。</span><span class="sxs-lookup"><span data-stu-id="e55f2-103">Packages use transactions to bind the database actions that tasks perform into atomic units, and by doing this maintain data integrity.</span></span> <span data-ttu-id="e55f2-104">すべての種類の [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンテナー (パッケージ、For ループ コンテナー、Foreach ループ コンテナー、シーケンス コンテナー、タスクをカプセル化するタスク ホスト) でトランザクションを使用するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="e55f2-104">All [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types-packages, the For Loop, Foreach Loop, and Sequence containers, and the task hosts that encapsulate each task-can be configured to use transactions.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e55f2-105">には、トランザクションを設定するオプションとして、 **NotSupported**、 **Supported**、および **Required**の 3 つが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e55f2-105">provides three options for configuring transactions: **NotSupported**, **Supported**, and **Required**.</span></span>  
  
-   <span data-ttu-id="e55f2-106">**Required** は、親コンテナーで既に開始されているトランザクションがない限り、コンテナーでトランザクションを開始するように指定します。</span><span class="sxs-lookup"><span data-stu-id="e55f2-106">**Required** indicates that the container starts a transaction, unless one is already started by its parent container.</span></span> <span data-ttu-id="e55f2-107">開始されているトランザクションが存在する場合は、トランザクションが結合されます。</span><span class="sxs-lookup"><span data-stu-id="e55f2-107">If a transaction already exists, the container joins the transaction.</span></span> <span data-ttu-id="e55f2-108">たとえば、トランザクションをサポートするように設定されていないパッケージに **Required** オプションが設定されたシーケンス コンテナーが含まれている場合、シーケンス コンテナーは固有のトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="e55f2-108">For example, if a package that is not configured to support transactions includes a Sequence container that uses the **Required** option, the Sequence container would start its own transaction.</span></span> <span data-ttu-id="e55f2-109">パッケージが **Required** オプションを使用するように設定されている場合、シーケンス コンテナーはパッケージのトランザクションを結合します。</span><span class="sxs-lookup"><span data-stu-id="e55f2-109">If the package were configured to use the **Required** option, the Sequence container would join the package transaction.</span></span>  
  
-   <span data-ttu-id="e55f2-110">**Supported** は、コンテナーがトランザクションを開始せず、親コンテナーが開始したトランザクションを結合するように指定します。</span><span class="sxs-lookup"><span data-stu-id="e55f2-110">**Supported** indicates that the container does not start a transaction, but joins any transaction started by its parent container.</span></span> <span data-ttu-id="e55f2-111">たとえば、4 つの SQL 実行タスクがあるパッケージでトランザクションが開始され、4 つのタスクすべてに **Supported** オプションが設定されている場合、いずれかのタスクが失敗すると、SQL 実行タスクで実行されたデータベース更新すべてがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="e55f2-111">For example, if a package with four Execute SQL tasks starts a transaction and all four tasks use the **Supported** option, the database updates performed by the Execute SQL tasks are rolled back if any task fails.</span></span> <span data-ttu-id="e55f2-112">パッケージでトランザクションが開始されない場合、4 つの SQL 実行タスクはトランザクションによってバインドされないため、失敗したタスクで実行されたデータベース更新以外はロールバックされません。</span><span class="sxs-lookup"><span data-stu-id="e55f2-112">If the package does not start a transaction, the four Execute SQL tasks are not bound by a transaction, and no database updates except the ones performed by the failed task are rolled back.</span></span>  
  
-   <span data-ttu-id="e55f2-113">**NotSupported** は、コンテナーがトランザクションを開始せず、既存のトランザクションも結合しないように指定します。</span><span class="sxs-lookup"><span data-stu-id="e55f2-113">**NotSupported** indicates that the container does not start a transaction or join an existing transaction.</span></span> <span data-ttu-id="e55f2-114">親コンテナーで開始されたトランザクションは、トランザクションをサポートしないように設定された子コンテナーに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="e55f2-114">A transaction started by a parent container does not affect child containers that have been configured to not support transactions.</span></span> <span data-ttu-id="e55f2-115">たとえば、トランザクションを開始するように設定されたパッケージに **NotSupported** オプションが設定された For ループ コンテナーが含まれていた場合、For ループのタスクが失敗してもロールバックは行われません。</span><span class="sxs-lookup"><span data-stu-id="e55f2-115">For example, if a package is configured to start a transaction and a For Loop container in the package uses the **NotSupported** option, none of the tasks in the For Loop can roll back if they fail.</span></span>  
  
 <span data-ttu-id="e55f2-116">トランザクションの設定は、コンテナーの TransactionOption プロパティで設定します。</span><span class="sxs-lookup"><span data-stu-id="e55f2-116">You configure transactions by setting the TransactionOption property on the container.</span></span> <span data-ttu-id="e55f2-117">このプロパティは、 **の [** プロパティ [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]] ウィンドウを使用して、またはプログラムによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="e55f2-117">You can set this property by using the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], or you can set the property programmatically.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e55f2-118">`TransactionOption` プロパティは、コンテナーによって要求された `IsolationLevel` プロパティの値が適用されるかどうかに影響します。</span><span class="sxs-lookup"><span data-stu-id="e55f2-118">The `TransactionOption` property influences whether or not the value of the `IsolationLevel` property requested by a container is applied.</span></span> <span data-ttu-id="e55f2-119">詳細については、「パッケージのプロパティの設定」のプロパティの説明を参照してください `IsolationLevel` 。 [Setting Package Properties](set-package-properties.md)</span><span class="sxs-lookup"><span data-stu-id="e55f2-119">For more information, see the description of the `IsolationLevel` property in the topic, [Setting Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-configure-a-package-to-use-transactions"></a><span data-ttu-id="e55f2-120">パッケージでトランザクションを使用するように設定するには</span><span class="sxs-lookup"><span data-stu-id="e55f2-120">To configure a package to use transactions</span></span>  
  
-   [<span data-ttu-id="e55f2-121">トランザクションを使用するようにパッケージを構成する</span><span class="sxs-lookup"><span data-stu-id="e55f2-121">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
## <a name="external-resources"></a><span data-ttu-id="e55f2-122">外部リソース</span><span class="sxs-lookup"><span data-stu-id="e55f2-122">External Resources</span></span>  
  
-   <span data-ttu-id="e55f2-123">www.mssqltips.com のブログ [「SQL Server Integration Services (SSIS) でトランザクションを使用する方法」](https://go.microsoft.com/fwlink/?LinkId=157783)</span><span class="sxs-lookup"><span data-stu-id="e55f2-123">Blog entry, [How to Use Transactions in SQL Server Integration Services SSIS](https://go.microsoft.com/fwlink/?LinkId=157783), on www.mssqltips.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55f2-124">参照</span><span class="sxs-lookup"><span data-stu-id="e55f2-124">See Also</span></span>  
 <span data-ttu-id="e55f2-125">[継承されたトランザクション](../../2014/integration-services/inherited-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="e55f2-125">[Inherited Transactions](../../2014/integration-services/inherited-transactions.md) </span></span>  
 [<span data-ttu-id="e55f2-126">複数のトランザクション</span><span class="sxs-lookup"><span data-stu-id="e55f2-126">Multiple Transactions</span></span>](../../2014/integration-services/multiple-transactions.md)  
  
  
