---
title: トランザクションを使用するようにパッケージを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f469c2439deb2d16ac9046a1628e82c34e39b31d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713401"
---
# <a name="configure-a-package-to-use-transactions"></a><span data-ttu-id="b2c49-102">トランザクションを使用するようにパッケージを構成する</span><span class="sxs-lookup"><span data-stu-id="b2c49-102">Configure a Package to Use Transactions</span></span>
  <span data-ttu-id="b2c49-103">トランザクションを使用するようにパッケージを構成する場合、次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b2c49-103">When you configure a package to use transactions, you have two options:</span></span>  
  
-   <span data-ttu-id="b2c49-104">パッケージで 1 つのトランザクションを使用する。</span><span class="sxs-lookup"><span data-stu-id="b2c49-104">Have a single transaction for the package.</span></span> <span data-ttu-id="b2c49-105">この場合、このトランザクションを *開始* するのはパッケージ自体で、パッケージ内の個々のタスクやコンテナーはこの 1 つのトランザクションに参加します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-105">In this case, it is the package itself that *initiates* this transaction, whereas individual tasks and containers in the package participate in this single transaction.</span></span>  
  
-   <span data-ttu-id="b2c49-106">パッケージで複数のトランザクションを使用する。</span><span class="sxs-lookup"><span data-stu-id="b2c49-106">Have multiple transactions in the package.</span></span> <span data-ttu-id="b2c49-107">この場合、パッケージでトランザクションがサポートされますが、トランザクションを実際に開始するのはパッケージ内のタスクやコンテナーになります。</span><span class="sxs-lookup"><span data-stu-id="b2c49-107">In this case, the package supports transactions, but individual tasks and containers in the package actually initiate the transactions.</span></span>  
  
 <span data-ttu-id="b2c49-108">次の手順では、これらの 2 つのオプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-108">The following procedures describe how to configure both options.</span></span>  
  
## <a name="configuring-a-single-transaction"></a><span data-ttu-id="b2c49-109">1 つのトランザクションの構成</span><span class="sxs-lookup"><span data-stu-id="b2c49-109">Configuring a Single Transaction</span></span>  
 <span data-ttu-id="b2c49-110">このオプションでは、パッケージ自体が 1 つのトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-110">In this option, the package itself initiates a single transaction.</span></span> <span data-ttu-id="b2c49-111">パッケージの TransactionOption プロパティをに設定することによって、このトランザクションを開始するようにパッケージを構成し `Required` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-111">You configure the package to initiate this transaction by setting the TransactionOption property of the package to `Required`.</span></span>  
  
 <span data-ttu-id="b2c49-112">次に、この 1 つのトランザクションに特定のタスクやコンテナーを参加させます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-112">Next, you enlist specific tasks and containers in this single transaction.</span></span> <span data-ttu-id="b2c49-113">タスクまたはコンテナーをトランザクションに参加させるには、そのタスクまたはコンテナーの TransactionOption プロパティをに設定し `Supported` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-113">To enlist a task or container in a transaction, you set the TransactionOption property of that task or container to `Supported`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a><span data-ttu-id="b2c49-114">1 つのトランザクションを使用するようにパッケージを構成するには</span><span class="sxs-lookup"><span data-stu-id="b2c49-114">To configure a package to use a single transaction</span></span>  
  
1.  <span data-ttu-id="b2c49-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、トランザクションを使用するように構成するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use a transaction.</span></span>  
  
