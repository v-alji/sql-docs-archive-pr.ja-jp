---
title: データベースのロックおよびロック解除 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96afa94f7c9c20072ae88b09a436d079ce0478ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720367"
---
# <a name="locking-and-unlocking-databases-xmla"></a><span data-ttu-id="1d72a-102">データベースのロックおよびロック解除 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="1d72a-102">Locking and Unlocking Databases (XMLA)</span></span>
  <span data-ttu-id="1d72a-103">データベースのロックおよびロック解除を行うには、それぞれ XML for Analysis (XMLA) の[ロック](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)およびロック[解除](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1d72a-103">You can lock and unlock databases using, respectively, the [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) and [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) commands in XML for Analysis (XMLA).</span></span> <span data-ttu-id="1d72a-104">通常、他の XMLA コマンドは、実行時にコマンドを完了させる必要に応じて、自動的にオブジェクトをロック/ロック解除します。</span><span class="sxs-lookup"><span data-stu-id="1d72a-104">Typically, other XMLA commands automatically lock and unlock objects as needed to complete the command during execution.</span></span> <span data-ttu-id="1d72a-105">データベースを明示的にロックまたはロック解除して、[バッチ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)コマンドなどの1つのトランザクション内で複数のコマンドを実行し、他のアプリケーションが書き込みトランザクションをデータベースにコミットするのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="1d72a-105">You can explicitly lock or unlock a database to perform multiple commands within a single transaction, such as a [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) command, while preventing other applications from committing a write transaction to the database.</span></span>  
  
## <a name="locking-databases"></a><span data-ttu-id="1d72a-106">データベースのロック</span><span class="sxs-lookup"><span data-stu-id="1d72a-106">Locking Databases</span></span>  
 <span data-ttu-id="1d72a-107">`Lock` コマンドは、現在アクティブなトランザクションのコンテキスト内で、共有オブジェクトまたは排他的に使用されるオブジェクトをロックします。</span><span class="sxs-lookup"><span data-stu-id="1d72a-107">The `Lock` command locks an object, either for shared or exclusive use, within the context of the currently active transaction.</span></span> <span data-ttu-id="1d72a-108">オブジェクトをロックすると、そのロックが解除されるまでトランザクションはコミットできません。</span><span class="sxs-lookup"><span data-stu-id="1d72a-108">A lock on an object prevents transactions from committing until the lock is removed.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="1d72a-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、共有ロックと排他ロックの2種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1d72a-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports two types of locks, shared locks and exclusive locks.</span></span> <span data-ttu-id="1d72a-110">でサポートされるロックの種類の詳細につい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ては、「 [Mode 要素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d72a-110">For more information about the lock types supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Mode Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="1d72a-111">では、データベースに対するロックだけが可能です。</span><span class="sxs-lookup"><span data-stu-id="1d72a-111">allows only databases to be locked.</span></span> <span data-ttu-id="1d72a-112">[Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)要素には、データベースへのオブジェクト参照が含まれている必要があり [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1d72a-112">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) element must contain an object reference to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="1d72a-113">`Object` 要素が指定されていない場合、またはデータベース以外のオブジェクトを `Object` 要素が参照している場合には、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1d72a-113">If the `Object` element is not specified or if the `Object` element refers to an object other than a database, an error occurs.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1d72a-114">`Lock` コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけです。</span><span class="sxs-lookup"><span data-stu-id="1d72a-114">Only database administrators or server administrators can explicitly issue a `Lock` command.</span></span>  
  
 <span data-ttu-id="1d72a-115">他のコマンドは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに対する `Lock` コマンドを暗黙的に発行します。</span><span class="sxs-lookup"><span data-stu-id="1d72a-115">Other commands implicitly issue a `Lock` command on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="1d72a-116">データベースからデータまたはメタデータを読み取るすべての操作 ( [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)メソッドや[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを実行する[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドなど) は、データベースの共有ロックを暗黙的に発行します。</span><span class="sxs-lookup"><span data-stu-id="1d72a-116">Any operation that reads data or metadata from a database, such as any [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method or an [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method running a [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command, implicitly issues a shared lock on the database.</span></span> <span data-ttu-id="1d72a-117">データベース上のオブジェクトに対してデータまたはメタデータの変更をコミットするトランザクション [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ( `Execute` [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)コマンドを実行するメソッドなど) は、データベースに対する排他ロックを暗黙的に発行します。</span><span class="sxs-lookup"><span data-stu-id="1d72a-117">Any transaction that commits changes in data or metadata to an object on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as an `Execute` method running an [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command, implicitly issues an exclusive lock on the database.</span></span>  
  
## <a name="unlocking-objects"></a><span data-ttu-id="1d72a-118">データベースのロック解除</span><span class="sxs-lookup"><span data-stu-id="1d72a-118">Unlocking Objects</span></span>  
 <span data-ttu-id="1d72a-119">`Unlock` コマンドは、現在アクティブなトランザクションのコンテキスト内で確立されたロックを解除します。</span><span class="sxs-lookup"><span data-stu-id="1d72a-119">The `Unlock` command removes a lock established within the context of the currently active transaction.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1d72a-120">コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけ `Unlock` です。</span><span class="sxs-lookup"><span data-stu-id="1d72a-120">Only database administrators or server administrators can explicitly issue an `Unlock` command.</span></span>  
  
 <span data-ttu-id="1d72a-121">すべてのロックは、現在のトランザクションのコンテキスト内で保持されます。</span><span class="sxs-lookup"><span data-stu-id="1d72a-121">All locks are held in the context of the current transaction.</span></span> <span data-ttu-id="1d72a-122">現在のトランザクションがコミットまたはロールバックされると、そのトランザクション内で定義されたすべてのロックは自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="1d72a-122">When the current transaction is committed or rolled back, all locks defined within the transaction are automatically released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d72a-123">参照</span><span class="sxs-lookup"><span data-stu-id="1d72a-123">See Also</span></span>  
 <span data-ttu-id="1d72a-124">[XMLA&#41;&#40;Lock 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="1d72a-124">[Lock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 <span data-ttu-id="1d72a-125">[XMLA の &#40;要素のロックを解除&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="1d72a-125">[Unlock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 [<span data-ttu-id="1d72a-126">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="1d72a-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
