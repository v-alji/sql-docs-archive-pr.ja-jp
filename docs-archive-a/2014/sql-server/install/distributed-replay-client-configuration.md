---
title: 分散再生クライアントの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 53124029483c25ed7894b279283e1de02c647350
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645368"
---
# <a name="distributed-replay-client-configuration"></a><span data-ttu-id="3aa47-102">分散再生クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="3aa47-102">Distributed Replay Client Configuration</span></span>
  <span data-ttu-id="3aa47-103">**インストール ウィザードの** [分散再生クライアントの構成] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページを使用して、分散再生クライアント サービスに対する管理権限を付与するユーザーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa47-103">Use the **Distributed Replay Client Configuration** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the users you want to grant administrative permissions to for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="3aa47-104">管理権限を持つユーザーには、分散再生クライアント サービスへの無制限のアクセス許可が与えられます。</span><span class="sxs-lookup"><span data-stu-id="3aa47-104">Users that have administrative permissions will have unlimited access to the Distributed Replay client service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3aa47-105">Options</span><span class="sxs-lookup"><span data-stu-id="3aa47-105">Options</span></span>  
 <span data-ttu-id="3aa47-106">**[コントローラー名]**</span><span class="sxs-lookup"><span data-stu-id="3aa47-106">**Controller Name**</span></span>  
 <span data-ttu-id="3aa47-107">これは省略可能なパラメーターで、既定値は \<*blank*> です。</span><span class="sxs-lookup"><span data-stu-id="3aa47-107">This is an optional parameter, and the default value is \<*blank*>.</span></span>  
  
 <span data-ttu-id="3aa47-108">分散再生クライアント サービスと通信するクライアント コンピューターであるコントローラーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3aa47-108">Enter the name of the controller that the client computer will communicate with for the Distributed Replay client service.</span></span> <span data-ttu-id="3aa47-109">次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3aa47-109">Note the following:</span></span>  
  
-   <span data-ttu-id="3aa47-110">名前は完全修飾ドメイン名 (FQDN) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3aa47-110">The name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="3aa47-111">たとえば、Microsoft の製品階層の server1 というホストに、server1.products.microsoft.com という FQDN を設定できます。</span><span class="sxs-lookup"><span data-stu-id="3aa47-111">For example, a host called server1 in the products hierarchy at Microsoft may have an FQDN of server1.products.microsoft.com.</span></span>  
  
-   <span data-ttu-id="3aa47-112">コントローラーを既にセットアップしてある場合は、各クライアントを構成するときにコントローラーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3aa47-112">If you have already set up a controller, enter the name of the controller while configuring each client.</span></span>  
  
-   <span data-ttu-id="3aa47-113">コントローラーをまだセットアップしていない場合は、コントローラー名を空白にしておくことができます。</span><span class="sxs-lookup"><span data-stu-id="3aa47-113">If you have net yet set up a controller, you can leave the controller name blank.</span></span> <span data-ttu-id="3aa47-114">ただし、コントローラー名を **クライアント構成** ファイルに手動で入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3aa47-114">However, you must manually enter the controller name in the **client configuration** file.</span></span>  
  
 <span data-ttu-id="3aa47-115">**作業ディレクトリ**</span><span class="sxs-lookup"><span data-stu-id="3aa47-115">**Working Directory**</span></span>  
 <span data-ttu-id="3aa47-116">分散再生クライアント サービス用の作業ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa47-116">Specify the working directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="3aa47-117">既定の作業ディレクトリは、\<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\ です。</span><span class="sxs-lookup"><span data-stu-id="3aa47-117">The default working directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.</span></span>  
  
 <span data-ttu-id="3aa47-118">**[結果ディレクトリ]**</span><span class="sxs-lookup"><span data-stu-id="3aa47-118">**Result Directory**</span></span>  
 <span data-ttu-id="3aa47-119">分散再生クライアント サービス用の結果ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa47-119">Specify the result directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="3aa47-120">既定の結果ディレクトリは、\<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\ です。</span><span class="sxs-lookup"><span data-stu-id="3aa47-120">The default result directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.</span></span>  
  
  