2.  <span data-ttu-id="b2c49-116">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b2c49-117">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c49-117">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="b2c49-118">制御フローのデザイン画面の背景で任意の場所を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c49-118">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="b2c49-119">[**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Required` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-119">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
6.  <span data-ttu-id="b2c49-120">**[制御フロー]** タブのデザイン画面で、トランザクションに登録するタスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c49-120">On the design surface of the **ControlFlow** tab, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="b2c49-121">[**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Supported` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-121">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2c49-122">トランザクションに接続を登録するには、トランザクションで接続を使用するタスクを登録します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-122">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="b2c49-123">詳細については、「[Integration Services (SSIS) の接続](connection-manager/integration-services-ssis-connections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2c49-123">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
8.  <span data-ttu-id="b2c49-124">トランザクションに登録する各タスクおよびコンテナーに対して、手順 6. と 7. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-124">Repeat steps 6 and 7 for each task and container that you want to enroll in the transaction.</span></span>  
  
## <a name="configuring-multiple-transactions"></a><span data-ttu-id="b2c49-125">複数のトランザクションの構成</span><span class="sxs-lookup"><span data-stu-id="b2c49-125">Configuring Multiple Transactions</span></span>  
 <span data-ttu-id="b2c49-126">このオプションでは、パッケージでトランザクションがサポートされますが、パッケージ自体はトランザクションを開始しません。</span><span class="sxs-lookup"><span data-stu-id="b2c49-126">In this option, the package itself supports transactions but does not start a transaction.</span></span> <span data-ttu-id="b2c49-127">トランザクションをサポートするようにパッケージを構成するには、パッケージの TransactionOption プロパティをに設定し `Supported` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-127">You configure the package to support transactions by setting the TransactionOption property of the package to `Supported`.</span></span>  
  
 <span data-ttu-id="b2c49-128">次に、トランザクションを開始するかトランザクションに参加するように、パッケージ内の目的のタスクおよびコンテナーを構成します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-128">Next, you configure the desired tasks and containers inside the package to initiate or participate in transactions.</span></span> <span data-ttu-id="b2c49-129">トランザクションを開始するようにタスクまたはコンテナーを構成するには、そのタスクまたはコンテナーの TransactionOption プロパティをに設定し `Required` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-129">To configure a task or container to initiate a transaction, you set the TransactionOption property of that task or container to `Required`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a><span data-ttu-id="b2c49-130">複数のトランザクションを使用するようにパッケージを構成するには</span><span class="sxs-lookup"><span data-stu-id="b2c49-130">To configure a package to use multiple transactions</span></span>  
  
1.  <span data-ttu-id="b2c49-131">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、複数のトランザクションを使用するように構成するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-131">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use transaction.s</span></span>  
  
2.  <span data-ttu-id="b2c49-132">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-132">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b2c49-133">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c49-133">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="b2c49-134">制御フローのデザイン画面の背景で任意の場所を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c49-134">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="b2c49-135">[**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Supported` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-135">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2c49-136">パッケージでトランザクションがサポートされますが、トランザクションは、パッケージ内のタスクまたはコンテナーによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-136">The package supports transactions, but the transactions are started by task or containers in the package.</span></span>  
  
6.  <span data-ttu-id="b2c49-137">**[制御フロー]** タブのデザイン画面で、トランザクションを開始するパッケージ内のタスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c49-137">On the design surface of the **ControlFlow** tab, right-click the task or the container in the package for which you want to start a transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="b2c49-138">[**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Required` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-138">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
8.  <span data-ttu-id="b2c49-139">トランザクションがコンテナーによって開始される場合、トランザクションに登録するタスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c49-139">If a transaction is started by a container, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
9. <span data-ttu-id="b2c49-140">[**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Supported` ます。</span><span class="sxs-lookup"><span data-stu-id="b2c49-140">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2c49-141">トランザクションに接続を登録するには、トランザクションで接続を使用するタスクを登録します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-141">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="b2c49-142">詳細については、「[Integration Services (SSIS) の接続](connection-manager/integration-services-ssis-connections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2c49-142">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
10. <span data-ttu-id="b2c49-143">トランザクションを開始する各タスクおよびコンテナーに対して、手順 6. ～ 9. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b2c49-143">Repeat steps 6 through 9 for each task and container that starts a transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c49-144">参照</span><span class="sxs-lookup"><span data-stu-id="b2c49-144">See Also</span></span>  
 [<span data-ttu-id="b2c49-145">Integration Services のトランザクション</span><span class="sxs-lookup"><span data-stu-id="b2c49-145">Integration Services Transactions</span></span>](integration-services-transactions.md)  
  
  
