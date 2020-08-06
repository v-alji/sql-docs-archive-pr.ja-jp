---
title: バッチ操作の実行 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69899077cf534482879accbf10640f6295e3866a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632770"
---
# <a name="performing-batch-operations-xmla"></a><span data-ttu-id="96f91-102">バッチ操作の実行 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="96f91-102">Performing Batch Operations (XMLA)</span></span>
  <span data-ttu-id="96f91-103">XML for Analysis (XMLA) の[Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)コマンドを使用して、1つの xmla [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドを使用して複数の xmla コマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="96f91-103">You can use the [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) command in XML for Analysis (XMLA) to run multiple XMLA commands using a single XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span> <span data-ttu-id="96f91-104">`Batch` コマンドに含まれる複数のコマンドは、単一のトランザクションとして実行することも、あるいはコマンドごとに別個のトランザクションとして直列または並列で実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="96f91-104">You can run multiple commands contained in the `Batch` command either as a single transaction or in individual transactions for each command, in serial or in parallel.</span></span> <span data-ttu-id="96f91-105">また、不一致バインドや、複数のオブジェクトを処理するためのその他のプロパティをコマンドで指定することもでき `Batch` [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="96f91-105">You can also specify out-of-line bindings and other properties in the `Batch` command for processing multiple [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a><span data-ttu-id="96f91-106">トランザクションおよび非トランザクション バッチ コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="96f91-106">Running Transactional and Nontransactional Batch Commands</span></span>  
 <span data-ttu-id="96f91-107">`Batch` コマンドは、コマンドを以下の 2 つのいずれかの方法で実行します。</span><span class="sxs-lookup"><span data-stu-id="96f91-107">The `Batch` command executes commands in one of two ways:</span></span>  
  
 <span data-ttu-id="96f91-108">**トランザクション**</span><span class="sxs-lookup"><span data-stu-id="96f91-108">**Transactional**</span></span>  
 <span data-ttu-id="96f91-109">`Transaction`コマンドの属性が true に設定されている場合、コマンドは、コマンド `Batch` `Batch` に含まれるすべてのコマンドを `Batch` 1 つのトランザクション (*トランザクション*バッチ) で実行します。</span><span class="sxs-lookup"><span data-stu-id="96f91-109">If the `Transaction` attribute of the `Batch` command is set to true, the `Batch` command run commands all of the commands contained by the `Batch` command in a single transaction-a *transactional* batch.</span></span>  
  
 <span data-ttu-id="96f91-110">トランザクションバッチ内のいずれかのコマンドが失敗した場合、は、失敗したコマンドの前に実行されたコマンド [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 内のすべてのコマンドをロールバックし、 `Batch` `Batch` コマンドはすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="96f91-110">If any command fails in a transactional batch, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rolls back any command in the `Batch` command that ran before the command that failed and the `Batch` command immediately ends.</span></span> <span data-ttu-id="96f91-111">`Batch` コマンド内でまだ実行されていないコマンドはいずれも実行されません。</span><span class="sxs-lookup"><span data-stu-id="96f91-111">Any commands in the `Batch` command that have not yet run are not executed.</span></span> <span data-ttu-id="96f91-112">`Batch` コマンドが終了した後、`Batch` コマンドは失敗したコマンドについて発生したすべてのエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="96f91-112">After the `Batch` command ends, the `Batch` command reports any errors that occurred for the failed command.</span></span>  
  
 <span data-ttu-id="96f91-113">**非トランザクション**</span><span class="sxs-lookup"><span data-stu-id="96f91-113">**Nontransactional**</span></span>  
 <span data-ttu-id="96f91-114">`Transaction`属性が false に設定されている場合、コマンドはコマンド `Batch` に含まれる各コマンドを `Batch` 別のトランザクション (*非トランザクション*バッチ) で実行します。</span><span class="sxs-lookup"><span data-stu-id="96f91-114">If the `Transaction` attribute is set to false, the `Batch` command runs each command contained by the `Batch` command in a separate transaction-a *nontransactional* batch.</span></span> <span data-ttu-id="96f91-115">非トランザクション バッチ内のいずれかのコマンドが失敗した場合、`Batch` コマンドは、失敗したコマンドの後にあるコマンドの実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="96f91-115">If any command fails in a nontransactional batch, the `Batch` command continues to run commands after the command which failed.</span></span> <span data-ttu-id="96f91-116">`Batch` コマンドが、`Batch` コマンドに含まれるすべてのコマンドの実行を試みた後、`Batch` コマンドは発生したすべてのエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="96f91-116">After the `Batch` command tries to run all the commands that the `Batch` command contains, the `Batch` command reports any errors that occurred.</span></span>  
  
 <span data-ttu-id="96f91-117">`Batch` コマンドに含まれるコマンドが返す結果はすべて、それらのコマンドが `Batch` コマンド内に含まれている順序と同じ順序で返されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-117">All results returned by commands contained in a `Batch` command are returned in the same order in which the commands are contained in the `Batch` command.</span></span> <span data-ttu-id="96f91-118">`Batch` コマンドによって返される結果は、`Batch` コマンドがトランザクション バッチまたは非トランザクション バッチのいずれであるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="96f91-118">The results returned by a `Batch` command vary based on whether the `Batch` command is transactional or nontransactional.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96f91-119">コマンドに `Batch` [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)コマンドなどの出力を返さないコマンドが含まれており、そのコマンドが正常に実行された場合、 `Batch` コマンドは結果要素内の空の[ルート](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)要素を返します。</span><span class="sxs-lookup"><span data-stu-id="96f91-119">If a `Batch` command contains a command that does not return output, such as the [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) command, and that command successfully runs, the `Batch` command returns an empty [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) element within the results element.</span></span> <span data-ttu-id="96f91-120">空の `root` 要素があることにより、`Batch` コマンドに含まれるそれぞれのコマンドが、そのコマンドの結果の適切な `root` 要素と確実に対応します。</span><span class="sxs-lookup"><span data-stu-id="96f91-120">The empty `root` element ensures that each command contained in a `Batch` command can be matched with the appropriate `root` element for that command's results.</span></span>  
  
### <a name="returning-results-from-transactional-batch-results"></a><span data-ttu-id="96f91-121">トランザクション バッチの結果から結果を返す処理</span><span class="sxs-lookup"><span data-stu-id="96f91-121">Returning Results from Transactional Batch Results</span></span>  
 <span data-ttu-id="96f91-122">トランザクション バッチ内で実行されたコマンドの結果は、`Batch` コマンド全体が完了するまで返されません。</span><span class="sxs-lookup"><span data-stu-id="96f91-122">Results from commands run within a transactional batch are not returned until the entire `Batch` command is completed.</span></span> <span data-ttu-id="96f91-123">それぞれのコマンドが実行された後に結果が返されないのは、トランザクション バッチ内のいずれかのコマンドが失敗すれば、`Batch` コマンド全体、および含まれるすべてのコマンドがロールバックされるためです。</span><span class="sxs-lookup"><span data-stu-id="96f91-123">The results are not returned after each command runs because any command that fails within a transactional batch would cause the entire `Batch` command and all containing commands to be rolled back.</span></span> <span data-ttu-id="96f91-124">すべてのコマンドが開始され、正常に実行されると、コマンドのメソッドによって返される[ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse)要素の[return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla)要素には `Execute` `Batch` 1 つの[結果](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla)要素が含まれます。この要素には `root` 、コマンドに含まれる正常に実行されたコマンドごとに1つの要素が含まれ `Batch` ます。</span><span class="sxs-lookup"><span data-stu-id="96f91-124">If all commands start and run successfully, the [return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) element of the [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) element returned by the `Execute` method for the `Batch` command contains one [results](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) element, which in turn contains one `root` element for each successfully run command contained in the `Batch` command.</span></span> <span data-ttu-id="96f91-125">`Batch` コマンド内のいずれかのコマンドが起動できない場合、または完了に失敗した場合、`Execute` メソッドは、失敗したコマンドのエラーを含む SOAP エラーを `Batch` コマンドについて返します。</span><span class="sxs-lookup"><span data-stu-id="96f91-125">If any command in the `Batch` command cannot be started or fails to complete, the `Execute` method returns a SOAP fault for the `Batch` command that contains the error of the command that failed.</span></span>  
  
### <a name="returning-results-from-nontransactional-batch-results"></a><span data-ttu-id="96f91-126">非トランザクション バッチの結果から結果を返す処理</span><span class="sxs-lookup"><span data-stu-id="96f91-126">Returning Results from Nontransactional Batch Results</span></span>  
 <span data-ttu-id="96f91-127">非トランザクション バッチ内のコマンドによる結果は、それらのコマンドが `Batch` コマンド内に含まれている順序で、各コマンドごとに返されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-127">Results from commands run within a nontransactional batch are returned in the order in which the commands are contained within the `Batch` command and as they are returned by each command.</span></span> <span data-ttu-id="96f91-128">`Batch` コマンド内のいずれのコマンドも正常に起動できなかった場合、`Execute` メソッドは、その `Batch` コマンドについてのエラーを含む SOAP エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="96f91-128">If no command contained in the `Batch` command can be successfully started, the `Execute` method returns a SOAP fault that contains an error for the `Batch` command.</span></span> <span data-ttu-id="96f91-129">少なくとも 1 つのコマンドが正常に起動された場合、その `return` コマンドに対する `ExecuteResponse` メソッドによって返される `Execute` 要素の `Batch` 要素には、1 つの `results` 要素が含まれます。この要素には、`root` コマンドに含まれる各コマンドに対して 1 つの `Batch` 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96f91-129">If at least one command is successfully started, the `return` element of the `ExecuteResponse` element returned by the `Execute` method for the `Batch` command contains one `results` element, which in turn contains one `root` element for each command contained in the `Batch` command.</span></span> <span data-ttu-id="96f91-130">非トランザクションバッチ内の1つ以上のコマンドを開始できない場合、または完了できなかった場合、 `root` その失敗したコマンドの要素にはエラーを説明する[error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="96f91-130">If one or more commands in a nontransactional batch cannot be started or fails to complete, the `root` element for that failed command contains an [error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) element describing the error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96f91-131">非トランザクション バッチ内の少なくとも 1 つのコマンドが起動できれば、その非トランザクション バッチに含まれるすべてのコマンドが `Batch` コマンドの結果にエラーを返した場合であっても、その非トランザクション バッチは正常に実行されたものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="96f91-131">As long as at least one command in a nontransactional batch can be started, the nontransactional batch is considered to have successfully run, even if every command contained in the nontransactional batch returns an error in the results of the `Batch` command.</span></span>  
  
## <a name="using-serial-and-parallel-execution"></a><span data-ttu-id="96f91-132">直列および並列実行の使用</span><span class="sxs-lookup"><span data-stu-id="96f91-132">Using Serial and Parallel Execution</span></span>  
 <span data-ttu-id="96f91-133">`Batch` コマンドでは、含まれるコマンドを直列または並列で実行することができます。</span><span class="sxs-lookup"><span data-stu-id="96f91-133">You can use the `Batch` command to run included commands in serial or in parallel.</span></span> <span data-ttu-id="96f91-134">コマンドが直列に実行される場合、`Batch` コマンド内に含まれる次のコマンドは、`Batch` コマンド内で現在実行中のコマンドが完了するまで起動できません。</span><span class="sxs-lookup"><span data-stu-id="96f91-134">When the commands are run in serial, the next command included in the `Batch` command cannot start until the currently running command in the `Batch` command is completed.</span></span> <span data-ttu-id="96f91-135">コマンドが並列で実行される場合、`Batch` によって複数のコマンドを同時に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="96f91-135">When the commands are run in parallel, multiple commands can be executed simultaneously by the `Batch` command.</span></span>  
  
 <span data-ttu-id="96f91-136">コマンドを並列実行するには、コマンドの[parallel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla)プロパティに並列で実行されるコマンドを追加し `Batch` ます。</span><span class="sxs-lookup"><span data-stu-id="96f91-136">To run commands in parallel, you add the commands to be run in parallel to the [Parallel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) property of the `Batch` command.</span></span> <span data-ttu-id="96f91-137">現在、で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、連続したシーケンシャル[プロセス](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)コマンドのみ並列実行できます。</span><span class="sxs-lookup"><span data-stu-id="96f91-137">Currently, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] can run only contiguous, sequential [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) commands in parallel.</span></span> <span data-ttu-id="96f91-138">[Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)や[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)など、プロパティに含まれるその他の XMLA コマンド `Parallel` は、順次実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-138">Any other XMLA command, such as [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) or [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), included in the `Parallel` property is run serially.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="96f91-139">は、`Process` プロパティに含まれるすべての `Parallel` コマンドの並列実行を試みますが、すべての `Process` コマンドが並列で実行されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="96f91-139">tries to run all `Process` commands included in the `Parallel` property in parallel, but cannot guarantee that all included `Process` commands can be run in parallel.</span></span> <span data-ttu-id="96f91-140">各 `Process` コマンドはインスタンスによって分析され、並列で実行できないとインスタンスが判断した `Process` コマンドは直列に実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-140">The instance analyzes each `Process` command and, if the instance determines that the command cannot be run in parallel, the `Process` command is run in serial.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96f91-141">コマンドを並行で実行する場合は、`Transaction` コマンドの `Batch` 属性を true に設定する必要があります。これは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってサポートされるアクティブなトランザクションは接続ごとに 1 つだけであるのに対し、非トランザクション バッチは各コマンドを個別のトランザクションで実行するためです。</span><span class="sxs-lookup"><span data-stu-id="96f91-141">To run commands in parallel, the `Transaction` attribute of the `Batch` command must be set to true because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports only one active transaction per connection and nontransactional batches run each command in a separate transaction.</span></span> <span data-ttu-id="96f91-142">非トランザクション バッチに `Parallel` プロパティを含めると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="96f91-142">If you include the `Parallel` property in a nontransactional batch, an error occurs.</span></span>  
  
### <a name="limiting-parallel-execution"></a><span data-ttu-id="96f91-143">並列実行の制限</span><span class="sxs-lookup"><span data-stu-id="96f91-143">Limiting Parallel Execution</span></span>  
 <span data-ttu-id="96f91-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、インスタンスが実行されているコンピューターの制限範囲で、可能な限り多くの `Process` コマンドを並列で実行しようとします。</span><span class="sxs-lookup"><span data-stu-id="96f91-144">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance tries to run as many `Process` commands in parallel as possible, up to the limits of the computer on which the instance runs.</span></span> <span data-ttu-id="96f91-145">同時に実行する `Process` コマンドの数は、`maxParallel` プロパティの `Parallel` 属性を、並列で実行できる `Process` コマンドの最大数を示す値に設定することにより制限できます。</span><span class="sxs-lookup"><span data-stu-id="96f91-145">You can limit the number of concurrently executing `Process` commands by setting the `maxParallel` attribute of the `Parallel` property to a value indicating the maximum number of `Process` commands that can be run in parallel.</span></span>  
  
 <span data-ttu-id="96f91-146">たとえば、`Parallel` プロパティに以下の順序でコマンドが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="96f91-146">For example, a `Parallel` property contains the following commands in the sequence listed:</span></span>  
  
1.  `Create`  
  
2.  `Process`  
  
3.  `Alter`  
  
4.  `Process`  
  
5.  `Process`  
  
6.  `Process`  
  
7.  `Delete`  
  
8.  `Process`  
  
9. `Process`  
  
 <span data-ttu-id="96f91-147">この `maxParalle` プロパティの `Parallel` 属性は 2 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="96f91-147">The `maxParalle`l attribute of this `Parallel` property is set to 2.</span></span> <span data-ttu-id="96f91-148">そのため、インスタンスは上のコマンドの一覧を以下の説明のとおりに実行します。</span><span class="sxs-lookup"><span data-stu-id="96f91-148">Therefore, the instance runs the previous lists of commands as described in the following list:</span></span>  
  
-   <span data-ttu-id="96f91-149">コマンド 1 は直列に実行されます。コマンド 1 は `Create` コマンドであり、並列で実行できるのは `Process` コマンドだけであるためです。</span><span class="sxs-lookup"><span data-stu-id="96f91-149">Command 1 runs serially because command 1 is a `Create` command and only `Process` commands can be run in parallel.</span></span>  
  
-   <span data-ttu-id="96f91-150">コマンド1が完了すると、コマンド2は順次実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-150">Command 2 runs serially after command 1 is completed.</span></span>  
  
-   <span data-ttu-id="96f91-151">コマンド3は、コマンド2が完了した後に順次実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-151">Command 3 runs serially after command 2 is completed.</span></span>  
  
-   <span data-ttu-id="96f91-152">コマンド3が完了した後、コマンド4および5が並列で実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-152">Commands 4 and 5 run in parallel after command 3 is completed.</span></span> <span data-ttu-id="96f91-153">コマンド 6 も `Process` コマンドですが、`maxParallel` プロパティが 2 に設定されているため、コマンド 6 がコマンド 4 と 5 と共に並行で実行されることはありません。</span><span class="sxs-lookup"><span data-stu-id="96f91-153">Although command 6 is also a `Process` command, command 6 cannot run in parallel with commands 4 and 5 because the `maxParallel` property is set to 2.</span></span>  
  
-   <span data-ttu-id="96f91-154">コマンド 6 は、コマンド 4 とコマンド 5 の両方が完了した後に直列に実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-154">Command 6 runs serially after both commands 4 and 5 are completed.</span></span>  
  
-   <span data-ttu-id="96f91-155">コマンド 7 はコマンド 6 の完了後に直列に実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-155">Command 7 runs serially after command 6 is completed.</span></span>  
  
-   <span data-ttu-id="96f91-156">コマンド 8 と 9 はコマンド 7 の完了後に並列で実行されます。</span><span class="sxs-lookup"><span data-stu-id="96f91-156">Commands 8 and 9 run in parallel after command 7 is completed.</span></span>  
  
## <a name="using-the-batch-command-to-process-objects"></a><span data-ttu-id="96f91-157">バッチ コマンドを使用したオブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="96f91-157">Using the Batch Command to Process Objects</span></span>  
 <span data-ttu-id="96f91-158">`Batch` コマンドには、複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理をサポートするために特に用意された、以下の省略可能なプロパティおよび属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96f91-158">The `Batch` command contains several optional properties and attributes specifically included to support processing multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects:</span></span>  
  
-   <span data-ttu-id="96f91-159">`ProcessAffectedObjects` コマンドの `Batch` 属性は、指定したオブジェクトを処理する `Process` コマンドに含まれる `Batch` コマンドの結果、再処理が必要になったオブジェクトがある場合に、インスタンスがそれらのオブジェクトも処理するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="96f91-159">The `ProcessAffectedObjects` attribute of the `Batch` command indicates whether the instance should also process any object that requires reprocessing as a result of a `Process` command included in the `Batch` command processing a specified object.</span></span>  
  
-   <span data-ttu-id="96f91-160">[Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)プロパティには、コマンド内のすべてのコマンドで使用される不一致バインドのコレクションが含まれてい `Process` `Batch` ます。</span><span class="sxs-lookup"><span data-stu-id="96f91-160">The [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) property contains a collection of out-of-line bindings used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="96f91-161">[DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)プロパティには、コマンド内のすべてのコマンドで使用されるデータソースの不一致バインドが含まれてい `Process` `Batch` ます。</span><span class="sxs-lookup"><span data-stu-id="96f91-161">The [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) property contains an out-of-line binding for a data source used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="96f91-162">[DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)プロパティには、コマンド内のすべてのコマンドで使用されるデータソースビューの不一致バインドが含まれてい `Process` `Batch` ます。</span><span class="sxs-lookup"><span data-stu-id="96f91-162">The [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) property contains an out-of-line binding for a data source view used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="96f91-163">[Errorconfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)プロパティは、コマンド `Batch` に含まれるすべてのコマンドで発生したエラーをコマンドが処理する方法を指定し `Process` `Batch` ます。</span><span class="sxs-lookup"><span data-stu-id="96f91-163">The [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) property specifies the way in which the `Batch` command handles errors encountered by all `Process` commands contained in the `Batch` command.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="96f91-164">`Process` コマンドが `Bindings` コマンドに含まれている場合、その `DataSource` コマンドには `DataSourceView`、`ErrorConfiguration`、`Process`、および `Batch` プロパティを含めることができません。</span><span class="sxs-lookup"><span data-stu-id="96f91-164">A `Process` command cannot include the `Bindings`, `DataSource`, `DataSourceView`, or `ErrorConfiguration` properties, if the `Process` command is contained in a `Batch` command.</span></span> <span data-ttu-id="96f91-165">`Process` コマンドにこれらのプロパティを含める必要がある場合、その `Batch` コマンドを含む `Process` の対応するプロパティに、必要な情報を指定してください。</span><span class="sxs-lookup"><span data-stu-id="96f91-165">If you must specify these properties for a `Process` command, provide the necessary information in the corresponding properties of the `Batch` command that contains the `Process` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f91-166">参照</span><span class="sxs-lookup"><span data-stu-id="96f91-166">See Also</span></span>  
 <span data-ttu-id="96f91-167">[XMLA&#41;&#40;のバッチ要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="96f91-167">[Batch Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) </span></span>  
 <span data-ttu-id="96f91-168">[XMLA&#41;&#40;プロセス要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="96f91-168">[Process Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) </span></span>  
 <span data-ttu-id="96f91-169">[多次元モデルオブジェクトの処理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="96f91-169">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="96f91-170">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="96f91-170">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  