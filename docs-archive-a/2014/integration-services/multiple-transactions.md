---
title: 複数のトランザクション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ff909c92a23c965047edc0fcf278e17e4c76d94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641060"
---
# <a name="multiple-transactions"></a><span data-ttu-id="9c978-102">複数のトランザクション</span><span class="sxs-lookup"><span data-stu-id="9c978-102">Multiple Transactions</span></span>
  <span data-ttu-id="9c978-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージでは、関連しないトランザクションをパッケージに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9c978-103">It is possible for a package to include unrelated transactions in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="9c978-104">入れ子になったコンテナー階層の中間にあるコンテナーでトランザクションがサポートされない場合、階層の上位または下位にあるコンテナーがトランザクションをサポートするように構成されている場合はそのコンテナーで別個のトランザクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="9c978-104">Any time a container in the middle of a nested container hierarchy does not support transactions, the containers above or below it in the hierarchy start separate transactions if they are configured to support transactions.</span></span> <span data-ttu-id="9c978-105">トランザクションは、入れ子になったコンテナー階層において最も内側のタスクから順にパッケージにコミットまたはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="9c978-105">The transactions commit or roll back in order from the innermost task in the nested container hierarchy to the package.</span></span> <span data-ttu-id="9c978-106">ただし、内側のトランザクションがコミットされた後、その外側のトランザクションが中止された場合は、内側のトランザクションをロールバックできません。</span><span class="sxs-lookup"><span data-stu-id="9c978-106">However, after the inner transaction commits, it does not roll back if an outer transaction is aborted.</span></span>

## <a name="illustration-of-multiple-transactions"></a><span data-ttu-id="9c978-107">複数のトランザクションの図</span><span class="sxs-lookup"><span data-stu-id="9c978-107">Illustration of Multiple Transactions</span></span>
 <span data-ttu-id="9c978-108">たとえば、パッケージにシーケンス コンテナーが含まれていて、このコンテナーは、それぞれの 2 つの SQL 実行タスクを含む 2 つの Foreach ループ コンテナーを保持しているとします。</span><span class="sxs-lookup"><span data-stu-id="9c978-108">For example, a package has a Sequence container that holds two Foreach Loop containers, and each container include two Execute SQL tasks.</span></span> <span data-ttu-id="9c978-109">シーケンス コンテナーはトランザクションをサポートします。Foreach ループ コンテナーはトランザクションをサポートしませんが、SQL 実行タスクはサポートします。</span><span class="sxs-lookup"><span data-stu-id="9c978-109">The Sequence container supports transactions, the Foreach Loop containers do not, and the Execute SQL tasks do.</span></span> <span data-ttu-id="9c978-110">この例では、各 SQL 実行タスクでそれぞれのトランザクションが開始され、シーケンス タスクのトランザクションが中止されてもロールバックされません。</span><span class="sxs-lookup"><span data-stu-id="9c978-110">In this example, each Execute SQL task would start its own transaction and would not roll back if the transaction on the Sequence task was aborted.</span></span>

 <span data-ttu-id="9c978-111">この場合、シーケンス コンテナーの TransactionOption プロパティ、Foreach ループ コンテナー、および SQL 実行タスクを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="9c978-111">The TransactionOption properties of the Sequence container, Foreach Loop container and the Execute SQL tasks are set as follows:</span></span>

-   <span data-ttu-id="9c978-112">シーケンス コンテナーの TransactionOption プロパティを **[Required]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9c978-112">The TransactionOption property of the Sequence container is set to **Required**.</span></span>

-   <span data-ttu-id="9c978-113">Foreach ループ コンテナーの TransactionOption プロパティを **[NotSupported]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9c978-113">The TransactionOption properties of the Foreach Loop containers are set to **NotSupported**.</span></span>

-   <span data-ttu-id="9c978-114">SQL 実行タスクの TransactionOption プロパティを **[Required]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9c978-114">The TransactionOption properties of the Execute SQL tasks are set to **Required**.</span></span>

 <span data-ttu-id="9c978-115">次の図は、パッケージ内の 5 つの関連しないトランザクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="9c978-115">The following diagram shows the five unrelated transactions in the package.</span></span> <span data-ttu-id="9c978-116">1 つのトランザクションはシーケンス コンテナーによって開始され、4 つのトランザクションは SQL 実行タスクによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="9c978-116">One transaction is started by the Sequence container and four transactions are started by the Execute SQL tasks.</span></span>

 <span data-ttu-id="9c978-117">![複数のトランザクションの実装](media/mw-dts-trans2.gif "複数のトランザクションの実装")</span><span class="sxs-lookup"><span data-stu-id="9c978-117">![Implementation of multiple transactions](media/mw-dts-trans2.gif "Implementation of multiple transactions")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="9c978-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9c978-118">Related Tasks</span></span>
 [<span data-ttu-id="9c978-119">トランザクションを使用するようにパッケージを構成する</span><span class="sxs-lookup"><span data-stu-id="9c978-119">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)


