---
title: ADOMD.NET サーバープログラミング |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 7f7ff5be-3826-43a5-b94d-ddeec5ddb2eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 522478af0b19f1745d80f167e40345d4751136b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711118"
---
# <a name="adomdnet-server-programming"></a><span data-ttu-id="1423b-102">ADOMD.NET サーバー プログラミング</span><span class="sxs-lookup"><span data-stu-id="1423b-102">ADOMD.NET Server Programming</span></span>
  <span data-ttu-id="1423b-103">ADOMD.NET の ADOMD.NET サーバー コンポーネントは、(msmgdsrv.dll 内の) `Microsoft.AnalysisServices.AdomdServer` 名前空間内に存在します。</span><span class="sxs-lookup"><span data-stu-id="1423b-103">The ADOMD.NET server components of ADOMD.NET reside within the `Microsoft.AnalysisServices.AdomdServer` namespace (in msmgdsrv.dll).</span></span> <span data-ttu-id="1423b-104">これらのサーバーコンポーネントを使用して、のインスタンスで実行されるカスタム多次元式 (MDX) 関数およびストアドプロシージャを作成し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1423b-104">You use these server components to create custom Multidimensional Expressions (MDX) functions and stored procedures that are run on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1423b-105">サーバー オブジェクトによって、キューブとマイニング モデルをクエリする機能、および指定されたコンテキストで式を評価する機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1423b-105">The server objects provide the capabilities for querying cubes and mining models, and for evaluating expressions in a given context.</span></span> <span data-ttu-id="1423b-106">カスタム関数とストアド プロシージャを作成する利点としては、実行の高速化、配置の集中管理、メンテナンスのしやすさの向上などがあります。</span><span class="sxs-lookup"><span data-stu-id="1423b-106">The benefits for creating custom functions and stored procedures include fast execution, centralized deployment, and improved maintainability.</span></span>  
  
 <span data-ttu-id="1423b-107">次の表に、ADOMD.NET サーバー アプリケーションの開発に役立つトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="1423b-107">The topics in the following table will help you develop ADOMD.NET server applications.</span></span>  
  
|<span data-ttu-id="1423b-108">トピック</span><span class="sxs-lookup"><span data-stu-id="1423b-108">Topic</span></span>|<span data-ttu-id="1423b-109">説明</span><span class="sxs-lookup"><span data-stu-id="1423b-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1423b-110">ADOMD.NET のサーバー機能</span><span class="sxs-lookup"><span data-stu-id="1423b-110">ADOMD.NET Server Functionality</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-functionality)|<span data-ttu-id="1423b-111">ADOMD.NET サーバー オブジェクトの使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1423b-111">Describes the uses for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="1423b-112">ADOMD.NET サーバー オブジェクト アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="1423b-112">ADOMD.NET Server Object Architecture</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-object-architecture)|<span data-ttu-id="1423b-113">ADOMD.NET サーバー オブジェクトのオブジェクト アーキテクチャを説明します。</span><span class="sxs-lookup"><span data-stu-id="1423b-113">Describes the object architecture for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="1423b-114">ユーザー定義関数およびストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1423b-114">User Defined Functions and Stored Procedures</span></span>](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures)|<span data-ttu-id="1423b-115">ユーザー定義関数またはストアド プロシージャを作成するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1423b-115">Walks you through the process of creating a user defined function or stored Procedure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1423b-116">参照</span><span class="sxs-lookup"><span data-stu-id="1423b-116">See Also</span></span>  
 <span data-ttu-id="1423b-117">[ADOMD.NET クライアントプログラミング](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span><span class="sxs-lookup"><span data-stu-id="1423b-117">[ADOMD.NET Client Programming](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span></span>  
 [<span data-ttu-id="1423b-118">ADOMD.NET での開発</span><span class="sxs-lookup"><span data-stu-id="1423b-118">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
  
  
